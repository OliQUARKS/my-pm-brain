# Skill: discovery-service-blueprint (Service Blueprint)

**Your goal:** map what happens *behind* the user's journey (the systems, people, and handoffs
on the business's side) when the real problem is operational, not just interface. This is the
"backstage" version of a journey map.

## Where it fits

Stage 7; see [`briefings/_ciclo-preventa.md`](../../briefings/_ciclo-preventa.md) § Discovery
and [`briefings/_kit-discovery.md`](../../briefings/_kit-discovery.md). Run after
[`discovery-journey-map`](./discovery-journey-map.md) when the map's pain points keep tracing
back to something happening inside the business, not on the user-facing surface. Complements
[`discovery-event-storming`](./discovery-event-storming.md) for complex-domain clients: the
blueprint maps the *current* operational process, event storming models the *domain logic*
underneath it; run the blueprint first if the client can't yet articulate their process end
to end.

## When to use it

Manual processes, multiple internal handoffs, legacy systems nobody fully documented; a law
firm moving paper files between paralegal/associate/partner, a credit desk routing approvals
through multiple systems. If the problem is purely "the screen is confusing" with no backstage
complexity, this is overkill; a journey map alone is enough.

## Input

- Journey-map output for the same process, if one exists; the blueprint extends it downward.
- Whoever actually performs the backstage steps in the room, not just their manager describing
  it secondhand; managers narrate the documented process, staff narrate the real one.

## How you facilitate it

Map the **current state (as-is) first**, always; never jump to to-be before as-is is nailed
down; the two get confused otherwise and the redesign inherits invisible assumptions.

Four horizontal lines, top to bottom:

1. **Customer actions**, same row as the top of a journey map, kept for reference.
2. (*line of interaction*)
3. **Onstage (frontstage) employee actions**, what staff do that the customer can see/hear.
4. (*line of visibility*)
5. **Backstage employee actions**, what staff do that the customer never sees.
6. (*line of internal interaction*)
7. **Support processes**, systems, other departments, external vendors that make the backstage
   actions possible.

At each line crossing, ask: **where does this fail today?** (a handoff that drops the ball, a
system that doesn't talk to another, a step that only one person knows how to do). Mark every
failure point explicitly; that list is the actual deliverable, more than the diagram itself.

## Tool

Primary: **Miro** for a live collaborative session, or **Excalidraw** when the client wants an
offline file they can keep and annotate later without a Miro seat; this repo already has
precedent for Excalidraw process diagrams (see `perc-flujos-sprint4.excalidraw`). Either way:
four horizontal swimlanes with the three lines drawn as visible dividers, not implied.

## Output & where it lands

Board/diagram reference (URL, or the `.excalidraw` file path) + retrieved-at timestamp +
description of all four lanes and every marked failure point →
`source/meetings/YYYY-MM-DD-<client>-service-blueprint.md` per `CLAUDE.md` § Source
preservation fallback rule (or, if Excalidraw, the file itself is the source; copy it into
`source/meetings/` alongside a short markdown pointer). Synthesis, with failure points ranked by
how often they were mentioned as painful → `ingestion/meetings/YYYY-MM-DD-<client>-service-blueprint.md`.

Route per § Canonical ownership: operational failure points that are decision-relevant or
recurring → the relevant `knowledge/product/features/<slug>.md`; if a failure point implicates a
specific stakeholder's process ownership → note it on their `stakeholders/<slug>.md`.

## Quality criteria

✅ As-is mapped and validated before any to-be discussion starts
✅ Staff who actually perform backstage steps were in the room, not just their manager
✅ All four lanes present, three lines drawn and used to locate failures, not decorative
✅ Every line-crossing failure point named explicitly, ranked, not left implicit in the diagram
✅ Excalidraw file (if used) copied into `source/meetings/`, not left as a loose repo file
