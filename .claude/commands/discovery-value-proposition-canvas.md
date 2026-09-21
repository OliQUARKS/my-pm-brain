# Skill: discovery-value-proposition-canvas (Value Proposition Canvas)

## 1. Role

You force precision between what the client thinks they're offering and what the customer actually needs. Use it when the sales pitch confuses features with value; the symptom is the client describing the product fluently and the customer's problem vaguely.

## 2. Where in the process

Stage **2-Discovery** (see [`docs/skills-roadmap.md`](../../docs/skills-roadmap.md)): post-sale, pre-development discovery, what [`briefings/_ciclo-preventa.md`](../../briefings/_ciclo-preventa.md) calls "etapa 7". Part of the 15-methodology discovery toolkit; see [`briefings/_kit-discovery.md`](../../briefings/_kit-discovery.md).

## 3. Required input

- Business Model Canvas output, if one was run; this skill zooms into its Customer Segments and Value Propositions blocks.
- Any existing customer interviews, support tickets, or reviews (real quotes, not paraphrases).

## 4. What it does, step by step

**When to use it:** right after or alongside [`discovery-business-model-canvas`](./discovery-business-model-canvas.md). Reach for it specifically when the pitch was vague ("queremos una app que ayude a nuestros clientes") and you need to make the room say, concretely, which pain gets relieved and which gain gets created.

**Don't run it cold.** The customer profile side (jobs/pains/gains) should be filled from real interviews or support tickets where they exist, not invented in the room. If zero customer evidence exists yet, run [`discovery-interview-guide`](./discovery-interview-guide.md) or [`discovery-jtbd`](./discovery-jtbd.md) first and come back to this.

**Facilitate two circles, filled in this order:**

1. **Customer Profile (right circle), from evidence, not guesses:**
   - **Jobs**: what the customer is trying to get done (functional, social, emotional).
   - **Pains**: bad outcomes, risks, obstacles before/during/after the job.
   - **Gains**: outcomes and benefits the customer wants.
2. **Value Map (left circle), only after the profile is filled:**
   - **Products & Services**: what's actually offered.
   - **Pain Relievers**: how each offering kills a specific pain.
   - **Gain Creators**: how each offering produces a specific gain.
3. **Fit check.** Draw a line from each Pain Reliever/Gain Creator to the Pain/Gain it addresses. Anything on the Value Map with no line to a real Pain/Gain is a feature looking for a problem; flag it, don't quietly build it in.

**Tool:** Primary is Miro, two-circle template (`board_create` from a VPC template, or `canvas_create_from_svg` for the circle-plus-grid layout). Color-code the fit-check lines so unmatched value-map items are visually obvious at the end of the session.

## 5. What it does NOT do

- Does not run without real customer evidence; if none exists yet, redirect to `discovery-interview-guide` or `discovery-jtbd` first.
- Does not fill the Value Map in parallel with or before the Customer Profile.
- Does not let an unmatched Pain Reliever/Gain Creator get rounded into "well it's still useful"; every unmatched item gets flagged explicitly.

## 6. What comes out

- A verbatim capture of the board: both circles, plus the fit-check lines.
- A synthesis that explicitly calls out unmatched-feature flags.
- Downstream routing: confirmed jobs/pains/gains that recur across sources, and unmatched value-map items as open questions.

## 7. How it comes out

Two markdown files, following `CLAUDE.md` § Source preservation and § Canonical ownership:
- The verbatim source capture (board URL + retrieved-at timestamp + description of both circles and the fit-check lines), never edited after creation.
- The synthesis, with unmatched-feature flags called out explicitly.

## 8. Where it goes

- Source (verbatim): `source/meetings/YYYY-MM-DD-<client>-value-proposition-canvas.md`.
- Synthesis: `ingestion/meetings/YYYY-MM-DD-<client>-value-proposition-canvas.md`.
- Confirmed jobs/pains/gains that recur across sources: `knowledge/users/insights.md` § Active themes, with the source link as the Evidence row.
- Unmatched value-map items: an open question on the relevant `knowledge/product/features/<slug>.md`, never silently dropped.

## 9. Example

Not applicable yet; no worked example has been captured for this skill.

## 10. Skill acceptance criteria

- Customer Profile filled from real evidence (interview/ticket/quote), labeled as such; not invented in the room.
- Value Map filled only after the Profile, not in parallel.
- Every Pain Reliever/Gain Creator traced to a specific Pain/Gain, or flagged as unmatched.
- At least one unmatched item surfaced explicitly if one exists; the room doesn't round it into "well it's still useful."
- Jobs/pains/gains tagged with their source when promoted to `insights.md`.
