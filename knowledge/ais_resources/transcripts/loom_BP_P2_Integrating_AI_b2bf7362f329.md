# Loom Transcript · BP_P2_Integrating_AI

**Source video ID:** b2bf7362f32942e0bd725fcb6f96d70c
**Loom URL:** https://www.loom.com/share/b2bf7362f32942e0bd725fcb6f96d70c
**Detected language:** en (probability 1.00)
**Duration:** 654.1s

---

[00:00] All right, so the fun stuff is integrating AI into these workflows and into our automations.
[00:07] And it takes these standard automations to a whole new level and it is, it's really
[00:10] cool stuff.
[00:11] And it's not too new, well, I guess AI automation is more new, but automation is obviously
[00:17] not too new.
[00:20] And I remember when I was working in automation and I pitched these AI elements to some people
[00:26] on my team and they were just completely mind blown.
[00:29] And I was really excited because I thought I was going to be doing AI automations at work
[00:34] until they told me like, you know, we can't.
[00:37] And I didn't understand why, I mean, I understood that financial data is sensitive, but I didn't
[00:42] truly get that like, you know, the data would be running through a model and there's just
[00:47] like a lot of exposure there, all that kind of stuff.
[00:50] But anyways, the AI capabilities in any then, there's multiple AI ways, there's multiple
[00:56] ways for us to integrate AI.
[00:58] The first one that probably comes to mind is through an AI agent, which enables us to
[01:03] feed in specific data and also system prompted in a specific way.
[01:08] And then we also have the ability to do things like, give it tools and have its structure,
[01:12] its output and connect a different LLM to it.
[01:17] Because with our AI agents, we can give it a chat model and that chat model can be in
[01:21] thropic's clawed models or can be llama or can be mistral or can be open AI.
[01:26] So we have the ability to choose when we're setting up an agent, which brain do we want
[01:29] to give it?
[01:30] There's lots of times when we want to do different ones depending on the use case, but we have
[01:33] the ability to choose which brain do we want to give it.
[01:39] Then we have just a standard like large language model that we can run things through and it's
[01:44] the exact same thing.
[01:45] So yeah, actually, I'm not even going to dive into that because it's the exact same thing
[01:50] as processing text with a large language model.
[01:52] Same exact thing as processing text with an AI agent.
[01:54] So I'm not going to get into that.
[01:59] But we also have things like vector databases because that basically uses like semantic search
[02:05] to, first of all, we send off a query to that vector database and then it semantically searches
[02:10] and pulls stuff back.
[02:12] So you may hear terms like quadrant, pine cone or super base which all offer vector databases.
[02:19] And so what I'm talking about in this video is more about like how do you identify the
[02:24] opportunities for AI integration.
[02:27] And based on the previous videos of mapping out these steps and talking about decision points,
[02:31] you may have a good idea, but the reason I wanted to dedicate a video towards this is because
[02:37] I've been guilty of it too, but a lot of people have forced AI into processes where it's
[02:42] not needed and all it's doing is going to waste you money and it's going to increase the
[02:46] latency of the automation and probably increase the inconsistency of the end result.
[02:54] So you're looking for opportunities for AI in your process maps and you're going to look
[02:59] for areas where you need text processing tasks, which could be content generation, summarization
[03:05] is a prime one, and then translation.
[03:08] Or maybe you need classification, so categorization, sentiment analysis or intent recognition.
[03:15] And if you can't do those things with code or filters, you need AI.
[03:20] In support, you need to analyze data and suggest actions, knowledge retrieval, we need
[03:25] to extract relevant info from large data sets using AI rather than like a SQL query.
[03:31] Or maybe you need AI to create that SQL query, which is another use case of AI.
[03:36] Or personalization, you want to tailor some sort of output based on a user context.
[03:40] So there's been those automated emails for years, right?
[03:45] Where you can automate them based on a placeholder or variables.
[03:49] So hey, customer's name, blah, blah, blah, blah, blah, blah, from person's name, excuse
[03:58] me.
[03:59] Sorry about that.
[04:03] Yeah, so like, emails could be automated with placeholders.
[04:10] But if you want to automate personalized emails, that's when we need AI.
[04:15] So quick and scale draw diagram down here of a rule based or an AI powered decision point.
[04:20] And coming data for rule based, we're basically saying is X greater than 10.
[04:23] I think I did this example earlier, but if it is greater than 10, we're going to go this
[04:27] way.
[04:28] And if it's less than 10, we're going to go this way.
[04:30] And that's a simple filter.
[04:33] But now we need to analyze the actual content of an email and say, is it complaint billing
[04:37] or promotion?
[04:39] That's when we need AI.
[04:42] So to map these AI component requirements, what's the capability?
[04:46] What is AI doing?
[04:48] What is the input context?
[04:49] What information does AI need to make a decision?
[04:54] Output expectations, what type of decision does the AI make or like, what does that decision
[04:58] action look like?
[05:00] Is that just branching or is that outputting a different type of content?
[05:04] Integration points, where do we connect AI in or just AI connect to any tools?
[05:09] And then fallback procedures, of course, is how to handle these AI errors.
[05:14] So practical example, content, moderation, workflow, hopefully these practical examples are helpful
[05:19] to paint a picture, but maybe it's just like, I'm saying the same things over and over.
[05:25] But we have a trigger.
[05:26] So we're getting it from a website form.
[05:28] We're feeding in text, author ID, and timestamp to an AI component.
[05:32] And it's going to use that to classify this content.
[05:35] So a text classifier, text classifier node, we're going to give it the full text.
[05:40] We're going to tell it how to output things, which is going to be a classification.
[05:43] And we're basically saying, okay, you're going to read this and you're going to output
[05:45] either safe, unsafe, or review.
[05:49] And based on that output, it'll go down to different branch.
[05:51] So we've talked about all this kind of stuff before.
[05:54] Then we would just define what happens for each branch.
[05:56] As you can see, there's two different sort of paths here.
[05:59] Or we have the, where's the manual view?
[06:03] Okay, right here.
[06:05] So there's AI component.
[06:07] Or we have the manual review.
[06:08] And then after those, we're basically doing the data update, which is restoring that decision
[06:12] somewhere with the following fields.
[06:15] And that is basically like a quick example of using AI to make a decision.
[06:18] But also we're looping back in human oversight if needed.
[06:23] So how do you get that process map?
[06:27] Now that you have the triggers, the nodes, the functions, the data retrievals, all that
[06:32] kind of stuff into something like n and n.
[06:36] So here's an example.
[06:37] We've got a trigger.
[06:38] And we would just kind of try to correlate that to some sort of node in n and n.
[06:41] So triggers a lot of times will be webhooks or schedules or events.
[06:48] Data retrieval, a lot of times will be an HTTP request to some sort of API.
[06:52] Or it will be a SQL query through to a database or a vector database.
[06:57] Or it will be an app-specific node where in your Gmail nodes, you can have like a get all
[07:02] or get emails or an airtap where you can have search air table or get records.
[07:06] Or in your CRM, you can say get records.
[07:09] That's how you're going to retrieve data is through those type of operations.
[07:13] Then you have data transformations, which usually go in the form of the function node or the
[07:17] code node.
[07:18] The edit fields are the set fields or you have summary nodes or you have sort nodes.
[07:24] That's how the other ways you can transform data.
[07:28] But typically transformations are going to happen within n and n.
[07:30] So we can use the native basic logic nodes.
[07:34] We don't have to send it outside of n and n to do something like a transformation typically.
[07:39] Decision points, we can use if, we can use switches, we can use filters, or we can use AI nodes.
[07:45] And then external systems is pretty similar to data retrieval, which is, you know, HTTP
[07:49] request to an API, a database or an app-specific node.
[07:53] And then of course with AI, we have lots of different options.
[07:55] We have agents, we have basic chains, we have message and model node, we have text classifier,
[08:00] we have all these things.
[08:05] But that's essentially when we're using AI, feeding in data, we're telling it what to do,
[08:10] and then it does something.
[08:12] So when it comes implementation planning, of course, we want to select the nodes and we want
[08:16] to understand the integrations and the tool stack or the text stack so that we can do that.
[08:20] For each of these nodes, we're probably going to need some sort of credential to actually
[08:23] get into that service.
[08:25] We're going to have a development sequence, meaning we have a logical build order most of
[08:29] the time.
[08:30] So modularization is breaking the workflow into smaller tasks and sub workflows.
[08:37] Maybe it's not even that.
[08:38] Maybe it's more like, we have this process and it's 30 steps.
[08:41] Let's break that process into tasks.
[08:43] And then we can sort of automate those tasks one of the time.
[08:46] And then we can combine them all together so it's easier to swallow.
[08:49] And then error handling.
[08:52] The best practices for ending an implementation is if there's templates, and by templates,
[08:57] I'm typically meaning modules or building blocks that you've already built out.
[09:03] Go ahead and leverage those.
[09:05] You want to test in chunks.
[09:06] So whenever I'm building, I think if you've ever seen step by step that I do, I'll usually
[09:11] get data into that trigger.
[09:14] And I'll pin the data in the trigger so that I can test step by step and I'll create the
[09:18] next node and move the data over and see if it works.
[09:21] And if it works, then I'll create another node and move the data over.
[09:24] And I'll just do that iteratively.
[09:26] I think that's pretty intuitive, but you don't want to build out the whole workflow and
[09:28] then hit run and then you're going to err on all the steps, right?
[09:32] So that's what I talk about.
[09:33] Pinning sample data.
[09:34] I'll show that when we get into NADN.
[09:36] But in the top right of most of the nodes, unless it's binary, binary is funky in NADN, you
[09:42] can hit the pin button in the top right.
[09:44] And this basically means I'm just going to keep the data here.
[09:46] And that's really useful for something like an API call or when your data retrieving.
[09:51] Because let's say something like tably, which is a web search API.
[09:55] I'm searching the web for tably and that costs me one credit.
[09:58] I can then just pin that data there and keep it there while I'm testing things so I can
[10:02] map my variables and do what I need to do with that data.
[10:05] And then every time I rerun it, I don't have to spend an API credit.
[10:08] So that's like why you can pin data.
[10:11] Clear naming.
[10:12] It's good to name it.
[10:14] It's good to label nodes with purpose, but also you can use the sticky notes in NADN.
[10:18] So you've been seeing that on my templates recently, I'm sure, where I'm labeling everything
[10:22] of what's happening in each process.
[10:23] And you can use sticky notes to keep yourself organized with different functions.
[10:28] And then that kind of goes along with document everything.
[10:31] So that you know what's going on in your workflows.
[10:34] You have them labeled, you have them in your right folders.
[10:36] And then if anyone needs to take over that workflow, they don't have to spend the whole time
[10:41] getting caught up with how it works.
[10:43] So that's kind of the integrating AI piece and I just wanted to touch on that quick and
[10:47] end up being 11 minutes, so it wasn't super quick.
[10:50] Hopefully that all makes sense and I'll see you guys in the next one.
