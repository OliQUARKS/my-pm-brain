# /backloguer

Breaks down a PRD into epics, then epics into INVEST user stories (the full backlog, ready to
push to a tracking tool). Replaces the former separate `/epics` + `/stories` commands: one skill,
one flow, matching the backloguer process end to end.

## Where it fits

Runs after [`/prd`](./prd.md) closes discovery, at the start of the development cycle; never
fed directly by a discovery-stage skill. `discovery-story-map` stops at title-level and hands
off only to `/prd`; see [`briefings/_kit-discovery.md`](../../briefings/_kit-discovery.md).

## Input

Feature name, slug, or nothing (infers the active feature from `knowledge/strategy.md`, or the
PRD in `knowledge/product/features/<slug>.md`). Optional flags:
- `--detail <EP-XX or name>` (full epic template for that epic)
- `--stories <EP-XX>` (break that epic down into INVEST stories)
- `--detail <EP-XX-US-YY>` (full story template for that story)
- `--push` (at the end, offers to push to ClickUp; see § Closing)

## Loads

- `knowledge/strategy.md` (active feature, priorities, non-goals)
- `knowledge/product/features/<slug>.md` (problem, `## Scope by capability` (from `/prd`), OQs,
  linked decisions)
- `decisions/INDEX.md` (decisions affecting dependencies and acceptance criteria)
- `hypotheses/INDEX.md` (active hypotheses related to the feature)
- previous `ingestion/adhoc/*-epics-<slug>.md` and `*-stories-<slug>-*.md` (non-redundancy
  memory: which epics/stories were already generated for this feature)

## Process

1. **Épicas: primera pasada, solo lista.** For each candidate epic: sequential ID `EP-XX`
   (continues numbering if previous epics exist in `ingestion/adhoc/`) + title in infinitive
   form. **Functional-exclusivity criterion**: each epic solves a distinct user problem; group
   by the nature of the problem, not by where it happened to get documented in the PRD;
   something already assigned to one epic can't reappear in another. Deliver ONLY the ID +
   title list; no detail yet.
2. **Épicas: detalle (`--detail <EP-XX>`).** Before detailing a new epic, review the ones
   already detailed this session; complement, don't repeat. If a criterion or backbone activity
   is already covered elsewhere, reference it briefly ("Uses the same verification mechanism as
   EP-01") instead of restating it. Then apply the epic template below.
3. **Historias (`--stories <EP-XX>`).** Split the epic's backbone into small, independent units
   of work (INVEST). Sequential `[EP-XX]-US-YY` IDs. Non-redundancy across epics: if another
   epic in the same feature already defined a flow, this story assumes the user went through it
   and focuses on its own differential value. Every story needs at least one non-happy-path
   scenario, unless that unhappy path is big enough to be its own story.
4. **DoR/DoD: especificidad.** Definition of Ready and Definition of Done live at the epic
   level, once, covering the epic as a whole. A story's own DoR/DoD section stays empty unless
   there's a condition specific to that story that the epic's DoR/DoD doesn't already cover (a
   specific test dataset, a story-specific technical dependency); never copy the epic-wide
   DoR/DoD into a story.
5. Verify INVEST (below) before surfacing any story. Stories that don't pass get split, no
   exceptions.

## Regla de procedencia

Every epic and every story carries, in its technical-notes/dependencies section, a reference to
the artifact it came from (the PRD section, a `decisions/` file, an ingested discovery session).
An epic or story with no traceable origin can't be estimated or discussed with any confidence.

If the originating artifact wasn't itself verified against the real system (e.g. it came from a
stakeholder claim or an unconfirmed doc), say so explicitly in "Riesgos y supuestos" / "Notas
técnicas"; don't estimate an unconfirmed claim with the same confidence as a verified one.

## Slicing (epics only)

- Level 1, Minimum Viable Slice (MVS): functionality critical to validate the full flow
- Level 2, Midgame: improvements and increments, complex rules
- Level 3, Endgame: refinement, performance, accessibility

## Updates

- `ingestion/adhoc/<date>-epics-<slug>.md` (generated epics: list or detail). Source for the
  stories step and non-redundancy memory for future runs.
- `ingestion/adhoc/<date>-stories-<slug>-<epic>.md` (generated stories: ID, title, slice,
  estimated size).
- Nothing in durable layers; epics/stories are planning artifacts. The brain records the
  outcome when `/ingest` captures the sprint retro.

Nothing committed without operator confirmation per autonomy mode.

## Surfaces

**Épicas, sin `--detail`**: table `EP-XX | Title (infinitive) | Slice | Blockers | Expected KPI`.
MVS first.

**Épicas, con `--detail <EP-XX>`**, plantilla de épica:

- **Epic identification**, Title (infinitive) + ID
- **Problem framing**, Target users / User problem / Business value
- **Definition of Ready**, epic-wide preconditions: blocking decisions closed, dependencies
  available, stakeholders aligned, no backbone-blocking open OQ
- **Backbone**, left-to-right narrative flow, minimum 3 activities
- **Slicing**, MVS / Midgame / Endgame (see above)
- **High-level acceptance criteria**, Expected outcome (behavior change) + Success metrics
  (quantifiable)
- **Definition of Done**, epic-wide completion bar: every MVS story shipped and accepted,
  backbone works end-to-end, metrics instrumented, no blocking Open OQ left
- **Riesgos y supuestos**, feasibility risks + assumptions + **origen** (artifact this epic
  came from, per § Regla de procedencia)

Open OQs from the feature file that block acceptance criteria are marked
`⚠️ Open OQ: [description]`.

**Historias, sin `--detail`**: table
`[EP-XX]-US-YY | Title ("As a [role], I want [action]") | Slice | Estimated size`. MVS first.

**Historias, con `--detail <ID>`**, plantilla de historia:

- **Identification**, `USER STORY [EP-XX]-US-YY`
- **Title**, clear action
- **Narrative**, As a [role] / I want [functionality] / So that [value]
- **Definition of Ready**, story-specific only; "Inherits epic DoR (no story-specific
  preconditions)" if nothing extra applies
- **Acceptance criteria**, Given/When/Then; happy path + at least 1 unhappy path
- **Technical notes and dependencies**, other epics/stories/services referenced, `decisions/`
  constraints, `⚠️ Open OQ`, **origen** (per § Regla de procedencia)
- **Definition of Done**, story-specific only, same inheritance rule as DoR
- **Estimated size**, XS (<4h) | S (<1d) | M (<3d) | L (<1wk) | XL → split before pushing

## INVEST criteria (verify before generating a story)

- **I**ndependent: doesn't block/depend on another story in the same slice except for explicit
  dependencies
- **N**egotiable: a conversation with the team, not a contract
- **V**aluable: delivers something verifiable to the user or the system
- **E**stimable: size is assignable with the information available
- **S**mall: finishes in ≤ 3 dev days, or gets split
- **T**estable: at least 1 verifiable acceptance criterion

## Closing

Always ask: **"Push this to ClickUp, to another tool, or leave it as is?"**

- **ClickUp** → create/reuse a ClickUp List for the feature (`clickup_create_list`), a Task per
  epic (`clickup_create_task`) using the epic template as the description, and each story as a
  Task within its epic's Task/List, referencing the parent. XL stories aren't pushed; flagged
  to split first.
- **Another tool** → same content reformatted as strict plain text (no markdown, section/epic/
  story titles in UPPERCASE, hyphen lists, three line breaks between sections); ready to paste
  into Jira/Linear/GitHub Issues/a ticket description.
- **Leave it as is** → nothing further; the `ingestion/adhoc/` files are already the source.

## Quality criteria

- Each epic has exactly 1 user goal; split if it has more than one
- MVS is a single happy path with no edge cases; split the epic if there's more than one
- Endgame doesn't duplicate MVS or Midgame
- Non-goals from `strategy.md § Explicit non-goals` don't appear as epics, in Midgame, or in any
  story
- Every epic and every story cites its origin per § Regla de procedencia; no exceptions
- Unconfirmed origins are flagged in Riesgos y supuestos / Notas técnicas, not estimated at full
  confidence
- Definition of Ready is never empty at the epic level; "No blocking preconditions identified"
  if genuinely none
- Story DoR/DoD never restates the epic's; only the delta, or the inheritance line
- Unhappy paths are mandatory, at least 1 per story unless split out as its own story
- Stories that fail INVEST get split before surfacing, no exceptions
- Before detailing a new epic or story, the memory of what's already detailed for this feature
  was reviewed (non-redundancy)
