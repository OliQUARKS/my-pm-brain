# /stories

Descompone una épica en historias de usuario INVEST. Sin flags: lista de historias. Con `--detail <historia>`: plantilla completa. Con `--push <project-id>`: crea las historias como issues en el proyecto Linear dado.

## Input

Nombre de épica (desde contexto de `/epics` o como argumento) o project ID de Linear. Flags opcionales:
- `--detail <historia>` — plantilla completa para esa historia
- `--push <linear-project-id>` — crear historias como issues dentro del proyecto Linear

## Loads

- `ingestion/adhoc/<date>-epics-<slug>.md` — output del último `/epics` para la feature (fuente de contexto de la épica)
- `knowledge/product/features/<slug>.md` — OQs abiertas que afectan criterios de aceptación
- `decisions/` relacionadas con la épica — para notas técnicas y restricciones
- `knowledge/strategy.md` — para verificar que ninguna historia implementa un non-goal

## Updates

- `ingestion/adhoc/<date>-stories-<slug>-<epic>.md` — log de historias generadas: título, slice, tamaño estimado, y (si se pusheó) ID del issue Linear creado.
- Nada en durable layers — mismo principio que `/epics`.

Nothing committed without operator confirmation per autonomy mode.

## Surfaces

Sin `--detail`: lista de historias con título en formato "Como [rol], quiero [acción]", slice (MVS / Midgame / Endgame), y tamaño estimado (XS / S / M / L / XL). Ordenado: MVS primero.

Con `--detail <historia>`: plantilla completa con:

- **Objetivo** — qué problema resuelve
- **Épica padre**
- **Slice** — MVS | Midgame | Endgame
- **Criterios de aceptación — happy path** — en formato Given / When / Then
- **Criterios de aceptación — unhappy paths** — al menos 1, obligatorio
- **Notas técnicas** — restricciones de `decisions/` o OQs marcadas `⚠️ OQ abierta: [descripción]`
- **Dependencias** — historias o decisiones que bloquean esta
- **Tamaño estimado** — XS (<4h) | S (<1d) | M (<3d) | L (<1sem) | XL → partir antes de pushear

Con `--push <linear-project-id>`: tabla de issues creados (título + issue ID). Historias XL no se pushean — se señalan al PM para partir primero.

## Criterios INVEST — verificar antes de generar

- **I**ndependiente: no bloquea ni depende de otra historia del mismo slice, salvo dependencias explícitas
- **N**egociable: no es un contrato, es una conversación con el equipo
- **V**aliosa: entrega algo verificable para el usuario o el sistema
- **E**stimable: el tamaño es asignable con la información disponible
- **S**mall: termina en ≤ 3 días de dev. Si no, partir.
- **T**esteable: tiene al menos 1 criterio de aceptación verificable

Historias que no pasan INVEST se parten antes de surfacear, sin excepción.

## Notas

- Unhappy paths son obligatorios. Al menos 1 por historia. Si no hay ninguno obvio, la historia está mal definida — redefinir.
- OQs sin respuesta que afecten criterios de aceptación → `⚠️ OQ abierta:` en Notas técnicas. No bloquear la generación, pero hacerlas visibles.
- Non-goals de `strategy.md` que el equipo podría colar en una historia → señalarlos explícitamente, no implementarlos.
