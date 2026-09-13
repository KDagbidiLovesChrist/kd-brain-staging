---
name: reference-elevenlabs-voice-cloning
description: "Hard-won how-to for cloning King's voice on ElevenLabs (Creator plan) via API. Instant clone = bad for accents (3/10); Professional Voice Cloning (PVC) is the real fix. Key gotchas: Restrict Key OFF, Creator-not-ElevenAPI workspace, 1 PVC slot, captcha verification MUST be live in the app."
metadata: 
  node_type: memory
  type: reference
  originSessionId: c9e3beda-28d3-480c-ac1c-34dcbb7ddfa6
---

# ElevenLabs voice cloning · the hard-won how-to (learned 2026-06-26)

Cloning King's voice for the [[project-content-engine]]. Key = `ELEVENLABS_API_KEY` in `.env.master`. Header = `xi-api-key`.

## 1. Instant clone (`/v1/voices/add`) = NOT good enough for accents
A quick instant clone from 4-15 min of audio scored only **3/10** on King's Irish accent, it smooths distinctive accents into a generic/"foreign" voice. More audio does NOT fix this (it's an instant-clone ceiling). Use instant only for quick tests, never the final.

## 2. THE API KEY GOTCHA (cost us ~10 attempts)
New ElevenLabs API keys default to **"Restrict Key" ON = every endpoint set to "No Access"** → all calls return `401 missing_permissions` (user_read, voices_read, etc.). **FIX: when creating/editing the key, turn the "Restrict Key" switch OFF** (gives full access). Then copy the key. Verify with `GET /v1/user/subscription`.

## 3. THE WORKSPACE GOTCHA
King has 3 ElevenLabs products: **ElevenCreative (= his Creator plan, HAS cloning)**, ElevenAgents, and **ElevenAPI (a separate $0 metered pay-as-you-go product, NO cloning)**. Cloning + credits run on the **Creator plan**, not the empty ElevenAPI balance. Don't be fooled by the ElevenAPI "$0 / Add credits" page.

## 4. Professional Voice Cloning (PVC) = the real fix. Flow:
1. **Delete any junk in the PVC slot first.** Creator plan = only **1 PVC slot**. A broken half-made "Untitled voice" was hogging it → `DELETE /v1/voices/{id}` to free it. (Library voices like Hale/Grant DON'T use your PVC slot; only voices YOU create do.)
2. `POST /v1/voices/pvc` `{name, language:"en", description}` → returns `voice_id`.
3. `POST /v1/voices/pvc/{voice_id}/samples` (multipart `files`), add audio. Need **30 min+ total** before `is_allowed_to_fine_tune` can become True. Convert m4a→mp3 with ffmpeg (`-ac 1 -ar 44100 -b:a 160k`). ~36 min worked.
4. **VERIFICATION (the real blocker):** `GET /v1/voices/pvc/{voice_id}/captcha` returns a **PNG image** with a sentence. The user must record themselves reading it. Submit via `POST /v1/voices/pvc/{voice_id}/captcha` (field `recording`).
   - **⚠️ CANNOT be done over email/voice-memo**, the captcha expires in ~2 min, faster than email can deliver (failed twice: "Time limit for voice verification exceeded"). **King MUST do verification LIVE in the ElevenLabs app** (Voices → the voice → Verify → read the shown sentence → instant submit). That flips `is_allowed_to_fine_tune` → True.
5. `POST /v1/voices/pvc/{voice_id}/train` `{model_id:"eleven_multilingual_v2"}` → state goes to `fine_tuning` (vs "not_started" if not eligible). Takes **a few hours**.
6. When `fine_tuning` state == `fine_tuned`, generate TTS: `POST /v1/text-to-speech/{voice_id}` with `model_id:"eleven_multilingual_v2"`, `voice_settings {stability:0.5, similarity_boost:0.8, use_speaker_boost:true}`.

## 5. Reading the state (diagnose blockers)
`GET /v1/voices/{voice_id}` → `fine_tuning.is_allowed_to_fine_tune` (the gate), `fine_tuning.state` (per-model: not_started / fine_tuning / fine_tuned / failed), `fine_tuning.dataset_duration_seconds` (None = samples not processed yet), `voice_verification.is_verified`.

## 6. Tools built this session
`content-engine\voice\watch_training.py` = background poller that emails + ntfy-pushes King the test when training finishes. I can't HEAR audio → King scores 1-10 by ear (be honest about this; an objective speaker-match tool needs torch/resemblyzer which failed to install on Windows).

## 7. Clone is TRAINED · but the PACING fix is what makes it usable (learned 2026-06-26)
King scored the trained PVC ("King" `ErET8T1peh7wSinZbf7N`) across 3 versions. Verdict: **identity/similarity is
good, but on default settings the tone + PACING read robotic.** The fix that flipped it to "way better, it will
work": **engineer the pacing.** Put `<break time="0.4s" />`-style tags between lines + slow it slightly with
`"speed": 0.93` in `voice_settings` (kept `stability 0.45, similarity_boost 0.85, style 0.15, use_speaker_boost
true`). So the clone is a viable **scale fallback** ONLY with the pacing method; King's REAL voice still leads
the portfolio/premium work (perfect natural pacing). More natural-source recordings = the real long-term lift.

