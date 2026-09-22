# Skill: postmortem

## 1. Role

You capture what worked, what didn't, and what should change, at the close of a project or engagement, so the lessons feed forward into future discovery and setup work instead of staying locked in one person's head.

## 2. Where in the process

Stage **6-Post** (see [`docs/skills-roadmap.md`](../../docs/skills-roadmap.md)), at the very end of a project, once the client-facing deliverable has shipped and been accepted (after UAT and the user manual). This is roughly the "handoff" point between the engagement and whatever comes next for that client or team.

## 3. Required input

- The build-context (the consolidated post-Discovery plan, scope, and feasibility read).
- The PRD (`knowledge/product/features/<slug>.md`): committed scope and non-goals.
- The TRF history (`briefings/<client>-trf.md`): the commitments made across the sprint and how they actually played out.
- The UAT results and the user manual: what actually got delivered and accepted.
- Any client feedback gathered informally along the way.

## 4. What it does, step by step

1. **Compare committed vs. delivered scope.** Line up the original PRD/build-context against what actually shipped; name what changed and why, not just that it changed.
2. **Review the TRF history for recurring friction.** Look for a pattern (the same kind of commitment slipping repeatedly, the same dependency always the blocker) as a process signal, never as a way to single out one person's fault.
3. **Capture what worked well** and should be repeated on the next engagement, concretely enough to actually reuse ("the 3-proposal design gate before the first sprint kept the client aligned early," not "communication was good").
4. **Capture what didn't work** and what would change next time, with the same level of concreteness.
5. **Identify reusable assets or client-specific knowledge** worth keeping for future similar clients: an integration pattern, a domain glossary, a design system, a feasibility read that turned out right or wrong.
6. **Flag anything that looks like a durable process change** (a new skill rule, a new checklist item) separately from what's specific to this one client; a process change gets surfaced to the PM for review, never applied on its own.

## 5. What it does NOT do

- Does not turn into a blame exercise; recurring friction is named as a process signal, not attributed to an individual's fault.
- Does not silently fold a proposed process change into any skill or template; it gets surfaced for the PM's review instead.
- Does not duplicate the client-facing close-out communication; this is entirely internal.
- Does not skip capturing what worked; both what worked and what didn't get equal weight, otherwise the lesson skews toward avoiding risk without reinforcing what to repeat.

## 6. What comes out

- Committed vs. delivered scope, with what changed and why.
- Process friction observed, framed as a signal, not blame.
- What worked and should be repeated.
- What didn't work and what would change.
- Reusable assets or client-specific knowledge worth keeping.
- Any proposed process change, flagged for review rather than applied.

## 7. How it comes out

A markdown note, internal only.

## 8. Where it goes

- `briefings/<client>-postmortem.md`.
- Any proposed process change gets surfaced to the PM directly in the close-out message, not written into another skill's file without confirmation.

## 9. Example

Not applicable yet; no worked example has been captured for this skill.

## 10. Skill acceptance criteria

- Committed vs. delivered scope is compared explicitly, not just asserted as "we shipped it."
- Both what worked and what didn't are captured; the note isn't one-sided.
- Recurring friction is framed as a process signal, never as blame on a person.
- Reusable assets or client-specific knowledge are named, not lost.
- Any proposed process change is surfaced for PM review, never applied silently.
- Output is 100% Latin American Spanish.
