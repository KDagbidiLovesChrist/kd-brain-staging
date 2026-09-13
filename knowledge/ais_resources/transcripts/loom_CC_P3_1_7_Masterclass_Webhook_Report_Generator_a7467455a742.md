# Loom Transcript · CC_P3_1.7_Masterclass_Webhook_Report_Generator

**Source video ID:** a7467455a7424d3f9797f3a339d4306a
**Loom URL:** https://www.loom.com/share/a7467455a7424d3f9797f3a339d4306a
**Detected language:** en (probability 1.00)
**Duration:** 967.9s

---

[00:00] Okay, let's take a look at our second masterclass here.
[00:02] We're going to be building a webhook triggered report generator.
[00:06] So basically we're going to have a webhook coming in, and it's going to fire the triggered
[00:10] to have tasks.
[00:11] That way, the task is going to get a payload from the webhook that has the form filled, so
[00:16] that we filled out.
[00:17] And then it's going to generate a dock file and generate a report on that, and then it's
[00:23] going to put it into our Google Drive automatically, and we touched nothing.
[00:28] So let's review real quick what is a webhook, basically digital doorbell, it's a URL, it's
[00:33] listening for the incoming data, and then it wants something, receives it, it wakes up
[00:38] and then it runs, and it has the data coming with it.
[00:42] For this, we're going to be using an IDN web form and HTTP requests, since we're all very
[00:47] familiar with that.
[00:48] So step one, we need to obviously plan in plan mode through block code.
[00:53] We're going to give it a prompt.
[00:55] We copy paste this exact one, but I want to build a triggered to have task triggered
[00:59] by a webhook via an IDN form slash HTTP requests.
[01:05] It receives a JSON payload, so that's how we're going to be sending the data with our fields.
[01:10] So we'll put in our fields right there.
[01:12] It'll generate a dock extra ports, and then it'll save it to Google Drive.
[01:16] Here's where we get into the logging, the air handling, so that everything's taken care
[01:21] of from the initial prompt.
[01:23] No midrun questions, handle errors without crashing, log every step, help me plan this.
[01:28] So then Cloud will start planning.
[01:30] It might ask some of these questions like, well, what are the report sections you want on
[01:34] the document, what Google Drive folder do we need to put it in, what's the format, what
[01:38] happens if I fail?
[01:39] So again, it might ask you stuff, it might not, it might ask you different stuff, so just
[01:43] be prepared for that, make sure you read and follow along.
[01:46] So then we're going to review the plan.
[01:50] It'll generate the TypeScript report.
[01:54] Let's look at the fields that it's mapped out.
[01:56] It's going to produce the document file, the Google Drive.
[02:00] We're going to check all of this and go from there.
[02:02] So I'm going to go to Cloud Code right now and paste in this prompt.
[02:06] Okay, so we're back in Cloud Code here.
[02:09] I have the prompt paste that in, the only thing I did was add our fields, which we know is
[02:14] going to be company name, industry goal, and challenge, and we're in plan mode.
[02:19] So we're going to let that go and let Cloud Code think and give us a plan.
[02:25] Okay, so Cloud Code is finished with the plan.
[02:28] Let's take a look now.
[02:31] User wants to trigger a debit task, triggered by Naden requests.
[02:36] She sees JSON payload, so it's highlighting everything that we wanted at bullet points.
[02:42] It's going to create the TypeScript file and it in configuration, which is what we'll handle.
[02:55] Critical files, already referenced in, so we'll need our Anthropic API, all of our Google
[03:03] APIs, and then it looks like we're going to need a Google Drive folder ID, which is optional.
[03:10] If we don't provide the Google ID, it's going to just put it in our core Google Drive folder,
[03:14] which may or may not work, but if you want to say organize, which I recommend, we can do
[03:19] that.
[03:20] Error handling summary, verification, okay, so we're going to hit yes and auto accept.
[03:28] So now Cloud is going to start actually building and implementing the plan.
[03:33] Okay, so Cloud Code is finished.
[03:38] Let me go back and show you there.
[03:41] So originally, we were going to use tally for this for web form, but that did not work.
[03:47] We'll work out from the API standpoint, so we're going to use in it in.
[03:50] That's why you see tally on here, not by sure it went back to that, but cool.
[03:55] So it's got our TypeScript report.
[03:57] If we look at that real quick, so it's importing the criteria there, here are the types of from
[04:06] the payload.
[04:07] We've got company name, industry, challenge, goal, that's great.
[04:11] We have a success run status where partial it's going to do.
[04:15] This is where it looks like it's going to normalize the in it in form label, so everything
[04:18] comes across how we want it to be okay.
[04:23] There's the task.
[04:24] Okay, so it's built all this.
[04:26] If we go back to our trigger.dev, now we should see a new task in there.
[04:30] So this is our web book report task, and that is great.
[04:35] All right, so step three, let's do a test prompt.
[04:39] So we're going to tell Cloud, hey, start the dev server tests, report task with this payload,
[04:45] we're just going to give it a company name, industry, challenge, and goal.
[04:50] And then see if it will go all the way through, create the DocX file, put it in Google Drive,
[04:56] and so on.
[04:57] All right, so we've told Cloud to, hey, go in and start the dev, and do a test task, basically,
[05:03] we gave some information.
[05:04] So we're going to do some bash commands here, while it's going to start that up, says dev
[05:09] server is up, now let me trigger the task, so we're going to, yes, go ahead and do that.
[05:15] All right, so if we go back over to trigger.dev now, and we go to Runs, we can see that it
[05:21] did just complete, it went through all the steps, there's the payload information in the format
[05:27] that it said, and the information that we gave it, and then looking at this, it shows us
[05:34] what the file name is of the DocX file, and then says the runtime and then Google Drive
[05:41] open report, so if I click on this, it's going to open it over here, which I can show you.
[05:47] And so now it's given us a Doc file with the name, and then it's figured out all of these
[05:56] paragraphs, and again, we can, you know, specify, we didn't specify, but it came up with the
[06:02] executive summary, industry context, challenges, and all that, based on those four, just tiny,
[06:08] bit of information coming across, so very cool, that's in our Google Drive, that's working great,
[06:13] so now we need to get it hooked up to the Niden form with the web, with the HTTP requests, so we're
[06:24] going ahead over to Niden right now. Okay, so inside of our Niden, we need just two nodes, we need
[06:32] a form submission trigger, which if we go in, this is what it looks like, very, very basic,
[06:41] obviously when you want, this is just for the test, for the example, for this part of the masterclass,
[06:46] but if there's a form system that you use that does accept webhooks and API, you can definitely
[06:53] do the same thing with that, but since we all are familiar with Niden for right now,
[06:57] this was the best way to kind of show how this works, so we've got our four fields,
[07:03] gave it a basic name, the submit button there, stop listening to that,
[07:09] so here we've got the four elements, so that's what it says, it's a text input, and so on,
[07:13] if we wanted to add more, we can give it a label and choose what type of input is there,
[07:20] if you do add something that's other than a text label, you might have to change some of the payload
[07:25] JSON information there, that we've got right there, okay, so that is the form, and then you need to
[07:35] add an HTTP request node, the method will be post, the URL here, this is the format, and then for this
[07:44] part right here, I'll make it a bit bigger, you're going to insert your task ID, which is really just
[07:51] the name of it, so for this particular one that I'm showing you here is called webhook-report,
[07:58] so if I come back over here, it's under my production here, webhook-report, so you need to just put in
[08:07] whatever yours is called, whatever cloud named it, or you told cloud to name it, you're going to put
[08:12] that in there, so authentication, you can set to none, we're just going to send headers this way,
[08:18] obviously there's different ways you can do this, so we've got send headers turned on, using the
[08:23] fields below, the name is authorization, and then we're going to put bearer space, and then we're
[08:31] going to put our API key ID, so if we're back into trigger dev, we'll go to API keys on the left,
[08:40] then here is our secret key, you can just click this to copy it, and we're going to paste that,
[08:46] make sure you do bearer space, and then paste, and then that's good, and then we're going to send
[08:52] the bodies, so this is basically going to take the fields, we want to send the body content as JSON,
[08:59] using the fields below, we're going to name it just payload, and then we'll do JSON here, so that's
[09:07] going to take all of it here, and I'll put it right there, so that is all ready to go right there,
[09:15] and then when you're ready, you can execute this step, you can do fill out the form, test company,
[09:24] test industry, just challenge, test goal, and then you send it on its way,
[09:33] over here you can see the output, there's everything we just put through, and then the HTTP request
[09:41] is here, and that output there, so then we can go back to trigger dev, and we can see
[09:50] running right here, so there it's executing, if we can click on it again, we can watch
[09:54] everything in real time, over here on the payload, you can see it did come through, since we're in
[09:58] trigger dev now, that is all great, and then the next step would be going to our Google drive, and seeing
[10:08] that doc file generated, so here we are, I opened up the file, test company report, we didn't really
[10:15] give it real information, just test stuff, but still generated the report, in those same categories,
[10:22] test company faces, primary channel, set it on, test challenge, right, so it worked, everything
[10:27] came through, obviously it would break it down based off of the actual information that you gave it,
[10:34] but yeah, that is working really great, all right, so we have our form, it's sending the information
[10:40] to trigger dev, it's generating the port, it's putting it in our Google drive, so now to kind of connect
[10:46] all the pieces from the master classes that we've done, right, trigger dev is still being triggered
[10:52] from Claude as of right now, so what we need to do now, remember GitHub is going to house all of our
[11:01] code files in the cloud, so that it's not on our local device, so now we need to tell Claude to set
[11:07] up this flow to where, when we iterate with Claude, it will push the updates to GitHub, and then
[11:15] GitHub will then push on to trigger that dev that way, the latest file, the files that you've
[11:20] updated are always there and ready to go, so we're going to take this tiny little, tiny little ask
[11:27] here and give it to Claude and start setting up that process, okay, so we put it here in the field,
[11:33] let's get Claude cracking on that, so it will automatically push to our GitHub, there is one thing
[11:40] we'll have to do, looks like we can install a GitHub actions extension here into VS code, which might
[11:50] be nice for now, I'm going to just click out of that, click yes on that bash command, all right,
[11:56] so we've got one more bash command here, it says everything's wired up, another one, I think it's
[12:03] pushing it on now, so where did you go, yes, go ahead, okay, we do need to do one more thing inside of
[12:12] GitHub, we need to go and link GitHub with our trigger dev now, so let me go show you how to do that right
[12:19] now while Claude is continuing on with everything, so in our GitHub here, it's a bit bigger, up here
[12:30] on settings, so the middle menu about halfway or the middle, middle through there, down here on the
[12:36] left side under security, there's secrets and variables, you're going to click actions, okay,
[12:42] and then down here under repository secrets, you're going to click new repository secrets,
[12:49] and here, let's see what would we call that, we did trigger access tokens, this is going to be our
[12:55] trigger dev key there, so trigger access token, and then in this value field you're going to paste
[13:06] your API key, your secret key here from trigger dev, so you'll paste that in this field here,
[13:15] it updates, so now when GitHub has the files, it can connect to your trigger dev and everything else
[13:22] on the backend is configured properly, so we're going to keep allowing these bash commands,
[13:29] and we'll go from there, okay, so to give it the final test to make sure everything is live and
[13:35] working, you're going to go back to anything and make sure you publish so that it is live production,
[13:41] you're going to take your production URL for now, open that up, and then type in a new one here,
[13:47] so we'll do Acme Builders, Industry, Construction, Resources, I'm just typing in random stuff,
[14:01] and then go more building, it's right, we'll hit submit, that's great, so then again, with the web
[14:10] form, you can use this in AIDN form or use another one that can do the API, but you can embed it on
[14:16] a website, put it in an email, that sort of thing, so I've submitted the form, let's go over here
[14:23] to trigger dev and refresh, and now we can see that it's executing, we'll click on it and watch
[14:28] that in real time, there's our payload, Acme Builders, Construction, Challenges, New Resources,
[14:34] Buildings, okay, so that's going, and then we will check our Google Drive to see if the report is
[14:42] generated, so let me refresh this page over here, that's sure enough, there it is, let me open it and
[14:47] bring it over for you, there it is, just like we needed, so everything seems to be working great,
[14:58] again, Cloud Code might have those different steps for you, just pay attention and read if there's
[15:03] any errors, copy that error, paste it in to Cloud troubleshoot from there, and yeah, you now have
[15:13] this hosted in the Cloud going on its own, whenever someone fills out that form and you are just waiting
[15:23] for the file to show up in your Google Drive to do what you want with them, all right, so let's recap
[15:30] this last masterclass here, so our webbook payload is our fixed input, right, we had four fields,
[15:36] you can change the fields, you can add more fields, whatever you want, but now you see the process
[15:39] flow to make that happen, we tested it locally, without the form first, then we tested it locally
[15:45] with the form, and then we put it into the Cloud and tested it, and it worked great, you can do
[15:51] multiple tests, just make sure it's really good, and then the webup URL is shareable or embeddable,
[15:57] however you want to do that using the inadein form for now, so this is awesome, this is the second
[16:03] masterclass done, and yeah, we're ready to move on from here.
