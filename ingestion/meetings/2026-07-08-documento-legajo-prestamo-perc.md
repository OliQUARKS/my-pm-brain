# Ingesta — Documento / Legajo de Préstamo (PERC, 2026-07-08)

- **Fuente (transcript):** [../../source/meetings/2026-07-08-documento-legajo-prestamo-perc.md](../../source/meetings/2026-07-08-documento-legajo-prestamo-perc.md)
- **Fuente (documento legal):** [../../source/adhoc/2026-07-08-legajo-prestamo-amfays-v1.md](../../source/adhoc/2026-07-08-legajo-prestamo-amfays-v1.md)
- **Participantes:** Olivier (PM Quarks), Marcos Perez (dev Quarks), Sebastián Cárdenas (PO PERC)
- **Shape:** meeting
- **Tema:** el documento/legajo legal del flujo de crédito — formato, campos y cómo cargarlos.

## Contexto

El documento es un **legajo de préstamo emitido por AMFAYS** (Asociación Mutual de las Fuerzas Armadas y de Seguridad). No es de PERC ni de Quarks: es una plantilla de una mutual, cuyos formularios **están aprobados por una entidad regulada por la Superintendencia de Seguros**. PERC insistió en usar este mismo documento porque ya está aprobado. Contiene **9 sub-documentos/formularios** (identificados por código A###):

| Código | Documento | Rol en el flujo |
|---|---|---|
| A104 | Solicitud de Socio AMFAYS | Alta como socio de la mutual |
| A237 | Solicitud de S.A.E.M. (Servicio de Ayuda Económica Mutual) | **La solicitud del préstamo** (núcleo) |
| A172 | Resumen TYC SAEM (Com. A 7199 BCRA) | Resumen de disposiciones significativas (tasas, revocación, precancelación) |
| A116 | Pagaré a la vista (descuento) | Título ejecutivo de la deuda |
| A169 | Instrucción irrevocable para desembolso | Instrucción de liquidación |
| A118 | Constancia de liquidación y recibo de pago | Recibo del desembolso |
| A152 | Autorización de débito de haberes | Autorización de retención mensual |
| A136 | Solicitud de Servicios Sociales | Servicios sociales/subsidios (óptica, farmacia, turismo, subsidios) |
| A143 | DDJJ PEP / UIF (Res. 99/2023 + 35/2023) | Declaraciones juradas antilavado |

## Observaciones (tagged)

- **(observation)** Carga del documento debe ser **siempre en HTML** (para editar variables: apellido, nombre, fecha de nacimiento, documento, etc.); el sistema lo entrega en **PDF** al usuario. Coincide con la decisión previa [decisions/2026-06-01-documentos-dinamicos-html.md](../../decisions/2026-06-01-documentos-dinamicos-html.md) (HTML→PDF). — Seba, [source/meetings/2026-07-08-documento-legajo-prestamo-perc.md](../../source/meetings/2026-07-08-documento-legajo-prestamo-perc.md)
- **(observation)** El .docx llegó con formato "raro": tablas, cuadraditos, campos imprimibles (`#FIRMA#`, líneas para completar a mano). Es un **formato de imprimir-y-llenar a mano**, no un template digital. — Seba, ídem.
- **(interpretation → sugerencia de Seba)** Convertir todo a **formato plano/texto** (no tablas) para poder insertar variables `{{campo}}` y reemplazarlas por datos del usuario; las tablas "van a quedar raras". — Seba, ídem.
- **(observation)** El endpoint `mi cuenta` (datos de la cuenta logueada) devuelve: **antigüedad, legajo, localidad, código postal, PJ** (entre otros). "Todo lo demás no está." Para el resto: (a) anexar campos al endpoint de cuenta, o (b) un front de data entry. — Seba, ídem.
- **(observation / scope)** Un **formulario de data entry** donde el usuario carga datos **no está en el scope** — nunca se diseñó ni se conversó. Confirmado por Olivier. — [source/meetings/...](../../source/meetings/2026-07-08-documento-legajo-prestamo-perc.md)
- **(observation / scope)** Campos de **datos familiares** y **datos del beneficiario del subsidio** (tablas en A104) son de carga manual y **quedan fuera del alcance**. — Olivier, ídem.
- **(assumption, Seba, 2026-07-08)** Lo que aprueba la Superintendencia/entidad reguladora es **el contenido, no el formato** (Seba lo cree "obvio" pero debe confirmarlo). Si aprobaran también el formato, cambiar a HTML plano sería más complejo. **No confirmado.**
- **(observation)** El endpoint **"obtener CVU" indica si la cuenta tiene dinero pero NO informa cuánto** — es un booleano tiene/no-tiene, no un saldo. Insuficiente para validar fondos contra el monto a desembolsar. — Seba, ídem.
- **(observation)** El endpoint de **cash out** (desembolso) todavía no se pudo probar: **pide variables que no están en el Insomnia** que PERC pasó. Seba lo va a pedir por el grupo. — Seba/Marcos, ídem.
- **(interpretation, equipo)** Riesgo de **race condition** entre consultar fondos y transferir: entre ambos pasos (aunque sea microsegundos) los fondos pueden dejar de estar disponibles o quedar en estado no-enviable. Idea planteada (Seba + Olivier): un endpoint que **consulte-y-reserve** o que **consulte-y-desembolse** en una sola llamada (indicar cuánto quiero, verifica y saca). Reconocido como fuera de la tarea de Quarks — dependería de PERC. — ídem.
- **(observation)** **FIFO reconfirmado** en el call: "primero que entra es el primero que sale" (Marcos preguntó; Olivier confirmó). Coherente con [decisions/2026-06-17-desembolso-fifo.md](../../decisions/2026-06-17-desembolso-fifo.md). — ídem.

## Coordinación / logística

- **(observation)** Job (reviewer de PRs, PERC) está **de licencia hasta el lunes 2026-07-13**. PERC **no trabaja mañana ni pasado (Jul 9 y 10)**. Quarks manda los PRs y quedan en cola; PERC los revisa el lunes. — Seba, ídem.
- **(observation)** Plan acordado: mientras se aprueban PRs, Quarks avanza el **happy path** asumiendo que pasan. — Seba, ídem.
- **(decision operativa, Olivier + Seba)** Escenarios para el UAT:
  - **Best case:** el lunes 13 se cuenta con los documentos + el endpoint de fondos → sale el UAT con margen para correcciones.
  - **Worst case:** el lunes a la tarde sin documentos y/o sin endpoint de validación de fondos → **se mueve la reunión / el UAT**.
- **(action)** Olivier pasa a Seba el **requerimiento del documento en limpio y estructurado** (esta tarea). Seba lo lleva internamente a PERC para que decidan.
- **(action, Seba)** Seba pide por el grupo: (1) endpoint para **consultar saldo/fondos** de la cuenta recaudadora, (2) variables faltantes del endpoint de **cash out**.

## Las 3 preguntas que Seba se llevó a PERC

1. **¿Se puede cambiar el formato?** (pasar de imprimir-y-llenar a HTML plano con variables) — depende de si la Superintendencia aprueba formato o solo contenido.
2. **¿Cuáles son los datos mínimos necesarios** para pedir el préstamo? (no hace falta llenar todos los campos del legajo).
3. **¿Cómo se hace el input de los datos** que no vienen en `mi cuenta`? Tres caminos: (a) anexar campos al endpoint de cuenta; (b) que el usuario complete un formulario (**fuera de scope**); (c) idea nueva de PERC.

## Ruteo

- **Durable (propuesto, requiere OK del PM — propose-and-wait):**
  - `knowledge/product/features/flujo-credito.md` → resolver/actualizar la open question "cuáles documentos exactos" (ahora conocemos los 9 formularios AMFAYS); agregar dependencia "endpoint de saldo/fondos" (el CVU no informa monto) y "endpoint cash out incompleto"; agregar riesgo de race-condition consultar-vs-transferir.
  - `stakeholders/sebastian.md` + `stakeholders/marcos-perez.md` → touchpoint 2026-07-08.
  - `knowledge/compliance/credito/` → nota sobre el origen AMFAYS/Superintendencia de Seguros de los formularios y la pregunta abierta de "aprueban formato o contenido".
  - Posible decisión futura: qué se hace con los campos fuera-de-endpoint (esperar definición de PERC).
- **Sin promoción a `knowledge/users`** — no es señal de usuario, es definición de producto/compliance.

## Contradicciones / tensiones

- Toca la tensión **"5 docs → 1"** de [strategy.md](../../knowledge/strategy.md#tensions): este legajo tiene **9 formularios**, no 5. Habrá que reconciliar qué documentos entran realmente en el flujo de firma del MVP vs. cuáles son de la mutual y no aplican (p.ej. A136 Servicios Sociales parece ajeno al préstamo; A104 alta de socio; datos familiares/subsidio). **No resuelto** — dato para el requerimiento y para revisar con Seba/legales.
