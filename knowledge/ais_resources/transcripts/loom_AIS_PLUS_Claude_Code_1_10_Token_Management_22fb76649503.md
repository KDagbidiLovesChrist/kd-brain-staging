# Loom Transcript · AIS_PLUS_Claude_Code_1.10_Token_Management

**Source video ID:** 22fb766495034f7aafb276439d7b453c
**Loom URL:** https://www.loom.com/share/22fb766495034f7aafb276439d7b453c
**Detected language:** en (probability 1.00)
**Duration:** 404.7s

---

[00:00] In this video, we're going to learn the prompting patterns that get us consistent high quality
[00:04] results from Cloud Code. Plus, we're also going to see how to manage token budget so that
[00:10] our sessions are productive and we're not burning tokens in the meantime. Okay, let's start with
[00:15] this five prompting patterns for Cloud Code. Pattern number one, we need to define the goal
[00:20] not the steps. And as we talked before, this is the core principle of agenda workflows.
[00:25] Instead of saying, hey, I need to do step one, step two, step three, we're going to tell the agent
[00:30] what we want, the end result that we're looking for, and the agent is going to figure out the steps.
[00:36] Pattern number two, we need to be specific about the output. For example, a prompt that's vague could be
[00:41] make me a report, but what we're looking for actually would be something more like create a PDF report
[00:47] with an executive summary, three competitor profiles, and a recommendation section. In here, you could include
[00:53] file format, structure, naming, and word to save it. Pattern number three, use plan mode first,
[01:00] and then execute. I recommend that you always start with plan mode for anything non-trivial.
[01:05] You could say something like, here's a rough idea of what I want. Help me turn this into a solid
[01:10] plan. You can ask me as many questions as you want. And this way, the agent is going to brainstorm.
[01:15] It's going to reason. It's going to do research. It's going to ask you all the right questions,
[01:18] and it's going to come up with a plan. Once you approve the plan, you can switch to bypass permissions
[01:24] and you can let it execute. Pattern number four, you should give feedback not corrections.
[01:30] Instead of saying something like, that's wrong, redo it. I would say something more like,
[01:34] I liked this structure, but the tone is too formal. This way, the agent is going to understand you
[01:39] better and it's going to update the approach and the corresponding workflow for the next time.
[01:44] And finally, pattern number five, you should treat the agent like an expert. Think about yourself
[01:50] like the manager. You're not the developer here. You should tell the agent what results you want.
[01:56] So for example, you could say, I want a competitive analysis. Ask me anything you need to know about my
[02:01] business, but figure out what is going to be the best approach, which tools to use, what data sources
[02:07] to check, and how to structure the output. You can see that this way, you are the manager that's
[02:12] going to tell what you want and the agent is going to be the developer who needs to figure out how to
[02:17] achieve that. Now, let's talk about token management. Let's talk about what context rot is and how we
[02:22] can avoid it so that we don't burn tokens in useless answers from cloud code. So let's talk about this
[02:29] concept that's going to save you hours of frustration. What is context rot? The thing with cloud code is
[02:35] that the more that you talk to it in a single session, the worse it gradually gets. And this is not a
[02:41] bug. This is actually how attention mechanisms work. Basically, once your context usage passes 60%,
[02:48] you're going to start noticing that the model starts making mistakes that it would not have made before.
[02:53] This happens because the model's context window starts feeling with noisy conversational history.
[02:59] And it is forced to prioritize recent, maybe irrelevant messages over core important rules about
[03:06] what you want to achieve. So how do we avoid context rot? To do so, we can follow the context threshold
[03:12] strategy. Whenever you are between 0 to 50%, you're safe, you're good to work freely, you should not worry
[03:19] about it. But then when you get more between 50 to 70%, you're entering the yellow zone and you should
[03:25] start thinking about compacting. When you get to 70 to 85%, you are in the orange zone. You should run
[03:31] compact command proactively. And finally, when you get over 85%, it's advised that you run clear
[03:38] to clean the entire conversation and that you start fresh. So in the previous slide, I talk about clear
[03:44] and compact. What are these commands? These commands help cleaning the context so that we avoid context rot.
[03:50] And what is the difference between each one? When we call slash clear, it's going to do a full
[03:56] research. It's going to clean the entire conversation. It is advised to call this command whenever
[04:01] you're switching tasks or whenever you notice that quality has been degraded. When you start seeing
[04:06] that cloud card starts making a lot of mistakes, you may want to pay attention to the context and you
[04:11] may need to call the clear command. So with clear, we're starting fresh. So how about compact?
[04:18] What compact does is instead of clearing the entire conversation, it's going to create a smart
[04:23] summary. It's going to keep all the key information and it's going to compress the rest.
[04:28] We could use the compact command whenever we are still working within a task, but we notice that our
[04:34] context percentage is starting to get high. So as we said before, if we are between 50 or 85%,
[04:40] we can run compact. So it's going to compress the information and it's going to keep the most relevant
[04:45] one. And whenever we are over 85%, we want to run clear so that we can start fresh.
[04:51] Okay, let's wrap up this video with some practical token saving strategies.
[04:56] Strategy number one, do one task per session. You want to start fresh a new conversation
[05:02] for every new task. Do not reuse a bloated conversation for something unrelated to your original
[05:08] task. Whenever you're done with that task, run the clear command and you're good to start a new task.
[05:14] Strategy number two, define done. Give cloud a clear endpoint. For example, I need exactly
[05:20] 75 profiles. Once you have 75, you're done. If you don't specify something like this, for
[05:25] example, the agent could loop endlessly and spend on tokens looking for 100 profiles when you
[05:31] only need 75. Number three, you should use skills for specialized workflows. Specific instructions
[05:38] in skills are going to save context compared to putting everything in the cloud MD file.
[05:44] Strategy number four, disable unused MCP servers. Each active MCP server is going to add tool
[05:50] definitions to the context. So if you're not using that MCP server anymore, you can disable it.
[05:56] And strategy number five, keep cloud MD file lean. Try to keep it under 500 lines, move specialized
[06:04] instructions to skills and only include in this file what applies to every session.
[06:10] So what are the key takeaways from this video? Define the goal not the steps. Try to be specific
[06:16] about the output format. Remember that we want to define the goal and not the steps. Always use
[06:21] plan mode first for non-trivial tasks. We should pay attention to the context percentage that we are on
[06:28] and if we are past 60%, we either want to run clear or compact. Remember to do one task per session
[06:35] and then run clear. Tell, what is the definition of done? Disable unused MCP servers and try to keep
[06:41] cloud MD file lean.
