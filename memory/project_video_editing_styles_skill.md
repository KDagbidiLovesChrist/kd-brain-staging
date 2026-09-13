---
name: project-video-editing-styles-skill
description: "BUILT (2026-06-01), /video-edit Video Editing Style Library: 4 prop-driven Remotion styles (CinematicReel, HypeCut, TalkingHead, DocStory) picked by video type. Engine proven end-to-end."
metadata: 
  node_type: memory
  type: project
  originSessionId: 521cb92c-4d87-4cc1-a59c-1b5a865990f8
---

# /video-edit · Video Editing Style Library [BUILT 2026-06-01]

The **Video Editing Style skill** King wanted is **built and proven end-to-end** (gig 10). Earlier drift
("planned, not built") was wrong, the skill, SOP, orchestrator, and the CinematicReel style already existed,
and on 2026-06-01 the remaining **3 styles were built + test-rendered**. All 4 styles now work.

## The 4 styles (auto-pick by video type; client can override)
- **CinematicReel** (9:16), premium product/brand/showcase. The shipped portfolio reel. `styles/CinematicReel.jsx`.
- **HypeCut** (9:16), fast beat-synced hard cuts + bold gold stamp captions; gym/PT/product-drop. `styles/HypeCut.jsx`.
- **TalkingHead** (9:16), full-bleed to-camera + WORD-BY-WORD captions auto-synced via whisper; creators/PTs/tips. `styles/TalkingHead.jsx`.
- **DocStory** (16:9), black+gold faceless-YouTube documentary: ghost chapter #s, highlighter captions, count-up stats + draw-on graphs; long-form. `styles/DocStory.jsx`.

## How it runs (WAT)
- **W:** `Documents\Website Builder\video-edit\STYLE_LIBRARY.md` (style specs + prop schemas) + the `/video-edit` SOP (`commands\video-edit.md`).
- **A:** Claude, intake → pick style → author `jobs/<id>/job.json` beats/scenes → review QA stills.
- **T:** `Documents\Website Builder\video-edit\tools\video_edit.py` (stage → ElevenLabs voice → whisper captions → render → QA) + Remotion styles in `Documents\Built With AI\remotion\styles\*.jsx` (registered in `remotion\Root.jsx`) + ffmpeg.
- **S:** `/video-edit`. **Money:** gig 10, $89 short / $229 premium / custom long-form.

## Key build facts (2026-06-01)
- Engine is **aspect-aware**: orchestrator passes `width`/`height` into props; each style's `calculateMetadata` returns them (DocStory renders true 16:9).
- **Captions → props:** `captions.auto` → faster-whisper word-timings injected inline as `props.captionWords` ({w,start,end} in seconds); TalkingHead consumes it.
- **publicDir BUG FIXED:** per-job media must stage to `Built With AI\assets\jobs\<id>\` (the real Remotion publicDir from `setPublicDir("./assets")`), NOT `remotion\assets\jobs\`. Was causing 404s for any job with its own footage.
- Test jobs (also serve as templates): `jobs\test-hype`, `jobs\test-docstory`, `jobs\test-talkinghead`, `jobs\test-smartcut`.
- **SMART AUTO-CUT added (2026-06-01):** `video-edit\tools\smart_cut.py`, the FREE/PRIVATE/owned answer to "upload-your-footage" auto-edit plugins King saw advertised. WAT: Whisper transcribes raw clip → Claude reads `*.transcript.txt` + writes `<clip>.cuts.json` ({"keep":[[s,e]…]}) → ffmpeg `apply` (filter_complex trim/atrim+concat, frame-accurate, A/V in sync). Also `autosilence` (deterministic pause-trim, no LLM). Proven: 12.0s→8.2s (smart) / 11.4s (autosilence). Client footage never leaves the machine. Pre-step for TalkingHead/podcast/vlog. Why: tighter pacing = a top quality lever; own the automation, don't rent a plugin.
- **Honest ceiling unchanged** [[reference-video-pipeline-v2]]: code tops at a strong 8 (sleek ~8.5); cinema-10 = a human motion designer funded by client money. Default standard = cinematic/top-tier [[feedback-top-tier-design-standard]].

## NEXT
Gig 10 is now sellable to ANY video type. To sell: publish the Video Editing Fiverr gig (#10, reel = proof at
video-samples.vercel.app) + offer talking-head/hype/doc edits in outreach. On a real client job, drop their
footage in `jobs/<id>/raw/`, author the job.json, render, QA, deliver.
