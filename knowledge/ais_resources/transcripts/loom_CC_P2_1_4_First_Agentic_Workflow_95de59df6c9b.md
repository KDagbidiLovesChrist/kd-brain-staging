# Loom Transcript · CC_P2_1.4_First_Agentic_Workflow

**Source video ID:** 95de59df6c9b4377b94a972d9f9b2589
**Loom URL:** https://www.loom.com/share/95de59df6c9b4377b94a972d9f9b2589
**Detected language:** en (probability 1.00)
**Duration:** 598.7s

---

[00:00] Okay, it's time now to boot the WAD framework into action.
[00:03] In this video, we're going to run our first
[00:05] agenda workflow. The goal is to see the framework working in real time
[00:09] before we keep adding more tools into the mix. This is what we're going to be
[00:14] doing. Let's say we have a messy notes document,
[00:17] something you typed very quickly and you want to create a structured document
[00:21] that is more cleaned up, organized and you want to make it look more
[00:24] professional. We're going to create an agenda workflow that's going to do
[00:28] to do this. We're going to follow these five steps. First, we're going to set up the project in
[00:32] Visual Studio Code. We're going to create the Cloud MD file with the WAD framework.
[00:38] Then we're going to tell Cloud Code what we want. We're going to tell it the output and
[00:42] not how to build it. Then we're going to turn on plan mode so that Cloud is going to read the
[00:46] Cloud MD file and it's going to ask us a few questions. It's going to build a plan and once we
[00:51] approve the plan, we're going to see Cloud Code in action and we're going to see how it creates
[00:55] the WAD framework. Then we're going to ask it to build the structured document. It's going to
[01:00] generate this document and finally, we're going to iterate. We're going to see the document. We're
[01:04] going to give feedback and with our feedback, Cloud is going to update the workflow and the tools.
[01:09] Okay, now that we know the steps that we're going to be following, let's go into Visual Studio and
[01:13] start working. Okay, we are now in Visual Studio. I have created a new folder for this project,
[01:19] which is going to be called first agenda workflow. Our first task is going to be create the Cloud MD
[01:25] file. We're going to open Cloud Code and we're going to ask it to create the Cloud MD file.
[01:32] For this, I already have a prompt created where I basically explain the WAD framework that it should
[01:37] follow. I'm going to go to plan mode and I'm going to paste the prompt, which basically says create a
[01:44] Cloud MD file at the root of this project using the WAD framework workflows agent tools. This file
[01:50] is going to be the master configuration that Cloud Code reads at the start of every session.
[01:55] I explain what the WAD framework is and the folder structure that I would like to use. We're basically
[02:01] going to have a workflows folder for all the instructions, a tools folder, which is going to contain
[02:07] the scripts, a temporary folder where we're going to have all the resources or the outputs,
[02:11] and an environment file, which is going to contain the API keys and secrets, which is a file that we
[02:17] should never commit. Okay, let's hit enter. Now Cloud Code is thinking and it's going to start
[02:21] planning how to create the Cloud MD file. Okay, once it has finished creating the plan, we're going to
[02:26] review it and we're going to go hit yes and auto accept, and it is now going to start creating our
[02:31] project structure and our Cloud MD file. Okay, now that he has stopped working, we can see that he
[02:36] has created all the folders, all the necessary folders with the WAD framework and it has created
[02:41] the Cloud MD file. We can take a look at it here, explains what workflows agent and tools are,
[02:48] how it works, what's the project structure and what each folder should have, some directory rules,
[02:54] and some agent instructions like read this file first, what to do when executing a workflow,
[03:00] and what to do when creating new workflows or tools. Feel free to review this document and whatever
[03:06] you want to modify, you can go into Cloud Code and ask it to modify here. Okay, now that we have our
[03:11] structure created and our Cloud MD file created, what are we going to do? The goal here was to create
[03:17] a workflow that's going to help us create a more professional document from our raw meeting nodes file.
[03:23] We're going to give Cloud Code our raw file. We're going to move it into the temporary folder within
[03:28] resources. We're just going to move it here. Cloud Code now has access to our meeting nodes. Next,
[03:35] we're going to clear this conversation so that we can start over with a new context. We're going to go
[03:41] into plan mode again and I'm going to ask Cloud Code to start creating all the workflows and tools.
[03:47] For this, I'm going to tell it. I have a file called meeting nodes with messy nodes from a team meeting.
[03:52] I need you to read through it and produce a clean structure summary document. I want it organized
[03:56] into key decisions, action items, discussion points, and next steps. The output should be a document
[04:02] file in the temporary folder. Actually, it should be in the temporary outputs folder. Help me plan
[04:09] this out. First, I need you to create the required workflows and scripts. Do not create the
[04:16] final document yet. First, we want Cloud Code to create the workflows and the scripts or the tools,
[04:21] and then we're going to ask you to create the final document. We're going to hit enter
[04:26] and it's going to start creating the plan. Now that it has finished with the plan, we're going to review
[04:31] it. Plan for meeting node summarizer, some context of what I need. The files to be created, one tool,
[04:39] to generate the document and one workflow. No changes needed to Cloud MD or environment files.
[04:46] Okay, so it's going to generate one tool, one script, and it's going to create one workflow for
[04:50] the meeting summary. Here, it explains how the WIT pattern works and how it's going to verify how
[04:56] everything works afterwards. So it looks pretty good. I'm just going to go ahead and auto accept.
[05:01] And it's going to start creating the tool and the workflow. All right, it has finished creating the
[05:07] script as we can see here. This is our Python script. We don't need to read it or understand it.
[05:13] This is what's going to be creating the final document and it has created the workflow
[05:18] with all the logic on how the workflow should work. It explains the goal, what's the input,
[05:23] what's the expected output, and all the steps that it should follow. Now all we have to do is actually
[05:28] ask Cloud Code to generate the actual summary document. And it even says so here, Cloud Code is telling us
[05:35] to say just say run the meeting summary workflow and I'll follow the steps defined in the workflow.
[05:41] So I'm going to follow the instructions and I'm going to copy this and paste it here.
[05:46] I'm going to select bypass permissions. I'm going to hit enter and now Cloud Code should start
[05:52] executing the workflow. And as a result, we should see under outputs. We should see our final document.
[05:58] Okay, so let's hit enter. It's going to be following all these steps from the workflow
[06:02] and it's going to start working on the document. And now just after a few seconds later,
[06:08] maybe a minute or two, it has finally created the summary document. It should be under outputs
[06:14] and we can see that it's right here. We're going to open it and see if everything's okay. It created
[06:19] the Q2 planning meeting. It has identified the key decisions made. It has creating the action items
[06:26] with the name of the task. Who is the owner and when is the deadline? This is perfect. It has
[06:31] identified the discussion points and what are the next steps from that meeting.
[06:37] This actually looks pretty good for being our first try, but let's say we would like to modify something.
[06:42] Let's say that something's missing or there's an error and you figure out that you would like
[06:47] something different. So just to give an example of how to modify things after the document has been created,
[06:53] let's say we'd like to modify instead of blue. Our brand actually uses red. So how can we modify? How can
[07:00] we ask Cloud Code to modify this so that our text color is red? We're going to go back to Cloud Code
[07:07] and we're going to say the document looks perfect. I just want to change the color of the document.
[07:17] Right now the accent color is blue. I'd like to replace it to red tones. Update the workflow and
[07:29] tool required for this. And then update the doc file. And this is how we can iterate so that we teach
[07:41] Cloud Code what we want. This is why I'm asking you to modify the workflows and the tools so that in
[07:46] the future, if I want to create a new document from a raw file, it's going to generate these documents
[07:51] in a red accent color so that there's no need for me in the future for a new document to use red.
[07:57] I just asked you to update the workflow and the script and that's it. It says that it has changed
[08:02] the Python script, the meeting summary workflow, and it has regenerated the meeting summary document.
[08:10] So let's take a look at that document. We can see that it has updated the text color to red. It did
[08:16] not update this line though. And probably the table is going to be blue too. Yeah, here it is. So
[08:23] this is perfect. These are great examples on how to iterate. It perfectly fixed and modified all the
[08:28] text. I don't have any blue in text anymore. What I would have to do next is do a new iteration and ask
[08:35] to modify all the lines and the table lines so that they're not blue anymore and I want them to be red.
[08:41] And I can do the same thing as before. I want you to update the workflow and tools so that
[08:51] lines are also red instead of blue. And this is how you can constantly keep iterating with
[09:00] CloudCode to ask whatever it is that you want to modify. And this is how we have been through all
[09:05] the steps from setting up the CloudCode project, going into plan mode, building, and finally iterating
[09:11] on whatever it is that we want to modify. So a few key takeaways from this video. We just learned
[09:17] how the w80 framework works with CloudCode and how to create the Cloud MD file. We learned that we
[09:24] should describe the outcome, not the steps. We learned about the iteration loop. CloudCode builds it.
[09:30] We reviewed. We give it feedback and we keep on iterating until we get our final desired results.
[09:37] We also learned that workflows persist that we can build this one workflow, for example, to create a
[09:42] more professional documents from a raw text file. And in the future, we can use this same workflow
[09:48] in similar tasks. So congratulations on building your first agentic workflow. In the next videos,
[09:54] we're going to start adding more complexity like MCP servers and skills.
