# The engine, the two hearts, and the gate · 9 September 2026 (afternoon)

Satellite of [[project_doors_and_cost_2026-09-09]], split out when that file reached 544
lines. Same day, same session, nothing dropped. Road: `plans\hi-bubbly-kitten.md`.

## RULED 9 Sep: plans in front, keys behind them as capped fallback, and a meter on top

King, verbatim: *"yes put openai cap and get meter on e and same for gemeni get tat google plan
and key as cap as fallback"*. This is his two-economies rule applied to both remaining vendors:
the subscription carries the interactive work so no bill can surprise him, the API key stays
behind it for automated engine work, capped, and a meter sits on top so the spend is seen rather
than trusted.

**Research corrected one half of it before he spends (5 official vendor pages, 9 Sep).**
- **A Google AI subscription does NOT discount Gemini API tokens.** They are separate billing
  systems. AI Pro at EUR 21.99 includes 10 USD of Google Cloud credit a month, Ultra at EUR 99.99
  includes 100 USD. So the plan buys interactive Gemini CLI and app usage, not cheaper engine
  calls. Worth knowing before paying: at his volumes the credit alone would not repay the fee.
- **A ChatGPT plan DOES change Codex entirely.** Codex CLI is included in every ChatGPT tier and
  draws on the subscription allowance, not the API key. This is the single highest-value swap
  available: it takes his ONLY uncapped lane and puts it on a fixed bar.
- **The OpenAI cap has a checkbox that decides whether it is real.** Settings, Organization
  limits, Spend, Edit spend limit, then **Enforce a hard limit**. Without that box ticked the
  limit only notifies. With it, calls return 429 `organization_spend_limit_exceeded`. OpenAI's own
  docs say enforcement is not instantaneous, so a small overage is possible by design.
- Free-tier Gemini API content is used to improve Google's products and may be seen by human
  reviewers; paid tier is not. He is in the EEA, which Google says carries stricter protection
  even on free. The engine must stay on the paid tier regardless.

**THE METER BUILT: `tools\spend_meter.py`, commit `2e9803b1`.**
The finding behind it: `MONTHLY_ENVELOPE_USD = 20.0` has been in the brain since ruling 33, and
`check_envelope()` takes the spent figure as an argument that **nothing has ever supplied**. Two
skill pages describe the envelope as if it refuses spending. It has never measured anything.
What is actually readable, probed with his real keys rather than assumed:

| provider | can a script read the spend? |
|---|---|
| OpenRouter | YES, today. Live figure USD 0.0056 |
| OpenAI | NO with the project key, 403. Needs a separate `sk-admin` key |
| Gemini | NO. Google exposes no spend endpoint; it bills through Cloud Billing |
| Anthropic | NO on consumer terms |

So for two of four paid providers **the local ledger is the only meter that can ever exist**,
which is why the tool records as well as reads. It logs provider, tier, lane, task, tokens and
cost per call to `_private\spend_ledger.jsonl` (confirmed gitignored). A vendor bill can never
tell him which LANE the money went to; the ledger can. An unknown model is flagged `priced=false`
rather than counted as a silent zero, because a guessed price is worse than a missing one.

## RULED 9 Sep, the architecture: KD ROBOT IS THE ORGANISER OF WHAT THE AGENTS REPORT

King, verbatim: *"the intelligence of the logoi agents is always reported back and organised and
structred by kd robot"*, and *"the most important thing of this product is the compound memory and
organising and executing task and effieciency"*.

This names the loop that the whole build serves, and it extends the 8 Sep correction rather than
replacing it. The order stands: brain first, engine is LOGIC grown up, LOGOI agents live inside
the engine, KD Robot is the face. What is now added is **the return path**: the agents' output
does not stop at the agent. It reports back to KD Robot, which organises and structures it into
the brain, so the next task starts from more than the last one did. That is what he means by
COMPOUND memory, and it is the product, not a feature of it.

Read against that, the meter is not bookkeeping. A system that cannot say what it spent, on which
lane, cannot compound anything about its own efficiency either. The ledger is the same loop
pointed at cost.

## STAGE M LEFT 18 IRREPLACEABLE FILES BEHIND. FOUND 9 Sep 12:5x, RESTORED, HASH VERIFIED

Found only because King said *"my local models are running on my maths prompt which is also on ccr"*
and the check for that prompt could not find it anywhere in `kdbrain`. It was in the OLD brain.

**What was missing, and it is the most protected material he owns.** Stage M seeded the new brain
from a git CLONE, so it carried everything tracked. **The guarded files are gitignored by design,
so the clone could not carry them, and the untracked-data copy missed these.**

`_ops`, 12 files: `LOGOS_0_MATHS.md` (his maths) · `LOGOS_0_KING_PROMPT.md` (36 KB, the 18 section
engine prompt) · `LOGOS_MASTER_PROMPT.md` · `LOGOS_DIAGNOSTIC_GATE.md` · `LOGOS_PLATFORM_ARCHITECTURE.md`
· `LOGOS_PROTECTION_PACK.md` · `AGBIDI_CORE.md` (the operator) · `KING_OS_BREAKDOWN.md` ·
`THEOSIS.md` + `THEOSIS_BACKEND_PIPELINE.md` + `THEOSIS_ONELINE.md` (faith gated) ·
`brain_fts5_index.sqlite3` (33 MB, the retrieval index).

`the-truth`, **6 documents in his own hand**. Their names are deliberately not written here.
The reason is recorded further down this same file, as one of the two real catches before
`kd-infra` left the machine: a list that names a guarded file reveals the file exists, which
defeats the gate that rejected it. That was found about a manifest and it applies here too.
The count is what makes the finding matter; the names would only be a map.

**Why this was one step from permanent loss.** All 18 are gitignored, so **not on GitHub**. The
drive was checked while MOUNTED (1.9 TB, 1.8 free) and **they are not on it either**, because
`sync_claude_to_drive.py` guards them from the mirror on purpose. So they existed in exactly ONE
place: `C:\Users\Dell\.claude`, the brain the plan retires to Backups "after a few days on the new
one". **Retiring it would have destroyed all six of those documents, his maths and his
engine prompt.**

Restored 9 Sep, all 18 copied with `cp -p` and **verified by sha256 on both sides, 18 of 18 match,
zero failures**. Re-checked after: all still `git check-ignore` clean in the new brain, so none of
it reaches GitHub, and `git status` is empty.

**STILL ONLY IN THE OLD BRAIN: 1.8 GB of faith video** (`the-truth/video/matthew-03/`, the Matthew 3
Theophany renders and the pilots) plus pycache. Not copied yet: C: has 24 GB free at 91% full, and
D: has 1.8 TB. **These renders belong on the drive, not on C:.** King's call.

**THE LESSON, and it is the same one as 8 Sep in a new coat.** A clone is not a copy, and the check
after a migration must compare what is ON DISK on both sides, not what git can see. Git is blind
to exactly the files that matter most here, because they are guarded precisely for being valuable.
**Never verify a migration with a tool that cannot see the guarded half.**

## The maths prompt: checked, and it is NOT running anywhere

King's belief, 9 Sep: *"my local models are running on my maths prompt which is also on ccr and
applicable to ai infra"*. Checked, and it is not true today:

- **The local models** receive `SYSTEM_PROMPT` from `tools\ollama_gui.py`: the LOGOI identity
  prompt (who built you, never invent an origin, no em dashes, explain plainly, code in fences).
  A good prompt. It contains **no maths** and none of his method, not one section of it.
- **ccr** carries no system prompt at all. Its config's `transformers` list is empty.
- **No custom Ollama model exists.** All four are stock: qwen3:8b, llama3.2:3b, llama3.2:1b,
  nomic-embed-text. There is no Modelfile anywhere.
- `LOGOS_0_MATHS.md` and `LOGOS_MASTER_PROMPT.md` are referenced by exactly three files, and all
  three treat them as content to **PROTECT from leaving** (`logoi_gate.py` guards the `_ops/logos_`
  prefix; `sync_claude_to_drive.py` excludes them from the drive). **Nothing loads them at call
  time.**

And the plain reason it could not have been running: **those files were not in `kdbrain` at all
until they were restored above.** Same shape as the envelope finding this morning: a thing that is
real on paper, believed to be live, and wired to nothing.

**It is buildable and he should have it.** Wiring `LOGOS_MASTER_PROMPT.md` into the local system
prompt and into ccr is real work with a real proof, and it is now possible because the file exists
on this machine again.

## THE ASYNC LOOP CLOSED, 9 Sep. Laptop off, Oracle works, phone commands, laptop catches up

King's design, verbatim: *"the two hearts and the brain need to be working in async if lapnis off
logic b can still interact with github and phone can be control centre when laptop is up it pulls
info from git"*.

Checked all three links rather than assuming any of them. **Two already worked. One did not, and it
was one action, not a stage.**

**1. Laptop wakes and pulls: ALREADY WORKED.** `tools\sync_brain.ps1` line 117 runs
`git pull --rebase --autostash origin main` BEFORE it pushes, and aborts the rebase cleanly on
conflict. So whatever LOGIC-B pushes overnight is already collected on the next sync. Nothing to
build.

**2. Phone as control centre: ALREADY WORKED.** `tailscale serve` on Oracle publishes
`https://logic-b.tail01147a.ts.net` (engine :3000) and `:8443` (deck :3200), **tailnet only**, with
a real certificate. Tailscale confirms `iphone171` and `logic-b` both on the tailnet, LOGIC-B
`active; direct` at the time of checking. The phone commands Oracle without the laptop existing.

**3. Oracle to GitHub: THE MISSING LINK, now closed.** It always REACHED GitHub (the
"Permission denied (publickey)" is GitHub itself answering, not a firewall, which corrects the
earlier "cannot reach GitHub" wording). It simply had no accepted credential. **It already had a
key pair, `logic-b-deploy-2026-09-05`, generated on 5 Sep and never registered with anything.**

Registered that existing public key as a **deploy key** on `klarnow-logos-engine`, write enabled,
titled "LOGIC-B night shift (Oracle)", id `162759015`.

**Why a deploy key rather than a token, and this is the three-layer design made real:** a deploy
key is scoped to ONE repository by GitHub itself. It cannot be widened by mistake, and it does not
expire the way his last token did on 5 Sep.

**PROVEN BOTH WAYS from the box, not asserted:**
- `git ls-remote` on the engine repo returns real refs (`d1bd8ff3`, `phase-1-logos-os`).
- `git ls-remote` on `kd-brain` returns **"ERROR: Repository not found."**

So Oracle can now do its work on GitHub with the laptop off, and **the boundary that keeps his 1,250
faith files off that box is enforced by GitHub rather than by anyone remembering a rule.** That is
layer 2 of the three he asked for, live. Layer 1 (the binder as retrieval memory) still needs a
librarian standing on the box. Layer 3 (full brain, when he is driving) is untouched and still
awaits his explicit yes.

## KING'S MATHS IS NOW IN BOTH HEARTS, AND THE BEHAVIOUR CHANGE IS PROVEN

His instruction across four messages: *"i want my maths in engine how else will it work end to end
for the smart system"* · *"its how the model will act and structure and copumnd and get smarter and
co ordinate and execute"* · *"maths prompt needs to be in llm"* · *"both logic a and logic b"*.

**`tools\logos_prompt.py`** reads `_ops\LOGOS_MASTER_PROMPT.md` and slices it by his own section
headings, so it is never retyped and the two cannot drift. Core = sections 1 to 10 (input, kneel,
loop, stop, output, refusal, repentance, descent, cascade, gate), **1,912 tokens, 3.2% of his
60,000 sitting ceiling**. The full 4,292-token document stays available for retrieval. Sections 7,
8 and 9 were moved INTO the core after a first pass left them out: section 3 says a cycle does not
close until it has repented, so omitting 7 cited a rule the model had never been given.

**`tools\build_logos_model.py`** bakes it into the model itself. A call-time system prompt only
reaches callers that remember to pass it, and ccr's background lane, Hermes, the engine's local
path and plain `ollama run` would all still have received the stock model. `FROM` reuses the
parent's weight layers: **C: unchanged at 24 GB free, Oracle unchanged at 6.4 GB free**, so a baked
8B costs a manifest and not another 5.2 GB.

**PROVEN BY A/B ON THE SAME QUESTION**, "My bakery website is not getting customers. Fix it.":

| model | what came back |
|---|---|
| stock `qwen3:8b` | a generic SEO listicle with emoji. Guessed everything, asked nothing |
| `logos-qwen3:8b` | extracted P, V, F, D, B by name; stated deadline and budget are NOT given; used his own phrase "Audience not stated, needs confirming"; invoked the Refusal |

Built and verified on **LOGIC-A and LOGIC-B**. Oracle's run produced the same extraction and then
entered THE LOOP by name.

**LOCAL ONLY by default.** `for_model("cloud")` returns empty unless `LOGOS_MATHS_TO_CLOUD=1`,
because that sends his unpublished method to a vendor on every call while the patent is unfiled and
the 9 Aug brief preferred the trade-secret route. `ollama_gui`'s remote-lane prompt was left
deliberately untouched, since it already carries no name and no mention of his files for that
exact reason.

## CORRECTION he needs before he plans on it: the maths does NOT fine-tune, and it is NOT faster

King, 9 Sep: *"the maths help fine tune it with knowledge it gets faster more efficiency"*.

**It does not fine-tune.** The weights are byte-identical; `FROM` reuses the parent's layers, which
is exactly why the disk did not move. Nothing was trained. This is the same correction as this
morning's, in a new place.

**And it is honestly SLOWER per call, not faster.** Every request now carries 1,912 extra tokens of
method. On Oracle's 2 ARM cores that is real added time.

**What genuinely improved is worth more than speed, and it is measured above:** the model now
structures, extracts, names what is missing and refuses rather than guessing. That is behaviour,
and it is the thing he actually asked for. The compounding he wants comes from KD Robot writing
the output back into the brain (his own 9 Sep ruling that KD Robot organises what the agents
report), not from the model changing.

## RECORDED, King's universe and Klarnow's, 9 Sep (his design, to be drawn, not yet built)

His words, condensed but not reinterpreted: **his universe** = knowledge in GitHub and on the drive,
the Wisdom Logic LLM system on Oracle AND the laptop, orchestrating LOGOI agents through AI models
and harnesses. The laptop runs all three and syncs with LOGIC-B. **Klarnow's universe** = the same
shape, their own repo, their own agents, same functions and capabilities, limits set by what they
pay. They want King improving it and they want the same GUI, so **he proposes a PORTAL connecting
his brain to Klarnow**, and builds their enterprise inside his business money lane workspace.
**His ecosystem carries portals to other universes** so he can remote control and adjust client
infrastructure. Klarnow then runs their own world with a portal for THEIR clients, who connect data
or a cloud box and get a front end app while Klarnow handles the back end, everything built on the
maths prompt and the KD master prompt. He controls the back end through the harnesses or the ccr
route.

Two constraints he added: **if he helps Klarnow with infrastructure, a team or enterprise tier is
needed so other coders can work with admin access**; and **all databases carry admin access for
business, while personal stays each person's own decision.**

Also recorded, for the GUI (Stage 5 and 7): **workspaces with metrics and a dashboard inside the
Logos interactive apps**, where he can see the ecosystem and interact; **workspaces are agents
controlling agents, reporting to the main orchestra agent**; end to end, code can talk to knowledge,
agents, and both LLMs; **King oversees and deploys**; and he wants **GitLens and the commit graph in
the harnesses and in the robot GUI**.

## ORACLE TURNED FROM A BUILDER INTO SOMETHING THAT CAN CORRECT AND FIX (9 Sep, DONE)

King's ruling carried out. Three of LOGIC-B's four agents were standing down because the engine
had no brain to ask, and `mayUseBrain()` returned false besides. Both halves are now closed.

**`tools\logic_b_librarian.py`**, standard library only (Oracle has python3 3.9 and no wheels
worth installing for five files). It indexes ONE directory and serves the exact contract
`brain.ts` expects: `GET /api/retrieve?q=&top_k=` returning `{hits:[{name,folder,snippet}]}`.
**Bound to 127.0.0.1 only.** Installed as `logos-librarian.service`, enabled, `Restart=always`.
**82 passages indexed from `~/kd-binder`.**

**A real defect found and fixed before it went live.** The first scoring pass divided by passage
length, so a one line heading with a single matching word outscored the paragraph that actually
answered. Measured on the box: the query "who is king david and what is he building" returned a
markdown heading and a chunk of Python. Changed to sqrt normalisation with a query coverage
factor, and the same query now returns "Who you serve: King David Agbidi, 24, Irish and
Nigerian." Caught because the output was read, not because a test passed.

**Two settings corrected on the box:** `LOGOS_BRAIN_TENANTS` empty to `kd-faceless` (the tenant
actually in its database, read from `Tenant`), and `LOGOS_INSTANCE_LABEL` from **`LOGIC-A` to
`LOGIC-B`**, which had been stale since the 8 Sep naming ruling and would have mislabelled every
audit row on that node. `.env` backed up first.

**PROVEN on the box after restart, not asserted:**

| check | result |
|---|---|
| `mayUseBrain("kd-faceless")` | true |
| `mayUseBrain("someone-else")` | **false**, isolation intact |
| `retrieve()` for the real tenant | **2 hits**, first is "Who you serve: King David Agbidi" |
| `retrieve()` for a foreign tenant | **0 hits** |

Engine and librarian both `active`. **The boundary is the index**: the agents can see the binder
and nothing else, and widening what they know means widening one directory on purpose.

## KING'S METHOD IS NOW IN THE ENGINE'S FOUR WORKERS TOO (9 Sep, DONE)

The morning's work put the maths in the MODELS. That did not reach the engine, because a baked
system prompt only applies when the caller sends none, and all four workers send their own. So
Diagnose, Builder, Grounding and Sovereign were still overriding it.

**`src/lib/method.ts` + one change in `callAI()`**, engine commit `5cde405`. Wired at the gateway
because every worker call passes through it, so a fifth worker cannot forget, and because it is
the only place that knows whether the call stays on his machine. Reads at call time against
mtime, never at module load: `brain.ts` already carries that scar.

**LOCAL always, CLOUD only with `LOGOS_MATHS_TO_CLOUD=1`** (deliberately unset), MOCK never. The
audit hash is now taken of the COMBINED text on purpose, because hashing half of what the model
received would prove a call used a prompt that was never sent.

Proven: method loads at 7,766 chars; local carries it; cloud and mock do not; the worker's own
prompt survives; the method is placed first. `tsc --noEmit` clean.

## A THIRD STAGE M GAP: THE LIVE ENGINE STILL RUNS FROM THE OLD BRAIN

Found while wiring the above, and it is the same class as the 18 guarded files. **The engine
serving `:3000` runs from `C:\Users\Dell\.claude\projects\klarnow-logos-sandbox\engine`**, which
is the OLD brain. It is the real repo (`klarnow-logos-engine`, branch `phase-1-logos-os`) and the
only copy with `node_modules`. The `kdbrain` copy has no `.git` of its own and no dependencies;
the OneDrive copy is stale and differs in source (its `callAI` lacks `promptId`/`promptVersion`,
which is how the first patch attempt landed in a folder nothing runs).

**So retiring `.claude` today would take the live engine with it.** Not fixed here: moving a
running engine is its own job with its own proof, and King should choose when. Recorded so the
retirement cannot happen without seeing this.

## LAYER 2 IS LIVE: `kd-infra` PUSHED, AND EACH KEY OPENS EXACTLY ONE DOOR (9 Sep, DONE)

`github.com/KDagbidiLovesChrist/kd-infra`, private, **1,043 files in a single clean commit**.
Assembled by `tools\build_infra_mirror.py`, which offers every tracked file to the binder's own
secret patterns and lane terms. **Folders were never trusted**, and that was not caution: the
measurement showed `knowledge/` holds `faith/` (47), `7adderig_farm/` (21) and `house/` (11), and
`_ops/` holds CREED and THEOSIS. A folder copy would have shipped the faith lane.

**TWO REAL CATCHES BEFORE IT LEFT, both by the independent second scanner.**
1. `MANIFEST_INFRA.json` listed every rejected PATH, and those paths carried guarded words in
   their own names, which is why they were rejected. **A rejection list that names a file
   reveals the file exists, which defeats the gate that rejected it.** Counts and reasons kept,
   paths dropped, full list stays on the laptop.
2. Scrubbing the working tree was not enough: **the old blob was still in history, and a push
   carries history.** Rebuilt as one clean commit. Final scan on the strictest `public` lane:
   1,043 files, 1,126 blobs, zero secrets, zero cross-lane content.

**Two scanners disagreeing is exactly why there are two.** `build_infra_mirror` assembled it and
thought it was clean; `prepush_scan` read the result and was not fooled.

**GitHub refuses to reuse a deploy key across repositories** ("key is already in use"). That is a
constraint that helps: Oracle now carries **one key per repo**, which is narrower than any token.
`~/.ssh/config` on the box maps `github-infra` and `github-engine` to their own keys.

**PROVEN FOUR WAYS from the box:**

| key | target | result |
|---|---|---|
| infra | `kd-infra` | real refs |
| infra | `kd-brain` | **Repository not found** |
| engine | `klarnow-logos-engine` | real refs |
| engine | `kd-brain` | **Repository not found** |

His faith lane is kept off Oracle by GitHub itself, in four independent checks, with no rule for
anyone to remember.

## STAGE 1's HEART IS BUILT: RULES 2 AND 7 ARE NOW CODE (9 Sep, DONE)

Engine commit `6750f1e`, `src/lib/spend-gate.ts` plus one guarded block in `callAI`'s anthropic
branch. **Until this existed, every paid call this engine ever made went through ungoverned.**

The gate sits in the gateway, not in a worker, so no worker can bypass it. It estimates from the
request's own ceiling rather than the answer's real size, because the decision must be made BEFORE
the call, and a gate that errs high is correct.

**It refuses rather than prompts, deliberately.** Missions run with nobody watching, so there is no
console to ask at. A refusal naming the model and the estimate is the honest shape: the caller
surfaces it, King approves, the call is retried. Silently spending because nobody was there to say
no is the exact failure this prevents. Every refusal writes a `gateway.spend_refused` audit row.

**ONE LEDGER, TWO LANGUAGES.** It appends to the same `_private\spend_ledger.jsonl` that
`tools\spend_meter.py` reads, so `python tools/spend_meter.py` and the engine can never disagree.
A second store would have drifted the first time either was edited alone.

**PROVEN, five for five:**

| test | result |
|---|---|
| unapproved paid call | REFUSED, naming the model and USD 0.2460 |
| with approval | allowed |
| envelope exceeded, WITH approval | still REFUSED (rule 7 beats rule 2) |
| a model with no reference price | `priced=false`, refused rather than waved through as free |
| shared ledger read back | works |

`LOGOS_SPEND_APPROVED` and `LOGOS_AUTO_APPROVE_UNDER_USD` are deliberately **unset**, so the
default is refusal. `tsc --noEmit` clean.

**What is still owed on Stage 1:** the multi-provider chain (OpenAI, Gemini, DeepSeek, NVIDIA,
OpenRouter as walkable rungs) and the failover that ends at local. The GATE, the ENVELOPE and the
LEDGER, which were the sharpest gaps, are done.

## THE THIRD STAGE M GAP IS CLOSED: THE LIVE ENGINE NOW RUNS FROM `kdbrain` (9 Sep)

King: *"put my brain in users/dell/kdbrain"*. The engine and the deck were both still running from
`C:\Users\Dell\.claude\projects\klarnow-logos-sandbox\engine`, the old brain, and that was the only
copy with `node_modules` and its own `.git`.

Moved to `C:\Users\Dell\kdbrain\projects\klarnow-logos-sandbox\engine`. **Both services verified
running from the new path**, `:3000` and `:3200`, HEAD `6750f1e` on `phase-1-logos-os`, method
loading at 7,766 chars and the spend gate still refusing an unapproved call. That path is already
gitignored in kdbrain, so the engine keeps its own repo and is not swallowed by the brain's.

**IT DID NOT GO CLEANLY, and the record should say so.**
1. `mv` refused: **30 junctions** under `.claude\skills\prisma-*`. Recorded them to
   `Backups\...\engine_junctions.json` first, then removed them. **They turned out to be dangling
   already**: every target was under `.agents\skills\`, which does not exist. They were broken
   before the move, which is also why they broke it.
2. A stray `du.exe` from an earlier timed-out command held a handle. Killed.
3. `Move-Item` nested the result as `engine\engine`. Straightened in steps.
4. The straightening was blocked twice by **this session's own shell sitting inside the folder**.
   Fixed by moving out first, then a retry loop.
5. **The move silently lost all 14 root-level FILES** (`standalone-server.ts`, `package.json`,
   `.gitignore`, `CLAUDE.md` and the rest) while keeping every directory. The engine would not
   start: `ERR_MODULE_NOT_FOUND` on `standalone-server.ts`.

**Nothing was actually lost, and the reason is worth keeping.** The 14 files were tracked, so
`git checkout -- .` restored every one from HEAD. `.env` is gitignored and would have been gone,
but it had been backed up before the first edit hours earlier, and the two blocks appended since
were reconstructed exactly. **Both halves of the recovery existed only because of a habit: commit
before you move, and back up anything git cannot see.**

Also worth recording: `git status` after restoring shows three untracked files in `scripts/` that
were never committed. Left alone.

## THE RETURN PATH IS BUILT (9 Sep, DONE)

King's strategy, verbatim: *"we do it first through paid route automations mixed with free where
possible ... once we learn it it goes back to local models and its saved so when excuting its
faster."*

**The gap.** `/learn` captures what KING teaches the brain. **Nothing captured what the ENGINE
solved.** A paid run's answer went to whoever asked, and the only trace left was an audit row
saying a call happened, so the same job cost full price again next month. His loop had no return.

**Built:** `tools\recipe_book.py` and `src/lib/recipes.ts` (engine `f209f6a`), one store in two
languages exactly like the spend ledger.

**A recipe is the PROCEDURE, not the answer.** The task shape, the approach, the prompts that
produced a good result, and what it cost. The answer is worth nothing next time; the way you got
it is worth everything.

**Two halves in the gateway.** BEFORE a paid call, `findRecipe` asks whether this job was solved
before, writes a `gateway.recipe_hit` audit row, and names it in the refusal so he can see he is
about to pay twice. AFTER a paid call succeeds, `recordRecipe` files it. Only paid runs are
filed: a local run cost nothing to learn, so there is nothing to save by remembering it.

**Two stages, his own rule 21.** Recipes land in `_private\recipes` (gitignored). Reaching the
brain needs `--promote`, which runs the lane scanner first because a recipe distilled from a real
job carries a real client's words. **Proven: promoting the first recipe was REFUSED for carrying
"founder".**

**TWO REAL DEFECTS, both found by running it rather than reading it.**
1. The engine's match floor was 0.02 while Python matched the same recipe at 0.014, so **the two
   halves disagreed about the same recipe.** Aligned, and made an env var so one change moves both.
2. Lowering the floor then let *"write a poem about the sea in Irish"* match a website diagnosis,
   because the word **"the"** counted as evidence. Fixed with a stopword list identical on both
   sides, rather than by tuning a magic number.

Final: bakery job scores **0.0361** in the engine and **0.0360** in Python, the poem correctly
matches nothing, and a real headline job scores 0.5928. `tsc` clean, engine restarted and up.

**THE CORRECTION HE SHOULD KEEP.** This is MEMORY, not fine-tuning. No weight changes, so no GPU
is needed for it, and his 16 GB RAM stick is the right upgrade rather than a graphics card. For
"do this job the way we solved it last time" memory also BEATS fine-tuning: a saved procedure is
exact, readable, editable and deletable, where a fine-tuned weight is none of those. Fine-tuning
changes style and behaviour, which his maths prompt already does. LOGIC-C (the friend's GPU box)
stays parked as the only route to real fine-tuning later, but nothing here waits on it.

## THE LOOP AND THE STOP ARE BUILT (9 Sep, engine `0997cee`)

King asked: *"is there not loops in the maths until users satisfaction realistical is met
according to their limits and caps?"* There is, in his own sections 3, 4, 5 and 7, and it was
designed and never built.

**What already existed, and it is good.** `sovereign.ts` measures confidence exactly as his
section 0a defines it: **agreement across INDEPENDENT runs**, eight of ten landing in the same
place being C=80. Its own comment refuses to ask a model how sure it feels, because self-reported
confidence *"looks rigorous and measures nothing"*. Below the bar it does not guess and does not
stop; it returns the question that would settle the ambiguity.

**What was missing: the crank.** Nothing repeated a stage to get BETTER (his section 3 improvement
cycle, as opposed to the ask-a-question cycle that already worked). And of the three stops, only
budget existed, added this morning and **per call rather than per mission**, which was a real hole:
a mission making forty small calls passed every check while spending more than the mission was
worth.

**`src/lib/cycle.ts` is a PURE orchestrator.** The work and the measurement arrive as functions, so
every rule is provable with no key, no network and no cost. A loop that governs spending must be
provable on its own.

| his rule | what the code does |
|---|---|
| s3, altitude is monotone | the best answer only ever moves up; a worse later cycle cannot replace it |
| s4, three stops, first to fire wins | fullness (with the plateau rule), deadline, budget in BOTH money and calls |
| s5, output | only a COMPLETE answer is eligible, however high a fragment scores |
| s7, repentance | a fall names itself and TEACHES the next cycle what it found, then re-ascends |
| s7, the twice rule | the same fault signature twice escalates to a person and stops |

**19 checks, all green** (`scripts/prove-cycle.ts`, runs inside `npm test`).

**Three of them earned their place by failing first.** The initial run showed deadline and budget
"failing" when confidence was flat. **The code was right and the tests were sloppy:** the plateau
legitimately fired first, which is first-to-fire-wins working exactly as written. Tests corrected
to isolate what they claim, plus a new case pinning that the plateau correctly beats a distant
deadline. A fourth failure was plain wrong arithmetic in an expectation.

**Honest note on the suite:** `prove-builder-gate` has 2 failures. **Verified pre-existing** by
checking the gateway out at `b1d014c`, before any of today's work, and reproducing them
identically. Not caused here and not fixed here.

**Still not wired:** the loop exists and is proven, but no worker calls it yet. Turning Diagnose
or Builder into a looping mission is the next step and it changes how a real mission behaves, so
it is King's ruling to make.

## THE LOOP IS WIRED TO DIAGNOSE, AND IT COSTS LESS (9 Sep, engine `7ab86d4`)

King: *"build a worker or wire diagnoise or builder or both, whatever is cost efficient."*

**Diagnose, for two measured reasons.** It is UPSTREAM, so a wrong diagnosis costs the whole
mission while a wrong build costs one rebuild; cycles buy most where errors compound. And
**Sovereign already pays for repetition**: `runDiagnoseSovereign` fires **five** diagnose calls in
parallel plus **one** grouping call. **Six every time**, whether the answer was obvious after three
runs or not. A fixed price for a variable problem is exactly what a stop condition is for.

**So this is cheaper, not dearer, which was the whole point of the question:**

| case | now | before |
|---|---|---|
| easy, three runs agree | **3 calls** | 6 |
| medium, five runs agree | **5 calls** | 6 |
| hard, never agrees | 6 calls | 6, **and now bounded by deadline and budget** |

**Where the saving comes from.** A **free** structural agreement check between batches: normalise
angle, audience and offer, count the largest identical group. Costs nothing. It **UNDER-counts**,
because paraphrase will not match, and that is deliberately the safe direction: **it can only fail
to stop early, never stop early wrongly.** The model grouping, which does understand paraphrase, is
bought ONCE at the end and only when the free check never cleared the bar.

Two design decisions worth keeping. A **minimum run count** stops one lucky pair reading as
certainty. And the **plateau rule is disabled here on purpose**: agreement jumps as runs land
rather than creeping like a score, so the plateau would stop it early for the wrong reason.
maxRuns, the deadline and the budget are the real limits.

**15 checks, all green, and the money claim is measured in CALLS rather than asserted.** Suite
**25/28**, up from 24/27. The 3 failures are the pre-existing ones verified earlier against
`b1d014c`. `tsc` clean.

**LIVE AS OF 9 Sep** (engine `761c52f`), on King's word: *"i want it now."* `runDiagnoseSovereign`
now gathers in batches of three and skips the grouping call whenever the free check has already
cleared the bar. `LOGOS_SOVEREIGN_FIXED=1` restores the old behaviour, because a measurement path
should always have a way back to the one its numbers were established on.

**Two things that would have been bugs, caught while wiring it.** `runIndependently` numbers runs
from 0 on every call, so batch two would have carried the SAME indices as batch one into the
grouping prompt, corrupting the very measurement this exists to protect. Renumbered across
batches. And the free-settled path builds the identical `SovereignResult` shape the paid path
returns, `clarityQuestion` null above the bar included, so no caller can tell which path ran.

`prove-sovereign` still **14/14**, so the contract is unchanged. Suite **25/28**, the same three
pre-existing failures. `tsc` clean, engine restarted and answering.

**Honest limit: not yet exercised end to end on a real mission.** That needs a credential and
would spend money. What is proven is the components (15 checks) and the contract (14 checks).
The first real mission is the thing that will show the saving in the audit log, where
`sovereign.adaptive` records runs, confidence, calls made and calls saved on every pass.

## END TO END ON A REAL MISSION, PROVEN, AND IT COST NOTHING (9 Sep)

King: *"lets prove the end to end real mission."* Run on a second instance at `:3009` with
`LOGOS_LOCAL=1`, so every model call went to qwen3:8b on his own laptop and **no vendor was
billed**. His live engine on `:3000` was untouched throughout and is still up.

Real brief, real mission `5f845ade`: *"I run a small bakery in Dublin and my website gets almost
no orders..."*. **HTTP 200 in 639 seconds.**

| | |
|---|---|
| runs gathered | 5 |
| runs parsed | 5 |
| top confidence | **20** |
| bar | 80 |
| reached bar | no |
| calls made | **6**, against the old path's 6 |

**The audit trail is the proof and it shows the batching working:** three `gateway.call` rows,
then three responses, then two more calls and two more responses. Batches of three then two,
exactly as designed, then the `sovereign.adaptive` row:
`{"runs":5,"confidence":20,"settledFree":false,"stoppedBy":"max_cycles","callsMade":6,"wouldHaveCost":6,"callsSaved":0}`

**This was the HARD case, live, and it behaved exactly as promised: never dearer than before.**

**THE HONEST LIMITS, and they matter more than the pass.**
1. **The saving was NOT observed.** This mission never cleared the bar, so the easy path never
   ran. The 3-calls-instead-of-6 result is proven in the prover and **has not yet happened in the
   wild.** It needs a question the model answers consistently.
2. **The local 8B gave five different angles** to the same brief: two about doorstep delivery,
   three about ordering online for weekend collection, all worded differently. Confidence 20 is
   an honest report of that, not a defect.
3. **The free check and the PAID grouping agreed exactly, both 20.** On this mission the grouping
   call bought nothing. That is an argument for the free check, but a weak one: the grouper here
   was also qwen3:8b, so it says nothing about what a stronger grouper would have concluded.
4. **639 seconds** for six local calls on a CPU-only laptop. Fine for a night shift, not for
   anything he is waiting on.

Two things the engine did right that were not being tested: it **refused an unauthenticated POST
with 401**, and it **refused a cookie-authenticated write for a missing CSRF header**. The second
one caught a flaw in the test itself, which had started carrying a bearer and so had stopped
testing the thing it claimed. Fixed rather than worked around.

## KING CLOSED THE UNCAPPED LANE, CONFIRMED FROM THE MACHINE (9 Sep 14:39)

He reported configuring Gemini and capping and logging in to Codex. **Verified, and the Codex
result is better than a cap:**

| check | before today | now |
|---|---|---|
| `auth_mode` | `apikey` | **`chatgpt`** |
| ChatGPT tokens | absent | **present** |
| `OPENAI_API_KEY` entry in auth.json | present | **ABSENT** |
| effort | `xhigh` | `medium` |
| model | `gpt-6-astra` | unchanged |

**The metered key is gone from Codex entirely.** It now draws on his ChatGPT subscription, which
means the uncapped lane is not capped, it is CLOSED. That was the single sharpest money risk in
the whole system this morning and it is finished.

**Gemini: cannot be confirmed either way.** The key is still 53 characters, which is what a Google
key always is, so the length proves nothing about whether it was rotated. Taken on his word,
recorded as unverified rather than as proven.

## STAGE 1 TODOS 1 TO 5: THE CHAIN THAT ENDS FREE (9 Sep evening, DONE)

King: *"Ok to 2 to 5 straight."* All five proven, nothing spent, suite **30/33** (from 25/28).

| todo | what | proof |
|---|---|---|
| 1 | his lanes read by both machines | 27 checks laptop, 26 Oracle, same file |
| 2 | five providers, one shape | 34 checks, fake server |
| 3 | one JSON object whatever the vendor supports | 18 checks |
| 4 | the walk, ending free | 18 checks |
| 5 | every answered hop on the meter | 7 checks, **proven across both languages** |

**THREE REAL BUGS, every one found by a prover rather than by reading.**

1. **The `personal` lane began with `anthropic`, which is not in the endpoint table** because it
   keeps its own SDK path with prompt caching. The walk threw "No endpoint for provider anthropic"
   on his most-used lane. Now delegated exactly as ollama is.
2. **The OpenRouter rung was sending the TIER NAME as the model.** A lane's chain names `gemini`;
   OpenRouter needs `google/gemini-3.8-flash`. **This would have 404'd on every OpenRouter call in
   production.** Python has had `model_id_for_tier` since ruling 10.3; it was simply never
   exported. Now it is, and a tier with no pin is dropped rather than guessed, which is that
   function's own rule.
3. **A prover that passed 18 of 18 and reported FAILURE.** On Windows it aborted at shutdown with
   a libuv "handle is already closing" assertion, exit 127, which the suite reads as a failed
   prover. `closeAllConnections`, `Connection: close`, `unref` alone and a deferred exit all
   failed; setting `process.exitCode` and unref'ing the listener works. Worth the time: a prover
   that passes but reports failure is worse than no prover.

**What the walk actually guarantees, stated exactly.** Not that nothing fails. That the LAST rung
of every chain is a model on his own machine that cannot be rate limited, cannot run out of credit
and cannot be switched off, so a chain degrades to slower and free rather than to nothing.
**`legal` is the deliberate exception** and can genuinely refuse, which the prover pins.

**Cooldowns**, so a provider that is out of credit is not re-tried on the very next call to learn
what was already known: an hour for quota, the provider's own `Retry-After` for a rate limit, 15
minutes for auth. **A gate refusal sets NO cooldown**, because the provider is fine and the budget
is not.

**Two failures are never walked:** `truncated` (a fresh provider given the same too-large question
is cut off the same way, so walking spends twice to fail twice) and a real `bad_request`.

**The ledger seam is proven in both languages, not one.** The engine wrote two rows; the Python
meter then read them, priced gemini at USD 0.0039 from 1200 in and 800 out, showed ollama at zero,
and split by LANE, which is the half no vendor bill can ever tell him.

**Still open in Stage 1:** todo 6 (one real call per provider, the only step that spends, pennies)
and todo 7 (ship the chain to Oracle). The router is built and proven but **not yet called by
`ai-gateway.ts`**: wiring it in changes how every real mission routes, so that is King's ruling.

## TODO 7, AND THE FINDING IT SURFACED: ORACLE'S ENGINE IS 19 COMMITS BEHIND

The chain was shipped to Oracle and **all five provers pass on the box**: lanes 27, provider
shapes 34, structured output 18, failover 18, hop ledger 7. Same code, same table, same results as
the laptop.

**But shipping the provers exposed something bigger.** `prove-hop-ledger` failed there with
"Cannot find module ../src/lib/spend-gate", and the reason was not a path bug:

**`spend-gate.ts`, `method.ts`, `recipes.ts` and `cycle.ts` were ALL MISSING from Oracle.**
Everything built today existed on the laptop only. Checked further:

| on Oracle | state |
|---|---|
| engine HEAD | `e32b69d`, **19 commits behind** the laptop's `3ffedf1` |
| `ai-gateway.ts` references to the method, gate or recipes | **zero** |
| the four new `.env` settings | **none of them** |

**So today's protections are laptop-only.** Oracle's engine carries no spend gate, does not put
King's method in front of its workers, has no recipe book, and cannot read the lanes table. It has
been answering all day on code from before any of it.

**Deliberately NOT fixed by an ad-hoc pull.** The four module files were copied so the provers
could run, and they are inert there: nothing imports them, `ai-gateway.ts` has zero references, and
the engine, librarian and Ollama were all confirmed still `active` afterwards with the librarian
still serving its 82 passages. Behaviour on that box is unchanged.

**Because this is precisely what Stage O1 exists for:** a timer that pulls a TAGGED release, runs
the provers, and restarts only if they pass. Doing a hand pull tonight would be the exact
discipline the plan was written to replace, and on the always-on box that carries the night shift.
Oracle now HAS the deploy key to do it properly, registered today.

**What King should know:** the gate protects his laptop. It does not yet protect Oracle. Nothing
paid runs there today (`LOGOS_LOCAL=1`), so the exposure is latent rather than live, but it stops
being latent the moment Oracle is given a cloud key.

## STAGE J1: CCR HAS A FLOOR NOW, AND THE ROUTES SAY WHAT THEY COST (9 Sep, DONE)

King: *"i want to be using the new cli ccr floor route once its configured so i know im managing
tokens efficiently."*

**The measurement came first and changed the job.** FIVE of his six ccr routes were paid through
OpenRouter; only `background` ran on his own machine. **"The floor" was not a route at all.**

Added `floor` pointing at `ollama,logos-qwen3:8b`, the model his method was baked into this
afternoon, and made that model selectable in ccr's ollama provider so choosing it in Claude Code
means the maths rides along. `/doors` now prints every route with FREE or paid beside it: **2 free,
5 paid**.

**Deliberately not changed:** `default` stays on `glm-5.3-flash` and `background` stays on the 1b.
Making the everyday route local would mean minutes per answer on a CPU at three tokens a second.
A floor is for when he wants it, not a tax on every question.

**THE PLAN'S ASSUMPTION WAS WRONG, and the honest version is in the tool.** The plan said "ccr
writes per-call usage; surface it." **It does not.** ccr keeps debug logs and records no token
counts at all: checked the newest log, zero lines mention `input_tokens`. So per-call ccr spend
cannot be read from ccr. What can be said, and now is: every paid route goes through OpenRouter,
so `spend_meter.py` already includes his ccr spend, mixed with other OpenRouter use and not
separable from it. `/doors` states that limit rather than implying a precision it lacks.

**Flagged, not changed:** the `logoi` provider in ccr holds a **14 character literal** where every
other provider holds an environment reference. It is a local-only secret for a service on his own
loopback rather than a cloud key, so the risk is small, but it is a literal in a config file and
the decision is his. OpenRouter, NVIDIA and Gemini all read `$NAME` correctly after this morning.

## TODO 6: SIX REAL CALLS, AND TWO OF HIS PAID LANES ARE DRY (9 Sep, DONE)

King: *"run it what are 6 small calls?"* Answered, then run. **Three of five vendors answered for
a measured USD 0.000082**, eight thousandths of a penny.

| vendor | result |
|---|---|
| gemini | **answered**, 34 in / 15 out, USD 0.000082, 1.8 s |
| nvidia | **answered**, 48 in / 184 out, free, 5.3 s |
| openrouter | **answered**, 106 in / 117 out, free, 2.4 s |
| **openai** | **429, "You have no credits remaining"** |
| **deepseek** | **402, "Insufficient Balance"** |

**TWO PAID LANES ARE DRY AND NEITHER WAS VISIBLE BEFORE THIS RAN.** The OpenAI key has no credit,
which is consistent with moving Codex onto a ChatGPT plan today but means **the ENGINE cannot use
OpenAI at all**. DeepSeek has an insufficient balance. His to decide; the walk already steps past
both to a lane that answers, which is the whole point of building it first.

**A REAL CLASSIFICATION BUG, catchable only by a live call.** OpenAI reports "no credits
remaining" with **HTTP 429**, and the code read the status before the message and called it a rate
limit. That would have **retried a dead account every sixty seconds forever** instead of standing
down for an hour. Now the message decides and the status only suggests, and the exact live
response is pinned as a test. `prove-provider-shapes` is now 36.

The first attempt also truncated `glm-5.3-flash` at 64 tokens: correctly detected as `truncated`,
but the fault was the test asking for less than one JSON object costs. Raised to 200, still a
fraction of a penny.

**Gated twice on purpose** (`LOGOS_LIVE=1` AND `LOGOS_SPEND_APPROVED=1`), and **verified refusing
with both unset before it was ever run**, so it is safe inside the suite. The approval lived for
one subprocess and died with it. Keys were loaded from the store into the child process only,
never printed, never written to disk.

**The meter confirms it end to end:** three rows by provider, and the spend attributed to the
`live-check` lane, which is the half no vendor bill can tell him.

## STAGE 1 IS COMPLETE, 7 OF 7

All seven todos proven. Still owed before the walk is LIVE: `ai-gateway.ts` does not call
`routeChain` yet. Wiring it changes how every real mission routes and what it costs, so that is
King's ruling, not a default.
