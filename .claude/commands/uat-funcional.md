# Skill: uat-funcional

Generate a **functional** UAT table (no endpoints, no APIs) from the Linear stories of the PERC team.

## Purpose

Create a UAT tracker focused **purely on the functional side**. It takes each Linear story, extracts **the scenarios** (acceptance criteria), and organizes them into an editable table for QA, one scenario per row.

What matters is **the scenarios**, not the narrative. Endpoints, Insomnia, Swagger, or any technical listing are never mapped.

## Input

- **Linear CSV export** (Issues → Export), the source of truth.
  - Filtered to `Team = PERc`.
  - **Subtasks are discarded**: any issue with a non-empty `Parent issue`.
- Alternatively, direct Linear reads via connector (if authenticated).

## Scenario-capture rules

### What counts as a scenario and what doesn't

- **YES:** every acceptance criterion in the story.
- **NO:** the `COMO / QUIERO / PARA` [AS A / I WANT / SO THAT] narrative (or `Como / quiero / para` in bold). Always ignored.
- **NO:** auxiliary sections. Blocks headed by the following are ignored: `Alcance` [Scope], `Fuera de alcance` [Out of scope], `Notas` [Notes], `Reglas de negocio` [Business rules], `Consideraciones` [Considerations], `Observaciones` [Remarks], `Dependencias` [Dependencies], `Aclaraciones` [Clarifications], `Supuestos` [Assumptions], `Definiciones` [Definitions].
- Markdown images (`![...](...)`) and the `NARRATIVA:` / `CRITERIOS DE ACEPTACIÓN:` [NARRATIVE: / ACCEPTANCE CRITERIA:] markers are also ignored.

### The 4 formats to recognize

Stories don't follow a single format. The parser recognizes all four:

1. **Bullet with bold Gherkin** (each bullet is a complete scenario):
   ```
   * **Dado** que ..., **cuando** ..., **entonces** ...
   ```
2. **Numbered with bold title** (the number/title opens the scenario; the Gherkin comes in the following lines):
   ```
   1. **Título del escenario**
      **Dado que** ...
      **cuando** ...
      **entonces** ...
   ```
3. **"Escenario N" [Scenario N] header** (with or without a title, Gherkin in plain text):
   ```
   Escenario 1 (Título):
   Dado que ...
   Cuando ...
   Entonces ...
   ```
4. **Listing without Gherkin** (the story lists criteria as bullets/numbering/loose lines under a `Criterios de aceptación:` [Acceptance criteria:] marker). In this case **each item in the list is a scenario** (one row).

Note: the Gherkin keywords above (`Dado que` / `Cuando` / `Entonces` / `Y`) appear in Spanish because the source Linear stories are written in Spanish; the parser matches these literal Spanish keywords in the real story text.

### Continuations and nested lists (critical, do not truncate)

- A scenario can have **`Y ...`** [And ...] lines that add conditions to the `Dado que` / `Cuando` / `Entonces`. **All of them are kept**, each on its own line within the cell.
- A scenario can contain a **list of parameters or validations** (e.g. "Y cada préstamo incluye las variables:" [And each loan includes the variables:] followed by bullets). That list gets **folded into the scenario** it belongs to; it's never cut or turned into separate scenarios.
- Indented sub-bullets get folded into their parent item.

### Numbering

- `N° Escenario` [Scenario No.] is numbered **per story**, starting at 1. If a story has 5 scenarios → rows 1..5 with the same `ID Historia` [Story ID].
- If the scenario has no explicit title → `Nombre Escenario = "Escenario N"` [Scenario Name = "Scenario N"].

### Stories without criteria

If a story has neither Gherkin nor a criteria list (technical tasks, design, infra, open questions), generate **one stub row** with whatever text is available, or `"Sin descripción / sin criterios"` [No description / no criteria]. The row still exists so QA can see it.

## Epics

The **Épica** [Epic] column = the Linear **`Project`** field (the project the story belongs to). No categories are invented. Stories with no project → `"Sin épica"` [No epic].

## CSV structure (11 columns, in this order)

| Column | Content | Filled by |
|---|---|---|
| **Épica** [Epic] | Linear project | pre-filled |
| **ID Historia** [Story ID] | `PER-XXX` | pre-filled |
| **Nombre Historia** [Story Name] | Story title | pre-filled |
| **N° Escenario** [Scenario No.] | Number within the story (1..N) | pre-filled |
| **Nombre Escenario** [Scenario Name] | Scenario title, or `Escenario N` | pre-filled |
| **Escenario (Dado/Cuando/Entonces)** [Scenario (Given/When/Then)] | Full Gherkin + `Y` [And] continuations + lists | pre-filled |
| **Validación** [Validation] | What QA checks | empty (QA) |
| **Resultado Esperado** [Expected Result] | Correct behavior | empty / suggested |
| **Resultado Obtenido** [Actual Result] | Filled in by QA during testing | empty (QA) |
| **Status** | `Pendiente` [Pending] / `Aprobado` [Approved] / `Fallido` [Failed] / `Con comentarios` [With comments] | `Pendiente` |
| **Asignación** [Assignee] | Owner | empty (QA) |

Note: the column headers and status values above are literal; the deliverable CSV itself is 100% Spanish (see § Language), since it's consumed by a Spanish-speaking QA team/client. The bracketed glosses are for this document's readers only.

## Language

**EVERYTHING IN SPANISH**, headers, scenarios (Dado que / Cuando / Entonces / Y), epic names, and scenario names. Nothing in English.

## Encoding (hard rule)

Write the CSV as **UTF-8 with BOM** (`utf-8-sig`). Without the BOM, Google Sheets breaks accented characters on import. Verify the first 3 bytes are `EF BB BF`.

## Output

- **A single CSV** at `uat-perc-flujo-credito.csv`, importable into Google Sheets without breaking accents.
- **Summary**: total stories, total scenarios, scenarios per epic, stories with no criteria (stubs).

## Success Criteria

✅ Only `PERc` stories, no subtasks (no `Parent issue`)
✅ Each row = 1 scenario; correct numbering per story
✅ All 4 formats captured; `Y` continuations and nested lists captured **in full** (no truncation)
✅ `COMO/QUIERO/PARA` narrative and auxiliary sections ignored
✅ List format → 1 scenario per item
✅ Epic = Linear project
✅ 100% Spanish [deliverable]
✅ No mention whatsoever of endpoints / APIs / Insomnia / Swagger
✅ UTF-8 BOM, accents intact in Sheets

## Iteration

The skill is versionable. If QA or the PM spot missing scenarios, badly split ones, or a new story format → the pattern gets added to the parser and the CSV gets regenerated from the Linear export.

## Implementation reference

State-machine parser: `scratchpad/parse_uat.py` (walks line by line, detects the start of a scenario, accumulates the body, folds lists, ignores narrative/auxiliary sections).
