---
name: translating-design-to-code
description: Convert any design into production code — from a verbal description, screenshot, wireframe, mockup, or design tool export. Supports React, Vue, Svelte, Next.js, and plain HTML/CSS. Covers component architecture, responsive implementation, accessibility semantics, and testing. Works with any design input — no specific design tool required.
---

# Translating Design to Code

Good design-to-code translation preserves three things: the visual intent, the interaction behavior, and the accessibility semantics. Generating code that looks right but is semantically wrong (div-soup, missing ARIA, no keyboard support) produces a visual copy, not a real implementation.

## Start Here: Context Questions

Before writing any code, ask the user:

1. What is the tech stack — React, Vue, Svelte, Next.js, plain HTML/CSS? With or without TypeScript?
2. Is there an existing component library or design system to pull from (Shadcn, Radix, Chakra, custom)?
3. What styling approach — Tailwind, CSS Modules, styled-components, vanilla CSS?
4. Is this a new component or a modification of something that exists?
5. What are the responsive requirements — mobile-first, specific breakpoints?

These answers prevent a complete rewrite after the first output. A React TypeScript Tailwind answer is different code than a Vue vanilla CSS answer.

## Component Architecture

Design before implementing. For any non-trivial component, define:

**Component hierarchy** (before writing any code):
```
ParentContainer
  ├── HeaderSection
  │   ├── Logo
  │   └── NavigationMenu
  │       └── NavItem (repeating)
  └── ContentArea
      ├── HeroSection
      └── FeatureGrid
          └── FeatureCard (repeating)
```

**Props interface** (TypeScript):
```typescript
interface ButtonProps {
  label: string;
  variant: 'primary' | 'secondary' | 'ghost' | 'destructive';
  size?: 'sm' | 'md' | 'lg';
  disabled?: boolean;
  loading?: boolean;
  onClick?: () => void;
  icon?: React.ReactNode;
}
```

Define the interface first — it reveals what the component needs and catches design decisions that weren't explicit (what size is the default? what happens when both icon and loading are true?).

## Production Code Standards

**Responsive implementation:**
- Mobile-first: base styles apply at all sizes, breakpoints add complexity
- Use relative units for typography (rem/em) and layout (%, fr), fixed units only for pixel-perfect elements
- Never use magic pixel values — pull from the spacing scale

**Accessibility (built in, not added later):**
- Semantic HTML: `<button>` not `<div onclick>`, `<nav>` not `<div class="nav">`, `<h1>` through `<h6>` in logical order
- ARIA only when semantic HTML is insufficient — `aria-label` for icon buttons, `aria-expanded` for dropdowns, `aria-live` for dynamic content
- Focus management: after modal opens, focus moves to first focusable element; after modal closes, focus returns to trigger
- Keyboard handlers: Enter and Space for buttons, Arrow keys for custom select/listbox, Escape to close modals/dropdowns

**State handling:**
- Loading: disable the trigger element during async operations; show loading indicator
- Error: surface error messages near the point of failure, not only in a toast
- Empty: always handle the case where the data array is empty
- Disabled: disabled prop should disable interaction, not just visually dim

## Styling Implementation

**Design token mapping:**

When a design system has tokens, map them explicitly:
```css
/* Instead of: */
background: #3B82F6;
padding: 12px 16px;

/* Use: */
background: var(--color-primary-500);
padding: var(--spacing-3) var(--spacing-4);
```

**Tailwind class ordering** (consistency reduces cognitive overhead):
Layout → Display → Position → Sizing → Spacing → Typography → Colors → Borders → Effects → States

Example: `flex items-center justify-between w-full px-4 py-3 text-sm font-medium text-gray-900 bg-white border border-gray-200 rounded-lg shadow-sm hover:bg-gray-50 focus:outline-none focus:ring-2`

**Dark mode:**
- CSS class-based (`dark:` prefix in Tailwind, `:root[data-theme="dark"]` for CSS vars)
- Don't hardcode colors in dark mode — use semantic tokens that invert
- Test at implementation time, not after

## Animation and Transitions

Keep transitions purposeful and fast:
- Entry/exit animations: 150–200ms ease-out
- State change transitions (hover, focus): 100–150ms
- Page transitions: 200–300ms
- Use `prefers-reduced-motion` media query to disable animations for users who need it

```css
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    transition-duration: 0.01ms !important;
  }
}
```

## Performance Considerations

**Image handling:**
- Use `next/image` or equivalent for automatic optimization, lazy loading, and responsive `srcset`
- Always specify `width` and `height` to prevent layout shift (CLS)
- Serve WebP with fallback

**Component optimization (React):**
- `React.memo` for components that receive the same props frequently
- `useMemo` for expensive calculations; `useCallback` for stable function references passed to children
- Code split at route level and for large below-fold components (`React.lazy`)

**Bundle size:**
- Tree-shake icon libraries — import individual icons, not entire icon sets
- Prefer CSS animations over JS animations for simple transitions

## Testing Strategy

Every component needs three test types:

**Unit tests (React Testing Library):**
- Renders without errors with required props
- Renders each significant variant
- Handles each interactive state (onClick fires, form submits, loading/error states)

**Accessibility tests (axe-core via jest-axe):**
```typescript
it('has no accessibility violations', async () => {
  const { container } = render(<Button label="Submit" />);
  expect(await axe(container)).toHaveNoViolations();
});
```

**Responsive test cases (Playwright or Storybook viewport addon):**
- Test at mobile (375px), tablet (768px), desktop (1440px)
- Verify layout doesn't break at text zoom (200%)

## Designer's Intent Comments

Add comments in code that explain why a design decision was made, not what the code does:

```typescript
// Designer's intent: Button padding asymmetric (12px top/bottom, 20px left/right)
// to compensate for optical weight of uppercase text at this size
className="py-3 px-5"

// Designer's intent: Shadow only on bottom-right to create directional depth
// consistent with the simulated light source from top-left in the design system
className="shadow-[2px_2px_0px_0px_rgba(0,0,0,0.15)]"
```

These comments survive refactoring and prevent well-meaning developers from "fixing" intentional design decisions.

## Anti-Patterns to Avoid

- `<div>` elements for interactive components — they have no keyboard or screen reader support
- Inline styles for values from the design system — they bypass tokens and prevent theming
- Copy-pasting design token values as raw hex/pixel values instead of variables
- Implementing loading states after launch — they're visible in every user session
- Testing only at the designed viewport width — responsive failures appear at 375px

