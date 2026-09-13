# Loom Transcript · BP_P2_Intro_to_Context_Engineering

**Source video ID:** aef4006627ee410ca9e1702c860b6a3f
**Loom URL:** https://www.loom.com/share/aef4006627ee410ca9e1702c860b6a3f
**Detected language:** en (probability 1.00)
**Duration:** 793.8s

---

[00:00] Hey guys, so I wanted to talk about context engineering, so I just made a YouTube video about this, which will be linked below in this sort of resource.
[00:10] But the reason I wanted to put it here before we jump into N&N, I don't want to get to technical here. I don't want to overwhelm.
[00:17] But this is going to be a really important kind of like mindset shift to have going into building things in N&N.
[00:26] So you know, this module we talked about stuff like data sources and transformation, we talked about integrating AI and like planning out your workflow.
[00:35] And so some of this stuff, you know, like we've got some visuals here to show what it may look like in N&N.
[00:40] And of course this PDF will also be linked down below.
[00:44] But some of this stuff, I'm not going to get too technical, like I said, but just the way we think about, you know, like when we're setting up our agents, like what is the end goal?
[00:53] I built over 200 AI animations and I'm just going to break down six kind of like context engineering lessons and don't be intimidated by the term engineering.
[01:02] Same thing as like prompt engineering. It's very, very simple engineering is just thinking about the way that we build it so that it's, you know, the most effective, right?
[01:10] So context engineering is the practice of feeding your AI agent the right information at the right time.
[01:16] While prompt engineering while prompt engineering focuses on crafting a single instruction, context engineering is about building systems that dynamically provide relevant information so the agent can make smart decisions.
[01:28] So the best analogy here is, you know, like what I have down here and I just I'd love it because I think it's just so applicable.
[01:35] Prompt engineering is basically like you study for the exam, you cram all week and you have to memorize everything.
[01:42] And then once you know, you go into that exam room to take the test, you have to do it all based on memory.
[01:49] So that would be like giving our agent basically no context or tools and making it cram and understand what it needs to do.
[01:56] And then we're just going to feed it tons of questions and expected to do everything right.
[01:59] It can, it will get things right, but not as accurately as if we had context engineering, which basically is like our cheat sheet.
[02:07] So you get a little note card that you take into the exam with you and now I can look at a question.
[02:11] I can say, okay, I don't remember this, but I know in my note card, I have this information.
[02:15] So I'm going to go find it and then I'm going to answer more accurately.
[02:18] So that's kind of what it is.
[02:20] And really it's something that you've probably already done or understand.
[02:23] And it just needs to be thought about a little bit deeper, which is giving your agent the access to different context.
[02:30] So what we have here is like what an NANA agent looks like, right?
[02:35] So we have a couple different things that I wanted to highlight here.
[02:38] The first one is the user input.
[02:40] So this is the dynamic question that it's going to be getting every single time.
[02:44] That feeds in as context.
[02:46] Then it has its instructions.
[02:48] So this is kind of where the prompt engineering comes into play.
[02:51] And this basically tells the agent, okay, here is what your role is, here's what you do.
[02:56] And here are the different tools you have access to to get more context.
[03:00] So based on the message coming in, I need to look in my memory real quick, which is context.
[03:05] I need to maybe look in my retrieve knowledge, super base, vector database.
[03:09] Maybe I need to look in my tool.
[03:11] Maybe I need to also understand the type of output that I need to give.
[03:15] So don't worry too much about like these actual physical pieces in NANN.
[03:19] Just think about the fact that when you have an agent, it should be able to access different things in order to get the right information.
[03:26] And that's just an example of what that could look like.
[03:30] So memory is kind of the first one we talked about.
[03:33] There are different types of memory in your AI agents.
[03:35] You've got working memory, which basically means for each query, the agent is going to have a log of like,
[03:41] here's what I'm going to do.
[03:42] And this is like the things I've done already.
[03:44] And that's on like an execution basis.
[03:46] So if you ask the agent to do something and it calls three different tools, it's going to remember what it's doing as it's running.
[03:52] But without short-term memory, as soon as that executions over, it forgets everything.
[03:56] Clean slate starts over.
[03:58] So short-term memory lets us basically look at recent conversations.
[04:01] So here's just a quick example down here where I'm having a conversation with my agent.
[04:06] I said, sorry if it's small. I said, hi, my name's Nate.
[04:09] It's at hey, Nate. How can I assist you?
[04:11] I said, I have a dog named workflow.
[04:13] That's a great name. How does workflow what kind of dog?
[04:15] I said, he is a gold retriever. What should we do this weekend?
[04:18] And then it tells me stuff because it remembers my name's Nate.
[04:21] And it remembers that I have a dog named workflow.
[04:24] But what happens here is this short-term memory basically works with a context window.
[04:29] So if we have a context window of three, here's our first message.
[04:33] Here's our second message. Here's our third message.
[04:35] If we tried to talk to our agent again, it would then lose this first message.
[04:39] And then it would keep one, two, and then whatever comes next.
[04:42] So it's just going to be the last three messages.
[04:45] You have the ability to make the context window more or less.
[04:48] Your trade off there is if you have a larger context window,
[04:51] you're going to be processing more conversations.
[04:54] And if you're processing more conversations that cost more tokens,
[04:58] so it costs you more money.
[05:00] At a high level, I just want you guys to understand how this stuff works.
[05:03] We don't have to get too technical now.
[05:06] I won't even touch on session ID stuff. That's basically just the ability for your agent to have
[05:11] different conversation windows and histories with different people.
[05:15] So in your contact, in your phone, you're texting Nate or having our conversation.
[05:21] And then you go to text, you know, your dad, and you and your dad have a conversation.
[05:26] And they're separate.
[05:28] So there's that, and then there's also long-term memory,
[05:30] which is basically more persistent information that survives across sessions.
[05:34] And this can be stored in multiple ways.
[05:36] It could be any user graph. It could be literally just in a Google Doc.
[05:39] It could be a vector store. It could just be your CRM.
[05:43] But the idea here is that long-term memory is something that gets processed every single run.
[05:48] And it's like the system prompts, maybe the agent just knows it,
[05:52] rather than having to go grab it. So that's like memory.
[05:56] Now we have where things get interesting with dynamic rag and tool calling,
[06:01] which basically means your agent gets your question,
[06:04] and it understands I don't know the answer, but I have this tool to go get the answer.
[06:09] So that's where it gets cool.
[06:10] And tools can be a vector database. It can be searching the web.
[06:13] It can be accessing a CRM. There's different ways to have a tool.
[06:17] So in here, I have like, you know, my example with the ultimate assistant.
[06:20] If I asked it to send an email, it knows I can send emails with my email agent tool.
[06:25] But, you know, Nate asked me to send an email to Michael Scott.
[06:30] But I don't know Michael Scott's contact information.
[06:33] What I can do is I can go right here to my contact agent.
[06:37] And that's how I can get that information.
[06:39] And then I can go send the email because now I have what I need.
[06:42] So without that context of knowing I have a contact agent that I can get that,
[06:46] it would never be able to send the email to my Scott.
[06:49] It would need an actual email.
[06:50] Or it would probably just make one up and then, you know, it doesn't go anywhere.
[06:55] So there's rag and memory.
[06:57] They're sorry, rag and tool calling.
[06:59] And then this kind of goes along with rag because I think a lot of people,
[07:02] and they think of rag, they think of vector search.
[07:05] And, you know, we've talked about an agent zero vector databases and what those are.
[07:09] I'm not going to dive too deep into here, but I'm just going to talk about.
[07:13] Rag isn't always vector database stuff, right?
[07:16] Because when you have stuff into a vector database, it gets chunked up into vectors.
[07:21] So we have we have a text here.
[07:24] Unless pretend this is a YouTube transcript.
[07:26] So I have a YouTube transcript and I chunk that up.
[07:29] So it has to go into three chunks because the YouTube videos too long to all be one chunk.
[07:33] Those chunks get processed.
[07:36] And once those are processed as an embedding, it gets put into the vector database based on the meaning of these chunks.
[07:43] So let's say this first chunk up here means it's a YouTube video where I'm talking about.
[07:50] AI agents.
[07:51] So it gets placed up here and any other chunks about AI agents will be placed near it.
[07:56] In this chunk, let's say I'm talking about perplexity.
[07:59] So it goes over here with other like web search chunks are, you know, based on the meaning.
[08:04] And then finally, you know, I'm talking about the school community.
[08:07] So down here is like community, right?
[08:09] So they're placed differently.
[08:11] But the issue is we don't know that these chunks relate to each other.
[08:16] We don't know they're coming from the same YouTube video.
[08:19] And that's why you can do stuff like metadata to just enrich the context of, you know, these chunks.
[08:24] We can say, okay, what title of the full video and what URL of the full video did they come from just to give more information about the vector.
[08:31] So metadata means data about data.
[08:35] So it's not in it's not in the chunk.
[08:38] It doesn't affect the meaning or the placement.
[08:40] But when we pull back the chunk, we can look at more stuff about it.
[08:43] So it's like, imagine you have a library of books.
[08:46] And you're reading different books.
[08:48] But none of them have metadata like when the book was written and who the author was.
[08:53] So otherwise you'd be searching all of your books in the library.
[08:56] But you just wouldn't know more about them.
[08:58] So we enrich it with metadata like, okay, this book was written by Charles Dickens.
[09:03] And it was written in 1990 or whatever.
[09:06] I don't know if that was even remotely accurate.
[09:08] But now we just have more information about the book, right?
[09:11] It doesn't change anything about like within the actual chapters of the book.
[09:16] Fifth one, we have summarization techniques.
[09:20] So essentially, like I said earlier, every time you process a token, that costs you more.
[09:26] If you're using a closed source open, if you're using like, you know, a closed source model,
[09:30] that's hosted in the cloud by someone else.
[09:32] If you're running stuff locally, it's free because it's running locally, right?
[09:37] So the idea is, if you can process less words, you're going to spend less money.
[09:45] So an example here is an AI agent that's searching through a super base vector database.
[09:49] And let's say it pulls back four chunks and each of those chunks have 500 words.
[09:53] It's then processing 2,000 words.
[09:56] What we could do is we could set up something like a flow to rather than process 500 words per chunk.
[10:02] We're going to have a different system extract, you know, with maybe a cheaper model,
[10:08] summarize the big chunks and just pull out the most important highlights.
[10:13] So this could turn from, you know, 2,000 words to 10 words or 20 words that are just the most important things that the eight main agent needs.
[10:22] So right now, if this looks confusing with like the tool calling and the sub workflow, don't worry about that.
[10:28] That's not what I'm trying to drive home.
[10:30] I'm just trying to drive home the mindset of making things shorter if possible to save money.
[10:38] And finally, the mindset, which is just kind of wrapping it all together of why I wanted to make this video for you guys before you get into building some stuff.
[10:47] So start with the end in mind.
[10:49] I know we talked about that a lot with process mapping and wire framing.
[10:53] And that is how you basically understand the type of queries and the type of questions your system would be handling in order to make your context better.
[11:02] So same thing with like an exam.
[11:05] You're making a cheat sheet.
[11:07] But if you didn't know what type of questions we're going to be on the exam, you wouldn't know how to make it good cheat sheet.
[11:13] A clean dynamic data pipeline.
[11:15] I'm not going to talk about that right now.
[11:17] It's just a little more technical data accuracy, of course, context windows, making stuff shorter if possible.
[11:25] And then specializations and other good one to talk about.
[11:28] When you do have different, when you have like different things you want to process with AI.
[11:34] Rather than sending everything into one AI model that you prompt, split it up into different, you know, specialized tasks like an assembly line.
[11:42] You know, if you're building a, a jack in the box, it's going to be way more efficient and probably a higher quality jack in the box.
[11:51] If you have one person doing the handle, one person making the spring, one person making the clown and one person making the box.
[11:59] And then they're basically just getting really, really good at their specific thing.
[12:03] You know, I could, if I got really good at making those springs, I could pump out 10 of them really quick compared to someone that would need to make spring handle box clown and then start from the beginning.
[12:14] You know, it's just like specialization with these AI workers that you can prompts better.
[12:18] They can become, you know, just you can refine that prompt over and over and they're focused on one thing rather than overwhelming them with multiple aspects.
[12:26] So that is what I want to talk about today. This PDF will be dropped down below.
[12:31] Once again, I'll have a full kind of, there's a full YouTube video where I do go over this kind of stuff and a little more depth.
[12:39] And in that YouTube video, what I do is I go over this Excalibur here where I'm kind of talking about the same things, right.
[12:46] And I have a little bit more pictures and more context about some stuff with N and N.
[12:50] But I'll also link that Excalibur in this post as well.
[12:53] If you do want to just go check it out, but it's kind of similar to this document here anyways.
[12:58] So yeah, appreciate you guys watching this one.
[13:03] And yeah, I'm excited to hop into like actually building some stuff now.
[13:06] And I think it's really important.
[13:07] We've set a good foundation.
[13:08] So let's go start building some stuff.
[13:10] So you guys in the community.
