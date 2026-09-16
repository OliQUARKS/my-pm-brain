# Skill: discovery-interview-guide (Semi-structured interviews)

**Your goal:** the base technique underneath almost everything else in this kit. When the
client "no tiene ni idea" and there's no research at all, this (and nothing else) already
unblocks most of the discovery.

## Where it fits

Stage 7; see [`briefings/_ciclo-preventa.md`](../../briefings/_ciclo-preventa.md) § Discovery
and [`briefings/_kit-discovery.md`](../../briefings/_kit-discovery.md). Feeds almost every other
skill in the kit: [`discovery-journey-map`](./discovery-journey-map.md) and
[`discovery-empathy-map`](./discovery-empathy-map.md) should be built from what comes out of
this, not invented cold.

## When to use it

Default first move whenever there's no existing customer research. Not a survey; this produces
depth on a handful of people, not breadth across many; if the client wants breadth, that's a
different tool (analytics, a quantitative survey) outside this kit.

## Input

- Who to talk to and why, 5-8 people covering the segments that matter, not just whoever's
  easiest to reach.
- Whatever assumptions the client's team already holds, written down *before* the interviews so
  they can be checked against what actually comes out (not rationalized after the fact).

## How you facilitate it

1. **Guide, not questionnaire.** A loose list of topics + a funnel per topic: broad open
   question first ("tell me about the last time you [did the thing]"), then narrow only if
   the broad question didn't surface it.
2. **Behavior over hypotheticals.** "¿Cuándo fue la última vez que...?" beats "¿usarías esta
   feature?" every time; people are unreliable narrators of their own future behavior, decent
   narrators of a specific recent past event.
3. **Follow the energy, not the script.** If something lights the person up or visibly
   frustrates them, go three levels deeper with "why" before moving to the next topic.
4. **No leading questions.** Never phrase a question so the "right" answer is implied by its
   wording (bad: "don't you think this is confusing?"; better: "walk me through what happened
   here").
5. **Close by asking what you didn't ask** ("is there anything about this I should have asked
   and didn't?")

## Tool

Primary: **Doc**. A live guide (topics + funnel questions) plus a running transcript per
participant. Record (with consent) rather than relying on notes alone whenever the client's
policy allows it.

## Output & where it lands

Full transcript, verbatim, → `source/interviews/YYYY-MM-DD-<client>-<participant>.md` per
`CLAUDE.md` § Source preservation; this is a real interview, preserve it whole, don't
paraphrase into the source file.

Synthesis (themes, direct quotes with attribution, contradictions between participants) →
`ingestion/interviews/YYYY-MM-DD-<client>-<participant>.md`.

Route per § Canonical ownership and § Memory promotion: a theme repeated across 2+ independent
participants → `knowledge/users/insights.md` § Active themes with one Evidence row per
supporter, same-population dissent logged under § Contradictions (audit-trail rules apply in
full (see `hypotheses/_SCHEMA.md` for the provenance vocabulary). A single participant's
observation stays in ingestion, tagged as one data point, until it recurs.

## Quality criteria

✅ No leading questions in the guide; spot-check phrasing before the session, not after
✅ At least one "tell me about the last time" per topic, not a hypothetical framing
✅ Verbatim transcript in `source/`, synthesis (never the raw transcript) in `ingestion/`
✅ Quotes attributed to source when promoted, never invented or composited across participants
✅ Contradictions between participants preserved, not flattened into "diverse feedback"
✅ Recruited participants cover the segments that matter, not just whoever answered fastest
