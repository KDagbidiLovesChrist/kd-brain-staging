# REF · "Claude killed interior design" TikTok (@ai.honeycove) · King's interactive-3D reference

> **Why this file exists:** King sent this clip to the brain as the look he wants for the 7 Adderig
> walkthrough ("how interactive the 3d was"). Video files don't sync to the brain (`.gitignore` blocks
> `.mov`/`.mp4`), so the clip itself kept getting lost. This is the permanent text record. Source clip
> pulled from King's Gmail (sent 2026-06-20 09:25) → `7 adderig farm\references\_tiktok_refs\claude_interior_design_tiktok.mp4` (47s).

## What it is
A tutorial by **@ai.honeycove**: "Claude just killed [interior-design apps], redesign any room." Shows how
to redesign a room from a photo using **Claude + a "banana" skill + Google AI Studio (Gemini Nano Banana image model)**.

## The method it teaches (time-coded)
1. Google "banana skill claude" → open the GitHub result (`github.com/AgricDaniel/banana-claude`), copy the URL.
2. In Claude, paste the URL + `install this skill`.
3. Google "Google AI Studio" → `aistudio.google.com` → API keys → Create API key → copy it.
4. Back in Claude, paste the key + `set this up`.
5. Upload a room photo + `/banana redesign my room like a professional interior designer`.
   Variants shown: `/banana change the furniture`, `/banana change the colors`, `/banana change the layout`.

## 🔑 The key insight (what King calls "the interactive 3D")
The moving "redesign any room" shot is a **parallax / 2.5D animation applied to a STILL image**, a subtle
camera zoom + slight pan giving depth, plus gentle light glow. **It is NOT a real walk-around 3D model and
NOT a full flythrough.** It's a short, pre-rendered moving clip of one redesigned still.

## What this means for our build
- **The redesign engine is identical to ours:** Gemini Nano Banana on the real room photo
  (`tools\gemini_render.py --ref`). We're already doing this.
- **The only thing to add = the MOTION layer** on each redesigned still to get that "alive/3D" feel:
  - cheapest: a web parallax / Ken Burns (slow zoom + pan) in the page, or
  - truest match: image-to-video (Seedance via KIE / Kling / Runway) to add depth-aware camera motion.
- **Foundation rule still applies (King, 2026-06-20):** show **floor only** for now (pale-oak), no
  furniture. Furniture/full redesign is Phase 2.
- A genuine *walk-around explore* (what "explore" might also imply) is a separate, later piece = the
  Polycam phone scan once the floor's laid, or the build-from-plan 3D `house.html`.

## Related
- Engine + method: `walkthrough\README_empty_to_designed.md` · renders: `tools\gemini_render.py`.
- Real house footage King sent (use as reference): terrace-doors = the **living room**
  (`references\_tiktok_refs\terrace_doors_livingroom.mov`), plus downstairs-layout + doorway clips in Gmail
  (Google Drive links, 2026-06-20).
