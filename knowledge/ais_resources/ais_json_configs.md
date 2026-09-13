# AIS JSON Configs & Environment Templates
**Source:** GitHub, czlonkowski/n8n-mcp + AIS classroom
**Date extracted:** 2026-05-17
**Purpose:** Exact configs to set up n8n MCP, Claude Code integration, and environment variables

---

## CONFIG 1 · Add n8n-mcp to Claude Code (settings.json)
Add this to `C:\Users\Dell\.claude\settings.json` under `mcpServers`:

```json
{
  "mcpServers": {
    "n8n-mcp": {
      "command": "npx",
      "args": ["n8n-mcp"]
    }
  }
}
```

**Quick start command:** `npx n8n-mcp`
**No installation needed**, npx downloads and runs automatically

---

## CONFIG 2 · n8n-mcp .env Template (Local/Standard)
Save as `.env` in your n8n-mcp project folder:

```env
# === DATABASE ===
NODE_DB_PATH=./data/nodes.db
MCP_LOG_LEVEL=info
NODE_ENV=development
REBUILD_ON_START=false

# === SERVER ===
MCP_MODE=stdio
MCP_SERVER_PORT=3000
MCP_SERVER_HOST=localhost

# === HTTP MODE (only if MCP_MODE=http) ===
PORT=3000
HOST=0.0.0.0
AUTH_TOKEN=your-secure-token-here   # generate: openssl rand -base64 32

# === N8N API (required for workflow management tools) ===
N8N_API_URL=                        # your n8n instance URL (no /api/v1 suffix)
N8N_API_KEY=                        # from n8n: Settings > n8n API > Create API Key
N8N_API_TIMEOUT=30000
N8N_API_MAX_RETRIES=3

# === OPENAI (optional · for template metadata generation) ===
OPENAI_API_KEY=
OPENAI_MODEL=gpt-4o-mini
```

---

## CONFIG 3 · n8n-mcp .env Template (Docker)
Save as `.env` for Docker deployment:

```env
# === n8n ===
N8N_BASIC_AUTH_ACTIVE=true
N8N_BASIC_AUTH_USER=admin
N8N_BASIC_AUTH_PASSWORD=changeme    # CHANGE IN PRODUCTION
N8N_HOST=localhost
N8N_PORT=5678
N8N_PROTOCOL=http
N8N_WEBHOOK_URL=http://localhost:5678/
N8N_ENCRYPTION_KEY=                 # generate: openssl rand -hex 32

# === n8n-mcp ===
MCP_PORT=3000
MCP_AUTH_TOKEN=                     # generate: openssl rand -hex 32
N8N_API_KEY=                        # from n8n: Settings > n8n API > Create API Key
LOG_LEVEL=info

# === GitHub (only for custom builds) ===
GITHUB_REPOSITORY=czlonkowski/n8n-mcp
VERSION=latest
```

---

## CONFIG 4 · n8n-mcp System Prompt (add to CLAUDE.md for n8n projects)
Add these principles when building n8n workflows with Claude:

```
## n8n Workflow Rules
- Silent Execution: Run tools without commentary. Respond AFTER all tools complete.
- Templates First: ALWAYS check 2,352 available templates before building from scratch.
- Never Trust Defaults: Default parameter values cause runtime failures. Explicitly configure ALL parameters.
- Validation Pattern: validate_node(mode='minimal') → validate_node(mode='full') → validate_workflow
- Safety Rule: NEVER edit production workflows directly with AI.
```

---

## KEY FACTS
| Item | Value |
|------|-------|
| GitHub Repo | github.com/czlonkowski/n8n-mcp |
| npm Package | `npx n8n-mcp` |
| Hosted Option | dashboard.n8n-mcp.com (free: 100 calls/day) |
| n8n Templates Available | 2,352 workflow templates |
| n8n Nodes Documented | 1,650 (820 core + 830 community) |
| Stars | 21k GitHub stars |
