# 8 · WAT and the recipes · how work is done, and re-done free

**Part 7 said where you sit. This part says how work actually gets done from that seat, and why
the same job costs full price every time it comes back.**

```
W  Workflow   the steps, written down as a markdown SOP
A  Agent      the thing that reasons. Claude, or a local model.
T  Tool       the thing that executes. Python, an MCP server, an API.
L  Logic      the /command that runs the whole chain
```

**WAT is Nate Herk's framework**, taught in the AIS+ course, and it is his when you pitch it.
**"Logic" is your own naming** of the fourth layer, from the Logos. Say it that way in a client
room.

---

## 8.1 Why the four layers are four and not one

Each layer fails differently, which is the whole reason to separate them.

**A workflow with no tool** is a document. It describes work nobody does.

**A tool with no workflow** is a script whose reason has been lost. Six months later nobody knows
why it exists or what it was for, so nobody dares delete it, and it sits there.

**An agent with neither** is a chat. Good answers, no leverage, and you pay again tomorrow.

**All three with no Logic** is the common case and the expensive one: the pieces exist, and
running them takes you, by hand, remembering the order.

**The `/command` is the leverage.** It is the thing that turns "I know how to do that" into "that
is done".

---

## 8.2 What you actually have, counted tonight

| layer | count | where |
|---|---|---|
| **Logic** commands | **64** | `commands/*.md` |
| Tools, Python | **306** | `tools/*.py` |
| Tools, PowerShell | **22** | `tools/*.ps1` |
| Plugin skills | **57** | on the seat's vitals |
| MCP servers | **2** | n8n-mcp, playwright |
| Keys, for tools that need one | **49** | 16 providers |

That is a real estate of machinery. **The gap is not the doing. It is the re-doing.**

---

## 8.2b Research, which had no owner until now

*Added 12 September 2026. The original node map gave research its own region, "RESEARCH &
INTELLIGENCE, multi-source consensus before any answer", with Perplexity, Brave and an Obsidian
RAG tool as nodes. The fourteen parts mentioned it nowhere. It belongs here, in the T layer.*

**Rule 16 is why it matters:** research uses the ACTUAL tools, not just a web search, and finishes
on a multi-source consensus. That rule needs tools behind it or it is a wish.

| tool | what it is for | key present |
|---|---|---|
| **Perplexity** | deep web research with citations | yes |
| **Brave Search** | an independent index, so consensus is not one vendor twice | yes |
| **Tavily** | a second search lane | yes |
| **Firecrawl** | turns any page into clean text | yes |
| **Apify** | scrapes TikTok, Instagram, YouTube | yes, 4 credentials |
| **Playwright** | drives a real browser for what has no API | wired as an MCP server |

**Six research lanes, all with credentials in the store.** That is a genuinely strong bench, and
it is the reason a consensus can be independent rather than the same source read twice.

**The honest part.** Only Playwright is wired as an MCP server that a session reaches by itself.
The rest are keys waiting for a caller, the same shape as the recipe book below. Having the key
is not the same as having the habit.

---

## 8.3 The return path, which is the point of this part

Your own words, 9 September: *"we do it first through paid route ... once we learn it it goes back
to local models and its saved so when excuting its faster."*

That is the return path, and it is the difference between a tool estate and a compounding one.

**The gap it was built to close.** `/learn` captures what YOU teach the brain. Nothing captured
what the ENGINE solved. When a paid run succeeded, the answer went to whoever asked and the only
trace left was an audit row saying a call happened. **The expensive lesson evaporated, so the same
job cost full price again next month.**

**What a recipe is, and is not.** It is a PROCEDURE: the shape of the task, the approach that
worked, the prompts that produced it, and what it cost. It is not the answer. An answer is worth
nothing next time; the way you got it is worth everything.

**Two stages, which is your own QA gate.**

```
LEARNED   _private/recipes/     gitignored, never leaves the machine, written automatically
TRUSTED   knowledge/recipes/    in the brain, versioned, only by --promote
```

Promotion runs the lane scanner first, because a recipe is distilled from a real job and may carry
a client's words. **Nothing reaches the brain on its own say so.**

---

## 8.4 What the recipe book actually holds

**One recipe. Run zero times. Saved zero.**

```
id            ca0ab6d9e798
at            2026-09-09
task          diagnose why a small business website gets no customers
lane          business
approach      extract P V F D B from the founder sentence first, name what is
              missing rather than guessing, then rank fixes
learned_from  anthropic, claude-sonnet-4-5, est 0.246 USD, 2,000 in / 1,600 out
runs          0
saved_usd     0.0
```

**And the sharper fact underneath it.** `tools/recipe_book.py` is imported by **nothing**. The
only file in the repository that mentions it is itself. So:

- no engine run records a recipe automatically, whatever it cost;
- nothing looks a recipe up before paying for the same work again;
- `knowledge/recipes/` does not exist, because nothing has ever been promoted.

**The arithmetic that makes this matter.** That recipe cost 0.246 USD to learn. The mechanism was
built so the second run of that job costs nothing. It has been run zero times, so the saving so
far is 0.246 USD spent and 0.00 returned. **The return path has never once returned.**

That is not a broken module. Every function in it works. It is the same shape found three times
in one evening elsewhere in this estate: **a module that works perfectly and that no code path
reaches.** Your own engine comment names it: *a thing nothing calls is not built, it is drafted.*

---

## 8.5 What it would take

Two hooks, both small, and neither is a rewrite.

1. **Record on success.** When a paid run finishes clean, call `record()` with the task shape, the
   approach and the cost. The data it needs is already in the audit row.
2. **Look before paying.** Before a paid call, call `find()` on the task. A hit means the procedure
   is known and a local model can follow it.

**Until both exist, the recipe book cannot compound**, and the phrase "pay once, run free forever"
describes an intention rather than a mechanism.

---

## REAL TODAY

| | |
|---|---|
| **real** | 64 Logic commands, 306 Python tools, 22 PowerShell, 57 plugin skills, 2 MCP servers. The doing is genuinely built. |
| **half built** | the recipe book: every function works, its two stages are designed, and its gate is right |
| **zero** | the return path itself. 1 recipe, 0 runs, 0.00 USD saved, 0 files in `knowledge/recipes/`, and 0 callers anywhere in the repository. |

⚠️ **`recipe_book.py` is imported by nothing.** Until something records on success and looks
before paying, every solved job is solved again at full price.

**Proof:** counted on 12 September. `commands/*.md` 64, `tools/*.py` 306, `tools/*.ps1` 22. The
single recipe read directly from `_private/recipes/ca0ab6d9e798.json`, showing `runs: 0` and
`saved_usd: 0.0`. `knowledge/recipes/` does not exist. A repository search for `recipe_book`
returns one file, `tools/recipe_book.py` itself.

**Next:** [9 · The engine](09_the_engine.md)
