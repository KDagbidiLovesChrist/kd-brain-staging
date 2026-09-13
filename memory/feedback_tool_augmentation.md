---
name: feedback-tool-augmentation
description: "Think tool-first: when Claude hits a capability wall, wire a tool/key/MCP around it instead of saying 'can't'. King's directive. Example: Gemini API = video eyes (Claude can't watch video); Claude stays the brain that synthesises."
metadata: 
  node_type: memory
  type: feedback
  originSessionId: 46b68814-1de0-4e09-8365-85ca635c959f
---

King's directive (2026-06-03): **think tool-first.** When I hit a capability limit, the move is to connect a key/tool/MCP/model that doesn't have that limit, not to stop at "I can't."

**Why:** my capability is extensible through tools, that's the WAT model (I'm the Agent; tools are the T). Each key King connects grows the studio's arsenal and what we can deliver to clients. King values this and called it out explicitly ("we can connect you to keys and do stuff, you need to think like that").

**How to apply:**
- Hit a wall → name the tool that solves it → wire it (with King's key) → use it as a sense/hand while I synthesise and decide.
- **Proven example:** Claude can't watch video; **Gemini (gemini-2.5-flash) has native video understanding.** Built `tools\gemini_watch.py` (GEMINI_API_KEY in `.env.master`, validated). Flow: Gemini watches a video (YouTube link or file) → I read its breakdown → fold it into the work. Same pattern for any future gap.
- **Be honest about the split:** the tool is the eyes/hands, I'm the brain. Don't overclaim "I can now do X", say "we wired X so the system can."
- Keep it lean: prefer free tiers (Gemini free, Ollama for bulk text), flag any real spend.

Related: [[reference-wat-framework]], [[feedback-lean-spend-llama-routing]].
