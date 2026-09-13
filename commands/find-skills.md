# /find-skills · Do Any Task the Best Way (Scout → Build the Master Prompt/Skill)

**Trigger:** `/find-skills <task>` OR "find the best way to do X", "what's the best prompt/skill/workflow for Y", "make our X skill better"
**Purpose:** For any task, hunt EVERY platform for the best existing prompt, skill, workflow, MCP or agent; rank by multi-source consensus; vet; present; then on King's yes BUILD it, a master prompt, a new `/skill`, or an upgrade to one we already have, so the task is done the best way AND that quality is banked as a reusable skill for next time.

> Not hooks/content, that's `/content-engine` + `tools\hook_harvest.py`. This is "how do I do *this task* better." It's also the scout/front-door `skill-forge` was always meant to have.

---

## WHY (the point)
Never do a task at "whatever I already know" level. Before building anything, go SEE what the best people and tools out there are actually doing, fold that best practice in, and save it as a skill. Every task done best, every time, and the brain compounds.

## MAXIMUM-DEPTH PRINCIPLE (the whole point), MANDATORY
King's standing rule, in his words: every skill should be "marked out to the depth... done to the maximum possible best ability. That should be the whole point." Whatever this skill finds or builds is taken to the MAXIMUM best ability for that task, never surface-level. Concretely:
- **Bake in the FULL proven best practice.** When the scout returns a winner, fold in EVERY recurring signature from the consensus (every move the best examples share), not a watered-down sketch of it. A skill built at "whatever I already know" level fails the whole point of find-skills.
- **Visual tasks hold to the DEEP STORYBOARD STANDARD.** Any master prompt / new skill / upgrade that produces video or visuals must hold the output to the MiniMax-depth deep-storyboard standard: a Comprehensive Design Sheet Brief, then a Character Model Sheet, then shot-by-shot stills with the per-scene fields (emotion first). See [[reference-deep-storyboard-standard]] + Rule #18 (visual storyboard).
- **Scale depth to stakes (Rule #17).** Max depth means thorough where it counts, not busywork on trivial steps. The principle: do not leave the task half-done or shallow when depth is what makes it win.

## REFERENCE-QA (the output must be MEASURED against the reference, not internally checked)
Anything this skill builds that is **modeled on a reference, competitor or data** (which, per Rule #16/#17, is almost always) must be verified with **REFERENCE-QA: a measured similarity check against the real reference numbers**, never internal checks alone ("does it run, no errors"). Pull the actual reference (download it, don't guess), measure both it and ours on the dimensions that matter (for short-form video: voice words-per-second + voiceover yes/no, cut length, caption style, visual format, energy, hook), score them side by side, and fix every miss until ours matches. Internal-only QA is the failure mode that let a slideshow-quality video ship when the reference was far tighter. Full standard + the free tools (yt-dlp, ffmpeg scene-detect, faster-whisper, frame reading): [[reference-reference-qa-standard]].

## TWO HALVES
1. **SCOUT**, search everywhere, run consensus, vet, present the best.
2. **BUILD**, on King's yes, turn the winner into a master prompt / new skill / upgrade. **Never auto-build or auto-install** (skill-forge guardrail + Rule #1).

## GOALS & THE LOOP (King's framing · important)
- **Many goals, ranked.** A task's point is never ONE thing. Name the MAIN goal + any secondary (e.g. main = brands/UGC paying King · secondary = own-brand followers + product sales). Pass them all: `--goal monetization,followers`. The same search and the ranking both aim at them, and every find is tagged with which goal(s) it serves (🎯). Goals: `monetization`/`money` · `followers` · `audience` · `traffic` · `engagement`.
- **It's a LOOP, not a one-shot.** Produce → measure the real result per platform per goal → find the better way → improve → repeat. **find-skills is the "find the better way" step inside that loop** (the produce + measure steps are the content engine + its analytics). The goal never "finishes", re-run as results come in; it can be scheduled on a recurring `/loop`. That's the never-ending improvement King means.

---

## STEP 0 · Discovery (don't guess)
Say back the task in one line + what KIND of help fits (prompt / skill / workflow / MCP / agent, default all) + the **GOAL(S)** it must serve and their order (main first). Goals = money/monetization · followers · audience · traffic · engagement; multiple is normal. Ask only if unclear.

## STEP 1 · Harvest EVERY platform (MANDATORY multi-source, Rule #16)
Run the scout tool AND the agent-side web sweep in parallel:

```
python tools\skill_finder.py "<task>" --goal monetization,followers   # aim every platform at the goal(s)
# zero-spend:    python tools\skill_finder.py "<task>" --goal money --free   (GitHub + n8n only)
# refine social: python tools\skill_finder.py "<task>" --social-query "best ai tool for <task>"
```
The tool covers the **programmatic sources**: GitHub repo search (free, uses the PAT) · n8n.io workflow templates (free) · TikTok/IG/YouTube/X/Facebook (Apify, reuses `hook_harvest.py`'s verified actors; a few cents/run, printed). It writes ranked JSON to the scratchpad `.tmp\` and prints a per-platform count so you SEE every platform fired.

In parallel, the **agent** covers the **registry / blog / forum / marketplace side** with **WebSearch + Firecrawl**. The tool prints the **curated registries** (highest-signal for skills/MCP, check these every time): **ClaudeSkills.info** (658+ incl. official Anthropic) · **Skills.sh** · **claudemarketplaces.com** · **smithery.ai** (MCP) · **anthropics/skills** · **ComposioHQ/awesome-claude-skills** · **rohitg00/awesome-claude-code-toolkit**. Plus: PromptHub / FlowGPT · `awesome-prompts` / `awesome-workflows` READMEs · Reddit r/ClaudeAI + r/PromptEngineering · Product Hunt.
- On a strong video lead (a TikTok/YT that clearly demos the tool), optionally run `/watch` on it (Gemini) to read the prompt/tool off-screen.

**Rule:** at least 2 independent platforms must return real data. If one is empty, SAY SO, never fake consensus (the `hook_harvest` lesson: wiring ≠ working).

## STEP 2 · Consensus + Vet (the Agent)
- **Dedup + consensus:** the same tool/prompt/workflow recurring **across platforms** = the strongest signal (a GitHub repo that's ALSO a viral video beats a lone repo). The tool flags obvious cross-platform links (`+CROSS:`); you confirm the real consensus.
- **Quality:** stars, recency (maintained beats abandoned), license, real engagement.
- **Have-it check:** cross-reference the 36 `/commands` + 8 plugin skills + `skill-forge\MANIFEST.md` → mark ✅ have / 🟡 overlap / 🆕 new / ⚠️ duplicate. Don't re-find what King already owns.
- **Cost-check (Rule #12):** free vs paid + the cheaper/free alternative.
- **Safety-flag (skill-forge guardrail):** 🔴 HOLD anything that touches memory, imposes its own methodology, runs auto-mode, or is unvetted code, flag it, don't action it.

## STEP 3 · Present (use the `/research` consensus style)
Top 3, 5 picks, strongest first, plain English. Each pick:
```
[name], [link]
  WHAT: one line   ·   TYPE: prompt/skill/workflow/mcp/agent
  WHY IT WON: which platforms agreed, stars/engagement, recency
  COST: free / paid (+ cheaper alt)   ·   SAFETY: ✅ clean / 🔴 hold (reason)
  HAVE-IT: 🆕 new / 🟡 overlaps /X / ⚠️ dup of /Y
  HOW IT'D PLUG IN: one line
```

## STEP 4 · King picks an outcome → BUILD it (never auto-build/install)
The findings now become the best way to do the task. Four routes:
- **(a) Master prompt** → synthesise the best-of-breed techniques into one strong, reusable prompt, via the **`/master_prompt`** skill. Save it where King can grab it (`knowledge\` or the project).
- **(b) New skill** → build a fresh `/command` that bakes in the best approach, via the **`write-a-skill`** skill → register through `skill-forge\workflow\skill_acquisition_sop.md` (catalogue → cost-check → conflict-flag → install → register in `CLAUDE.md` → test once → log a `skill-forge\sessions\` entry).
- **(c) Upgrade an existing skill** → fold the better technique into a `/command` King already has (e.g. sharpen `/website`, `/cv-tailor`). Show the before/after, get King's ok, edit the skill file, re-test. This is how OLD skills keep getting better.
- **(d) Install as-is** → if a found skill/MCP is already great, install it via the skill-forge SOP.

Then **test it once** (Rule #5) and, if it's a new/changed skill, it's now banked for every future task.

---

## EXAMPLE USES
- `/find-skills extract tables from a PDF` → finds `ispras/dedoc` + an MCP server + a Reddit prompt → build a `/pdf-tables` skill.
- `/find-skills write cold outreach that gets replies` → consensus across GitHub prompt repos + viral TikToks → synthesise a master cold-email prompt → upgrade `/cold-email`.
- `/find-skills make our /website skill better` → scout the best site-build prompts/workflows → fold into `commands\website.md`.

## WAT
**W** = this SOP (`commands\find-skills.md`). **A** = Claude scouts, runs consensus, vets, then synthesises + builds. **T** = `tools\skill_finder.py` (GitHub + n8n + Apify social) + WebSearch + Firecrawl + `/watch`; build reuses `/master_prompt` + `write-a-skill` + `skill-forge`. **S** = `/find-skills`.
