---
name: reference-project-template
description: "Standard folder structure and required files for every new project King David builds. Use this as the blueprint when creating any new automation, service, or tool."
metadata: 
  node_type: memory
  type: reference
  originSessionId: 4b621969-d6bd-419c-9280-c6a4e0333ae8
---

# Project Template · Standard Structure

Every project King David builds follows this exact structure. Consistency means
Claude always knows where to find things, and every project can be handed to a client
or another developer without confusion.

---

## STANDARD FOLDER STRUCTURE

```
[Project Name]\
├── CLAUDE.md              ← Project brain (READ FIRST pointer + WAT chain)
├── .env                   ← API keys and secrets (NEVER share or commit)
├── .gitignore             ← Tells git to ignore .env + temp files
├── workflow\
│   └── [project]_sop.md  ← W: the step-by-step workflow (plain English)
├── tools\
│   ├── [tool_1].py        ← T: individual tool scripts
│   ├── [tool_2].py
│   └── run_[project].py  ← T: master runner (calls all tools in order)
├── commands\
│   └── [project].md      ← S: /skill trigger file
├── sessions\              ← Session history (auto-saved)
├── handoffs\              ← Session handoff files
└── .tmp\                  ← Temporary outputs (CSV, HTML, JSON, throwaway)
```

---

## REQUIRED FILES

### 1. CLAUDE.md (Project Brain)
Every project must have this. Template:

```markdown
> **READ FIRST:** `C:\Users\Dell\.claude\CLAUDE.md`, master brain, operating rules,
> WAT framework. Read it before doing anything in this project.
> **BRAND:** `C:\Users\Dell\.claude\brand_assets\brand_guidelines.md`, read before
> generating any external-facing content.

# [Project Name] · Project Brain

## What This Project Does
[One paragraph: what problem it solves, who it's for, what it outputs]

## WAT Chain
- **W (Workflow):** `workflow\[name]_sop.md`
- **A (Agent):** Claude, reads SOP, orchestrates the pipeline
- **T (Tools):** `tools\`, [number] Python scripts + master runner
- **S (Skill):** `/[skill-name]`, one command runs everything
- **Money:** [how this generates income, price, method, target client]

## Folder Structure
[paste the actual folder tree here]

## APIs Used
[list each API, what it does, where the key lives in .env]

## Setup (one-time)
[numbered steps to get it running for the first time]

## Status
[COMPLETE / IN PROGRESS / PENDING], [date]. [one line of context]
```

### 2. .env (Secrets File)
Template for every project:
```
# [Project Name] · Environment Variables
# DO NOT SHARE. DO NOT COMMIT TO GITHUB.

# Anthropic (Claude AI)
ANTHROPIC_API_KEY=your_key_here

# [Project-specific keys]
PERPLEXITY_API_KEY=your_key_here
FIRECRAWL_API_KEY=your_key_here
GMAIL_ADDRESS=your_gmail_here
GMAIL_APP_PASSWORD=your_app_password_here
```

### 3. .gitignore
Always include this so API keys don't accidentally get pushed to GitHub:
```
.env
.tmp/
__pycache__/
*.pyc
sessions/
handoffs/
```

### 4. Workflow SOP (workflow\[name]_sop.md)
The W in WAT. Written in plain English. This is the recipe.

Template structure:
```markdown
# [Project Name] · Workflow SOP

## Purpose
[One sentence: what this workflow does]

## Trigger
[What starts this workflow, a /skill command, a schedule, a request]

## Steps
1. [Step 1, what happens, which tool runs]
2. [Step 2, what happens, which tool runs]
3. [Step 3, what happens, which tool runs]
[etc.]

## Error Handling
- If [X] fails: [what to do]
- If [Y] fails: [what to do]

## Output
[What the workflow produces, file, email, report, etc.]

## Success Criteria
[How do you know it worked correctly?]
```

### 5. Master Runner (tools\run_[project].py)
The T in WAT. Calls all tools in order.

Template:
```python
#!/usr/bin/env python3
"""
[Project Name], Master Runner
Runs the full pipeline end-to-end.
Usage: python run_[project].py
"""

import subprocess
import sys
from pathlib import Path

def run_step(script_name, description):
    print(f"\n{'='*50}")
    print(f"STEP: {description}")
    print('='*50)
    result = subprocess.run([sys.executable, script_name], capture_output=True, text=True)
    if result.returncode != 0:
        print(f"ERROR in {script_name}:")
        print(result.stderr)
        sys.exit(1)
    print(result.stdout)
    print(f"✓ {description} complete")

if __name__ == "__main__":
    run_step("tool_1.py", "Step 1 description")
    run_step("tool_2.py", "Step 2 description")
    run_step("tool_3.py", "Step 3 description")
    print("\n✓ Pipeline complete.")
```

---

## NAMING CONVENTIONS

| Thing | Convention | Example |
|-------|-----------|---------|
| Project folder | Title Case with spaces | `Newsletter Demos` |
| Python files | snake_case | `fetch_articles.py` |
| Workflow files | snake_case + `_sop` | `newsletter_sop.md` |
| Skill files | lowercase | `newsletter.md` |
| .tmp files | include timestamp | `leads_20260515_143022.csv` |
| Session files | date format | `session_2026-05-15.md` |

---

## BEFORE STARTING ANY NEW PROJECT

Checklist:
- [ ] Create the folder structure above
- [ ] Write CLAUDE.md with READ FIRST pointer + WAT chain
- [ ] Create .env with placeholder keys
- [ ] Create .gitignore
- [ ] Write the workflow SOP (even rough, refine as you build)
- [ ] Build tools one by one, testing each before the next
- [ ] Build the master runner last (after tools are tested individually)
- [ ] Create the /skill file in C:\Users\Dell\.claude\commands\
- [ ] Test the full pipeline end-to-end at least 3 times
- [ ] Add to CLAUDE.md Active Projects section
- [ ] Add memory entry to MEMORY.md if significant learnings

---

## BRAND ASSETS INTEGRATION

For any project that produces external-facing content:
1. Add to CLAUDE.md: `> **BRAND:** C:\Users\Dell\.claude\brand_assets\brand_guidelines.md`
2. At the start of any content generation, read brand_guidelines.md
3. Apply: colors, tone, bio format, value language

This ensures every newsletter, website, and proposal feels like King David, consistent,
professional, faith-grounded.
