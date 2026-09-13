---
name: integrated-voice-dashboard-pattern
description: Browser HUD + Flask backend for real-time voice interaction (Web Speech Recognition + Kokoro TTS)
metadata: 
  node_type: memory
  type: reference
  originSessionId: c4812fd8-0dc2-47b5-bc05-ff428aa9891a
---

# Integrated Voice Dashboard Pattern

**Built 2026-07-05** for the KD Brain's AI Aide integration.

## Architecture

**Frontend:** Browser (Edge) running VAULT_HUD.html
- Web Speech Recognition API captures mic input
- Modal panel shows live transcription + response
- Sends transcription to Flask server via fetch/POST

**Backend:** Flask API server (localhost:5000)
- Accepts `POST /voice { "text": "user speech" }`
- Reuses existing voice logic (ask_claude, ask_ollama, speak functions)
- Generates Kokoro TTS audio file
- Returns `{ "response": "text", "audio_file": "/path/to/audio.wav" }`

**Audio:** Browser plays audio via `<audio>` element with file:// URL

## Files

- `_ops\VAULT_HUD.html` — Modal UI + Web Speech Recognition handler + fetch call
- `tools\voice\voice_aide_api.py` — Flask server wrapping voice_aide.py functions
- `tools\voice\start_voice_server.bat` — Hidden startup launcher
- `Startup\KD Voice Server.lnk` — Auto-start shortcut (WindowStyle 7 = hidden)

## Key Decisions

1. **Modal over console window** — Unified dashboard experience, no context-switching
2. **Web Speech Recognition** — Built-in to browsers, no extra installation, respects OS mic permissions
3. **Flask backend** — Local HTTP API, browser-safe, reuses existing Python voice logic
4. **File:// audio playback** — Kokoro/edge-tts output saved to temp dir, browser plays it
5. **Hidden Flask startup** — WindowStyle 7 (hidden), no visible console clutter at login

## Deployment

1. Create Flask API wrapper around existing voice script
2. Create silent startup .bat file
3. Create hidden Startup shortcut for .bat
4. Add voice button + modal to HUD HTML
5. Add Web Speech Recognition handler + fetch to HUD JS
6. Test: Double-click start .bat, verify localhost:5000/health responds

## Gotchas

- **Unicode encoding:** Flask print statements fail with emojis on Windows console. Use `[text]` instead of ✝️ for startup logs.
- **Audio path:** Browser can only play audio from `file:///` URLs or HTTP. Temp dir paths work.
- **Mic permissions:** Windows may prompt on first use. Check Settings → Privacy → Microphone.
- **Flask dependencies:** Requires `flask`, `requests`, `soundfile`, `edge-tts` (backup TTS).
- **CORS:** Localhost fetch from Edge works without CORS headers (same-machine, no browser security).

## Reuse

Copy this pattern for any browser dashboard that needs to call local Python scripts:
1. Wrap Python script in Flask endpoint
2. Launch Flask server silently at startup
3. Browser sends fetch request to localhost:5000
4. Return JSON with results + file paths
5. Browser displays results, plays audio/displays files

Cost: ~80 lines Python (Flask wrapper) + ~150 lines JS (modal + Web Speech). No external services.
