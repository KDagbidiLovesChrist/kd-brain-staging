---
name: reference-bedrock-agents-architecture
description: "Amazon Bedrock Agents, how it works, why we use it for DCEO Brain, what it replaces"
metadata: 
  node_type: memory
  type: reference
  originSessionId: 8b13e16a-2e53-418d-996a-88cfddd7dcc5
---

# Amazon Bedrock Agents · DCEO Brain Architecture Reference

## What It Is
Amazon's native managed AI agent service. Runs inside AWS. Amazon pays.
Replaces manual Lambda orchestration code with a managed service that does it natively.

## Why We Use It (Not Custom Lambda Orchestration)
- Multi-agent collaboration built in, no orchestration code needed
- Knowledge Base built in, upload folder, Bedrock indexes it automatically (RAG native)
- Tool routing built in, Action Groups replace manual API calls
- 100% inside Amazon infrastructure, NDA safe
- Amazon pays all costs, Lambda + Bedrock Agents + Claude model

## How It Works With Slack

```
DCEO types @DCEO Brain [message] in Slack
        │
        ▼
Lambda (simplified, just the webhook handler)
Receives Slack message → passes to Bedrock Agent
        │
        ▼
Bedrock Agents (supervisor = Orcha)
Reads DCEO_MASTER_CONTEXT.md (agent instructions)
Queries Knowledge Base (DCEO_BRAIN folder, all .md files)
Routes to correct sub-agent
        │
        ▼
Sub-agents run (parallel if needed):
Email / Briefing / Handover / Risk / Tickets / Admin
        │
        ▼
Response back to Lambda → posted to Slack thread
```

## Multi-Agent Collaboration
Bedrock calls this natively. Supervisor agent routes to sub-agents.
Complex tasks: multiple sub-agents run in parallel, results merged.
No code needed, defined in Bedrock console.

## Knowledge Base
- Upload DCEO_BRAIN\ folder once
- Bedrock indexes all .md files automatically (RAG)
- Agent queries it when it needs information
- Update: re-upload folder → Bedrock re-indexes → all agents updated instantly

## Action Groups (Tools)
How Bedrock Agents connects to tools (email, calendar, tickets):
- Define an Action Group in Bedrock console
- Point it at a Lambda function that calls the tool
- Agent decides when to use it based on the request
- Microsoft Graph API (email reading) → add as Action Group in Phase 3

## Lambda's New Role (Simplified)
With Bedrock Agents, Lambda only:
1. Receives Slack @mention (webhook)
2. Passes message to Bedrock Agent
3. Returns response to Slack
Orchestration, knowledge loading, prompt building, all moved to Bedrock Agents.

## Cost
All costs within Amazon's AWS account. King David pays £0.
- Lambda invocations, Amazon pays
- Bedrock Agents, Amazon pays
- Claude Opus 4.7 model calls, Amazon pays
- Knowledge Base storage, Amazon pays

## Files That Map to Bedrock Agents
| File | Maps to |
|------|---------|
| DCEO_MASTER_CONTEXT.md | Agent Instructions (system prompt) |
| knowledge\ .md files | Knowledge Base (auto-indexed) |
| skill .md files | Knowledge Base (auto-indexed) |
| lambda_function.py | Simplified webhook handler only |

## Setup Steps (After Manager Approval)
1. Create Bedrock Agent in AWS console → name: DCEO Brain
2. Set DCEO_MASTER_CONTEXT.md as agent instructions
3. Create Knowledge Base → upload DCEO_BRAIN folder
4. Create sub-agents for each skill (email, briefing, etc.)
5. Enable Multi-Agent Collaboration → set Orcha as supervisor
6. Update lambda_function.py to call Bedrock Agent instead of direct invoke
7. Test @DCEO Brain in Slack → verify response
