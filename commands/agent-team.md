# /agent-team · Multi-Agent Coordinator

**Trigger:** User types `/agent-team` OR says "launch agents", "run agents in parallel", "multi-agent task"
**Purpose:** Spin up coordinated teams of agents for tasks that benefit from parallel work

---

## WHEN TO USE THIS

Use /agent-team when:
- A task has 3+ independent parts that can run at the same time
- Research needs multiple sources cross-checked (consensus pattern)
- A deliverable requires multiple types of work (research + write + check)
- Speed matters and sequential is too slow

Do NOT use for simple tasks a single agent handles fine.

---

## TEAM TEMPLATES

### Team 1 · Research Consensus (3 agents)

Use when: "What's the best approach to X?" or "Can I do X?"

| Agent | Role | Where it searches |
|-------|------|------------------|
| Agent 1 | Web researcher | Brave Search / WebSearch · current best practice |
| Agent 2 | Internal researcher | knowledge\ folder via /search · what we already know |
| Agent 3 | AIS researcher | ais_all_learnings.md + YouTube database |

**Rule:** If 2 of 3 agree → that's the answer. All 3 conflict → flag to King David.

---

### Team 2 · Lead Gen Pipeline (3 agents)

Use when: Scraping + verifying + formatting leads for a Fiverr order

| Agent | Role | Task |
|-------|------|------|
| Agent 1 | Scraper | /scrape · pulls raw leads from Firecrawl |
| Agent 2 | Verifier | Checks phone/email format, removes duplicates |
| Agent 3 | Formatter | Cleans CSV · name, phone, city, source column |

---

### Team 3 · Newsletter Pipeline (3 agents)

Use when: Running /newsletter end-to-end fast

| Agent | Role | Task |
|-------|------|------|
| Agent 1 | Researcher | Perplexity · pulls 5 key points on the topic |
| Agent 2 | Writer | Turns research into newsletter HTML |
| Agent 3 | Sender | Gmail SMTP · sends to list |

---

### Team 4 · Client Proposal (4 agents)

Use when: Client inquiry comes in and needs a fast professional proposal

| Agent | Role | Task |
|-------|------|------|
| Agent 1 | Matcher | Checks skills_catalog.md for matching service |
| Agent 2 | ROI calculator | Estimates value using pricing formula |
| Agent 3 | Writer | Generates /proposal output |
| Agent 4 | Checker | Reviews for tone, length, accuracy |

---

### Team 5 · Morning Briefing (/exec mode)

Use when: /exec is triggered for daily briefing

| Agent | Role | Memory it reads |
|-------|------|----------------|
| Agent 1 | Faith | CLAUDE.md values section |
| Agent 2 | Finances | memory\project_income_targets.md |
| Agent 3 | Health | CLAUDE.md Health domain |
| Agent 4 | Work (DCEO) | memory\project_dceo_work_ai.md |
| Agent 5 | Projects | CLAUDE.md Active Projects + memory\project_upcoming_tasks.md |

All 5 run simultaneously. Main agent combines into one briefing.

---

## HOW TO LAUNCH

When a user requests a multi-agent task, state:
```
Launching [N]-agent team for [task].
Agent 1: [role], starting now
Agent 2: [role], starting now
Agent 3: [role], starting now
[Wait for all to return]
Combining results...
```

Then spawn agents using the Agent tool and synthesize their outputs.

---

## STANDARD HANDOFF FORMAT (every agent returns this)

```
Agent: [name]
Task: [what was requested]
Output: [the result]
Status: success | partial | failed
Next: [recommended next step or agent]
```

Orchestrator collects all handoffs, merges them, and delivers one clean result.

---

## OUTPUT FORMAT

After all agents complete:
```
TEAM RESULT, [Task Name]
─────────────────────────
Agent 1 found: [summary]
Agent 2 found: [summary]
Agent 3 found: [summary]

CONSENSUS: [synthesized answer]
CONFIDENCE: High / Medium / Low
ACTION: [what to do next]
```

---

## ENVIRONMENT NOTE
All agents share one environment, same local files, same knowledge base, same WAT framework.
Read `commands\subagent_registry.md` for the full agent menu.
Read `commands\master_prompt.md` before any client-facing task.
