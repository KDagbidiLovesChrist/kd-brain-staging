---
name: reference-subagents
description: "What sub-agents are, when to use them, how to brief them properly, and King David's specific use cases for parallel Claude agents."
metadata: 
  node_type: memory
  type: reference
  originSessionId: 4b621969-d6bd-419c-9280-c6a4e0333ae8
---

# Sub-agents · Parallel Claude Agents

## What Is a Sub-agent?

A sub-agent is Claude spawning another Claude to handle a specific task.

**Analogy:** You're a manager. Instead of doing every task yourself, you delegate.
You give a clear brief to a team member, they go away and do the work, come back with
the result. You review it and move on.

In Claude Code, you (the main Claude) are the manager. Sub-agents are the team members.
You brief them with exactly what you need, they execute, return the result.

**Why it matters:** Tasks that would take you 30 minutes of waiting can be done in
5 minutes by running 6 sub-agents in parallel, each handling one piece.

---

## WHEN TO USE SUB-AGENTS

### Good for sub-agents:
- **Parallel research**, research 5 competitors at once, not one at a time
- **Parallel processing**, scrape 5 pages simultaneously instead of sequentially
- **Specialised tasks**, one agent writes, another edits, another formats
- **Long background tasks**, send a sub-agent off to do a long task while you continue working
- **Isolation**, you want a fresh perspective without the current conversation's bias

### Not good for sub-agents:
- Tasks that depend on each other in sequence (do these one at a time)
- Simple quick tasks (faster to just do it directly)
- Tasks where you need real-time visibility (sub-agents report at the end)

---

## HOW SUB-AGENTS WORK

The main Claude (you, the manager) uses the **Agent tool** to spawn a sub-agent.

Key rule: **A sub-agent starts with zero context.** It only knows what the briefing tells it.
This is why briefing quality is everything. A vague brief = vague result.

### Foreground vs Background

**Foreground sub-agent:** Main Claude waits for the result before continuing.
Use when: You need the result before you can do the next step.

**Background sub-agent:** Main Claude continues working while sub-agent runs.
Use when: The task is independent and you have other things to do in parallel.
Note: You get notified when the background agent finishes.

---

## HOW TO WRITE A GOOD SUB-AGENT BRIEF

The brief is everything. Think of it as the job description you hand to a new employee
who has never seen your project before.

**A good brief includes:**
1. **Context:** What's the bigger goal? Why does this task matter?
2. **Specific task:** Exactly what to do (not "research this" but "find the top 5 competitors
   in the Irish lead gen market, their pricing page URL, their main USP, and any gap I could exploit")
3. **Format:** How to return the result (bullet list, table, code, JSON?)
4. **Length:** Short report? Detailed? Under 200 words?
5. **What NOT to do:** Common mistakes or things to explicitly avoid

**Example, Vague (bad):**
> "Research my competitors"

**Example, Specific (good):**
> "Research competitors for a lead generation scraper service targeting Irish tradespeople.
> Find 5 services that sell business lead lists for Irish/UK markets. For each: business name,
> URL, pricing (what they charge and for how many leads), their main selling point, and one
> gap or weakness. Return as a markdown table. Under 300 words total."

---

## KING DAVID'S USE CASES FOR SUB-AGENTS

### 1. Parallel Lead Research
Instead of researching one city/trade at a time:
- Sub-agent 1: Plumbers in Dublin
- Sub-agent 2: Plumbers in Cork
- Sub-agent 3: Electricians in Dublin
- Sub-agent 4: Electricians in Cork
- Sub-agent 5: Cleaners in Dublin

All 5 run in parallel. Results in 2 minutes instead of 10.

### 2. Newsletter Research + Writing
- Sub-agent 1: Research the topic (Perplexity API)
- Sub-agent 2: Find 3 relevant statistics and sources
- Sub-agent 3: Find 2 expert quotes or case studies
- Main Claude: Takes all results and writes the newsletter

### 3. Client Proposal Package
- Sub-agent 1: Research the client's industry
- Sub-agent 2: Find competitor insights
- Sub-agent 3: Draft the ROI calculation
- Main Claude: Assembles into a proposal using /monetize template

### 4. Website Building
- Sub-agent 1: Research design inspiration for the site type
- Sub-agent 2: Write all the copy (headlines, body text, CTA)
- Sub-agent 3: Generate the HTML structure
- Main Claude: Assembles and applies brand guidelines

---

## SUB-AGENT BRIEFING TEMPLATE

Use this structure when briefing any sub-agent:

```
GOAL: [One sentence, what success looks like]

CONTEXT: [2-3 sentences, why this matters, what the bigger picture is]

YOUR TASK: [Specific bullet list of exactly what to do]
- [Task 1]
- [Task 2]
- [Task 3]

RETURN FORMAT: [Exactly how to structure the response]

LENGTH: [Under X words / X bullet points / full report]

DO NOT: [Things to explicitly avoid]
```

---

## SUB-AGENT QUALITY CHECKLIST

Before sending a sub-agent:
- [ ] Does the brief include enough context for someone with zero knowledge?
- [ ] Is the task specific (not vague)?
- [ ] Is the output format defined?
- [ ] Is the length guidance given?
- [ ] Are there any "do not" instructions needed?

If any are missing, improve the brief first. A 2-minute brief improves a 30-minute result.

---

## QUICK REFERENCE

```
WHAT: Claude spawning another Claude for a task
WHY:  Parallel work, faster results, specialisation
HOW:  Brief clearly → specify format + length → foreground or background

FOREGROUND: Wait for result → use when next steps depend on it
BACKGROUND: Continue working → use for independent parallel tasks

BRIEF FORMULA:
  Goal + Context + Specific task + Output format + Length + Do not

KEY RULE: Sub-agent starts with ZERO context. Brief it like a new hire.
```
