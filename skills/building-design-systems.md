---
name: building-design-systems
description: Create design systems, color palettes, typography scales, spacing systems, design tokens, component libraries, and developer handoff documentation. Activate when the user mentions "design system", "color tokens", "type scale", "component spec", "brand foundations", "design language", or asks how to make a UI consistent across a product. Works with any design tool or code-first workflows.
---

# Building Design Systems

A design system is a shared language between design and code. The goal isn't to produce documentation — it's to make decisions once and apply them consistently forever. Start small, validate early, expand deliberately.

## Start Here: Context Questions

Before generating anything, ask the user:

1. Does a brand identity already exist (logo, colors, fonts)? Or are we starting from scratch?
2. What platform — web app, native mobile, marketing site, or multiple?
3. Who uses this system — one product team, multiple teams, or external developers?
4. What's the most critical deliverable right now: color and type foundations, a component library, or token output for dev handoff?

The answers determine scope. Don't generate a 30-component library when the user needs a color decision today.

## Foundations: Color System

Start with a single anchor color — the primary brand color. Every other decision cascades from it.

**Thinking process:**

1. Choose primary based on primary emotion: trust (blue family), urgency (red/orange), calm (green/blue), excitement (vivid yellow/coral). Avoid colors that conflict with the brand's industry conventions unless the differentiation is intentional.
2. Derive semantic colors from the same family — don't invent new hues for success/error; adapt shades of the existing palette where possible.
3. Build a neutral scale (9 grays: 50 through 950) independently of brand colors. Neutrals carry most of the UI weight.
4. Test every text+background combination against WCAG AA: 4.5:1 for body text, 3:1 for large text and UI components.
5. Design dark mode as a parallel system from the start — not an afterthought. Swap neutrals, adjust color saturation slightly, verify contrast again.

**Output format per color:**
- Hex, RGB, HSL
- WCAG contrast ratio on white / on black
- Semantic label (primary, primary-hover, primary-disabled, etc.)
- Usage rule: one sentence describing what this color communicates and when to use it

Deliver: primary (6 shades), secondary (4 shades), neutral (9 stops), semantic (success/warning/error/info with light+dark variants).

## Foundations: Typography

One decision drives the whole system: what role does type play in this brand? Expressive display type or functional body clarity? Both can coexist but one leads.

**Thinking process:**

1. Choose body font first — readability above expressiveness. Test at 16px on screen before committing. Avoid system fonts (Arial, Helvetica) for branded work — they signal genericness.
2. Choose display font second — can be more expressive. Must pair with body: pair a geometric sans with a humanist sans, a serif display with a sans body, not two fonts of the same category.
3. Define only the levels the product genuinely needs. Minimum: Display, Heading, Body, Caption. Add Subheading, Label, Overline only when a real hierarchy gap exists — not speculatively.
4. Mobile-first sizing: start at 16px body, scale up for desktop. Never below 14px for body, 11px for captions.
5. Line height: 1.4–1.6× for body copy, 1.1–1.2× for display/heading.

**Output per type level:**
- Font family, weight
- Size in px and rem at mobile / tablet / desktop
- Line height, letter spacing
- Usage rule (one sentence: when to use, when not to)

## Foundations: Spacing System

Use an 8px base unit. Every spacing value is a multiple or half-multiple: 4, 8, 12, 16, 24, 32, 48, 64, 96, 128.

Assign semantic meaning, not just numbers:
- 4px — micro (icon-to-label gap, badge padding)
- 8px — tight (form element internal padding)
- 16px — default (card content padding, list item gap)
- 24px — comfortable (section breathing room, modal padding)
- 32–48px — generous (major content separation)
- 64px+ — layout (page section breaks)

When spacing feels wrong, the fix is almost always: use a larger step or a smaller one — not an arbitrary value between them.

## Foundations: Layout Grid

Three breakpoints, 12-column grid:
- Desktop: 1440px max-width, 80px gutters, 24px edge margins
- Tablet: 768px, 24px gutters, 16px edge margins
- Mobile: 375px, 16px gutters, 16px edge margins

Define safe areas for mobile: 44px bottom (iOS home indicator zone), 20px top (status bar zone).

## Component Strategy

Don't design 30+ components before validating the foundations. Start with the 5 that every other component depends on:

1. **Button** — all variants (primary, secondary, ghost/text, destructive, icon-only) × all states (default, hover, active, focus, disabled, loading)
2. **Input / text field** — all states (empty, focus, filled, error, disabled, readonly), with and without label, with and without helper text
3. **Card** — the base layout unit; establish padding, shadow, border-radius, and hover behavior here
4. **Navigation** — header (web) or bottom tab bar (mobile); this defines the spatial logic for everything else
5. **Modal / dialog** — the overlay pattern; establishes z-index hierarchy and focus trap behavior

For each component define:
- **Anatomy**: name every part (container, label, leading-icon, trailing-element, state-layer)
- **States**: the full set relevant to this component
- **Usage rule**: one sentence of when to use it; one sentence of when NOT to use it
- **Accessibility**: ARIA role, keyboard interactions, focus indicator specifications
- **Specifications**: exact padding values, border-radius, shadow, minimum touch target (44×44px)

## Design Tokens

Tokens are the bridge from design decisions to code. Generate tokens only after foundations are decided — not before.

**Token naming convention:** `{category}.{variant}.{state}`
- `color.primary.default` / `color.primary.hover`
- `spacing.component.padding-sm`
- `typography.body.size` / `typography.body.line-height`
- `shadow.card.default`

Design tokens separate the semantic layer (what a value means) from the value itself. This enables theming, white-labeling, and dark mode to be a configuration change rather than a code rewrite.

## Documentation

Every design system needs exactly three documents — not twenty:

1. **Principles** (3 max): the *why* behind key decisions; helps new team members make consistent choices without asking
2. **Usage rules**: what each component and foundation element means, when to use it, when not to
3. **Getting started guide for developers**: how to install tokens, import components, and handle the 5 most common edge cases

Avoid documentation that nobody will maintain. If it can't be auto-generated or easily updated in the same workflow as code changes, simplify it.

## Anti-Patterns to Avoid

- Designing all 30+ components before validating the 5 core ones in real product screens
- Introducing more than 3 brand colors plus semantic colors — palette proliferation is a maintenance tax
- Defining spacing values that aren't on the 8px grid — one-off values are a signal the grid is wrong, not that an exception is needed
- Treating dark mode as a post-launch feature — contrast ratios and color logic are much harder to retrofit
- Skipping the "when NOT to use" rule for each component — without it, components get misused

