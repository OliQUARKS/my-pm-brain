# Skill: build-context (ex post-briefing, POST)

**Your goal:** after the briefing meeting, expand the context with what actually came out of it and build the project/client's **internal context**. From that context, a **client-facing pre-proposal** is derived. The output is larger than briefing-context; it's not the pre corrected, it's the pre **expanded**. End goal: for the brief to have real leverage in closing the deal.

## Where it fits

Stage 4 of the cycle (see [`briefings/_ciclo-preventa.md`](../../briefings/_ciclo-preventa.md)). Starts from the briefing transcript + client documentation.

Careful with "discovery": when the pre-proposal (§ B) sells a discovery, it refers to the **post-sale/pre-development** stage (several paid sessions), not the briefing meeting.

## The three layers: don't mix them up

1. **Project context (build-context): INTERNAL.** What you build here. Never delivered to the client. It's the working input: expanded problem, context, users, stakeholders, roles, feasibility, and how we'd work it (methodological context).
2. **Pre-proposal / draft plan: CLIENT-FACING (light).** Derived from the build-context: "here's what we saw, here's the problem, here's the solution we propose, here's a demo/prototype of what we're imagining, are you interested?" No locked-in team/cost/timeline.
3. **Real proposal: only once there's a "yes".** Team, timeline, cost, discovery, who's in charge. This skill does **not** build it; this skill leaves the build-context ready and the pre-proposal pre-assembled.

## Purpose

The output of this meeting yields a **pre-proposal within 1-2 days**; don't let it go cold. Discovery comes next, where it gets refined into something concrete and the project kicks off; but it starts off in much better shape. Process rule: reserve 15 minutes right after the meeting to process the output and create the task, instead of chaining meetings and writing up notes at night.

## How you work

- **You expand, you don't rewrite from scratch.** You start from the Preparation Document and add what's new to it.
- **Honest about feasibility.** If we don't have the experience, API, or access, say so; it can still be proposed.
- **Precise and actionable.** No placeholders, no ambiguity. What's left open is named as open, not filled in.
- **Internal vs. client-facing always separated.** The context is internal; the pre-proposal is what's shown. Don't mix them.

## Input

- **The Preparation Document** (output of `/briefing-context`).
- **Answers obtained** in the meeting.
- **Transcript**: Granola / Meet.
- **Documents sent by the client.**
- **Info created by us**: what came out of internal meetings / our own judgment (not just the client's input).
- Any other info that came up.

## What you absolutely have to resolve: information goals

On the pre's goals, now with data from the meeting, resolve:

1. **Real problem (expanded)**: what we understood before vs. what we understand now; name what changed.
2. **New context**: systems, constraints, numbers, priorities, who decides.
3. **Users / roles / permissions**: confirmed or corrected.
4. **Feasibility**: can we help? with what (experience, API, access)? what's missing?
5. **Stakeholders**: who each one is and what role they play (see section 6).
6. **How we'd work it**: methodological context (see section 7).

## Mandatory analysis axes

Revalidate the pre's three axes with what came out of the meeting, and go deep on whichever is the crux:

- **Regulatory**: what was confirmed about the bodies/regulations that reach the solution.
- **Legal framework**: what can/can't be done (data, delegation, contracts).
- **Tech stack**: real stack, possible integrations, what's reusable vs. what needs rebuilding.

## Output

### A. Project context (internal)

**1. Problem statement (expanded)**
What we understood before vs. now. Explicitly name what changed.

**2. Expanded context**
Everything new: systems, constraints, numbers, priorities, decision-makers.

**3. Users / roles / permissions**
Refined with what was confirmed in the meeting.

**6. Stakeholders: who each one is**
Mini profile per person: role in the project and what matters to them (to steer the proposal). One line per person.

Each stakeholder's motivations and style are **interpretations**: label them and anchor them to the transcript/source they came from.

Out of scope for this skill: day-to-day operational style (preferred channel, what causes friction, how to escalate with each person, e.g. "Seba via WhatsApp not Discord") is day-to-day management → goes to the future `communication-context` skill, not here.

**7. Methodological context: how we'd work it**
How we work with this client: roles and responsibilities on both sides, environment management, communication model, reviews/documentation, SLA, and what absolutely needs defining. This is the block that answers the recurring concern "how do we work together?" and gives the proposal its edge.

Use the reusable template: [`briefings/_contexto-metodologico.md`](../../briefings/_contexto-metodologico.md). Standard Quarks baseline + per-client adjustment (full management vs. with dependencies). Each dependency → owner + risk if unresolved.

### B. Pre-proposal (client-facing, light)

**4. Proposal**
- **Scope**: what's in, what's out.
- **Discovery**: 1 to 4 weeks depending on complexity. (Sold as "a team for this long/this cost, and first a discovery to make the best use of it"; discovery isn't sold standalone.)
- **Prototype if feasible**: could be a website, an explanation, or a flow. Not always a screen.
- **How we'd work it**: excerpt from the methodological context: not just what we do, but how.
- **Can we help or not?**: honest feasibility; if API/experience/access is missing, it goes here.

### C. Operational output

**5. Meeting notes and next steps**
The meeting notes are an expected output of this skill, but they're generated by calling the `/minutero` skill, not drafted here. This skill leaves identified:

- **Open items.** What was left unresolved.
- **Actions.** Send the notes to the client right away / within 1-2 days max; create the tasks for the next deliverable.

## Output format: formatted Google Doc (+ markdown backup)

This skill's deliverable is always a formatted Google Doc, never a standalone `.md`. Two artifacts are produced, in this order:

1. **Markdown backup** (repo). Generate the project context (blocks A/B/C) as markdown and save it where it already lives in the repo (`briefings/YYYY-MM-<client>-build-context.md`, plus the `source/` of the meeting when applicable). It's the second brain's audit anchor; it doesn't get deleted.
2. **Formatted Google Doc** (deliverable). Create the document with the Google Drive connector from that same markdown:
   - Tool: Google Drive connector's `create_file`.
   - `title`: `Project Context, <Client>, <YYYY-MM-DD>`.
   - `textContent`: the full markdown.
   - `contentMimeType`: `text/markdown`.
   - Do not enable `disableConversionToGoogleType`; let Drive convert the markdown into a Google Doc with headings, bold, and tables.
   - If the PM specified a Drive folder, pass its `parentId`; otherwise it goes in the root.
3. Close by returning the Google Doc link plus the path to the backup `.md`.

This skill's Google Doc is **internal** (project context), not the one sent to the client; the client-facing proposal comes out of the `/propuestador` skill. Rule: the raw markdown is not the final deliverable; the deliverable is the Google Doc, and the `.md` stays in the repo purely for traceability.

## Worked example: from meeting to pre-proposal

**Input:** AL2/ACA Preparation Document + Granola transcript of the meeting + doc of the current onboarding process they sent over.

**How you interpret it:** in the pre, we assumed "unify wallet and brokerage onboarding." In the meeting it's confirmed that the crux is the **regulatory axis**: AL2's KYC (BCRA) can't be reused as-is to open ACA Valores' brokerage account (CNV/UIF, non-delegable AML). The real goal shifts to **a single onboarding that branches**, not a single sign-up.

**Output (excerpt):**
- *Expanded problem statement:* it's not "one sign-up for both"; it's a **shared entry point** that reuses shareable data and triggers two different KYC flows depending on the regulator.
- *Pre-proposal:* 3-week discovery; flow prototype (not a screen) mapping which data is requested only once and where it branches by regulation; integrates with each product's core.
- *Feasibility:* medium-high; we have fintech experience (AL2 is already a client); pending: identity API and what legal/UIF allows.
- *Stakeholder, Genaro (CEO):* business/embedded-finance decision-maker; cares about the business case and conversion.
- *Stakeholder, Nahuel (CTO, ex-Wenance):* technical role; cares about KYC/AML and integration.

## Out of scope (v2)

- Feeding the proposal with the **team's prior experience by industry** ("for this, talk to Irra/Nico/Juani"); depends on the skills map, which is surveyed separately.
- Reusable experience doc by domain (e.g. everything learned on a CRM project) for future clients of the same type.
- `communication-context`: a future, separate skill for day-to-day operational communication style per person (channel, friction, escalation).

## Quality criteria

✅ The three layers stay separated: context (internal) → pre-proposal (client-facing) → real proposal (post-yes, later)
✅ The problem statement is expanded, not rebuilt from scratch; what changed vs. the pre is named
✅ The 3 axes (regulatory/legal/stack) revalidated with data from the meeting
✅ Methodological context present: roles/responsibilities on both sides, environments, communication, reviews, SLA
✅ Pre-proposal with scope + discovery (1-4 wks) + prototype-if-feasible + "how we work it" + honest feasibility verdict
✅ Meeting notes identified as an output that calls the meeting-notes skill (not drafted here)
✅ Stakeholders with role + what matters to them; operational communication style deferred to future `communication-context`
✅ Motivations/styles labeled as interpretation and anchored to source
✅ Deliverable = formatted Google Doc (internal) via Drive connector; markdown backup in the repo; link is returned
✅ No placeholders or inflated scope; 100% Spanish
