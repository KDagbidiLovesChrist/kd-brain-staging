---
name: project-ccr-wording-and-keepalive-2026-09-12
description: "R5.5 and R5.6 done just after midnight on 12 Sep: King chose B for the ccr door (keep the paid routes, correct the three places that called it free), and the LOGOI keepalive now stops only LOGOI instead of every python process on the laptop."
metadata: 
  node_type: memory
  type: project
  originSessionId: 2333f35b-611b-48ad-85ea-c72f5435ee93
  modified: 2026-09-11T23:11:37.082Z
---

# The ccr wording (R5.5) and the LOGOI keepalive (R5.6), 12 Sep 2026, just after midnight

## R5.5, the ccr door: King chose B

**The choice, with the measurement he was given:** ccr's routes are 5 paid (OpenRouter
`google/gemini-3.8-flash`) and 1 free (`background`, local `llama3.2:1b`). Measured cost: OpenRouter
reports **USD 0 this month and USD 0 in total**, and the ledger holds one OpenRouter call at about
one hundredth of a cent, so the paid door has cost nothing because it is barely used. The local
alternative writes at 10 to 30 tokens a second, too slow for everyday work. **He chose B: keep the
paid routes, correct the wording.** No behaviour changed.

**Corrected, three places that called door 1 free:**
- `commands/doors.md`, the ladder table row for `ccr code`.
- `tools/harness_status.py`, the door blurb, which contradicted its own route table ("1 free, 5
  paid") on the same screen.
- `tools/cockpit.py`, which listed ccr under "free lanes" AND named the wrong model
  (`logos-qwen3:8b`; the background route is `llama3.2:1b`).

Proven by running the tools: the door list now reads "5 of its 6 routes are PAID (OpenRouter), only
background is free on the laptop". No test pinned the old wording. Storyboard part 5.4 still records
the choice itself; the routes are unchanged.

## R5.6, the LOGOI keepalive: it would have killed every python program

**The fault, read from the live machine:** `tools/ollama_gui_keepalive.ps1` collected
`Get-Process -Name python`, EVERY python process, and called `Stop-Process -Id $p.ProcessId` on
each. Six were running that night: Mission Control, the voice aide, the progress board, VS Code's
helper, the floor watch, and LOGOI. **Only a typo saved them:** `Get-Process` objects carry `Id`,
not `ProcessId`, so the id was null and nothing was ever stopped. That is also why a second LOGOI
survived on 11 Sep, the symptom that first raised it. **Correcting the property alone would have
killed all six**, so the filter was the fix, not the property.

**Fixed:** `Get-LogoiProcs` matches the command line through `Win32_Process`
(`kdbrain\tools\ollama_gui.py`), never the image name. A healthy LOGOI still exits before any stop.

**Proof, test first (`tests/test_ollama_gui_keepalive.ps1`, which never stops a process):**
- **Red:** 3 checks failed against the old script.
- The first draft of the test failed on the new script's own header, which quotes the old line; the
  source checks now read CODE only, not comments. Honest note: the test was corrected, not the fix.
- **Red proven again after that correction:** the same hardened test, run against the OLD script
  copied out of git into a temp folder, failed 3 checks. The live script was never touched.
- **Green:** all checks pass, with the finder matching exactly one process (pid 7228, the one
  listening on 5056) and none of the other five.
- **Live:** running the real keepalive with LOGOI up killed nothing; all 6 python pids survived and
  the log says "Helper alive on 5056 ... leaving it".
