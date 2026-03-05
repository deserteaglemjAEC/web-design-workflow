---
name: design-master
description: Use when designing, building, or critiquing any visual interface — web frontends (React/Next.js/Tailwind/Framer Motion) OR HTML email (Klaviyo, campaign, newsletter, welcome sequence). Covers premium DTC/editorial aesthetics, bold creative direction, dial-based design variance, motion specs, email HTML constraints, AG1-style email patterns, Nano Banana image workflow, dark mode, CTA rules, and pre-flight checks. Replaces design-taste-frontend, email-design-premium, and frontend-dev-guidelines.
---

# Design Master

## MODE SELECTION

**At the start of every design task, identify the medium:**

| Mode | When | Stack |
|------|------|-------|
| **FRONTEND** | Web components, pages, apps | React/Next.js + Tailwind + Framer Motion |
| **EMAIL** | Campaigns, sequences, Klaviyo templates | HTML tables + inline CSS |

EMAIL and FRONTEND have incompatible constraints. Do NOT apply frontend patterns (flexbox, JS, hover states) to email. Do NOT apply email patterns (table layouts, inline styles) to frontend.

---

## PART 0 — AESTHETIC PHILOSOPHY (Both Modes)

Before writing a single line of code or HTML, commit to a bold aesthetic direction:

- **Purpose** — What problem does this solve? Who uses it?
- **Tone** — Pick a direction and own it: brutally minimal, luxury/refined, editorial/magazine, dark-tech, warm-DTC, maximalist, organic, brutalist, retro-futuristic. Half-committed aesthetics look like slop.
- **The Unforgettable Factor** — What is the ONE thing someone will remember?

**The Premium DTC Reference Stack:**

| Brand | Signature | Apply when |
|-------|-----------|------------|
| AG1 | Cream bg + serif headline + educational blocks | Wellness, supplements, nutrition |
| Eight Sleep | Dark `#0A0A0A` + ice blue + animated GIF | Tech, hardware, sleep |
| CRAFTD | Black bg + lifestyle model photo + red CTA | Menswear, jewelry, streetwear |
| Notion | Ultra-minimal, monochrome, type-led | SaaS, productivity |
| Kylie | Full brand palette, editorial product shots | Beauty, cosmetics |
| Big Day | Muted palette, 3D floating product, educational structure | Beverages, wellness |

---

## PART 1 — FRONTEND MODE

### 1A. Dial Configuration (Required at Session Start)

Display this to the user before generating any code:

```
Design Master loaded. Set your dials (Enter = defaults):

| Dial              | Default | Scale                                    |
|-------------------|---------|------------------------------------------|
| DESIGN_VARIANCE   | 5       | 1 = Perfect Symmetry → 10 = Artsy Chaos  |
| MOTION_INTENSITY  | 7       | 1 = Static → 10 = Cinematic Physics      |
| VISUAL_DENSITY    | 5       | 1 = Art Gallery → 10 = Cockpit Packed    |

Reply with values e.g. "6, 4, 7" — or "defaults" for (5, 7, 5).
```

Lock these values globally for the session. Do not re-ask.

**Dial Definitions:**

`DESIGN_VARIANCE`:
- 1–3: Flexbox `justify-center`, strict 12-col symmetry, equal paddings
- 4–7: Overlapping elements, varied aspect ratios, left-aligned over center-aligned
- 8–10: Masonry, fractional CSS Grid (`2fr 1fr 1fr`), massive empty zones (`padding-left: 20vw`)
- Mobile override: Any asymmetry above `md:` MUST collapse to strict single-column `w-full px-4`

`MOTION_INTENSITY`:
- 1–3: CSS `:hover` and `:active` only
- 4–7: `transition: all 0.3s cubic-bezier(0.16, 1, 0.3, 1)`, `animation-delay` cascades, `transform` + `opacity` only
- 8–10: Framer Motion scroll triggers, parallax. NEVER `window.addEventListener('scroll')`

`VISUAL_DENSITY`:
- 1–3: Huge section gaps, everything expensive and clean
- 4–7: Normal web app spacing
- 8–10: Tiny paddings, 1px lines instead of cards, `font-mono` for all numbers

### 1B. Architecture Constraints

**MANDATORY before any 3rd-party import:** Check `package.json`. If missing, output `npm install package-name` before code. Never assume a library exists.

- **Framework:** React or Next.js. Default to Server Components (RSC).
- **RSC Safety:** Global state = Client Components only. Wrap providers in `"use client"` component.
- **Interactivity Isolation:** Animated/interactive components MUST be isolated leaf components with `'use client'` at top.
- **Styling:** Tailwind CSS (v3/v4). Check version before writing config. v4: use `@tailwindcss/postcss`, NOT `tailwindcss` plugin.
- **Icons:** `@phosphor-icons/react` or `@radix-ui/react-icons` only. Standardize `strokeWidth` globally.
- **Viewport:** NEVER `h-screen`. ALWAYS `min-h-[100dvh]`.
- **Grid over Flex-Math:** NEVER `w-[calc(33%-1rem)]`. ALWAYS CSS Grid.

### 1C. Design Engineering Rules (Bias Correction)

**Typography:**
- Display: `text-4xl md:text-6xl tracking-tighter leading-none`
- Body: `text-base text-gray-600 leading-relaxed max-w-[65ch]`
- Font stack: `Geist`, `Satoshi`, `Cabinet Grotesk`, `Outfit` — Inter is BANNED
- Serif ONLY for editorial/creative contexts. NEVER on dashboards/SaaS.

**Color:**
- Max 1 accent. Saturation < 80%.
- AI Purple/neon gradients: BANNED. Use Zinc/Slate base + one sharp accent.
- Never `#000000` — use Zinc-950 or charcoal.
- One warm/cool gray system per project. Never mix.

**Layout:**
- Centered hero when `DESIGN_VARIANCE > 4`: BANNED. Use Split Screen, Left-Aligned, or Asymmetric.
- 3-column equal card rows: BANNED. Use Bento, Zig-Zag, or asymmetric grid.

**States (Mandatory — LLMs skip these):**
- Loading: Skeletal loaders matching layout sizes
- Empty: Composed empty states explaining how to populate
- Error: Clear inline error reporting
- Tactile: On `:active` use `-translate-y-[1px]` or `scale-[0.98]`

**Motion (when `MOTION_INTENSITY > 5`):**
- Magnetic hover: NEVER `useState`. EXCLUSIVELY `useMotionValue` + `useTransform`.
- Spring physics: `{ type: "spring", stiffness: 100, damping: 20 }`
- Staggered reveals: `staggerChildren` — parent + children MUST be same Client Component tree.
- Layout transitions: Always use Framer `layout` + `layoutId` props.
- Perpetual animations: Memoize with `React.memo`, isolated in microscopic Client Components.
- NEVER mix GSAP/ThreeJS with Framer Motion in same component tree.

**Performance:**
- Grain/noise: Fixed `pointer-events-none` pseudo-elements only. NEVER on scrolling containers.
- Animate ONLY `transform` and `opacity`. Never `top`, `left`, `width`, `height`.
- Z-index: Only for systemic layers (navbars, modals, overlays).

### 1D. Glassmorphism Standard
When glassmorphism needed: go beyond `backdrop-blur`. Add `border-white/10` inner border + `shadow-[inset_0_1px_0_rgba(255,255,255,0.1)]` for physical edge refraction.

### 1E. Bento Grid Architecture (When Building Feature Sections)
- Background: `#f9fafb`. Cards: `#ffffff` + `border-slate-200/50` 1px border.
- Corners: `rounded-[2.5rem]`. Shadow: `shadow-[0_20px_40px_-15px_rgba(0,0,0,0.05)]`.
- Labels below cards (gallery-style). Padding `p-8`–`p-10`.
- Every card needs a perpetual micro-animation: Pulse, Typewriter, Float, or Carousel.

### 1F. AI Tells — Hard Bans

**Visual:** No neon outer glows. No `#000000`. No oversaturated accents. No gradient text on large headers. No custom cursors.

**Typography:** No Inter. No oversized H1s without weight/color hierarchy. No serif on dashboards.

**Layout:** No 3-column equal card rows. No `h-screen`. No complex flex-math percentages.

**Content:** No "John Doe"/"Sarah Chan" names. No predictable numbers (`99.99%`, `50%`). No "Acme"/"Nexus"/"SmartFlow" brand names. No "Elevate"/"Seamless"/"Unleash"/"Next-Gen" copy.

**External:** No Unsplash URLs. Use `picsum.photos/seed/{string}/800/600`. Never use shadcn in default state — always customize radii, colors, shadows.

### 1G. Frontend Pre-Flight Check
- [ ] No deep prop-drilling without proper state management
- [ ] Mobile collapse guaranteed for high-variance designs
- [ ] Full-height sections use `min-h-[100dvh]`
- [ ] `useEffect` animations have cleanup functions
- [ ] Empty, loading, and error states provided
- [ ] CPU-heavy animations isolated in Client Components
- [ ] No emojis in code or markup (use Phosphor/Radix icons)

---

## PART 2 — EMAIL MODE

### 2A. The Structural Law — Inverted Pyramid

```
┌──────────────────────────────────┐  ← Hero (75% of effort)
│  Headline + Hero Image + CTA     │    Every recipient sees this.
├──────────────────────────────────┤
│  Why-before-the-buy education    │  ← 2–3 modular blocks max
├──────────────────────────────────┤
│  Social proof + trust signals    │
├──────────────────────────────────┤
│  Footer CTA + unsubscribe        │
└──────────────────────────────────┘
```

**Single column. Always.** 600px. Multi-column = 2018.

**Color Blocking Rule (Sunlo pattern):** Alternate background colors between sections — dark hero → light body → dark closing. This creates scroll rhythm and visual momentum.

**The Why Before The Buy:** Before every purchase CTA, include a 3-point educational section (ingredients/specs/benefits with icons). Teach → show → sell.

### 2B. The AG1 Formula

- **Background:** Cream `#FAF7F2` — never stark white, never colored.
- **Typography:** Serif headline (Georgia fallback) + sans-serif body (Helvetica/Arial). Serif = authority signal in 2025.
- **Photography:** Hands-on product interaction, lifestyle-editorial. Not isolated product shots.
- **Copy angle:** Frame the ritual, not the product. "Your morning" not "our greens."
- **CTA problem:** AG1 uses green on green = wallpaper. Don't repeat.

### 2C. CTA Rules (Most Violated Rule in Email)

- **MUST contrast** dominant palette — NEVER match brand color
- Shape: `border-radius: 6px` or pill (growing fast)
- Fill: solid, not outline
- Height: 47–50px minimum (Apple touch target = 44px)
- Width: full-width 540px OR centered 200–280px
- Copy: **First-person wins by 90%** — "Start my free trial" not "Start your free trial"
- Best verbs: Get, Shop, Start, Find, Join, Read, Book, View
- BANNED: "Click Here", "Buy Now"
- Max 14 characters in button text

### 2D. Typography

| Element | Size | Weight |
|---------|------|--------|
| Hero headline | 32–48px | Bold — render as image for brand fonts |
| Section headline | 20–24px | SemiBold |
| Body copy | 15–16px | Regular (min 13px mobile) |
| CTA text | 16px | Bold |
| Line height | 1.4–1.6x | — |
| Line length | 45–75 chars | `max-width: 40ch` on paragraphs |

### 2E. Technical Specs

```
Container:     600px (640px max)
Hero image:    Build at 1200px, display at 600px (2x retina)
Hero dims:     1200 × 400–600px
File size:     <100KB ideal, <200KB max
Format:        JPG for photos, PNG for transparency
Body padding:  20–30px sides
Section pad:   40–60px top/bottom
Total height:  800–1,200px ideal
Subject line:  30–65 characters
Preheader:     40–70 characters (complements subject, never repeats it)
```

### 2F. Dark Mode (Non-Optional — 35% of Opens)

```css
@media (prefers-color-scheme: dark) {
  body, .email-wrapper { background-color: #121212 !important; }
  .email-body { background-color: #1E1E1E !important; }
  h1, h2, h3, p { color: #E8E8E8 !important; }
  .secondary-text { color: #A0A0A0 !important; }
}
```

- Dark mode bg: `#121212` (NEVER `#000000` — eye strain)
- Never pure black text on white — use `#1A1A1A` or `#2D2D2D`
- Logo: always transparent PNG

### 2G. Bulletproof CTA Button (Outlook-safe)

```html
<table width="100%" cellpadding="0" cellspacing="0">
  <tr>
    <td align="center" style="padding: 24px 0;">
      <!--[if mso]>
      <v:roundrect xmlns:v="urn:schemas-microsoft-com:vml"
        href="URL" style="height:50px;v-text-anchor:middle;width:220px;"
        arcsize="12%" strokecolor="#2C5234" fillcolor="#2C5234">
        <w:anchorlock/>
        <center style="color:#ffffff;font-family:sans-serif;font-size:16px;font-weight:bold;">
          Start my free trial
        </center>
      </v:roundrect>
      <![endif]-->
      <!--[if !mso]><!-->
      <a href="URL" style="background-color:#2C5234;border-radius:6px;
        color:#ffffff;display:inline-block;font-family:Arial,sans-serif;
        font-size:16px;font-weight:bold;line-height:50px;text-align:center;
        text-decoration:none;width:220px;-webkit-text-size-adjust:none;">
        Start my free trial
      </a>
      <!--<![endif]-->
    </td>
  </tr>
</table>
```

### 2H. Image Generation Workflow (Nano Banana)

```
1. GENERATE  → /generate [prompt] inside Claude Code (~$0.04/image)
2. REMOVE BG → Photoroom (products) or remove.bg
3. ADD TEXT  → your design tool (Figma, Canva, etc.) — NEVER render text in AI prompt
4. OPTIMIZE  → squoosh.app → target <150KB
5. DEPLOY    → Klaviyo: upload 1200px, display 600px, always set alt text
```

**Universal hero prompt formula:**
```
[shot type] of [subject], [setting], [lighting], [mood],
[color palette], wide aspect ratio, no text,
email marketing hero image, commercial photography quality
```

Always append `no text` — AI text in emails is unreadable.

**Nano Banana commands:**
- `/generate [prompt]` — text to image
- `/edit [image] [instruction]` — swap backgrounds, modify
- `/pattern [prompt]` — seamless texture backgrounds
- `--count=4` — 4 variations at once
- `--styles="editorial, lifestyle, commercial"`

**Midjourney params:** `--ar 3:1 --style raw --s 50 --chaos 5 --v 7`

### 2I. Premium vs Generic

| Element | Generic | Premium |
|---------|---------|---------|
| Layout | Multi-column, cluttered | Single column, spacious |
| Headline | 18–20px | 32–48px, serif |
| Background | Pure white | Cream, off-white, or dark |
| Section breaks | Thin line | Full-width color block alternation |
| CTA color | Matches brand | Contrasts palette |
| CTA copy | "Buy Now" | "Start my free trial" |
| Photography | Stock | Original lifestyle/editorial |
| Education | None | 3-point "why it works" section |
| Trust signals | Footer text | Designed icon rows + press logos |
| Dark mode | Afterthought | Designed for |

### 2J. Email Pre-Send Checklist
- [ ] One email = one idea = one CTA
- [ ] Hero above fold contains headline + image + button
- [ ] CTA contrasts background
- [ ] CTA uses first-person copy
- [ ] Color blocking creates scroll rhythm (dark/light alternation)
- [ ] Educational "why before buy" section present
- [ ] Trust signals (press logos, review count, icon grid) designed as a section
- [ ] All images have alt text
- [ ] Preheader set and not repeating subject line
- [ ] Dark mode CSS included
- [ ] Logo is transparent PNG
- [ ] Total file size <200KB
- [ ] Unsubscribe link visible
- [ ] Tested: Gmail, Apple Mail, Outlook, mobile
- [ ] Subject line 30–65 chars
- [ ] Live HTML text (not baked into images)

---

## 2025–26 Trends (Both Modes)

- **Serif renaissance** — AG1, Nike, Oakley, Netflix all went serif. Authority signal.
- **Dark mode as primary** — Design dark first, 35% of email opens
- **Color blocking** — Alternating section backgrounds create rhythm without decorative elements
- **3D floating product shots** — Isolated product in space = luxury signal (email heroes + frontend)
- **Bold scale typography** — Headline IS the hero in type-dominant layouts
- **Comfort-driven palettes** — Pastels, rounded edges, warm photography vs digital fatigue
- **Educational structure** — Teach → show → sell beats promotional blasting every time
