# Skill: discovery-business-model-canvas (Business Model Canvas / Lean Canvas)

## 1. Role

You facilitate getting the client's own business model onto one page, in their own words, before designing anything. Use Lean Canvas instead of the classic BMC when the client already has traction and you want to go straight at problem/solution instead of the full 9-block picture.

## 2. Where in the process

Stage **2-Discovery** (see [`docs/skills-roadmap.md`](../../docs/skills-roadmap.md)): post-sale, pre-development discovery, what [`briefings/_ciclo-preventa.md`](../../briefings/_ciclo-preventa.md) calls "etapa 7". Part of the 15-methodology discovery toolkit; see [`briefings/_kit-discovery.md`](../../briefings/_kit-discovery.md) for how this compares to the other 14 methods and how to pick a combo.

## 3. Required input

- Attendee list: needs whoever actually owns pricing/revenue decisions in the room, not just the product counterpart.
- Any existing pitch deck, one-pager, or investor materials (skip re-deriving what's already written; use the session to pressure-test it instead).

## 4. What it does, step by step

**Step 1: decide classic BMC vs. Lean Canvas.**
- **Classic BMC (9 blocks)**, when the client has no traction yet or the model spans multiple sides (e.g. marketplace): Customer Segments, Value Propositions, Channels, Customer Relationships, Revenue Streams, Key Resources, Key Activities, Key Partnerships, Cost Structure.
- **Lean Canvas (9 blocks, Ash Maurya variant)**, when the client has traction and wants problem/solution speed: Problem, Customer Segments, Unique Value Proposition, Solution, Channels, Revenue Streams, Cost Structure, Key Metrics, Unfair Advantage.

**Step 2: run the session.**
1. Fill left to right, but problem/segments first, cost/revenue last; teams that start with money anchor on a number before the problem is even agreed.
2. One sticky per idea, one idea per sticky; no paragraphs.
3. Expect "no lo sé" as a valid answer on at least 2-3 blocks. Mark those cells explicitly as open; don't let the room invent a number to fill the silence.
4. Budget 60-90 minutes total; don't let any single block eat more than 15.

**Step 3: pick the tool.**
- Primary: Miro. Create a board from the canvas template (`board_create` + `board_create_format` with the BMC/Lean Canvas layout, or `canvas_create_from_svg` if building the 9-block grid from scratch). One color per block category if running BMC, so the client can visually group front-stage (segments/value/channels) vs. back-stage (resources/activities/partners/costs) blocks during the walkthrough.
- Fallback: if the client has no Miro seat and won't create one, run it on a shared Google Doc with a 3x3 table; loses the sticky-note fluidity but keeps the structure.

## 5. What it does NOT do

- Does not run when the client already has a documented, current business model; route to [`discovery-value-proposition-canvas`](./discovery-value-proposition-canvas.md) or [`discovery-jtbd`](./discovery-jtbd.md) instead.
- Does not force a filled-in answer where the room doesn't know; "no lo sé" stays marked open, never silently invented.
- Does not start with revenue/cost blocks before problem/segments are agreed.
- Does not produce paragraph-length stickies; one idea per sticky.

## 6. What comes out

- A verbatim capture of the board (per the source preservation fallback rule): board URL, retrieved-at timestamp, and a description of what's on each block.
- A synthesis: what's solid, what's marked "no lo sé", what contradicts the sales pitch.
- Downstream routing: revenue-model or segment claims that recur or are decision-relevant go to canonical knowledge; open blocks the client couldn't fill become questions for the next session.

## 7. How it comes out

Two markdown files, following `CLAUDE.md` § Source preservation and § Canonical ownership:
- The verbatim source capture (board URL + timestamp + per-block description), never edited after creation.
- The synthesis (what's solid / open / contradictory), which can be revised.

## 8. Where it goes

- Source (verbatim): `source/meetings/YYYY-MM-DD-<client>-business-model-canvas.md`.
- Synthesis: `ingestion/meetings/YYYY-MM-DD-<client>-business-model-canvas.md`.
- Recurring or decision-relevant revenue-model/segment claims: `knowledge/market/landscape.md` or the relevant `knowledge/product/features/<slug>.md`.
- Open blocks the client couldn't fill: feed directly into the next `discovery-interview-guide` or `discovery-jtbd` session as questions to resolve.

## 9. Example

Not applicable yet; no worked example has been captured for this skill.

## 10. Skill acceptance criteria

- Problem/segments filled before revenue/cost blocks.
- Every "no lo sé" cell named explicitly, not silently invented.
- One sticky equals one idea; no paragraph-stickies.
- Whoever owns pricing/revenue was in the room, not just the product counterpart.
- Output routed as open questions to the next session, not left stranded on the board.
- Board URL and timestamp preserved even though the canvas itself lives outside the repo.
