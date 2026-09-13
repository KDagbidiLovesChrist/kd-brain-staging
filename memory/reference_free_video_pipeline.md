---
name: reference-free-video-pipeline
description: Working free voice/music/B-roll stack for Remotion proofs, edge-tts + ffmpeg + Pexels API. Music sources that failed tonight and which to try next.
metadata: 
  node_type: memory
  type: reference
  originSessionId: 8a918888-62f1-45e7-b6da-0e50caf372bc
---

# Free Video Pipeline Stack (Validated 2026-05-26 Night)

For producing dramatic-docu YouTube proof renders without paid subscriptions, this stack is working end-to-end as of 2026-05-26:

## Voice · edge-tts (Microsoft Neural)
- **Install:** `pip install edge-tts` (~5 sec, no API key, no signup)
- **CLI:** `edge-tts --voice=en-US-BrianMultilingualNeural --rate=-15% --pitch=-3Hz --text "..." --write-media out.mp3`
- **Critical syntax note:** Use `=` form (`--rate=-15%`) not space form (`--rate "-15%"`), argparse treats `-15%` as a flag otherwise.
- **Best voices for dramatic narrator:**
  - `en-US-BrianMultilingualNeural`, "Approachable, Casual, Sincere", chosen for proof v2
  - `en-US-AndrewMultilingualNeural`, "Warm, Confident, Authentic, Honest"
  - `en-US-ChristopherNeural`, "News, Novel, Reliable, Authority"
  - `en-US-GuyNeural`, "News, Novel, Passion"
  - `en-GB-RyanNeural`, British male, Irish-adjacent
- **Pacing trick for precise timing:** Per-phrase generation + ffmpeg-concat with explicit silence gaps gives full control over dramatic pauses. See `Documents\Built With AI\tools\build_proof_voice.py` for the pattern.
- **List voices:** `edge-tts --list-voices | grep -iE "Brian|Davis|Guy|Andrew|Ryan|Christopher|Eric"`

## Music · ffmpeg synth (placeholder only · needs upgrade)
- Generate a multi-layer sine wave drone with `ffmpeg -f lavfi -i "sine=frequency=55:duration=30"` etc. → 5-layer chord + pink noise + fade in/out → ~720 KB 30s mp3 at 192 kbps.
- See `Documents\Built With AI\assets\music\music_bed_v1.mp3` for the artifact.
- **Sounds thin.** Functional for proving the concept, not for a published video. Real music is the biggest pending upgrade for Built With AI.

## Music sources that FAILED tonight · don't retry without different approach
- **Mixkit:** CDN URLs behind JS interaction. WebFetch can't extract them.
- **Bensound:** URL pattern `https://www.bensound.com/bensound-music/bensound-epic.mp3` returned 9-byte error.
- **Pixabay:** 403 Cloudflare on WebFetch.

## Music sources to try next when needed
- **archive.org music collections**, direct download URLs work via curl, public domain + CC-licensed
- **incompetech.com (Kevin MacLeod)**, known URL pattern: `https://incompetech.com/music/royalty-free/mp3-royaltyfree/<TrackName>.mp3`
- **FreePD.com**, public domain music, direct downloads
- **Paid (when justified):** Storyblocks ($15/mo, real cinematic library), Epidemic Sound ($15/mo)

## B-roll · Pexels Videos API (free with PEXELS_API_KEY)
- **Endpoint:** `https://api.pexels.com/videos/search?query=<keyword>&per_page=3&size=medium&orientation=landscape`
- **Auth:** `Authorization: <key>` header
- **CRITICAL gotcha:** Pexels CDN blocks default `urllib` User-Agent on the actual MP4 download. Must use `requests` with `Mozilla/5.0` browser UA + `Referer: https://www.pexels.com/`.
- See `Documents\Built With AI\tools\fetch_proof_broll.py` for working pattern.

## Video render · Remotion 4.0.442 (free, already installed)
- Composition file: `remotion/VideoDocStyle.jsx` (registered in `remotion/Root.jsx`)
- Render: `npx remotion render remotion/index.jsx ProofDocStyle outputs/proofs/out.mp4`
- **Critical config:** `Config.setPublicDir("./assets")` in `remotion.config.js` makes `staticFile("broll/foo.mp4")` resolve to `assets/broll/foo.mp4` instead of default `public/`.
- 30-sec 1080p/30fps render takes ~4-5 min on CPU.

## Visual primitives proven tonight (in VideoDocStyle.jsx)
- Kinetic text (fade + slide-up + slight zoom on entry)
- Letter-by-letter typewriter with yellow cursor
- Number counter (interpolated from 0 to target)
- Color-graded B-roll (CSS filter contrast/saturate/brightness)
- Dark vignette (radial gradient overlay)
- Teal/orange tint (linear gradient + multiply blend mode)
- Spring-bounced logo punch
- Small labels with letter-spacing tracking

## Paid upgrades when justified
- ElevenLabs Creator $22/mo, KD's cloned voice (deferred until visual quality landed)
- Storyblocks $15/mo, cinematic B-roll library (replaces generic Pexels)
- Pika $10/mo or Runway $12/mo, AI-generated cinematic B-roll
- Submagic $41/mo, kinetic word-by-word captions (Phase 3 only)

## Related
- [[built-with-ai-strategy]], overall brand strategy
- [[reference-driven-design]], why this whole pipeline got built but not landed on first try
