# Skill: uat-funcional

Generar tabla de UAT **funcional** (sin endpoints, sin APIs) desde las historias de Linear del equipo PERC.

## Propósito

Crear un rastreador de UAT enfocado **solo en lo funcional**. Toma cada historia de Linear, extrae **los escenarios** (criterios de aceptación) y los organiza en una tabla editable para QA — un escenario por fila.

Lo que importa son **los escenarios**, no la narrativa. Nunca se mapean endpoints, Insomnia, Swagger ni ningún listado técnico.

## Entrada

- **Export CSV de Linear** (Issues → Export) — es la fuente autoritativa.
  - Se filtra por `Team = PERc`.
  - Se descartan las **subtareas**: cualquier issue con `Parent issue` no vacío.
- Alternativamente, lectura directa de Linear vía conector (si está autenticado).

## Reglas de captura de escenarios

### Qué es un escenario y qué NO

- **SÍ:** cada criterio de aceptación de la historia.
- **NO:** la narrativa `COMO / QUIERO / PARA` (o `Como / quiero / para` en negrita). Se ignora siempre.
- **NO:** secciones auxiliares. Se ignoran los bloques encabezados por: `Alcance`, `Fuera de alcance`, `Notas`, `Reglas de negocio`, `Consideraciones`, `Observaciones`, `Dependencias`, `Aclaraciones`, `Supuestos`, `Definiciones`.
- Se ignoran también las imágenes markdown (`![...](...)`) y los marcadores `NARRATIVA:` / `CRITERIOS DE ACEPTACIÓN:`.

### Los 4 formatos que hay que reconocer

Las historias no siguen un único formato. El parser reconoce los cuatro:

1. **Viñeta con Gherkin en negrita** — cada viñeta es un escenario completo:
   ```
   * **Dado** que ..., **cuando** ..., **entonces** ...
   ```
2. **Numerado con título en negrita** — el número/título abre el escenario; el Gherkin viene en líneas siguientes:
   ```
   1. **Título del escenario**
      **Dado que** ...
      **cuando** ...
      **entonces** ...
   ```
3. **Encabezado "Escenario N"** — con o sin título, Gherkin en texto plano:
   ```
   Escenario 1 — Título:
   Dado que ...
   Cuando ...
   Entonces ...
   ```
4. **Listado sin Gherkin** — la historia lista criterios en viñetas / numeración / líneas sueltas bajo un marcador `Criterios de aceptación:`. Entonces **cada ítem del listado es un escenario** (una fila).

### Continuaciones y listas anidadas (crítico — no truncar)

- Un escenario puede tener líneas **`Y ...`** que agregan condiciones al `Dado que` / `Cuando` / `Entonces`. **Se conservan todas**, cada una en su línea dentro de la celda.
- Un escenario puede contener un **listado de parámetros o validaciones** (p. ej. "Y cada préstamo incluye las variables:" seguido de viñetas). Ese listado se **pliega dentro del escenario** al que pertenece — no se corta ni se convierte en escenarios separados.
- Sub-viñetas indentadas se pliegan dentro de su ítem padre.

### Numeración

- `N° Escenario` se numera **por historia**, empezando en 1. Si una historia tiene 5 escenarios → filas 1..5 con el mismo `ID Historia`.
- Si el escenario no tiene título explícito → `Nombre Escenario = "Escenario N"`.

### Historias sin criterios

Si una historia no tiene ni Gherkin ni listado de criterios (tareas técnicas, diseño, infra, preguntas), se genera **una fila stub** con el texto disponible o `"Sin descripción / sin criterios"`. La fila existe igual para que QA la vea.

## Épicas

La columna **Épica** = el campo **`Project`** de Linear (el proyecto al que pertenece la historia). No se inventan categorías. Historias sin proyecto → `"Sin épica"`.

## Estructura del CSV (11 columnas, en este orden)

| Columna | Contenido | Llenado |
|---|---|---|
| **Épica** | Proyecto de Linear | pre-llenado |
| **ID Historia** | `PER-XXX` | pre-llenado |
| **Nombre Historia** | Título de la historia | pre-llenado |
| **N° Escenario** | Número dentro de la historia (1..N) | pre-llenado |
| **Nombre Escenario** | Título del escenario, o `Escenario N` | pre-llenado |
| **Escenario (Dado/Cuando/Entonces)** | Gherkin completo + continuaciones `Y` + listas | pre-llenado |
| **Validación** | Qué verifica QA | vacío (QA) |
| **Resultado Esperado** | Comportamiento correcto | vacío / sugerido |
| **Resultado Obtenido** | QA llena en testing | vacío (QA) |
| **Status** | `Pendiente` / `Aprobado` / `Fallido` / `Con comentarios` | `Pendiente` |
| **Asignación** | Responsable | vacío (QA) |

## Idioma

**TODO EN ESPAÑOL** — encabezados, escenarios (Dado que / Cuando / Entonces / Y), nombres de épicas y de escenarios. Nada en inglés.

## Encoding — hard rule

Escribir el CSV en **UTF-8 con BOM** (`utf-8-sig`). Sin el BOM, Google Sheets rompe los tildes/acentos al importar. Verificar que los 3 primeros bytes sean `EF BB BF`.

## Salida

- **CSV único** en `uat-perc-flujo-credito.csv`, importable a Google Sheets sin romper tildes.
- **Resumen**: total de historias, total de escenarios, escenarios por épica, historias sin criterios (stubs).

## Success Criteria

✅ Solo historias `PERc`, sin subtareas (sin `Parent issue`)
✅ Cada fila = 1 escenario; numeración correcta por historia
✅ Los 4 formatos capturados; continuaciones `Y` y listas anidadas **completas** (sin truncar)
✅ Narrativa `COMO/QUIERO/PARA` y secciones auxiliares ignoradas
✅ Formato listado → 1 escenario por ítem
✅ Épica = proyecto de Linear
✅ 100% español
✅ Sin ninguna mención a endpoints / APIs / Insomnia / Swagger
✅ UTF-8 BOM — tildes intactos en Sheets

## Iteración

El skill es versionable. Si QA o PM detectan escenarios faltantes, mal partidos o un formato nuevo de historia → se agrega el patrón al parser y se re-genera el CSV desde el export de Linear.

## Referencia de implementación

Parser de máquina de estados: `scratchpad/parse_uat.py` (recorre línea por línea, detecta inicio de escenario, acumula cuerpo, pliega listas, ignora narrativa/secciones auxiliares).
