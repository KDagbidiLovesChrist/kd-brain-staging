# Loom Transcript · CC_P1_2.4_Masterclass_Verification_Testing

**Source video ID:** 287d64d0b20d4b098d62e1dce436bdb2
**Loom URL:** https://www.loom.com/share/287d64d0b20d4b098d62e1dce436bdb2
**Detected language:** en (probability 1.00)
**Duration:** 367.7s

---

[00:00] All right, let's get into a pre-test verification.
[00:03] Now that the workflows are built,
[00:06] let's go down a little checklist
[00:07] just before we get into some heavy testing on this.
[00:10] So is the workflow configured correctly?
[00:15] It was kind of a visual checklist, right?
[00:17] Do we have any indicators?
[00:19] Are all the connections solid?
[00:21] Does it look like everything makes sense
[00:24] in this logical flow?
[00:25] And yeah, I think as we reviewed that, it did.
[00:31] These are some good steps to follow
[00:33] before you get into some of this other testing
[00:36] which we're gonna do right now.
[00:37] So again, if something's wrong,
[00:40] we're gonna describe that issue to Claude.
[00:42] You copy paste the error, let them know where it was.
[00:45] Sometimes the error already tell them that,
[00:48] but it's good to be specific as possible.
[00:51] Share those error messages and then let Claude diagnose it.
[00:56] So test number one, we've done a little test already
[00:59] but test number one, return question.
[01:02] Let's see if all of these can be checked off
[01:06] with a green check.
[01:09] So we're gonna ask about buying a laptop three weeks ago,
[01:13] but it's not working for my needs.
[01:14] Can I return it?
[01:15] It's been opened.
[01:16] So let's go send an email with this
[01:18] and see how our workflow responds.
[01:21] All right, so I got the first test question loaded.
[01:23] Return question, how about a laptop three weeks ago,
[01:25] but it's not working for my needs.
[01:26] Can I return it?
[01:27] It's been open.
[01:28] So sending that email to myself,
[01:31] we'll go back to an 8 in here
[01:35] and we'll click execute the workflow.
[01:39] There we go.
[01:40] Now the AIHN is developing a draft.
[01:43] It's pulling from the knowledge base right now.
[01:46] Now it's writing the draft and then it's gonna
[01:50] put it into the Gmail tool in just a second.
[01:52] Okay, so let's go back to our draft's folder.
[01:56] Let's take a look, let's zoom out a little bit more.
[02:01] There we go.
[02:02] So that's what I sent originally.
[02:04] Here's the draft response.
[02:05] Thanks for reaching out.
[02:07] We're going to get a laptop purchase.
[02:08] It was a laptop.
[02:10] According to our return policy,
[02:12] you have a 30-day window from delivery date
[02:14] to return items.
[02:16] And so what we said three weeks,
[02:18] so that's within 30 days.
[02:20] And we did say it's been open.
[02:21] So it's saying open items are accepted for returns
[02:24] if they're defective.
[02:26] However, for non-defective,
[02:28] that simply don't make your needs.
[02:29] You may return them, et cetera.
[02:32] There's a restocking fee.
[02:33] Okay, so I feel like this past test number one.
[02:37] All right, so our checklist for test one.
[02:39] Like I said, we really hit all of these.
[02:41] We got the email.
[02:43] It was support that we found the return policies.
[02:46] It drafted the answer with the specifics
[02:48] and it was in our draft folder.
[02:50] So test one definitely definitely approved.
[02:52] Let's move to test number two.
[02:55] We're going to do a warranty question.
[02:57] My TV stopped working after eight months.
[02:59] There's the email for the warranty question.
[03:01] Very basic.
[03:02] We'll send that.
[03:03] We'll go back to our NADN, execute.
[03:08] Now it's going to pull in the new email.
[03:10] The text is classifying.
[03:11] It did go to the relevant ones,
[03:13] which means it does think it's text support related.
[03:15] That was very fast.
[03:17] To check the knowledge base came back.
[03:19] You can see the two.
[03:20] It means it hit this twice.
[03:22] And then hit a draft.
[03:24] Let's just jump in here to check.
[03:25] Over here, we can see it's thinking for reaching out.
[03:29] Our warranty policy includes one
[03:31] of your manufacturer warranty, great.
[03:33] And then flipping over here to the drafts,
[03:34] you can see everything's correct.
[03:39] Warranty policy, new electronics,
[03:41] one of your manufacturer warranty,
[03:42] contact the manufacturer directly.
[03:44] So everything seems to be correct based off
[03:46] of the knowledge base that we gave it.
[03:49] All right, so we didn't get the email.
[03:52] It didn't find us support because it would have stopped.
[03:54] Otherwise, it found the warranty policies.
[03:58] It drafted the answers and we got the email.
[04:00] So test two is also good.
[04:04] Another test we're going to do is non-support.
[04:06] So let's do one.
[04:07] We're just asking about the store hours.
[04:10] All right, so we have the store hour question
[04:12] for test three loaded in email.
[04:14] We'll go ahead and send that.
[04:15] We'll go back to NADN.
[04:18] We'll hit execute workflow.
[04:21] It's classifying it as tech support, hit the knowledge base,
[04:25] and it's hit a drafts.
[04:28] And then here, I apologize for the convenience,
[04:30] but it seems I don't have the current store hour information.
[04:33] And they're right, the policies and the FAQ
[04:37] are not listed on the PDF.
[04:40] So what this does is a couple of things.
[04:42] It proves that the AI is not going to just make up store hours
[04:47] and pull from some random place, which is good.
[04:52] And it's proving that it's only going to take the information
[04:55] we've given it there on the PDFs.
[04:57] So this is great.
[04:59] All right, so for test three, we got the email.
[05:04] Now here, there's some great area, right?
[05:06] Like is asking store hours tech support?
[05:09] So it is a support question.
[05:12] So this could have gone either way.
[05:15] Maybe since it's not policy and all the things we listed,
[05:19] maybe it should have stopped the workflow.
[05:21] But it did indeed just say, hey, I'm sorry,
[05:24] I don't have the answer to that.
[05:26] So again, it's going to come down to the preference
[05:28] of what do you want this workflow to handle or not handle?
[05:32] Just the final verification.
[05:34] So we know the documents are processing, right?
[05:37] Because it's pulling information that's there
[05:38] and it's saying when information that is not there.
[05:42] It has the correct info.
[05:44] It's executing now without errors.
[05:46] We troubleshoot both of those.
[05:48] The responses do match the documents.
[05:52] The specific dates, number, season, all that are correct.
[05:55] And then the non-support, remember earlier,
[05:57] we did the hey, dinner, right?
[05:59] That's definitely not support.
[06:01] That one stopped the workflow right away.
[06:03] So I'd say yes, verification, everything's working
[06:06] just as it should be.
