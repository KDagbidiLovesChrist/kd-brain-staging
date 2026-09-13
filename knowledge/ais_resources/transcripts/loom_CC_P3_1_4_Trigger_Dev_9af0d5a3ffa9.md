# Loom Transcript · CC_P3_1.4_Trigger_Dev

**Source video ID:** 9af0d5a3ffa94eb1a447a085f7ce3074
**Loom URL:** https://www.loom.com/share/9af0d5a3ffa94eb1a447a085f7ce3074
**Detected language:** en (probability 1.00)
**Duration:** 769.4s

---

[00:00] All right, moving on to trigger.dev.
[00:03] What is it?
[00:04] How do we set it up?
[00:05] Again, let's talk briefly about it.
[00:08] So think about leaving a note on a desk
[00:11] versus having a reliable assistant.
[00:14] So the task is obviously the note,
[00:17] and then trigger.dev is going to be the assistant.
[00:19] They'll do the work, handles the problems,
[00:21] and reports back.
[00:22] Again, all of our automations are in the cloud using the engine.
[00:27] So again, why?
[00:29] No timeouts, the task will run as long as they need to.
[00:32] It'll have built-in retries to do it automatically,
[00:35] full trace logging to show every single thing that's going on.
[00:39] We can do the schedules, we can do the webhooks
[00:41] for our two different projects we'll be trying.
[00:44] And it's cloud code-friendly.
[00:46] There's an official MCP server, which we'll jump into here
[00:48] momentarily.
[00:50] So step one, let's set up our account with trigger.dev,
[00:53] which is the URL.
[00:55] We'll go to trigger.dev, we'll click get started.
[00:58] We're going to sign up with our GitHub account,
[01:00] if you don't already have an account, with trigger.dev.
[01:03] And it should connect the two automatically, which is nice.
[01:06] We're going to go through this onboarding
[01:08] to create our organization and project.
[01:10] And then the final step for this will copy the project ID
[01:14] from the dashboard.
[01:15] So let's jump over and do that right now.
[01:17] So here I am at trigger.dev.
[01:19] I'm going to click get started up here at the top.
[01:23] We're going to continue with GitHub.
[01:27] And then we're going to hit authorize, trigger.dev.
[01:35] And then let's put in our name.
[01:38] There's the email.
[01:40] How do you hear about us?
[01:43] What role fits you best?
[01:45] Well, just a student, you know, always be learning.
[01:48] OK.
[01:49] Organization.
[01:55] Organization.
[01:56] URL is not mandatory.
[01:58] OK.
[02:00] Create new project.
[02:03] This is our project name.
[02:04] So I am going to label this what we labeled our GitHub repo
[02:08] here.
[02:09] So I'm going to label it phase three dash automations.
[02:15] What are you working on?
[02:15] We don't have to fill out what technology
[02:17] are using what we're trying to do.
[02:19] Not required.
[02:20] I'm not going to do it for this.
[02:21] You definitely can.
[02:22] I'm going to hit create.
[02:24] OK.
[02:24] So the next step is very important.
[02:25] Remember, a Cloud Code created a folder for us in our documents
[02:31] or wherever you wanted to put it.
[02:33] So over here, if you see blue buttons as old folder,
[02:36] you open folder.
[02:37] You can click that.
[02:38] Or you can come up here also and click open folder.
[02:43] Once we do that, you'll navigate to the folder
[02:46] that was created.
[02:48] And then that will open that project essentially.
[02:51] So that is very important because it's
[02:56] going to start building all the files
[02:58] and put them in this folder so that Cloud Code can then
[03:00] connect to GitHub and Trigger.dev.
[03:04] Now we need to connect our Cloud Code to Trigger.dev.
[03:08] It has an official MCP server, so we will
[03:11] be able to have Cloud Code manage it through conversation
[03:14] there in VS Code.
[03:16] So we're going to use this prompt, help me install the Trigger.dev
[03:18] MCP server for Cloud Code.
[03:20] So I can manage my Trigger.dev project from here.
[03:23] So let's go paste that into Cloud Code.
[03:26] So put that in there and hit Enter.
[03:30] All right, so I was asking, hey, can I search for this MCP server?
[03:35] We're going to say yes, two times for both of that.
[03:40] And now allow searching for this query.
[03:43] Trigger.dev, MCP server, GitHub, repository, installation docs.
[03:46] Yes, that's fine.
[03:47] Again, you might have different things popping up,
[03:49] GitHub Ashes and whatnot, but just allow those.
[03:52] Make sure you're reading, following along,
[03:53] to understand what Cloud's doing.
[03:55] It should make a lot more sense at that point.
[03:57] So we're going to let Cloud keep going.
[04:02] OK, so now it's telling us it has an official MCP, which
[04:07] we know built into their CLI.
[04:09] Here's how to add it to Cloud Code, run this command,
[04:12] or restrict it.
[04:13] So it's giving all of these steps to follow.
[04:15] And then it's asking, do you want me to run the Cloud MCP
[04:20] Add command for you?
[04:21] So we'll just say yes, please.
[04:24] All right, we're going to allow it to do so.
[04:31] OK, we're going to allow some bash commands.
[04:34] OK, so it says it's done.
[04:37] MCP server is installed and connected.
[04:39] It's available across all of your projects.
[04:42] The first time you ask me to do something,
[04:43] requires your account, this project,
[04:46] Trigger Run, et cetera, it will prompt you to log in.
[04:49] OK, perfect, so we're ready to proceed.
[04:51] OK, so step three, we need to initialize the project.
[04:54] We're going to use the prompt, help me initialize Trigger
[04:57] Dev in my project folder.
[04:58] My project ID is, and then we're going to copy and paste
[05:01] that ID in there.
[05:03] So that's going to do a couple things.
[05:04] It's going to create our Trigger Config type script file
[05:08] in the project configuration in a directory where all the tasks
[05:11] will live.
[05:12] So that side folder there that we created
[05:14] is going to start populating as Cloud Code starts connecting
[05:18] and building all these things for us.
[05:19] All right, just as a quick reminder, once we're in Trigger Dev,
[05:23] you scroll down under Project Settings on the left side.
[05:25] You'll see General.
[05:26] Click on that.
[05:27] Up at the top, it will have your project ID number.
[05:30] You can copy that, and we're going to paste that with this prompt.
[05:34] Help me initialize Trigger.dev in my project folder.
[05:37] My project ID is boom, and then we're going to hit Go.
[05:40] And it should start populating over here right now.
[05:43] In this folder, we should have nothing.
[05:46] OK, so it says that our folder is empty, which it is.
[05:49] The Trigger.dev init command is interactive,
[05:51] so I can't run it non-interactively from here.
[05:54] You'll need to run it yourself in your terminal.
[05:56] So I've copied this code.
[05:58] It's given me there.
[05:59] Looks like it's saying it's going to ask us some questions
[06:01] after we do this.
[06:02] So I've entered that.
[06:04] It's going to initialize the project.
[06:05] Let me see if I can make it a little bit bigger for you guys.
[06:12] It's going to go off my screen here.
[06:14] All right, where would you like to create the Trigger.dev directory?
[06:18] We're going to hit that.
[06:21] Choose an example to create in the directory.
[06:25] So we will do the simple hello world.
[06:27] Great.
[06:29] It's going to do all of that.
[06:31] So the next step, start developing,
[06:33] run the MPX Trigger at latest dev
[06:36] in your project directory.
[06:38] OK, so I've gone back to the terminal,
[06:40] and these next steps start developing.
[06:42] You need to run the MPX Trigger.dev.
[06:44] So I've pasted that down here, and it's building local worker.
[06:49] Local worker ready, and then it has to end up there.
[06:52] So now, if I go back to Trigger.dev,
[06:53] you can see that little screen to start three easy steps is gone.
[06:59] We have a task here that says hello world, which is the ID.
[07:04] We have the file, which is where it is.
[07:06] It's running completed activity.
[07:08] We'll move down here real quick duration.
[07:10] So all the information for this one that starts to build.
[07:13] If we go back to Cloud Code, you can see over here under the folder,
[07:17] it's starting to populate with some TypeScript files,
[07:20] Trigger.config, TypeScript, and all of that.
[07:24] So now that we've told Cloud Code to connect us,
[07:28] let's make sure that it can see our Trigger.dev.
[07:33] So let's ask for a prompt just to confirm that.
[07:36] So we'll just say, can you confirm your connected to my Trigger.dev account
[07:39] and can see the example task?
[07:41] OK, so it's asking, do you want to proceed with MCP Trigger.dev list projects?
[07:47] If it gives you an error before that,
[07:49] and make sure you've restarted Cloud Code.
[07:53] Once you install an MCP, it's always a good idea
[07:56] to just restart Cloud Code so that it'll show up next time.
[08:00] So if you get an error, that's probably what's going on with there.
[08:03] So now we can see connected and confirm.
[08:05] Here's what I see, organization, up it, project-based 3-automations.
[08:09] OK, no runs have been triggered yet,
[08:12] since it was just initialized.
[08:14] So one more thing we'll do, just to ensure everything is working,
[08:18] is we'll ask it to trigger the example task
[08:22] that we have there, the Hello World one.
[08:24] So I'm just going to quickly ask it, hey, can you trigger that real quick?
[08:29] And then it's going to ask for permission there.
[08:34] The worker has one task registered, triggering it now.
[08:37] Let's give it permission.
[08:38] It's just about to switch over.
[08:40] It looks like it's doing it, view it, run in the dashboard.
[08:44] So let me switch over real quick.
[08:47] Runs, it looks like this one just completed at 12.02.
[08:53] So yeah, this one just went right now.
[08:57] It shows the duration, how long it took, view it by the way.
[09:01] Queue when it was created.
[09:03] So you have all this information, right,
[09:04] and trigger dev that I was saying.
[09:07] Let me go back and see, it's asking for one more thing.
[09:12] Wait for run to complete, which it's already done.
[09:14] It looks like it took around six seconds.
[09:16] Everything is working into in, you're fully set up.
[09:18] I could trigger task, modern runs, and manage your project directly
[09:21] within cloud code.
[09:22] What would you like to build next?
[09:24] So again, cloud might tell you different things.
[09:29] It's not going to be probably exactly what's on my screen.
[09:31] Additionally, your folder over here might look slightly different, right?
[09:36] That's the thing with AI is it's interpretive.
[09:40] It's not going to be exact each time.
[09:42] So the important thing is to read what it's saying
[09:45] and to ensure the outcome is the same.
[09:48] We know we want to connect, get hub, we know we want
[09:50] to connect our trigger.dev file account.
[09:54] So I think we're ready to proceed.
[09:57] All right, let's take a look at the trigger.dev dashboard
[10:01] a little more thoroughly.
[10:02] We're going to see from that example much, much more details
[10:07] in these are called traces of every step run by run
[10:09] of what's happened.
[10:12] We can show you where the test trigger button is, schedules,
[10:15] the alerts, that sort of thing.
[10:16] So I'm going to switch back over to that really fast.
[10:19] OK, so we're back in our profile.
[10:21] So we've seen this around our task view here.
[10:24] It shows hello world, our file, all of that.
[10:26] And we can see now it's green that we have completed one.
[10:29] I go down here to Runs, we can see this will list all the runs
[10:32] that I've ever taken place with that information.
[10:36] Now, if we click on one to go in,
[10:38] you can show this is the root task.
[10:40] And then it'll go, each line is a step that's taken place.
[10:43] And then over here in the middle is kind of like the timeline.
[10:46] So all together, 5.8 seconds, attempt one,
[10:51] started about here, it was 5 seconds, it ran.
[10:54] There it is, hello world.
[10:55] And then it's waiting for 5 seconds.
[10:58] Over here on the right, you can see a summary of the timeline
[11:01] there.
[11:02] And then the payload and the output, which is hello
[11:05] from Cloud Code, which was the test there.
[11:09] Down below here, you've got your schedules, cues,
[11:12] everything sorted, really easy to find over here.
[11:15] So one super important thing here is the environment.
[11:17] So there's the two environments, there's
[11:19] the development and the production, which is very common
[11:23] when you're doing anything like this at websites
[11:25] or whatnot.
[11:26] You've got the development side, which allows you
[11:28] to come in and test without it actually going live
[11:31] and pushing out, right, and doing anything.
[11:33] And then you have the production.
[11:34] So definitely keep an eye on where you're
[11:38] doing your building, right?
[11:40] You want to build and test and everything in development.
[11:42] And then when you're ready to go live,
[11:44] you want to make sure that we switch it to production
[11:46] and it's live on the production environment.
[11:50] Let's recap kind of what we've done in this one video here.
[11:53] So remember, TriggerDeb is running our tests in the Cloud
[11:56] without the timeouts, the retries.
[11:58] It's logging everything.
[11:59] We have way, way good visibility of everything
[12:02] that's going on.
[12:04] We've signed up using our GitHub account.
[12:07] We've installed the MCP server, so Cloud can manage the TriggerDeb
[12:10] just through the conversation.
[12:14] The mpxtrigger.dev at latest sets up our project, which
[12:17] we've done.
[12:18] Remember, you've got to open your project folder inside of VS Code
[12:23] so that Cloud Code has access to everything that we've set up.
[12:27] Otherwise, you'll be going back to terminal
[12:28] like we were doing initially.
[12:30] And we need to do it just through conversation and Cloud Code.
[12:32] So make sure we do that.
[12:34] And then the dashboard is really your bridging that gap.
[12:38] Remember, since Cloud Code's not looking at the errors
[12:40] and stuff, the dashboard is going to be your window
[12:43] to kind of see what's going on.
[12:44] So yeah, get all that set up and then we'll be ready to move on.
