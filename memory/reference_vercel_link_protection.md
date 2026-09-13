---
name: reference-vercel-link-protection
description: "Vercel team deployments are login-walled by default → King's phone links are DEAD. Fix: turn off ssoProtection."
metadata: 
  node_type: memory
  type: reference
  originSessionId: 60aeae2b-6ab5-4c4d-8f38-6902f7392a47
---

# Vercel link protection · why King's "tap to watch" links were dead

**The trap (found 2026-06-26):** the Vercel CLI (authed as `kdagbidiloveschrist`) now deploys into the **team
`king-david-s-projects2`** ("King David's projects"), and that team has **Deployment Protection on by default**
(`ssoProtection: {deploymentType: "all_except_custom_domains"}`). So every `*.vercel.app` deploy URL **302-redirects
to a Vercel login** → King (and anyone) gets a login wall, NOT the content. Links sent to his phone silently fail;
he only ever saw the **email attachments**. This likely killed several past "tap to watch" deliveries.

**You CANNOT just deploy public anymore:** `vercel deploy --scope <personal>` errors with
*"You cannot set your Personal Account as the scope."* (the personal account isn't a usable scope now).

**THE FIX, turn off protection on the project via the API** (`VERCEL_TOKEN` is in `.env.master`):
```python
# GET team id by slug → PATCH the project's ssoProtection to null
teams = api("GET","https://api.vercel.com/v2/teams")                  # find slug king-david-s-projects2 → team_...
api("PATCH", f"https://api.vercel.com/v9/projects/{projId}?teamId={tid}", {"ssoProtection": None})
```
Then **re-deploy** (`vercel deploy --prod --yes`) and verify: `curl -s -o /dev/null -w "%{http_code}" <url>` and
`<url>/film.mp4` should both be **200** (not 302 to /sso). Protection is per-project, so set it once per new project.

**Always verify a delivery link is HTTP 200 BEFORE sending it to King.** An old public project still works:
`site-nine-tau-34.vercel.app` = 200. Related: [[reference-faith-narrated-video-engine]], [[feedback-always-send-gmail-and-link]].
