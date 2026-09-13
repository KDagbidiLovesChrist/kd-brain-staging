---
name: project-content-engine
description: "King's digital-product money machine, REPOSITIONED 2026-06-26 to 'The Faceless Hook Engine' (€19, anchor €47) for faceless AI creators: a whole-package product (50 hooks + 10 scripts + make-the-video + record-voiceover + 30-day plan + engines + captions), AI-does-more ladder, results-based guarantee. Final 29pg PDF + paste-ready Payhip package delivered. Voice = the ElevenLabs PVC clone ErET8T1peh7wSinZbf7N since 2026-07-03 (old real-voice/clone-parked plan superseded). Part of the Proof Engine (Layer 1 = own product; /ugc = Layer 2)."
metadata: 
  node_type: memory
  type: project
  originSessionId: bafd5c1d-e893-4169-8099-7a242d34cfab
---

# The Content Engine · King's digital-product money machine (repositioned 2026-06-26)

Lives in `C:\Users\Dell\.claude\proof-engine\content-engine\`, read its `MANIFEST.md` + `REPOSITION.md` +
`NUMBERS_PACK.md` first.

## 🟢 2026-06-27 (newest) · FULL VIDEO #1 STORYBOARD (every scene) + hustle.faceless EDITING DECODED
King flagged: (a) the talking-avatar is good but the TOP visuals were too flat (one static mockup), model how
**@hustle.faceless** actually edits; (b) the storyboard only showed the 6s hook, he wants the **WHOLE video,
scene by scene, mapped to the full script** (Rule #18, full breadth).
- **Decoded @hustle.faceless for real (no Gemini needed):** pulled their top TikToks via `tools\hook_harvest.py`
  (Apify, `@hustle.faceless --platform tiktok`), got URLs from the saved JSON, **downloaded with yt-dlp + read the
  frames myself** (free, beats Gemini /watch which is down). Their style = **fast-cut MONTAGE (~2-3s/shot)**:
  real **screen-recordings of the AI tool** (the STAR) + **cinematic character b-roll** (their masked HF guy in
  scenes) + a **bold headline pill** (black-on-white) for the hook + **small clean caption pills** for spoken
  words (NOT giant yellow-pop) + masked presenter at the bottom in some shots. Content = AI-TOOL DEMOS.
- **King's calls (locked):** captions = **clean hustle.faceless style** (pills + headline box, not yellow-pop);
  visual source = **mix per video type** (hook/teaching videos = I build graphics free · tool-demo videos = King
  screen-records the real tool); **same look for channel + brand**.
- **KEY NUANCE (King):** shot CONTENT depends on video TYPE. Theirs = tool demos (screen-recs). **Video #1 is a
  HOOK LESSON** → top visuals = teaching graphics (views dying at 0:02, giant STOP, 200-vs-viral chart, hook
  cards), hustle.faceless RHYTHM but hook-lesson CONTENT.
- **Built the FULL 9-scene visual storyboard** for the whole ~45-60s script (`channel_video1_vo`): Hook → Problem
  → "steal these 3" → Hook#1/#2(STOP)/#3 → Payoff(200→viral) → Reinforce(SEO) → CTA(comment HOOKS/€19). Each scene
  = 9:16 thumbnail + the VO line + caption + source tag, Character C presenter every scene. Built as one HTML page
  → screenshotted via **chrome-headless-shell** (Playwright MCP was locked) → `deliverables\videos\v01_3hooks\
  VIDEO1_FULL_STORYBOARD.png`. **Emailed + pushed.** Scene 6 = the only one needing King (screen-rec).
- **⚠️ GEMINI: NO key persisted anywhere** (.env.master/.env/session all empty), the old "AQ." key was ephemeral
  + prepay credits were depleted. `/watch` is OFF until King adds a funded Gemini key (AI Studio pay-as-you-go).
  NOT a blocker, frame-reading downloads replaces it for free.
- **🆕 UPGRADED the storyboard (King's refinements):** (1) King's reference "video I sent" = a Gmail attachment
  `export_*.mov` (subject **"Video ai animation storyboard learn"**) = **@theanimationstudio demoing MiniMax Hub's
  `/character-scene-storyboard`** → its lesson = the **pro storyboard FORMAT (shot list: Shot Type · Camera Action ·
  Emotion/Energy · Characters + a Visual-Style picker)**. Found it by Gmail API search + downloaded the attachment +
  read frames (free, no Gemini). Added **Shot · Cam · Energy** to every scene card. (2) **King: "I don't want
  amateur stuff... b-roll instead of screen recording?"** → DECISION: **NO screen-recs on video #1** (a hook lesson
  has nothing to "prove"; raw screen-recs read amateur) → use **cinematic b-roll (free Pexels) + clean graphics**;
  King records **only his voice**. Screen-recs reserved for future TOOL-DEMO videos, framed premium (zoomed, on
  navy/gold, smooth), never raw. (3) **AUDIO plan confirmed (King asked):** fix PACING (cut dead air/tighten gaps) +
  CRISP/articulate/NON-robotic via free AI enhancer (Adobe Podcast / Auphonic) + light EQ/level (keep his REAL
  voice) + ducked BG music (upbeat-tech bed under voice) + whoosh/click on cuts. Re-emailed the upgraded board.
- **⏳ AWAITING KING:** tweak any scenes (he said he will) → record his voice on the **DJI mic** → I build the
  moving video #1 (all visuals free: b-roll + graphics + talking Character C). Storyboard scaffold reusable:
  `scratchpad\storyboard\storyboard.html`. **Gemini still has NO key** (use the download+read-frames method for refs).

## 🟢 2026-06-27 (latest) · LAYOUT FORK: fully-faceless vs TALKING-AVATAR (King's steer) + find-skills on the avatar tool
King looked at the A+B proofs and flagged: they prove the ENGINE works, but I'd assumed the LAYOUT. The real
@faceless.inc.proj format = **a presenter talking at the bottom + visuals/app up top** (split), not a centered
static avatar. King: model the lane (consensus, not one account), do a VISUAL storyboard first (Rule #18), and
decided: **try BOTH layouts and compare** + **same look for channel AND brand**.
- **`/find-skills` ran** (the talking-avatar method): **free-local lip-sync (SadTalker/Wav2Lip/MuseTalk) is OUT on
  King's hardware** (no GPU; SadTalker ~5/10 anyway). Paid cloud = HeyGen (best, free watermarked tier) / Hedra
  Character-3 (top quality) / Zoice (cheapest all-in-one, $7.99/mo, listicle-sourced) / D-ID / Synthesia, all
  show a realistic face (less "faceless") + monthly fee fights lean-first-euro → **PARKED for premium/brand later.**
  **King picked the FREE route: animated Character C as the presenter** (in-engine, €0, truly faceless).
- **⚠️ Character C has NO face features (blank avatar) → "talking" can't be a mouth-flap.** Sold it with a head
  bob + a **gold voice-bar waveform** + a glow pulse at the bottom = reads as "speaking", stays faceless.
- **Built the talking layout** = `Documents\hyperframes-editor\video-projects\faceless-hook-talking\` (HyperFrames):
  `topvisual.html` (phone app, top), `captions.html` (band, bottom:808), `presenter.html` (Character C bottom +
  bob/glow/waveform), reused `ambient-bg.html`. **GOTCHA fixed:** a mid-timeline `fromTo` flash painted the top
  grey for the first 3.6s, GSAP `immediateRender:true` applies the from-state at t=0; fix = `immediateRender:false`
  (+ a `tl.set(...,0)` rest). Draft frame-verified.
- **VISUAL STORYBOARD built + emailed** (Rule #18, approve-before-finalize):
  `content-engine\deliverables\videos\faceless-hook-test\STORYBOARD_talking-layout.png` (5 shots, PIL contact sheet).
- **⏳ AWAITING KING:** "go" → finalize the moving talking video + deliver it next to the fully-faceless A/B for the
  layout pick; OR tweak the board. Then: chosen layout → record DJI VO → full ~45-60s video #1.

## 🟢 2026-06-27 (later) · A+B REAL ANIMATED PROOFS BUILT, FRAME-VERIFIED + DELIVERED (King: "build both, compare")
The "prove a REAL animated test" task is DONE for BOTH engines. King steered: model a **consensus of channels**
(@faceless.inc.proj **+ @hustle.faceless** 356k/median 88k + lane), not one account; use `/find-skills`; stay on
the latest content-engine. **Step-0 consensus edit-spec + channel playbook** written =
`content-engine\deliverables\videos\FACELESS_CONSENSUS_SPEC.md` (triangulates the 2 decoded channels + the
HyperFrames short-form 10-rule codification + prior find-skills "Submagic+Remotion" verdict; honest note that a
deeper live Apify/Gemini peer-harvest can deepen it later, left lean per Rule #12).
- **Both ~7s 1080×1920 proofs match the signature** (Character C anchor masked to a feathered circle + gold
  @30KINGDAVID kicker + navy/gold ambient; **Montserrat 900 white captions, power word pops YELLOW** #FFE34D on
  "DIE"/"HOOK"; phone-mockup "AI VIDEO GENERATOR" beat with gold GENERATE + tap-ripple + punch-in zoom; glitch
  white-flash cut; VO + whoosh/bass/tap SFX). Frame-verified every beat (read PNGs), fixed 2 real bugs found on
  v1: **caption segment overlap** (cross-fade → garbled boundaries; fix = SNAP-swap, render one segment at a time)
  and a **too-long white flash** (→ 2-frame punctuation).
- **A (HyperFrames)** = `Documents\hyperframes-editor\video-projects\faceless-hook-test\` →
  `renders\faceless-hook-HYPERFRAMES.mp4`. 4-layer faceless scaffold (ambient-bg/scene1-hook/scene2-proof/captions),
  adapted from may-shorts-19 (swap talking-head video for Character C still + phone mockup). `npx hyperframes lint`
  0 errors → render. **GOTCHA:** every `<audio>` needs an `id` or it renders SILENT.
- **B (Remotion)** = `Documents\Built With AI\remotion\styles\FacelessHook.jsx` (registered in `Root.jsx`, id
  `FacelessHook`, FH_DURATION 215f) → `outputs\faceless-hook-REMOTION.mp4`. `npm install` was needed (node_modules
  was missing). Assets staged to `assets\faceless-hook\` (publicDir=`./assets`). Font via
  `@remotion/google-fonts/Montserrat` loadFont (weights 500/700/900) so 900 renders, not a fallback.
- **Shared assets:** placeholder VO = **edge-tts en-IE-ConnorNeural** (Irish, 7.13s), HyperFrames TTS needs
  kokoro-onnx (not installed), edge-tts was the lean win. Per-word timings = proportional distribution inside the
  edge-tts SRT sentence windows (WordBoundary events didn't surface in this edge-tts build). SFX = **synthesized
  with ffmpeg** (whoosh/tap/bass, free, deterministic, no downloads). Character C = `persona_v2_c.png`.
- **Route B no-code** = `content-engine\deliverables\videos\v01_3hooks\NOCODE_ROUTE_SOP.md` (CapCut + Submagic
  "Hormozi" caption preset, exact font/colors #FFFFFF/#FFE34D, King runs it himself).
- **DELIVERED:** both MP4s emailed to King's 2 inboxes + ntfy push, with an A/B "which feels more like the model?"
  note. Both proofs in `content-engine\deliverables\videos\faceless-hook-test\`.
- **⏳ AWAITING KING:** pick **A or B** (that engine becomes the reusable factory) → record the real VO on the DJI
  mic → then build the full ~45-60s video #1 on the chosen engine. The 6s proves STYLE, not voice (placeholder TTS).

## 🔴 2026-06-27 · VIDEO #1 PROPER REBUILD (King rejected the first as "ew wtf")
- **Audit:** engine sound but bypassed, throwaway `build_video1.py` skipped the storyboard, used raw
  auto-captions (garbage) + random Pexels. Same pipeline hit Aunty/Revolut/Mum.
- **NEW RULES (CLAUDE.md):** #17 consensus-on-everything + proven-pattern-first ([[feedback-consensus-everything-rule]]);
  #18 VISUAL storyboard before any build. content-engine.md hardened (storyboard GATE, captions-from-script/
  freestyle, mandatory AUDIO MASTERING, visual board). `/storyboard` Master Prompt saved
  ([[storyboard-master-prompt]]).
- **Audio:** muffle = the RECORDING (HF ~13dB low), not the file. Fix = close mic (King BUYING a DJI Mic) +
  AI enhancer (Adobe Podcast/Auphonic); EQ alone fails. Guides emailed.
- **Reference (profile-vetted by MEDIAN views):** Daniel=fluke (382 foll). @hustle.faceless 356k/median 88k.
  **King chose @faceless.inc.proj (173k, 2.7M+2.6M)**, decoded via /watch → exact spec
  [[reference-faceless-inc-edit-style]] (Montserrat ExtraBold white+YELLOW POP captions, 1-2s cuts, STEP
  cards, glitch, zooms, phone-mockup screen-recs, SFX). HERO = **Character C** (`persona_v2_c.png`).
- **Gemini key** fixed (funded project; use gemini-2.5-pro). **find-skills max-output** = Submagic + Postiz +
  n8n/Remotion ([[reference-content-engine-suite]]).
- **HONEST LESSON:** my static PIL mockups (v1 navy/gold + v2 character) are NOT the edit; oversold "matches."
  The style = ANIMATED (captions/SFX/zooms/glitch) → needs Remotion (owned) or CapCut/Submagic.
- **NEXT = do A (Remotion animated engine) + B (CapCut/Submagic) IN SYNC, prove a REAL animated test**, then
  King records VO on his DJI mic → build video #1. Read [[project-upcoming-tasks]] +
  [[reference-faceless-inc-edit-style]] FIRST.

**🪝 HOOK MACHINE built into `/content-engine` (2026-06-26, from King's "Hook skill" TikTok):** the HOOK
BUILDER now has real tools. **Route A (free, multi-source consensus per Rule #16):** `tools\hook_harvest.py` (Apify → top hooks across
**TikTok + Instagram + YouTube + X + Facebook**, all 5 actors live-verified; grouped per platform, agent
finds patterns recurring across all) + `tools\hook_grader.py` (free 0-100 scorer, rubric
`knowledge\hook_grader_rubric.md`). **IG: use `@profile` for real engagement** (#hashtag = weak recent);
**FB needs a @page/URL**; **Snapchat unsupported** (ephemeral, no scraper). B-roll: `tools\pexels_fetch.py`
(free; bakes in a browser UA, Pexels 403s the default Python UA). PEXELS_API_KEY in `.env.master`.
**EVERY layer is consensus-driven now (Rule #16):** Layer 1/Hooks = `hook_harvest.py` (5 platforms) ·
**Layer 5 SEO = `tools\seo_keywords.py`** (consensus keywords + 🔥rising across Google+YouTube
autosuggest+Trends via pytrends, free no-key; Trends rate-limits sometimes → graceful skip) ·
**Layer 4 Produce = `tools\produce_spec.py`** (MATH: harvests winners, derives engagement-optimal LENGTH
band per platform+situation + edit rubric, faceless-AI TikTok wins at **45-60s**) + **`tools\edit_analyze.py`**
(DEEP: yt-dlp downloads top winners → ffmpeg measures real cut pacing, view-weighted → faceless-AI TikTok =
**~60s, hard cut every ~8s**; HARD cuts only; `--semantic` = Gemini captions/sound, GATED on Gemini credits
[depleted now] → top up or route cheapest vision tool) + `tools\gen_router.py` (provider consensus) + model
on harvest winners. Monetise (L6) = SOP + live Payhip shop. ⚠️ Gemini API prepay credits DEPLETED (429), affects Veo + deep semantic watch; cut-pacing math + autosuggest SEO + Apify harvest all work without it.
**Route B (paid quick):** Sandcastles.ai web app ($39/mo, 7-day trial, NOT a Claude plugin). Also: all
gen now routes cheapest via `tools\gen_router.py` (Gemini Veo Lite / MuAPI / kie), see [[reference-muapi-cost-router]]. Part of [[project-proof-engine-money-plan]]. Skills = `/content-engine` (the
distribution/production engine) + `/ugc` (Layer 2, brands pay King). Plan history:
`plans\open-money-project-folder-sprightly-feigenbaum.md`.

## 🟢 THE PRODUCT · repositioned (READY TO SELL, pending King's upload)
- **The Faceless Hook Engine, €19 (anchored €47)** on Payhip (payhip.com/b/jSCeu). Was "Steal My 10 Hooks"
  at €12.
- **Niche = faceless AI content creators** (narrowed from "creators" via a 3-lane multi-source consensus
  scan: video platforms + marketplaces + written. Verdict: lane is proven but the old packaging was too
  broad, too thin, underpriced, framed as a list not a system).
- **Whole-package product (29-page premium PDF):** done-for-you FIRST, 50 swipe hooks + 10 plug-and-play
  scripts + a consensus-backed **"how to make your faceless video"** walkthrough (first-3-seconds /
  completion, cut every 2-4s, slow zoom, captions, loop ending, free tools) + a **"record your voiceover"**
  step + a copy-paste **30-day plan**; then the 10 **Hook Engines** (unlimited more) + the **Caption
  System**. Plus a quick-start spine that ties it together.
- **AI-does-more ladder:** free 3-hook magnet → **€19** (AI writes for you) → **€97** Faceless Content
  System (AI runs the machine) → **€297+** done-for-you (AI runs your channel for you).
- **Results-based guarantee:** run the full 30-day plan; do it and still no results = full refund; plus
  "DM me for help, free." A Payhip refund-policy block is written.
- **King = living proof** (his @30Kingdavid channel runs the same engine he sells, no fake testimonials).
- Source files: `PRODUCT.md` + `PRODUCT_DONE_FOR_YOU.md` + `STORE_LISTING.md`; **current PDF =
  `deliverables\The-Faceless-Hook-Engine-v2.pdf`** (from `faceless-hook-engine.html` via Chrome print-to-pdf;
  v1 kept for history). Paste-ready Payhip package emailed to King.

## 🆕 v2 DEEPER REBUILD + MULTI-SESSION (2026-06-26, Session A = TikTok)
King ran **parallel sessions** (TikTok / Instagram / content-skill + a UGC session), coordinated via a new
board **`proof-engine\SESSION_SYNC.md`** (lanes + collision rules + a "post SKILL DONE" trigger; the brain IS
the comms channel since live sessions cannot message each other). TikTok lane home doc =
**`proof-engine\TIKTOK_LANE.md`**; King's one-sitting record+setup sheet = **`proof-engine\ACTION_DAY.md`**.
**Deeper product rebuild (v2, King's call, data-driven, NOT homogenized):** FIXED the length advice
(15-30s → **45-60s**, hard cut ~6-8s + slow zoom; the old advice contradicted our own
`produce_spec`/`edit_analyze` data); named **current tools** (Kling/Runway/Veo/CapCut AI) in the AI swipe
section; **AI does the editing is now emphasised + TAUGHT in the €19** (CapCut AI/Submagic/Opus Clip) while
**€297 stays the done-for-you tier**; baked in the **"AI video" keyword lesson** (lead public
titles/hashtags with "AI video", never "faceless"/"UGC" = keyword traps); added **"free lifetime updates" +
a v2 stamp**. KEPT the 50 hooks' variety (a blanket regrade to the heuristic `hook_grader` would homogenize
the swipe file = deliberately avoided; the grader is a single-hook floor-check, not a bulk filter).
**Payhip LISTING keyworded** (`STORE_LISTING.md`): title + tags now lead with "AI video" (brand name kept).
**Installed poppler/pdftoppm** (winget `oschwartz10612.Poppler`; binary at
`...\WinGet\Packages\oschwartz10612.Poppler_..._8wekyb3d8bbwe\poppler-25.07.0\Library\bin\pdftoppm.exe`) →
**visually QA'd every changed PDF page** (cover/make-video/guarantee, all clean, nothing clipped). Final PDF
emailed to King ("USE THIS one"). **Video #1 (channel @30Kingdavid):** hook A-graded 95 = "I tried 3 AI
hooks so you never get buried again"; on-screen SEO phrase = **"AI video hooks"** (was "faceless video
hooks"); length **~45-60s** (script in `ACTION_DAY.md` Part 1, King tweaks to his voice).

## 🎙️ VOICE · DECISION (2026-06-26) — ⚠️ SUPERSEDED 2026-07-03
**Current (King's call, 2026-07-03): the ElevenLabs PVC CLONE (voice_id `ErET8T1peh7wSinZbf7N`) IS the
voice for @30Kingdavid content** — take-mixing could never pass his consistency bar; he settled the
invoice himself; sub reviewed month-end via `/money`; video #1 FINAL shipped on the clone. See
`memory\project_faceless_content_engine.md` (Rounds 11-12).
*(Old 06-26 decision, kept for history: REAL voice per script → bank to `voice\voicebank\` → retrain the
clone at ~30-60 min; clone parked for scale because 6 tuning rounds hit a settings ceiling; v3 model
rejected for losing his accent. See [[reference-elevenlabs-voice-cloning]].)*

## 📊 SEO / content angle (real tool data via pytrends)
**"ai video generator" = ~14x the search demand of "AI content creation"**; BREAKOUT rising terms = **nano
banana, seedance 2.0, higgsfield** (the AI video tools King already uses). **LEAD content with the
AI-tools angle**, pair with the hooks niche. Full proof stats + keyword targets + tools in `NUMBERS_PACK.md`
and [[reference-faceless-video-results-consensus]]. Rule: strongest-numbers consensus + wire the real tool
([[feedback-multi-source-consensus-research]]).

## 🎯 GOAL LENS wired in (2026-06-26) · answer to "make the content engine better"
Ran `/find-skills` (every-platform consensus) on the engine for the monetization goal. Honest verdict:
the engine is **already strong on per-video quality** (hooks, length math, cut pacing, SEO); the one gap
the money-consensus across all 5 platforms leans on is **volume + auto-posting at scale + a tighter funnel**
(a repo literally named `ai-video-funnel` kept surfacing), a real upgrade IF the goal is monetizing
King's OWN socials. Built instead of guessing: a **pipeline-wide GOAL LENS**, shared `tools\goals.py`
(money/followers/audience/traffic/engagement, multiple + ranked) now wired into `hook_harvest`,
`seo_keywords`, `produce_spec`, `edit_analyze` and this skill (`--goal a,b`). So every consensus layer
now ranks toward what King WANTS, not just "what's popular" (tested: SEO surfaces buyer-intent keywords,
hooks tag 🎯). It's a **loop** (produce → measure per platform/goal → find better way → improve). King's
goal hierarchy: **main = UGC/brands paying (the `/ugc` lane) · secondary = own brand + €19 sales**; he
chose "all three, UGC first." See [[reference-multi-source-consensus-research]] + `tools\goals.py`.

**🆕 COMPLETION BUILD (2026-06-26), King: "build both now".** The scout's two gaps are now built:
(1) **Auto-post engine** `tools\autopost.py`, turns one video into goal-aligned per-platform packs
(caption + hashtags + "link in bio" CTA for TikTok/IG/YouTube). **HONEST:** full-auto posting to TikTok/IG
isn't safely free (official-API app approval; browser automation = BAN RISK, excluded per King's rule) →
it preps the pack, King taps publish; YouTube can API-upload unlisted. Wire a free official scheduler
(Upload-Post/Postiz) later to drop the last tap. (2) **Funnel** `proof-engine\content-engine\funnel\`
, the missing **opt-in page** (`index.html`, LIVE preview funnel-hm73zqs77-king-david-s-projects2.vercel.app,
ssoProtection removed → public 200) using the existing `LEAD_MAGNET.md` + `EMAIL_SEQUENCE.md`; wiring
steps in `funnel\FUNNEL_SETUP.md`. **King's actions to finish the wire:** free MailerLite account + paste
the form URL + make the magnet PDF. The page works as a preview now (shows success + €19 CTA); email
capture needs that last wire. Tested: autopost packs + funnel page render clean.

## NEXT
King's actions (emailed step-by-step): (1) **re-upload the v2 PDF + the keyworded listing** to Payhip (the
"USE THIS one" email) → shop live + upgraded; (2) **set up @30Kingdavid TikTok** (Business, the updated
"AI video tips for creators" bio, warm up 5-7 days); (3) **record the voiceovers**, video #1 is now the
**~45-60s** version (new hook). Then Claude builds **video #1** (~45-60s, hard cut ~8s, "AI video hooks" SEO)
via `/content-engine` + distributes. Parallel: the **UGC lane** (`/ugc`, now **IG-first** per the UGC
session). Still **€0**, shop ready + upgraded, first sale pending. Toolkit deadline = first euro by end-July.

## 2026-06-27 · Video #1 visual route: FREE-vs-AI comparison board SENT (awaiting King's pick + voice)
Built + delivered a side-by-side board so King can compare the visual route for Video #1 BEFORE committing:
- **File:** `scratchpad\compare\VIDEO1_FREE_vs_AI.png` (3 scenes × FREE-stock vs FULL-AI columns; same layout = Character C presenter bottom + captions; only the top visual changes). Source `scratchpad\compare\compare.html` (data-driven; AI imgs in `compare\ai\`, free Pexels in `compare\free\`).
- **AI images** via `tools\gen_router.py image` (kie.ai Nano Banana, ~$0.08 each, $0.24 total): s1_hook · s6_aiwork (gold neural brain) · s7_viral, natively navy/gold cinematic, clearly beat the free Pexels stock.
- **Cost ladder shown:** FREE €0 · **AI-images + free-motion ~€3-5/mo (RECOMMENDED)** · +1 hero AI clip ~€8-12 · FULL AI video ~€25-55/mo (deferred until earning). ~$9.58 on MuAPI covers first weeks.
- **Accountant verdict (logged in `finances\LEDGER.md`):** 💡 NO to the €50 Gemini pre-load, deep reference analysis is FREE (download + read frames myself). Top up the MINIMUM (~€10) only when a specific paid task lands; quote cost before each run.
- **Delivered:** emailed kingagbidi@gmail.com + Kingdavidagb@icloud.com + ntfy push.
- **⏭️ NEXT (waiting on King):** (1) pick the route, (2) send scene tweaks, (3) record VO on DJI mic → then build the full moving Video #1 (b-roll/AI-images + graphics + talking Character C) with audio mastering (pacing + ducked music + crisp/non-robotic). Storyboard scaffold ready: `scratchpad\storyboard\storyboard.html` + `VIDEO1_FULL_STORYBOARD.png`. Engines staged: HyperFrames `faceless-hook-test\` + Remotion `FacelessHook.jsx` + talking layout `faceless-hook-talking\`. Rules #17 (consensus) + #18 (visual storyboard) honoured.

## 2026-06-28 · MOVING PREVIEW (animatic) built + delivered + placeholder voice mastered
King asked to SEE a moving placeholder before recording. Built `scratchpad\storyboard_deep\VIDEO1_ANIMATIC.mp4` (3MB, 58.9s, 1080x1920): 12 full-res scene frames (`frames\frame_NN.png` from `_solo_scene_NN.html`) + per-scene Ken-Burns + hard cuts + per-scene edge-tts Irish placeholder VO (en-IE-ConnorNeural). **Voice FIXED per King + content-engine audio standard:** each VO run through the mandatory mastering chain (highpass 90 -> presence EQ 3.4k -> air 6.2k -> de-ess 7.4k -> acompressor -> loudnorm I=-14) = crisp, not robotic. QA: all 12 scenes land correct, audio peak -1.4dB no clip. Emailed + pushed. Assembler = `scratchpad\storyboard_deep\assemble_animatic.py`.
- **⚠️ ffmpeg lesson (save for reuse):** `zoompan` with `-loop 1` EXPLODES clip length (d frames PER input frame x many looped frames = clips of 500-1190s). FIX = feed zoompan a SINGLE still (NO -loop), `d=<total frames>`, `-shortest`. Also kill stray ffmpeg.exe (`taskkill //F //IM ffmpeg.exe`) before deleting locked clips; background ffmpeg tasks STALL when the session goes idle (finish them inside an active turn).
- **⏭️ NEXT (waiting on King):** his opinion on BOTH the 7-page storyboard + this preview → record real DJI voice → I swap VO, re-time per his pacing, add ducked music bed, word-by-word captions = final Video #1. Then distribution pack (Layer 5) + funnel wire (Layer 6).

## 2026-06-27 (later) · DEEP STORYBOARD (MiniMax depth) BUILT + DELIVERED + made a permanent rule
King wanted the storyboard as deep as the @theanimationstudio "Anime World Cup" MiniMax Hub TikTok he sent (Gmail "Video ai animation storyboard learn", decoded by downloading + reading frames). Its depth = 3 deliverables: (1) Comprehensive Design Sheet Brief, (2) Character Model Sheet ("SHANY" rule = same character every shot), (3) shot-by-shot production storyboard.
- **Built the full 7-page deep pack** for Video #1 (52s, 12 scenes): Page1 Design Sheet Brief · Page2 Character C Model Sheet (+4 states) · Page3 whole-video overview · Pages4-7 shot-by-shot (each scene = a real composed frame + EMOTION-first fields: VO/script, shot type, camera/MOTION = how the still becomes moving, visual+tool, SFX/music, transition, the real image/motion prompt). Source `scratchpad\storyboard_deep\` (build_deep.py + out_01..07 PNGs). 8 AI hero stills via gen_router (~$0.64 total). All 7 QA'd clean, rendered via chrome-headless-shell.
- **Delivered:** 7 PNGs emailed (kingagbidi@gmail.com + Kingdavidagb@icloud.com) + ntfy push.
- **MADE IT A PERMANENT RULE (King's steer):** background agent baked the DEEP STORYBOARD STANDARD into `commands\content-engine.md` + a MAXIMUM-DEPTH principle into `commands\find-skills.md` + created `memory\reference_deep_storyboard_standard.md` (indexed in MEMORY.md, linked from reference_visual_production_pipeline.md). Every video/skill from now hits this depth.
- **Plan improvement pass (vs upgraded /content-engine):** hook "I tried 3 AI hooks..." re-graded **A/95** via `tools\hook_grader.py` (alternatives 56, 30) = data-locked. THREE free additions surfaced, not yet built: (1) Distribution pack (Layer 5: SEO caption w/ "AI video hooks" keyword + hashtags + post window + "comment HOOKS" CTA), (2) wire SC12 CTA to the live funnel (Beacons → MailerLite → €19), (3) graded-hook lock-gate (now auto via skill). Offered to build #1+#2 now or after King reviews. **⏭️ Still waiting on King: approve the board + scene tweaks + record DJI voice.**
