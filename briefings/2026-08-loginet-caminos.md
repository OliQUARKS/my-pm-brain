# Loginet — Fase 0: análisis de caminos (interno, nunca cara al cliente)

> Deriva de [`briefings/2026-08-loginet-build-context.md`](./2026-08-loginet-build-context.md). Checkpoint pendiente — este documento presenta 3 caminos rankeados para que el equipo elija antes de expandir la Fase 1 (documento de propuesta cara al cliente).

## Perfil que calibra los 3 caminos

- **Experiencia previa:** parcialmente "soldado herido" (mala experiencia de soporte con el bot Extract a medida) + greenfield en desarrollo de software integral. → favorece un camino que **muestre resultado rápido y tangible** antes de pedir confianza para algo más grande.
- **Horizonte de tiempo/urgencia:** 3 meses mínimo, marco de "quick win", propuesta de junio ya lleva ~2 meses sin cerrar — el cliente quiere ver algo concreto pronto, no un roadmap largo.
- **Postura oficial del cliente (abril 2026):** "no es una opción considerar un cambio de sistema" (reemplazar Kai) — aunque Anahí Cappi personalmente lo preferiría. Esto **downgradea** cualquier camino que implique tocar o reemplazar Kai de fondo.
- **Riesgo no resuelto:** colaboración de Pablo (encargado de Kai) — cualquier camino que dependa de datos/cambios en Kai hereda este riesgo.

---

## Camino A — Mínimo: capa de validación documental (sin integración de naviera)

### 1. Flujo paso a paso — hoy vs. camino A

| Paso | Hoy | Con camino A | Quién lo hace |
| --- | --- | --- | --- |
| Recepción de declaración | Llega por email (Excel/PDF) del despachante/cliente | Igual | Cliente/despachante (sin cambio) |
| Lectura de la declaración | Un operador la lee y transcribe a mano | El sistema extrae y normaliza automáticamente a un esquema único | Sistema (nuevo) |
| Validación contra reglas de negocio | **No existe hoy** — se descubre el error cuando ya se cargó mal | El sistema valida (temperatura, peso, campos obligatorios) y marca errores antes de enviar | Sistema (nuevo) |
| Revisión humana | No hay paso de revisión separado — se carga directo | Un operador revisa la salida ya validada antes de aprobarla | Operador (cambia: revisa en vez de transcribe) |
| Carga en el portal de la naviera | El operador copia y pega a mano en la web de la naviera | **Igual — sigue siendo manual**, pero copiando datos ya limpios en vez de leyendo el Excel original | Operador (sin cambio en el acto en sí) |
| Corrección de errores post-BL | Se descubre al recibir el BL, corrección tardía y con costo | Se reduce drásticamente porque el error se atrapó antes de enviar | — |

### 2. Chequeo papel-a-pantalla

**Parcialmente pasa el chequeo.** El paso de carga en el portal de la naviera **sigue siendo 100% manual** — no se reduce el tiempo de tipeo. Pero la extracción+normalización+validación **no existe hoy en ninguna forma** (ni manual): hoy nadie chequea reglas de negocio antes de cargar. Este camino no es "cambiarle el soporte a algo que ya se hacía" — es agregar una capa de control que hoy no existe. El ahorro real es en **reducción de errores costosos**, no en tiempo de digitación.

### 3. Premisas y su colapso

- **Premisa 1:** las declaraciones llegan en un formato razonablemente consistente (Excel/PDF con campos identificables), aunque varíen entre despachantes. *Si falla:* la extracción requiere reglas ad-hoc por formato, sube el costo de mantenimiento — pero no colapsa el camino, solo lo encarece.
- **Premisa 2:** las reglas de negocio (rangos de temperatura, campos obligatorios por tipo de carga) se pueden formalizar sin más discovery del que ya existe. *Si falla:* hace falta una ronda de discovery adicional antes de poder validar — retrasa el arranque, no invalida el enfoque.
- **Premisa 3 (la más fuerte):** el operador humano sigue haciendo la carga final en el portal de la naviera. *Esto no es una premisa que pueda fallar — es una limitación aceptada del camino, no un riesgo.*

### 4. Ventajas y desventajas sin maquillar

- **Ventaja:** no depende de Pablo ni de Kai en absoluto — cero riesgo del bloqueador identificado. No depende de conseguir acceso a ninguna API de naviera. Rápido de construir y de mostrar.
- **Ventaja:** ataca directamente el dolor de mayor severidad cuantificada (~USD 3-4k/mes en errores) sin tocar nada del ecosistema Kai/Extract.
- **Desventaja — sin maquillar:** no reduce el trabajo manual de carga en el portal de la naviera — solo reduce el error en lo que se carga. El cliente puede percibirlo como "menos transformador" de lo que espera si llega esperando automatización de punta a punta.
- **Desventaja:** no toca la fricción comercial-administración por cotización no cargada (pain #4 del build-context) ni la falla de Extract en la conciliación de facturas (pain #2) — dos de los cuatro dolores relevados quedan intactos.

### 5. Qué cambia vs. qué queda igual

**Cambia:** existe por primera vez una validación automática antes de enviar la shipping instruction. **Queda igual:** el acto de cargar en el portal de la naviera sigue siendo manual; Extract y Kai no se tocan; la fricción comercial-administración sigue intacta.

### 6. Valor marginal

Ataca el dolor #1 (el único cuantificado en dinero, ~USD 3-4k/mes) con el menor riesgo y el menor tiempo. No ataca #2, #3 ni #4. Valor alto por unidad de esfuerzo, pero acotado en alcance.

### 7. Riesgos/dudas a validar

- ¿Qué tan consistente es el formato de la declaración entre los distintos despachantes con los que trabaja Loginet? (afecta directamente el costo de mantenimiento de la extracción)
- ¿Las reglas de negocio (temperatura, pesos, campos obligatorios) están ya escritas en algún lado, o hay que relevarlas de cero con Vanina Focaraccio/Manuel Vasquez?

### 8. Conclusión

**Sirve como punto de entrada de bajo riesgo** — ideal si el objetivo primario es un quick win visible en semanas, sin depender de nadie del lado cliente (ni Pablo, ni una API de naviera). No sirve como única propuesta si el cliente espera ver "se acabó la carga manual" — hay que ser explícitos en que ese paso queda igual en este camino.

---

## Camino B — Intermedio: capa de validación + integración Maersk + DB propia (= alcance ya redactado en la propuesta de junio 2026)

### 1. Flujo paso a paso — hoy vs. camino B

| Paso | Hoy | Con camino B | Quién lo hace |
| --- | --- | --- | --- |
| Recepción y validación de declaración | Igual que hoy, sin control | Igual que Camino A (extracción + normalización + validación) | Sistema (nuevo) |
| Revisión humana | No existe como paso separado | Dashboard de aprobación humana obligatoria antes de enviar | Operador (cambia) |
| Envío de shipping instruction — **solo Maersk** | Copiar y pegar a mano en el portal de Maersk | **Automático vía API de Maersk** — sin intervención manual | Sistema (nuevo, reemplaza el acto manual) |
| Envío de shipping instruction — **resto de navieras (~8-9)** | Manual | **Sigue siendo manual** — fuera de alcance de este camino | Operador (sin cambio) |
| Recepción y chequeo del Draft BL | Chequeo manual visual contra la declaración | El sistema valida el Draft BL devuelto contra lo enviado y actualiza la base de datos propia | Sistema (nuevo) |
| Registro de la operación | Fragmentado entre Kai, Excel maestro y mails | Base de datos propia normalizada, con trazabilidad y auditoría | Sistema (nuevo) |

### 2. Chequeo papel-a-pantalla

**Pasa el chequeo para Maersk específicamente** — ahí sí se elimina el acto manual de carga (API reemplaza tipeo). **No pasa para el resto de las navieras** — ahí sigue siendo exactamente el mismo trabajo que hoy. Este camino no exagera: solo una porción del volumen total (Maersk, una de las 2-3 navieras principales) se automatiza de punta a punta.

### 3. Premisas y su colapso

- **Premisa 1 (heredada de Camino A):** formato razonablemente consistente de declaraciones. Mismo colapso que en A.
- **Premisa 2:** la API de Maersk permite enviar la Shipping Instruction con los campos que hoy se cargan manualmente, sin bloqueos de autenticación/permisos del lado de Maersk. **Sin confirmar en el build-context** — es la premisa más fuerte de este camino. *Si falla:* el camino se degrada al alcance de Camino A solo para Maersk (validación sin envío automático), perdiendo buena parte de su valor diferencial.
- **Premisa 3:** el Draft BL que devuelve Maersk viene en un formato parseable (no solo PDF escaneado). *Si falla:* la validación automática del Draft BL requiere OCR adicional, sube costo y baja confiabilidad.

### 4. Ventajas y desventajas sin maquillar

- **Ventaja:** es el alcance que **ya está redactado y presupuestado** en la propuesta de junio 2026 — no hay que reinventar el scoping, solo confirmar que sigue vigente.
- **Ventaja:** arranca la base de datos propia — primer paso real hacia la propiedad de datos (pain #3), sin tocar Kai.
- **Desventaja — sin maquillar:** para ~8-9 de las ~10 navieras con las que trabaja Loginet, el proceso de carga sigue siendo 100% manual — el cliente puede tener la expectativa de que "ya no se carga nada a mano" y eso sería falso.
- **Desventaja:** no toca la fricción comercial-administración (pain #4) ni las fallas de Extract en la conciliación de facturas de compra (pain #2, el "Rock").
- **Riesgo de tiempo:** el propio Juan Pablo Norverto (CTO) cuestionó en la llamada interna del 27/5 si 3 meses alcanzan — la propuesta de junio estima 14 semanas (~3,5 meses), ya más que el "mínimo 3 meses" mencionado como marco de venta.

### 5. Qué cambia vs. qué queda igual

**Cambia:** Maersk queda 100% automatizado de punta a punta; existe por primera vez una base de datos propia con trazabilidad. **Queda igual:** el resto de las navieras se sigue cargando a mano; Kai y Extract no se tocan; la fricción comercial-administración por cotización sigue intacta.

### 6. Valor marginal frente a Camino A

Agrega automatización real (no solo validación) pero **solo sobre una porción del volumen total** (la naviera de mayor peso, no todas). El esfuerzo adicional (integración API + DB propia vs. solo validación) es proporcional al valor si Maersk efectivamente concentra buena parte del volumen — **dato pendiente de confirmar exactamente qué % del volumen mensual pasa por Maersk específicamente** (el build-context solo dice que Maersk y "Japac"/Hapag son las 2-3 navieras principales, sin desglose).

### 7. Riesgos/dudas a validar

- ¿Qué porcentaje del volumen mensual de shipping instructions pasa específicamente por Maersk? (determina si el esfuerzo de la integración se justifica)
- ¿La API de Maersk permite el envío completo de la Shipping Instruction con los campos que hoy se cargan a mano, o solo un subconjunto?
- ¿El Draft BL de Maersk llega en un formato parseable, o hay que planificar para PDF/imagen?

### 8. Conclusión

**Es el camino de negociación central** — ya tiene scoping y presupuesto borrador (propuesta de junio), ataca el dolor más caro con automatización real (no solo validación) para la naviera de mayor peso, y no depende de Pablo ni de Kai. Conviene **si** se confirma que Maersk concentra un % relevante del volumen — si no, el esfuerzo de la integración API puede no justificarse frente a extender Camino A a más navieras vía validación solamente.

---

## Camino C — De máxima: backoffice propio con fricción comercial-administrativa resuelta

### 1. Flujo paso a paso — hoy vs. camino C

| Paso | Hoy | Con camino C | Quién lo hace |
| --- | --- | --- | --- |
| Todo lo de Camino B | — | Incluido | — |
| Cotización comercial | Manual en Excel, no siempre se carga a tiempo en Kai | Se carga en un front propio (reemplaza el módulo comercial de Kai para este paso), dispara recordatorio automático si falta | Comercial (cambia la herramienta, no necesariamente el esfuerzo) |
| Conciliación de facturas de compra ("Rock") | Manual, Extract falla >50% | Motor de validación propio compara factura vs. cotización antes de generar el Rock | Sistema (nuevo, reemplaza parte del trabajo de Manuel Vasquez) |
| Tracking de contenedores (Cargoes) | Excel actualizado cada 6hs, no integrado a Kai | Integrado a la base de datos propia, alertas automáticas de demora | Sistema (nuevo) |
| Visibilidad para admin/facturación | Tiene que entrar a Kai | Dashboards propios sin depender de entrar a Kai | — |

### 2. Chequeo papel-a-pantalla

**Riesgo real de fallar el chequeo en el paso de cotización.** Un recordatorio automático **no automatiza la carga de la cotización** — solo le avisa al mismo humano que la tiene que cargar, antes. Si el "front propio" para comercial no reemplaza genuinamente el paso de tipeo (por ejemplo, si solo envía una notificación pero el comercial igual escribe todo a mano en el mismo lugar que antes), este componente específico **no pasa el chequeo** — es la misma carga manual con un empujón. Para que sí pase el chequeo, el front propio tendría que capturar la cotización con menos fricción que hoy (ej. prellenado desde el WhatsApp del cliente, plantillas por ruta habitual) — **no está confirmado en el build-context que esto sea parte del alcance**, es una extensión no validada.

### 3. Premisas y su colapso

- **Premisa 1 y 2 (heredadas de B):** mismo colapso.
- **Premisa 3 — la más crítica del camino:** requiere colaboración de Pablo para cualquier dato/reporte de Kai que el backoffice necesite leer o escribir (aunque sea solo lectura para no duplicar). *Si falla (Pablo no colabora):* el camino se degrada severamente — quedaría un backoffice paralelo que no puede sincronizar con Kai, duplicando el trabajo en vez de reemplazarlo. Este es el riesgo más alto de los tres caminos.
- **Premisa 4:** el cliente acepta invertir en un alcance que su propia postura oficial de abril descartó ("no es opción considerar un cambio de sistema ahora"). *Si falla:* el camino no se vende, independientemente de su mérito técnico.

### 4. Ventajas y desventajas sin maquillar

- **Ventaja:** es el único camino que ataca los 4 dolores del build-context, incluyendo la fricción comercial-administración (pain #4), que ni A ni B tocan.
- **Ventaja:** siienta las bases reales para eventualmente prescindir de Kai, si el cliente lo decide más adelante — alineado con lo que Anahí Cappi personalmente prefiere.
- **Desventaja — sin maquillar:** contradice la postura oficial del cliente de abril 2026. Venderlo como el camino principal sería ignorar una señal directa del cliente.
- **Desventaja — sin maquillar:** requiere más de 3 meses con alta probabilidad — ya el propio CTO de Quarks dudó de que 3 meses alcancen para el alcance de Camino B, que es más chico que este.
- **Desventaja:** depende de la colaboración de Pablo, el único riesgo identificado explícitamente como no resuelto por el propio dueño del cliente (Facundo).

### 5. Qué cambia vs. qué queda igual

**Cambia:** en teoría, los 4 dolores relevados. **Queda igual (riesgo):** si Pablo no colabora, o si el front de cotización no reduce genuinamente la fricción de carga, buena parte de la promesa de este camino no se materializa en la práctica.

### 6. Valor marginal frente a Camino B

Alto **en el papel** (ataca fricción #4, que hoy es descripta como "altísima" por el propio dueño) pero **el valor real depende enteramente de premisas no confirmadas** (colaboración de Pablo, y que el front de cotización efectivamente reduzca el esfuerzo y no solo lo recuerde). No es un camino "más de lo mismo pero mejor" — es una apuesta a que esas dos premisas se resuelvan a favor.

### 7. Riesgos/dudas a validar

- ¿Pablo va a colaborar con integraciones/acceso a Kai, sí o no? Esta pregunta condiciona la viabilidad completa del camino y debería resolverse **antes** de proponerlo, no durante la ejecución.
- Si se construye un front propio de cotización, ¿qué reduce realmente el esfuerzo del comercial (plantillas, prellenado desde WhatsApp) más allá de un recordatorio? Sin esto, el componente de cotización no pasa el chequeo papel-a-pantalla.
- ¿El cliente está dispuesto a extender el marco de "3 meses, quick win" a un alcance que objetivamente requiere más tiempo?

### 8. Conclusión

**No conviene como primera propuesta.** Ataca el dolor más profundo (la fricción comercial-administración) pero sobre premisas no validadas (colaboración de Pablo, reducción real de esfuerzo en cotización) y contra una postura oficial del cliente que ya lo descartó en abril. Serviría **como fase 2**, una vez que Camino A o B ya generaron confianza y se resolvió explícitamente si Pablo colabora — no como apuesta inicial con un cliente que pidió "no tocar Kai" y quiere ver resultados en 3 meses.

---

## Tabla de síntesis comparativa

| | Camino A — Mínimo | Camino B — Intermedio | Camino C — De máxima |
| --- | --- | --- | --- |
| Esfuerzo relativo | Bajo | Medio (ya scopeado en propuesta de junio, ~14 sem) | Alto, mayor a 3-4 meses |
| Riesgo técnico | Bajo | Medio (depende de API Maersk + formato Draft BL) | Alto (depende de Kai + front de cotización real) |
| Riesgo de adopción | Bajo | Bajo-medio | Alto (contradice postura oficial de abril) |
| ¿Ataca causa raíz o síntoma? | Síntoma del dolor #1 (reduce error, no automatiza carga) | Causa raíz de #1 para Maersk; síntoma para el resto | Causa raíz de #1, #2 y #4 — si las premisas se cumplen |
| Depende de premisas sin validar | Baja dependencia | Media (% volumen Maersk, API real, formato BL) | Alta (colaboración de Pablo, reducción real de esfuerzo en cotización) |
| Mejor encaje según perfil de cliente | Cliente cauteloso, quiere ver resultado ya, sin fricción con Pablo | Cliente que ya tiene la propuesta de junio semi-aceptada — es continuidad, no un pivot | Cliente dispuesto a invertir más tiempo/riesgo — **no es el perfil actual de Loginet según lo relevado** |

## Ranking recomendado

1. **Camino B (Intermedio)** — es la continuidad natural de lo ya presentado en junio, ataca el dolor más caro con automatización real para la naviera principal, y no requiere renegociar el marco de tiempo que el cliente ya tiene en la cabeza. **Recomendado como propuesta principal**, condicionado a confirmar el % de volumen que efectivamente pasa por Maersk.
2. **Camino A (Mínimo)** — buen "plan B" o complemento de arranque inmediato si el cliente quiere ver algo andando en semanas mientras se cierra el resto, o si la integración con Maersk se traba por algún motivo (permisos, tiempos de la naviera).
3. **Camino C (De máxima)** — downgradeado explícitamente. No se presenta como opción de cierre ahora; queda como conversación de "fase 2" una vez resuelta la colaboración de Pablo.

## Preguntas de validación para la próxima conversación con el cliente

1. ¿Qué porcentaje del volumen mensual de shipping instructions pasa específicamente por Maersk vs. el resto de las navieras?
2. ¿Pablo va a colaborar con integraciones/acceso a Kai, sí o no? (condiciona si Camino C es viable a futuro)
3. ¿Cuán consistente es el formato de las declaraciones entre los distintos despachantes?
4. ¿La API de Maersk permite enviar la Shipping Instruction completa, o solo un subconjunto de campos?
5. ¿El Draft BL de Maersk llega en formato parseable (no imagen escaneada)?

---

**Checkpoint:** pendiente de elección del equipo. Recomendación: Camino B como base de la Fase 1 (documento de propuesta), con la posibilidad de ofrecer Camino A como arranque acotado si el cliente prioriza ver algo funcionando ya mismo.
