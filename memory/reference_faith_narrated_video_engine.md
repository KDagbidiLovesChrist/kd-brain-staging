---
name: reference-faith-narrated-video-engine
description: "How to make King's faith lessons as narrated storybook videos (The Truth), storybook illustration + REAL icons + George VO + ffmpeg 9:16"
metadata: 
  node_type: memory
  type: reference
  originSessionId: f8b7712e-bc02-4bbf-a134-2be9a39062bd
---

# Faith narrated-video engine (The Truth)

King wants his `/faith` lessons as **narrated animations** (he learns by sight + sound + story).
Built 2026-06-26. Lives in `the-truth\video\` (see its `README.md`).

**The format King chose (locked):**
- **Storybook watercolour illustrations** for places/atmosphere (Gemini via `tools\gemini_image.py`).
- **Real public-domain traditional icons** for the holy persons/events (download from Wikimedia Commons
  Special:FilePath; verify by viewing). **NEVER AI-fake a holy figure or icon**, AI only paints places,
  never Christ's/a saint's face. This is the sacred line I told King; honour it.
- **Warm male narrator** = ElevenLabs "George" voice id `JBFqnCBsd6RMkjVDRZzb` (via `tools\elevenlabs_tts.py`).
- 9:16 vertical, navy/gold, Georgia serif captions, gentle Ken-Burns on illus, still gold-framed icon panels.

**Engine = ffmpeg, per-scene** (same pattern as `tools\build_guide2.py`): for each scene → TTS (cached by
md5 of the line) → ffprobe duration → render a 1080x1920 segment (Ken-Burns illus / navy icon panel / title
card + wrapped caption + fades) → concat. Scene kinds: `illus`, `icon`, `title`(chapter cards).
Scripts: `build_video.py` (short ~2 min), `build_full_video.py` (full chaptered film).

**Delivery:** email if < ~20 MB; else compress (`-crf 28 -movflags +faststart`) and **host on Vercel**
(static page + film.mp4) → tap-to-watch link, always also copy master to Desktop. Brain media is gitignored,
so it does NOT auto-sync to phone, deliver by email/link.

**Done 2026-06-26:** short Matthew 3 sample (emailed) + full film "everything so far + Matthew 3" (9.5 min,
32 scenes) hosted at https://site-nine-tau-34.vercel.app. King reacting; if he blesses it, wire into `/faith`.
Cost ≈ a few cents/lesson (voice + images); render is free. See [[project-the-truth-faith]].

## v2 · "TAKE 2", the animated film (2026-06-26, King's feedback)
Engine: `the-truth\video\matthew-03\build_v2.py` (full film) + `build_anim_sample.py` (taste).
King's notes drove it: add captions, "something always happening between the scripts", felt incomplete,
"i want everything animated", inspired by the **Bible Animations** YouTube channel (NOT copied).
- **Synced captions** = real word timings from a new tool `tools\elevenlabs_tts_timed.py` (ElevenLabs
  `/with-timestamps` endpoint → mp3 + `.words.json`); cues revealed phrase-by-phrase via `drawtext enable=between`.
  Lifted to y≈1452 clear of the phone play-bar; outline+shadow, NO hard box.
- **⚠️ Windows `\r\n` caption bug:** write drawtext textfiles with `open(...,newline="")` or the stray `\r`
  adds a blank line (huge gap between caption lines). Fixed via `wtext()`.
- **Living icons:** pre-compose navy + soft GOLD halo via `vignette` (NOT geq, geq gave a magenta colour bug),
  icon high so captions sit below in clear navy; then same camera move + drifting `fx_motes.png` (screen blend)
  so the formerly-dead icon scenes breathe. Holy image never warped.
- **Moving story elements** (the "Bible animation" feel) = silhouette/luminous sprites over our watercolours:
  `fx_caravan.png` (Magi, colorkey WHITE→transparent, travels the desert) + `fx_dove.png` (colorkey BLACK,
  descends). DON'T add a flat sprite that duplicates painted art (a flat star clashed with bg_star's painted one).
- **Cross-dissolves** (`xfade`) + **varied camera** + **vignette** + **drifting motes** on every scene.
- **Music** = a generated reverent ison-style drone (sine D3+A3+D4 + faint A4, tremolo+aecho+lowpass), ducked.
- **⚠️ AUDIO BUG King caught:** only the FIRST voice played. Cause = reusing the `[voice]` filter label twice
  (sidechain key + final mix) silently drops every voice after the first. **Fix = `asplit` → [vkey][vmix].**
  ALWAYS verify each voice window with `volumedetect` before delivering.
- Bible-Animations style takeaways (from Gemini watch): their motion is mostly **parallax/2.5D camera over
  layered flat art** + faceless figures + thematic colour + highlighted key words. We adapt the technique,
  keep watercolour + REAL ICONS for holy figures (our sacred line). Next depth upgrade = layer scenes for parallax.
- Full film = 36 scenes incl. extension (Divine Liturgy Pt2/Pt3 + a **Pascha** crescendo on the Anastasis icon).
- **⚠️ Vercel delivery gotcha → see [[reference-vercel-link-protection]].** Lesson SOP enrichment (Key Quotes /
  consensus / questions / prayer-to-repeat sections + in the visuals) discussed with King, pending build.

## ⭐ DECISION (2026-06-26): KEEP the still-icon style; defer real animation
King's clear ruling after a long iteration: **keep the beautiful still-icon film** (watercolour + real icons +
camera + synced captions + sources + music). Real "people doing stuff" animation is **deferred**, revisit
**AI video later for educational/social content** (where it can pay for itself). The cheap/free middle paths were
both tried and rejected by King:
- **Slid silhouette cut-outs** (caravan/dove over stills) → King: *"nothing changed, you just added the black silhouette."* A pasted PNG that translates is NOT animation.
- **Free hand-rigged GSAP figures** (proven pipeline below) → real articulated movement (John's arm raises via
  `gsap svgOrigin`), but King judged the silhouette figures **too simple/basic** ("closer to the stickmen"). So free hand-animation is possible but its quality ceiling isn't worth it for this film.
- **The free browser-capture pipeline WORKS and is reusable:** `_scene_proof.html` (HTML+GSAP, paused master
  timeline + `window.seekTo(t)`) → `capture.py` (Playwright Chromium, seek-per-frame screenshots 1080x1920,
  needs `playwright` + chromium) → ffmpeg frames → composite VO/captions/music. Good for future motion-graphics.
- **Honesty lesson (King's no-overselling rule):** I called slid cut-outs "acting it out", that oversold it.
  Don't claim animation for translate/scale/fade of a static image.

## ⏭️ NEXT (when King wants it, free): enrich the FULL still-icon film with the WHY + all 4 sources on screen
The **pilot** (`build_pilot.py`, the Baptism / John-at-the-Jordan) proved the enriched-teaching style in the
still-icon look: on-screen **source callouts** (gold, top) + the **why** + **verified** quotes from all four, **Bible** (Matthew 3 refs), **Jesus' words** (Matt 3:15), a **Church Father** (St Gregory the Theologian, Oration
39, verified at newadvent), the **Church** (Troparion of Theophany, verified at OCA). King's standing rule: every
teaching includes the WHY + sources (Bible/Father/Jesus/Church), **spoken AND shown**, every quote verified. The
job left = fold that across the full `build_v2.py` film. Tighter, ear-catching scripts (present tense, hooks).
