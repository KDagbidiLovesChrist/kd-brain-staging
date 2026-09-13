---
name: feedback-multi-source-consensus-research
description: "Standing rule for ALL research: pull MANY sources including VIDEO (YouTube/TikTok/Instagram/Facebook) + blogs + marketplaces + forums, cross-check them, and land on a strong deterministic consensus. Never rely on a single source."
metadata: 
  node_type: memory
  type: feedback
  originSessionId: bafd5c1d-e893-4169-8099-7a242d34cfab
---

King's rule (2026-06-26): when researching ANYTHING, never trust one source. Pull MANY sources across
formats and platforms, cross-check them, and conclude only where they AGREE.

**Sources must span formats, not just blogs:** VIDEO (YouTube, TikTok, Facebook, Instagram), written
(blogs, articles, docs), marketplaces (Gumroad/Etsy/Payhip/Whop), forums (Reddit), "anything online,
essentially." Video especially: a lot of the real, current signal (what's selling, what's trending)
lives on YT/TikTok/IG/FB, not in blog posts.

**Output = a strong, deterministic consensus.** State clearly where the sources converge (the consensus
King acts on) and flag any outliers/disagreements. Cite URLs. A single-source claim is not an answer.

**Why:** single sources are biased, outdated, or wrong, and King makes real money + product decisions
on this research, so it must be de-risked by triangulation.

**How to apply:** fan out across source types (parallel subagents, or the `/research` // `deep-research`
skills), always include video platforms, then synthesise the consensus. Pairs with
[[learning-digital-product-viral-sales-model]] (find PROVEN winners, don't guess) and the verify-before-
asserting habit [[feedback-verify-before-rerun]].

**Strongest numbers, and WIRE the tool (King, 2026-06-26):** every consensus must surface and LEAD WITH
the strongest numbers (the hard, most-credible sources), not just list any figure. And when a task needs
precise data, **WIRE THE ACTUAL TOOL** (free tier / CLI / API / MCP) and pull real numbers, only falling
back to web-search estimates when no free tool exists. Don't approximate when a free real tool is one
`pip install` away. Proven-free already: **Google Trends via `pytrends`** (no key, CLI, real interest +
rising terms), **YouTube Data API** (free, King's Google creds), **TikTok Creative Center / Creator Search
Insights** (scrape via Playwright/Firecrawl). Add API keys / MCP servers when needed, same for ALL apis +
mcps. [[feedback-tool-augmentation]]

**Dedicated trend/research tools (King, 2026-06-26):** use as extra sources in the fan-out, **VidIQ + TubeBuddy** (YouTube keyword/trend scores), **TikTok Creative Center**, **Google Trends**,
**Exploding Topics**, Answer the Public, Keywords Everywhere. **This applies to EVERYTHING we plan and
research, not just content/this project** (King re-stated this). Baked into the `/content-engine` DATA &
TREND LOOP, but the rule is global.
**Use tools WHEN NECESSARY + RELEVANT (King, 2026-06-26):** apply the right tool for the task with
judgment, not every tool every time. The constant is multi-source + consensus; the specific tools depend
on what's being researched/planned.

**⚠️ APPLIES TO TOOLS YOU BUILD, NOT JUST MANUAL RESEARCH (King, 2026-06-26, for ALL sessions):** any
script/harvester/scraper/router/agent we build that gathers signal MUST pull from MULTIPLE sources and run
the consensus, never ship a single-source tool. **And VERIFY each source actually returns data** (wire ≠
working). Cautionary example: the Hook Machine `hook_harvest.py` was first built TikTok-only, that broke
this rule; it was fixed to TikTok + Instagram + YouTube, and the IG/YT adapters had to be debugged live
before they returned data. The pricing/cost work (`gen_router.py`) was multi-source from the start (MuAPI
API + kie page + Google official + web). **Cross-session directive:** if you (any session) previously did
research or built a gather-tool from ONE source, RE-DO it multi-source + consensus. Audit before trusting
old single-source outputs.
