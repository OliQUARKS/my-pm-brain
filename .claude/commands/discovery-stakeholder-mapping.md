# Skill: discovery-stakeholder-mapping (Stakeholder Mapping / RACI)

**Your goal:** know who actually decides before the discovery runs out of runway. Not glamorous,
but it's the single most common reason a discovery stalls mid-way; the person who signed the
contract isn't the person who approves scope.

## Where it fits

Stage 7; see [`briefings/_ciclo-preventa.md`](../../briefings/_ciclo-preventa.md) § Discovery
and [`briefings/_kit-discovery.md`](../../briefings/_kit-discovery.md). Run it **first**, before
any other discovery skill; every other method in the kit assumes you already know who needs to
be in the room.

## When to use it

Always, early; this isn't optional the way the others are. The only judgment call is depth:
a single-decision-maker SMB client gets a 10-minute version; a multi-department client (legal +
compliance + ops, like a fintech or a law firm's practice groups) gets the full RACI.

## Input

- Contract/proposal signer + whoever attended the briefing/build-context sessions, starting
  roster, not the final one.
- Org chart or team page if the client has one public.

## How you facilitate it

1. **List everyone touched** (decision-makers, users, people who can block, people who'll be
   asked to approve budget or compliance later even if they weren't in earlier meetings).
2. **Plot on the Power/Interest grid** (Mendelow matrix), 2×2:
   - High power / high interest → **manage closely**
   - High power / low interest → **keep satisfied**
   - Low power / high interest → **keep informed**
   - Low power / low interest → **monitor**
3. **RACI per major discovery deliverable** (not per micro-task): who's **R**esponsible,
   **A**ccountable, **C**onsulted, **I**nformed for each of (scope sign-off, prototype
   feedback, final discovery report). One person accountable per deliverable, always; if two
   names land in the "Accountable" column, that's the flag to raise with the client, not
   something to quietly average out.
4. Ask directly: "if this needs budget or legal sign-off later, who else needs to be looped in
   now?" (the RyD/PERC pattern is a compliance or legal stakeholder who only shows up at the
   worst possible moment if not mapped early).

## Tool

Primary: **Miro**, 2×2 power/interest board + a RACI table alongside it (`board_create` +
`table_create` for the RACI grid, or a Miro table widget). Keep both on the same board so the
grid and the RACI stay visually linked to the same names.

## Output & where it lands

Board URL + retrieved-at timestamp + description of grid placement and RACI assignments →
`source/meetings/YYYY-MM-DD-<client>-stakeholder-mapping.md` per `CLAUDE.md` § Source
preservation fallback rule. Synthesis → `ingestion/meetings/YYYY-MM-DD-<client>-stakeholder-mapping.md`.

This is the one discovery skill whose output has a **direct canonical home per person**, not
just a themed insight: create or update `stakeholders/<slug>.md` for every named individual
(role, influence quadrant, current RACI role) and add each to `stakeholders/INDEX.md` per
`CLAUDE.md` § INDEX maintenance; this is a hard rule, not an optional promotion. Motivations
inferred rather than stated are labeled as interpretation and anchored to this session.

## Quality criteria

✅ Every named stakeholder has a `stakeholders/<slug>.md` file and an `INDEX.md` row, no
   silent gaps
✅ Every discovery deliverable has exactly one Accountable name, not zero or two
✅ At least one explicit question asked about downstream budget/legal/compliance sign-off
✅ Power/Interest quadrant assigned to everyone, not just the obvious high-power names
✅ Motivations/concerns inferred (not stated outright) are labeled as interpretation with source
✅ Run before any other `/discovery-*` skill in the engagement, not after
