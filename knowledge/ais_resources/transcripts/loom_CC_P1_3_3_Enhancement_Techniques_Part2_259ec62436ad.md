# Loom Transcript · CC_P1_3.3_Enhancement_Techniques_Part2

**Source video ID:** 259ec62436ad416c9f492e5d9b52d079
**Loom URL:** https://www.loom.com/share/259ec62436ad416c9f492e5d9b52d079
**Detected language:** en (probability 1.00)
**Duration:** 686.4s

---

[00:00] Okay, let's move into our last three enhancements. These are going to focus on the output quality
[00:04] and the performance side of our workflow. So number four for this enhancement, let's work on
[00:12] brand voice. So this is going to be an easy one. So like right now, the responses, they're accurate,
[00:18] but they're very generic. We need something that matches the gadgets and more friendly tech savvy
[00:23] voice, a voice. So our new request could be, hey, update the tone to match this brand voice. We'll
[00:30] give an example. It's friendly, helpful, tech savvy, casual, language, enthusiastic.
[00:36] So again, we don't know what cloud will do. It'll update AI node prompt to maybe add some
[00:41] brand voice guidelines and include some example phrasing. It's at its own discretion on what it's
[00:47] going to do here. Adds tone matching logic and then we're going to do some tests with some samples.
[00:54] All right. So back in cloud code here, I'm going to paste and remember, we're going to give it
[01:04] some grounding here in our Gmail workflow. Let's update the tone to match this brand voice.
[01:17] Friendly, helpful, tech savvy, casual, language, enthusiastic in the emails. We're going to be a
[01:26] little more specific, right? We don't want to assume it knows what we're talking about because we don't
[01:29] want a new workflow. So okay, we're going to send that in, see what it comes up with. So cloud has
[01:36] looked through the workflow and notified two places where it sees the email tone is set one is the
[01:42] AI agent system prompt, which is controlling the tone of the AI generated plays when it is tech
[01:47] related. And then our draft, which is our new second Gmail node, when there's no tech support,
[01:53] this is our kind of generic fallback. So this is the two places where we need to update the brand voice.
[01:58] So now it's going through, it's going to update that and we'll see how that looks.
[02:04] So now, they've applied both updates to AI system prompt that rewrote the personality
[02:10] instructions. So there's a greeting style, tone directives, encouraging phrases, tech savvy,
[02:17] but never condescending, and then sign off with a couple different options there. And then the same
[02:24] is applied to our generic response there. So let's go to in and in and check that out. Okay, so inside
[02:30] of our workflow here, we'll go into the AI agent and then down here, I can already see at the top
[02:35] of your system message here, you're a friendly tech savvy customer support rep. Think of yourself
[02:40] with that helpful friend who just happens to know everything about like trunk store policies,
[02:44] policies, your vibe, warm, casual approachable, genuinely enthusiastic, tech savvy, never condescending.
[02:49] So it's adding all of that here into this part. And then we'll come over here to the draft need research
[02:56] and it looks like, hey there, exclamation point, I want to be sure you get the best possible answer.
[03:02] So this has changed and it is more, you know, hip tech savvy. So very, very cool.
[03:10] Let's send one email just to see what it will actually generate having that in it's in a Ted.
[03:17] We'll go over here, send an email. Let's do
[03:22] shipping. What are your normal shipping time frames? Okay, I'm going to just send that to myself.
[03:34] Okay, so back into and I didn't want to zoom out. We're getting big here. We'll get execute workflow.
[03:40] It's going to check that new email that I just sent. It is tech support. It isn't automated. So it
[03:45] bypassed that. It bypassed this. Our AI agent just checked it. Just wrote a draft.
[03:51] And now let's go back to my email and take a look. Hi, great, great question.
[03:58] Exclamation point. So it does have more personality. This side of the email is still not configured.
[04:05] Hope that helps. Exclamation. So this is great. It's working. And we can proceed to the next one.
[04:10] All right, so enhancement number five, the customer name, right? This is again, a very minor thing, but
[04:17] over time, all these little things add up and it really, really optimizes this. And it makes all
[04:21] the difference. So right now, we have an opportunity to make the responses more personal by using
[04:29] a customer's name, if it's provided. Obviously, we might not have the name, but a request will be
[04:36] something like we're going to extract the customer's name from the signature or closing and then use it
[04:41] in a greeting. And then the fallback, if we don't find that will be hi there. So what will cloud do?
[04:47] It will probably add some kind of name extraction. We'll find the pattern spests. John, thanks, Sarah.
[04:53] It'll store it as a variable. And then it'll update that as it goes along into the templates. So
[04:58] let's go add that to cloud and see what happens. Okay, so in our Gmail workflow, let's make
[05:04] the response a more personal with the customer's name extract the customer's name from signature
[05:08] closing using a greeting fallback to hi there, if not found. So we're going to do bypass. This
[05:15] should be an easy one, hopefully, and let's see what it comes up with. All right, so cloud codes
[05:20] looked through everything. It understands workflow structure. I need to add a code node to extract
[05:25] the customer's name from their email, wired into the flow, update the email or the AI agent prompt to
[05:32] use the extracted name and then have the fallback to use the name. Okay, still still going through
[05:40] there. Okay, so it's got a plan here. It's going to apply these new changes. It's going to add a new
[05:46] code node. I guess it's going to be doing the extraction. It's going to rewire the false branch of
[05:51] is automated. So I'm curious to see what's going on there. It's going to update the AI agent prompt,
[05:57] update the draft needs research to use the name and then this one's really interesting. It's going
[06:03] to shift the nodes to the right to make room visually. So it has nothing to do with what we've asked,
[06:08] but it's kind of cleaning up and it's seeing things, I mean, we're getting a lot of nodes in there.
[06:13] So it's going to shift things to the right. So very, very interesting. All 16 applications have been
[06:18] applied. It's checked everything off. It's got a new node that's extracting the name. Okay,
[06:26] let's head over to inadein and check it out. So I'll give the page refresh. Let's see, it does look
[06:32] like things that shifted slightly. There's our new node, extract customer name. Let's just take a
[06:39] little look. So it's got a bunch of code in here. It looks like it's looking at all these closing
[06:46] patterns. You were truly with appreciation. Take care. Wow. It's doing a lot of things here. Okay.
[06:54] That's what it means by by reworking the false. Let's go to here. Over to there. So did I sign off?
[07:03] No, but my email address has my name in it. So let's see if that works. So we'll run this. It
[07:10] should go. It won't go because it's not unread. So let's send a new one just to test. This is
[07:17] why you test. This is why you test. So send it to myself. Um, warranty info. Let's just throw one
[07:26] in the mix. My email is going to say Cody. My sign off is going to be Bob. I don't know which one
[07:31] it will do. But this will be a good pushing it to the limit test. So I'm going to send that.
[07:38] We'll go back here. We're going to hit execute. It's extracted a name. What did it go with?
[07:48] Will it tell us here? Customer name Cody. So it's probably defaulted to the email. The greeting
[07:56] it's going to use. You can see there is high code. So now if we go to my draft email,
[08:01] we can look here and sure enough, high code right there. So
[08:07] interesting. So it's going to default to the question. So now,
[08:13] I'd say that that's working good. And it's went all the way through to the draft reply. Okay,
[08:19] let's move on to our final enhancement. Okay. So enhancement number six, the last one we'll be adding
[08:24] to this is a confident score. So this one's really interesting. It's very different, but
[08:29] we have an opportunity to show how confident the whole system, the work with AI was in its response
[08:36] to answer the question. So we're going to ask Claude to add a confidence indicator at the very
[08:41] bottom of the draft of the email, whether it's high, medium or low, based on its search results.
[08:46] That'll be for our internal review. You might not want to send that to customers, but again,
[08:52] this could be used so many different workflows, so many different fields. So let's give this a try.
[09:00] Claude will probably find different ways to calculate this. So high relevance could be greater than
[09:05] 0.8, medium is 0.6 to 0.8, and then low could be below 0.6. And then how will it display that,
[09:13] right? It could be like internal notes and Michael and confidence level high, medium or low. Okay,
[09:18] so in here, let's show how confident the system was in its response to response email based on
[09:25] its research for the answer at a confidence indicator at the bottom of draft emails, high, medium,
[09:29] low, based on vector search scores. So our final one, let's let it go. Let's see what method
[09:38] Claude code will come up to add this. All right, so Claude's coming up with something.
[09:44] It's approach. The AI agent is also going to output high, medium, low marker based on how well
[09:51] the knowledge base matched. Check the policy match, parse the confidence marker, build an HTML badge,
[09:59] interesting, pass both downstream, create a draft reply. It's going to put the badge there.
[10:06] And the same with the need research. It will show none because there's no confidence there because
[10:12] there was nothing that showed up. Okay, so it looks like it now parses both markers. We've got a green
[10:20] dot for high, a yellow dot for medium, red dot for low, and a gray dot for none. Let's jump over to
[10:26] NADEM and see exactly what that's going to look like. The only updates that I think it said it was
[10:34] doing was in the AI agent. So if we come down here, all right, so down here at the bottom,
[10:42] example of the first line policy found confidence high, et cetera, et cetera. So really the best way
[10:47] to see if this is going to work, let's add one more test email here. This will be
[10:53] price matching, DMS price match phones. We're going to send that through. We'll go back here,
[11:02] execute the workflow. It is textbook related. We're searching the knowledge base. We have a draft
[11:11] email. Let's go check it out price matching down here at the bottom. We even have a little
[11:17] mode view of the robot, AI confidence, green circle, high, based on verified store policies.
[11:24] Awesome. Very, very cool.
