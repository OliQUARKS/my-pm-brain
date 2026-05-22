# /epics

Descompone una feature en épicas con slicing MVS/Midgame/Endgame. Sin flags: lista de épicas. Con `--detail <nombre>`: plantilla completa. Con `--push`: crea cada épica como proyecto en Linear.

## Input

Feature name, slug, o nada (infiere la feature activa de `knowledge/strategy.md`). Flags opcionales:
- `--detail <nombre>` — plantilla completa para esa épica
- `--push` — crear cada épica como proyecto en equipo PERc (`85b61bce-28d4-4e0c-946d-04a402ccd5a2`)

## Loads

- `knowledge/strategy.md` — feature activa, prioridades, non-goals
- `knowledge/product/features/<slug>.md` — componentes, OQs, estados, decisiones vinculadas
- `decisions/INDEX.md` — decisiones que afectan dependencias y criterios de aceptación
- `hypotheses/INDEX.md` — hipótesis activas relacionadas con la feature

## Updates

- `ingestion/adhoc/<date>-epics-<slug>.md` — log de épicas generadas: nombre, objetivo, slice, y (si se pusheó) ID del proyecto Linear creado. Sirve como fuente para `/stories`.
- Nada en durable layers — las épicas son artefactos de planificación. El brain registra el resultado cuando `/ingest` captura el retro del sprint.

Nothing committed without operator confirmation per autonomy mode.

## Surfaces

Sin `--detail`: lista de épicas con nombre, objetivo, slice (MVS / Midgame / Endgame), dependencias bloqueantes citadas de `decisions/`, y KPI esperado. Ordenado: MVS primero.

Con `--detail <épica>`: plantilla completa con:

- **Objetivo** — qué resuelve y para quién
- **Persona** — rol beneficiado
- **Slice** — MVS | Midgame | Endgame
- **MVS** — historia principal ("Como [rol], quiero [acción] para [beneficio]") + criterios de aceptación (un solo happy path)
- **Midgame** — extensiones post-validación del MVS
- **Endgame** — fuera de scope ahora, pero sin bloquear el diseño
- **Criterios de aceptación de la épica** — done-when conditions
- **Bloqueantes / Dependencias** — links a `decisions/` con paths relativos correctos
- **KPI de la épica**

Con `--push`: tabla de proyectos Linear creados (nombre + project ID). El project ID es el input de `/stories --push`.

OQs abiertas de la feature file que bloqueen criterios de aceptación se marcan `⚠️ OQ abierta: [descripción]` en la épica correspondiente.

## Criterios de calidad

- Cada épica tiene exactamente 1 objetivo de usuario. Si tiene más de uno, partir.
- MVS es un solo happy path sin edge cases. Si hay más de uno, partir la épica.
- Endgame no duplica MVS ni Midgame.
- Non-goals de `strategy.md § Explicit non-goals` no aparecen como épicas ni en Midgame.
- Dependencias bloqueantes citan `decisions/` con links relativos válidos.
