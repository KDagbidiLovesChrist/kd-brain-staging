---
name: reference-google-token-reauth
description: "How to fix the Gmail/Google OAuth token when it dies (invalid_grant: token expired or revoked). Recurs every ~7 days until the app is published to production. Includes the re-auth gotcha + the SMTP send fallback."
metadata: 
  node_type: memory
  type: reference
  originSessionId: c5d1dd4c-61db-477b-8314-0bd126c8ffbc
---

# Google OAuth token re-auth (kingagbidi@gmail.com)

**Symptom:** any Gmail read/send via `token.json` fails with
`google.auth.exceptions.RefreshError: ('invalid_grant: Token has been expired or revoked.')`.
This kills `read_gmail_jobs.py`, the **KD Upwork Watcher**, and any Gmail-API send.

**Root cause:** the Google Cloud project `king-david-automation` OAuth consent screen is in
**"Testing"** publishing status → Google **expires refresh tokens after ~7 days**. Not a mistake, a timer.

## Re-auth (fixes it now, ~2 min, needs King at the browser on THIS laptop)
1. **GOTCHA:** `tools\google_auth.py` tries to *refresh* the dead token and crashes instead of starting fresh.
   First move the dead token aside: `mv C:\Users\Dell\.claude\token.json token.json.revoked-<date>.bak`
2. Run `python tools\google_auth.py` **in the background** (it blocks on `run_local_server`).
3. Read the task output: use the **`Please visit this URL` line (the 2nd/line-3 URL, the one whose `state` the local server expects)**, not the first `AUTH_URL:` line.
4. King opens it on this laptop (redirect is `http://localhost:<port>`), signs in as kingagbidi@gmail.com,
   clicks **Advanced → Go to king-david-automation (unsafe)** past the "unverified app" warning, then **Allow**.
5. Script prints `OK: Authentication successful. Token saved` → `token.json` is back. Verify with `read_gmail_jobs.py`.

## Permanent fix (stop the 7-day death)
Console → project **king-david-automation** → **APIs & Services → OAuth consent screen** (newer UI: **"Audience"**)
→ **Publish app** → confirm push to production. Unverified is fine for King's own account (sensitive Gmail scopes
just show the warning). After publishing, refresh tokens stop expiring on the 7-day clock.

## Send fallback when the OAuth token is dead
Gmail **SMTP with the app password** still works (bypasses OAuth): `GMAIL_APP_PASSWORD` in `.env.master`,
`smtp.gmail.com:587` + starttls + `s.login("kingagbidi@gmail.com", app_pw)`. Used in
`tools\send_upwork_batch_2026-06-09.py`. SMTP is send-only, it cannot READ Gmail, so the watcher still needs the token.

`gcloud` CLI is **not installed**, so APIs cannot be enabled / app cannot be published from the command line, it's browser-only. Related: [[reference-upwork-mail-watcher]].
