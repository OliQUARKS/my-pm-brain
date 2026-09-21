# Discovery, Norton (fuerza de ventas)

**Fecha:** 2026-09-16
**Tipo:** Meeting (discovery call, cliente nuevo/prospecto)
**Fuente:** [../../source/meetings/2026-09-16-norton-discovery.md](../../source/meetings/2026-09-16-norton-discovery.md)
**Asistentes (lectura del transcript, sin diarización estructurada; ver Open questions):** Olivier Luce (Quarks, PM), Juan Pablo Norverto (Quarks, CTO/socio), Martín (Norton, área comercial/fuerza de ventas — rol exacto sin confirmar), Tomás (Norton, confirmado por el PM 2026-09-16; rol exacto sin confirmar — interviene validando el encuadre de Martín), mención suelta de "Hernán" al cierre (identidad sin confirmar, posible ruido de transcripción)

## Contexto (cliente nuevo, no PERC)

Primer discovery call con **Norton** (identificado como cliente nuevo por el título de la reunión y el cierre explícito "nuevo cliente NORTON" en la transcripción; el nombre aparece transcripto como "Horto"/"Horton" en varios pasajes de audio, léase como error de transcripción de "Norton"). Es la primera reunión con este cliente en el brain; no hay hipótesis ni decisiones previas que esta ingesta actualice. Llamada de encuadre/relevamiento inicial sobre la problemática de fuerza de ventas, con el objetivo declarado (Olivier) de identificar **Quick Wins** antes de armar una propuesta.

## Observaciones (tagged)

**La empresa y su contexto de sistemas**
- (observation) Norton comercializa a través de **3 canales**: directa, indirecta/distribución (off-trade), y supermercado/mayorista, con una sola lista de clientes segmentada por niveles. `[source/meetings/2026-09-16-norton-discovery.md]`
- (interpretation) El producto que vende la fuerza de ventas es vino, a juzgar por las referencias reiteradas a puntos de venta con/sin "vino en Norton" y a distribución de bebidas; no confirmado de forma explícita y directa en la llamada. `[source/meetings/2026-09-16-norton-discovery.md]`
- (observation) Sistema actual: **Arbalón**. La compañía está en transición a un ERP/CRM corporativo nuevo, **QAD**, del cual recién se hizo el kickoff; implementación estimada en ~1 año (hasta julio 2027). Hay módulos de CRM dentro del universo QAD, pero no se confirmó si incluyen app mobile. `[source/meetings/2026-09-16-norton-discovery.md]`
- (observation) Gran parte de la información de ventas ya está modelada en **Power BI** por el equipo de sistemas ("director de sistema muy comercial"): clientes, ventas, volúmenes, compradores/no compradores, por marca/zona. El histórico completo está disponible, aunque la comparación operativa habitual es contra plan y contra año anterior (no multi-año), salvo para cuentas estratégicas. `[source/meetings/2026-09-16-norton-discovery.md]`
- (observation) Los vendedores usan cuentas Microsoft; el login de una eventual herramienta podría apoyarse en eso. `[source/meetings/2026-09-16-norton-discovery.md]`

**El problema central (relatado por Martín)**
- (observation, Martín) La dinámica de visita a clientes no está sucediendo como él esperaba; no hay un mecanismo sistemático que priorice qué clientes visitar y cuándo (la vieja lógica de "ficha por cliente" que armaba la ruta de venta se perdió con la modernización). `[source/meetings/2026-09-16-norton-discovery.md]`
- (observation, Martín) La información para decidir existe (Power BI), pero **no hay tiempo ni "cabeza" para ejecutar el análisis**: los jefes no repasan la nómina completa de vendedores, los vendedores no analizan su propia cartera de clientes, y oportunidades chicas (ej. un cliente que dejó de comprar hace 2 meses) se pierden en el volumen. `[source/meetings/2026-09-16-norton-discovery.md]`
- (observation, Martín) Consecuencia: la venta se concentra al final del mes ("los últimos 15 días llenando lo que falta") en vez de distribuirse, y Martín mismo dedica medio día de análisis manual antes de cada reunión de ventas para poder tomar decisiones con su equipo — función que en otro equipo resuelve un área de Business Intelligence que Norton no tiene ni planea tener en el corto plazo. `[source/meetings/2026-09-16-norton-discovery.md]`
- (observation, Martín) Ejemplo concreto de este gap: un reporte de cobertura de precios que Martín armó manualmente en Excel tras visitar 50 puntos de venta en un mes, porque nadie estaba haciendo ese análisis de forma sistemática. `[source/meetings/2026-09-16-norton-discovery.md]`

**Solución conceptual esbozada en la llamada (equipo Quarks, validada por Martín/Tomás como foco inicial)**
- (interpretation, equipo Quarks) Capa básica propuesta: **sistema predictivo de agenda** — a partir del análisis de cartera por vendedor (recencia de compra, stock estimado agotado, comparación contra presupuesto), sugerir qué clientes visitar cada semana/día, con ruteo por geolocalización (ej. 5 visitas/día por zona), sugerencia de pedido y de ofertas/lanzamientos a empujar. `[source/meetings/2026-09-16-norton-discovery.md]`
- (interpretation, equipo Quarks) Segunda capa: **reporte de eficiencia** por vendedor (cumplimiento de visitas, conversión comprador/no comprador, frecuencia, surtido, calidad, margen) que reemplace el análisis manual que hoy hace Martín, para que un jefe de área pueda sentarse con cada vendedor con el diagnóstico ya armado. `[source/meetings/2026-09-16-norton-discovery.md]`
- (observation, Martín, confirmado por Tomás) El foco inicial declarado es **gestión/control de gestión del vendedor, productividad del vendedor y seguimiento de adición de nuevos clientes** — no fotos, no inteligencia competitiva en el punto de venta, no captura de oportunidades geolocalizadas. Esas quedan explícitamente como "otra capa" a futuro, no como alcance inicial. `[source/meetings/2026-09-16-norton-discovery.md]`

**Ideas adicionales mencionadas (fuera del foco inicial, capas futuras)**
- (interpretation, Juan Pablo Norverto) Captura de oportunidades de distribución: registrar puntos de venta detectados sin presencia de la marca (ej. un almacén que vende vino pero no el de Norton) y asignarlos a seguimiento — al vendedor de zona si es canal directo, o quedar pendiente si es indirecto. `[source/meetings/2026-09-16-norton-discovery.md]`
- (observation, Martín) Para canal indirecto/distribución, Norton **no tiene conexión con la red de sus distribuidores** ni acuerdos de exclusividad por zona, así que no puede saber hoy si un distribuidor visita o no un punto de venta dado; esta pieza quedaría desconectada/manual por ahora. `[source/meetings/2026-09-16-norton-discovery.md]`
- (observation, Martín) Tareas de campo adicionales mencionadas como deseables a futuro: sacar fotos de producto/precio/posicionamiento en el punto de venta, relevar lanzamientos de competencia. `[source/meetings/2026-09-16-norton-discovery.md]`

**Intentos previos y riesgo de adopción**
- (observation, Martín) Hace ~3 meses probó un CRM en la nube para seguimiento de vendedores con otro proveedor; se abandonó porque requería carga manual constante, venía con dimensiones de trabajo preseteadas no ajustables, y faltaba alguien dedicado a analizar los datos que generaba. Su lectura: **"hoy lo que me falta son manos, no me falta sistema."** `[source/meetings/2026-09-16-norton-discovery.md]`
- (interpretation, equipo Quarks) La adopción es un riesgo transversal independiente del sistema elegido: una herramienta sin un mecanismo de "empuje" (comunicación activa vía mail/WhatsApp/etc.) hacia los usuarios no genera uso, incluso con datos e infraestructura sólidos. `[source/meetings/2026-09-16-norton-discovery.md]`
- (observation, Martín) Referencia a un proyecto grande previo (road-to-market, con consultora PCG) que generó rechazo explícito por la carga de implementación: **"me preocupa mucho menos la solución que me des que cómo la vamos a implementar."** Prioriza que su equipo pueda operar la herramienta sobre la sofisticación de la solución. `[source/meetings/2026-09-16-norton-discovery.md]`

**Encuadre de la propuesta (Quarks)**
- (observation) Quarks propone evaluar una **solución intermedia** (posiblemente reusando algo ya desarrollado para otro cliente) mientras avanza la implementación de QAD (~1 año), con la idea de ensamblar/migrar cuando QAD esté listo — condicionado a chequear con **Fede Pinto** (contacto de sistemas de Norton, no confirmado como asistente de esta llamada) qué cubre y qué no cubre el CRM de QAD, para no duplicar ni ir a contramano. `[source/meetings/2026-09-16-norton-discovery.md]`
- (interpretation, equipo Quarks) Reafirman su forma de trabajo habitual: no es solo instalar una herramienta, incluye capacitación del proceso y iteración progresiva ("le ponemos cascote... si aguanta, seguimos"). `[source/meetings/2026-09-16-norton-discovery.md]`

**Assumption**
- (assumption, equipo Quarks) Se asume que el ejemplo dado ("jefe de un área con 4 vendedores") es ilustrativo del tamaño de un equipo/zona, no el headcount total de la fuerza de ventas de Norton — no se relevó el tamaño total del equipo comercial en esta llamada.

## Contradicciones / tensiones
Ninguna; es la primera ingesta de este cliente, no hay evidencia previa con la que contrastar.

## Rutas de promoción (no aplica todavía)
Ningún ítem cruza la barra de promoción a `knowledge/` en esta ingesta (una sola fuente, primera reunión). Todo queda en `ingestion/` como working memory hasta una segunda señal (ej. siguiente call, propuesta técnica).

## Open questions (para próxima reunión / propuesta)
- **Identidad y rol exacto de Martín** en Norton — se infiere responsabilidad directa sobre la fuerza de ventas (presupuesto, KPIs, reuniones de venta), pero no hay cargo confirmado.
- **Rol exacto de Tomás** — confirmado del lado Norton (PM, 2026-09-16). Participa validando decisiones de foco/alcance junto con Martín ("Digo, Tomás, no sé qué te parece a vos"), lo que sugiere un par o superior de Martín, pero el cargo puntual sigue sin confirmar.
- **Mención de "Hernán" al cierre** — contexto insuficiente para identificarlo; podría ser un asistente real de la llamada o ruido de transcripción. No asumir vínculo con otros clientes del brain (ej. Hernán Capolupo de RyD Abogados) sin confirmación explícita.
- ¿Qué cubre exactamente el módulo CRM de QAD? Pendiente de chequear con Fede Pinto.
- Tamaño real de la fuerza de ventas de Norton (headcount total, no solo el ejemplo de "4 vendedores por zona").
- Alcance, presupuesto y timeline de una eventual propuesta — nada definido; queda en "Quarks vuelve con un plan de trabajo para iterar."

## Next steps mencionados en la llamada
- Quarks (liderado por Juan Pablo Norverto, seguiendo el mismo patrón que en RyD Abogados) arma un primer plan/propuesta de trabajo para volver a presentar y iterar con Norton.
