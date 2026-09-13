---
name: feedback-vault-second-device-test
description: A password vault is only TRUSTED after a same-day login from a second device; master password on paper BEFORE typing; the 15-min fresh-start rescue pattern
metadata: 
  node_type: memory
  type: feedback
  originSessionId: 934066d1-73ab-42fe-9038-0d6b02dd0271
---

# 🔐 Vault rule · second-device test the SAME DAY, paper before keyboard

**What happened (2026-07-02):** King's Bitwarden vault "worked" for 2 days, but only as a remembered laptop session. When the phone finally asked for the master password, it was **lost** (confused with the 48-digit BitLocker key). Hours of "Username or password incorrect" followed. We recovered by the fresh-start pattern below; total loss: nothing.

**Why:** a logged-in session proves nothing about the key. A vault whose master password can't open a SECOND device is not a backup, it's a decoration. And a password that exists only in someone's head is one bad day from gone.

**How to apply:**
1. **Paper before keyboard**, any new master password is written on the physical emergency sheet FIRST, then typed from the paper. Hint field always filled.
2. **Same-day second-device test**, creating/changing a vault password isn't DONE until a fresh login succeeds on another device (phone). That's the QA gate; a live session doesn't count.
3. **Never confuse the locks:** BitLocker 48-digit key = the laptop-disk rescue key (a NOTE in the vault). Master password = the vault's own key. One is stored IN the other, never the same thing.
4. **Fresh-start rescue** (when a Bitwarden master password is truly lost but a session lives): check nothing exists ONLY in the vault → copy anything that does → delete the account via `vault.bitwarden.com/#/recover-delete` (email link, no password needed) → recreate same email, paper-first → refill (`.env.master` splits at ~line 70 into 2 Secure Notes under the ~7k-char limit, `head -n 70 | clip` / `tail -n +71 | clip`, Claude never sees values) → phone test → delete any self-sent key emails (Sent+Inbox+Bin) + Win+V Clear all.
5. **Phone app gotchas** that mimic a wrong password: stale/deleted account cached in the app (delete + reinstall fixes), wrong server region ("Logging in on:" must match .com/.eu), snips/copies silently replacing the clipboard.

Related: [[reference-remote-control-phone-laptop]] · the emergency sheet lives with King's serious documents.
