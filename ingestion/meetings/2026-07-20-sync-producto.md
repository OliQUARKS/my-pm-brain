# Ingesta — SYNC Producto (Quarks interno, 2026-07-20)

- **Fuente (transcript):** [../../source/meetings/2026-07-20-sync-producto.md](../../source/meetings/2026-07-20-sync-producto.md)
- **Shape:** meeting (sync interno de producto Quarks — recap + retro informal de PERC)
- **Participantes:** Olivier (PM Quarks, "Me"), Juan Pablo Norverto (CTO Quarks), Federico Fernandez "Fefe" (COO Quarks), Danilo Luce.
- **Contexto:** sync de producto de Quarks. Olivier hace el recap de PERC (call AMFAYS del viernes 17/7) y se abre un **debate retrospectivo** sobre dos frentes de la demora de la entrega: (a) la **reescritura de lambdas**, y (b) la **fricción de velocidad entre el front (JP/Moyanito) y el back (Marcos)**. Fefe pide una **review técnica con Nico y Marcos**.
- **Nota del PM (alcance):** DAEA/CURSIJA/MEGALABS/LINKEDIN/AL2/iFlow **no son PERC** — quedan fuera del ruteo durable (solo se anota lo mínimo que toca al equipo/soporte de PERC). Lo sustantivo de esta ingesta es el debate JP↔Marcos + la re-atribución de la bomba de lambdas + el debate de captura de datos del documento AMFAYS.

---

## 1. Recap AMFAYS (Type A — refresco, ya ingestado el 17/7)

- **(observation)** Olivier recapituló el call del viernes con **AMFAYS** (la mutual que provee el instrumento) al equipo. Sin novedades respecto de [la ingesta del 2026-07-17](2026-07-17-call-amfays-documento-prestamo.md). — Olivier, [source](../../source/meetings/2026-07-20-sync-producto.md)
- **(observation)** Olivier señaló que AMFAYS pide **KYC biométrico**, pero PERC **ya lo captura en el onboarding de la billetera (Perk)** — falta resolver **cómo enlazar** esa identidad ya capturada con lo que exige el documento AMFAYS ("hay que hacer algo para que diga: es este / lo agarraste"). — Olivier.

## 2. ⭐ Debate: ¿dónde se capturan los ~20 campos del documento AMFAYS? (open question de diseño — NUEVO)

- **(observation)** Olivier: el documento AMFAYS requiere **~20 datos a capturar**; **hoy sólo ~5 están disponibles**; el resto requiere trabajo/integración (ej. **generar el nº SAEM/SAIN**). El problema no es tener los datos sino que **no hay un front para cargarlos**. — Olivier + Fefe ("Oli dice que mirándolo bien tiene todo; el problema es que no tiene un front para poner esos datos").
- **(interpretation, Norverto — postura)** La captura de esos datos **NO debe meterse en el onboarding** de la billetera; debe llevarse **al momento del "taggeo"** en el Back Office (cuando PERC selecciona/etiqueta quiénes pueden pedir crédito). "Si nos metemos en el onboarding, esto no termina nunca." Propone habilitar en el BO una pantalla para cargar esos datos en el momento del tagueo. (stakeholder-verbal, Juan Pablo Norverto, 2026-07-20)
- **(interpretation, Fefe — objeción)** Técnicamente, hacer el taggeo con esa carga de datos **"es un caos"**. Prefiere **esperar a la reunión de hoy** (C12) antes de comprometerse. (stakeholder-verbal, Federico Fernandez, 2026-07-20)
- **(decision en evaluación — no cerrada)** Opción sobre la mesa (Fefe la pasó por mensaje/cap a Olivier, quien la está evaluando): **poner placeholders en el documento** y **capturar los datos después** ("acá va a ir esto, acá va a ir esto"). Se resuelve en la reunión de hoy. — Olivier + Fefe.
- **(assumption)** Norverto asume que la aprobación del préstamo pasa por un paso de **taggeo manual en BO**; Olivier aclara que **la aprobación es automática** (pre-aprobado), y que lo que existe en BO es el **taggeo** de elegibles — no un paso de aprobación. Consistente con lo ya definido (préstamo pre-aprobado; ver [2026-07-16 UAT §1](2026-07-16-uat-prestamos-lambdas-perc.md)). — Olivier.

## 3. Re-atribución de la bomba de lambdas (refina la ingesta del 16/7)

- **(interpretation, Norverto)** La consolidación de lambdas (**~50→~20**) fue una **decisión arquitectónica de PERC**, no de Quarks: PERC maneja todo con lambdas ("una lambda por operación"); **Nico advirtió sobre el costo en las charlas previas al proyecto** ("si son muchas lambdas se te va el costo"). Al chocar con un **límite/quota (RLA)** y ver que el costo se disparaba, PERC decidió reagrupar. Norverto lo enmarca como **"iteración normal de cualquier proyecto, no un problema"** (cita el precedente de las colas de mensajería en "AL2"). (stakeholder-verbal, Juan Pablo Norverto, 2026-07-20)
- **(interpretation, Fefe)** Lo que le llama la atención no es el cambio en sí (lo entiende) sino **por qué surgió dos días antes de terminar** — algo tan importante debería haberse sabido antes, de ambos lados. Pide **doble-check con Nico** (más cerca del día a día). (stakeholder-verbal, Federico Fernandez, 2026-07-20)
- **(nota de contraste con evidencia previa)** La [ingesta del 16/7](2026-07-16-uat-prestamos-lambdas-perc.md) registró la lambda como **~65→~20** y con un tono más crítico de Olivier ("no nos prestaron atención… debió surgir el día 2"). La versión de Norverto **re-atribuye la causa a la arquitectura de PERC + una advertencia temprana de Nico**, y baja el tono de "error" a "iteración normal". **No es contradicción de hecho** (ambos coinciden en que se pidió tarde y obliga a reescribir); es un **matiz de causación/responsabilidad**. La cifra difiere (65 vs 50 de origen) — se preserva la de la fuente técnica (16/7: ~65 hoy). A cerrar en la review técnica con Nico/Marcos.

## 4. ⭐ Debate JP (Moyanito) ↔ Marcos — fricción de velocidad en el front (NUEVO, sustantivo)

Retro informal sobre por qué el **frontend no siguió el ritmo del backend** en PERC. Todo lo de abajo es **interpretación / verbal**, sin artefacto más allá del transcript.

- **(observation)** El **front no iba a la velocidad del back**. Olivier lo fue tratando con Nico a lo largo del proyecto. — Olivier.
- **(interpretation, Olivier)** Causa probable mixta: **seniority** (Moyanito lleva ~2 años en la empresa) **+ lenguaje/stack que no manejaba** (venía de otro stack; Fefe menciona que dedicó ene-feb-mar a aprender **Flutter** mientras estaba "papando moscas"). — Olivier + Fefe.
- **(observation)** Moyanito terminaba **"pelando el recurso de Marcos"**: le pedía a Marcos que le terminara tareas de front ("terminalo vos que tengo que entregar"). **No se pelearon de frente**; la fricción llegaba a Olivier por mensajes cruzados de uno y otro. — Olivier.
- **(observation → acción de Olivier)** A mitad de proyecto, al ver que se complejizaba, **Olivier hizo un prototipo del Back Office** (no se había hecho en el proyecto previo "Gaia") y diseñó el prototipo, para cerrar el gap del front. — Olivier.
- **(interpretation, Norverto — perfil de Moyanito)** "Es muy **autónomo, pero a un extremo de que se queda sin herramientas**": bajo presión **se cierra** ("lo hago como pueda"), **no da parte diario**, cuesta mucho **hacerle seguimiento de tareas**, y **nunca viene con el planteo de un problema**. Viene de trabajar solo en Gaia (con su hermano) hasta nov-2025, autogestionado. (stakeholder-verbal, Juan Pablo Norverto, 2026-07-20)
- **(interpretation, Norverto + Fefe — responsabilidad de gestión)** Norverto asume culpa de gestión: **"estamos en falta con él"**; debió pedirle a Nico que estuviera encima y no lo hizo; "es una persona a la que dejamos siempre sola". Fefe coincide: **"al último que hay que ir es a Moyanito"** (la falla es de acompañamiento). (stakeholder-verbal, Juan Pablo Norverto + Federico Fernandez, 2026-07-20)
- **(decision, equipo)** **Moyanito sale de PERC.** A partir de esta semana queda **exclusivamente en DAEA**; Norverto se mete de lleno a darle seguimiento. **Nati** pasa a ser el **punto de contacto/acompañamiento de JP** (no solo Nico); Debo escala como referente de frontend. — Norverto + Fefe. *(DAEA/Debo fuera de scope PERC — se anota solo la salida de Moyanito del equipo PERC.)*
- **(acción, Fefe)** Fefe quiere una **review técnica con Nico y Marcos** esta semana o la que viene, por dos temas: **(1)** qué pasó entre Marcos y JP ("chispazos", criterio de Olivier: no pueden trabajar más juntos); **(2)** la reescritura de lambdas. — Fefe.

## 5. Decisión del sprint extra (converge la tensión del deadline)

- **(decision operativa, Fefe)** Si la entrega necesita **un sprint más (1–2 semanas sobre 12 = ~10%)**, **se pasa así como está** — "es lo lógico, está perfecto, dejemos correr". Marca el contraste con "cursija": PERC "se cobró muy bien" y lo hace hoy **un solo dev**. (stakeholder-verbal, Federico Fernandez, 2026-07-20)
- **(observation)** La decisión sobre el sprint extra se toma **hoy en la reunión C12** con **Nico y Seba** (Olivier, Nico, Seba, punto por punto). **Marcos no está** (vacaciones en Saint Tropez) → **Seba toma la decisión** y el equipo ve cómo ejecutar. — Olivier + Fefe.
- **(nota)** Esto es la vía "(a) extender un sprint por las buenas" de la [tensión del deadline en strategy §Tensions](../../knowledge/strategy.md). El deadline "hard-stop martes 2026-07-21" queda **de facto reemplazado por +1 sprint aceptado internamente**, a confirmar con PERC (Seba) hoy.

## 6. Pendientes = mayormente bugs (refina el tablero)

- **(observation, Olivier)** Al leer la lista de pendientes, **gran parte son bugs reportados**, más que nuevas funcionalidades. Hay que **organizarlos en la tiquetera**. — Olivier + Norverto ("tenemos que organizar… ver cómo hacemos support"). Refina el encuadre de [pendientes-produccion.md](../../knowledge/product/pendientes-produccion.md): el camino a producción es cada vez más **estabilización/bugfix** que feature nuevo.

## 7. Cobertura de soporte / vacaciones (ops, toca a PERC)

- **(observation)** **Nati** se va **del 24 al 31** (agosto); **Moyanito pidió 5 días en agosto** (misma ventana aprox.) — a coordinar entre ellos. Esa semana **Olivier queda de guardia**. Para el **soporte de PERC** post-entrega Norverto propone poner a **Marcos** (Olivier: "le tengo que enseñar entonces"). — Olivier + Fefe + Norverto. *(No durable por ahora; watch para el plan de soporte post-go-live.)*

## 8. Fuera de scope PERC (registrado y descartado del ruteo)

- **iFlow** (nuevo proyecto, KT/shadowing jul-ago, ~47 clientes a futuro, Marcos entraría al KT), **DAEA/Debo/Juani**, **cursija** (entrega inminente, costos 25+20), **MegaLabs** (soporte mínimo pago hasta fin de año), **LinkedIn/Natilú** (estrategia de contenido de Danilo), **AL2** (precedente de arquitectura citado). **No se rutean** — el PM lo marcó explícitamente como no-PERC.

## 9. Ruteo — destinos durables (PROPUESTOS, requieren OK del PM — Autonomy = propose-and-wait)

- **`stakeholders/juampi-moyano.md`** — **reescritura sustantiva** (requiere OK: cambia concerns/perfil). Actualizar friction (low→**medium**, por impacto en la entrega de PERC), agregar perfil de trabajo (autónomo al extremo/se cierra/no reporta), la salida de PERC → DAEA, y touchpoint 2026-07-20. + fila INDEX.
- **`stakeholders/marcos-perez.md`** — touchpoint 2026-07-20: diferencia de velocidad con el front; le derivaban tareas de front; candidato a soporte PERC post-entrega + KT iFlow (fuera de scope). Last-touched 2026-07-20.
- **`stakeholders/juan-pablo-norverto.md`** — touchpoint 2026-07-20 (re-atribución lambdas a arquitectura PERC + advertencia de Nico; perfil de Moyanito; postura "captura al taggeo, no al onboarding"). Last-touched 2026-07-20.
- **`stakeholders/federico.md`** — touchpoint 2026-07-20 (pide review técnica Nico/Marcos; aval de +1 sprint "pasar como está"; taggeo "es un caos"; delega decisión a Seba). Last-touched 2026-07-20.
- **`knowledge/product/features/flujo-credito.md`** — §Timeline: entrada 2026-07-20 (sync interno: +1 sprint avalado por Fefe, Moyanito sale del front, debate de captura de datos). §Open questions: **dónde se capturan los ~20 campos AMFAYS** (onboarding vs. taggeo en BO vs. placeholders) — hoy sólo ~5 disponibles, sin front de carga. §Risks: nota sobre gap de velocidad del front como causa de la demora + management gap (Moyanito sin acompañamiento).
- **`knowledge/product/pendientes-produccion.md`** — §Meta-decisión plazo: anotar que Fefe avala +1 sprint y que la decisión formal la toma Seba en la C12 del 20/7. §4/§15b: agregar la open question de **dónde/cómo se cargan los campos AMFAYS** (falta front de carga; opción placeholders). Encuadre general: pendientes ≈ mayormente bugs.
- **`knowledge/strategy.md` §Tensions** — actualizar la tensión del deadline: converge hacia **resolución (a) +1 sprint aceptado internamente** (Fefe avala; Seba confirma con PERC el 20/7). **Requiere OK del PM (cambio en strategy).**
- **`decisions/`** — candidata futura (no abrir hoy): *"Los ~20 campos del documento AMFAYS se cargan en [onboarding | taggeo BO | placeholders diferidos]"* — se resuelve en la C12 del 20/7. Y posible registro de *"Entrega PERC = +1 sprint sobre las 12 semanas"* si el PM quiere anclarla.

## 10. Contradicciones / tensiones con evidencia previa

- **Lambdas (§3):** matiz de causación vs. la [ingesta del 16/7](2026-07-16-uat-prestamos-lambdas-perc.md), no contradicción de hecho. Cifra de origen difiere (50 vs 65) — se preserva la técnica (16/7). Se resuelve en la review técnica.
- **Captura de datos (§2):** primera vez que aparece explícito el debate **onboarding vs. taggeo BO vs. placeholders** para los campos AMFAYS. Coherente con "el usuario final no carga nada" (el debate es del lado operador/BO, no del usuario). No contradice; **abre** una open question de diseño.
- **Moyanito (§4):** el stakeholder file lo tiene como friction **low**; esta reunión lo sube a **medium** por impacto en la entrega. Cambio de perfil → propuesto, no aplicado.
