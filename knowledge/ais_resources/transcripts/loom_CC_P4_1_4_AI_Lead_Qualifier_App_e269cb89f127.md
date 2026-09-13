# Loom Transcript · CC_P4_1.4_AI_Lead_Qualifier_App

**Source video ID:** e269cb89f12747bd99ff643e7224f7ba
**Loom URL:** https://www.loom.com/share/e269cb89f12747bd99ff643e7224f7ba
**Detected language:** en (probability 1.00)
**Duration:** 1343.4s

---

[00:00] In this video, we're going to be building our first full stack app.
[00:03] And what do we mean by full stack?
[00:04] Full stack means that we're going to be building the front end and the back end.
[00:08] So far, we've been building workflows.
[00:11] Workflows are the back end.
[00:12] All these are the business logic.
[00:14] And we used to trigger these workflows either locally or by deploying them on trigger.dev.
[00:20] But what if we want to trigger this from, let's say a website?
[00:24] What if we want to create an interface that makes it easier for other people to
[00:28] interact with our workflow?
[00:30] This is when we need a front end.
[00:32] The front end is all the visual side of an app is what the user sees.
[00:35] It's what they interact with when dealing with a workflow.
[00:38] In this case, we're going to be building an AI lead qualifier.
[00:41] We're going to be sending our workflow information about a company.
[00:44] And AI is going to analyze that company.
[00:47] And it's going to retrieve us information about whether it is qualified as a lead or not.
[00:51] And in order to interact with this workflow, we're going to be creating a front end.
[00:55] We're going to be creating a website that's going to have a form where we're
[00:58] going to feel the information about the company.
[01:00] And then we're going to have a results page where we're going to be able to see a report
[01:04] that the AI agent has created about that lead.
[01:07] As you can see, the workflow is not going to be super complex.
[01:10] It's actually pretty simple because what we want to focus on in this video is how to create
[01:14] the front end, how to create the website and how to connect that website, the front end
[01:19] with our workflow, the back end.
[01:21] Okay, to get this started, we're going to go to VS code.
[01:24] I have created a new folder, a new project for our AI lead qualifier and to summarize
[01:29] a bit, what we're going to be asking Cloud Code to do is first, we're going to start creating
[01:34] our Cloud MD file.
[01:35] We're going to be following the WAT framework.
[01:38] We're going to ask Cloud Code to create the workflow.
[01:40] We're going to be deploying that workflow into trigger.dev.
[01:43] As we've seen in the previous section of this course, then we're going to ask Cloud Code
[01:47] to create the website, the front end.
[01:49] We're going to be deploying that website into Versal.
[01:52] And finally, we're going to be connecting both.
[01:54] We're going to be connecting the front end, the website with the back end.
[01:57] The back end is going to be our workflow in trigger.dev.
[02:01] So this way, whenever anyone wants to interact with our workflow, we're just going
[02:05] to send them a link to our website and they're going to be able to see the form.
[02:09] They're going to be able to complete all the information about that company.
[02:12] And they're going to be able to from the website trigger the workflow on trigger.dev.
[02:16] So that the AI model is going to be analyzing all the information and then it's going
[02:21] to be sending back a report.
[02:22] And the user is going to be able to see that report on the website.
[02:26] OK, so our first step, as we said, is going to be to create our Cloud MD file.
[02:31] For this, I'm going to go to plan mode as we always do first.
[02:34] And I'm going to say the following prompt, help me draft the Cloud MD file.
[02:38] I want to build a workflow using the WIT framework.
[02:41] I need you to create a folder for each section except for the agent.
[02:45] And this framework is to build the workflow.
[02:47] The workflow is an AI lead qualifier.
[02:50] I will send you information about a lead and AI will qualify it.
[02:53] The tech stack that we're going to be using is I will be deploying this workflow to trigger.dev.
[02:58] I will be creating a front end with your help where I will fill out a form about a lead.
[03:03] I'm going to click on analyze and the workflow in trigger.dev is going to be called once that
[03:08] workflow finishes working is going to show the results in the front end.
[03:11] And finally, we're going to be deploying the front end, the website into verso through GitHub.
[03:16] So my backend is going to be in trigger.dev and my front end is going to be in verso.
[03:20] And they should be able to communicate with each other.
[03:22] We're going to hit enter is going to start creating the plan to build this workflow.
[03:27] And we should be able to see the plan in a few seconds or minutes.
[03:31] Once it's finished planning, we can review the plan over here is going to be creating the Cloud MD file
[03:36] plus the base structure with the WIT framework.
[03:39] So we're going to go ahead and out of accept.
[03:44] And in just a few seconds, we can see that it has created the Cloud MD file.
[03:48] We can take a look over here here, some context about what the workflow is going to be, the WIT framework.
[03:55] The text tag that we're going to be using, the architecture, some instructions and the project structure directory rules tools.
[04:04] OK, it all looks perfect.
[04:06] We can see that it has also created the base structure.
[04:09] We have the workflows directory, the tools directory.
[04:13] So we follow the WIT framework.
[04:15] So now that we have our Cloud MD, we have our base, we are ready to start creating the workflow.
[04:21] So we're going to ask Cloud code to create the workflow now.
[04:25] I will be deploying it to trigger.dev.
[04:27] So I want you to create the workflow and guide me on how to deploy to trigger.dev.
[04:32] We are going to hit enter and Cloud is now going to start creating the workflows and the scripts for this workflow.
[04:39] And at the end, it should also be telling us how to deploy to trigger.dev in case you've never done it before.
[04:44] OK, it's finished working and we can see here that it has created two workflows.
[04:49] One is a complete AI lead qualification workflow.
[04:52] Then it has also created a deployment workflow for when we want to deploy to trigger.dev and verso.
[04:59] And it's also created some trigger.dev tasks and config files.
[05:04] We also asked it to help us set up trigger.dev.
[05:08] So we're going to be able to see some instructions here on how to do it.
[05:11] So we're going to start by going to trigger.dev, sign in in and creating a new project.
[05:16] So we'll go to trigger.dev, we're going to login, we're going to create a new project,
[05:21] we're going to set a project name.
[05:23] In this case, it could be lead qualifier.
[05:27] We're going to select what we are working on.
[05:29] It could be an internal tool.
[05:31] This is optional. You can fill them out if you want, but if not, you can just skip them and go to create.
[05:36] Once we have created a project, we're going to see the set up screen for this project.
[05:41] From here, what we want is our project ID or reference, which is the one over here.
[05:47] We're going to copy this and you can ignore these steps, these commands.
[05:51] We're actually going to be asking Cloud Code to do this to run this for us.
[05:55] So we're going to go back to VS Code and we can see that one of the steps
[05:59] that Cloud Code is telling us to do is to replace our project ref,
[06:03] which is our project ID that we just copied into the trigger config TS file.
[06:08] So we're going to come over here and we're going to replace
[06:12] this with our project.
[06:14] We're going to go back to trigger.dev, we're going to copy this information
[06:19] and we're going to tell Cloud.
[06:21] I'm seeing these steps in trigger.dev.
[06:26] Help me set this, I've already updated trigger.comfig with my project ref.
[06:37] We're going to hit enter and Cloud Code is actually going to be doing this setup for us
[06:42] so that we don't have to do it manually.
[06:44] I'm going to accept this bash command and it's going to continue working.
[06:48] And a few seconds later, it's finished working and it says that it's running successfully.
[06:52] We should be able to go to trigger.dev to our dashboard and we should now see our
[06:57] qualified lead task. So we're going to go to trigger.dev and we can see that this screen used to
[07:03] have the setup steps, the instructions and it's automatically updated and now it is showing our task.
[07:10] This is our actual lead qualification workflow and we can see that it's been added to our development
[07:15] environment and we also have a production environment. It hasn't been setup for production yet,
[07:20] so we're going to go to Cloud and we're going to ask it to do it for us.
[07:24] The task has been added to dev environment in trigger.dev but I don't see it in production
[07:36] environment. Set it up for me. Okay, and now that it's finished working, it says that it was
[07:42] deployed successfully. We should be able to go to our dashboard in trigger.dev.
[07:47] We are in production environment and we can see that we have the task. We have our workflow
[07:51] in production too. So we can see this in development and production. So let's go back to VS Code
[07:58] and Cloud Code is reminding us that we need to add the Anthropic API key as an environment variable
[08:04] in the trigger.dev dashboard. And why do we need the Anthropic API key? This is going to be for our
[08:10] workflow. We are building an AI lead qualification workflow. This means that we're going to be sending
[08:15] the information about a company to our workflow where an AI is going to be analyzing this
[08:20] information. And that AI is going to be a model from Anthropic. You could replace this with an
[08:25] open AI API key, Gemini, whatever you want. In this case, I'm going to be using Anthropics.
[08:31] So to create an Anthropic API key, I'm going to go to platform.clod.com. I'm going to go to get
[08:37] API key. I'm going to create a new key. I can name it AI lead qualifier add. I'm going to copy my
[08:45] key. I'm going to close this. I'm going to go back to trigger.dev dashboard. I'm going to go to
[08:51] environment variables. I'm going to select add new key. I'm going to pick both development and
[08:59] production. Ideally, you would want to have a different key one for development and one for production
[09:05] so that you can keep track of which environment is using each key. And you have more control over
[09:10] the usage and the costs. But to simplify this demo, I'm just going to be using the same key for both
[09:16] environments. I'm going to paste my key here and for the name, do a Anthropic API key. Let's go
[09:23] double check the name. Anthropic API key. Okay, good. So I'm going to click on save. And this is how
[09:31] we can set up our cloud API key so that our workflow has access to cloud. Okay, so we are done. We
[09:37] have finished working on our backend. We have already created our workflow and it's been deployed
[09:43] into trigger.dev. What do we need to do next? Next, we need to create our front end. We need to create
[09:48] our website and that website needs to be connected to trigger.dev so that the front end our website
[09:55] can communicate with our workflow. So we're going to go back to cloud code. We're actually going to
[10:00] clear the conversation to clear the context. We're going to go to plan mode. And we're going to say
[10:06] now that I have my backend ready, my AI lead qualifier workflow, I want to build the front end. The
[10:17] front end should be a form where I can feel out information about a company. And when I click on
[10:27] analyze, it should call my workflow on trigger.dev. Once my workflow has finished analyzing,
[10:37] I want to see the results on my website. First, I want to see my website locally to analyze the
[10:47] design. Once the design is approved, I will want to deploy it to versatile. For the design
[10:56] of this website, I want you to use Anthropics front end design skills. If you're not familiar with
[11:05] front end design skills, it's actually a skill that's going to help us make our website a bit different
[11:11] and not make it look like it's being created by AI. It's going to help us with typography,
[11:16] colors, motions, and it's going to help us avoid generic patterns. So that our website does not
[11:21] look predictable or like a cliche AI generated website with purple gradients, for example.
[11:27] So we're going to copy the skill and we're going to paste it into cloud code. And we're going to
[11:31] ask it to use this skill when creating the website. I'm going to set this to plan mode before creating
[11:37] the website. And I'm going to hit enter. Okay, now that it's top planning, we're going to take a look
[11:42] at the plan. Here's some context. It's going to be creating the front end. We're going to be using
[11:47] the front end design skill, which in fact, we can see over here that it downloaded it and installed
[11:53] it correctly. This is Anthropics front end design skill. Let's go back to our plan. Infrastructure,
[12:00] layout, it's going to be creating the homepage and lead form. It's going to be creating the results
[12:05] page. Okay, let's go ahead and hit auto accept so that it can start creating our website and we can
[12:11] take a look at it. Okay, we can see that it started creating our website. So we're going to give it
[12:16] probably a few minutes so that it can complete the work. I'm going to accept these bash comments and
[12:21] let's give it a few minutes to continue working. Okay, it's finished working. I actually had to pause
[12:26] a video for a few minutes. It took like three, four minutes, but now it seems that it finished the task
[12:31] and it's telling me that it built a website with this infrastructure, the pages. We're going to have
[12:36] a homepage with the form and we're going to have a results page. It created some components,
[12:41] some animations. It used the front end design skills. Okay, let's now go and take a look at our website.
[12:47] I asked Claude code that I wanted to test it locally first. So this is going to be the location for
[12:53] my website, but this is local. This is only going to be living in my computer. This is just for testing
[12:58] and once I approve the design, I'm going to ask Claude to deploy it to versatile so that anyone can
[13:03] access my website. But right now we're going to test it locally. I'm going to click on this link.
[13:08] Okay, we can see our website. It looks pretty good. Taking to account that it was a one shot,
[13:13] just one prompt. It looks modern. I like the colors. I like the fonts. Of course,
[13:18] you can iterate on this if you don't like the colors. If you want a different font. If you want to
[13:22] improve the form, in my opinion, it looks pretty good. So I'm not going to change anything, but you
[13:27] could even add your logo. You could go to VS code, add an assets folder, put your logo in there,
[13:34] and ask Claude code to add your logo into the website. You could even get inspiration from another
[13:40] website that you like. There are websites like drivel.com where you can get design inspiration. You could
[13:48] maybe go to landing page and it's going to show you different landing pages. Let's say you like this
[13:53] one. You could take a screenshot or download this image, upload it into Claude code or add it into
[13:59] an assets folder here. You could ask Claude to build a similar website to this one in terms of
[14:05] UI so that you can use the same color palette, for example, or the same font. So you can see how easy,
[14:11] in just a few minutes, we build a professional looking website. In this case, with just one prompt,
[14:17] but you can definitely iterate on this and improve it based on what you need. So in our case,
[14:22] we're going to be able to type the company name that we want to analyze, the industry, company size,
[14:28] qualification criteria, urgency, pain points, and when we click on analyze, this should be calling
[14:35] our workflow in trigger.dev. So what do we want to do next? Next, we want to first, we want to deploy
[14:42] this website into versatile so that we are not going to access to that website locally, meaning that
[14:47] we are not going to be hosting this website locally on our computer, but we're actually going to host
[14:52] this on the internet. So that's where versatile comes in. So we're going to go back to Claude. We're
[14:57] going to clear the conversation, and we're going to say the website looks great. I now want to
[15:05] deploy it to versatile. Also make sure my website can communicate with my workflow in trigger.dev
[15:16] when I click on analyze. We're going to click enter. Okay, after a few minutes of work,
[15:22] it has deployed into versatile. There is one step that you may have to do in the meantime,
[15:27] I had to pause a video because these took like three or four minutes. But if you have never
[15:31] used versatile before, you're going to have to go to versatile.com. I connected it to my GitHub account,
[15:37] and that's it. Once I was logged in into my versatile account, Claude was able to do all this
[15:42] setup, all the deployment. I didn't have to do anything. So let's go back to Claude. It says that my
[15:49] site is available at this URL, and this is pretty cool. You can actually see that our website is now
[15:55] hosted on the internet. So anyone that goes to this URL can actually access this website.
[16:03] So what do we need to do next? Now we need to connect our workflow in trigger.dev,
[16:08] our backend, our business logic, with our website, with our front end. And how do we do that?
[16:13] We need to connect versatile with trigger.dev. And in order to do that, we're going to go back to Claude.
[16:19] And we can see that it's asking us for our trigger secret key. This is our trigger.dev secret key.
[16:25] And by connecting the secret key, our website on versatile is going to be able to connect to our
[16:31] workflow in trigger.dev. So Claude is telling me that I can just paste my secret key on the chat,
[16:38] and Claude is going to do all this setup. But personally, I don't like that. I don't like sharing secret
[16:43] keys on the chat. So I'm going to set it myself. And I'm going to ask Claude code where I can find it
[16:48] and how to set it up. So it's telling us to go to trigger.dev, select the project, click API keys,
[16:55] and copy the secret key. So I'm going to go to trigger.dev, go to API keys. I'm going to copy the key.
[17:03] I'm going to go back to Claude's instructions. It says that I can go to my versatile project dashboard
[17:09] and under environment variables, I can add a new variable. I can copy the value as client key. It's
[17:15] going to be trigger secret key. This is going to be for production and development. And I'm going to
[17:21] click on save. So now my versatile project knows how to communicate with our workflow in trigger.dev.
[17:28] So I'm going to go back to Claude and I'm going to say, I've already set up the secret key in
[17:36] Versailles dashboard. We're going to hit enter and it should redeploy to Versailles. Okay, after a
[17:43] few seconds, it finished working. And it's telling me that the app is live and it's ready to be tested.
[17:49] So we're going to click on these URL. I'm going to fill out company name, testing, industry,
[17:55] manufacturing, company size, 11 to 15 employees, budget range, timeline, pain points. I need to
[18:04] implement AI into my business. Additional context, we're going to ignore this. I'm going to click
[18:10] analyze. And if everything went well, this should be connected to our workflow in trigger.dev. And we
[18:16] should be able to see the run if our workflow found any issues or if it was executed correctly.
[18:21] And if everything went well, we should be able to see the analysis, the response from the AI
[18:26] here on this page. So I'm going to click on analyze. It's evaluating and it actually found an error.
[18:32] So let's go back to runs. What is good is that we can see that our front end with our back end
[18:38] are connected. Otherwise, the run would not have happened. So we can see that the task was run and
[18:44] it failed. And over here we can see the same error, the 404, then we can see over here. It seems
[18:52] from what the error message, it seems that the name of the model that we are trying to use does not
[18:59] exist. So we're going to copy this error and we're going to ask Claude to fix it for us. What is also
[19:05] really good is that we have tested an error scenario and we're able to see that our website is capable of
[19:11] catching that error. So in terms of UI, this looks pretty good. It's not like the website broke.
[19:16] It's letting us know that there's an error with the name of the model. We can try again or we can go
[19:22] back to our home website. So in terms of UI UX, I really like this. So let's go back to Claude.
[19:30] Let's paste the error and we're going to say I tried running the workflow, but I got this error. Fix it
[19:38] and redeploy. It has identified that the name of the model is wrong and it's going to update that.
[19:43] And now it's redeploying to trigger.dev and versatile. Okay, it's finished working. It has redeployed.
[19:49] So we're going to go back to our website. We're going to fill out this again, industry, manufacturing,
[19:56] company size, annual budget, timeline. I want to implement AI. We're going to go to analyze.
[20:03] I really like the in-progress website too. Okay, so now it's working and we can see our results page.
[20:09] It's giving us a lead score. It's telling us that it's a warm lead. After the AI has analyzed our lead,
[20:15] it's telling us how qualified it is. It's giving us a score of 68 over 100. It says it's a warm lead.
[20:23] I know if you saw it, but when this loaded, I really like the animation. I really like the website overall.
[20:29] The icons, the colors, taking to account that this was a one-shot prompt. And honestly,
[20:35] it looks fantastic. If we had not used the front end design skills, it would probably not be looking
[20:41] like this. So I highly suggest that you use that skill when building front ends. So we have an AI
[20:46] summary. We can see a score breakdown. And finally, as next steps, it's suggesting us to do a
[20:53] discovery call to identify specific AI use cases, to identify also who is the decision maker,
[20:59] and to develop a concrete ROI framework about AI in manufacturing companies. We could also click here
[21:06] and analyze a different lead. But honestly, I am impressed. In less than an hour, we were able to
[21:11] create a workflow and build a website so that anyone is able to interact with our workflow. So if we go
[21:18] to trigger.dev, we go to runs, we're going to be able to see here. This is the run, the workflow
[21:23] that was executed. We're going to be able to see the information about that execution. And over
[21:28] here, we're going to be able to see the payload, which is the information that we entered on the
[21:33] form about the company. And we're going to be able to also see the output. This is the final
[21:39] information that the AI is giving us after analyzing the company. And this is the exact same information
[21:45] that we are showing on our website. So to wrap things up in this video, we were able to create a workflow
[21:52] deployed to trigger.dev. We created our website. We created our front end. Remember, we used
[21:58] Anthropics front end design skills to create a better looking website. We deployed our website to
[22:03] verso and deploying our website to verso allowed us to access our website from anywhere and also allows
[22:10] anyone to access our website and use our workflow in trigger.dev. Because now our website on verso
[22:16] is connected to our workflow in trigger.dev. And this is basically how you create a full stack app.
