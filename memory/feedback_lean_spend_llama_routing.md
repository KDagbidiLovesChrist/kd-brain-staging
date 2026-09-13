---
name: feedback-lean-spend-llama-routing
description: "Lean-spend rule + Llama-vs-Claude task routing. King tops up a prepaid card manually (no auto-drain); the €600 is SUNK COST already spent, not a recurring bill. Earning engine runs nearly free. Flag every task Llama(free/bulk) vs Claude(premium)."
metadata: 
  node_type: memory
  type: feedback
  originSessionId: dae0fabf-3099-45e0-8377-3149f004ed3e
---

# Lean Spend + Llama-vs-Claude Routing (set 2026-06-02)

How I should handle cost and tool-choice for King going forward.

- **Spend model:** King uses a **prepaid top-up card**, he only tops up when a payment is actually
  due, so **nothing auto-charges and he controls every euro.** The **"€600" is NOT a recurring bill**,   it's roughly his **sunk cost already spent** building the whole operation. Recurring cost is
  low/unconfirmed. (Earlier "€600/month fear" framing was wrong, corrected by King 2026-06-02.)
- **Goal that the €600 maps to:** earn **€600 back in 30 days to reach profit**, see
  [[project-income-targets]] for the dated target + what €600 looks like in sales.
- **The earning engine is nearly free:** Vercel hosting €0 · Fiverr listing €0 · outreach/DMs €0 ·
  domain ~€1/mo. **Build phase (sites/videos/3D) is CLOSED**, the expensive part is behind him. The
  next phase (outreach + selling what's already built) costs nothing. So revenue ≈ profit.
- **Apify (~$49/mo)** = the main *pausable* cost. 146 demos already built → no need to scrape more to
  start earning. Pause it when not actively prospecting a fresh niche.
- **LLAMA ROUTING RULE (the operating habit):** for every task, flag it out loud,   **"Llama job"** = free, local Ollama, for bulk/repetitive/low-stakes work (lead sorting, rough
  first-draft messages, summaries), vs **"Claude job"** = worth the spend (premium building,
  reasoning, client-facing quality). Route the cheap stuff to Llama automatically.
- **Honest caveat (don't oversell Llama):** it won't cut hundreds. It can't replace Claude for the
  premium building, nor Apify for scraping (Apify isn't an LLM). The real bill-slasher is simply that
  **the build phase is done** → stop topping up to build, and sell what already exists (free).
- **Decision framework for any paid tool:** **KEEP** (needed to earn now) / **PAUSE** (off now, back on
  when money flows) / **CUT** (cancel).
- **INVEST-TO-WIN exception (King, 2026-06-03):** King is willing to **pay out of pocket to build the next
  *best* demo when it is genuinely worth it.** A small spend to win a €900, €4k client is great ROI. Spend
  is justified when the lead is **high-ticket or high-conviction**, OR the spend buys a **reusable asset**
  usable across many future pitches (a real domain on a flagship demo, premium stock imagery to replace
  placeholders so it feels real, a small API/AI budget for a genuinely functional demo). NOT justified for
  unconfirmed low-budget leads (e.g. do not build a paid LMS for a €330 signal). **Always name the exact
  item + cost and let King greenlight each time**, lean by default, invest deliberately.

**Why:** King got stressed about spend with €0 income and reached for Llama as a lifeline. Knowing he
controls every top-up and that the earning engine is free removes the panic; the Llama/Claude routing
rule gives a concrete, ongoing way to stay lean without dropping the quality that actually sells.

**How to apply:** default to lean. Before any spend-bearing task, name it a Llama job or a Claude job.
Treat hosting / outreach / selling as the free core of the business. Never push a paid tool unless it
directly earns. When King worries about cost, anchor him to facts (his card statement, what's actually
recurring), not fear. Related: [[project-upcoming-tasks]], [[feedback-pivot-to-global-market]].

**"OPTIMISE WHAT IS BEST" (King, 2026-06-16):** when I framed his Claude OS as max-cost (Opus +
extra-high thinking + verbose) vs his lean-spend rule, he chose **"optimise what is best"**, i.e.
lean-spend does NOT mean cheapest. Keep the levers that make the *output* better, because the output is
the product that earns (kept Opus + xhigh reasoning), and cut only genuine waste (turned off verbose;
killed a Stop hook that spawned 2072 junk files). Apply: optimise for best value/outcome, not minimum
spend, trim waste, never trim the quality that sells. See [[reference-claude-os-config]].

**GLM 5.2 = the upgraded cheap lane (watched 2026-06-17, `knowledge/video_studies/2026-06-17_glm_5_2.md`):**
Z.ai's GLM 5.2 (1M context, MIT open weights) is a near-frontier *coding* model at **~$0.18/prompt vs Opus
$0.93 / GPT-5.5 $0.94 (~5× cheaper)**. In Povilas Korop's real tests it jumped to 15/20 (from 5.1's 9/20):
**5/5 on simple Laravel/Filament**, but **failed complex/nuanced work** (N+1 query: claimed success, tests
failed), and it shipped with **no official benchmarks**. **ROUTING UPGRADE:** GLM 5.2 is a stronger
"grunt lane" than Llama for **simple/bulk coding + content**, but **always verify its output (it lies
about success)** and **keep Claude (me) for complex/client-facing/critical work.** Access = OpenRouter API
or GLM Coding Plan (~$10/mo, ~1/10th cost). NOT set up yet, needs an API key/plan + King's go (spend
decision). Use only if a real volume of cheap, verifiable tasks appears; otherwise me by default.

