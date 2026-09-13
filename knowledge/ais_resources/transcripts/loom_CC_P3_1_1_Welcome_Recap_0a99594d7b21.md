# Loom Transcript · CC_P3_1.1_Welcome_Recap

**Source video ID:** 0a99594d7b21425ab39ae00d97ecea60
**Loom URL:** https://www.loom.com/share/0a99594d7b21425ab39ae00d97ecea60
**Detected language:** en (probability 1.00)
**Duration:** 283.1s

---

[00:05] Hey, everybody. Welcome back. This is phase three hosted
[00:08] Automations, which basically means your scripts will run on the internet without you.
[00:14] I hope you're super excited. Let's jump right in to see what exactly this means, what we're
[00:20] going to be covering, and then what you're going to be building.
[00:23] So so far you've done phase one where we got in it and workflows to be built using Cloud
[00:30] Code, and we manually triggered that. We told Cloud Code, hey, I would like to build a workflow.
[00:36] That does this, right? We set up, connected our NADN. We got the skills, we got the MCP,
[00:41] everything configured, and Cloud Code would build the workflows for us, and we got to keep talking
[00:47] to it that way. Phase two, you built some agentic workflows using the WAT, the WOT system,
[00:54] and you triggered those as a human locally to enable those.
[00:59] And phase three here, we're going to host the automations that we're building and have them scheduled
[01:05] or them triggered by an event, all right? So looking back at phase two, there's a limit with this.
[01:12] You can only scale as fast as you can show up, right? We all need sleep, we all need a vacation
[01:18] every now and then. So phase two is a great assistant when we asked for it.
[01:23] But we saw it to be present to engage, to enable, and that sort of thing.
[01:28] Phase three, our systems that will work while you sleep. So this is really exciting.
[01:33] I think this is, I think most people when you think of getting into the space and exploring
[01:38] automations in AI, this is kind of where your head goes, right? It's like what can happen
[01:43] that I don't need to worry about that's happening behind the scenes while I'm sleeping,
[01:48] while I'm on vacation, while I'm in the background. So let's take a look at what you're going to be building.
[01:53] So we're going to do two builds. Build one, we're going to build a scheduled research agent.
[01:58] It'll run every morning. Now you can change these later on. This is just what we're building for this phase three.
[02:04] But we're going to have it run every morning on a crunch schedule.
[02:08] It's going to research topic and then output to Google Sheets. Pretty straightforward.
[02:13] And there's zero human development involvement after the setup, which is pretty awesome.
[02:19] Build two. So first one is scheduled. Build two is going to be a web hook triggered, right?
[02:25] It's going to generate a report after it receives the web hook. And it's going to be delivered automatically.
[02:32] So again, it's none of this is rocket science, but we're taking those baby steps in showing how it's going to work in phase three.
[02:40] So there's a couple new players, couple new tools in the field here. One of them is trigger.dev.
[02:46] It's great. It does all of these things. So scheduling with the Cron.
[02:51] It'll handle our web hook triggers. It'll automatically retry if there's a fail.
[02:56] We've got lots of visibility with full trace logging and the failure alerts.
[03:01] There's no middleman needed because trigger.dev is going to handle everything for us in this case.
[03:06] Let's look at the other new stuff. So there's two officially new ones.
[03:11] GitHub is probably not new for you, but it's the first time we're introducing it in this series.
[03:16] But that's where your code is going to live in the cloud. We'll deep dive into each of these as we get further into the videos.
[03:22] So GitHub is one trigger.dev, which we've already kind of briefly touched on, but it's where all your tasks run, get triggered and get monitored.
[03:30] Now, modal is another one that's basically just like trigger.dev.
[03:34] But trigger.dev gives us a lot more visibility. I think it looks prettier.
[03:39] You'll learn that about me. I love a good branding and good UI. That sort of thing.
[03:44] Now, the big difference here is that trigger.dev runs on TypeScript instead of Python.
[03:51] So previously, we've been using Python. modal does run on Python. Nobody freak out because cloud can help us.
[03:58] We'll use cloud exactly the same way we have been, but we'll use cloud to help us do TypeScript.
[04:04] And it's like no difference, but we need to call out that trigger.dev runs on TypeScript.
[04:09] You'll see the TS files instead of Python. But we'll set up both of these from scratch before we build anything else.
[04:17] Okay. So key takeaways from this first video here.
[04:22] Both of these workflows are going to be built fresh and design developed from day one.
[04:28] Trigger.dev is going to handle the scheduling, the webhooks, the retries, the logging, the alerts, all of the good stuff.
[04:34] And then GitHub is just storing that, right? Storing the code. Trigger.dev. I'm going to run everything else.
[04:40] So hope you're super excited. Let's jump right in.
