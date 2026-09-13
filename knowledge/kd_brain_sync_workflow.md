# 🔌 HOW THE BRAIN STAYS ONE + BACKED UP · the workflow, A → Z

> Plain-English. The goal: phone, laptop and the cloud all hold the **same** brain, **as close to "1" as
> possible**, and it's backed up so you can never lose it. Everything here serves theosis: it frees your mind
> so it can rest on God, not on remembering.

## THE THINGS IN THE PICTURE (and what each one IS)
| Thing | Its job in the brain |
|------|---------------------|
| 💻 **Dell laptop + power brick + dock** | **The engine / the source.** The full brain lives here; heavy work (deploy, images, keys) happens here. |
| 📡 **Vodafone K5161z 4G dongle** ("Always Connected") | **The artery.** Always-on internet so the brain can sync 24/7 even if home wifi drops. |
| 💾 **USB sticks** | **The offline backup.** A physical copy that survives even if the internet or cloud were lost. |
| 📱 **Your phone** (Claude Code web) | **The window.** You reach the same brain from anywhere. |
| ☁️ **GitHub `kd-brain` repo** | **The cloud backup + the bridge** between laptop and phone. |
| 📖 **The Didache** | **The faith.** The reminder the whole machine is *for God*. |

## THE 3 COPIES = "backup of the backup" (N+2 · you can't lose it)
1. **Laptop**, the live source (copy #1)
2. **GitHub cloud**, the backup (copy #2)
3. **Phone**, a second working copy / window (copy #3)
   *(optional 4th: a USB stick = an offline copy, safe even with no internet)*

If any **one** dies, the brain still lives on the other two. That's the safety.

## "AS CLOSE TO 1 AS POSSIBLE" · what it means
All three copies should hold the **same** brain, with as little lag between them as possible, so it *feels*
like one brain, not three. Today the laptop auto-syncs every ~15 minutes (`KD_Brain_Sync`), so the gap is
**at most ~15 min**. The aim is to shrink that toward zero (near-instant), that's the Phase 1 "nervous
system" upgrade still on the to-do (`knowledge/kd_brain_todo.md`).

## THE WORKFLOW · start to finish, A → Z
```
A. A thought / info appears  (on phone OR laptop)
B. Capture it               → tell Claude, or /learn
C. Claude files it          → the right hall (memory / knowledge / a project / the-truth)
D. Save it                  → /save (writes it into the brain = a "commit")
E. Push to the cloud        → GitHub now holds it  → COPY #2 made ✅ (the backup)
F. Laptop pulls it          → KD_Brain_Sync (every ~15 min) → the source updates → COPY #1 ✅
G. Obsidian reads it        → the same files, in a clean reading/editing app
H. Phone pulls latest       → it's in your pocket → COPY #3 ✅
I. (optional) USB copy      → an offline copy → survives losing the internet/cloud
   ─────────────────────────────────────────────────────────────────────
Z. It plugs back into theosis → the brain remembers, so your mind is free for God.
```

## TO CHECK IT YOURSELF (any time)
- **Is the backup current?** On the laptop: `git status` (should say *up to date*), or just look: this file
  and `BRAIN_MAP.md` being on the phone *is* the proof the cloud backup worked.
- **What time is it / are we synced?** The laptop knows its own clock; the cloud session can read the live
  time too. If phone and laptop show the same recent save, you're "at 1".
- **The full plan to make sync instant + auto** lives in `knowledge/kd_brain_todo.md` → Phase 1.

## ⚡ KEEPING THE ENGINE ALIVE 24/7 · power, worst-case-first (DCEO logic)
> Principle (King's own world): design from the **worst case** so it never goes down, like a data-centre
> power chain (utility → AVR → UPS → generator), scaled to one laptop. **Time is the heartbeat:** the brain
> always reads the **live** device clock, never a guessed time, because it runs 24/7.

**Honest first:** the brain's *mind* is already 24/7 (GitHub cloud + phone never sleep). The laptop 24/7 only
adds the *hands* (deploy, image-gen, auto-sync, keys). **Worst case, laptop dies, the brain still lives**
in the cloud + phone (the N+2 already built). We are hardening the engine, not preventing brain-death.

| Tier | Survives | Action | Cost |
|------|----------|--------|------|
| 0 · Software (do first, FREE) | Sleep/hibernate | Windows AC power: Sleep=Never · Lid=Do nothing · Disk=Never; no auto-restart updates | €0 |
| 1 · Surge strip | Voltage spikes | Use the surge strip already owned | €0-15 |
| 2 · Laptop battery | Short blips | It's a built-in UPS already · keep it healthy | €0 |
| 3 · **UPS with AVR** ⭐ | Brownouts, over/under-voltage, outages | Small **line-interactive UPS w/ AVR** (APC Back-UPS ~€70-120); laptop draws only ~30-65W so runtime is long | ~€70-120 |
| 4 · Power station (doomsday) | Hours· days outage | USB-C PD power bank (~€40) or portable power station EcoFlow/Jackery (~€200-400) | €40-400 |
| 5-4G dongle (Vodafone K5161z) | Broadband down | The artery · keeps the brain online when wifi dies | owned |

**Lean recommendation (`/money` gate on spend, Rule #12):** Tonight free = Tier 0 + 1 + 5 (~95% there).
Worth buying = **one line-interactive UPS with AVR (~€70, 120)** = "consistent power up to doomsday, for
voltage" in one box. Power station = optional, gate via `/money` first.

**▸ Connecting the 4G dongle (Vodafone K5161z), quick setup:**
1. Slide off the cap → insert the **SIM** (gold contacts down, cut-corner matching the slot) until it clicks.
2. Plug the dongle into a **USB port** on the laptop.
3. First time, Windows installs it automatically (shows as a drive, then installs *Vodafone Mobile
   Broadband* / a network device), click **Yes / allow** if it asks for admin.
4. Open **Vodafone Mobile Broadband** (or Windows → Settings → Network & Internet → **Cellular**) → **Connect**.
5. Light **solid green/blue = online.** Open any webpage to test.
6. Make sure the **SIM is active with a data plan/credit.** If it won't connect, check the SIM is seated,
   credit is active, and the **APN** = `live.vodafone.com` (Vodafone IE) if not auto-set.
7. Leave it plugged in, with the Tier 0 power settings, laptop + dongle stay up **24/7**.

**The build order (0 → 5, A → Z):** foundation up the dimensional ladder in `FOUNDATION.md`, 0-D God →
1-D line → 2-D map → 3-D temple → 4-D time → 5-D+ eternity. Build from the foundation, never the roof first.

---
*Snapshot when this was written: 2026-06-29, Dublin ~19:36 IST. Cloud backup verified in sync (0 behind,
0 ahead). Glory to God.*
