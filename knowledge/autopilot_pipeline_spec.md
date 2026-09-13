# Built with AI · Autopilot Pipeline Spec

**Owner:** King David Agbidi
**Project:** Built with AI (faceless YouTube + newsletter + Twitter)
**Spec written:** 2026-05-26 evening (post 12:30pm strategy lock)
**Implements:** Sessions 1, 3 build, Wed 2026-05-27 onward
**Status:** Contract v1.1, revised 2026-05-26 evening after research findings (`knowledge\autopilot_research_findings.md`) landed. Key shifts: Remotion locked as renderer, Whisper+ffmpeg for captions in Phase 1, Twitter API moved to pay-per-use, Submagic deferred to Phase 3 only.

---

## 1. Purpose + Success Criteria

The pipeline produces and ships **one 10-minute long-form YouTube video plus its full multi-channel repurpose pack (newsletter, Twitter thread, Shorts) every week, with zero King David input after one-time setup**. King David's lifetime actions for this system are: (a) sign up to the listed tools once, (b) record one 3-min voice sample once into ElevenLabs, (c) keep the subscription cards on file. After that, he leaves.

Claude does everything else autonomously on a cron schedule: topic research, scripting, voice generation, video assembly, captions, thumbnail design, upload, scheduling, newsletter dispatch, Twitter thread post. King David receives one weekly status email confirming the video shipped (or one error email if a step failed, with a one-line fix path).

### Quantified success criteria

| Metric | Target | How measured |
|---|---|---|
| Video output cadence | ≥ 1 long-form video / week | YouTube Studio publish log |
| King David active time / video (post-setup) | 0 minutes | Self-attested |
| Claude compute time / video (end-to-end) | ≤ 2 hours wall clock | Orchestrator log timestamps |
| Variable cost / video | ≤ €8 | Sum of API spend per `outputs\runs\<ts>\cost.json` |
| Monthly fixed running cost | ≤ €60/mo | Sum of subscription line items |
| Failure rate | ≤ 1 step failure / 4 runs | Orchestrator error log |
| Notification reliability | 100% · every failure emails King David | Sentry-style send-on-fail |

---

## 2. Pipeline Architecture · 6 Steps

### Step 1 · Topic Research

| Field | Value |
|---|---|
| **Input** | Position in 12-video calendar (`built_with_ai_brand.md` row N), prior run dir |
| **Agent/tool** | `tools\topic_research_agent.py` · Claude Sonnet 4.5 reasoning + Perplexity API search + YouTube transcript scan (top 3 competing videos) + Reddit hot-topic scrape (r/sidehustle, r/AIsidehustle, r/Entrepreneur) |
| **Output** | `outputs\runs\<ts>\01_topic_brief.md` · chosen title, 3 backup titles, 5 supporting data points with source URLs, target keywords (8-15), thumbnail concept brief, key hook sentence |
| **Failure handling** | If Perplexity 429 → retry 3× w/ exp backoff → fall back to Brave Search MCP. If both fail → email + stop. |
| **Cost / run** | ~€0.40 (Perplexity ~€0.20 + Claude ~€0.20) |
| **API used** | Perplexity `sonar-pro`, Anthropic Claude Sonnet 4.5, Brave Search MCP (fallback), YouTube Data API v3 (transcript hop via `extract_youtube_transcript.py`) |

### Step 2 · Script Generation

| Field | Value |
|---|---|
| **Input** | `01_topic_brief.md` + `prompts\script_prompt.md` + brand voice cheat sheet (`built_with_ai_brand_kit.md` §9) + Video #1 reference structure (`video_01_full_package.md`) |
| **Agent/tool** | `tools\script_generator.py` · Claude Opus 4.7 (highest-quality voice match) with prompt caching on brand voice block |
| **Output** | `outputs\runs\<ts>\02_script.md` (human-readable) **+ `02_script.json` (beat schema · hook, problem, stat, insight, solution, CTA · each beat carries text + duration + B-roll keywords)** following the locked 6-section structure (Cold Open, Hook, Story Setup, Body, Real Talk, CTA). Beat schema enables Remotion auto-timing in Step 4 (pattern from Tim McAllister 2026-03-28). |
| **Failure handling** | Word count enforcement: <1,500 or >1,900 → auto-regen once. Voice-check pass (no em-dashes, no "delve/leverage/landscape") via regex linter → fail = regen once. |
| **Cost / run** | ~€0.80 (Opus with caching, ~6k input cached + 2k output) |
| **API used** | Anthropic Claude Opus 4.7 |

### Step 3 · Voice Generation

| Field | Value |
|---|---|
| **Input** | `02_script.md` (voice-over text only, stripped of stage directions) |
| **Agent/tool** | `tools\voice_generator.py` · ElevenLabs API, King David's cloned Irish voice (voice_id stored in `.env.master` as `ELEVENLABS_KD_VOICE_ID`) |
| **Output** | `outputs\runs\<ts>\03_voice.mp3` (single file, 44.1kHz, mono) + `03_voice.json` (duration, char count, cost) |
| **Failure handling** | If ElevenLabs 5xx → retry 2× → email + stop. If character quota exceeded → email "ElevenLabs quota hit, upgrade or wait reset". |
| **Cost / run** | ~€2.00 (~9k chars × ElevenLabs Creator rate) |
| **API used** | ElevenLabs TTS v1 `/text-to-speech/{voice_id}` |

### Step 4 · Video Generation

| Field | Value |
|---|---|
| **Input** | `03_voice.mp3` + B-roll keyword list parsed from `02_script.md` + thumbnail brief from `01_topic_brief.md` |
| **Agent/tool** | `tools\video_generator.py` · **Locked path (Phase 1+):** **Remotion** (React-based code-driven renderer, free, 2026 Claude-first consensus per MindStudio + Blotato + Tim McAllister) consumes `02_script.json` beat schema + Pexels B-roll + voice MP3 → renders 1080p MP4 via `npx remotion render`. **HeyGen ruled OUT** · free API tier killed Feb 2026, can't enrol on old plans, and BUILT WITH AI niche (case studies with screenshots) needs no avatar. |
| **Output** | `outputs\runs\<ts>\04_video_raw.mp4` (1080p, voice baked in, B-roll cut every 3-5 sec per beat, no captions yet) |
| **Failure handling** | If <8 min duration → log + email (script too short). If Pexels returns <10 clips for any keyword → fall back to generic "AI / tech / desk" stock pool. Remotion render fail → check Node version + ffmpeg presence → email. |
| **Cost / run** | ~€0 · Remotion + ffmpeg + Pexels all free. |
| **API used** | Remotion (local, **pin to ≥4.0.442 or <4.0.439** · loader-utils CVE in 4.0.439-441), Pexels API (free, registered), ffmpeg (local). **Exclude `@remotion/mcp` package** · unauthenticated external calls. |

### Step 5 · Captions + Polish

| Field | Value |
|---|---|
| **Input** | `04_video_raw.mp4` |
| **Agent/tool** | `tools\caption_polisher.py` · **Phase 1 default: Whisper (local) + ffmpeg subtitle burn-in.** Free. No SFX. Submagic deferred to Phase 3 (after first €500/mo) because its API requires $41/mo Business plan + $0.69/min · not viable until revenue. |
| **Output** | `outputs\runs\<ts>\05_video_final.mp4` (1080p, captions burned) |
| **Failure handling** | Whisper transcription fail → log + email. `ffmpeg amix` filter MUST specify `normalize=0` or output silences (research gotcha). |
| **Cost / run** | €0 Phase 1 (Whisper local + ffmpeg local). Phase 3 upgrade: ~€7/run via Submagic ($41/mo plan + $0.69/min × 10 min). |
| **API used** | OpenAI Whisper (local), ffmpeg (local). Submagic API only from Phase 3. |

### Step 6 · Multi-channel Publish

| Field | Value |
|---|---|
| **Input** | `05_video_final.mp4` + `01_topic_brief.md` (title/desc/tags) + `02_script.md` (for newsletter/Twitter repurpose) |
| **Agent/tool** | `tools\publisher.py` · calls 4 helpers in parallel: `youtube_api.py` (upload + schedule), `buttondown_api.py` (newsletter send · pending Buttondown approval), `twitter_playwright.py` (Playwright browser automation against logged-in session in Phase 1; switch to paid API when revenue ≥ $50/mo), thumbnail generator (kie.ai Nano Banana via `commands\get-kie-image.py`) |
| **Output** | `outputs\runs\<ts>\06_publish_receipts.json` (YouTube video_id + URL, newsletter send_id, tweet_id, thumbnail_url) |
| **Failure handling** | Each channel isolated · one failure does NOT block others. Failed channel = email with retry command. YouTube quota check before upload (**big win: video uploads dropped from 1,600 → 100 units/call on 2025-12-04 = 100 uploads/day on free tier, no quota anxiety**). **HARD RULE: YouTube upload payload MUST set `selfDeclaredMadeForKids=false` AND tick "Altered or Synthetic Content" field · missing = permanent ad-rev ban. Never skip.** |
| **Cost / run** | ~€0.15 (kie.ai €0.10 thumbnail + ~€0.05 Twitter at $0.01 × ~5 posts/thread). YouTube + Buttondown free at this volume. |
| **API used** | YouTube Data API v3 (OAuth, scope `youtube.upload`), Buttondown API v1, **Twitter API v2 pay-per-use** ($0.01/post created · free tier dead for new devs since Feb 2026), kie.ai Nano Banana |

### Per-video total cost rollup (revised post-research)

| Step | Cost |
|---|---|
| 1. Topic research | €0.40 |
| 2. Script | €0.80 |
| 3. Voice | €2.00 |
| 4. Video (Remotion + Pexels + ffmpeg) | €0.00 |
| 5. Captions (Whisper + ffmpeg) | €0.00 |
| 6. Publish (kie.ai thumbnail + Twitter pay-per-use) | €0.15 |
| **Variable / video** | **€3.35** |
| Fixed subs / month (4 vids) Phase 1 | €33 → ~€8.25 / vid |
| **Total / video Phase 1** | **~€11.60** (well under €60/mo cap @ 4 vids/mo) |

Research-validated benchmark: Tim McAllister + MindStudio confirm $0.55-$3.60 API cost per video for similar Claude-first pipelines. Our €3.35 lands inside that range.

---

## 3. Cross-cutting Concerns

### 3.1 Scheduling

| Item | Value |
|---|---|
| **Cron platform** | Claude Code Routines (cloud, free, already wired per CLAUDE.md) |
| **Schedule** | Saturday 20:00 Europe/Dublin · runs full pipeline overnight, video lands on YouTube draft Sunday morning, **scheduled-publish for Tuesday 09:00 as the DEFAULT, but day/time can flex** (Mon/Wed equally fine). Posting day flexes as analytics_puller surfaces peak-audience windows per KD's specific viewers. Saturday cron is the BUILD trigger; publish time is a separate decision. |
| **Why not Sunday** | Faith filter · Sunday is rest day per CLAUDE.md. Pipeline must complete by Saturday EOD. |
| **Manual trigger** | `/autopilot` skill (see §4) · runs the same pipeline ad-hoc |

### 3.2 Logging + Shared State

Per the 2026 Claude-first consensus (MindStudio manifest.json pattern + Tim McAllister beat schema), one JSON file is the single source of truth across steps. Numbered intermediate files for predictable debugging.

```
C:\Users\Dell\Documents\Built With AI\outputs\runs\<YYYY-MM-DD_HH-MM>\
├── manifest.json           # SHARED STATE, every step reads/writes here
├── 00_run.log              # stdout + stderr from orchestrator, all 6 steps
├── 00_state.json           # which steps completed (for idempotent rerun)
├── 01_topic_brief.md
├── 02_script.md            # human-readable script
├── 02_script.json          # beat schema (hook/problem/stat/insight/solution/CTA)
├── 03_voice.mp3 + 03_voice.json
├── 04_video_raw.mp4
├── 05_video_final.mp4
├── 06_publish_receipts.json
└── cost.json               # rollup of per-API spend for this run
```

### 3.3 Error handling

| Rule | Detail |
|---|---|
| **No silent failures** | Every step wraps its work in try/except. On exception → write traceback to `00_run.log`, write step status to `00_state.json`, send email via Gmail API to `Kingdavidagb@icloud.com` with subject `[Built with AI] Run <ts> failed at step <N>` and body containing the run dir path + traceback. |
| **Email helper** | `tools\helpers\notify.py` · wraps existing Gmail OAuth token at `C:\Users\Dell\.claude\token.json`. |
| **Severity levels** | `INFO` (step complete), `WARN` (fallback used, run continues), `ERROR` (run stopped, email sent), `FATAL` (orchestrator crashed, email sent). |
| **No retries beyond what each step defines** | Orchestrator does not retry whole pipeline · King David / human runs `/autopilot --resume <run_dir>` |

### 3.4 Cost monitoring

| Item | Detail |
|---|---|
| **Per-run rollup** | Each helper writes its spend to `cost.json` keyed by `api_name → eur_amount` |
| **Weekly status email** | Sundays 09:00 Europe/Dublin — `tools\weekly_status.py` runs, reads last 7 days of `cost.json`, sums API spend, pulls subscription totals from `.env.master` ledger, sends one summary email |
| **Budget alert** | If month-to-date variable spend > €40 → email `[Built with AI] Budget alert: €XX of €60 cap used` |

### 3.5 Secrets

| Item | Detail |
|---|---|
| **Master file** | `C:\Users\Dell\.claude\.env.master` (already exists per CLAUDE.md, holds Anthropic, Perplexity, Gmail, Brave, Supabase, Cal.com, Apify, kie.ai keys) |
| **Project file** | `C:\Users\Dell\Documents\Built With AI\.env` · symlink or local copy. Loaded via `python-dotenv`. |
| **Never hardcoded** | All `tools\*.py` read keys via `os.getenv()`. CI lint check `grep -rE "sk-[a-zA-Z0-9]{20,}" tools\` rejects commits. |
| **New keys to add** (this project) | `ELEVENLABS_API_KEY`, `ELEVENLABS_KD_VOICE_ID`, `PEXELS_API_KEY`, `BUTTONDOWN_API_KEY`, `TWITTER_BEARER_TOKEN`, `TWITTER_ACCESS_TOKEN`, `TWITTER_ACCESS_SECRET`, `TWITTER_API_KEY`, `TWITTER_API_SECRET`, `YOUTUBE_CLIENT_ID`, `YOUTUBE_CLIENT_SECRET`, `YOUTUBE_REFRESH_TOKEN`. **HeyGen + Submagic deferred to Phase 3 · no keys yet.** |

### 3.6 Idempotency

| Rule | Detail |
|---|---|
| **State file** | `00_state.json` written after every successful step: `{"step": 3, "status": "complete", "output": "03_voice.mp3"}` |
| **Resume command** | `python tools\pipeline_orchestrator.py --resume outputs\runs\2026-06-01_20-00` · reads `00_state.json`, starts at step N+1, reuses prior outputs |
| **Step purity** | Each step function signature is `def run(run_dir: Path, ctx: dict) -> dict` · pure with respect to `run_dir`, no global state. Re-running step N overwrites only its own outputs. |

---

## 4. Project File Layout

```
C:\Users\Dell\Documents\Built With AI\
├── CLAUDE.md                              # project brain, references master
├── .env                                    # local copy of secrets
├── .env.template                           # checked-in, keys-only no values
├── README.md                               # 50-line orientation
├── prompts\
│   ├── topic_research_prompt.md            # system prompt for step 1
│   ├── script_prompt.md                    # system prompt for step 2 (caches brand voice)
│   ├── thumbnail_prompt.md                 # kie.ai prompt template (Cash Yellow + Black)
│   └── newsletter_prompt.md                # script → 820w newsletter conversion
├── tools\
│   ├── topic_research_agent.py             # step 1
│   ├── script_generator.py                 # step 2
│   ├── voice_generator.py                  # step 3
│   ├── video_generator.py                  # step 4 (Path A default, Path B flag)
│   ├── caption_polisher.py                 # step 5
│   ├── publisher.py                        # step 6 (orchestrates 4 helpers)
│   ├── pipeline_orchestrator.py            # main entrypoint, runs steps 1→6
│   ├── weekly_status.py                    # Sunday email
│   └── helpers\
│       ├── notify.py                       # Gmail-based email alerts
│       ├── youtube_api.py                  # OAuth wrapper + upload + schedule
│       ├── elevenlabs_api.py
│       ├── heygen_api.py                   # Phase 2 only
│       ├── pexels_api.py
│       ├── buttondown_api.py
│       ├── twitter_api.py
│       ├── kie_thumbnail.py                # wraps existing get-kie-image.py
│       ├── ffmpeg_stitcher.py              # B-roll + voice concat for Path A
│       └── cost_tracker.py                 # appends to cost.json
├── outputs\
│   └── runs\
│       └── <YYYY-MM-DD_HH-MM>\             # one dir per run
├── tests\
│   ├── test_topic_research.py
│   ├── test_script_generator.py
│   ├── test_voice_generator.py
│   ├── test_video_generator.py
│   ├── test_orchestrator.py
│   └── fixtures\
└── C:\Users\Dell\.claude\commands\autopilot.md   # the /autopilot skill
```

### Key function signatures (locked)

```python
# pipeline_orchestrator.py
def main(resume: Path | None = None, dry_run: bool = False) -> int

# each step
def run(run_dir: Path, ctx: dict) -> dict   # ctx flows step-to-step

# helpers\notify.py
def send_alert(subject: str, body: str, severity: str = "ERROR") -> None

# helpers\cost_tracker.py
def record(run_dir: Path, api: str, eur: float) -> None
```

---

## 5. API + Key Map

| API | Key name(s) in `.env.master` | Status | Fixed €/mo | Variable € | Where used |
|---|---|---|---|---|---|
| Anthropic (Claude Opus + Sonnet) | `ANTHROPIC_API_KEY` | ACTIVE | €0 (PAYG) | ~€1.20/run | Step 1, 2, weekly status |
| Perplexity | `PERPLEXITY_API_KEY` | ACTIVE (€50 credit loaded) | €0 (PAYG) | ~€0.20/run | Step 1 |
| Brave Search | `BRAVE_SEARCH_API_KEY` | ACTIVE | €0 (free tier) | €0 | Step 1 fallback |
| YouTube Data API v3 | `YOUTUBE_CLIENT_ID`, `YOUTUBE_CLIENT_SECRET`, `YOUTUBE_REFRESH_TOKEN` | PENDING signup (existing Google project `king-david-automation`) | €0 | €0 (10k units/day free) | Step 1 (competitor scan), Step 6 (upload) |
| ElevenLabs | `ELEVENLABS_API_KEY`, `ELEVENLABS_KD_VOICE_ID` | PENDING · Wed signup ($22/mo Creator = 100k credits, enough for 4 × 10-min videos/mo) | €22 | included | Step 3 |
| Pexels | `PEXELS_API_KEY` | PENDING signup (free, 200 req/hr) | €0 | €0 | Step 4 |
| Remotion (renderer) | n/a (local npm package, **pin ≥4.0.442 or <4.0.439**) | PENDING · Wed `npm install remotion` | €0 | €0 | Step 4 |
| Buttondown | `BUTTONDOWN_API_KEY` | PENDING signup (free <100 subs, $9/mo after) | €0 → €9 | €0 | Step 6 |
| Twitter / X | **Playwright browser automation (no API)** in Phase 1 · uses logged-in session via `/browser` skill. Switch to paid API ($0.01/post pay-per-use) only when monthly revenue clears $50. | €0 (Playwright local) | €0 Phase 1 / ~$0.05/video Phase 2 | Step 6 |
| Gmail API (notify) | `token.json` at `.claude\token.json` | ACTIVE | €0 | €0 | All steps (email alerts) |
| kie.ai (thumbnail) | `KIE_AI_API_KEY` | ACTIVE | €0 (PAYG) | ~€0.10/run | Step 6 |
| ~~HeyGen~~ | · | **RULED OUT** · free tier dead Feb 2026, niche needs no avatar | · | · | · |
| ~~Submagic~~ | · | **DEFERRED to Phase 3** · needs $41/mo Business + $0.69/min | · | · | · |

**Phase 1 fixed (Wed 27 May onward):** ~€33/mo = €22 ElevenLabs + ~€9 Buttondown when sub count requires it + ~€2 Anthropic PAYG amortized. (Twitter pay-per-use ~€2/mo at 4 vids/mo.)
**Phase 2 (when first €500/mo lands):** +€38/mo Submagic ($41) → ~€71/mo total. **EXCEEDS €60 cap**, only enable when revenue justifies.
**Cap:** €60/mo Phase 1. Phase 2 budget conversation triggered by first paid month.

**⚠️ Claude Agent SDK billing change 2026-06-15**, usage moves to separate monthly Agent SDK credit pool. Revisit cost model after that date.

---

## 6. Wednesday Session 1 Concrete Build List

### Session 1 · Foundation (Wed 2026-05-27, ~3-4 hrs)

| Task | Deliverable |
|---|---|
| Create project skeleton at `C:\Users\Dell\Documents\Built With AI\` | All dirs from §4, `CLAUDE.md`, `.env.template`, empty `tools\helpers\__init__.py` |
| King David signs up ElevenLabs Creator + records 3-min sample | `ELEVENLABS_KD_VOICE_ID` saved in `.env.master` |
| Wire `helpers\notify.py` | Gmail alert helper using existing OAuth token |
| Build `topic_research_agent.py` (Step 1) | Produces `01_topic_brief.md` for Video #2 calendar entry |
| Build `script_generator.py` (Step 2) | Produces `02_script.md` matching Video #1 structure |
| Build `pipeline_orchestrator.py` skeleton | Runs steps 1 + 2 only, writes `00_state.json`, supports `--resume` |
| Write `commands\autopilot.md` (skill) | `/autopilot` triggers the orchestrator |
| End-to-end test | Topic brief → script for Video #2, verified by King David read |
| Save | Commit Session 1, plan Session 2 |

### Session 2 · Voice + Video (Thu 2026-05-28, ~4 hrs)

| Task | Deliverable |
|---|---|
| Build `voice_generator.py` + `helpers\elevenlabs_api.py` | `03_voice.mp3` from script |
| Build `video_generator.py` Path A + `helpers\pexels_api.py` + `helpers\ffmpeg_stitcher.py` | `04_video_raw.mp4` from voice + stock B-roll |
| Decide Path B (HeyGen) timing · Session 3 or Phase 2 backlog | Decision logged |
| Orchestrator extended to steps 1-4 | End-to-end: topic → final raw video |
| Cost tracker live | `cost.json` populated per run |

### Session 3 · Captions + Publish + Cron (Fri 2026-05-29, ~3-4 hrs)

| Task | Deliverable |
|---|---|
| Build `caption_polisher.py` (Submagic API or Whisper fallback) | `05_video_final.mp4` |
| Build `publisher.py` + 4 channel helpers (`youtube_api.py`, `buttondown_api.py`, `twitter_api.py`, `kie_thumbnail.py`) | `06_publish_receipts.json` |
| Wire YouTube OAuth (use existing `king-david-automation` Google project) | `YOUTUBE_REFRESH_TOKEN` in `.env.master` |
| Buttondown + Twitter signup, keys captured | Keys in `.env.master` |
| Build `weekly_status.py` | Sunday digest email |
| Register Claude Code Routine: Saturday 20:00 Europe/Dublin | Cron job live |
| Full end-to-end dry run · Video #2 ships to YouTube draft | Video published as scheduled for Tue 09:00 |

---

## 7. Risks + Open Questions

| # | Question | Default if not answered | Decide by |
|---|---|---|---|
| 1 | Step 4 renderer: Remotion vs ffmpeg-only vs HeyGen? | **RESOLVED by research · Remotion (free, code-driven, React) is the 2026 Claude-first winner.** HeyGen ruled out (no free tier, niche needs no avatar). ffmpeg = supporting helper, not the renderer. | DONE |
| 2 | Cron timing: Saturday 20:00 vs Sunday 04:00? | **Saturday 20:00** · Sunday is rest day per faith filter; pipeline must complete before Sunday. | Session 3 |
| 3 | Submagic public API · exists? | **RESOLVED · exists but needs $41/mo Business plan.** Defer to Phase 3 (after first €500/mo). Phase 1 uses Whisper + ffmpeg. | DONE |
| 4 | HeyGen per-render cost on Creator tier · exact € | **RESOLVED · HeyGen ruled out entirely. Free API tier dead Feb 2026.** Niche doesn't need avatars. | DONE |
| 5 | YouTube "Altered or Synthetic Content" disclosure auto-tick · does Data API v3 support it? | **RESOLVED · yes, via upload payload field. Hard rule encoded in Step 6.** Missing = permanent ad-rev ban. | DONE |
| 6 | Twitter API v2 free tier (17 posts/day) sufficient for one weekly thread? | **REVERSED · no free tier for new devs since Feb 2026.** Pay-per-use $0.01/post = ~$0.05/video. Budget ~$2/mo. | DONE |
| 7 | Voice quota · ElevenLabs Creator = 100k chars/mo. 4 videos × 9k = 36k. Safe. | Confirmed · 64k headroom for retries. | Confirmed |
| 8 | Idempotency on YouTube upload · what if step 6 succeeded but `00_state.json` write failed? | Orchestrator checks YouTube for existing video with same title-hash before re-uploading. Helper exposes `upload_or_skip()`. | Session 3 |
| 9 | Course transcript ingestion · block Session 1 or run in parallel? | **Parallel background.** Session 1 build does not wait on courses. Patterns absorbed in Session 4 polish. | Decided |
| 10 | What if Claude Routines cron silently skips a Saturday? | `weekly_status.py` checks "did a run happen in last 7 days?" · if no, emails escalation. | Session 3 |
| 11 | Thumbnail design · kie.ai prompt-driven (current plan) vs templated PIL composite from `built_with_ai_brand_kit.md` Variant A/B/C | **kie.ai Phase 1** for speed. Templated PIL fallback if kie.ai cost balloons or off-brand outputs land. | Session 3 |
| 12 | Video #1 · handled by manual + Mubashir or routed through this autopilot? | **Manual ship for Video #1** (already scripted in `video_01_full_package.md`). Pipeline starts at Video #2. | Decided (per handoff) |

---

## 8. Acceptance test for Session 3 sign-off

End-to-end dry run produces, for Video #2:

1. `outputs\runs\<ts>\01_topic_brief.md`, chosen Video #2 title matches calendar row 2.
2. `02_script.md`, 1,600, 1,800 words, passes voice-check linter.
3. `03_voice.mp3`, plays, King David's cloned voice, no robotic artefacts.
4. `04_video_raw.mp4`, 9, 11 min, B-roll cuts every 3, 5 sec.
5. `05_video_final.mp4`, captions burned, hook SFX present.
6. `06_publish_receipts.json`, YouTube draft URL (NOT yet published live, scheduled for Tue 09:00), Buttondown draft URL, Twitter thread scheduled.
7. King David receives one email: `[Built with AI] Run <ts> complete, scheduled for Tue 09:00`.
8. Total cost recorded ≤ €8. Total wall clock ≤ 2 hours.

If all 8 pass → Session 3 ships, pipeline goes autonomous, King David steps away.

---

**END OF v1.1 SPEC.**

---

## 9. SHORTS + MULTI-PLATFORM EXTENSION (added 2026-05-26 14:30 · Phase 1.5, builds Sessions 4-5 next week)

Per KD's daily-cadence ask. Long-form pipeline ships first (Sessions 1-3 this week). Shorts pipeline added next week as a separate orchestrator path. Daily cron + multi-platform cross-post via Playwright.

### Cadence

| Format | Cadence | Source | Platforms |
|---|---|---|---|
| Long-form 10-min | 1/week Tue 09:00 | Autopilot pipeline (Sessions 1-3) | YouTube |
| Hero Short 60-sec | 1/week Wed 09:00 | Repurposed from long-form's strongest beat (auto-extracted from `02_script.json` highest-impact beat) | YouTube Shorts + TikTok + IG Reels |
| Daily Shorts 30-45 sec | 6/week Mon-Sat 09:00 | Generated original via daily Shorts pipeline | YouTube Shorts + TikTok + IG Reels |

Total: 8 pieces / week (1 long-form + 7 shorts) from one weekly cron run + one daily cron.

### Shorts pipeline (new · `tools\shorts_orchestrator.py` next week)

3-step pipeline (lighter than long-form):
1. **Short Topic + Script**, Claude Sonnet (cheaper than Opus for shorts), produces 100-150 word vertical script + 9:16 beat schema. Output: `01_short_script.json`.
2. **Voice + Vertical Render** — ElevenLabs voice for the script + Remotion 9:16 composition (1080x1920 vertical). Pexels B-roll fetched vertical. Output: `02_short.mp4`.
3. **Multi-platform Publish**, YouTube Shorts API + TikTok via Playwright + IG Reels via Playwright (same logged-in cookie pattern as Twitter). Output: `03_short_receipts.json`.

### Hero Short extraction (new · `tools\hero_short_extractor.py`)

After each Long-form run completes (Step 6 publish receipts written):
1. Read `02_script.json` beats
2. Score each beat: cold_open + hook + body_3 (the climax) typically win
3. Cut the chosen beat's audio segment from `03_voice.mp3` via ffmpeg
4. Trim to 50-60 sec, re-render via Remotion 9:16 composition
5. Add "watch the full video →" end-card with long-form URL
6. Schedule publish for Wednesday 09:00 across 3 short platforms

### Multi-platform Playwright publishers (new helpers)

- `helpers\tiktok_playwright.py`, uploads via logged-in TikTok session (cookies in `C:\Users\Dell\.playwright_state\tiktok.json`)
- `helpers\instagram_playwright.py`, uploads via logged-in IG session (cookies in `C:\Users\Dell\.playwright_state\instagram.json`)
- `helpers\youtube_shorts.py`, same Data API v3 as long-form but with `#Shorts` tag + vertical metadata

### Cost rollup (Shorts addition)

| Item | Cost / Month |
|---|---|
| Long-form (~€3.35 × 4) | €13.40 |
| Hero Shorts (~€0.40 × 4) | €1.60 |
| Daily Shorts (~€0.50 × 24) | €12.00 |
| **Variable monthly total** | **€27.00** |
| Fixed (ElevenLabs $22) | €20.00 |
| Anthropic PAYG amortized | €2.00 |
| **All-in monthly Phase 1.5** | **~€49/mo** |

Still under €60/mo cap.

### Build sessions (Phase 1.5 · week of 2026-06-03)

| Session | When | What |
|---|---|---|
| Session 4 (Wed 2026-06-03 eve) | After DCEO day | Build `shorts_orchestrator.py` + 9:16 Remotion composition + Sonnet-based Short script prompt. End-to-end: text → vertical MP4 ~60 sec. |
| Session 5 (Thu/Fri 2026-06-04/05 eve) | After DCEO day | Build `hero_short_extractor.py` + `tiktok_playwright.py` + `instagram_playwright.py` + `youtube_shorts.py`. Daily Shorts cron registered. First multi-platform publish dry run. |

### KD pre-flight for Phase 1.5

When KD has a free 5 min in the next week:
- Sign up TikTok with `@builtwithai_ie` handle (or fallback), bio from `built_with_ai_brand_kit.md` §7
- Sign up Instagram with `@builtwithai_ie` handle (or fallback), bio from `built_with_ai_brand_kit.md` §7
- Log into each in Chromium so Playwright can save the auth state (Claude walks through this when Session 4 starts)

### Why NOT start Shorts in Session 1

Sessions 1-3 ship the weekly long-form. Adding Shorts in parallel = high chance both break + nothing ships. Get long-form Video #2 published successfully first (Tue 2026-06-02), then build Phase 1.5 with a working baseline.

---

## 10. YOUTUBE ANALYTICS INTELLIGENCE LOOP (Phase 1.6 · week 2, builds between long-form pipeline + Shorts)

Per KD's ask. Auto-pulled YouTube Studio stats → Claude analysis → weekly intel email → auto-applied safe adjustments + permission-gated strategic shifts.

### New tools (Phase 1.6, ~3 hrs build)

| Tool | Job |
|---|---|
| `tools\analytics_puller.py` | Daily cron · pulls YouTube Analytics API v2 (free tier, same OAuth as upload). Writes raw JSON to `outputs\analytics\YYYY-MM-DD.json`. Pulls: CTR, AVD, retention curve, peak audience times, traffic sources, top search queries, subs gained/lost, demographics. |
| `tools\weekly_intel.py` | Sunday cron · Claude Opus reads last 7 days vs. previous 4 weeks → generates 1-page intelligence email. Identifies: 3 things working, 3 things broken, 2 strategic shifts for KD approval, auto-applied changes summary. |
| `tools\adaptive_optimizer.py` | After each new video gets 48h of data · auto-regenerate thumbnail if CTR <3%, auto-rewrite title if CTR <3% AND views <100, auto-shift posting cron within ±3h to hit peak audience window. |

### Auto-applied vs ask-first

**Auto (no permission):** posting time shift ±3h, thumbnail regen, title rewrite for low-CTR videos, topic queue reorder based on traffic data.

**Ask-first (email approval):** posting day change, format pivot (length), niche angle shift, spending increases (upgrade tier).

### Pre-data defaults (Weeks 1-3 until ≥4 videos shipped + statistically meaningful)

| Setting | Default | Reasoning |
|---|---|---|
| Posting time | Tue 09:00 Europe/Dublin | Catches UK+IE+EU morning + US East pre-coffee |
| Posting day | Tuesday | Tue/Thu outperform Sun/Mon for AI/business niches |
| Thumbnail style | Cash Yellow + Pure Black + big number + mascot right-third | Highest-CTR cash-cow pattern |
| Title format | `[number] + [verb] + [outcome]` | Specificity + curiosity + claim |
| Hashtags | `#builtwithai #aisidehustle #claudecode` + topic-specific | Brand-trail clustering |

### One-time YT Studio settings (KD does once, 5 min)

- Settings → Channel → Channel keywords (8-12 phrases)
- Settings → Channel → Country: Ireland
- Settings → Upload defaults → Default tags + description footer

### Cost impact

€0. YouTube Analytics API v2 free tier covers single channel. Claude analysis ~€0.10/week.

### Build session

**Session 4 (Wed 2026-06-03 eve OR Thu/Fri eve), squeeze in alongside Shorts pipeline build.** Adds ~3 hrs to that session's scope. Worth it because data starts compounding from week 2 onward.

---

## 11. END OF v1.3 SPEC

v1.0 → original draft
v1.1 → research-driven edits (Remotion, Whisper, Twitter Playwright, HeyGen ruled out, Submagic deferred)
v1.2 → Shorts + multi-platform extension (Phase 1.5)
v1.3 → YouTube Analytics intelligence loop (Phase 1.6)

Next ratification needed: KD reads sections 9 + 10 tonight before Session 1, confirms or flags changes.

