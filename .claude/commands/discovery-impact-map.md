# Skill: discovery-impact-map (Impact Mapping)

**Your goal:** ground scope in a business goal before it turns into a feature list. The more
executive-friendly alternative to a story map; starts from "why," not "what."

## Where it fits

Stage 7; see [`briefings/_ciclo-preventa.md`](../../briefings/_ciclo-preventa.md) § Discovery
and [`briefings/_kit-discovery.md`](../../briefings/_kit-discovery.md). Can run *before*
[`discovery-story-map`](./discovery-story-map.md) and feed it; the map's deliverables become
candidate backbone activities once the story-mapping vocabulary is introduced.

## When to use it

C-level or founder audience who wants to see *why* before *what*; the room that pushes back
on "let's map user stories" with "wait, why are we building this at all." Also useful when the
sales pitch listed features but never named the business outcome those features are meant to
move.

## Input

- One measurable business goal, stated by the client; if they can't state one, that's the
  session's first job, not a blocker to starting.
- Rough list of actors who touch or are touched by that goal (don't pre-filter to "users" only;
  include internal staff, partners, regulators if relevant).

## How you facilitate it

Four columns, built left to right, each column only makes sense once the one before it exists:

1. **Why**, the single business goal, stated as a measurable outcome ("reduce onboarding
   drop-off by X%"), not an activity ("launch the new portal"). If the room offers an activity,
   push back: "and why does that matter?" until it becomes a real goal.
2. **Who**, actors who can help or hurt that goal: end users, but also staff, partners,
   regulators, competitors. For each, ask "how could they help this goal happen, and how could
   they block it?"
3. **How**, the specific behavior change desired in each actor (not a feature): "a paralegal
   uploads case docs same-day instead of end-of-week."
4. **What**, the deliverables/features that would produce that behavior change. This is the
   only column that looks like a roadmap, and it should be visibly the *last* thing decided, not
   the first.

Keep the goal singular per map. If the room has two competing goals, run two maps rather than
merging; a shared "who/how/what" tree across two unrelated goals produces false consensus.

## Tool

Primary: **Miro**, tree/mind-map layout, one central goal node branching into actors, then
impacts, then deliverables (`board_create` + a mind-map or tree template, or
`canvas_create_from_svg` for a custom tree). Keep the four column levels visually distinct
(color or vertical banding) so the "why → what" direction reads at a glance.

## Output & where it lands

Board URL + retrieved-at timestamp + description of the full tree → `source/meetings/YYYY-MM-DD-<client>-impact-map.md`
per `CLAUDE.md` § Source preservation fallback rule. Synthesis (the goal, actor list, and
prioritized deliverables) → `ingestion/meetings/YYYY-MM-DD-<client>-impact-map.md`.

Route per § Canonical ownership: the business goal, once agreed, is decision-relevant; draft it
into `decisions/YYYY-MM-DD-<slug>.md` if the client is committing to it as the discovery's
north star, or into the relevant `knowledge/product/features/<slug>.md` if it's scoped to one
feature area rather than the whole engagement.

## Quality criteria

✅ The goal is measurable and outcome-shaped, not an activity in disguise
✅ Actor list includes more than end users where relevant (staff, partners, regulators)
✅ Every "How" entry is a behavior change, not a feature restated
✅ "What" column is visibly derived last, not the starting point of the session
✅ Two competing goals produced two maps, not one merged tree
✅ Agreed goal routed to a decision record or feature file, not left stranded on the board
