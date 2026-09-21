# Skill: build-context (build_context)

## 1. Role

You consolidate everything that came out of the paid Discovery stage, whichever 2-4 methodologies `/discovery-prep` recommended, into one authoritative project "bible," right when Discovery finishes. `/prd-writer` then reads this bible to draft the formal functional/technical/design requirements document.

This mirrors `/discovery-context`'s role one stage earlier: `/discovery-context` consolidates the pre-sale briefing; this skill consolidates the paid Discovery stage. Not to be confused with each other despite the shared naming history; see [`briefings/_ciclo-preventa.md`](../../briefings/_ciclo-preventa.md) for the disambiguation.

## 2. Where in the process

The close of Discovery, stage **2-Discovery** (see [`docs/skills-roadmap.md`](../../docs/skills-roadmap.md)), what [`briefings/_ciclo-preventa.md`](../../briefings/_ciclo-preventa.md) calls "etapa 7". Runs once all the discovery sessions `/discovery-prep` planned have actually happened. Feeds `/prd-writer` immediately, and stays the reference document that `/backloguer`, the design-system work, `qbs_setup`, `/trf`, UAT, the user manual, and `/postmortem` all read from later; none of them re-derive it.

## 3. Required input

- `/discovery-prep`'s plan: which methodologies were selected, and why.
- The synthesis output (`ingestion/meetings/...`) of every discovery session that actually ran: whichever combo of `discovery-business-model-canvas`, `discovery-value-proposition-canvas`, `discovery-jtbd`, `discovery-stakeholder-mapping`, `discovery-interview-guide`, `discovery-journey-map`, `discovery-event-storming`, `discovery-story-map`, `discovery-premortem`, user persona work, information architecture work, or `discovery-proto` sessions were run for this client.
- The original `/discovery-context`, for continuity on the feasibility read and the regulatory/legal/tech-stack axes.

## 4. What it does, step by step

1. **Pull every discovery session's synthesis**, not the raw source transcripts; the `ingestion/` layer, not `source/`.
2. **Consolidate into one narrative, organized around the same 4 axes `/discovery-prep` used**: functional, technical, design, methodological. Resolve each open question `/discovery-prep` flagged, or name it as still open if Discovery didn't actually close it.
3. **Reconcile contradictions across sessions** (e.g. stakeholder mapping said one thing, an interview said another); surface the tension explicitly, don't silently pick a side.
4. **Carry forward and update the feasibility read** and the regulatory/legal/tech-stack axes from `/discovery-context`, folding in anything newly confirmed during Discovery.
5. **Name what's still genuinely open**, honestly, so `/prd-writer` doesn't draft with false confidence on an unresolved point.
6. **Update project-context and client-context.** Append a Timeline entry to `briefings/<client>-project-context.md` (see [`briefings/_project-context-template.md`](../../briefings/_project-context-template.md)) and update `knowledge/org/<client-slug>.md` with anything durably learned across the whole Discovery stage (not session by session; that granularity stays in each discovery methodology's own routing).

## 5. What it does NOT do

- Does not run any discovery methodology itself; it only consolidates sessions that already happened.
- Does not draft the PRD; that's `/prd-writer`'s job, immediately downstream of this.
- Does not silently resolve a contradiction between two discovery sessions; it surfaces the tension instead.
- Does not get created before at least the planned discovery sessions have run; if `/discovery-prep`'s combo isn't finished yet, that's the blocker to name, not a reason to summarize prematurely.

## 6. What comes out

The consolidated bible: problem and context (confirmed vs. still open), users, business model/value proposition (if those methodologies ran), stakeholders, feasibility, the updated methodological context, and the open questions still unresolved going into PRD writing. Also: an updated `project-context` Timeline entry and a refreshed `client-context`.

## 7. How it comes out

A markdown document, internal, meant to be read by `/prd-writer` right away and referenced (not regenerated) by every skill downstream of it for the rest of the engagement.

## 8. Where it goes

`briefings/YYYY-MM-<client>-build-context.md`, dated when Discovery actually closes. That date is what keeps it from colliding with an older `<client>-build-context.md` a client might already have from before the 2026-09-21 rename (that file is now what `/discovery-context` produces, from an earlier, pre-sale-era date).

- `project-context`: `briefings/<client>-project-context.md` (append the Timeline entry).
- `client-context`: `knowledge/org/<client-slug>.md` (update).

## 9. Example

Not applicable yet; no worked example has been captured for this skill.

## 10. Skill acceptance criteria

- Consolidates only sessions that already ran; doesn't run a discovery methodology itself.
- Organized around the same 4 axes `/discovery-prep` used: functional, technical, design, methodological.
- Contradictions across discovery sessions are surfaced, not silently resolved.
- The feasibility and regulatory/legal/tech-stack read is carried forward and updated from `/discovery-context`, not rebuilt from scratch.
- Feeds `/prd-writer` directly, and stays the reference `/backloguer`, design system, setup, `/trf`, UAT, the user manual, and `/postmortem` read from.
- `project-context` and `client-context` are both updated.
- Output is 100% Latin American Spanish.
