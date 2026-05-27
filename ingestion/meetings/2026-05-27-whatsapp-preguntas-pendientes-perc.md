# Ingestion: Preguntas Pendientes Resueltas (27/5/26)

## Observations

### 1. La Mantovana — estructura clara, timeline pending
**(decision, resolved partially)** Isis (La Mantovana/Finnegans) ahora pasará dos artefactos: (a) Excel para que suban las cuotas y sean descontadas; (b) Informe para descarga de comprobantes. Estructura bidireccional confirmada, pero timing del reporte mensual aún unclear. `[source/meetings/2026-05-27-whatsapp-preguntas-pendientes-perc.md]`

### 2. Plazo desembolso (24h) — pending confirmación Marcos
**(decision, pending)** Seba no tiene confirmación aún. Olivier sugirió 24h en 2026-05-22, pero Marcos (CEO PERC) no lo cerró. Seba lo manda por mail. Sin confirmación, imposible cerrar histórico para BO. `[source/meetings/2026-05-27-whatsapp-preguntas-pendientes-perc.md]`

### 3. PRs pendientes — Jose a confirmar
**(observation)** Seba se lo averigua a Jose (Dev PERC). No está claro cuántos PRs ni qué repo. Bloquea confirmación de integración. `[source/meetings/2026-05-27-whatsapp-preguntas-pendientes-perc.md]`

### 4. Empleados PJ — hay confusión en la pregunta
**(assumption, Olivier, needs clarification)** Olivier preguntó si están "discriminados en los datos que llegan, para poder identificarlos en BO". Seba preguntó si "la persona juridica a la cual pertenecen es un dato que ustedes [Quarks] nos den". Hay brecha de entendimiento. Olivier probablemente preguntaba: ¿PERC tiene un flag/field en su data que indique si un empleado es PJ? Seba lo interpretó: ¿Quarks necesita que PERC proporcione esa data? Sin claridad, no se puede implementar BO (si no hay form field para PJ, no se puede distinguir). `[source/meetings/2026-05-27-whatsapp-preguntas-pendientes-perc.md]`

### 5. Documentos HTML (dinámicos vs estáticos) — blockeado, requiere reunión
**(decision, blocked on meeting)** Seba no tiene respuesta de Patricio (Compliance PERC). Le preocupa. Solicita reunión tripartita: Nicolas Ortiz (a confirmar rol), Patricio Ertola (Compliance PERC), ambos equipos. Sin aclarar dinámicos vs estáticos, no se puede estimar parser + mapeo de variables. Esto es una bloqueante técnica. `[source/meetings/2026-05-27-whatsapp-preguntas-pendientes-perc.md]`

### 6. Cancelación anticipada — decisión abierta a Quarks
**(decision, deferred to Quarks)** Seba confirma: "es una decision de ustedes. lo que sea mejor. nosotros no tenemos un requerimiento." Es decir, PERC no requiere específicamente precalculada vs on-demand. Olivier lo marcó como "good", implicando que irá a Quarks (probablemente on-demand es más limpio). Nico (Tech Lead) debe confirmar enfoque. `[source/meetings/2026-05-27-whatsapp-preguntas-pendientes-perc.md]`

### 7. IVA en cancelaciones — observable técnico
**(observation, raises design question)** Olivier nota que el Excel lo marca como "configurable" (flag B8 = 1). "Eso me hace ruido" implica que la lógica es: si el usuario paga before cancelación, ¿por qué se le cobra penalidad? Esto es más un tema de UX/negocio que técnico. PERC no lo aclaró, pero Olivier está levantando la question. Sin respuesta explícita, la fórmula es: Total = Capital restante + (Int. futuros × % penalidad) + (Capital × % comisión) + IVA. Si PERC quiere "no cobrar si paga bien," necesita cambiar el flujo (ej. ofrecer calculadora antes de la solicitud). `[source/meetings/2026-05-27-whatsapp-preguntas-pendientes-perc.md]`

## Routing

### Durable Layer Updates

**`stakeholders/sebastian.md`:**
- Touchpoint log: agregar 2026-05-27 entry
- Open asks: actualizar con pending (plazo desembolso, docs dinámicos, empleados PJ claridad, IVA design question)

**`knowledge/product/features/flujo-credito.md`:**
- Open questions: actualizar con estado de cada pregunta (resolved / pending / blocked on meeting)
- Risks: actualizar con "Documentos dinámicos" como bloqueante de reunión tripartita

**`decisions/`:**
- Crear 2026-05-27-cancelacion-anticipada-decisión-abierta.md (on-demand vs precalculada — PERC no requiere, Quarks decide)
- Crear 2026-05-27-iva-cancelacion-design-question.md (si configurar % o deshabilitar cobro cuando usuario paga antes)

### No promotion to hypotheses or strategy this round
- Observations are routing-level only.
- Strategy tension (Seba fricción) ya está documentada en strategy.md.

## Open Questions for PM

1. **Empleados PJ — claridad:** ¿PERC proporciona field/flag PJ en los datos del usuario, o Quarks debe solicitar BO form field? Impacto: BO feature completeness.
2. **IVA cancelación — intención:** ¿PERC quiere permitir al usuario calcular cancelación anticipada ANTES de solicitar (para que vea costo y decide)? ¿O es un costo que siempre se aplica? Impacta UX + cálculo de cancelación.
3. **Reunión documentos HTML:** ¿Olivier coordina? ¿Nico lidera? Participes: Nicolas Ortiz, Patricio Ertola (Compliance PERC), ambos equipos. Timing urgente.
