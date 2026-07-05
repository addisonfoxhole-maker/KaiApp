---
name: design-critique
description: Get structured design feedback on usability, hierarchy, and consistency. Trigger with "review this design", "critique this mockup", "what do you think of this screen?", or when sharing an artifact, screenshot, or description for feedback at any stage from exploration to final polish.
argument-hint: "<artifact, screenshot, or description>"
---

# /design-critique

> House rules, connectors, and the design bible: see [CONNECTORS.md](../../CONNECTORS.md).
> **Always critique against `ALONGSIDE_UIUX_ThemeSystem.pdf`** — its philosophy
> (§1), laws (§2), ADHD rules (§3), card logic (§4), tokens (§5), and quality
> floor (§8) are the measuring stick, not generic taste.

Get structured design feedback across multiple dimensions.

## Usage

```
/design-critique $ARGUMENTS
```

Review the design: @$1

If an artifact or file is referenced, read and render it. There is **no Figma** —
reason from the actual HTML/CSS/React code and a screenshot, not a design-tool
export. Otherwise, ask the user to share or describe the design.

## What I Need From You

- **The design**: artifact, screenshot, or detailed description
- **Context**: What is this? Who is it for? What stage (exploration, refinement, final)?
- **Which theme**: Which bible theme (§6) is it on, or which brand (Foxhole /
  OrcaTeknic / Academy)?
- **Focus** (optional): "Focus on mobile" or "Focus on the onboarding flow"

## Critique Framework

Run the five general lenses, then the **Alongside conformance pass** — the part
that makes this critique ours and not generic.

### 1. First Impression (2 seconds)
- What draws the eye first? Is that the single focal "do this next" thing (§1, Von Restorff)?
- Is the purpose immediately clear and calm — or busy/shaming?

### 2. Usability
- Can the user reach their goal? Intuitive nav? Obvious interactive elements?
- One focal action per screen (Hick's), or competing CTAs?

### 3. Visual Hierarchy
- Clear reading order; right elements emphasized; whitespace earning its keep.
- One hero metric with the rest subordinate — not everything shouting.

### 4. Consistency
- Tokens used, not hardcoded hex/spacing (§5 contract).
- Status colors (`--good/--watch/--bad`) constant in meaning across light/dark.

### 5. Accessibility
- Contrast, touch targets, focus ring, reduced motion. (Full pass = the
  /accessibility-review skill; flag blockers here.)

### 6. Alongside conformance pass (the house lens)
Check the design against the bible's non-negotiables and flag each as
✅ holds / ⚠ drifts / 🔴 violates:

- **AI-default tells (§1):** Is it leaning on cream-serif-terracotta, near-black +
  acid accent, or hairline broadsheet columns? Is boldness concentrated in *one*
  signature element, or sprayed everywhere?
- **No AI imagery:** any generated art present or implied? (🔴 — it's banned.)
- **Shame/manipulation (§1, §3):** any streak, points, fake-progress, or
  guilt-tripping lapse copy? Is lapse microcopy gentle ("water when you can")?
- **Card logic (§4):** is anything over-carded (hero, nav, single big number,
  continuous flow) or under-carded (a discrete object with no affordance)?
- **Externalized time (§3, R5):** are "overdue / Nd ago," a "today" marker, and
  freshness shown where relevant? Is stale/offline distinct from bad?
- **Miller / body-doubling corrections (§3):** any "7-tile cap" rationalization,
  or over-claimed co-working mechanics?
- **Token discipline (§5):** does it actually reference the variable contract, so
  a theme swap would just work?

## How to Give Feedback

- **Be specific**: "The CTA competes with the nav" not "the layout is confusing."
- **Cite the bible**: tie each point to a section (e.g. "§4 — the nav shouldn't
  be a card").
- **Suggest the fix**, don't just name the problem.
- **Acknowledge what works**, including where it nails the brand identity.
- **Match the stage**: exploration ≠ final polish.

## Output

```markdown
## Design Critique: [Design Name] · Theme/Brand: [e.g. Reef Night / OrcaTeknic]

### Overall Impression
[1–2 sentences — what works, the biggest opportunity]

### Usability
| Finding | Severity | Recommendation |
|---------|----------|----------------|
| [Issue] | 🔴 Critical / 🟡 Moderate / 🟢 Minor | [Fix] |

### Visual Hierarchy
- **What draws the eye first**: [Element] — [correct? is it the focal thing?]
- **Reading flow**: [how the eye moves]
- **Emphasis**: [right things emphasized?]

### Consistency
| Element | Issue | Recommendation |
|---------|-------|----------------|
| [Typography/spacing/color/token] | [Inconsistency] | [Fix] |

### Alongside Conformance (§ bible)
| Non-negotiable | Status | Note / Fix |
|----------------|--------|------------|
| AI-default tells (§1) | ✅/⚠/🔴 | [...] |
| No AI imagery | ✅/🔴 | [...] |
| No shame / no fake progress (§1,§3) | ✅/⚠/🔴 | [...] |
| Card logic (§4) | ✅/⚠/🔴 | [...] |
| Externalized time & freshness (§3) | ✅/⚠/🔴 | [...] |
| Token discipline (§5) | ✅/⚠/🔴 | [...] |

### Accessibility (blockers only — full pass via /accessibility-review)
- **Color contrast**: [pass/fail for key text]
- **Touch targets**: [adequate?]
- **Focus / reduced motion**: [present?]

### What Works Well
- [Positive 1] · [Positive 2]

### Priority Recommendations
1. **[Most impactful]** — [why + how, cite § where relevant]
2. **[Second]** — [...]
3. **[Third]** — [...]
```

## Tips

1. **Tell me the theme and brand** — critique differs for Foxhole field-manual vs.
   OrcaTeknic bioluminescent.
2. **Specify your stage** — early exploration gets different feedback than final.
3. **Ask me to focus** — "just the nav" gives you more depth on one area.
