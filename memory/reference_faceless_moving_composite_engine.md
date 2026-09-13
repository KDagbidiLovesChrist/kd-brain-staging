---
name: reference-faceless-moving-composite-engine
description: "The proven FREE-ish engine for faceless short-form videos where EVERYTHING moves (King's hard rule, no still slideshows). Image-to-video brings the character ALIVE while keeping identity; ffmpeg composites a floating phone + word-by-word white/yellow captions + red-circle draw + 3D hand pointer over an animated navy bg. Built + reference-QA'd against faceless.inc.proj 2026-06-28."
metadata:
  node_type: memory
  type: reference
  originSessionId: 377b479b-4ca1-4b54-a7d6-e4d24f3654c3
---

# Faceless MOVING-composite engine (everything moves, nothing static)

King's rule (2026-06-28): faceless short-form videos must have **NO still images, everything moving**,
and must be **REFERENCE-QA'd** to match the channels we model (see [[reference-reference-qa-standard]]).
This is the engine that delivers that. Proven on Video #1 test for @30Kingdavid (the Faceless Hook Engine).

## What the reference actually does (decoded from faceless.inc.proj recent video, frame by frame)
"Everything moving" is NOT rapid hard cuts. The recent 28s video had only **5 hard cuts**. The energy is
**continuous in-frame animation**, all layers moving at once:
1. A **living character** anchor at the bottom (animated/lip-syncs the whole time).
2. A **real moving phone screen** up top (real footage + app UI + an **animating number**, e.g. follower
   count ticking, then a **red circle drawn** on it).
3. Big bold **white + yellow-highlight captions**, revealed **word by word**.
4. A **3D hand pointer** that slides in + a **red circle** drawn on the key number (their signature gag).
Our earlier failure was an **AI-photo slideshow + slow Ken-Burns + 2.2 wps voice**. That is the gap.
It was a METHOD problem, not a money problem.

## The engine (mostly free; ~$0.50 total per test)
### 1. Character ALIVE = image-to-video (keeps identity, the key unlock)
- Host the character PNG to **catbox.moe**, then `tools\gen_router.py` / `muapi_generate.py video` with
  slug **`seedance-pro-i2v`** (MuAPI, ~**$0.36** for 8s 720p, cheapest i2v; balance check via /money).
- Prompt = "**subtle idle motion only, keep this EXACT character identical** (list every feature: blank
  faceless face with NO eyes/nose/mouth, brown skin, braids, navy hoodie, gold headphones, cross, gold
  halo), gentle breathing + soft head bob + braids/hood sway + halo glow pulse, **camera locked, do NOT
  change the design, do NOT add a face**, premium 3D, smooth loop, dark navy bg."
- WHY this beats free in-engine bob: Seedance uses the still as the **first frame**, so **identity is
  locked** (no AI-redraw drift, the usual faceless-character risk) AND the motion is organic. Verified it
  kept King's blank face perfectly. This **supersedes** the earlier "animate the PNG in-engine" idea for
  the character itself.

### 2. Overlay layers = chrome-headless-shell HTML -> transparent PNG
- Phone screen, caption frames (white text + key word on a `#FFD21E` yellow box, Arial Black for the test
  / **Montserrat ExtraBold for final**), all rendered with `--default-background-color=00000000`.
- 3D hand pointer = generate via kie nano-banana on a **flat solid magenta bg** (the AI ignores "#00FF00"
  and gives a gradient, so green-key fails). Key it in PIL: `mag=(r>120)&(g<150)&(b>120)&((r-g)>40)&
  ((b-g)>40)`, MinFilter/MaxFilter despeckle, autocrop bbox.
- Red ring = a CSS rounded border ellipse rendered transparent.

### 3. Composite = ONE ffmpeg filter_complex
- **CRITICAL: loop every still input** `-loop 1 -framerate 30 -t DUR` BEFORE `-i`. `fade`/`enable` on a
  single-frame still leaves alpha stuck at 0 (the bug that made all captions + the ring invisible).
- Background: animated `gradients` lavfi, **navy-only** (`c0=0x0b1426:c1=0x05080f:nb_colors=2`). Gold in
  the gradient exposes the character's square. Keep it dark navy to blend.
- **Feather the character** so its square seam disappears: a horizontal+top feather **gray mask**
  (PIL: L/R fade 12%, top fade 14%, bottom solid) + `[chs][mask]alphamerge`. Bottom stays solid (it runs
  off-frame).
- Composition (matches the reference): **phone hero upper**, **caption band just below it**, **character
  head peeking at the very bottom** (scale ~720, anchor low so only head+halo+headphones show).
- Motion everywhere: phone + character gentle `sin(t)` float/bob; captions fade+pop per word; ring
  `fade in` on the number beat then `fade out` after; hand slides up via `clip((t-t0)/d,0,1)`.
- Lock the ring + hand onto the **floating** number (add the phone's float term to their y), or they drift
  off it.

### 4. Voice (placeholder for tests, edit to the reference pace)
- `edge-tts en-IE-ConnorNeural --rate=+22%` then `silenceremove` + presence-EQ + compress + loudnorm.
- Target the reference **words-per-second** (faceless.inc.proj = 3.71; ours hit **3.79**). Edit it tight,
  not raw TTS. Real DJI-mic voice or a clone goes on the final.

## REFERENCE-QA result (the bar = "not unlike theirs")
Ours passed every dimension vs faceless.inc.proj: 3.79 vs 3.71 wps, continuous in-frame motion (0 hard
cuts), living character, white+yellow word captions, hand + red-circle annotation, hook in first 2s,
everything moving. **One deliberate difference:** their character has a moving mouth; King's stays
**blank-faced** (his brand identity from his old pic) but fully alive. Flag this for King to confirm; a
literal mouth changes his character's face.

## Files (this build)
`scratchpad\moving_test\`: `build_layers.py` (phone+caps), `assemble2.py` (the composite), `char_anim.mp4`
(i2v alive character), `hand_crop.png`, `MOVING_TEST.mp4`. Base character = #5 Pixar 3D from the char8 grid.

## Related
[[reference-reference-qa-standard]] · [[reference-faceless-inc-edit-style]] · [[project-content-engine]] ·
[[reference-muapi-cost-router]] · [[reference-visual-production-pipeline]] · [[feedback-qa-before-handover]]
