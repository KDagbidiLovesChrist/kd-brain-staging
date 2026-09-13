# Loom Transcript · CC_P3_1.8_Error_Handling

**Source video ID:** bd7a44286768421ea4f11b6a9721fb86
**Loom URL:** https://www.loom.com/share/bd7a44286768421ea4f11b6a9721fb86
**Detected language:** en (probability 1.00)
**Duration:** 348.2s

---

[00:00] Alright, let's take a look at some error handling so as we've gone through this there's been quite a few errors that have popped up here
[00:06] There and there's different ways that we can go through them like we have or to get club code to kind of help step in and take control since it's not
[00:16] Managing the errors like it did in phase one phase two so
[00:21] Trigger dev is
[00:23] Helping right gives us that visibility. It can retry the things automatically
[00:30] But it only can retry what it knows is a failure so
[00:35] If the errors are unclear it's really hard to try to figure out what is broken
[00:40] So we need to get into practice of doing some good logging so instead of just saying task failed
[00:46] It's fire crawl return to 429 on source three, right?
[00:51] So it gives us that context that then we can take to club code and kind of help us out with that
[00:55] So let's look at this in a couple layers of debugging and kind of this error troubleshooting
[00:59] So one of them is logging as you saw inside Trigger dev we have all of our traces and we can see
[01:05] Every meaningful step and this is what we've asked in our two examples, right review my task files and add a clear log at every meaningful step
[01:13] So I'm starting the research fire crawl return
[01:16] So it's letting us know exactly what's happening. So that is kind of a layer one step one
[01:22] layer two would be the error handling when they actually happen layer one gives us that visibility layer two is for the handling of that so
[01:33] The good thing about Trigger dev is that we'll retry right the whole the whole task
[01:38] it will log with the context and
[01:43] One of the good prompts used to be like hey try catch around every external API call
[01:48] Log the error with context continue where possible and then only throw for critical errors
[01:55] or failures so
[01:58] Again, this is something we've already kind of implanted in
[02:01] To our prompts of the things that we've built so alert to something that we haven't really touched on yet
[02:07] So I'm gonna show you that here in just a second, but it's good to be alerted before your client before you know
[02:13] Someone out in the field. It's using your form or whatnot. It is
[02:18] So we're gonna go into Trigger dev there's project settings
[02:20] There's actually an area called alerts and we're able to add an email a Slack or a webhook that will notify when alert happens
[02:28] So that we can keep an eye on it. We can choose the environments and the type of failures that sort of thing and
[02:35] Yeah, it's pretty easy to set up. So let's jump over real quick and take a look at alerts inside Trigger dev
[02:41] All right, so we're back in Trigger dev over here on the left. We're gonna scroll down
[02:45] You'll see underneath manage. There's alerts right here. You can get alerted when deployed run fail
[02:52] It currently supports sending Slack email and webhook so we can click new alerts here
[02:56] You can see the three options there if you've got slack you can connect can set up a webbook or just be email when it happens
[03:03] You just put in your email you can choose what you want to be alerted about the environments that it happens and you click save
[03:10] Boom, I mean, that was less than two minutes really so super fast
[03:14] Really great to have that visibility popping up as soon as something happens
[03:19] All right, so let's talk about configuring retries. So we're gonna let
[03:26] Trigger dev as it's been doing
[03:29] The retries we can configure in our task definition
[03:32] So a prompt we could use is like add a retry configuration to my task up to three retries with exponential back-off starting at 30 seconds
[03:41] So the retries will help with temporary API issues if it's a timing thing if it needs to wait a certain amount of time or update right trying again might
[03:53] Go through maybe the second time, but it doesn't fix a bug if there's an actual error
[03:57] So it's good to kind of know the difference there as you've seen from this
[04:01] We're gonna still use cloud to debug, but it's not doing it for us
[04:05] We still have to pass it over so with the traces and with cloud that will give us a fast diagnosis
[04:12] But we still have to be here. So when a run does fail as you've seen
[04:16] We've clicked on the trace that failed that went red in the dashboard. We copied the error
[04:23] And we pasted it into cloud and we said you know similar stuff
[04:26] Hey, here's the trace that failed. We pasted it. What's wrong? How do I fix it and for the most part clouds identified it
[04:33] It suggested a fix and then it would redeploy and then test it right away and we were good to go after that. So
[04:41] This is obviously very important. It's all about bridging that gap. You know since cloud's not
[04:46] self-healing at the whole time, but
[04:51] We want to make sure when we do
[04:53] Ask cloud to build for us to have it log everything meaningfully and
[04:58] Wrap the external calls with the APIs that can try in the catch
[05:02] So we can handle the failures at the right level when it does not to the API
[05:07] We want to set up those alerts and trigger devs so we can be notified before we walk away
[05:12] And then we want to set up make sure it's doing retries for those APIs to
[05:18] To find the logic errors that sort of thing and then we're gonna use cloud by pasting the trace errors if there's an error
[05:26] Into cloud it'll help us diagnose and fix it so
[05:33] Very important stuff, you know once all this is set up and you get used to prompting cloud in a way that covers all of these
[05:39] It's just gonna become natural and you know looking at the errors and watching the traces will just become easier and easier
