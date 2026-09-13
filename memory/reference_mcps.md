---
name: reference-mcps
description: "Complete guide to MCPs (Model Context Protocol), what they are, every MCP connected to King David's setup, how to add new ones, and when to use MCP vs Python tool."
metadata: 
  node_type: memory
  type: reference
  originSessionId: 4b621969-d6bd-419c-9280-c6a4e0333ae8
---

# MCPs · Model Context Protocol Guide

## What Is an MCP?

**Plain English:** An MCP is a power-up for Claude. It gives Claude a new superpower, the ability to do something it couldn't do before, like browse the web, control a browser,
search GitHub, or interact with Google services.

**Analogy:** Claude is a smart person sitting in a room. Without MCPs, they can only use
what they already know. With MCPs, you're handing them tools, a phone to browse the web,
a laptop to write code, a keyboard to control a browser. Each MCP is a new tool handed in.

**Technical reality:** MCPs are server processes that Claude connects to. When Claude needs
to use an MCP (like scraping a website with Firecrawl), it sends a request to the MCP server,
the server does the work, and returns the result to Claude. Claude never leaves the conversation
, the MCP does the heavy lifting.

---

## MCPs CURRENTLY CONNECTED

### 1. Firecrawl MCP ✓ ACTIVE
**What it does:** Web scraping, web search, content extraction, site crawling
**When to use:**
- Scraping a business directory for leads
- Extracting content from a web page
- Searching the web for research
- Crawling a full website to read all its content

**Tools available:**
- `firecrawl_scrape`, scrape a single URL
- `firecrawl_crawl`, crawl an entire site
- `firecrawl_search`, web search with results
- `firecrawl_extract`, extract structured data from a page

**Key:** In settings.json, connected via `https://mcp.firecrawl.dev/fc-[KEY]/v2/mcp`
**Rate limit:** Varies by Firecrawl plan

### 2. Playwright MCP ✓ ACTIVE
**What it does:** Full browser automation, navigate, click, fill, extract, screenshot
**When to use:**
- When Firecrawl is blocked by a site's anti-scraping measures
- Automating repetitive web tasks (form fills, logins, clicking through pages)
- Taking screenshots of websites
- Extracting data that only appears after JavaScript loads (dynamic content)

**Tools available:** See `/browser` skill for full tool list
**Key:** No API key needed, runs locally via npx

### 3. n8n-mcp ✓ ACTIVE
**What it does:** Automation via n8n's node library, workflow orchestration, integrations with 300+ services
**When to use:**
- When you need to orchestrate multi-step workflows across services
- Connecting APIs and automating complex business processes
- Triggering external workflows from Claude sessions

**Tools available:**
- `n8n_list_workflows`, list active workflows
- `n8n_execute_workflow`, run a workflow
- `n8n_get_workflow`, read workflow details

**Key:** In settings.json, runs via `npx -y n8n-mcp`

---

## MCPs TO ADD (Pending Your Accounts)

### 4. Brave Search MCP
**Status:** Added 2026-06-16, removed same day (broken placeholder key). See `knowledge\TOOLS_CONNECTED.md` for details.

### 5. GitHub MCP (Needs GitHub Account + Token)
**What it does:** Git operations directly from Claude, push, pull, create repos, manage branches
**When to use:**
- Pushing newsletter or scraper tools to GitHub for deployment
- Creating a new repo for a project
- Managing branches when using GitHub Worktrees
- Deploying to trigger.dev (which reads from GitHub)

**Setup:**
1. Create GitHub account at github.com
2. Go to Settings → Developer Settings → Personal Access Tokens → Generate new token
3. Select scopes: `repo`, `workflow`, `read:org`
4. Copy the token
5. Add to settings.json + .env

**Config snippet:**
```json
"github": {
  "command": "npx",
  "args": ["-y", "@modelcontextprotocol/server-github"],
  "env": { "GITHUB_PERSONAL_ACCESS_TOKEN": "YOUR_TOKEN_HERE" }
}
```

### 6. Google MCP (Needs Google Cloud Setup)
**What it does:** Access Gmail, Sheets, Drive, Calendar directly from Claude
**When to use:**
- Reading and sending emails via Gmail API (better than SMTP)
- Archiving newsletter data to Google Sheets
- Syncing files to/from Google Drive
- Reading/writing calendar events for DCEO Brain

**Setup:** See `reference_google_cli.md` for full step-by-step (requires Google Cloud project)

---

## HOW TO ADD A NEW MCP TO SETTINGS.JSON

Open `C:\Users\Dell\.claude\settings.json` and find the `"mcpServers"` section.
Add the new MCP config block inside it. Example:

```json
"mcpServers": {
  "firecrawl": { ...existing... },
  "playwright": { ...existing... },
  "brave-search": {
    "command": "npx",
    "args": ["-y", "@modelcontextprotocol/server-brave-search"],
    "env": { "BRAVE_API_KEY": "your_key_here" }
  }
}
```

Or use the `/update-config` skill, it safely edits settings.json with Claude's help.

---

## MCP vs PYTHON TOOL · When to Use Which

| Situation | Use MCP | Use Python Tool |
|-----------|---------|----------------|
| Scraping a website | Firecrawl MCP | Only if Firecrawl is blocked |
| Controlling a browser | Playwright MCP | N/A · Playwright IS the MCP |
| Processing data (clean, filter, export) | N/A | Python tool |
| Sending emails | N/A | Python tool (send_gmail.py) |
| Complex data transformations | N/A | Python tool |
| Web search mid-session | Brave Search MCP | N/A |
| Git operations | GitHub MCP | N/A |
| Reading Google Sheets | Google MCP | Python (gspread library) |

**Rule of thumb:**
- MCP = reaching out to the web or an external service
- Python tool = processing data you already have locally

---

## ⚠️ MID-SESSION DISCONNECTS (found 2026-07-16)
Playwright and Context7 both silently disconnected partway through a long session (King noticed the system notices, asked why). Checked live: Node/npx healthy, `npx @playwright/mcp@latest --version` launched clean in seconds, config in `settings.json` correct. **Verdict: not broken, just a dropped connection** (like a phone call cutting out), most likely from the session running open a long time. Claude cannot reconnect an MCP mid-session, there is no tool for it. **Fix = close and reopen the Claude Code window/app** (a VS Code "reload window" or full restart), which forces a fresh handshake and both reconnect. Context7 is wired through the VS Code extension side (not `settings.json`, it showed up under `plugins/marketplaces/.../context7/.mcp.json` instead), same underlying pattern (`npx @upstash/context7-mcp`).
**Standing rule:** at the start of any session doing website building or QA (Playwright-dependent work), check the tool is actually connected (not just configured) before relying on it for the QA gate (Rule 21); if it's dropped, tell King early so he can reload rather than discovering it mid-QA.

## MCP QUICK REFERENCE

```
CONNECTED NOW:
  Firecrawl  → Scraping, search, extract       → Active ✓
  Playwright → Browser automation              → Active ✓
  n8n-mcp    → Workflow automation, integration → Active ✓

TO ADD (needs accounts):
  GitHub      → Git operations                 → Need GitHub account
  Google      → Gmail, Sheets, Drive, Calendar → Need Google Cloud

PREVIOUSLY TRIED:
  Brave Search → Web search in sessions        → Removed (broken placeholder key)

HOW TO ADD:
  Open settings.json → add to "mcpServers" section → restart Claude Code

MCP VS PYTHON:
  MCP   → external service, web interaction
  Python → local data processing, file operations
```
