# Loom Transcript · CC_P1_2.3_Masterclass_Building_the_Workflow

**Source video ID:** 55c2a8ac846b469594cf74b62b199a50
**Loom URL:** https://www.loom.com/share/55c2a8ac846b469594cf74b62b199a50
**Detected language:** en (probability 1.00)
**Duration:** 797.9s

---

[00:00] So Claude is developed the plan, we said yes, go ahead, and now it's currently building behind the scenes
[00:08] into our net account these workflows.
[00:13] And we're going to go back over and take a look and
[00:17] see how it's handling the document processing. Is this going to work or not?
[00:21] And then the workflow through the Gmail, is this going to be tech support?
[00:25] I'm really interested to see how it's going to actually pull the vector store information
[00:30] from the way we gave it to it.
[00:33] All right, so let's jump over, let's take a look at what we found.
[00:37] Okay, so Claude code has finished, and this is what it's saying.
[00:42] Now, workflow one, knowledge-based indexer, it's valid, but inactive, workflow two,
[00:48] customers for email agents, every 15 minutes, unread only, for many.
[00:54] It's going to route to an AI agent, which is going to create a draft.
[00:59] If it's not related, it skips.
[01:02] And down here, before activating, we need to configure credentials, so we need to configure our Gmail.
[01:09] We will need to configure an open AI API to use with the chat models and the embeddings.
[01:17] It's saying to run workflow one first, we'll execute it manually to populate the vector store
[01:22] with the knowledge-based, and then we'll activate workflow two, and it'll start pulling every 15
[01:28] minutes, and then we'll do some testing. So let's jump over to our inadein and see what these look
[01:35] like. All right, so in our inadein here, we can for sure see four minutes ago, two minutes ago,
[01:40] these two gadgets and more knowledge-based indexer, and a customer support email agent.
[01:45] So let's look at the knowledge-based indexer first. This is going to be the one that's going to
[01:51] load the documents. We'll just kind of move this out of the way here. So we have a manual trigger.
[02:00] Remember, a trigger is what starts the workflow, what needs to happen before the rest.
[02:06] Do that. So manual is when we literally just push this button to start it. Nothing else can
[02:11] happen to start this other than us pressing it. That's going into a code node, which it mentioned.
[02:16] Let's take a look at this. So this is, it looks like it's literally just put in the text from the
[02:28] documents, from its analysis into this code node. Interesting, okay? And then that's going to put it into
[02:38] a vector store. It's inserting documents. It gave it a memory key gadget more. So this is a way to
[02:49] classify the documents that are there, okay? So we have an error here because we have not
[02:57] linked our open-eye credentials yet. That's fine. Default data loader, JSON, and then this is our
[03:06] character splitter. Okay. So if I hit go, this will not work because we don't have our credentials
[03:13] set up for that yet, which is fine. So we'll go back out. I want to take a look at the other one.
[03:18] So the customer support email agent, let's, it's always fun seeing something created and you didn't
[03:27] do it. Like AI did this and it's just, it's just crazy. We'll move this over just so we can read
[03:34] everything. We have a good idea of what's going on. So our trigger for this one is the Gmail
[03:41] trigger, which we're all familiar with now. It's giving us an error because we don't have an account
[03:46] set up, but there we go. That's just been enabled. So Gmail trigger every 15 minutes, okay? Text
[03:57] classifier. So this is going to categorize as support, meaning relevant as a tech support email
[04:06] asking about returns, refunds, repairs, pricing, and promotion. So it listed all of the things, okay?
[04:14] And then if it's, it would be not relevant if it doesn't talk about these things, okay? So I mean,
[04:22] it's pretty straightforward. If it's not relevant, it's going to skip. So nothing happens.
[04:28] So you could have this do something. Remember to ask us, what do you want it to do if it's not
[04:33] tech support? You could still have it craft a different email. You could have you get notifications
[04:37] somewhere else, choices, yours there. If it is relevant, it's going to go to this AI agent here.
[04:44] And this is the prompt that it's given us. Okay, open this one. This is that one we read. Remember,
[04:55] you are a friendly professional customer support agent. Here's your role, there's your tone,
[05:00] format the email, and then sign off that. Okay. It's connected to the knowledge base here.
[05:12] And then we're using that same gadgets, more kb, which was the same from the previous one.
[05:17] This AI agent is powered by OpenAI's brain using chatGPT40. Okay, so let's go back. Now that we've
[05:33] taken a look at these, let's just do a test and see if it's going to work. So I need to go in here.
[05:40] I already have my OpenAI setup. We'll walk through how you're going to do that here in just a minute.
[05:46] But let's push the button, see what happens. So as things progress positively, without error,
[05:52] they're going to turn green all the way down. So now it's all just workflow executed successfully.
[05:59] And what does that mean? Well, let's look in here. On the left, it'll show everything that's happened
[06:06] previous to this node. And then on the right is the output. Once it's come through the node, which is the
[06:11] middle part. What is outputting here? So it looks like again, it's just taking our text documents
[06:21] from our code node and outputting this here. Okay, putting it out in JSON. Cool. So that all is green.
[06:30] And it's saying it's working. I can look here and I see the content coming over. So now if we go out
[06:37] to our customer support email agent, the way to test this would now to be send a text support email.
[06:48] So if we compose an email, I'll just send an email to myself. Help with warranty. Okay.
[06:59] I have a warranty question. And I've got a list of example questions that we will send to y'all
[07:06] here in the curriculum that will be good to test with this. Okay, we'll just do something simple
[07:14] like that. I'm going to send it to me. There we go. Now we'll go back here. We're going to so
[07:20] Gmail is waiting every 15 minutes. But in order to make that go faster, we're going to click execute.
[07:27] Okay, so we have our first error message. So it's error and sub node open a model classifier. I'm going to
[07:35] copy this and go ahead and open the node. See if it's going to say anything different. It doesn't look
[07:44] like it is. So we're going to take that message that we've copied here. Remember this node, which one
[07:55] is this one? This node's classifying if it's a relevant text support question or not. This isn't the
[08:02] way I would have done this. But it is Claude's first attempt to do this. So let's go back to Claude.
[08:08] Give it this error code and see what it comes up with for a solution. I'm getting an error. Where were we at?
[08:19] Text classify. So again, you just copy paste whatever the error was, explain where it was. And let's see
[08:30] what Claude comes up with to potentially fix that. I can tell us what's wrong, hopefully.
[08:36] Okay, so Claude finished its figuring out of what the error was saying it's likely a credential
[08:43] and model configuration issue. So down here it was thinking, I found the issue.
[08:52] The model property requires a certain format instead of a plain string. So it had model GPT-40 mini,
[09:00] but 1.3 expects mode, ID, value. So it's just the way things were listed. That again, it did. So now
[09:08] it said it fixed. The model now properly uses it. And it showed the before and after. Try running it again.
[09:15] So we'll go back. We'll give it a go. We're going to refresh the page actually just to be sure.
[09:22] Now we'll give it a go. We'll hit manual. Okay, so we got a different error this time. This time,
[09:30] the OpenA model classifier did go green. It was red last time. We're getting this
[09:36] error right here. So I'm going to copy all of this. It's failing to parse text.
[09:42] And it gives some line of code there. Okay, let's go back. Give it here.
[09:49] Getting another error. All right, sending that on. So now Claude is going to do exactly the same thing.
[10:01] It's going to figure out what it was doing. And so it looks like it already knows it's caused by
[10:06] API responses. That's enabled by default. Something with this default version 1.3 that seems to be
[10:16] kind of tricking right here. So now it says, try running it again. The classifier should parse
[10:20] correctly now. So we'll go back. We do need to refresh the page as we saw from before. So I will
[10:26] reload. There we go. Okay, we'll hit execute workflow. It did go green that time. So see, it gave us
[10:35] two errors. Claude, both times was able to fix. I didn't know what was going on. But Claude could
[10:42] look, could figure it out because that's all the information we gave it before. So let's zoom out
[10:46] just a bit. It did go green all the way through. But I remember what I said before is just because
[10:52] everything's green doesn't mean it necessarily succeeded with what our expectations should be.
[10:57] But let's really know by going to my drafts folder and check. Okay. So here's what I wrote. Remember,
[11:07] I have a warranty question. Can you write me back? It said, this is my draft. That is not sent yet.
[11:14] Thank you for reaching out for your warranty inquiry. At Gadget Simura, we offer the following
[11:19] policies. New items. These come with a one year manufacturer warranty in addition to 30-day
[11:24] replacement. Okay. Let's go check our documents. So one year manufacturer warranty. Okay.
[11:33] Where is that warranty? New items. One year manufacturer warranty, 30-day Gadget Hub replacement
[11:39] guarantee. Is that where we're at? Let's go. 30-day replacement guarantee. Okay.
[11:48] So it looks like it did pull everything correctly. Please note that the warranty is void of the product
[11:55] damage due to misuse. And then it's signed off right there. So I'm impressed. Wow. So there you
[12:03] can see that that's amazing. That's really cool. So now to do a full test, let's send an email.
[12:11] That's not relevant. It has nothing to do with tech support just to make sure that that's working
[12:18] properly as well. So we'll create a new email. I'll send it to myself one more time. Dinner tomorrow.
[12:27] Right. That's not tech support. Hey, still good for dinner tomorrow nights. Sign off Bob. I
[12:37] don't know. Send. Okay. So we'll go back to NADM. We're going to execute the workflow again. It's
[12:45] going to pull because we click the button. And there we go. So now because it wasn't relevant if we go
[12:54] in here, you can see, hey, so good for dinner tomorrow nights. That's going to tag it. It's not
[13:00] relevant, which means it comes down this bottom row, which it just dies right here. It stops. It
[13:05] doesn't continue on. We don't get a draft to dinner. Now we could change that, right? And have the draft
[13:13] be for any situation. But in this case, it worked great.
