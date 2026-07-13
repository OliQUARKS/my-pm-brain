# Sprint 4 Refinement — Synthesis & Observations
**Date:** 2026-06-09  
**Participants:** Olivier (PM), Seba (PO PERC), Eze (Tech PERC)  
**Duration:** ~1 hour

---

## Theme 1: La Mantovana Ida y Vuelta (File Exchange Flow)

### Observation
The payment deduction cycle requires two file exchanges: (1) Quarks sends monthly "novedades" file listing which employee cuotas to deduct; (2) La Mantovana returns a "liquidación" file confirming which cuotas were actually deducted and the amounts. The reconciliation between sent and returned amounts is **manual in MVP** (operator compares, flags discrepancies, logs them).

*Provenance:* [source/meetings/2026-06-09-sprint4-refinement-perc.md](../../source/meetings/2026-06-09-sprint4-refinement-perc.md), 00:04–00:09 (ida y vuelta setup)

### Interpretation
This is a **strong coupling point** — if La Mantovana's file format changes, or if they delay returns, Sprint 4 desembolso flow stalls. Reconciliation complexity (what if monto discrepancy is ±$1?) is being deferred to manual BO operator judgment, which introduces human error risk and audit opacity.

### Decision Recorded
- (stakeholder-verbal, Seba, 2026-06-09): ida y vuelta rhythm is monthly (send one file, receive one back ~15 días later)
- (stakeholder-verbal, Eze, 2026-06-09): La Mantovana can return partial-batch confirmations; if 100 sent, may return 95 confirmed + 5 with errors; Quarks can re-submit corrected 5 in separate file

---

## Theme 2: File Delivery Method — Security vs Simplicity

### Observation
Three options discussed:
1. **Email (MVP baseline):** Operator manually downloads auto-generated Excel, sends via email to La Mantovana. Pro: simple. Con: editable Excel, audit trail breaks if operator modifies values before sending.
2. **S3 repo:** Auto-generated file placed in S3, La Mantovana downloads. Pro: immutable, logged. Con: requires cyber/compliance buy-in, unclear ownership (Quarks infra or PERC infra?).
3. **Backoffice download:** File generated and downloaded from BO UI. Pro: operator controls timing. Con: still editable locally.

Olivier flagged vulnerability: operator downloads Excel → modifies (e.g., changes $100 to $99.99) → sends to La Mantovana → system can't audit the change.

*Provenance:* [source/meetings/2026-06-09-sprint4-refinement-perc.md](../../source/meetings/2026-06-09-sprint4-refinement-perc.md), 00:30–00:35 (file format & delivery debate)

### Decision
**MVP approach:** Generate file automatically (configurable day/time), operator downloads and sends by email. Compromise: trackable (file generated log + email sent log), but vulnerable to Excel tampering.

**Escalation needed:** Validate with Tano (cybersecurity PERC) and Ariel (cybersecurity PERC) whether S3 is acceptable or if mail is the only viable MVP option.

*Provenance:* (stakeholder-verbal, Seba + Eze, 2026-06-09)

---

## Theme 3: Desembolso with Insufficient Funds (FIFO + Timeout)

### Observation
If La Mantovana has no funds to disburse a loan, the loan enters a **pending state**. The system polls the account balance every 5 minutes (parametrizable). If funds arrive within 24 hours, the loan disburses automatically in **FIFO order — but with a nuance: FIFO-by-payable-amount, not strict FIFO by arrival.**

Example: Two pending loans: $100 (arrived first) and $200 (arrived second). Account balance: $80. The system does NOT disburse $100 first and wait for $200; instead, it checks which loan(s) the $80 can cover and processes those. If $80 covers loan #3 ($80), loan #3 disburses even if loans #1 and #2 arrived earlier.

Olivier: "...o sea el archivo que yo envío y el archivo que yo recibo tiene que ser idéntico."  
Eze: "FIFO, pero de los que puedo pagar por ahora."

*Provenance:* [source/meetings/2026-06-09-sprint4-refinement-perc.md](../../source/meetings/2026-06-09-sprint4-refinement-perc.md), 00:19–00:25 (FIFO + polling logic)

### Interpretation
This is a **business rule clarification** that simplifies the implementation vs strict FIFO: "pay what you can in order, not in strict arrival order." Reduces complexity of queue management.

### Decision
- Poll frequency: Every 5 minutes (parametrizable via environment variable, not BO config)
- Timeout: 24 hours from pending state → loan expires/canceled
- Disbursement logic: FIFO-by-payable, not strict FIFO
- Notification: Show in-app "pending" status; when funds arrive, show "disbursed" (push notifications deferred to later iteration)

*Provenance:* (stakeholder-verbal, Seba + Eze, 2026-06-09)

---

## Theme 4: Scheduled Export — Who Configures?

### Observation
The file export needs to run automatically on a specific day/time each month (e.g., día 20 a las 14hs). Olivier asked: is this a Quarks Lambda/worker, or PERC infra handles it?

Eze suggested: "si eso es una Landa o un worker, si lo configura Gonza del lado de la infra cuándo ejecutar esa acción."

**Outcome:** Deferred for later. No decision recorded.

*Provenance:* [source/meetings/2026-06-09-sprint4-refinement-perc.md](../../source/meetings/2026-06-09-sprint4-refinement-perc.md), 00:29–00:31

### Open Question
- Who owns the scheduled task infrastructure for monthly export?
- How is the export day/time parameterized (env variable, database, BO config)?

---

## Theme 5: Batch Error Handling (Partial Success)

### Observation
If La Mantovana sends a batch of 100 cuota records and row 17 has a bad legajo, the system processes rows 1–16 successfully before hitting the error on row 17. Two approaches:
1. **Rollback:** Undo all 16 successful records, return batch for re-submission.
2. **Partial commit:** Keep the 16 successful, flag row 17 as error, allow re-import of corrected row 17 only.

Olivier initially favored rollback (consistency). Eze argued: "por lo menos así lo hacemos nosotros cuando hacemos pagos masivos...Si hay 235 que se procesaron bien, se enviaron la plata, está todo bien." → Accept partial success.

Seba proposed middle ground: Create a "preflight" validation state where all 100 rows are validated before writing to DB; if any fail, reject the entire batch. This trades 1 round-trip for safety.

**No firm decision.** Eze: "Nosotros podemos remontar donde fallan registros dentro del lote" (we can define casuísticas later).

*Provenance:* [source/meetings/2026-06-09-sprint4-refinement-perc.md](../../source/meetings/2026-06-09-sprint4-refinement-perc.md), 00:56–01:00

### Interpretation
This is a **critical edge case for accounting accuracy.** Partial success with manual remediation is operationally simpler but audit-heavier. Preflight validation is safer but slower. Decision deferred.

---

## Theme 6: Partial Payment Errors (Discrepancy Handling)

### Observation
If Quarks tells La Mantovana to deduct $100 but La Mantovana deducts $99, the reconciliation detects the $1 gap. What happens?

- Option A: Flag as error, operator manually notes "+$1 para cobrar en cuota próxima" in a notepad.
- Option B: Auto-adjust next cuota to include the $1.
- Option C: Create a "correction entry" in the system.

Seba: "hay que investigar por qué sucedió eso, porque todo el sistema está automatizado, nadie nunca pone algo a mano."

Eze: "se le puede cobrar en la siguiente cuota."

Olivier: "Yo, o sea, sé que es un caso recontra de borde, pero dije, ojo acá."

**Outcome:** Accept as edge case (Marcos said "casos border...los tratemos a mano, no son significativos"), manual BO resolution for MVP.

*Provenance:* [source/meetings/2026-06-09-sprint4-refinement-perc.md](../../source/meetings/2026-06-09-sprint4-refinement-perc.md), 00:08–00:13 (conciliación debate)

### Interpretation
This is a **balance-sheet risk.** Even small discrepancies add up across payroll cycles. Deferring to manual handling is pragmatic for MVP but needs audit trails and eventual automation.

---

## Theme 7: File Content & Format

### Observation
The Mantovana file must include:
- Employee identification: CUIL or DNI or legajo (depends on La Mantovana's finegans layout)
- Loan ID
- Cuota amount
- Cuota state (pagada, pendiente, etc.)

Seba: "Ahí yo te tengo que dar el Excel que consume Finegans y va a tener todas las columnas necesarias."

Fields are conditional on whether La Mantovana is processing individual vs empresa payroll (PJ vs CUIL/DNI).

*Provenance:* [source/meetings/2026-06-09-sprint4-refinement-perc.md](../../source/meetings/2026-06-09-sprint4-refinement-perc.md), 00:35–00:40

---

## Theme 8: Notification Model (Deferred)

### Observation
How does an employee know their pending loan is waiting for funds, or when it's disbursed?

Options:
1. Push notification (not ready for MVP)
2. In-app status screen (showing "pending, awaiting funds...")
3. Email (would add integration)
4. SMS (out of scope)

**Decision:** MVP uses in-app status only. "Alcanza con esa pantalla" — show "estás en fila de espera" and "fondos llegaron, tu préstamo se procesó."

*Provenance:* [source/meetings/2026-06-09-sprint4-refinement-perc.md](../../source/meetings/2026-06-09-sprint4-refinement-perc.md), 00:26

---

## Contradictions with Prior Decisions

**None detected.** This meeting details Sprint 4 desembolso + La Mantovana flow, which is distinct from Sprint 1–3. No reversal of earlier decisions.

---

## Promotion Candidates

### To feature file
- [ ] Desembolso logic (with/without funds, FIFO-by-payable, 24h timeout)
- [ ] La Mantovana file exchange (send + receive + reconcile)
- [ ] File delivery method (email MVP, S3 deferred)
- [ ] Batch error handling approach (partial success vs preflight)
- [ ] Reconciliation and discrepancy edge cases

### To decisions/ (new)
- [ ] **Decision: File delivery method (email MVP)** — once Tano/Ariel validate
- [ ] **Decision: FIFO-by-payable disbursement** — explicit algorithm definition

### To hypotheses/
- None new; desembolso logic is already in scope per PRD

---

## Open Questions (No Judgment Yet)

1. **File delivery: which option is acceptable?** Mail (vulnerable) vs S3 (complex) — needs cyber sign-off.
2. **Scheduled export ownership:** Quarks Lambda or PERC infra?
3. **Exact export day/time:** When does Seba want the file sent to La Mantovana?
4. **Batch partial-failure handling:** Rollback-entire vs partial-commit vs preflight validation?
5. **Discrepancy ±$1:** Manual note, auto-carry-forward to next cuota, or system correction entry?

---

*Ingestion complete. Synthesis promotes desembolso + La Mantovana flow to feature file; open questions flag to Seba for next refinement.*
