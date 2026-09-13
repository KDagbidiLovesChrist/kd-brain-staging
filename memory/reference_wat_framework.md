---
name: reference-wat-framework
description: "Full WAT framework explanation, what each layer is, how they connect, Skills vs Tools vs APIs vs MCP"
metadata: 
  node_type: memory
  type: reference
  originSessionId: dd50c725-355b-46cf-a43e-1da1abd7e81c
---

## WAT = Workflows, Agents, Tools

**Origin (corrected 2026-05-23):** This is **Nate Herk's framework**, taught in his AIS+ Claude Code course Phase 2 Module 1.3 "The WAT Framework". King David learned it from Nate and adopted it into his own system. Previous CLAUDE.md framing as "King David's invention" was inaccurate. **King David confirmed: *"I learned from Nate, so that's why I took his WAT framework."***

**How to talk about it:** When pitching to clients or in public, attribute to Nate ("Nate Herk's WAT framework I use to structure every automation"). Don't claim authorship, easy to disprove and unnecessary. The framework is no less powerful when correctly attributed.

---

A framework that separates AI reasoning from deterministic execution to improve reliability. Each step at 90% accuracy = 59% success after 5 steps. WAT fixes this by keeping Claude in the decision layer only.

### The 3 Layers

| Layer | Location | What It Is |
|---|---|---|
| Workflows | `workflows/*.md` | Markdown SOPs · written instructions for a specific job |
| Agents | · | Claude · reads the SOP, sequences tools, handles errors |
| Tools | `tools/*.py` | Python scripts · execute one job reliably every time |

### Key File Types

- **CLAUDE.md**, Claude's brain for this project. Rules, operating style, how to behave. Project-wide and permanent.
- **`workflows/task_name.md`**, The SOP for one specific automation. Tells Claude which tools to run and in what order.
- **`tools/script_name.py`**, Executes one job. Already wired to its API. Claude just runs it.
- **`.env`**, Secret keys (API credentials). Never written into scripts.
- **`.tmp/`**, Disposable output files. Regenerated on every run.
- **`.claude/commands/skill_name.md`**, Makes a `/skill-name` slash command. Triggers Claude to read the workflow.

### Skills vs Tools vs APIs vs MCP

| Term | What It Is | Example |
|---|---|---|
| Skill | Slash command trigger · fires the workflow | `/newsletter` |
| Tool | Python script that executes one job | `fetch_rss.py` |
| API | External service the tool calls | Anthropic API, AWS SES |
| MCP | Direct Claude connector · no Python script needed | Gmail MCP server |

### How Claude Knows Which API to Use

Claude doesn't choose, the tool already knows. The Python script is pre-wired to its API. The workflow tells Claude which tool to run. Claude's only job is sequencing and error handling.

### The Chain

```
Skill (/newsletter)
  → Claude reads workflow SOP
    → Claude runs tool (fetch_rss.py)
      → Tool calls API (AWS RSS feed)
        → Result returns to Claude
          → Claude runs next tool
            → ... until output is complete
```

### WAT is Universal

Same framework applies to any repeatable automation:
- Email summarizer → `workflows/email_summarizer.md` + fetch/summarize/send tools
- YouTube channel → `workflows/youtube_channel.md` + script/thumbnail/upload tools
- Lead research → `workflows/lead_research.md` + scrape/filter/export tools

Each automation: one new workflow file + the tools it needs + one new skill command.
Existing tools (like `summarize_content.py`) get reused across automations.
