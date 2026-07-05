---
name: ux-copy
description: Write or review UX copy — microcopy, error messages, empty states, CTAs. Trigger with "write copy for", "what should this button say?", "review this error message", or when naming a CTA, wording a confirmation dialog, filling an empty state, or writing onboarding text.
argument-hint: "<context or copy to review>"
---

# /ux-copy

> House rules, connectors, and the design bible: see [CONNECTORS.md](../../CONNECTORS.md).
> Copy is design material. The bible's voice rules (§1 "never shaming," §3
> guardrails, frontend writing principles) are binding.

Write or review UX copy for any Alongside interface context.

## Usage

```
/ux-copy $ARGUMENTS
```

## What I Need From You

- **Context**: What screen, flow, or feature?
- **Brand**: Foxhole (field-manual) / OrcaTeknic (bioluminescent) / Academy /
  neutral system?
- **User state**: What are they doing? How are they feeling? (A lapse? A win? An error?)
- **Constraints**: Character limits, platform guidelines?

## Principles

1. **Clear** — say exactly what you mean. No jargon, no ambiguity.
2. **Concise** — fewest words that carry the full meaning.
3. **Consistent** — same term for the same thing everywhere; an action keeps its
   name through the whole flow ("Publish" → "Published").
4. **Useful** — every word helps the person act.
5. **Human, never robotic.**
6. **Never shaming, never manipulative** (the house rule). No guilt, no fake
   urgency, no dark patterns. This overrides any other tone goal.

## Copy Patterns

### CTAs
- Verb-first, specific: "Start free trial," "Save changes," "Download report" —
  not "Submit." Match the label to the outcome.

### Error messages
What happened + why + how to fix, **in the interface's voice — errors don't
apologize and are never vague.**
- "Payment declined. Your bank declined the card. Try another card or contact your bank."

### Empty states
What this is + why it's empty + how to start — an invitation to act, not mood.
- "No repair orders yet. Create your first to start tracking jobs."

### Lapse / off-track copy (the Alongside signature)
Gentle and non-judgmental, for both under- and over-correction (§3 guardrails):
- ✅ "Water when you can." / "Looks a little wet — ease off watering."
- ❌ "You forgot." / "You overwatered." / "You broke your streak."

### Confirmation dialogs
- Name the action + consequence: "Delete 3 files? This can't be undone."
- Buttons say the action: "Delete files" / "Keep files" — not "OK" / "Cancel."

### Milestones (honest only)
Real moments, no manufactured ones: "Reached flowering." "First harvest." No
points, badges, or streak counters.

### Tooltips / loading / onboarding
Concise and never obvious; set expectations to reduce anxiety; progressive
disclosure, one concept at a time.

## Voice and Tone

Adapt tone to context **and brand**:
- **Foxhole** — field-manual: terse, competent, stenciled. "Confirm before
  condemning." Instructional, never patronizing.
- **OrcaTeknic** — telemetry/hydrophone: precise, in-world, a little playful.
  Signal/contact metaphors, UTC framing.
- **Success**: celebratory but grounded · **Error**: empathetic + actionable ·
  **Warning**: clear + actionable · **Neutral**: informative + concise.

## Output

```markdown
## UX Copy: [Context] · Brand: [Foxhole/OrcaTeknic/Academy/neutral]

### Recommended Copy
**[Element]**: [Copy]

### Alternatives
| Option | Copy | Tone | Best For |
|--------|------|------|----------|
| A | [Copy] | [Tone] | [When] |
| B | [Copy] | [Tone] | [When] |

### Rationale
[Why it works — user state, clarity, action-orientation, brand fit. Confirm it
passes the no-shame / no-manipulation rule.]

### Localization Notes
[For Translation-SaaS-adjacent contexts: idioms to avoid, character expansion,
and — critically — Spanish automotive terms generic translators mishandle. The
glossary is the defensible asset; flag any term that needs a shop-specific
translation rather than a literal one.]
```

## Tips

1. **Name the brand** — Foxhole and OrcaTeknic don't talk the same way.
2. **Tell me the user's emotional state** — errors need empathy; a lapse needs
   gentleness; a win can celebrate (honestly).
3. **Flag bilingual contexts** — Spanish-speaking customers are a core audience;
   literal translation of shop vocabulary is a known failure mode.
