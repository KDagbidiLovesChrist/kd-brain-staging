# AIS Workflow Patterns · Claude Code Equivalents
**Source:** AIS classroom lessons (n8n patterns translated to Claude Code)
**Date extracted:** 2026-05-17
**Purpose:** n8n workflow logic converted to Claude Code skills, no n8n dependency

---

## TRANSLATION KEY
Every n8n node becomes a Claude Code equivalent:

| n8n Node | Claude Code Equivalent |
|----------|----------------------|
| HTTP Request | `WebFetch` MCP tool |
| Trigger (schedule) | Claude Routines (scheduled automations) |
| Trigger (webhook) | Playwright MCP → listen for events |
| AI Agent node | Claude prompt in skill |
| Gmail node | Gmail SMTP via Python / Gmail API |
| Google Sheets node | Google Sheets API |
| Set node | Variable assignment in skill |
| If/Switch node | Conditional logic in skill markdown |
| Code node | Python script via Bash tool |
| Merge node | Combine outputs in skill |

---

## WORKFLOW 1 · Customer Support Email Agent
**Source:** Lesson 2.3 Masterclass, Building the Workflow
**What it does:** Checks Gmail every 15 minutes → AI reads email → matches against knowledge base → drafts reply

**Claude Code version:**
```
Trigger: Claude Routine (every 15 min)
Step 1: Gmail API → fetch unread emails
Step 2: For each email → Claude reads subject + body
Step 3: Claude checks knowledge_base/ folder for relevant info
Step 4: If relevant → draft reply → send via Gmail SMTP
Step 5: If not relevant → skip / label
```
**Files needed:** `.env` (GMAIL_APP_PASSWORD), knowledge base markdown files
**Skill to build:** `/email-agent`

---

## WORKFLOW 2 · Knowledge Base Indexer
**Source:** Lesson 2.3 Masterclass
**What it does:** Ingests documents → indexes them → makes them searchable by the email agent

**Claude Code version:**
```
Trigger: Manual (/index command) or on new file in folder
Step 1: Read all .md / .pdf / .txt files in knowledge_base/ folder
Step 2: Claude extracts key facts, FAQs, product info
Step 3: Write structured summary to knowledge_base/index.md
Step 4: Used by email agent for context
```

---

## WORKFLOW 3 · Lead Scraper Pipeline
**Source:** /scrape skill (already built)
**What it does:** Search local businesses → extract contact details → export CSV

**Current skill:** `/scrape`, fully functional
**Enhancement from AIS:** Add error handling + output quality checks (lesson 3.x Enhancement Philosophy)

---

## WORKFLOW 4 · Newsletter Automation
**Source:** /newsletter skill (already built)
**What it does:** Research topic → write content → send via Gmail

**Current skill:** `/newsletter`, functional, needs Perplexity API key

---

## ENHANCEMENT PHILOSOPHY (Lesson 3.1)
When upgrading any workflow/skill, check in this order:
1. **Error handling**, does it fail gracefully? Does it notify and recover?
2. **Output quality**, is output clean, formatted, consistent, client-ready?
3. **User experience**, easy to trigger? Easy to read? Easy to adjust?

Enhancement ≠ adding features. Enhancement = making existing work more reliable.

---

## VIBE CODING FRAMEWORK (Lesson 2.1)
**Wrong way:** "Write a for loop that iterates over the list and checks each item"
**Right way:** "Scan the list of businesses and flag any that don't have a website"

Always describe the OUTCOME you want, not the code steps. This is the WAT framework in practice.
