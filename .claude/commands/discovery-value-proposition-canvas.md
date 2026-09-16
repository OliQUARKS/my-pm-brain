# Skill: discovery-value-proposition-canvas (Value Proposition Canvas)

**Your goal:** force precision between what the client thinks they're offering and what the
customer actually needs. Use it when the sales pitch confuses features with value; the
symptom is the client describing the *product* fluently and the *customer's problem* vaguely.

## Where it fits

Stage 7; see [`briefings/_ciclo-preventa.md`](../../briefings/_ciclo-preventa.md) § Discovery
and [`briefings/_kit-discovery.md`](../../briefings/_kit-discovery.md).

## When to use it

Right after or alongside [`discovery-business-model-canvas`](./discovery-business-model-canvas.md)
; it zooms into that canvas's Customer Segments + Value Propositions blocks. Reach for it
specifically when the pitch was vague ("queremos una app que ayude a nuestros clientes") and you
need to make the room say, concretely, which pain gets relieved and which gain gets created.

Don't run it cold, without any customer evidence; the customer profile side (jobs/pains/gains)
should be filled from real interviews or support tickets where they exist, not invented in the
room. If zero customer evidence exists yet, run [`discovery-interview-guide`](./discovery-interview-guide.md)
or [`discovery-jtbd`](./discovery-jtbd.md) first and come back to this.

## Input

- Business Model Canvas output if one was run; this skill zooms into two of its blocks.
- Any existing customer interviews, support tickets, or reviews (real quotes, not paraphrases).

## How you facilitate it

Two circles, filled in this order:

1. **Customer Profile (right circle), from evidence, not guesses:**
   - **Jobs**, what the customer is trying to get done (functional, social, emotional).
   - **Pains**, bad outcomes, risks, obstacles before/during/after the job.
   - **Gains**, outcomes and benefits the customer wants.
2. **Value Map (left circle), only after the profile is filled:**
   - **Products & Services**, what's actually offered.
   - **Pain Relievers**, how each offering kills a specific pain.
   - **Gain Creators**, how each offering produces a specific gain.
3. **Fit check.** Draw a line from each Pain Reliever/Gain Creator to the Pain/Gain it addresses.
   Anything on the Value Map with no line to a real Pain/Gain is a feature looking for a problem;
   flag it, don't quietly build it in.

## Tool

Primary: **Miro**, two-circle template (`board_create` from a VPC template, or
`canvas_create_from_svg` for the circle-plus-grid layout). Color-code the fit-check lines so
unmatched value-map items are visually obvious at the end of the session.

## Output & where it lands

Board URL + retrieved-at timestamp + description of both circles and the fit-check lines →
`source/meetings/YYYY-MM-DD-<client>-value-proposition-canvas.md` (verbatim, per `CLAUDE.md`
§ Source preservation fallback rule). Synthesis, with unmatched-feature flags called out
explicitly → `ingestion/meetings/YYYY-MM-DD-<client>-value-proposition-canvas.md`.

Route per § Canonical ownership: confirmed jobs/pains/gains that recur across sources →
`knowledge/users/insights.md` § Active themes (with the source link as the Evidence row);
unmatched value-map items → open question on the relevant `knowledge/product/features/<slug>.md`,
not silently dropped.

## Quality criteria

✅ Customer Profile filled from real evidence (interview/ticket/quote), labeled as such; not
invented in the room
✅ Value Map filled only after the Profile, not in parallel
✅ Every Pain Reliever/Gain Creator traced to a specific Pain/Gain, or flagged as unmatched
✅ At least one unmatched item surfaced explicitly if one exists; don't let the room round it
into "well it's still useful"
✅ Jobs/pains/gains tagged with their source when promoted to `insights.md`
