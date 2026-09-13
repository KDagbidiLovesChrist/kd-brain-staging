# Loom Transcript · CC_P1_2.2_Masterclass_Starting_the_Convo

**Source video ID:** 58f38b86c195485282e23e609e6eb21c
**Loom URL:** https://www.loom.com/share/58f38b86c195485282e23e609e6eb21c
**Detected language:** en (probability 1.00)
**Duration:** 779.4s

---

[00:00] All right, so let's start the masterclass.
[00:03] We're going to start the conversation with FLOAD
[00:05] to get this workflow started to be planned and then built.
[00:10] So with the setup, I mentioned this foe electronic store gadgets
[00:15] and more, we have two PDFs that are provided
[00:18] with this training with a policies.pdf,
[00:21] which has returned exchange policies and then FAQs,
[00:24] it's got a whole bunch of information.
[00:26] Let's take a look at those real quick,
[00:27] just so you have a brief understanding.
[00:29] So inside of a Google Drive here, I've got a policies PDF.
[00:34] We take a look at that.
[00:35] It's got shipping and delivery, refunds, warranty,
[00:38] billing, pricing, promotion, privacy, gift cards,
[00:41] inside FAQs, hey, I wish charged twice.
[00:45] Do you sell my info?
[00:46] How long is shipping?
[00:47] So it's just basic information for electronic stores.
[00:51] And electronics are great because most of us,
[00:53] no matter where we're from, can relate to something
[00:55] with electronics going wrong or warranties or shipping
[00:58] and that sort of thing.
[00:59] So this will be a good kind of baseline thing for us to try.
[01:03] So we've got two PDFs that we're going to use.
[01:06] All right, so our opening request, right?
[01:07] This is our very first prompt.
[01:09] We're going to give to Claude to start giving it
[01:12] the idea of what this workflow is of what we want to build.
[01:14] So let's go through this.
[01:16] I need to build a customer support agent
[01:18] for gadgets and more electronics.
[01:20] Cool.
[01:21] Read these two PDF documents I've uploaded
[01:24] and extract all important info about returns, repairs,
[01:27] warranties, exchanges, and store policies
[01:29] from these documents.
[01:31] Then build a workflow that monitors Gmail every 15 minutes,
[01:36] identifies if emails are questions about returns,
[01:39] repairs, warranties, or store policies.
[01:41] It searches the extracted PDF information
[01:44] for relevant answers and then creates a draft response
[01:47] in Gmail using the info found.
[01:50] So we've given it the expectation of what we want.
[01:55] And we didn't get any tech questions.
[01:58] We didn't get in the weeds.
[02:00] This is what we want in a very long run on sentence.
[02:04] So why does this work, right?
[02:06] It's a complete outcome, including the document processing.
[02:09] This is going to be the interesting part, right?
[02:11] I could have said, hey, build a vector store.
[02:13] But I want to see how Claude code is going
[02:15] to handle giving it these PDFs.
[02:17] Like, how is it going to decide to store this information?
[02:20] It's going to let it handle the extracting story and searching.
[02:24] It's going to reference the uploaded files directly
[02:26] because we're going to give it through the chat.
[02:28] And then it's one conversation that
[02:30] whole prompt for the entire solution.
[02:33] OK, so we're back in VS Code, that Claude code loaded,
[02:36] I'm going to go to plan mode.
[02:38] Remember, this is where you want to start when you're planning.
[02:40] I'm going to paste in that, I'd say long,
[02:44] but it's not that long of a prompt.
[02:46] I'm going to delete these extra quotes.
[02:49] OK, so we're in plan mode.
[02:52] We have what we wanted to do.
[02:55] There's another one.
[02:56] But the last thing I need to do, I need
[02:58] to upload the PDFs with this prompt.
[03:01] So to get the two PDF documents here
[03:04] to go with this prompt, really the best way to do this
[03:07] is to add those PDFs.
[03:10] To remember, we made that folder, set this up.
[03:13] Mine was called inade and test.
[03:14] You might have named it inade and workflows.
[03:17] Put those PDFs in that folder.
[03:19] You can see here, now on the left side,
[03:21] I can see both of those PDFs in my file lists here.
[03:27] So now what I can do here, I can actually
[03:29] add and then tag both PDFs right there.
[03:35] So now when I'm saying read these two PDF documents
[03:39] I've uploaded and tagging it, it knows which ones to use there.
[03:43] So with the prompt in place, the PDF documents
[03:48] we wanted to reference their tag.
[03:52] We can hit go.
[03:54] We need to make sure we're in plan mode.
[03:56] There we go.
[03:58] And we can hit submit and let's see what happens.
[04:02] So it's going to say, let me start by reading both PDF documents
[04:06] to understand the content, then explore
[04:08] how to build this workflow.
[04:10] So it's reading the FAQ's PDF and the policies PDF.
[04:14] So that's great.
[04:14] So we know it did get them from the way
[04:17] we connected them.
[04:19] It's extracted all the policy content from both PDFs.
[04:22] Let me explore the in and in nodes and patterns
[04:24] needed to build this workflow.
[04:26] It's exploring Gmail, it's exploring the AI agent nodes
[04:30] because we need AI inserted to determine
[04:33] if the email is tech support not.
[04:38] It's looking through the NCP get node.
[04:43] It's looking at AI workflow templates
[04:45] so can you similar things to pull pieces from?
[04:49] So while it's thinking and planning over there,
[04:51] let's go back and talk about what's going to happen next.
[04:54] So we've sent the prompt in.
[04:56] We need to think about what Claude's response
[04:59] and follow up questions could be.
[05:01] So for instance, some of them
[05:03] it might ask, do I want to extract all the information
[05:07] or specific sections?
[05:08] Again, this is just, these might be the question.
[05:11] We don't know what Claude is going to ask in this case.
[05:13] So how should I structure the vector store?
[05:17] Do you want the exact wording or summarize?
[05:20] And then for the workflow, what qualifies
[05:22] as a tech support question?
[05:25] Do you want to have a formal occasional tone?
[05:27] These are all things.
[05:28] We don't know.
[05:29] Let's see what we could expect from this.
[05:31] So let's go back to Claude and see what questions
[05:35] maybe it has for us right now.
[05:37] All right, so we have one question here.
[05:39] Which AI provider would you like to use
[05:41] for email classification and response generation?
[05:44] Very cool.
[05:47] We're going to do open AI.
[05:49] How should the workflow handle the FAQ policy knowledge base?
[05:54] Your documents are small around one page each.
[05:56] So two approaches work well.
[05:59] One, system prompt, which it's recommending,
[06:03] it would embed all the FAQ policy text directly
[06:07] into the AI agent system prompt.
[06:09] Simple as no extra infrastructure, perfect for small docs,
[06:12] like yours, or a vector store rag, full rag pipeline
[06:18] with embeddings, vector store retrieval, more complex,
[06:21] but scalable if you plan to add more documents later.
[06:25] So this brings up a great question, right?
[06:28] Because the system prompt in the text windows,
[06:34] while it's true, right, it is the simplest
[06:36] and it's great for the small documents.
[06:38] But if we needed to scale this for an actual company
[06:43] or implement it for something later on,
[06:45] we kind of stuck, right?
[06:48] Plus, it's a little more costly to do it
[06:53] from the context window, whereas if you're doing a vector store,
[06:58] it's going to search only the specific sections
[07:02] of way more documents in a more organized fashion.
[07:05] So let's decide which of these we want to do.
[07:10] I think for now, because we want it to be scalable
[07:14] and just take a step towards not the easiest,
[07:19] I'm curious to see what it's going to do with the vector store.
[07:22] And then the last question has forced,
[07:25] should emails that are not about returns, warranties,
[07:27] repairs, policies be handled differently?
[07:31] It tells we can skip them, only generate
[07:33] drafts for those support topics,
[07:35] which is kind of what we were going for.
[07:37] You can label and skip them or draft a generic reply.
[07:41] For now, we're going to skip them.
[07:43] Now that we have an answer to all of these,
[07:46] if you're going to go back and change,
[07:47] you can just click on the tab for that specific question
[07:50] and then change it.
[07:51] They don't actually get submitted until you're at the last one.
[07:54] And down here, you hit submit answers.
[07:56] So we've submitted those three questions that it had.
[07:59] Now it's going to go and reference the workflow
[08:02] based on our requests and see what it comes up with.
[08:07] All right, so I let Claude go for a little bit here.
[08:09] It looks like we're almost down.
[08:10] It's checklist that it had.
[08:13] It's researched the Gmail sugar and the node configurations.
[08:16] It's looking at AI, line chain node configurations
[08:19] for agents, vector store embeddings, text class fire.
[08:23] It's a research document loader and text splitters.
[08:27] So it's researching all of these things.
[08:29] And now we're at the final step.
[08:31] Design complete workflow architecture
[08:34] and write an implementation plan.
[08:35] So I'm imagining our next step is going to be
[08:38] reviewing the plan that it has to start building this workflow.
[08:43] So we'll give that just a couple more minutes.
[08:45] And then we'll come back, review the plan very well
[08:48] to make sure it's a good sound plan for the first pass.
[08:51] And then if it's all good, we'll push it through.
[08:55] Okay, so Claude has finished with its proposal.
[08:58] Let's scroll up and take a look at what's going on here.
[09:05] Okay, gather some more electronics customer support agent.
[09:10] So it's saying there's two workflows.
[09:13] Workflow one is the knowledge-based indexer.
[09:16] Once it runs, it'll rerun when documents change.
[09:20] Workflow two is an email support agent
[09:23] runs every 15 minutes via Gmail polling.
[09:26] Okay, so the workflow one is going to get the information
[09:30] into an in-memory vector store.
[09:33] Looks like with open-air embeddings,
[09:37] manual trigger, we have the two documents.
[09:43] Okay, so it's going to be a manual trigger
[09:49] to the documents to the vector store.
[09:56] Okay, workflow two, customer support email agent.
[10:01] We're going to have the Gmail trigger,
[10:04] text classifier open-air model or classification.
[10:09] Okay, the AI agent, this one's going to generate
[10:12] draft reply using the knowledge base.
[10:17] There's our vector store retrieving the relevant information
[10:22] and then creating a Gmail draft
[10:24] and then skipping non-relevant emails.
[10:27] Okay, so in theory, that looks good.
[10:33] Here, it's going to show us what the AI system prompt is.
[10:36] So this is going to be what the prompt is
[10:37] within the actual AI agent node.
[10:40] You're a fairly professional customer support agent
[10:42] for getting more electronics.
[10:44] Here's the information about your role tone, all of that.
[10:50] Here's more about the vector tool.
[10:54] Here's the credentials we're going to need Gmail
[10:57] and open AI API.
[11:01] Okay, and then it tells us how to verify and test.
[11:04] So now we have some options.
[11:05] We can yes, an auto accept or yes,
[11:08] and mainly approve the edits or no keep planning.
[11:12] And then we can also come down here
[11:13] until clock what to do instead.
[11:18] So I think for this, it looks good on first pass
[11:22] until we actually have the nodes in the workflow
[11:24] built to kind of see how it's piecing this together.
[11:27] It's kind of hard to say.
[11:28] So I'm going to go ahead for the sake of this challenge.
[11:31] Go ahead and accept the first one here.
[11:33] Yes, an auto accept.
[11:34] So now it's going to actually take the plan
[11:36] and start building everything inside of our inadein.
[11:41] So while it's generating here,
[11:42] something we do is I've clicked down here
[11:45] and we were in plan, right?
[11:47] But now I can go to bypass permissions.
[11:49] It's going to be the red outline with the red button.
[11:52] And now it's going to bypass any time
[11:55] and thinks it needs to ask me something for permission.
[11:57] It's just going to do it anyway.
[11:58] It's going to do what it needs to do to get the plan done.
[12:01] So I switched it to that so that this can just continue on
[12:04] without having to pull me.
[12:06] So while that's continuing to build,
[12:08] some other things to look at when you're ready
[12:11] to review these plans with Cloud Code.
[12:13] Is it going to extract the right information?
[12:16] That's something we're going to have to ask it
[12:18] and we'll do some testing.
[12:19] Is the vector store going to work?
[12:21] That's probably the biggest thing we need to test,
[12:24] especially since it's saying to do it in two workflows.
[12:29] We need to make sure that it's going to be able to pull
[12:32] in the email workflow from the other document
[12:36] and just with PDF workflow.
[12:38] So that's going to be interesting.
[12:40] Is the workflow a lot to correct?
[12:41] That's something, obviously, we're going to be testing.
[12:44] And then yeah, if it looks good, which for now,
[12:47] yeah, let's go through, but that's part of it.
[12:49] We're going to troubleshoot using Cloud Code.
[12:51] And then obviously we could have added other things
[12:54] so you can also do price matching.
[12:57] Add that info in there as well.
