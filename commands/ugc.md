# /ugc · UGC-as-a-Service (get paid by brands to make their ads)

**Trigger:** King types `/ugc`, or says "run the UGC business", "find UGC clients", "make a UGC ad for
[brand]", "UGC portfolio / pitch / rates".

**Purpose:** Make money making short, authentic-style ads **FOR brands who pay you** (per video + usage
rights + retainers). This is the **"Layer 2 / fast cash" lane**, a DIFFERENT business from
`/content-engine` (which builds King's OWN audience for his OWN product). Here brands buy the **content**,
not your audience, so **follower count is irrelevant**. Runs **in parallel** with the content engine and
**reuses it** (`/content-engine` does the hooks/TSV/trends/produce; `/ugc` is the CLIENT + SALES + DELIVERY
motion on top). Money-plan context: [[project-proof-engine-money-plan]] + [[reference-content-engine-suite]].

---

## GOLDEN RULES
1. **Lean / free until paid.** Portfolio + outreach cost nothing. Paid tools (seeclic.ai etc.) only behind
   King's spend gate ([[feedback-lean-spend-llama-routing]]).
2. **Demo-first (King's superpower).** A free, tailored sample ad wins the gig, lead with proof, not pitch
   ([[feedback-demo-first-AB-standard]] / [[feedback-personalised-demos]]).
3. **Data + consensus.** Verify current rates + which platforms accept Ireland before acting, never one
   source ([[feedback-multi-source-consensus-research]]).
4. **Faith filter.** No off-limits niches (gambling/alcohol/adult/deception) ([[feedback-faith-values-filter]]).

## STEP 0 · POSITION (lock the offer)
**✅ CONSENSUS PICK (locked 2026-06-26, multi-source research):**
- **Niche = Tech / SaaS / AI tools**, highest-paying UGC ($300-700 entry, $3-8k/mo retainers), fits King's
  AI edge, faceless-native (screen-record + voiceover, no face, no physical product), and his own toolkit
  content doubles as portfolio proof. **Beauty/skincare = easy-volume 2nd lane** later.
- **Style = faceless voiceover + visuals + captions in King's REAL voice clone** (data edge: narrated =
  +32% comments / +49% watch time / 60-70% completion; human voice = trust). Visual = **screen-record for
  software**, hands-only demo for physical. Hook in first 3s. **NOT AI avatar** (off-brand, see verdict).
- **Rates (verify current, see PRICING):** lock a starter rate + a usage-rights add-on + a retainer offer.
(Original options kept as alternates: real-on-camera / AI-UGC avatar / other niches, switch only with reason.)

## LAYER 1 · PORTFOLIO (the unlock · brands hire off THIS, not followers)
Make **3-5 SPEC ads** (unpaid sample UGC for dream brands). Each = a real UGC ad (Hook → Problem → product
demo → CTA) built with `/content-engine`'s **HOOK MACHINE + Produce**. This IS your proof. Host on a simple
page / Beacon / a clean Google Drive folder. **No portfolio = no clients**, so this comes first.
- **Hooks = data-driven, A-grade:** `python tools\hook_harvest.py "<niche or @competitor>"` (real winners,
  5 platforms) → model → `python tools\hook_grader.py "<hook>"` → keep grade A (≥85). King's 7 spec hooks
  are A-graded in `proof-engine\UGC_SPEC_PORTFOLIO.md`.
- **Produce on a FORMAT CONSENSUS (not by feel):** from the harvested winners extract the winning format
  (clip length, cut pace, caption style, sound, structure) + cross-check
  [[reference-faceless-video-results-consensus]]; lock it per ad, produce to match (see Layer 4).
- **Distribute (FOCUS = Instagram first for this studio lane; Session A drives TikTok):** produce each ad
  multi-platform-ready, but POST Instagram-first (@30kingdavidstudio), add YouTube/X/Facebook later at King's
  pace (produce once, re-dress per platform). **Public titles/hashtags = "AI video / AI ads / AI content"**
  (real demand); keep **"UGC / faceless"** for the bio + marketplaces + brand outreach only (keyword-trap).

## LAYER 2 · FIND CLIENTS
- **Marketplaces:** Influee, Insense, Collabstr, Influentials, Twirl. **⚠️ Billo + JoinBrands BLOCK Ireland**
  (King's brain), skip those.
- **Direct outreach:** DM/email small-to-mid DTC brands (beauty, supplements, apps, gadgets) with the spec link.
- **Warm:** King's creator network (a real edge most UGC creators lack).
- **Get paid via:** Wise / PayPal / Revolut / Stripe.

## LAYER 3 · PITCH (demo-first)
Short DM/email: *who you help + the spec sample link + a free/cheap first-video offer.* Lead with the
portfolio, not a wall of text. Personalise to the brand (rebuild a quick sample for THEM = highest close).

## LAYER 4 · PRODUCE THE AD
The deliverable = a **data-derived-length ad** (Instagram ~20-40s) : **Hook (A-graded, on screen by ~2s) →
Problem → product demo → CTA**. Make **2-4 hook variations** (brands A/B test). **Produce to the TOOL-DERIVED
spec, not taste:** `python tools\produce_spec.py "<product/niche>" --platform instagram --situation faceless
--goal money` (length + edit rubric) + optional `tools\edit_analyze.py` (measured cut pace) → see
`proof-engine\UGC_FORMAT_CONSENSUS.md`. Visuals via `tools\gen_router.py` (cheapest), free b-roll via
`tools\pexels_fetch.py`, voice = King's REAL voice, burned-in word-by-word captions. **QA against the spec,
until King approves** ([[feedback-qa-until-king-approves]]).

## LAYER 5 · DELIVER + USAGE RIGHTS
- Deliver **raw + edited + aspect variations** (9:16 + 1:1 + 4:5).
- **License terms:** organic-only vs **PAID-ads usage**, charge **~+30%** when they'll run it as a paid ad.
- Simple one-page agreement + a clear **revisions policy** (e.g. 1-2 rounds). Then invoice.

## LAYER 6 · GET PAID + RETAIN
- **Invoice** (Stripe / Revolut / PayPal / Wise).
- Turn one-off → **monthly retainer** (e.g. 4-8 videos/mo) = stable income at a better per-video rate.
- Collect **testimonials + the brand's results** → use them to raise rates + win the next client.

## PRICING (verify current · from this session's multi-source research)
- **Base:** ~$75-150/video starter → **$200-500+** experienced. **Usage rights:** **+~30%** for paid ads.
- **Packages** (3-5 videos) + **retainers $1,500-$5,000/mo**. Diversified UGC creators reach $5-12k/mo.
- **Follower count does NOT matter**, they buy the content. (Re-confirm rates per the consensus rule.)

## TOOLS (free-first, all run with `--goal money` · the shared goal lens `tools\goals.py`)
- **Engine:** `/content-engine` (hooks / TSV / trends / produce). **Hook Machine (free):**
  `tools\hook_harvest.py` (real winners, 5 platforms) + `tools\hook_grader.py` (0-100, keep grade A).
- **Spec + SEO (consensus, the data-driven produce + distribute):** `tools\produce_spec.py` +
  `tools\edit_analyze.py` (optimal length + real cut pace from winners) · `tools\seo_keywords.py` (title
  keyword + hashtags). Output → `proof-engine\UGC_FORMAT_CONSENSUS.md`.
- **Produce:** `tools\gen_router.py` (cheapest gen, auto-fallback) + `tools\pexels_fetch.py` (free b-roll) + ffmpeg/Remotion/HyperFrames.
- **AI-UGC (client ads only):** seeclic.ai / HeyGen / Arcads (PAID → spend gate, verify quality + cost first).
- **Film:** phone. **Edit:** CapCut / our engines. **Voice:** King's REAL voice for this UGC lane (`UGC_VOICE_PLAN.md`). *Note 2026-07-03: the PVC clone `ErET8T1peh7wSinZbf7N` is now LIVE for @30Kingdavid content (no longer "parked"); whether UGC also uses the clone = King's call per job.*
- **Distribute:** Buffer/Metricool (free, schedule the multi-platform re-dresses).
- **Invoicing:** Revolut / PayPal / Wise / Stripe. **Clients:** Influee / Insense / Collabstr / Twirl.

## OUTPUT / DONE-WHEN
- [ ] Positioned: niche + mode + rates locked (Step 0).
- [ ] **3-5 spec portfolio ads** built + hosted (Layer 1).
- [ ] Client platform list + outreach targets (Layer 2).
- [ ] Pitch sent with a free-sample offer (Layer 3).
- [ ] First ad produced + delivered with usage terms (Layers 4-5).
- [ ] Invoiced + paid → push for a retainer (Layer 6).

## WAT
**W** = this SOP. **A** = Claude (runs positioning, sales, delivery; reuses the engine). **T** =
`/content-engine` + AI-UGC tools + CapCut/HyperFrames + invoicing + client platforms. **S** = `/ugc`.
→ brands pay → money. This is **Layer 2 (fast cash)**; the content engine is **Layer 1 (own product)**.
Run both in parallel.
