---
name: designing-ui-patterns
description: This skill should be used when the user wants to design a UI, create UX patterns, design app screens, define user flows, spec a dashboard, create wireframes, design a fintech app, social app, e-commerce interface, or any mobile or web application interface. Activate when the user mentions "UI design", "UX patterns", "screen design", "wireframe", "app UI", "user flow", "onboarding screen", "dashboard layout", "navigation pattern", or asks how a feature should look or work. Also use when the user needs to define interaction specifications, micro-interactions, or accessibility for a specific interface.
---

# Designing UI Patterns

Good UI design is invisible — users achieve their goals without noticing the interface. Start with what users need to accomplish, not with what looks impressive.

## Start Here: Context Questions

Before designing anything, ask the user:

1. What platform — iOS, Android, web app, or responsive web?
2. Who is the primary user, and what is the single most important thing they need to do?
3. Does a design system or component library already exist? (Affects which components to use vs. invent)
4. What are the 3 biggest usability complaints users have with the current solution — or with competitors?
5. Which screen is most critical to get right first?

Design the most critical screen first. Breadth first produces shallow design; depth first produces decisions that scale.

## Hierarchy and Layout

Visual hierarchy is a reading guide. Users don't read UI — they scan it. Design for the scan.

**Three-level hierarchy:**
1. **Primary**: The one thing users must see first (usually the main action or the current state)
2. **Secondary**: Supporting information that enables the primary action
3. **Tertiary**: Details accessed after primary and secondary are understood

Test hierarchy by squinting at the screen — the primary element should still be identifiable at low resolution.

**Layout decisions:**
- F-pattern: left-to-right reading cultures scan left→right across the top, then down the left edge. Put primary navigation and key information there.
- Z-pattern: landing pages and sparse layouts follow a Z — top-left → top-right → diagonal → bottom-left → bottom-right. CTA goes bottom-right.
- Content density: more density suits power users with frequent use (dashboards, admin panels); less density suits consumers and infrequent tasks (onboarding, checkout). Don't default to dense — earn it.

## Platform-Specific Patterns

**Mobile (iOS/Android):**
- Primary navigation: bottom tab bar (iOS) or bottom navigation bar (Android) for 3–5 destinations; drawer for 6+
- Stack navigation for drill-down flows (list → detail → action)
- Modal sheets for temporary contexts (filters, quick actions, confirmations)
- Minimum touch target: 44×44pt (iOS), 48×48dp (Android)
- Thumb zone: primary actions in the bottom 40% of the screen; destructive or rare actions at top

**Web app:**
- Sidebar navigation for 6+ destinations or complex hierarchies
- Top navigation for 3–5 destinations or content-heavy sites
- Modal dialogs for confirmations, quick forms; full-page routes for complex tasks
- Hover states required; touch states optional but recommended
- Keyboard navigation must work: Tab, Enter, Space, Arrow keys, Escape

## Critical Screen Design

Design 3 screens in depth before expanding. For each screen, define:

**1. Layout structure**: Describe the grid used, major content regions, and their relative proportions. What takes the most space, and why?

**2. Component inventory**: List every element on screen — headers, buttons, inputs, cards, labels, icons, navigation elements. Nothing should be on the screen without a reason.

**3. Interaction specifications**: For each interactive element: what happens on tap/click? What transition plays? What state changes? What is the undo mechanism if the action is destructive?

**4. Empty state**: What does the screen look like before there is any data? Empty states should communicate: what this screen does, why it's empty, and what action fills it. Never show a blank screen.

**5. Loading state**: Skeleton screens for content loading (not spinners for initial loads). Spinners only for actions in progress. Set maximum wait expectations — show progress for anything over 2 seconds.

**6. Error state**: Every screen that can fail must have an error treatment. Error messages need: what went wrong (plain language), what to do next (actionable), a way to retry or escalate.

**Screens to prioritize** (in order of user and business criticality):
- Home/Dashboard: the "state of the world" view
- Primary task screen: where the core user job gets done
- Onboarding: first experience sets long-term retention expectations
- Empty/error states: often designed last, experienced early

## Component Specifications

**Button hierarchy (use in this priority order):**
1. Primary: one per screen maximum, the main action
2. Secondary: supporting actions (2–3 per screen max)
3. Ghost/Text: low-emphasis actions (cancel, back, view more)
4. Destructive: red variant, always requires confirmation before executing

**Form patterns:**
- Labels above fields (not placeholder text — placeholder disappears on focus)
- Inline validation: show errors as soon as the field loses focus, not only on submit
- Error messages: "Enter a valid email address" not "Invalid email"
- Success state: confirm completion before navigating away from multi-step forms

**Card patterns:**
- Cards should do one thing — one primary action, one destination, one piece of content
- Card padding: minimum 16px internal, 8px gap between cards
- Avoid cards-within-cards (nesting creates visual confusion)

## Micro-Interactions

Define transitions that reward interaction and communicate state:

- **Duration**: 150–250ms for UI transitions; anything slower feels sluggish, anything faster feels abrupt
- **Easing**: ease-out (fast start, slow end) for elements entering; ease-in for elements leaving; ease-in-out for position changes
- **Haptic feedback (mobile)**: light impact for selections, medium for confirmations, heavy for errors or warnings
- **Reduce motion**: always provide a non-animated alternative for users with vestibular disorders (CSS `prefers-reduced-motion`)

## Accessibility Requirements

Build accessibility in at design time, not as a retrofit:

- **Color contrast**: 4.5:1 for body text, 3:1 for large text and interactive UI
- **Color independence**: never use color as the only way to convey information (also use icon, label, or pattern)
- **Focus states**: every interactive element needs a visible focus indicator (2px outline, 3:1 contrast minimum)
- **Touch targets**: minimum 44×44pt on mobile; interactive elements need adequate spacing between them (8px gap minimum)
- **Dynamic Type**: on iOS, support font sizes up to 310% — test layouts at accessibility sizes

## Designer's Notes Format

When explaining design decisions, use this format: **Decision** (what was chosen) → **Why** (the reasoning) → **What to watch for** (when this decision should be revisited). This makes handoff documentation actionable rather than decorative.

## Anti-Patterns to Avoid

- Designing 8 screens without validating the first 3 — shallow breadth produces shallow decisions
- Using placeholder text as form labels — it disappears on focus and fails accessibility
- Inline error messages only on submit — users lose context of which field failed
- Three primary buttons on one screen — hierarchy collapses when everything is primary
- Building feature-complete empty states last — they're the first thing new users see

