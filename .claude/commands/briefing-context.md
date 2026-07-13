# Skill: briefing-context (PRE)

**Tu objetivo:** preparar mejor la primera reunión (preventa) identificando **qué información necesitamos obtener** y **qué preguntas conviene hacer según el contexto del cliente**. Transformás un input crudo y vago en un briefing útil para discovery — no en un cuestionario genérico.

## Propósito

Que quien va a la reunión llegue **con contexto, no en pelotas**: que pueda tocar una fibra sensible desde el minuto uno y que la charla deje de ser "les contamos qué hacemos" y pase a ser otra cosa. El doc **no reemplaza el criterio ni la experiencia** — es el piso de contexto que habilita las preguntas buenas ("¿y esto les impacta las ventas?"), no que las responde.

## Cómo trabajás

- **No uses un cuestionario fijo.** Adaptá el análisis y las preguntas al **rubro/industria, tipo de empresa, tipo de problema y tipo de producto/servicio** del caso.
- **Reformulá en el lenguaje del cliente.** Una pregunta genérica ("¿qué sistemas usan?") se vuelve concreta ("¿el alta de la cuenta comitente se apoya en el KYC que ya hicieron en la billetera?").
- **Puntual y acotado al objetivo declarado.** Profundidad en lo que importa > cobertura superficial. No infles el scope: si el pedido es un flujo interno, no derives en un plan de producto entero.
- **Nada inventado.** Lo que falta se marca como "a preguntar en la reunión". Fuentes verificables → observación; motivaciones y lecturas → interpretación, etiquetada.

## Entrada

Input crudo y variado — **no esperes una spec**. Lo típico: "me llamó Juan de tal empresa, tiene un quilombo operativo / quiere automatizar / tiene un problema de posicionamiento, quiere que nos juntemos". Con eso alcanza.

- **El cliente** — empresa y quién contactó.
- **La página del cliente** — URL (si hay).
- **Los asistentes** — nombres/roles de ambos lados (los que se sepan).
- **Por qué se juntan** — el disparador, en las palabras que llegaron.

Si un campo falta, no lo inventes: queda como "a preguntar".

## Qué tenés que entender sí o sí — objetivos de información

Estos objetivos son **la guía principal del skill**. Para cada reunión, relevá siempre:

1. **Contexto de la empresa** — qué hace, a quién, cómo gana plata.
2. **Problema a resolver** — el dolor concreto que los trajo.
3. **Objetivo de la reunión** — qué esperan que salga de este encuentro.
4. **Usuarios involucrados** — para quién se resuelve; roles y permisos.
5. **Dolores principales** — del rubro y del caso puntual.
6. **Stakeholders presentes** — quién decide, qué le importa a cada uno.

Después **traducí cada objetivo en preguntas contextualizadas al cliente**. Las preguntas genéricas de más abajo son solo **ejemplos de apoyo** para inspirar la formulación — no una estructura obligatoria ni un checklist a copiar.

## Ejes obligatorios de análisis

Además de los objetivos, evaluá siempre estos tres ejes y **profundizá el que aplique especialmente** al caso:

- **Regulatorio** — qué organismos/normas alcanzan al negocio (ej.: BCRA, CNV, UIF).
- **Marco legal** — restricciones legales sobre datos, contratos, delegación de funciones.
- **Stack tecnológico** — con qué viven hoy (CRM, ERP, core, proveedores de identidad), qué integra, qué es reutilizable.

Si uno de estos ejes es el nudo del problema (p. ej. doble regulador en un onboarding fintech), es donde va la profundidad — no lo trates como una casilla más.

## Qué procesa / busca

1. **Analizar la página del cliente** — qué hacen, a quién, tono, productos visibles.
2. **Buscar info de la empresa y su rubro** — tamaño, mercado, modelo.
3. **Buscar info de las personas** — LinkedIn / rol / seniority. Motivaciones **inferidas**, marcadas.
4. **(Opcional) Competidores** — solo si aplica (ver abajo).

## Salida — Documento de Preparación

Incluí, **cuando aplique** al caso:

- **Contexto de empresa y rubro** — detalle de la empresa (un párrafo), del rubro, y su modelo.
- **Glosario específico del cliente** — términos del rubro y de la empresa (siglas, productos, nombres propios) que van a aparecer en la reunión y hay que manejar.
- **Dolores del rubro y del caso** — los típicos de la industria + los que sugiere este cliente. Son el disparador de las preguntas empáticas.
- **Usuarios** — para quién se resuelve, roles y permisos (lo inferible; el resto → a preguntar).
- **Stakeholders / personas en la mesa** — mini perfil por asistente: rol, LinkedIn, y qué le puede importar (inferido). Una línea por persona.
- **Riesgos y restricciones relevantes** — regulatorios, legales, técnicos.
- **Preguntas de discovery contextualizadas** — organizadas por objetivo de información, en lenguaje del cliente. **Accionables y puntuales**, no genéricas.

Reglas de la salida: **sin texto placeholder ni ambiguo.** Si algo no se sabe, se nombra como gap explícito ("a preguntar"), no se rellena. Priorizá preguntas que muevan la aguja del discovery sobre preguntas de manual.

## Ejemplos de apoyo — preguntas genéricas

Solo como inspiración para formular las contextualizadas. **No copiar tal cual.**

- Problema/objetivo: ¿qué los trajo a buscar ayuda ahora?, ¿qué cambió?, ¿cómo lo resuelven hoy?
- Impacto: ¿esto afecta ventas/costos/tiempos?, ¿cómo lo miden?, ¿quién lo sufre a diario?
- Usuario/proceso: ¿para quién se resuelve?, ¿roles/permisos?, ¿con qué sistemas viven hoy?
- Factibilidad: ¿qué intentaron que no funcionó?, ¿tienen APIs/accesos/documentación?

## Ejemplo trabajado — de contexto bruto a briefing

**Input (bruto):** "El cliente es AL2, es como una doble compañía con ACA Valores, las dos vienen de la Asociación de Cooperativas Argentinas (agro). Contactó el CEO: quiere rehacer el onboarding para unificar el de los dos productos. AL2 es la billetera; ACA Valores la financiera (acciones, letras, bonos). Van el CEO, el líder de PMs, el CTO y el líder de producto. Páginas: al2.com.ar, acavalores.com.ar."

**Cómo lo interpretás:**
- El objetivo es **unificar un flujo interno** → build de proceso, **no** batalla competitiva → competidores queda opcional.
- Dos productos con **dos reguladores** (billetera = BCRA/PSP; financiera = CNV/ALyC/cuenta comitente) → el **eje regulatorio/legal es el nudo**: ahí va la profundidad, porque "un onboarding para los dos" choca con requisitos de KYC distintos y con PLD que la ALyC no puede delegar.
- Usuario compartido probable: el productor agropecuario asociado → verificar si es el mismo perfil en ambos productos.
- Van cuatro decisores (CEO+CTO+producto+PMs) → reunión de definición, tema prioritario.

**Output (extracto):**
- *Glosario del cliente:* ALyC, cuenta comitente, PSP/PSPCP, CDC (Cuenta Corriente Cooperativa), MEP, KYC/PLD-UIF, CNV vs. BCRA.
- *Dolor central:* unificar el alta implica reconciliar dos regímenes de KYC (BCRA y CNV) sobre la misma persona, sin poder delegar el conocimiento del cliente de la financiera.
- *Pregunta contextualizada (regulatorio):* "¿El alta de ACA Valores puede apoyarse en el KYC ya hecho en AL2, o legal/UIF lo prohíbe?"
- *Pregunta contextualizada (usuario):* "¿Es la misma persona en ambos productos o son segmentos distintos? ¿Persona humana y jurídica?"
- *Riesgo:* el BCRA endureció reglas de billeteras/PSP en 2025-26 → el flujo nuevo tiene que nacer alineado a lo último.

## Opcional: competidores

Correr **solo** si el objetivo es ayudar al cliente con **su producto** (no un problema interno). Por competidor: FODA; directo/indirecto/disruptivo y por qué; tracción, funding, base de usuarios; últimos movimientos. Identificar ~5, marcando dato verificable vs. estimación.

## Fuera de alcance (v2)

Anotado, **no** en esta versión:
- **Mapa de habilidades del equipo** — quién hizo mobile/fintech/gestión, para decir "tenemos gente con experiencia en tu rubro".
- **Experiencias previas por rubro** — post-mortems de proyectos (AL2, PERC, Fichin, Acavalores) que alimenten futuros briefs.

## Criterios de calidad

✅ Corre con input mínimo/vago sin trabarse
✅ Releva los 6 objetivos de información y los traduce en preguntas contextualizadas al cliente
✅ Evalúa los 3 ejes (regulatorio / legal / stack) y profundiza el que aplica
✅ Salida con glosario del cliente, stakeholders, dolores, riesgos y preguntas de discovery accionables
✅ Preguntas puntuales y contextualizadas, no genéricas; sin placeholder ni scope inflado
✅ Observación vs. interpretación etiquetadas; lo que falta queda como gap explícito
✅ Competidores solo si aplica (producto, no problema interno)
✅ 100% español
