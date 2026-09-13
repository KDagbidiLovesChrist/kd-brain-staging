# AIS Classroom PDF Resources
**Source:** AI Automation Society Plus classroom, downloadable PDFs
**Date extracted:** 2026-05-17

---

## PDF 1: n8n MCP Pre-Flight Setup Checklist
**Lesson:** 1.4 n8n MCP Server, Claude Code module
**Purpose:** Complete before starting the n8n MCP lesson, saves hours of troubleshooting

### SECTION 1 · Open Your Project Folder
- Open the project folder from lesson 1.3 (Project + CLAUDE.md) in VS Code
- Open Claude Code from INSIDE that folder
- **Why:** If you open from the wrong location, the MCP server configures globally instead of at project level, causing a security warning every time Claude Code restarts

### SECTION 2 · Install Node.js
**Windows:**
- Go to nodejs.org → download LTS installer → run → accept all defaults
- Ask Claude: "Can you check if Node.js is installed and tell me the version?"

**Mac:**
- Ask Claude: "Can you install Homebrew for me?" → approve permissions
- Ask Claude: "Can you install Node.js using Homebrew?"
- Ask Claude: "Can you check if Node.js is installed and tell me the version?"

### SECTION 3 · Set Up n8n Account & API Key
- API keys require a PAID n8n Cloud plan (free plan has no API access)
- Log in → Settings → n8n API → Create API Key
- Give it a label, set expiration (or no expiration)
- Copy immediately, shown only once
- Copy your instance URL from the browser address bar

### SECTION 4 · n8n MCP Repo (clone during lesson)
```
https://github.com/czlonkowski/n8n-mcp
```

### SECTION 5 · Credentials to Have Ready
- n8n API key + instance URL
- API keys go in the `.env` file ONLY, NOT in chat, NOT in `.mcp.json`

### SECTION 6 · Verification Checklist Before Starting Lesson
- [ ] Claude confirms Node.js and npm installed
- [ ] n8n is accessible (cloud URL loads)
- [ ] API key created and copied
- [ ] Project folder open in VS Code, Claude Code running inside it

### Support
Post in Support Needed channel with: OS · Node.js version · terminal screenshot · exact error · which section you got stuck on
