---
name: reference-api-key-setup-sop
description: "How new API keys get wired into this brain safely and permanently, one-time setup via .env.master, never through chat, plus which jobs need a real API (video/vision) vs what the free local model (Cheap Lane) can already do."
metadata: 
  node_type: memory
  type: reference
  originSessionId: d754f180-4002-4033-9b55-ae85aec9e421
  modified: 2026-08-23T11:50:48.443Z
---

# API Key Setup: One-Time, Not Repeated

King's ask (2026-08-06): store keys somewhere central so this isn't redone every time, and remember the exact steps so future sessions move faster. Here's the standing system, already mostly built, plus the one gap this session found and fixed.

## The central storage already exists: `C:\Users\Dell\.env.master`

This file is the single source of truth for every API key in the brain. Tools that need a key (like `tools\watch_video.py`) check the OS environment first, then fall back to reading this file automatically. **Once a key is filled in here, every tool that needs it finds it forever, in every future session, with zero repeat setup.** That's the "remember how it executed the step" King asked for, it's not a step to remember, it's a file to fill in once.

**The file's own stated rule, and why it matters:** "Claude creates this structure. YOU fill in the values. Claude never reads or stores your actual keys." This isn't caution for its own sake. On 2026-05-25 a Supabase DB password was compromised specifically because it had been typed into a chat transcript. Since then, the standing practice is: secrets never pass through the conversation, in either direction. When checking whether a key is present, use `sed 's/=.*/=/'` or similar to see key NAMES only, never the values. When a key needs adding, King types it into the file himself, Claude never asks for it in chat and never writes it in.

## Update 2026-08-23: the store was right, one reader was pointing at the wrong file

`tools\logoi_keys.py` built its path from its own location, and since it lives in `tools\`, its
idea of "the store" was `C:\Users\Dell\.claude\.env.master`, a small 3 key file, not the real
one a level up. LOGOI could therefore reach only **4 of 16** keys. Nothing was missing, it was
reading the wrong file. This is what made a working Firecrawl key look absent and got LOGOI
written off as having no web search.

Fixed by giving the module an explicit ordered list, `STORE_PATHS`, ending at the real store.
Reachable keys went **4 of 16 to 15 of 16** (only `VAPI_API_KEY` is genuinely blank). The two
small duplicate files were folded in and retired to
`_private\retired_env_2026-08-23\`.

**The lesson worth keeping:** a key reported as "missing" should be checked against *which file
was actually read* before anyone goes and generates a new one. Every other tool in `tools\`
already used the full absolute path and was fine.

**Also standing now:** `OPENROUTER_API_KEY` and `NVIDIA_API_KEY` exist as Windows USER variables
as well as in the store, because `claude-code-router`'s config references them as
`$OPENROUTER_API_KEY` and `$NVIDIA_API_KEY` rather than holding a literal secret. A router
started from a terminal that was already open before those variables were set will not see them,
which looks exactly like a broken key. Open a fresh terminal, or start it with the values
injected from the store.

## How to add a new key, step by step (for King, non-technical)

1. Windows key + R, type `notepad "C:\Users\Dell\.env.master"`, Enter.
2. Ctrl+F, search for the key's name (e.g. `GEMINI_API_KEY`).
3. Click right after the `=`, paste the key, no spaces or quotes.
4. Ctrl+S to save, close Notepad.
5. Tell Claude it's done. Claude verifies by checking presence only (never the value) and re-runs whatever needed it.

## Making a key available everywhere, not just to Python scripts that check `.env.master`

For keys used a lot across a working session, Claude Code itself can be told to load an environment variable automatically for every terminal command it runs, via the `update-config` skill (writes to `settings.json`, not `.env.master`). This is the right move once a key is confirmed working and used often. Same rule applies: King runs the command that sets the value himself, or the skill is invoked once King confirms the key already exists somewhere Claude doesn't need to see the raw value to reference it.

## The gap this session found: `GEMINI_API_KEY` was never actually live

`tools\watch_video.py` (the engine behind the `/watch` skill) needs `GEMINI_API_KEY` to do a real deep video watch. On 2026-08-06 this was found completely empty in `.env.master`, an old value existed only as a comment ("old free-tier key backup, 2026-06-09"), never in the real `GEMINI_API_KEY=` line. Claude did not activate that backup value, per the rule above. King needs to either move that old value into the real line himself (fastest, might be expired) or generate a fresh one free at aistudio.google.com (2 minutes, no card needed).

## Which jobs need a real (paid-tier-capable) API vs the free local model

King's Cheap Lane setup (`ccr code` → local qwen3:8b, see `[[reference-cheap-lane-setup]]`) is genuinely free and good for routine text work: writing, reasoning, summarizing, classifying. **It is text-only. It cannot see images or video.** Any job that requires actually watching a video or looking at a photo needs a vision/video-capable model. Gemini (via `GEMINI_API_KEY`) is the one already wired into this brain for that job, and its free tier covers it. Don't reach for the local model on a video/image task expecting it to work, it structurally can't, regardless of cost.
