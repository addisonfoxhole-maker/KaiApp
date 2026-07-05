# Connectors & House Rules — Alongside Design Plugin

Every skill in this plugin points here. This file replaces the generic connector
placeholders (`~~design tool`, `~~knowledge base`, `~~user feedback`,
`~~project tracker`) with the real stack and the standing rules for all
Alongside-family work.

---

## The design bible (read this first, every time)

**`ALONGSIDE_UIUX_ThemeSystem.pdf` is the source of truth for everything visual.**
Before any design work — critique, audit, handoff, new component, copy — the
philosophy (§1), UX laws (§2), ADHD/retention rules (§3), card logic (§4), token
contract (§5), theme library (§6), selection matrix (§7), and quality floor (§8)
in that document are the standard to measure against. Do not re-derive any of
that research per project; it's settled. If a request conflicts with the bible,
say so and cite the section.

When a new app/build chat starts: confirm the bible is loaded, pick a theme by
number from §6 (or recommend one via the §7 matrix), then apply the shared
component layer (§5) + the chosen theme token block. A theme swap is ~15 CSS
variables, never a rebuild.

---

## The toolchain (no Figma)

There is **no Figma / design-tool connector**. Designs are built directly as
HTML/CSS/React artifacts. So everywhere a skill says "pull from Figma" or
"inspect the design tool," substitute:

- **Build/inspect the artifact directly.** Read the artifact's code, render it,
  screenshot it, and reason from the actual markup and tokens — not from a
  design-tool export.
- **Tokens come from the bible's §5 contract**, expressed as CSS custom
  properties (`--bg`, `--ink`, `--accent`, `--good/--watch/--bad`, etc.). Audit
  against those variable names, not Figma styles.

**Tracking / handoff connectors:**

- **Asana** (connected) — business app builds live here: Foxhole Academy, THE APP
  (shop management software), Translation SaaS. Use for handoff specs, build
  sub-tasks, and longer-horizon work.
- **TickTick** (connected) — the daily hub. Create tasks here directly **without
  asking for confirmation**. TickTick holds gentle callbacks to the Asana work.
  - ⚠ **Gotcha:** when adding tasks to **The Academy** list (Timeline view),
    "Arrange Tasks" must be ON or new tasks appear to vanish. Flag this
    proactively whenever adding there.
- **Google Drive** (connected) — reference docs and source material.
- **Cloudflare** (connected) — DNS/Pages deploy target (gray-cloud DNS →
  Netlify for the Academy landing page).

There is **no separate `user feedback` or `product analytics` connector.** When a
skill offers to "cross-reference user feedback," treat that as: work from what
the user actually reports, plus the data-minimization posture below. Don't invent
analytics that don't exist, and don't propose adding tracking that violates the
privacy stance.

---

## Non-negotiables (carry into every skill)

These come straight from the bible's philosophy plus Kayce's standing values.
They override default skill behavior.

1. **No AI-generated imagery. Ever.** Kayce explicitly opposes it. Illustration,
   photography, and iconography are real or hand-made. Do not propose generated
   art as a solution, a placeholder, or a "quick option."

2. **Avoid the AI-default look** (bible §1). Steer around the three tells:
   (a) cream + elegant-serif + terracotta accent; (b) near-black + one
   acid-green/vermilion accent; (c) hairline broadsheet columns. Spend boldness
   in one signature element; keep the rest quiet.

3. **Calm, glanceable, never shaming.** A lapse is met with "water when you can,"
   never "you forgot." No points, streaks, or manufactured urgency — honest
   completion and real milestones only. (§1, §3 guardrails.)

4. **Accessibility is a floor, not a finish** (§8). Contrast ≥ 4.5:1 body /
   ≥ 3:1 large & UI; touch targets ≥ 44×44px; visible `:focus-visible`; honor
   `prefers-reduced-motion`; never encode meaning in color alone; status colors
   (`--good/--watch/--bad`) keep constant meaning across light/dark.

5. **Externalize time and state** (§3, R5). Draw the clock: explicit due dates,
   "overdue / Nd ago," a "today" marker, freshness ("updated 3m ago"). Stale or
   offline is **distinct** from bad — never show a green reading for dead data.

6. **Two evidence corrections are rules, not suggestions** (§3): body doubling is
   *not* "~30%" — frame any co-working timer honestly; Miller's 7±2 is *not* an
   on-screen item cap — never limit a dashboard to 7 tiles "to respect Miller."
   Reduce load via hierarchy and chunking instead.

7. **Cards earn their place** (§4). Use a card for a discrete object, the single
   focal action, or a grouped-data unit. Don't card the immersive hero, the
   nav/chrome, a single big number, or a continuous reading flow.

8. **Ethics over polish, to an annoying degree.** Kayce is building everything as
   ethically as possible — Texas Public Benefit LLC, data minimization, shops own
   and can export their data. Default to the privacy-preserving, user-owned,
   non-manipulative option even when a flashier or stickier one exists. Honesty
   where evidence is weak; don't over-engineer mechanics on contested effects.

9. **Open / local / owned by default.** Strong preference for local storage and
   data ownership over cloud lock-in (NAS, local-first recording, self-hostable
   sync). Reflect that bias in any architecture or storage recommendation.

---

## Voice & copy defaults (for ux-copy and everywhere words appear)

- Plain verbs, sentence case, no filler. Name things by what the person
  controls, not how the system is built.
- An action keeps its name through the whole flow ("Publish" → "Published").
- Errors explain what happened + why + how to fix, in the interface's voice —
  never apologize, never vague.
- Empty states are an invitation to act, not mood-setting.
- Never shaming, never manipulative urgency. No dark patterns.

---

## Brand contexts (when a build is brand-specific)

The bible's nine themes are the general library; these are Kayce's established
brand identities, which may map onto a theme or stand alone:

- **Addison Foxhole** — 1960s military field-manual aesthetic. Olive / rust /
  cream. Oswald + Special Elite. Stencil stamps, grid paper, field-manual voice.
- **OrcaTeknic** — deep-ocean / bioluminescent. Cyan / coral / gold.
  IBM Plex Mono. Hydrophone/telemetry, UTC timestamps, animated waveforms.
  (Closest bible themes: Reef Night / Spectrum.)
- **Foxhole Academy** — coaching funnel; field-manual family, warmer.

When a skill produces tokens for one of these, honor the established palette and
fonts rather than substituting a generic theme — unless Kayce asks to align it to
a bible theme.
