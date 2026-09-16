# Skill: discovery-event-storming (Event Storming)

**Your goal:** map a complex business domain (many rules, many actors, many exceptions) by
talking in the business's own verbs, not in data models or screens. The right tool when the
domain itself (not the interface) is where the real complexity lives, like a fintech credit
flow or a law firm's case-management rules.

## Where it fits

Stage 7; see [`briefings/_ciclo-preventa.md`](../../briefings/_ciclo-preventa.md) § Discovery
and [`briefings/_kit-discovery.md`](../../briefings/_kit-discovery.md). Complements
[`discovery-service-blueprint`](./discovery-service-blueprint.md): the blueprint maps the
current operational process end to end, this skill models the *domain events and rules* inside
it. Run the blueprint first if the client can't yet narrate their process start to finish;
run this first if the process is already well understood but the *rules* are the unknown.

## When to use it

Complex domain, many business rules, multiple regulators or exception paths; the PERC credit
flow and RyD Abogados' legal-matter rules are exactly this shape. Works even with non-technical
domain experts in the room, because the vocabulary is business verbs ("case gets filed",
"client signs retainer"), not technical terms. Overkill for a simple, mostly-linear process;
use a journey map or service blueprint instead.

## How you facilitate it

Three passes, run as separate sessions if time allows (don't compress all three into one
sitting for a genuinely complex domain):

1. **Big Picture**, orange stickies, one **domain event** each, in past tense ("Case Filed",
   "Payment Received", "Document Rejected"), placed in rough chronological order on a long wall
   or board. No structure yet beyond time order. Get every domain expert in the room contributing
   events in parallel; silence is a red flag, not efficiency.
2. **Process Modeling**, layer on:
   - **Commands** (blue), the action that triggers each event ("File Case").
   - **Actors** (yellow, small), who issues the command.
   - **Policies** (purple), automatic reactions ("When Payment Received, then Invoice Closed").
   - **Read models** (green), what information an actor needs to decide.
   - **Hotspots** (pink/hot color), mark disagreement or unresolved questions right where they
     surface; do not stop to resolve them in the moment, just mark and move on.
3. **Software Design** (optional third pass, only if this feeds actual system design), group
   events into aggregates and bounded contexts. Skip this pass if the discovery's output is a
   scope document, not an architecture; don't let the session drift into premature technical
   design.

Mechanics that matter regardless of pass: **explore before agreeing**; get the wall roughly
full before debating any single sticky's wording or position; arguing over one event too early
kills the room's momentum on the rest.

## Tool

Primary: **Miro**, unlimited-canvas sticky-note board is the natural fit (`board_create`,
sticky-note widgets, color-coded per element type above). **Excalidraw** as the offline
alternative when the domain experts prefer a file they can keep locally; this repo already has
Excalidraw precedent for flow diagrams (`perc-flujos-sprint4.excalidraw`,
`perc-historias-mantovana-sprint4.excalidraw`).

## Output & where it lands

Board/diagram reference + retrieved-at timestamp + description of the full event timeline
(events, commands, actors, policies, hotspots) → `source/meetings/YYYY-MM-DD-<client>-event-storming.md`
per `CLAUDE.md` § Source preservation fallback rule (or copy the `.excalidraw` file itself into
`source/meetings/` with a markdown pointer). Synthesis, with every hotspot listed as an
explicit open question → `ingestion/meetings/YYYY-MM-DD-<client>-event-storming.md`.

Route per § Canonical ownership: confirmed domain rules and policies that are decision-relevant
→ the relevant `knowledge/product/features/<slug>.md`; unresolved hotspots → feed directly into
the next discovery session's agenda, named individually, not summarized away.

## Quality criteria

✅ Big Picture pass done in past-tense domain events, not tasks or screens
✅ All present domain experts contributed events; no single voice dominating the wall
✅ Every hotspot marked in the moment and listed individually in the synthesis, not resolved
   prematurely or dropped
✅ Software-design pass only run when the output actually feeds system design, not by default
✅ Commands/actors/policies color-coded consistently so the board reads without a legend
✅ Excalidraw file (if used) copied into `source/meetings/`, not left as a loose repo file
