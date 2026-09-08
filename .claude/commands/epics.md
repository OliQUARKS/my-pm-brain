# /epics

Descompone un PRD o feature en épicas usando el proceso backloguer: identificación con criterio de exclusividad funcional, backbone narrativo, slicing MVS/Midgame/Endgame. Sin flags: lista de épicas (ID + título en infinitivo). Con `--detail <EP-XX o nombre>`: plantilla completa. Con `--push`: al terminar, ofrece subir a ClickUp.

## Input

Feature name, slug, o nada (infiere la feature activa de `knowledge/strategy.md`, o del PRD en `knowledge/product/features/<slug>.md` si existe). Flags opcionales:
- `--detail <EP-XX o nombre>` — plantilla completa para esa épica
- `--push` — al terminar, ofrece subir a ClickUp (ver § Cierre)

## Loads

- `knowledge/strategy.md` — feature activa, prioridades, non-goals
- `knowledge/product/features/<slug>.md` — problema, componentes, OQs, decisiones vinculadas, y `## Scope by capability` si existe (viene de `/prd`)
- `decisions/INDEX.md` — decisiones que afectan dependencias y criterios de aceptación
- `hypotheses/INDEX.md` — hipótesis activas relacionadas con la feature
- `ingestion/adhoc/*-epics-<slug>.md` previos — para el chequeo de no-redundancia: qué épicas ya se generaron/detallaron para esta feature

## Proceso (backloguer)

1. **Identificación**: para cada épica candidata, ID secuencial `EP-XX` (continúa la numeración si ya hay épicas previas para esta feature en `ingestion/adhoc/`) + título en infinitivo.
2. **Criterio de exclusividad funcional**: cada épica resuelve un problema de usuario distinto. Si una funcionalidad ya quedó asignada a una épica, no puede reaparecer en otra.
3. **Sin `--detail`**: entregar ÚNICAMENTE la lista ID + título. No desarrollar detalle todavía.
4. **Con `--detail`**: revisar primero las épicas ya detalladas de la misma feature. Si un criterio de aceptación o una actividad del backbone ya está cubierto en una épica anterior, omitirlo o referenciarlo brevemente ("Usa el flujo de login definido en EP-01") en vez de repetirlo. Después, aplicar la plantilla completa.

## Updates

- `ingestion/adhoc/<date>-epics-<slug>.md` — épicas generadas (lista o detalle), en Markdown, con IDs `EP-XX`. Sirve como fuente para `/stories` y como memoria de no-redundancia para corridas futuras de `/epics`.
- Nada en durable layers — las épicas son artefactos de planificación. El brain registra el resultado cuando `/ingest` captura el retro del sprint.

Nothing committed without operator confirmation per autonomy mode.

## Surfaces

**Sin `--detail`**: tabla `EP-XX | Título (infinitivo) | Slice | Bloqueantes | KPI esperado`. Ordenado: MVS primero.

**Con `--detail <EP-XX>`**: plantilla completa (formato backloguer, en Markdown):

- **Identificación de la épica** — Título (acción en infinitivo) + ID
- **Enmarcado del problema** — Usuarios objetivo / Problema de usuario / Valor para el negocio
- **Backbone** — flujo narrativo de izquierda a derecha, mínimo 3 actividades
- **Slicing**
  - Nivel 1 — Mínima Solución Viable (MVS): funcionalidad crítica para validar el flujo completo
  - Nivel 2 — Midgame: mejoras e incrementos, reglas complejas
  - Nivel 3 — Endgame: refinamiento, rendimiento, accesibilidad
- **Criterios de aceptación de alto nivel** — Outcome esperado (cambio de comportamiento) + Métricas de éxito (cuantificables)
- **Riesgos y supuestos** — riesgos de factibilidad + supuestos, dependencias técnicas y reglas de negocio

OQs abiertas de la feature file que bloqueen criterios de aceptación se marcan `⚠️ OQ abierta: [descripción]` en la sección correspondiente.

## Cierre

Al terminar de surfacear (con o sin `--push`), preguntar siempre: **"¿Subís esto a ClickUp, a otra herramienta, o queda como está?"**

- **ClickUp** → crear o reusar una Lista de ClickUp para la feature (`clickup_create_list` si no existe), y una Tarea por épica dentro de esa lista (`clickup_create_task`), usando la plantilla de detalle como descripción de la tarea.
- **Otra herramienta** → ofrecer el mismo contenido reformateado en texto plano estricto (formato backloguer original): sin markdown, títulos de sección y de épica en MAYÚSCULAS, listas con guiones, tres saltos de línea entre secciones. Listo para copiar y pegar.
- **Queda como está** → no se hace nada más; `ingestion/adhoc/<date>-epics-<slug>.md` ya es la fuente.

## Criterios de calidad

- Cada épica tiene exactamente 1 objetivo de usuario. Si tiene más de uno, partir.
- MVS es un solo happy path sin edge cases. Si hay más de uno, partir la épica.
- Endgame no duplica MVS ni Midgame.
- Non-goals de `strategy.md § Explicit non-goals` no aparecen como épicas ni en Midgame.
- Dependencias bloqueantes citan `decisions/` con links relativos válidos.
- Antes de detallar una épica nueva, se revisó la memoria de épicas ya detalladas de la misma feature (no-redundancia).
