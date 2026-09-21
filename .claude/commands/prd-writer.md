# Skill: prd-writer (prd_writer)

## 1. Role

You write a strategic, generalist PRD (problem, goals, non-goals, scope by capability, success metrics) from a problem or feature idea. You do not break down into epics or stories; `/backloguer` does that afterward.

## 2. Where in the process

Stage **2-Discovery** (see [`docs/skills-roadmap.md`](../../docs/skills-roadmap.md)). Runs on a feature or problem already in scope for the product, whether brand new or already tracked in `knowledge/product/features/`; hands off to `/backloguer` to break the PRD down into epics and stories.

## 3. Required input

- Feature name, problem, user request, or vague idea. With no argument: ask which feature/problem to address.
- `/build-context`, if this feature came out of a Quarks client engagement that ran a paid Discovery stage; it's the primary input in that case (see [`docs/skills-roadmap.md`](../../docs/skills-roadmap.md)). Not every PRD has one, an internal product idea with no client engagement won't.
- What you load before writing:
  - `knowledge/strategy.md` (global non-goals, so this PRD doesn't step on them; priorities; active feature).
  - `knowledge/product/features/<slug>.md` if it already exists (don't repeat what's documented, update instead of rewriting).
  - `hypotheses/` related to the problem (prior evidence).
  - `decisions/` related to the problem (commitments already made that bound the scope).
  - Relevant recent ingestion (interviews, meetings) touching the problem.

## 4. What it does, step by step

1. **Understand the problem.** Accept any form of input (feature name, problem statement, user request, vague idea). If `/build-context` exists for this engagement, start from it rather than from a blank page; it already carries the consolidated Discovery picture.
2. **Gather context conversationally**, without dumping all questions at once: user problem, target users, success metrics, constraints, prior art. Retrieval-first; only ask what can't be recovered from the repo or from `/build-context`.
3. **Generate the PRD** with the sections in step 6.
4. **Review and iterate**: offer to expand sections, and offer the natural next step, `/backloguer <slug>`, to break it down into epics.

## 5. What it does NOT do

- Does not break the problem down into epics or stories; that's `/backloguer`'s job.
- Does not let "Scope by capability" drill into story-by-story detail; if that's demanded, the signal belongs in `/backloguer`, not here.
- Does not override global non-goals from `knowledge/strategy.md`.
- Does not create `ingestion/`, `hypotheses/`, or `decisions/` entries; a PRD is a strategic document, not evidence or a commitment.
- Does not commit anything without operator confirmation, per the autonomy mode.

## 6. What comes out

The PRD, with these sections:
- **Context and problem** (2-3 sentences; who experiences it and how often; cost of not solving it; evidence linked to `source/`/`ingestion/`).
- **Goals** (3-5 measurable outcomes, not outputs).
- **Non-goals** (3-5 things explicitly out of scope, each with its rationale).
- **Scope by capability** (prioritized capabilities, P0/P1/P2: Must/Should/Could; stays at the capability level, never drills into story-by-story detail).
- **Success metrics** (leading and lagging, with concrete targets).
- **Open questions** (tagged with who answers, blocking vs. non-blocking).
- **Phasing and timeline** (hard deadlines, dependencies, suggested phasing).

## 7. How it comes out

- The full generated PRD, presented for review.
- Creates or updates `knowledge/product/features/<slug>.md` (canonical home for feature status per `CLAUDE.md` § Canonical ownership).

## 8. Where it goes

- `knowledge/product/features/<slug>.md`. Requires extending `knowledge/product/features/_SCHEMA.md` with two sections before the first run, if they don't exist yet: `## Non-goals` and `## Scope by capability`.
- Nothing gets committed without operator confirmation per the autonomy mode.
- Surface, at the end: the full generated PRD; what was created/updated in `knowledge/product/features/<slug>.md`; the next step ("Break this down into epics with `/backloguer <slug>`?"); and "Apply these changes? (y / edit / no)".

## 9. Example

Not applicable yet; no worked example has been captured for this skill.

## 10. Skill acceptance criteria

- Non-goals are never empty; if none surface, re-read the problem, something is out of scope.
- Scope by capability stays at the capability level; if it starts demanding story-by-story detail, that signal belongs in `/backloguer`, not here.
- Metrics are specific and measurable ("50% adoption within 30 days," not "high adoption").
- Doesn't override global non-goals from `knowledge/strategy.md`.
- Output (the PRD content itself) is 100% Latin American Spanish, consistent with the rest of `knowledge/product/features/`.
