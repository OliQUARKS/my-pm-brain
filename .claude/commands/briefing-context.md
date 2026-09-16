# Skill: briefing-context (PRE)

**Your goal:** prepare better for the first meeting, the **briefing meeting** (pre-sale), by identifying **what information we need to obtain** and **what questions make sense given the client's context**. You turn a raw, vague input into a useful briefing, not a generic questionnaire.

> **Where it fits:** stage 2 of the cycle (see [`briefings/_ciclo-preventa.md`](../../briefings/_ciclo-preventa.md)). Prepares the briefing meeting; don't confuse that meeting with *discovery* (the post-sale, pre-development stage).

## Purpose

That whoever goes to the meeting arrives **with context, not empty-handed**: able to touch a nerve from minute one, so the conversation stops being "here's what we do" and becomes something else. The doc **doesn't replace judgment or experience**; it's the baseline context that enables the good questions ("and does this hit your sales?"), not one that answers them.

## How you work

- **Don't use a fixed questionnaire.** Adapt the analysis and questions to the case's **industry/vertical, company type, problem type, and product/service type**.
- **Rephrase in the client's language.** A generic question ("what systems do you use?") becomes concrete ("does opening the brokerage account rely on the KYC you already did in the wallet?").
- **Precise and scoped to the stated goal.** Depth on what matters > shallow coverage. Don't inflate scope: if the ask is an internal flow, don't drift into a full product plan.
- **Nothing invented.** What's missing gets marked as "to ask in the meeting." Verifiable sources → observation; motivations and readings → interpretation, labeled.

## Input

Raw, varied input; **don't expect a spec**. Typical case: "Juan from such-and-such company called me, they have an operational mess / they want to automate / they have a positioning problem, they want to meet." That's enough.

- **The client**: company and who reached out.
- **The client's website**: URL (if any).
- **The attendees**: names/roles on both sides (whatever is known).
- **Why they're meeting**: the trigger, in the words that came through.

If a field is missing, don't invent it: leave it as "to ask."

## What you absolutely have to understand: information goals

These goals are **the skill's main guide**. For every meeting, always gather:

1. **Company context**: what they do, for whom, how they make money.
2. **Problem to solve**: the concrete pain that brought them here.
3. **Meeting objective**: what they expect to come out of this meeting.
4. **Users involved**: who this is being solved for; roles and permissions.
5. **Main pain points**: from the industry and from this specific case.
6. **Stakeholders present**: who decides, what matters to each of them.
7. **Time horizon / urgency**: what timeline the client is working with, what happens if it's not met, whether there's an external deadline pressuring them (compliance, a commitment already made upstream). **Mandatory, not optional:** without this, no proposal can be calibrated afterward ("if we don't know what timeline the client has, we don't know anything", internal feedback, 2026-08-14). Different from objective #3: that one is about what they expect from *this meeting*; this one is about the project's timeline.
8. **Prior-experience profile**: what kind of experience the client is coming from: are they arriving bruised from a failed project with another vendor? are they greenfield/starting from scratch? are they an established company innovating within their ecosystem? This calibrates the tone and, later, how aggressive the proposal `/propuestador` builds can be. Inferred from what the client tells you; mark it as interpretation, not fact, unless stated explicitly.

Then **translate each goal into questions contextualized to the client**. The generic questions further below are only **supporting examples** to inspire the phrasing, not a mandatory structure or a checklist to copy.

## Mandatory analysis axes

Besides the goals, always evaluate these three axes and **go deeper on whichever applies** to the case:

- **Regulatory**: which bodies/regulations reach the business (e.g.: BCRA, CNV, UIF, Argentine financial/securities/AML regulators).
- **Legal framework**: legal constraints on data, contracts, delegation of functions.
- **Tech stack**: what they run today (CRM, ERP, core, identity providers), what integrates, what's reusable.

If one of these axes is the crux of the problem (e.g. dual regulators in a fintech onboarding flow), that's where the depth goes; don't treat it as just another checkbox.

## What it processes / looks for

1. **Analyze the client's website**: what they do, for whom, tone, visible products.
2. **Look up info on the company and its industry**: size, market, model.
3. **Look up info on the people**: LinkedIn / role / seniority. Motivations are **inferred**, and marked as such.
4. **(Optional) Competitors**: only if applicable (see below).

## Output: Preparation Document

Include, **when it applies** to the case:

- **Company and industry context**: a paragraph on the company, on the industry, and its business model.
- **Client-specific glossary**: industry and company terms (acronyms, products, proper nouns) that will come up in the meeting and need to be handled.
- **Industry and case pain points**: the typical ones for the industry + the ones this client suggests. These are the trigger for the empathetic questions.
- **Users**: who this is being solved for, roles and permissions (what's inferable; the rest → to ask).
- **Stakeholders / people at the table**: mini profile per attendee: role, LinkedIn, and what might matter to them (inferred). One line per person.
- **Relevant risks and constraints**: regulatory, legal, technical.
- **Time horizon / urgency**: the timeline the client is working with and what's driving it, or "to ask" if it didn't come up in the raw input.
- **Prior-experience profile**: inferred archetype (bruised by another vendor / greenfield / established company innovating), with the specific evidence that suggests it.
- **Contextualized discovery questions**: organized by information goal, in the client's language. **Actionable and precise**, not generic.

Output rules: **no placeholder or ambiguous text.** If something isn't known, name it as an explicit gap ("to ask"), don't fill it in. Prioritize questions that move the discovery needle over textbook questions.

## Output format: formatted Google Doc (+ markdown backup)

This skill's deliverable is **always a formatted Google Doc**, never a standalone `.md`. Two artifacts are produced, in this order:

1. **Markdown backup (repo).** Generate the Preparation Document as markdown and save it where it already lives in the repo (`briefings/YYYY-MM-<client>-briefing-context.md`). It's the second brain's audit anchor; it doesn't get deleted.
2. **Formatted Google Doc (deliverable).** Create the document with the Google Drive connector from that same markdown:
   - Tool: Google Drive connector's `create_file`.
   - `title`: `Briefing PRE, <Client>, <YYYY-MM-DD>`.
   - `textContent`: the full markdown.
   - `contentMimeType`: `text/markdown`.
   - **Do not** enable `disableConversionToGoogleType`; let Drive convert the markdown into a Google Doc with headings, bold, and tables.
   - If the PM specified a Drive folder, pass its `parentId`; otherwise it goes in the root.
3. **Close by returning the Google Doc link** plus the path to the backup `.md`.

Rule: the raw markdown is not the final deliverable. The deliverable is the Google Doc; the `.md` stays in the repo purely for traceability.

## Supporting examples: generic questions

Only as inspiration for phrasing the contextualized ones. **Don't copy verbatim.**

- Problem/objective: what brought them to look for help now?, what changed?, how do they handle it today?
- Impact: does this affect sales/costs/time?, how do they measure it?, who deals with it daily?
- User/process: who is this being solved for?, roles/permissions?, what systems do they run today?
- Feasibility: what have they tried that didn't work?, do they have APIs/access/documentation?

## Worked example: from raw context to briefing

**Input (raw):** "The client is AL2, it's like a twin company with ACA Valores, both come from Asociación de Cooperativas Argentinas (agro). The CEO reached out: he wants to redo onboarding to unify it across both products. AL2 is the wallet; ACA Valores is the brokerage (stocks, notes, bonds). Attending: the CEO, the lead PM, the CTO, and the head of product. Sites: al2.com.ar, acavalores.com.ar."

**How you interpret it:**
- The goal is to **unify an internal flow** → a process build, **not** a competitive battle → competitors stays optional.
- Two products with **two regulators** (wallet = BCRA/PSP; brokerage = CNV/ALyC/brokerage account) → the **regulatory/legal axis is the crux**: that's where the depth goes, because "one onboarding for both" collides with different KYC requirements and with AML rules the brokerage can't delegate.
- Likely shared user: the affiliated agricultural producer → verify whether it's the same profile in both products.
- Four decision-makers attending (CEO+CTO+product+PM) → a definition-stage meeting, high priority.

**Output (excerpt):**
- *Client glossary:* ALyC (brokerage/dealer), brokerage account, PSP/PSPCP, CDC (Cooperative Checking Account), MEP, KYC/AML-UIF, CNV vs. BCRA.
- *Central pain point:* unifying onboarding means reconciling two KYC regimes (BCRA and CNV) on the same person, without being able to delegate the brokerage's know-your-customer obligation.
- *Contextualized question (regulatory):* "Can ACA Valores' onboarding rely on the KYC already done in AL2, or does legal/AML prohibit it?"
- *Contextualized question (user):* "Is it the same person across both products, or different segments? Individuals and legal entities both?"
- *Risk:* BCRA tightened wallet/PSP rules in 2025-26 → the new flow needs to be born aligned with the latest rules.

## Optional: competitors

Only run this **if** the goal is to help the client with **their own product** (not an internal problem). Per competitor: SWOT; direct/indirect/disruptive and why; traction, funding, user base; recent moves. Identify ~5, flagging verifiable data vs. estimate.

## Out of scope (v2)

Noted, **not** in this version:
- **Team skills map**: who's done mobile/fintech/management work, to be able to say "we have people experienced in your industry."
- **Prior experience by industry**: post-mortems of past projects (AL2, PERC, Fichin, Acavalores) to feed future briefs.

## Quality criteria

✅ Runs on minimal/vague input without getting stuck
✅ Covers the 8 information goals and translates them into contextualized client questions
✅ Evaluates the 3 axes (regulatory / legal / stack) and goes deep on whichever applies
✅ Output includes client glossary, stakeholders, pain points, risks, and actionable discovery questions
✅ Questions are precise and contextualized, not generic; no placeholders or inflated scope
✅ Observation vs. interpretation labeled; what's missing is left as an explicit gap
✅ Competitors only if applicable (product, not internal problem)
✅ Deliverable = formatted Google Doc via Drive connector; markdown backup in the repo; link is returned
✅ 100% Spanish
