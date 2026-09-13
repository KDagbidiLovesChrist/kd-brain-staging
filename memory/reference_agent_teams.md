---
name: reference-agent-teams
description: "How to build and orchestrate multi-agent teams, lead agent + specialists working together. Templates for content teams, client teams, and research teams."
metadata: 
  node_type: memory
  type: reference
  originSessionId: 4b621969-d6bd-419c-9280-c6a4e0333ae8
---

# Agent Teams · Multi-Agent Orchestration

## What Is an Agent Team?

A single sub-agent handles one task. An agent team handles a complex project by having
multiple specialised agents work together under one orchestrator.

**Analogy:** Think of a newsroom.
- The **editor-in-chief** (lead agent) assigns work and assembles the final piece
- The **researcher** (research agent) digs up facts and sources
- The **writer** (writing agent) turns research into compelling copy
- The **fact-checker** (review agent) verifies accuracy before publish
- The **designer** (design agent) formats the final output

Each person has a role. Each does their part. The editor assembles the result.

In Claude Code: each agent has a specific CLAUDE.md / brief. The lead agent orchestrates.
The specialists execute. The output is higher quality than any single agent could produce.

---

## WHEN TO USE AN AGENT TEAM vs A SINGLE AGENT

| Situation | Single Agent | Agent Team |
|-----------|-------------|-----------|
| Simple task (scrape a page) | ✓ | Overkill |
| Write a short email | ✓ | Overkill |
| Build a full newsletter | ✓ (usually fine) | Better for quality |
| Complex client proposal | Consider team | ✓ |
| Full website build | Consider team | ✓ |
| Multi-source research project | ✓ | Better for depth |
| Onboarding a new DCEO member | ✓ | ✓ |

**Rule of thumb:** Use a team when the task has distinct phases that benefit from specialisation.

---

## TEAM STRUCTURE TEMPLATES

### Team 1: Newsletter Production Team
For producing the highest-quality newsletters.

```
LEAD AGENT (Orchestrator)
  Reads brief from King David
  Assigns tasks to specialists
  Reviews all outputs
  Assembles final newsletter
  Applies brand guidelines
       |
  _____|_____________________________
  |          |           |          |
RESEARCH   STATS      WRITER    FORMATTER
AGENT      AGENT      AGENT     AGENT
  |          |           |          |
Finds 3-5  Finds 3-5   Writes all  Builds HTML
key stories key stats   sections    email
from web    with sources in brand   with images
           + sources    voice
```

**How to use it:**
1. King David types: "/newsletter write me a newsletter about [topic]"
2. Lead agent spawns: Research agent, Stats agent, Writer agent, Formatter agent
3. Research + Stats run in **parallel** (background, independent)
4. Writer gets research + stats → writes copy (foreground, needs their output)
5. Formatter gets copy → builds HTML email (foreground, needs writer output)
6. Lead agent reviews → sends to King David for human review

### Team 2: Client Proposal Team
For building professional, high-converting proposals.

```
LEAD AGENT (Orchestrator)
  Takes client brief
  Coordinates research + writing
  Assembles final proposal
       |
  _____|________________________
  |           |         |      |
INDUSTRY   COMPETITOR  ROI    WRITER
RESEARCH   RESEARCH    CALC   AGENT
AGENT      AGENT       AGENT    |
  |           |         |    Assembles
Research    Find 3-5   Run    all sections
their       competitors ROI   into proposal
industry    + gaps      calc  format
```

### Team 3: Lead Generation Team
For large-scale lead collection across multiple targets simultaneously.

```
LEAD AGENT (Orchestrator)
  Takes search brief (trade + cities)
  Spawns scrapers for each combination
  Collects + deduplicates results
  Exports to Excel
       |
  _____|_________________________________
  |         |         |         |       |
SCRAPER   SCRAPER   SCRAPER  SCRAPER  SCRAPER
Dublin    Cork      Galway   Limerick  Belfast
Plumbers  Plumbers  Electricians Cleaners Plumbers
```

This runs 5 scrapers in parallel → 5x faster than sequential scraping.

### Team 4: Research + Analysis Team
For deep dives on a topic (market research, competitor analysis, opportunity identification).

```
LEAD AGENT (Orchestrator)
  Takes research question
  Spawns research specialists
  Synthesises findings
  Produces report
       |
  _____|_______________________
  |           |          |    |
MARKET     COMPETITOR  TREND  OPPORTUNITY
RESEARCH    ANALYSIS   WATCH  IDENTIFIER
AGENT       AGENT      AGENT  AGENT
```

---

## HOW TO DESIGN YOUR OWN AGENT TEAM

When facing a complex task, use this framework:

1. **What is the final output?** (Newsletter, proposal, website, report)
2. **What are the distinct phases to produce it?** (Research → Write → Format → Review)
3. **Which phases can run in parallel?** (Research + Stats can both happen at once)
4. **Which phases depend on each other?** (Writing depends on research being done first)
5. **Design the team:** One agent per phase. Lead agent orchestrates.

**Diagram it before building:**
```
LEAD
  |
  |· PARALLEL PHASE (agents A, B, C run simultaneously)
  |
  |· SEQUENTIAL PHASE (agent D waits for A, B, C to finish)
  |
  |· FINAL PHASE (lead agent assembles everything)
```

---

## AGENT TEAM BRIEF TEMPLATE

Brief the LEAD AGENT with:

```
You are the lead agent for a [project type] team.
Your job: orchestrate specialist agents and assemble the final output.

FINAL OUTPUT NEEDED: [what King David wants]

YOUR TEAM:
- Agent 1 (Research): [exactly what to research]
- Agent 2 (Writing): [exactly what to write, after research]
- Agent 3 (Formatting): [exactly how to format, after writing]

SEQUENCE:
1. Spawn Agent 1 and Agent 2 in parallel (they're independent)
2. Once both return, give results to Agent 3
3. Agent 3 produces final output
4. Review for quality
5. Return to King David

QUALITY STANDARD: [what good looks like, tone, length, format]
```

---

## CONNECTION TO WAT FRAMEWORK

Agent teams are an evolution of the WAT framework:

```
SINGLE AGENT WAT:           AGENT TEAM WAT:
W → Workflow (SOP)          W → Orchestration plan
A → One Claude              A → Lead Claude + Specialist Claudes
T → Python tools            T → Python tools + specialist briefings

The W becomes the orchestration script.
The A becomes a team, not just one agent.
The T stays the same, tools are still tools.
```

---

## QUICK REFERENCE

```
WHAT: Multiple Claude agents working together under one lead
WHY:  Better quality, faster parallel work, specialisation
WHEN: Complex tasks with distinct phases, research, write, format, review

TEAM DESIGN:
  1. Define final output
  2. Break into distinct phases
  3. Identify what can run in parallel
  4. One agent per phase + one lead orchestrator

BRIEF THE LEAD: Give it the full picture, the team structure, and the sequence
BRIEF SPECIALISTS: Give them only their specific task (they have zero context)
```
