# Loom Transcript · BP_AZ_RAG_Context_Windows

**Source video ID:** 728ba4c2cf1240b885119b2e7040e351
**Loom URL:** https://www.loom.com/share/728ba4c2cf1240b885119b2e7040e351
**Detected language:** en (probability 1.00)
**Duration:** 398.5s

---

[00:00] All right, so it's part of this vector database series something to understand would be context windows
[00:05] So this is going to be a quick one
[00:07] What is context window? It's basically just the amount of text that an AI model can remember and process at one time
[00:12] So it's kind of like their attention span or their sort of short-term working memory
[00:17] That is exactly what it is. So obviously a smaller one
[00:19] It's going to only be able to focus on a short passage of text and maintain that context of what it has previously read and then you know
[00:26] On the opposite side of things with a larger one. It's going to be able to analyze entire docs entire conversations and it can you know
[00:33] Remember the first thing that we said as well as what we're currently talking about
[00:37] enable
[00:38] Enable in order to sort of reference that and have its outputs be more accurate. It's it's answers be more accurate
[00:45] It's tool calling be more accurate all that kind of stuff. So
[00:48] If you were reading a book, but you could only see a few lines at a time a small context window means you might forget
[00:53] What happened earlier while large one allows you to read and remember more of the story
[00:58] Whether that's you know, you're doing a book report or whatever it is you'll be able to answer better. So
[01:03] How they work air models don't read the way that humans do so
[01:06] We we've talked about tokenization. They break everything into tokens
[01:10] So whether that's you know, your sentences get chunked up and split into tokens and that is how the window is measured in terms of these tokens that are sent over
[01:18] To you know, maybe open AI or to pine cone or whatever it is
[01:22] um
[01:23] Anyways, so rough estimate 1000 tokens. Let's say it's roughly 750 words, which is which is a page of text and
[01:32] This is just obviously how the AI processes books transcripts are multiple docs and that's why
[01:37] You know with the context window that that is small
[01:39] That's why we do the the process of rag and having to go retrieve stuff and retrieve chunks back because we can't read an entire book and
[01:47] Make an answer about that. We'd be able to retrieve relevant chunks in order to return what we're looking for so
[01:54] I made a video in the community about like where's rag right now?
[01:57] That'd be a good one to watch and then maybe come back to this one or just watch this that one after this anyways
[02:03] Gemini recently came out with a
[02:06] One million token
[02:09] Window for to a flash and as you can see like when this stuff all started started happening
[02:14] 3.5 turbo had 4,000 and it's been it's been increasing really quick like you know are our four O models and the ones that we're using right now are
[02:22] 128,000 200,000
[02:24] But then it jumped from 300,000 to a million which is pretty cool
[02:27] And so that video talks about like the significance of these in advancements and this technology and why it really matters but
[02:34] Wanted to show this link for the leaderboards as well as this link down here for hallucination rates
[02:40] Which as you can see as these models get more and more context the hallucination rate is going to continue to decrease
[02:45] Which is really cool because they're just gonna have more information. They're gonna have better reasoning ability to actually answer you
[02:51] And we are going to be able to have more trust in the fact that what they're saying is true because they've just had more text to actually scan through rather than pulling chunks so
[03:01] As becoming smarter and more useful because it's able to have more
[03:06] Context window which leads to being able to have more complex information complex queries
[03:12] Returned in a way where we didn't have to break it into smaller chunks
[03:15] so
[03:17] You know, we've already kind of talked about this but the four main things here of why these larger context window windows matter is that
[03:23] We can answer more complex questions. We can analyze longer conversations. We can process entire documents now without having to chunk them up into
[03:31] You know 50 pieces. We could just read a whole earnings report and one fell swoop and then we've got
[03:37] All of that turns into reducing hallucinations, which is the end goal when it comes to AI so
[03:43] But obviously with this kind of stuff where you're gonna have to take into consideration is the cost so more tokens is going to be more expensive
[03:50] Every model is a little different of course
[03:52] But you know when we when deep seek released and everyone was talking about you know, it's 97% cheaper or 27 times cheaper
[03:58] That was because of the input tokens and the output tokens
[04:01] So this is an open AI example where we can look at their pricing which ebd40
[04:06] For a million input tokens. It's two two bucks 50 cents and then for a million output tokens. It's going to be ten bucks
[04:14] Obviously things will change when you know these models are expanding their context windows and they're being coming cheaper and cheaper for the tokens
[04:20] Or you can even you know, they're open source so you can even run them locally
[04:23] All that kind of stuff right but it really just comes down to what's the use case here when do you need to use you know
[04:29] Models with huge context windows to save some money when do you need to use one a bigger one?
[04:35] Yeah, so just deciding between that kind of stuff right
[04:39] And then the final takeaways here like I said this one was going to be quick. I just wanted to throw out the idea of like what a context window is
[04:46] Determines how much information your AI can process at once
[04:50] The longer the larger the context window better memory, but also higher cost not always, but typically more tokens in
[04:57] More tokens out is going to be a higher cost and
[05:00] recent AI models Gemini, you know, this was literally a couple days ago where where I saw these videos about Gemini with a million
[05:07] Token context window. It's going to be able to you know pass in a full doc rather than having to grab relevant chunks from that document
[05:14] We're just going to make the aspect of rag more and more powerful and
[05:19] At the end of the day it comes comes down to when you're building these applications
[05:23] Understand the typical tokens you may be passing through understand your pricing sort of requirements here understand
[05:31] What you're looking for as far as latency and how how efficient does this need to be I mean I see you always want your things to be most efficient
[05:38] But I would say like sometimes a large large context window isn't always necessary
[05:43] So it's about figuring out when to use the right models and where and I know that there's so many models and then the stuff
[05:50] Moves really really quick. So I'd say vellum is a good resource. This is basically just like an AI leaderboard that always is
[05:56] Leaderboard comparison tool that's always being updated because you know
[06:01] A new one drops every day
[06:02] It seems like and they all have different strengths in summer open source some aren't somewhere made by Nvidia's most recent chips somewhere old chips
[06:09] You know some have a mixture of experts where it's not utilizing all of the parameter weights at one go and it's kind of sending it off where we need to
[06:17] Summer being fine tuned in different ways. So
[06:20] It's tough to stay up to date with all this kind of stuff, right?
[06:22] But it's all about sort of adapting and shifting to
[06:26] Currently, what's going on and so that's why I wanted to make that video about you know
[06:29] What where is rag right now in February because that's going to be different than where rag is in five months most likely
[06:35] So help this one helped thanks guys
