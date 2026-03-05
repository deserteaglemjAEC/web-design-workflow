---
name: critiquing-designs
description: This skill should be used when the user wants a design critique, design review, UX evaluation, design feedback, heuristic analysis, or wants to know what's wrong with a design and how to fix it. Activate when the user mentions "design critique", "review this design", "design feedback", "what's wrong with this UI", "UX review", "evaluate this layout", "design audit", "heuristic evaluation", or shares a design and asks for thoughts, improvements, or suggestions.
---

# Critiquing Designs

A good design critique is a teaching moment, not a verdict. The goal is actionable improvements the designer can act on immediately, in priority order. Vague praise and vague criticism both waste time — every piece of feedback needs a specific location, a specific problem, and a specific fix.

## Start Here: Context Questions

Before evaluating, ask:

1. What is this design for — what does it do and who uses it?
2. What is the primary user goal on this screen/flow?
3. What stage is this — early concept, pre-launch review, or post-launch audit?
4. Are there known constraints (existing tech, brand guidelines, accessibility requirements)?
5. Is there a specific area of concern the designer wants focused attention on?

The stage matters. Early concept feedback should focus on strategy and structure; pre-launch feedback focuses on execution and edge cases; post-launch focuses on measurable usability issues.

## Heuristic Evaluation

Evaluate against Nielsen's 10 Usability Heuristics. For each one, provide: a finding (specific, with location) or a pass.

**1. Visibility of System Status**
Does the user always know what's happening? Look for: loading states, progress indicators, success/error feedback after actions, active navigation states.
- Pass if: every action has a response within 0.1s (instant), 1s (feedback), or 10s (progress indicator)
- Flag if: actions complete without visual confirmation, or states are ambiguous

**2. Match Between System and Real World**
Does the language and mental model match the user's world? Look for: jargon, insider terminology, unfamiliar icons, processes that don't match real-world equivalents.

**3. User Control and Freedom**
Can users undo and escape? Look for: back buttons, cancel options, undo functionality, "are you sure?" dialogs for destructive actions, clear exit paths from every state.

**4. Consistency and Standards**
Are similar things treated the same way? Look for: inconsistent button styles for the same action, different terminology for the same concept, platform conventions violated without reason (iOS back-left, Android navigation-bottom).

**5. Error Prevention**
Does the design prevent mistakes before they happen? Look for: confirmations before destructive actions, constraints on input fields, disabled states that prevent invalid actions, clear affordances.

**6. Recognition Rather Than Recall**
Is everything visible rather than hidden in memory? Look for: navigation that requires remembering where things are, actions buried in menus that should be contextual, form fields without labels.

**7. Flexibility and Efficiency of Use**
Does it work for both novice and expert users? Look for: keyboard shortcuts or power-user paths, bulk actions for repeat tasks, search functionality for large lists, saved preferences.

**8. Aesthetic and Minimalist Design**
Is everything necessary? Look for: information that doesn't help the user decide or act, competing visual elements at the same weight, decorative elements that increase cognitive load.

**9. Help Users Recognize, Diagnose, and Recover from Errors**
When errors occur, are they clear and actionable? Look for: error messages in plain language, specific guidance on how to fix the error, no blame-casting language ("You entered an invalid email" vs "The email address format is incorrect").

**10. Help and Documentation**
Is help available when needed? Look for: complex features without contextual help, onboarding for non-obvious workflows, tooltip support for icons or technical terms.

## Visual Hierarchy Analysis

Test visual hierarchy in 5 seconds: look at the screen without reading any text. Ask:
- What's the first element that draws the eye?
- Is that the right element (the most important action or information)?
- Is there a clear second element after the first?
- Is there visual rest — enough white space that the primary elements can breathe?

**Common hierarchy failures:**
- Everything is the same visual weight (buttons same size as labels, headings too close to body size)
- Multiple competing primary elements (three things are trying to be the most important thing)
- Important information in small, gray text while decorative elements are large and colorful

## Typography Audit

- **Font choice**: does it match the brand personality? A playful rounded sans-serif on a legal document feels wrong; a rigid geometric on a children's app feels cold.
- **Type scale**: is there enough size difference between heading levels? A 4px difference between H2 and H3 doesn't create hierarchy.
- **Line length**: 45–75 characters per line for body text. Lines that are too long (100+ characters) or too short (30 characters) reduce readability.
- **Contrast**: body text should meet 4.5:1 on its background. Check all gray-on-white combinations — light gray text is a common accessibility failure.
- **Spacing**: line height 1.4–1.6× for body text. Tight line height makes paragraphs unreadable; excessive line height disconnects lines.

## Color Analysis

- **Brand alignment**: do the colors express the right emotion for the product?
- **Contrast compliance**: run every text+background pair through a contrast checker. Flag any failures.
- **Meaning**: is color used meaningfully (red = error, green = success) or arbitrarily?
- **Color independence**: does any important information depend solely on color to communicate? (e.g., a graph where red/green are the only differentiators — fails for colorblindness)
- **Dark mode**: if the product supports it, check it separately — many designs look fine in light mode and break in dark.

## Strategic Alignment

Before prioritizing visual fixes, check strategic alignment:
- Does the primary CTA serve the business objective?
- Is the value proposition visible above the fold (on landing pages)?
- Does the information architecture match the user's priority order — or the business's?
- Would a user with no context understand what this is and what to do within 5 seconds?

## Prioritized Recommendations

Deliver feedback in three tiers:

**Critical (fix before launch):**
- Accessibility failures (WCAG AA contrast violations, keyboard inaccessible elements)
- Usability failures that prevent task completion
- Missing error/empty/loading states
- Brand inconsistencies that undermine credibility

**Important (fix in next iteration):**
- Hierarchy issues that create confusion but don't block completion
- Missing affordances that force trial-and-error discovery
- Inconsistencies that reduce trust without blocking completion

**Polish (nice to have):**
- Micro-interaction improvements
- Copy refinements
- Visual alignment and spacing cleanup

## Feedback Format

Use this format for each finding:

> **[Location]**: [What the problem is] → [Why it matters] → [Specific recommended fix]

Example:
> **Primary CTA button**: Uses secondary button style (outlined) despite being the main conversion action → Users underestimate its importance relative to three competing links → Change to filled primary style with higher contrast; remove or demote competing actions

## Anti-Patterns in Critique

- "It just doesn't feel right" — feelings are data but they're not feedback; translate the feeling into a specific visual or structural issue
- Leading with praise to soften criticism — the designer needs to know the most important thing first
- Critiquing decisions that are constraints (brand colors, tech limitations) — flag them as constraints, not as failures
- Feedback without a suggested direction — "this is wrong" is less useful than "this is wrong because X, and here's one way to fix it"
