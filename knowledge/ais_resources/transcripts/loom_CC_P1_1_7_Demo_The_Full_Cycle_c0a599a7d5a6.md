# Loom Transcript · CC_P1_1.7_Demo_The_Full_Cycle

**Source video ID:** c0a599a7d5a64be0bb4d0ba77e0ffa3f
**Loom URL:** https://www.loom.com/share/c0a599a7d5a64be0bb4d0ba77e0ffa3f
**Detected language:** en (probability 1.00)
**Duration:** 1003.6s

---

[00:00] Okay, now let's start getting to the fun stuff.
[00:03] We've confirmed multiple times that Claude is set up using VS Code.
[00:08] It's connected to our MCP server and our NADIN tools.
[00:12] Let's do a demo together to show the full cycle of this.
[00:16] We'll break the send a three phase.
[00:17] This phase one is the plan mode.
[00:19] We're going to show you these buttons in VS Code and how they work differently as we're
[00:24] using it.
[00:25] So, we're going to tell Claude, I need a workflow that monitors Gmail for emails with
[00:29] urgent and the subject and logs them in a Google sheet.
[00:33] Very straightforward, very basic.
[00:36] Claude is going to ask clarifying questions and get them guaranteed.
[00:40] It's going to then propose a plan and then we get to approve the plan yes or no, or we can
[00:45] make changes.
[00:46] So, let's start with phase one first.
[00:48] All right, so before Claude starts running any commands, I want to show you something in
[00:53] settings that a lot of people miss.
[00:55] It's called the bypass permissions mode.
[00:57] So, if you are familiar or not, there are four modes and they can control how much Claude
[01:02] can do without asking you first.
[01:04] So, if we go on here at the bottom, you can click this.
[01:08] There's been some updates to VS Code from when the original video came out.
[01:11] You may look similar to this and may not have the drop down like this.
[01:15] But you can see here, we've got an ask for edits, so Claude will ask for approval before
[01:20] making each edit.
[01:21] So, as we get into this, you'll notice all these little winners popping up, hey, do this
[01:24] bash command.
[01:25] Hey, do I have permission to do this?
[01:27] It doesn't mean anything's wrong.
[01:28] It just means Claude's asking for permission based on what mode you have selected.
[01:33] So, that's the ask for before edits.
[01:35] We've got edit automatically.
[01:38] Claude will edit your selected text or the whole file automatically.
[01:42] That's fine.
[01:43] Plan mode.
[01:44] This one is where you always want to start before you get into anything because you're making
[01:49] the plan.
[01:50] What is Claude going to be building?
[01:51] Claude will plan for me and then you're going to review it.
[01:55] Auto mode.
[01:56] Claude's going to automatically choose the best permission mode for each task.
[01:58] I believe this is a newer one before the video came out here.
[02:03] And then bypass permissions.
[02:04] This is one that I wanted to show you.
[02:06] Claude will not ask for approval before running potentially dangerous commands.
[02:10] So yes, it allows Claude to just go and not ask you permission for anything, which is nice
[02:15] because you're like, oh, I don't need to worry about anything.
[02:18] But it's also, you have to be careful because you're not seeing what Claude is doing.
[02:23] So if you don't see this here, you have to go into settings over here on the left.
[02:28] You're going to go to settings.
[02:30] There are so many settings, but luckily they have a search bar.
[02:33] If you just type in bypass down here, it looks like it's one to the third one down Claude
[02:39] code.
[02:40] Allow dangerously skip permissions.
[02:41] If you just check this and then probably restart Claude down on the bottom, you will see
[02:47] this here.
[02:48] These are very important.
[02:50] And if you're getting way more pop-up than I am in my videos, just double check which one
[02:54] of these are on.
[02:55] Always be sure.
[02:56] You're on the one that's appropriate for the ask or for the project that you're doing at
[03:00] the time.
[03:01] And you'll be good to go back in VS Claude for Claude code.
[03:05] We're going to paste in the prompt that we had on our slide and need a workflow that monitors
[03:10] Gmail for emails with urgent in the subject and then logs them in a Google sheet.
[03:16] Those were planning.
[03:17] These are very first thing we're going to tell Claude as we get into building a new workflow.
[03:22] And with most things, you should plan first.
[03:25] So we're going to make sure we're on blue for plan mode as we get into this.
[03:29] And we'll show the other ones here in a little bit.
[03:32] So I'm going to go ahead and send that on.
[03:34] So now Claude's going to start thinking and building a plan around building this workflow
[03:40] for us.
[03:42] Right now they're researching the relevant nodes inside in and in and patterns to design
[03:47] the workflow.
[03:49] Now it's looking at the Google Sheets node configuration.
[03:54] So we're going to let Claude do its thing and then we'll come back once there's a next
[03:58] step.
[03:59] Great search results.
[04:00] I have a clear picture of the nodes and patterns needed.
[04:02] Let me write up a plan.
[04:03] So it did all the research on what it will need for this.
[04:06] Now it's putting a plan together on what the workflow will look like.
[04:13] It's saying before I finalize a couple of quick questions, so it's about to prompt
[04:17] us with some questions, probably specifically, of how we want things to behave.
[04:22] What columns do you want logs in the Google Sheets?
[04:24] Okay.
[04:25] So the first one date from subject, a snippet, the message ID, it's saying that's the recommended
[04:30] or we can choose date from subject, date from subject, full body message, or other.
[04:35] We'll go ahead and go for this with the recommended.
[04:39] Second question.
[04:40] Any extra actions beyond logging to Google Sheets?
[04:43] We can also have it apply a Gmail label, also send a notification, which is great.
[04:49] And really cool that Claude's thinking ahead and we might not even thought he's like,
[04:53] oh yeah, let's have it apply a label.
[04:54] But again, for this, we're just going to have it log and then we'll hit submit.
[04:59] So now it's going to take our answers and then apply those changes.
[05:02] Okay.
[05:03] Before we continue, your output is not going to look exactly like mine.
[05:08] Remember Claude is non-deterministic.
[05:09] Which means it makes slightly different decisions every time.
[05:12] Different node names, different structure, different file layout.
[05:15] None of that means something went wrong.
[05:17] All that matters is that it's doing what it's supposed to do.
[05:19] So don't compare it exactly to my screen.
[05:22] Okay.
[05:22] So it's done with the plan.
[05:25] So let's scroll up here and take a look at the beginning of the plan.
[05:29] So workflow, monitor Gmail for urgent emails, log to Google Sheets.
[05:36] So the workflow structure is our trigger is going to be a Gmail trigger which makes sense.
[05:40] And then it's going to be a Google Sheets appendero.
[05:43] So two nodes, one connection, very, very easy.
[05:46] So node one, it's going to be our Gmail trigger.
[05:49] That looks good.
[05:51] node two is going to be our Google Sheets.
[05:55] It's appending rows.
[05:56] It's going to add a row.
[06:01] Those are our suggested Google Sheet columns.
[06:06] Okay.
[06:07] This all looks good.
[06:08] And hit yes, auto accept.
[06:11] So now that we've approved the plan, we're going to move into phase two.
[06:16] So phase two is build mode.
[06:18] So cloud is going to create the actual workflow inside of NADN.
[06:21] Yeah, in like NADN.
[06:24] So here in a moment, we'll see a new workflow named probably something similar to what the
[06:29] prompt was.
[06:30] And then all the nodes, which in this case is two, are there and configured other than
[06:33] our credentials that will need to set up.
[06:36] It's going to show the workflow structure.
[06:37] And it's going to figure all the rest of the node settings properly.
[06:41] So here it says create the NADN workflow with Gmail trigger and Google Sheets nodes now.
[06:46] And it's got that checked off.
[06:47] Now it's going to validate the workflow and then auto fix any validation issues.
[06:52] Looks like it's already checked off all three of those.
[06:56] It's created and validated.
[06:57] Here's the summary.
[06:59] But it does say we need to set up the credentials, which is fine because cloud code cannot do
[07:04] that for us.
[07:05] But let's go and take a look at what it's built.
[07:07] So let me tab over to our NADN account, I'm going to refresh the page.
[07:13] There we go, updated just so now, monitor Gmail for urgent emails, and then arrow log to
[07:19] Google Sheets.
[07:20] Let's jump in and look.
[07:21] You should have two.
[07:22] This is exactly what it showed from the plan.
[07:24] We have a Gmail trigger, let's see what the, so every minute it's pulling to check for
[07:30] new emails, and then it's going to put it into a pending row for Google Sheets, and then
[07:38] because we don't have any credentials linked here, we have no documents to choose from.
[07:43] But it did all of that perfectly, like it was saying it would, but let's actually set up
[07:50] our credentials in there so we can give it a good test to see how well cloud code did.
[07:55] So the first one will set up, we'll start here on the trigger, which is Gmail, we double
[07:59] click to go into the node, we need to create a credential.
[08:03] So we'll click create new credential, leave the default recommended OAuth 2, down here you'll
[08:08] see sign in with Google, little box will pop up, and then you will choose which Gmail account
[08:15] or the only one if you only have one that you want to log in with, you'll click that,
[08:20] and then you'll have to validate, if you've not done it before, continue connection successful,
[08:26] it'll show green, and we're ready to go there, okay, so our little red error messages
[08:31] gone, we only have one left here, so Google Sheets, so we'll double click in here, exactly
[08:37] the same thing, create new credential, OAuth 2 is recommended, sign in with Google, it will
[08:42] pop up, you're going to choose the account you want to use for that, and then for this one
[08:47] you might have to select what you have access to, what you give it access to, I'll just
[08:53] select all, and hit continue, boom, another connection successful, and that is green,
[08:59] so the only thing left to do is to actually get a document with those columns and point
[09:07] this to that, all right, so I've created a brand new Google Sheet, and I have the five columns
[09:12] that Cloud Code recommended, which are date from subject snippet and ID, so once I've created
[09:19] that, and make sure you're creating this sheet in the same Google account that you verified,
[09:25] we go back to inade and now, we'll go into the Google Sheets node, you might have to close
[09:30] it and refresh, but if I click this, now I'll see there it is, inade and cloud test, and
[09:35] then that's the document, and then the sheet, it'll probably just be sheet one, because I
[09:40] only have one, now it's going to fetch all of our columns, there they are, date from subject
[09:46] snippet and ID, those are all ready to go, so the last thing we need to do to really test
[09:52] this is to get an email with urgent in the subject line, so I'm going to send an email to myself,
[09:58] I'm going to just type urgent as a subject line, test body, and I'll sign off with, and there,
[10:09] okay, so I'm going to send this to myself, we're going to give it just seconds inside inade
[10:15] and then we'll go ahead and execute to try to push that along, okay, so it did turn
[10:21] green there, and then we have an error with our Google Sheets, at least one value has to
[10:25] be added under values to send, so let's scroll down here and take a look at that, so now we're
[10:32] going to drag over some of the variables from the left and fill out these fields, that's
[10:36] what's giving us the error, so the from field, let's find the from, so it's from, we're going
[10:41] to drag it over there, okay, the subject line looks like it's right here, we're going to
[10:46] drag the subject over there, the snippet, where is the snippets, there it is right there,
[10:54] which is the body right or part of it, and then an ID, there's our Gmail ID for that email,
[11:03] and now let's find the date, there's an internal date here, you know, that'll be fine for
[11:09] right now, so boom, all of those are green, now if we execute this step, it should bring
[11:14] it over, and now it is indeed working, and you can see in JSON here it's got our from, subject
[11:21] snippet ID and date, and both are green, so Cloud Code did everything it needed to do on
[11:29] its side, the rest that was left to us was setting up our Gmail account, creating the document
[11:37] that things would be loaded into, and then running that test, so now if we go back to
[11:43] the cloud test document that I had, I'll just make these little bigger, you can in fact see
[11:48] that yeah, it brought everything over, just like it said it would, so our phase three would
[11:55] be troubleshoot, right, something's not working, here's the error message, so if you give that
[12:02] to Cloud Code, you can watch it diagnose issue and potentially fix the problem, always ask
[12:07] it for help to diagnose, as you've seen it has access to the tools, it knows how things
[12:12] are supposed to work, and if something's not working properly, chances are it can probably
[12:17] fix that, in our case luckily it was a very simple workflow, there was things that we needed
[12:23] to handle that Cloud Code wouldn't handle, but other than that we didn't have any issues
[12:26] to scroll around, now your exact output might not be my exact output, or the next
[12:31] person's output, right, so it's always good to read what Cloud's done, read when it prompts
[12:36] you to approve or deny something, and then ask it to troubleshoot if something does pop up.
[12:41] Phase four, the last thing would be optimized, right, so can we make this check five minutes
[12:47] instead of 15, I think it gave us a one minute check, can we add the sender's name to the Google
[12:54] sheet, and then Cloud will iterate and improve, so let's try one of these now, maybe we just
[12:58] haven't changed the time, no, we could easily go in and do that ourselves, but that's not
[13:04] the point, if we go into the Gmail trigger right now, it's at every minutes, let's go back
[13:11] to our VS Code, and let's say let's change the email polling to every five minutes, so just
[13:23] by talking to Cloud, it's going to make that change for us, which is literally just changing
[13:29] that drop down, so we'll hit yes, we can do that, so now it says it's done, the Gmail
[13:35] trigger node now pulls every five minutes instead of using the default intervals, so if we
[13:40] go back to our NADIN to confirm, I'll just refresh this workflow, just to be sure we go
[13:47] back into the trigger node, it is every X minutes and it's at 14 hour, so this is actually
[13:58] correct, so this is great, we can go back a phase to troubleshooting, and we can get
[14:04] this, there we go, if we just copy the issue that you see, if we click on this, we can copy
[14:11] well not all of it, copy the issue, it's given 14 hours, so I'm not sure what it's trying
[14:18] to do here, and that's okay, this is a great example, so I get an error message on the
[14:26] Gmail trigger node, and then we'll paste that, so now it's going to check the correct polling
[14:41] time format, it's going looking through its MCB documentation, now it's going to look at
[14:47] a real template to see how polling is configured in practice, so it's grabbing it from the template,
[14:57] so found it, the template uses mode every minute, let me check what valid nodes exist by looking
[15:03] at the schedule, okay, so now it's going to actually look at the drop down, it was trying
[15:08] to do something custom I guess, with the X minutes, but then there's the 14, so now I see
[15:14] the issue, Gmail triggers poll times only supports every minute in a custom mode with a C-ron
[15:20] expression, for every five minutes I'll use a C-ron expression, let me validate to confirm
[15:26] it's clean now, okay, so now it's validating, zero errors, so it validated for us, can you
[15:32] confirm the errors gone on your end, okay, let's go take a look, get out of here, I'm going
[15:37] to refresh, do my trigger, okay, so now it's switched this drop down to custom, and it's
[15:47] given this C-ron expression slash five, so there's no red error there, we can run the workflow
[15:59] which kind of bypasses every five minutes anyway, but because there's no red error, I
[16:04] think we're good to go, which is crazy, because there's all these other ones you could choose,
[16:13] but this is interesting to see a way that it did it, again, like how would you really have
[16:17] known that, right, so I think we're good to go there, all right, so this was a big one, just
[16:24] hopefully you can see just from these tiny examples that, like this is vibe coding, right,
[16:27] we're just explaining plain English, plain language to Claude, and it's outputting what
[16:35] we're expecting, we're not getting into the weeds of what node to use, we're just talking
[16:39] what we want the outcome to be, not the technical side.
