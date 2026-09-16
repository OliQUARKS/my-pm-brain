# Skill: discovery-opportunity-tree (Opportunity Solution Tree)

**Your goal:** work through real ambiguity about which problem to attack first, connecting a
business outcome to opportunities grounded in research, multiple candidate solutions per
opportunity, and small experiments before committing. The most research-hungry skill in this
kit; it needs a steady stream of customer contact to stay honest.

## Where it fits

Stage 7; see [`briefings/_ciclo-preventa.md`](../../briefings/_ciclo-preventa.md) § Discovery
and [`briefings/_kit-discovery.md`](../../briefings/_kit-discovery.md).

## When to use it

Genuine ambiguity about which problem matters most; not a client who already knows what they
want built (that's [`discovery-story-map`](./discovery-story-map.md) territory) and not a
client with zero research yet (start with
[`discovery-interview-guide`](./discovery-interview-guide.md) or
[`discovery-jtbd`](./discovery-jtbd.md) first; this tree has nothing to hang opportunities on
without them).

**Sizing check before running this in a fixed-scope discovery:** Teresa Torres' method assumes
continuous weekly customer contact to keep the opportunity layer current. A 2-4 week fixed-scope
discovery engagement can build a first version of the tree, but say so explicitly in the
output; a tree built once and never revisited goes stale fast. If the client has no ongoing
interview cadence planned post-discovery, note that as a named risk rather than silently
presenting the tree as durable.

## Input

- A single measurable business outcome (same shape as the "Why" in
  [`discovery-impact-map`](./discovery-impact-map.md); if both skills run in the same
  engagement, reuse the same outcome rather than re-deriving it).
- Existing interview/JTBD synthesis to mine for opportunities; this tree is built from what
  customers have actually said, not brainstormed cold.

## How you facilitate it

Four layers, top to bottom:

1. **Outcome**, one measurable business result at the top. Reuse the impact map's "Why" if one
   exists.
2. **Opportunities**, customer pains, needs, or desires pulled from actual research (interview
   quotes, support tickets), each phrased as the customer's problem, not a solution
   ("paralegals lose track of which version of a document is current"; not "add version
   history"). Nest sub-opportunities under a parent when one pain has multiple facets.
3. **Solutions**, multiple candidate solutions per opportunity, generated only after the
   opportunity layer is populated. More than one solution per opportunity is the point; picking
   the first idea that comes up defeats the tree.
4. **Experiments**, the smallest test that would tell you whether a solution is worth building,
   attached to each solution before any gets built for real.

## Tool

Primary: **Miro**, tree/org-chart layout, outcome at top branching down through opportunities,
solutions, experiments (`board_create` + a tree template). Color-code opportunities by which
source interview(s) they came from, so the evidence trail stays visible on the board itself.

## Output & where it lands

Board URL + retrieved-at timestamp + description of the full tree, with each opportunity's
source interview(s) noted → `source/meetings/YYYY-MM-DD-<client>-opportunity-tree.md` per
`CLAUDE.md` § Source preservation fallback rule. Synthesis → `ingestion/meetings/YYYY-MM-DD-<client>-opportunity-tree.md`,
naming explicitly whether the client has a post-discovery interview cadence to keep the tree
alive (per the sizing check above).

Route per § Canonical ownership: opportunities that recur across the underlying interviews →
`knowledge/users/insights.md` § Active themes (Evidence rows point to the original interviews,
not the tree; the tree is a synthesis view, not a new independent source). The chosen
outcome, if the client commits to it, → a decision record.

## Quality criteria

✅ Every opportunity traces to a real interview/ticket source, not brainstormed cold
✅ Opportunities are phrased as customer problems, never as solutions in disguise
✅ At least 2 candidate solutions considered per opportunity before one is picked
✅ Every solution has an attached experiment before it's treated as "the plan"
✅ Sustainability of the tree (ongoing interview cadence or lack thereof) named explicitly in
   the output, not assumed
✅ Opportunity evidence routed back to the original interviews, not double-counted as new
   confirmation
