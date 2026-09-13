---
name: knowledge-demo-library
description: "King's live demo arsenal mapped by service, the lookup that answers 'which demo proves I can do this job'. Read by /upwork and /apply to pick the right proof link. URLs last verified HTTP 200 on 2026-06-06."
---

# Demo Library · Service → Proof Map

The single source of truth for **"which live demo proves King can do this job."**
Read by `/upwork` (Step 3) and `/apply` (Step 3) to pick the strongest proof link for a prospect.

## Rules (read before using any link)
1. **Verify HTTP 200 before a link goes in any proposal or message.** Vercel aliases drift.
   Quick check: `Invoke-WebRequest <url> -Method Get -TimeoutSec 20 -UseBasicParsing` → expect 200.
2. **Pick 1, 2 demos max per pitch**, the closest match to *their* brand/need, not a wall of links.
3. **Lead with the demo that matches their world** (a clinic → LUMÉ, a store → AMBRÉ, an AI job → NEXA).
4. Black+gold personal sites (kingdavidagbidi.com) are KD's **own** brand, use them to show "this is
   the bar I build to," never as a client's brand example.
5. URLs last verified **2026-06-06**. The bare `kd-demos.vercel.app` root is a 404, always use
   `/portfolio`, `/shopify`, or a specific `/<slug>/`.

---

## The map (by service)

| Service King offers | Best proof demo(s) | Live URL | One-liner |
|---|---|---|---|
| **Websites / web design (flagship 3D)** | LUMÉ aesthetic clinic | https://lume-clinic.vercel.app | Warm luxury clinic site with a soft glowing 3D serum drop. |
| | AXION fintech | https://axion-fintech.vercel.app | Near-black + cyan with a kinetic glowing 3D wireframe. |
| | AURUM fine jewellery | https://aurum-fine.vercel.app | Charcoal + gold with a slow faceted 3D gem. |
| | VERDE botanical wellness | https://verde-wellness.vercel.app | Sage + terracotta with a flowing organic 3D ribbon. |
| **Cinematic scroll-scrub sites (whole-page AI video journey)** | ISOLA (hospitality / private island) | https://kd-isola.vercel.app | The whole page is an AI cinematic flight from a bright aerial down into a beachfront villa, scrubbed on scroll. Best for hospitality / resort / luxury travel. |
| | MARÉA (private estates / real estate) | https://kd-marea.vercel.app | Warm villa journey with serif chapters over moving footage. Best for real estate / property / luxury homes. |
| | AETHER (space / tech / bold brand) | https://kd-aether.vercel.app | Deep-space flight toward a planet. Best for tech / AI / ambitious "frontier" brands. |
| | ASCENT (architecture / construction) | https://kd-ascent.vercel.app | A tower assembling itself at golden hour. Best for architecture / construction / engineering. |
| **Immersive 3D morphing flythrough (TOP web flagship)** | LUMO (calm AI product) | https://kd-claude-studio.vercel.app | One particle cloud MORPHS through 5 worlds on scroll (galaxy→city of light→ocean→data-network→core), drag/spin the core, tap-to-burst, ambient sound, + a calm AI chat mockup. Real-time Three.js + cinematic bloom, seamless loop. THE top wow piece. Best for AI / SaaS / tech / creative brands. Skill: `/immersive-site`. Built 2026-06-09. |
| **Real-time 3D CITY flythrough (TOP property/architecture flagship)** | **AUREO · fly through a living city** | https://kd-aureo.vercel.app | A real-time low-poly NEON city you FLY THROUGH on scroll: photoreal **golden→dusk→night** sky, real districts + lived-in venues (shops/school/hospital/police/mall/bank/gym/bar/stalls), **crowds + kids + orderly traffic**, proper roads/pavements/canal-bridges, a Penthouse property listing card, LED art billboards. ~1.2s load, **60fps on mobile**, passed a strict multi-angle/multi-device clipping QA (0 issues). **THE proof for property / real-estate / architecture / city-development / luxury / ambitious-brand jobs.** Engine/method: `memory\reference_lived_in_city_engine.md`. Source: `Documents\Website Builder\replicas\aureo\`. Built + King-approved 2026-06-09 (verified 200). |
| **Websites (range + small-biz)** | Portfolio of unique designs | https://kd-demos.vercel.app/portfolio | 6 hand-built unique layouts + pricing tiers. |
| **Website · recruitment / application-form / lead-capture** | OceanHire (tailored maritime recruitment site) | https://kd-oceanhire.vercel.app | A full professional recruitment site: hero, departments grid, about, a COMPLETE multi-section application form (personal + professional + document uploads + motivation), FAQ, contact. Maritime theme, mobile-first. **USE/ADAPT for any recruitment / agency / application-form / candidate-database website job.** Source: `Documents\Website Builder\kd-oceanhire\`. Built 2026-06-09. |
| | Local one-pagers (146 live) | https://kd-demos.vercel.app/&lt;slug&gt;/ | Per-shop premium one-pagers (barber/home-service), real photos + reviews. |
| | The studio hub | https://kd-hub-bay.vercel.app | All services in one place · the front door. |
| **Online stores / e-commerce / Shopify** | AMBRÉ fragrance store | https://ambre-store.vercel.app | Premium store with a real working cart. |
| | Shopify store designs | https://kd-demos.vercel.app/shopify | 4 store mockups + launch pricing. |
| **Real-time 3D / WebGL** | LUMÉ · AXION · AURUM · VERDE | (URLs above) | The "looks like it cost a fortune" tier. |
| | LUMINA (3D + accessible) | https://a11y-3d.vercel.app | The rare combo: a 3D hero that's also fully accessible. |
| **Accessibility (WCAG)** | HAVEN | https://a11y-demo-gamma.vercel.app | Dark/light, dyslexia font, calm mode, instant EN/ES. |
| | LUMINA | https://a11y-3d.vercel.app | Accessible AND real-time 3D · most studios can't do both. |
| **SEO** | ASCEND | https://ascend-marketing-gold.vercel.app | Marketing + SEO landing experience. |
| **Marketing / landing pages** | ASCEND | https://ascend-marketing-gold.vercel.app | Conversion-focused marketing landing. |
| **AI automation / chatbots** | NEXA | https://nexa-ai-delta-flax.vercel.app | AI / automation studio site. |
| | Lead Finder | https://lead-finder-coral-delta.vercel.app | Automated lead-gen that finds fit-right customers daily. |
| | **LessonForge** (LIVE AI tool · tailored for the education/curriculum Upwork job) | https://lessonforge-demo.vercel.app | A genuinely working AI content pipeline: type topic + objective + grade → generates a full structured lesson draft live (Claude Haiku behind a hidden server key, ~fractions of a cent/run). Proves "I build real AI workflows," not just talk. Source: `Documents\Website Builder\lessonforge-demo\` (index.html + api/generate.js; Vercel env var ANTHROPIC_API_KEY, runtime-sanitised for BOM). Reuse pattern for any "AI that generates X" demo. |
| **n8n · service-business automation (booking / CRM / leads)** | **Studio Flow** (tailored yoga build) | https://kd-studio-flow.vercel.app | A real yoga-studio n8n engine (4 lanes): website form -> GoHighLevel contact -> WhatsApp confirmation -> Supabase log -> wait + attendance check -> onboarding sequence OR no-show rebooking nudge; a VAPI voice receptionist (Claude); a WhatsApp FAQ/lead-capture bot with human handoff; and an error-trigger that logs + alerts. **USE THIS for any service-business automation job (booking, no-show recovery, GoHighLevel, VAPI/voice, WhatsApp/Twilio chatbot, CRM, lead capture)** · yoga/fitness/wellness/trades/clinics/salons. Source: `demos\yoga-studio-flow\`. Built 2026-06-09. |
| **n8n · agentic / RAG / framework-as-a-service** | **Contractor Engine** | https://kd-n8n-proof.vercel.app | A 4-workflow n8n engine: orchestrator (webhook -> load state -> Ollama embed -> pgvector RAG -> Claude supervisor agent -> write state back) + Score & Advance + daily Staleness Watchdog + Ingest & Embed. Multi-tenant by `contractor_id`, error-trigger logging, secrets from `$env`. **USE THIS for jobs about an AI AGENT with MEMORY/RAG, a methodology/framework engine, or multi-tenant per-client state** · NOT for a plain booking/CRM job (use Studio Flow for those). Source: `demos\n8n-contractor-engine\`. Built 2026-06-08. |
| **n8n RAG support / docs Q&A (LIVE working tool)** | **RAG Support Assistant** | https://kd-rag-support.vercel.app | A REAL grounded support assistant: type a customer question → keyword retrieve from a sample doc set → Claude Haiku answers **only** from those passages **with a citation (doc ID)**, and **escalates to a human instead of guessing** when the answer isn't in the docs. Shows the n8n flow (trigger→retrieve→ground→draft/escalate). **USE THIS for any "n8n RAG / answer support tickets from our docs / no-hallucination chatbot" job** · beats the Contractor Engine link for support-RAG specifically. Serverless pattern = CopyForge. Source: `Documents\Website Builder\kd-rag-support\`. Built 2026-06-09. |
| **WhatsApp AI concierge + Odoo/CRM (tailored)** | **Panama Concierge** | https://kd-panama-concierge.vercel.app | Tailored "Sightseeing Panama" demo: press play → a WhatsApp enquiry comes in, the assistant qualifies it, a **live Odoo CRM panel** fills in (contact, service, tags New→Hot Lead, pipeline stage) and the hot lead is **handed to a human**. **USE/ADAPT for any WhatsApp concierge / lead-qualify / CRM-sync / human-handoff job** (tours, relocation, concierge, high-touch service). Static, no backend. Source: `Documents\Website Builder\kd-panama-concierge\`. Built 2026-06-09. |
| **AI content generation tool (marketing)** | **CopyForge** (LIVE working tool) | https://kd-copyforge.vercel.app | A real AI marketing-content generator: product + channel + tone in -> 3 on-brand variations + hashtags + CTA + tip out, live (Claude Haiku via a Vercel serverless fn, key server-side). **USE THIS for any "AI that generates marketing/social/ad/email copy" or AI-content-platform job.** Same serverless pattern as LessonForge; build on OpenAI or Claude to fit the client. Source: `Documents\Website Builder\kd-copyforge\`. Built 2026-06-09. |
| **Content-ops / creator automation** | **FlowLine** (static content-ops dashboard demo) | https://kd-flowline.vercel.app | A clean creator content-ops dashboard: post schedule (live/queued), buffer gauge + low-buffer flag, pre-post QC checks, auto end-of-day report, verified-research note. Static (no backend, $0). Source: `Documents\Website Builder\kd-flowline\`. Powers the "Creator Content-Ops" gig card on kingdavidagbidi.com + the `offer_ai_content_ops_for_creators` pitch. |
| **Lead generation** | Lead Finder | https://lead-finder-coral-delta.vercel.app | Same · pairs with the `/scrape` CSV gig. |
| **Lead/reservation engine (venue, tailored)** | **Venue Reservation Engine** | https://kd-venue-leads.vercel.app | Press start → enquiries arrive from web/WhatsApp/Instagram, AI qualifies them in seconds, they become **booked reservations** with **no-shows auto-recovered**; live stat cards tick up. **USE THIS to reframe any "lead generator / get us bookings" job as a SYSTEM build (not a manual SDR).** Static, no backend. Source: `Documents\Website Builder\kd-venue-leads\`. Built 2026-06-09. |
| **Video editing / short-form** | Video samples | https://video-samples.vercel.app | Cinematic short-form for Reels / TikTok / Shorts. |
| **Content / social** | Video samples (visual) | https://video-samples.vercel.app | Short-form content proof; pair with newsletter for written. |
| **Newsletter / email marketing** | `/newsletter` engine | (no public demo · offer a free 1-issue sample) | Research → write → HTML → send. Sell €50-200/mo. |
| **SaaS / web & mobile apps** | RELAY CRM (real, working app) | https://relay-crm-one.vercel.app | A genuinely functional SaaS: real signup/login, live Postgres database, clients + deals pipeline + tasks with full CRUD, live dashboard charts, per-user security (RLS). Anyone can sign up and use it. The proof King builds apps "businesses buy & use", not just front-ends. |
| **SaaS · vendor/procurement (tailored)** | VendorIQ (re-themed off RELAY for the Upwork Vendor Portal job) | https://vendoriq-demo.vercel.app | Working Vendor Qualification Portal: supplier profiles, qualification pipeline (New→Screening→Assessment→Approved→Rejected), onboarding tasks, live dashboard. Next.js + Supabase. Source: `Documents\Website Builder\vendoriq-demo\`. Pattern = copy relay-crm, re-theme display strings only, deploy as new Vercel project. |
| **Web PDF editor / document tooling (LIVE working tool)** | **Web PDF Editor** | https://kd-pdf-editor.vercel.app | A real in-browser PDF editor: upload (drag-drop) → render with **PDF.js** (page nav + zoom) → **pdf-lib** edits that actually work (add text stamp, rotate page, delete page) → download the edited file; plus an honest **Stirling-PDF** server-side panel for destructive redaction/OCR/flatten (architecture + disabled button, not faked). All client-side, no backend. **USE THIS for any PDF-manipulation / document-editor / PDF.js / pdf-lib job.** Built 2026-06-09 (agent). Source: `Documents\Website Builder\kd-pdf-editor\`. |
| **Award-tier photoreal flagships (the top bar)** | NIVA · cinematic scroll-scrub | https://kd-niva-ice.vercel.app | Foggy-valley igloo that physically pushes in as you scroll (real Seedance camera move, frame-scrubbed on a canvas). igloo.inc-tier. |
| | ATRIA · white architectural | https://kd-atria.vercel.app | Light-mode luxury "premium workspace" brand: giant kinetic letters + a photoreal white sculptural hero. |
| | PRISMA · iridescent studio | https://kd-prisma.vercel.app | Liquid-chrome interactive-studio site; doubles as a studio reel (links to real RELAY/VendorIQ/NIVA work). |
| | FORMA · cream museum/exhibition | https://kd-forma.vercel.app | Luxury art-exhibition microsite: filigree sphere, elegant serif, soft museum light. |

> The 4 flagships above are King's **own original brand concepts** built to match award-site references (igloo.inc / aircenter / shader.se / Art Here). Use them like the black+gold sites, "this is the award-site bar I build to", not as a client's brand example. Method: `memory\reference_photoreal_flagship_method.md`. Verified 200 on 2026-06-08.

---

## KD's own standard-setters (show the bar, not as a client example)
- **kingdavidagbidi.com**, live personal flagship (black+gold, cinematic gallery). The quality bar.
- **kd-site-v2.vercel.app**, the approved personal site build behind the domain.

## Tier / pricing hint (full detail: `Website Builder\PRICING.md`)
- **Standard one-pager** ~€99 + €39/mo · **Signature** premium custom · **3D / Seedance flagship** €4k+.
- Right-size to the job's budget, most small clients get a clean Signature build, NOT a forced 3D flagship.
- Default close: a **small first milestone or free sample** so they see quality before paying.

## Maintenance
- Re-run the HTTP 200 sweep (the 17 URLs above) whenever a demo is redeployed or an alias changes.
- New flagship/animated deploys (e.g. the `-animated` cinematic set) can be added here once their
  live URLs are confirmed 200, keep this map the one place demos are listed so `/upwork` + `/apply`
  stay in sync. Keep the file under 500 lines.
