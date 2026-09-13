---
name: project_wisdom_kernel_pool_leak_2026-08-29
description: "WISDOM (the laptop) had an 8-day kernel nonpaged pool leak of 11.68 GB from a file-system filter driver; how it was measured without admin, what it broke, the reboot facts, and what the supervisor must probe so it never runs silent again"
metadata: 
  node_type: memory
  type: project
  originSessionId: 7fc8a4b4-550d-4060-9c39-02cf8febbd51
  modified: 2026-08-29T06:13:08.378Z
---

# The laptop's kernel memory leak, found 29 Aug 2026

**What was seen first:** Ollama refused to load qwen3:8b (`failed to allocate CPU_REPACK buffer of size 3312451584`, HTTP 500), the engine's provers flaked in a different set every run (12, 13, 11, 12, 12 of 14), `Get-CimInstance` hung on every call, `KD_Lead_Pinger` failed with `0x800705AA` "insufficient system resources", and at the end PowerShell itself could not start (`Starting the CLR failed with HRESULT 80004005`).

**What it was, measured with Win32 calls and `NtQuerySystemInformation`, no admin needed:**
- Uptime **8 d 0 h 49 m** (booted 21 Aug 2026 about 06:16, which matches the last at-logon task run at 06:21).
- Physical memory 19.88 GB, load 91 to 97%, but every process working set summed to only 5.9 GB.
- **Pool nonpaged 11.68 GB, pool paged 7.63 GB, commit 49.33 of 49.53 GB.** That is where the missing 12 GB was: inside the kernel, invisible to Task Manager's process list.
- Top pool tags, all per-file bookkeeping: `File` 2,719 MB, `WCsc` 2,602, `FMfc` 1,301, `IoFE` 1,084, `WCfc` 951, `FMwi` 867.
- **The System process (PID 4) held 7,112,425 handles.** Normal is a few thousand. No user process was above 7,605.
- 22 file-system filter drivers installed (read from the registry, no admin); **`wcifs.sys` (Windows Container Isolation FS, auto-start) is the only one whose name fits the `WC` tags**, with `fc` and `sc` being the usual minifilter suffixes for file context and stream context. Strong candidate, not yet proven: proof needs `poolmon`, or a growth watch after reboot with suspects disabled one at a time.

**Why the machine leaks this fast:** it does enormous file churn 24/7 as a server (`git add -A` over 55k files every 15 min, OneDrive syncing 16 GB of Documents, Notion syncs every 30 min, Defender scanning all of it, two IDEs' file watchers over `.claude`). A filter that leaks one context per open reaches 11 GB in 8 days on that workload.

**What it caused downstream, each now explained:**
- Two keepalive scripts (`tools/ollama_gui_keepalive.ps1:31`, `tools/remote_control_keepalive.ps1:20,36`) call `Get-CimInstance`; WMI hung, so each firing hung; both tasks carry a **72-hour** kill cap, so they piled up (53 zombie PowerShells at the peak, cleared by hand twice). Killing them freed only about 1 GB: they were a symptom, not the cause.
- Six repeating `KD_` tasks carry the 72 h cap: Brain_Notion_Sync, Lead_Pinger, Logoi_Tunnel_KeepAlive, OllamaGUI_KeepAlive, RemoteControl_KeepAlive, VaultData_Refresh. `KD_Brain_Sync` and `KD_Brain_Health` already have 10 min.

**Reboot facts (his call, his machine):** every `KD_` task is **"Interactive only"**, runs as Dell, and `AutoAdminLogon` is not set, so after a reboot LOGOI (:5056), the deck (:3200), Mission Control, voice and Remote Control stay down until he logs in at the keyboard. Tailscale is a service and comes back alone. BitLocker is unverified (needs admin to check): if the boot asks for a key he needs it in hand.

**How to apply:**
- The Stage 3 supervisor (`kd_loop.py supervise`) gets three live probes from this: **nonpaged pool bytes**, **System handle count**, and **uptime**, read the same admin-free way, with limits (say 3 GB, 200k handles, 7 days) that raise a STAR brief long before the wall. This failure ran silent for 8 days because nothing watched the kernel. The sovereign meter should carry it as a term too, so 100% cannot show on a machine that is about to fall over.
- After the reboot: run `npm test` once for the 14/14 record, set the six 72 h caps to 10 min, replace the two `Get-CimInstance` calls with `Get-Process`, and record the pool number daily for a week to name the driver by its growth.
- Diagnosing on a starved machine: stop spawning processes. Each `powershell.exe` here cost 30 s or hung outright; `reg.exe`, `node`, `curl` and direct Win32 calls kept working. Read before you spawn, and never chain a slow diagnostic behind another.

Related: [[project_kd_robot_three_nodes_2026-08-29]] (the plan this interrupted; Stage 1 committed as `af7fcb0` before the reboot on purpose, the 25 Aug lesson) · [[project_logos_engine_fixes_2026-08-25]] · [[feedback_verify_route_by_last_run]] (a guard is worth its last hostile run: the keepalives showed "Running" for hours and reported nothing).
