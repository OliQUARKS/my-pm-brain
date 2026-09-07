# Discovery, RyD Abogados (pedidos de pago, Provincia ART)

**Fecha:** 2026-09-03
**Tipo:** Meeting (discovery call, cliente nuevo/prospecto)
**Fuente:** [../../source/meetings/2026-09-03-ryd-abogados-discovery.md](../../source/meetings/2026-09-03-ryd-abogados-discovery.md)
**Asistentes:** Juan Francisco Verde (RyD Abogados, socio/lead legal), Hernán Capolupo (RyD Abogados, socio/gestión operativa), Juan Pablo Norverto (Quarks, CTO), Lucía Guyet (Quarks, UX/UI; trabajó con RyD previamente), Olivier Luce (Quarks, PM), Federico Fernandez (Quarks, COO; se une sobre el final)

## Contexto (nuevo engagement, no PERC)

Este es un **discovery call para un cliente/proyecto nuevo de Quarks Alchemist**, no relacionado con PERC/Flujo Crédito. RyD Abogados es un estudio jurídico que gestiona litigios de compañías de seguros (10 clientes, principal: **Provincia ART**) y busca automatizar la carga de "pedidos de pago" post-sentencia/acuerdo. Es la primera reunión con este cliente en el brain; no hay hipótesis ni decisiones previas que esta ingesta actualice.

## Observaciones (tagged)

**Volumen y estructura del estudio**
- (observation) RyD Abogados tiene ~13,000 expedientes en trámite, 9 personas en el equipo de Juan (incluye a Hernán y Juan), 10 clientes (compañías de seguros). El foco de esta reunión es el cliente **Provincia ART**. `[source/meetings/2026-09-03-ryd-abogados-discovery.md]`
- (observation) El equipo de Juan Verde tiene 7 personas dedicadas a carga de pedidos de pago; Hernán estima que una sola persona puede tener ~20 pedidos de pago agendados para un día. `[source/meetings/2026-09-03-ryd-abogados-discovery.md]`
- (observation) Hernán recibe ~600 mails/día, muchos para reenviar manualmente. `[source/meetings/2026-09-03-ryd-abogados-discovery.md]`
- (observation) Ayer (2026-09-02) llegaron ~25 mails automáticos de confirmación de pago de Provincia ART en una sola tanda. `[source/meetings/2026-09-03-ryd-abogados-discovery.md]`

**El proceso actual (pedido de pago post-sentencia/acuerdo)**
- (observation) Sistema usado: **Lex Doctor** (ex Doctor). Cada expediente tiene un estado (ej. "sentencia firme" / "acuerdo homologado"). Tiene un sistema de placeholders binarios (`@125`, `@64`, etc.) para autocompletar datos del expediente en documentos Word/PDF; descrito por Hernán como "rígido, estructurado, sin evolución", "pronto va a desaparecer". `[source/meetings/2026-09-03-ryd-abogados-discovery.md]`
- (observation) El flujo, según el instructivo compartido por RyD ("CARGA DE PEDIDOS DE PAGO, CUENTA JUDICIAL/PARTICULAR"): (1) cambiar estado del proceso + verificar sentencia/homologación/liquidación cargada; (2) crear evento "SOLICITUD FONDOS - ACUERDO/SENTENCIA"; (3) requisitos difieren por tipo de pago; capital a cuenta particular (CBU+DNI del actor), honorarios letrados/peritos a cuenta particular (CBU + constancia ARCA + factura discriminada, no admite factura tipo B), pago a cuenta judicial (agrupa conceptos salvo tasa de justicia), tasa de justicia (evento separado, CABA vs. PBA con boleta de https://tasadejusticia.scba.gov.ar). `[source/meetings/2026-09-03-ryd-abogados-discovery.md]`
- (observation) Un mismo expediente puede generar **6-7 pedidos de pago separados** (uno por CBU/parte: abogado, actor, perito, tasa de justicia, etc.) porque cada uno tiene distinto CBU/documentación; antes bastaba un solo pago a la cuenta judicial. `[source/meetings/2026-09-03-ryd-abogados-discovery.md]`
- (observation) El estado de "pagado" en Lex Doctor es dependiente del conjunto: un expediente queda "trabado" en el mismo estado si falta un solo pago (ej. falta el perito aunque actor y abogado ya estén pagados). `[source/meetings/2026-09-03-ryd-abogados-discovery.md]`
- (observation) El seguimiento de qué falta por expediente se hace vía la función de **"agenda"** de Lex Doctor (recordatorios manuales por expediente, no hay vista global de "qué está trabado y por qué"; solo la agenda diaria/semanal de cada persona). `[source/meetings/2026-09-03-ryd-abogados-discovery.md]`
- (observation) El pedido de datos a terceros (abogado de la parte actora, perito) es por **mail manual**, pidiendo DNI del cliente, CBU del cliente, factura de honorarios y CBU propio. Llega "a cuentagotas"; a veces en partes, por WhatsApp o mail, no siempre estructurado. `[source/meetings/2026-09-03-ryd-abogados-discovery.md]`
- (observation) Hay una base de datos interna de abogados recurrentes ("abogados bolseros") con datos ya cargados (CBU, nombre, cuenta); 10 abogados representan ~50% del volumen, pero **cada caso puntual igual requiere una factura nueva** (no se puede reusar). `[source/meetings/2026-09-03-ryd-abogados-discovery.md]`
- (observation) Cierre del ciclo: la compañía (Provincia ART) manda un mail automático con constancia de pago (PDF) una vez procesada la orden de pago; RyD debe acreditar eso en el expediente manualmente (bajarlo, subirlo/redactar escrito). Hoy es manual; Hernán menciona que sería "ideal" que esa notificación se cargue automáticamente en el expediente. `[source/meetings/2026-09-03-ryd-abogados-discovery.md]`
- (observation) No hay instancia de aprobación intermedia en el flujo de pedido de pago; quien hace la carga entra directo al portal de Provincia ART y sube todo. `[source/meetings/2026-09-03-ryd-abogados-discovery.md]`
- (observation) El estudio solo cobra su propia factura cuando **todas las partes** de un expediente cobraron ("si no cobraron todos, nosotros no cobramos"); la administración interna emite la factura del estudio según el convenio de honorarios de cada compañía. `[source/meetings/2026-09-03-ryd-abogados-discovery.md]`

**Dolor / fricción (respuesta directa a la pregunta de Olivier sobre qué automatizar)**
- (observation, Juan Verde) La mayor fricción es la **carga en las compañías**: armar un evento por imputación/pedido, multiplicado por 6-7 pedidos por caso, con varias sentencias/homologaciones por día. `[source/meetings/2026-09-03-ryd-abogados-discovery.md]`
- (observation, Hernán) El trabajo es "las dos cosas": **buscar/pedir la información** (mails a abogados y peritos pidiendo CBU/factura/DNI) Y **cargarla** en el sistema de la compañía. Ambas partes consumen tiempo. `[source/meetings/2026-09-03-ryd-abogados-discovery.md]`
- (interpretation, Juan Pablo Norverto) La tarea es "totalmente administrativa, no tiene nada de abogacía en el medio"; desplaza tiempo de abogados especializados (ej. contestación de demanda) hacia trabajo mecánico repetitivo. `[source/meetings/2026-09-03-ryd-abogados-discovery.md]`
- (observation, Hernán) El estudio está descuidando la parte técnica/defensa legal porque el volumen de facturación/pedidos de pago absorbe al equipo (ejemplo dado: 400 contestaciones de demanda en un día repartidas entre el equipo). `[source/meetings/2026-09-03-ryd-abogados-discovery.md]`

**Intentos previos de optimización**
- (observation) Único intento previo: uso de placeholders binarios de Lex Doctor (`@125`, `@64`, etc.) para autocompletar campos por default en documentos; ahorra carga manual de esos campos, pero no toca el cuello de botella real (pedido de datos a terceros + carga en portal de la compañía). Es la primera vez que el estudio evalúa una optimización seria de este proceso. `[source/meetings/2026-09-03-ryd-abogados-discovery.md]`
- (observation) Hernán conoce un caso de un abogado (cliente de RyD: Triunfo Seguros) que ya delega credenciales a un agente/asistente que se loguea, entra al portal, busca el caso, baja documentación y genera el mail, sin que la compañía necesariamente lo sepa. Señala que Caja de Seguros es una compañía "avanzada" que podría exigir verificación de persona humana en el login. `[source/meetings/2026-09-03-ryd-abogados-discovery.md]`
- (observation) El equipo de RyD ya usa IA de forma informal (resumir sentencias, "hacer cosas") sin política formal. `[source/meetings/2026-09-03-ryd-abogados-discovery.md]`

**Adyacencias mencionadas (fuera del foco de hoy, pero señaladas como oportunidad futura)**
- (observation) **Mediaciones**: mail automático → alta en Lex → asignación de audiencia a abogado → mail al mediador. Flujo distinto, mencionado "muy por arriba" por Hernán como otro candidato a automatizar. `[source/meetings/2026-09-03-ryd-abogados-discovery.md]`
- (observation) Reglas de reenvío de mail (ej. Outlook), sugerido por Juan Pablo Norverto como quick-win no-IA. `[source/meetings/2026-09-03-ryd-abogados-discovery.md]`

**Alcance / encuadre del discovery (definido en la llamada)**
- (decision, en la llamada; Federico + Juan Pablo Norverto) El discovery se enfoca en **el área de Juan Verde** (las 7 personas cargando pedidos de pago), explícitamente para "disminuir la carga operativa", sin expandirse a mediaciones/contestaciones de demanda/otras áreas todavía. Federico insistió en no "caer en la macro" para no perder tiempo del discovery. Juan Pablo Norverto encuadró la prioridad como el "puntapié inicial" que debe poder enganchar con otras áreas después. `[source/meetings/2026-09-03-ryd-abogados-discovery.md]`
- (observation) Federico preguntó por restricciones legales de tratamiento de datos. Juan Pablo Norverto respondió que aplica la ley de protección de datos, pero que en la práctica "nadie cumple" en Argentina, y señaló el riesgo real vigente: uso informal de ChatGPT/Claude por el estudio sin política de qué se comparte con los modelos. **No se definió ninguna política ni requisito técnico concreto**; quedó como tema a tener en cuenta, no resuelto. `[source/meetings/2026-09-03-ryd-abogados-discovery.md]`

**Assumption**
- (assumption, equipo Quarks) Se asume que Provincia ART es representativo del patrón de "pedido de pago" que aplica a los otros 9 clientes del estudio (no confirmado en esta llamada; solo se relevó el caso Provincia ART en detalle).

## Contradicciones / tensiones
Ninguna; es la primera ingesta de este cliente/proceso, no hay evidencia previa con la que contrastar.

## Rutas de promoción (no aplica todavía)
Ningún ítem cruza la barra de promoción a `knowledge/` en esta ingesta (una sola fuente, primera reunión). Todo queda en `ingestion/` como working memory hasta una segunda señal (ej. propuesta técnica, siguiente call, o kickoff formal).

## Open questions (para próxima reunión / propuesta)
- ¿Cuál es el volumen mensual real de pedidos de pago (para dimensionar el ROI de automatizar)?
- ¿Provincia ART expone alguna API o solo hay portal web (automatización = RPA/scraping vs. integración)?
- ¿Los otros 9 clientes de RyD tienen el mismo patrón de pedido de pago o es específico de Provincia ART?
- ¿Qué feedback dio Lucía Guyet de su paso previo por el estudio (mencionado por Hernán, no explorado en la llamada)?
- Sin definir: alcance formal de la propuesta, presupuesto, timeline; quedó en "Juan Pablo Norverto y equipo Quarks se juntan a analizar y armar propuesta."

## Next steps mencionados en la llamada
- RyD comparte el instructivo PDF de Provincia ART (ya en manos de Juan Pablo Norverto vía mail, adjunto parcialmente transcripto arriba).
- Quarks (Juan Pablo Norverto) arma propuesta interna sobre por dónde atacar y cómo encararlo, antes de la siguiente reunión.
