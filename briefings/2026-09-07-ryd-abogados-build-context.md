# Contexto de proyecto, RyD Abogados, 2026-09-07

## A. Contexto del proyecto (interno)

### 1. Problemática (ampliada)

**Antes** (encuadre inicial, previo a la llamada): "RyD quiere automatizar la carga de pedidos de pago", ask genérico de reducir carga operativa.

**Ahora** (post-discovery del 2026-09-03): el problema tiene dos cabezas, no una. Un expediente que llega a sentencia firme o acuerdo homologado no genera un solo pago sino **6-7 pedidos de pago separados** (uno por parte: actor, abogado, perito, tasa de justicia), cada uno con distinto CBU y distinta documentación requerida. El cuello de botella real es la combinación de:
1. **Pedir datos a terceros** (mail manual a abogados/peritos pidiendo CBU/DNI/factura, llega "a cuentagotas", a veces por WhatsApp, sin estructura).
2. **Cargar fragmentado** en el portal de Provincia ART, sub-pago por sub-pago.

Lo que cambió respecto al pre: no es "automatizar una carga", es **automatizar (o asistir) un proceso de recolección + seguimiento de datos dispersos entre terceros, más una carga que se ramifica**. Además, el estado "pagado" en Lex Doctor es dependiente del conjunto: un expediente queda trabado si falta un solo sub-pago, y hoy no hay vista consolidada de qué está trabado y por qué (solo agenda individual por persona). `[ingestion/meetings/2026-09-03-ryd-abogados-discovery.md]`

Scope explícitamente acotado en la llamada (decisión de Federico + Juan Pablo Norverto): **solo el área de Juan Verde (7 personas, pedidos de pago) y solo Provincia ART**. Mediaciones, contestaciones de demanda y los otros 9 clientes del estudio quedan fuera por ahora.

### 2. Contexto ampliado

- **Sistemas:** Lex Doctor 11 (Caddel S.A., 2021; arquitectura cliente/servidor, "rígido", "sin evolución", según Hernán "pronto va a desaparecer") + portal web de Provincia ART (login manual). `[ingestion/adhoc/2026-09-04-lexdoctor-manuals-ryd.md]`
- **Provincia ART, portal de proveedores:** existe un portal público dedicado a proveedores/prestadores (`proveedores.artprovincia.com.ar`, separado del sitio general de pólizas/siniestros). Es web con login/registro, con dos funciones públicas: *Facturación* (alta de facturas, seguimiento de status, info de pago) y *Cotización* (presupuestos para compulsas). La página pública no menciona API, SDK ni carga masiva. `[ingestion/adhoc/2026-09-07-provinciart-portal-recon.md]` **Gap:** la terminología ("Facturación" = alta de la propia factura del proveedor) no calza obviamente con "pedido de pago a terceros" (CBU de actor/perito/abogado) tal como lo describió RyD; no está confirmado si es la misma sección u otra distinta.
- **Restricciones técnicas:** los manuales de Lex Doctor no documentan API REST/SOAP ni acceso SQL directo; automatización nativa limitada a placeholders binarios (documento ← sistema, no al revés). `[ingestion/adhoc/2026-09-04-lexdoctor-manuals-ryd.md]`
- **Números:** ~13,000 expedientes en trámite (todo el estudio); 7 personas dedicadas a pedidos de pago; ~20 pedidos de pago agendados por persona/día; Hernán recibe ~600 mails/día; llegó una tanda de ~25 mails automáticos de confirmación de pago el 2026-09-02; 10 abogados recurrentes concentran ~50% del volumen (pero cada caso igual exige factura nueva, no reusable). `[ingestion/meetings/2026-09-03-ryd-abogados-discovery.md]`
- **Prioridades:** foco Provincia ART / área Juan Verde; explícitamente no expandir a mediaciones ni a los otros 9 clientes todavía (Federico: "no caer en la macro ahora").
- **Quién decide:** Juan Francisco Verde (área legal) + Hernán Capolupo (gestión operativa), ambos socios, ambos ya estuvieron en la reunión. No hay decisor ausente que convocar.
- **Protección de datos / uso de IA, resuelto:** [decisión 2026-09-07](../decisions/2026-09-07-ryd-prototipos-datos-genericos.md), los prototipos usan datos genéricos/sintéticos, no datos reales de expedientes. La política de IA del equipo de RyD en general queda fuera de este alcance (sigue sin definir, no bloquea el proyecto).

### 3. Usuarios / roles / permisos

- **Usuarios primarios:** las 7 personas del equipo de Juan Verde que cargan pedidos de pago. No se relevó si tienen carteras de expedientes propias o trabajan sobre un pool compartido (gap abierto).
- **Terceros proveedores de datos:** abogados de la parte actora y peritos, no son usuarios del sistema, reciben mail pidiendo CBU/DNI/factura.
- **Sin instancia de aprobación intermedia:** quien carga entra directo al portal de Provincia ART y sube todo, sin revisión previa. `[ingestion/meetings/2026-09-03-ryd-abogados-discovery.md]`
- **Niveles de acceso Lex Doctor** (Nivel 1-5, Supervisor, Reservado) existen en el sistema pero no se confirmó cómo se mapean al equipo de 7. `[ingestion/adhoc/2026-09-04-lexdoctor-manuals-ryd.md]` (gap abierto).

### 6. Stakeholders, quién es cada uno

- **Juan Francisco Verde** (socio, área legal, RyD): decisor + responsable del equipo de 7; le importa que su gente deje de perder tiempo administrativo y vuelva a trabajo legal (contestaciones de demanda, defensa). Más conciso que Hernán, confirma detalles técnicos cuando se le pregunta directo. (interpretation, ancla: [ingestion/meetings/2026-09-03-ryd-abogados-discovery.md](../ingestion/meetings/2026-09-03-ryd-abogados-discovery.md))
- **Hernán Capolupo** (socio, gestión operativa/facturación, RyD): champion de la automatización; mostró Lex Doctor en vivo; prefiere evolutivo ("que se vaya alimentando de a poco"), no big-bang. Menciona conocer un caso de un cliente del estudio (Triunfo Seguros) que ya delega credenciales a un agente que opera el portal, señal de apetito de riesgo moderado-alto en el cliente, aunque no es su propia postura confirmada. (interpretation, ancla: [stakeholders/hernan-capolupo.md](../stakeholders/hernan-capolupo.md))
- **Juan Pablo Norverto** (CTO, Quarks): lideró el relevamiento técnico; quedó a cargo de armar la propuesta interna post-discovery.
- **Federico Fernandez** (COO, Quarks): guardián de scope ("no caer en la macro"); levantó el tema de protección de datos (ahora resuelto, ver §2).
- **Lucía Guyet** (UX/UI, Quarks): ya había trabajado con este estudio antes (feedback previo mencionado por Hernán pero no explorado en la llamada, abierto); aportó las preguntas sobre visibilidad consolidada de estado por expediente.

*(Estilo de trato operativo por persona, canal preferido, qué genera fricción, queda fuera de este skill; va a `communication-context` cuando exista.)*

### 7. Contexto metodológico, cómo lo trabajaríamos

> No existe todavía `briefings/_contexto-metodologico.md` (plantilla estándar Quarks). Lo de abajo es criterio propio para este caso, no una decisión ni una plantilla formal (intuition, PM, 2026-09-07).

- **Roles y responsabilidades:** Quarks lidera discovery técnico y arma la propuesta conceptual. RyD provee acceso en vivo a Lex Doctor (ya mostrado), documentación técnica (manuales ya compartidos), y el material operativo que se releve durante el discovery pago.
- **Entornos:** sin API/SQL confirmada en Lex Doctor ni en el portal de proveedores de Provincia ART, cualquier prototipo depende de capturas/grabaciones controladas o de un ambiente de prueba (a definir con RyD si existe sandbox o si todo debe mockearse). Datos: siempre genéricos/sintéticos ([decisión 2026-09-07](../decisions/2026-09-07-ryd-prototipos-datos-genericos.md)).
- **Comunicación:** hasta ahora por mail (instructivo PDF ya compartido con Juan Pablo Norverto); no hay canal de mensajería instantánea confirmado con RyD todavía.
- **Reviews / documentación:** próximo checkpoint natural es la reunión de presentación de la propuesta de discovery.
- **SLA:** no definido, corresponde a la propuesta real, post-"sí".
- **Qué hay que definir sí o sí:**
  - Si el prototipo puede tocar el portal real de Provincia ART o debe mockearse (responsable: Juan Pablo Norverto; riesgo: sin definir esto, la factibilidad del prototipo (§B.4) queda ambigua).
  - Dueño de la validación del flujo del lado de RyD (¿Juan Verde, Hernán, o alguien del equipo de 7?) (responsable: RyD; riesgo: sin un validador único, el circuito relevado puede quedar sin confirmar).
  - (Política de datos/IA para los prototipos: resuelta, ver §2.)

## B. Pre-propuesta (cara al cliente, liviana)

### 4. Propuesta

- **Alcance:**
  - **Sí:** mapear y asistir/automatizar el circuito de pedido de pago para Provincia ART (área de Juan Verde), atacando los dos cuellos de botella reales: pedido de datos a terceros y carga fragmentada por sub-pago; visibilidad consolidada de qué expedientes están trabados y por qué.
  - **No (por ahora):** mediaciones, contestaciones de demanda, los otros 9 clientes del estudio, integración directa con Lex Doctor/Provincia ART si no se confirma una vía programática.
- **Discovery:** 2-3 semanas. Objetivo: confirmar si Lex Doctor u Provincia ART exponen alguna vía programática (API/SQL/portal scriptable) o si todo es RPA a nivel UI; validar con ejemplos reales (sentencia vs. acuerdo) si el circuito varía; relevar el material operativo (instructivo completo, ejemplos reales, captura del portal, volumen mensual, patrón en otros clientes, ver [decisión 2026-09-07](../decisions/2026-09-07-ryd-minuta-sin-pedido-material.md)).
- **Prototipo si es factible:** no una pantalla, un **flujo**, con datos genéricos ([decisión 2026-09-07](../decisions/2026-09-07-ryd-prototipos-datos-genericos.md)). Mapear qué dato se pide una sola vez, dónde se bifurca por tipo de pago (capital/honorarios/tasa de justicia), y dónde un asistente puede automatizar el tramo de pedido y seguimiento de datos a terceros (el cuello de botella más claro), independientemente de si la carga en el portal termina siendo manual, asistida o vía RPA.
- **Cómo lo trabajaríamos:** ver §7, RyD provee acceso y material durante el discovery, Quarks lidera el relevamiento técnico, próximo paso es la reunión de propuesta de discovery ya anunciada en la minuta.
- **¿Podemos ayudar o no?** Factibilidad **media**: tenemos experiencia en automatización de procesos operativos, pero **no hay confirmación de que Lex Doctor o el portal de proveedores de Provincia ART expongan ninguna vía programática** (los manuales de Lex Doctor no documentan API ni acceso SQL; la página pública del portal de proveedores tampoco). Si no la hay, la vía realista es RPA a nivel UI (frágil ante cambios de interfaz) o un asistente que automatiza solo el tramo de recolección/seguimiento de datos de terceros, dejando la carga en el portal semi-manual pero asistida. Esto se dice explícito, no se promete integración que no sabemos si existe.

## C. Salida operativa

### 5. Minuta y próximos pasos

La minuta cara-al-cliente ya existe, revisada: [briefings/2026-09-03-ryd-abogados-minuta.md](./2026-09-03-ryd-abogados-minuta.md). Por [decisión 2026-09-07](../decisions/2026-09-07-ryd-minuta-sin-pedido-material.md), **no** pide el material operativo (los 6 ítems); eso pasa a ser alcance del discovery pago. El mail ahora solo valida el flujo y anuncia que Quarks va a traer una propuesta de discovery.

**Abiertos:**
- Confirmar si la minuta (versión revisada) ya se envió; ya pasaron 4 días desde la reunión (2026-09-03 → 2026-09-07).
- Alcance y precio concretos del discovery pago, todavía no armados.
- Si Lex Doctor tiene API/SQL no documentada (dev-only, soporte de Caddel S.A.).
- Si el pedido de pago a terceros se carga en la sección "Facturación" del Portal de Proveedores de Provincia ART o en otra sección/sistema.
- Feedback previo de Lucía Guyet sobre su paso anterior por el estudio (mencionado por Hernán, no explorado).

**Acciones:**
- Enviar la minuta revisada ya (ventana de 1-2 días ya vencida).
- Armar el alcance + precio del discovery pago como parte de la propuesta cara-al-cliente (`/propuestador`).

---

**Historial de revisión:** versión inicial 2026-09-07 (post-discovery 2026-09-03 + manuales Lex Doctor 2026-09-04); actualizada el mismo día con reconocimiento del portal de proveedores de Provincia ART y con las decisiones de datos genéricos + minuta sin pedido de material.
