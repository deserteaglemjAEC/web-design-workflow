---
name: seo-web-design
description: SEO skill for web designers covering the modules most relevant to site creation and management — meta tags, schema markup, technical SEO, keyword research, content structure, and AI/GEO visibility. Use when building pages, optimizing existing sites, or preparing for launch.
---

# SEO for Web Designers

SEO is not a post-launch add-on — it's a design decision. Page structure, heading hierarchy, URL patterns, load speed, and schema markup are all established during design and development. Retrofitting SEO is 3x harder than building it in.

## When to Use This Skill

- Structuring a new website's pages and URLs
- Writing meta tags (title, description, OG) for pages
- Adding schema markup (JSON-LD) for rich search results
- Auditing an existing site's technical SEO
- Planning content strategy or keyword targeting
- Optimizing for AI search (Google AI Overviews, ChatGPT, Perplexity)

## Module 1: Meta Tags

**Title Tag Formula:** `Primary Keyword | Unique Benefit | Brand Name`
- Length: 50-60 characters (visible in SERPs without truncation)
- Front-load the primary keyword
- Include a number or power word when relevant
- Test: "Would I click this over the result above and below it?"

**Meta Description Formula:** `[Benefit statement]. [Social proof or specificity]. [CTA].`
- Length: 155-160 characters
- Include primary keyword (Google bolds it in SERP)
- Treat as ad copy — this is your pitch to searchers

**Open Graph (Social Sharing):**
- `og:title` — headline optimized for shares (can differ from SEO title)
- `og:description` — hook + value, 2-3 sentences
- `og:image` — 1200x630px, brand-consistent, text readable at small size

**Red Flags:**
- Generic titles ("Home | Brand Name") — rewrite immediately
- Missing or duplicate meta descriptions — write unique ones for every page
- Titles exceeding 60 chars — truncated in SERPs

## Module 2: Schema Markup (JSON-LD)

Structured data enables rich results in search — star ratings, FAQ accordions, product prices, and more.

**Schema Type Selection:**

| Content Type | Schema Type | Rich Result |
|-------------|------------|------------|
| FAQ page / FAQ section | FAQPage | Expanded FAQ accordion in SERP |
| How-to article | HowTo | Step-by-step card |
| Product page | Product | Price, ratings, availability |
| Blog post | Article | Author, date, image |
| Local business | LocalBusiness | Map, hours, ratings |
| Review | Review + AggregateRating | Star ratings |
| Service page | Service | Service details |
| Person/team page | Person | Knowledge panel info |

**Implementation:** Add JSON-LD in `<script type="application/ld+json">` in the page `<head>`. Never use microdata or RDFa — JSON-LD is Google's preferred format and doesn't touch your HTML structure.

**Validation:** Test every schema implementation at https://search.google.com/test/rich-results

## Module 3: Technical SEO Checklist

Run this before any site launch:

**Crawlability:**
- [ ] `robots.txt` allows crawling of all public pages
- [ ] XML sitemap generated and submitted to Google Search Console
- [ ] No orphan pages (every page reachable via internal links)
- [ ] Click depth: important pages within 3 clicks of homepage

**Performance (Core Web Vitals):**
- [ ] LCP (Largest Contentful Paint) < 2.5 seconds
- [ ] FID/INP (Interaction to Next Paint) < 200ms
- [ ] CLS (Cumulative Layout Shift) < 0.1
- [ ] Images optimized (WebP, lazy loading, explicit width/height)
- [ ] Critical CSS inlined, non-critical deferred

**URL Structure:**
- [ ] Clean URLs: `/practice-areas/family-law` not `/page?id=47`
- [ ] HTTPS enforced everywhere (no mixed content)
- [ ] Canonical tags on all pages (prevent duplicate content)
- [ ] 301 redirects for any changed URLs

**Mobile:**
- [ ] Mobile-responsive (Google uses mobile-first indexing)
- [ ] No horizontal scroll on mobile
- [ ] Touch targets at least 44x44px
- [ ] Text readable without zooming

**Accessibility = SEO:**
- [ ] Proper heading hierarchy (H1 > H2 > H3, one H1 per page)
- [ ] All images have descriptive alt text
- [ ] Links have descriptive anchor text (not "click here")
- [ ] Page language declared in `<html lang="en">`

## Module 4: Keyword Research (Simplified for Designers)

You don't need to be an SEO specialist to target the right keywords. Focus on:

**Page-Level Keyword Assignment:**
Every page should target ONE primary keyword and 3-5 secondary keywords.

| Page Type | Keyword Pattern |
|-----------|----------------|
| Homepage | `[brand/service] + [location]` |
| Service page | `[service] + [location]` or `[service] + [modifier]` |
| Blog post | `[question/topic] + [long-tail]` |
| About page | `[brand name]` + `[industry] [location]` |

**Keyword Placement Checklist:**
- [ ] Primary keyword in title tag (first 60 chars)
- [ ] Primary keyword in H1
- [ ] Primary keyword in first 100 words of body
- [ ] Primary keyword in at least one H2
- [ ] Secondary keywords in H2s/H3s naturally
- [ ] Primary keyword in URL slug

## Module 5: Internal Linking

Internal links distribute authority and help search engines understand site structure.

**Rules:**
- Every page links to at least 3 other pages on the site
- Hub pages (services, practice areas) receive the most internal links
- Anchor text should be descriptive — "family law services" not "click here"
- New pages get linked from 3+ existing pages within 48 hours of launch

**Red Flags:**
- Orphan pages (zero internal links) — fix immediately
- Important pages buried more than 3 clicks deep — restructure navigation
- Generic anchor text ("read more", "learn more") — rewrite with keywords

## Module 6: AI/GEO Visibility

Google AI Overviews, ChatGPT, and Perplexity are changing how people find websites. Optimize for AI visibility:

- **Answer-first content** — lead with the direct answer, then elaborate
- **FAQ sections** — direct question-answer pairs are heavily cited by AI
- **Entity signals** — consistent brand name, founder name, and expertise across all pages
- **Structured data** — schema markup helps AI systems understand your content
- **"Key Takeaways" boxes** — summary sections at top of articles get cited more often

**Test your AI visibility:** Ask ChatGPT or Perplexity "What is [Brand]?" — if the answer is wrong or missing, your entity signals need work.

## Pre-Launch SEO Checklist

Before going live:
- [ ] Every page has a unique title tag (50-60 chars)
- [ ] Every page has a unique meta description (155-160 chars)
- [ ] Every page has OG tags (title, description, image)
- [ ] Schema markup on relevant pages (LocalBusiness, FAQ, Product, etc.)
- [ ] XML sitemap generated
- [ ] Google Search Console verified
- [ ] robots.txt reviewed
- [ ] All images have alt text
- [ ] Heading hierarchy correct on every page
- [ ] Core Web Vitals passing (test at PageSpeed Insights)
- [ ] Internal linking complete (no orphan pages)
- [ ] 301 redirects set up for any old URLs
- [ ] HTTPS enforced
- [ ] Mobile responsive verified
