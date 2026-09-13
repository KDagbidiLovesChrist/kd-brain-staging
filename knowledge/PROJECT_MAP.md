# Where everything actually lives

*Built 2026-08-23 during the restructure. The problem this solves: several projects answer to
two or three different names, and two folder pairs look like duplicates but are not. Nothing was
moved to fix that, because code and docs reference these paths by name and a tidy rename would
break working things for no gain. This file is the map instead.*

## The alias table (one project, several names)

| You might call it | It actually lives at | Notes |
|---|---|---|
| Hook Engine · Faceless Hook Engine · Content Engine | `.claude\proof-engine\content-engine\` | ONE project. "Hook Engine" is the **product** (EUR 19 on Payhip); "content-engine" is the folder that sells it. 154 files. |
| Faceless Engine · the @30Kingdavid channel | `.claude\faceless-content-engine\` | A **different** project from the above. Easy to confuse, they are not related. |
| UGC Studio · King David Studio · @30kingdavidstudio | split across three folders, see below | One business, three artifact types. |
| Website Builder · the website sales engine | `OneDrive\Documents\Website Builder\` | The real business, 9,494 files. |
| Scrapers · Scrapers - Copy | `.claude\scrapers\` | Moved into the brain. The OneDrive folders are `MOVED.md` stubs. |

## The UGC split (deliberately three folders, do not merge)

| Folder | What it is | Why it stays put |
|---|---|---|
| `.claude\ugc-studio\` | Marketplace listing prep (rate card, platform profiles). 3 text files. | Referenced by `tools\brainify.py` (code), `commands\aide.md`, `_ops\REVENUE_QUEUE.md`, `_ops\SESSION_SYNC.md`. Moving it breaks a script silently. |
| `.claude\proof-engine\ugc-ads\` | Ad production: storyboards, voiceover, b-roll, the Revolut ad. 107 files, mostly media. | Large binaries; nothing gained by moving. |
| `.claude\proof-engine\ugc-portfolio\` | The **live** portfolio site (ugc-portfolio-peach.vercel.app). | Contains `.vercel\`. **Moving it breaks the deployment.** |

⚠️ **Open decision, flagged by the files themselves, still unanswered:** `ugc-studio\RATE_CARD.md`
prices a video at **USD 100** as a marketplace entry rate, while `proof-engine\UGC_RATE_CARD.md`
(earlier, 8+ sources) locks **USD 250 to 300** and warns that 50 to 100 "signals amateur to SaaS
buyers". Both are honest positions. Nothing can be listed until King picks one.

## The two pairs that look like duplicates and are not

**Website Builder.** `OneDrive\Documents\Website Builder\` is the business: client sites, demos,
deploy tooling, 9,494 files. `.claude\website-builder\` (19 files) is a deliberate **phone mirror
of the docs only**; its own `_BRAIN_MIRROR.md` says "This is NOT the full project." Keep both.
Do not treat the small one as a stale copy to delete.

**DCEO.** `.claude\DCEO_BRAIN\` is the maintained brain (persona, knowledge, commands). `OneDrive\
DCEO_Brain\` is a thin **staging folder** whose job is carrying deployable Slack-bot code to the
work laptop over OneDrive sync. Different jobs. The Slack bot appears in both on purpose: the copy
in `.claude` is explicitly archived and frozen, the OneDrive one is the live deployable.

## Fixed on 2026-08-23 while mapping this

- `WEBSITE_SALES_WORKFLOW.md` told the reader to run scripts from `Scrapers - Copy\tools\`, which
  is now a `MOVED.md` stub. Five references rewritten to `.claude\scrapers\tools\`. Following the
  SOP literally would have failed at step 1.
- The same file carried a stale Vercel account (`kinglovesjessie`); corrected to
  `kdagbidiloveschrist`, which the phone mirror had right and the real project did not.

## Related

`knowledge\SKILL_SYSTEMS_EXPLAINED.md` does the same job for `commands\` vs `skills\` vs
`skill-forge\`. `memory\ACTIVE_PROJECTS.md` holds status; this file holds location.
