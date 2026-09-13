# 🧠 BRAIN_BOOTSTRAP · From a Clean Clone to a Working Brain

> **Why this exists:** This guide proves the brain survives losing the laptop and is step one toward the sellable King AI OS (`/os_builder`). It's the checklist for going from "I cloned the GitHub repo" to "everything works."

---

## Step 0 — What you need already installed

Before you start, confirm you have these tools on the machine. Run each check command in PowerShell:

1. **Git** — `git --version` (should say 2.40+)
2. **Python 3.12+** — `python --version` (should say 3.12 or newer)
3. **Node.js + npx** — `npx --version` (should say 8.0+)
4. **Claude Code CLI** — `claude --version` (should say it's installed)

If any fail, install it before continuing. (Ask Claude Code for a quick install command if stuck.)

---

## Step 1 — Clone from GitHub

This is the proof that matters: clone from the *real* remote, not a local folder.

```powershell
git clone https://github.com/KDagbidiLovesChrist/kd-brain.git "C:\Users\Dell\Documents\kd-brain-test"
cd "C:\Users\Dell\Documents\kd-brain-test"
```

After cloning, confirm it's current:
```powershell
git log -1
```
Note the commit hash. Compare it to the one on your laptop's live brain (`git -C C:\Users\Dell\.claude log -1`). If they match, GitHub has the latest. If not, push any missing commits from the laptop to GitHub first.

---

## Step 2 — Restore secrets (the hardest part)

The brain needs several secrets to work fully. They live in different places:

### Claude Code login (do this FIRST, or nothing runs)
The brain runs inside Claude Code, and Claude Code's own auth token lives at `<config-dir>\.credentials.json`. It is correctly gitignored, so a fresh clone does NOT contain it. Symptom if you skip this: every command returns "Not logged in / Please run /login".
- **On a real second machine** (clone placed at `~/.claude`): just run `claude login` once and sign in.
- **When testing via `CLAUDE_CONFIG_DIR` on this laptop:** either run `claude login` while pointed at the clone, or copy `C:\Users\Dell\.claude\.credentials.json` into the clone root (delete it again after the test).
(Verified 2026-07-04 regeneration test: this was the one missing step. Now documented.)

### `.env` (in the root of the cloned brain)
Contains: `KIE_AI_API_KEY`
- **Where to get it:** KIE.ai dashboard → API keys → your key
- **Where to put it:** Create `C:\Users\Dell\Documents\kd-brain-test\.env` with one line: `KIE_AI_API_KEY=your_key_here`

### `.env.master` (also in the root)
Contains: `PLAINLY_API_KEY`, `ELEVENLABS_API_KEY`
- **Where to get them:** Plainly AI dashboard + ElevenLabs dashboard → API keys
- **Where to put it:** Create `C:\Users\Dell\Documents\kd-brain-test\.env.master` with:
  ```
  PLAINLY_API_KEY=your_plainly_key
  ELEVENLABS_API_KEY=your_elevenlabs_key
  ```

### Google OAuth (for Google Drive/Sheets/Calendar)
Files: `credentials.json`, `token.json`
- **Where to get them:** Google Cloud Console → OAuth 2.0 Client ID → download credentials
- **Where to put them:** Copy into the cloned brain's root folder (same place as `.env`)

### GitHub PAT (personal access token)
File: `.git-credentials` (intentionally *outside* the repo, a Windows security boundary)
- **Where it lives on your laptop:** `C:\Users\Dell\.git-credentials`
- **This is separate from the clone.** If cloning from GitHub requires auth, you may need to set it up on the new machine. (Git will prompt you or use existing credentials.)

### Firecrawl MCP (embedded in settings.json, already present)
- **Status:** `settings.json` has a live Firecrawl URL-key. It works but is not a secret-safe pattern (see "Known Gaps" below).
- **Action:** No setup needed for the test, but this is flagged for future rotation.

---

## Step 3 — Install Python + tool dependencies

The voice stack (faster-whisper + Kokoro + ffmpeg) handles its own setup.

```powershell
cd "C:\Users\Dell\Documents\kd-brain-test"
.\tools\voice\setup_voice.ps1
```

This script will:
- Install Python packages via pip (faster-whisper, kokoro-onnx, sounddevice, etc.)
- Download two large model binaries (325MB + 28MB, gitignored because they're too big for GitHub)
- Warm up the speech recognizer

Also install system-wide (one time per machine, not per brain clone):
- **Ollama** — download from ollama.ai, install, run `ollama pull qwen2.5-coder` for the cheap-lane model
- **ffmpeg** — install via `winget install ffmpeg` or download from ffmpeg.org

---

## Step 4 — Point Claude Code at the cloned brain

**For the regeneration test (what you're doing now):**

Open a fresh PowerShell terminal (separate from any running Claude Code session):

```powershell
$env:CLAUDE_CONFIG_DIR = "C:\Users\Dell\Documents\kd-brain-test"
cd "C:\Users\Dell\Documents"
claude
```

This tells Claude Code "load your config from the clone, not the live laptop brain." Zero risk — the live brain is never touched.

**For a real second machine (future):**

On the new machine, just put the cloned brain at `~/.claude` (e.g., `C:\Users\[newuser]\.claude\`). No environment variable needed, Claude Code finds it automatically.

---

## Step 5 — Verify MCP servers connect

The brain has three MCP servers configured in `settings.json`:

1. **Playwright** — runs via npx, auto-fetches on first use
   - Test: inside the Claude session, ask the Playwright skill to "list available browsers"
   - Success: it responds with browser names

2. **n8n-mcp** — also via npx
   - Test: ask about available workflows or n8n connection
   - Success: it responds without auth errors

3. **Firecrawl** — remote HTTP MCP, no local install needed
   - Status: just works, no setup required beyond the key in settings.json

---

## Step 6 — The "how you know it worked" checklist

Run these in order inside the Claude session from Step 4:

1. **Skill loads:** Type `/` and confirm the skill list renders (should show 54+ commands)
2. **Invoke a simple skill:** Type something like `/aide` or `/find-skills`; confirm it responds using the clone's own files (not an error)
3. **Memory reads:** Ask something answerable only from `memory\MEMORY.md`, like "What's the current money mode status?" — confirm it answers correctly from the clone's copy
4. **Hooks behavior:** Start a new session (stop, then start again in the same terminal). Check whether the `SessionStart` hook fires (it may or may not, see "Known Gaps" below). This is just observation, not a pass/fail.
5. **HUD renders:** Inside the terminal where the clone is active, run:
   ```powershell
   python tools\vault_data.py
   ```
   Then open `_ops\VAULT_HUD.html` in a browser. Confirm it renders with numbers (0 console errors in the browser dev tools). The numbers should reflect the clone's own files, not the laptop's.
6. **Voice stack:** Run the setup script again (idempotent, so safe):
   ```powershell
   .\tools\voice\setup_voice.ps1
   ```
   Confirm pip-install + model downloads succeed. (Actual mic/speaker test is optional and hardware-dependent; skip if there's no real mic.)

If all 6 above work, the clone is a working brain. Celebrate. 🎉

---

## Known Gaps (stated honestly, not hidden)

### 1. The `rules\` folder now syncs
As of 2026-07-05, `!/rules/` was added to `.gitignore`, so the three path-scoped rules files (DCEO work wall, faith guidelines, tool safety) now sync to GitHub. They didn't before. If you cloned before that date, re-pull to get them.

### 2. Hooks hardcoded to this exact path/user
The three hooks in `settings.json` (SessionStart, Stop, PreCompact) have absolute paths: `C:\Users\Dell\.claude\tools\*.py`. On a different machine or user account, these paths won't exist, so the hooks will fail silently. This is a known fragility flagged for the future client-template fix. For the regen test on the same machine, they should work (or fail gracefully, either is fine for the test).

### 3. The Firecrawl key is exposed in a tracked file
`settings.json`'s `mcpServers.firecrawl.url` contains a live key-like segment. It's in a private repo with one collaborator, so contained today, but it violates the "zero secrets in the repo" claim. This is queued for rotation into a proper `.env`-style secret in a future session, not blocking today's test.

### 4. Voice mic/speaker QA needs real hardware
The voice-aide setup can be tested (pip-install + model download), but actual microphone input and speaker output need a real machine with audio hardware. Cloud sessions / sandboxes / headless machines can't fully test this half. This is expected and okay.

### 5. True zero-dependency bootstrap not testable here
This laptop already has Python, Ollama, ffmpeg, Node.js installed. A truly blank machine test would need Windows Sandbox (free, built into Win 11 Pro) or a literal second machine. That's a Tier-2 optional stretch test, not required for today's proof.

---

## To clean up after the test

```powershell
Remove-Item -Recurse -Force "C:\Users\Dell\Documents\kd-brain-test"
$env:CLAUDE_CONFIG_DIR = ""    # unset the env var
```

The live brain at `C:\Users\Dell\.claude` is untouched.

---

## Troubleshooting

**"skills don't load" / "memory doesn't read"**
- Confirm `CLAUDE_CONFIG_DIR` is set: `$env:CLAUDE_CONFIG_DIR`
- Confirm it points to a valid brain folder: `ls $env:CLAUDE_CONFIG_DIR` should show CLAUDE.md, memory/, skills/, etc.

**"hook didn't fire"**
- This is expected and documented (see "Known Gaps"). The hook paths are hardcoded to the laptop's user. Log it as observed behavior, don't treat as a failure.

**"MCP server didn't connect"**
- Playwright/n8n need npx and Node.js: `npx --version` and `node --version`
- Firecrawl needs the URL-key in settings.json (already there, nothing to fix)

**"python script failed"**
- Confirm Python 3.12+: `python --version`
- Confirm you're in the cloned brain folder: `pwd` should show the clone's path
- Confirm .env + .env.master exist if the script tries to load them

---

**Next:** Once all 6 checks pass, log the results in `_ops\BRAIN_REGEN_TEST_<date>.md` following the format in the packaging plan. Walk King through it. Get his approval. Log as a Trust Ledger stone.
