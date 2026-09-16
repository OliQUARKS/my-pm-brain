# Kit de Discovery: catálogo y selección (etapa 7)

> **Qué es:** el catálogo de metodologías disponibles para la etapa 7 (Discovery, post-venta,
> pre-desarrollo, ver [`_ciclo-preventa.md`](./_ciclo-preventa.md) § Discovery) y la lógica para
> elegir cuáles correr en cada engagement. No se corren las 15 en cada proyecto; se elige un
> combo de 2-4 según la madurez del cliente y la forma del problema.
>
> Cada fila linkea a su skill (`/discovery-<slug>`). La skill enseña *cómo* correr la técnica
> con *qué* herramienta; este archivo enseña *cuál* elegir y *por qué*.

## 1. Para alinear negocio y estrategia

Antes de hablar de producto, cuando el cliente no tiene claro su propio modelo de negocio,
o el pitch de venta fue vago ("queremos una app que ayude a nuestros clientes").

| Método | Cuándo | Skill |
|---|---|---|
| Business Model Canvas / Lean Canvas | Modelo de negocio no está claro, o es una línea nueva dentro de una empresa existente. Lean Canvas si ya hay tracción y se quiere ir directo a problema/solución. | [`discovery-business-model-canvas`](../.claude/commands/discovery-business-model-canvas.md) |
| Value Proposition Canvas | Complementa al anterior; fuerza precisión cuando el pitch confunde features con propuesta de valor. | [`discovery-value-proposition-canvas`](../.claude/commands/discovery-value-proposition-canvas.md) |
| Jobs to be Done (JTBD) | El cliente confunde features con necesidades. Mejor punto de entrada cuando hay usuarios reales a entrevistar. | [`discovery-jtbd`](../.claude/commands/discovery-jtbd.md) |
| Stakeholder Mapping / RACI | Siempre temprano; evita que el discovery se caiga porque el que firmó no es el que decide. | [`discovery-stakeholder-mapping`](../.claude/commands/discovery-stakeholder-mapping.md) |

## 2. Para entender el problema y el usuario

Cliente no-técnico o sin research previo.

| Método | Cuándo | Skill |
|---|---|---|
| Entrevistas semiestructuradas | Base de todo. Si el cliente "no tiene ni idea", esto solo ya destraba mucho. | [`discovery-interview-guide`](../.claude/commands/discovery-interview-guide.md) |
| Customer Journey Mapping | El producto digitaliza o mejora un proceso que ya existe offline o en otro sistema. Visual, fácil de que el cliente lo entienda sin vocabulario técnico. | [`discovery-journey-map`](../.claude/commands/discovery-journey-map.md) |
| Empathy Mapping | Más liviano, aperitivo en un taller de medio día para romper el hielo con stakeholders sin experiencia en ejercicios de UX. | [`discovery-empathy-map`](../.claude/commands/discovery-empathy-map.md) |
| Service Blueprint | El problema no es solo de interfaz sino de operación (procesos manuales, sistemas y personas del lado del negocio). | [`discovery-service-blueprint`](../.claude/commands/discovery-service-blueprint.md) |
| Diary studies / shadowing | Hay presupuesto y tiempo, y el comportamiento real difiere mucho de lo que la gente dice en entrevista (procesos operativos, logística, salud). | [`discovery-diary-study`](../.claude/commands/discovery-diary-study.md) |

## 3. Para pasar de problema a alcance de producto

| Método | Cuándo | Skill |
|---|---|---|
| User Story Mapping | El cliente (o su contraparte de producto) maneja épica/historia. Puente hacia `/backloguer`, pero de entrada asume vocabulario ágil. | [`discovery-story-map`](../.claude/commands/discovery-story-map.md) |
| Impact Mapping | Alternativa más ejecutiva; parte de un objetivo de negocio, no de una lista de features. Mejor para C-level. Puede alimentar el story map después. | [`discovery-impact-map`](../.claude/commands/discovery-impact-map.md) |
| Opportunity Solution Tree | Ambigüedad real sobre qué problema atacar primero. Requiere cadencia de entrevistas continua; si el cliente no puede sostenerla, el árbol se pudre rápido. | [`discovery-opportunity-tree`](../.claude/commands/discovery-opportunity-tree.md) |
| Event Storming | Dominio complejo (fintech, legal, logística, muchas reglas de negocio, tipo PERC o RyD Abogados). Requiere facilitación fuerte pero funciona con gente no técnica: se habla en verbos de negocio. | [`discovery-event-storming`](../.claude/commands/discovery-event-storming.md) |
| Feature/Effort-Impact Matrix (2×2) | Cierre de un batch de discovery; converge lo ya dicho en voz alta, no genera ideas nuevas. | [`discovery-impact-matrix`](../.claude/commands/discovery-impact-matrix.md) |

## Premortem: chequeo de riesgo, no de scoping

| Método | Cuándo | Skill |
|---|---|---|
| Premortem | Cierre del discovery o kickoff de desarrollo; antes de que los compromisos se endurezcan. Saca a la luz riesgos que nadie dice en voz alta al principio. | [`discovery-premortem`](../.claude/commands/discovery-premortem.md) |

## Cómo elegirlos según madurez del cliente

| Cliente | Combo recomendado |
|---|---|
| No tiene idea de nada, quiere "una web" | Fuera de este kit; ver catálogo de materiales de bajo-conocimiento-técnico (moodboards, sitemap, wireframes lo-fi) en `propuestador`/`prototipador`, no en Discovery. |
| Tiene una idea de negocio pero no de producto | `discovery-business-model-canvas` o `discovery-jtbd` + `discovery-journey-map` + `discovery-impact-map` |
| Tiene equipo de producto propio, habla en features | `discovery-story-map` directo, con `discovery-stakeholder-mapping` de fondo |
| Dominio complejo con muchas reglas de negocio (tipo PERC, RyD Abogados) | `discovery-event-storming` + `discovery-service-blueprint` antes que cualquier story map |
| Cierre de cualquier combo, antes de comprometer equipo/tiempo/costo | `discovery-impact-matrix` (converger) → `discovery-premortem` (pulsear riesgo) |

## Fuera de este kit (v2, evaluado y descartado por ahora)

Decisión de Olivier, 2026-09-14 (stakeholder-verbal): estos quedan afuera del primer corte de
skills, no porque no sirvan, sino porque no son el foco inmediato:

- **Sección 4 del catálogo** (moodboard, sitemap + wireframes lo-fi, card sorting, elevator-pitch
  canvas); materiales para clientes de bajo conocimiento técnico. Viven conceptualmente cerca
  de `propuestador`/`prototipador`, no de Discovery.
- **Design Sprint y Design Thinking Workshop**; formatos de facilitación de taller (sección 5),
  no metodologías puntuales. Quedaron afuera a favor de profundizar solo en Premortem.
- **Kano Model, RICE/ICE scoring, Assumption Mapping / Riskiest Assumption Test**; sugeridos en
  el chat que originó este kit como complementos de priorización y validación de riesgo, pero no
  pedidos explícitamente. Candidatos naturales si `discovery-impact-matrix` resulta insuficiente
  para priorizar backlogs largos, o si `discovery-premortem` necesita un paso previo más formal
  de mapeo de supuestos.
- **Sección 6 del catálogo** (Miro/FigJam, repositorio de research, checklist de kickoff); son
  herramientas y materiales transversales, no metodologías; cada skill de este kit ya nombra su
  herramienta primaria en su propia sección `## Tool`.
