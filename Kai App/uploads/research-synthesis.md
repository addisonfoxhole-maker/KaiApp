---
name: research-synthesis
description: Synthesize user research into themes, insights, and recommendations. Use when you have interview transcripts, survey results, usability test notes, support tickets, or app reviews that need distilling into patterns, segments, and prioritized next steps.
argument-hint: "<research data, transcripts, or survey results>"
---

# /research-synthesis

> House rules, connectors, and the design bible: see [CONNECTORS.md](../../CONNECTORS.md).
> See the **user-research** skill for methods, guides, and the ethics/data-
> minimization rules — those apply to synthesis too.

Synthesize research data into actionable insights for Alongside-family products.

## Usage

```
/research-synthesis $ARGUMENTS
```

## What I Accept

- Interview transcripts/notes · survey results (CSV, pasted) · usability notes ·
  support messages/feedback · app-store reviews

There is **no product-analytics or user-feedback connector.** Synthesize from the
material the user actually provides — don't reference dashboards that don't exist,
and don't recommend adding tracking that violates the privacy stance. If
behavioral validation is genuinely needed, say what *minimal, owned* signal could
provide it rather than reaching for a third-party analytics platform.

## Evidence honesty (bible discipline, applied to research)

The bible corrected two over-claimed effects (body doubling, Miller's 7±2) by
insisting on honest evidence. Carry that here:

- **Separate observation from interpretation.** "7 of 10 clicked the wrong
  button" is an observation; "the placement is confusing" is a hypothesis.
- **Quantify or qualify.** "Most users" → "7 of 10." Small-n findings are flagged
  as directional, not proven.
- **Flag weak ground.** If a theme rests on one or two voices, say so. Don't let a
  recommendation outrun the evidence — the same reason we don't build mechanics on
  contested effects.
- **Anonymize.** Strip identifying detail from quotes, especially for
  mixed-status / Translation-SaaS participants.

## Output

```markdown
## Research Synthesis: [Study] · Product: [Academy/THE APP/Translation SaaS/content]
**Method:** [Interviews/Survey/Usability] | **Participants:** [X]
**Date:** [range] | **Confidence:** [strong / directional / exploratory]

### Executive Summary
[3–4 sentences]

### Key Themes
#### Theme 1: [Name]
**Prevalence:** [X of Y] · **Confidence:** [strong/directional]
**Summary:** [what it's about]
**Evidence:**
- "[anonymized quote]" — P[X]
**Implication:** [what it means for the product]
[repeat]

### Insights → Opportunities
| Insight | Opportunity | Impact | Effort |
|---------|-------------|--------|--------|
| [Learned] | [Could do] | H/M/L | H/M/L |

### User Segments
| Segment | Characteristics | Needs | Rough size |
|---------|----------------|-------|-----------|
| [e.g. rural solo shop] | [offline-prone] | [graceful offline] | [%] |

### Recommendations
1. **[High]** — [why, which findings, confidence]
2. **[Medium]** — [...]
3. **[Lower]** — [...]

### Questions for Further Research
- [What we still don't know]

### Methodology Notes
[How conducted; limitations/biases; data handling & purge status]
```

## Filing it

Product synthesis + resulting build work → **Asana**. Personal follow-ups →
**TickTick** (direct; Academy list needs "Arrange Tasks" ON).

## Tips

1. **Include raw (anonymized) quotes** — they make insights credible.
2. **Separate observation from interpretation** — habitually.
3. **Quantify where possible; flag where you can't** — honesty over a clean story.
