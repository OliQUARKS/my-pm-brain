# Skill: discovery-journey-map (Customer Journey Mapping)

**Your goal:** make an existing process (offline, or living in another system) visible end to
end, in a shape the client can follow without knowing product vocabulary. The single most
client-friendly visual in this kit; reach for it when the audience isn't fluent in épica/historia.

## Where it fits

Stage 7; see [`briefings/_ciclo-preventa.md`](../../briefings/_ciclo-preventa.md) § Discovery
and [`briefings/_kit-discovery.md`](../../briefings/_kit-discovery.md). Frequently paired with
[`discovery-empathy-map`](./discovery-empathy-map.md) as a warm-up, and feeds
[`discovery-service-blueprint`](./discovery-service-blueprint.md) when the problem turns out to
be as much backstage as front-of-house.

## When to use it

The product digitizes or improves a process that already exists (offline, in spreadsheets, in
a legacy system, over phone/email). If the process doesn't exist yet (greenfield), this skill has
nothing real to map; use [`discovery-jtbd`](./discovery-jtbd.md) or
[`discovery-impact-map`](./discovery-impact-map.md) instead.

Build it **from evidence** (prior interviews, shadowing, or ticket data), not from what the
internal team assumes the journey looks like. If no such evidence exists yet, run
[`discovery-interview-guide`](./discovery-interview-guide.md) first.

## Input

- Prior interview transcripts or shadowing notes for the segment being mapped.
- One persona/segment per map; if two segments diverge meaningfully (e.g. a paralegal's
  journey vs. a partner's journey through the same case), map them separately rather than
  merging into one average journey that's true for nobody.

## How you facilitate it

1. **Name the phases first**, left to right, in the client's own vocabulary for their process
   (not a generic "awareness → consideration → purchase" template unless it actually fits).
2. **Swimlanes underneath each phase:**
   - **Actions**, what the person actually does.
   - **Touchpoints**, systems, people, documents they interact with.
   - **Thoughts**, what they're thinking (from evidence, quoted where possible).
   - **Emotions**, plot as a curve across the phases; the dips are where the opportunities are.
   - **Pain points**, named explicitly, one per dip.
3. **Opportunities row last**, one line per pain point, not a solution yet, just "what would
   need to be true for this pain to go away."
4. Timebox: 90 minutes for a first pass covers 4-6 phases; don't try to map the whole lifecycle
   in one sitting if it's genuinely long (e.g. a multi-year legal case).

## Tool

Primary: **Miro**, horizontal swimlane template (`board_create` + a journey-map format, or
`canvas_create_from_svg` for a custom phase/swimlane grid). Use the emotion-curve line widget
so the dips are visually obvious without reading every sticky.

## Output & where it lands

Board URL + retrieved-at timestamp + description of phases/swimlanes/emotion curve →
`source/meetings/YYYY-MM-DD-<client>-journey-map-<segment>.md` per `CLAUDE.md` § Source
preservation fallback rule. Synthesis (named pain points + opportunities) →
`ingestion/meetings/YYYY-MM-DD-<client>-journey-map-<segment>.md`.

Route per § Canonical ownership: pain points that recur across the underlying interviews →
`knowledge/users/insights.md` § Active themes, each Evidence row linking back to the specific
interview that surfaced it; the journey map itself is a synthesis artifact, not a new
independent source, so don't double-count a pain point as confirming itself.

## Quality criteria

✅ Built from cited prior evidence (interviews/shadowing), not invented in the room
✅ One map per segment when segments diverge; no averaged "typical user" journey
✅ Emotion curve present, not just a list of steps
✅ Every dip in the curve has a named pain point, every pain point has an opportunity line
✅ Opportunities stay solution-agnostic ("what would need to be true"), not pre-baked features
✅ Phases named in the client's own process vocabulary, not a generic funnel template
