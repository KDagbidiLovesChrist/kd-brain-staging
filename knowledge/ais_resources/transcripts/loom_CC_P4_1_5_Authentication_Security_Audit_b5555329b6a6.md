# Loom Transcript · CC_P4_1.5_Authentication_Security_Audit

**Source video ID:** b5555329b6a644ab82086732514cb538
**Loom URL:** https://www.loom.com/share/b5555329b6a644ab82086732514cb538
**Detected language:** en (probability 1.00)
**Duration:** 728.1s

---

[00:00] All right. So now our app is live. And as long as people have our URL, they're going to be able to use it.
[00:06] And this is fine for a demo or if you're testing out cloud code, but I don't recommend you keep that app in production for a very long time.
[00:13] Because as I said, anyone can use your app as long as they have the URL. And what does this mean? It means that they can trigger your workflow.
[00:21] And they can use your A model tokens. In this case, we were using Anthropic. So they would be able to use your Anthropic tokens.
[00:28] And that means you're paying for someone else's usage. Besides that, if you want to create an app with real users, where people sign in, sign up and have their own data, we need to add these two things into our app security and authentication.
[00:41] So in this video, we're going to iterate on our AI lead qualifier and we're going to add authentication data protection and a security first mindset that you can apply to any app that you want to build.
[00:53] So we're going to go back to cloud code and we're going to be working on our AI lead qualifier app. The one that we've been working on in our previous videos, what we want to include in this project is a security and an authentication layer.
[01:05] So we're going to go to cloud, we're going to switch to plan mode and we're going to tell cloud, I want to add authentication to the AI lead qualifier, users should be able to sign up, log in and see their own leads scoring history.
[01:19] I want to set this up using super base and protect the main app routes. So only logged in users can access them. In this case, I'm going to be using super base personally, because I'm more used to it. I've been using this with an 8n and it never had any issues.
[01:32] But if there's a different platform that you prefer using like cleric or Firebase, you can definitely go ahead and use that. Or if you're not sure, you could also ask cloud code to suggest you which platform you should be using based on your app requirements and needs.
[01:47] So you could ask something like, Hey, I want to add authentication to my app, which platform should I use based on my app requirements and cloud code is going to analyze different options is going to analyze the code requirements and it's going to suggest different alternatives for your apps security and authentication.
[02:03] But in this case, we're going to be using super base. So I'm going to click enter and it's going to start creating the plan to add authentication into our app.
[02:11] OK, after a few minutes, it has finished working and it came up with a plan. So let's quickly review the plan is going to be adding super base authentication to our a lead qualifier.
[02:21] Currently, the app is fully public. There's no user accounts, no persistent history. So it's going to be adding super base to give users accounts, protect roads and enable persistent leads scoring history.
[02:33] These are the steps that is going to follow. It's going to be creating super base utilities. It's going to be building the off pages and components.
[02:41] This is for the UI, all the buttons, the inputs, the cards. This is for the UI. It's also going to be creating a navigation bar how the database for our leads is going to look like.
[02:51] OK, it all looks pretty good. So I'm going to go ahead and out of accept. So now it's going to start creating all the files, all the pages and it's going to start executing all these tasks.
[03:02] OK, after a few minutes, it has finished working and it has created all these files, super base utilities, infrastructure, navigation and history API and storage.
[03:13] And it has modified a few files. So it's pretty impressive for a one shot prompt. I've worked as a developer for 10 years. I built apps for 10 years.
[03:22] And this kind of logic and building the UI for these pages and connecting it to the database doing signups and logins back before generative AI and before cloud code.
[03:34] This could perfectly take a couple of days and maybe a week of work. So I'm very impressed by how far this has all gone. And the fact that you can do it without any technology, you can just do it with natural language. I think it's very impressive.
[03:47] OK, so now we have all our files. What we need to do next is set up super base. So we're going to go to Claude and we're going to say I've never used super base before in case you haven't held me set it up. Tell me step by step what to do. We're going to hit enter.
[04:05] OK, so let's go to step one. We need to go to super base and sign up and create a new project. OK, let's go to super base.
[04:13] You're going to need to have an account in case you don't you can create a new one with your either your github account or an email and password. I already have one. So I'm just going to go ahead and go to new project project name AI lead qualifier.
[04:27] I'm going to ask it to suggest a strong password. This password is different from our super base login password. It's actually going to be the database password region America's security enabled data API.
[04:39] I'm going to enable RLS RLS means role level security and these are basically rules that live in the database itself to avoid users seeing other users information in case there's a bug in the front end.
[04:53] So it is adding an extra security layer into our app. So I'm going to create the project next. I'm going to need the project URL which is this one over here.
[05:03] And I'm also going to need the publishable key. So I'm going to copy these two values and will be pasting these values into versatile. So this way, super base database is going to be able to communicate with our backend in versatile.
[05:17] So we are going to copy these two values from here and we're going to add these two into versatile as environment variables.
[05:24] So this way, super base can communicate with versatile, which is where we have our backend.
[05:29] But before doing this, we're going to go to cloud code and we're going to ask it to push the code that it just created into our GitHub.
[05:36] Because as you can remember from our previous video, our backend, which was hosted in versatile gets automatically updated whenever we push something into GitHub.
[05:46] So we need to push this code into GitHub and it's going to be automatically deployed to versatile.
[05:51] Once we do that, we're going to go to versatile and we're going to add these two keys in the environment variables.
[05:57] So the first one is the super base URL. So in versatile, we're going to go to settings, environment variables, we're going to add a new environment variable.
[06:07] The first one is going to be our super base URL. We're going to add another one. This one is going to be our key.
[06:13] We're going to click on save and we're going to redeploy.
[06:16] Okay, it has now been deployed. So we're going to copy our versatile URL.
[06:21] We're going to go to super base. We're going to go to authentication URL configuration.
[06:26] And we need to add our versatile URL over here. We're going to save changes and cloud code is also telling us that we need to add a redirect URL.
[06:35] So we're going to add it over here under redirect URLs. We need to replace this part with our versatile app.
[06:43] Okay, now it's ready. So we're going to save it and final step. We need to run the database migration.
[06:49] So in super base, we need to add a new query. This is to basically create a new table for the leads and don't worry if you don't know how to create a query because cloud code has started for you.
[06:59] In my case, it created the contents of that query in this file. So I'm just going to go ahead and copy this.
[07:06] And as you can see here, there's no need for you to understand what it says here, but it's basically creating a new table called leads.
[07:13] So I'm going to copy all these. I'm going to go to super base and go to the SQL editor.
[07:19] So over here, I'm going to go to SQL paste and I'm going to click on run.
[07:25] As we can see here, we got a success message. So the lead stable has now been created.
[07:30] And this was the final step of the setup. So if we go to versatile and we navigate to our app, we should now see that our app has been updated.
[07:39] And we now have a login page with email password. If we don't have an account, we can go to sign up.
[07:45] So we also have a sign up page. And since I don't have an account yet, I'm going to go ahead and create one.
[07:51] Create account and I can now access the lead qualifier.
[07:56] This is a website that we had created in our previous video where we would fill out this form with the company name industry and we would analyze the lead.
[08:04] But now we can also see that besides having the login and sign up pages, we also have a navigation bar here at the top where we have details of our account.
[08:13] We can sign out if we want to and we can see a history page here. We're going to be able to see a history of all the leads that we had analyzed before.
[08:23] So we can click here and after we have analyzed a few leads, we should see a list of leads over here right now.
[08:30] These are first analysis on this account. So we don't have any leads yet, but we can go ahead and run a new analysis.
[08:37] We're going to add company name, testing, healthcare, budget, timeline, pain points, and we can click on analyze.
[08:56] This has triggered our workflow in trigger dot depth and it's analyzing our lead.
[09:02] And after a few seconds, we're going to be able to see the final report as we used to see in our previous video.
[09:08] We can see the score breakdown. The difference is that now if we go to history, now we're going to be able to see the analysis of this lead.
[09:17] So now we have an account with our username and an email. And when we log in with our email, we're going to be able to see the history of all the leads that we have analyzed before in our previous video.
[09:28] So if you can remember, we didn't have any of these. We didn't have login. We didn't have an account. And after we had analyzed a lead, if we closed the browser, we would have lost that information.
[09:38] In this case, since we have a leads table in super base, we are now able to save this information. So whenever we log in, we're going to be able to see it.
[09:46] And this is how we just a few prompts. You're going to be able to go from having a simple workflow that you can use yourself to having a full up with security and with authentication.
[09:56] So you can control who can access your workflow and your users can now have their own account with their very own history and their account information.
[10:05] And before we wrap up this video, there's one thing that I want to show you. I'm going to show you how to run a security audit to make sure that our app is safe for other users.
[10:14] So we're going to go back to cloud code. I'm going to clear the conversation and I'm going to tell Claude, I want you to audit the code base for security issues.
[10:23] I want you to check that all protected routes require authentication. No API keys are exposed in the front end code environment variables are used for all secrets and role level security RLS is enabled correctly and report anything that doesn't pass.
[10:39] So we're going to execute this and what we are basically doing here is we are asking the AI to act as a security expert.
[10:47] This way we can add an extra layer of security within our apps. After a few minutes, it finished the audit. So let's take a look. So in the results, we got the passing checks.
[10:58] There's authentication on projected routes, no API keys exposed, environment variables for all secrets, RLS is enabled, super based client separation input validation tokens coping.
[11:10] Okay, these are all the checks that passed. Let's go and see the issues that it found.
[11:16] Okay, we got one medium severity issue, low, low, three lows and one info issue. And the final verdict, there are no critical or high severity issues.
[11:26] The main actionable item is adding rate limit, which is the medium one to the qualified endpoint to prevent cost abuse.
[11:33] And finally, if we decide that we want to fix these issues, all we need to do is ask cloud code to check them out and to fix them.
[11:42] So far in the course, we have created our backend, our front end for our app. And now we have added security and authentication.
[11:50] So we now have more control over the users, over the people that are going to be using our app.
[11:56] And finally, we saw how to run a security audit to double check that there are no security vulnerabilities in our code.
[12:03] And if there was one, we could go and ask cloud code to go ahead and fix it.
