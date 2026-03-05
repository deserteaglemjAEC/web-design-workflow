---
name: nanobanana-image-generation
description: Generate or edit images using Google Gemini API through the nanobanana tool. Supports multiple aspect ratios, resolutions up to 4K, and image editing/compositing.
---

# Nanobanana Image Generation Skill

Generate or edit images using Google Gemini API through the nanobanana tool.

## Requirements

1. **GEMINI_API_KEY**: Must be configured in `~/.nanobanana.env` or `export GEMINI_API_KEY=<your-api-key>`
2. **Python3 with dependent packages**: google-genai, Pillow, python-dotenv
   ```bash
   pip install google-genai Pillow python-dotenv
   ```
3. **nanobanana.py script**: Install via the Claude Code plugin system (`claude plugin add nanobanana-skill`) or copy the script manually from the plugin's repository. Ensure the script is in your PATH or reference it by full path.

## Instructions

### For image generation

1. Ask the user for:
   - What they want to create (the prompt)
   - Desired aspect ratio/size (optional, defaults to 9:16 portrait)
   - Output filename (optional, auto-generates UUID if not specified)
   - Model preference (optional, defaults to gemini-3-pro-image-preview)
   - Resolution (optional, defaults to 1K)

2. Run the nanobanana script with appropriate parameters:

   ```bash
   python3 nanobanana.py --prompt "description of image" --output "filename.png"
   ```

3. Show the user the saved image path when complete

### For image editing

1. Ask the user for:
   - Input image file(s) to edit
   - What changes they want (the prompt)
   - Output filename (optional)

2. Run with input images:

   ```bash
   python3 nanobanana.py --prompt "editing instructions" --input image1.png image2.png --output "edited.png"
   ```

## Available Options

### Aspect Ratios (--size)

- `1024x1024` (1:1) - Square
- `832x1248` (2:3) - Portrait
- `1248x832` (3:2) - Landscape
- `864x1184` (3:4) - Portrait
- `1184x864` (4:3) - Landscape
- `896x1152` (4:5) - Portrait
- `1152x896` (5:4) - Landscape
- `768x1344` (9:16) - Portrait (default)
- `1344x768` (16:9) - Landscape
- `1536x672` (21:9) - Ultra-wide

### Models (--model)

- `gemini-3-pro-image-preview` (default) - Higher quality
- `gemini-2.5-flash-image` - Faster generation

### Resolution (--resolution)

- `1K` (default)
- `2K`
- `4K`

## Examples

### Generate a simple image

```bash
python3 nanobanana.py --prompt "A serene mountain landscape at sunset with a lake"
```

### Generate with specific size and output

```bash
python3 nanobanana.py \
  --prompt "Modern minimalist logo for a tech startup" \
  --size 1024x1024 \
  --output "logo.png"
```

### Generate landscape image with high resolution

```bash
python3 nanobanana.py \
  --prompt "Futuristic cityscape with flying cars" \
  --size 1344x768 \
  --resolution 2K \
  --output "cityscape.png"
```

### Edit existing images

```bash
python3 nanobanana.py \
  --prompt "Add a rainbow in the sky" \
  --input photo.png \
  --output "photo-with-rainbow.png"
```

### Use faster model

```bash
python3 nanobanana.py \
  --prompt "Quick sketch of a cat" \
  --model gemini-2.5-flash-image \
  --output "cat-sketch.png"
```

## Web Design Use Cases

### Hero Images
```bash
python3 nanobanana.py \
  --prompt "Professional law office interior, warm lighting, mahogany desk, legal books, modern architecture, editorial photography, no text" \
  --size 1344x768 \
  --resolution 2K \
  --output "hero-law-office.png"
```

### Background Textures
```bash
python3 nanobanana.py \
  --prompt "Subtle marble texture, cream and gray tones, seamless pattern, luxury material" \
  --size 1024x1024 \
  --output "bg-marble.png"
```

### Team/About Section
```bash
python3 nanobanana.py \
  --prompt "Modern professional headshot background, soft gradient, neutral tones, studio lighting, no person" \
  --size 896x1152 \
  --output "headshot-bg.png"
```

## Universal Hero Prompt Formula

```
[shot type] of [subject], [setting], [lighting], [mood],
[color palette], wide aspect ratio, no text,
website hero image, commercial photography quality
```

Always append `no text` — AI-generated text is unreliable and looks unprofessional.

## Best Practices

1. Be descriptive in prompts — include style, mood, colors, composition
2. For logos/graphics, use square aspect ratio (1024x1024)
3. For website heroes, use 16:9 (1344x768) or 3:2 (1248x832)
4. For social media stories, use 9:16 (768x1344)
5. Start with 1K resolution for testing, upgrade to 2K/4K for final output
6. Use gemini-3-pro-image-preview for best quality, gemini-2.5-flash-image for speed
7. After generation, use Photoroom or remove.bg for background removal on product shots
8. Add text overlays in your design tool (Figma, Canva, etc.) — never in the AI prompt

## Error Handling

If the script fails:

- Check that `GEMINI_API_KEY` is exported or set in ~/.nanobanana.env
- Verify input image files exist and are readable
- Ensure the output directory is writable
- If no image is generated, try making the prompt more specific about wanting an image
