# Client-Projects Tool Research - Full Briefs (2026-06-22)

# TRACK: webdesign

The exact Aceternity Pro license terms didn't load cleanly, so I'll flag that as "verify." I have enough verified data to deliver the briefing.

---

# Research Track: Best Tools to Build a Top-Tier Course/Community Sales Site (Hustlers-University vibe) in Claude Code

**For:** Olly's premium paid-course / community site. King's strongest lane (websites). Goal = a custom, "design however we want" sales site, built fast inside Claude Code.

**Key framing:** Two separate jobs here. **(A) The marketing/sales site** (the landing page that sells the course, this is the "Hustlers University vibe" and where King's web arsenal shines). **(B) The actual course/community engine** (login, paid members, lessons, chat). King should NOT hand-build B from scratch, that's a solved, sellable platform decision. Most tools below solve A. I cover B at the end because skipping it would leave the build half-finished.

---

## A. Tools for the SALES SITE (build inside Claude Code)

### 1. shadcn/ui + the shadcn MCP · **FREE** ⭐ core
- **What:** Open-source React/Tailwind component system (buttons, cards, dialogs, pricing blocks). The official **shadcn MCP server** lets Claude Code browse/install components by plain-English request ("add a pricing section"), pulling real code instead of guessing.
- **Price:** Free, MIT-licensed, no API key, runs locally. Commercial use allowed.
- **Claude Code fit:** Best-in-class. It's an MCP, drops straight into King's existing workflow (same pattern as his playwright/firecrawl MCPs). This is the biggest genuine upgrade to his current "/website hand-coded HTML/CSS" approach.
- **Non-technical fit:** High, King describes, Claude installs verified components. Note: it's React/Next.js, a step up from his plain HTML/CSS. Worth it for a premium build.
- **Verdict: INSTALL. The free backbone.** Beats hand-coding from scratch and reduces Claude's guesswork (their own pitch: cuts "looks right but fails at runtime" errors).
- Sources: [ui.shadcn.com/docs/mcp](https://ui.shadcn.com/docs/mcp), [shadcn.io/mcp/claude-code](https://www.shadcn.io/mcp/claude-code)

### 2. Magic UI · **FREE** ⭐
- **What:** 50+ animated React components (Framer Motion + Tailwind), marquees, animated beams, shimmer buttons, particle effects. The "expensive/hyped" look Hustlers-style sites use.
- **Price:** Fully free and open source.
- **Claude Code fit:** Installs via the shadcn registry/CLI, so the same MCP flow reaches it. Pairs perfectly with #1.
- **Non-technical fit:** High via Claude.
- **Verdict: INSTALL alongside shadcn.** Free premium polish. This is what makes a $0 stack look like a $4k site.
- Source: [Design Systems Collective review](https://www.designsystemscollective.com/the-ui-component-libraries-that-actually-save-hours-part-1-3-e9503b3d8642)

### 3. Aceternity UI · **FREE core / $199 Pro one-time (verify license)**
- **What:** 200+ animation-heavy React/Tailwind/Framer-Motion components, the most "premium agency" aesthetic of the free libraries. Free tier is MIT (commercial OK). Pro adds templates + premium blocks.
- **Price:** Free tier MIT-licensed. **Pro = $199 one-time, lifetime updates** (per search results, but I could **not** load the live pricing/license page to confirm the $199 figure *or* whether the Pro license permits reselling client sites. **Verify both before paying.**)
- **Claude Code fit:** Free components install via shadcn registry. Pro templates are a manual download King points Claude at.
- **Verdict: Use the FREE tier now (huge value).** Only consider Pro once a paying client (Olly) is signed and a specific template saves real hours, and only after verifying the resale license.
- Sources: [ui.aceternity.com](https://ui.aceternity.com/), [Tiny Startups review](https://www.tinystartups.com/tools/aceternity-ui)

### 4. 21st.dev (Magic MCP) · **FREE tier (100 credits/mo) / $20/mo Pro**
- **What:** "Magic" MCP that generates UI component variations from a prompt; also a marketplace of community shadcn components.
- **Price:** Free = 100 credits/month, usage-based. Pro = $20/mo. (Currently in beta, some features free during beta, so **verify live credit limits**.)
- **Claude Code fit:** It's an MCP, installs like shadcn's. Good as an *idea generator* (multiple variations, pick one).
- **Verdict: OPTIONAL.** Overlaps heavily with shadcn MCP + Magic UI, which are free and already cover King's needs. Try the free tier only if he wants on-the-fly variations. Don't pay $20/mo yet.
- Sources: [help.21st.dev/magic-chat/pricing](https://help.21st.dev/magic-chat/pricing), [21st.dev/mcp](https://21st.dev/mcp)

### 5. Tailwind Plus (formerly Tailwind UI) · **$299 one-time, personal**
- **What:** Official Tailwind 500+ pro UI blocks + full site templates (React/Next). Battle-tested, clean, conversion-focused (not as flashy as Aceternity).
- **Price:** $299 one-time personal / $979 team, lifetime access incl. future content. No subscription.
- **Claude Code fit:** Manual asset, King buys, points Claude at the files. No MCP.
- **Verdict: SKIP for now.** It's solid but $299 buys polish King already gets free from shadcn+Magic UI. Revisit only if he's doing this repeatedly for paying clients and wants premium templates as a time-saver.
- Source: [tailwindcss.com/plus](https://tailwindcss.com/plus), [Tailwind Plus announcement](https://tailwindcss.com/blog/tailwind-plus)

### 6. v0.dev (Vercel) · **FREE ($5 credits, 7 msgs/day) / $20/mo Premium**
- **What:** Vercel's AI UI generator, describe a UI, get React/shadcn/Tailwind code. Output drops cleanly into a Claude Code project and deploys to King's existing Vercel.
- **Price:** Free = $5 credits/mo + 7 messages/day (credits burn on token usage, runs out fast). Premium = $20/mo. Team $30/user.
- **Claude Code fit:** Good handoff, generates the exact shadcn/Tailwind stack Claude then edits. Same Vercel account King already uses.
- **Verdict: Use the FREE tier as a starting-point generator.** Don't subscribe, Claude Code + shadcn MCP already does most of this for free. Free v0 is handy for a fast first draft of a hero/pricing section, then Claude refines.
- Sources: [v0.app/pricing](https://v0.app/pricing), [Vercel updated v0 pricing](https://vercel.com/blog/updated-v0-pricing)

### 7. Lovable.dev · **FREE (5 credits/day) / $25/mo Pro**
- **What:** Full "vibe-coding" app builder, generates a whole working app (front + back) from prompts.
- **Price:** Free = 5 daily credits (~30/mo). Pro = $25/mo. Credit-based; real projects exhaust free fast.
- **Claude Code fit:** **Weak, it's a competing environment, not a Claude Code plugin.** Code lives in Lovable's app; exporting to King's workflow is friction.
- **Verdict: SKIP.** It duplicates what King already has (Claude Code builds the app). Paying $25/mo for a parallel builder breaks lean-spend.
- Sources: [lovable.dev/pricing](https://lovable.dev/pricing), [No Code MBA](https://www.nocode.mba/articles/lovable-pricing)

### 8. Framer · **FREE (branded) / $10 Basic / $30 Pro per site**
- **What:** Visual no-code site builder with gorgeous templates + animations. Hosts the site itself.
- **Price:** Free = Framer subdomain + Framer branding. Basic $10/mo (custom domain), Pro $30/mo (CMS/forms). Editor seats now $20/mo.
- **Claude Code fit:** **None, it's a closed visual editor, not code.** Doesn't fit "build in Claude Code."
- **Verdict: SKIP for King's workflow.** It's a different way of working (he'd design by hand in Framer, not via Claude). Only relevant if a client specifically wants to self-edit later.
- Source: [framer.com/pricing](https://www.framer.com/pricing)

### 9. Webflow · **FREE (subdomain) / $15 Basic / ~$25-39 Premium per site**
- **What:** Pro visual website builder + CMS. Powerful, designer-favourite, hosts the site.
- **Price (May 2026 update):** Free Starter (2 pages, Webflow badge). Basic $15/mo yearly. Premium $25/mo yearly ($39 monthly). Team $2,500/mo (irrelevant).
- **Claude Code fit:** **None, closed visual builder.** Same mismatch as Framer.
- **Verdict: SKIP for the build.** Adds monthly cost + a non-code workflow King doesn't need. He owns Vercel hosting for free.
- Sources: [webflow.com/pricing](https://webflow.com/pricing), [Webflow May 2026 pricing](https://help.webflow.com/hc/en-us/articles/51059955082387-Updated-pricing-and-simplified-plans-for-May-2026)

---

## B. The course/community ENGINE (don't hand-build · this is the other half)

A "Hustlers University" site is a sales page **plus** a paid members area (login, lessons, chat, leaderboards). King's web skills nail the sales page; the members area is a platform choice, not a code project. Honest options:

- **Skool, $99/mo flat.** What Hustlers University / The Real World actually feels like (community + courses + gamification). Unlimited courses/members. *Olly (the client) pays this, not King.* King builds the premium **sales/landing site** that funnels into it.
- **Whop, $0/mo, takes a % per sale.** Best if Olly sells access/files and wants zero fixed cost. Strong commerce, lighter community.
- **Self-hosted (WordPress + FluentCommunity $159/yr or BuddyBoss $299/yr):** zero platform cut, Olly owns everything via Stripe. More setup, but King *could* charge to build/manage it, a bigger paid scope.

**Honest take:** For speed and the authentic Hustlers vibe, the play is **King builds a custom premium sales site (free stack below) → it sells into Skool or Whop** that Olly owns. Don't reinvent the members area. If Olly wants everything self-owned and is willing to pay King more, the WordPress route is the upsell.
Sources: [Skool alternatives 2026](https://www.creatoreconomytools.com/blog/skool-alternatives-2026), [Whop blog](https://whop.com/blog/skool-alternatives/), [Kajabi alternatives / Mighty Networks](https://www.mightynetworks.com/resources/kajabi-alternatives)

---

## Bottom line

### Best FREE combo (recommended · start here) ⭐
**Claude Code + shadcn MCP + Magic UI + Aceternity (free tier) → deploy to King's Vercel**, with **free v0.dev** as an optional first-draft sketcher. Sales site funnels into **Skool ($99/mo, paid by Olly)** or **Whop ($0)** for the actual course/community.
- **Cost to King: €0.** This genuinely beats his current hand-coded HTML/CSS, the shadcn MCP gives Claude *real, verified components* instead of guessing, and Magic UI/Aceternity supply the expensive animated look for free.
- This is also a React/Next step up from plain HTML/CSS, a one-time learning curve, but it's where premium web work lives.

### Best PAID combo (only after Olly signs)
Same free core **+ Aceternity Pro (~$199 one-time, verify price & resale license) and/or Tailwind Plus ($299 one-time)** for premium templates that save hours on repeat client work. Both are one-time, not subscriptions, lean-spend friendly.
- **Is paid worth it over free? Not yet.** The free combo already produces a top-tier result. Buy a one-time template pack *only* when a paying client is locked and a specific template demonstrably saves hours. **Avoid all monthly subscriptions** (v0 Pro, Lovable, 21st Pro, Framer, Webflow), they duplicate what Claude Code + free MCPs already do.

### My single top pick
**shadcn MCP + Magic UI (both free), inside King's existing Claude Code + Vercel workflow.** Highest real value, €0, installs the same way as his current MCPs, and directly upgrades his strongest skill.

### Flagged to verify (not stated as fact)
- Aceternity Pro **$199 price** and **whether its license allows reselling client sites**, live page wouldn't load; confirm before any purchase.
- 21st.dev free-tier credit limits (beta pricing in flux).

---

# TRACK: mcps

I have enough verified data to write a tight, honest briefing. One note: the Magic MCP free-tier numbers vary across sources (beta-free vs ~5 requests vs 100 credits), so I'll flag that as "verify". Let me compile the final briefing.

---

# Web Design/Build Toolkit for Claude Code · Skill Forge Briefing

**Scope:** MCPs, skills/plugins, and GitHub template repos that make **building websites in Claude Code** noticeably better. Built for King's arsenal (Claude Code + /website + Three.js + Vercel). Lean-spend lens: free-first, paid only if it earns. **King decides what installs, nothing here is auto-install.**

Pricing note: most "free during beta" claims shift fast. Anything I couldn't pin to an official page is marked **(verify)**.

---

## TIER 1 · GENUINELY USEFUL (install candidates)

### 1. shadcn MCP · **TOP PICK** ⭐
- **What:** Lets Claude Code browse, search and install components from shadcn/ui (and any shadcn-compatible registry) by natural language straight into a project, "build a pricing page from the shadcn registry." Source of truth = real components, so far less hallucinated/broken UI code.
- **Free?** **100% free, open source.** No account, no key.
- **Install:** add to project `.mcp.json`:
  ```json
  { "mcpServers": { "shadcn": { "command": "npx", "args": ["shadcn@latest", "mcp"] } } }
  ```
  Restart Claude Code → `/mcp` to confirm "Connected".
- **Fit:** Strong. King's /website output is hand-rolled HTML/CSS; shadcn gives a consistent, accessible, modern component base for **Olly's course site** (pricing, auth forms, dashboards) and any client SaaS. Pairs with web-design-guidelines skill he already has.
- **Conflict/risk:** Pulls in React/Tailwind/Next, best for new component-based builds, not his pure-HTML Vercel one-pagers or Three.js sites. No risk to existing projects (per-project config).
- Source: [ui.shadcn.com/docs/mcp](https://ui.shadcn.com/docs/mcp)

### 2. 21st.dev "Magic" MCP · strong, but watch the meter
- **What:** Natural-language → modern React/Tailwind UI components ("/ui a hero with pricing toggle"), generates multiple variations, pulls from a large community component library. Genuinely speeds up landing-page sections.
- **Free?** **Freemium, the part to verify.** Sources conflict: "free during beta" vs **~5 free generations** vs **100 credits/mo** free, with a **~$20/mo** paid tier for higher limits. Treat free tier as **small**; **verify current limits at signup before relying on it.**
- **Install:** `npx @21st-dev/cli@latest install claude --api-key <KEY>` (needs a free 21st.dev API key).
- **Fit:** Good for fast, varied landing-page sections (great for **Aunty's cooking-business site** and quick client demos). Output overlaps with shadcn but is more "design-generated" vs "registry-installed."
- **Conflict/risk:** Requires an API key/account; credit cap can interrupt mid-build; React/Tailwind output. **Lean verdict: install free, do NOT pay until a client is paying.**
- Sources: [21st.dev/magic](https://21st.dev/magic) · [help.21st.dev/magic-chat/pricing](https://help.21st.dev/magic-chat/pricing)

### 3. tweakcn · visual theme generator (not strictly an MCP)
- **What:** Free, open-source visual editor for shadcn/Tailwind themes, colours, radius, shadows, typography, with AI "image/prompt → production theme." Export CSS variables straight into a build.
- **Free?** **Yes, fully free + open source** (~9.8k★). No signup.
- **Install/use:** web app at [tweakcn.com](https://tweakcn.com), generate theme, paste the CSS vars into the shadcn project. (MCP support is **not confirmed**, verify; use it as a web tool.)
- **Fit:** Best paired with #1. Lets King give **each client its own brand world** (his stated rule) in minutes instead of hand-tuning. Perfect for Olly's premium "Real World"-style palette.
- **Conflict/risk:** None, it's a generator, output is plain CSS.
- Source: [github.com/jnsahaj/tweakcn](https://github.com/jnsahaj/tweakcn)

### 4. Icons8 MCP · icons inside Claude Code
- **What:** 368k+ icons, 116 styles, served into Claude Code by request, "give me a knife-and-fork line icon set." **PNG previews free; full SVG delivery needs a key.**
- **Free?** **PNG = free, no auth. SVG = paid (~$15** one-time/sub, **verify** current terms).
- **Install:** add their MCP endpoint to `.mcp.json`; pass Bearer API key only if you want SVGs.
- **Fit:** Decent convenience, but **largely redundant**, King already has kie.ai/Nano-Banana + Gemini images, and free icon libs (Lucide ships with shadcn). **Only worth it if icon-hunting becomes a real time sink.**
- **Conflict/risk:** Low. Don't pay for SVG unless a project needs branded icon sets.
- Sources: [icons8.com/mcp](https://icons8.com/mcp) · [github.com/icons8/icons8-mcp](https://github.com/icons8/icons8-mcp)

---

## TIER 2 · USEFUL ONLY IF THE JOB DEMANDS IT

### 5. Figma Dev Mode MCP (official)
- **What:** Claude Code reads a Figma file (components, variables, layout, FigJam) and generates code from selected frames; can also push code → editable Figma.
- **Free?** **Server free, but gated:** Starter/free plan = **only 6 MCP calls/month** (useless for real work). Real use needs **Professional ~$12/mo Dev seat or $16/mo Full seat (verify).**
- **Install:** `claude mcp add --transport http figma https://mcp.figma.com/mcp` (or the Figma plugin).
- **Fit:** **Only if a client hands King a Figma design.** None of his 3 warm clients (Olly/Mum/Aunty) have Figma files, they want builds from scratch. **Skip for now; revisit when a design-to-code client appears.**
- **Conflict/risk:** Monthly cost with no current earning use = fails lean-spend today.
- Sources: [Figma Learn, Claude Code setup](https://help.figma.com/hc/en-us/articles/39888612464151-Claude-Code-and-Figma-Set-up-the-MCP-server) · [toolradar pricing](https://toolradar.com/tools/figma-mcp/pricing)

---

## TEMPLATE REPOS · best starting points (free, open source)

**For Olly's course/community site** (Hustlers University / "The Real World" style = paid course + community):

- **classroomio/classroomio**, open-source LMS, explicit "alternative to Teachable/Thinkific/Moodle," self-hostable. **Best structural starting point for a real paid-course platform.** Verify license before commercial resale. [github.com/classroomio/classroomio](https://github.com/classroomio/classroomio)
- **learnhouse/learnhouse**, modern open-source learning platform, clean UI. Good if Olly wants a polished course-content experience. [github.com/learnhouse/learnhouse](https://github.com/learnhouse/learnhouse)
- **Next.js SaaS Starter (Vercel, 15.5k★)**, landing page + **Stripe checkout + auth + roles + dashboard** out of the box. If Olly's site is more "paid membership + gated content" than full LMS, this is the fastest path to **taking money.** [vercel Next.js SaaS starter]
- **Open SaaS (13.6k★)**, most complete free full-stack SaaS boilerplate (landing → admin → payments). Heavier; good if it grows into a product.

**For landing pages (Aunty's cooking business, client one-pagers, demos):**

- **cruip/open-react-template** (4.4k★), polished free Next.js + Tailwind v4 landing page, animated hero, **Figma files included.** ⚠️ **GPL, "don't republish/redistribute/resell the template."** Fine as a *starting base you heavily customise per client*; do not sell the template itself. [github.com/cruip/open-react-template](https://github.com/cruip/open-react-template)
- **cruip/tailwind-landing-page-template** ("Simple Light"), same team, simpler. Same GPL caveat.
- **AstroWind**, most-starred Astro theme 3 years running; **zero-JS, fastest load + best SEO/Core Web Vitals.** Best when speed/SEO is the selling point. (verify license)

> **License flag (King's honesty rule):** GPL/template-resale clauses matter. Use these as *bases to build custom client sites on*, not as products to resell as-is. Confirm each repo's LICENSE file before any paid delivery.

---

## HYPE / SKIP (don't bother)

- **AI "icon generator" MCPs** (IcoGenie etc.), redundant; King already has Nano-Banana + Gemini for custom imagery and Lucide for UI icons.
- **Most "20 best template" listicle sites**, affiliate-driven; go straight to the GitHub repos above and read the LICENSE.
- **Paying for Magic MCP or Figma now**, both have real free/cheap use, but **zero current earning justification.** Lean-spend says wait for a paying client.

---

## MY TOP PICK + RECOMMENDED MOVE

**Install now (all free, zero risk):**
1. **shadcn MCP**, biggest single quality jump for component-based client sites. Free, per-project, no account.
2. **tweakcn** (web tool), instant per-client theming on top of shadcn.
3. **21st.dev Magic MCP**, install on the **free tier only**; verify the credit cap; great for fast demo sections.

**For Olly specifically:** start from **classroomio** or **learnhouse** (if it's a true course platform) OR the **Vercel Next.js SaaS Starter** (if it's gated membership + payments). Build with **shadcn MCP + tweakcn** for a premium custom look. This is King's strongest lane and the most likely first-paid win.

**Defer:** Figma MCP (no Figma-equipped client yet), Icons8 SVG (redundant), any paid upgrade (lean-spend, wait for revenue).

**One honest caveat:** shadcn/Magic/templates all assume a **React/Next/Tailwind** stack, a shift from King's pure-HTML /website flow. Worth it for app-like sites (Olly's course platform); for a simple Aunty one-pager, his existing /website is still faster.

**Verify-before-trusting:** exact free-tier limits for 21st.dev Magic and current Figma Dev-seat price (both move); and each template repo's LICENSE before any commercial delivery.

---

# TRACK: platform

I have verified pricing from multiple sources. That's enough to write the briefing without fabricating the Whop white-label detail (I'll flag it as "verify"). Here is the briefing.

---

# Olly's Course Site · Build-Path Briefing (sourced)

## What "Hustlers University / The Real World" actually run on

Not a SaaS platform Olly could buy. The Real World (TRW) is a **fully custom app** built by a dev shop (reported as Poseidon Software Solutions), running on **their own servers**, they deliberately moved OFF Discord (the old Hustlers University setup) for total control, and even use their **own payment system** to dodge Stripe/PayPal content objections. ([crunchbase](https://www.crunchbase.com/organization/the-real-world-andrew-tate/technology), [therealworldportal.com](https://www.therealworldportal.com/about-the-real-world))

**Takeaway for Olly:** that is a six-figure custom build with a full dev team behind it. The *look and feel* (premium, gated, community + courses + tiers) is 100% reproducible. The *bespoke backend + own payment rails* is NOT worth copying, Olly needs to take payments and deliver a course, not dodge banks. So the real question is: where do payments + course delivery + community live, and how premium does the front end look.

---

## The 5 paths compared

| Path | Cost to Olly | Payments | Community | Course delivery | Premium look | Speed to ship | King bills for |
|---|---|---|---|---|---|---|---|
| **1. Fully custom (King builds) + membership layer** | Membership tool $47-49/mo + Stripe ~2.9%+30¢ + Vercel free | Stripe (via Memberstack/Outseta) | Weak · King would have to build it | King builds gated lessons | ★★★★★ total control | Slow (weeks) | Big build fee + retainer |
| **2. Skool** | $9 or $99/mo | Built-in (Stripe under hood) | ★★★★★ its main strength | Built-in courses | ★★ generic Skool look | Hours | Setup + content/management |
| **3. Whop** | $0/mo, ~6-7% per sale | Built-in | ★★★★ (TRW-style) | Built-in courses | ★★★ decent, less custom | Hours | Setup + content/management |
| **4. Teachable / Kajabi / Thinkific** | $36· $199/mo | Built-in | ★ weak (Kajabi mid) | ★★★★★ best LMS | ★★★ template-y | Days | Setup + retainer |
| **5. HYBRID: King builds premium landing/sales page → Skool or Whop for delivery** | $0-99/mo platform + Vercel free | Skool/Whop | ★★★★★ | ★★★★★ | ★★★★★ on the page Olly sells from | Days | **Premium build fee + monthly** |

---

## Path-by-path detail (verified pricing)

### 1. Fully custom site King builds + payments/membership layer
King's strongest lane (websites). He builds the whole thing in HTML/CSS/Three.js → Vercel, then bolts on a membership/paywall tool so Olly can take recurring payments and gate lessons:
- **Memberstack**, from **$49/mo**, ~2, 4% transaction fee + Stripe fees. Adds login + Stripe + gated content to any custom-coded site. ([memberstack.com/pricing](https://www.memberstack.com/pricing))
- **Outseta**, from **$47/mo** (Founder, up to 1,000 contacts), 2% fee dropping to 1% on higher plans + Stripe fees. All-in-one: payments + auth + gated content + CRM + email. ([outseta.com/pricing](https://www.outseta.com/pricing))

**Verdict:** Most premium and fully owned, but King would have to hand-build community (forum/chat), which is exactly what TRW spent big money on. **Overkill for a first paid case study.** Best reserved for v2 once Olly has revenue.

### 2. Skool · $9 or $99/mo
- **Hobby $9/mo** (10% transaction fee) or **Pro $99/mo** (2.9% fee + custom URL). Unlimited members/courses/videos/calls on both. 14-day trial. ([skool.com/pricing](https://www.skool.com/pricing))
- The $9 plan is fine until ~$1,300/mo revenue; above that the 10% fee makes $99 Pro cheaper. ([Kourses](https://kourses.com/skool-pricing/))
- **Strength:** community is its whole identity (it's literally what Nate's AIS uses). **Weakness:** every Skool looks like Skool, Olly can't get a premium custom look inside it.

### 3. Whop · $0/mo, pay per sale
- **No monthly fee.** ~**2.7% + $0.30** processing + **3% platform** = real cost **~6, 7% per sale** all-in. ([Whop pricing](https://whop.com/network/pricing/), [Dodo breakdown](https://dodopayments.com/blogs/whop-fees-explained))
- Does courses + chat + forums + communities natively, **closest off-the-shelf clone of the TRW model** (tiered access, community + courses in one). ([Whop blog](https://whop.com/blog/best-online-course-platforms/))
- Custom-domain / full white-label depth: **verify**, Whop markets "custom branding" but I could not confirm a true custom-domain white-label on a live page (the page 404'd). Treat as "branded storefront, not fully white-labeled" until checked.
- **Strength:** zero fixed cost (great for a launching creator), TRW-shaped. **Weakness:** percentage fee scales with success; look is "Whop-ish."

### 4. Teachable / Kajabi / Thinkific (classic LMS)
- **Thinkific**, Basic ~**$36/mo, 0% transaction fees**, unlimited courses. Best value. ([learningrevolution](https://www.learningrevolution.net/teachable-vs-thinkific/))
- **Teachable**, Starter ~$29/mo but **7.5% fee**; Builder ~$69/mo 0% fee. Fees punish low tiers. ([edubracket](https://edubracket.com/articles/teachable-pricing-2026))
- **Kajabi**, **$143, $399/mo**, 0% fee, all-in-one but pricey and weak community. ([Ruzuku](https://www.ruzuku.com/learn/articles/kajabi-alternatives))
- **Verdict:** Best pure *course delivery*, but **community is weak**, and Olly's reference (TRW) is community-first. Wrong center of gravity for this brief.

### 5. ★ HYBRID · King builds the premium sales/landing page → Skool or Whop runs delivery + payments + community
King builds a **cinematic, custom, TRW-grade sales/landing page** (his core skill, /website, /immersive-site, /seedance-site) that does all the *selling* and the premium first impression. The **"Join" button hands off to Skool or Whop**, which handles payments + gated courses + community out of the box.

- **Cost to Olly:** Vercel (free) + Skool $9, 99/mo *or* Whop $0/mo+fees.
- **Premium look:** ★★★★★ exactly where it matters (the page that converts the buyer).
- **King delivers + bills:** premium landing-page build fee up front + monthly retainer for the page + content. The platform does the heavy backend so King isn't on the hook for payment bugs or community moderation tooling.
- **Speed:** days, not weeks → a real, shippable **case study fast**.

---

## Recommendation

**Top pick: Path 5 (Hybrid), King-built premium landing page → Whop (or Skool) for delivery.**

Why:
1. **Plays to King's strength** (the custom, premium, TRW-grade front end) while a platform handles payments/community/courses, the parts that are slow, risky, and not where King adds value.
2. **Cheapest for Olly to start:** **Whop = $0/mo** (pays only when he earns), so Olly carries no fixed cost before first sale. Switch the handoff to **Skool ($99/mo)** if community/discussion is the priority over a lower fee.
3. **Fastest real case study** for King, ship in days, get a live paying creator site in the portfolio, then upsell the fully-custom v2 (Path 1) later once revenue justifies it.

**Decision rule for the platform behind the page:**
- **Community is the product (TRW-style daily engagement)?** → Skool ($99 Pro once he's over ~$1.3k/mo).
- **Wants $0 fixed cost + course+community in one + closest TRW clone?** → Whop.

**Do NOT** chase a fully bespoke TRW-style backend (own servers / own payments) for v1, that's a six-figure dev-shop build and adds no value to Olly's actual goal (sell the course, look premium).

**Flag (do not state as fact):** Whop's true custom-domain/white-label depth, **verify** on whop.com before promising Olly a fully branded URL.

---

### Sources
- [The Real World tech, Crunchbase](https://www.crunchbase.com/organization/the-real-world-andrew-tate/technology) · [What TRW is, Portal](https://www.therealworldportal.com/about-the-real-world)
- [Skool pricing](https://www.skool.com/pricing) · [Skool fee analysis, Kourses](https://kourses.com/skool-pricing/)
- [Whop pricing](https://whop.com/network/pricing/) · [Whop true fees, Dodo](https://dodopayments.com/blogs/whop-fees-explained) · [Whop course platforms](https://whop.com/blog/best-online-course-platforms/)
- [Teachable pricing, edubracket](https://edubracket.com/articles/teachable-pricing-2026) · [Thinkific vs Teachable, learningrevolution](https://www.learningrevolution.net/teachable-vs-thinkific/) · [Kajabi alternatives, Ruzuku](https://www.ruzuku.com/learn/articles/kajabi-alternatives)
- [Memberstack pricing](https://www.memberstack.com/pricing) · [Outseta pricing](https://www.outseta.com/pricing)

---

# TRACK: content

I have everything I need to write a verified, sourced briefing. King already has the video-creation engine (HyperFrames, make-a-video, Seedance, ElevenLabs, short-form-video, autopilot), the genuine gap is the auto-posting/distribution layer and niche/cadence strategy, not more generators. Let me compile.

---

# RESEARCH BRIEFING · MUM (faceless AI viral channel) + AUNTY (cooking content)

Scope: best CURRENT pipelines for (A) faceless AI "story" channels and (B) food short-form, mapped against King's existing stack. Free-first. Prices verified June 2026; anything I couldn't pin down is marked **verify**.

## The headline (read this first)

King already owns the entire *video-creation* half of both jobs. HyperFrames + make-a-video + Seedance 2.0 + ElevenLabs + short-form-video + autopilot = script → AI visuals → voiceover → captions → render. The all-in-one tools below (Kineclip, AutoShorts, FlowShorts, Faceless.so) bundle exactly that PLUS one thing he's missing: **multi-platform auto-posting**. So the verdict for both clients is the same shape:

- **DON'T buy a video generator.** His stack already does it, with more control and at near-zero marginal cost. Buying AutoShorts/Kineclip would be paying $19, 39/mo to replace tools he has and downgrade the quality.
- **The ONE genuine gap is the publishing/distribution layer**, getting finished MP4s + captions onto TikTok, YouTube Shorts and Facebook on a schedule without King hand-uploading 3, 5x a week per client.

---

## (A) MUM · faceless AI viral "story" channel

### What he should just USE (already owns)
| Step | Tool he has | Notes |
|---|---|---|
| Script/idea | Claude (autopilot research→script) | Free core |
| AI visuals | Seedance 2.0 + Nano-Banana/Gemini images | ~$1.33/cinematic piece; he knows the cost |
| Voiceover | ElevenLabs | Already keyed |
| Captions/assembly | short-form-video + HyperFrames | 9:16, word-timed captions |
| Whole pipeline | `autopilot` skill (research→script→voice→video→captions→publish) | This is his biggest asset · it already *names* "publish" as a stage |

### The genuine gap: multi-platform auto-posting
This is the only thing the paid "faceless" SaaS does that he can't. Options, lean-first:

| Tool | Free/Paid | Price (verified) | Fit |
|---|---|---|---|
| **Postiz (self-hosted)** | **FREE** open-source (AGPL-3.0) | $0 self-hosted; hosted from $29/mo | **TOP PICK.** Supports TikTok/YouTube/Facebook + REST API + official n8n node + Make integration + AI captions. Self-host = lean-spend ideal. Hosted plan exists if self-hosting is a hassle. [github](https://github.com/gitroomhq/postiz-app) [postiz.com](https://postiz.com/) |
| **Upload-Post** | Free tier + paid | **Free = 10 uploads/mo**; $24/mo unlimited posts/5 accounts | Best paid API if he wants zero infra. Official n8n node, one API call posts everywhere. Free tier is enough to TEST the pipeline before charging Mum. [upload-post.com](https://www.upload-post.com/) [docs](https://docs.upload-post.com/api/overview/) |
| **post-bridge** | Paid, 7-day trial | **verify** · sources conflict: SaaSworthy shows Starter $9 / Creator $15 / Pro $27; other sources show $29/$49. Treat $9-29 as the range, confirm on their pricing page | Simple dashboard, 9 platforms incl. TikTok/YT/FB. Good non-technical fallback if API route is too fiddly. [post-bridge.com/pricing](https://www.post-bridge.com/pricing) |
| **Ayrshare** | Paid | **$299/mo+** (10 profiles) | ❌ AVOID for now · agency-grade, overkill, kills lean-spend. Only if Mum becomes a multi-client agency. [ayrshare.com](https://www.ayrshare.com/) |

**My pick for Mum:** Wire `autopilot` → **Postiz self-hosted** (free) OR **Upload-Post free tier** (10/mo) to validate, then Upload-Post $24/mo once it's earning. Either gives him a one-call "post to TikTok + YT Shorts + FB" so he can schedule a batch and walk away. This turns his existing skills into the *exact* product AutoShorts.ai sells for $39/mo, but it's his, brandable, and the marginal cost is the Seedance render only.

⚠️ **Honest constraint to flag to King:** TikTok and Facebook periodically tighten their content-posting APIs and some require app review / business verification. Whichever tool he picks, the *account-connection* step is real setup work, and platforms can throttle obviously-automated accounts. This is true of EVERY tool in this list, it's a platform reality, not a tool flaw.

### Niches that actually go viral (faceless, AI-friendly, 2026)
Verified across multiple niche reports. Ranked by viral-ease for a beginner channel:

1. **Horror / scary stories**, the single most-proven faceless format. Endless free source material (r/nosleep, r/LetsNotMeet, urban legends). Post 3, 4x/week. Lowest barrier. [fliki](https://fliki.ai/blog/best-faceless-youtube-niches) [stackedbuddy](https://www.stackedbuddy.com/7-faceless-youtube-niches-that-will-explode-in-2026/)
2. **Psychology / "did you know" facts**, high relatability, endless angles, strong on Shorts.
3. **Reddit story narration** (revenge / AITA / confessions), proven retention format.
4. **True crime**, huge but needs careful sourcing/sensitivity.
5. **Money/AI-tools**, highest RPM ($10, 30) but slower to grow and more competitive.

**My pick for Mum's first channel:** **Horror/scary-story Shorts**, 3, 4x/week. It's the fastest to momentum, fully faceless, source material is free, and it suits his Seedance cinematic visuals perfectly. Start with ONE platform-niche, prove it, then cross-post. (Faith filter note: keep it "creepy/mystery," steer clear of occult/gore-glorifying content to stay within King's values.)

---

## (B) AUNTY · cooking / food short-form + local sales

Different job: this is REAL footage of Aunty's cooking, not AI slop. So the AI-video engine matters far less; the win is editing speed + hooks + cadence + posting.

### What he should just USE (already owns)
- **short-form-video** skill = 9:16 reels with word-timed captions (the core deliverable).
- **/video-edit** = cut her raw phone footage into a punchy reel.
- **ElevenLabs** only if she wants narration; mostly food reels use trending audio + natural ASMR cooking sound (don't AI-voice these, authentic > polished is the 2026 trend).
- Same **posting layer as Mum** (Postiz/Upload-Post) for scheduling to TikTok/IG Reels/FB/YT Shorts.

**Verdict: he needs ZERO new creation tools for Aunty.** His arsenal already covers it.

### The strategy (this is the real deliverable for Aunty · verified)
- **Hook in first 3 seconds**, algorithm weights it heavily. Use food-specific hooks: the result-first shot ("This sold out in 2 hours"), the question hook, the ASMR cold-open. [marketeze](https://www.marketeze.ai/blog/food-creators-guide-to-viral-hooks-make-mouths-water-in-3-seconds)
- **Length: 8, 19 seconds** is the viral sweet spot; longer only if storytelling is strong.
- **Cadence: 3, 5 quality reels/week** beats daily low-effort. Post evenings/weekends.
- **Authentic > polished**, raw, real, behind-the-scenes street-food prep with natural sound now outperforms over-produced. Big advantage: cheap and fast to make.
- **Local sales conversion** (the actual goal, orders, not just views): every reel needs a clear next step, orderable link/WhatsApp in bio, location tag, "DM to order," local hashtags + Google Business Profile. Views ≠ orders; the CTA is what converts.

### Worth ADDING for Aunty (optional, cheap)
| Tool | Free/Paid | Fit |
|---|---|---|
| **CapCut** (templates + trending audio) | Free tier | Useful for matching trending food-reel templates fast; **verify** current free-tier limits as CapCut has shifted features behind paywalls. King's /video-edit covers most of this already, so optional. |
| **Metricool / Postiz** for posting + best-time analytics | Free tier (Metricool) / free self-host (Postiz) | Same posting layer as Mum; Metricool's free analytics help find Aunty's peak post times. [metricool](https://metricool.com/schedule-tiktok-videos/) |

**My pick for Aunty:** No new creation tools. Build a repeatable SOP: Aunty films raw on her phone → King runs **/video-edit + short-form-video** → schedule via the **same Postiz/Upload-Post pipeline** → CTA to WhatsApp/Google Business for local orders. Sell it as a monthly "content manager" retainer.

---

## Bottom line for King

- **One gap, shared by both clients: the auto-posting layer.** Everything else he already owns.
- **Top pick (lean-spend): Postiz self-hosted (free), or Upload-Post free tier (10/mo) to start, $24/mo when earning.** Both wire into n8n and into his existing `autopilot` skill.
- **Do NOT buy AutoShorts/Kineclip/FlowShorts/HeyGen**, they replace tools he has and add a monthly bill for less control.
- **Avoid Ayrshare** ($299/mo) until/unless this becomes a multi-client agency.
- **Mum's fastest win:** horror/scary-story Shorts, 3, 4x/week, via his Seedance + autopilot stack.
- **Aunty needs strategy + editing + posting, not AI generation**, hook-first, 8, 19s, 3, 5x/week, authentic, with a hard local-order CTA.

**Verify before quoting as fact:** post-bridge exact price ($9, 29 range, sources conflict); CapCut current free-tier limits; TikTok/Facebook content-API approval requirements for whichever poster he picks (these change and affect every tool).

**Sources:** [Kineclip niches](https://kineclip.com/blog/top-ai-tools-faceless-creators-2026/) · [AutoShorts.ai](https://autoshorts.ai/) · [Postiz GitHub](https://github.com/gitroomhq/postiz-app) · [Upload-Post](https://www.upload-post.com/) · [Upload-Post pricing review](https://www.linkstartai.com/en/agents/upload-post) · [post-bridge pricing](https://www.post-bridge.com/pricing) · [Ayrshare](https://www.ayrshare.com/) · [Fliki faceless niches](https://fliki.ai/blog/best-faceless-youtube-niches) · [StackedBuddy niches](https://www.stackedbuddy.com/7-faceless-youtube-niches-that-will-explode-in-2026/) · [Marketeze food hooks](https://www.marketeze.ai/blog/food-creators-guide-to-viral-hooks-make-mouths-water-in-3-seconds) · [Metricool scheduling](https://metricool.com/schedule-tiktok-videos/)
