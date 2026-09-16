# Skill: discovery-diary-study (Diary studies / shadowing)

**Your goal:** capture what people actually do, over time or in the moment, when what they say
in an interview is likely to diverge from real behavior; common in operational, logistics, or
healthcare-adjacent workflows. The most expensive skill in this kit; use it only when the gap
between stated and real behavior is the actual risk.

## Where it fits

Stage 7; see [`briefings/_ciclo-preventa.md`](../../briefings/_ciclo-preventa.md) § Discovery
and [`briefings/_kit-discovery.md`](../../briefings/_kit-discovery.md).

## When to use it

Budget and time exist for it, and there's a specific reason to distrust self-report, e.g. a
process that's stigmatized, habitual to the point of being invisible to the person doing it, or
spread irregularly across a day/week in a way no single interview could reconstruct. If
[`discovery-interview-guide`](./discovery-interview-guide.md) already produced a confident,
consistent account across participants, this skill is probably not worth its cost; don't run it
by default just because it's in the catalog.

## Input

- A recruited group of 4-8 participants willing to commit 1-2 weeks (diary) or a few hours of
  observed time (shadowing); over-recruit slightly, diary studies lose participants to fatigue.
- A specific behavior or moment to focus on; this isn't a general-purpose "watch someone work
  all day" exercise; name what you're trying to see before starting.

## How you facilitate it

**Diary study:**
1. Give participants a short, structured logging template (trigger, action taken, time spent,
   friction encountered, emotion) filled in near the moment it happens, not reconstructed at
   day's end.
2. Keep the daily burden under 2-3 minutes per entry, or completion drops off fast.
3. Duration: long enough to catch the behavior's natural cycle (a weekly billing task needs at
   least 2 weeks, a daily habit needs less).
4. Debrief interview at the end, walking through their own entries with them; the debrief
   surfaces more than the raw entries alone.

**Shadowing / contextual inquiry:**
1. Observe in the person's actual context, doing the actual task; not a re-enactment in a
   meeting room.
2. Apprentice model: you're there to learn the craft, not to audit it. Ask "why" in the moment
   a decision happens, not in a post-hoc interview where the reasoning gets rationalized.
3. Note what the person does that they *don't* mention, and what they mention that they *don't*
   actually do; the gap itself is the finding.

## Tool

Primary: **Doc**, a shared log template (spreadsheet or form works fine for the diary; plain
observation notes for shadowing). Not a Miro exercise; the output is longitudinal text/data, not
a spatial artifact.

## Output & where it lands

Raw entries/observation notes, verbatim, → `source/interviews/YYYY-MM-DD-<client>-diary-<participant>.md`
per `CLAUDE.md` § Source preservation (treat diary entries and shadowing notes as interview-kind
source; they're first-person account, preserved whole). Synthesis (patterns across
participants, say/do gaps found) → `ingestion/interviews/YYYY-MM-DD-<client>-diary-synthesis.md`.

Route per § Correlational vs. causal caution in `CLAUDE.md`: a diary/shadowing finding is
observational, not automatically causal; if it contradicts an interview-based insight already
in `knowledge/users/insights.md`, surface it as a tension in that file's § Contradictions, don't
silently overwrite the interview-based entry.

## Quality criteria

✅ A specific behavior/moment was named before starting; not open-ended "watch everything"
✅ Diary entries logged near the moment, not reconstructed at day's end (check timestamps if
   the tool captures them)
✅ At least one explicit say/do gap named in the synthesis, if one was found
✅ Verbatim entries/notes preserved in `source/interviews/`, synthesis kept separate
✅ Findings that contradict existing interview-based insights are logged as a tension, not
   quietly overwritten
✅ Only run when a real reason to distrust self-report was identified, named in the synthesis
