# Skill: trf (Tarea, Responsable, Fecha)

## 1. Role

You track the tasks, owners, and due dates that come out of a sprint's recurring meetings during Build, and keep the shared client communication channel updated on who owes what by when. A lightweight cross-meeting tracker, not a project-management tool replacement.

## 2. Where in the process

Stage **5-Build** (see [`docs/skills-roadmap.md`](../../docs/skills-roadmap.md)), running continuously across the sprint's recurring meetings and syncs, alongside `/uat`. It reads what's already planned in the backlog (`/backloguer`, and the future `backlog_review`) so it never invents new scope; it only tracks the one-off human commitments that don't belong in the backlog (a pending client answer, a document someone promised to send, a blocker someone said they'd chase).

## 3. Required input

- The transcript or notes from the latest sprint meeting or sync.
- The running TRF list from the previous update, if one exists (non-redundancy: update existing items' status instead of recreating them).
- The current backlog state (`ingestion/adhoc/*-epics-<slug>.md` / `*-stories-<slug>-*.md`), to tell a one-off commitment apart from an actual unit of product scope.

## 4. What it does, step by step

1. **Extract every commitment stated in the meeting**: the task, who owns it (internal or client-side), and a date, explicit or inferred from context ("for the next sync").
2. **Filter out backlog scope.** A TRF item is a one-off commitment or action, not a unit of product functionality. If something raised in the meeting is actually product scope, it doesn't get tracked here; flag it for `/backloguer` or `backlog_review` instead.
3. **Update the running list.** Carry over open items from the previous update; mark them done, still pending, or overdue based on what the new meeting says. Append genuinely new commitments.
4. **Flag overdue items explicitly.** A due date that passed with no update doesn't get dropped or quietly rolled forward; it's marked overdue until someone addresses it.
5. **Draft the client-facing status recap**, in the same middle-ground professional tone as `/minutero` (no emojis, no slang, no over-familiarity): what the client owes, what Quarks owes, and what's overdue on either side.

## 5. What it does NOT do

- Does not create or modify backlog items (epics/stories); that's `/backloguer` and `backlog_review`.
- Does not silently drop an overdue item; overdue items stay visible until resolved.
- Does not invent an owner or a date when the meeting didn't specify one; those get marked "a confirmar."
- Does not replace the sprint's actual refinement or planning ritual; it only tracks cross-meeting commitments in between.

## 6. What comes out

- The running TRF table: task, responsible, due date, status (pendiente / hecho / vencido), and the meeting it came from.
- A short client-facing status recap for the shared communication channel.

## 7. How it comes out

Two parts in the same file, updated in place (not a new dated file each time, since it's cumulative across the whole Build stage):
- The full internal TRF table.
- The client-facing recap, ready to paste into the communication channel.

Follow `CLAUDE.md § Operating preferences § Autonomy mode`. Under `propose and wait`, present the updated table and the recap, and wait for confirmation before saving or sending.

## 8. Where it goes

- `briefings/<client>-trf.md`, appended and updated across the whole Build stage; not a new file per meeting.
- The client-facing recap is handed to the PM to post; this skill doesn't send it.

## 9. Example

Not applicable yet; no worked example has been captured for this skill.

## 10. Skill acceptance criteria

- Every tracked item has a task, a responsible party, and a date, or is explicitly marked "a confirmar."
- Commitment-tracking stays separate from backlog scope; no epics or stories get created here.
- Overdue items are flagged, never silently dropped or rolled forward without comment.
- Updating the list doesn't recreate items already tracked; it updates their status.
- The client-facing recap is a separate, shorter artifact from the full internal table, in the same tone as `/minutero`.
- Output is 100% Latin American Spanish.
