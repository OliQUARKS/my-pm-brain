# Ingestion: Preguntas Pendientes Resueltas (27/5/26)

## Observations

### 1. La Mantovana — estructura clara, timeline pending
**(decision, resolved partially)** Isis (La Mantovana/Finnegans) ahora pasará dos artefactos: (a) Excel para que suban las cuotas y sean descontadas; (b) Informe para descarga de comprobantes. Estructura bidireccional confirmada, pero timing del reporte mensual aún unclear. `[source/meetings/2026-05-27-whatsapp-preguntas-pendientes-perc.md]`

### 2. Plazo desembolso (24h) — pending confirmación Marcos
**(decision, pending)** Seba no tiene confirmación aún. Olivier sugirió 24h en 2026-05-22, pero Marcos (CEO PERC) no lo cerró. Seba lo manda por mail. Sin confirmación, imposible cerrar histórico para BO. `[source/meetings/2026-05-27-whatsapp-preguntas-pendientes-perc.md]`

### 3. PRs pendientes — Jose a confirmar
**(observation)** Seba se lo averigua a Jose (Dev PERC). No está claro cuántos PRs ni qué repo. Bloquea confirmación de integración. `[source/meetings/2026-05-27-whatsapp-preguntas-pendientes-perc.md]`

### 4. Empleados PJ — aclaración: requiere field/flag en datos PERC
**(observation, clarified via chat)** Olivier clarifica: "Ustedes tenían la necesidad de poder filtrar personas jurídicas. Mi pregunta va más desde cómo manejamos el dato en back. **¿En los datos que nos envían ustedes, tenemos identificado el campo que dice que es una persona jurídica?**" Contexto: "uno de los criterios de aceptación era poder filtrar por persona jurídica vs persona física." Seba confirma que sí es un dato, pero la pregunta original sobre si estaban "discriminados" generó confusión inicial. **Acción:** PERC debe confirmar que proporciona el field/flag en los datos para que BO pueda filtrar. `[source/meetings/2026-05-27-whatsapp-preguntas-pendientes-perc.md]`

### 5. Documentos HTML (dinámicos vs estáticos) — blockeado, requiere reunión
**(decision, blocked on meeting)** Seba no tiene respuesta de Patricio (Compliance PERC). Le preocupa. Solicita reunión tripartita: Nicolas Ortiz (a confirmar rol), Patricio Ertola (Compliance PERC), ambos equipos. Sin aclarar dinámicos vs estáticos, no se puede estimar parser + mapeo de variables. Esto es una bloqueante técnica. `[source/meetings/2026-05-27-whatsapp-preguntas-pendientes-perc.md]`

### 6. Cancelación anticipada — decisión abierta a Quarks + aclaración sobre mora
**(decision, deferred to Quarks)** Seba confirma: "es una decision de ustedes. lo que sea mejor. nosotros no tenemos un requerimiento." Es decir, PERC no requiere específicamente precalculada vs on-demand. Olivier lo marcó como "good". **Aclaración adicional sobre mora:** Seba está rearmando tabla Excel (más simple). Sobre mora: "la mora si se cobra como un adicional... es un % extra un chiquitin especial." Olivier pregunta: "pero si el tipo la paga en término, cómo es eso?" Seba responde: "es parte del costo. no hay devoluciones de nada." **Esto sugiere que la mora se cobra **siempre** como % fijo del capital, no como penalidad condicional.** `[source/meetings/2026-05-27-whatsapp-preguntas-pendientes-perc.md]`

### 7. IVA en cancelaciones — observable técnico + aclaración de Seba
**(observation, raises design question)** Olivier nota que el Excel lo marca como "configurable" (flag B8 = 1). "Eso me hace ruido" porque: si el usuario paga antes de cancelación, ¿por qué se le cobra penalidad? **Seba clarifica durante chat:** Está rearmando la tabla "es mas simple de lo que estamos pensando." Dice que solo necesita consultar "si se cobra algo de los interese futuros como penalidad o no." Esto implica que **la pregunta abierta es si se cobra % sobre intereses futuros como penalidad** (en caso de cancelación anticipada). Sin respuesta explícita, la fórmula es: Total = Capital restante + (Int. futuros × % penalidad) + (Capital × % comisión) + IVA. `[source/meetings/2026-05-27-whatsapp-preguntas-pendientes-perc.md]`

### 8. Excel rearmado — más simple
**(observation)** Seba está rehaciendo la tabla de cálculo. "Es mas simple de lo que estamos pensando." Hizo un sheet nuevo. Cambios: tabla más limpia, y pendiente aclaración sobre si se cobra penalidad sobre intereses futuros (cancelación anticipada). Olivier sugiere: "dejame verlo con fefe" (COO Quarks) antes de cerrar la decisión sobre cancelación/mora. `[source/meetings/2026-05-27-whatsapp-preguntas-pendientes-perc.md]`

## Routing

### Durable Layer Updates

**`stakeholders/sebastian.md`:**
- Touchpoint log: actualizar con nueva aclaración (empleados PJ, cancelación anticipada/mora, Excel rearmado)
- Open asks: actualizar con estado (plazo desembolso, docs dinámicos, Empleados PJ—requiere field/flag confirmación, penalidad sobre intereses futuros)

**`knowledge/product/features/flujo-credito.md`:**
- Open questions: actualizar con nueva info sobre mora (siempre se cobra como % fijo) y penalidad intereses futuros
- Risks: actualizar con "Documentos dinámicos" como bloqueante de reunión tripartita
- Cuota methodology: Excel being refactored — simplificado

**`decisions/`:**
- Crear 2026-05-27-cancelacion-anticipada-decisión-abierta.md (on-demand vs precalculada — PERC no requiere, Quarks decide)
- Crear 2026-05-27-mora-estructura-confirmada.md (mora = % fijo capitalizado, no condicional)

### No promotion to hypotheses or strategy this round
- Observations are routing-level only.
- Strategy tension (Seba fricción) ya está documentada en strategy.md.

## Open Questions for PM

1. **Penalidad sobre intereses futuros:** ¿PERC requiere cobrar % sobre intereses futuros en caso de cancelación anticipada? Seba dice que está consultando. Olivier sugiere "verlo con Fefe" (COO).
2. **Empleados PJ — confirmación:** ¿PERC confirma que proporciona field/flag PJ en los datos? Requerido para BO filtering.
3. **Reunión documentos HTML:** ¿Olivier coordina? ¿Nico lidera? Participes: Nicolas Ortiz, Patricio Ertola (Compliance PERC), ambos equipos. Timing urgente.
