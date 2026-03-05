# Example: Restaurant Website

Restaurant websites live or die on three things: the menu is easy to find, the photos make you hungry, and you can book a table in under 30 seconds.

## Step 1: Research (Phase 1)

```
"Research current web design trends for restaurants and food service.
What should we adopt, monitor, or ignore?"
```

## Step 2: Design System (Phase 1)

```
"Create a design system for a modern Italian restaurant called Nonna's Table.
Warm, inviting aesthetic. Earthy tones with one rich accent color.
Include color palette, typography, and spacing."
```

### Design Direction Notes

- **Dials**: DESIGN_VARIANCE=5, MOTION_INTENSITY=6, VISUAL_DENSITY=4
  - Moderate asymmetry, smooth scroll animations, clean but inviting
- **Color**: Warm earth tones (terracotta, olive, cream) + one rich accent (wine red or burnt orange)
- **Typography**: Serif or display font for the restaurant name, clean sans-serif for menu items
- **Photography**: Food photos are everything. Generate with nanobanana:
  ```
  Close-up of fresh handmade pasta on rustic wooden table,
  warm directional lighting, shallow depth of field,
  steam rising, editorial food photography, no text
  ```

## Step 3: Build the Site (Phase 2)

```
"Use design-master to build a restaurant website for Nonna's Table.
DESIGN_VARIANCE=5, MOTION_INTENSITY=6, VISUAL_DENSITY=4

Build these pages:
1. Homepage with full-screen hero image, hours, and reservation CTA
2. Menu page with categories (appetizers, mains, desserts, drinks)
3. About page with the restaurant story and team
4. Contact page with reservation form, map, and hours"
```

### Key Pages

1. **Homepage** — full-bleed hero photo, hours + location visible without scrolling, prominent "Reserve a Table" CTA
2. **Menu** — categorized, easy to scan, no PDF-only menus (bad for SEO and accessibility)
3. **About** — the story, the chef, the team. Warmth and personality.
4. **Reservations/Contact** — simple form, phone number prominent, embedded map

## Step 4: Generate Food Photography (Phase 2)

```
"Generate 4 hero images for an Italian restaurant:
1. Fresh pasta close-up with steam, warm lighting
2. Restaurant interior, candlelit tables, evening ambiance
3. Chef preparing food in open kitchen, action shot
4. Dessert plating, overhead shot, marble surface

Use wide aspect ratio for hero images, square for menu items."
```

## Step 5: SEO Setup (Phase 4)

```
"Add SEO to all pages. This is a restaurant in Brooklyn, NY.
Add Restaurant schema markup with menu, hours, and location.
Add FAQ schema for common questions (parking, dress code, allergies)."
```

- Restaurant schema markup (hours, menu, cuisine type, price range)
- "Italian restaurant [neighborhood]" keyword targeting
- Google Business Profile with photos, menu, and hours

## Step 6: Accessibility + Security (Phases 3 & 4)

```
"Run accessibility and security audits on my restaurant site.
The reservation form collects personal data."
```

## You're Done When

- [ ] Menu is HTML text (not a PDF image)
- [ ] Reservation CTA visible on every page
- [ ] Food photos optimized (WebP, lazy loading, alt text)
- [ ] Restaurant schema markup with hours and menu
- [ ] Mobile responsive (most restaurant searches are mobile)
- [ ] Page load under 2.5 seconds despite image-heavy design
- [ ] Reservation form validates input and confirms submission
