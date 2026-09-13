# Loom Transcript · CC_P2_1.8_Skills_in_Action

**Source video ID:** 23a9b9dd252d43cfa0850e9afb5d863b
**Loom URL:** https://www.loom.com/share/23a9b9dd252d43cfa0850e9afb5d863b
**Detected language:** en (probability 1.00)
**Duration:** 357.2s

---

[00:00] In this video, we're going to put skills into practice.
[00:03] We're going to ask God Code to build a skill for a task that we would actually repeat on our day-to-day work.
[00:08] We're going to test it, refine it, and we're going to see how skills can make our workflows instantly reusable.
[00:14] For this example, we're going to pick a repeatable task, try to think about something that you would do regularly that follows a similar pattern each time.
[00:22] Some ideas could be drafting an email, creating a social media post, summarizing a document or an article, or generating a weekly status update.
[00:31] For this demo, I'm going to build the draft email skill, which is something almost everyone uses every day.
[00:37] So we're going to go to VS Code.
[00:39] We're going to start a new project. I created a new folder for this project.
[00:43] And I'm going to tell Claude,
[00:45] I want you to create a skill called draft email.
[00:48] Here's what it should do. I'll give you bullet points with the key information I want in that email,
[00:53] plus hoods for and the tone that I want, professional, casual, whatever.
[00:57] You're going to write a polished email draft, and you're going to save it in the temporary folder.
[01:02] The email should be concise, no fluff, just clear communication.
[01:06] Build this as a skill so I can reuse it.
[01:08] And you should follow the official Claude Code skill format when creating it.
[01:12] I'm going to go to plan mode, and I'm going to execute this.
[01:16] Is it going to start planning how to create the skill?
[01:19] And once it's done, I'm going to review it.
[01:22] The user wants a reusable skill that takes bullet points.
[01:26] This is okay. Within a Claude folder, there's going to be a skills folder.
[01:31] This skills folder is going to contain all the skills created for this project.
[01:35] In this case, the skill is going to be called draft email.
[01:39] So each skill is going to have its own folder.
[01:42] And what's important here is that within this folder, there's a skill.md, skill.markdown.
[01:48] That's going to specify all the instructions for this skill.
[01:51] Just like we did with the workflows in previous videos, skills and workflows are basically the same.
[01:57] It's the same concept.
[01:58] The difference is that skills are now an official part of Claude Code.
[02:02] And this is not only going to be a skill that we can use as a workflow, but thanks to Claude Code.
[02:07] This is also going to be a slash command.
[02:09] And we can call it and reuse it as many times as we want.
[02:12] We're going to see this in a couple of minutes.
[02:14] Let's finish creating this skill.
[02:16] It all looks good.
[02:17] So I'm going to hit yes and auto accept.
[02:20] Okay, it's finished working.
[02:21] And we can see that it created the temporary folder.
[02:24] This is where we're going to see all the outputs, all the email drafts.
[02:28] And it has created the Claude slash skills folder.
[02:31] This skills folder is going to contain all the skills that we want to create.
[02:35] In this case, we do have a draft email folder.
[02:38] Within this folder, we're going to find the skill markdown.
[02:42] And what can we find in a skill markdown?
[02:44] First and most important, we're going to find the name and the description.
[02:47] Whatever argument this skill may need.
[02:49] Like, for example, it's going to be expecting from us the bullet points for the email, the recipient and the tone to create the email.
[02:57] And then it's going to explain what the skills should do.
[02:59] This is exactly the same concept as we did with workflows.
[03:03] It's going to mention the instructions and all the steps that the workflow should follow.
[03:07] The only difference is that maybe two months ago, Claude merged what were called slash commands into skills.
[03:14] So now we can use or we can call a skill or a workflow as a slash command.
[03:19] And what is a slash command?
[03:21] Remember when we use clear, for example, this is a slash command.
[03:24] We're calling slash clear.
[03:27] In this case, we should be able to call slash draft email.
[03:32] So as you can see by just calling a slash command, we can reuse and call as many times as we want this skill or workflow.
[03:40] So I'm actually going to clear context first.
[03:43] And I'm going to go ahead and call draft email.
[03:47] And since in that command, I didn't specify any bullet points, the tone or who the email is for.
[03:54] Claude code is now asking me that information.
[03:56] So I'm going to say this is going to be sent to a client.
[04:00] I'll provide the bullet points and it should have a professional tone.
[04:04] And I'm going to paste a few bullet points that I have.
[04:08] And with this information, it's now going to start running the skill.
[04:13] And as we can see, it's finished working and it has created the email draft under the temporary folder.
[04:19] And if we would like to modify anything, we can just ask in Claude code.
[04:23] Like we've been doing so far, but I actually want to show how easy it is to reuse these skills.
[04:28] So I'm going to try with a new email.
[04:30] So let's say I need to draft a new email.
[04:33] I'm going to clear the conversation and I'm going to type slash draft email.
[04:39] So in this case, I want to draft an email to a client.
[04:43] The tone is going to be professional and these are my key points.
[04:47] I'm going to run the skill.
[04:49] When running the skill, it's going to go into the skill markdown into the skill instruction.
[04:55] It's going to follow all the steps.
[04:57] And as we can see, it has created a new file with the new draft.
[05:02] So this has been an intro to what skills are in Claude code and how they are basically the same as workflows in the WAT framework.
[05:10] And in addition to being a workflow, now they can also become slash commands.
[05:15] And thanks to that, we now have a reusable command that can turn bullet points.
[05:18] And that can turn bullet points into an email draft in just a few seconds.
[05:22] So every time we use this slash command draft email is going to follow the same rules to be concise to use the right tone and to analyze bullet points.
[05:32] And if you ever want to modify this workflow or this skill, you just come here and ask whatever modification you want and Claude code is going to do it.
[05:40] And this is how you build a custom skill from scratch using Claude code.
[05:44] Just by telling it what you need, then you can test it, refine it and iterate on that.
[05:48] And we have also seen how skills and workflows are very similar in theory and how skills are instantly reusable.
