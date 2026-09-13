# Loom Transcript · AIS_PLUS_Claude_Code_1.3_WAT_Framework

**Source video ID:** 559d5d8f6b97461b9ff2fdd29e2367f7
**Loom URL:** https://www.loom.com/share/559d5d8f6b97461b9ff2fdd29e2367f7
**Detected language:** en (probability 1.00)
**Duration:** 373.5s

---

[00:00] Okay, in this video, we're going to learn the framework that's going to power every
[00:04] authentic workflow that we're going to build.
[00:06] This is the WAT framework.
[00:09] You're also going to learn how to write a professional Cloud MD file that's going to work
[00:13] for these cases and that's going to let you build full automated workflows from scratch.
[00:19] Honestly, you could open Cloud Code right now and start talking to it and it's going to do
[00:24] just fine if your use case is simple.
[00:27] But without a structure, without a framework, things can get messy pretty fast.
[00:31] Think about it like a workdesk.
[00:33] If you just threw every paper, every homework assignment, every node from every subject
[00:38] onto your desk with no organization, you could still study and do pretty well, but it's
[00:43] going to be tough.
[00:44] That's why you would have folders, you would have shelves, you would have notebooks because
[00:47] structure makes things easier.
[00:50] So how do we make things easier when building workflows?
[00:53] We use the WAT framework, where W stands for workflows, A stands for agent, and T stands
[01:00] for tools.
[01:01] Let's start talking about the workflows.
[01:03] The workflows are the instructions.
[01:05] These are going to be instruction files written in markdown.
[01:09] If you've never seen a markdown file, it's basically natural language with headers, bullet
[01:14] points and bold text so that the agent knows what's important.
[01:19] And you can think of a workflow like a job description or an SOP.
[01:22] And basically tells the agent what to do.
[01:25] For example, you may have a workflow called competitor analysis.
[01:28] The workflow tells the agent to research businesses, gather data from five competitor sources,
[01:34] analyze the findings, and then create a PDF report.
[01:37] It's a process, it's a sequence of steps and guidelines that the agent is going to use to
[01:41] figure out how to achieve the end goal.
[01:44] And the cool part here is, as the agent works and gives you outputs, you can say I like
[01:49] this, but I didn't like that.
[01:50] And the agent's going to actually update the workflow, the markdown file.
[01:54] So that next time it calls that workflow, it does it better.
[01:57] This is actually called the self improvement loop, which we're going to see later.
[02:01] So next, we have the agent.
[02:03] The agent is the coordinator.
[02:05] This is going to be cloud code itself.
[02:07] Think of it like the brain.
[02:08] It's going to read your workflows and instructions.
[02:11] It's going to look at what tools it has available.
[02:13] And it's going to make decisions about which tool to use and when.
[02:16] You can think of it like your project manager.
[02:18] You give them instructions and they're going to delegate tasks to the right tools.
[02:22] And finally, we have the tools.
[02:24] These are basically the workers.
[02:26] Tools are Python scripts that actually do the work.
[02:29] Each tool is going to have a one specific job, ideally, like scraping a website, generating
[02:34] a PDF, analyzing data, and the agent's going to call these tools when it needs to, based
[02:39] on what the workflow says.
[02:41] And don't worry about the fact that these are Python scripts because it's going to be cloud
[02:44] code, the one in charge of creating these scripts.
[02:47] So cloud code is going to build them.
[02:50] It's going to repair them if they fail.
[02:52] So don't worry about learning Python or scripts.
[02:54] Cloud code is going to handle this.
[02:56] OK, now let's talk about the self improvement loop that we mentioned before.
[03:00] Self improvement is one of the most powerful concepts in agent workflows.
[03:04] What happens is the agent runs a workflow and finds an error.
[03:08] It reads the error and it tries to figure out what went wrong and tries to fix the tool.
[03:13] Then it's going to update the workflow file so that the error never happens again.
[03:17] This way, the next time we run this workflow, it's going to run smoother and faster.
[03:22] This is how an agent workflow can fix itself.
[03:25] So just like in phase one, four and eight, and we need a cloud MD file, let's see what
[03:30] we should include in our cloud MD for agent workflows.
[03:34] In case you don't remember, cloud MD file is the onboarding document.
[03:38] It's going to tell the agent from the beginning what you want to do and how to do it.
[03:42] So a good cloud MD file should include the framework that you want to use.
[03:46] In this case, DW80 framework and how each layer works.
[03:50] Some operating rules, for example, look for existing tools first, then learn and adapt when
[03:56] things fail and keep workflows current.
[03:59] What's the file structure where workflows tools and temporary files should be located.
[04:04] We should also include project specific contexts like what the project does, who's it for and
[04:10] important constraints if there are any.
[04:12] And finally, we're going to add style preferences like what's the format of the output, what's
[04:18] the tone, and some naming conventions if applicable.
[04:21] In the previous slide, we said that we should specify the project folder structure and how
[04:26] to organize the files within this project.
[04:28] So for the DW80 framework, we want to organize our project around five folders.
[04:34] One folder is going to have the workflows, which remember are the markdown instruction files.
[04:39] Another folder is going to have the tools, which are the Python scripts that do all the work.
[04:44] Then we're going to have a temporary folder, which is going to have temporary files or intermediate
[04:48] output files.
[04:49] Then we're going to have an environment file, which is where we're going to store our API keys
[04:53] and secrets.
[04:54] Remember, never to share this file.
[04:57] And finally, we're going to have the cloud MD file, which is the onboarding document and
[05:01] what are some golden rules for the cloud MD file.
[05:04] One, try to keep it under 500 lines.
[05:07] And if you ever notice that cloud code keeps doing something wrong, even though you have rules
[05:11] and that you have specified that it shouldn't be doing that, you may want to check the cloud
[05:16] MD file.
[05:17] The file may be too long, so probably the rule is getting lost between everything and the agent
[05:22] may be confused by this.
[05:24] Try to be concise.
[05:25] You may want to move these instructions into a skills folder, which we're going to see in
[05:29] a future video, instead of adding every specific instruction within the cloud MD file.
[05:35] This may not make sense right now because we haven't seen skills yet, but it's going
[05:38] to make more sense in a few videos when we talk about skills.
[05:41] OK, so in this video, we talked about what the WAD framework is.
[05:46] We mentioned that workflows are markdown files that tells the agent what to do.
[05:50] We talked about the self-improvement loop and how agent workflows improve their instructions
[05:55] by themselves.
[05:56] We talked about the cloud MD file and what it is, and how to create a good cloud MD file
[06:00] for agent workflows.
[06:02] And finally, we talked about the project structure that an agent workflow should follow.
[06:07] In the next video, we're going to put all these into practice with a real example in cloud code.
