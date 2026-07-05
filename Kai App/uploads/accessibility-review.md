---
name: accessibility-review
description: Run a WCAG 2.1 AA accessibility audit on a design or page. Trigger with "audit accessibility", "check a11y", "is this accessible?", or when reviewing a design for color contrast, keyboard navigation, touch target size, or screen reader behavior before handoff.
argument-hint: "<artifact, URL, or description>"
---

# /accessibility-review

> House rules, connectors, and the design bible: see [CONNECTORS.md](../../CONNECTORS.md).
> Accessibility is the bible's **§8 quality floor — a floor, not a finish.** This
> skill enforces it.

Audit a design or artifact for WCAG 2.1 AA compliance. There is **no Figma** —
inspect the artifact's actual CSS values, computed colors, and markup, plus a
rendered screenshot.

## Usage

```
/accessibility-review $ARGUMENTS
```

Audit for accessibility: @$1

## WCAG 2.1 AA Quick Reference

### Perceivable
- **1.1.1** Non-text content has alt text
- **1.3.1** Info/structure conveyed semantically
- **1.4.3** Contrast ≥ 4.5:1 (normal), ≥ 3:1 (large)
- **1.4.11** Non-text contrast ≥ 3:1 (UI components, graphics)

### Operable
- **2.1.1** All functionality via keyboard
- **2.4.3** Logical focus order
- **2.4.7** Visible focus indicator
- **2.5.5** Touch target ≥ 44×44 CSS px

### Understandable
- **3.2.1** Predictable on focus
- **3.3.1** Error identification (describe the error)
- **3.3.2** Labels/instructions for inputs

### Robust
- **4.1.2** Name, role, value for all UI components

## Alongside-specific checks (beyond raw WCAG)

These are bible rules that a generic a11y pass would miss:

- **Status never color-only.** `--good/--watch/--bad` must pair with text or icon,
  and keep constant meaning across light/dark (§1, §8). A user who can't
  distinguish the hues must still get the status.
- **Token contrast pairs (§5).** Spot-check the easy-to-miss pairs: `--soft` on
  `--bg`, and any text-over-media (`--metaink` over the photo/video scrim). The
  bible flags these as not-yet-formally-measured — so measure them here.
- **Freshness is an accessibility issue, not just UX (§3, R5).** "Green but dead"
  is a dangerous lie. Stale/offline must be visually distinct from a bad reading,
  and media falls back to the last image — never a blank panel.
- **Reduced motion** must zero out animation/transition (`prefers-reduced-motion`),
  and interactions stay < 400ms animating transform/opacity only (§2, §8).
- **No 7-tile cap rationalized as accessibility.** Dashboards reduce load via
  hierarchy/chunking, not by capping visible items (§3 correction).

## Testing Approach

1. Automated reasoning over the CSS/markup (catches ~30%)
2. Keyboard-only walk of the tab order
3. Screen-reader mental model (VoiceOver/NVDA) — flag what can't be verified
   without real AT
4. Color-contrast math on every token pair in use
5. Zoom to 200% — does the layout hold (phone Now-Bar → tablet/desktop rail)?

## Output

```markdown
## Accessibility Audit: [Design/Artifact] · Theme: [§6 name]
**Standard:** WCAG 2.1 AA + Alongside §8 | **Date:** [Date]

### Summary
**Issues:** [X] | **Critical:** [X] | **Major:** [X] | **Minor:** [X]

### Findings
#### Perceivable
| # | Issue | WCAG | Severity | Recommendation |
|---|-------|------|----------|----------------|
#### Operable
| # | Issue | WCAG | Severity | Recommendation |
#### Understandable
| # | Issue | WCAG | Severity | Recommendation |
#### Robust
| # | Issue | WCAG | Severity | Recommendation |

### Color Contrast (§5 token pairs)
| Pair | Foreground | Background | Ratio | Required | Pass? |
|------|-----------|------------|-------|----------|-------|
| Body | --ink | --bg | [X]:1 | 4.5:1 | ✅/❌ |
| Secondary | --soft | --bg | [X]:1 | 4.5:1 | ✅/❌ |
| Over media | --metaink | scrim | [X]:1 | 4.5:1 | ✅/❌ |
| Status | --bad | --bg | [X]:1 | 3:1 | ✅/❌ |

### Alongside §8 Floor
| Check | Status |
|-------|--------|
| Status not color-only (paired w/ text/icon) | ✅/❌ |
| Status meaning constant L↔D | ✅/❌ |
| Touch ≥44px | ✅/❌ |
| Visible :focus-visible | ✅/❌ |
| prefers-reduced-motion honored | ✅/❌ |
| Interactions <400ms, transform/opacity only | ✅/❌ |
| Stale/offline ≠ bad; media falls back to last image | ✅/❌ |
| No Miller-7 cap rationalization | ✅/❌ |

### Keyboard Navigation
| Element | Tab order | Enter/Space | Escape |
|---------|-----------|-------------|--------|

### Screen Reader
| Element | Announced as | Issue |
|---------|-------------|-------|

### Priority Fixes
1. **[Critical]** — blocks [who] from [what]
2. **[Major]** — improves [what] for [who]
3. **[Minor]** — polish
```

## Tips

1. **Start with contrast + keyboard** — highest-impact, most common.
2. **Real AT still matters** — this is a strong first pass; VoiceOver/NVDA catch
   what code-reasoning can't.
3. **Freshness counts** — test the stale/offline state, not just the happy path.
