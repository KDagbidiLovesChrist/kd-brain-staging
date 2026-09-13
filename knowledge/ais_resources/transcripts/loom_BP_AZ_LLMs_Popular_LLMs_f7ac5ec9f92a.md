# Loom Transcript · BP_AZ_LLMs_Popular_LLMs

**Source video ID:** f7ac5ec9f92a4337ae61b2147611fbe0
**Loom URL:** https://www.loom.com/share/f7ac5ec9f92a4337ae61b2147611fbe0
**Detected language:** en (probability 1.00)
**Duration:** 651.4s

---

[00:00] All right, so in this section, we're talking about popular LLMs, large amount of models.
[00:05] Because when you're just starting out or if you're working with clients, the space changes
[00:10] very quick.
[00:11] And so being able to understand the differences, the model families, why you might want to
[00:17] choose a certain model for a certain use case and a different model for a different use case
[00:21] is very important.
[00:22] So that's kind of what we're going to be diving into today.
[00:26] We've touched on tokens and stuff like that, but it's really important to understand.
[00:29] So besides the way that you actually break down a particular sentence and have your tokens,
[00:33] as you can see here, you need to think about it as far as like, this is basically my cost.
[00:38] So pricing is usually based on token usage.
[00:41] We also have context limits that are measured in tokens.
[00:44] And so being able to estimate this kind of stuff is really important for you internally
[00:47] or for your potential client stuff like that.
[00:51] And so just as a quick aside, if we go to OpenRouter, which is what I typically like to use for my
[00:57] NADN AI agents and automations, which you guys will all see as we get into different material
[01:02] here.
[01:03] But OpenRouter lets you connect your agents to pretty much all of the LLMs.
[01:09] So you can see the unified interface for LLMs.
[01:11] If I go to models, you can see we've got some of these which you may not recognize right
[01:16] away because it's got a ton.
[01:17] But anyways, if I come down here to series, we can see like GPC, Cloud, Gemini, which are in
[01:21] my mind kind of the top three proprietary closed source models.
[01:27] So let's just for now, click on GBT, right?
[01:29] And we have something like GPT 5 Pro.
[01:33] Now, if I click on this, you can already see we have 711 million tokens.
[01:38] We've got 400k context.
[01:40] And then we have this pricing information too.
[01:42] And so basically this is saying, let me find, okay, so 400,000, 400,000 context.
[01:47] That's basically telling us that this thing can process 400,000 tokens at once.
[01:52] And that's like its window of how much it can look at.
[01:54] So that's important to understand.
[01:57] We also have something like the input and the output tokens.
[01:59] And notice that these are charged differently.
[02:02] So on the input, which would be like us sending information to GPT 5 Pro.
[02:07] For every token of input or for every million token of input, that's $15.
[02:11] And then on the output, when it responds to us and it generates information for every million
[02:15] of those output tokens, it's $120.
[02:18] So it may sound expensive, but a million tokens is a ton of tokens.
[02:21] So 400,000 is still a really big context window.
[02:24] And these context windows are getting bigger and bigger every day.
[02:27] We're just really starting to change the way that the space works.
[02:29] So anyways, just wanted to show you guys that real quick.
[02:32] And that's why it matters, right?
[02:35] So we also have parameters.
[02:38] Parameters is kind of just like the size of the model.
[02:40] How the different weights and like the technical things that go into building that model itself.
[02:44] And I don't understand how that works.
[02:46] I don't understand the formulas.
[02:48] That's not what I'm trying to teach you guys.
[02:50] And I don't think you ever need to understand that.
[02:52] Just having the high level understanding of like, okay, a 7 billion parameter model is much
[02:56] smaller and likely faster and cheaper to host if it was like locally running than a large
[03:02] 671 billion parameter model, stuff like that.
[03:06] So we typically have two model types and we can really get granular.
[03:11] But the way I like to think about it is we've kind of got our standard elements and we've got
[03:13] our reasoning elements.
[03:16] Standards are typically going to be faster on the token by token.
[03:19] They're going to be things like your GPT 40, your clogged sonnets.
[03:22] Some people might argue that sonnet could be reasoning.
[03:25] There's kind of these hybrids.
[03:26] We've got stuff like Gemini Pro or Gemini Flash.
[03:30] And then like I said, general purpose tasks, maybe some agentic things, writing, QA summarization.
[03:36] And then we've got our heavier reasoning models.
[03:39] They typically take longer.
[03:40] If you've noticed in your chat GPT environment, you might have like, enable thinking or not.
[03:45] Or sometimes you ask in a complex question and it will say thinking and it will say thought
[03:48] for 40 seconds.
[03:50] But if you ask something simple like, hey, what's a definition of gravity, then it's going
[03:55] to be able to spit that out right away.
[03:57] So reasoning models, standard elements, and we'll talk a little bit about how you're able
[04:01] to tell the difference.
[04:03] They're usually slower but more accurate.
[04:04] They have more reasoning and thinking going on.
[04:07] So for things like complex problems or maybe some math and coding, sometimes like stuff
[04:11] like that.
[04:13] So now we have families.
[04:14] So OpenAI and Theropic and Google, those are kind of the three, like I said, the ones in
[04:19] my mind that are the best closed source proprietary models.
[04:24] With an OpenAI, we've got GPT models.
[04:26] So we've got GPT 4.0.
[04:27] We've got GPT 3.5.
[04:28] We've got GPT 5.
[04:31] Those are kind of the general purpose language models.
[04:34] And then we've got turbo models.
[04:35] So you've heard four turbo, three, one, five turbo, all these.
[04:38] These are typically a little bit cheaper and they're speed optimized versions of these GPT
[04:42] models.
[04:43] And then we've got the O series, which are literally their thinking models.
[04:47] I don't know why I said literally, they're their thinking models.
[04:49] So if you've got the O in front like GPT 03, 04, 03 mini, that's how you know from OpenAI
[04:55] that that's a reasoning model.
[04:57] So the reason why I didn't throw specific numbers in here is because to make this content
[05:02] a little bit more evergreen, by understanding the way that these families work, you will
[05:07] understand like what they are.
[05:08] So if GPT goes out and drops an O 10, we know that's a reasoning.
[05:13] If GPT drops a 10 mini, we know that's probably just a regular GPT.
[05:17] So that's what I wanted to lay out here.
[05:19] Andthropic is kind of similar, they've got their sonnet, which is kind of their general
[05:22] purpose.
[05:23] They've got their HIKU, which are the speed optimized versions.
[05:26] And usually these are the cheapest, the speed optimized ones.
[05:29] And then Opus, which are their kind of like deliberative thinking models.
[05:32] Now, sonnet, you're able to enable thinking and sometimes have it do some deeper thinking,
[05:37] which is why people might call it more of a hybrid reasoning.
[05:39] But as far as like being heavy and typically larger context, and from a cost perspective, Opus
[05:46] is their hard, hard reasoning and thinking models.
[05:50] And then with Google, we have Pro models, we have Flash models and we have Flash Lite.
[05:55] Honestly, I've never really used Flash Lite in practice, but I've used Flash a ton, super,
[05:59] super fast, cheapest and fastest that I've ever used and still very good.
[06:05] And then their Pro models is kind of their flagship thinking, but it's also very kind of general
[06:09] hybrid, I would say.
[06:11] But I just wanted to at least come in here and show you guys that sort of stuff.
[06:15] But it's not just these three models, right?
[06:16] These are like I said, I've said proprietary closed source models.
[06:20] Now there's other ways to think about it.
[06:21] So like Grok is also one of those closed source models, but we've got stuff like Met Islam,
[06:25] and we've got stuff like DeepSeek, which are the open source models.
[06:28] And there's more than just these when it comes to open source, but some of the ones that come to my mind.
[06:33] And we've talked a little bit about this, but essentially closed source means you can use it.
[06:38] It's being hosted on Grok's server or Google server or OpenAI server.
[06:42] It's closed off to them, and we can't see really the code and the prompts that are in there.
[06:47] But open source ones are a little bit more customizable.
[06:49] You're able to actually basically pull them in and host them on your local device.
[06:54] And you can basically alter how they work.
[06:56] So you can download a 236 billion parameter DeepSeek model onto your local machine.
[07:03] There's obviously a different considerations with how much RAM do you need?
[07:07] How much storage, all this kind of stuff, but that's not what this video is about.
[07:14] So yeah, we're going to stop it there for open source stuff.
[07:19] Anyways, when you start to think about cost saving, like I said, you've got this balance of
[07:26] for your task, how much power do you need, and how much speed do you need?
[07:31] Sometimes you don't need speed. Sometimes you do. Sometimes you need deep reasoning.
[07:33] Sometimes you don't. So it wouldn't make sense to have a deep reasoning model doing some basic
[07:37] like email classification and tagging, but it would make sense for having a reasoning model
[07:42] doing stuff like audits or helping create like proposals and strategies.
[07:47] And on the same level, it wouldn't make sense to have a flash model or a turbo model doing that deep
[07:52] reasoning. So trying to figure out, you know, when people ask me, what's your favorite chat model?
[07:56] Or, you know, what model do you like to use? It's, you can't make a blanket statement.
[08:00] I always kind of come back with a clarification question of, well, what's the use case?
[08:03] You know, how much context are we dealing with? Do we have any cost considerations or speed
[08:08] considerations? Things like that. There's ways that you can get into saving tokens. You can have it
[08:13] the only processing words that are the most important. You can be sending summaries rather than full
[08:19] text. There's ways to, you know, play with stuff like that. But at this video, which was going to be
[08:23] more of a high level introduction to these popular LLMs and how to think about them. That's what I
[08:28] wanted to talk about. And the last thing I wanted to show you guys is two cool tools, which I will link
[08:32] below. The first one is vellum LLM leaderboard. So this was last updated as of 21st of October. So
[08:39] the date of recording yesterday. And this will basically show you how these different models are
[08:44] comparing in stuff like math, reasoning, agentic coding. And this will help you kind of just add a
[08:50] glance, be able to look and see where the different models rank. And so right now you can see a GPT-5
[08:56] was one of the most recent models that have dropped. And it's doing really well on a lot of these
[09:00] benchmarks. We've got LAMMA over here, which is really good in tool use. And once again,
[09:05] this is Meta's model that can be open source. We've got some AWS model here too. We've got Gemini
[09:11] coming over really good here in the adaptive reasoning. So we've got speed. As you can see, latency,
[09:18] cheapness, cheapness, cost. And then you can actually compare models head to head. So like when you're
[09:24] at Best Buy and you're doing your head to head comparisons of two different laptops, it's like that.
[09:29] Context window is a consideration, cutoff date. Cutoff date, by the way, means how much knowledge is
[09:34] loaded into it when it was trained. So these models are trained on a bunch of data. Sometimes those
[09:38] CGBT say, hey, I don't know that because my cutoff date training data only goes back to November of 2022,
[09:44] stuff like that. Max output, latency, all this kind of stuff. And then you can just compare
[09:49] our models down here. And then LAMMA Reena is also similar. You can chat with models and you can have
[09:55] outputs of different ones. And you can see which answers you like best. You can also
[10:00] go to the leaderboard. And you can see how people are anonymously ranking these different models
[10:04] for different things. So there's an overview. We've got text. And my understanding is that people basically
[10:12] talk to these different models and then they rank them. But they don't know which one they're talking
[10:15] to. And then that's how they kind of get these votes as you can see. So Gemini 2.5 pro is a really good
[10:19] hybrid model. Like I said, we can also go to vision. And you can see what is the best of vision,
[10:24] text to image, image edit, searching. So these are just cool tools if you want to sort of get caught
[10:30] up on what the general population's thinking and what the latest benchmarks are revealing. So that's
[10:34] going to do it for this one. Hope you guys found this one insightful. As always, if you have any
[10:38] questions, feel free to drop a comment in the post, drop a comment in the community. We'll get back
[10:46] to you, shoot me DM, whatever it is. And yeah, I will see you guys around. Thanks everyone.
