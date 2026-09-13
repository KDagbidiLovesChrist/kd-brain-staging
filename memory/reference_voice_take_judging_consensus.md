---
name: reference-voice-take-judging-consensus
description: "How to pick the best VO take by CONSENSUS without 'hearing' it: DATA leg (ffmpeg loudness/clipping/silence + faster-whisper transcript for content/stumbles/WPM) + EAR leg (Gemini listens, judges tone/delivery). Includes the Gemini-API top-up gotcha (real key = Google AI Studio pay-as-you-go, NOT a third-party PRO subscription app)."
metadata: 
  node_type: memory
  type: reference
  originSessionId: c1e0908a-d6d9-4077-8815-fca19510d9e1
---

# Judging voice takes by consensus (no ears needed)

When King sends multiple VO takes, DON'T say "I can't judge sound" and DON'T just guess. Judge by a 2-leg
CONSENSUS (King's correction, 2026-06-26, he was right that the data-only pick skipped the ear).

## Leg 1 · DATA (free, always do this)
- **Durations:** `ffprobe -v error -show_entries format=duration -of csv=p=0 file` → spot false starts /
  outliers (a 131s take among ~68s takes = a double-read → skip).
- **Signal stats (ffmpeg):** `-af volumedetect` → mean/max dB (**max at 0.0 dB = CLIPPING = bad**);
  `-af silencedetect=noise=-30dB:d=0.4` → count awkward gaps. **Loudness is FIXABLE** (`loudnorm=I=-14`);
  clipping + stumbles are not.
- **Content (faster-whisper, installed v1.2.1):** transcribe each with `word_timestamps=True` → catches
  re-reads/stumbles ("if your videos die, if your videos die"), missing lines, and a **muddy CTA** (a take
  whose final line transcribes wrong = unclear delivery). Also gives WPM (pace) + the word timing for captions.

## Leg 2 · EAR (Gemini LISTENS · the leg that actually hears tone)
- Use `google.genai` (`from google import genai`, model `gemini-2.5-flash`) exactly like
  `tools\gemini_watch_local.py`: `client.files.upload(file=take)`, wait ACTIVE, then `generate_content` with
  all takes + a prompt to score clarity/confidence/naturalness/pace, rank, and name the BEST. Gemini CAN
  process audio (m4a/mp3). This is the tone/delivery leg the data cannot measure.

## Combine
Reconcile the two legs. Agree → done. Disagree → weigh tone heavily for a hook video, but NEVER pick a take
with stumbles or a muddy CTA. (Worked example 2026-06-26: data picked Take 4 of the channel video #1 =
cleanest read + crispest CTA; Gemini ear-leg pending a credit top-up at the time.)

## Polish + master the chosen take (free, ffmpeg) + verify by ear
Chain: `highpass=f=85, equalizer=f=300:t=q:w=1.2:g=-1.5 (de-mud), equalizer=f=3500:t=q:w=2:g=2 (presence),
deesser, acompressor=threshold=-18dB:ratio=2.5:attack=5:release=120, loudnorm (2-pass)`; trim lead/trail silence.
**The -14 LUFS target belongs to the FINAL MIX (voice+music+SFX), NOT the bare voice stem**, a peaky phone VO
can't reach -14 alone without squashing it (over-processing). Leave the stem ~-17 LUFS clean, normalize the
finished ad to -14. **Verify the polish by ear with TWO Gemini models** (A/B raw vs polished: "clearer AND still
natural? any artifacts?"). On the Revolut VO, Pro + Flash both said "ship it, natural, no artifacts."

## ⚠️ Gemini API top-up gotcha (money guardian)
- `429 RESOURCE_EXHAUSTED: prepayment credits depleted` = the EXISTING `GEMINI_API_KEY` (in `.env.master`)
  just needs CREDITS, NOT a new key. Top up at **Google AI Studio (aistudio.google.com → Get API key /
  Billing)**. It is **pay-as-you-go and tiny** (judging a few audio clips = fractions of a cent).
- **Per-PROJECT credits (correction 2026-06-27):** credits attach to the key's PROJECT. If still 429 AFTER a
  top-up, the money went to a DIFFERENT project than the key. Fix = copy the API key FROM the funded project and
  swap it into `.env.master` (done 2026-06-27: the old `...owlg` key was empty; King's funded key `...z_NQ` is now live).
- **DO NOT** buy a third-party "all AIs in one app / Upgrade to PRO" subscription (e.g. €1 trial → €29.99/mo)
  to "get a Gemini key", those give chat access in THEIR app, NOT a Google API key, and the recurring charge
  is a trap (King nearly bought one 2026-06-26). The real key lives only at Google AI Studio.
