# Contexto de proyecto — Loginet — 2026-08-19

> **Documento interno.** Nunca se entrega al cliente. La pre-propuesta cara-al-cliente (§ B) es lo único derivable de acá para mostrar afuera.

**Cliente:** Loginet (LoginetSA) — freight forwarder, Argentina (60-70%) y Chile (30-40%), especializado en perecederos y productos congelados (principalmente fruta).
**Tamaño:** ~12 personas.
**Contactos:** Facundo Ramirez (dueño), Maggie (socia — sin reunión con Quarks aún), Anahí Cappi (Quality Control Manager), Manuel Vasquez (administración), Vanina Focaraccio (operativo). Ver § 6.
**Historial con Quarks:** reunión de briefing 2026-02-24, segundo mapeo/discovery 2026-04-06, scoping interno Quarks 2026-05-27, propuesta comercial redactada jun-2026 (**sigue sin cerrar** al 2026-08-19), llamada de repaso Olivier↔Jony 2026-08-19 (input directo de este documento).
**Fuentes:** [`ingestion/meetings/2026-02-24-loginet-briefing-quarks.md`](../ingestion/meetings/2026-02-24-loginet-briefing-quarks.md), [`ingestion/meetings/2026-04-06-loginet-2do-mapeo.md`](../ingestion/meetings/2026-04-06-loginet-2do-mapeo.md), [`ingestion/meetings/2026-05-27-loginet-scoping-interno-jony-jp.md`](../ingestion/meetings/2026-05-27-loginet-scoping-interno-jony-jp.md), [`source/adhoc/2026-06-loginet-propuesta-mvp-texto.md`](../source/adhoc/2026-06-loginet-propuesta-mvp-texto.md), [`source/adhoc/2026-08-19-loginet-flujo-proceso-transcripcion.md`](../source/adhoc/2026-08-19-loginet-flujo-proceso-transcripcion.md), [`source/meetings/2026-08-19-loginet-propuestador-call-olivier-jony.md`](../source/meetings/2026-08-19-loginet-propuestador-call-olivier-jony.md).

---

# A. Contexto del proyecto (interno)

## 1. Problemática (ampliada)

**Qué entendíamos antes.** El único documento previo ([`briefings/2026-08-loginet-briefing-context.md`](./2026-08-loginet-briefing-context.md)) era 100% especulativo — se armó con nombre de cliente + URL pública, sin ningún contacto real. Especulaba sobre digitalización aduanera estatal (VUCEA, OEA, Declaración Aduanera Digital) como posible eje regulatorio del caso.

**Qué sabemos ahora — y qué cambió.** Esa hipótesis regulatoria **se descarta**: en ninguna de las tres reuniones reales (24/2, 6/4, 27/5) ni en la llamada de hoy aparece mención alguna a VUCEA, OEA, ni a ningún organismo estatal como driver del proyecto. El problema real es **100% interno y operativo**, no regulatorio:

1. **Ingreso manual de declaraciones** — Excel/PDF/email de despachantes/clientes se carga a mano en los portales de cada naviera. Alto riesgo de error (temperatura, peso, contenedor, sellos), con costo directo cuantificado: **~USD 3.000-4.000 en multas solo en marzo 2026** (temporada alta), según cálculo de Anahí Cappi.
2. **Bot "Extract" con fallas recurrentes** — dependencia de un proveedor externo que falla en más del 50% de las cargas a Kai, sobre un universo de ~8-10 navieras (bastante determinístico, no aleatorio).
3. **Falta de control/propiedad de datos** — la información real de la operación vive fragmentada entre Kai (ERP-TMS legacy sin API), un "Excel maestro" (la hoja viva real, porque Kai nunca está actualizado a tiempo), Cargoes/Carghost (tracking, actualiza cada 6hs vía Excel, no integrado), y WhatsApp (canal real de cotización con el cliente).
4. **Fricción alta entre operaciones y administración** — la cotización no cargada a tiempo en Kai bloquea la facturación; ambas áreas se echan culpas (descripto por Facundo como "altísima": peleas, retrasos).

## 2. Contexto ampliado

**Sistemas actuales:**
- **Kai / K / CAI** — ERP-TMS legacy. Sin API. Cubre facturación, administración, comercial. Limitación confirmada: no permite descargar reportes que separen costos por proveedor dentro de una misma operación.
- **Extract** — bot que lee facturas/BL en PDF y carga a Kai. Falla >50% de las veces. La carga automática requiere coincidencia exacta entre el monto de la factura y un ítem interno llamado **"Rock"** (prefactura que administración genera a mano); si no coincide exactamente (contenedor + importe), Kai rechaza la carga.
- **Cargoes / Carghost** — tracking de contenedores en tránsito, reportes cada 6hs. No integrado a Kai (discrepancia de nomenclatura de puertos entre sistemas).
- **INTRA** — única integración semi-automatizada existente, y solo para un subconjunto chico de navieras.
- **Excel maestro** — la fuente de verdad real del día a día (cortes documentales/físicos, contratos por temporada en una solapa dedicada).

**Números clave:**
- ~3.500-4.000 Bill of Ladings/año.
- Temporada alta: marzo-septiembre, hasta ~400 contenedores/semana.
- ~500-600 facturas de navieras a conciliar por mes en temporada alta ("Rocks": ~50 generados en 20 min de trabajo manual — el cuello de botella es el volumen total, no la velocidad unitaria).
- ~10 navieras en total, 2-3 concentran la mayoría del volumen (Maersk y "Japac"/Hapag mencionadas explícitamente, ambas con API).
- ~20 destinos principales.
- ~USD 3.000-4.000/mes en costos extra por errores (dato de un solo mes de temporada alta — **watch item, N=1 mes, no proyectar linealmente sin más data**).

**Decisores y urgencia:**
- Decisión de compra recae en **Facundo Ramirez** (dueño) y **Maggie** (socia, sin contacto aún con Quarks). Anahí Cappi es la championa técnica/funcional interna, pero no es la decisora final de presupuesto.
- La propuesta de junio 2026 llevaba ~2 meses sin cerrar al 19/8/2026; el objetivo declarado (en la llamada de hoy) era cerrar y avanzar para fin de agosto 2026.
- Plazo de ejecución deseado: **3 meses mínimo** (potencialmente 4), enmarcado como "quick win" antes de una transformación mayor.

**Experiencia previa (perfil del cliente):** primera vez que encaran un desarrollo de software a medida. Tuvieron un bot a medida (Extract) con muy mala experiencia de soporte — cambios simples tardaron meses. Archetype: **parcialmente "soldado herido"** respecto a proveedores de automatización puntual, pero **greenfield** respecto a desarrollo de software integral. Esto es una ventaja de venta explícita para Quarks (ya lo identificó Jony): el cliente entiende que "no es lo mismo con nosotros".

**Usuarios:** confirmado explícitamente hoy — **100% interno, sin usuarios externos** (los clientes de Loginet no tendrían acceso a ningún sistema propio).

**Depósito fiscal / despachante:** depósito fiscal tercerizado; no tienen despachante de aduana propio, trabajan con varios según la operación.

## 3. Usuarios / roles / permisos (confirmado)

- **Comercial** — recibe pedidos por WhatsApp, cotiza de memoria (rutas/navieras), no siempre carga la cotización en Kai a tiempo (causa raíz de la fricción con administración).
- **Operativo** — arma el booking, gestiona la shipping instruction y el chequeo contra el BL, sostiene el Excel diario. Fricción alta con Kai por falta de tiempo de carga.
- **Administrativo/facturación** — factura tras la salida del buque (ventana de 48hs), concilia facturas de compra de navieras vía "Rock". Depende 100% de que Kai tenga la cotización y el BL bien cargados.
- **Sin usuarios externos** (clientes de Loginet) — descartado explícitamente.

## 6. Stakeholders — quién es cada uno

- **[Facundo Ramirez](../stakeholders/facundo-ramirez.md)** — dueño, decisor de negocio, contacto histórico de Jony ("amigote"). Le importa el ROI y la confianza operativa antes que el detalle técnico. **(interpretación, anclada en `source/meetings/2026-08-19-loginet-propuestador-call-olivier-jony.md`)**
- **[Maggie](../stakeholders/maggie-loginet.md)** — socia, co-decisora, **sin ninguna interacción registrada con Quarks todavía**. Riesgo real: la propuesta se construyó leyendo solo a Facundo.
- **[Anahí Cappi](../stakeholders/anahi-cappi.md)** — Quality Control Manager, championa interna del cambio. Viene de una empresa que construyó su propio sistema en 6 años y hoy es referente regional — favorece personalmente reemplazar Kai, aunque el mensaje "oficial" del cliente en abril fue no tocarlo todavía. Aporta los números (ROI, volumen de facturas).
- **[Manuel Vasquez](../stakeholders/manuel-vasquez.md)** — administración, dueño operativo del proceso de conciliación ("Rock"). Fuente de conocimiento de proceso, no decisor.
- **[Vanina Focaraccio](../stakeholders/vanina-focaraccio.md)** — operativo/procesos, la que mejor conoce el flujo documental completo. Propuso usar históricos de tránsito propios para mejorar estimaciones de ruta — señal de que piensa en aprovechar datos, no solo tapar el dolor inmediato.
- **[Pablo](../stakeholders/pablo-loginet.md)** — encargado del sistema Kai. **Riesgo organizacional identificado por el propio Facundo**: reacio a colaborar en integraciones. No participó de ninguna reunión relevada. Cualquier alcance que dependa de cambios/acceso a Kai debe asumir este riesgo como no resuelto.

## 7. Contexto metodológico — cómo lo trabajaríamos

Usando como base [`briefings/_contexto-metodologico.md`](./_contexto-metodologico.md):

- **Grado de gestión: total.** Loginet no tiene equipo de desarrollo propio — Kai es un sistema de terceros administrado internamente solo por Pablo (rol no técnico de desarrollo, sino de administración funcional del ERP). Quarks asumiría el ciclo completo (repos, CI, ambientes, pruebas).
- **Dependencia crítica #1 — colaboración de Pablo.** Cualquier automatización que dependa de datos, reportes o cambios en Kai requiere su colaboración. **Responsable:** Loginet (gestionar internamente). **Riesgo si no se resuelve:** cualquier alcance que toque Kai puede bloquearse silenciosamente — igual que el aprendizaje de PERC documentado en la plantilla ("definir esto al inicio, no sobre la marcha").
- **Dependencia crítica #2 — acceso a APIs de navieras.** Maersk confirmada con API; falta confirmar el resto (Hapag/"Japac" mencionada, sin confirmar). **Responsable:** Quarks gestiona el alta, pero depende de que la naviera la otorgue en tiempo razonable.
- **Modelo de comunicación:** a definir en kickoff — hasta ahora toda la interacción con el cliente pasó por Jony Ayerbe de forma informal (WhatsApp/llamadas), sin una herramienta de gestión compartida identificada.
- **Reviews y documentación:** a definir — sin precedente todavía con este cliente.
- **Qué hay que cerrar sí o sí antes de arrancar:** (1) reunión con Maggie, (2) confirmación de colaboración de Pablo, (3) pricing final de la propuesta de junio (quedó con montos sin completar — "USD xxxx").

---

# B. Pre-propuesta (cara al cliente, liviana)

## 4. Propuesta

**Alcance — qué sí, qué no.**
- **Sí:** capa de ingesta/normalización de declaraciones de embarque (Excel/PDF/email) → validación contra reglas de negocio (ej. rangos de temperatura por tipo de carga) → revisión humana obligatoria → integración con la naviera de mayor volumen que tenga API (Maersk confirmada) para el envío de la Shipping Instruction → validación del Draft Bill of Lading devuelto → base de datos propia como fuente de verdad, no un reemplazo de Kai.
- **No, en esta primera etapa:** reemplazar Kai. El propio cliente lo dijo explícitamente en abril ("no es una opción considerar un cambio de sistema... arrancando la temporada") — la venta debe ser honesta en que esto es una capa satelital, no un rewrite, aunque construida para que ese reemplazo sea posible más adelante si el cliente lo decide.
- **No cubierto en el MVP:** el resto de las ~8-10 navieras sin API (quedan para una fase posterior, vía RPA u otro mecanismo, a evaluar).

**Discovery.** Gran parte del relevamiento superficial ya está hecho (2 reuniones de mapeo + diagrama de flujo + llamada de repaso). Un discovery formal acotado de **1-2 semanas** alcanzaría para: confirmar el detalle técnico de la integración con Maersk, formalizar las reglas de negocio (rangos de temperatura y demás validaciones), y resolver si Pablo colabora o no. No hace falta partir de cero.

**Prototipo — factible.** Ya existe una prueba de concepto interna (Jony extrajo y normalizó drafts de BL de Maersk y "Japac" con un LLM, con mejor resultado que Extract). Se puede mostrar como demo temprana del núcleo de extracción/normalización, más un mockup del dashboard de revisión humana.

**Cómo lo trabajaríamos.** Extracto de § 7: gestión total del ciclo por parte de Quarks, con dos dependencias críticas explícitas del lado cliente (colaboración de Pablo con Kai, confirmación de acceso a APIs de navieras) — cada una con responsable y riesgo nombrado, no asumida en silencio.

**¿Podemos ayudar? — factibilidad honesta.**
- **Alta** para el núcleo de extracción/normalización/validación de declaraciones — ya validado técnicamente por el propio equipo de Quarks.
- **Media-alta** para la integración con Maersk — la API existe, falta implementarla y probarla en producción.
- **Incierta** para el resto de navieras sin API — depende de si se opta por RPA (más costoso y frágil) y no está resuelto todavía.
- **Riesgo no controlado por Quarks:** la colaboración de Pablo. Si no se resuelve, el alcance debe recortarse a lo que no dependa de Kai.

---

# C. Salida operativa

## 5. Minuta y próximos pasos

**Abiertos:**
- Reunión con Maggie — pendiente de agendar por Jony.
- Pricing final de la propuesta de junio 2026 — quedó con montos sin completar ("USD xxxx"); hay que cerrarlo antes de la presentación de cierre.
- Confirmación de colaboración de Pablo con el sistema Kai — no resuelta.
- Confirmación de qué navieras además de Maersk tienen API utilizable (Hapag/"Japac" mencionada, sin confirmar formalmente).

**Acciones recomendadas:**
- Correr [`/minutero`](../.claude/commands/minutero.md) si se quiere dejar registro cara-al-cliente de este historial — dado que ya pasaron meses desde la última interacción formal, podría valer más una llamada de realineación que una minuta retroactiva.
- Correr [`/propuestador`](../.claude/commands/propuestador.md) a partir de este build-context, aprovechando el rediseño de Fase 0 (3 caminos + checkpoint de decisión) documentado en [`ingestion/meetings/2026-08-14-sync-jony-preventa-feedback.md`](../ingestion/meetings/2026-08-14-sync-jony-preventa-feedback.md) — el perfil de experiencia previa de Loginet (parcialmente "soldado herido" respecto a automatización, greenfield respecto a desarrollo integral) es justamente el insumo que ese rediseño pide para rankear los 3 caminos.
- Si se corre `/propuestador`, cualquier estimado de tiempo/esfuerzo debe trazarse a datos concretos de este build-context (los USD 3-4k/mes, el volumen de 500-600 facturas, la propuesta de junio ya redactada) o marcarse explícitamente como estimación a validar — no fabricar números nuevos.
