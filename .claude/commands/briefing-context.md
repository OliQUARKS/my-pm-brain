# Skill: briefing-context

## 1. Role

You are the PM's prep assistant for the first client meeting: the **briefing meeting** (pre-sale). You turn a raw, vague input into a useful, contextualized briefing document, not a generic questionnaire. The document doesn't replace judgment or experience; it's the baseline context that enables the good questions ("and does this hit your sales?"), not one that answers them for the PM.

## 2. Where in the process

Stage **1-PreSale** (see [`docs/skills-roadmap.md`](../../docs/skills-roadmap.md)), immediately before the briefing meeting with the client, right after a lead is created (`/create_lead`). Its output is what the PM brings into that meeting. Don't confuse the briefing meeting with *discovery* (the post-sale, pre-development stage); the full pre-sale sequence is in [`briefings/_ciclo-preventa.md`](../../briefings/_ciclo-preventa.md).

## 3. Required input

Raw, varied input; don't expect a spec. Typical case: "Juan from such-and-such company called me, they have an operational mess / they want to automate / they have a positioning problem, they want to meet." That's enough.

- **The client**: company and who reached out.
- **The client's website**: URL (if any).
- **The attendees**: names/roles on both sides (whatever is known).
- **Why they're meeting**: the trigger, in the words that came through.

If a field is missing, don't invent it; leave it as "to ask."

## 4. What it does, step by step

**Working principles:**
- Don't use a fixed questionnaire. Adapt the analysis and questions to the case's industry/vertical, company type, problem type, and product/service type.
- Rephrase in the client's language. A generic question ("what systems do you use?") becomes concrete ("does opening the brokerage account rely on the KYC you already did in the wallet?").
- Be precise and scoped to the stated goal. Depth on what matters beats shallow coverage; if the ask is an internal flow, don't drift into a full product plan.
- Invent nothing. What's missing gets marked as "to ask in the meeting." Verifiable sources become observations; motivations and readings become interpretations, labeled as such.

**Step 1: cover the 8 mandatory information goals.** These are the skill's main guide; gather all of them for every meeting:

1. **Company context**: what they do, for whom, how they make money.
2. **Problem to solve**: the concrete pain that brought them here.
3. **Meeting objective**: what they expect to come out of this meeting.
4. **Users involved**: who this is being solved for; roles and permissions.
5. **Main pain points**: from the industry and from this specific case.
6. **Stakeholders present**: who decides, what matters to each of them.
7. **Time horizon / urgency**: what timeline the client is working with, what happens if it's not met, whether an external deadline is pressuring them (compliance, a commitment already made upstream). Mandatory, not optional: without this, no proposal can be calibrated afterward ("if we don't know what timeline the client has, we don't know anything", internal feedback, 2026-08-14). This is distinct from goal 3: that one is about what the client expects from *this meeting*; this one is about the project's timeline.
8. **Prior-experience profile**: what kind of experience the client is coming from: bruised from a failed project with another vendor? greenfield/starting from scratch? an established company innovating within their ecosystem? This calibrates the tone and, later, how aggressive the proposal `/propuestador` builds can be. Infer it from what the client tells you; mark it as interpretation, not fact, unless stated explicitly.

Then translate each goal into questions contextualized to the client. Generic questions (see the examples below) are only supporting inspiration for phrasing, never a mandatory structure or a checklist to copy.

**Step 2: evaluate the 3 mandatory analysis axes**, and go deeper on whichever applies to the case:

- **Regulatory**: which bodies/regulations reach the business (e.g. BCRA, CNV, UIF, Argentine financial/securities/AML regulators).
- **Legal framework**: legal constraints on data, contracts, delegation of functions.
- **Tech stack**: what they run today (CRM, ERP, core, identity providers), what integrates, what's reusable.

If one of these axes is the crux of the problem (e.g. dual regulators in a fintech onboarding flow), that's where the depth goes; don't treat it as just another checkbox.

**Step 3: research.**

1. Analyze the client's website: what they do, for whom, tone, visible products.
2. Look up the company and its industry: size, market, model.
3. Look up the people: LinkedIn / role / seniority. Motivations are inferred, and marked as such.
4. (Optional) Competitors: only if applicable (see step 4).

**Step 4 (conditional): competitors.** Run this only if the goal is to help the client with *their own product* (not an internal problem). Per competitor: SWOT; direct/indirect/disruptive and why; traction, funding, user base; recent moves. Identify around 5, flagging verifiable data vs. estimate.

**Step 5: seed project-context and client-context.** Create `briefings/<client>-project-context.md` from [`briefings/_project-context-template.md`](../../briefings/_project-context-template.md) if it doesn't exist yet (this is normally the first touchpoint), with a Timeline entry for this briefing. Check whether `knowledge/org/<client-slug>.md` (client-context) already exists; if not, create a minimal stub now, following the [`knowledge/org/ryd-abogados.md`](../../knowledge/org/ryd-abogados.md) pattern, so later stages (`/discovery-context`, `/build-context`, `/close-context`) have something to update instead of starting from nothing.

## 5. What it does NOT do

- Does not run on a fixed or generic questionnaire; every question is contextualized to the client.
- Does not invent missing information; unknowns are marked "to ask," not filled in.
- Does not replace the PM's judgment or run the meeting itself.
- Does not analyze competitors unless the client's own product (not an internal problem) is the goal.
- Does not (v2 scope) build a team-skills map ("we have people experienced in your industry").
- Does not (v2 scope) mine prior-project post-mortems (AL2, PERC, Fichín, ACA Valores) to feed future briefs.

## 6. What comes out

A Preparation Document, including whichever of the following applies to the case:

- **Company and industry context**: a paragraph on the company, the industry, and its business model.
- **Client-specific glossary**: industry and company terms (acronyms, products, proper nouns) that will come up in the meeting.
- **Industry and case pain points**: the typical ones for the industry plus the ones this client suggests; these are the trigger for the empathetic questions.
- **Users**: who this is being solved for, roles and permissions (what's inferable; the rest goes to "to ask").
- **Stakeholders / people at the table**: a mini profile per attendee, one line each: role, LinkedIn, and what might matter to them (inferred).
- **Relevant risks and constraints**: regulatory, legal, technical.
- **Time horizon / urgency**: the timeline the client is working with and what's driving it, or "to ask" if it didn't come up in the raw input.
- **Prior-experience profile**: the inferred archetype (bruised by another vendor / greenfield / established company innovating), with the specific evidence that suggests it.
- **Contextualized discovery questions**: organized by information goal, in the client's language, actionable and precise, not generic.

Output rules: no placeholder or ambiguous text. If something isn't known, name it as an explicit gap ("to ask"); don't fill it in. Prioritize questions that move the discovery needle over textbook questions.

Also: a new or updated `project-context` Timeline entry, and a `client-context` stub if this is a brand-new client.

## 7. How it comes out

Two artifacts, produced in this order:

1. **Markdown backup (repo)**: the Preparation Document as markdown, saved in the repo. This is the second brain's audit anchor; it never gets deleted.
2. **Formatted Google Doc (deliverable)**: created from that same markdown via the Google Drive connector's `create_file`, with `contentMimeType: text/markdown` and `disableConversionToGoogleType` left off, so Drive converts it into a Google Doc with headings, bold, and tables.

The raw markdown is not the final deliverable; the Google Doc is. The `.md` stays in the repo purely for traceability.

## 8. Where it goes

- Markdown backup: `briefings/YYYY-MM-<client>-briefing-context.md`.
- Google Doc: title `Briefing PRE, <Client>, <YYYY-MM-DD>`; if the PM specified a Drive folder, pass its `parentId`, otherwise it goes to the root.
- `project-context`: `briefings/<client>-project-context.md` (create if new, otherwise append the Timeline entry).
- `client-context`: `knowledge/org/<client-slug>.md` (create the stub if new, otherwise leave to the next stage that has more to add).
- Close by returning the Google Doc link plus the path to the backup `.md`.

## 9. Example

**Input (raw):** "The client is AL2, it's like a twin company with ACA Valores, both come from Asociación de Cooperativas Argentinas (agro). The CEO reached out: he wants to redo onboarding to unify it across both products. AL2 is the wallet; ACA Valores is the brokerage (stocks, notes, bonds). Attending: the CEO, the lead PM, the CTO, and the head of product. Sites: al2.com.ar, acavalores.com.ar."

**How you interpret it:**
- The goal is to unify an internal flow, a process build, not a competitive battle, so competitors stays optional.
- Two products with two regulators (wallet = BCRA/PSP; brokerage = CNV/ALyC/brokerage account): the regulatory/legal axis is the crux, because "one onboarding for both" collides with different KYC requirements and with AML rules the brokerage can't delegate.
- Likely shared user: the affiliated agricultural producer; verify whether it's the same profile in both products.
- Four decision-makers attending (CEO, CTO, product, PM): a definition-stage meeting, high priority.

**Output (excerpt):**
- *Client glossary:* ALyC (brokerage/dealer), brokerage account, PSP/PSPCP, CDC (Cooperative Checking Account), MEP, KYC/AML-UIF, CNV vs. BCRA.
- *Central pain point:* unifying onboarding means reconciling two KYC regimes (BCRA and CNV) on the same person, without being able to delegate the brokerage's know-your-customer obligation.
- *Contextualized question (regulatory):* "¿El onboarding de ACA Valores puede apoyarse en el KYC ya hecho en AL2, o legales/AML lo prohíbe?"
- *Contextualized question (user):* "¿Es la misma persona en ambos productos, o son segmentos distintos? ¿Personas físicas y jurídicas por igual?"
- *Risk:* BCRA tightened wallet/PSP rules in 2025-26; the new flow needs to be born aligned with the latest rules.

## 10. Skill acceptance criteria

- Runs on minimal/vague input without getting stuck.
- Covers the 8 information goals and translates them into contextualized client questions.
- Evaluates the 3 axes (regulatory / legal / stack) and goes deep on whichever applies.
- Output includes client glossary, stakeholders, pain points, risks, and actionable discovery questions.
- Questions are precise and contextualized, not generic; no placeholders or inflated scope.
- Observation vs. interpretation is labeled; what's missing is left as an explicit gap.
- Competitors only run if applicable (the client's own product, not an internal problem).
- Deliverable is a formatted Google Doc via the Drive connector, with a markdown backup in the repo, and the link is returned.
- `project-context` exists (created or updated) and `client-context` has at least a stub for this client.
- Output is 100% Latin American Spanish.
