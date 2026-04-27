---
name: "lite-youtube-embed"
description: "Replace raw YouTube iframes with clickable screenshot cover images that lazy-load the player on click"
domain: "jekyll, frontend, performance"
confidence: "medium"
source: "earned — built for signal-archive week-8 post, verified working pattern"
---

## Context

When a Jekyll post embeds multiple YouTube videos via raw `<iframe>` tags, the page loads every iframe on first paint — slow, heavy, and unnecessary. This skill replaces each iframe with a screenshot cover image + play button overlay. Clicking loads a single iframe on demand.

Use this whenever a post has 2+ YouTube embeds, or when custom thumbnails (screenshots) are available for video moments.

## Patterns

### 1. Reusable Jekyll Include — `_includes/youtube.html`

Takes three parameters:
- `id` — YouTube video ID (e.g., `5739RGIMPyU`)
- `start` — start time in seconds (e.g., `1808`)
- `cover` — filename in `assets/screenshots/` (e.g., `charlie-week8-01-5739RGIMPyU-1812s.png`)

```html
<div class="yt-cover" onclick="this.innerHTML='<iframe width=\'560\' height=\'315\' src=\'https://www.youtube.com/embed/{{ include.id }}?start={{ include.start }}&autoplay=1\' title=\'YouTube video player\' frameborder=\'0\' allow=\'accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share\' referrerpolicy=\'strict-origin-when-cross-origin\' allowfullscreen></iframe>'">
  <img src="{{ '/assets/screenshots/' | append: include.cover | relative_url }}" alt="Video thumbnail" loading="lazy">
  <div class="yt-play-btn" aria-label="Play video">
    <svg viewBox="0 0 68 48" width="68" height="48">
      <path d="M66.52 7.74c-.78-2.93-2.49-5.41-5.42-6.19C55.79.13 34 0 34 0S12.21.13 6.9 1.55c-2.93.78-4.64 3.26-5.42 6.19C.06 13.05 0 24 0 24s.06 10.95 1.48 16.26c.78 2.93 2.49 5.41 5.42 6.19C12.21 47.87 34 48 34 48s21.79-.13 27.1-1.55c2.93-.78 4.64-3.26 5.42-6.19C67.94 34.95 68 24 68 24s-.06-10.95-1.48-16.26z" fill="#212121" fill-opacity="0.8"/>
      <path d="M45 24L27 14v20" fill="#fff"/>
    </svg>
  </div>
</div>
```

### 2. SCSS Styles — in `assets/main.scss`

```scss
.yt-cover {
  position: relative;
  cursor: pointer;
  max-width: 560px;
  margin: 1em 0;
  background: #000;
  border: 1px solid var(--border);

  img {
    display: block;
    width: 100%;
    height: auto;
    opacity: 0.85;
    transition: opacity 0.2s;
  }

  &:hover img { opacity: 1; }

  .yt-play-btn {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    opacity: 0.8;
    transition: opacity 0.2s;
  }

  &:hover .yt-play-btn { opacity: 1; }

  iframe {
    width: 560px;
    height: 315px;
    max-width: 100%;
  }
}
```

### 3. Usage in Posts

Replace raw iframes:

```markdown
<!-- BEFORE -->
<iframe width="560" height="315" src="https://www.youtube.com/embed/VIDEO_ID?start=SECONDS" ...></iframe>

<!-- AFTER -->
{% include youtube.html id="VIDEO_ID" start="SECONDS" cover="screenshot-filename.png" %}
```

### 4. Screenshot Naming Convention & Source

Screenshots live in `assets/screenshots/` with this naming pattern:
```
charlie-week{N}-{sequence}-{videoId}-{timestamp}s.png
```
Example: `charlie-week8-01-5739RGIMPyU-1812s.png`

The video ID and timestamp in the filename make it easy to match screenshots to embeds.

**Source method:** Screenshots are captured using Playwright with **video player element only** (excluding YouTube header, sidebar, chat, recommendations, comments, and page chrome). See `charlie-quote-verification` SKILL section "Playwright Screenshots (Video Element Only)" for the element-capture methodology with concrete selectors and code patterns. This ensures clean thumbnails showing only the video playback area with controls — perfect for blog embed covers.

## Examples

From `_posts/2026-04-17-week-8.md` — 11 embeds across 3 videos, each with a unique screenshot:

```liquid
{% include youtube.html id="5739RGIMPyU" start="1808" cover="charlie-week8-01-5739RGIMPyU-1812s.png" %}
{% include youtube.html id="cuj0Ny9KrVI" start="1244" cover="charlie-week8-03-cuj0Ny9KrVI-1248s.png" %}
{% include youtube.html id="FT0J4FPBy7M" start="2778" cover="charlie-week8-07-FT0J4FPBy7M-2782s.png" %}
```

## Anti-Patterns

- **Don't embed raw `<iframe>` tags** when a screenshot is available — it loads the full YouTube player immediately, wasting bandwidth
- **Don't use YouTube's default thumbnail URL** (`img.youtube.com/vi/ID/maxresdefault.jpg`) when you have a custom screenshot — the default shows the video start, not the specific moment
- **Don't forget `loading="lazy"`** on the cover image — it prevents offscreen images from loading until scrolled into view
- **Don't forget `autoplay=1`** in the iframe URL — users expect the video to play immediately after clicking the cover
