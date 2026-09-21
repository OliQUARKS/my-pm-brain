# Skill: discovery-prep (discovery_prep)

## 1. Role

You prepare the Discovery stage before it starts: work out the open questions across the 4 areas, functional, technical, design, and methodological, and recommend which 2-4 discovery methodologies from the kit fit this client, so the team doesn't run the whole catalog or wing it session by session.

## 2. Where in the process

Stage **2-Discovery** (see [`docs/skills-roadmap.md`](../../docs/skills-roadmap.md)): the very first step of the paid Discovery stage, what [`briefings/_ciclo-preventa.md`](../../briefings/_ciclo-preventa.md) calls "etapa 7", right after the deal closes and before any of the `/discovery-*` facilitation skills run.

## 3. Required input

- Whatever pre-sale context exists: `/discovery-context` if it was run, otherwise `/briefing-context` and `/minutero`.
- Signals about the client's maturity and the problem's shape (has a product team or not, technical sophistication, domain complexity), per [`briefings/_kit-discovery.md`](../../briefings/_kit-discovery.md)'s selection table.
- The discovery kit's selection logic itself (`_kit-discovery.md`), to ground the methodology recommendation.

## 4. What it does, step by step

1. **Build the open-questions map across the 4 areas**: functional, technical, design, methodological. Not a fixed checklist; scoped to what's actually still unknown for this specific client, starting from the gaps already flagged in `/discovery-context` or `/briefing-context`.
2. **Assess the client's maturity and problem shape** against `_kit-discovery.md`'s table: no clear idea of anything, has a business idea but not a product idea, has its own product team and speaks in features, or a complex domain with many business rules.
3. **Recommend a combo of 2-4 discovery methodologies** from the kit, with a one-line rationale each, following the kit's own selection logic. Never recommend the full 15-method catalog.
4. **Sequence the recommended methodologies**: which one runs first, which builds on which.
5. **Flag hard prerequisites vs. optional methods**: some methods (like stakeholder mapping) should run early almost regardless of the combo; call those out separately from the situational picks.

## 5. What it does NOT do

- Does not run any of the discovery methodologies itself; it only plans which ones and in what order.
- Does not recommend running the entire 15-method catalog; always narrows to 2-4, per `_kit-discovery.md`'s own rule.
- Does not invent an open question that isn't grounded in an actual gap from `/discovery-context` or `/briefing-context`; every open question traces to something genuinely unknown.
- Does not skip the methodological axis (how the engagement will actually work) just because it feels soft; it's one of the 4 mandatory areas, same as the others.

## 6. What comes out

- An open-questions map across the 4 areas (functional, technical, design, methodological), each question tied to where the gap came from.
- A recommended, sequenced combo of 2-4 discovery methodologies, each with a one-line rationale.
- Hard prerequisites flagged separately from situational picks.

## 7. How it comes out

A markdown planning document, internal.

## 8. Where it goes

`briefings/<client>-discovery-prep.md`.

## 9. Example

Not applicable yet; no worked example has been captured for this skill.

## 10. Skill acceptance criteria

- Every listed open question traces to an actual gap already flagged in `/discovery-context` or `/briefing-context`, not invented from scratch.
- All 4 areas are covered, even if one comes up empty; an empty area is stated explicitly, not omitted.
- Recommends 2-4 methodologies, never the full 15, each with a rationale tied to `_kit-discovery.md`'s selection logic.
- The recommended methodologies are sequenced, not just listed.
- Output is 100% Latin American Spanish.
