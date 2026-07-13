# Sprint 4 Refinement — PERC — Jun 9, 2026

**Participants:** Olivier Luce (PM Quarks), Sebastián Cárdenas (PO PERC), Ezequiel Manfredi (Tech Lead PERC)  
**Duration:** ~1 hour  
**Date:** 2026-06-09

---

## Transcript (Verbatim)

[Full transcript as provided in /ingest input — see ingestion/ file for synthesis]

### High-level agenda
1. **Ida y vuelta con La Mantovana** — novedad file format, timing, delivery method, reconciliation
2. **Desembolso de préstamos** — escenarios con/sin fondos, FIFO, timeout 24h, notificaciones
3. **Generación de archivo de novedades** — automático vs manual, qué campos, cuándo exportar
4. **Importación de liquidaciones** — recepción, validación, conciliación, errores, auditoría
5. **Cancelaciones** — ya resueltas (3 tipos: 24h sin fondos, arrepentimiento 10d, anticipada con costo)

### Key decisions / agreements reached
- **File export timing:** Day-of-month + time parametrizable (e.g., día 20 a las 14hs), vs always automatic
- **File delivery:** MVP = file generated automatically, operator sends by email to La Mantovana manually (traceable but vulnerable)
- **FIFO disbursement:** Not strict FIFO by arrival, but FIFO-by-payable-amount (if pending loans are $100 + $200, and $100 arrives, loan A disburses; if $80 arrives before $200, loan B disburses if it's $80)
- **Reconciliation:** Quarks sends cuota file → La Mantovana returns descuento file 15 días después → BO operator compares and flags discrepancies
- **Partial payment errors:** If La Mantovana descuenta $99 when asked for $100, log error in BO, operator notes difference (+$1 para next cuota), audit the discrepancy
- **Notification for pending loans:** Show in-app "estás en fila de espera"; when funds arrive, same push/notification system (deferred, will iterate when push is ready)
- **File format fields:** CUIL/DNI + loan ID + monto cuota + estado; CUIL vs QUID columns depend on Finegans layout
- **Batch error handling:** If 100 records sent and 95 succeed, 5 fail, mark as error and allow re-import with corrected 5-record file (don't rollback the 95)

### Open questions / pending clarification
- **Who configures scheduled export?** Olivier asked if it's Quarks (Lambda) or PERC infra (Gonza) — tabled for later
- **File delivery method final decision:** Mail (MVP, traceable but vulnerable) vs S3 (needs compliance/cyber alignment) — needs validation with Tano (cyber PERC) and Ariel (cyber PERC)
- **Exact day/time of export:** "día a configurar" — needs Seba + PERC to confirm (mentioned ejemplo: día 20 a las 2pm)
- **FIFO priority when amount partially covers:** Clarity on exact algorithm when arriving amount doesn't cover highest-pending loan but covers others
- **Push notifications:** Deferred; using in-app only for MVP; will iterate when notifications ready

### Tensions / edge cases flagged
- **Vulnerability of editable Excel export:** If operator downloads Excel that's open for editing, they can manually change values (invert amounts, etc.) before sending to La Mantovana — audit trail breaks. Mitigation: accept as MVP risk, validate with Tano/Ariel whether S3 + encrypted link is acceptable or mail is only viable
- **Batch partial failure handling:** If La Mantovana sends batch of 10 and 1 record has wrong legajo, won't know until row 10 processes; other 9 already processed → need to allow re-import of corrected record(s)
- **Correction on already-paid cuota:** If La Mantovana re-sends a cuota that's already been paid, system should reject it as error; but La Mantovana likely re-exports entire batch, meaning all 9 good records get re-processed (potential duplicate payment risk)
- **Multiple exports per month:** If file generation fails partway (95/100), La Mantovana has 15-day window to reprocess; Quarks may send multiple files in the month; reconciliation must match "file sent on X" with "file returned on X+15"

### Stakeholder postures captured
- **Seba:** Favors simple flow (send file monthly with that month's cuotas, La Mantovana returns confirmation), defers complexity to next iteration; unsure about file format/delivery but leans toward email as baseline
- **Eze:** Pragmatic on error handling ("partial batches are normal, we process the good ones and handle outliers manually"); concerned about reconciliation logic and needs time to think through FIFO edge cases
- **Olivier:** Pushing for clarity on edge cases (partial discrepancies, discrepancy ±$1 scenarios, notification timing); flagging audit/security risks of editable Excel approach

---

## Raw notes from earlier parts
- Olivier spent 37th birthday working ("no laboré pero pidieron el chat")
- Fede (COO Quarks) was missed ("Fefe te extrañó")
- Nico (Tech Lead Quarks) was late to other meeting, not in attendance
- Call was originally supposed to happen earlier but was postponed for technical/other reasons

---

*This is the immutable source artifact. Do not edit after creation.*
