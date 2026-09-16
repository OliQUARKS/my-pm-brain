# Skill: discovery-jtbd (Jobs to be Done interviews)

**Your goal:** find out what job the customer is "hiring" the product to do; not what feature
they say they want. Best entry point when the client talks fluently about their product and
vaguely about the customer's actual problem.

## Where it fits

Stage 7; see [`briefings/_ciclo-preventa.md`](../../briefings/_ciclo-preventa.md) § Discovery
and [`briefings/_kit-discovery.md`](../../briefings/_kit-discovery.md).

## When to use it

Client confuses features with needs, and real end users exist to interview (not just internal
stakeholders; JTBD needs the person who actually made the switch/purchase/adoption decision).
If there's no access to real customers yet, run [`discovery-interview-guide`](./discovery-interview-guide.md)
first to get in the room with them at all, then come back to this once access exists.

## Input

- Access to 5-8 customers who recently adopted (or rejected) something comparable; recency
  matters, memory of the actual decision degrades fast.
- Whatever the client already believes the "job" is (to pressure-test, not to lead with).

## How you facilitate it

Structure per the Christensen/Moesta "Switch" interview; reconstruct the **timeline**, don't
ask hypotheticals:

1. **First thought**, when did they first realize something needed to change? What was
   happening around them (not inside their head) at that moment?
2. **Passive looking / active looking**, what did they try before this? What almost-solutions
   did they consider and reject, and why?
3. **The moment of decision**, what specific event tipped them from looking to committing?
   ("Tell me about the day you decided.")
4. **Anxieties and habits**, what almost stopped them from switching even after deciding
   (fear of the new, comfort with the old)?
5. **After the purchase**, did it deliver the job, or did they discover a different job
   underneath?

Classify what comes out along three dimensions (functional, emotional, social) and write it
as a **job story**: *"When [situation], I want to [motivation], so I can [expected outcome]."*
Not a persona, not a feature request.

## Tool

Primary: **Doc** (Google Doc or repo markdown). This is a text-heavy interview guide + verbatim
transcript exercise, not a visual canvas; resist the urge to put it on Miro. One doc per
interview: guide at the top, verbatim quotes below, job-story synthesis at the bottom.

## Output & where it lands

Full transcript, verbatim, → `source/interviews/YYYY-MM-DD-<client>-jtbd-<participant>.md` per
`CLAUDE.md` § Source preservation (this is a real interview, not a fallback case; preserve it
in full, don't summarize into the source file).

Synthesis (timeline reconstruction + job story + functional/emotional/social tags) →
`ingestion/interviews/YYYY-MM-DD-<client>-jtbd-<participant>.md`.

Route per § Canonical ownership: a job story that recurs across 2+ independent participants →
promote to `knowledge/users/insights.md` § Active themes, one Evidence row per participant,
same-population non-supporters logged under § Contradictions per the insights.md audit-trail
rules in `CLAUDE.md`. A single interview's job story stays in ingestion until it recurs; don't
promote on N=1.

## Quality criteria

✅ Timeline reconstructed (first thought → decision → anxieties → after), not a hypothetical
   feature-preference conversation
✅ At least one job story written as "When X, I want Y, so I can Z"; not a feature list
✅ Functional/emotional/social dimensions distinguished, not flattened into one
✅ Verbatim transcript preserved in `source/`, synthesis (not the raw transcript) in `ingestion/`
✅ Promotion to `insights.md` only after 2+ independent participants say the same thing
✅ Recruited participants are recent adopters/rejecters, not proxies (internal staff guessing)
