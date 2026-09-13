---
name: project-premium-3d-venture
description: "Premium 3D rebrand of King David's web/store business. 5 original flagship sites + 4 NEW unique-per-brand 3D demos (LUMÉ clinic, AXION fintech, AURUM jewellery, VERDE wellness) all LIVE 2026-05-31. Portfolio now leads with a Flagship-3D section + tier-ladder pricing. Rule re-affirmed by KD: every brand its OWN world, never a recoloured template. Next: update launch posts to the new demos + KD reviews + sends."
metadata: 
  node_type: memory
  type: project
  originSessionId: d0cd8cf9-62f8-4d50-be84-92e7fd76fdc2
---

# Project: Premium 3D Rebrand (LIVE · started 2026-05-31)

King David levelled up the whole business: every demo/site/portfolio must look top-tier / $1M /
Apple-grade, with real-time 3D/WebGL as the flagship tier. The look IS the sales pitch + price
justification. Standard + rules locked in [[feedback-top-tier-design-standard]].

## 5 ORIGINAL flagship sites (all own Vercel projects, CLEAN public aliases · team-scoped = 401)
- **a11y-demo-gamma.vercel.app**, accessible + multilingual (the MindyCore proof). Hand-coded.
- **flagship-demo-dusky.vercel.app**, MERIDIAN, dark-luxe architecture studio (GSAP horizontal scroll).
- **kd-3d.vercel.app**, real-time 3D WebGL proof (Three.js custom shader orb). Navy/gold.
- **vanta-store-six.vercel.app**, premium 3D streetwear STORE (WebGL hero + WORKING cart). Mono.
- **kd-portfolio-eosin.vercel.app**, KD's 3D PORTFOLIO HUB.

## 4 NEW unique-per-brand 3D demos (built 2026-05-31, session 2 · each its OWN world)
Sources: `Documents\Website Builder\proofs\{lume-clinic, axion-fintech, aurum-fine, verde-wellness}\`
(index.html + style.css + app.js each). All verified live, HTTP 200, public, ZERO console errors.
- **lume-clinic.vercel.app**, LUMÉ aesthetic & skin clinic. Warm pink/champagne/plum, Cormorant+Jost,
  slow calm motion, soft glowing "serum drop" (noise-displaced sphere shader). NOTE: pink is LUMÉ-ONLY.
- **axion-fintech.vercel.app**, AXION fintech. Near-black + electric cyan/violet, Space Grotesk + mono,
  sharp kinetic glowing WIREFRAME geodesic + light-up nodes + counter-rotating core, dev code-block.
- **aurum-fine.vercel.app**, AURUM fine jewellery. Charcoal + real gold, Marcellus serif, slow opulent,
  flat-FACETED gold gem (true facets via dFdx/dFdy screen-space normals + sharp glints). Needs
  `extensions:{derivatives:true}` on the ShaderMaterial.
- **verde-wellness.vercel.app**, VERDE botanical wellness. Bright sage + forest green + terracotta (NOT
  pink), Newsreader + DM Sans, slow organic, flowing noise-displaced TORUS-KNOT ribbon + rising pollen.

## Portfolio UPDATED 2026-05-31 (kd-demos.vercel.app/portfolio)
Source: `Documents\Website Builder\kd-demos\portfolio\index.html` (navy/gold KD-branded hub).
- Added a **"Flagship, real-time 3D"** section at the top: 4 cards w/ REAL hero screenshots
  (`kd-demos\portfolio\shots\{lume,axion,aurum,verde}.jpg`), each linking to its live site, gold-violet 3D badge.
- Hero refreshed (10 unique designs · 146 demos · 3D flagship tier). Added inline favicon (no more 404).
- Pricing rebuilt to the TIER LADDER: Standard €99+€39 · Professional €299+€45 · Signature €900+€69 ·
  3D Flagship from €4,000+€129, 249/mo. Kept the 6 niche demos + 146-demos + online-shops bands.
- Deploy: `vercel --cwd "...\kd-demos" deploy --prod --yes` → aliases to kd-demos.vercel.app (whole bundle ~633KB).

## Proven build scaffold (reuse for every new brand)
Three.js r128 (cdnjs) + GSAP 3.12.5 + ScrollTrigger, all progressive-enhancement (content shows if
WebGL/CDN fail). Embedded GLSL (Ashima simplex noise for displaced solids; screen-space derivative
normals for flat facets; LineSegments+Points for wireframes). Custom cursor, preloader, magnetic CTAs,
scroll reveals. Per-deploy: each demo = its own Vercel project, the `<name>.vercel.app` alias is the
clean PUBLIC one (the `-king-david-s-projects2` deployment URL is 401). Always verify w/ Playwright
(navigate → console errors → screenshot).

## RULES locked (see [[feedback-top-tier-design-standard]])
- **RE-AFFIRMED 2026-05-31 by KD (emphatic):** every brand gets its OWN world, own colour, font, motion,
  3D idea. The QUALITY/3D capability is the constant; the LOOK changes every time. Pink was LUMÉ's
  identity ONLY; never reuse one palette/look across demos. "One pink clinic is beautiful, ten pink
  sites are a template." Proven this session with 4 deliberately different worlds.
- Reference-driven: KD shows examples (liked Adrien Ninet WebGL; @wennyvisual stores). Match + beat.
- Honest: fictional brands, no fake clients on KD's OWN site; demos carry KD's email in the footer.

## Session 3 additions (2026-05-31) · assets complete, now distribution
- **AMBRÉ** 3D fragrance STORE w/ working cart (verified): ambre-store.vercel.app. Different store world to VANTA.
- **LUMÉ 2D / lite** (no-WebGL, pure-CSS hero) for cheaper tiers/laptops: lume-2d.vercel.app.
- **Reusable 3D STARTER KIT** (blank, client-neutral, NO KD branding, pick-a-shape CONFIG + README):
  `Website Builder\templates\3d-starter\`. KD's rule: delivered client sites carry NO KD branding.
- **Portfolio = 11 unique designs**, AMBRÉ added as a Flagship-3D card. **Standalone domain-ready portfolio**:
  portfolio-ivory-kappa-89.vercel.app (root=portfolio, verified).
- **GTM pack** `drafts\premium_buyers_gtm_2026-05-31.md` (where €4k+ buyers are + pitches + hit-list).
- **Launch posts** updated to the 4 new demos + IG + AIS: `drafts\launch_posts_2026-05-31.md`.
- **Ad image** 1080x1350: `C:\Users\Dell\kd-ad-ig.jpeg`. **Domain guide**: `drafts\domain_setup_2026-05-31.md`.
- Decisions: domain = personal name (kingdavidagbidi.com); spend = organic-first (NO paid ads; €226 held minus ~€12 domain).

## Next (distribution = the money lever)
1. KD buys kingdavidagbidi.com (guide ready) → tell Claude when live → link sweep.
2. MONDAY: KD posts launch content + the ad image (LinkedIn/IG/AIS/X). Update LinkedIn headline/About first.
3. Work the GTM hit-list: Claude finds live agency/startup buyers + writes pitches; KD sends + forwards replies.
4. KD sends the 7 freelance apps. Honest goal: Monday = in the €4k rooms; end of June = first €4k+. €0 earned still.
