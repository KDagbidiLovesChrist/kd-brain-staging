# Cluster A+B · Claude Code Fundamentals + Build Portfolio Phase 3
*Phase 4 absorption, generated 2026-05-23 from full read of 9 Loom transcripts.*

---

## 1. WAT FRAMEWORK (AIS+ Claude Code 1.3)

**Canonical definition (Nate's words):**
- **W = Workflow**, markdown SOP (the steps)
- **A = Agent**, Claude (reads, reasons, decides)
- **T = Tool**, Python / MCP / API (executes)

**King David's adopted extension:** adds **S = Skill** layer (/command that triggers the full WAT chain).

**Nuance vs King David's framing:** Nate teaches this as a framework for designing agentic automations. King David's CLAUDE.md correctly attributes it to Nate now (corrected 2026-05-23, was previously framed as "your invention", drift fix locked in).

---

## 2. TOKEN MANAGEMENT (AIS+ Claude Code 1.10)

### 5 Prompting Patterns
1. **Define the goal, not the steps**, let Claude figure out HOW; tell it WHAT
2. **Be specific about the output**, formats, structure, length, audience
3. **Plan mode first**, for non-trivial tasks, plan before executing
4. **Give feedback, not corrections**, explain the WHY of changes, let Claude re-derive
5. **Treat the agent as an expert**, don't micromanage; trust judgment + push back

### Context Rot Thresholds
- **0, 50% Green**, full focus, all features on
- **50, 70% Yellow**, start thinking about `/compact`
- **70, 85% Orange**, run `/compact` now
- **85%+ Red**, run `/clear` immediately, you're hallucinating

### 5 Token-Saving Strategies
1. **One task per session**, don't pile work into one conversation
2. **Define "done" clearly**, exit criteria written upfront
3. **Use skills, not bloated CLAUDE.md**, skills load on demand
4. **Disable unused MCP servers**, every MCP eats startup context
5. **Keep CLAUDE.md under 500 lines**, hard cap

---

## 3. BUILD PORTFOLIO PHASE 3 · FULL DISCOVERY FRAMEWORK

### 3.1 Intro to Phase 3
**Goal:** identify automation opportunities for clients → produce two paid deliverables:
- **Opportunity Map**, ranked list of automation ideas with ICE scores
- **Wireframe / Blueprint**, visual mockup of #1 priority drawn in front of client

**Phase 3 = the repeatable discovery process you can charge for.**

### 3.2 Time Lens for Businesses
**Two CEO/manager questions:**
1. *"Which team or person is most burdened by manual, repetitive work?"*
2. *"If you gave them back 5 hours a week, what would they do with that time?"*

**Where to look:** communication patterns · data movement · process bottlenecks
**Pitch frame:** quantify hours saved → translate to FTE cost saved → present as ROI

### 3.3 Income Lens for Businesses
**Two bottleneck questions:**
1. *"If we doubled your leads tomorrow, what process would break first?"*
2. *"What's the constraint currently tethering your revenue?"*

**Frame in revenue terms:** automation = revenue unlocked (not just hours saved)
**Examples:** faster lead response → higher conversion · more capacity → more clients

### 3.4 SOP Audit (Inventory vs Creation)
**3-step gap-finding process:**
1. **Inventory**, review what SOP documentation already exists
2. **Compare**, compare docs to actual practice (gaps surface)
3. **Tribal knowledge**, find what's only in people's heads (never documented)

**Charge for the audit itself**, many businesses don't realise the value until you show the gap.
**Output:** documented SOP + gap analysis → foundation for automation

### 3.5 Scoring Before Mapping (Business ICE)
**Score every opportunity 1-10 on:**
- **I (Impact)**, how much time / revenue does it unlock?
- **C (Confidence)**, how clearly defined is the process?
- **E (Ease)**, how complex is the implementation?

**Critical rule: score WITH the client, not alone.**
- Builds trust (they own the priority)
- Aligns expectations
- Catches edge cases you'd miss

**Output:** scored list → clear #1 priority for first project

### 3.6 Live Blueprint (Mapping in the Room)
**The aha-moment / close technique.**
Draw the wireframe REAL-TIME in front of CEO/manager. Establishes "visual authority."

**5-step wireframe:**
1. **Trigger**, what starts the process?
2. **Data flow**, where does info move between?
3. **Decision points**, where does logic split?
4. **AI steps**, where does Claude/LLM add value?
5. **Output**, what does the human see / what action happens?

**Deliverables from this session:** Opportunity Map + Wireframe (both paid)
**Practice exercise:** 10-min timer, draw any process step-by-step. Repeat until confident.

### 3.7 Should You Charge for the Opportunity Map?
**Depends on credibility:**

| Credibility Level | Pricing Model |
|---|---|
| **Authority** (client results, published content, industry experience) | Charge upfront · premium pricing |
| **Beginner + warm network** (referrals, personal connections) | Pay-after model (results-based) |
| **Beginner + cold prospects, no network** | Skip discovery charge · do one automation first, build proof |

**Two opportunity map versions:**
- **Light**, 1-2 hours, can be free (lead magnet)
- **Deep Dive**, multi-day, always paid (consulting product)

---

## 4. TOOLS / FRAMEWORKS MENTIONED IN THESE TRANSCRIPTS

| Tool | Purpose | When Used |
|---|---|---|
| Excalidraw / Miro | Live wireframing in front of client | Phase 3.6 Live Blueprint |
| Notion / Google Docs | SOP documentation deliverable | Phase 3.4 SOP Audit |
| CRM / Sheets | Track opportunity map progress | Phase 3.5 ICE Scoring |
| Slack / Email / Forms | Sample triggers in wireframes | Phase 3.6 Blueprint mock-ups |
| Claude Code skills | Codify SOPs as reusable /commands | Token Mgmt lesson |
| `/compact` and `/clear` | Manage context rot | Token Mgmt thresholds |

---

## 5. SURPRISES / CONTRADICTIONS vs KING DAVID'S CURRENT APPROACH

1. **Pay-after is valid**, not a "free giveaway." For warm-network beginners, results-based is the right pricing.
2. **Two opportunity map versions** (Light free, Deep Dive paid), current /dtransform assumes single tier.
3. **Live wireframing IS the conversion**, not the written report. The drawing-in-the-room session is the close.
4. **SOP audit is its own revenue line**, businesses pay just to know what's missing from their documentation.
5. **Context thresholds are hard numbers**, 50/70/85% are explicit, not vibes. Apply across all skills.
6. **"Define done" upfront is non-negotiable**, every skill SOP should open with exit criteria.
7. **Credibility gates discovery pricing**, never charge upfront to cold prospects. Build proof first.

---

## 6. APPLICABLE NEXT-30-DAYS ACTIONS

- Apply ICE scoring to King David's own skill backlog (rank what to build next using the same framework)
- Phase 3 framework is the foundation for the PT_Client engagement (/dtransform), use it verbatim
- For Dublin plumber outreach: lead with Time Lens question #1 ("which team is burdened by manual work?")
- Add `/clear` reminder to /save skill when context > 70%
- Cap CLAUDE.md at 500 lines (currently 373 ✓, already in spec)
