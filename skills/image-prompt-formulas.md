---
name: image-prompt-formulas
description: Proven prompt formulas for AI image generation (Gemini, Midjourney, DALL-E). Covers hero images, product shots, team photos, background textures, social media graphics, and more. Use when generating imagery for websites, marketing, or social content.
---

# Image Prompt Formulas

Proven prompt templates for generating professional imagery with AI. These formulas work across Gemini (nanobanana), Midjourney, DALL-E, and other generators.

## Golden Rules

1. **Always append "no text"** — AI-generated text is unreliable and looks amateur
2. **Be specific about lighting** — it's the single biggest quality lever
3. **Include a style reference** — "editorial photography", "commercial product shot", "flat illustration"
4. **Specify what you DON'T want** — negative constraints improve output dramatically
5. **Generate at low res first** — test at 1K, then regenerate winners at 2K/4K

## Formula 1: Website Hero Image

```
[shot type] of [subject], [setting], [lighting], [mood],
[color palette], wide aspect ratio, no text,
website hero image, commercial photography quality
```

**Examples:**
```
Wide shot of modern co-working space, floor-to-ceiling windows,
warm golden hour lighting, productive calm mood, neutral earth tones,
wide aspect ratio, no text, website hero image, commercial photography quality
```

```
Aerial view of vineyard landscape at sunset, rolling hills,
warm directional lighting, serene and premium mood, green and gold palette,
wide aspect ratio, no text, website hero image, editorial photography
```

**Size:** `--size 1344x768` (16:9) or `--size 1248x832` (3:2)

## Formula 2: Product Shot

```
[product] on [surface/background], [lighting style],
[angle], clean composition, product photography,
no text, sharp detail, [mood/feeling]
```

**Examples:**
```
Premium leather briefcase on marble surface, soft studio lighting,
45-degree angle, clean composition, product photography,
no text, sharp detail, luxury and sophistication
```

**Size:** `--size 1024x1024` (1:1) or `--size 896x1152` (4:5)

## Formula 3: Team / About Page Portrait

```
Professional [person description] in [setting],
[pose/expression], [lighting], editorial portrait,
corporate photography, no text, shallow depth of field
```

**Examples:**
```
Professional woman in her 30s in modern office, confident relaxed pose,
soft window lighting, editorial portrait, corporate photography,
no text, shallow depth of field, warm neutral tones
```

**Size:** `--size 896x1152` (4:5) or `--size 864x1184` (3:4)

## Formula 4: Background / Texture

```
[material/texture] pattern, [color palette],
seamless, subtle, [mood], high resolution,
background texture for web design
```

**Examples:**
```
Subtle concrete texture with fine grain, light gray and white tones,
seamless, minimal, modern industrial mood, high resolution,
background texture for web design
```

**Size:** `--size 1024x1024` (1:1 — tile-friendly)

## Formula 5: Social Media / Blog

```
[composition style] depicting [concept/metaphor],
[art style], [color palette], [mood],
social media graphic, no text, [aspect ratio hint]
```

**Size:** `--size 1024x1024` (1:1 feed) or `--size 768x1344` (9:16 stories)

## Formula 6: Icon / Logo Concept

```
Minimal [style] icon of [subject], [color] on [background],
clean lines, geometric, scalable design, centered composition,
graphic design, no text, flat
```

**Size:** `--size 1024x1024` (always square for icons)

## Formula 7: E-commerce / Lifestyle

```
[product] in [lifestyle context], [person/activity],
[natural lighting], authentic candid feel, lifestyle photography,
no text, [mood], [color warmth]
```

## Post-Generation Workflow

```
1. GENERATE  -> nanobanana or your preferred AI tool
2. REVIEW    -> pick best of 3-4 variations
3. REMOVE BG -> Photoroom (products) or remove.bg (if needed)
4. ADD TEXT  -> your design tool (Figma, Canva, etc.) — NEVER in the AI prompt
5. ENHANCE   -> upscale to 2K/4K for production (nanobanana --resolution 2K)
6. OPTIMIZE  -> squoosh.app -> target <150KB for web
7. DEPLOY    -> set alt text on every image
```

## Size Quick Reference

| Use Case | Size | Aspect Ratio |
|----------|------|-------------|
| Website hero | `1344x768` | 16:9 |
| Blog header | `1248x832` | 3:2 |
| Product shot | `1024x1024` | 1:1 |
| Portrait | `896x1152` | 4:5 |
| Social story | `768x1344` | 9:16 |
| Social feed | `1024x1024` | 1:1 |
| Ultra-wide banner | `1536x672` | 21:9 |
| Icon/logo | `1024x1024` | 1:1 |
