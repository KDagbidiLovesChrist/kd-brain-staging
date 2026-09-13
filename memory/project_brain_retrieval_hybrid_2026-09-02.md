---
name: project_brain_retrieval_hybrid_2026-09-02
description: "King ruled 2 Sep: hybrid retrieval for the brain (FTS5 + BM25 first, then a local embedding model + sqlite-vec fused by reciprocal rank fusion), queued as rung R right after Stage 2, measured on 20 real questions before any yes. Elasticsearch refused at this scale."
metadata: 
  node_type: memory
  type: project
  originSessionId: ae01ba25-a571-403d-b5ba-1c8458631cfc
  modified: 2026-09-04T04:05:27.558Z
---

# Hybrid retrieval for the brain, ruled 2 Sep 2026

**The question that started it, his words:** *"This data base is it elastic search engine . we can honeslty combine our engine with the best seacrh engine to make this llm most powerful what you think?"*

**Measured before answering (Rule 16):** the engine's database is SQLite (`node:sqlite`, about 40 call sites in `db.ts`; Prisma in `package.json`, never imported), not Elasticsearch. `tools\brain_retrieval.py` is keyword/TF-IDF over `memory\` and `knowledge\`, no embeddings, by its own header *"upgradeable to embedding search later if this proves weak."* Node's built-in SQLite has **FTS5 with `bm25()` compiled in**: proven live in the engine's own runtime that night (a ranked hit came back from an in-memory FTS5 table). No embedding model in Ollama yet (llama3.2:1b, qwen3:8b, llama3.2). The brain is 750 markdown files; `memory\` is 2.3 MB.

**The ruling, verbatim, spelling untouched:** *"add a local embedding model plus sqlite-vec in the same database, fused with BM25 by reciprocal rank fusion. so Queue it as a small staged build right after Stage 2: FTS5 index of the brain inside LOGOI, measured before and after with 20 real questions from your own memory files (hit@5, seconds), the 14 provers still green, then your yes on whether to add the embedding lane. Say the word and it goes on the ladder as its own iota with the four cells. When will we do this?"*

**Why not Elasticsearch:** wrong tool for 750 files on a 20 GB laptop with no GPU that had just spent eight days in a kernel leak from file watchers; a JVM service idling at 2 to 4 GB. July's six-skeptic panel (`_ops\PARITY_CONSENSUS_2026-07-04.md`) had already ruled *"vector DBs: the brain's index beats embeddings at this scale."* Elasticsearch stays the Stage 9 answer: a client with millions of records, business lane, on a box on his network.

**On the ladder:** rung **R**, right after Stage 2, on the living board (`tools\progress_board.py`, `STAGE_LADDER` and `RETRIEVAL_IOTAS`):
- **R.1** FTS5 index of the brain inside LOGOI; `/api/retrieve` reads it. Test: 20 real questions drafted from his memory files (his veto on the list), hit@5 and seconds on TF-IDF first, then on FTS5, both numbers on the board; the 14 provers green; the index rides to the drive inside the brain family.
- **R.2** the embedding lane: `nomic-embed-text` through Ollama (about 270 MB, free) plus `sqlite-vec` in the same database, BM25 and vectors fused by reciprocal rank fusion. Built only on R.1's numbers and his yes. The model never sees a faith file (lane rule); the same door on Claude and Ollama (ruling 11).

**When (estimates, grade S, each step behind his yes):** Thu 3 Sep close Stage 2; Fri 4 Sep the friend's PC (4b); Sat 5 Sep or the first free evening after, R.1; the week of 7 Sep, R.2 if R.1's numbers earn it. If Stage 2 slips, R slips with it.

**Why it matters (his commercial model):** better retrieval means more claims traceable, the grounding gate passes more, more GREEN missions, higher q, higher billed. It also attacks the speed problem: tighter context handed to the tracer, which today fails to complete 57% of the time on this CPU. In his loop it is the Integrate step: gather the right facts, then Derive, then Solve.

**How to apply:** keep search over *his brain* (this) and search over *the web* (Perplexity, Firecrawl, Tavily, the planned LOGOI `search_web` door with receipts per ruling 8) as two different doors; never merge them into one system. Related: [[project_kd_robot_three_nodes_2026-08-29]], [[project_logoi_agent]], [[project_lllm_logic_layer_2026-08-25]].

## Both rungs closed, 4 Sep 2026, real numbers

**R.1 and R.2 are both done, proven on the real 20-question benchmark against the real 4,849-section corpus, not a sample.** Real result: **TF-IDF 12/20 hit@5 (0.353s total) → FTS5 14/20 (0.116s total) → Hybrid 15/20 (4.124s total, ~0.2s/query)**. Each rung beats the one before it; the embedding lane earns the cost King accepted with "do the further upgrade" (`_ops\KD_ACCEPTANCES.md`). All 4,849 sections embedded via `nomic-embed-text` through Ollama, 0 skipped.

**Two real bugs found by the build itself, both fixed before any number was trusted (the whole point of testing against the real corpus instead of a toy fixture):**
1. **The FTS5 rebuild was silently deleting R.2's embeddings.** `brain_retrieval_fts5.build_index()` used to swap the whole database file on rebuild (atomic, but the embeddings and FTS5 tables share one file); any later FTS5 rebuild wiped the embedding lane clean. Caught when the benchmark reported "embeddings not built" moments after a real embedding run had just finished. Fixed by rebuilding the `sections` table in place inside a SQL transaction instead of swapping files, so sibling tables survive.
2. **RRF fusion was keying results by file, not by section.** `search_hybrid()`'s reciprocal-rank fusion used `(path, name)` as its dedup key; when one file had two matching sections (routine on a real corpus), their scores got summed and could out-rank a file with one strong section, breaking the "degrades to plain FTS5 order when one lane is empty" guarantee. Caught by a real test against the live corpus, not a synthetic one. Fixed by keying on `(path, name, snippet)` instead, matching the section-level granularity every other search function already uses.

Both fixes are why the numbers above are trustworthy: they were only accepted after re-verifying against the real corpus, not the first run's output. Full suite green (1,288 passed; the sole failure, a Google Drive quota mock test, is unrelated and pre-existing since 10 Jul). Gate green at 69.38% (floor 50). Board rebuilt, the live loop restarted to serve the fixed code, committed and pushed to GitHub (`f53a3370`).
