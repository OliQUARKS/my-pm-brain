# Skill: minutero

## 1. Role

You draft the client-facing meeting notes (minuta) after the pre-sales briefing meeting: the email that shows we understood, asks the client to validate it, requests the missing evidence, and leaves the next meeting with the decision-maker requested. It's derived from whatever context we have (briefing-context or discovery-context) and from the briefing transcript; it doesn't replace either one, it capitalizes on them for the outward-facing piece.

## 2. Where in the process

Stage **1-PreSale** (see [`docs/skills-roadmap.md`](../../docs/skills-roadmap.md)), right after the briefing meeting itself. See the canonical map: [`briefings/_ciclo-preventa.md`](../../briefings/_ciclo-preventa.md). Two things matter here:

- It runs pre- or post-discovery-context. With the briefing-context plus the briefing transcript it can already run (write up what we understood, follow the action items); useful when the documentation hasn't arrived yet. If the discovery-context already exists, that's better.
- This is not discovery. The meeting notes close out a (pre-sales) briefing meeting. Discovery is a later stage (post-sale, pre-development) and isn't touched here.

## 3. Required input

- The best context available (`briefings/<...>-discovery-context.md` if it already exists; otherwise the Preparation Document from `/briefing-context`). Cycle rule: discovery-context if it exists, briefing-context if not.
- The briefing transcript (`source/meetings/<date>-<client>-briefing.md`, or `-discovery.md` depending on how the source was labeled).
- Client documentation, if they sent any.
- Corrections from later internal calls (what to promise and what not, who gets escalated to, which path takes priority).

You don't need to wait for the discovery-context to run this skill: the briefing-context plus the transcript is enough. But if the discovery-context already exists, use it; it gives better context.

## 4. What it does, step by step

**Working principles:**
- Reflect what we understood, not what we assume. Everything about the process is framed as "this is what we understood, please validate," never as established truth about a process we didn't witness.
- Ask for concrete evidence, not vague data: photos of the spreadsheets, a real example of a message, screenshots of every screen of the system. (Lesson from the Frigorífico case: "send us info" isn't enough; you need to spell out which photo/screenshot of what.)
- Be honest about scope. Don't promise what isn't feasible (prototype, integration); stay aligned with the discovery-context's feasibility read. If the prototype isn't feasible, don't mention it.
- Keep a middle-ground professional tone (see below).
- Unlock the next step. The meeting notes always leave the validation, the material, and the meeting with the decision-maker requested.

**Tone rule:** middle ground between professional and warm. No emojis, no casual Argentine slang ("che", "abrazo", "boludo", "un abrazo"), no over-familiarity. Warm but measured: "gracias por el tiempo," "quedamos a disposición," "Saludos, Equipo Quarks." Formal verbs ("insume," "vuelve a cargar," "registra") rather than spoken register. The deliverable itself is written entirely in Latin American Spanish.

**Build the meeting notes**, including whichever of these applies to the case:

1. **Internal header (do not send).** A `> Nota interna` block above everything: the email's goal, what NOT to promise, who to escalate to, who builds on the draft. Deleted before sending.
2. **Brief greeting.** Thank them for the time. Flag that a summary is coming for validation plus a request for material. Note they can forward it to the decision-maker.
3. **What we understood about the current process.** The flow in numbered steps, in the client's own language. Close with an explicit request for validation ("is this flow correct?").
4. **Where we identified the pain point.** Concrete, with numbers if available (time, errors, volume).
5. **What we'd need to move forward.** Numbered list of evidence plus open questions. Each item specific.
6. **Next steps.** Validation + material, then a meeting with the decision-maker for a conceptual proposal, then what we do in parallel.
7. **Professional close.** "Quedamos a disposición. Saludos, Equipo Quarks."

## 5. What it does NOT do

- Does not replace the internal context (discovery-context). The meeting notes never dump stakeholders, feasibility, technical unknowns, or "how we'll work it internally"; all of that stays in the discovery-context.
- Does not send the email. This skill leaves a draft ready to copy/send; the account lead builds on it before sending (e.g. Oli drafts, Jony adds his part).
- Does not promise what isn't feasible (prototype, integration); stays aligned with the discovery-context's feasibility read.
- Does not present the understood process as established truth; it's always framed as pending validation.

## 6. What comes out

A file with:
- The internal header (do not send).
- The client-facing body, ready to copy (structure above).

Follow `CLAUDE.md § Operating preferences § Autonomy mode`. Under `propose and wait`, present the draft and wait for confirmation before saving.

## 7. How it comes out

The draft is delivered as a formatted Google Doc, not a loose `.md`, so the account lead can build on it before sending without fighting raw markdown. Two artifacts, in this order:

1. **Markdown backup (repo)**: saved as before; the audit anchor, never deleted.
2. **Formatted Google Doc (editable draft)**: created via the Google Drive connector's `create_file` from that same markdown, with `contentMimeType: text/markdown` and `disableConversionToGoogleType` left off, including the "do not send" internal header (the account lead deletes it before copying the body into the email).

It's still a draft that the skill doesn't send: the Google Doc is for building on and then copying the body (without the internal header) into the email.

## 8. Where it goes

- Markdown backup: `briefings/<meeting-date>-<client>-minuta.md`.
- Google Doc: title `Minuta, <Client>, <YYYY-MM-DD> (draft)`; if the PM specified a Drive folder, pass its `parentId`, otherwise it lands in the root.
- Close by returning the Google Doc link plus the `.md` path.

## 9. Example

**Input:** [build-context](https://github.com/OliQUARKS/my-pm-brain/blob/main/briefings/2026-07-frigorifico-merlo-build-context.md) + [discovery Jul 23](https://github.com/OliQUARKS/my-pm-brain/blob/main/source/meetings/2026-07-23-frigorifico-merlo-discovery.md) + internal Oli-Jony call Jul 24.

**How you read it:**
- The internal call decided: don't promise a prototype (the full flow isn't prototypable because of the WhatsApp integration); it comes out of the email.
- The email's goal becomes validating the flow plus requesting evidence (photos of the sheets, a real WhatsApp order example, ERP screenshots, how they differentiate premium/standard) and requesting the meeting with the owner.
- The end-to-end approach (vs. an isolated patch) gets positioned in the meeting with the owner, not hammered into the email.

**Output:** [minuta Jul 23](https://github.com/OliQUARKS/my-pm-brain/blob/main/briefings/2026-07-23-frigorifico-merlo-minuta.md), with internal header + flow to validate + 7 material requests + next steps, in the middle-ground tone.

## 10. Skill acceptance criteria

- Called `minutero`.
- Embeds the best context available (discovery-context if it exists; otherwise briefing-context); never confuses briefing with discovery.
- Client-facing and delivered as a draft the account lead builds on; not sent by the skill.
- Never dumps internal content (stakeholders, feasibility, technical unknowns, "how we'll work it internally").
- The understood flow is framed as to-be-validated, not established truth.
- Requests concrete, itemized evidence (which photo/screenshot of what), not "send us info."
- Doesn't promise what isn't feasible (prototype/integration); aligned with the discovery-context.
- Leaves the meeting with the decision-maker plus the conceptual proposal requested.
- Middle-ground professional tone: no emojis, no slang, no over-familiarity.
- Internal header (do not send) at the very top; output is 100% Latin American Spanish.
- Deliverable is a formatted Google Doc (draft) via the Drive connector; markdown backup in the repo; link returned.
