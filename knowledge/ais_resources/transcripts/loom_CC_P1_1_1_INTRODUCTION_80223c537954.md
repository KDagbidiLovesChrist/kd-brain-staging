# Loom Transcript · CC_P1_1.1_INTRODUCTION

**Source video ID:** 80223c5379544a57b0021f5aa064916b
**Loom URL:** https://www.loom.com/share/80223c5379544a57b0021f5aa064916b
**Detected language:** en (probability 1.00)
**Duration:** 245.8s

---

[00:05] Hey, ready, welcome to the vibe coding challenge.
[00:07] This is the very, very beginning of this challenge.
[00:11] Super fun module one.
[00:12] We're going to cover the foundation and the setup.
[00:14] What is vibe coding?
[00:15] Why is it important?
[00:17] Some best practices.
[00:18] Take a look at kind of what we can expect
[00:20] throughout this challenge.
[00:21] I hope you're pumped.
[00:21] I hope you're super excited.
[00:23] Let's dive right in.
[00:24] So the first thing I want to talk about
[00:25] is what is vibe coding, right?
[00:28] And the best way to explain this is
[00:29] if you're just having a conversation, right?
[00:31] You talk to the AI just like we're talking right now.
[00:34] And the AI will build what you've asked it to
[00:37] using that plain language.
[00:39] And then say you want to change something.
[00:41] Will you have more of that just basic conversation?
[00:44] And it updates it that way.
[00:46] So you're just kind of vibing.
[00:47] You're going with the flow.
[00:48] You're like, you know what, it'd be really cool
[00:49] if I had an automation that did this.
[00:51] And then, you know what, let's change that.
[00:53] You're just kind of relaxing and going with it.
[00:55] You're not worrying about the complex things.
[00:58] And this is important because speed, right?
[01:01] Being able to communicate what you want
[01:03] just using words easily.
[01:05] And the AI is doing all the heavy lifting.
[01:08] Less technical overhead.
[01:10] I am not a coder.
[01:11] That is not my background.
[01:12] So having AI be able to do that.
[01:14] And I just explain what I want
[01:17] and what I think the outcome should be is amazing.
[01:20] I can focus on solving the problems I need to.
[01:24] And the AI is doing all the nodes.
[01:25] And what should it be?
[01:27] Why is this not working, right?
[01:28] Like that is not where our wheelhouse needs to be.
[01:32] That is what AI is really, really great for.
[01:35] So let's talk about what we're going to be building
[01:37] in this overview.
[01:40] We're going to break it down into three modules.
[01:42] You're here, module one, which we're covering
[01:44] the foundation and the setup module two.
[01:47] We're going to start building your very first
[01:49] vibe-coded workflow.
[01:50] And then in module three, we're going to take that workflow
[01:53] and we're going to iterate.
[01:54] We're going to enhance, we're going to make it better.
[01:56] And we're going to learn throughout all of these
[01:57] and best practices to do all three.
[02:01] So by the end of this course,
[02:02] you will be able to build complex workflows
[02:06] using cloud code vibe-coding manner
[02:09] and able to debug and optimize them with AI assistance
[02:13] and then deliver the client-ready
[02:15] or workflows and automations for yourself much, much faster.
[02:19] All right, so let's take a look at what the heck I'm talking about,
[02:23] vibe-coding, cloud code, and put cloud to work
[02:26] so you can kind of get a better idea of this.
[02:28] So I'm going to switch over to VS code.
[02:32] And I've thought of just a very easy workflow.
[02:35] This isn't the one we'll be building.
[02:36] I just want to do an easy one for a demo.
[02:38] But I say, I need a workflow that checks my Gmail
[02:41] for new emails every 10 minutes.
[02:44] And if I've received a new one, send me notification on Slack.
[02:47] So I sent that to cloud.
[02:50] And it gave me all of this.
[02:55] It put a plan together.
[02:56] It's going to have access to all the NADN tools.
[02:58] And it's going to have access to your actual workspace.
[03:02] It went through all of this, came up with a plan.
[03:04] And throughout this, it's asking me,
[03:06] like one of the questions for this particular one was,
[03:09] which Slack channel did it want the notification in?
[03:12] Or do you want it as a DM?
[03:13] And I was like, you know what, send it as a DM.
[03:16] It goes through here, sets all this up, gives you a summary.
[03:20] And then if I go over to my NADN now,
[03:25] I've got a new workflow called Gmail to Slack every 10 minutes.
[03:30] So it created that.
[03:31] It named it that.
[03:31] And it created all of these nodes.
[03:34] And we'll dive into how some of this works.
[03:36] But you can see it's set up a trigger to check
[03:38] for every 10 minutes, which is what I've asked it to do
[03:41] for new emails.
[03:42] There's an if statement.
[03:43] So if there is one, it's going to go to this code node,
[03:46] which it did all of this coding itself.
[03:48] I didn't type any of that.
[03:50] And it's going to send a Slack DM to me
[03:52] with the formatted message.
[03:54] So super powerful, super time saving, super easy
[04:00] if you don't know code, but you know what you want.
[04:03] So let's dive in.
