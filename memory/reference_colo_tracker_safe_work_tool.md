---
name: reference-colo-tracker-safe-work-tool
description: "The colo capacity tracker (DCEO/L4) + the SAFE work-tool pattern: build a generic empty tool on personal, plug real data only at work via a local paste."
metadata: 
  node_type: memory
  type: reference
  originSessionId: c640a8a3-eeb5-4501-9af2-beb0d7a1ab8d
---

# Colo Capacity Tracker + the safe work-tool pattern

**What:** a web-dashboard **colo capacity tracker** for King's DCEO work (the tool his chief asked for; doubles as **L4 / full-Operator** evidence). Built 2026-07-01.
- **File:** `colo-tracker\colo_dashboard_v1.html` (self-contained, no deps, no fetch).
- **Live (unlisted, fake data):** **https://colo-deploy.vercel.app**
- **Spec came from a 7-agent DCIM research workflow.** Expert-grade content: measure against **usable/DE-RATED** capacity (NEC 80% rule), not nameplate; **A/B failover math** (a rack that exceeds 100% on one-feed-loss isn't truly redundant); **committed vs allocated vs actual** (where stranded/reclaimable capacity hides); **runway-to-full** forecast; the **capacity triangle** (power/space/cooling, a rack is full when it exhausts ANY axis); data-accuracy governance (freshness/source/ghost-asset detection); tiered Warning/Critical alerts.
- **Dashboard has:** 6 chief KPIs, an overall-power gauge, per-room utilization bars, an "Actions Required Today" punch-list, a sortable/filterable rack table (power% bars, redundancy chips, status chips), and a "🧠 thinking behind it" panel (chief 5-sec read + pitfalls + L4-evidence notes).

## 🔐 THE SAFE WORK-TOOL PATTERN (reuse for ANY work-adjacent build)
> **Build the empty machine on the personal side; the real fuel only ever goes in at work.**
- 🟢 **Safe here:** the generic tool/layout/formulas/method + **fake sample data** + the "how to use it at work" guide + the L4 write-up (generic terms).
- 🔴 **Work-laptop only:** real values (rack IDs, power/capacity, tenants, sites, locations), security/access details, internal docs/tickets/customer data, wiring to any real Amazon system.
- 🟡 **Check first:** confirm the **AUP / manager / approved-AI setup** before treating it as sanctioned or connecting to work systems.
- **Mechanism:** the tool ships with a **local "paste CSV" loader**, at work King pastes real data, it renders **in-browser only, never uploaded, never saved to disk**. So the tool lives in the (private) repo with only fake data; real data never touches the personal machine or `kd-brain`.
- **The golden rule:** if a stranger read it and learned something *real* about Amazon's data centres, it doesn't belong here.

## Why it matters to King (both, together)
Daily: fewer manual spreadsheets, catches maxed breakers / broken redundancy **before** they trip. Career: the tool + the "how I run operations" narrative **is** his L4 evidence (documenting how ops work = the promotion case). → L4 = higher grade = more income, God's way. Venue: the **Robbie Tighe** meeting ([[project-robbie-tighe-l4-meeting]]). See also [[project-dceo-work-ai]] · [[project-dceo-brain-vision]].
