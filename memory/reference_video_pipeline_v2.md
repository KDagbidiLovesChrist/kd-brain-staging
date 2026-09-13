---
name: reference-video-pipeline-v2
description: "Cinematic reel pipeline + tools + the zoompan bug + HONEST quality ceilings (code~8, B-style~8.5, Bolt-tier=human studio). Built session 6, 2026-05-31."
metadata: 
  node_type: memory
  type: reference
  originSessionId: 521cb92c-4d87-4cc1-a59c-1b5a865990f8
---

# Cinematic Reel Pipeline v2 + Honest Ceilings (2026-05-31)

## HONEST QUALITY CEILINGS (read before promising anything on video)
- **Code (Remotion/ffmpeg) tops at a strong 8.** The **sleek B style (Apple/Linear: black space, slow smooth
  push-ins, refined minimal type, premium grade, calm narrator) = up to 8.5**, restraint plays to code's strengths.
- **Flashy/cinema-ad (the Bolt ad King loved) = NOT achievable in code.** That Bolt ad was made by **Superside with
  18 pro designers** (After Effects + 3D motion). True cinema = a **human studio/freelancer**, full stop.
- **I CANNOT perceive video playing** (I read still frames). That's the real ceiling, I can't fine-tune felt timing.
- **Path to a true 10:** a **freelance motion designer ($150, 500)** briefed with the script + footage + voice + a
  reference. Commission it with CLIENT money, not before earning. Ship the premium-8 + sell first.

## TOOLS I CAN vs CAN'T drive
- ✅ **Remotion** (code video, FREE for solo), what to use. ✅ **ffmpeg** (FREE).
- ✅ **ElevenLabs API**, Creator **$22/mo** = pro voice + commercial + 192kbps. $99 only adds volume (same quality).
- ✅ **Plainly/Nexrender (~$59/mo)**, renders REAL After Effects templates via API → ~9, but needs bought AE
  templates (~$20, 40) + only worth it at VOLUME. ✅ Shotstack/Creatomate (~$41, 49), slicker than ffmpeg, still ~8.
- ❌ **CapCut**, no API I can drive (tap-by-hand app). Don't pay for it expecting me to use it; it's for a human.
- ❌ AI footage generators (Runway/Pika/Kling), generate footage, not needed (we have real footage).

## CAPTURE: real moving portfolio footage (KEY WIN)
`Website Builder\tools\capture_portfolio.py`, **headed** Playwright (`headless=False`) renders the live WebGL 3D
(NOT black, headless gives black). Records each demo (~15s) scrolling/interacting → `reel\clips_raw\*.webm`.
**So King does NOT need to screen-record demos himself.**

## VOICE pipeline
- King records lines on Voice Memos → emails to kingagbidi@gmail.com → `tools\fetch_voice.py` / `fetch_line5.py`
  pull attachments via the Gmail API (token at `.claude\token.json`, gmail.readonly scope).
- `tools\transcribe_voice.py` (faster-whisper, base.en) transcribes each clip → map clips to script lines by CONTENT
  (filenames are unreliable, iPhone auto-names them "Paddocks Crescent N"). Catches missing/duplicate lines.
- **edge-tts is DEAD** (robotic AI slop). Use King's own voice (treated) or ElevenLabs.
- Cinematic VO chain (ffmpeg, in build_reel_v2/v3): `highpass=90, afftdn (denoise), EQ (warmth 130 / cut 320 /
  presence 4k / air 9k), acompressor, deesser, aecho (space), loudnorm`. Removes background noise + steadies shaky takes.

## ZOOMPAN BUG (cost hours · remember this)
Ken-Burns push-in on a still: use **single image input + `zoompan=...:d={frames}:fps=25`** then `-r 25`.
**DO NOT** use `-loop 1 -t {d} -i img -vf zoompan=...:d={frames}` → that MULTIPLIES (input frames × d) → clips balloon
to thousands of seconds + the render "hangs"/encodes garbage. Also: a killed ffmpeg leaves a corrupt mp4 (moov atom
not found), a resumable check must validate, not just check file exists.

## REMOTION reel
`Built With AI\remotion\UnforgettableReel.jsx` (registered in Root.jsx, 1080×1920, fps 30). Assets via
`staticFile("kd/...")` from publicDir `./assets` (set in `remotion.config.js`). Render:
`cd "Built With AI"; npx remotion render remotion/index.jsx UnforgettableReel out.mp4 --concurrency=2`.
Primitives to reuse (from VideoDocStyle.jsx): KineticText, CinematicGrade, push-in via interpolate, spring logo.
**B-rebuild TODO** (when ElevenLabs key arrives): more black/space, slower, refined minimal captions (not bold stamps),
deep calm narrator voice.

## CURRENT REEL
Shipped **8** at video-samples.vercel.app. Script: `Website Builder\reel\SCRIPT_v1.md` ("UNFORGETTABLE" storyboard).
Related: [[feedback-reference-driven-design]] · [[reference-notify-and-video-pipeline]] · [[project-video-editing-styles-skill]].
