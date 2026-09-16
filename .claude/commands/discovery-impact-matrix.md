# Skill: discovery-impact-matrix (Feature/Effort-Impact Matrix)

**Your goal:** converge a batch of already-voiced ideas into a rough priority order. This is
the "hacemos paralelos y ya" of prioritization; the fastest, lowest-ceremony tool in the kit.
It generates no new ideas; it only sorts ones that already exist.

## Where it fits

Stage 7; see [`briefings/_ciclo-preventa.md`](../../briefings/_ciclo-preventa.md) § Discovery
and [`briefings/_kit-discovery.md`](../../briefings/_kit-discovery.md). Typically the **closing**
step of a discovery batch; run it after
[`discovery-journey-map`](./discovery-journey-map.md), [`discovery-impact-map`](./discovery-impact-map.md),
or any interview-based session has already produced a list of candidate ideas.

## When to use it

A handful of ideas (roughly 5-15) already articulated out loud, and the room just needs to agree
on rough sequencing before moving to a heavier prioritization tool or straight into
[`/prd`](./prd.md). Past ~15-20 items the 2×2 gets noisy and subjective; that's the signal to
use a scored method (RICE/ICE) instead; this kit doesn't include one yet (see
`briefings/_kit-discovery.md` § Fuera de este kit).

## Input

- The candidate list itself; pull directly from whatever prior session produced it (journey-map
  opportunities, impact-map deliverables, raw interview asks). Don't regenerate the list from
  scratch in this session; that's a different exercise.

## How you facilitate it

1. Draw the 2×2: **Effort** (low→high) on one axis, **Impact** (low→high) on the other.
2. Place every candidate idea as its own sticky. Placement is a group estimate, not a single
   person's call; if the room disagrees sharply on where something lands, that disagreement is
   itself useful information, not noise to average away.
3. Read the four quadrants:
   - **High impact / low effort**, quick wins, do these first.
   - **High impact / high effort**, big bets, worth planning deliberately, not squeezed in.
   - **Low impact / low effort**, fill-ins, do only if there's slack.
   - **Low impact / high effort**, questionable, name explicitly why it's still on the list if
     it stays.
4. Close by asking the room to point at the quadrant boundary they'd be least comfortable
   defending later; that's usually where the real disagreement about impact or effort is
   hiding, not resolved by the exercise itself.

## Tool

Primary: **Miro** (2×2 board, one sticky per idea) for a live workshop, or a **Doc** with a
simple table when it's just the internal team converging without the client in the room.

## Output & where it lands

Board/doc reference + retrieved-at timestamp + the final quadrant placement of every idea →
`source/meetings/YYYY-MM-DD-<client>-impact-matrix.md` per `CLAUDE.md` § Source preservation
fallback rule. Synthesis (ranked list by quadrant, with any placement disagreements named) →
`ingestion/meetings/YYYY-MM-DD-<client>-impact-matrix.md`.

Route per § Canonical ownership: the resulting priority order feeds directly into `/prd`'s
scope-by-capability section or `/backloguer`'s slicing; name that handoff explicitly in the
synthesis. This exercise doesn't itself generate `knowledge/` or `hypotheses/` entries; it only
orders what already exists.

## Quality criteria

✅ Candidate list pulled from a prior session's output, not regenerated from scratch here
✅ Placement is a group estimate; sharp disagreements on placement are named, not averaged away
✅ All four quadrants used and read aloud, not just "do the quick wins"
✅ Anything in low-impact/high-effort that stays on the list has an explicit reason recorded
✅ Output explicitly handed off to `/prd` or `/backloguer`, not left as a standalone artifact
✅ Not used past ~15-20 items; flagged for a scored method instead when the list is longer
