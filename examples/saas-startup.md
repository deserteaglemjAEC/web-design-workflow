# Example: SaaS Startup Landing Page

SaaS landing pages have one job: convert a visitor into a signup. Every design decision serves that goal.

## Step 1: Research (Phase 1)

```
"Research current web design trends for SaaS and B2B software.
What should we adopt, monitor, or ignore?"
```

## Step 2: Design System (Phase 1)

```
"Create a design system for a project management SaaS called TaskFlow.
Clean, modern, minimal. Professional but not corporate.
Include color palette, typography, and spacing."
```

### Design Direction Notes

- **Dials**: DESIGN_VARIANCE=6, MOTION_INTENSITY=7, VISUAL_DENSITY=5
  - Asymmetric layouts, scroll-triggered animations, moderate density
- **Color**: Zinc/Slate base + one sharp accent (blue, violet, or teal). No neon. No gradients.
- **Typography**: Clean sans-serif only (Geist, Satoshi, or Cabinet Grotesk — never Inter)
- **Aesthetic**: Notion-inspired ultra-minimal, or dark-tech like Linear/Vercel

## Step 3: Build the Landing Page (Phase 2)

```
"Use design-master to build a SaaS landing page for TaskFlow.
DESIGN_VARIANCE=6, MOTION_INTENSITY=7, VISUAL_DENSITY=5

Sections:
1. Hero with headline, subhead, CTA, and product screenshot
2. Social proof bar (logos of companies using it)
3. Feature bento grid (4-6 features with micro-animations)
4. How it works (3-step process)
5. Pricing table (Free, Pro, Enterprise)
6. Testimonials
7. Final CTA section
8. Footer"
```

### Key Sections

1. **Hero** — headline that states the benefit (not the feature), one CTA, product screenshot or animation
2. **Social proof** — company logos or "Trusted by X teams" — appears before features
3. **Feature grid** — bento layout, not 3-column cards. Each feature gets a micro-animation
4. **Pricing** — 3 tiers max. Highlight the recommended plan. Annual/monthly toggle
5. **CTA** — repeat the primary CTA at the bottom. Same button, same copy

## Step 4: Generate Product Screenshots (Phase 2)

```
"Generate a product screenshot mockup for a project management dashboard.
Clean UI with task cards, progress bars, and team avatars.
Dark theme, modern design, shown inside a browser mockup frame.
No text artifacts, sharp detail, product photography style."
```

## Step 5: SEO + Schema (Phase 4)

```
"Add SEO to the TaskFlow landing page. Target 'project management tool'
and 'team task management software'. Add SoftwareApplication schema,
FAQ schema for the pricing section, and proper OG tags for social sharing."
```

- SoftwareApplication schema (pricing, features, rating)
- Long-tail keywords: "project management tool for small teams"
- FAQ schema under pricing (reduces support load and gets rich results)

## Step 6: Security + Performance (Phase 3)

```
"Run a security review on my SaaS landing page.
Check the signup form and any API endpoints.
Also check Core Web Vitals — this page needs to load fast."
```

SaaS pages are performance-critical — every 100ms of load time costs conversions.

## You're Done When

- [ ] Above-the-fold loads in under 1.5 seconds
- [ ] CTA appears at least twice (hero + bottom)
- [ ] Pricing is clear with no hidden costs
- [ ] Social proof visible before features section
- [ ] Mobile responsive with touch-friendly pricing toggle
- [ ] SoftwareApplication schema markup present
- [ ] OG image is 1200x630px and looks good when shared
- [ ] Signup form validates email and handles errors inline
- [ ] No accessibility violations (WCAG AA)
