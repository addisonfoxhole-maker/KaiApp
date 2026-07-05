---
name: design-handoff
description: Generate developer handoff specs from a design. Use when a design is ready for build and needs a spec sheet covering layout, design tokens, component props, interaction states, responsive breakpoints, edge cases, and animation details.
argument-hint: "<artifact or design description>"
---

# /design-handoff

> House rules, connectors, and the design bible: see [CONNECTORS.md](../../CONNECTORS.md).
> Tokens reference the **§5 contract**; states/quality reference **§4 and §8.**

Generate comprehensive build-handoff documentation from a design. There is **no
Figma** — pull exact values from the artifact's actual CSS/markup. Spec everything
the builder would otherwise have to guess.

## Usage

```
/design-handoff $ARGUMENTS
```

Generate handoff specs for: @$1

## What to Include

### Visual specs
- Exact measurements (padding, margins, widths)
- **Token references, not raw values** — `--accent` not `#0fb1bf`; map each to its
  §6 theme value in the token table.
- Responsive breakpoints (phone Now-Bar → tablet/desktop left rail + top banner)
- Component variants and states

### Interaction specs
- Click/tap, hover, transitions (duration < 400ms, transform/opacity only, §2)
- `prefers-reduced-motion` fallback
- Gesture support where relevant

### Content specs
- Character limits, truncation, empty / loading / error / **stale-offline** states

### Edge cases
- Min/max content, long international strings (Spanish expansion), slow
  connections, missing data, dead-sensor / offline freshness

### Accessibility (the §8 floor travels with the spec)
- Focus order, ARIA, keyboard, screen-reader announcements, status-not-color-only

## Principles

1. **Don't assume** — if it's unspecified, the builder guesses. Specify it.
2. **Tokens, not values** — reference `--spacing`/`--accent`, list the resolved
   value once in the token table.
3. **Show all states** — default, hover, active, disabled, loading, error, empty,
   **stale/offline.**
4. **Describe the why** — "collapses on mobile because one-handed use" helps the
   builder make good calls.

## Output

```markdown
## Handoff Spec: [Feature/Screen] · Theme: [§6 name] · Brand: [if any]

### Overview
[What it does, user context]

### Layout
[Grid, breakpoints, phone→desktop responsive behavior]

### Design Tokens Used (§5 → §6 resolved values)
| Token | Resolves to (this theme) | Usage |
|-------|--------------------------|-------|
| `--accent` | #[hex] | focal action, active nav |
| `--good/--watch/--bad` | #[hex]×3 | status (constant meaning L/D) |
| `--display / --body / --data` | [families] | headings / body / numerics |
| `--card / --cardln` | [values] | card surface / hairline |

### Components (§4 catalogue)
| Component | Variant | Props | Notes |
|-----------|---------|-------|-------|
| [Focal-alert card] | [...] | [...] | Von Restorff isolation; one-tap; no-shame copy |

### States and Interactions
| Element | State | Behavior |
|---------|-------|----------|
| [CTA] | Hover | [...] |
| [CTA] | Loading | [spinner; <400ms; transform/opacity] |
| [Sensor/data] | Stale/Offline | [distinct from bad; fall back to last image] |
| [Form] | Error | [what happened + how to fix, in-voice] |

### Responsive Behavior
| Breakpoint | Changes |
|------------|---------|
| Desktop (>1024) | left rail + "needs attention" top banner |
| Tablet (768–1024) | [...] |
| Mobile (<768) | bottom Now-Bar; single column |

### Edge Cases
- Empty / Long text (incl. Spanish expansion) / Loading / Error / Offline-stale

### Animation / Motion
| Element | Trigger | Animation | Duration | Easing |
|---------|---------|-----------|----------|--------|
| [bars] | load | [grow] | 300–400ms | [ease] |
| [gauge] | load | [sweep] | 500–600ms | [ease] |
(reduced-motion: all of the above → none)

### Accessibility Notes (§8)
- Focus order · ARIA labels/roles · keyboard · screen-reader text · status not color-only
```

## Where the handoff goes (the tracker step)

After producing the spec, offer to file it:

- **Business app (Foxhole Academy / THE APP / Translation SaaS)** → **Asana**.
  Create the spec as a task with build sub-tasks (one per spec section). Suggest a
  preview first if the user wants to confirm structure.
- **Daily / personal callback** → **TickTick** (create directly, no confirmation
  needed). ⚠ If it lands in **The Academy** list, remind that "Arrange Tasks"
  must be ON in Timeline view or tasks appear to vanish.

## Tips

1. **Tell me the theme** — token values resolve per §6 theme.
2. **Mention edge cases** — "what about 100 items / a 40-char Spanish string?"
3. **Stack is HTML/CSS/React artifacts** — I'll spec to that, not a framework you
   don't use.
