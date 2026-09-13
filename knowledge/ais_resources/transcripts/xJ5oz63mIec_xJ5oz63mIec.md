# YouTube Transcript — xJ5oz63mIec

**Video ID:** xJ5oz63mIec
**Source:** https://www.youtube.com/watch?v=xJ5oz63mIec

---

[00:00] If you've been using Cloud for a while,
[00:01] you've probably built a lot of skills
[00:02] and a lot of agents. So, today I'm going
[00:03] to talk about three different simple
[00:05] ways to actually deploy those agents so
[00:06] that they run while you sleep. So, I
[00:08] don't want to waste any time, let's just
[00:09] get straight into today's video. Okay,
[00:11] so before we get into the different
[00:12] methods, let me just paint you a picture
[00:14] here. There's kind of two different
[00:15] things that we're going to be looking at
[00:17] because the different ways that you
[00:18] deploy your agents have different pros
[00:20] and cons. So, here's kind of like the
[00:22] slider we're looking at. The first thing
[00:24] is where does it actually run? Does this
[00:25] run on your machine and is it dependent
[00:27] on your machine staying on or is it
[00:30] running somewhere on the cloud, whether
[00:31] that's like Anthropic's cloud or your
[00:33] own sort of cloud environment, modal,
[00:35] trigger, VPS, whatever it may be. And
[00:37] then on the vertical here, we basically
[00:39] have how deterministic is this thing? Is
[00:41] this the full agentic autonomous agent
[00:43] loop or is this more of a script that
[00:45] just runs basically the same way every
[00:47] time and there's not like that
[00:49] autonomous decision-making magic agent.
[00:53] So, as I'm breaking down these different
[00:54] methods, I will explain based on this
[00:56] method, where does it sit on this scale?
[00:58] Because the truth is, there's not one
[00:59] best way to deploy an automation. It
[01:01] depends on the type of automation. So,
[01:03] here is kind of a quick breakdown that
[01:04] we're going to be coming back to
[01:06] throughout the video, so don't feel like
[01:07] you need to absorb all of this right
[01:08] now. But for each of these methods,
[01:10] we're going to be looking at where it
[01:11] actually runs. We're going to be looking
[01:13] at the WAT framework that I've talked
[01:14] about, so workflow, agent, tools, and
[01:17] what's actually getting deployed and
[01:18] what's not. We'll be looking at if your
[01:20] computer needs to be on and if your
[01:21] session needs to be on, so I will break
[01:22] all of this down. It's going to be
[01:23] super, super simple. Okay, so method
[01:25] number one is just setting up a loop,
[01:27] which I think is a super cool way to
[01:29] just like very quickly deploy an
[01:31] automation. Basically, the idea is you
[01:33] ask Cloud Code to run a loop and do X,
[01:35] Y, and Z in the loop. So, basically,
[01:37] it'll fire off every 10 minutes or so,
[01:39] it'll run the skill, it'll run the
[01:40] automation, execute what it needs to,
[01:42] and then it will stop. And then, in 10
[01:44] more minutes, it will just fire up again
[01:46] and it will loop through that process
[01:47] until you either tell it to stop or it's
[01:49] hit its limit. So, how does this
[01:50] actually work under the hood? Cloud Code
[01:52] has three different tools for this sort
[01:55] of thing, which is called cron create,
[01:57] cron list, and cron delete. And if
[01:59] you've ever heard me or other people in
[02:00] the AI space say cron, that just
[02:02] basically means a scheduled task. A cron
[02:04] is like what time it fires off at. So,
[02:07] saying that you're going to set up a
[02:07] cron is basically like I'm just going to
[02:09] set up a scheduled automation. And the
[02:10] scheduler is actually internal to the
[02:12] cloud code process. And what's really
[02:14] cool is that all of these crons that you
[02:16] might set up or these loops are
[02:17] session-scoped. So, if you're working in
[02:19] five different sessions, you know, five
[02:20] different terminals or five different
[02:22] tabs in your desktop app, then each one
[02:25] of those individual sessions can have
[02:26] their own loops, and they don't
[02:27] interfere with each other. Unless
[02:29] they're all like writing to the same
[02:30] file or something, which in that case
[02:31] they would, but they're session-scoped.
[02:33] So, you can run these in the cloud
[02:35] desktop app or in the terminal, which is
[02:37] pretty cool. The terminal does give you
[02:38] a few extra things for some reason,
[02:41] which I will explain, but for now let me
[02:43] just show you how easy this is because
[02:44] you don't actually have to remember
[02:45] syntax of like how you do like a slash
[02:47] loop and how you, you know, explain how
[02:49] this works. You can see you can
[02:51] obviously do the slash loop and then
[02:52] tell it to do something every 10 minutes
[02:54] or so. Or you can just use natural
[02:56] language. So, I can say, "Hey, can you
[02:57] just go ahead and set up a loop for
[02:59] every 10 minutes to remind me to take
[03:00] out the trash?"
[03:02] So, I shoot that off, and now you can
[03:03] see it's going to use a specific tool
[03:05] and a specific skill in order to set up
[03:07] that loop. And right now I'm showing the
[03:08] desktop app. Like I said, I will bounce
[03:10] over to the terminal in just a sec. You
[03:12] can see that it just ran a skill called
[03:14] slash loop, and now it's using its tool
[03:16] search, and it's going to have to use
[03:17] the tool that we talked about, which was
[03:18] called cron create, as you can see right
[03:20] there. And this is basically just like
[03:22] cron syntax, and you don't have to
[03:24] understand how to read it because it
[03:25] will explain it to you in natural
[03:26] language. Now, what's kind of cool about
[03:28] this and interesting is that when you
[03:30] create a cron and you say every 10
[03:31] minutes, that doesn't mean the first
[03:33] one's going to be 10 minutes from now.
[03:34] Right here you can see at the bottom, it
[03:36] actually tells you in the desktop app
[03:37] how many seconds are left until your
[03:39] next cron. And you can see that it says
[03:41] every 10 minutes, next in 1 minute, ends
[03:43] in 3 days. So, when you set up a loop,
[03:46] you're basically going to be limited to
[03:47] how long they run, which is 3 days in
[03:48] the desktop app. And it does does
[03:50] because it doesn't want to have everyone
[03:52] running a cron every 10 minutes on, you
[03:54] know, like 10:50, 11:00, 11:10, 11:20,
[03:58] because then, you know, their API would
[03:59] get throttled. So, it kind of does like
[04:01] this random jitter thing, which I'll
[04:02] talk about in just a sec. So, anyways,
[04:04] that's how easy it is to use on the
[04:05] desktop app. And then, if you wanted to
[04:07] stop it, you could just come in here and
[04:08] say kill that loop, and it will go ahead
[04:09] and use the cron delete and kill it. Or,
[04:12] you could obviously just like open up
[04:13] this tab and just like close the
[04:15] session. Now, what's interesting is in
[04:17] the desktop app, if you were running a
[04:18] loop every 5 minutes or so, and you
[04:20] clear your chat, it will kill that cron.
[04:23] But, what's cool is that in the
[04:24] terminal, it doesn't actually do that.
[04:26] So, here's an example that I just worked
[04:27] on to show you guys. I said set up a
[04:29] loop every minute to remind me to take
[04:30] out the trash. It creates this cron job,
[04:32] right? And then, it fires it. And then,
[04:35] what I did is a {slash} clear. And then,
[04:37] after I cleared the session, I said, "Do
[04:38] you have any crons in this session?" And
[04:40] it used its cron list tool to take a
[04:41] look, and it said, "Yes, I still have
[04:43] the once-a-minute remind me to take out
[04:45] the trash." So, that's cool. You can
[04:47] basically in the terminal clear sessions
[04:49] if your context is starting to fill up,
[04:51] and your crons are still alive, as long
[04:53] as you don't actually terminate that
[04:54] session. And then, the next thing is
[04:56] that I wanted to set up a loop every 5
[04:57] minutes that will run the {slash} clear
[04:59] command. Because if you have a loop
[05:00] running every 10 minutes, and it's
[05:02] processing skills and looking at data,
[05:04] then your context window's going to
[05:05] slowly fill up, and you're going to hit
[05:07] context rot. So, it would be nice to set
[05:08] up another cron, and in this case, I
[05:10] said every 5 minutes, but it's going to
[05:11] run the {slash} clear command. And it's
[05:13] interesting because Claude Code actually
[05:15] doesn't think that's going to work, but
[05:16] it does. I basically tried it. I set one
[05:19] up where I inject just the word {slash}
[05:21] clear, and it actually treated it like a
[05:23] clear command. Right here was the actual
[05:24] cron firing off. And then, after it
[05:27] cleared it once again, I said, "What
[05:28] crons do you have?" And it found both of
[05:29] them still alive. So, that is why
[05:32] whenever I'm really going to use loops,
[05:33] I'm using it in the terminal, because
[05:35] you get functionality like this, which
[05:37] you don't get in the desktop app for
[05:38] some reason. And another interesting
[05:40] thing is that these crons or these loops
[05:42] are supposed to actually run for 7 days.
[05:44] And right now, in the desktop app, you
[05:46] could see that it said three. Now maybe
[05:47] if I relaunched and I updated, that
[05:49] would update and now we would see that
[05:50] these live for 7 days. But typically
[05:52] when you're using the terminal, you just
[05:54] get more functionality. And then real
[05:55] quick, that jitter thing that I was
[05:57] talking about, to avoid every session
[05:59] hitting the API at the same exact
[06:00] moment, the recurring tasks fire up to
[06:03] 30 minutes after the scheduled time. So,
[06:05] if you want something to run like at
[06:07] 9:17 and 9:27 exactly, it might not do
[06:11] it because of this whole jitter thing.
[06:13] But it would still set up an interval to
[06:14] run like every 10 minutes. So, one
[06:16] example that I was using this for is
[06:17] when I first started doing the Nate's AI
[06:19] agent responding to comments on my
[06:20] YouTube videos, I would just upload a
[06:22] video and then I would go into Cloud
[06:24] Code and say, "Hey,
[06:25] set up a loop for every 10 minutes to
[06:27] read the comments on my new upload and
[06:29] respond to them using the transcript and
[06:31] you know, point them in the right
[06:31] directions." And so, that was me just
[06:33] setting up a loop. I could even say,
[06:34] "Set up a loop to do that for every 10
[06:36] minutes and then automatically kill the
[06:37] loop after 24 hours." And it would do
[06:39] that. Okay, anyways, real quick, pros
[06:41] and cons. The first pro is that this is
[06:43] zero setup. You literally just say, "Set
[06:45] up a loop." and it runs. You get the
[06:46] full agentic loop because all this is
[06:48] doing is working inside of your session.
[06:50] So, all your skills, all your files,
[06:52] anything that you do normally when
[06:53] you're doing your knowledge work in
[06:54] Cloud Code, you get access to. You can
[06:57] even do a loop that runs skills
[06:59] explicitly. It You can make it shut
[07:01] itself down after a certain amount of
[07:02] iterations and you can run the slash
[07:05] commands directly like you guys just saw
[07:06] me do with the slash clear loop. Now
[07:09] some cons, the session has to stay open,
[07:10] obviously. So, if you close out of that
[07:12] terminal session, the loop dies. Your
[07:14] machine has to stay on. So, if your
[07:16] computer turns off, the loop also turns
[07:18] off. You've got a 7-day expiry and then
[07:20] the whole fixed interval thing that we
[07:22] talked about. And then of course, the
[07:24] different nuance there with desktop app
[07:25] versus terminal. So, that was loop. This
[07:28] is basically what we're seeing. Your
[07:29] machine is where it lives. You get the
[07:31] workflow, you get the agent and you get
[07:32] the tools. And one quick thing to clear
[07:35] up is
[07:35] with this WAT framework, people have
[07:37] been asking me like, "Okay, well where
[07:39] do skills live in there?" Well, skills
[07:40] are basically the W and the T. Because
[07:43] sometimes you have a skill that's just a
[07:44] W, right? Sometimes your skill is just
[07:46] here's how I write a LinkedIn post, and
[07:47] that's just a workflow. But sometimes
[07:49] you have a skill where it's like, okay,
[07:51] here's how I write a LinkedIn post and
[07:53] generate the infographics. And in that
[07:55] generate infographic section of the
[07:56] workflow or the skill, you're probably
[07:58] pointing to this image generator and
[08:01] this API, and you're combining those
[08:02] together. The tools with the workflow is
[08:05] a skill. Anyways, you're getting all
[08:07] three of those elements, WAT. Your
[08:08] computer has to stay on, and your
[08:10] session has to stay open as well. Real
[08:12] quick, guys, I know we're about to cover
[08:13] a ton of information in this one, so I
[08:15] broke all of this down into a very
[08:17] simple resource guide, which you can
[08:18] access for completely free. The link for
[08:20] that is down in the description. All you
[08:21] have to do is join my free school
[08:22] community, and once you get in there,
[08:24] click on classroom and go to all YouTube
[08:26] resources, and you'll be able to find
[08:28] everything in there. So, if you want to
[08:29] grab that resource guide, completely
[08:30] free, head over there. But anyways,
[08:32] let's get back to the video. Thanks,
[08:33] guys. All right, so now let's move on to
[08:35] this next one, which is desktop
[08:37] scheduled tasks and cloud routines. And
[08:39] the reason I put them together in one
[08:41] bucket is because if you open up your
[08:42] Claude desktop app and you go to
[08:44] routines, you can see right here that
[08:46] you can create different routines. And
[08:48] in here you can either have local or
[08:49] remote. So, they work very, very
[08:51] similarly, but there's one main
[08:53] difference, and that is what I'm going
[08:55] to talk about real quick. And it's
[08:56] honestly pretty obvious. Like right
[08:58] here, scheduled tasks run on your
[09:00] machine. So, if you close out of the
[09:01] desktop app, they won't run. And the
[09:03] cloud routines will run no matter what,
[09:05] because they're actually running inside
[09:06] of Anthropic's infrastructure on
[09:08] Anthropic's cloud, which is why if
[09:10] you're doing the cloud routines, you're
[09:11] limited to how many runs you can do per
[09:14] day. So, right here I'm on a max plan,
[09:16] and I get 15 runs a day for remote
[09:18] scheduled tasks. And if you're on the
[09:20] pro, you only get five. And I think if
[09:21] you're on team or enterprise, you get
[09:23] 25. Otherwise, it'll just cost you extra
[09:26] usage. But what's really cool about
[09:27] these is it's very similar to that loop,
[09:29] because you're basically just getting to
[09:31] inject a prompt into the conversation of
[09:34] a regular Claude code terminal. So, it's
[09:36] nothing too crazy. So, for example, if I
[09:38] look at that school wins engagement one,
[09:40] which I currently have paused because I
[09:42] switched this over to a Hermes agent,
[09:44] you can see that I have these
[09:44] instructions, right? I basically say,
[09:46] "Hey, run the wins engagement skill.
[09:48] This means you do X, Y, Z in this order.
[09:50] Here are all my instructions." And so,
[09:52] when this actually runs, if I go down to
[09:53] like an example that ran, you can see
[09:55] May 6th, what it does is it just injects
[09:58] that entire prompt into a Claude Code
[10:00] session, and then it just executes it,
[10:02] right? This project has my API keys. It
[10:05] has my context. It has everything that
[10:06] it needs, and it can even search through
[10:08] other things. So, you get the full
[10:09] agentic loop right here. You get Claude
[10:11] Code on a timer. Now, the cloud routines
[10:14] are basically the exact same way, right?
[10:16] Let me just click on this remote one,
[10:18] which is a paused one at the moment. You
[10:20] put in a specific prompt, and that just
[10:23] gets injected right into the session,
[10:24] same exact way.
[10:26] The only difference is that because
[10:27] these run on Anthropic's cloud,
[10:30] you are basically getting like a clone
[10:31] of a repo in the cloud, and so you have
[10:34] to set environment variables
[10:35] differently. So, I'm not going to do a
[10:37] full breakdown right now, but I did a
[10:38] full breakdown video, which I will tag
[10:40] right up here if you're interested in
[10:41] checking that out. Click up there. Okay,
[10:44] so pros and cons here. The pro, this is
[10:46] built into Claude Code on the desktop
[10:48] app, so there's no extra infrastructure
[10:50] or configuration. You obviously get your
[10:52] full Claude Code session capabilities
[10:55] with skills, um shell MCPs, sub agents,
[10:57] reasoning, all that. The cloud variant
[10:59] is awesome because you can literally set
[11:00] up those cloud routines, and your
[11:02] machine can be off, and your terminal
[11:04] can be closed, whatever it is, that will
[11:06] always run no matter what.
[11:08] Something else that's really cool about
[11:09] the local ones. So, remember if you guys
[11:11] saw I had all of these local ones
[11:13] running, too.
[11:14] If I accidentally turned off my computer
[11:16] for like 5 days, and then I turned it
[11:18] back on,
[11:19] when I open up the desktop app, Claude
[11:21] Code would look through all of the local
[11:22] tasks that hadn't fired while it was
[11:24] turned off, and it would play catch up,
[11:26] which is pretty cool. But, definitely
[11:27] keep that in mind because if you don't
[11:29] want it to play catch up, you're going
[11:30] to want to make sure that you like pause
[11:31] those. Otherwise, it will play catch up.
[11:33] And what else is cool on the remote ones
[11:35] is that you can have those be called by
[11:37] an API. So, it's basically a webhook
[11:40] that you could have other automations
[11:42] call on. So, besides those just being
[11:44] time-based, they can also be
[11:45] event-driven because you can also set
[11:47] them up to be called by like a GitHub
[11:49] action. So, here is me creating a new
[11:51] cloud routine. You can see I can choose
[11:53] schedule, GitHub event, or API. So,
[11:56] that's pretty neat. Of course though,
[11:58] it's tough because you only have 15 per
[11:59] day unless you want to use extra usage.
[12:01] Anyways, cons. The cloud routines, you
[12:03] have a 1-hour minimum interval. So, you
[12:05] couldn't run like one every 20 minutes.
[12:07] If you wanted to do something like that,
[12:08] you would probably just want to do a
[12:10] {slash} loop. The cap can be pretty
[12:12] tight, five a day with pro, but you
[12:14] know, you can always upgrade. Of course,
[12:15] if you're doing the desktop ones, the
[12:16] local ones, you have to keep everything
[12:18] on. And the other thing to think about
[12:19] is whenever you're injecting prompts
[12:21] into your cloud code sessions and the
[12:23] idea is that you don't have to give any
[12:25] input, you really want to play with the
[12:26] prompts and you really want to watch it
[12:28] for a while to make sure that it can
[12:29] just autonomously go do whatever because
[12:31] careless prompt scoping can cause
[12:33] unwanted actions, which is just the
[12:35] nature of an autonomous automation.
[12:37] Okay, so that was these two right here.
[12:39] These two scheduled tasks. We have
[12:40] obviously this one is on your machine.
[12:42] This one is in Anthropic's cloud. They
[12:44] all have the WA and the T, which is
[12:46] great. And then the scheduled tasks
[12:48] needs your desktop app open and your
[12:50] machine open. You don't need the session
[12:51] open because it starts a new session.
[12:53] And then the cloud routines, you don't
[12:54] need anything on or any sessions open,
[12:57] so it's truly a 24/7 type of system.
[13:00] Okay, so moving on to method three, we
[13:02] have deploying to something like Modal
[13:05] or trigger.dev, which is kind of It's
[13:07] not your own cloud, it's either Modal or
[13:09] trigger.dev's cloud, but it's not
[13:10] Anthropic's. It's something that you are
[13:11] kind of configuring on your own, but
[13:13] it's not very difficult. The idea here
[13:14] is that you basically write a script, so
[13:16] Python if you're using Modal or
[13:18] TypeScript if you're using trigger.dev.
[13:20] You deploy that script to Modal or
[13:23] Trigger.
[13:24] And you can have have run on a schedule
[13:25] or even like a webhook fire, so it can
[13:27] be like an an API endpoint essentially.
[13:30] And then it executes that Python script
[13:31] or TypeScript script, and then it gives
[13:34] you the output, and you get a dashboard
[13:36] in Modal or Trigger to see how many
[13:37] times they've run, and you can see, you
[13:39] know, errors and how long it took and
[13:41] stuff like that. So, what's the
[13:42] difference between Modal and
[13:44] trigger.dev? Well, Modal is Python
[13:45] serverless, you write a Python function,
[13:48] and you just push it over to Modal, and
[13:50] then it runs in the cloud on a cron. So,
[13:52] this very much feels more like a script
[13:54] on a timer. trigger.dev uses TypeScript,
[13:57] and it feels a little bit more agentic,
[13:59] because sometimes your things get broken
[14:00] down into like two different like
[14:02] scripts that would call on the other
[14:04] one. So, typically, I have preferred to
[14:06] use trigger.dev, but at the end of the
[14:08] day, if you have a very deterministic
[14:09] process, they're both going to achieve
[14:11] you the same result. And I don't really
[14:12] know how to write code in Python or
[14:14] TypeScript, obviously my Cloud Code does
[14:16] it for me, but if you do understand
[14:18] Python way better than TypeScript, then
[14:20] you probably would want to go with
[14:21] Modal. Cloud Code works with both of
[14:22] these two options very, very well. It
[14:24] understands how to push scripts to the
[14:26] dev, move them to the prod. It
[14:28] understands that you need to put your
[14:29] environment variables over on Modal or
[14:31] trigger.dev, so that your automation can
[14:33] actually access things. I'm not going to
[14:34] do a full breakdown right now, but I
[14:36] have done multiple videos with Modal on
[14:38] this channel. I will tag one of those
[14:39] right up here.
[14:40] And then I will also tag a video that I
[14:41] did with trigger.dev that I made on this
[14:43] channel, which breaks it down a little
[14:45] bit more. I will tag that one right up
[14:47] here. Anyways, the one-line analogy,
[14:49] Modal is a cron job in the cloud.
[14:50] trigger.dev is a durable workflow engine
[14:53] that happens to also support cron. But
[14:54] once again, both of these could be
[14:57] an API endpoint. You could turn that
[14:58] into a webhook call. Okay, so that was
[15:00] Modal, trigger.dev. You can see here
[15:02] that's going to run on your cloud, or
[15:03] technically like Modal's cloud. And for
[15:06] the WAT framework, you're basically just
[15:08] deploying your skill. You're basically
[15:10] just deploying the workflow and the
[15:12] tools. You don't get that autonomous
[15:14] agent loop, and what else that means is
[15:16] all of the AI processing that you're
[15:18] going to be doing there will be an API
[15:20] call. Whether that's the Cloud API or
[15:21] whether it's the open router, it will be
[15:24] not your Claude code subscription, which
[15:26] means it might be more expensive, right?
[15:27] Because you're running an AI processing
[15:29] that's token-based, pay per token. But,
[15:31] the other cool thing about this is that
[15:33] a lot of these automations that you're
[15:34] going to deploy, because they're going
[15:36] to be primarily pretty deterministic,
[15:38] might not even use AI at all. And that's
[15:41] where I would opt for one of these is if
[15:43] the process doesn't need AI and I can
[15:44] just chuck that script up somewhere to
[15:46] run on a cadence. Because it doesn't
[15:47] need your computer on and it doesn't
[15:48] need any sort of session to be open.
[15:50] Now, what you guys noticed down here is
[15:51] I do show you an option with Modal and
[15:53] trigger.dev that gives you the A part of
[15:56] the WAT framework. And that is using the
[15:58] Agent SDK. So, what is the Claude Agent
[16:00] SDK? So, this is not really an official
[16:02] method that I'm diving into right now.
[16:03] It's just kind of like a little bonus
[16:04] thing to think about. But, the Agent
[16:06] SDK, it almost gives you like an
[16:09] endpoint for Claude code. Because
[16:10] essentially, Claude code is kind of just
[16:12] like
[16:13] a user interface built on top of
[16:16] Claude's Agent SDK. It has the tools, it
[16:18] has the query ability, it has more of
[16:20] that agent feel compared to if you just
[16:23] hit, you know, a raw Claude API
[16:25] endpoint. Where you're just kind of
[16:27] talking to the model and you get an
[16:28] answer back. But, the Agent SDK is like
[16:30] Claude code where it has like that
[16:31] harness and it can call tools and things
[16:33] like that. So, yeah, the Claude API
[16:35] gives you just the brain that talks
[16:36] back, while the Agent SDK gives you
[16:37] Claude code, essentially. The brain plus
[16:40] the hands, so it can do all of these,
[16:41] you know, bash, file edits, web search,
[16:43] that whole loop. And it's already wired
[16:44] up so that you can actually do the work
[16:46] instead of just give you some sort of
[16:48] like text-based output. So, here's kind
[16:50] of what it would look like. You would
[16:52] send off a query. You would shoot off an
[16:53] API call to
[16:55] this Agent SDK. The agent would read
[16:57] that. It would decide on what tools it
[16:59] would reason. It would run the tools. It
[17:00] would get the results and it would keep
[17:01] iterating. And then it would give you
[17:03] some sort of output. And so, that's
[17:04] essentially what Claude code is, right?
[17:06] It's just wrapped up nice, like I said.
[17:08] Now, the one thing that used to confuse
[17:09] me a lot about how the Agent SDK worked
[17:11] and how Claude code worked was when
[17:12] you're in a Claude code session. So, for
[17:14] example, if I just pull up this this
[17:15] we can see how much has been used of my
[17:18] limit. And I could do something like a
[17:20] {slash} clear, and I could do a {slash}
[17:21] compact, and I could do things like
[17:23] that. And I know that if I'm having a
[17:25] long ongoing conversation, and I keep
[17:26] scrolling up, Claude will actually read
[17:28] that and help use that as context for my
[17:31] next decision.
[17:32] And the thing about the Agent SDK is by
[17:33] default, every message that you send off
[17:36] is going to be stateless, meaning it
[17:38] wakes up, no memory, nothing. So,
[17:40] basically, the fix there is when you
[17:41] make your request to the Agent SDK, if
[17:43] you're sending over the session ID,
[17:45] that's how you have an ongoing session.
[17:47] The Agent SDK will also auto compact and
[17:48] things like that, but I don't think it
[17:50] does a {slash} clear. If you want to do
[17:51] a {slash} clear, you would basically
[17:53] just start a new session. But anyways,
[17:55] it can do all of these tools, of course,
[17:56] and it can utilize sub-agents, MCPs,
[17:59] hooks, skills, {slash} commands,
[18:00] Claude.md, memory, compaction, all that
[18:03] kind of stuff. And obviously, this is an
[18:05] official SDK from Anthropic. But the one
[18:08] thing that, of course, is bad about this
[18:09] is that you cannot use your Claude
[18:10] subscription if you're using the Agent
[18:12] SDK. It requires a Claude API key. So,
[18:15] it's going to be much more expensive
[18:16] than you just using Claude code in your
[18:20] app or VS Code, your terminal, whatever
[18:22] it is, wherever you use Claude code. I'm
[18:24] so glad that I waited a few days to post
[18:25] this video because then, on May 13th,
[18:28] they just announced that your monthly
[18:32] credit can actually go towards
[18:35] something like the Claude Agent SDK, but
[18:37] it's not exactly like super
[18:38] straightforward. It's not the same
[18:40] weekly usage that you get. It's like a
[18:42] different dedicated budget. So, I'm not
[18:44] going to dive into that too much right
[18:46] now. I just wanted to let you guys know.
[18:48] Um Theo made a really good breakdown,
[18:50] where he kind of dives into like the
[18:51] scale and the different nuances. So, I
[18:53] will link that in the description if you
[18:54] guys want to check that out after this
[18:55] if you're interested in like
[18:57] understanding what this really means.
[18:58] But just want to let you guys know. So,
[19:00] let's get back to the video. But the
[19:01] idea of pushing some sort of automation
[19:03] to Modal or Trigger.dev is still the
[19:05] same, except for you just get the agent
[19:08] now, which obviously lets those
[19:09] automations be a little bit more
[19:11] non-deterministic, a little bit more
[19:12] agentic. Not even a little bit more, a
[19:14] lot more agentic. Okay, so there are two
[19:16] more things that I wanted to very, very
[19:17] briefly touch on. I'm not going to dive
[19:19] into them in this video, but I did want
[19:21] to call them out. So, the first thing is
[19:22] managed agents, which is a fairly new
[19:25] service that Anthropic has spun up,
[19:27] which lets you do managed agents
[19:30] completely on Anthropic's cloud. Now,
[19:31] the reason I'm not going to dive into
[19:32] them in this video is because I played
[19:34] around with it and I honestly don't love
[19:36] it. Like, I'm just going to keep working
[19:38] in my own infrastructure the way that I
[19:39] have my routines, the way that I have my
[19:41] endpoints, things like that. I think a
[19:42] big value of the managed agents is for
[19:44] people who've probably never opened up
[19:46] cloud code before and they're looking to
[19:47] start building some agents. It just
[19:49] feels a little bit more like wrapped up
[19:51] nicely, but there's some functionality
[19:52] in there that I don't get. So, if you
[19:55] already are using cloud code and you
[19:56] understand it really well, then I would
[19:57] just say stick with cloud code. But, if
[19:59] you guys do want me to play around with
[20:00] them more and give you a video, just let
[20:01] me know in the comments. Obviously, I'm
[20:03] here to experiment and figure out what
[20:05] works for what use case. And the other
[20:06] thing that I wanted to touch on was
[20:07] hooks, which honestly I haven't talked
[20:09] about too much on this channel, but it's
[20:11] a really, really important and really
[20:12] cool feature of cloud code. So, hooks
[20:14] are basically like event-driven
[20:17] little automations and they're much more
[20:19] deterministic. So, you write something
[20:21] to cloud code, right? The agent does
[20:23] something, whether that's a a grep or a
[20:25] glob or an edit to a file. And after a
[20:28] specific event happens, you can set up a
[20:31] hook to fire. So then, that hook script
[20:33] runs every time a certain action happens
[20:36] and that is very, very powerful if you
[20:38] kind of layer a bunch of hooks together.
[20:40] So, a real quick example is every time
[20:42] cloud code sends you a message, that is
[20:45] something that can fire a hook. And you
[20:46] can have that hook fire a noise
[20:48] notification so that if you're working,
[20:49] you can hear when cloud code has sent
[20:51] you a message. The other things, of
[20:53] course, could be like a pre-tool use, it
[20:55] could be a post-tool use, it could be a
[20:56] session start or a session end. So,
[20:58] there's a lot of power, I think if you
[21:00] already just starting to like have some
[21:01] lightbulb moments of oh, wow, every time
[21:03] the session ends I want it to do this or
[21:05] every single time it uses like one of
[21:07] these tools, I would like it to do this
[21:08] for me.
[21:09] That's where you start to sort of loop
[21:10] them together. So, it's a very, very
[21:12] powerful feature. If you guys want to
[21:13] see like a full kind of masterclass
[21:15] breakdown of hooks and different use
[21:16] cases and how they work, let me know and
[21:18] I would love to bring you guys a video
[21:19] about that as well. But anyways, that is
[21:21] going to do it for today and I know we
[21:23] covered a ton of information in this
[21:24] one, so I threw all of this into a
[21:25] resource guide that you can access for
[21:27] completely free. The link for that is
[21:28] down in the description. You just have
[21:29] to join my free school community. This
[21:31] is what it will look like once you join
[21:32] and then once you're in there, you're
[21:33] going to go to classroom and then you'll
[21:34] just click on all YouTube resources.
[21:36] Everything that I've ever shared for
[21:38] free is in there. But if you guys
[21:39] enjoyed the video or you learned
[21:40] something new, please give it a like. It
[21:41] helps me out a ton. And as always, I
[21:43] appreciate you guys making it to the end
[21:44] of the video and I will see you all in
[21:46] the next one. Thanks everyone.
