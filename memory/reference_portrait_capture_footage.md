---
name: reference-portrait-capture-footage
description: "THE footage fix (2026-06-06): capture King's sites/gigs in PORTRAIT/mobile so they fill a 9:16 video, not cropped landscape. Plus interactive chatbot capture. Tools: capture_portrait.py + capture_chatbot.py."
metadata: 
  node_type: memory
  type: reference
  originSessionId: d48256c4-8574-4445-a2c4-514e15ac0f3d
---

# Portrait Footage Capture · the fix for vertical promos

## The problem (King caught it)
Site/gig footage for 9:16 videos was being captured **desktop/landscape (1920x1080)** then dropped into the tall composition with `objectFit: cover` → only a **thin centre strip** of a desktop page showed. Looked cropped and cheap. This was THE reason every promo "didn't look good," not the engines.

## The fix · capture in PORTRAIT/mobile
`Website Builder\video-edit\tools\capture_portrait.py`:
- Playwright headed Chromium (so WebGL/3D renders), **mobile context**: `viewport {540,960}`, `device_scale_factor=2`, `is_mobile=True`, `has_touch=True`, iPhone user-agent.
- `record_video_size {1080,1920}` → records at 1080x1920. The site renders its MOBILE layout (single column, fills vertical) and is captured crisp.
- Hold on hero (~2.4s) → smooth eased full-page scroll (~9s) → settle. webm → h264 mp4.
- Output overwrites `muba-promo\raw\<name>.mp4`. Then re-stage + re-render to use them.
- Result: sites FILL the 9:16 frame, look like "your site on a phone", credible + premium.

## Interactive chatbot capture
`tools\capture_chatbot.py`, same portrait context, but DEMONSTRATES the product: opens the Rivella assistant (`ai-assistant-demo-blond.vercel.app`), taps suggestion chips (buttons whose text contains "?") + types a question + Enter, with waits so the bot's replies render. Shows the chatbot ANSWERING live, far stronger than a scroll. Pattern reusable for any interactive demo (SaaS, forms).

## Reuse rule
For ALL future vertical (9:16) site/gig footage, capture PORTRAIT with these tools. For 16:9, capture landscape. Never crop a landscape capture into a tall frame again. See [[feedback-reference-driven-design]].
