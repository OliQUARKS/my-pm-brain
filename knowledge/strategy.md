# Strategy

> The north star. Loaded at the start of any prioritization, planning, or review task. Updated only deliberately — drift is surfaced, not silently absorbed.

## North-star metric
<!-- Pre-production. No live metric yet. Candidate metric: loan adoption rate among eligible employees (accepted loans / total eligible employees). Target TBD post-launch. -->
**Candidate:** Tasa de adopción — préstamos aceptados / empleados habilitados. Current value: N/A (pre-producción). (chat, no artifact)

## 1–2 quarter priorities
<!-- 3 max. Ordered. Each with: what, why now, what success looks like. -->
1. **Llevar Flujo Crédito a producción (MVP)** — es el único scope activo y el entregable contratado. Éxito: empleados de PERC (8,000 usuarios habilitados) pueden autogestionar un préstamo de extremo a extremo sin intervención manual. (stakeholder-verbal, Olivier, 2026-05-21)
2. **Cerrar definiciones bloqueantes con PERC** — integración Watson sin validar, pipeline CI/CD no acordado. **Tech stack decidido** (Lambda + Angular, 2026-04-20 — [decisions/2026-04-20-tech-stack.md](../decisions/2026-04-20-tech-stack.md)). Sin Watson y CI/CD, no hay estimaciones firmes. Éxito: integración Watson validada + pipeline CI/CD acordado al finalizar el mes de discovery. (source/adhoc/2026-05-21-prd-flujo-credito.md §5)
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
2026-06-17 — ingest planning Sprint 4. Tensión "circuito de cancelaciones = scope creep" agregada (escala a Fefe). Pendiente PM: resolver fork de scope de cancelaciones.
2026-06-12 — review #3. Cadencia propagada (5 stakeholders 6/9+6/12). Tensión T&C 5→1 agregada. Pendiente PM: trigger de escalación Seba (¿cumplido?), BIND 65 días.
2026-05-22 — review #2. P#2 actualizada (tech stack decidido). Tensión Seba agregada.

## Tensions
<!-- Maintenance and ingestion append here when signals conflict with the strategy. Tensions are not rejections — new bets, features, opportunities, and user needs can inform strategy just as strategy informs them. Each entry: signal, what it tensions, possible resolutions (update strategy / reject signal / hold as open tension). PM resolves deliberately. -->

**Fricción de Seba como riesgo de velocidad para el discovery.** Seba (PO PERC) postergó o no respondió definiciones en ≥4 instancias entre 2026-05-13 y 2026-05-22: email pendientes sin respuesta ([ingestion/adhoc/2026-05-13-email-definiciones-pendientes-perc.md](../ingestion/adhoc/2026-05-13-email-definiciones-pendientes-perc.md)); documentos dinámicos/estáticos sin cerrar ([ingestion/meetings/2026-05-20-refinement-backlog-perc.md](../ingestion/meetings/2026-05-20-refinement-backlog-perc.md)); IVA cancelación y cancelación anticipada diferidos al lunes 2026-05-26 ([ingestion/adhoc/2026-05-22-whatsapp-excel-calculo-prestamos.md](../ingestion/adhoc/2026-05-22-whatsapp-excel-calculo-prestamos.md)); pregunta BIND compliance sin respuesta desde 2026-04-08. Tensa: prioridad #1. Trigger de escalación: si las definiciones bloqueantes siguen abiertas 2+ sprints post-discovery, escalar a Marcos Copello (CEO PERC). Resoluciones posibles: (a) escalar a Marcos; (b) desbloquear vía spike técnico donde sea factible; (c) renegociar timeline con Quarks. `(observation, múltiples fuentes, 2026-05-13 a 2026-05-22)`

**Circuito de cancelaciones = posible scope creep vs. contrato "registro-only".** En la planning del 2026-06-17, el equipo razonó que confirmar correctamente una cancelación (arrepentimiento / anticipada / desistimiento) desde el BO obligaría a construir un **circuito completo de reporte de cancelaciones** (extracción + envío a La Mantovana + recepción + conciliación del total descontado) — un alcance que **nunca se conversó en el contrato**, cuyo límite original fue "Quarks **registra** cancelaciones pero **no las efectúa**" (flujo manual). Tensa: prioridad #1 y la decisión de scope del 20/5. Riesgos planteados: un BO podría marcar "cancelado" sin evidencia; los datos del reporte son sensibles. Por ahora se quitó la validación de fondos de las historias de cancelación (BO solo cambia de estado). Resoluciones posibles: (a) mantener registro-only y dejar la conciliación de cancelaciones como proceso manual fuera de Quarks; (b) construir el circuito como **step 2 / oportunidad comercial** (renegociar scope con PERC); (c) confiar en el BO con trazabilidad de usuario, sin reporte de vuelta. **No resuelto** — Olivier lo escala primero a Fefe/Juampi, luego a PERC, para definir el nivel de trazabilidad deseado. `(interpretation, equipo Quarks, [ingestion/meetings/2026-06-17-planning-sprint4-perc.md](../ingestion/meetings/2026-06-17-planning-sprint4-perc.md))`

**Unificación de T&C (5 documentos → 1) vs. modelo de sábana/firma.** En el call del 2026-06-12 Seba mencionó que **legales estaría permitiendo unificar los términos y condiciones en un solo archivo**, cuando antes eran cinco ("voy a consultar si sigue siendo uno, pero idealmente es uno"). Tensa la decisión [decisions/2026-05-20-sabana-no-persiste.md](../decisions/2026-05-20-sabana-no-persiste.md) (sábana render-only + **5 documentos persistidos** para compliance) y, potencialmente, el modelo de firma (TOTP → persistir N docs). **No resuelto:** es un cambio propuesto por legales, aún sin confirmar — Seba dijo "voy a consultar". La decisión del 20/5 sigue válida como artefacto; lo que puede cambiar es el número de documentos persistidos, no el principio de persistencia para compliance. Resoluciones posibles: (a) esperar confirmación escrita de legales y recién ahí revisar la decisión de sábana; (b) mantener el diseño a N documentos hasta confirmación (más seguro); (c) si se confirma 1 doc, simplificar firma y persistencia. `(observation, [ingestion/meetings/2026-06-12-proceso-prestamos-mantovana.md](../ingestion/meetings/2026-06-12-proceso-prestamos-mantovana.md))`
