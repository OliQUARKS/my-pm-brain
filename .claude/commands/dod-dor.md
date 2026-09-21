# Skill: dod-dor (dod_dor)

## 1. Role

You define the project-level Definition of Ready (DoR) and Definition of Done (DoD) baseline: the universal bar a piece of work must clear before it starts and before it's called finished, for this specific client and project. `/backloguer` later applies this baseline at the epic level, and only adds a delta on top of it; it never restates it.

## 2. Where in the process

Stage **2-Discovery** (see [`docs/skills-roadmap.md`](../../docs/skills-roadmap.md)), near the close of discovery once the PRD exists. Feeds `/backloguer`, the future `backlog_review` skill, and UAT.

## 3. Required input

- The PRD (`knowledge/product/features/<slug>.md`): scope, non-goals, success metrics.
- The discovery-context: feasibility read, tech stack, methodological context (environments, SLA, dependencies).
- Any client-specific compliance or quality standard already known from discovery (a browser/device support matrix, an accessibility requirement, a security/regulatory sign-off).
- A prior project's DoR/DoD baseline, if the PM wants to reuse one as a starting point rather than draft from zero.

## 4. What it does, step by step

1. **Gather what's already fixed.** Pull feasibility constraints from the discovery-context, scope/non-goals from the PRD, and anything from the regulatory/legal/tech-stack axes that constrains readiness or completion.
2. **Draft the Definition of Ready baseline.** The preconditions that must be true before any epic can start: dependencies unblocked, design direction approved, environment provisioned, stakeholders aligned, no blocking open question left on the feature file.
3. **Draft the Definition of Done baseline.** The completion bar every epic must clear: acceptance criteria passed, deployed to the agreed environment, documentation updated, metrics instrumented, accessibility/security bar met where it applies.
4. **Separate universal from project-specific.** Tag each item as either the standard Quarks baseline (applies to every project) or specific to this client (a particular browser matrix, a particular compliance sign-off), so `/backloguer` knows which parts are non-negotiable everywhere vs. local to this engagement.
5. **Phrase every criterion as testable.** Each item must resolve to a clear yes/no when checked; no aspirational language ("high quality," "well tested"). This is the same spirit as the IEC/IEEE-grounded acceptance-criteria conventions already used for UAT in this repo.

## 5. What it does NOT do

- Does not write epic-level or story-level DoR/DoD; that's `/backloguer`'s job, which only adds the delta on top of this baseline.
- Does not get skipped for simple projects; even a minimal project states its baseline explicitly ("no blocking preconditions beyond X"), never silently absent.
- Does not restate acceptance criteria for an individual story or feature; it sets the bar, not the checklist for one item.
- Does not invent a compliance or quality requirement that wasn't actually raised during discovery; unconfirmed items get flagged as open, not assumed.

## 6. What comes out

Two lists:
- **Definition of Ready baseline**: preconditions before any epic can start.
- **Definition of Done baseline**: the completion bar every epic must clear.

Each item is phrased as a testable yes/no condition and tagged as either the universal Quarks standard or specific to this client/project.

## 7. How it comes out

A markdown section, written directly (no external tool/board needed); English field labels following the schema, content in Spanish, consistent with the rest of `knowledge/product/features/`.

## 8. Where it goes

- `knowledge/product/features/<slug>.md`, new `## DoR / DoD baseline` section. Requires extending `knowledge/product/features/_SCHEMA.md` with that section before the first run, if it doesn't exist yet (same pattern `/prd-writer` used for `## Non-goals` and `## Scope by capability`).
- Nothing committed without operator confirmation per the autonomy mode.

## 9. Example

Not applicable yet; no worked example has been captured for this skill.

## 10. Skill acceptance criteria

- Every DoR item and every DoD item is phrased as a testable yes/no condition, not an aspiration.
- The baseline is stated even when minimal; never silently skipped.
- Client/project-specific items are tagged separately from the universal Quarks baseline.
- Doesn't duplicate or restate what `/backloguer` will do at the epic level; stays at the project-wide bar.
- Unconfirmed compliance/quality requirements are flagged as open, not assumed.
- Output is 100% Latin American Spanish, consistent with the rest of `knowledge/product/features/`.
