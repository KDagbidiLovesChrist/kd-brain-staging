# Loom Transcript · BP_AZ_LLMs_Open_vs_Closed_Source

**Source video ID:** ddc2bb486de84f2682aaf1eb664a4ec7
**Loom URL:** https://www.loom.com/share/ddc2bb486de84f2682aaf1eb664a4ec7
**Detected language:** en (probability 1.00)
**Duration:** 711.4s

---

[00:00] Okay, so I'm hopping right off that last one talking about open source versus closed source models
[00:06] Hopefully, you know, it's kind of windy in my windows right here. So hopefully you guys can't hear that I I just adjusted this this mic
[00:13] I got and now it's like facing me correctly someone on my YouTube video was like, hey, that's not how you should be talking into that mic and I was like
[00:21] I had no idea
[00:22] But anyways open source first closed source models
[00:26] What is the difference here and I kind of alluded to it in that last video open source versus closed source is a good thing to understand in general
[00:33] Not just when it comes to models because that's like it's gonna be something you hear a ton like that's one of the biggest value props between like
[00:39] I should I use maker and it in and it in as open source and so you can self-host it. It's gonna be cheaper. You can run it
[00:46] you know
[00:47] basically locally and privately and
[00:50] Make and zap your close source so you can't you don't have that ability. So anyways
[00:56] What is a closed source LLM these are proprietary models developed in private by these companies?
[01:01] So Google is developing their Gemini models in private
[01:05] They're in control of their training data their weights and the code and that's not shared publicly with all of us consumers
[01:11] Same thing with open AI and a topic which are kind of like I would say the three main leading popular closed source
[01:17] models right now
[01:18] So the way that we access those is
[01:21] either
[01:23] In our browser and we go to trash abt or we go to Anthropic or we go to Google Gemini Studio and we talked to those models
[01:30] And so like behind the scenes there's like some sort of system prompting going on and we choose which model we want to talk to and
[01:35] That's like the data is being sent over to their server basically
[01:39] But in something like an end-to-end we'll have the chat model that's plugged into the AI agent
[01:43] So I'm sure you guys all know what I'm talking about that's where we choose
[01:46] Which model we want to access and so if we're accessing these closed source models
[01:51] We're doing that basically sending an API call to that model and then it's coming back with some sort of response
[01:55] We're sending over our input tokens
[01:57] It's thinking and then it sends back some output tokens and that data is going past externally
[02:03] To that third-party API, which would be Google Anthropic or open AI
[02:08] So they are basically in full control of like our data and what we're sending over so it's tightly managed by the organization that developed that specific model and
[02:16] The advantages of using these closed source models first of all
[02:20] They have spent tons and tons and tons of billions of dollars on the research and development that go into training these models and
[02:27] Kind of optimizing them
[02:29] So we're accessing state-of-the-art capabilities before the open source alternatives catch up because
[02:35] Typically the open source alternatives are just not as powerful and so if you guys remember when deep-seek dropped
[02:40] And it was an open source model and it was just like insane and it was cheaper and all this kind of stuff
[02:45] That's why it took the world by storm because it was using like less or
[02:50] Older Nvidia chips than like open AI was and it was doing everything for cheaper all of its research and training for cheaper and then offering it to the public for cheaper as well
[02:58] So that's why everyone was freaking out
[03:00] Because you also have the ability to host it privately and it was kind of insane
[03:04] So there's that dedicated support so like the whole server infrastructure and the whole uptime of that model is on
[03:12] that models
[03:14] Side like it's their responsibility to be stable patch things update things they have their regulatory compliance in their hands and then like any technical assistance we need
[03:25] Managed infrastructure so we don't need to worry about okay like if I want to have access to this large language model
[03:31] How much RAM do I need what CPUs do I need what GPUs do I need that's not my area of expertise so don't ask me questions about that
[03:37] But that's exactly why like I don't want to worry about that right now
[03:40] So I'm not going to be hosting all these huge 214 billion parameter models on my PC and start a fire in my room
[03:47] Because I don't have enough stuff allocated and that probably wouldn't happen, but
[03:51] you get the point right
[03:54] And the automatic scaling and performance optimization that's great right so it's all there
[03:58] And then obviously the drawback keep in mind is well, I guess we'll get into the disadvantages town here, but then we've got quality assurance
[04:05] um
[04:07] Better alignment with human values rigorous testing and evaluation and reduce reduced risk of harmful outputs
[04:14] But now moving into some of the disadvantages of these closed source models
[04:18] And when you hear like the local AI package or whatever it is
[04:21] It's usually to get rid of these disadvantages, right? So the first one is limited control and customization
[04:27] Because you can't modify or sort of like deeply tailor these models now you do have the ability to like fine tune a model
[04:33] Which is basically different. You're kind of just feeding in like some some data to train it on
[04:38] Not something that I like I would say that I specialize in though
[04:41] The way that we go about fine tuning most of times and in any in any YouTube video you've seen for me
[04:47] We're fine tuning those models by giving it a system prompt and by giving it
[04:51] Rag access to certain data to use to take action or to create its responses
[04:57] um
[04:58] So because of that because we're using these closed source models
[05:01] We have to just accept that whatever the provider is giving us as far as the default behavior
[05:05] We just have to accept that luckily
[05:07] There's a tons of different models within the model family typically so we can kind of pick and choose
[05:12] But we have to accept what happened on
[05:16] Sort of sorry not on what happened
[05:19] Under the hood of that model
[05:22] Before it was given to us
[05:24] So obviously higher costs when you're running something locally it can essentially be free besides the compute costs and like what you need to actually run it
[05:31] But we're paying every single time you're hitting that API we're paying
[05:36] So it's either going to be a subscription like you're 20 bucks a month for your chat jbt plus
[05:39] Or it's going to be every API call you're making from any then
[05:43] There's going to be the input and output tokens associated with that API call which you get built on and at scale
[05:49] This can obviously become expensive if you're running the automation a thousand times a day and not only are you just running the automation a thousand times a day
[05:57] But you're having it output full emails or full content for you
[06:01] That obviously is going to increase your output token
[06:03] cost
[06:07] Yeah, so then the third one and probably one of the biggest ones as far as conversation is like the privacy and date concerns
[06:13] So if you're working with you know any sort of
[06:16] PII
[06:18] You don't want to be sending that through an open AI model
[06:21] um
[06:22] Financial information healthcare information
[06:25] Part of the reason why so far at the agency we haven't really like worked with like your healthcare
[06:30] Because of all those regulations
[06:32] but um
[06:34] There can just be a lot of compliance hurdles and regulated industries
[06:38] So that's actually you know part of the main reason why I ended up leaving my job
[06:41] So I was at Goldman Sachs and you know lots of financial data
[06:46] I wanted to start of sort of implement this AI stuff. I had just seen so many gaps like even this simple as
[06:53] Not having a meeting AI note taker
[06:55] Because I was the one having to send out these meeting notes and take notes during the meeting
[06:59] And I was like this is just a major waste of time and I can't focus and share ideas in this meeting because I'm just kind of focused on like
[07:05] What the actions items are for everyone
[07:08] um
[07:09] But it's because they would need their own model and they need to train it and dedicate a lot of resources towards that
[07:15] In order to comfortably have like all of the companies information and meeting information and and client information
[07:22] Go through a model and then dependency risks um vulnerable to pricing or policy changes
[07:29] Limited fallback if the service is discontinued and then no control over feature updates or model access
[07:34] But now when we get down here to open source LLM
[07:38] Which the main one that comes to my mind right away is llama and deep seek
[07:43] Models will publicly or sorry these are models with publicly available weights. So
[07:48] They'll show kind of like their training methods and we can download them modify them and deploy them pretty much anywhere locally
[07:54] um
[07:55] We have full freedom to customize retrain and deploy as needed and so here they're kind of the main advantages
[08:00] Of course, which kind of almost like exactly counter these disadvantages up here which are complete control
[08:06] Cost efficiency so you can run like a model for free
[08:09] Privacy and security you know everything staying on your own infrastructure no third party exposure
[08:14] And then of course you have your own innovation where you can sort of iterate on top of what's being going on
[08:20] um in the community or what you want to do with that model
[08:23] That sort of stuff
[08:24] But the disadvantages of course are the technical requirements. You need compute resources
[08:30] GPUs if you want to do like Kubernetes clustering in order to actually host this stuff and scale up
[08:35] Optimally and dedicate resources towards it
[08:37] Most of that was just like stuff I heard I don't specialize in that infrastructure
[08:42] But also you need to maintain all this kind of stuff
[08:45] So a skilled team to deploy and maintain you need like a dev ops team in case any of this stuff shuts down
[08:50] That's probably something where it's like
[08:53] We need someone to help fix this ASAP if all of our models are down or all of our workflows are down because our local local model is down
[09:01] So performance gap it also may lag behind the state of the art proprietary models because
[09:06] They're typically just trained on fewer resources and they're smaller or even less fine-tuned
[09:10] You have limitations with support because you don't have a third-party vendor who's kind of like managing
[09:15] Billions of people running this API. It's just kind of all on you
[09:19] And then safety and alignment challenges meaning you must manually implement these safety filters and guardrails
[09:24] And there's risk of misuse if and properly secured or customized
[09:29] So when it comes to making the choice
[09:31] It really depends on the use case
[09:33] So open source obviously offers more flexibility
[09:36] Close source is going to win at most of these general applications straight out of the box quick wins
[09:42] Let me do some stuff like that
[09:43] Resource availability
[09:45] Technical talent. Do you have the internal expertise in house already? Would you need to hire people to help you
[09:51] Run this stuff locally at scale with the infrastructure look like and then what does your budget look like obviously close source over time
[09:59] May cost more open source is gonna be more upfront because you have to get probably a lot of the stuff to actually host and run this this
[10:06] This model and then when it comes to strategic priorities
[10:10] Is it control or convenience
[10:13] What is the speed of the innovation you're looking to go at and then of course your vendor strategy
[10:18] But I have seen that a lot of a lot of times you can sort of use a hybrid approach like maybe there's just
[10:24] A lot of those general purpose tasks are fine
[10:26] And you want to get like these summaries and you want to get this stuff categorized and sent out and automatically like you know personalized outreach
[10:33] But
[10:34] Maybe you want to go open source when you're actually like loading in this customer data
[10:38] In order to I don't know like sync your CRMs or
[10:42] Financial data to do financial reports for your your clients or for your vendors or internally
[10:49] So that option obviously allows for flexibility and cost optimization
[10:53] Depending on the use case and a hybrid approach in general it seems to be
[10:58] In automation in general hybrid approach typically works really well
[11:01] Just because you have to understand like the pros and cons of all your different tools all your different options and when to use each one
[11:07] um
[11:07] So yeah, I hope that that painted a good picture as far as like in general what open source versus close source means and when you know
[11:13] What are the advantages there
[11:16] But specifically when it comes to models and understanding a little bit about which ones are which
[11:21] Probably most of the stuff that you've been doing at this point with AI has been the state of the art closed source models because that's like
[11:28] What we're most seeing and what most people are using especially if they're not deep into the weeds of like AI automation and and using AI
[11:35] Practically and they're kind of just playing around with the stuff
[11:37] It's probably anthropic and opening eye
[11:40] Google's obviously been dropping a ton of great stuff lately for free which has been insane but
[11:46] Yeah, hopefully that one helps paint a better picture in your guys's mind. I'll see you in the next one
