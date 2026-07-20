# Sebastián Cárdenas — Product Owner, PERC

## Snapshot
- Role: Product Owner, PERC
- Reports to / works with: Marcos Copello (CEO PERC)
- Influence on my work: high
- Friction level: high

## What they care about
<!-- Interpretation — basado en el contexto del proyecto. -->
- Que el producto cumpla los requisitos de compliance y operación interna de PERC
- Control del scope y prioridades del MVP
(intuition, PM, 2026-05-21)

## Concerns / watch-outs
**Principal fuente de fricción:** tarda mucho en proveer definiciones, lo que bloquea el refinement del equipo Quarks. (stakeholder-verbal, Olivier, 2026-05-21)
- Definiciones de negocio pendientes (integración Watson) bloqueadas en su lado. Stack técnico resuelto por Eze (CTO PERC) — ya no es su responsabilidad.

## Communication style
Disponible en calls, participativo cuando está presente. Tarda en responder fuera de las reuniones (mails y chats sin respuesta inmediata). Mejor canal: reuniones sincrónicas con agenda clara. (stakeholder-verbal, Olivier, 2026-05-20)
**Actualización 2026-05-22:** WhatsApp con bullets cortos y numerados es canal efectivo — respondió en ~6 minutos. (interpretation, [ingestion/adhoc/2026-05-22-whatsapp-pendientes-perc.md](../ingestion/adhoc/2026-05-22-whatsapp-pendientes-perc.md))

## Open asks
- ~~Cálculo de cuotas~~ — **Excel recibido 2026-05-22 15:44.** Metodología Sistema Francés completa. Pendientes derivadas: seguro de vida y relación monto prestado/capital solicitado. (observation, [ingestion/adhoc/2026-05-22-excel-calculo-prestamos-perc.md](../ingestion/adhoc/2026-05-22-excel-calculo-prestamos-perc.md))
- Plazo desembolso (24hs) — No hay confirmación aún. Seba lo manda por mail. Marcos (CEO) debe decidir. (stakeholder-verbal, Seba, 2026-05-27) [source/meetings/2026-05-27-whatsapp-preguntas-pendientes-perc.md]
- ¿Documentos dinámicos o estáticos? **Bloqueado en reunión tripartita.** Seba solicita: Nicolas Ortiz, Patricio Ertola (Compliance), ambos equipos. Seba tiene preocupación. (stakeholder-verbal, Seba, 2026-05-27) [source/meetings/2026-05-27-whatsapp-preguntas-pendientes-perc.md]
- Empleados PJ — hay confusión en la pregunta. Olivier preguntó si están discriminados en data; Seba preguntó si Quarks necesita que PERC lo proporcione. Sin claridad, no se puede implementar BO. (assumption, [ingestion/meetings/2026-05-27-whatsapp-preguntas-pendientes-perc.md](../ingestion/meetings/2026-05-27-whatsapp-preguntas-pendientes-perc.md))
- ~~PRs pendientes~~ — Seba se lo averigua a Jose. (stakeholder-verbal, Seba, 2026-05-27)
- Validación de integración con Watson — pendiente.
- IVA en cancelaciones — Olivier nota que es configurable (flag B8 = 1). Pregunta abierta: ¿PERC quiere cobrar penalidad si usuario paga antes de cancelación? Impacta fórmula de cálculo. (observation, [ingestion/meetings/2026-05-27-whatsapp-preguntas-pendientes-perc.md](../ingestion/meetings/2026-05-27-whatsapp-preguntas-pendientes-perc.md))

## Touchpoint log
- 2026-07-20 — SYNC PERC (C12) con Fefe + Nico. **Touchpoint decisivo:** resolvió la estrategia de datos del documento AMFAYS (existentes vía accounts/Sherlock; faltantes **mockeados** + proveeduría real diferida del lado PERC; documento desacoplado del MVP — decisión [2026-07-20-captura-datos-amfays](../decisions/2026-07-20-captura-datos-amfays.md)). Se comprometió a **mapear hoy** los datos que ya existen. Aportó la lectura estratégica de AMFAYS (cartera asegurable/securitizable → no le importa el drop-off). Tomó el caso de máxima en el biométrico (re-pedir en el flujo). **Engagement constructivo y resolutivo** — contrasta con el patrón de fricción por demora. [../ingestion/meetings/2026-07-20-sync-perc-c12.md](../ingestion/meetings/2026-07-20-sync-perc-c12.md)
- 2026-07-17 — Call Amfays <> PERc (relevamiento del documento). Confirmó que el **número de legajo está disponible en el endpoint** (= número de usuario) y hay que enviarlo; cerró que el cruce técnico de qué datos ya se capturan vs. hay que integrar lo definen él y Olivier. [../ingestion/meetings/2026-07-17-call-amfays-documento-prestamo.md](../ingestion/meetings/2026-07-17-call-amfays-documento-prestamo.md)
- 2026-07-16 — Demo/UAT con cliente. Levantó dos preocupaciones de negocio: (1) **conciliación financiera** — que "dar por pagado"/devoluciones sean auditables y cuadren contra la caja del banco (Marcos confirmó historial + finalización solo con balance exacto); (2) **decimales** — terceros que truncan harían caer todo a pago con error → pidió tolerancia. Derivó en el **threshold/delta** (a acordar aparte con Olivier, decisión de negocio de PERC). [../ingestion/meetings/2026-07-16-demo-uat-cliente-perc.md](../ingestion/meetings/2026-07-16-demo-uat-cliente-perc.md)
- 2026-06-12 — Call PERC × La Mantovana × Quarks (Proceso de Préstamos). Cerró el ida y vuelta: reporte = solo cuota del mes, día 20, por legajo, arrepentimiento requiere fondos, ajustes mes siguiente. Se llevó: casuística border (cancelación entre día 20 y pago) + fuente del legajo. Mencionó que legales permitiría unificar T&C de 5 docs a 1. [../ingestion/meetings/2026-06-12-proceso-prestamos-mantovana.md](../ingestion/meetings/2026-06-12-proceso-prestamos-mantovana.md)
- 2026-06-09 — Sprint 4 refinement interno. Desembolso con/sin fondos (FIFO-by-payable, polling 5 min, timeout 24h), file delivery por mail (MVP), batch partial-failure. [../ingestion/meetings/2026-06-09-sprint4-refinement-perc.md](../ingestion/meetings/2026-06-09-sprint4-refinement-perc.md)
- 2026-05-27 — WhatsApp: Olivier manda 7 preguntas pendientes. Seba responde: La Mantovana se contactó (excels + informe), plazo desembolso no confirmado aún (Marcos decide), documentos HTML bloqueado en reunión, empleados PJ hay confusión, PRs pendientes se lo averigua, cancelación anticipada es decisión de Quarks, IVA configurable genera pregunta de diseño. [source/meetings/2026-05-27-whatsapp-preguntas-pendientes-perc.md](../source/meetings/2026-05-27-whatsapp-preguntas-pendientes-perc.md)
- 2026-05-22 (16:10) — WhatsApp: comentarios sobre Excel. Confirmó seguro capitalizado al inicio + mora como costo en capital inicial. IVA cancelación difiere al lunes 2026-05-26. Pregunta abierta: cancelación precalculada o on-demand. [source/adhoc/2026-05-22-whatsapp-excel-calculo-prestamos.md](../source/adhoc/2026-05-22-whatsapp-excel-calculo-prestamos.md)
- 2026-05-22 (15:44) — Excel CALCULO DE PRESTAMOS PERC recibido. Metodología Sistema Francés completa con fórmulas de cuota y cancelación anticipada. Pendientes: seguro de vida + monto prestado vs capital solicitado. [ingestion/adhoc/2026-05-22-excel-calculo-prestamos-perc.md](../ingestion/adhoc/2026-05-22-excel-calculo-prestamos-perc.md)
- 2026-05-22 — WhatsApp pendientes PERC. Respondió 5 items en ~6 min: HTML con Patricio, Excel hoy, desembolso sugiere 24hs (Marcos decide), Isis no asistió al meet, PJ confirmados. [ingestion/adhoc/2026-05-22-whatsapp-pendientes-perc.md](../ingestion/adhoc/2026-05-22-whatsapp-pendientes-perc.md)
- 2026-05-20 — Refinement backlog PERC. Definiciones parcialmente resueltas (cuotas, cancelación anticipada, mora/desvinculación, estados del préstamo, firma). Pendiente: desembolso, documentos dinámicos, repo del front. [ingestion/meetings/2026-05-20-refinement-backlog-perc.md](../ingestion/meetings/2026-05-20-refinement-backlog-perc.md)

## Last touched
2026-07-20

