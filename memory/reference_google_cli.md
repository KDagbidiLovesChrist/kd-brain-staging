---
name: reference-google-cli
description: "Step-by-step guide to setting up Google Cloud CLI and Google APIs. Unlocks Gmail API, Google Sheets, Drive, and Calendar for King David's automations and DCEO brain."
metadata: 
  node_type: memory
  type: reference
  originSessionId: 4b621969-d6bd-419c-9280-c6a4e0333ae8
---

# Google CLI & Google Cloud Setup · Step-by-Step Guide

## What This Unlocks

Once Google Cloud is set up, you get:
- **Gmail API**, send/read emails properly (better than SMTP, higher limits)
- **Google Sheets**, read/write data (archive newsletter stats, client tracking)
- **Google Drive**, sync files automatically (share DCEO brain with work laptop)
- **Google Calendar**, read your calendar in DCEO briefings
- **Google MCP**, Claude can interact with all of the above mid-session

---

## PLAIN ENGLISH EXPLANATION

Right now your newsletter sends via Gmail SMTP, like logging into Gmail through a
side door. It works but has limits and can break if Google updates security settings.

Google Cloud gives you the official front door. You register as a developer, tell Google
"I'm going to use my own Gmail account programmatically," Google gives you a credential file,
and your tools use that to send emails properly. More reliable. Higher limits. More capable.

---

## STEP 1: CREATE A GOOGLE ACCOUNT / USE EXISTING

You likely already have a Google account (Google = Gmail, Google Drive, YouTube, etc.)
Use your existing account or create one at accounts.google.com.

**Recommendation:** Use the same Google account linked to your Gmail (Kingdavidagb@gmail.com
or similar) so the APIs can access your actual email.

---

## STEP 2: CREATE A GOOGLE CLOUD PROJECT

1. Go to: **console.cloud.google.com**
2. Sign in with your Google account
3. Click the project dropdown at the top (says "Select a project")
4. Click **"New Project"**
5. Name it: `king-david-automation` (or anything you like)
6. Click **"Create"**
7. Wait ~30 seconds for it to be created
8. Make sure you're now inside that project (name shows at top)

---

## STEP 3: ENABLE THE APIS YOU NEED

Still in Google Cloud Console:
1. Click the hamburger menu (≡) → **APIs & Services** → **Library**
2. Search for and enable each of these:
   - **Gmail API** → click it → click "Enable"
   - **Google Sheets API** → click it → click "Enable"
   - **Google Drive API** → click it → click "Enable"
   - **Google Calendar API** → click it → click "Enable"
3. Each one takes about 10 seconds to enable

---

## STEP 4: CREATE CREDENTIALS

1. Go to: **APIs & Services** → **Credentials**
2. Click **"+ Create Credentials"** → **"OAuth client ID"**
3. First time: it will ask you to configure the OAuth consent screen
   - Click "Configure Consent Screen"
   - Select "External" → click "Create"
   - App name: `King David Automation`
   - User support email: your Gmail
   - Developer contact email: your Gmail
   - Click "Save and Continue" through the rest (leave scopes empty for now)
   - Click "Back to Dashboard"
4. Back on Credentials → "+ Create Credentials" → "OAuth client ID"
5. Application type: **Desktop app**
6. Name: `King David Desktop`
7. Click "Create"
8. A popup appears with your Client ID and Client Secret, click **"Download JSON"**
9. Save the file as `credentials.json`
10. Move it to: `C:\Users\Dell\.claude\credentials.json`

---

## STEP 5: INSTALL GOOGLE PYTHON LIBRARIES

In PowerShell or terminal:
```powershell
pip install google-auth google-auth-oauthlib google-auth-httplib2 google-api-python-client
```

---

## STEP 6: AUTHENTICATE (First Time Only)

Run this Python script once to generate your token:
```python
from google.auth.transport.requests import Request
from google.oauth2.credentials import Credentials
from google_auth_oauthlib.flow import InstalledAppFlow
import os

SCOPES = [
    'https://www.googleapis.com/auth/gmail.send',
    'https://www.googleapis.com/auth/spreadsheets',
    'https://www.googleapis.com/auth/drive.file',
    'https://www.googleapis.com/auth/calendar.readonly'
]

creds = None
if os.path.exists('token.json'):
    creds = Credentials.from_authorized_user_file('token.json', SCOPES)
if not creds or not creds.valid:
    flow = InstalledAppFlow.from_client_secrets_file('credentials.json', SCOPES)
    creds = flow.run_local_server(port=0)
    with open('token.json', 'w') as token:
        token.write(creds.to_json())

print("Authentication successful! token.json created.")
```

This opens a browser window → sign in with your Google account → grant permissions →
closes → `token.json` is created. This file is your authentication token, keep it safe.

Move `token.json` to: `C:\Users\Dell\.claude\token.json`

Add both files to .gitignore: `credentials.json` and `token.json`

---

## STEP 7: UPGRADE THE NEWSLETTER TO USE GMAIL API

Once authenticated, the newsletter's `send_gmail.py` can be upgraded from SMTP to the
proper Gmail API. Claude will do this automatically once you confirm the token is working.

**What changes:**
- Before: Simple SMTP (like a basic email client)
- After: Gmail API (official, more reliable, higher send limits, can read inbox too)

---

## STEP 8: CONNECT TO GOOGLE MCP (Optional)

Once credentials are set up, the Google MCP can be added to settings.json so Claude
can interact with Google services directly mid-session. Claude will help configure this
when you're ready.

---

## WHAT EACH GOOGLE SERVICE UNLOCKS

| Service | What King David Can Do With It |
|---------|-------------------------------|
| Gmail API | Send newsletters properly, read emails for DCEO brain |
| Google Sheets | Archive newsletter stats, client database, lead tracking |
| Google Drive | Sync DCEO brain between home PC and work laptop |
| Google Calendar | DCEO morning briefings include today's schedule |

---

## STATUS TRACKER

```
[ ] Step 1: Google account confirmed
[ ] Step 2: Google Cloud project created
[ ] Step 3: APIs enabled (Gmail, Sheets, Drive, Calendar)
[ ] Step 4: credentials.json downloaded and saved
[ ] Step 5: Python libraries installed
[ ] Step 6: token.json generated (authenticated)
[ ] Step 7: Newsletter upgraded to Gmail API
[ ] Step 8: Google MCP added to settings.json
```

When King David says "let's set up Google", start from the first unchecked step above.
