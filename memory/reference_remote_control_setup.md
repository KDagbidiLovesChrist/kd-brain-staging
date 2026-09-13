---
name: reference-remote-control-setup
description: "How King David remote-controls his personal laptop from his iPhone, Tailscale tunnel + Windows Remote Desktop. Setup details, IPs, account, troubleshooting."
metadata: 
  node_type: memory
  type: reference
  originSessionId: 226f5606-69e9-4aa3-b329-a1fab7a95d49
---

# Remote Control: iPhone → Personal Laptop

Set up 2026-05-26 night. Lets King David drive his personal laptop (VS Code, Claude Code, all skills) from his iPhone anywhere there's data signal.

## The stack
- **Tunnel:** Tailscale (free tier, 100 device cap), secure mesh VPN between his devices.
- **Remote desktop server:** Windows Remote Desktop (built into Win 11 **Pro**, not Home).
- **iPhone client:** Microsoft "Windows App" (renamed from "Microsoft Remote Desktop" in 2024).
- **Tailscale account:** signed in with **Google** (`kingagbidi@gmail.com`). MUST be the same identity on every device added to the tailnet. Do NOT mix Apple/GitHub/Microsoft sign-ins.

## Laptop facts (personal · DESKTOP-GRULS39)
- Tailscale IPv4: **100.103.239.114** (run `tailscale ip -4` if it ever changes)
- Computer name: `DESKTOP-GRULS39`
- Local IPv4 (home wifi only): `192.168.1.19`
- Windows user: `Dell` (password must exist, RDP blocks blank-password accounts)
- RDP service: `TermService` (auto-start)
- Firewall group enabled: `Remote Desktop`
- Network Level Authentication: required (UserAuthentication=1)

## Setup script
`C:\Users\Dell\.claude\tools\setup_remote_control.ps1`, re-runnable, idempotent. Enables RDP + installs Tailscale via `winget`. Needs UAC elevation. Re-use on the **work laptop** ONLY if Amazon IT has approved remote access (see Risk below).

## Daily use
1. Laptop must be **awake**. Power settings: "Sleep when plugged in = Never". Lid-close action = Do nothing.
2. iPhone: open **Tailscale** app → toggle ON. Then **Windows App** → tap "My Laptop" tile.
3. Address used in Windows App PC entry: `100.103.239.114` (the Tailscale IP, NOT the local 192.168.x).
4. Touch = click. Two-finger drag = scroll. Pinch = zoom.

## Security posture
- Tailscale ACL: default (own-devices-only). NEVER share nodes externally.
- NO port 3389 exposed on router. Tailscale replaces that need.
- 2FA must stay on for the linked Google account.
- If iPhone lost: log into Google → Tailscale admin → remove the iPhone node = instant cutoff.

## Risk · DO NOT replicate to work laptop without IT approval
Installing Tailscale + enabling RDP on the Amazon work laptop almost certainly violates Amazon network policy. The DCEO Brain (on work laptop) is **not** to be made remote-accessible via this setup. Personal laptop only.

## Troubleshooting
- **Can't connect from cellular:** confirm Tailscale toggled ON in iPhone Settings → VPN, and that mobile data is allowed for Tailscale.
- **Credentials rejected:** Windows password for `Dell` is wrong/blank. Reset via `netplwiz` or Settings → Accounts.
- **Connects then drops fast:** laptop slept. Re-check power settings.
- **Black screen on connect:** another RDP session is active. Sign out locally first.

## Related
- [[reference-onboarding-v3]], main onboarding index
- See also `C:\Users\Dell\.claude\plans\i-want-to-connect-happy-rabin.md` for the full original plan with diagrams.

---

## Live status (2026-05-26 night) · RESUME HERE if session restarted

Mid-setup. State at time of laptop reboot:
- Laptop Tailscale: ✅ up at `100.103.239.114`, signed in as `kingagbidi@gmail.com`
- iPhone Tailscale: ✅ up at `100.79.248.119` (iphone171), green
- Laptop RDP service: running, fDenyTSConnections=0, firewall enabled (Any profile)
- iPhone Windows App: PC entry added, Credentials = `Dell` + newly-set Windows password
- **Blocker:** RDP listener not binding to port 3389 even after restarting TermService + UmRdpService + SessionEnv. Service restart script reported "STILL NOT LISTENING. Reboot will fix it."
- **Action requested of King David:** reboot laptop, sign back in, then retry iPhone Windows App connection.
- **Next verify command (run after reboot):** `Get-NetTCPConnection -LocalPort 3389 -State Listen`, should now return a row.
- If still empty after reboot: check Windows Defender Firewall logs, group policy `gpresult /h`, and any third-party security software blocking 3389.

Windows password for `Dell` was set tonight via Settings → Sign-in options (King David chose it himself, I don't have it). PIN/Hello still work for local sign-in.
