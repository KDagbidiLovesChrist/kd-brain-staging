# /apply · Find Buyers → Personalised Demo → Drafted Application

**Trigger:** King types `/apply`, or says "draft today's pitches", "scan and apply", "find me work", "apply for jobs".
**Purpose:** Turn live buyer/[HIRING] posts into ready-to-send applications, each with a **personalised, transformative demo** of that prospect's own brand and an application written the **AIS selling way**. Claude does everything except the tap-to-send. **King sends from his own accounts.**

> READ FIRST: master `CLAUDE.md` + `memory\project_freelance_applications.md` + `memory\feedback_personalised_demos.md`. This skill obeys all of them.

---

## The split (never broken)
- **Claude does:** scan, judge fit, WebFetch the prospect's brand, build + deploy the personalised demo, QA it, write the application + every reply, build the won work, log it.
- **King does ONLY:** the actual tap-to-send from his own accounts (Reddit / email / form / platform) + forwarding replies. Reason: auto-posting from his accounts gets them BANNED (Reddit + Gmail bot detection), and Claude has no access to his logins.
- **Honesty rule:** never mark something `sent` that King hasn't sent. Never fabricate awards, named testimonials, credentials or photos, use clearly-labelled placeholders.

---

## STEP 1 · Scan where the buyers hang out
Run the existing scanner (do NOT rebuild it):

```
python "C:\Users\Dell\.claude\tools\daily_client_scan.py"
```

- It pulls live `[HIRING]`/`[task]` posts from Reddit (forhire, freelance_forhire, jobbit, DesignJobs, web_design, slavelabour, hiring, DoneDirtCheap, Design_to_Hire, HireaWriter, Wordpress, shopify, webdev, digital_marketing, Entrepreneur) + HackerNews "SEEKING FREELANCER", filters to King's services, and writes `drafts\daily_clients_<today>.md`.
- If the file for today already exists, read it instead of re-running.
- Method/fallback details: `memory\reference_reddit_job_scan.md` (RSS + browser User-Agent; `.json` is 403-blocked).
- The big-money channels (Contra, PeoplePerHour) can't be scanned by bot, surface those from `drafts\buyer_setup_2026-06-03.md` and remind King to browse them by hand.

## STEP 2 · Judge fit + kill scams
For each post, keep only **genuine fits for King's arsenal**: websites · landing pages · Shopify / online stores · AI automation / chatbots · SEO · social / content · video editing · accessibility · writing/copy.

**SKIP:** full-time salaried roles (he has Amazon), specialist trades he doesn't do (native iOS, backend/QA, illustration), geo-restricted roles he can't qualify for, and faith conflicts (gambling, alcohol, adult, occult/tarot, deception), see `memory\feedback_faith_values_filter.md`.

**Scam tells (skip):** pay mismatched to skill, big money for no skill ("reply to chats, follow scripts"), no company/product named, pay-to-start / crypto, commission-only cold-calling. Real buyers name a specific skill + deliverable and often ask to see work. Full list: `memory\project_freelance_applications.md`.

Present King the shortlist (5-10 best) and the reason each made the cut, before building. (If he already said "do them all", proceed.)

## STEP 3 · Build a PERSONALISED, transformative demo per prospect
**This is the differentiator. Never send a generic showcase link.** (`memory\feedback_personalised_demos.md`)

For each chosen prospect:
1. **WebFetch their live site / profile** for real brand: name, colours, fonts feel, tone, content, and the one thing their current site is **missing**.
2. **Clone the closest existing proof** as a structural base, then **re-theme fully to THEIR brand**, it must read as *their brand levelled up*, not a different premium brand pasted on. Reuse only primitives; each demo its **own world** (`memory\feedback_each_3d_world_truly_unique.md`).
3. **Build in the specific missing feature** (e.g. before/after gallery + booking for a clinic, working cart for a store, immersive gallery for a builder, 3D showroom for a kitchen maker).
4. **Right-size to budget**, most small local businesses get a clean premium Signature-tier build, NOT a forced €4k 3D flagship. Save heavy 3D for genuine high-ticket visual trades. (`Website Builder\PRICING.md`)
5. **Deploy to its own Vercel project** (`[slug].vercel.app`), then **QA**: HTTP 200, zero console errors, screenshot. Do NOT add to the shared `kd-demos` bundle (gen_premium.py wipes it).
6. Use parallel agents to build several at once when the batch is large.

## STEP 4 · Write the application the AIS selling way
Voice = King's (warm, plain English, faith-first). **Zero em-dashes** (`memory\feedback_sound_human_not_ai.md`). Structure every application/DM:

1. **Personalised hook**, name them + one specific, true observation about their business or post (proves it's not copy-paste).
2. **Proof, not promise**, *"I already built you a sample of this, here it is: [their personalised demo link]."* (AIS framing: "I built X, it works, let me adapt it for you", not "I can build you X". `knowledge\ais_master_summary.md` §15.3.)
3. **One discovery question**, open a conversation, learn their real constraint (the income/time lens: "what would 2x leads break first?"). Don't pitch everything.
4. **Demo-first close**, low-friction next step: *"If you like it, I'll finish the full build. You only pay if you love it."* Front-end demo beats any spec. (§17.1)
5. **Pricing**, outcome/retainer framing, never dev hours. Right-sized to the post's budget.

Keep it short, human, and specific. No jargon, no hype, no fabricated credentials.

## STEP 5 · Output the send-pack (King's single source of truth)
Write everything to `C:\Users\Dell\.claude\drafts\applications_<today>.md`:
- One block per prospect: the post link + channel (Reddit comment/DM, email, form, platform bid), the personalised demo URL, the full application text, and a **`SENT? [ ]`** checkbox.
- A short "where to paste / how to send" line per prospect.
- Log each as `ready_to_send` in `knowledge\clients.md`.

Then tell King the pack is ready and ping his phone:
```
python "C:\Users\Dell\.claude\tools\push_kd.py" "Applications ready: <N> personalised pitches. Open the send-pack and tap send."
```

## STEP 6 · King sends → forward replies → Claude responds
- King taps-send each from his own accounts, ticks `SENT?`.
- He forwards every reply. Claude drafts the response, and **on a yes, builds the full deliverable.**
- Mark `won` in `knowledge\clients.md` **only when cash clears** (`memory\project_first_client_FALSE_ALARM_2026-05-25.md`, no "client" without a receipt).

---

## Where King's buyers hang out (money order · see `drafts\buyer_setup_2026-06-03.md`)
1. **Contra + PeoplePerHour**, where the $1k, $25k jobs live (browse by hand; Claude drafts every bid).
2. **Fiverr**, buyers search to him (publish the 5 remaining gigs).
3. **Discord / Slack / Facebook**, passive trickle (post only in for-hire/showcase channels).
4. **Bark.ie**, paid lead-gen (only respond to well-budgeted requests).
Reddit + HackerNews (Step 1) feed the proactive applications. Default to **global markets, not narrow niches** (`memory\feedback_pivot_to_global_market.md`). **AIS+ posting is OFF the table** unless King reopens it.

## Tools used
- `tools\daily_client_scan.py` (scan) · `tools\scan_leads_now.py` (on-demand variant) · `tools\push_kd.py` (phone ping) · Vercel CLI (deploy demos) · WebFetch (prospect brand) · parallel agents (batch builds).

## Done =
A reviewed send-pack of personalised demos + AIS-style applications, each deployed (HTTP 200) and shown to King, with phone ping sent. **The bottleneck this fixes: SENDING.** Building was never the problem.
