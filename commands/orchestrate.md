# /orchestrate · Head Chef SOP

**Trigger:** Any task that needs more than one agent, or when King David describes a goal
without naming a specific skill. The orchestrator reads, decides, dispatches, merges.
**Environment:** Shared. All agents in the same local ecosystem.

---

## Step 1 · Read the Shared Environment
Before anything else, confirm context:
- Read `C:\Users\Dell\.claude\commands\subagent_registry.md`, available agents
- Read `C:\Users\Dell\.claude\commands\master_prompt.md`, who King David is + current priorities
- Check `C:\Users\Dell\.claude\memory\project_upcoming_tasks.md`, what's most urgent

---

## Step 2 · Parse the Task
Break the goal into components:
1. What is the END OUTPUT? (leads CSV / deployed website / proposal PDF / Skool post)
2. What DATA or RESEARCH is needed first?
3. What TOOLS are required? (check subagent_registry.md)
4. Can any steps run IN PARALLEL? (if yes, fire them simultaneously)
5. What's the HANDOFF order? (which agent feeds the next)

---

## Step 3 · Dispatch Agents

Narrate before firing so King David can see the kitchen work:
```
Dispatching [N]-agent team for: [task description]
→ Agent 1: [Scraper], pulling [data] from [source]
→ Agent 2: [Writer], standing by to format output
[firing now, running in parallel where possible]
```

Fire agents using the Agent tool. Each agent:
- Operates within the shared environment (reads same files)
- Returns standard handoff format: Agent / Task / Output / Status / Next
- Passes result directly to orchestrator (not to each other)

---

## Step 4 · Merge + Format Output

Collect all handoffs. Combine into one clean result.
Apply WOW standard: if it doesn't impress, restructure before delivering.

Output format:
```
ORCHESTRATOR RESULT, [Task]
─────────────────────────────────
[Agent 1]: [summary of what it returned]
[Agent 2]: [summary]

FINAL OUTPUT:
[the actual deliverable, leads list / copy / site URL / etc.]

NEXT STEP: [what King David should do or what fires next]
```

---

## Step 5 · Write to Memory
After every completed task:
- Memory Agent writes a summary to Obsidian vault (port 27124)
- Any new pattern or client info → `knowledge\patterns.md` or `knowledge\clients.md`
- Run `/save` if session is ending

---

## Four Metrics Check (before marking done)
- Less time: did agents run faster than manual? ✓/✗
- More money: is this output billable or income-generating? ✓/✗
- Better quality: is this better than a single-agent output? ✓/✗
- WOW factor: would someone cold say "wow, okay"? ✓/✗

If any metric fails → revise before delivering.
