---
name: specifying-figma-layouts
description: This skill should be used when the user needs Figma-ready technical specifications, wants to set up auto-layout, define component variants, prepare design handoff for developers, configure design tokens in Figma, create component architecture, or convert a design description into Figma-specific implementation instructions. Activate when the user mentions "Figma", "auto-layout", "component variants", "Figma tokens", "design handoff", "Figma specs", "component properties", "constraints", "prototyping", "Figma frames", or asks how to build or organize something in Figma.
---

# Specifying Figma Layouts

Figma is a communication tool as much as a design tool. Specs that work are ones developers can follow without a conversation — every value explicit, every state named, every interaction mapped. The test of good Figma specs: can a developer implement it correctly without asking follow-up questions?

## Start Here: Context Questions

Before generating specifications, ask the user:

1. What component or screen is being specified?
2. What design system (if any) are tokens pulling from — Figma Tokens plugin, custom variables, or none?
3. Who is the handoff audience — front-end devs, a design team, or both?
4. What framework will consume the handoff — React, Vue, Flutter, native iOS/Android?
5. Are variants needed, or is this a single-state specification?

The answers determine the level of technical detail needed and the naming conventions to use.

## Frame Structure

Organize every Figma file with consistent page and layer conventions. Developers read Figma left-to-right like code — messy layers produce incorrect implementations.

**Page organization:**
- `🎨 Design` — production-ready screens and components
- `🔩 Components` — master component library
- `📐 Tokens` — color/type/spacing style definitions
- `🧪 Playground` — WIP, experiments, rejected explorations (never hand off from here)

**Layer naming convention:** `Component/Variant/State`
- `Button/Primary/Default`
- `Button/Primary/Hover`
- `Card/Featured/Loading`

**Frame naming convention:** Screens use route-style names: `Home/Desktop`, `Settings/Mobile/Profile`, `Onboarding/Step-2`

## Auto-Layout Specifications

For every component, define auto-layout properties explicitly. Vague specs produce inconsistent implementation.

**Auto-layout output format for each component:**

```
Component: [Name]
Direction: horizontal | vertical
Alignment: top-left | center | space-between | etc.
Padding: top [n]px · right [n]px · bottom [n]px · left [n]px
Item spacing: [n]px
Resizing (width): hug-contents | fill-container | fixed [n]px
Resizing (height): hug-contents | fill-container | fixed [n]px
Min width: [n]px (if applicable)
Max width: [n]px (if applicable)
```

**Key Figma resizing rules:**
- `hug-contents`: component grows to fit its content — use for buttons, tags, labels
- `fill-container`: component stretches to fill its parent — use for inputs, cards in a grid
- `fixed`: component has an explicit, non-responsive size — use only when necessary

**Common auto-layout patterns:**

*Horizontal button with icon:*
- Direction: horizontal, Alignment: center
- Padding: 12px top/bottom, 16px left/right
- Item spacing: 8px
- Width: hug-contents, Height: fixed 44px

*Vertical card:*
- Direction: vertical, Alignment: top-left
- Padding: 16px all sides
- Item spacing: 12px
- Width: fill-container, Height: hug-contents

## Component Architecture

**Master component structure:**
Every interactive component needs a master component with all variants. Avoid one-off component instances — they break when the master is updated.

**Variant properties (the 4 types):**
1. `Variant` — mutually exclusive visual styles (Size: small/medium/large)
2. `Boolean` — toggle on/off (Has icon: true/false, Loading: true/false)
3. `Instance swap` — swap a nested component (Icon: left-arrow/right-arrow/close)
4. `Text` — editable text content override (Label: "Submit")

**Variant combination matrix format:**

```
Component: Button
Variants:
  Type: Primary | Secondary | Ghost | Destructive
  Size: Small (32px) | Medium (40px) | Large (48px)
  State: Default | Hover | Active | Disabled | Loading
  Has icon: True | False

Total variants: 4 × 3 × 5 × 2 = 120
```

Only create variant combinations that exist in the actual product — 120 states for one button creates maintenance debt if most are never used. Create the states that exist; add others when needed.

## Design Token Integration

**Color styles:** Name as `{category}/{variant}/{state}`
- `Primary/500` (the base color)
- `Primary/500/Hover` (the hover state color)
- `Semantic/Error/Default`
- `Neutral/100`

**Text styles:** Name as `{level}/{size}/{weight}`
- `Display/Large/Bold`
- `Body/Medium/Regular`
- `Caption/Small/Medium`

**Effect styles (shadows):**
- `Shadow/Card` — subtle card elevation
- `Shadow/Dropdown` — dropdown overlay
- `Shadow/Modal` — modal overlay

**Spacing** (use Figma's spacing tokens or consistent padding/gap values from the 8px grid): always use the spacing scale — never type arbitrary padding values.

## Prototype Connections

For user flow documentation, define interactions explicitly:

**Interaction map format:**
```
Frame: [Source screen/component]
Trigger: On click | On hover | On drag | After delay
Action: Navigate to [Frame] | Open overlay | Close overlay | Scroll to
Animation: Smart animate | Dissolve | Move (direction)
Easing: Ease in | Ease out | Ease in-out | Linear
Duration: [n]ms
Delay: [n]ms (if applicable)
```

Smart animate only works between frames that share layers with the same name — verify layer name consistency before using it.

## Developer Handoff Preparation

Before marking a file ready for developer handoff:

1. **Run a layer audit**: all layers named, no unnamed groups, all components using master instances (not detached)
2. **Verify spacing**: no hardcoded gaps; all spacing uses grid or spacing tokens
3. **Export assets**: mark all raster images for export (1×, 2×, 3×); SVG icons as SVG; logos as both SVG and PDF
4. **Check all states**: every component that has a hover/focus/disabled state has it designed
5. **Add redlines** for non-obvious spacing: annotate any value that isn't directly readable in inspect panel

**Asset naming for export:**
- Images: `product-screenshot-hero@2x.png`
- Icons: `icon-arrow-right.svg`
- Logos: `logo-primary.svg`, `logo-reversed.svg`

## Accessibility Annotations

Add accessibility annotations as a dedicated annotation layer (not part of the component itself):

- **Tab order**: number each interactive element in keyboard navigation order
- **ARIA labels**: annotate when the visible label differs from what a screen reader should say
- **Roles**: annotate non-standard interactive elements (custom dropdowns, date pickers)
- **Focus indicators**: annotate focus ring style for each component that receives focus

## Anti-Patterns to Avoid

- Detaching component instances before delivery — developers can't maintain detached components
- Using opacity to represent disabled states instead of a `Disabled` variant — opacity doesn't communicate semantics
- Unnamed layers and groups — "Group 47" tells a developer nothing
- One master frame with everything on it — use separate frames per screen/state
- Embedding auto-layout-breaking absolute positioning inside auto-layout frames

## Additional Resources

- **`references/component-architecture.md`** — Full component variant matrix templates for Button, Input, Card, Navigation, Modal, and Form elements with complete property definitions
