---
name: design-system
description: Audit, document, or extend your design system. Use when checking for hardcoded values or token drift across artifacts, documenting a component's variants and states, or designing a new pattern that fits the Alongside system.
argument-hint: "[audit | document | extend] <component or system>"
---

# /design-system

> House rules, connectors, and the design bible: see [CONNECTORS.md](../../CONNECTORS.md).
> The system **already exists**: `ALONGSIDE_UIUX_ThemeSystem.pdf`. This skill
> audits/documents/extends *against* it — it does not invent a new system.

Manage the Alongside design system — audit artifacts for token conformance,
document components, or design new patterns that fit the shared layer.

## Usage

```
/design-system audit                    # Check an artifact against the bible
/design-system document [component]     # Document a component in the catalogue
/design-system extend [pattern]         # Design a new pattern on the shared layer
```

## The system is the bible (don't re-derive)

- **Tokens = §5 contract.** The canonical set is the CSS custom properties:
  `--bg`, `--bgfade`, `--ink`, `--soft`, `--metaink`, `--accent`, `--accent2`,
  `--good`, `--watch`, `--bad`, `--rule`, `--ruleV`, `--track`, `--card`,
  `--cardln`, `--display`, `--body`, `--data`. Audit against these names.
- **Themes = §6 library.** Nine locked token sets (Lagoon, Reef Night, Vivarium,
  Tiki, Sunset Shore, Herbarium, Spectrum, Atelier, Graphite). A theme is a token
  block, not a codebase. Lagoon's light palette is **locked — do not drift.**
- **Components = §4 catalogue.** Full-bleed media hero, focal-alert card,
  grouped-vitals card, band/tide meter, gauge-done-right, Now-Bar nav, freshness
  indicator, progressive-disclosure collapsible. All theme-agnostic.
- **Selection = §7 matrix.** Picking a theme is a lookup, not a debate.

There is **no Figma.** Audit the artifact's actual CSS/markup. "Token coverage"
means: how much references the §5 variables vs. hardcoded hex/spacing.

## Principles

1. **Conformance over creativity** — the system exists so we don't rebuild screens.
2. **Token swap, not rebuild** — a new app's theme is ~15 variables.
3. **Document everything** — if a pattern isn't in the catalogue, it doesn't exist.
4. **Append-only bible** — real changes get a dated §10 changelog entry + version
   bump (MINOR = new theme/pattern, PATCH = fix, MAJOR = token-contract break).

## Output — Audit

```markdown
## Design System Audit: [Artifact] · Theme: [§6 name]

### Summary
**Components reviewed:** [X] | **Issues:** [X] | **Conformance:** [X/100]

### Token Conformance (§5)
| Category | Using tokens | Hardcoded values found |
|----------|--------------|------------------------|
| Color (--accent/--good/--watch/--bad…) | [X] | [X] hardcoded hex |
| Spacing | [X] | [X] arbitrary values |
| Type (--display/--body/--data) | [X] | [X] off-system fonts/sizes |
| Status meaning constant L/D? | ✅/❌ | [...] |

### Card Logic (§4)
| Element | Is a card? | Should it be? | Action |
|---------|-----------|---------------|--------|
| [Hero/nav/metric/object] | [y/n] | [y/n] | [add/remove card] |

### Quality Floor (§8)
| Check | Status |
|-------|--------|
| Contrast ≥4.5/3:1 | ✅/❌ |
| Touch ≥44px | ✅/❌ |
| Focus-visible ring | ✅/❌ |
| prefers-reduced-motion honored | ✅/❌ |
| Freshness: stale/offline ≠ bad | ✅/❌ |
| No AI-default tells / one signature | ✅/❌ |
| Corrections honored (no Miller-7 cap; honest body-doubling; no Spectrum grid) | ✅/❌ |

### Priority Actions
1. [Most impactful] · 2. [Second] · 3. [Third]
```

## Output — Document

```markdown
## Component: [Name]  (catalogue §4)

### Description
[What it is + when to use it. Reference the worked plant-screen example if relevant.]

### Tokens Used (§5)
- Color: [which vars] · Type: [which vars] · Surface: [--card/--cardln/--track]

### Variants / States
| State | Visual | Behavior |
|-------|--------|----------|
| Default | [...] | — |
| Hover | [...] | [interaction] |
| Active | [...] | [interaction] |
| Disabled | [...] | Non-interactive |
| Loading | [...] | [animation, <400ms, transform/opacity] |
| Stale/Offline | [distinct from bad] | [fallback to last image, never blank] |

### Accessibility
- **Role**: [ARIA] · **Keyboard**: [Tab/Enter/Esc] · **Screen reader**: [announced as…]
- Status never color-only — paired with text/icon.

### Do's and Don'ts
| ✅ Do | ❌ Don't |
|------|---------|
| [Card a discrete object] | [Card the nav/hero/big number] |

### Code Example
[Shared component CSS from §5, using the token variables]
```

## Output — Extend

```markdown
## New Pattern: [Name]

### Problem
[What gap this fills that the §4 catalogue doesn't already cover]

### Existing Catalogue Patterns
| Related (§4) | What's shared | Why it's not enough |
|--------------|---------------|---------------------|

### Proposed Design (on the shared layer)
#### Tokens Used (§5 only — no new ad-hoc colors)
- Color / Type / Surface: [which vars]

#### Variants / States
[Default, hover, disabled, loading, stale/offline — same table as Document]

### Accessibility
- Role / Keyboard / Screen reader / not-color-only

### Bible Impact
- [ ] New catalogue entry needed → propose §4 wording + §10 changelog line + MINOR bump
- [ ] Fits existing entry → no bible change

### Open Questions
- [Decision needing review] · [Edge case]
```

## Tips

1. **Audit before extending** — most "new" needs are an existing §4 pattern.
2. **Document while building** — easier than reverse-engineering later.
3. **If you're adding a color outside the token block, stop** — it probably
   belongs as a theme variable, or it's drift.
