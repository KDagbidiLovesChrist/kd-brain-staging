---
name: project_security_posture_2026-08-26
description: "Security posture of the brain and the laptop as audited 26 Aug 2026 and updated 29 Aug: what is verified good, what is still unverified (BitLocker), what expires (three GitHub tokens about 31 Aug), and what was refused"
metadata: 
  node_type: memory
  type: project
  originSessionId: 7fc8a4b4-550d-4060-9c39-02cf8febbd51
  modified: 2026-09-03T05:28:33.644Z
---

# Security posture, audited 26 Aug 2026, updated 29 Aug

**Verified good (26 Aug):** no real keys in git history · `kd-brain` on GitHub is PRIVATE · Windows firewall on · Defender real-time protection and tamper protection on.

**Still open:**
- ⚠️ **BitLocker UNVERIFIED.** Checking needs admin; King's to run (`manage-bde -status` in an elevated prompt). It matters twice: if the laptop is lost, and at every reboot (a PIN or a recovery-key prompt stops an unattended boot).
- ⚠️ **Three GitHub tokens expire about 31 Aug 2026 and the brain sync will stop silently when they do.** Rotate before then; the sync task reports nothing on an auth failure.

**Refused, with the reason recorded:** "encrypt it in my own maths so hackers can't hack" is security through obscurity, refuted since Kerckhoffs (1883): a system must stay secure when everything but the key is public.

**Updated 29 Aug:**
- The raw robocopy backup on D: (`Backups\claude-brain`) carried **500 credential-shaped files** (env, token, key and secret in their names) plus all of `the-truth` and `DCEO_BRAIN`. Deleted with King's yes; the clean git clone on D:, which by `.gitignore` never held them, is the only copy now. → [[project_kd_robot_three_nodes_2026-08-29]]
- The write guard refuses any file write that names a credential file and a network tool in the same text. It fired on the memory index for the literal name of the central key store plus a three-letter PowerShell web alias that happens to sit inside an ordinary English word. The index now points at the key SOP instead of naming the store, and that word is gone from it. A false positive with the right reflex; leave the guard alone.

**How to apply:** BitLocker and the token expiry are the two live items and neither is Claude's to do. Never write the central key store's file name into any file that a tool writes alongside anything network-shaped.

**Updated 3 Sep 2026, two finds during Stage 2 cleanup:**
- **A loose, unmatched SSH private key was sitting on the portable drive** (`D:\ollama\id_ed25519`),
  matching neither of the laptop's two known keys, a credential ruling 2 says the drive must never
  carry. Rescued byte-verified to `_private\rescued_d_ollama\` (gitignored) before removal, so nothing
  was lost; its purpose is still unidentified and worth King's eye if he recognises the fingerprint
  `SHA256:3Ga2JenHDND9z/7Vib+YstF6b2vr82Q2yLnrH9AzsBk`.
- **A three-route guard gap closed properly, not silently.** `memory\reference_lllllm_naming_and_layers.md`
  (describes the master-prompt-as-commercial-lock mechanism) was untracked from git on 30 Aug by the
  content-scanning guard test (`tests\unit\test_sync_claude_to_drive.py`), which treats any file
  describing that method as unsafe on git, full stop. King ruled it back onto git specifically, since
  GitHub is proven his own private space (404 to a stranger, 2 Sep); Drive and every model's retrieval
  stay closed. Rather than widen the test's existing allowlist (reserved for files that disclose no
  method at all, by design), a separate `GIT_AUTHORIZED` list was added, one entry, a real dated ruling
  as its reason, with its own test proving the exception can never quietly widen. Pattern worth reusing
  if another guarded file needs the same narrow exception.
- **A process risk, not a code risk:** the 15-minute auto-sync task committed and pushed a repair mid-edit
  once this session, landing a broken test script on origin/main briefly. Caught and fixed within the
  same session; see [[project_kd_robot_three_nodes_2026-08-29]] for the detail.

Related: [[project_wisdom_kernel_pool_leak_2026-08-29]] (the reboot that makes BitLocker matter this week) · [[reference_api_key_setup_sop]] · [[project_work_lane_and_boundaries_2026-08-26]] (the same day's audit of the doors) · [[project_kd_robot_three_nodes_2026-08-29]].
