---
name: video-to-website
description: Turn a video file (MP4, MOV) into a premium scroll-driven animated website with GSAP, canvas frame rendering, and layered animation choreography. Deploy to Vercel for client delivery.
---

# /video-to-website · Video to Premium Animated Website

Turns any video into a scroll-driven website with canvas frame rendering, GSAP animations, and smooth Lenis scroll. Use for product showcase sites, portfolio pieces, or premium client deliveries.

## Prerequisites

- FFmpeg installed (check: `ffmpeg -version`), if not installed: `choco install ffmpeg` or download from ffmpeg.org
- Node.js (already installed)
- Vercel CLI (already installed: `vercel`)

## Premium Checklist (Non-Negotiable)

1. Lenis smooth scroll (native scroll feels "web page", Lenis feels "experience")
2. 4+ animation types, never repeat the same entrance animation consecutively
3. Staggered reveals, label → heading → body → CTA, never all at once
4. No glassmorphism cards, text on clean backgrounds, hierarchy via font size/weight/color
5. Direction variety, sections enter from different directions (left, right, up, scale, clip)
6. Dark overlay for stats, 0.88, 0.92 opacity, counters animate up
7. Horizontal text marquee, at least one oversized element sliding on scroll (12vw+)
8. Counter animations, all numbers count up from 0, never appear statically
9. Massive typography, hero 12rem+, section headings 4rem+, marquee 10vw+
10. CTA persists, `data-persist="true"` keeps final section visible
11. Hero prominence + generous scroll, hero gets 20%+ scroll range, 800vh+ total for 6 sections
12. Side-aligned text ONLY, all text in outer 40% zones, never centered (exception: stats with full dark overlay)
13. Circle-wipe hero reveal, canvas reveals via `clip-path: circle()` as hero scrolls
14. Frame speed 1.8, 2.2, product animation completes by ~55% scroll

## Workflow

### Step 1 · Analyze the video

```bash
ffprobe -v error -select_streams v:0 -show_entries stream=width,height,duration,r_frame_rate,nb_frames -of csv=p=0 "<VIDEO_PATH>"
```

Decide:
- **Target frame count:** 150, 300 frames
  - Short video (<10s): original fps, cap at ~300
  - Medium (10, 30s): extract at 10, 15fps
  - Long (30s+): extract at 5, 10fps
- **Output resolution:** match aspect ratio, cap width at 1920px

### Step 2 · Extract frames

```bash
mkdir frames
ffmpeg -i "<VIDEO_PATH>" -vf "fps=<FPS>,scale=<WIDTH>:-1" -c:v libwebp -quality 80 "frames/frame_%04d.webp"
```

Count frames: `(Get-ChildItem frames).Count`

### Step 3 · Scaffold

```
project-root/
  index.html
  css/style.css
  js/app.js
  frames/frame_0001.webp ...
```

No bundler. Vanilla HTML/CSS/JS + CDN.

### Step 4 · Build index.html structure

```html
<!-- 1. Loader: #loader > .loader-brand, #loader-bar, #loader-percent -->
<!-- 2. Fixed header: .site-header > nav with logo + links -->
<!-- 3. Hero: .hero-standalone (100vh, solid bg) -->
<!-- 4. Canvas: .canvas-wrap > canvas#canvas (fixed, full viewport) -->
<!-- 5. Dark overlay: #dark-overlay (fixed, full viewport, pointer-events:none) -->
<!-- 6. Marquee(s): .marquee-wrap > .marquee-text (fixed, 12vw font) -->
<!-- 7. Scroll container: #scroll-container (800vh+) -->

<!-- CDN scripts (end of body): -->
<script src="https://cdn.jsdelivr.net/npm/lenis@1/dist/lenis.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/gsap@3/dist/gsap.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/gsap@3/dist/ScrollTrigger.min.js"></script>
<script src="js/app.js"></script>
```

Content section template:
```html
<section class="scroll-section section-content align-left"
         data-enter="22" data-leave="38" data-animation="slide-left">
  <div class="section-inner">
    <span class="section-label">002 / Feature</span>
    <h2 class="section-heading">Feature Headline</h2>
    <p class="section-body">Description text here.</p>
  </div>
</section>
```

### Step 5 · CSS key patterns

```css
:root {
  --bg-light: #f5f3f0;
  --bg-dark: #111111;
}
/* Side-aligned text zones */
.align-left  { padding-left: 5vw; padding-right: 55vw; }
.align-right { padding-left: 55vw; padding-right: 5vw; }
.align-left .section-inner,
.align-right .section-inner { max-width: 40vw; }
```

### Step 6 · JS core patterns

Lenis (mandatory):
```js
const lenis = new Lenis({ duration: 1.2, smoothWheel: true });
lenis.on("scroll", ScrollTrigger.update);
gsap.ticker.add((time) => lenis.raf(time * 1000));
```

Canvas padded cover mode:
```js
const IMAGE_SCALE = 0.85;
function drawFrame(index) {
  const img = frames[index];
  const scale = Math.max(canvas.width / img.naturalWidth, canvas.height / img.naturalHeight) * IMAGE_SCALE;
  const dw = img.naturalWidth * scale, dh = img.naturalHeight * scale;
  ctx.fillStyle = bgColor;
  ctx.fillRect(0, 0, canvas.width, canvas.height);
  ctx.drawImage(img, (canvas.width - dw) / 2, (canvas.height - dh) / 2, dw, dh);
}
```

Frame scroll binding:
```js
const FRAME_SPEED = 2.0;
ScrollTrigger.create({
  trigger: scrollContainer, start: "top top", end: "bottom bottom", scrub: true,
  onUpdate: (self) => {
    const index = Math.min(Math.floor(Math.min(self.progress * FRAME_SPEED, 1) * FRAME_COUNT), FRAME_COUNT - 1);
    if (index !== currentFrame) { currentFrame = index; requestAnimationFrame(() => drawFrame(currentFrame)); }
  }
});
```

### Step 7 · Test

1. `npx serve .` (or `python -m http.server 8000`)
2. Scroll through, verify each section has a DIFFERENT animation type
3. Confirm: smooth scroll, frame playback, staggered reveals, marquee, counters, dark overlay, CTA persists

### Step 8 · Deploy

```bash
vercel --prod
```

Client gets a live URL. Embed in portfolio or send directly.

## Animation Types

| Type | Effect |
|------|--------|
| `fade-up` | y:50 → 0, opacity 0→1 |
| `slide-left` | x:-80 → 0, opacity 0→1 |
| `slide-right` | x:80 → 0, opacity 0→1 |
| `scale-up` | scale 0.85→1, opacity 0→1 |
| `rotate-in` | y:40, rotation:3 → 0 |
| `stagger-up` | y:60 → 0, staggered |
| `clip-reveal` | clipPath inset 100%→0% |

## Money

- Price: €300, €2,500 per site
- Deliver via Vercel URL
- Add maintenance retainer: €100, 300/month
