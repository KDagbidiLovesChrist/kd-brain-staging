# Loom Transcript · CC_P2_1.6_Research_Workflow_Firecrawl_MCP

**Source video ID:** 853282c0b9d1410fab6d1457e4f2c302
**Loom URL:** https://www.loom.com/share/853282c0b9d1410fab6d1457e4f2c302
**Detected language:** en (probability 1.00)
**Duration:** 460.8s

---

[00:00] In this video we're going to build a real workflow from scratch and we're going to be using Firecrawl
[00:04] MCP. The goal of this workflow is we're going to give it a topic. It's going to research it on the
[00:09] web using Firecrawl. It's going to summarize the findings and as an output it's going to create a very
[00:14] professional formatted document with all the findings from the research. To do this first we're going
[00:19] to plan it. We're going to start Cloud Code and ask it to generate a plan. We're going to build it.
[00:23] Cloud Code is going to create the workflows and the tools. We're going to run the workflow. We're
[00:28] going to ask Cloud to research about some topic. We're going to analyze the output and we're going to
[00:32] iterate on it and finally we're going to test it until we get the desired result. So let's get into
[00:37] VS Code. I have created a new folder for this project. I called it Research Workflow and just as we did
[00:43] in the previous videos, what do we need to do first? First we need the Cloud MD file. So I'm going to
[00:49] go to plan mode and I'm going to ask Cloud to create the MD file at the root of the project using
[00:55] DWAT framework. I explain what the DWAT framework is and I define the folder structure that I want.
[01:02] We're going to hit Enter and now Cloud Code should be planning our Cloud MD file. After a few seconds,
[01:08] it's finished with the plan. I'm going to quickly review it. The folder structure seems okay. It's
[01:14] going to create the Cloud MD file. It got the DWAT framework correctly. Okay, so we can click yes and
[01:21] auto accept. Cool. Now that it's finished, let's take a look at the Cloud MD file. This is the master
[01:27] configuration for Cloud Code. It's going to read this file at the start of every session. Here it explains
[01:33] DWAT framework, workflows agent, tools, folder structure, workflows as markdown tools, temporary files,
[01:42] some rules to follow. Okay, everything looks perfect. So what do we want to do now? We want it to
[01:47] create a research workflow. So first, I'm going to clear the conversation and I'm going to ask Cloud
[01:56] to create a research workflow. I want you to be a research workflow. Here's what I'm looking for. I
[02:01] want to be able to give you a topic and you go research it on the web, find the most relevant and
[02:06] current information and then compile everything into a structured brief. I want the output as an
[02:10] essay formatted document in the temporary folder. Help me plan this out and ask me any questions. The
[02:15] goal here is to generate the necessary workflows and tools using FireClaw MCP. We're going to hit enter
[02:21] and after a few seconds of planning, it's asking me a few questions about FireClaw MCP.
[02:26] Is your FireClaw MCP configuring your Cloud Code settings? Not yet. What output format do you want
[02:32] for the final research brief? Actually, I want markdown to then be converted into a document file.
[02:43] How many sources should the research typically aim to consult for topic? Let's go with the standard
[02:48] and it's going to continue planning. It kept going for a couple of minutes, so I paused the video
[02:53] and now it's finished the plan, so I'm going to review it. The context looks okay, use the WT framework.
[03:00] I need to create a complete research workflow, search the web via FireClaw and compile everything
[03:06] into a structured research brief, save us both the markdown and a document file. These are the files that
[03:12] it's going to be generating. It explains one by one each file. These look okay, the research workflow.
[03:19] Okay, we're good to go, so we're going to hit yes and out of accept. It's going to start generating all
[03:23] the files, all the tools, all the workflows that are needed for this research workflow. Okay, it's
[03:29] done working. It has created an environment file, the MCP JSON for the FireClaw MCP. It has created a tool
[03:36] to convert from markdown to document and it has created the research workflow. So let's take a look
[03:42] at the workflow. It specifies the triggers, the inputs, the steps, search for sources. It's
[03:50] specifying that it should aim to three to five targeted searches, what to do in case of errors,
[03:55] how to evaluate and pick the sources. Okay, this all looks pretty good. It's actually very complete.
[04:02] So let's go ahead and trigger this workflow. We're going to clear the conversation and we're
[04:06] going to tell Claude to research on this topic. What is the current state of AI automation in small
[04:12] businesses, adoption rates, common use cases, and barriers to entry? Let's hit enter. We can see that
[04:18] it's reading the research workflow and it started executing it. It is now using FireClaw for the
[04:25] web search. It's looking at different sources and after summarizing and analyzing, it has started
[04:31] writing the research brief. Okay, it's finished working. We can see that after writing the research
[04:36] brief, it converted it into a document. So as an output, we should have the markdown file and the
[04:42] document file. So if we go to temporary files, outputs, we can see that they're both here. We can see
[04:48] the markdown here with an executive summary, key findings and analyses, gaps and limitations,
[04:55] recommendations, and finally, all these sources. So let's see how the final document looks like.
[05:01] We have a table of contents, the research brief, executive summary. It actually looks pretty good.
[05:08] The formatting is what I expected. It's pretty simple to read. I'm not a big fan of this. I think
[05:14] it's a table. Yeah. I'm not a big fan of how it formatted these sources. So instead of a table,
[05:20] I actually want to have a list. So let's go back to Cloud Code and actually iterate on this.
[05:26] So let's go back to Cloud. I'm going to clear the conversation and I'm going to say everything looks
[05:33] great. I just prefer to format these sources as a list instead of a table. Like
[05:41] number of source, title, author, date, URL, access. Okay. Let's hit enter and it should start updating
[05:54] the workflow. Okay. It seems like it's finished. It updated the markdown file. We can see that it
[06:00] deleted. Here in red is what it deleted. It deleted the table and it added the list, but I don't think
[06:06] it updated the final document. Yeah. No, it just updated the markdown file. So
[06:13] this looks great. Update the document file. Done. Okay. Let's go and take a look at the document.
[06:23] Let's scroll down sources. Okay. Here they are. Now they are formatted as a list instead of a table.
[06:31] And this is a great example on how you can iterate. If there's something you don't like,
[06:35] or if you want to modify anything, or if you want to do a new research on a different topic,
[06:39] you can go back to Cloud. I suggest that you clear the conversation and for example try with a new
[06:45] search. So a few key takeaways from this video. Always start with plan mode. Let Cloud ask you a few
[06:51] questions before building. Review the plan. If you don't like the plan, you can make some modifications.
[06:56] You can ask Cloud to do some modifications. Once you review it and you think that everything looks good,
[07:01] go ahead and execute it. Run the workflow. And if the first run is not perfect,
[07:05] actually in general, the first run is not perfect, but you can go ahead and modify whatever you need.
[07:10] This is what the iteration loop is for. Just like we just did, I asked Cloud to change the sources
[07:15] format from a table to a list. When iterating, give structure feedback, say I liked this,
[07:21] but I want you to change that. The more specific you are in what you want, the better. And of course,
[07:26] you can test with different inputs with different topics to verify that your workflow is working
[07:31] correctly. And if it's not working correctly, you just ask Cloud code to fix whatever the issue is
[07:36] and it's going to go and fix itself. This is called the self healing loop.
