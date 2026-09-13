---
name: project-hub-ad
description: "The Explainer video style + King's 2.2-min hub/service ad (8 gigs, George narrator), BUILT 2026-06-02. Deep scroll-through footage. Next: interactive capture, 8 minis, deploy to video gig, then MONEY."
metadata:
  node_type: memory
  type: project
  originSessionId: 521cb92c-4d87-4cc1-a59c-1b5a865990f8
---

# Hub Ad + Explainer Style [SHIPPED 2026-06-02 · captioned + deployed LIVE + domain live]

## SESSION 10 UPDATE (2026-06-02 ~18:19) · build phase CLOSED, mini-social fixed, domain LIVE
- **mini-social was STALE** (rendered before the social copy edit), showed "CONSISTENTLY" /
  "SHOW UP DAILY". FIXED: added a reusable `--only <slug>` flag to `build_minis.py`, rebuilt just the
  social job (new hook VO + correct copy), re-rendered. Now "GROW YOUR AUDIENCE" / "BUILD YOUR
  AUDIENCE" (QA-confirmed).
- **video-samples.vercel.app REFRESHED + LIVE**, web-optimized the v3 hub-ad (38→11.6MB, ffmpeg
  libx264 crf27 +faststart, keep audio) + 8 new minis + regen poster, `vercel --prod`, verified 200.
- **kingdavidagbidi.com LIVE on the hub at last.** Was an `alias_conflict`: apex+www were bound to the
  OLD "portfolio" project (prj_hBEfWWW4hLUEdqGWzKVBU8D8k7pu). Freed the deploy aliases
  (`vercel alias rm`), then moved both to **kd-hub** via Vercel REST API (the CLI `domains` group can't
  move a project-level binding, only account-level remove). Apex + www both `verified:true`, SSL
  auto-issued, serving the hub ("Leverage AI to Grow Your Business Online").
- King **declined** switching to kdagbidi.com (available ~$11/yr), *"i don't want to waste money"*. Keep kingdavidagbidi.com.
- Style library confirmed at **5 styles**: CinematicReel, HypeCut, TalkingHead, DocStory, Explainer
  (`Built With AI\remotion\styles\*.jsx`; specs `Website Builder\video-edit\STYLE_LIBRARY.md`).
- **NEXT = EXPOSURE/DISTRIBUTION BLITZ** (King fired up, wants results). See [[project-upcoming-tasks]].

## SESSION 9 UPDATE (2026-06-02 PM) · DONE + LIVE at video-samples.vercel.app
- **Interactive capture:** `tools\capture_gigs_interactive.py` (headed Playwright now CLICKS/hovers/types per site, try/except-safe, webm→mp4 in-script) → `jobs\hub-ad\raw\di_*.mp4` (8). social=hover-only, leadgen=no form (honest).
- **Hub ad re-rendered as an UPGRADE:** di_ footage + **upgraded grid hook** (8 site cards glowing behind ONE PERSON). Loved scroll cut saved = `hub-ad_scrollonly_LOVED.mp4`. King shipped the new one.
- **8 minis** rebuilt on di_ footage, CTA = **DM ME / kingdavidagbidi.com** (`build_minis.py`).
- **CAPTIONS = reusable engine feature:** `RunningSubtitle` in `Explainer.jsx` + `beat_captions()` in `video_edit.py` (per-beat whisper word-timings). Tunable **`CAP_FONT=54`** (King: "a touch bigger"), `CAP_TOP=0.88`, current word gold, suppressed on CTA; hyphen-merge fix in `_transcribe_words`. `captions:true` default → EVERY video captioned now.
- **Deployed LIVE:** `video-samples.vercel.app` (hero hub ad + 8-mini gallery + reel). Web-optimized (hub 41→15MB, keep audio). index.html.bak kept.
- **Domain** kingdavidagbidi.com: Active but DNS zone NOT provisioned (Namecheap SERVFAIL) → King in live chat; auto-watcher pinging. Hold Meta ads til live.
- **Gigs:** all 10 publish-ready (`drafts\gigs_all_services_2026-05-31.md`, video gig de-"stop-the-scroll"-ed, minis=boosted clips) + `drafts\video_gig_and_outreach_2026-06-02.md`.
- **PIVOT:** King, much built, €0. STOP building, RUN daily outreach (demos + DMs). See [[project-upcoming-tasks]].

## What it is
A premium **2.2-min ad for King's service/hub** walking through ALL 8 gigs (Websites, Online Stores, AI,
SEO/Marketing, Social, Video Editing, Accessible, Lead Gen). Black+gold (King's personal brand), George (warm
UK) narrator, floating-card showcase of each gig's live site scrolling through its sections. King's verdict on
the first 68s cut: **"this video is amazing."** Then he asked to go deeper/longer → the 2.2-min deep version.
**Also becomes the demo on the Video Editing gig** (video-samples.vercel.app).

## The NEW style: Explainer (`Built With AI\remotion\styles\Explainer.jsx`, registered in Root.jsx)
Matches King's refs (ref3/ref5, the dynamic blue "explainer"): dark bg + ONE accent, **FloatingCard** (tilted
3D card w/ perspective + parallax + drop-shadow + per-gig glow, the signature), label pills, bold kinetic
captions (gold keyword), ring-logo hook, gold CTA. Beat kinds: `hook | gig | close | cta`. Aspect-aware 9:16.
- **CRITICAL TECH:** uses **OffthreadVideo + mp4** (raw Playwright **webm crashes Remotion** with delayRender
  timeouts, always convert captures to h264 mp4 first). Caption gold-word needs `marginRight:"0.28em"` so it
  doesn't eat the trailing space (the "FREESAMPLE" bug, fixed).

## Assets / pipeline (all in `Documents\Website Builder\video-edit\`)
- **Job:** `jobs\hub-ad\job.json` (LONG, 131.6s, deep footage + M-VO). Output `hub-ad.mp4` (38.6MB). 68s cut saved `hub-ad_68s_BACKUP.mp4`.
- **Deep footage:** `jobs\hub-ad\raw\d_*.mp4` (8 gigs, ~20s full top-to-bottom scroll-through). Captured by `tools\capture_gigs_deep.py` (headed Playwright, smooth easeInOut scroll). Short-scroll `g_*.mp4` also there.
- **Voice:** George = voice_id **JBFqnCBsd6RMkjVDRZzb**. Long narration `M0-M10.wav` (`tools\eleven_narrate_long.py` + sharpened bookends `tools\regen_bookends.py`). Short narration `L0-L10.wav` (`tools\eleven_narrate.py`) for minis.
- **8 mini jobs** assembled: `jobs\mini-{websites,stores,ai,seo,social,video,accessible,leadgen}\` (`tools\build_minis.py`), but built with SHORT footage; **REBUILD with deep footage + gig-hero + "DM me/see my page" CTA**.
- **ElevenLabs key** saved in `.env.master` (ELEVENLABS_API_KEY). **SCOPED: TTS works, voice-CLONING blocked** (key missing `create_instant_voice_clone` perm). To clone King's voice later → new unrestricted key. Voice picker: `tools\eleven_voices.py`. Clone attempt: `tools\eleven_clone.py`.
- **Refs** (King's taste): `jobs\references\` (7 analyzed; ref3/ref5 = chosen explainer style; ref6/ref7 = dramatic doc). Move frames: `references\analysis\moves\`.

## NEXT SESSION (King wants multi-agents)
1. **Interactive + deeper capture**, footage should scroll MORE *and interact* (click around shops, lead-gen, AI). Upgrade `capture_gigs_deep.py` to click/hover/interact.
2. **Build the 8 minis** with deep footage, each gig is the HERO of its own ~15-20s short + soft CTA "find out more, DM me / kingdavidagbidi.com". (`build_minis.py` exists; swap to d_*.mp4 + new CTA.)
3. **Deploy** the final ad (or a mini) to the **Video Editing gig** (video-samples.vercel.app).
4. Possible polish: dynamic hook (the ~15s hook is a touch static), sound ducking, motion variety.
5. **Then the OG GOAL (from ~2026-05-31): MONEY**, outreach + publish remaining Fiverr gigs + run this ad on Meta. [[project-upcoming-tasks]]

## Positioning locked (King's calls)
Target = ALL business owners but **win the highest-payers** → premium "agency-quality, no-compromise, one person who cares" + free-sample de-risk. **King = personal brand selling B2B services to business owners** (not B2C; the personal angle is the moat vs faceless agencies).
**TRADES ARE HALF THE AUDIENCE, say it everywhere (King flagged 2026-06-02).** King serves BOTH (1) online
businesses/e-commerce AND (2) **local trades & service businesses** (plumbers, electricians, builders, barbers,
cleaners, salons, etc., his proven base: 146 demos = 124 barbers + 22 home-service). Never frame the offer as
"online only", that pushes trades away. Hub hero fixed to "online & on the tools"; for trades lead with: proper
website, **get found on Google ("near me")**, more jobs booked, reviews. Free-sample model fits trades perfectly.
**(2026-06-02 expanded to FULL inclusivity):** King serves EVERYONE, any business at any stage: just-starting,
sole traders, LLCs/limited companies, established/successful, AND those who don't yet realise they need it. ALL
gigs must be accessible to anyone. Lead every message with the **BENEFIT (save time, money, effort + win more
customers)**. RULE: inclusive at the BRAND/hub level, but SPECIFIC at the AD level, one persona per ad via
targeting; "talk to everyone" = nobody stops. Hub lede + overview updated to "any business at any stage" + benefit-led.
