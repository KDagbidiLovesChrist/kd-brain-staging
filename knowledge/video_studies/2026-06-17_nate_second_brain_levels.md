# Reference · Nate's "Second Brain" 5 Levels + where KD sits

*Source: Nate Herk, "Every Level of a Claude Second Brain Explained" (youtube DTCyvo6cC54), watched
2026-06-17 via `/watch`. Full study: `knowledge/video_studies/2026-06-17_nate_second_brain_levels.md`.*

## The 5 levels (climb ONLY if there's pain)
1. **Foundation / Router**, `CLAUDE.md` (loads at session start; says who you are + where things live) +
   `context/` (about-me, stack/conventions) + `decisions/log.md` + `projects/`. Stops re-explaining.
2. **Curated Wiki**, `wiki/` (concepts/comparisons/sources/techniques, cross-linked + index pages) +
   `MEMORY.md` auto-memory sidecar (AI updates it; toggle with `/memory`). Build on past notes.
3. **Semantic Search**, `vector-index/` + a vector DB (Pinecone/Qdrant/Supabase): chunk → embed → search
   by *meaning*. Use only when keyword search "whiffs."
4. **Knowledge Graph**, `knowledge-graph/` (entities.json + relationships.json, typed links, multi-hop;
   LightRAG/Neo4j). Only if your questions are about tracing relationship chains (CRM-like).
5. **Always-on Brain-OS**, autonomous background "dream cycle" syncing. Needs a running server. Heavy.

## Nate's rules
- **"Start with the question, not the tech."** Pick the level by how you'll RECALL the data.
- **"Most people land at 1, 3."** Complexity climbs as you go up, higher ≠ better.
- **"Find the lowest level that fits. If there's no pain, why create more?"** Stop at the first yes.
- A single project can run different folders at different levels.
- **Context vs Connections:** Context = evergreen knowledge (store it). Connections = live data
  (Slack/Gmail/ClickUp), *access on demand, don't store* (avoids noise). Lookup order: internal first, then external.
- The hard part is **ingestion** (getting what's in your head INTO the system), use `/grill-me` to interview yourself.

## WHERE KD SITS  →  Level 1, strong into Level 2  (exactly where Nate says to be)
- L1 ✅ `CLAUDE.md` router + `memory/` (= context) + handoffs/sessions (= decisions log) + Active Projects + per-project scaffold.
- L2 ✅ `knowledge/` (= wiki) + `MEMORY.md` index + `autoMemoryDirectory` auto-memory.
- L3, L5 ❌ on purpose. **No vector DB / knowledge graph / always-on.** = supermemory/Archon territory.

## DIRECTIVE (lean-spend, Rule #12)
**Stay at Level 1, 2. Do NOT climb to 3, 5 (supermemory/Archon/vector DB) unless KD hits real keyword-search
pain.** Nate himself + Cole both build direct for control. Our SessionStart+Stop loop already gives the
self-improving retrieval. To improve: deepen INGESTION with `/grill-me`, keep notes cross-linked, and add
live "Connections" (MCP) rather than storing more.
