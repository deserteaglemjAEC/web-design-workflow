# The Web Design Workflow

A complete web design system for Claude — 11 skills organized into 4 phases that cover the full lifecycle of a website, from idea to post-launch management. Works entirely within Claude Code — no Figma or external design tools required. Use any tools you prefer alongside it.

## What Are Skills?

Skills are markdown instruction files that give Claude deep domain expertise. When loaded, Claude follows the skill's methodology instead of generating generic responses. Think of them as "expert modes" you can activate on demand.

## How to Install

### Option A: Claude Code (CLI)

```bash
git clone https://github.com/deserteaglemjAEC/web-design-workflow.git
cp -r web-design-workflow/skills/* ~/.claude/skills/
```

Each skill auto-activates when you describe a matching task. You can also invoke directly:
```
"Use the design-master skill to build this landing page"
"Run an accessibility audit on this site"
```

### Option B: Claude.ai (Web)

1. Go to claude.ai and create a new **Project**
2. Click "Add project knowledge"
3. Upload the `.md` files from `skills/` as project knowledge
4. Claude will reference them in every conversation within that project

**Recommended project setup:**
- Project 1: "Web Design" — Phase 1 + Phase 2 skills
- Project 2: "Security & Launch" — Phase 3 + Phase 4 skills
- Project 3: "Image Generation" — nanobanana + image-prompt-formulas

### Option C: Cursor / Windsurf / Other AI IDEs

Copy `.md` files into your project's rules directory:
- **Cursor**: `.cursor/rules/`
- **Windsurf**: `.windsurfrules/`

---

## The 4 Phases

### Phase 1: Website Idea Generation

*Research, plan, and establish design foundations before touching any code.*

| Skill | File | What It Does |
|-------|------|-------------|
| **Researching Design Trends** | `researching-design-trends.md` | Analyze current trends in your client's industry. Produces adopt/monitor/ignore recommendations with competitive landscape mapping. |
| **Building Design Systems** | `building-design-systems.md` | Establish color palettes, typography scales, spacing systems, and design tokens. The foundation every other decision builds on. |
| **Designing UI Patterns** | `designing-ui-patterns.md` | Design user flows, wireframes, screen layouts, and navigation patterns. Platform-specific guidance for web, iOS, and Android. |

**Phase 1 Workflow:**
```
1. Research trends in the client's industry        --> researching-design-trends
2. Establish brand foundations (color, type, space) --> building-design-systems
3. Design the 3 most critical screens in depth     --> designing-ui-patterns
4. Self-review before presenting to client         --> critiquing-designs
```

---

### Phase 2: Website Creation & Code

*Turn designs into production-ready code with professional imagery.*

| Skill | File | What It Does |
|-------|------|-------------|
| **Design Master** | `design-master.md` | The core design skill. Premium visual interface design for React/Next.js/Tailwind + HTML email. Dial-based variance control, motion specs, aesthetic philosophy, pre-flight checks. |
| **Translating Design to Code** | `translating-design-to-code.md` | Convert any design input (verbal description, screenshot, wireframe, mockup) to production code (React, Vue, Svelte, HTML/CSS). Component architecture, responsive implementation, accessibility semantics, and testing. |
| **Nanobanana Image Generation** | `nanobanana-image-generation.md` | Generate and edit images using Google Gemini API. Multiple aspect ratios, resolutions up to 4K, image editing and compositing. |
| **Image Prompt Formulas** | `image-prompt-formulas.md` | Proven prompt templates for hero images, product shots, team photos, textures, social graphics. Works with any AI image generator. |

**Phase 2 Workflow:**
```
1. Set design dials (variance, motion, density)    --> design-master
2. Build components and pages from any design input --> translating-design-to-code
3. Generate hero images and visual assets          --> nanobanana + image-prompt-formulas
4. Run the pre-flight checklist                    --> design-master (section 1G or 2J)
```

---

### Phase 3: Code Security

*Review code for vulnerabilities before deployment.*

| Skill | File | What It Does |
|-------|------|-------------|
| **Security Review** | `security-review.md` | OWASP Top 10 coverage — secrets management, input validation, SQL injection, XSS, CSRF, authentication, authorization, rate limiting, dependency security. Includes a pre-deployment checklist. |

**Phase 3 Workflow:**
```
1. Run the pre-deployment security checklist       --> security-review
2. Check: secrets, input validation, auth, headers
3. Run npm audit for dependency vulnerabilities
4. Verify HTTPS, CORS, CSP headers configured
5. Fix all critical/high issues before deploying
```

---

### Phase 4: Post-Launch Management

*Optimize, audit, and maintain the site after it's live.*

| Skill | File | What It Does |
|-------|------|-------------|
| **SEO for Web Designers** | `seo-web-design.md` | Meta tags, schema markup (JSON-LD), technical SEO audit, keyword targeting, internal linking, AI/GEO visibility, and a pre-launch SEO checklist. |
| **Auditing Accessibility** | `auditing-accessibility.md` | WCAG 2.2 AA compliance audits using the POUR framework. Severity-classified findings with specific remediation steps. |
| **Critiquing Designs** | `critiquing-designs.md` | Structured design critique using Nielsen's 10 heuristics. Actionable, prioritized feedback for iterating on live sites. |

**Phase 4 Workflow:**
```
1. Run accessibility audit (WCAG AA)               --> auditing-accessibility
2. Run SEO audit (meta tags, schema, performance)  --> seo-web-design
3. Fix critical accessibility and SEO issues
4. Set up ongoing monitoring:
   - Google Search Console for search performance
   - PageSpeed Insights for Core Web Vitals
   - Quarterly accessibility re-audits
5. Content refresh cycle (every 6-12 months)        --> seo-web-design (Module 5)
6. Design critique for UX improvements              --> critiquing-designs
```

---

## End-to-End: Complete Website Project

Here's the full workflow using all 4 phases:

```
PHASE 1: IDEA GENERATION
  [1] Research industry design trends
  [2] Build design system (color, type, spacing)
  [3] Design critical screens (home, primary task, contact)
  [4] Self-critique before client review

PHASE 2: CREATION & CODE
  [5] Set design dials + build pages in code
  [6] Generate hero images and visual assets
  [7] Run design pre-flight check

PHASE 3: SECURITY
  [8] Run security checklist (OWASP Top 10)
  [9] Fix all critical vulnerabilities
  [10] Verify HTTPS, headers, auth

PHASE 4: POST-LAUNCH
  [11] Run accessibility audit (WCAG AA)
  [12] Run SEO audit + add schema markup
  [13] Submit sitemap to Google Search Console
  [14] Set up quarterly re-audit schedule
```

---

## Setup Requirements

### For Image Generation (Nanobanana)

1. Get a free Google Gemini API key at https://aistudio.google.com/apikey
2. Save it:
   ```bash
   echo 'GEMINI_API_KEY=your-key-here' > ~/.nanobanana.env
   ```
3. Install Python dependencies:
   ```bash
   pip install google-genai Pillow python-dotenv
   ```

### For Everything Else

No setup required. The design, critique, security, SEO, and implementation skills work purely through Claude's instructions.

---

## Quick Reference

| I want to... | Phase | Skill |
|--------------|-------|-------|
| Research what's trending in web design | 1 | researching-design-trends |
| Create a color palette / type scale | 1 | building-design-systems |
| Design screens and user flows | 1 | designing-ui-patterns |
| Build a website with premium aesthetics | 2 | design-master |
| Convert any design to React/Vue/HTML | 2 | translating-design-to-code |
| Generate a hero image or product shot | 2 | nanobanana + image-prompt-formulas |
| Check code for security vulnerabilities | 3 | security-review |
| Audit accessibility (WCAG AA) | 4 | auditing-accessibility |
| Optimize SEO, meta tags, schema markup | 4 | seo-web-design |
| Get structured design feedback | 4 | critiquing-designs |

---

## Examples

See the `examples/` folder for industry-specific guides:
- **[Law Firm Website](examples/law-firm.md)** — Design direction, accessibility priority, key pages, and local SEO notes

---

## License

[MIT](LICENSE) — free to use, modify, and share.
