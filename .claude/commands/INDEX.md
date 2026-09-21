# Commands

Operator-facing verbs. Each command is a thin spec: input, files to load, files to update, what to surface. The agent reads the spec, executes against the brain, and reports back per `CLAUDE.md § Operating loop`.

| Verb | When to run it |
| --- | --- |
| [`/ingest`](./ingest.md) | Any new artifact lands (interview, meeting notes, market signal, ad-hoc note) |
| [`/prep`](./prep.md) | Before a 1:1, exec review, roadmap discussion, or any stakeholder conversation |
| [`/review`](./review.md) | Weekly maintenance sweep (default: Friday) |
| [`/hypothesize`](./hypothesize.md) | Generate or refresh hypotheses for a feature (pre-ship across the 5 risk areas, or post-ship from data) |
| [`/decide`](./decide.md) | Log a decision: draft the file from the evidence trail, surface for PM sign-off |
| [`/strategy-check`](./strategy-check.md) | Drift check between recent decisions / hypotheses / ingestion and `knowledge/strategy.md` |
| [`/ideate`](./ideate.md) | A problem needs solution directions grounded in existing evidence and hypotheses |
| [`/risk`](./risk.md) | A feature or plan needs the 5-area risk scan; maps to hypothesis hygiene |
| [`/plan`](./plan.md) | A new objective lands; turn it into discovery questions, interviews, experiments, hypotheses, decision points |
| [`/review-prd`](./review-prd.md) | Adversarial panel on a PRD: 5 lenses (strategist, customer, data, risk, stakeholder) load their section of the brain and critique from their angle |

## Quarks engagement pipeline (see `docs/skills-roadmap.md`)

In roughly the order they run across an engagement, 1-PreSale through 6-Post.

| Verb | When to run it |
| --- | --- |
| [`/briefing-context`](./briefing-context.md) | Prepare a first meeting (pre-sale): surfaces information objectives plus regulatory/legal/stack angles → Prep Document with contextualized discovery questions |
| [`/minutero`](./minutero.md) | After the briefing (pre-sale): draft client-facing meeting minutes, validating what was understood, requesting evidence, and requesting a meeting with the decision-maker → Google Doc + backup `.md` |
| [`/discovery-context`](./discovery-context.md) | Post-briefing (formerly `/build-context`, formerly `/post-briefing-context`): builds the project's internal context (expanded problem, users, stakeholders, methodological context) plus client-facing pre-proposal (scope, discovery, prototype) |
| [`/propuestador`](./propuestador.md) | Post discovery-context: converts the internal pre-proposal into the client-facing proposal document (7 sections) → Google Doc + backup `.md` |
| [`/discovery-prep`](./discovery-prep.md) | Start of paid Discovery (etapa 7): open-questions map across functional/technical/design/methodological + recommended 2-4 methodology combo from the discovery toolkit |
| [`/build-context`](./build-context.md) | At the close of paid Discovery, before `/prd-writer`: consolidate every discovery session that ran into one project bible; not to be confused with `/discovery-context` |
| [`/prd-writer`](./prd-writer.md) | Write a strategic PRD from `/build-context` or a problem/feature idea (context, goals, non-goals, scope by capability, metrics, phasing); hands off to `/backloguer` |
| [`/dod-dor`](./dod-dor.md) | Once the PRD exists: define the project-wide Definition of Ready / Definition of Done baseline that `/backloguer` applies at the epic level |
| [`/backloguer`](./backloguer.md) | Break down a PRD into epics (EP-XX, backbone, functional exclusivity, MVS/Midgame/Endgame slicing) then into INVEST stories (EP-XX-US-YY); on close, option to push to ClickUp |
| [`/trf`](./trf.md) | During Build: track tasks/owners/dates from the sprint's recurring meetings, flag overdue items, keep the client communication channel updated |
| [`/postmortem`](./postmortem.md) | At project close (post-UAT, post-manual): committed vs. delivered scope, what worked/didn't, reusable knowledge, proposed process changes flagged for review |
| [`/close-context`](./close-context.md) | Right after `/postmortem`: final update to `project-context` (status → cerrado) and `client-context`, or creates them if this was the client's first project |

`/briefing-context`, `/discovery-context`, `/build-context`, and `/close-context` each also update two shared, mutating artifacts as a side effect (added 2026-09-21): `project-context` (one file per engagement, `briefings/<client>-project-context.md`, see [`briefings/_project-context-template.md`](../../briefings/_project-context-template.md)) and `client-context` (one file per client, `knowledge/org/<client-slug>.md`, spans multiple projects over time).

## Discovery toolkit (stage 7)

Post-sale, pre-development; the client already signed. One skill per methodology; pick 2-4
per engagement, don't run the whole catalog. Selection logic (client maturity → combo) lives in
[`briefings/_kit-discovery.md`](../../briefings/_kit-discovery.md).

| Skill | When to run it |
| --- | --- |
| [`/discovery-business-model-canvas`](./discovery-business-model-canvas.md) | Client's own business model isn't clear yet, or this is a new line inside an existing company |
| [`/discovery-value-proposition-canvas`](./discovery-value-proposition-canvas.md) | Sales pitch confuses features with value proposition; forces precision |
| [`/discovery-jtbd`](./discovery-jtbd.md) | Client talks in features, not needs; real users exist to interview |
| [`/discovery-stakeholder-mapping`](./discovery-stakeholder-mapping.md) | Always early; the signer isn't always the decider |
| [`/discovery-interview-guide`](./discovery-interview-guide.md) | Client has no research at all; base technique for everything else |
| [`/discovery-journey-map`](./discovery-journey-map.md) | Digitizing/improving a process that already exists offline or in another system |
| [`/discovery-empathy-map`](./discovery-empathy-map.md) | Light icebreaker before a deeper exercise, stakeholders new to UX workshops |
| [`/discovery-service-blueprint`](./discovery-service-blueprint.md) | Problem is operational, not just interface; manual processes, backstage systems |
| [`/discovery-diary-study`](./discovery-diary-study.md) | Budget/time available and stated behavior likely diverges from real behavior |
| [`/discovery-story-map`](./discovery-story-map.md) | Client's product counterpart already speaks epic/story |
| [`/discovery-impact-map`](./discovery-impact-map.md) | C-level wants to see the business goal before the feature list |
| [`/discovery-opportunity-tree`](./discovery-opportunity-tree.md) | Real ambiguity on which problem to attack first, and interview cadence to sustain it |
| [`/discovery-event-storming`](./discovery-event-storming.md) | Complex domain, many business rules (fintech, legal, logistics) |
| [`/discovery-impact-matrix`](./discovery-impact-matrix.md) | Converging a batch of already-voiced ideas before committing scope |
| [`/discovery-premortem`](./discovery-premortem.md) | Before commitments harden; surfaces risks nobody says out loud |

## Conventions

- Every command loads before acting and updates after. No blind drafting.
- Every command ends by surfacing 2-4 bullets per `CLAUDE.md § Operating loop § 7`.
- `/prep` is read-only at call time. The operator runs `/ingest` after the conversation. All other commands draft or update files per autonomy mode.
- Commands respect `CLAUDE.md § Operating preferences § Autonomy mode`. Under `propose and wait`, drafts are presented for approval before saving.
- All file paths in each spec are relative to the brain root.

## Scope: what these verbs are not

PM Brain is the memory and reasoning layer. PM workflows (JTBD interview structure, Kano analysis, RICE prioritization, opportunity solution trees, experiment design templates) belong in workflow-specific skills, not here. A workflow skill produces an artifact; PM Brain ingests it via `/ingest` and routes the evidence into durable layers. The split keeps each system thin.
