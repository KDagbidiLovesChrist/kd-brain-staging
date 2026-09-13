---
name: project-session-2026-05-23-install-sweep
description: Major install + signup + AIS absorption + Google CLI wire-up session. Loom batch paused at 30/88, resume TSV ready.
metadata: 
  node_type: memory
  type: project
  originSessionId: 3b0be448-832b-41ee-ab60-c78de43e5f61
---

# Session 2026-05-23 evening · Install Sweep + Google CLI

## Summary
Bun + ffmpeg + gh installed via winget. Newsletter Demos .env fixed. Phase 4 AIS absorption via 3 parallel agents → distilled to `knowledge\ais_master_summary.md`. ONBOARDING.md rewritten lean v7 (438 lines). CLAUDE.md drift fixed. Loom URL crawl + 88-video TSV built + batch ran to 30/88 then paused for clean home restart. Three third-party signups complete (ClickUp, Cal.com, Resend). Google CLI fully wired end-to-end across all 4 APIs.

## Resume Command (next session)
```powershell
cd C:\Users\Dell\.claude
python tools/transcript_extractor/loom_transcript.py --batch knowledge/ais_resources/transcripts/loom_batch_urls_resume.tsv
```

## Key Architecture Wins
1. **Google CLI gotcha:** Google now hides client_secret post-creation. Solution: intercept the create-client API response in Playwright's network log to capture `clientSecret` from `clientSecrets[0].clientSecret` field. Build `credentials.json` manually with all the standard fields (auth_uri, token_uri, etc.).
2. **OAuth in testing mode requires Test Users:** chip must be COMMITTED via Enter before Save click, otherwise email isn't added.
3. **Playwright + auto-OAuth flow:** the auth script can print the OAuth URL (with open_browser=False) → load URL in Playwright → drive through clicks → callback caught on localhost server → token.json written.

## Deferred by King David's Decision
- Premium AIS+ upgrade
- n8n paid plan
- GitHub PAT renewal (works until Jun 16 2026)
- Glaido extension install

## Resume Pointers
- Handoff: `handoffs\handoff_2026-05-23_18-00_save.md`
- AIS daily reference: `knowledge\ais_master_summary.md`
- Cluster reports: `knowledge\.tmp\absorb_cluster_*.md` + `absorb_audit_meta.md`
- Loom resume TSV: `knowledge\ais_resources\transcripts\loom_batch_urls_resume.tsv`
