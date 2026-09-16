# Skill: prototipador (builds the navigable functional prototype, POST build-context)

**Your goal:** turn what we understood about the client into a **navigable functional prototype**: a self-contained, clickable HTML/CSS/JS file that shows the core screens of the envisioned MVP. It's not a static mockup or a document: it's something the client opens, navigates, and "touches." Ultimate goal: get the client to *see* the solution and say yes.

**100% private use (never published as an Artifact).** The prototype contains client information (brand, workflows, sometimes example data close to the real thing). A published Artifact is reachable by anyone who has the link (and potentially indexable if the link leaks); that is exactly what this skill has to avoid. The deliverable is always the `.html` as a file, never a public link (change made 2026-08-14, see [ingestion/meetings/2026-08-14-sync-jony-preventa-feedback.md](../../ingestion/meetings/2026-08-14-sync-jony-preventa-feedback.md)).

## Where it fits in the cycle

See [`briefings/_ciclo-preventa.md`](../../briefings/_ciclo-preventa.md). Runs **after `build-context`**. Its relationship to [`/propuestador`](./propuestador.md) depends on whether `propuestador` ran in multi-path mode (see `propuestador.md § Phase 0`):

- **If `propuestador` already decided a path** (passed its Phase 0 checkpoint) → prototype **that chosen path**, not the raw build-context. This is the default since the `propuestador` redesign.
- **If `propuestador` hasn't run yet, or ran in "simple case" mode without comparing paths** → falls back to the usual behavior: prototype directly from the build-context (§ Hard gate below).
- If the case warrants prototyping more than one path (uncommon, only if the team explicitly asks for it), it's fine to generate more than one `.html`, one per path.

## Hard gate: no brief, no prototype

- **Ideal:** the path decided by `propuestador` exists (or, if `propuestador` didn't run in multi-path mode, the client's `build-context`) → the MVP screens get prototyped with a solid basis.
- **Minimum acceptable:** there's a `briefing-context` plus a briefing transcript → a more conceptual prototype (fewer screens, more simulated).
- **Less than that (only a cold start, no meeting held):** **don't build it.** Say so and stop. Prototyping without having listened to the client is inventing.

## Golden rule: client-facing, internal never crosses over

Same criterion as `/propuestador`. The prototype shows **the product**, never our own kitchen: no internal tensions, no stakeholder reads, no competitors, no amounts, no reused internal assets. If something is internal, it stays in the build-context.

**Watch out: internal product logic ≠ client UI.** What the system **validates behind the scenes** (stock/quota/price/credit controls, business rules, approval queues) is one thing, and what the **end user sees** is another. Those controls don't get shown as a checklist on the client's screen; they surface through their UX (a stock badge, their account balance, a message if something doesn't check out), and their **full view lives in the backoffice**, not in the client's app. For every block, ask yourself: "does the client see this, or is it internal operation?"

## Branding: three-level cascade

1. **The client's brand manual (if they sent one).** Colors, typefaces, logo, visual tone. **Everything inline, no exceptions**: palette as CSS variables, logo/images as `data:` URIs, embedded typefaces or the closest system fallback. No `<link>` to external fonts or CDNs. This is no longer an Artifact technical constraint (we stopped publishing there); it's a rule kept **for the same privacy reason**: a 100%-private file shouldn't be making calls to external servers (metadata leak that the file was opened, plus a dependency on internet access if it's sent as an offline attachment).
   - **Logo and typography = assets, not improvised.** The manual usually **prohibits altering the logo's composition**, and external webfonts are ruled out by the rule above. If you don't have the logo in usable SVG/PNG or the font file to embed as a `@font-face` data URI, **prototype with an approximation but label it as such** (approximate logo / system stack that evokes the original) and **flag the official asset as a gap** to request. Don't distort the real logo to make it "fit."
2. **No manual, but researched web presence.** Derive the palette and style from the client's sites already researched by `briefing-context`/`build-context` (brand colors, typeface, visual density of the industry).
3. **Nothing available.** Clean, neutral, standard system look, sober, fit for the industry. Don't invent a fake brand identity.

## Prototype scope

- **Navigable MVP, not the real product.** Clickable flows with **mocked data**; no backend, no real auth, no live integrations. What's simulated looks simulated (obviously example data, not figures that look like real client numbers).
- **Core screens first.** From the build-context's MVP scope, pick the happy path that best demonstrates the value. Don't cover the whole roadmap; that confuses MVP with future.
- **Format: web vs. mobile (a decision, not a default).** Choose based on the product and its users: a backoffice/internal panel or a B2B web app is **desktop web** (don't frame it inside a phone); a consumer app or one for field workers is **mobile-first**. A PWA can be either: define which is the case's primary view. Don't shove everything into a phone frame out of habit.
- **A two-sided product → prototype both sides (or state which one is missing).** Many products have **a client app + an internal panel**. If the build-context's scope lists both, the prototype should ideally show both (with a switch to toggle between them), or at least explicitly say which one was left pending and why.
- **Responsive and theme-aware** by default (the file looks right in light/dark, and at the width appropriate to the chosen format).
- **Feasibility honesty.** If the real flow isn't prototypable (e.g.: depends on a WhatsApp or ERP integration), prototype the part that does show value and leave the rest as a labeled illustrative screen; never simulate a capability we won't be able to deliver.

## UX best practices: happy path

These are the decisions that separate a prototype with judgment from an improvised one. They apply only to the happy path; this isn't an edge-case checklist.

- **Clear visual hierarchy.** One primary action per screen, visually dominant (size/color/position). Secondary actions don't compete with it.
- **Immediate feedback.** Every action along the happy path responds visually: active state, confirmation, transition. The user never clicks "into the void."
- **Component consistency.** Same button/card/input pattern repeated across every screen of the prototype. Don't reinvent the pattern screen by screen.
- **Predictable navigation.** The user always knows where they are (active tab, section title, breadcrumb if it applies) and how to go back.
- **Minimal cognitive load.** Show only what the happy path needs at each step, not every field/option at once.
- **Clear affordance.** What's clickable looks clickable; non-interactive elements don't disguise themselves as buttons.
- **Readable forms.** Visible labels (not just placeholder text), logical field grouping, field size matching the expected data.
- **Density suited to the product.** A backoffice/internal panel tolerates more information density; a consumer app, less.
- **Basic accessibility.** Sufficient contrast for text and CTAs, tap targets ≥44px on mobile.

## How you work

1. Load the **best context available** (build-context if it exists; otherwise briefing-context) + branding (manual / web / standard).
2. **Before writing the Artifact, load the `artifact-design` skill**; it calibrates how much design the case warrants.
3. Define the minimum set of screens for the MVP's happy path.
4. Before writing each screen, review § UX best practices (happy path).
5. Write the self-contained HTML/CSS/JS (everything inline, no external calls) as a single file. **Don't publish it with the `Artifact` tool**; it stays a file, never a link.
6. Save it versioned in the repo and close out with the PM (see § Output); distribution to the client is the PM's decision and action, not the skill's.

## Input

- **The build-context** of the project (MVP scope from `§ B`, users/roles from `§ A3`), or the briefing-context if the build-context doesn't exist yet.
- **The client's brand manual**, if they sent one.
- **Research on the client's websites** gathered by prior skills (to derive style if there's no manual).
- **Internal decisions** on scope (what's in the MVP, with design or not).

## Output

1. **HTML file versioned in the repo:** `briefings/<YYYY-MM>-<client>-prototipo.html`, self-contained, clickable locally in the browser. **This is the deliverable**, not a backup.
2. **Backup note:** `briefings/<YYYY-MM>-<client>-prototipo.md`: which screens were prototyped, where the branding came from (manual/web/standard), what was left mocked or illustrative, what's still needed to make it real.
3. **Close-out to the PM:** `.html` and `.md` paths + what was prototyped + what stayed simulated + gaps the client needs to confirm. The PM decides how and when it reaches the client (attached via their private channel); the skill doesn't publish or share anything.

> **Bridge to Figma (optional, evaluate case by case).** Without a public Artifact link, importing into Figma requires uploading the `.html` through some other private channel (or generating a temporary Artifact just for that specific purpose and deleting it afterward). Not the default; only if design explicitly asks for it, weighing whether the privacy exception is worth it for that case.

## Out of scope

- The client-facing **proposal** (commercial document) → [`/propuestador`](./propuestador.md).
- The meeting notes → [`/minutero`](./minutero.md).
- A real product with backend / live integrations → post-sale, not here.

## Quality criteria

✅ Gate respected: without at least a briefing meeting, it doesn't get built
✅ If `propuestador` ran in multi-path mode, prototypes the chosen path, not the raw build-context without a decision
✅ Deliverable = self-contained, navigable (clickable) `.html` file, **never published as an Artifact**
✅ Branding cascade respected: manual → researched web → standard; everything inline (no external fonts/CDNs), for privacy and portability
✅ Client-facing: no amounts, tensions, stakeholders, competitors, or internal assets
✅ MVP sharp, happy path; what's simulated looks simulated; roadmap isn't prototyped as if it were the MVP
✅ Every happy-path screen respects the § UX best practices checklist (hierarchy, feedback, consistency, navigation, cognitive load, basic accessibility)
✅ Feasibility honesty: no simulating a capability we won't be able to deliver
✅ Responsive + theme-aware
✅ `.html` source versioned in the repo + `.md` note + close-out returned to the PM
✅ No placeholders or inflated scope; 100% Spanish, client's register
