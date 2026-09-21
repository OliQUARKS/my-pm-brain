# Skill: discovery-premortem (Premortem)

## 1. Role

You surface the risks nobody says out loud at the start of a project, before commitments (team, timeline, cost) harden. Cheap, fast, and the one technique in this kit explicitly designed to fight groupthink rather than build consensus.

## 2. Where in the process

Stage **2-Discovery** (see [`docs/skills-roadmap.md`](../../docs/skills-roadmap.md)): post-sale, pre-development discovery, what [`briefings/_ciclo-preventa.md`](../../briefings/_ciclo-preventa.md) calls "etapa 7". Part of the 15-methodology discovery toolkit, see [`briefings/_kit-discovery.md`](../../briefings/_kit-discovery.md). Run it near the end of a discovery batch, or right at the kickoff of development; after enough is known to imagine a specific failure, before the plan is locked in.

## 3. Required input

- A concrete future point to imagine failing at ("it's [ship date + 6 months] and this project failed"); vague framing produces vague risks.
- The full team and, ideally, the client's own team in the room; premortems work better with the people who'd actually be blamed for each failure mode present to name it themselves.

## 4. What it does, step by step

**When to use it:** any engagement, really; it's cheap enough that the main reason to skip it is time pressure, not fit. Most valuable when a team is confident (confidence is exactly what premortems are designed to pressure-test) or when a client has been burned before and is quietly anxious about a repeat failure they haven't said out loud (see `/briefing-context`'s "prior-experience profile" axis; a client "bruised from a failed project" is the strongest signal to run this).

**Facilitate it per Gary Klein's method; the order is what makes it work, don't skip the silent-writing step:**

1. **Frame it as already failed**, specifically: "It's [date]. This project failed. Badly." Not "might fail"; the past-tense framing measurably produces more and sharper reasons than a hypothetical framing.
2. **Silent, individual writing first.** Everyone privately writes their own reasons why it failed, 5-10 minutes, no discussion yet. This is the step that fights anchoring: if the loudest person speaks first, everyone else's list shrinks to fit theirs.
3. **Round-robin share.** One reason at a time per person, going around until lists are exhausted; not an open floor, which lets the same few voices dominate.
4. **Cluster** the reasons that came up (they'll overlap; that overlap is a signal of real risk, not redundancy to prune).
5. **For each cluster: name an owner and a leading indicator**, something observable early that would tell the team this failure mode is starting to happen, plus a mitigation if one's obvious. A risk with no owner and no leading indicator is not actually captured, just mentioned.
6. **Hold psychological safety** more carefully here than in any other skill in this kit: frame the exercise explicitly as safe-to-critique ("we're assuming this could fail, so naming problems is the job right now, not a criticism of the plan").

**Tool:** primary is a shared doc. Silent writing works better on individual notes (physical or a shared doc where entries stay hidden until the share-out) than on a live Miro board where people can see others typing and anchor on them. Cluster and owner/indicator table afterward, in the same doc.

## 5. What it does NOT do

- Does not frame the failure as hypothetical ("might fail"); it's always framed as already happened.
- Does not skip the silent individual-writing step, or let group discussion happen before it.
- Does not use an open floor for sharing; it's always round-robin, one reason per person per turn.
- Does not leave a clustered risk without both an owner and a leading indicator; without those, it's just mentioned, not captured.
- Does not prune overlapping reasons across individuals as redundant; the overlap itself is signal.

## 6. What comes out

- The full list of raw individual reasons, before clustering.
- The clustered risk table, with an owner and a leading indicator per cluster.

## 7. How it comes out

Two markdown files, following `CLAUDE.md` § Source preservation and § Canonical ownership:
- The verbatim source: raw individual lists plus the clustered risk table with owners/indicators, never edited after creation.
- The synthesis.

## 8. Where it goes

- Source (verbatim, raw individual lists preserved, not just the clustered summary): `source/meetings/YYYY-MM-DD-<client>-premortem.md`.
- Synthesis: `ingestion/meetings/YYYY-MM-DD-<client>-premortem.md`.
- Risks with a named owner become tracked items. If a risk is severe and decision-relevant (e.g. it would change scope or timeline if realized), draft it into `decisions/YYYY-MM-DD-<slug>.md`, naming the mitigation and reversal condition. Lower-severity risks stay as tracked items on the relevant `knowledge/product/features/<slug>.md`.

## 9. Example

Not applicable yet; no worked example has been captured for this skill.

## 10. Skill acceptance criteria

- Framed in the past tense as already-failed, not as a hypothetical "might fail."
- Silent individual writing happened before any group discussion; verify this wasn't skipped.
- Round-robin share used, not an open floor dominated by one or two voices.
- Every clustered risk has both an owner and a leading indicator, not just a description.
- Raw individual lists preserved in `source/`, not only the clustered summary.
- Severe, decision-relevant risks routed to a decision record with a reversal condition.
