# /review-prd

Adversarial panel on a PRD. Five lenses, each loading its own section of the brain and critiquing from its own angle. Final synthesis that prioritizes by severity and names tensions between lenses.

## Input

Path to the PRD (external or in the repo). Optionally, a list of lenses to apply:

- `/review-prd ~/Downloads/perc-cobranza-v2.md` (runs all five)
- `/review-prd ~/Downloads/perc-cobranza-v2.md --with data,risk` (runs only those)
- `/review-prd ~/Downloads/perc-cobranza-v2.md --with strategist` (a single pass, fast)

Available lenses: `strategist`, `customer`, `data`, `risk`, `stakeholder`.

If the path doesn't exist, don't infer; ask.

## Loads

Before invoking lenses:

- The full PRD (verbatim, not rewritten)
- `CLAUDE.md § Evidence hierarchy` and `§ Knowledge hygiene` (evidence bar)
- `INDEX.md` (map PRD references to brain areas)

Each lens loads its own material when it runs:

| Lens | Loads |
|---|---|
| **strategist** | `knowledge/strategy.md`, `decisions/INDEX.md` + the last 3 decisions |
| **customer** | `knowledge/users/insights.md`, personas, and the `source/interviews/` the PRD cites or that touch the same problem |
| **data** | `hypotheses/INDEX.md` + related hypotheses, `knowledge/product/metrics.md` |
| **risk** | `knowledge/compliance/INDEX.md` (mandatory) + the relevant files for the PRD's domain; `knowledge/strategy.md § Non-goals`; recent decisions with analogous reversal-conditions |
| **stakeholder** | `stakeholders/INDEX.md` + files for stakeholders the PRD names or implies, recent `ingestion/meetings/` |

## Mechanics

If there are 3+ lenses: parallel fan-out (`Agent` tool per lens). If 1-2: sequential inline.

Each lens returns a structured output:

```
### <Lens>
**Strengths:** (what the PRD does well from this angle, max 3)
**Gaps:** (what's missing, each with severity: blocking / serious / minor)
**Contradictions:** (PRD claims that clash with the brain, citing the file)
**Questions for the PM:** (the ones that materially affect direction)
```

After the lenses, **synthesis**:

- **Tensions between lenses** (when one lens is happy and another is furious about the same thing; strategist ok + customer furious = signal). Name them, don't flatten them.
- **Aggregate severity** (top-3 blockers preventing a decision).
- **What's missing before a decision can be made** (concrete list: which interview, which data pull, which stakeholder not consulted, which regulation not loaded).

## Updates

- `reviews/YYYY-MM-DD-<prd-slug>.md` (the review document), with frontmatter:

  ```
  ---
  prd_path: <original path>
  prd_hash: <sha of the file at review time>
  reviewed_at: <date>
  lenses: [strategist, customer, data, risk, stakeholder]
  ---
  ```

  Body: one section per lens + synthesis. Drafted, not committed (per autonomy mode `propose and wait`).

- **Does NOT edit** the original PRD. The PRD is external and the PM decides what to incorporate.
- **Does NOT create** decisions or hypotheses automatically. If the panel suggests one, it goes in the synthesis as a "Question for the PM".

## Hard constraints

- **No fabricating evidence.** If a lens wants to claim "this contradicts X in the brain," it must cite the file and the line/section. Without a citation, it goes as a "Question," not a "Contradiction."
- **Verbatim PRD quotes.** When a lens questions a PRD claim, quote it verbatim, don't paraphrase.
- **Honest severity.** "Blocking" means: can't decide without resolving this. Don't inflate it.
- **Don't resolve tensions in this turn.** The review surfaces the tension; the decision is the PM's in the next turn.
- **Risk: don't invent regulation.** The risk lens can't state "this doesn't comply with regulation X" without citing the specific file in `knowledge/compliance/`. If the regulation applies but isn't loaded, it says "I can't evaluate this aspect; need to load regulation Y in `knowledge/compliance/`" instead of inventing it.

## Surfaces

- Path to the created review file
- Top-3 blockers (1 line each)
- Tensions between lenses (1 line each)
- "Apply this review as drafted? (y / edit / no)"
