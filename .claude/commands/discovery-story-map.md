# Skill: discovery-story-map (User Story Mapping, discovery-stage scoping)

**Your goal:** turn a validated problem into a visual, sequenced backbone of user activities,
each column probed for needs, biases, expectations, blockers, risks, priority/urgency,
versioning, dependencies, and required stakeholders; *before* any epic or story is written to
the bone. This skill prepares the board and the live dynamic; it does not itself run the
session (that happens with the client) and it never writes descriptions or acceptance criteria.

**Scope boundary, read this before running it:** this skill stays at **title level**
(backbone activities, epic/feature column titles, candidate story titles underneath each column).
It never writes a story description, an acceptance criterion, a scenario, or a Gherkin line;
that's the backloguer process (`/backloguer`), and it runs **after** `/prd` closes
the discovery, at the start of the *development* cycle, not during discovery. If this skill's
output starts reading like a backlog, stop and hand it to `/prd` instead of going deeper.

## Where it fits

Stage 7; see [`briefings/_ciclo-preventa.md`](../../briefings/_ciclo-preventa.md) § Discovery
and [`briefings/_kit-discovery.md`](../../briefings/_kit-discovery.md).

**Handoff chain, this skill only feeds the next link, never skips ahead:**
`discovery-story-map` (this skill, live session + ingestion) → [`/prd`](./prd.md) (consolidates
everything the discovery produced, closes the stage) → *development cycle starts* →
[`/backloguer`](./backloguer.md) (full breakdown, Definition of Ready/Done, acceptance
criteria, scenarios). This skill's output is **never** a direct input to `/backloguer`; `/prd`
sits in between as the consolidation step, and `/backloguer` doesn't run until the discovery is
over and development begins.

## When to use it

The client (or their product counterpart) already speaks épica/historia fluently; this method
assumes that vocabulary from minute one. If they don't, run
[`discovery-journey-map`](./discovery-journey-map.md) or
[`discovery-impact-map`](./discovery-impact-map.md) instead and translate into a story map
later once there's a scoped direction.

Don't reach for this just because pre-sale (`build-context`) already sketched a rough flow;
the point of running it during paid discovery is to surface what a one-hour sales conversation
never could: real biases, blockers, risks, dependencies, and priority calls. If most of the
answers are already sitting in `build-context` or the briefing docs, this session still runs,
but its job is to **validate and go deeper on the 9 lenses below**, not to restate what's
already known.

## Input

- Validated problem statement, from `build-context`, or from earlier discovery sessions this
  engagement (journey map, JTBD, or impact map output).
- The people who'll actually use the product in the room, not just their manager narrating the
  workflow.
- Whatever's already known about the process, pulled in explicitly as the *starting* backbone to
  validate/correct in the room; not to save time skipping the exercise, but so the room's
  energy goes to what's actually unknown instead of re-narrating the obvious.

## How you facilitate it (three passes, not one)

**Pass 1 (Backbone).** The user's activities in narrative order, left to right, as they'd
describe their own process ("first I do X, then Y, then Z"). Start from what's already known
(pre-sale docs, prior discovery sessions) as a draft, and have the room correct it live; the
value is in what changes, not in redrawing what was already right.

**Pass 2 (Columns), each one passed through 9 lenses before moving to the next.** Under each
backbone activity: the epic/feature title it belongs to, and a rough list of **candidate story
titles** underneath it (title only, "As a [role], I want [action]" headline, no description, no
acceptance criteria; that detail is the backloguer's job later, not this session's). Then, for
that same column, before moving to the next one, work through:

| Lens | Sticky color | Prompt |
|---|---|---|
| Necesidad | 🟦 blue | What does the person need here to move forward (data, system, approval)? |
| Sesgo/supuesto | 🟪 purple | What are we (or the client) assuming here that hasn't actually been verified? |
| Expectativa | 🟨 yellow | What do they expect the product to do here, said or not? |
| Bloqueante | 🟥 red | What blocks this step today? |
| Riesgo | 🟧 orange | What could go wrong if this gets automated/built? |
| Prioridad/urgencia | ⚪ dot-vote 1-5 | How urgent is solving this step relative to the others? |
| Versionado | 🟩 green | Does this step change depending on case type/variant? |
| Dependencia | ⬛ gray | What system/person/third party does this step depend on? |
| Stakeholder necesario | 🟫 brown/avatar | Who else needs to be involved to decide or validate this? |

"No sabemos" is a valid answer on any lens; mark it explicitly as an open question, same
principle as every other skill in this kit; don't let the room invent an answer to fill a blank
sticky.

**Pass 3 (Walking skeleton).** Pick the thinnest version of each column that still lets the user
get through the whole backbone end to end, informed by what Pass 2 surfaced; high-risk or
heavily-dependency-laden steps don't belong in the skeleton just because they came up first.
Subsequent release rows go below it, ordered by the priority/urgency dot-votes.

Resist scope creep throughout: a step that doesn't serve the backbone activity above it gets
parked to the side, not slotted in to make someone happy in the room.

## Tool

Primary: **Miro**, backbone-and-rows template (`board_create` + a story-map format), with the
9 lenses as a collapsible sticky-note section under each column, color-coded per the table above
so the board reads without a legend. Dot-voting widget for the priority/urgency lens.

## Output & where it lands

Board URL + retrieved-at timestamp + description of the backbone, every column's lens contents,
and the walking-skeleton/release rows → `source/meetings/YYYY-MM-DD-<client>-story-map.md` per
`CLAUDE.md` § Source preservation fallback rule. Synthesis → `ingestion/meetings/YYYY-MM-DD-<client>-story-map.md`,
with two things named explicitly:
- The walking-skeleton slice, as the MVP boundary.
- Every lens finding that resolves a previously-open question (cross-reference against the
  client's `knowledge/org/<client>.md` § Open questions, if one exists, and mark which ones this
  session closed).

**Handoff:** this synthesis is input to `/prd`, and only `/prd`. Name that explicitly in the
output. Do not run `/backloguer` from this session's output; that happens later, from the PRD,
once discovery is over.

## Quality criteria

✅ Backbone reads as the user's own narrated process, not an org chart of internal teams
✅ All 9 lenses touched for every column, "no sabemos" marked explicitly where it applies; not
   silently skipped
✅ Story titles only; no description, acceptance criterion, or scenario written; if one creeps
   in, cut it and note it belongs to the backloguer stage instead
✅ Walking skeleton informed by Pass 2's risk/dependency/priority findings, not just "the easy
   step from each column"
✅ Parked/out-of-scope steps recorded, not silently dropped or silently included
✅ End users (or people who directly do the work) were in the room, not just their manager
✅ Synthesis explicitly closes out any previously-open question it resolved, cross-referenced
✅ Output routed to `/prd` only; never presented as ready for `/backloguer`
