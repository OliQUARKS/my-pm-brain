# Skill: discovery-empathy-map (Empathy Mapping)

**Your goal:** a light, fast way to get a room full of stakeholders thinking about the user as
a person before diving into process detail. Lighter than a journey map; use it as the
icebreaker, not the main event.

## Where it fits

Stage 7; see [`briefings/_ciclo-preventa.md`](../../briefings/_ciclo-preventa.md) § Discovery
and [`briefings/_kit-discovery.md`](../../briefings/_kit-discovery.md). Typically runs right
before [`discovery-journey-map`](./discovery-journey-map.md) in the same session; the empathy
map warms the room up, the journey map does the real work.

## When to use it

Stakeholders who've never done a UX exercise before, in a half-day workshop where you need to
break the ice fast (20-30 minutes) before something heavier. Skip it entirely with a client
team that's already product-fluent; it'll read as filler to them.

## Input

- Same evidence base as the journey map: prior interviews, tickets, or direct quotes. If none
  exists yet, this can still run as a *hypothesis-generating* exercise, but every quadrant entry
  must then be labeled as assumption, not observation; see Quality criteria.

## How you facilitate it

1. Draw the four quadrants around a center circle labeled with the persona/segment name:
   - **Says**, direct quotes, verbatim where you have them.
   - **Thinks**, what they're likely thinking but wouldn't necessarily say out loud.
   - **Does**, observable actions.
   - **Feels**, the emotional state, named specifically (not just "frustrated"; frustrated
     about what, exactly).
2. Optional fifth/sixth quadrants, **Pains** and **Gains**, add them when the room is moving
   fast and wants to jump straight to friction points and desired outcomes.
3. One persona per map. If the room starts arguing about two different users, that's the signal
   to split into two maps, not to merge into one contradictory one.
4. Tag each sticky with its source: a real quote gets attributed, an assumption gets flagged
   "supuesto" right on the sticky; don't let assumptions blend into the same visual weight as
   evidence.

## Tool

Primary: **Miro**, four-quadrant template (`board_create` + empathy-map format). Two sticky
colors: one for evidence-backed entries, one for assumptions, so the source distinction survives
a screenshot or export.

## Output & where it lands

Board URL + retrieved-at timestamp + description of all quadrants, with the evidence/assumption
tag preserved per sticky → `source/meetings/YYYY-MM-DD-<client>-empathy-map-<segment>.md` per
`CLAUDE.md` § Source preservation fallback rule. Synthesis → `ingestion/meetings/YYYY-MM-DD-<client>-empathy-map-<segment>.md`,
explicitly separating what's observation from what's interpretation per `CLAUDE.md` § Knowledge
hygiene.

This is a warm-up exercise, not itself evidence strong enough to promote to `knowledge/` on its
own; its value is in what it hands off to the journey map or the next interview round, not as
an independent Evidence row.

## Quality criteria

✅ One persona per map, split into two maps if the room disagrees on who's being mapped
✅ Every sticky tagged evidence vs. assumption; no unmarked blend
✅ "Feels" entries are specific emotions tied to a cause, not generic labels
✅ Run as a 20-30 minute warm-up, not stretched into the session's main deliverable
✅ Not promoted to `knowledge/` as standalone evidence; feeds the next, heavier exercise instead
