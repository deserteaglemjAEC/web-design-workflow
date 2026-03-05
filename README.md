# The Web Design Workflow — Claude Skills System

A curated collection of 12 Claude skills that form a complete web design system. These skills transform Claude into a specialized design partner — covering everything from UI patterns and accessibility audits to AI image generation and Figma handoff specs.

This is the **Web Design Workflow** — a reusable system for any web design project.

## What Are Skills?

Skills are markdown instruction files that give Claude deep domain expertise. When loaded, Claude follows the skill's methodology instead of generating generic responses. Think of them as "expert modes" you can activate on demand.

## How to Install

### Option A: Claude Code (CLI) — Full Power

If you use Claude Code (the terminal CLI), drop the entire `skills/` folder into your config:

```bash
cp -r skills/* ~/.claude/skills/
```

Each skill auto-activates when you describe a matching task. You can also invoke them directly:
```
"Use the design-master skill to review this landing page"
"Run an accessibility audit on this component"
```

### Option B: Claude.ai (Web) — Projects

1. Go to claude.ai and create a new **Project**
2. Click "Add project knowledge"
3. Upload each `.md` file from the `skills/` folder as project knowledge
4. Claude will reference these skills in every conversation within that project

**Recommended project setup:**
- Project 1: "Web Design" — add: design-master, designing-ui-patterns, building-design-systems, critiquing-designs, researching-design-trends
- Project 2: "Frontend Dev" — add: translating-design-to-code, frontend-patterns, auditing-accessibility, specifying-figma-layouts
- Project 3: "Image Generation" — add: nanobanana-image-generation, nanobanana-prompt-library, image-enhancer

### Option C: Cursor / Windsurf / Other AI IDEs

Copy the `.md` files into your project's rules directory:
- **Cursor**: `.cursor/rules/`
- **Windsurf**: `.windsurfrules/`

---

## Skills Included

### Core Design Skills

| Skill | File | What It Does |
|-------|------|-------------|
| **Design Master** | `design-master.md` | Premium visual interface design — React/Next.js/Tailwind + email HTML. Aesthetic philosophy, motion specs, CTA rules, dial-based design variance, pre-flight checks. The most comprehensive design skill. |
| **Designing UI Patterns** | `designing-ui-patterns.md` | UI/UX patterns, wireframes, user flows, dashboard layouts. Covers platform-specific patterns (iOS, Android, web), micro-interactions, and accessibility requirements. |
| **Building Design Systems** | `building-design-systems.md` | Create complete design systems — color palettes, typography scales, spacing systems, design tokens, component libraries. Start-to-finish methodology. |
| **Critiquing Designs** | `critiquing-designs.md` | Structured design critique using Nielsen's 10 heuristics. Produces actionable, prioritized feedback with severity levels and specific fixes. |
| **Researching Design Trends** | `researching-design-trends.md` | Competitive visual analysis, emerging aesthetics, trend adoption phase analysis. Helps you decide what to adopt, monitor, or ignore. |

### Implementation Skills

| Skill | File | What It Does |
|-------|------|-------------|
| **Translating Design to Code** | `translating-design-to-code.md` | Convert Figma/mockups to production code (React, Vue, Svelte). Covers component architecture, accessibility semantics, responsive implementation, and testing. |
| **Frontend Patterns** | `frontend-patterns.md` | React composition patterns, state management, performance optimization, forms, animations, accessibility patterns — with full code examples. |
| **Specifying Figma Layouts** | `specifying-figma-layouts.md` | Figma auto-layout specs, component variants, design tokens, developer handoff documentation. Makes Figma files implementation-ready. |
| **Auditing Accessibility** | `auditing-accessibility.md` | WCAG 2.2 AA compliance audits. Covers the full POUR framework — perceivable, operable, understandable, robust. Produces severity-classified findings with specific remediation. |

### Image Generation Skills

| Skill | File | What It Does |
|-------|------|-------------|
| **Nanobanana Image Generation** | `nanobanana-image-generation.md` | Generate and edit images using Google Gemini API. Supports multiple aspect ratios, resolutions up to 4K, and image editing/compositing. |
| **Nanobanana Prompt Library** | `nanobanana-prompt-library.md` | 6,000+ curated image generation prompts organized by use case (social media, product marketing, e-commerce, web/app design, posters, avatars, etc.). Includes a remix workflow for customization. |
| **Image Enhancer** | `image-enhancer.md` | Upscale, sharpen, and optimize images for web, social media, or print. Batch processing supported. |

---

## Optimal Workflow Guide

### Workflow 1: Designing a New Website

```
Step 1: Research  -->  Use "researching-design-trends" to analyze current trends in your client's industry
Step 2: System    -->  Use "building-design-systems" to establish color, typography, spacing foundations
Step 3: Design    -->  Use "designing-ui-patterns" to design the critical screens (home, primary task, onboarding)
Step 4: Critique  -->  Use "critiquing-designs" to self-review before client presentation
Step 5: Spec      -->  Use "specifying-figma-layouts" to prepare dev-ready Figma handoff
Step 6: Build     -->  Use "translating-design-to-code" + "frontend-patterns" to implement
Step 7: Audit     -->  Use "auditing-accessibility" to verify WCAG AA compliance
Step 8: Assets    -->  Use "nanobanana" skills to generate hero images, product shots, social assets
```

### Workflow 2: Design Review / Critique

```
Step 1: Load the design (screenshot, Figma link, or live URL)
Step 2: Use "critiquing-designs" for heuristic evaluation
Step 3: Use "auditing-accessibility" for compliance check
Step 4: Combine findings into a prioritized report (Critical > Important > Polish)
```

### Workflow 3: Generating Website Imagery

```
Step 1: Describe what you need (hero image, product shot, background texture, etc.)
Step 2: Use "nanobanana-prompt-library" to find a matching curated prompt from the 6,000+ library
Step 3: Select a prompt template and customize it for your specific needs
Step 4: Use "nanobanana-image-generation" to generate the image
Step 5: Use "image-enhancer" to upscale/sharpen for production use
```

**Nanobanana Pro Tips:**
- Always append "no text" to prompts — AI-generated text is unreliable
- Generate at 1K first for testing, then regenerate at 2K/4K for final output
- Use `--size 1344x768` for hero banners (16:9 landscape)
- Use `--size 1024x1024` for logos and icons (1:1 square)
- Use `--size 768x1344` for social stories (9:16 portrait)
- For product shots on white backgrounds, generate then use Photoroom or remove.bg for background removal
- Add text overlays in Figma after generation — never in the AI prompt

### Workflow 4: Client Landing Page (End-to-End)

```
Step 1: "researching-design-trends" — What's working in the client's industry right now?
Step 2: "building-design-systems" — Establish brand foundations (even a minimal set)
Step 3: "design-master" (FRONTEND mode) — Set the dials and build the page
         - Configure DESIGN_VARIANCE, MOTION_INTENSITY, VISUAL_DENSITY
         - Follow the pre-flight checklist before delivery
Step 4: "nanobanana-prompt-library" + "nanobanana-image-generation" — Generate hero images
Step 5: "image-enhancer" — Upscale hero to 2K+ for retina displays
Step 6: "auditing-accessibility" — Final WCAG AA check before launch
```

### Workflow 5: For a Law Firm Website Specifically

Law firm websites need to balance authority with approachability. Recommended approach:

**Design Direction:**
- Use "design-master" with dials: DESIGN_VARIANCE=3, MOTION_INTENSITY=4, VISUAL_DENSITY=4
  - (Conservative layout, subtle motion, clean density — professional authority)
- Color: Deep navy or forest green primary + warm neutral grays. Avoid stark black.
- Typography: Serif for headlines (signals authority + tradition), sans-serif for body
- Photography: Real team photos > stock. If generating, use nanobanana with prompts like:
  ```
  Professional law office interior, warm lighting, mahogany desk,
  legal books on shelves, modern architecture, editorial photography,
  no text, wide aspect ratio
  ```

**Accessibility Priority (law firms face extra scrutiny):**
- Run "auditing-accessibility" as the FIRST step, not the last
- Law firm websites are frequent ADA lawsuit targets — WCAG AA is non-negotiable
- Ensure all PDFs linked from the site are also accessible

**Key Pages to Design:**
1. Homepage — hero with firm's value proposition, practice areas, trust signals
2. Practice area pages — structured content with clear CTAs for consultation
3. Attorney profiles — professional photos, credentials, approachable bios
4. Contact/consultation page — simple form, phone number prominent, map

---

## Setup Requirements

### For Image Generation (Nanobanana)

Nanobanana requires a Google Gemini API key:

1. Go to https://aistudio.google.com/apikey
2. Create a free API key (generous free tier)
3. Save it:
   ```bash
   echo 'GEMINI_API_KEY=your-key-here' > ~/.nanobanana.env
   ```
4. Install Python dependencies:
   ```bash
   pip install google-genai Pillow python-dotenv
   ```

### For Everything Else

No setup required — the design, critique, and implementation skills work purely through Claude's instructions. Just load the skill file and go.

---

## Quick Reference Card

| I want to... | Use this skill |
|--------------|---------------|
| Design a website from scratch | design-master + designing-ui-patterns |
| Create a color palette / type scale | building-design-systems |
| Get feedback on my design | critiquing-designs |
| Check accessibility compliance | auditing-accessibility |
| See what's trending in web design | researching-design-trends |
| Convert a design to React/Vue/HTML | translating-design-to-code |
| Set up Figma for dev handoff | specifying-figma-layouts |
| Write React components with best practices | frontend-patterns |
| Generate a hero image or product shot | nanobanana-image-generation + nanobanana-prompt-library |
| Upscale or sharpen an image | image-enhancer |
