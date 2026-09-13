# Tools Connected (moved from CLAUDE.md 2026-07-04 reorg)

## Tools Connected
| Tool | What It Does | Status |
|------|-------------|--------|
| **Token Dashboard (Nate Herk)** | Local Claude Code token analytics · Overview/Prompts/Sessions/Projects/Skills/Tips/Settings. 7-tab UI at 127.0.0.1:8080 | ✅ Installed 2026-05-23 · `cd .claude\tools\token-dashboard && python cli.py dashboard` to launch |
| **YouTube Transcript Extractor** | Extract YouTube transcripts as markdown for AIS+ classroom audit (most lessons are videos). `python tools\transcript_extractor\extract_youtube_transcript.py <url>` | ✅ Built 2026-05-23 |
| **n8n-mcp** | 1,650 n8n nodes + 2,352 workflow templates accessible in Claude Code | ✅ Added to settings.json 2026-05-23 · **requires Claude Code restart to activate** |
| Firecrawl MCP | Scrape any website, search, extract | Active |
| Playwright MCP | Control real browser · click, fill, navigate | Active |
| Anthropic API | Claude reasoning + content generation | Active |
| Gmail SMTP (`tools\send_file_smtp.py`, raw app-password login) | Newsletter delivery | ❌ BROKEN 2026-08-01 · `GMAIL_APP_PASSWORD` in `.env.master` now fails login (535 Bad Credentials). **Use the OAuth path instead**: `token.json` + `google-auth`/`googleapiclient`, pattern in `tools\send_olly_to_yahoo.py`, confirmed working 2026-08-01 for sending to a third-party address with an attachment. |
| Perplexity API | Deep web research on any topic | ✅ Active · $50 credits loaded |
| Vercel CLI | Deploy websites for free | ✅ Installed v54.1.0, authed as kdagbidiloveschrist |
| n8n (local app) | Visual workflow builder UI on localhost:5678 | ✅ Installed v2.20.9 (2026-05-23 verified) |
| Ollama | Local LLM runner (Llama/Mistral on your machine) | ✅ Installed · **v0.33.2 as of 2026-09-08** (this row said v0.24.0 from 2026-05-23; corrected 9 Sep, it had gone stale and contradicted the harness table below). Models: qwen3:8b, llama3.2 3b and 1b, nomic-embed. |
| Bun | Fast JS runtime | ✅ Installed 2026-05-23 (PATH refresh on next CC restart) |
| ffmpeg (system-wide) | Audio/video codec · backbone of transcript pipeline | ✅ Installed via winget 2026-05-23 |
| gh (GitHub CLI) | Clean GitHub PAT renewal + repo ops | ✅ Installed via winget 2026-05-23 |
| GitHub | Version control + the `kd-brain` private repo (brain→phone) + Vercel deploys | ✅ **2026-06-16: `.claude` is a git repo → private `KDagbidiLovesChrist/kd-brain`.** Auth = a **PAT (repo scope)** in `C:\Users\Dell\.git-credentials` (works for git push/pull; NOT for `gh` CLI which needs `read:org`). Auto-sync via `KD_Brain_Sync` task. See `memory\project_brain_on_github_phone.md`. (gh CLI still NOT logged in; use git directly or the API.) |
| Claude Code Routines | Schedule automations 24/7 in the cloud · FREE | Built-in ✅ |
| Claude Agent SDK | Build agents programmatically · Haiku/Sonnet/Opus | Active · /claude-api skill |
| Brave Search MCP | ~~Web search inside Claude sessions~~ | ❌ REMOVED 2026-06-16 · had a broken placeholder key; search is covered by Firecrawl MCP + Perplexity + built-in WebSearch. Re-add only if needed. |
| Google CLI (Gmail + Sheets + Drive + Calendar APIs) | All 4 enabled in project `king-david-automation` · token at `.claude\token.json`, credentials at `.claude\credentials.json`, helper at `tools\google_auth.py` + checker `tools\google_check.py` (`google_test.py` never existed on disk, stale doc reference fixed 2026-07-26) | ⚠️ SCOPES REGRESSED 2026-07-31, RE-CONFIRMED STILL BROKEN 2026-09-06 (the separate 07-26 "invalid_grant, dead token" incident was already fixed 07-30, that old description is stale). Live check tonight: only Gmail read+send OPEN, Calendar/Sheets/Drive scopes still missing, root cause unchanged (a Gmail-only re-consent overwrote the 5-scope grant, app still in Testing mode). Fix: King re-runs the Google auth helper once. Permanent fix: set OAuth consent screen to "In production" in Cloud console, or it regresses again. See `memory\project_connect_everything.md`. |
| kie.ai (Nano Banana) | Excalidraw-style PNG image generation · `KIE_AI_API_KEY` · script: `commands\get-kie-image.py` | ✅ Key loaded in `.env.master` + `.claude\.env` (2026-05-23) |
| **MuAPI** (muapi.ai · gen-AI gateway) | Unified "one key, 200+ models" (Seedance/Kling/Veo/Flux/Nano Banana). `MUAPI_API_KEY` in `.env.master`. Used by the **cost router** `tools\gen_router.py` (quotes MuAPI + Gemini/Veo + kie.ai, runs cheapest). Live-tested OK. | ✅ LIVE 2026-06-26 · $9.58 bal; pay-as-you-go (top-ups via /money). See `memory\reference_muapi_cost_router.md` |
| **Supabase** (Postgres + Auth + RLS) | Production DB + auth for `/lead_qualifier_app`, client RAG agents. Project `king-david-prod` in eu-west-1. Both new (publishable/secret) AND legacy (anon/service_role) keys in `.env.master`. | ✅ LIVE 2026-05-25 · verified HTTP 200 |
| **Cal.com** (booking automation) | Booking page at cal.com/kingdavid · Google Calendar auto-connected · v2 API only (v1 decommissioned). For plumber pitch + voice agent flow. | ✅ LIVE 2026-05-25 · `CALCOM_API_KEY` in `.env.master`, verified v2/me |
| **Apify** (web scraping fallback) | Pre-built actors for sites Firecrawl can't crack (LinkedIn, Twitter, paywalls). $5/mo free credit + residential proxies. Use `apify/cheerio-scraper` first (cheap), `apify/web-scraper` for JS-heavy. | ✅ LIVE 2026-05-25 · token + proxy pw in `.env.master`, verified v2/users/me |
| **Bitwarden** (password manager) | King's encrypted vault for ALL passwords + the **BitLocker recovery key** (copy #2). Free tier; web + iPhone. Master password is **zero-knowledge** (not recoverable · guard it). | ✅ LIVE 2026-06-30 · vault created. NEXT = trusted-circle **Emergency Access** (Fr Bogdan + Joshua; may need Premium ~$10/yr → gate via `/money`) |
| **PreCompact auto-save hook** | `tools\precompact_save.py` · fires before every context compaction → secret-scrubbed recovery anchor to SYNCED `memory\AUTO_RECOVERY_LATEST.md` (reaches phone) + full transcript backup laptop-only. King never manually `/save`s. | ✅ LIVE 2026-06-30 · wired in `settings.json`, QA'd 8 stages, scrubber hardened 106/111 |
| **Browser Door** (`tools\browser_door.py`) | ONE tool for every app with no friendly API: WhatsApp Web · Payhip dashboard · LinkedIn · X · Instagram · Amazon orders. Persistent Chrome profile per site in `.claude\browser_profiles\` (git-ignored by default-deny). READ + DRAFT only, never sends/posts/buys. `login <site>` once (King's hands), then any session can `check <site>`. | ✅ BUILT + smoke-tested 2026-07-26 (WhatsApp QR page + Amazon sign-in both detected correctly). Logins pending King. See `memory\project_connect_everything.md` |
| **Payhip sale alerts** (webhook → ntfy) | Payhip Settings → Developer → webhook (event `paid`) POSTs straight to the ntfy topic → instant phone push, laptop can be OFF. Public API = coupons/licenses only (no sales endpoint), so on-demand checks = `tools\payhip_check.py` (browser door). | ✅ Alert path PROVEN 2026-07-26 (test push delivered, title "PAYHIP SALE"). Hand-step: King pastes the webhook URL (in `memory\project_connect_everything.md`) |
| **Social stats** (`tools\social_stats.py`) | King's own accounts' numbers, read-only: TikTok + Instagram + X via Apify (free credit) · YouTube via YOUTUBE_API_KEY when added. Feeds ROI tracker + Faceless/UGC engines. | ✅ LIVE 2026-07-26 · real pull: TikTok @30kingdavid = 7 followers/102 likes. @30kingdavidstudio returned nothing (handle unconfirmed). IG/X/YT handles = SET-ME in the file |
| **WhatsApp chat reader** (`tools\whatsapp_read_chat.py`) | Opens a named contact's chat on the existing `whatsapp` browser-door profile, dumps the recent message text, and downloads any document/PDF/docx attachments to `browser_profiles\_downloads\`. READ-ONLY, no typing or sending. | ✅ BUILT + used live 2026-08-01 (pulled Whitney's housing form). Usage: `python tools\whatsapp_read_chat.py "<contact name>"`, search by the contact's exact WhatsApp display name, not necessarily their real name |

## AI harnesses and model providers (the doors) · inventoried 2026-09-08
Full detail, faults and the door ladder: `knowledge\HARNESS_MAP_2026-09-08.md`.
**A model thinks; a harness has the hands.** A model running out is fixed by the engine's router
automatically; a harness running out is fixed by push, open the next door, pull.

| Door / provider | What it is | Status 2026-09-08 |
|---|---|---|
| **Claude Code** 2.1.263 | CLI + VS Code extension + desktop app. Claude models only. | ✅ INSTALLED, in daily use. **NOT routed through ccr** (no base URL override), so plain `claude` spends the Claude plan directly. The chair, legal and terminal coding live here. |
| **ccr** (claude-code-router) 2.0.0 | A gateway on `127.0.0.1:3456` that lets Claude Code use other models. Run it with `ccr code`. | ⚠️ RUNNING BUT UNUSED, and **its default routes are DEAD**: `gemini-2.0-flash` (shut down) and `gemini-1.5-pro` (gone). Fix before relying on it. King's 8 Sep ruling: **this becomes the everyday door**, free lanes. |
| **Antigravity** (Google) | Agentic IDE. Gemini 3.x, plus Claude Sonnet/Opus 4.6 and Nano Banana 2. | ✅ INSTALLED TWICE (2.12.2 app, 2.5.5 IDE). Account and plan unrecorded. Quota visible in-app only; its `agy` CLI is not installed. |
| **Codex** (OpenAI) 0.153.4 | GPT coding agent. Configured **`gpt-6-astra`** (corrected 9 Sep from a misread of `gpt-5.6-sol`). | ⚠️ Binary present, **NOT on PATH**. Runs pay as you go (`auth_mode = apikey`) at **`xhigh` effort with no cap**: the only uncapped lane, and on Astra at 10 and 50 USD per million rather than Sol's 4 and 20. King ruled 8 Sep: **cap the account and drop the effort first**, then judge a paid plan on a week of real numbers. |
| **Copilot CLI** 1.0.81 | Claude, GPT, Gemini, Grok and Kimi under one GitHub login, per plan. | ⚠️ INSTALLED, **plan unknown**, nothing in the brain records one. Usage IS readable by script if a plan exists. Worth checking: it may be a multi-model door already owned. |
| **Ollama** 0.33.2 | Local models: qwen3:8b, llama3.2 3b and 1b, nomic-embed. | ✅ LIVE. Rung one of every lane. Faith, private work and anything carrying his notes stop here by rule. Free, and cannot run out. |
| **Gemini CLI / Hermes Agent / `agy` / Cursor** | Terminal doors not yet installed. | ❌ NOT INSTALLED. Gemini CLI and Hermes are planned (Stage J); Hermes points at Ollama and is free. |
| **Kiro** (AWS) | Agentic IDE, Claude and GPT-5.6 and GLM, no Fable or Astra. | ⛔ WORK LAPTOP ONLY (King's 8 Sep ruling) and parked. There it must sign in with IAM Identity Center or the internal IdP, never a GitHub or social login, and Amazon's SOP policy is read before any file is loaded. |
| **OpenRouter / NVIDIA NIM / DeepSeek / Gemini API** | Model providers behind the router and ccr. | ✅ Keys present by name. OpenRouter free tier is the cheap lane; its credit is the one balance a script can actually read. |

---

