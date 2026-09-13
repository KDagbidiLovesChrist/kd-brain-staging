---
name: incident_ci_paged_king_2026-09-11
description: "Every GitHub CI run was paging King's phone with false 'a loop stalled' alerts: 230 of 231 in one 12-hour window, one burst per run, for probably 15 days. The one real alert was disguised by the same title. Fixed 11 Sep, proven by a run that sent nothing."
metadata: 
  node_type: memory
  type: project
  originSessionId: a04f54b1-fd2d-4691-9ba2-c14de9b5d663
  modified: 2026-09-11T04:34:42.004Z
---

# INCIDENT · CI was paging King's phone on every run

**Status: fixed and proven. Old runs, if re-run, will still page him.**

## The scale, measured from his own alert channel

ntfy keeps about twelve hours. On 11 Sep at 05:35 it held **232 messages. 231 were titled "KD
Robot: a loop stalled". 230 of those were false.** Every one came from a GitHub Actions run:

| CI run | ran (local time) | false burst |
|---|---|---|
| `ad65699c` | 21:00 to 21:04 | 21:01, 21:03 |
| `21e2b815` | 21:05 to 21:08 | 21:06, 21:07 |
| `4272576e` | 21:12 to 21:17 | 21:11 to 21:16 |
| `70a5835f` | 21:27 to 21:30 | 21:28, 21:29 |
| `2be2f877` | 21:45 to 21:48 | 21:46, 21:47 |
| `f89082d1` | 22:15 onward | 22:16 to 22:18 |
| `06d2f77c` | 22:30 to 22:34 | 22:31 to 22:33 |
| `446db4e6` | 22:36 to 22:38 | 22:36, 22:37 |
| `69adb10d` | 22:45 to 22:48 | 22:46, 22:47 |
| `91ddfaa3` | 04:44 to 04:46 | 04:45 |
| `f89082d1` re-run | ending 05:12 | 05:10, 05:11 |
| **`c2adca97`, the fix** | **05:27 to 05:30** | **none** |

**Eleven runs, eleven bursts, and the fixed run is the only one with none.** The runs before the
twelve-hour window, fifteen days of them while CI was red, almost certainly did the same; ntfy no
longer holds them.

**It was not the re-run.** King caught the 05:10 burst because he had just pressed Re-run, but
the 04:45 burst came from Claude's own push of the handoff an hour earlier, reported to him at the
time as "CI is green". Every run paged him.

## The worse part: the real alert was disguised

In those twelve hours the channel held exactly **two** real alerts: a job lead at 19:52, and at
**00:00 the supervisor's genuine kernel warning.** But `_alert()` sent every message under the
fixed title "KD Robot: a loop stalled", so **his one real alarm arrived looking identical to 230
false ones, under the wrong name.** The channel had stopped being able to tell him anything. That
is the failure mode this whole brain's alerting exists to prevent.

## Why a GitHub server could reach his phone

`test_main_runs_clean` called the real supervisor with every default, including a real ntfy push.
The topic is a constant in `tools/push_kd.py` and ntfy.sh is on the public internet. On a runner
there are no heartbeats and no brain, so every loop reads stalled; the throttle file is fresh and
empty, so nothing is suppressed; five matrix jobs run at once, so each alert arrives several times.

## What was fixed, 11 Sep

| fix | proof |
|---|---|
| `push_kd.push()` refuses on any CI server | **the next CI run, `c2adca97`, sent zero alerts**, read back from his ntfy channel |
| it still sends from King's own machine | tested, because a guard that silenced him at home would be worse than none |
| `test_main_runs_clean` no longer runs the real supervisor | no real push, task kill or stall-log write, on CI or at home |
| **the kernel alarm now says "the laptop needs a reboot"** | tested: it can no longer be mistaken for a loop stall |
| `tests/unit/test_push_kd_never_from_ci.py` | proven red: without the guard, a GitHub push reached the phone |

## What cannot be fixed

**Re-running an OLD run replays the OLD code**, which has none of these fixes. Pressing Re-run on
anything before `c2adca97` will page him again, and would look like the fix failing when it has
not.

## A standing risk, his call

**The alert topic is hardcoded**, so it lives in every past commit: anyone who can see the repo can
read his alerts or send him false ones. `kd-brain` is private, which contains it. Moving the topic
into the environment stops future exposure; only a new topic, with the phone resubscribed, retires
the old one. Not urgent while the repo stays private.

## The lesson

A test with real side effects is not a test, it is a scheduled action with no owner. And an alert
channel is only as good as its worst sender: **230 false alarms did not just annoy him, they hid
the one that mattered.** Anything that can page King must be impossible to reach from a machine
that is not his, and every alert must say what broke.

Related: [[incident_ccr_leak_2026-08-26]]
