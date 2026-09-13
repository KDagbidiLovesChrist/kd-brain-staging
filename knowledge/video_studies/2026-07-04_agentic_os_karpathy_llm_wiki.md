# Study — King's 2 YouTube links: "Agentic OS 10x" + "Fable 5 + Karpathy's LLM Wiki" (2026-07-04)
> Cloud session: YouTube itself is blocked by the network policy (no Gemini key here either — keys-off-cloud).
> Method instead (Rule 16): identified both videos, then went to the PRIMARY sources — Karpathy's own gist + the
> production skill repo — which beats a video summary. Full `/watch` on the laptop optional if King wants the presenter's exact takes.

## Video 1 — "The Agentic OS Setup That Will 10x Claude Code" ([link](https://youtu.be/HRw-vP0j8OM))
The Agentic-OS recipe circulating now: 4 layers — intelligence (Claude Code), execution (browser agents), research, memory (Obsidian) — plus domains→tasks→skills, hooks, shared business context. **Verdict for us: ~all already built.** The KD brain has the 5 sub-brains, 107 Logic skills, the standing army, master_prompt shared context, hooks (SessionStart, PreCompact), Obsidian vault, and now the V.A.U.L.T. HUD. Nothing new to copy; useful as confirmation the brain is ahead of the "10x" meta. Sources: [GrowwStacks guide](https://growwstacks.com/blog/build-agentic-os-for-claude-code) · [MindStudio guide](https://www.mindstudio.ai/blog/how-to-build-agentic-operating-system-claude-code)

## Video 2 — "Fable 5 + Karpathy's LLM Wiki is Basically Cheating" ([link](https://youtu.be/hQvwMj7IJe4))
**The real find.** Karpathy's llm-wiki pattern ([his gist](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f), Apr 2026): instead of re-searching raw documents every time (RAG), the LLM **maintains a persistent, compounding wiki** — 3 layers (immutable `raw/` sources · LLM-maintained `wiki/` pages · a schema doc that disciplines the LLM as maintainer) and 3 operations (**ingest → query-with-citations → LINT**), plus `index.md` + append-only `log.md`.

### Honest gap check vs the KD brain (it already IS ~70% an LLM wiki)
| Karpathy piece | KD brain today |
|---|---|
| schema doc | ✅ CLAUDE.md + MEMORY.md conventions |
| index.md | ✅ MEMORY.md (one line per memory) |
| ingest | ✅ `/learn` + inbox |
| query | ✅ `/search` |
| log | 🟡 handoffs (session-level, close enough) |
| **raw/ vs wiki/ separation** | ❌ knowledge/ mixes raw dumps + synthesis |
| **LINT pass** | ❌ **THE GAP.** Rule 19 (no self-contradiction) is a principle with no routine — no scheduled sweep for contradictions, stale claims (e.g. old skill counts!), orphan pages, missing cross-links |
| **answers become pages** | ❌ good `/search` answers evaporate in chat instead of compounding |

### Adopted (2026-07-04)
1. **Installed the skill:** `karpathy-llm-wiki` ([Astro-Han/karpathy-llm-wiki](https://github.com/Astro-Han/karpathy-llm-wiki), ~446★, production-proven 94 articles) → `skills/` (plugin #55). T1.
2. **The 3 upgrades to run with it:**
   - **BRAIN LINT** — monthly (or on `/context`): sweep memory/+knowledge/ for contradictions, stale numbers, orphans, missing links; fix or flag. This makes Rule 19 executable. First candidates the lint would catch: stale skill counts in older files.
   - **Compound the answers** — when a `/search`/research answer is good, save it as a knowledge page + index line (extend the /search habit; no new command needed).
   - **raw vs synthesis** — new dumps go to `knowledge/raw/` (or inbox) untouched; synthesized pages stay in knowledge/ proper. Adopt gradually, no big migration (money mode).
**Why it matters:** the brain's north star is "memory must surpass Senku" — Karpathy's pattern is exactly the maintenance discipline that makes memory COMPOUND instead of rot.
