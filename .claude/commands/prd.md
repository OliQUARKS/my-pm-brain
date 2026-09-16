# /prd

Writes a strategic, generalist PRD (problem, goals, non-goals, scope by capability, success metrics) from a problem or feature idea. Does not break down into epics or stories; `/backloguer` does that afterward.

## Input

Feature name, problem, user request, or vague idea. With no argument: asks which feature/problem to address.

## Loads

- `knowledge/strategy.md` (global non-goals, so this PRD doesn't step on them; priorities; active feature)
- `knowledge/product/features/<slug>.md` if it already exists (don't repeat what's documented, update instead of rewriting)
- `hypotheses/` related to the problem (prior evidence)
- `decisions/` related to the problem (commitments already made that bound the scope)
- Relevant recent ingestion (interviews, meetings) touching the problem

## Process

1. **Understand the problem**: accept any form of input (feature name, problem statement, user request, vague idea).
2. **Gather context conversationally**, without dumping all questions at once: user problem, target users, success metrics, constraints, prior art. Retrieval-first; only ask what can't be recovered from the repo.
3. **Generate the PRD** with the sections in § Structure.
4. **Review and iterate**: offer to expand sections, and offer the natural next step: `/backloguer <slug>` to break it down into epics.

## PRD Structure

- **Context and problem** (2-3 sentences; who experiences it and how often; cost of not solving it; evidence (link to `source/`/`ingestion/`))
- **Goals** (3-5 measurable outcomes, not outputs)
- **Non-goals** (3-5 things explicitly out of scope, each with its rationale)
- **Scope by capability** (prioritized capabilities, P0/P1/P2: Must/Should/Could. Stays at the capability level; never drills into story-by-story detail, that's `/backloguer`'s job)
- **Success metrics** (leading + lagging, with concrete targets)
- **Open questions** (tagged with who answers, blocking vs non-blocking)
- **Phasing and timeline** (hard deadlines, dependencies, suggested phasing)

## Updates

- Creates or updates `knowledge/product/features/<slug>.md` (canonical home for feature status per `CLAUDE.md § Canonical ownership`).
- Requires extending `knowledge/product/features/_SCHEMA.md` with two new sections before the first run: `## Non-goals` and `## Scope by capability`; they don't exist in the schema yet.
- Does not create `ingestion/`, `hypotheses/`, or `decisions/` entries; a PRD is a strategic document, not evidence or a commitment.

Nothing committed without operator confirmation per autonomy mode.

## Surfaces

- The full generated PRD
- What was created/updated in `knowledge/product/features/<slug>.md`
- Next step: "Break this down into epics with `/backloguer <slug>`?"
- "Apply these changes? (y / edit / no)"

## Quality criteria

- Non-goals are never empty; if none surface, re-read the problem; something is out of scope
- Scope by capability stays at the capability level; if it starts demanding story-by-story detail, that signal belongs in `/backloguer`, not here
- Metrics are specific and measurable ("50% adoption within 30 days", not "high adoption")
- Doesn't override global non-goals from `knowledge/strategy.md`
