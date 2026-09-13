# Loom Transcript · BP_AZ_Modern_AI_Understanding_AI_Agents

**Source video ID:** ea866e479959457392e4587a71fdd8f6
**Loom URL:** https://www.loom.com/share/ea866e479959457392e4587a71fdd8f6
**Detected language:** en (probability 1.00)
**Duration:** 729.1s

---

[00:01] All right, so this is the really fun stuff and probably what led you down the rabbit hole of joining this community
[00:08] And now why your YouTube feed is likely a ton of stuff about AI and AI agents is
[00:13] understanding AI agents and
[00:16] I wanted to just show here like this is the first YouTube video I posted and
[00:20] It was called how I wish someone explained AI agents to me as a beginner
[00:25] Because this is when I really started to understand like okay AI workflows
[00:29] This is where I first started, but then I saw this term going around everywhere and it was like the hype of the AI agents and
[00:35] Like the search term on on Google Trans is just like straight up
[00:41] But it's really important to understand what this what this actually means
[00:43] But also I think it's really important to understand that this is probably not the first place to start
[00:48] but anyways
[00:50] Understanding what is an AI agent it is an autonomous system that can make decisions and take actions based on input and context
[00:58] So unlike traditional AI workflows, which have like very predefined rules step one step two step three step four
[01:05] agents are more flexible and adaptive and they basically can take a problem
[01:09] They can understand what tools do I have how do I solve this problem?
[01:12] Let me make a plan and then actually take action to reach that end goal. So
[01:18] Let's say you have like five AI workflows that you've built out
[01:21] They're intelligent because they can take action within the parameters that you've set up and those five workflows
[01:28] Are now tools that you give access you give your agent access to so then when your agent faces a problem
[01:33] It says okay. I have these five workflows. I can use which one actually solves the problem I have at hand
[01:38] And then it will basically just like call on or activate or fire off data to that workflow and then it uses it so
[01:47] The reason why there was so much hype here was because if you really think about and like
[01:55] If we're stepping outside of just using like no code solutions at n8n
[01:59] What we have the ability to now do is create a remote employee so anything that you could hire a remote employee to do you could do with an AI agent
[02:09] Like just as really high-level make a broad blanket statement because
[02:15] With something like broad browser automation
[02:18] Robotic process automation whatever it is even if you don't have the API endpoints to access some sort of server to take out
[02:25] Action, you can basically program your mouse to move around and click on certain buttons. So that's I feel like a little bit of a ramble
[02:33] But that's why it's like it got so popular
[02:37] Because agents with their LLM chat model brains can do stuff like that
[02:42] Actually autonomously, but the value prop here was you know, we can build out these systems that can you know
[02:48] They have perfect memory because humans misremember things agents don't because they're only trained on what you give them
[02:53] They always follow instructions. Okay, maybe a bit of a hyperbole or an exaggeration because they can elucinate a little bit
[03:00] They may not do it right, but if you prompt them right they will basically be following those instructions to take action
[03:08] They're never going to sleep. That's true as long as you have your workflow is active and you have the compute resources
[03:13] You need and you have all your credentials plugged in and enough credits into your accounts to actually do stuff
[03:18] They'll never sleep. These systems can just work 24-7 and it is a hundred percent true
[03:23] It's going to cost a fraction of hiring a human when it comes to stuff like salaries and benefits
[03:28] asking for raises all this kind of stuff so
[03:32] The key components of an AI agent obviously we talked a lot about AI and large language models
[03:36] And this is what powers the entire AI agent because this is basically the brain
[03:41] So another video that I made was called how I teach a 10-year-old to build AI agents
[03:46] And I wanted to break down, you know, the actual architecture of what they look like so
[03:51] Here's the agent in this blue box and you can see inside the agent. We have a brain and we have instructions
[03:57] The instructions come in the form of a system prompt and the brain comes in the form of the LLM the large language model as well as some sort of memory
[04:04] whether that's short-term long-term or both and
[04:07] Then you give the agent access to different tools. So right here
[04:10] There's just one red circle, which is a tool, but you would have basically as many tools as you want and these can be API's
[04:16] Databases different functions sending emails accessing CRM
[04:21] Giving it the ability to actually do something and then you know what happens as you get an input
[04:27] Or you give an input to the agent the agent will use its brain to think it will look at it into its instructions
[04:33] It will use its tools. It will evaluate what it did and then it will send you back some sort of output
[04:38] That's like in a nutshell how it works and what it looks like so real-world analogy
[04:46] Brushing your teeth the reasoning is that you decide when and where to brush
[04:50] You use toothbrush and toothpaste to do so and then your memory is your preferences and your current status like have you already brushed today?
[04:58] You know like what what triggers you to brush and all this kind of stuff right so anyways how they work
[05:03] They recognize the input they determine the required tools they then use their memory and then they plan and execute and then output something back to you
[05:12] So you'll hear people talking about different types of agent frameworks and you know what we're doing is we're using
[05:18] NADN which in itself is not an agent
[05:21] Framework or an agentic framework. It is just the sort of the system that we're using to build out these agents in a no-code workflow builder
[05:28] But different frameworks you may hear
[05:31] Azure agent service
[05:35] Semantic kernel lane chain is probably the one you've heard the most and
[05:40] Basically just like a way for
[05:42] Code to talk to tools and like standardize the way that tool calling works really at like at the highest level and
[05:49] This is another golden rule thing. You don't have to know exactly how these work or the differences if you're focusing right now on like any
[05:56] Then work automation don't really worry about what's going on behind the scenes with these different frameworks
[06:01] You probably have heard you know, there's hugging face. There's crew AI was a big one that I heard of at first
[06:06] All this kind of stuff
[06:08] So any then and itself is not built on lane chain
[06:10] And you may have heard that before and I kind of used to think that it was
[06:14] But what it does is it offers lane chain integration through certain nodes so when we're
[06:20] Accessing certain like API calls are certain integrated or native NADN nodes to take to take action and something else
[06:27] That can be going through like the lane chain integration to standardize this request and actually like take action
[06:32] So the platform uses its own implementation of lane chains JavaScript framework while maintaining independence
[06:38] This allows users to combine lane chain functionality with NADN's visual UI and all of the app integrations
[06:46] And real quick before we wrapped up here. I wanted to talk about again
[06:51] AI workflows versus AI agents. So AI workflows predefined paths AI agents are responsive and autonomous in the way that they make decisions
[07:01] AI workflows have less autonomy because we're controlling
[07:05] the path
[07:06] AI agents have more autonomy because down here if you see like this agent has four tools
[07:11] An input could come in and we don't know if the agent's going to go tool 1, tool 2, tool 4 and then be done
[07:17] Or if it's going to go tool 4, tool 4, tool 4, tool 1 and then be done. So there's like an infinite amount of possibilities
[07:23] And it's non-deterministic
[07:25] But over here obviously there's less autonomy because it's basically input tool 1, LLM, tool 2, tool 3, output
[07:31] And then I'm sorry, this is kind of a small image, but
[07:34] Hopefully you can see what I'm talking about here
[07:37] the adaptability
[07:39] AI workflows are for repeatable stable predictable boring repetitive processes basically and that's why when we define some sort of standard operating procedure if we know
[07:49] These are the 10 steps and they happen in this order every time prime use case for an AI workflow
[07:54] But if we're looking at a standard operating procedure that okay, well if this happens then we could do this and then within that nested if we're going to have a different sort of logic
[08:02] Where it needs to be dynamic and really flexible and it's it's very
[08:09] Non-deterministic that's when you'd go for something like this where there's more of a brain and reasoning so an agent
[08:15] But anyways just in general like AI workflows are predictable and deterministic agents are unpredictable non deterministic
[08:23] I don't want to reiterate this because I think that's it's pretty clear by now, but tool calling
[08:28] Tool calling gives our agents the ability to
[08:32] Interact with some sort of external system so like I said when you would have chat to be to help you write an email
[08:38] And then you would then copy the email and paste it into your Gmail browser now with an agent
[08:43] It can basically write that email but also just copy and paste it and send it over because it's working directly with Gmail as a tool
[08:51] So the key concepts here are
[08:53] Co-creation or tool creation you define the function you define its purpose you define when to use it and you define like
[09:00] How you use it meaning what data do you send over or what parameters do you fill in?
[09:05] Tool binding as you connect that tool to the AI model that supports tool calling and what I mean by it supports tool calling is
[09:13] Chatchy BT40 great for tool calling but chatchy BT01 a reasoning model does not support function calling
[09:21] So most models do most reasoning models don't yet when reasoning models start to allow tool calling or more standardized
[09:29] Tool calling that's going to be super powerful because these reasoning models are probably going to be better at understanding
[09:35] Here's the problem I have here are the tools I have which ones do I use but now I can actually use them rather than just
[09:42] Making a plan it can actually take action
[09:44] Tool calling is when appropriate the model decides which tool to call and then passes data to that tool and then it's the tool execution
[09:52] Which means that they actually run that tool and use it and so this matters because
[09:57] It connects agents to real systems it actually makes them practical it extends them but beyond just natural language and actually to
[10:05] update something and it enables them to integrate deeply within your business logic your infrastructure your tech stack
[10:13] Just seamlessly working into your environment because they can actually like do things in them now same way a remote employee could do things in your environment as long as you have
[10:22] Given them credentials or permissions or authorization
[10:26] So just like an example of what that looks like in and in this is a customer support agent
[10:30] This is its brain GPT-40. It has two tools which are I have a vector store with
[10:37] Company data and I have a create draft in Gmail tool
[10:41] So what I'm going to do is I'm going to use my brain to think about it. I'm going to gather information based on the input
[10:46] I am going to create that draft and then I'm going to respond to the human and say I've created a draft
[10:53] These are a bit more complex, right, but this is the ultimate assistant and
[10:57] What you can do is you can start to have agents within agents
[11:00] So this is a ultimate assistant agent and as you can see down here
[11:03] It has an email agent a calendar agent a contact agent a content creator agent and so when it decides
[11:09] Okay, I need to send an email it's going to use its email agent
[11:11] And then what happens in the background is that email agent gets called on and it decides
[11:16] Okay, based on the user's request which one of my email tools do I use because I can get emails
[11:22] I can mark them as I'm read I can label them I can write a reply all this kind of stuff and so it has its options of tools down here
[11:28] And the reason I did it like this is because
[11:31] Let's say there's like eight email actions here. There's eight calendar actions eight contact actions
[11:36] Then you would just have this main agent hooked up to like 24 and or more tools and that would just be
[11:42] Tool confusion because there's just too many it would overwhelm the model and the agent
[11:47] So that is understanding a agents. We're starting to wrap up sort of this foundational course
[11:53] Hopefully you're getting a really good sense of like
[11:56] Practically how the stuff works and some of the stuff that goes on you know in the background of like setting up
[12:02] Setting yourself up to succeed when you actually start to build these systems. So see you guys in the next one
