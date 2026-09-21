# Skill: close-context

## 1. Role

You close out `project-context` and `client-context` once `/postmortem` is done, so the final state of the engagement and everything durably learned about the client get recorded, not just left inside the postmortem file.

## 2. Where in the process

Stage **6-Post** (see [`docs/skills-roadmap.md`](../../docs/skills-roadmap.md)), immediately after `/postmortem`.

## 3. Required input

- `/postmortem`'s output for this project.
- The project's `project-context` (`briefings/<client>-project-context.md`); it must already exist, seeded by `/briefing-context` and updated by `/discovery-context` and `/build-context`.
- The client's `client-context` (`knowledge/org/<client-slug>.md`); update it if it exists, or create it now (see step 4) if this was the client's first engagement and nobody created it earlier.

## 4. What it does, step by step

1. **Pull the postmortem's key facts**: delivered vs. committed scope, what worked and what didn't, reusable assets or knowledge, any proposed process change.
2. **Append the closing entry to `project-context`'s Timeline** (see [`briefings/_project-context-template.md`](../../briefings/_project-context-template.md)): a 1-2 line closing summary, linked to the postmortem file. Never rewrite an earlier Timeline entry.
3. **Flip `project-context`'s `Estado` to "cerrado"** in the Meta block; this is the one field that updates in place rather than appending.
4. **Update `client-context`** (`knowledge/org/<client-slug>.md`): add a dated final "Interacciones" entry for this project's close, and refresh the client profile with anything durably learned (a system capability now confirmed, a stakeholder's role or motivation, a recurring pain point), following the existing pattern in [`knowledge/org/ryd-abogados.md`](../../knowledge/org/ryd-abogados.md).
5. **If `client-context` doesn't exist yet** (this was the client's first project and nobody created it during briefing/discovery/build), create it now from the accumulated `project-context` history, in the same format.
6. **Note whether follow-up looks worth pursuing** (renewal, expansion, a referral) as an observation for the PM, not a decision made by the skill.

## 5. What it does NOT do

- Does not redo the postmortem's analysis; it reads `/postmortem`'s output, it doesn't re-derive learnings.
- Does not rewrite an earlier entry in `project-context`'s Timeline or in `client-context`'s Interacciones; both are append-only except for the `Estado` field.
- Does not decide on business-development follow-up (renewal, upsell) on its own; it surfaces the observation, the PM decides.

## 6. What comes out

- The final `project-context` Timeline entry, with `Estado` flipped to "cerrado."
- The final `client-context` update (or a newly created `client-context` file, if this was the first project for this client).

## 7. How it comes out

Two markdown appends (or one append plus one file creation), following the existing patterns in [`briefings/_project-context-template.md`](../../briefings/_project-context-template.md) and [`knowledge/org/ryd-abogados.md`](../../knowledge/org/ryd-abogados.md).

## 8. Where it goes

- `briefings/<client>-project-context.md` (append the closing Timeline entry; flip `Estado`).
- `knowledge/org/<client-slug>.md` (append the final Interacciones entry, or create the file if it doesn't exist).

## 9. Example

Not applicable yet; no worked example has been captured for this skill.

## 10. Skill acceptance criteria

- The closing entry in `project-context` cites the postmortem file it came from.
- `project-context`'s `Estado` flips to "cerrado," never left ambiguous.
- `client-context` gets a dated final interaction entry.
- Earlier entries in both files are never rewritten, only appended to.
- If `client-context` didn't exist yet, it gets created now, following the established pattern, not silently skipped.
- Output is 100% Latin American Spanish.
