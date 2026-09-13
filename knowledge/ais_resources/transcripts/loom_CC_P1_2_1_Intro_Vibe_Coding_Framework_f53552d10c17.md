# Loom Transcript · CC_P1_2.1_Intro_Vibe_Coding_Framework

**Source video ID:** f53552d10c174b5c9d0e5fd971c05ed2
**Loom URL:** https://www.loom.com/share/f53552d10c174b5c9d0e5fd971c05ed2
**Detected language:** en (probability 1.00)
**Duration:** 230.4s

---

[00:05] Hey, everybody, welcome back to the vibe coding challenge.
[00:09] We're at module two, believe it or not, and this is where we're going to be doing, jumping
[00:14] into the font stuff, right?
[00:15] Where we're building your very first vibe coded workflow.
[00:18] So let's take a look at what we're building.
[00:20] We're going to build a Gmail tech support agent for a foe fictional electronic store that
[00:27] I've created called gadgets and more.
[00:30] It's going to automate the customer support and then use policy documents to look up answers
[00:35] to those tech support questions and create a draft for us in our Gmail account.
[00:43] With this structure for this challenge, we're going to do a masterclass portion where you're
[00:47] going to watch and go through the steps and how it's going to work.
[00:51] Then we're going to turn over to you and it's your turn to do the challenge portion.
[00:54] It's your turn to build.
[00:56] So before we jump in, let's go through proper vibe coding frameworks that you have a good
[01:02] understanding of how the best way, the most efficient way to talk to cloud code, to get things,
[01:08] you'd like it to be the first ask, first go around.
[01:11] So I've said this before, but you need to describe the outcomes, not the next steps, right?
[01:18] You need to assume, and maybe you don't know all the nodes or all the possibilities inside
[01:23] in 8in.
[01:24] So you wouldn't use an if node with rejects, like, no, how about identify tech questions,
[01:31] right?
[01:32] Because in most basic speech, that's how we talk, right?
[01:36] So when we're explaining to cloud code what we want, use the outcomes, not the steps that
[01:41] follow, iterate in the plain language.
[01:43] So instead of saying something like change pulling interval to whatever number that it
[01:48] is, right?
[01:49] We will say, hey, can you just make it check hourly instead?
[01:52] And we've already done that.
[01:53] Let's do that in the first demo, right?
[01:56] Or asking for clarification, right?
[01:59] That's one of the coolest things about, hey, it's like, hey, why did you do it that way?
[02:03] Why did you use this node?
[02:05] What does this configuration do, right?
[02:07] Use this as a learning tool.
[02:09] Don't just set it and forget it and let it go.
[02:12] If you really want to understand this, you really want to grow and learn from this, ask
[02:16] questions.
[02:17] And why did you do that?
[02:18] Because then it'll stick in your mind, and you'll know even better moving forward the other
[02:23] times.
[02:24] Trust, but verify.
[02:25] AI is not perfect.
[02:26] As you saw from the demo, it can make mistakes to always test what gets created.
[02:31] And we'll dive into that later on as we get further down this build, proper ways, etiquette
[02:36] on how to test properly, and then to check the outputs against the expectation.
[02:42] So even if all the in and in workflow is green, meaning there's no errors, it still might
[02:47] not be giving us what we were expecting it to have, right?
[02:51] So that's another part of it.
[02:53] So here's some key conversation patterns when doing this vibe coding.
[02:58] Start with the desired outcome.
[02:59] This is what I'd like to have.
[03:02] Claude is great at asking clarifying questions.
[03:04] Like, well, what's the interval, or where do you want this information to go, or what columns
[03:09] do you want in that spreadsheet, right?
[03:12] Review the plan that it gives you.
[03:14] You can always change it later, but it's nice to have it from the beginning.
[03:18] So review it, and then approve.
[03:20] And then later you can iterate based on the results if it's not working properly through
[03:25] plain communication, again, adjust, adjust, and go from there.
[03:30] So all from one conversation, it's going to read our policy documents.
[03:34] It's going to extract the information, create that vector store, or the stores that it
[03:39] deems correct.
[03:40] It's going to be a fun thing.
[03:42] We're going to see what it's going to recommend, and then it's going to build the workflow for
[03:46] this Gmail tech support agent.
[03:48] So it's going to be super fun.
