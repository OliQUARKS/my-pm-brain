# /stories

Descompone una épica en historias de usuario INVEST usando el proceso backloguer. Sin flags: lista de historias. Con `--detail <ID historia>`: plantilla completa. Con `--push`: al terminar, ofrece subir a ClickUp.

## Input

ID de épica (`EP-XX`, desde contexto de `/epics` o como argumento) o nombre de épica. Flags opcionales:
- `--detail <EP-XX-US-YY>` — plantilla completa para esa historia
- `--push` — al terminar, ofrece subir a ClickUp (ver § Cierre)

## Loads

- `ingestion/adhoc/<date>-epics-<slug>.md` — output del último `/epics` para la feature (backbone y detalle de la épica padre)
- `knowledge/product/features/<slug>.md` — OQs abiertas que afectan criterios de aceptación
- `decisions/` relacionadas con la épica — para notas técnicas y restricciones
- `knowledge/strategy.md` — para verificar que ninguna historia implementa un non-goal
- `ingestion/adhoc/*-stories-<slug>-*.md` previos — para el chequeo de no-redundancia entre épicas de la misma feature

## Proceso (backloguer)

1. **Desglose**: partir el backbone de la épica en unidades de trabajo pequeñas. IDs `[EP-XX]-US-YY` secuenciales dentro de la épica.
2. **No-redundancia entre épicas**: si otra épica de la misma feature ya definió un flujo (ej. "sistema de login" en EP-01), las historias de esta épica no lo vuelven a detallar — asumen que el usuario ya pasó por ese flujo, y enfocan el diferencial de valor del incremento propio.
3. **Escenarios**: cada historia debe tener al menos un escenario no-happy-path, salvo que ese unhappy path ya esté tratado como historia individual aparte (si es lo suficientemente grande, se separa).
4. Verificar INVEST (ver checklist abajo) antes de surfacear cualquier historia.

## Updates

- `ingestion/adhoc/<date>-stories-<slug>-<epic>.md` — log de historias generadas: ID, título, slice, tamaño estimado.
- Nada en durable layers — mismo principio que `/epics`.

Nothing committed without operator confirmation per autonomy mode.

## Surfaces

**Sin `--detail`**: tabla `[EP-XX]-US-YY | Título ("Como [rol], quiero [acción]") | Slice | Tamaño estimado`. Ordenado: MVS primero.

**Con `--detail <ID>`**: plantilla completa (formato backloguer):

- **Identificación** — `HISTORIA DE USUARIO [EP-XX]-US-YY`
- **Título** — acción clara
- **Narrativa** — Como [rol de usuario] / Quiero [funcionalidad] / Para [valor o beneficio]
- **Criterios de aceptación** — escenarios en Given/When/Then; happy path + al menos 1 unhappy path
- **Notas técnicas y dependencias** — referencia a otras épicas/historias/servicios, restricciones de `decisions/`, OQs marcadas `⚠️ OQ abierta: [descripción]`
- **Tamaño estimado** — XS (<4h) | S (<1d) | M (<3d) | L (<1sem) | XL → partir antes de pushear

## Cierre

Al terminar de surfacear (con o sin `--push`), preguntar siempre: **"¿Subís esto a ClickUp, a otra herramienta, o queda como está?"**

- **ClickUp** → crear cada historia como Tarea dentro de la Tarea/Lista correspondiente a su épica en ClickUp (`clickup_create_task`, referenciando la tarea padre de la épica). Historias XL no se pushean — se señalan al PM para partir primero.
- **Otra herramienta** → ofrecer el mismo contenido en texto plano estricto (formato backloguer: sin markdown, títulos en MAYÚSCULAS, guiones, tres saltos de línea entre secciones).
- **Queda como está** → no se hace nada más; el archivo en `ingestion/adhoc` ya es la fuente.

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
- No-redundancia (backloguer): si el flujo ya fue cubierto por otra épica, referenciar en vez de repetir.
