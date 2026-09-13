---
name: reference-notify-and-video-pipeline
description: "How King's phone push (ntfy), instant lead pinger, and the cinematic ad-reel pipeline work. Built 2026-05-31 session 5. Includes the edge-tts stall gotcha + fix."
metadata: 
  node_type: memory
  type: reference
  originSessionId: ac77cecd-05bb-4881-9f59-94e991583161
---

# Phone Push + Lead Pinger + Video Reel Pipeline (2026-05-31, session 5)

## Phone push · ntfy.sh (FREE, working)
- Tool: `C:\Users\Dell\.claude\tools\push_kd.py` → `push(title, message, click_url)` POSTs to ntfy.
- Private topic: **kd-alerts-x7q3m9w2p8k4v** on the DEFAULT server **https://ntfy.sh**.
- King's iPhone: ntfy app installed + subscribed to that topic → **confirmed working**.
- GOTCHA that cost us time: the ntfy app's *default server* must be `https://ntfy.sh`. King had it on a wrong/custom
  server (`ntfy.home.io` is just a placeholder example) → his self-test arrived but our messages didn't. Fix = set
  default server to ntfy.sh + subscribe to the exact topic.
- Wired into `send_notify.py` + `notify_kd.py` (push only on primary iCloud addr to avoid triple-push from the
  3-address domain-watch loop). So domain-live alert pushes automatically. Email stays the backup channel.

## Instant lead pinger
- `tools\lead_pinger.py`: reuses `daily_client_scan.scan()/scan_hn()`, polls every 15 min, **pings the phone per NEW
  fit job** (dedupe set `tools\.leads_seen.json`, cap 800, **primes on first run** so no burst, caps 8 pings/run).
- Windows task **KD_Lead_Pinger** (every 15 min). Daily 8:30 task **KD_Daily_Client_Scan** kept as EMAIL digest only
  (its phone push was removed to avoid double-notify).
- To re-prime: delete `.leads_seen.json` then run `python lead_pinger.py` once.

## Cinematic ad-reel pipeline
- Style study: 6 TikTok refs downloaded via `yt-dlp` (`python -m yt_dlp`) → `Website Builder\reel\refs\ref1-6.mp4`.
  Frames extracted with ffmpeg. Blended style spec in `drafts\video_style_and_dramatic_script_2026-05-31.md`.
- Build: `tools\build_reel_v1.py`, stills + Ken-Burns (ffmpeg zoompan) + dramatic captions (drawtext, use
  `textfile=` to dodge comma/apostrophe escaping) + edge-tts VO (en-GB-RyanNeural --rate=-8%) + synth bed, vertical
  1080x1920. Output `reel\KD_master_reel_9x16_v1.mp4`.
- ⚠️ **edge-tts STALL GOTCHA:** edge-tts throttles/hangs after ~3 rapid calls → render stalls at scene 4 (happened
  twice). Current retry has no backoff. **FIX next session:** add `time.sleep(~8)` between voice calls, OR
  pre-generate all 8 audio files sequentially with backoff, OR swap to King's recorded voice / ElevenLabs ($22).
- ⚠️ **WebGL gotcha:** 3D/Three.js does NOT render in a headless/automated browser (black/loading screen), even
  with swiftshader. For live 3D motion, KING screen-records the demos on his real GPU. Static MCP screenshots DO
  capture the 3D fine (used as the v1 stills).
- Plan: 1 master cinematic reel (all gig video slots + post everywhere) → per-service mini shorts (hub-and-spokes).
  AI voice now, King's voice later. See [[feedback-top-tier-design-standard]] (cinematic+video) and
  [[feedback-reference-driven-design]].
