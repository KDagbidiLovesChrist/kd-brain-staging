# Wave 1 Absorption · 2026-05-23 evening
*Distillation of 8 unique transcripts (9 files; the two FATHOM files are duplicate content with different filenames). Cap: ≤120 lines.*

---

## 1. `loom_AISFREE_10HR10SEC_v2_1_17406264cead.md` (62.7s)
- **Teaches:** AIS-free intro / onboarding video. "Don't skip the video. Go to Start Here module. Watch 'requesting help guidelines.' Use screenshots + clear titles when posting."
- **Insight:** Community help culture, clear titles + screenshots = faster, higher-quality answers. Mirror this in our own Skool posts.
- **Recommendation:** SKIP install, pure community onboarding content.

## 2. `loom_AISFREE_10HR10SEC_v2_2_25d3f11098d5.md` (51.3s)
- **Teaches:** Cancel-page retention loop. Asks departing members for DM feedback + warns price-lock on re-join.
- **Insight:** Smart retention pattern, capture leaver feedback for product loop + signal price-lock as switching cost.
- **Recommendation:** SKIP, Skool-specific. But the *pattern* (feedback loop on cancel) is reusable for any future SaaS product.

## 3. `loom_AISFREE_10HR10SEC_v2_3_11479f0c6559.md` (49.0s)
- **Teaches:** How to download an n8n JSON template from the community → import into a fresh n8n workflow → follow setup guide.
- **Insight:** Reinforces "follow setup guide for auth", already in patterns.
- **Recommendation:** SKIP, known pattern.

## 4. `loom_AISFREE_10HR10SEC_v2_4_1e355aad92b4.md` (50.6s)
- **Teaches:** Community welcome, points members to Classroom → Building AI Agents module for video templates + resources.
- **Insight:** Same as #3.
- **Recommendation:** SKIP, known.

## 5. `loom_AISPLUS_COMMUNITY_RESOURCES_1_d50085e18960.md` (152.2s)
- **Teaches:** "Earn With Gems" initiative. Admins promote valuable posts to Gem category → pinned + $20 cash + stored in a Gems classroom module. Weekly/monthly recaps.
- **New insight:** **A "Gem-worthy post" on Skool = $20 cash + pinned exposure + classroom permanence.** That's a *direct monetisable channel*, sharing genuinely valuable client-system walk-throughs, frameworks, or productivity hacks can both earn cash and drive credibility/inbound DMs.
- **Quote:** *"Real value and practical insights rather than just being able to get a ton of likes through random methods."*, directly relevant to King David's Skool posting playbook (`commands\skool_post_playbook.md`).
- **Recommendation:** Update `/skool-post` skill to target gem-worthy patterns (frameworks, client walk-throughs, before/after demos). Note: this is a config tweak, not an install.

## 6. `loom_AISPLUS_MEMBER_PERKS_FULL_1_3eb9c34869db.md` (68.3s)
- **Teaches:** AIS+ annual members get access to 539+ tool discounts via a partnered platform. Examples called out: **Bolt.new, 1 year free Pro plan** · **Notion, 6 months free Business plan with unlimited AI** · Airtable · Apollo · Slack · Perplexity.
- **New insight:** King David is AIS+, he may already qualify for these discounts. Two are immediately valuable:
  - **Bolt.new 1-yr Pro free**, relevant for `/video-to-website` competitor scouting + rapid prototyping.
  - **Notion 6-mo Business + unlimited AI**, could replace some Obsidian flows if vetted, OR mirror docs for client deliverables.
- **Recommendation:** **Action for King David Monday morning**, log into AIS+ classroom → find the discounts portal → claim Bolt.new + Notion at minimum. ~5 min, zero cost, real value.

## 7. `loom_AISPLUS_MEMBER_PERKS_FULL_2_3b11d83c4892.md` (24.0s)
- **Teaches:** Empty body, transcript content is blank (24s video, no captions extracted or extraction failed silently).
- **Insight:** None.
- **Recommendation:** SKIP. Log a note: if extractor returns empty body for short clips, may indicate music-only intro or audio extraction failure. Not blocking.

## 8. `loom_AIS_PLUS_TrueHorizon_211k_Part1_FATHOM_fathom_pMnAz.md` (3,467s · 57min, the gold mine; duplicate at `..._Scoping_FATHOM...`)
- **Teaches:** Full walkthrough of TrueHorizon AI's $211k+ enterprise insurance deal, sales cycle, scope, pricing structure, discovery framework. Co-presented by Nate Herk + Millen (co-founder).
- **Already absorbed into §15 (master_summary)**, but several **NEW** details:

### 8a. New tools mentioned (not yet in tools_discovered_v3.md)
- **AWS RDS (Postgres)**, TrueHorizon does database replication of the client's AWS Postgres on RDS for the chatbot agent. NLP-to-SQL approach beats vector-DB for performance + latency on structured data. (Already known stack, adds context.)
- **Cloud Development Kit (CDK) / Terraform**, Millen mentions n8n saves overhead vs. these for cloud deployment. (Context only, no install.)
- **Apify**, called out as a partner: Nate gave away 3 codes ($50/$30/$20) on the call. Already on our install candidate list, confirms relevance.
- **Fathom**, the meeting recorder itself. Already used by AIS for these workshops; we don't need it (Loom + Whisper transcription pipeline already covers our needs).

### 8b. New methodologies / pricing patterns
- **Enterprise vs Business plan SLA structure:** Enterprise = top-tier PM + 2 engineers + solutions architect. Business = junior PM + 1 engineer. Faster response, faster onboarding. **Pattern reusable for King David's future client tiering.**
- **IP ownership clause:** Client owns the *deployed* IP. Pre-deployment IP stays with the agency (protects reusable components like Google Drive multimodal indexing workflow). **Direct contract-language pattern, note for future client work.**
- **Profit margin:** "Over 50%" on the base $12k/mo. Main cost = engineering salaries. LLM + n8n costs negligible (enterprise n8n license free via Nate's partnership; LLM credits from startup programs).
- **Buying signal hierarchy (NEW + sharper than §15):**
  1. Prospect comes to call WITH AI agent ideas already mapped → "highest buying signal we've seen"
  2. Bullish on AI + sees competitive necessity ("adopt or die" mindset)
  3. C-suite / decision-making power
  - → these three combined = **clear ICP signal**.
- **Customer revenue size for $211k deal:** $50M, $100M annual revenue (mid-market). Useful anchor.
- **Reusable component examples (their IP):** Google Drive multimodal indexer · NLP-to-SQL · NLP-to-n8n (proprietary) · n8n CI/CD DevOps tool (proprietary).
- **Front-end demo wins sales > n8n demo:** Millen confirms "the sale is a lot more effective if you can demo a front-end experience for the client rather than running a demo n8n flow with dummy data." → reinforces King David's `/video-to-website` + `/website` as sales-acceleration tools, not just deliverables.

### 8c. Quotes worth preserving
- *"If the prospect comes to the call with a bunch of ideas for automations, hands down it's the highest buying signal we've seen."*, Millen
- *"Most successful discovery calls have had some, and ideally all of those components."*, Millen on the 7-point discovery framework
- *"We're crushing delivery, and there's more agents that he keeps putting in the pipeline."*, Millen on why $211k will keep growing
- *"Build without docs = file on computer. Build + 2-min doc = client case study."* (already in §15.8, retained)

### 8d. Recommendation
- **No install** (Fathom = vendor tool, not for us).
- **Mirror to DCEO_BRAIN\knowledge\patterns.md:** YES, the discovery framework + IP ownership pattern + enterprise/business tiering + buying signal hierarchy are all *work-applicable* for DCEO Brain when Orcha handles stakeholder/vendor escalations or evaluates new internal projects. Process discipline + risk handling + tiered service levels = directly transferable.

---

## Aggregate work-applicable insights → DCEO_BRAIN\knowledge\patterns.md
From transcript #8 (TrueHorizon Fathom):
1. **Discovery cadence > build quality** (already mirrored in master §16.1 but worth re-stating in work context).
2. **IP ownership pattern**, for any cross-team work product: distinguish pre-deployment (agency-owned, reusable) vs. post-deployment (client-owned). At Amazon: pre-handoff vs. post-handoff ownership of runbooks, scripts, dashboards. Useful framing.
3. **Tiered SLA model**, enterprise vs. business plan. At work: high-pri tickets get senior engineer + faster response; low-pri get standard. Already implicit, but the explicit framing helps.
4. **Buying signal hierarchy → "engagement signal hierarchy"** at work: stakeholders who come to a meeting with their own draft / their own ideas = highest engagement → prioritise their requests.
5. **Front-end demo > raw workflow demo**, when pitching internal tools to non-technical managers, always lead with the visible artefact (dashboard, email, summary), never the workflow YAML or n8n graph.

---

*End of v3 wave 1 absorption, 8 transcripts (1 empty + 7 with content + 1 dup of #8).*
