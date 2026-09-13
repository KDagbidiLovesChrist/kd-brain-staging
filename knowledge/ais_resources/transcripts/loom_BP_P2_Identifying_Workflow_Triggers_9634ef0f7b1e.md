# Loom Transcript · BP_P2_Identifying_Workflow_Triggers

**Source video ID:** 9634ef0f7b1e410ab5fefc8ebf9c88d1
**Loom URL:** https://www.loom.com/share/9634ef0f7b1e410ab5fefc8ebf9c88d1
**Detected language:** en (probability 1.00)
**Duration:** 458.2s

---

[00:00] Workflow triggers is
[00:03] very important to understand because
[00:05] any automation regardless of
[00:08] N&N or make or Zapier or Lindy or Lizer or mine studio or whatever you end up deciding to use obviously this
[00:15] Community is primarily right now focused on N&N who knows what we'll be doing in six months here
[00:20] But what I do know for fact is that in order to automate things we need triggers and that is basically just the first step
[00:28] What triggers the workflow?
[00:30] So in the case of N&N, this is what it looks like when you open a blank workflow and there's a big button right here
[00:36] This is add first step when you click on that
[00:38] It's gonna pop up on the right hand side and say what triggers this workflow and these are the different types that we have
[00:43] Obviously, you know, there's way more than just these one two three four five six seven eight because these expand and then it's basically like
[00:52] Almost every single integration has a trigger meaning Gmail has a trigger
[00:56] Discord has a trigger slack telegram. What's that?
[00:59] HubSpot air table sheets every integration has some sort of trigger and
[01:05] What's going on behind the scenes of a trigger is it's basically just a webhook?
[01:08] We don't have to dive into that because that may be confusing, but
[01:12] We choose a trigger, right? So a webhook
[01:16] This fires when external systems send data to a unique URL and this is good for real-time automation
[01:21] So just to make it as simple as possible. Let's say we have a form submission on our website and when the user clicks submit
[01:28] That fires off data to a webhook and so every time a user submits a form your workflow would trigger if you set up this webhook
[01:35] Right and then the rest of the nodes that you set up would fire off
[01:41] You can also have a scheduled trigger meaning every day. I want this to run at 6 a.m. And then at
[01:47] 6 p.m. If you want to send out a morning briefing and a morning or a morning briefing in a
[01:52] End of day report. That's how you can set up a scheduled trigger. You can also do an n8n workflow trigger meaning I'm going to build out this one workflow
[02:00] That is going to fire off whenever I need to send an email. So I have my email workflow right here
[02:05] What I can do is I can build a different workflow
[02:08] To trigger this email workflow. So that's how you know when I talk about modularity and scalability is you can build out
[02:14] These little tools and building blocks as workflows and you can have other workflows trigger them which is really cool to think about like
[02:22] Common functions that you do or common functions in a workflow. Just build it out
[02:26] Keep it built out as a tool and then have other workflows call on them and trigger them
[02:30] So that's what like an ended end trigger would look like and then of course you have your all all of your external triggers
[02:35] Which is like every time I get a new email every time someone submits a ticket in my CRM every time someone
[02:43] Shoot some message to my WhatsApp like those are the other types of external service triggers you could have and what I was saying is that
[02:49] This is basically just a web hook, but that's just like wrapped up all pretty for us anyways
[02:53] And then we have manual triggers, which is usually just for sort of like testing or if you have an on-demand operation like
[03:03] Whenever I'm building a workflow, I'm using a test it with a manual trigger just so I can at the bottom
[03:07] I can hit test step and it will just run so I can just like you know see if things are working and what I meant by like an
[03:12] On-demand operation is like let's say you have a workflow that's going to
[03:17] Take an excel sheet and it's going to extract the data and it's going to parse it and it's going to create some visualizations
[03:23] And that's really just like a it's an automation that saves you time, but it's not some sort of
[03:28] Schedule so whenever you need to you can just take that excel sheet put it into this workflow and then hit run yourself
[03:34] And then you'll get spit out something which at the end of the day
[03:37] Which at the end of the day is still going to save you time because you built out that process
[03:40] But it's a manual trigger. So anyways
[03:44] Selecting the right trigger
[03:46] It's just really important to understand like
[03:48] When you have a process when you've mapped out your process and you've mapped out the way you do it manually
[03:53] There's always something that triggers you to do this process
[03:56] Whether that just means I get triggered once a day to do this
[04:00] Or it's I do this every time I receive an email from x person or every time I receive an email about x event
[04:06] So like identify the trigger
[04:08] What is the source? Where's it coming from?
[04:10] What is the timing of that trigger?
[04:12] What data is available when you get that when when you trigger this event what data is available because that helps you figure out what data
[04:18] Do I need to go get and then reliability how important is failproof execution?
[04:25] Then we have mapping that trigger configuration. So when you're planning your trigger document what login or API keys or credentials are needed
[04:34] What settings need to be defined
[04:37] Expect a data format. What does the incoming data look like and an error handling what if the trigger doesn't fire what happens
[04:45] So practical example here is we have basically the same
[04:50] Process but it can be triggered in three different ways
[04:55] So option A with a webbook
[04:58] So the use case here is a ticket system
[05:01] Supports webhook notification
[05:04] To configure this we need a webhook URL from n and n and we need to somehow embed that into our ticketing system
[05:09] So that we can link the two things to send over data to the webbook
[05:13] The data format here would be json
[05:15] Where we'd be sending over in json format a ticket id customer info description time stamp email whatever it is
[05:23] We can send over the data in json
[05:25] The pros of this method is that we have instant processing with clean structured data
[05:29] The cons are that we require webhook support from the ticket system
[05:33] So if the ticket system doesn't natively let us send off data to a webhook we can't use this trigger
[05:39] So let's say we can't use a webhook option B we can use the schedule
[05:43] So we have API access, but we don't have webhook of a functionality
[05:48] To configure this we need to set up an interval
[05:51] Of when we want this thing to run and we also need API credentials to access our ticketing system
[05:58] The data format is going to be
[06:01] Querying for new tickets since the last run so this can get messy because how many do we pull back?
[06:06] And how many do we know or how do we know which tickets have already been processed if this is running on a schedule rather than on an event trigger
[06:13] The pros that it works with any API based system
[06:17] The cons that there's delay between ticket creation and workflow run so another con there is yeah like besides the fact that we have to track
[06:23] Which ones have been processed or not
[06:25] We also have the the element of like are we going to run this every hour are we going to run this once a day twice a day
[06:31] Is there going to be a big gap between a ticket being submitted and the person receiving a response
[06:37] And then the other option we have is like an email trigger and there's probably even more than just these three
[06:41] But the third option we have is an email trigger
[06:43] Tickets can arrive via email as well as the ticketing system
[06:47] What we would need to do to configure this ticket or to configure this email trigger is we need an email login
[06:53] And we also need parsing rules meaning we need to understand what type of data is coming through in the email and how we're going to parse it to actually be able to use it
[07:01] So data format email body and attachments. What does that look like the pros here is that it's easy to set up for a basic workflow
[07:07] The cons are that it's way less structured data requires parsing and there's a lot of variability there with how many attachments could be sent through something like that
[07:15] So hopefully this gives you a good picture of like what triggers are
[07:19] Why they're important to understand and not just like the trigger but also like the type of data that that trigger will send you because
[07:27] Like I said before a workflow is just moving data from left to right and we really have to understand what it looks like and where
[07:33] How we need it in order to actually have an efficient workflow. So that's triggers
