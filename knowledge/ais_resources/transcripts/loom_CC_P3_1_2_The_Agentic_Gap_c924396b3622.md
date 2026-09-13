# Loom Transcript · CC_P3_1.2_The_Agentic_Gap

**Source video ID:** c924396b36224ecd980f8e6920776c35
**Loom URL:** https://www.loom.com/share/c924396b36224ecd980f8e6920776c35
**Detected language:** en (probability 1.00)
**Duration:** 303.3s

---

[00:00] Okay, welcome to video two.
[00:02] Let's talk about the agentic gap and what am I even talking about?
[00:05] But what changes when Cloud Code isn't watching, all right?
[00:09] So the self-healing loop, right?
[00:12] Like I say here, in phase two, even phase one, it really did feel magical.
[00:17] It was like something broke.
[00:19] I have no idea how even got to this point.
[00:22] I wouldn't know how to fix it, but guess what?
[00:24] Cloud Code does and it goes and it fixes it.
[00:28] It tells us what it did, how to fix it, what went wrong, all of that.
[00:32] Very magical.
[00:34] It could read the errors, it would do the fixes, it would update, it would
[00:37] try again until you got it to a place where it was working, right?
[00:42] So now what happens when Cloud Code isn't watching, right?
[00:46] Remember, we're going to put these out in the cloud and they're going to run on
[00:50] their own when a schedule fires or webhook fires.
[00:54] So Cloud Code isn't there to troubleshoot for us like it was before.
[00:58] So we've got this gap, right?
[01:01] It runs, but it can't adapt.
[01:02] And if something happens, Cloud Code definitely doesn't know about it.
[01:06] And we might not know about it.
[01:08] So how do we close this gap, right?
[01:10] So with TriggerDev, it'll automatically retry.
[01:14] So when there's a task that fails, we can set the terms for its automatically
[01:20] try again.
[01:20] And like I said before, it's got this full trace logging.
[01:23] We can see exactly what happened at every single step.
[01:25] We'll dive into that.
[01:26] It's super cool.
[01:27] Failure alerts.
[01:28] We can have those we sent to email or Slack or somewhere, the moment something
[01:32] breaks or we're notified of it.
[01:34] And then there's no timeout.
[01:35] So the task will run as long as they need to.
[01:40] Let's look at another way to prompt as we kind of move into it.
[01:44] So there are some new requirements.
[01:48] And we've kind of been doing most of these anyway.
[01:51] But I just want to kind of call these out again.
[01:53] But we need to have fixed inputs, right?
[01:56] Cloud Code would ask us some clarifying questions about where things are coming.
[01:59] But now when we're prompting, we need to say,
[02:03] instead of, hey, help me research this topic, we need a build a task that runs
[02:07] unattended every morning in researches this topic, right?
[02:11] So that runs unattended.
[02:13] It's very important because Cloud's going to understand, oh, OK, you're not involved
[02:18] with this.
[02:19] It's going to be on a schedule because you said every morning, right?
[02:22] So those are the kind of the keywords to get it into the space.
[02:25] Structured outputs, we need to give it a predictable format for every run
[02:30] that we're expecting the results to be in.
[02:32] And then error handling baked in, right?
[02:35] We don't want to assume Cloud will know how do you want these errors to?
[02:38] So we need to do that from the beginning and then logging at every step.
[02:42] And we're going to dive into all these as we get into the builds.
[02:45] We're just kind of touching this at a high level right now.
[02:47] But those are four things to start thinking about to include as we start prompting.
[02:52] So again, very important, we've already talked about this, but it's a new language,
[02:57] but it's the very same vibe code approach that we've been doing so far.
[03:01] But TriggerDeb does use TypeScript, not Python.
[03:05] But still, we describe what we want to Cloud code and it will write it in TypeScript,
[03:09] because it knows.
[03:11] And like I said, the vibe code approach does not change.
[03:14] You talk to Cloud, it'll give you what we need.
[03:17] OK, so one other new concept since we're kind of working with the scheduling is the
[03:22] current schedule.
[03:23] What does this mean?
[03:24] But basically, it's at some point of say, hey, run at this specific time.
[03:28] It tells the system exactly when it runs something automatically, right?
[03:32] So it's just a schedule timer, time reoccurrence pattern.
[03:36] So an example would be 0, 7, and then 3 aster.
[03:39] And that basically means 7 a.m. every day.
[03:42] And then over here on the right side, I have that broken down kind of vertically.
[03:45] The first place here is 0 is the minute marker.
[03:49] The second one is the hour markers.
[03:51] So we have 0 minutes, 7 hours, which just means 7 hours.
[03:55] And then those next three places, the next one be every day of the month, every month,
[04:00] and every day of the week because we did the aster.
[04:02] So that is in five digits a way to say at 7 a.m. every day.
[04:10] So very high level quickly of what a current schedule is.
[04:13] And as we get in, you'll see it.
[04:14] It'll make more sense.
[04:16] All right, so the phase three stack, we've kind of already covered two tools, really.
[04:21] There's a form one.
[04:22] We'll introduce here in a little bit.
[04:23] But GitHub, I think we're all familiar with, it's going to store your code.
[04:27] TriggerDev will handle everything else.
[04:29] And then, of course, we're using Cloud Code to kind of set all this up.
[04:33] So again, this agentic gap, right?
[04:36] Cloud Code's not going to be there to self-heal and do this.
[04:39] We're going to have a TriggerDev help us keep an eye on
[04:42] what's going on.
[04:43] If there's any errors, that sort of thing.
[04:47] Build deployment from the first prop, right?
[04:49] Remember those four things we're going to add in.
[04:51] Be a little more descriptive in what we're asking, what the errors are going to be,
[04:55] and what the results are.
[04:57] And then we've got GitHub and a TriggerDev.
[04:59] So let's keep going.
