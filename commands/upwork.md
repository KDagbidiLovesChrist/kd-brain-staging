# /upwork · Upwork Fit-Engine → Scored Jobs → Drafted Proposals

**Trigger:** King types `/upwork`, or says "score these Upwork jobs", "which Upwork jobs fit me", "draft my Upwork proposals", "find me Upwork work".
**Purpose:** Turn a batch of Upwork job posts into a **scored shortlist + a ready-to-send proposal for each strong fit**, each proposal backed by the one live demo that proves King can do it. Claude does everything except the tap-to-send. **King submits each proposal from his own Upwork account.**

> READ FIRST: master `CLAUDE.md` + `knowledge\demo_library.md` (the proof map) + `drafts\upwork_profile_setup_2026-05-31.md` (his profile + §8 proposal templates) + `memory\feedback_sound_human_not_ai.md`. This skill obeys all of them. It is the Upwork-specific sibling of `/apply` (`commands\apply.md`), same split, same honesty rules.

---

## Why this skill exists (the honest constraint)
Upwork killed its public RSS feed (2024), gates its job-search API behind developer approval, and hides job pages behind Cloudflare + a login wall. So there is **no clean auto-scan** like the Reddit scanner. **Phase 1 (this skill) = King pastes the jobs, Claude scores + drafts.** Phase 2 (later) adds an Apify auto-pull that writes the same jobs file. Either way the valuable part, *does it fit, and which demo proves it*, is identical.

**Connects matter:** every Upwork proposal costs King "Connects" (Upwork's paid credits). So **be selective**, only draft proposals for genuine high-fit jobs. The scoring below is what protects his Connects.

## The split (never broken)
- **Claude does:** score each job, kill scams/bad-fits, pick + verify the proof demo, draft the proposal in King's voice, build the send-pack, log it, and (on a reply) draft the response + build the won work.
- **King does ONLY:** the actual submit from his own Upwork account + forwarding replies. Reason: automating his logged-in Upwork risks an account ban (Upwork hunts for bots), and Claude has no access to his login.
- **Honesty rule:** never mark something `sent` King hasn't sent. Never fabricate awards, named testimonials, credentials or photos. Never send a dead demo link (verify HTTP 200 first). Never agree to go off-platform.

---

## INPUT · how jobs get in
King provides the jobs one of two ways:
1. **Pastes them into chat**, titles + links + descriptions copied from his logged-in Upwork search (sorted Newest, his filters from the profile setup).
2. **Saves them to a file**, `drafts\upwork_jobs_<today>.md`, one job per block. (Phase 2's `upwork_scan.py` will write this file automatically.)

If neither is present, ask King to paste a batch (and remind him: Upwork search → sort by Newest → copy the posts he's eyeing). Do not attempt to scrape or log into Upwork.

## STEP 1 · Score each job 0-100 (fit)
Score against King's **9 services** (websites · online stores/Shopify · SEO · marketing · content/social · AI automation/chatbots · SaaS · web/mobile apps · video editing, plus accessibility as a differentiator) and the `demo_library.md` proof map.

Weighted rubric:
- **Service match (0, 40):** is it squarely one of his services? Exact match = 40; adjacent = 20; not his service = 0.
- **Proof strength (0, 25):** do we have a strong, on-theme live demo (from `demo_library.md`)? Perfect-theme demo = 25; generic proof = 10; none = 0.
- **Budget fit (0, 15):** budget realistic + worth his time? Healthy fixed/hourly = 15; low-but-ok = 8; insulting = 0.
- **Client quality (0, 10):** payment-verified, good hire rate / reviews / spend = 10; unverified/new = 4; bad signals = 0.
- **Low competition / freshness (0, 10):** few proposals + posted recently = 10; crowded/old = 3.

**Bands:** 80, 100 = apply now (draft it) · 60, 79 = apply (draft it) · 40, 59 = stretch (draft only if a slow day / he asks) · <40 or any scam tell = **skip** (say why in one line).

## STEP 2 · Kill scams + bad-fit (before drafting)
**Skip + flag** any job with these tells:
- **Off-platform**, asks to chat/pay/verify on Telegram, WhatsApp, Signal, email, or crypto. Classic Upwork scam + a ToS violation. Never bite.
- **Free "test" task** disguised as a sample, or "do this small thing first unpaid".
- **Pay mismatched to skill**, big money for trivial work ("reply to messages, follow a script"), or pennies for a full build.
- **No real product/company named**, vague one-liners, "data entry" fronts for something else.
- **Full-time / salaried / on-site / visa / geo-locked** roles he can't take (he has Amazon; this is freelance only).
- **Faith conflicts**, gambling, alcohol, adult, occult/tarot, deception (`feedback_faith_values_filter.md`).

Real buyers name a specific deliverable + budget and often ask to see work. Full scam list: `memory\project_freelance_applications.md`.

## STEP 3 · Pick the proof demo (and verify it)
For each job scored ≥60 (or a stretch King asks for):
1. From `knowledge\demo_library.md`, pick the **1, 2 closest demos to THEIR world** (a clinic → LUMÉ, a store → AMBRÉ, an AI/automation job → NEXA/Lead Finder, accessibility → HAVEN/LUMINA, video → video-samples, etc.). Lead with the single best match.
2. **Verify each chosen URL is HTTP 200 before it goes in the proposal** (`Invoke-WebRequest <url> -Method Get -TimeoutSec 20 -UseBasicParsing`). If a link is dead, pick the next-best live demo. Never send a dead link.
3. For a genuinely high-ticket job with budget for it, optionally offer to build a **personalised demo of THEIR brand** first (the `/apply` Step 3 method), but for most Upwork bids the existing library demo + a small-milestone offer is the right, fast move.

## STEP 4 · Draft the proposal (King's voice)
Base it on `drafts\upwork_profile_setup_2026-05-31.md` §8 (General + Stretch-fit templates). Keep it **short, clients skim Upwork**. Structure:
1. **Personalised hook**, name the one specific thing in their post (proves it's not copy-paste). Skip "Dear hiring manager" filler.
2. **Proof, not promise**, *"I've already built one like this, here it is: [the matched live demo]."* (AIS framing: "I built X, it works, let me adapt it for you", not "I can build X".)
3. **One discovery question**, opens a conversation, surfaces their real constraint.
4. **Low-friction close**, a **small first milestone or free sample** so they see quality before committing.
5. **Pricing**, outcome/milestone framing, right-sized to the post's budget. Never quote dev hours.

**Hard voice rules:** warm, plain English, faith-first. **Zero em-dashes** (`feedback_sound_human_not_ai`). No jargon, no hype, no fabricated credentials. Match King's profile rate ($30/hr founder rate or fixed milestone).

## STEP 5 · Output the send-pack
Write everything to `C:\Users\Dell\.claude\drafts\upwork_applications_<today>.md`. One block per job:
```
### [score/100] <Job title>
- Link: <upwork job url>
- Matched service: <service>  |  Budget: <what they posted>  |  Competition: <if known>
- Proof demo (verified 200): <demo url>
- PROPOSAL (paste into the Upwork proposal box):
  <full proposal text>
- SENT? [ ]
```
Put the highest scores first. Add a one-line "why this scored what it did" under each. Skipped jobs go in a short **"Skipped (and why)"** list at the bottom so King sees the engine's reasoning.

Then log each drafted one as `ready_to_send` in `knowledge\clients.md`, and ping his phone:
```
python "C:\Users\Dell\.claude\tools\push_kd.py" "Upwork pack ready: <N> scored proposals. Open the send-pack and submit the strong ones."
```

## STEP 6 · King submits → forwards replies → Claude responds
- King opens each job in his Upwork, pastes the proposal, submits, ticks `SENT?`.
- He forwards every reply. Claude drafts the response, and **on a yes, builds the full deliverable** (or the personalised demo if that's the agreed next step).
- Mark `won` in `knowledge\clients.md` **only when cash clears** (`memory\project_first_client_FALSE_ALARM_2026-05-25.md`, no "client" without a receipt). Keep all money on Upwork until a relationship is established.

---

## Tools used
- `knowledge\demo_library.md` (proof map) · `drafts\upwork_profile_setup_2026-05-31.md` (profile + templates) · `tools\push_kd.py` (phone ping) · `Invoke-WebRequest` (verify demo links) · WebFetch (optional: read a prospect's own site for a personalised demo) · `knowledge\clients.md` (pipeline log).

## Phase 2 · Apify auto-pull (NOT built yet; add after Phase 1 is proven)
`tools\upwork_scan.py` (LAPTOP-ONLY: lives outside the synced brain — not built yet) will call a maintained Apify Upwork-jobs actor (`APIFY_API_TOKEN` + residential proxy from `.env.master`) with King's keywords/categories, pull fresh listings, run a FIT/BAD first pass, and write them to `drafts\upwork_jobs_<today>.md` for this skill to score. Caveats: brittle (breaks when Upwork changes its page), small Apify compute cost, ToS-grey. Pick + verify the actor at build time; test the cheapest first.

## Done =
A reviewed send-pack: every strong-fit Upwork job scored, the scams called out, each with a verified proof demo + a short proposal in King's voice, logged and phone-pinged. **The bottleneck this fixes: SENDING.** Building was never the problem, King submits, replies come, deals close.
