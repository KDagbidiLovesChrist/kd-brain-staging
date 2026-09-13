---
name: project-wat-newsletter
description: "AWS newsletter automation project, WAT framework, current build state, Phase 1 demo goals"
metadata: 
  node_type: memory
  type: project
  originSessionId: dd50c725-355b-46cf-a43e-1da1abd7e81c
---

Newsletter automation, FULLY LIVE 2026-05-17. All API keys configured.

**Status:** [LIVE ✅], Perplexity $50 credits loaded. Gmail password active. Anthropic key active. Ready to sell.

**Topic:** ANY topic (via Perplexity AI research), not just AWS. Pass topic as argument or via .tmp\newsletter_brief.txt.

**Content sources:**
- PRIMARY: Perplexity API (sonar model), researches any topic, returns structured stories
- FALLBACK: AWS RSS feeds (if no PERPLEXITY_API_KEY set)

**Folder:** `C:\Users\Dell\.claude\newsletter-demos\`
**Global skill:** `/newsletter` in `.claude\commands\newsletter.md`

**Full WAT chain:**
- `tools\fetch_perplexity.py`, T: Perplexity AI research → .tmp\articles.json
- `tools\fetch_rss.py`, T: fallback if no Perplexity key
- `tools\generate_newsletter.py`, T: Claude drafts copy
- `tools\generate_html.py`, T: builds HTML email
- `tools\send_gmail.py`, T: sends via Gmail SMTP
- `tools\run_newsletter.py`, master runner (updated to use fetch_perplexity)
- `tools\schedule_setup.py`, registers as Windows Task Scheduler job (Monday 8am)

**APIs used:** Anthropic API + Perplexity API + Gmail SMTP

**Before running:**
- Add `ANTHROPIC_API_KEY` to `.env`
- Add `PERPLEXITY_API_KEY` to `.env` (get from perplexity.ai/settings/api)
- Add `GMAIL_ADDRESS` + `GMAIL_APP_PASSWORD` to `.env`
- `pip install anthropic requests python-dotenv`

**Run with topic:** `python tools\run_newsletter.py agentic AI trends this week`

**Money:** €50, 200/month per client. Any niche, crypto, health, finance, local business.

**How to apply:** Run `python tools\run_newsletter.py` from the Newsletter Demos folder. Pass topic or it reads .tmp\newsletter_brief.txt.
