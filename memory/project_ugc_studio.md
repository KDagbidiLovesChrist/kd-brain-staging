---
name: project-ugc-studio
description: "King David Studio (@30kingdavidstudio), the UGC-as-a-Service business: get paid by AI/SaaS/fintech brands to make their faceless ads. Launched 2026-06-26 (this session). Portfolio + IG live; blocked only on King's first voiceover + clips to assemble ad #1."
metadata: 
  node_type: memory
  type: project
  originSessionId: 2b80c6e3-b219-4d69-82a7-c36e0e450778
---

# King David Studio · UGC-as-a-Service (@30kingdavidstudio)

The **Layer 2 / fast-cash** money lane of the [[project-proof-engine-money-plan]]: brands pay King per video
+ usage rights + retainers to make their faceless ads. Runs in PARALLEL to the brand/content-engine lane (the
€19 shop). Skill = **`/ugc`** (`commands\ugc.md`). All files live in `proof-engine\UGC_*.md` + `ugc-portfolio\`.
Follower count is irrelevant here, brands hire off the PORTFOLIO. Built 2026-06-26.

## 🟢 LIVE / DONE (2026-06-26)
- **Portfolio page LIVE:** https://ugc-portfolio-peach.vercel.app (`proof-engine\ugc-portfolio\index.html`, Vercel). Modern dark/violet-pink gallery, 7 ad cards, "hire me" CTA. Ready to drop real MP4s in. 200, mobile-clean, 0 em-dashes.
- **Instagram set up by King:** **@30kingdavidstudio** (rebranded his old "gymbrained", 0 posts = clean). Creator account, bio + portfolio link, profile pic = **Character C**.
- **Rates locked** (`UGC_RATE_CARD.md`, 8+ sources): standard €230-275/video, founding-client first video €140-185, 3-video pack €600-690, usage +30%, starter retainer €1,100-1,375/mo. Niche pays 2-4x beauty.
- **25 target brands** (`UGC_TARGET_BRANDS.md`), Tier-1 = tools King uses (CapCut/ElevenLabs/Opus Clip/Submagic/Canva). Marketplaces: Collabstr (first, Ireland-OK) → Influee → Insense (later). Skip Billo + JoinBrands (block Ireland).
- **7 spec ads designed** (`UGC_SPEC_PORTFOLIO.md`), hooks **all A-graded (89/100)** via `hook_grader.py`.
- **Brand character** = faceless persona (cornrows-into-twists + Orthodox cross) = `ugc-portfolio\assets\characters\persona_v2_c.png`. King chose C. Logo parked (not needed; UGC never watermarks client ads).

## DECISIONS LOCKED (King)
- **Niche** = Tech/SaaS/AI/fintech, **faceless** (screen-record + voiceover). **Voice = King's REAL voice** for this UGC lane (see [[reference-elevenlabs-voice-cloning]] + `UGC_VOICE_PLAN.md`). *Note 2026-07-03: the PVC clone `ErET8T1peh7wSinZbf7N` went LIVE for @30Kingdavid content, so "clone parked" is no longer true globally; clone-for-UGC = King's call per job.*
- **Handle** = @30kingdavidstudio (separate business from the brand @30Kingdavid).
- **FOCUS = Instagram first** (this lane); Session A drives the brand's TikTok. Multi-platform = long-term (produce once, re-dress), not all-5-at-once.
- **Keyword split:** public titles/hashtags = "AI video / AI ads / AI content" (real demand); "UGC/faceless" = bio + marketplace + outreach only (keyword traps, nobody searches them).

## PRODUCE = DATA-DRIVEN (not by feel) · `UGC_FORMAT_CONSENSUS.md`
Re-derived with the finished content-engine tools (`produce_spec.py`, `seo_keywords.py`, `--goal money`):
- **UGC ad length = ~20-40s** (TikTok winners 20-30s, YT 30-45s). NOTE: King's OWN creator content = ~45-60s (different format, no conflict).
- Hook on screen by ~2s · burned-in word-by-word captions · slow zoom every clip · SFX on cuts · trending audio · ~70% completion target.
- **Conversion beat (find-skills web consensus):** Hook → Agitate → Discovery ("then I found") → Demo → CTA ("free/no card"). Lead with outcome+number. UGC ads convert ~40% better than polished brand ads.

## ⛔ THE ONE BLOCKER → NEXT
King sends his **Revolut voiceover (A-grade hook) + 5 screen-clips** via a Drive link → I assemble ad #1 to
the format spec (gen_router for visuals, pexels_fetch for b-roll), QA, King approves → onto the portfolio →
then set up Collabstr + Influee. Build steps King is following = `UGC_BUILD_GUIDE.md` (also emailed). Still €0.

## Cross-session note
King runs parallel sessions; comms board = `proof-engine\SESSION_SYNC.md`. This lane does NOT edit
`commands\content-engine.md` (Session C's). Lane status posted there.
