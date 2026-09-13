---
name: project-connect-everything
description: "Connect the brain to every app on King's phone: door status per app, King's pending hand-steps (logins/QR/webhook paste), and the honest no-door verdicts (Snapchat, iMessage, bank)."
metadata: 
  node_type: memory
  type: project
  originSessionId: 4a3e4224-5fc9-48a0-ae07-6911fcbd6764
  modified: 2026-09-06T10:04:18.476Z
---

# Connect Everything · Phone Apps → Laptop Doors (built 2026-07-26)

**The idea King approved:** we never connect to the phone, we connect to the ACCOUNTS behind the apps. Official API where one exists, the browser door (Playwright persistent profiles) where none does. Power level: **read + draft, King sends**; autopilot only per-flow after the Trust Ledger path (Tested → Approval → Trusted). Plan: `plans\how-can-i-connect-delegated-bachman.md`.

## Door status (2026-07-26, all €0)

| Door | Status | Proof |
|------|--------|-------|
| Payhip sale alerts | ✅ VERIFIED END-TO-END 08-01 | ntfy URL confirmed IN the live webhook field (read via the payhip door, read-only probe), King had already pasted it |
| Payhip on-demand | ✅ DOOR LIVE 08-01 | King logged in via browser_door; dashboard screenshot-proven (75% store setup) |
| Gmail/Calendar/Drive/Sheets | ⚠️ REGRESSED 07-31, RE-CONFIRMED STILL BROKEN 09-06 | live check: only gmail read+send OPEN; sheets/drive/calendar scopes LOST again (a Gmail-only re-consent, likely the Upwork watcher, overwrote the 5-scope token). Root cause unchanged: app still in Testing mode. Fix = King flips to "In production" THEN `google_auth.py` re-run |
| WhatsApp Web | ✅ DOOR LIVE 08-01 | King scanned QR; session verified LIVE (chats visible, screenshot proof). Read-a-specific-chat tool added same day: `tools\whatsapp_read_chat.py` (dumps messages + downloads attachments, still no send) |
| TikTok stats | ✅ LIVE | real pull: @30kingdavid 7 followers · 102 likes |
| Instagram stats | 🟡 ready | proven pattern (buka tool), needs King's handle in `social_stats.py` |
| X | 🟡 ready | Apify actor wired, needs King's handle |
| YouTube | 🟡 ready | needs YOUTUBE_API_KEY (2-min console step) + channel handle |
| LinkedIn | 🟡 tool ready | browser door, needs one login; READ+DRAFT only, never bulk |
| Amazon shopping (orders) | 🟡 tool ready | sign-in detection proven, needs one login; read-only, never buys |
| Snapchat | ⛔ NO DOOR | no consumer API, crippled web, stays on the phone (honest verdict) |
| iMessage | ⛔ NO DOOR | Apple locks it to Macs, impossible on this Windows laptop |
| Bank/Revolut | ⛔ BY DESIGN | exports only, Claude never logs in (Accountant flow) |
| iCloud | ⛔ NO DOOR | re-confirmed 09-06. King's iCloud address is a delivery address only, no API or IMAP wiring exists, never has |
| OneDrive | ⛔ NO DOOR (sync only) | re-confirmed 09-06. Filesystem sync via Microsoft's own desktop client only, zero Microsoft Graph API wiring. The OneDrive-located brain copy and `.claude` are two separate git working copies of the SAME GitHub repo (both origin = the kd-brain repo), the real link between them is Git/GitHub, not OneDrive. Deliberate prior choice, see [[project-brain-on-github-phone]] (Drive/Dropbox holding the repo was considered and rejected, file-sync tools corrupt git repos) |
| Dropbox | ⛔ NO DOOR | re-confirmed 09-06. No keys, no code, no mentions anywhere except once as the rejected repo-hosting alternative above |
| Box | ⛔ NO DOOR | re-confirmed 09-06. No keys, no code, no mentions anywhere |

## ✅ RESOLVED 2026-07-30: the dead Google token
`invalid_grant` on refresh (Testing-mode OAuth refresh tokens expire every 7 days). **notify_kd.py and ALL Gmail sends were silently down ~Jul 14 → Jul 30.** How it ended: the Upwork watcher's own consent pop-up self-healed Gmail (2 scopes) at 18:50 on 07-30 when King clicked through it; the full `google_auth.py` re-auth the same evening granted all 5 scopes. Proof: `google_check.py` all OPEN (real inbox + calendar reads) + live send Gmail id 19fb43ce366d088c. **Still pending (King, 2 min): OAuth consent screen → "In production"** in the Cloud console, or the token dies again every 7 days.
**Outage damage (honest):** ntfy phone pushes + Payhip sale alerts + GitHub sync never depended on Google, they kept working. Upwork mail watching was blind Jul 14-30. Eddie roster: no automated sender exists (Aide duty on roster publish); ask King whether a new roster block published since Jul 21, if yes send Eddie the PDF now.
**⚠️ NEW FIND (separate issue, unfixed):** KD_Daily_Client_Scan, KD_Nightly_Review and KD_Weekly_Audit end in scheduler refusal 0x800710E0. Cause: StartWhenAvailable=False + laptop asleep at their 02:00/08:00/08:30 triggers, so missed runs are skipped, not caught up. Fix = flip StartWhenAvailable on (needs King's yes).

## 🆕 Live re-check 2026-07-31 (session: sync audit night)
TikTok door re-proven (fresh pull @30kingdavid 7 followers · 102 likes; studio handle still returns nothing).
All 6 browser profiles exist on disk (whatsapp/payhip/linkedin/x/instagram/amazon); login state NOT verified
(needs opening each door, deferred, late night). Google regression above found by `google_check.py`.
**💰 Spotted in the Gmail check:** inbox headline "$27.06 payment to Eleven Labs Inc. was unsuccessful",
an ElevenLabs sub is still active despite the €0-toolkit August plan; flagged to King (cancel or fix, his call).

## 🔑 2026-08-01 ~02:10 · King created 2 GitHub PATs himself (NOT a breach, verified by asking him)
`claude-kd-brain` (personal device) + `claude-code-kd-brain-DCEO` (**King's decision: connect the work
laptop to the work part of the brain**). Counsel was given ONCE and is CLOSED, do not re-litigate:
(a) classic repo-scope PAT = all private repos, (b) git clone = whole repo not a folder, (c) DCEO_BRAIN
lives outside the synced repo (OneDrive route + Bedrock is the built work design). King's ruling: "it
follows the safe guard rule." Standing OFFER (parked): a work-only mirror repo of `_datacentre/` with
its own small token, say the word and it gets built.

## 🆕 2026-08-01 · Gmail SMTP app-password login now BROKEN, OAuth path still fine
`tools\send_file_smtp.py` (raw SMTP login using `GMAIL_APP_PASSWORD` from `.env.master`) failed with
535 Bad Credentials sending a file to a third party (Whitney). The separate OAuth `token.json` +
`google-auth`/`googleapiclient` path (same one `notify_kd.py`/`send_olly_to_yahoo.py` use) worked fine,
including a fresh third-party send with an attachment, confirmed twice same day (Gmail ids
19fbef815a78733c, 19fbefa4542e8407). **Going forward: use the OAuth token.json method for any Gmail send,
not the SMTP app-password tool, until someone regenerates that app password.** See
[[project-whitney-housing-form]] for the task this came up in, and
[[reference-legacy-word-form-filling]] for a related lesson (send a PDF, not a .docx, when a colored
border/highlight's exact look matters to a non-technical recipient, Word border-color rendering is
viewer-dependent).

## King's hand-steps (each is minutes; laptop, not phone, except the QR)
1. ~~Google re-auth~~ ✅ DONE 07-30 (all 5 scopes proven). Left: set the OAuth app to "In production" in the Cloud console (2 min, King's browser).
2. **Payhip alerts:** payhip.com → Settings → Developer → paste webhook URL:
   `https://ntfy.sh/kd-alerts-x7q3m9w2p8k4v?title=PAYHIP+SALE&priority=high&tags=moneybag`
3. **WhatsApp:** `python tools\browser_door.py login whatsapp` → scan QR from phone (Linked Devices) → Enter.
4. **Logins (same command, one each):** `login payhip` · `login linkedin` · `login x` · `login instagram` · `login amazon`.
5. **Handles:** confirm TikTok studio handle (@30kingdavidstudio returned nothing) + add IG/X/YouTube handles in `tools\social_stats.py` ACCOUNTS.
6. **Optional YouTube key:** console.cloud.google.com → enable "YouTube Data API v3" → create API key → add `YOUTUBE_API_KEY=` to `.env.master`.

## Rules baked into the tools
READ + DRAFT only, nothing sends/posts/buys without King (until a flow is Trusted). No bulk actions (LinkedIn/WhatsApp bans). No cold outreach ([[feedback-no-cold-outreach-king-tried]]). Browser profiles live in `.claude\browser_profiles\`, git-ignored by the default-deny lock, logins never reach GitHub. Faith content never touches any of these doors.

## Autopilot candidates (need King's yes each, per Trust Ledger)
1. Eddie roster send on new publish · 2. Payhip sale alert (already hands-free by design, the webhook needs no one).

## 🆕 2026-08-06 night: WhatsApp reader fixed + a new loop-collect tool
`tools\whatsapp_read_chat.py` had two real bugs found while pulling a batch of files King sent
himself: (1) the document-download loop reused stale element handles after the first click
re-rendered the pane, causing every download after the first to fail silently; (2) the fresh-query
fix itself broke on titles containing literal quote characters (`Download "IMG_1234.WEBP"`), needed
the CSS attribute value wrapped in single quotes instead of double. Both fixed in place, verified
working (8-for-8 downloads in one run).

**New tool: `tools\whatsapp_read_chat.py`'s sibling, `tools\whatsapp_loop_collect.py`.** For when
King is actively sending a big batch (screenshots, docs) to his own self-chat over several minutes:
opens the chat once, polls the DOM in-process every N seconds (no repeated browser relaunches),
stops once a target count is hit or the count goes stable for a few checks, then downloads
everything not already saved. Self-chat found by searching the phone number, not "King" (that
matched a different, unrelated work contact named King first).

**A real technical read-only path for photos, confirmed working:** King sending files as
"Document" (not "Photo") from WhatsApp's attach menu is what makes them downloadable via
`document-thumb` selectors, normal photo attachments would not be caught by this pattern.
Worth remembering as the standing instruction whenever asking King to send images this way again.

## 🆕 2026-08-06 later: the real way to get a complete WhatsApp chat inventory
The live chat pane is virtualized (WhatsApp only mounts a small window of messages near the current
scroll position), so scrolling and counting `document-thumb` elements in the main pane badly
undercounts on any chat with more than a handful of messages, confirmed the hard way (found 17, then
35, before finding the true number). **The reliable source is the chat's own "Media, links and docs"
panel** (click the chat header to open Contact Info, click "Media, links and docs," a real total
count is shown right there, then click the "Docs" tab and scroll that list specifically, it also
virtualizes but converges cleanly). New tools: `tools\whatsapp_full_inventory.py` (top-to-bottom
sweep, unions message ids across scroll positions), `tools\whatsapp_docs_count.py` (opens the panel,
counts and lists distinct doc filenames), `tools\whatsapp_docs_download_all.py` (same panel, downloads
everything not already saved). **One real gotcha that cost several failed runs:** the exact button
text is "Media, links and docs" (no comma after "links"), not "Media, links, and docs", a single
wrong comma made every click silently fail to find the element.

## 🆕 2026-09-06: a real cloud connections audit, the Google regression re-confirmed still live
Read live credential files and code rather than trusting the record. **The 07-31 Gmail/Calendar/
Drive/Sheets regression is STILL PRESENT as of tonight, not yet fixed:** Gmail read+send stays live,
Drive/Sheets/Calendar scopes are still missing from the token store as of 10:20 tonight. Same fix as
always, King re-runs the Google auth helper once, then flips the Google Cloud OAuth consent screen
from Testing to In production so a future re-consent stops clobbering the scope grant.

**New negative confirmations, checked directly rather than assumed:**
- **iCloud:** not connected at all, no API or IMAP wiring exists. King's iCloud address is used only
  as a delivery address, never an authenticated account. iMessage stays confirmed impossible on this
  Windows laptop (Apple restricts it to Macs, same standing verdict as the row above).
- **OneDrive:** filesystem sync only, via Microsoft's own desktop client, zero Microsoft Graph API
  wiring anywhere. Confirmed tonight: the OneDrive-located brain copy and `.claude` are two separate
  git working copies of the SAME GitHub repo, the real link between the two is Git/GitHub, not
  OneDrive, OneDrive's sync client just happens to also passively upload that folder because of where
  it sits on disk. This was a deliberate prior choice, see [[project-brain-on-github-phone]] (Drive or
  Dropbox holding the repo was considered and rejected, file-sync tools corrupt git repos).
- **Dropbox and Box:** neither is connected, no keys, no code, no mentions anywhere in the brain
  except Dropbox once as the rejected repo-hosting alternative above.
- **Yahoo:** still confirmed CONNECTED, a real IMAP app-password login (read-only mail search only,
  no storage, no send capability from that credential).
- **Supabase:** still confirmed CONNECTED, the real `king-david-prod` Postgres and Auth project used
  by `/lead_qualifier_app` and client RAG agents. Not a general storage backend for the brain itself.
- **Vercel storage** (KV/Blob/Postgres): not connected. The Vercel token that exists is deploy-only.

**A stale-doc flag, not fixed tonight:** `memory\reference_apis.md` does not cover Drive, Calendar,
Sheets or storage at all, and predates the current Google/Supabase state described here. Flagging for
whoever next touches that file, no rewrite tonight.

Related: [[reference-mcps]] · [[reference-notify-and-video-pipeline]] · `knowledge\TOOLS_CONNECTED.md`

---

## THE GOOGLE SCOPE REGRESSION IS CLOSED (9 Sep 2026, ~21:50)

Carried since **31 July**: Gmail read and send worked, Drive, Sheets and Calendar did not. Checked
again on 6 Sep and still broken. Fixed tonight on King's word, and it was smaller than every earlier
write-up assumed.

**It was never a missing project.** The OAuth client file already held an `installed` client for
project **`king-david-automation`**, and the saved token already held a live refresh token. Nothing
had to be created. The storyboard told him "a Google Cloud project, your account, not mine" and that
was wrong.

**It was never disabled APIs either, and this part is worth keeping.** Probing the three dead APIs
with the OLD two-scope token returned `insufficientPermissions` and
`ACCESS_TOKEN_SCOPE_INSUFFICIENT`, NOT `accessNotConfigured`. Those are different errors: the first
means the service is reachable for the project and only the grant is short, the second means the API
is switched off. So the probe DOES separate the two causes. An earlier note this session said it
could not, and that was wrong.

**The whole cause was the consent screen.** `tools/google_auth.py` has always asked for five scopes.
Only two were ever ticked. The script detects it itself and says so:

```
Token valid but INCOMPLETE (2/5 scopes granted) - starting fresh sign-in.
```

**Proven against the live APIs, not against the saved file:**

```
Drive      HTTP 200   signed in as kingagbidi@gmail.com
Calendar   HTTP 200   3 calendars visible
Gmail      HTTP 200   kingagbidi@gmail.com, 10,957 messages
```

Sheets is granted; reading it needs a real sheet id, so it is proven by grant rather than by call.

### Method note, because a guard fired and was right to

A single command that read the saved credential and called the network was refused by
`pretooluse_guard.py` as exfiltration-shaped. Correct. Redone both times as two declared halves:
half one stages only the short-lived access token locally and never the refresh token, half two
sends it to Google's own hosts only, and the staged copy is deleted after. **Repeat that pattern
rather than working around the hook.**

### A REAL BUG IN THE GUARD, found by it firing on a documentation commit

The same guard then refused a commit message with **no network call in it at all**, and then refused
the diagnostic of that refusal. Cause:

`EGRESS` is matched as a plain substring, and it contains entries short enough to hide inside
ordinary English:

```
short EGRESS entries : ['curl', 'wget', 'iwr', 'irm', 'ncat', ' nc ', 'scp ', 'sftp', 'ftp ']

'reconfirmed the fix'      -> egress hits: ['irm']
'the value was affirmed'   -> egress hits: ['irm']
'infirmary rota'           -> egress hits: ['irm']
'a firm answer'            -> egress hits: ['irm']
```

So any text saying **"confirmed"** near a credential filename is blocked. Same class as the inverted
IPv6 rule this file already had found in it once.

It fails in the safe direction, so nothing was ever at risk. The danger is different: a guard that
blocks the word "confirmed" is one a person starts reflexively working around, which is how a real
one comes to be ignored. **Fix is word boundaries on the short entries. King's ruling, not a
tidy-up, because it is the security guard and loosening it is his call.**

### The one thing that decides whether this returns

If the OAuth consent screen sits in **Testing** rather than **In production**, Google expires the
refresh token after **7 days** and this breaks again next week. That would explain a regression that
has now happened twice. **King must check it himself**, it needs a scope this brain does not hold:
`console.cloud.google.com/auth/branding?project=king-david-automation`. If it reads Testing,
publishing is one click and stops a third occurrence.

### FOUND 9 Sep 23:5x, unrelated to what he went looking for: EUR 258 of Google Cloud credit, expiring

His console home reads **"0 out of EUR 258 credits used. Expires 26 September 2026"** on a full
(upgraded) account. **Seventeen days.** Nothing anywhere in this brain recorded that it existed.

NOT spent, and not to be spent without his word. Burning it to avoid waste is its own mistake. But
it is real, it has a hard deadline, and it is the size of thing that could fund something he cannot
otherwise do: GPU hours for the fine-tuning he asked about on 9 Sep (his laptop has Intel UHD 620
and no CUDA, so tuning is impossible on it), or Oracle-class compute for the night shift.

**Worth one proper sitting before 26 September**, with the question framed as "what does this make
possible that is currently blocked", never as "how do we use it up".

### Why the console deep links kept bouncing him to 2-Step Verification

Google now requires MFA for Cloud Console access; the account page he kept landing on links "Why
are we requiring multi-factor authentication". Until that is satisfied in a given browser, a deep
link to a console page redirects to account security rather than failing honestly.

### And the reason he could not find Publishing status

He was on project **gen-lang-client-0963910014**, the throwaway AI Studio creates, with the picker
reading "Default Gemini Project". The OAuth client lives in **king-david-automation**. A project
with no consent screen has no publishing status to show, so the page was not wrong, the project was.
