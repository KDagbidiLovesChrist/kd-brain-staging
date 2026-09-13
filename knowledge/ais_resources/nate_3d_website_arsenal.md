# Nate Herk 3D-Website Arsenal · consolidated (2026-06-04)

Built from Nate's AIS "Video Database" + Gemini watches of his current website videos. This is the
reference every Seedance build/upgrade agent reads. Source studies: `knowledge\video_studies\*WORKFLOW*`
(TcFeSjwTo7g, NvxiSG34mPU, ovabeVoWrA0, gAoZ95kqG7w, q0TgUtj6vIs). Links DB: `nate_video_database_LINKS.md`.

## Verdict: we are already on his exact current method
AI cinematic VIDEO scrubbed frame-by-frame on scroll (Nano Banana image → Seedance 2.0 video → ffmpeg
frames → sticky-canvas scrub + GSAP/Lenis → Vercel). The gains are a handful of free upgrades + the
depth/interactivity layer + (optional, paid) Claude Design as a design surface.

## 🟢 ADOPT NOW (free · apply in the rollout + bake into seedance-site skill/template)
1. **Seamless loop = SAME still as FIRST *and* LAST frame** in Seedance (we only set first). Update
   `tools\kie_generate.py` to accept/last-frame; loop has no jump. (Confirmed in ovabeVoWrA0.)
2. **Hero bg colour MUST equal the video's bg colour**, so the hero video blends into the page, never
   sits in a visible box. Hard rule in Step 4.
3. **`seedance-loop-prompt` SKILL (installed: `.claude\skills\seedance-loop-prompt\`)**, write every
   hero/section video prompt through its 7 sections (Scene · Camera · Action Arc · Text Choreography ·
   Lighting · Loop Seal · Technical). Static lighting + particle-reset + same first/last frame = perfect
   loop. Use it for the hub "King at a laptop" hero.
4. **Brand-spec-first prompt chain** (do in free Claude *chat*, not paid): brainstorm brand → get a single
   brand-spec md (product/mission/voice + hex palette + primary/secondary fonts) → that doc drives the
   image prompt + video prompt + the site copy. Add to Step 0.
5. **Section-by-section motion (depth)**, below-the-fold sections can each get their own small KIE clip /
   motion accent (not just the hero). This is the "engaging/professional" lift King asked for.
6. **Scrub feel defaults**, animation completes ~50% scroll, easing `power4.inOut` (and `power3.out` for
   reveals). Confirm in the template so motion is cinematic, not mechanical.
7. **Depth/Interactivity layer (the VEYRA reference, live on veyra-b.vercel.app)**, parallax (foreground
   ≠ background scroll speed), staggered reveals (fade+rise+scale), 3D mouse-tilt cards + glow, count-up
   stats, featured glow/sheen. Self-contained CSS+JS block, ports to all 10. SOURCE OF TRUTH = the two
   commented blocks at the bottom of `proofs\veyra-b\index.html`.
8. **Named design references beat adjectives**, "Linear 2023 with higher density" not "make it clean."
9. **motionsites.ai (free tier)**, gallery of animated-layout prompts; copy a layout's prompt for
   inspiration, then inject our brand. Use at Step 0 for layout ideas (no account needed for free browse).

## 📱 MOBILE OPTIMISATION (hard checklist · required on every site)
Nate's warning: the tools do NOT auto-optimise mobile; you must do it explicitly. Each per-site agent +
the template MUST verify on a 390×844 phone viewport:
- Loader reveals on first frame + 3.5s timeout (already baked), never hangs.
- Parallax reduced/off <768px; mouse-tilt OFF on touch; `prefers-reduced-motion` respected (already in ref).
- Hero text sizes down + stays readable over the video (scrim holds); hero video crops to the subject.
- Sections stack cleanly, no horizontal scroll, tap targets ≥44px, nav collapses.

## 🟢 ADOPT · for the VIDEO work (King's new "3D-sites music video")
**Hyperframes** (by HeyGen, FREE .md skill), teaches Claude to build proper animated launch/promo videos
(motion graphics, phone mockups, transitions) → export HTML → render MP4. This is the engine for the new
3D-sites music video + can refresh the hub ad. Download the .md skill and install alongside seedance-loop-prompt.

## 🔴 PAID · King's decision (lean-spend; default = NOT now)
- **Claude Design** (claude.ai/design, $20/mo, included if on Claude Pro), Nate's primary *design surface*:
  upload brand PDF/logo → full brand system (palette/type/components) → generate sections → "hand off to
  Claude Code". Faster section design + draw-to-edit, BUT separate weekly quota, research-preview rough
  edges (font substitution bug), doesn't auto-fix mobile. **Recommendation: stay on our free code engine;
  revisit when client money is in.** If adopted: brainstorm in free chat, Opus for first build / Sonnet for
  tweaks, one change per prompt, use the Tweaks panel (0 tokens) not prompts.
- **motionsites.ai $99 lifetime**, only if doing volume. Free browse is enough for now.
- **Glydo**, voice-to-text (King is voice-first); evaluate later.

## ⏭️ SKIP / OUTDATED
- Mar 3 "Nano Banana 2 + Kling" method, predecessor; Seedance 2.0 replaces Kling. Nothing net-new.
- `seedance-2-fast` as the default, use standard Seedance 2.0 with first+last frame for loop quality.

## ⚠️ RETEST
- **`google/nano-banana-2` on KIE**, our note says it 422'd; Nate uses "Nano Banana 2". Retest; if live,
  make it the default image model for sharper stills.
