# Skill: backloguer

## 1. Role

You break down a PRD into epics, then epics into INVEST user stories: the full backlog, ready to push to a tracking tool. Replaces the former separate `/epics` + `/stories` commands: one skill, one flow, matching the backloguer process end to end.

## 2. Where in the process

Stage **4-Define** (see [`docs/skills-roadmap.md`](../../docs/skills-roadmap.md)). Runs after [`/prd-writer`](./prd-writer.md) closes discovery, at the start of the development cycle; never fed directly by a discovery-stage skill. `discovery-story-map` stops at title-level and hands off only to `/prd-writer`; see [`briefings/_kit-discovery.md`](../../briefings/_kit-discovery.md).

## 3. Required input

- Feature name, slug, or nothing (infers the active feature from `knowledge/strategy.md`, or the PRD in `knowledge/product/features/<slug>.md`).
- Optional flags:
  - `--detail <EP-XX or name>` (full epic template for that epic)
  - `--stories <EP-XX>` (break that epic down into INVEST stories)
  - `--detail <EP-XX-US-YY>` (full story template for that story)
  - `--push` (at the end, offers to push to ClickUp; see § 7, How it comes out)
- What you load before writing:
  - `knowledge/strategy.md` (active feature, priorities, non-goals)
  - `knowledge/product/features/<slug>.md` (problem, `## Scope by capability` from `/prd-writer`, open questions, linked decisions)
  - `decisions/INDEX.md` (decisions affecting dependencies and acceptance criteria)
  - `hypotheses/INDEX.md` (active hypotheses related to the feature)
  - Previous `ingestion/adhoc/*-epics-<slug>.md` and `*-stories-<slug>-*.md` (non-redundancy memory: which epics/stories were already generated for this feature)

## 4. What it does, step by step

1. **Epics, first pass: list only.** For each candidate epic: sequential ID `EP-XX` (continues numbering if previous epics exist in `ingestion/adhoc/`) plus a title in infinitive form. Apply the functional-exclusivity criterion: each epic solves a distinct user problem; group by the nature of the problem, not by where it happened to get documented in the PRD; something already assigned to one epic can't reappear in another. Deliver only the ID plus title list; no detail yet.
2. **Epics, detail (`--detail <EP-XX>`).** Before detailing a new epic, review the ones already detailed this session; complement, don't repeat. If a criterion or backbone activity is already covered elsewhere, reference it briefly ("Uses the same verification mechanism as EP-01") instead of restating it. Then apply the epic template (§ 6, What comes out).
3. **Stories (`--stories <EP-XX>`).** Split the epic's backbone into small, independent units of work (INVEST, see step 6). Sequential `[EP-XX]-US-YY` IDs. Non-redundancy across epics: if another epic in the same feature already defined a flow, this story assumes the user went through it and focuses on its own differential value.
4. **Cover alternative scenarios and unhappy paths.** Every user story must systematically identify and specify all applicable acceptance criteria (Given/When/Then) across these 6 categories:
   1. **Alternative Flows**: secondary valid paths that reach the goal via a different route (e.g. a manual bypass, a secondary payment method, pre-calculated packages instead of custom inputs).
   2. **Business Rule Exceptions**: violations of domain rules, preconditions, or business constraints (e.g. insufficient balance, ineligibility by credit score, transaction limits exceeded, invalid data range).
   3. **Technical & System Failures**: infrastructure or third-party service failures (e.g. third-party API timeout/unavailability, database connection failure, HTTP 500/504, network drops mid-transaction).
   4. **Edge Cases & Boundary Value Analysis**: system behavior at the extreme borders of input data, volume, or time (e.g. 0 or the maximum allowed amount, a timer's exact expiration, maximum retry attempts reached, empty or massive lists).
   5. **Security & Authorization Exceptions**: unauthenticated or unauthorized access attempts, expired tokens/sessions, invalid MFA/TOTP codes, execution by a user with an insufficient role.
   6. **Interruptions, Concurrency & State Inconsistencies** (Interrupciones y Concurrencia): aborting/cancelling mid-flow, double-click/race conditions, acting on an entity that's in an invalid state.

   **Trivial Story Bypass.** Before applying the 6-category matrix, evaluate the story's nature. If it's a static, purely cosmetic change with no underlying business logic (copy updates, color/CSS tweaks, minor visual reorganization of components), skip the exhaustive unhappy-path sweep, to avoid overengineering:
   - Document only the happy path and any relevant visual impact (responsiveness, breakpoints).
   - Add this exact line to the story's Technical notes and dependencies section: "Trivial Story Bypass applied due to low complexity (cosmetic/static change)."
5. **DoR/DoD specificity.** Definition of Ready and Definition of Done live at the epic level, once, covering the epic as a whole. A story's own DoR/DoD section stays empty unless there's a condition specific to that story that the epic's DoR/DoD doesn't already cover (a specific test dataset, a story-specific technical dependency); never copy the epic-wide DoR/DoD into a story.
6. **Verify INVEST before surfacing any story:**
   - **I**ndependent: doesn't block/depend on another story except for explicit dependencies.
   - **N**egotiable: a conversation with the team, not a contract.
   - **V**aluable: delivers something verifiable to the user or the system.
   - **E**stimable: size is assignable with the information available.
   - **S**mall: finishes in 3 dev days or less, or gets split.
   - **T**estable: at least 1 verifiable acceptance criterion.
   Stories that don't pass get split, no exceptions.

**Origin rule, applied throughout:** every epic and every story carries, in its technical-notes/dependencies section, a reference to the artifact it came from (the PRD section, a `decisions/` file, an ingested discovery session). An epic or story with no traceable origin can't be estimated or discussed with any confidence. If the originating artifact wasn't itself verified against the real system (e.g. it came from a stakeholder claim or an unconfirmed doc), say so explicitly in "Riesgos y supuestos" / "Notas técnicas"; don't estimate an unconfirmed claim with the same confidence as a verified one.

## 5. What it does NOT do

- Does not run before `/prd-writer`; `discovery-story-map` hands off only to `/prd-writer`, never directly to this skill.
- Does not surface a story that fails INVEST; it gets split first, no exceptions.
- Does not restate the epic-wide DoR/DoD inside a story; only the delta, or the inheritance line.
- Does not force the 6-category unhappy-path sweep on a trivial/cosmetic story; those use the Trivial Story Bypass instead.
- Does not let non-goals from `knowledge/strategy.md § Explicit non-goals` appear as epics or in any story.
- Does not write to durable knowledge layers (`knowledge/`, `hypotheses/`, `decisions/`); epics and stories are planning artifacts, and the brain records the outcome later when `/ingest` captures the sprint retro.
- Does not commit or push anything without operator confirmation, per the autonomy mode.

## 6. What comes out

**Epics, without `--detail`:** a table: `EP-XX | Title (infinitive) | Blockers | Expected KPI`.

**Epics, with `--detail <EP-XX>`,** epic template:
- Epic identification: title (infinitive) plus ID.
- Problem framing: target users, user problem, business value.
- Definition of Ready: epic-wide preconditions (blocking decisions closed, dependencies available, stakeholders aligned, no backbone-blocking open question).
- Backbone: left-to-right narrative flow, minimum 3 activities.
- High-level acceptance criteria: expected outcome (behavior change) plus success metrics (quantifiable).
- Definition of Done: epic-wide completion bar (every story shipped and accepted, backbone works end-to-end, metrics instrumented, no blocking open question left).
- Riesgos y supuestos: feasibility risks, assumptions, and origen (the artifact this epic came from, per the origin rule).

Open questions from the feature file that block acceptance criteria are marked `⚠️ Open OQ: [description]`.

**Stories, without `--detail`:** a table: `[EP-XX]-US-YY | Title ("As a [role], I want [action]") | Estimated size`.

**Stories, with `--detail <ID>`,** story template:
- Identification: `USER STORY [EP-XX]-US-YY`.
- Title: clear action.
- Narrative: as a [role] / I want [functionality] / so that [value].
- Definition of Ready: story-specific only; "Inherits epic DoR (no story-specific preconditions)" if nothing extra applies.
- Acceptance criteria: Given/When/Then; happy path plus every applicable unhappy-path category (§ 4, step 4), or the Trivial Story Bypass line if the story qualifies.
- Technical notes and dependencies: other epics/stories/services referenced, `decisions/` constraints, `⚠️ Open OQ`, and origen (per the origin rule).
- Definition of Done: story-specific only, same inheritance rule as DoR.
- Estimated size: XS (under 4h), S (under 1 day), M (under 3 days), L (under 1 week), or XL, which must be split before pushing.

## 7. How it comes out

The tables and templates above, presented for review, plus a closing step. Always ask: "Push this to ClickUp, to another tool, or leave it as is?"

- **ClickUp**: create or reuse a ClickUp List for the feature (`clickup_create_list`), a Task per epic (`clickup_create_task`) using the epic template as the description, and each story as a Task within its epic's Task/List, referencing the parent. XL stories aren't pushed; they get flagged to split first.
- **Another tool**: the same content reformatted as strict plain text (no markdown, section/epic/story titles in uppercase, hyphen lists, three line breaks between sections); ready to paste into Jira/Linear/GitHub Issues/a ticket description.
- **Leave it as is**: nothing further; the `ingestion/adhoc/` files are already the source.

## 8. Where it goes

- `ingestion/adhoc/<date>-epics-<slug>.md` (generated epics: list or detail). Source for the stories step and non-redundancy memory for future runs.
- `ingestion/adhoc/<date>-stories-<slug>-<epic>.md` (generated stories: ID, title, estimated size).
- Nothing in durable layers; epics/stories are planning artifacts. Nothing committed without operator confirmation per the autonomy mode.

## 9. Skill acceptance criteria

- Each epic has exactly 1 user goal; split if it has more than one.
- Non-goals from `strategy.md § Explicit non-goals` don't appear as epics or in any story.
- Every epic and every story cites its origin per the origin rule; no exceptions.
- Unconfirmed origins are flagged in Riesgos y supuestos / Notas técnicas, not estimated at full confidence.
- Definition of Ready is never empty at the epic level; "No blocking preconditions identified" if genuinely none.
- Story DoR/DoD never restates the epic's; only the delta, or the inheritance line.
- Unhappy paths are mandatory for functional stories. Trivial/cosmetic stories must explicitly use the "Trivial Story Bypass" in their technical notes instead of forcing unnecessary error paths.
- Stories that fail INVEST get split before surfacing, no exceptions.
- Before detailing a new epic or story, the memory of what's already detailed for this feature was reviewed (non-redundancy).
- Epic and story titles, narratives, and acceptance-criteria content are written in Latin American Spanish, consistent with the rest of the repo's planning artifacts (see `ingestion/adhoc/2026-05-27-epics-flujo-credito.md`).
