# Skill: discovery-business-model-canvas (Business Model Canvas / Lean Canvas)

**Your goal:** get the client's own business model on one page, in their words, before designing
anything. Use Lean Canvas instead of the classic BMC when the client already has traction and
you want to go straight at problem/solution instead of the full 9-block picture.

## Where it fits

Stage 7; see [`briefings/_ciclo-preventa.md`](../../briefings/_ciclo-preventa.md) § Discovery
and [`briefings/_kit-discovery.md`](../../briefings/_kit-discovery.md) for how this compares to
the other 14 methods.

## When to use it

The client's own business model isn't clear yet (often because the sales pitch was "we want an
app that helps our customers" with no model behind it) or the project is a new line inside an
existing company (a bank launching embedded finance, a law firm launching a client portal) where
the *new* line's economics haven't been articulated separately from the parent business.

Skip it when the client already has a documented, current business model; don't make them
re-derive what they already know; go straight to [`discovery-value-proposition-canvas`](./discovery-value-proposition-canvas.md)
or [`discovery-jtbd`](./discovery-jtbd.md) instead.

## Input

- Attendee list, needs whoever actually owns pricing/revenue decisions in the room, not just
  the product counterpart.
- Any existing pitch deck, one-pager, or investor materials (skip re-deriving what's already
  written; use the session to pressure-test it instead).

## How you facilitate it

**Classic BMC (9 blocks)** (client has no traction yet, or the model spans multiple sides
(e.g. marketplace)): Customer Segments → Value Propositions → Channels → Customer Relationships
→ Revenue Streams → Key Resources → Key Activities → Key Partnerships → Cost Structure.

**Lean Canvas (9 blocks, Ash Maurya variant)** (client has traction, wants problem/solution
speed): Problem → Customer Segments → Unique Value Proposition → Solution → Channels → Revenue
Streams → Cost Structure → Key Metrics → Unfair Advantage.

Session mechanics either way:
1. Fill left-to-right, but **problem/segments first, cost/revenue last**; teams that start with
   money anchor on a number before the problem is even agreed.
2. One sticky per idea, one idea per sticky; no paragraphs.
3. "No lo sé" is a valid, expected answer on at least 2-3 blocks. Mark those cells explicitly as
   open, don't let the room invent a number to fill the silence.
4. 60-90 minutes total; don't let any single block eat more than 15.

## Tool

Primary: **Miro**. Create a board from the canvas template (`board_create` + `board_create_format`
with the BMC/Lean Canvas layout, or `canvas_create_from_svg` if building the 9-block grid from
scratch). One color per block category if running BMC, so the client can visually group
front-stage (segments/value/channels) vs. back-stage (resources/activities/partners/costs)
blocks during the walkthrough.

Fallback: if the client has no Miro seat and won't create one, run it on a shared Google Doc
with a 3×3 table; loses the sticky-note fluidity but keeps the structure.

## Output & where it lands

Capture per [`CLAUDE.md`](../../CLAUDE.md) § Source preservation fallback rule: board URL +
retrieved-at timestamp + a description of what's on each block, saved verbatim into
`source/meetings/YYYY-MM-DD-<client>-business-model-canvas.md`. Synthesis (what's solid, what's
marked "no lo sé", what contradicts the sales pitch) goes into
`ingestion/meetings/YYYY-MM-DD-<client>-business-model-canvas.md`.

Route downstream per `CLAUDE.md` § Canonical ownership: revenue-model or segment claims that
recur or are decision-relevant → `knowledge/market/landscape.md` or the relevant
`knowledge/product/features/<slug>.md`; open blocks the client couldn't fill → feed directly
into the next `discovery-interview-guide` or `discovery-jtbd` session as questions to resolve.

## Quality criteria

✅ Problem/segments filled before revenue/cost blocks
✅ Every "no lo sé" cell named explicitly, not silently invented
✅ One sticky = one idea, no paragraph-stickies
✅ Whoever owns pricing/revenue was in the room, not just the product counterpart
✅ Output routed as open questions to the next session, not left stranded on the board
✅ Board URL + timestamp preserved even though the canvas itself lives outside the repo
