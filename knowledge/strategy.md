# Strategy

> The north star. Loaded at the start of any prioritization, planning, or review task. Updated only deliberately — drift is surfaced, not silently absorbed.

## North-star metric
<!-- Pre-production. No live metric yet. Candidate metric: loan adoption rate among eligible employees (accepted loans / total eligible employees). Target TBD post-launch. -->
**Candidate:** Tasa de adopción — préstamos aceptados / empleados habilitados. Current value: N/A (pre-producción). (chat, no artifact)

## 1–2 quarter priorities
<!-- 3 max. Ordered. Each with: what, why now, what success looks like. -->
1. **Llevar Flujo Crédito a producción (MVP)** — es el único scope activo y el entregable contratado. Éxito: empleados de PERC (8,000 usuarios habilitados) pueden autogestionar un préstamo de extremo a extremo sin intervención manual. (stakeholder-verbal, Olivier, 2026-05-21)
2. **Obtener definiciones técnicas bloqueantes de PERC** — tech stack (Lambda/Java/TypeScript) y validación de integración Watson pendientes. Sin esto no hay estimaciones firmes. Éxito: stack definido + pipeline CI/CD acordado al finalizar el mes de discovery. (source/adhoc/2026-05-21-prd-flujo-credito.md §5)
3. **Compliance: firma unificada y documentos auditables** — requisito legal no negociable. Éxito: flujo de firma genera 1 PDF con 5 documentos embebidos, auditable y descargable por el usuario. (source/adhoc/2026-05-21-prd-flujo-credito.md §3.A)

## Explicit non-goals
<!-- What we are deliberately NOT doing this period. This is the most valuable section. -->
- Calculadora de préstamos para el usuario (source/adhoc/2026-05-21-prd-flujo-credito.md §6)
- Notificaciones push (source/adhoc/2026-05-21-prd-flujo-credito.md §6)
- Cancelación parcial (source/adhoc/2026-05-21-prd-flujo-credito.md §6)
- Préstamos personalizados desde Backoffice (source/adhoc/2026-05-21-prd-flujo-credito.md §6)
- Scoring en tiempo real (source/adhoc/2026-05-21-prd-flujo-credito.md §6)
- Créditos múltiples o simultáneos (source/adhoc/2026-05-21-prd-flujo-credito.md §6)
- Expansión a terceros / multitenant (estructura contemplada pero fuera de scope) (source/adhoc/2026-05-21-prd-flujo-credito.md §6)
- Nada después de que Flujo Crédito llegue a producción — no hay scope adicional contratado. (stakeholder-verbal, Olivier, 2026-05-21)

## Bets vs. commitments
- **Bets** (testing): see [`hypotheses/`](../hypotheses/)
- **Commitments** (decided): see [`decisions/`](../decisions/)

## Last reviewed
2026-05-21 — init desde entrevista de setup.

## Tensions
<!-- Maintenance and ingestion append here when signals conflict with the strategy. Tensions are not rejections — new bets, features, opportunities, and user needs can inform strategy just as strategy informs them. Each entry: signal, what it tensions, possible resolutions (update strategy / reject signal / hold as open tension). PM resolves deliberately. -->
