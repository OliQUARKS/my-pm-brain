# Skill: propuestador (builds the client-facing proposal, POST build-context)

**Your goal:** turn the `/build-context` (internal) into the proposal document delivered to the client. This isn't a summary of the context: it's the commercial piece that lays out what we understood, what we propose, what it does, how we work, and where it scales; written in professional, positive, closed language, ready to be read on the other side. Ultimate goal: get the client to say yes.

## The three layers: where this comes from and what it is

1. **Project context** (`/build-context`): **INTERNAL**. The input. Never delivered. From it comes the **4. Proposal** section (scope/discovery/prototype/feasibility) that this skill expands.
2. **Proposal** (this skill): **CLIENT-FACING**. The document that gets shared. It takes the pre-proposal from the build-context and turns it into a complete, professional, navigable document. Functional scope + how we work + roadmap. Amounts and the locked-in team go on a separate budget sheet (see § Operational output).
3. **Real proposal / contract**: post-"yes." Team lock-in, timeline, cost, and discovery kickoff. Not built here.

## Golden rule: internal never crosses into client-facing

The build-context has material that must never appear in the proposal. When deriving, leave out:

- **Amounts, rates, margins**: go on the separate budget sheet, not in the functional body.
- **Internal tensions and stakeholder reads**: skepticism, "start small as a tactic," who the gatekeeper is, what irritates whom.
- **Competitor analysis / how we win the deal.**
- **Unresolved feasibility doubts**: open items get named as "to be defined during discovery," never as "we don't know if we can do this."
- **Internal risk names, lessons from other clients, internal assets** (e.g.: "we're reusing X's CRM").

If something in the build-context is internal, it stays in the build-context. The proposal talks about value for the client, not about our own kitchen.

## How you work

- **You derive, you don't invent.** Every claim in the proposal is backed by the build-context (`briefings/<date>-<client>-build-context.md`) and its sources. Nothing new that isn't supported.
- **Professional, complete language.** Neither telegram-style bullets nor inflated prose. Each point says what it is and why it benefits the client. The register matches the client's (Spanish, the tone of their industry).
- **Sharp MVP, future kept separate.** What's in the MVP is clearly distinguished from what's a later phase. Don't promise the roadmap as if it were the MVP.
- **Iterative.** The first version is the base; it gets reviewed with the team and "sweetened" (more professional, more detailed language) before sending. Workflow diagrams (added by whoever owns that) and the budget sheet get added at the end.

## Input

- The project's `/build-context` (section **4. Proposal** as the skeleton; sections 1-3 and feasibility as input).
- Internal decisions already made (MVP scope vs. phases, design yes/no, way of working).
- Client mockups/prototypes, or ours, if any exist.
- Corrections from the internal review (what the team flagged reviewing the draft).

## Document structure: the 7 sections

Adapt the titles to the case, but this is the skeleton that works:

1. **What we understood.** The client's problem in their own language, with the concrete pain point and why now. Shows we listened. One or two sentences, no roundabout.
2. **The solution in one sentence.** What the product is, stated simply. If it has multiple faces (e.g.: end-user app + internal panel), name them here.
3. **What it does: MVP functionality.** The core. Broken down by product face when it applies (e.g.: A. Client app / B. Internal panel). Each feature in one clear line. Close with an explicit **"Out of MVP (later phases)"** block that lists what's deferred; it protects scope.
4. **How it plugs into the client's systems.** When there's legacy or an in-house IT team: make crystal clear that we're not replacing anything, what gets consumed/read vs. what keeps living in their system, and how it integrates (middleware/services, sync cadence). Lowers the client's technical anxiety.
5. **How we work.** Methodology (agile/Scrum), initial alignment stage, phased implementation, transparent management (meetings, visibility, documentation), quality/validation (live testing, adoption), and client ownership + long-term partnership. Each point with its "why"; this is the section that builds the most trust. Professional, developed register, not telegraphic.
6. **Future roadmap.** The phases after the MVP, framed as a path of value, not as an included promise.
7. **Next steps.** Concrete actions to move forward (closing technical points, a demo of prior work, confirming inputs, kicking off).

## Angles to watch depending on the case

- **Legacy / client's own IT** → section 4 is critical; emphasize integration and ownership.
- **Design-sensitive client** → name the experience/aesthetics as part of the value (not as a cost).
- **Product facing captive users** → adoption is part of the project, say so in section 5.
- **Regulated** → where compliance applies, without overpromising.

## Operational output

- **Markdown backup** (repo): `briefings/<date>-<client>-propuesta.md`. Audit anchor; never deleted.
- **Formatted Google Doc** (client-facing, editable), from that same markdown via the Google Drive connector:
  - Tool: `create_file` from the Google Drive connector.
  - `title`: `Propuesta, <Client>, <YYYY-MM-DD>`.
  - `textContent`: the body of the 7 sections (no amounts or budget).
  - `contentMimeType`: `text/markdown`; do not enable `disableConversionToGoogleType`.
  - If the PM specified a Drive folder, pass its `parentId`; otherwise it lands in the root.
- **Budget sheet**: added as a final section/sheet, separate from the functional body (e.g. `briefings/<date>-<client>-propuesta-presupuesto.md` or a separate tab in the Doc). Team, timeline, investment. Filled in at the PM's judgment (amounts are never invented by the skill).
- **Workflows / diagrams**: added by whoever owns that as an appendix; this skill leaves the placeholder (reference) but doesn't draw them.
- **Close-out to the PM:** `.md` path + Google Doc link + what's ready + what's still missing before sending (budget, workflows, final "sweetening") + gaps the client needs to confirm.

Follow `CLAUDE.md § Operating preferences § Autonomy mode`. Under `propose and wait`, present the draft and wait for confirmation before saving/creating the Doc.

## Worked example: Lodiser (professional channel)

**Input:** Lodiser build-context (closed B2B ecommerce) + internal decisions (with design, phased kickoff) + review corrections.

**How you derive it:**

- The build-context's pre-proposal ("PWA front + login + saves header/detail against the DB that Lodiser serves") becomes the functional body, broken down into **A. Client web app** (catalog, my regulars, cart with stock/quota/price/credit controls, checkout without payment, tracking) and **B. Lodiser panel** (customer CRUD, order entry by the salesperson, dashboard, view by product/client/salesperson).
- Section 4 makes clear the platform replaces nothing: it consumes the masters/controls via lightweight middleware and only records the order; the catalog is read-only (product/price CRUD stays in their system).
- Left out (internal): the systems manager's skepticism, the internal asset for the WhatsApp phase, the amounts, and the "start small" tactic.

**Output (excerpt):**

- *What we understood:* orders depend 100% on the salesperson manually entering them from WhatsApp voice notes → sales are lost outside business hours.
- *How we work:* initial alignment stage with the systems team + Scrum + phased implementation with clients jointly defined + client ownership. Each point with its "why."
- *Roadmap:* data/marketing, WhatsApp (bot that takes orders), other channels.

## Out of scope

- Final team/timeline/cost lock-in (post-"yes," in the real proposal/contract).
- The meeting notes (`/minutero`).
- Workflow/diagram design (contributed by whoever owns that; this skill leaves the placeholder).

## Quality criteria

✅ Derives from the build-context (`/build-context`), doesn't start from scratch; every claim backed
✅ Internal never crosses over: no amounts in the body, no tensions/stakeholders/competitors/internal assets
✅ The 7 sections present and adapted to the case; MVP sharp and separated from the roadmap
✅ Section 4 (support on the client's systems) present when there's legacy/in-house IT
✅ "How we work" developed and professional, each point with its "why"
✅ Explicit "Out of MVP" block to protect scope
✅ Budget and workflows identified as separate sheets/appendices (not in the functional body)
✅ Open items named as "to be defined during discovery," never as a feasibility doubt
✅ Deliverable = formatted Google Doc (client-facing) via the Drive connector; markdown backup in the repo; link returned
✅ No placeholders or inflated scope; 100% Spanish, client's register
