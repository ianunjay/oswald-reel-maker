# Kinetic Reel Maker

A browser-based tool for creating animated kinetic typography videos for Instagram Reels, YouTube Shorts, and TikTok. No installs. No accounts. No backend. One HTML file.

**Output:** 1080×1350px WebM video (4:5 portrait ratio). Instagram, TikTok, and YouTube Shorts all accept WebM.

**Works on:** Chrome or Firefox on desktop. Safari is not supported for video export (preview still works).

---

## Getting Started

### Option A — Open locally

Download `index.html`. Double-click it to open in Chrome. That's it. No server needed.

### Option B — Host on GitHub Pages

1. Create a new **public** repository on GitHub (e.g. `kinetic-reel-maker`)
2. Upload `index.html` and rename it if you want, or keep the name
3. Go to Settings → Pages → Source: Deploy from branch → Branch: `main` → Folder: `/ (root)`
4. Your tool will be live at `https://yourusername.github.io/kinetic-reel-maker`

To update: edit the file and push. GitHub Pages redeploys in about 60 seconds.

---

## The Interface

The tool has three columns:

**Left — Slides + Global Settings**
Where you manage your slide list and set defaults that apply to all slides.

**Middle — Slide Editor**
Four tabs for editing the active slide: Content, Style, Position, Background.

**Right — Preview**
Live canvas preview. Clickable dots to jump between slides. Preview and Export buttons.

---

## Building Your Reel

### Step 1 — Add slides

The tool starts with one example slide. Use the **+ Add Slide** button to add more. A typical reel has 5–8 slides.

Each slide in the list shows a preview of its first title line and which animation preset it uses.

To reorder slides, select a slide and use the **↑ Up** and **↓ Down** buttons in the Content tab. To duplicate a slide, use **⧉ Duplicate**.

### Step 2 — Edit slide content

Click any slide in the list to select it. The editor in the middle updates to show that slide's content.

The **Content tab** has five fields:

- **Eyebrow** — small label that appears above the title. Usually a category or context word (e.g. "real story", "the career", "the money"). Keep it short.
- **Title** — the main text. Press Enter to add a new line. Titles work best in 1–3 lines of 2–5 words each. Write in ALL CAPS for maximum impact.
- **Subtitle** — one line of supporting text below the title. Use it to expand on the title's idea.
- **Body** — supporting copy. Press Enter to split into multiple lines. Each line animates in separately. 2–3 lines maximum.
- **CTA** — the call-to-action label at the bottom of the slide (e.g. "swipe to continue", "link in bio").

### Step 3 — Set global settings

In the **Global Settings** panel (bottom of the left column), configure defaults that apply to all slides:

**Theme** — four colour palettes:
- Cream — warm paper background with burnt orange accents
- Dark — black background with white text
- Purple — deep purple with violet accents
- Magenta — dark with pink accents

**Brand** — text that appears vertically along the right edge of every slide. Usually your handle or site name.

**Default preset** — the entry animation used for all slides unless overridden per slide (see Style tab).

**Title animation** — how the title enters the slide:
- Words — each word flies in separately, one after the next
- Lines — each line of the title enters in sequence
- Chars — characters appear one by one (typewriter effect)
- Block — the entire title enters as one unit

**Body animation** — how subtitle and body text enters:
- Fade — elements fade in one by one
- Slide — elements slide up from below
- Instant — elements appear immediately

**Hold duration** — how long each slide stays on screen before the next one begins (1.5s to 7s).

**Stagger delay** — the gap between each word, line, or character entering. Lower values (40–80ms) feel fast and punchy. Higher values (150–250ms) feel slow and cinematic.

**Title size** — the default font size for titles, in pixels at 1080px canvas width.

---

## Per-Slide Overrides (Style Tab)

The **Style tab** lets you override global defaults for the currently selected slide. This is how you make each slide feel distinct while keeping a consistent overall look.

**Entry preset** — overrides the global default for this slide only. Options:
- **Slam** — words scale up and crash into position with a hard easing. Best for high-impact moments.
- **Drift** — words float upward smoothly. Clean and editorial.
- **Bounce** — elastic spring entry. Playful and energetic.
- **Snap** — elements appear instantly with a blur flash. Very punchy, works well with a single word.
- **Rise** — words float upward with a soft ease. The most "kinetic typography" feeling of all the options.
- **Fade Stagger** — elements fade in gently one by one. Works for quieter, more informational slides.

**Title animation** — overrides the global title animation mode for this slide.

**Title color** — click the colour swatch to pick a custom colour for the title on this slide. Use this for emphasis slides (e.g. a gold title on a dark background for the salary reveal). Click **Reset** to go back to the theme default.

**Title size** — override the font size for this slide's title. Useful when a title is very short (make it bigger) or very long (make it smaller).

**Background color override** — replaces the theme's background colour for this slide only. Click **Reset** to go back to the theme default.

---

## Text Placement (Position Tab)

The **Position tab** lets you nudge text elements away from their default positions. Each element (eyebrow, title, body, CTA) has independent X and Y controls.

Values are in pixels at 1080px canvas width. Positive Y moves text down. Negative Y moves it up. Positive X moves right, negative X moves left.

Use the **+ and −** buttons to adjust in 20px steps, or type a value directly into the field. The preview canvas updates live as you adjust.

Click **Reset all** to return everything to default positions.

This is useful when:
- A long subtitle is overlapping the body text
- You want the CTA higher or lower than default
- You want the eyebrow flush with the left edge or pushed further in

---

## Background Images (Background Tab)

Each slide can have its own background image. The image is cover-fitted to the slide (no stretching) and a dark overlay is applied automatically to keep text readable.

Click the upload area or the dotted box to select an image file (JPG, PNG, or WebP). The image loads immediately and the preview updates.

**Overlay opacity** — controls how dark the overlay is. 0% means no overlay (image at full brightness, text may be hard to read). 42% is the default. 80–90% makes the image almost invisible, just a subtle texture.

To remove an image, click the **✕ Remove image** link below the thumbnail.

Background images are slide-specific and are not included when you export JSON (base64 image data is too large to be useful in a JSON snippet). Re-upload the image after importing JSON if needed.

---

## Previewing

Click **▶ Preview All** to watch the full animation play through all slides on the preview canvas.

Click **■ Stop** at any time to stop playback.

Click any **dot** in the preview panel to jump directly to that slide's static preview without playing the animation. This is the fastest way to check how a specific slide looks after making edits.

The slide counter (e.g. "3 / 7") updates as you navigate.

---

## Exporting the Video

Click **⬤ Record Video** to start recording. The tool will:

1. Play through the entire animation on a hidden 1080×1350 canvas
2. Record the canvas output in real time using the browser's MediaRecorder API
3. When the last slide finishes, automatically stop recording and download the file

The recording takes as long as the video itself. For 7 slides at 3 seconds each, expect about 25–30 seconds.

The file downloads as `[brand-name]-kinetic.webm`. You can upload this directly to Instagram, TikTok, or YouTube Shorts. If you need MP4 specifically (for other platforms), open the WebM in HandBrake and convert — it takes under a minute.

**During recording:** a red blinking indicator shows which slide is currently being recorded. Do not close the tab or navigate away while recording.

---

## Using the JSON Panel

The **Import / Export JSON** panel (collapsed by default, click the header to open) gives you a text box that syncs with the current state of all slides.

This is useful when you want to use AI to generate slide content and paste it directly in.

**Three buttons:**

- **↓ Apply** — parses the JSON in the box and loads everything into the UI. Replaces all current slides and global settings. If the JSON has an error, the box turns red and shows the specific problem.
- **⧉ Copy** — syncs the current UI state into the box and copies it to the clipboard. Paste this into an AI chat to continue editing.
- **↺ Sync** — refreshes the box to reflect the current UI state. Use this after making edits to the slides to see the updated JSON.

When the panel is open, the JSON box updates automatically as you edit slides.

### Generating content with AI

Use this prompt in any Claude chat (or other AI):

```
Generate a carousel post about [YOUR TOPIC].

Output ONLY a JSON block, no explanation. Use exactly this format:

{
  "theme": "cream",
  "brand": "Your Brand",
  "titleSize": 94,
  "staggerMs": 110,
  "textAnim": "words",
  "bodyAnim": "fade",
  "slides": [
    {
      "eyebrow": "short label",
      "title": "BIG TITLE\nSECOND LINE",
      "subtitle": "One line that expands the title",
      "body": "Supporting copy line 1.\nLine 2 here.",
      "cta": "swipe to continue"
    }
  ]
}

Rules:
- 5–8 slides total
- Title: use \n for line breaks, UPPERCASE, 1–3 lines, max 5 words per line
- Body: max 3 lines, use \n between lines
- theme options: cream / dark-minimal / dark-purple / dark-magenta
- First slide: big hook, create tension or curiosity
- Last slide: cta pointing to your link or account

Per-slide optional overrides:
- "anim": slam | drift | bounce | snap | rise | fade-stagger
- "textAnim": words | lines | chars | none
- "titleColor": "#hex"
- "titleSize": number
- "bg": "#hex"
```

Copy the JSON output, open the JSON panel in Kinetic Reel Maker, paste it in, and click **↓ Apply**.

---

## JSON Schema Reference

Full schema for the JSON format. All per-slide fields are optional except `title`.

```json
{
  "theme": "cream",
  "brand": "Career Roads",
  "titleSize": 94,
  "staggerMs": 110,
  "textAnim": "words",
  "bodyAnim": "fade",
  "slides": [
    {
      "eyebrow": "small label above title",
      "title": "MAIN TITLE\nSECOND LINE\nTHIRD LINE",
      "subtitle": "One line below the title",
      "body": "Body line one.\nBody line two.\nBody line three.",
      "cta": "swipe to continue",

      "anim": "slam",
      "textAnim": "words",
      "titleSize": 100,
      "titleColor": "#f0c040",
      "bg": "#0a0a0a",
      "bgOverlay": 0.42,
      "nudge": {
        "eyebrowX": 0, "eyebrowY": 0,
        "titleX": 0,   "titleY": 0,
        "bodyX": 0,    "bodyY": 0,
        "ctaX": 0,     "ctaY": 0
      }
    }
  ]
}
```

**Global fields:**

| Field | Type | Default | Description |
|-------|------|---------|-------------|
| `theme` | string | required | `cream`, `dark-minimal`, `dark-purple`, `dark-magenta` |
| `brand` | string | `""` | Vertical side label on every slide |
| `titleSize` | number | `94` | Font size in px at 1080w |
| `staggerMs` | number | `110` | Delay between word/line/char entries in ms |
| `textAnim` | string | `words` | `words`, `lines`, `chars`, `none` |
| `bodyAnim` | string | `fade` | `fade`, `slide`, `none` |

**Per-slide fields (all optional except `title`):**

| Field | Type | Description |
|-------|------|-------------|
| `eyebrow` | string | Small uppercase label above the title |
| `title` | string | Main text. Use `\n` for line breaks |
| `subtitle` | string | One line below the title |
| `body` | string | Supporting copy. Use `\n` for line breaks |
| `cta` | string | Bottom label |
| `anim` | string | Entry preset override for this slide |
| `textAnim` | string | Title animation mode override |
| `titleSize` | number | Font size override |
| `titleColor` | string | Hex colour override for title |
| `bg` | string | Hex colour override for background |
| `bgOverlay` | number | 0–0.9, opacity of dark overlay over bgImage |
| `nudge` | object | X/Y offsets in px for eyebrow, title, body, cta |

---

## Technical Notes

**Why WebM instead of MP4?** The export uses the browser's native `MediaRecorder` API with `canvas.captureStream()`. This approach requires no external libraries, no server, and no `SharedArrayBuffer` (which GitHub Pages cannot provide). Chrome outputs WebM/VP9. Instagram, TikTok, and YouTube Shorts all accept WebM. If you need MP4, convert with HandBrake (free).

**Why not FFmpeg.wasm?** FFmpeg.wasm requires `SharedArrayBuffer`, which in turn requires specific HTTP headers (`Cross-Origin-Opener-Policy` and `Cross-Origin-Embedder-Policy`) that GitHub Pages and most static hosts do not set. The MediaRecorder approach works on any static host with no configuration.

**Recording is real-time.** The video is recorded as the animation plays, not rendered in advance. A 20-second reel takes 20 seconds to export. This is expected behaviour.

**Background images are not saved in JSON.** Base64 image data can be hundreds of kilobytes and is not practical to include in a JSON snippet. Re-upload images after importing JSON.

**Safari is not supported for export.** Safari has limited `MediaRecorder` support and does not reliably support `canvas.captureStream()`. Preview works fine on Safari, but use Chrome or Firefox for recording.

---

## Troubleshooting

**Preview shows nothing / blank canvas**
Fonts are still loading. Wait 2–3 seconds after opening the page and try again. Check the debug console (click "Show debug console" at the bottom of the preview panel) — it will show whether fonts loaded successfully.

**Export button does nothing**
You are likely on Safari. Open the file in Chrome. The debug console will show "MediaRecorder ready" if the browser supports recording.

**Video downloads but won't play**
The file is WebM format. On Mac, open with VLC or Chrome (drag the file into a Chrome tab). QuickTime does not support WebM by default. On Windows, open with VLC or the Movies & TV app.

**Instagram says "unsupported format"**
Instagram accepts WebM but occasionally rejects it depending on codec. If this happens, convert the WebM to MP4 using HandBrake (free, available at handbrake.fr) and upload the MP4.

**JSON Apply shows an error**
The most common causes: missing `"theme"` field, `slides` is not an array, a slide is missing `"title"`. The error message tells you exactly which field is wrong.

**Text is overlapping or cut off**
Use the Position tab to nudge elements. If the title is very long, reduce the title size in the Style tab or use the global title size slider.

---

## File Structure

```
kinetic-reel-maker/
└── index.html    ← the entire tool, self-contained
```

Everything is in one file. No dependencies to install. No build step. Push to GitHub and it works.
