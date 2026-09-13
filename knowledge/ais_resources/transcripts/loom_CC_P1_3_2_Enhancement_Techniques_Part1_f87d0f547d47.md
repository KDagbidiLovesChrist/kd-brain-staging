# Loom Transcript · CC_P1_3.2_Enhancement_Techniques_Part1

**Source video ID:** f87d0f547d474b6a8b367739ef7a16ee
**Loom URL:** https://www.loom.com/share/f87d0f547d474b6a8b367739ef7a16ee
**Detected language:** en (probability 1.00)
**Duration:** 901.2s

---

[00:00] Okay, so let's look at some error handling with our current workflow,
[00:03] and for this we're going to start with the logic side of things, and that'll make sense to your
[00:07] second. So, our enhancement number one, we're going to look at just error handling in general,
[00:13] right? So, our problem could be what happens if the vector store is empty or it returns with no results.
[00:21] So, our request now that we can talk to cloud with could be something like, hey,
[00:26] add error handling for cases where the vector store doesn't find relevant policy information.
[00:31] If no good matches, create a draft saying we'll research it, and we'll get back to them. So,
[00:36] remember back in module two, originally when cloud gave us the plan, it asked a clarifying question,
[00:41] hey, if we have to write an email where there is nothing, what do you want us to do? So,
[00:46] now we're kind of going back. Cloud was already thinking this ahead, but now we're like, you know what,
[00:50] we need to add that. So, we're going to jump back to cloud, we're going to give it this information,
[00:54] and then have it start making those changes. Some of the things it could ask is what,
[01:00] just a threshold for no good matches, right? So, again, we don't know that this is what cloud's
[01:05] going to ask, but these are good things to think about. And really just a good process in places,
[01:11] if you're about to ask cloud to make it change, or you want to make it change your workflow,
[01:15] think about what those next questions could be for that specific change. What should be the fallback
[01:21] message, right? And you still want us to create a draft. So, we can think maybe we want to have a
[01:27] polite message, hey, we'll research this, respond in 24 hours, and then yes, still create a draft,
[01:32] or, and then maybe there's a relevant score, like if it's, there's no results at all, then
[01:38] that's a pretty good threshold, I would say. So, let's go to cloud and put that in and see what we
[01:43] come up with. All right, back in cloud, add error handling for cases where the vexware doesn't find
[01:48] a relative call information. If no good matches, create a draft saying we'll get back to them. So,
[01:56] for this one, let's ask before edits, I want to see what it's going to do, right? And let's give
[02:03] that blessing, that approval on what's going to happen. So yes, go ahead and proceed,
[02:09] cloud's going to do its thing. I think we're all pretty used to this by now. Okay, so cloud's come
[02:13] back with an updated to do list for itself. It's going to update the AI agent system prompt to
[02:19] output confidence markers, right? So, remember we're kind of talking about that. It's going to add a
[02:23] code node to parse the confidence marker instead of flag. Add a if node to branch on policy match,
[02:31] and then looks like add a draft need research gmail node for no match cases, rewire connections
[02:37] and validate workflow. So, looks like it's going to do those steps that I just said. We've
[02:44] going to give it permission right now. Looks like the AI system prompt is going to output either policy
[02:49] found or no policy found, and that will kind of split that out for us. Okay, so it's updated the flow.
[02:57] There's three new nodes that are added. I won't read this, we're just going to let's go check.
[03:02] We've got a code node and if node, and then a new gmail draft node. So, let's go take a look back
[03:10] and in it and see what that looks like. So, here, let me just refresh and make sure this is the latest
[03:15] and greatest. Okay, so if you guys remember out of this AI agent last time, we had our create email
[03:24] draft node. So, now, these three, this one our code node is if node, and then this double gmail node
[03:33] are three new ones. So, let's take a look at this code node. It looks like it's going to be taking
[03:41] from this. Remember our system prompt is updated now. So, right there it says
[03:47] if policy found use this, if no policy found use that, and that's what's coming into here.
[03:56] It's got this code, and then true and false. If it has a match, if it doesn't have a match,
[04:03] if it does, true is going to come up here, or it should. It's going to draft a reply just like
[04:08] we had before. And then if not, it's going to draft on here, and it looks like let's see what the
[04:17] nice message is if we don't have the information. Thank you for reaching out. We've received your
[04:22] inquiry. I want to be sure we provide you with most accurate health information. We're researching your
[04:26] question. We'll get back to you in one, two business days. Okay, so that looks okay. Let's send
[04:35] ourselves an email and test this. So, let's ask a tech support question, but let's do it in a
[04:43] way to where we know it's probably not in those documents. See how this is going to handle this.
[04:48] So, I've got a shipping and subject line, and I'm asking if there's international shipping because
[04:53] the document does talk about shipping to all US states. So, I'm going to see how it's going to
[04:59] handle shipping. And we'll see what happens. So, back to Niden. Let's click the manual for Gmail.
[05:08] Okay, so it did pass that it was technically relevant. Now it's checking if it's in the policy.
[05:17] It has a policy match. It was false, which is these. This is a new one. This is a new one. And then
[05:22] it went down to our third new one, which is drafts needing research. So, this should have our nice
[05:28] message that we had. And if I go back to drafts, let's see the customer. Thank you for reaching out
[05:37] to catch more of our procedure inquiry. We want to make sure to provide you with accurate. So,
[05:41] that looks great. And this is actually formatted better than our original email. Remember,
[05:46] that was all just smashed. This is, we've got paragraphs. We've got line break after best regards. So,
[05:52] cool. That's working great. All of it is green. So, I would say it did this, right? We asked about
[06:01] international returns, and we got the fallback. It didn't hallucinate the information. So,
[06:06] that was a great first enhancement. Okay. Let's move on to a second enhancement with time-based
[06:12] filtering. So, currently, we're processing all unread emails, including older ones, right? It's
[06:18] checking, I think, right now every 15 minutes. And it's going to process all of them.
[06:25] Let's request that we only process emails from the last 10 minutes, and it's going to ignore
[06:31] all the older ones. So, let's give that a try. What cloud might do, again, we don't know what cloud
[06:39] will do, but one fix would be it could add a time check after the Gmail trigger, that first note,
[06:45] and it could figure out the time difference and then route it. So, route one, if it's within 10 minutes,
[06:50] it'll go one way. If it's older, it would in the workflow. I think in the real world, you would
[06:56] want to respond to all tech emails regardless of when they appeared, but just as a test to show,
[07:02] again, iterating, getting cloud to help, update, and enhance things. We're going to go this.
[07:08] Okay. So, let's jump over to cloud and give that a test. Okay. So, in cloud, we have, you know,
[07:13] let's make this a little nicer. Let's add filtering. So, we only process emails from the last 10 minutes,
[07:19] ignore the older ones. All right. I'm asking for edits, and let's send. All right. Let's see what
[07:28] cloud comes up with for this enhancement. Okay. So, cloud came back with some updates for this. So,
[07:34] it looked through the Gmail node to see some options, and it actually said that Gmail has a query syntax,
[07:43] and so now it says it's added a newer than 10 minutes within our trigger nodes. We don't even need
[07:49] to add a time-based one. All right. So, back inside in it in, we'll open up the Gmail trigger,
[07:54] scroll down, and ensure that under filters, we have newer than 10 minutes, and then we still have
[07:58] the unread emails only. So, that's great and made this change. Okay. So, what I had to do to get this
[08:04] test to work, since we're only choosing whatever the last email was, I've deleted some of the test.
[08:10] The last email I have that's unread is from the Automation Society. It's a weekly digest, right? So,
[08:16] they come in here and execute. It's going to go through, and it's going to skip, because it's not
[08:21] relevant. And there's a couple of reasons why that's not relevant. Obviously, the customer is not
[08:29] seeking technical support, but it's also way over 10 minutes ago. So, I'd say that's working very
[08:38] nicely. All right. So, then we'll move to our last enhancement for this section, which we want to
[08:43] filter out auto replies, or similar, right? So, we get marketing newsletters, auto replies,
[08:49] that sort of thing. So, we're going to ask God to filter out automated emails out of office,
[08:54] delivery notifications, newsletters, all that, and to skip those no reply addresses. So, again,
[09:01] we don't know what cloud's going to do. It could set up something to check the email headers for that
[09:06] auto reply indicator. It'll check the sender address for no reply patterns, the subject or
[09:13] body for out of office or unsubscribed. And then, if it is automated, or any of those things check
[09:18] out, then maybe it'll just in the workflow. If it's a no reply at some email, it'll stop. If it's
[09:23] out of office in the circuit line, it'll stop. It's a normal question, like we've been testing before,
[09:28] it should continue on and still process. So, let's jump back to cloud, give it this new ask,
[09:34] and see what it comes up with. All right. So, back in cloud, filter out automated emails,
[09:38] out of office, deliver notifications, newsletters, and skip no reply addresses. So, we'll send that and
[09:45] see what it comes up with. Okay. So, cloud's been going a little while now, but as I'm reading this,
[09:52] something very important has happened that I feel like I need to address. So, if you remember,
[09:58] what I sent, all I sent was filter out automated emails out of office, delivery, and whatnot.
[10:06] I didn't really give context to cloud on where that needs to take place. And if you remember,
[10:14] once you start building a lot of workflows, cloud has access to all of them.
[10:19] And so, as I'm reading what initially happened, is cloud started building a new workflow,
[10:25] because I didn't go into more details about specifically. So, now it's talking about
[10:31] building automated filter workflow with iMapTrigger, et cetera, et cetera. So, I stopped that.
[10:37] And then I sent a new one in our current Gmail reply overview,
[10:42] filled let's filter out, et cetera, et cetera. And now it's saying, let me find your existing one.
[10:48] And then they say, that looks like it's the gadgets and more customer support email agents.
[10:52] And now we're on the right track. So, as you start going, be careful of your words that you're
[10:58] using, again, the plain language, which is what's be specific, especially if you have more than one
[11:03] workflow, or don't let it believe you want a brand new workflow. So, in our workflow, we're working on,
[11:08] we're using the workflow name that cloud has created, and then you'll be good to go.
[11:13] Okay, cloud is wrapping up here. It says it was successful. It looks like it's going to add a filter
[11:18] after the trigger. And before the classification, it's going to filter out the no reply,
[11:25] all of the versions, postmaster, bounce, newsletter, marketing, notification system, everything,
[11:30] the subject lines, the code node ads is automated and Boolean, and filter reason to each email.
[11:39] Okay, so let's jump over to NADON and see what this looks like. So, I'm going to refresh our workflow.
[11:44] Should have a brand new node right after the trigger. We do. There it is.
[11:49] Filter automated emails. It's got all of that that we just looked at, but in code
[11:54] form here, and then let's move these around so we can see if it is automated,
[12:05] which is an email we don't want to respond to, it's going to come up here and skip. It'll stop.
[12:10] It's not automated. It can continue on and go through all other filters. So, we have three filters
[12:16] now. If it's automated, it stops. We go here. Is it tech support? It continues. If not, it stops.
[12:22] And then over here, is there an answer to the tech support question? If it is, we'll draft a
[12:28] reply. If there's not, it goes here. So, we're getting very, very advanced with this now. So,
[12:33] really the only way to test this now is to trigger it manually. The last recent email I have
[12:38] is a weekly digest from AI Automation Society. So, this should trigger it to go to skip right up here
[12:46] at the top, because it is not. Okay, so it looks like it didn't catch that. So, it passed through
[12:54] the is automated filter, but it didn't pass the tech support. So, that's correct, but it should have
[13:01] stopped and gone here. So, if I go back and look at the email, the email address is no reply at school.com.
[13:08] So, that should have filtered out. Let's go back to, again, there's no errors here, but it's not
[13:16] giving us our expected results. So, we'll go back to cloud. Let's see. An email with no reply
[13:26] was able to bypass the new filter. You check it to be sure it catches emails with
[13:48] send that to cloud. Obviously, to test all of these, you know, you'd have to
[13:56] get those no reply emails into you or sign up for a new newsletter, get a newsletter into you,
[14:01] but let's see. Cloud's going to look at the JavaScript that's deployed and figure out a solution for this.
[14:08] So, it looks like it's case sensitive. There's saying what the error is. So, it gets undefined with both
[14:15] matches. So, now the capital F and from and the capital S and subjects is capitalized. The
[14:22] code node was reading it lowercase. So, I guess it wasn't catching that. So, it would now match both.
[14:28] Let's give it a new try inside inadein and see. All right, so let's reload inadein and see if
[14:35] that does the trick. Okay, and sure enough, it did not pass on to the text classifier. It did skip
[14:45] because if we look through here filter reason it's an automated sender, which is correct. So,
[14:55] that is a great test and a great finale for the enhancement number three.
