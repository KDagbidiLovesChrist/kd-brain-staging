---
name: reference-remote-control-phone-laptop
description: "Claude Code Remote Control, phone drives sessions that EXECUTE on the laptop (all keys/tools local); how to connect, restart, and its limits"
metadata: 
  node_type: memory
  type: reference
  originSessionId: 934066d1-73ab-42fe-9038-0d6b02dd0271
---

# 📱→💻 Remote Control · the phone drives, the LAPTOP executes

**What it is (built into Claude Code v2.1.139+, free on Max):** `claude remote-control` runs a server on the laptop. King opens the **Claude mobile app → Code tab** (or claude.ai/code) and the session he types into **runs ON the laptop**, full filesystem, `.env.master` keys, Vercel/ffmpeg/Gmail, all MCP servers. The phone is just the steering wheel. Outbound HTTPS only, no ports opened, Anthropic relays.

**This supersedes "heavy lifting = laptop-only when King is home."** Deploys, image/video gen and email now work from anywhere, as long as the laptop is on and the server is running. (Tailscale+RDP remains the fallback door, [[reference-remote-control-setup]].)

## Start it (laptop)
```
claude remote-control --name "KD Laptop Brain"
```
- Answer `y` to "Enable Remote Control?". Headless/auto-yes: `{ printf 'y\n'; tail -f /dev/null; } | claude remote-control --name "KD Laptop Brain"`
- Runs as a persistent server (32 concurrent sessions, spawned in the cwd, start it in `C:\Users\Dell`).
- First set up 2026-07-02 (updated CLI 2.1.138→2.1.198; had to set `hasTrustDialogAccepted: true` for `C:/Users/Dell` in `.claude.json`, the interactive trust dialog can't be accepted headless).

## Connect (phone)
1. Claude app → **Code** tab → session **"KD Laptop Brain"** (environment "Dell") → tap it.
2. Or browser: the env link printed at start (changes per run), the app list is easier.
3. Type normally; permission prompts answer from the phone.

## If it FREEZES (proven fix, 2026-07-03)
King's phone session went unresponsive after the bridge ran ~22h (likely a laptop sleep broke the relay connection; the process stays alive but goes deaf). Fix that worked:
1. Find the pair: `Get-CimInstance Win32_Process` → the `remote-control` process AND its `--print --sdk-url ...cse_...` session worker. **Never kill the VS Code extension's claude.exe** (its command line starts with the `.vscode\extensions\...` path).
2. `Stop-Process -Force` both → relaunch detached: `Start-Process -FilePath "C:\Users\Dell\.local\bin\claude.exe" -ArgumentList 'remote-control','--name','"KD Laptop Brain"' -WindowStyle Hidden`
3. Nothing is lost: the bridge reconnects to the SAME cloud session ID, chat history intact. King re-opens "KD Laptop Brain" on the phone and it answers again.

## Honest limits
- The laptop must be ON with the server process alive; if it dies (reboot, closed window), someone at the laptop must rerun the start command, or ask the laptop Claude session to.
- Laptop **sleep** can leave the bridge alive-but-deaf → the phone session looks "frozen". Remedy = the restart above; after any sleep/reboot assume one relaunch is needed.
- >10 min offline = session times out (reconnects if the laptop comes back).
- Not a daemon/auto-start yet, candidate upgrade: a scheduled task at logon running the start command (needs King's yes).
- Cloud sessions on the kd-brain repo (the old phone door) still have NO keys, that rule is unchanged; Remote Control is different because execution is local.
