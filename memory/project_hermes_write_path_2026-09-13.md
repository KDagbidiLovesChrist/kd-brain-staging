---
name: hermes-write-path
description: "Hermes can now propose real brain updates for King approval, Stage 3 done 13 Sep"
metadata:
  type: project
---

Stage 3 of the supervised Hermes write path is done, 13 September 2026. King ruled 11 Sep that
Hermes may update the brain but it must be supervised. Two designs failed real testing first: a
Linux file-permission wall on Oracle (opc has passwordless sudo, no permission there is a real
wall) and GitHub branch protection on a personal repo (blocks the merge button, not a raw push,
proven live; the setting that would block a raw push needs an organization, refused on a
personal account). The design that held: the only credential able to write to the real, private
kd-brain has always lived on King's own laptop, never touched or extended. Hermes writes only to
a small public staging repo (kd-brain-staging), already pruned of anything guarded and scanned
clean. tools/hermes_promote.py, running on the laptop, pulls staging, re-scans every proposal a
second time, and writes nothing to the real brain until King runs --approve himself.
