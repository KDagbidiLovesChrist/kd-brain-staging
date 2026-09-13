# Loom Transcript · CC_P2_1.9_Slide_Deck_Generator

**Source video ID:** 078098add1884383a299ef94a091a251
**Loom URL:** https://www.loom.com/share/078098add1884383a299ef94a091a251
**Detected language:** en (probability 1.00)
**Duration:** 351.3s

---

[00:00] Okay, let's go through one more example of how to create
[00:03] a GenteG workflows with Cloud Code following the WAT framework.
[00:07] In this video, we're going to build a workflow that's going to act as a slide deck generator.
[00:11] We're going to give the workflow a document and it's going to generate a PowerPoint presentation out of it.
[00:16] We're going to go to VS Code.
[00:18] We're going to create a new folder for this project and we're going to open Cloud Code.
[00:23] So, what do we need first? First, we need the Cloud MD file.
[00:27] So, we're going to go to Plan Mode and we're going to ask Cloud Code to generate the Cloud MD file
[00:32] at the root of the project using DWAT framework.
[00:35] We're going to briefly explain what the DWAT framework is and we're going to specify
[00:40] the folder structure that we want.
[00:42] We're going to hit Enter and it's going to start planning how to create the Cloud MD file.
[00:47] Once it's done, we're going to review the plan.
[00:50] It got DWAT framework correctly.
[00:53] All the folder structure, we're going to hit Yes and Auto Accept and it's going to create the Cloud MD file.
[01:00] It has finished working and we can see that it created the Cloud MD plus also the folder structure.
[01:07] These are empty for now but we're going to be using these in a minute.
[01:11] And about the Cloud MD, it created a brief description for the project.
[01:15] It's a workflow for generating presentation slides, the DWAT framework,
[01:21] folder structure, conventions, okay, everything looks good.
[01:24] So, next step would be to actually create the workflow.
[01:28] So, we're going to clear the conversation and we're going to ask it to build the workflow.
[01:35] And the workflow is going to be, I have a document.
[01:37] It's going to be under temporary resources and I will want you to turn it into a slide deck.
[01:43] I want you to create the required workflows and tools to generate this.
[01:47] The workflow should be able to read the document, extract key points
[01:50] and create the presentation file.
[01:52] Make it clean and professional, help me plan this and ask me any questions.
[01:57] So, we're going to go to plan mode.
[01:58] We're going to hit Enter and it's going to start planning and thinking how to create the workflow.
[02:04] It's now asking me what language I prefer for the tools.
[02:07] I'm going to go with the recommended one which is Python.
[02:11] How should the key points be extracted from the document?
[02:14] Cloud does it. What style do you want for the generated presentation?
[02:19] This is going to be a business presentation so I'm going to go with corporate and professional.
[02:30] Okay, now that it's done planning, let's review the plan.
[02:34] We need a workflow to take a document from resources, extract the content,
[02:38] and Cloud should analyze and structure it into slides.
[02:42] All this seems okay. The tools.
[02:45] We don't really need to understand the Python tools.
[02:47] We just want to make sure that the workflow makes sense.
[02:50] And it's going to output what we need.
[02:52] Slide types, workflow's implementation, okay.
[02:57] All this looks perfect so I'm going to go to yes and out of accept.
[03:01] And it's going to start creating the workflows and the tools.
[03:04] Okay, now that it's done working, we can see that it created one workflow,
[03:08] document two slides, and it created two tools to Python scripts.
[03:13] So next, we need to paste our document here under temporary resources.
[03:18] So I'm going to move the document here, resources, I'm going to clear the conversation.
[03:25] And I'm going to say now run the workflow.
[03:29] You can find the document under temporary resources.
[03:34] I'm going to go to bypass permissions and we're going to hit enter.
[03:38] It is now reading the workflow.
[03:40] It's following the steps of the workflow.
[03:42] We can see the steps here.
[03:44] It's analyzing the content now.
[03:46] And now that it's done working, it seems that it has generated 26 slides
[03:50] and saved it under temporary outputs presentation.
[03:54] So we are going to open that file.
[03:57] And we're going to be able to see all 26 slides, summarizing our document.
[04:01] So original document was this one.
[04:04] It was a 10, around 10, 15, 16 pages with a lot of information about
[04:09] cloud code and how it impacts businesses.
[04:12] And our workflow summarized this entire document
[04:15] and created a more professional presentation.
[04:17] With the main titles, what is cloud code,
[04:21] the business case, why it matters,
[04:23] each section has bullet points.
[04:25] There's of course a lot of room for improvement.
[04:27] Maybe you don't like the design.
[04:29] Maybe you want something more casual.
[04:31] Maybe you don't like the colors.
[04:33] Or something else I'm noticing.
[04:35] All these slides seem to have bullet points.
[04:38] So we could definitely go back to cloud code and say,
[04:42] hey, I like a more casual presentation.
[04:44] I want to change the colors.
[04:45] I want to change the font or format.
[04:47] And instead of all the slides being bullet points,
[04:50] I would like a mix of text and bullet points.
[04:53] And there are even skills now that we've covered cloud code skills.
[04:57] Once you feel more comfortable with creating
[04:59] agentic workflows, I highly suggest that you start adding skills into this.
[05:04] For example, there's a great popular skill for slide deck design.
[05:08] So you could even use that skill and it would improve your design.
[05:12] So you could definitely use that skill within this workflow.
[05:14] And it would absolutely improve the design.
[05:16] Instead of having to explain to cloud code,
[05:19] what you need in terms of design.
[05:22] And this is how you can easily build an agentic workflow
[05:24] in cloud code using DWIT framework,
[05:27] just by using natural language and without the need of coding.
[05:30] All you have to do is create the cloud MD file,
[05:34] ask it to generate the workflow using DWIT framework,
[05:37] paste your document,
[05:39] the one that you want to summarize and create the slide deck,
[05:42] and then ask cloud code to run the workflow.
[05:45] And in just a few seconds,
[05:46] you're going to be able to see your slide deck
[05:48] generate under the outputs folder.
