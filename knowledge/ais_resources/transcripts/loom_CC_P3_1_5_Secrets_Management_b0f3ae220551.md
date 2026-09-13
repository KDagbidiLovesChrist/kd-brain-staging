# Loom Transcript · CC_P3_1.5_Secrets_Management

**Source video ID:** b0f3ae220551440385277c9429bf857b
**Loom URL:** https://www.loom.com/share/b0f3ae220551440385277c9429bf857b
**Detected language:** en (probability 1.00)
**Duration:** 560.4s

---

[00:00] All right, before we move on and creating stuff,
[00:02] let's take us back and talk about secret management.
[00:06] How do we keep our API safe?
[00:08] So the problem is over the course of these phases,
[00:12] you've collected an order of API keys
[00:14] and Thropic, Firepower, Google, and so on.
[00:17] In phase one and two, they lived in a .amv file,
[00:21] and then Cloud Code could read them locally there
[00:23] and the file browser, right?
[00:25] But phase three is going to introduce two new challenges.
[00:28] So GitHub is not a safe place for secrets, right?
[00:31] We don't want to put our APIs ever in anything public-facing.
[00:36] And furthermore, sugar.dev cannot read the .amv file, OK?
[00:41] So our solution for this is using something inside
[00:46] sugar.dev.
[00:47] So normally, with the .amv, the file is
[00:52] stored outside of your code.
[00:53] And it's only injected at the time that it needs it, right?
[00:56] So hey, go get the key from the environment.amv file.
[01:00] It picks it up where it's running.
[01:01] And then the code itself doesn't actually
[01:03] have the key in there, right?
[01:04] So on the left, the local computer has the .amv file.
[01:09] It's grabbing the code, putting the project when it needs it.
[01:13] Now, what we're going to do is use the sugar.dev Cloud
[01:18] environmental variables dashboard to store our secrets
[01:22] and API keys and stuff.
[01:23] So now when the file needs it, it will go there.
[01:25] Pull it when it needs it and then
[01:27] bring it into the project.
[01:28] So we're going to go into Cloud Code.
[01:30] We're going to give it this prompt or one very similar.
[01:33] Help me set up environmental variables for this project
[01:36] any keys for anthropic firewall Google Sheets.
[01:39] Create the .amv file.
[01:41] Make sure it is in the git ignore and set up the project
[01:45] to read from my environmental variables.
[01:47] So it's going to create the .amv file.
[01:50] Confirm that it has the git ignore, which I think
[01:52] it already created for us, which is great.
[01:54] And then it's going to update the task
[01:56] files to include the process.
[01:58] So once we do that, we're going to then
[02:01] go into the triggered.dev project settings,
[02:04] environmental variables.
[02:05] And we're going to add all the keys from the .amv file
[02:08] as a key value pair.
[02:10] And then we'll be good to go and it'll check it there.
[02:13] So three rules to follow.
[02:15] Again, we never want to paste the API keys into Cloud Code
[02:19] Chat, right?
[02:21] And we never want to commit to .amv file to GitHub, which
[02:25] I think because it starts with a period,
[02:26] it doesn't even do that.
[02:28] But again, it's just a good thing to remember.
[02:30] And then because you can generate the API keys,
[02:34] it's good to swap them out and to potentially
[02:36] use different keys for local and production when you can do that.
[02:40] So back in Cloud Code, I'm going to paste
[02:42] in what I had there to create the .amv file,
[02:46] which is looking over here.
[02:49] It doesn't look like it created .amv file, which is fine.
[02:53] It may not do that every time.
[02:54] So now it will.
[02:56] And we're going to need to get our API keys
[02:58] ready for Anthropic, FireCrawl, and Google Sheets.
[03:05] We're going to allow it to write to the .amv.
[03:07] Yes, that's fine.
[03:10] Yes, to write the example.
[03:12] And now, like it said, it's going to update the code
[03:16] to know where to pull it from.
[03:18] All right, so it's done.
[03:19] Here's what was set up the .amv file.
[03:21] We'll fill in the keys.
[03:23] It's already going to be get ignored.
[03:28] It's set up a .amv.example.
[03:31] So it's a safe to commit template, which is great.
[03:33] Trigger.config.ts.
[03:35] So that's what it synced those five keys
[03:37] to deploy the trigger.dev when it's ready.
[03:42] So we're going to take a look at the .amv file.
[03:47] If we click on it over here, it's
[03:49] going to open another window.
[03:50] And we can see we just need to paste our API keys
[03:54] for all of these things here.
[03:57] So that right there is good to go.
[03:59] So I'm going to get my API keys and put them in here right now.
[04:03] OK, so how to work with this a bit.
[04:05] I'm glad that it did this.
[04:06] So you remember my initial .amv.
[04:09] It was saying Google Sheets Service account.
[04:11] I doubt any of us are doing service account.
[04:14] I think we've all been doing the OAuth.
[04:15] So I've gone back to Cloud.
[04:18] And I've told it to, hey, we're using OAuth.
[04:21] So you can see it went in here to the .amv file
[04:24] and it changed it.
[04:24] So now it's clan ID, clan secret, a refresh token
[04:27] and the sheet ID.
[04:29] So it's done that.
[04:31] I'm going to walk you through where
[04:32] to find all of these again as a refresher.
[04:35] And then I'll show you again where
[04:36] to pull the Firepower API key.
[04:39] So we need to open up our Google Cloud account
[04:42] that we've set up phase one ago.
[04:46] I believe console.
[04:48] Let me move out of the way.
[04:49] Click on console up here.
[04:52] OK, we'll make this bigger.
[04:54] OK, so over here on the left, we'll
[04:56] click the navigation API service and then credentials.
[05:00] All right, and then we have our OAuth to clan IDs
[05:04] that are set up here.
[05:04] We can click on it here or the pencil over on the right side.
[05:08] So your clan ID is here at the top.
[05:13] You want to copy that and put that in there.
[05:16] Down at the bottom here is the clan secret,
[05:18] which you won't have access to.
[05:19] So you will have to add a new one, which I've done.
[05:22] And then you'll have the copy button there.
[05:24] And you'll be able to copy that.
[05:25] So you've got the clan ID, the clan secret.
[05:29] Those are those two there.
[05:31] Now you're sheet.
[05:32] What you'll need to do is go to a Google sheet.
[05:36] We will need to go ahead and make one for this project anyway.
[05:41] So this will just give us a nice little head start.
[05:45] I've got one made here.
[05:46] It is completely blank.
[05:47] We'll set this up later on.
[05:48] But your sheet ID, if you look up at the URL,
[05:52] it'll say spreadsheets, forward slash with a D
[05:55] or a single numeral.
[05:56] But after that slash, you have a really long code there
[06:01] before the next slash at the edit.
[06:02] That is your sheet ID.
[06:04] You can copy that, put that in there as well.
[06:08] Those are our Google ones.
[06:09] And then for Firecrawl, if we just go to Firecrawl.dev there,
[06:17] we want to make sure we are signed in.
[06:20] And then once you're signed in down the bottom left on the sidebar,
[06:25] you have API keys.
[06:26] You'll click on that.
[06:28] And you'll have one right there.
[06:29] If you don't, you can click Create to add one.
[06:32] We'll just copy that, paste it in.
[06:35] If you don't have a Firecrawl account for any reason,
[06:39] you can sign up.
[06:40] There's a free plan.
[06:41] It has API access.
[06:43] And you'll be good to go for that portion.
[06:48] So once we have the API keys we need,
[06:52] we need to go back to sugar.dev.
[06:56] And then over here on the bottom left,
[06:57] almost exactly where we were in Firecrawl.
[06:59] You'll see underneath Manage Environmental
[07:02] Variables, you'll click on that.
[07:04] Here it'll say, you haven't set up any environmental variables yet.
[07:08] If you haven't, we'll click Add New.
[07:11] OK, this is important.
[07:12] We want to be sure to check both development and production,
[07:17] because before I remember, you can set different variables
[07:22] for different ones, which you totally could.
[07:25] But for this right now, I'm going to just
[07:27] do the same secrets for both production and development.
[07:31] So down here, you don't need to check the secret,
[07:34] but you've got the key and the value.
[07:38] And then you can click Add Another, Add Another.
[07:41] And we're going to go back and forth and add all of them
[07:44] from the .env file and put them there.
[07:50] So we're going to do the blue part and the front,
[07:55] the white value in the back.
[07:57] So go through, do this for all of your variables.
[08:03] Let's say that I was done.
[08:04] We'll hit Save.
[08:06] And then there you'll see them listed the Firecrawl API key.
[08:10] You'll have the development one and the production one
[08:12] easily copied right there when you added it, who added it,
[08:15] and so on.
[08:16] So do that for all your API keys and variables there.
[08:19] And then we'll be ready to move on.
[08:21] All right, so let's recap from this past video here.
[08:26] The environmental variables in Trigger.dev
[08:29] are where we keep all of our secrets, our API keys,
[08:33] the client IDs, that sort of thing.
[08:35] It gets it out of the .env file, which we know we can't bring
[08:40] with us into GitHub.
[08:43] So the local one is the .env file in the cloud,
[08:46] where everything will live in Trigger.dev.
[08:48] It's the same, but we're storing them there.
[08:52] Claude has created our .env file.
[08:55] It's added to the Git Ignore, which we confirmed.
[08:58] And it'll update our test there.
[09:00] Again, never share the API keys in Claude.gov chat,
[09:03] or any chat, for that matter.
[09:04] And yeah, so from this point on, these first five videos,
[09:07] we've introduced the concepts and introduction
[09:11] of what we're building.
[09:12] And we begin setting up our accounts,
[09:14] getting everything connected, the not-so-fun stuff.
[09:18] Next, we're going to start actually building.
