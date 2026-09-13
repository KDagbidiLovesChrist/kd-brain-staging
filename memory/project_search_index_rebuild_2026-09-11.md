---
name: project-search-index-rebuild-2026-09-11
description: "R5.4 done 11 Sep: the brain's meaning-vectors rebuilt (5,148 of 5,148 sections, 0 old-brain paths, all aligned). The 20-question benchmark fell (Hybrid 15 to 13), traced to the corpus changing and two benchmark defects, not the rebuild. The rebuild also triggered sync incident 5."
metadata: 
  node_type: memory
  type: project
  originSessionId: 2333f35b-611b-48ad-85ea-c72f5435ee93
  modified: 2026-09-11T19:56:04.186Z
---

# The search index rebuild (R5.4, 11 Sep 2026)

**Why:** `_ops/brain_fts5_index.sqlite3` holds two halves. The word-search table (`sections`) was
rebuilt with kdbrain paths at 04:30 on 11 Sep; the meaning-vector half (`embeddings` plus
`embed_meta`) still carried 4,849 rows on the old `.claude` paths, so hybrid search was running on
word search alone.

**Measured before choosing how (read-only):** 5,080 sections, 0 old paths; 4,849 vectors, ALL old
paths; 4,671 of them with text matching a current section; 396 sections with no vector. One embed
call on this laptop: about 0.5 s warm. Chose the existing, tested command
(`python tools/brain_retrieval_hybrid.py build`) over new reuse code; the index was backed up first
(scratchpad, 34 MB; the index file is gitignored).

**Done 19:49 to 20:53:** `{'sections': 5148, 'embedded': 5148, 'skipped': 0}`. Verified: 5,148
sections and 5,148 vectors, 0 old paths in either, and all 5,148 vectors match their word-search row
by rowid AND text. Hybrid fusion keys on (path, name, snippet), never rowid, so the benchmark's own
word-table rebuild cannot misalign it.

**The benchmark, re-run 20:54** (`tools/bench_retrieval_r1.py`, writes `_ops/RETRIEVAL_BENCHMARK.md`):

| | 4 and 9 Sep | 11 Sep |
|---|---|---|
| TF-IDF | 12/20 | 10/20 |
| FTS5 | 14/20 | 13/20 |
| Hybrid | 15/20 | 13/20 |

**Why it fell, traced question by question:** 16 of 20 unchanged in every lane. "Ruling 37" lost in
all three lanes and "cold outreach" in TF-IDF only: lanes the rebuild never touched. The one hybrid
loss ("What is the DCEO Brain") is a near miss: its file ranks 3rd in meaning search, 9th in word
search, and falls just outside the fused top 5. "Who is Adeola?" missed on 9 Sep too; its top 5 are
all sections of the Majorca trip file (one file can fill the list).

**Two benchmark defects found (not fixed, a separate job, his call):**
1. **A stale target:** `project_kd_robot_three_nodes_2026-08-29.md` no longer contains "ruling 37"
   (the text moved to `memory/INDEX_PAST_2026-09-02_TO_09-03.md` when memory was compacted).
   `check_targets()` only checks the file EXISTS, not that it still holds the answer.
2. **The benchmark pollutes its own corpus:** `_ops/RETRIEVAL_BENCHMARK.md` (and
   `_ops/PROGRESS_BOARD.html`) are indexed and contain every question verbatim; for the ruling 37
   question the benchmark's own report ranks 3rd.
Fix, when ruled: exclude the report from the index, and make `check_targets()` verify a key phrase
in each target. Care needed so a target change can never become moving the goalposts.

**Side effect, fixed the same evening:** the rebuild held the index's `-journal` open; that file was
tracked, and it hung the 20:00 sync ([[reference-sync-hang-2026-08-29]], incident 5).
