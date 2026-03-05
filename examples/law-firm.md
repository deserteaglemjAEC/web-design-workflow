# Example: Law Firm Website

Law firm websites need to balance authority with approachability. Here's how to use the Web Design Workflow for a legal practice — step by step.

## Step 1: Research (Phase 1)

Open Claude Code and type:

```
"Research current web design trends for law firms.
What should we adopt, monitor, or ignore?"
```

Claude will analyze industry trends and give you a prioritized recommendation list.

## Step 2: Design System (Phase 1)

```
"Create a design system for a law firm called Parker & Associates.
Navy blue primary color, professional and trustworthy feel.
Include color palette, typography scale, and spacing system."
```

## Step 3: Build the Site (Phase 2)

```
"Use the design-master skill to build a full law firm website
for Parker & Associates. Use these dials:
DESIGN_VARIANCE=3, MOTION_INTENSITY=4, VISUAL_DENSITY=4

Build these pages:
1. Homepage with hero, practice areas grid, and trust signals
2. Practice area page for Family Law
3. Attorney profile page
4. Contact/consultation page with form

Use the design system we just created."
```

### Design Direction Notes

- **Dials**: DESIGN_VARIANCE=3, MOTION_INTENSITY=4, VISUAL_DENSITY=4
  - Conservative layout, subtle motion, clean density — professional authority
- **Color**: Deep navy or forest green primary + warm neutral grays. Avoid stark black.
- **Typography**: Serif for headlines (signals authority + tradition), sans-serif for body
- **Photography**: Real team photos > stock. If generating with nanobanana:
  ```
  Professional law office interior, warm lighting, mahogany desk,
  legal books on shelves, modern architecture, editorial photography,
  no text, wide aspect ratio
  ```

## Step 4: Accessibility Audit (Phase 4 — do this early)

Law firm websites are frequent ADA lawsuit targets — WCAG AA is non-negotiable.

```
"Run an accessibility audit on my law firm site.
This is high priority — law firms are common ADA lawsuit targets."
```

- Run this EARLY, not after launch
- Ensure all PDFs linked from the site are also accessible
- Contact forms must have proper labels and error messages

## Step 5: Security Review (Phase 3)

```
"Run a security review on this project. The contact form
collects client intake data — make sure it's secure."
```

Law firms handle sensitive client data. The consultation form needs:
- Input validation on all fields
- HTTPS enforced
- No client data in logs or error messages

## Step 6: SEO Setup (Phase 4)

```
"Add SEO optimization to all pages. This is a local law firm
in Austin, TX. Add LocalBusiness schema markup, FAQ schema
on practice area pages, and proper meta tags."
```

### SEO Notes for Law Firms

- Local SEO is critical — LocalBusiness schema markup on every page
- Practice area pages should target "[practice area] lawyer [city]" keywords
- FAQ schema on practice area pages (common legal questions)
- Google Business Profile must be claimed and optimized

## You're Done When

- [ ] All 4 pages built and responsive (test at 375px, 768px, 1440px)
- [ ] Accessibility audit passes WCAG AA (zero critical issues)
- [ ] Security review shows no critical/high vulnerabilities
- [ ] Every page has unique title tag, meta description, and OG tags
- [ ] LocalBusiness schema markup on every page
- [ ] Contact form validates input and handles errors gracefully
- [ ] Site loads in under 2.5 seconds (LCP)
