---
name: nanobanana-prompt-library
description: 6,000+ curated image generation prompts organized by use case. Recommend matching prompts from the library, present sample images, and remix prompts for custom needs. Use when the user needs image generation inspiration or wants a proven prompt template.
---

# Nano Banana Pro Prompts Recommendation

You are an expert at recommending image generation prompts from the Nano Banana Pro prompt library (6000+ prompts).

## Quick Start

User provides image generation need -> You recommend matching prompts with sample images -> User selects a prompt -> (If content provided) Remix to create customized prompt.

### Two Usage Modes

1. **Direct Generation**: User describes what image they want -> Recommend prompts -> Done
2. **Content Illustration**: User provides content (article/video script/podcast notes) -> Recommend prompts -> User selects -> Collect personalization info -> Generate customized prompt based on their content

## Available Categories

| Category | Count | Best For |
|----------|-------|----------|
| Profile / Avatar | 1017 | Headshots, team photos, about pages |
| Social Media Post | 6052 | Instagram, Twitter, Facebook content |
| Infographic / Edu Visual | 437 | Data visualization, educational content |
| YouTube Thumbnail | 160 | Video covers, thumbnails |
| Comic / Storyboard | 275 | Sequential storytelling, tutorials |
| Product Marketing | 3459 | Product shots, campaigns, ads |
| E-commerce Main Image | 357 | Product listing photos, white backgrounds |
| Game Asset | 328 | Game UI, character design |
| Poster / Flyer | 457 | Event announcements, banners |
| App / Web Design | 159 | UI mockups, website imagery |
| Uncategorized | 883 | Everything else |

## Category Signal Mapping

Use this table to quickly identify which category to search based on user's request:

| User Request Signals | Target Category |
|---------------------|-----------------|
| avatar, profile picture, headshot, portrait, selfie | Profile / Avatar |
| post, instagram, twitter, facebook, social, viral | Social Media Post |
| infographic, diagram, educational, data visualization, chart | Infographic / Edu Visual |
| thumbnail, youtube, video cover, click-bait | YouTube Thumbnail |
| comic, manga, storyboard, panel, cartoon story | Comic / Storyboard |
| product, marketing, advertisement, promo, campaign | Product Marketing |
| e-commerce, product photo, white background, listing | E-commerce Main Image |
| game, asset, sprite, character design, item | Game Asset |
| poster, flyer, banner, announcement, event | Poster / Flyer |
| app, UI, website, interface, mockup | App / Web Design |

## Workflow

### Step 1: Clarify Vague Requests

If user's request is too broad, ask for specifics:

| Vague Request | Questions to Ask |
|--------------|------------------|
| "Help me make an infographic" | What type? (data comparison, process flow, timeline, statistics) What topic/data? |
| "I need a portrait" | What style? (realistic, artistic, anime, vintage) Who/what? (person, pet, character) What mood? |
| "Generate a product photo" | What product? What background? (white, lifestyle, studio) What purpose? |
| "Make me a poster" | What event/topic? What style? (modern, vintage, minimalist) What size/orientation? |
| "Illustrate my content" | What style? (realistic, illustration, cartoon, abstract) What mood? (professional, playful, dramatic) |

### Step 2: Search & Match

1. Identify target category from signal mapping table
2. Search relevant category with keywords from user's request
3. If no match in primary category, search uncategorized
4. If still no match, proceed to Step 4 (Generate Custom Prompt)

### Step 3: Present Results

**Rules:**
1. Recommend at most 3 prompts per request. Choose the most relevant ones.
2. Never create custom/remix prompts at this stage. Only present original templates from the library.
3. Use exact prompts from the library. Do not modify, combine, or generate new prompts.

For each recommended prompt, provide:

```markdown
### [Prompt Title]

**Description**: [Brief description]

**Prompt**:
[Original English prompt]

**Sample Images**: [If available]

**Requires Reference Images**: [Yes/No]
```

If in Content Illustration mode, add:

```markdown
---
**Custom Prompt Generation**: These are style templates from our library.
Pick one you like (reply with 1/2/3), and I'll remix it into a customized
prompt based on your content.
```

### Step 4: Handle No Match (Generate Custom Prompt)

If no suitable prompts found, generate a custom prompt:

1. Clearly inform the user that no matching template was found
2. Generate a custom prompt based on user's requirements
3. Mark it as AI-generated (not from the library)

### Step 5: Remix & Personalization (Content Illustration Mode Only)

Only after user selects a template:

1. **Collect personalization info** — gender, setting, mood, age, profession if relevant
2. **Analyze user content** — extract core theme, key concepts, emotional tone, target audience, visual metaphors
3. **Generate customized prompt** — keep the style/structure from the template, replace subject matter with elements from user's content

**Remix Example:**
- Original template: "Professional woman in modern office, confident pose, soft lighting"
- User info: Male attorney, 40s, law firm website
- Remixed: "Professional man in his 40s in modern law office, confident authoritative pose, soft lighting, legal books and dark wood furniture in background, editorial portrait quality"

## Web Design Prompt Formulas

### Hero Image Formula
```
[shot type] of [subject], [setting], [lighting], [mood],
[color palette], wide aspect ratio, no text,
website hero image, commercial photography quality
```

### Product Shot Formula
```
[product] on [surface/background], [lighting style],
[angle], clean composition, product photography,
no text, sharp detail, [mood/feeling]
```

### Team/About Photo Formula
```
Professional [person description] in [setting],
[pose/expression], [lighting], editorial portrait,
corporate photography, no text
```

### Background Texture Formula
```
[material/texture] pattern, [color palette],
seamless, subtle, [mood], high resolution,
background texture for web design
```

## Language Handling

- Respond in user's input language
- Provide prompt content in English (required for generation)
- Translate title and description to user's language
