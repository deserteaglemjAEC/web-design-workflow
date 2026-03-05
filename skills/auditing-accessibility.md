---
name: auditing-accessibility
description: This skill should be used when the user wants to audit a design or interface for accessibility, check WCAG compliance, test for ADA compliance, evaluate color contrast, assess screen reader support, review keyboard navigation, check focus states, audit ARIA labels, or ensure a product works for users with disabilities. Activate when the user mentions "accessibility audit", "WCAG", "a11y", "color contrast", "screen reader", "keyboard navigation", "ADA compliance", "inclusive design", "focus state", "ARIA", or asks if a design is accessible.
---

# Auditing Accessibility

Accessibility is not a checklist — it's a commitment to building things that work for every user, including the 26% of U.S. adults living with a disability. Accessibility done right also improves usability for everyone: better contrast helps in sunlight, keyboard navigation helps power users, clear error messages help everyone.

Audit to WCAG 2.2 Level AA as the baseline — it's the legal standard in most jurisdictions and the threshold most enterprise procurement requires.

## Start Here: Context Questions

Before auditing, ask the user:

1. Is this a design (visual) audit or a live implementation audit — or both?
2. What platform — web, iOS, Android, or all three?
3. Are there known problem areas the user wants prioritized?
4. Is there a specific compliance requirement — WCAG 2.2 AA, Section 508, EN 301 549?

Design audits catch structural issues early. Implementation audits catch coding failures. Both are needed.

## Severity Classification

Classify every finding by severity to prioritize remediation:

- **Critical**: Blocks task completion for users with disabilities; legal liability; fix before launch
- **Major**: Significantly impairs usability but task is still completable with difficulty; fix in next sprint
- **Minor**: Friction for users with disabilities but workaround exists; fix in backlog

## POUR Framework

Evaluate against the four WCAG principles:

### Perceivable
Users must be able to perceive all interface information.

**Text alternatives:**
- Every meaningful image has an alt attribute with descriptive text
- Decorative images have `alt=""` (empty alt, not missing alt)
- Icons that convey meaning without a text label have ARIA labels
- Complex images (charts, diagrams) have extended descriptions

**Color and contrast:**
- Normal text (below 18pt regular, 14pt bold): minimum 4.5:1 contrast ratio
- Large text (18pt+ regular, 14pt+ bold): minimum 3:1 contrast ratio
- UI components (buttons, inputs, focus indicators): minimum 3:1 contrast ratio
- Color is never the sole means of conveying information — also use icon, label, or pattern

**Multimedia:**
- Video content has captions (not auto-captions — reviewed captions)
- Audio content has transcripts
- Autoplay audio/video: prohibited unless it stops within 3 seconds

**Adaptability:**
- Text resizes up to 200% without loss of content or functionality
- Content doesn't require horizontal scrolling at 320px width (equivalent to 400% zoom on 1280px)
- Orientation is not locked to portrait or landscape unless essential

### Operable
Users must be able to operate the interface.

**Keyboard accessibility:**
- All functionality operable by keyboard (no mouse-only interactions)
- No keyboard traps — users can navigate to and away from every component
- Skip navigation link available to bypass repetitive navigation (web)
- Focus order is logical — follows visual reading order
- Focus indicator is visible: minimum 2px outline, 3:1 contrast between focused and unfocused states

**Navigation:**
- Page titles are descriptive and unique
- Headings used to structure content (not for visual styling) — logical heading hierarchy (H1 > H2 > H3)
- Multiple ways to find content: navigation menu, search, sitemap

**Timing and motion:**
- No content flashes more than 3 times per second (seizure trigger)
- Time limits can be turned off, adjusted, or extended (except real-time tasks)
- Animations respect `prefers-reduced-motion` — provide static alternative
- Autoplay video/audio can be paused or stopped

**Pointer and touch:**
- Touch targets: minimum 44×44 CSS pixels on web; 44×44pt on iOS; 48×48dp on Android
- 8px spacing between touch targets minimum
- Single-pointer alternatives for all multi-point or path-based gestures (e.g., pinch-to-zoom has a zoom button)
- Drag-and-drop has a click alternative

### Understandable
Users must be able to understand the interface.

**Language:**
- Language of page declared in `<html lang="en">`
- Language of content sections that differ from page language declared on those elements

**Predictability:**
- Components that look the same behave the same across the interface
- Navigation appears in the same location on every page
- No context changes on focus or input (dropdowns don't auto-submit; links don't open without user action)

**Input assistance:**
- Labels are visible and persistent (not just placeholder text)
- Error identification: exactly which field has an error, and what the error is
- Error suggestions: if the system knows the fix, tell the user ("Use the format MM/DD/YYYY")
- Error prevention: confirmations for legal, financial, or data-submission actions; reversible where possible

**Cognitive accessibility:**
- Reading level: Grade 8 or below for consumer-facing copy (use Hemingway for verification)
- Consistent terminology: same name for same thing throughout
- Instructions don't rely on sensory characteristics only ("click the green button" fails for colorblind users — say "the Submit button")

### Robust
Content must be interpreted reliably by assistive technologies.

**Valid markup (web):**
- No duplicate IDs
- Elements have complete start and end tags
- Elements nested per their specification

**Name, role, value:**
- Every interactive component has an accessible name (visible label or aria-label)
- Role is appropriate and explicit for custom components
- State changes are programmatically determinable (`aria-expanded`, `aria-checked`, `aria-selected`)

**Status messages:**
- Dynamic content changes announced via ARIA live regions (`aria-live`)
- Form submission success/failure announced without focus moving to message

## Mobile-Specific Requirements

**iOS:**
- VoiceOver order matches visual order
- Custom gestures have VoiceOver alternatives
- UIAccessibility traits set correctly on custom components

**Android:**
- TalkBack order matches visual order
- Content descriptions set on all meaningful images and interactive elements

## Audit Output Format

For each finding, provide:

> **[Component/Location]** | **[Severity]** | **[WCAG Criterion]**
> Issue: [What is wrong, specifically]
> Impact: [Who is affected and how]
> Fix: [Specific remediation with code example or design spec]

Example:
> **Login form — password field** | **Critical** | **WCAG 1.3.1**
> Issue: Label "Password" is implemented as placeholder text only — it disappears on focus
> Impact: Users with cognitive disabilities and screen reader users lose context while typing
> Fix: Add persistent `<label for="password">Password</label>` above the field; placeholder text can remain but must not be the sole label

## Anti-Patterns to Avoid

- Using `title` attributes as the only accessible name — they're not consistently announced
- `aria-label` that contradicts the visible text — screen readers announce aria-label, confusing users who can see both
- Removing focus outlines in CSS without replacing them with something equally visible
- Testing only with keyboard navigation and not with an actual screen reader (NVDA, VoiceOver, TalkBack)
- Treating accessibility as a launch blocker checklist rather than an ongoing design standard

