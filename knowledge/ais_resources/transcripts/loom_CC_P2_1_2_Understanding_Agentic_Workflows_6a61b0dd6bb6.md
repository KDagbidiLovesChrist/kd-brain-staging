# Loom Transcript · CC_P2_1.2_Understanding_Agentic_Workflows

**Source video ID:** 6a61b0dd6bb642a990de08e73037e9de
**Loom URL:** https://www.loom.com/share/6a61b0dd6bb642a990de08e73037e9de
**Detected language:** en (probability 1.00)
**Duration:** 247.2s

---

[00:00] In this video, we're going to make sure we understand exactly what
[00:03] agenteic workflows are, how they're different from what we've been doing
[00:07] before with NADN, and which projects we're going to be building in this module.
[00:11] So, what are agenteic workflows?
[00:14] We can explain agenteic workflows by comparing it with NADN.
[00:18] NADN would be traditional automation, which basically within NADN you can drag
[00:23] nodes, you can connect them all together, and you can configure each step of your
[00:27] process. And if something breaks and if something's not working, you are in charge
[00:32] of fixing that. Now, agenteic workflows completely change that. Instead of
[00:36] telling the system how to do something step by step, you're going to talk
[00:40] cloud code, what you want, and the agent is going to figure out the rest. You're
[00:44] not going to be telling it how to do it step by step. You just tell them the
[00:48] results. Imagine like hiring a very experienced developer. You're just going to
[00:52] tell them what you want, and the developer is going to figure out how to do it.
[00:55] And that's what makes it agenteic. The system is going to reason, it's going
[00:59] to adapt. It may ask you a few questions to clarify stuff, but then it's going
[01:03] to be the agent who figures out how to do it to achieve the result that you want.
[01:07] And also, the agent is going to be able to fix the workflow when something breaks.
[01:11] We can also think about traditional automation with NADN as something
[01:16] deterministic, where whenever we have the same input, we're going to have the
[01:19] same output, and we know all the steps for that process, whereas agenteic workflows
[01:24] are going to be non-deterministic. With non-deterministic workflows, it's AI who
[01:29] decides the path. So to explain it a bit better, the terministic means predictable.
[01:34] You basically know what's going to happen every single time. And with automation,
[01:38] the terministic is actually beautiful. Boring is beautiful. A process that follows
[01:42] each single step the same way every single time, that's fantastic. Now, non-deterministic,
[01:48] it means that there are different variables. Given an input, you don't know exactly
[01:53] what the output will be. There's going to be judgment, there's going to be AI,
[01:57] and generative AI by nature is non-deterministic. So it is our job as AI automation
[02:03] builders to understand that agenteic workflows are non-deterministic. And that when we give
[02:09] an input, we may have different outputs, because in the middle, the AI is going to be
[02:13] reasoning different alternatives. So let's try to define agenteic workflows with
[02:19] an analogy. Let's say that traditional automation is like cooking dinner yourself from a recipe.
[02:23] You're going to follow each step of the recipe. You're going to make sure that you have all the
[02:27] ingredients. But if we skip something, some ingredient or some step, we are probably going to mess up.
[02:33] But agenteic workflows are like walking into a restaurant and telling the waiter,
[02:37] I won't steak for dinner. You're not going to tell the chef how to cook it, how to season it. They
[02:42] may ask you how do you want your steak cooked, and you may say medium rare or whatever. But you're just
[02:47] telling them the end result. They're going to figure out the ingredients and which steps to follow.
[02:53] And that's exactly how agenteic workflows work. So what are we going to see in phase two? We're going
[02:58] to learn what the WAT framework is, how to work with MCP servers in Cloud Code, how to build and
[03:05] what are skills in Cloud Code, and we're going to see some token management tips to keep our sessions
[03:10] productive and burn as less tokens as possible. To learn this, we're going to have two main projects,
[03:16] we're going to have a research brief workflow and a slide deck generator.
[03:20] And here's the mindset that we need to have for this phase. When working with agenteic workflows,
[03:25] we need to describe what we want, the final result. Let's try to avoid how to do it,
[03:30] and let's allow Cloud Code to decide and figure out how to do it. So the key takeaways from this video.
[03:37] Agenteic workflows tell the system what you want, not how to do it. The agent is going to reason
[03:43] adapt and ask questions, and it's going to self-heal whenever there's an issue. We saw the
[03:47] difference between deterministic, something predictable versus non-deterministic, when something's
[03:52] variable like AI and agenteic AI. And that we're going to be building two real workflows, one for research
[03:58] and one as a slide deck generator. All this is going to be triggered by you from your desk, and we're
[04:04] going to have Cloud Code do the work.
