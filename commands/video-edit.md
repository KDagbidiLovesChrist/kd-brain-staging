---
name: video-edit
description: Edit a video into a finished, on-style cut (Reels/TikTok/Shorts or 16:9 long-form). Picks an editing style by video type, renders via the Remotion style library, runs frame QA, delivers. The /video-edit gig engine (gig 10).
---

# /video-edit · Video Editing Style Library

**Triggers:** `/video-edit`, "edit this video", "make a reel from…", "client video edit", "cut this into a short".

**Purpose:** The reusable engine behind the **Video Editing gig (gig 10)**. Takes raw footage + a brief (the "script in → everything else done by us" model), auto-selects an **editing style**, renders a finished cut through the Remotion style library, runs a frame-by-frame QA, and delivers. Proof piece: King's portfolio ad (`video-samples.vercel.app`).

> **READ FIRST:** master `C:\Users\Dell\.claude\CLAUDE.md`. Style specs + job schema: `Documents\Website Builder\video-edit\STYLE_LIBRARY.md`. Channel/retention reference: `knowledge\faceless_youtube_playbook.md`.

---

## Honest ceiling (state it, don't oversell)
Code (Remotion + ffmpeg) tops at a strong **8** (sleek/minimal ~8.5). The gig sells exactly that tier, honestly deliverable. A true cinema-10 (hand-crafted After Effects motion graphics) needs a **human motion designer**, funded by client money later. **I cannot watch video play**, QA is always **still frames** + King watches the final once before it ships.

## The 4 styles (auto-pick from video type; client can override)
| Pick when… | Style |
|---|---|
| product / brand / website / showcase / "make it premium" | **CinematicReel** |
| person talking to camera / tips / voiceover-led | **TalkingHead** |
| gym / PT / product drop / hype promo / high energy | **HypeCut** |
| case study / founder story / finance-edu / faceless YouTube doc | **DocStory** |
| *unsure / default* | **CinematicReel** |

Each renders **9:16 (1080×1920)** or **16:9 (1920×1080)** via `width`/`height` props.

## Intake checklist (ask the client / King)
1. **The script** (or talking points), the core input.
2. **Footage**: files into `<job>/raw/`, OR "use stock B-roll" (Pexels, free), OR a website to capture (`tools\capture_portfolio.py` — LAPTOP-ONLY: lives outside the synced brain, in `Documents\Website Builder\video-edit\`).
3. Video type → style. Aspect (9:16 short / 16:9 long-form). Target length.
4. Brand: accent colour, logo, brand name, tagline, CTA.
5. Captions: provided text, or **auto from audio** (whisper).
6. Voice: client's own recording, **ElevenLabs** narrator, or music-only.
7. Music vibe (cleared tracks only). Tier ($89 short / $229 premium / custom for long-form doc).

## Smart auto-cut (optional pre-step · free, private, on-device)
The "remove the bad bits" pass, our owned alternative to upload-your-footage auto-edit plugins. Tightening
footage is one of the biggest quality levers. Tool: `Documents\Website Builder\video-edit\tools\smart_cut.py` (LAPTOP-ONLY: lives outside the synced brain)
(Whisper → Claude keep-list → ffmpeg).
1. **Transcribe** the raw clip: `python tools\smart_cut.py transcribe "<job>\raw\take1.mp4"` (LAPTOP-ONLY) → writes a
   timestamped `*.transcript.txt` (+ `.json`).
2. **Claude reads** the transcript and writes `<clip>.cuts.json` = `{"keep": [[start,end], ...]}` (seconds),
   dropping bad takes, repeats, filler, and long pauses.
3. **Apply:** `python tools\smart_cut.py apply "<job>\raw\take1.mp4" --cuts "<clip>.cuts.json" --out "<job>\raw\take1_tight.mp4" --pad 0.08` (LAPTOP-ONLY)
   → frame-accurate, A/V kept in sync. Feed the tight clip into the chosen style.
   - **Deterministic shortcut (no LLM):** `python tools\smart_cut.py autosilence "<clip>" --out "<tight>" --max-pause 0.6` (LAPTOP-ONLY)
     auto-trims pauses from the word-timings. Proven: 12.0s → 8.2s (smart) / 11.4s (autosilence).
Best for TalkingHead / podcast / vlog raw footage. **Client footage never leaves the machine.**

## How to run it
1. **Author the job**, create `Documents\Website Builder\video-edit\jobs\<id>\job.json` (style + width/height/fps + `props`). Put source media in `<id>\raw\` (bare filenames; the orchestrator stages them + prefixes paths). Reference shared brand assets as `kd/...`. See STYLE_LIBRARY.md for each style's prop shape.
2. **Run the orchestrator:**
   ```
   cd "C:\Users\Dell\Documents\Website Builder\video-edit\tools"
   python video_edit.py --job "..\jobs\<id>"
   ```
   - `--no-render` = stage + resolve props only (dry run). `--qa-only` = rebuild QA stills. `--steps stage,voice,captions,render,qa` = subset.
   - It stages assets → (optional) ElevenLabs VO from `job.json["voice"]` → (optional) whisper captions → writes `props.resolved.json` → `npx remotion render` → ffmpeg QA stills.
3. **QA**, open `<job>\qa\contact_sheet.png` + key frames. Check captions land, grade reads, no clipped text. Fix props/beats, re-render. Then **King watches the final once**.
4. **Deliver**, the `<id>.mp4`. Frame the portfolio entry like Mubashir: title + "client wanted X; we handled script→delivery."

## Editing technique checklist (research-backed, from `knowledge\video_studies`)
Run every cut through this checklist before calling it done. Pulled from the natecurtiss_tips technique tutorials + the ad-style breakdowns in `knowledge\video_studies\INDEX.md` (sections 7 and 9), not guesses. Full technique detail lives in those source files if a beat needs the exact numbers.

1. **Hook (first 2-3s):** open on the strongest visual or state the value immediately, no slow build-up. Put the most editing effort into the first 30 seconds, that is where retention is won or lost.
2. **Cut pace:** average 1-4 seconds per cut for most styles; under 1 second for HypeCut/high-energy SaaS-style promos; hold longer (3-5s) for CinematicReel's premium/cinematic beats. Reserve big transitions (wipes, morphs, zooms) for big moments only, use plain hard cuts everywhere else.
3. **B-roll ratio:** aim for roughly 3x as much B-roll as A-roll (talking head), or drop A-roll entirely if it would be boring on its own. Source from Pexels (free, commercial-cleared) or the client's own footage.
4. **Captions:** the pop-in keyframe recipe (center text, scale down and move to the bottom, keyframe from oversized to normal across ~5 frames) for punchy styles, or word-level karaoke sync from Whisper timestamps for TalkingHead/DocStory. Always caption the intro; use captions sparingly elsewhere so they support the visual instead of overtaking it.
5. **Sound design:** background music at -15 to -25dB under any voiceover; change the music at section changes, not randomly; add a whoosh/impact SFX for every meaningful visual beat. The research is blunt about this: sound design is the single biggest lever between a decent edit and a great one, never skip it.
6. **Motion and effects:** subtle push-ins on key reveals, motion tracking to pin an overlay (logo, price tag, caption) to a moving subject, scale a clip down to about 80 percent for emphasis or humor, Ken Burns (slow scale keyframe) on any static image or screenshot.
7. **Color grade:** correct exposure and white balance first if footage is rough, then keep one consistent grade across the whole cut so brand colors read true (Navy #0A1628, Gold #C9A84C, Off-White #F8F6F1, Forest Green #2D6A4F for King's own work; the client's brand colors for client work).
8. **Breathing room:** after a dense or loud beat, give one quieter, wider moment before the next push. Constant high-intensity bombardment fatigues viewers rather than exciting them.
9. **Outro:** keep it under 5 seconds, or cut it entirely. A long outro is where retention drops fastest, don't let a slow goodbye undo a strong edit.

## Faceless screen-record (AI-tools) recipe · from the 2026-07-10 TikTok study
For faceless AI-tools content (screen-record dominant, no face). Layer this on the chosen style (usually TalkingHead/DocStory props, drop the A-roll). Source: `knowledge\video_studies\2026-07-10_faceless_ai_tools_tiktok_refs.md`.
- **Show, don't tell:** screen-record every step; a bold text overlay LABELS each action ("Click here", "Paste this"). The overlay carries the tutorial in place of a face.
- **Key-word caption pop:** white bold captions with the key word HIGHLIGHTED (yellow/orange; red for a warning). Must read on mute.
- **Pace:** 1-2s cuts through the how-to steps (faster than talking-head, no face to hold the eye); motion/zoom between sparse hard cuts.
- **Music matched to the concept** (e.g. game music for a game analogy) beats generic upbeat.
- **Structure:** hook (3s, use a rubric hook type) → 2-3 labeled steps → payoff visual → keyword-comment CTA (see `/content-engine` MONETISE).

## CapCut finishing lane (optional · LAPTOP only)
After the Remotion render, a one-off cut can take a manual polish pass in **CapCut desktop (free)**: auto captions in King's white + **YELLOW pop** style (free up to ~10 min per video), text templates, quick tweaks. Watermark only appears if crown (Pro) assets are used, own footage exports clean at 1080p. CapCut has **no API** (manual laptop step, cannot run from cloud), so batch/programmatic gig work stays on the default whisper → Remotion caption path. Full routing rule: `/video` "CapCut finishing lane".

## Faith filter + hard rules
- **Only cleared music** (YouTube Audio Library / Uppbeat / Epidemic / client-supplied). Never ship unlicensed audio.
- **YouTube AI disclosure**: **disclose by default.** Tick "Altered or Synthetic Content" for any AI-generated/altered voice or visuals, **including a cloned voice (even the client's own)**. YouTube's 2026 policy has no clear own-voice-clone exception, and an undisclosed AI voice risks Partner Program eligibility. (Matches `/video` + `/content-engine`; confirm current YouTube policy.)
- No fabricated client results. Deliver the honest 8 we can actually hit; quote the human-editor upgrade for cinema-tier.

## Architecture (WAT)
- **W:** this SOP + `STYLE_LIBRARY.md`
- **A:** Claude (intake → authors the job.json beats → reviews QA)
- **T:** `video_edit.py` orchestrator · Remotion style library (`Built With AI\remotion\styles\*.jsx`) · ffmpeg · faster-whisper · ElevenLabs · Pexels
- **S:** `/video-edit`
- **Money:** gig 10, $89 short / $229 premium / custom long-form documentary.

> 🔊 **Cut-boundary rule (drift fix, 2026-07-04):** apply a ~30ms audio fade (afade/acrossfade) at every keep-segment join in smart-cut applies — seamless splices, no clicks.
