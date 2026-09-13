# Loom Transcript · CC_P4_1.7_Frontend_for_n8n_Workflow

**Source video ID:** 90f1f2c85f74461da6752f7ed164d08b
**Loom URL:** https://www.loom.com/share/90f1f2c85f74461da6752f7ed164d08b
**Detected language:** en (probability 1.00)
**Duration:** 635.0s

---

[00:00] In this video, we're going to see how we can connect our NADN workflow to a website, to a front end
[00:06] so that not only ourselves, but now anyone that we want is going to be able to access our website
[00:12] and it's going to be able to trigger and use our workflow.
[00:15] Let's say you already have a workflow, it's working in NADN.
[00:18] It is a quote generator and the trigger right now is a form.
[00:22] So when we execute this workflow, we're going to see a form.
[00:27] This form is to request quote, which is the idea of this workflow.
[00:31] So in this form, we will need to input the project description, the estimated hours and the client type
[00:37] so we can request a quote for dealing a landing page, for a healthcare company, estimated hours 120,
[00:46] client type, we could do enterprise.
[00:48] Okay, now we're going to click submit and this would execute the workflow.
[00:53] We can see that it executed over here and in this case I'm using a text file as an output.
[00:58] So once my workflow estimates the quote is going to generate a text file.
[01:02] This could have also been sent the information over email or create a new document in my Google Drive or whatever you prefer.
[01:09] But what if we want to create a website for this?
[01:12] And what if we also want other people to access that website so that they can use our workflow?
[01:17] So as you can see, this works but the user experience is not the most comfortable.
[01:22] So what we are going to see in this video is how can we connect our workflow to a website that's going to be deployed live
[01:28] and that anyone that we want is going to be able to access that website and it's going to be able to use and trigger our workflow.
[01:36] To do this, we're going to go to VS Code.
[01:38] I have created a new folder, a new project called N8N2UP.
[01:42] I'm going to open Cloud Code. I'm going to go to LAN mode and I'm going to sell Cloud.
[01:47] Help me create a Cloud MD file for this project.
[01:50] The goal is to build a web app front end for an N8N workflow.
[01:53] The workflow is a quote generator.
[01:56] The user inputs a project description estimated hours and client type and they get back a professional quote.
[02:03] The front end is going to send data to an N8N web hook and it should display the response.
[02:09] So why am I talking about a web hook over here when our trigger actually was a form.
[02:15] Once we have our website, we're going to be switching the form with a web hook so that our website is going to be able to call our N8N workflow through a web hook.
[02:24] So back to VS Code.
[02:26] We're going to be using the front end designer skill from and for a pick.
[02:30] Ask me any clarifying questions that you need.
[02:33] It has started creating the plan.
[02:34] So it's asking me a few questions like what text tag do I want for the front end?
[02:39] I'm going to go with the recommended one.
[02:42] Do you have the N8N web hook URL already?
[02:45] Let's go with the placeholder for now.
[02:48] We're going to replace that later.
[02:51] What does the N8N workflow return in its response?
[02:55] Right now in this case it returns a JSON but based on your own workflow, this may be different.
[03:00] So I'm going to go with JSON.
[03:02] It's going to keep working on the plan and if everything looks good, we're going to go ahead and add or accept.
[03:07] Okay, and we now have our Cloud MD file ready with all the description for this project.
[03:14] Okay, it all looks good.
[03:15] So let's go back to Cloud code and we're going to ask it to actually build the project to actually build the website.
[03:22] So we can say Cloud MD file looks good.
[03:27] Now go ahead and build a website.
[03:32] We're going to give it a few minutes.
[03:34] Okay, after a few minutes, it has finished working.
[03:37] It has created all the files and I've asked Cloud to run it because I want to test it locally.
[03:43] It's not going to be connected to N8N yet, but first I want to test it locally so I can see and I can take a look at the UI.
[03:50] So I'm going to test it locally on local host.
[03:54] And even though the form was generated correctly, we can definitely say that it has not used the front end design skills.
[04:01] Even though the prompt was very vague, it was very simple.
[04:04] We should not be doing that.
[04:06] This is completely plain.
[04:07] So it's actually very good to see the difference because so far we have only prompted very vaguely.
[04:13] So it kind of makes sense that we're going to get these kind of results.
[04:16] But let's see the difference when we add the front end design skills.
[04:20] So we're going to go to skills as H.
[04:23] We're going to look for the front end design skills from Anthropic.
[04:27] We're going to copy this and we're going to go back to Cloud Code.
[04:30] And we can say the UI looks very basic.
[04:34] Make sure you are calling front end design skills.
[04:39] So if we click on local host, we should be able to see the new website, which looks a million times better than the previous one.
[04:45] We didn't specify any branding colors, any fonts.
[04:49] We just use the same prompt, which I do not recommend.
[04:53] But now this website has way more personality.
[04:56] So we have the project description, the estimated hours and the client type.
[05:00] And what we will need to do next is to push this into GitHub, deploy it into Brazil.
[05:06] So it is live.
[05:07] And of course, we still need to connect our website to an 8N.
[05:10] Let's start with the 8N part first.
[05:13] Whenever we want to connect an 8N workload with a website, what we need to do is to replace the first node in this case our form and the last node.
[05:24] We need to replace them with the web hooks.
[05:26] So we're going to get rid of the form.
[05:28] And in my case, I'm going to get rid of the text file.
[05:31] And I'm going to add a web poop trigger.
[05:34] I'm going to connect it to my logic.
[05:36] These are the URLs that we're going to be using later.
[05:39] And in this case, we're going to be responding using the respond to webhook node.
[05:44] So we're going to close this.
[05:46] And we're going to add the response to webhook node.
[05:50] So before going back to cloud code, let's fetch the production URL.
[05:54] We're going to copy this.
[05:56] We're going to go back to VS code.
[05:59] We're going to clear the conversation to start a new task.
[06:02] And what do we want to do next?
[06:04] I'm going to paste the webhook URL.
[06:07] And I'm going to try to cloud when I use certain clicks on generate quotes.
[06:13] I want it to call this webhook replace the current place holder with it.
[06:22] Okay, next step.
[06:24] What do we want to do?
[06:25] We want to deploy this into VS code so that anyone with the URL can access our website.
[06:30] Because so far we've had the website running locally.
[06:33] And if we want other people, we need to deploy to the internet.
[06:36] And for this, we're going to be using VS sell.
[06:38] So we're going to go to VS sold.com.
[06:40] We are going to create a new project.
[06:42] And the first thing that is asking us is to import a guide repository.
[06:46] And why is this?
[06:47] Because the way VS sell works is it's constantly listening to updates on our GitHub repository.
[06:54] So our project, our website is going to be pushed into GitHub.
[06:58] And whenever there's a new push, whenever there's a new version of the code,
[07:01] it's going to be automatically deployed into VS sell.
[07:04] Which is going to make it available in a public URL that you can share with anyone
[07:08] so that anyone else can use your app.
[07:10] So next step is going to be we need to connect VS sell to our Git account.
[07:14] I've already done that.
[07:15] But I don't have a GitHub repository for this project.
[07:18] So I'm going to go to GitHub.
[07:20] I'm going to create a new repository.
[07:21] And I'm going to name it quote generator.
[07:24] I'm going to make it private, create repository.
[07:27] Okay, now that we have our repository, let's go back to VS sell.
[07:31] And we should be able to see the new project here.
[07:34] So we're going to click import.
[07:36] We're going to deploy it.
[07:37] But so far we haven't pushed our project into GitHub.
[07:41] So our repo here is empty.
[07:43] Which means that our project in VS sell is also going to be empty.
[07:46] So we need to go to VS code.
[07:48] And we need to push our project into GitHub.
[07:51] Okay, so let's go back to cloud code.
[07:53] I want to push this project into GitHub.
[07:58] This is my repo URL.
[08:00] For the URL, you just need to go back to GitHub.
[08:03] Get into your repo and just copy this URL over here.
[08:07] And you can give it to cloud code.
[08:09] So we're going to hit enter.
[08:11] Okay, once it's done pushing our code to GitHub, we can go to GitHub.
[08:15] And we're now going to see that the repo has our code.
[08:18] And since GitHub is connected to VS sell, if we go to VS sell.
[08:22] And we take a look at the project.
[08:24] It says that it has been updated just now.
[08:27] So if we click on our project, we're going to be able to find our URL.
[08:32] We can share this URL with anyone who wants to use our app.
[08:37] And if we click here, we're going to be able to see our deployed our live web app.
[08:42] So it seems to be working just fine.
[08:44] All we need to do left is to connect our website in VS sell to our web hook in NADN.
[08:50] First, we're going to go back to NADN to our workflow.
[08:53] We're going to make sure that the workflow is published.
[08:56] We're going to go to our web hook.
[08:58] We're going to go to production URL.
[09:00] And we're going to copy these URL.
[09:02] We're going to go back to VS sell.
[09:05] And within our project, we're going to go to settings, environment variables.
[09:11] We're going to add a new environment variable.
[09:14] We're going to name it NADN web hook URL or whatever cloud code told you to name it.
[09:19] So add new environment variable.
[09:22] NADN web hook URL.
[09:25] And here you're going to paste the web hook URL from NADN that we have just copied.
[09:30] Once you have that, you're going to save it.
[09:32] And you're going to see a message over here asking you to redeploy.
[09:36] You're going to redeploy.
[09:37] So this new environment variable is also deployed into the project.
[09:41] And when that deployment is ready, you're going to go back to your project.
[09:45] You're going to click on the website.
[09:47] And now we're going to be able to test in production our website
[09:50] and how it connects to our workflow in NADN.
[09:53] So project description, landing page for health care company estimated hours.
[10:00] We can go with 40 hours client type.
[10:03] It's an enterprise client.
[10:05] And now once we click generate quote, it is going to be calling our NADN workflow.
[10:11] So let's click on generate quote.
[10:13] It triggered our NADN workflow.
[10:15] And we got the response.
[10:17] And we're able to show that response that quote within our web app.
[10:21] And this is how you can now connect your NADN workflows with a website.
[10:25] And you can deploy that website with a virtual.
[10:28] So that now anyone with your URL is going to be able to use your app.
[10:32] It's going to be able to trigger your NADN workflow.
