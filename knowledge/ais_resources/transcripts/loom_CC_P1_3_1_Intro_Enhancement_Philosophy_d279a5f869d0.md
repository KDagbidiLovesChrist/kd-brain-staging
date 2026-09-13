# Loom Transcript · CC_P1_3.1_Intro_Enhancement_Philosophy

**Source video ID:** d279a5f869d04403a4d4e1413f25142a
**Loom URL:** https://www.loom.com/share/d279a5f869d04403a4d4e1413f25142a
**Detected language:** en (probability 1.00)
**Duration:** 309.4s

---

[00:05] Hey, everybody, welcome back to the vibe coding challenge.
[00:08] We're in module three.
[00:10] Pretty amazing.
[00:11] So in this one, we're doing the iteration and enhancing
[00:15] what we've done previously.
[00:17] So let's take a look at where we left off.
[00:21] Right now, our process is working, right?
[00:24] Would it be classified as production ready?
[00:26] Maybe, maybe depending on where your standards are at,
[00:29] but we're gonna take it and make it even better.
[00:32] So where we left off for module two
[00:34] or where you should have left off for your challenge,
[00:36] you should have checked all those boxes.
[00:37] But we have a workflow that reads the policy documents
[00:42] and it ingests that information.
[00:44] It created a vector store with all that policy information.
[00:48] And then we have a second workflow.
[00:51] Maybe yours put it all together, I don't know.
[00:52] But regardless, you have a workflow
[00:55] that also is monitoring Gmail for the customer support questions.
[00:59] And then it searches the policy information
[01:02] for the answer and then drafts an email in your Gmail.
[01:06] And this is where we're gonna go.
[01:07] So now we're gonna handle edge cases.
[01:10] So edge cases are those that are run on the edge of,
[01:13] it could fall either way, right?
[01:15] And needs to provide a better user experience.
[01:17] I think from my output, the emails I was getting
[01:20] was just blocks of text, right?
[01:22] It's not really set up as a pretty email.
[01:24] So maybe we can handle that.
[01:26] It's gonna perform efficiently every time.
[01:29] And then it's easy to monitor and maintain.
[01:31] Everything's cleaned up, even the way the workflows laid out.
[01:34] I know in Cloud does it, everything's kind of on top of each other,
[01:37] but just organizing things out, labeling them.
[01:40] You can even put some background colors,
[01:42] all that fun sort of thing.
[01:44] Let's talk about enhancements in the philosophy
[01:46] to be behind where you should do this first,
[01:50] where you should take it last.
[01:52] So number one, working versus working well.
[01:55] So if it's working, it's doing what it's supposed to do.
[01:58] It's basic, there's no errors, it's fine, right?
[02:02] Working well means all the edge cases,
[02:07] the user experience, the efficiency behind it,
[02:10] everything is far surpassing just doing the basic,
[02:14] just checking the boxes, right?
[02:15] You're going way beyond that.
[02:17] Principle two, I love this one.
[02:19] So you're iterating in layers.
[02:21] You don't do all of this at once, right?
[02:23] Oh, make it faster, make this better.
[02:25] You've got to start.
[02:26] And so looking at it in this way,
[02:28] in this stair step approach is really, really great,
[02:30] especially to not get overwhelmed by everything.
[02:34] So number one, error handling.
[02:37] What breaks, because that really is most important.
[02:39] It doesn't matter if the email looks great,
[02:40] if there's no email being produced worth email
[02:43] that's being sent is incorrect.
[02:45] So error handling, what is breaking it?
[02:48] Number two, would be the logic improvements.
[02:51] What's inefficient?
[02:52] What could be working better, how it's dissecting
[02:56] the information, that sort of thing?
[02:58] And then you get to number three, which is the quality of the output.
[03:00] What is the experience like?
[03:01] This probably falls into the whole, the email formatting, right?
[03:05] Like maybe it has bullet points,
[03:06] and the signature it signs off with is a little better.
[03:09] And then four is performance.
[03:11] Like, then you look at, okay, how long is it taking
[03:13] from when I get an email to it, thinking, pulling the information,
[03:17] and then giving me a draft.
[03:18] So this is a great thing to go back to.
[03:21] And this is true with anything in life.
[03:23] I think really it's just kind of going through these steps.
[03:27] Principle number three, test everything
[03:30] after you make a change.
[03:32] So you test the happy path.
[03:34] The happy path is the easy one.
[03:35] It's the very straightforward.
[03:37] It's definitely going to work.
[03:38] Make sure that that is still working
[03:40] because you never know when something could throw a wrench and something.
[03:43] And if you're testing the hard stuff,
[03:45] make sure the easy stuff is still working first.
[03:48] Test the edge cases, that's you're fixing.
[03:51] And then make sure that nothing else broke, as I said.
[03:54] There's a lot of room for error.
[03:57] There's a lot of room for error here.
[03:59] Luckily, Cloud has our back.
[04:01] We're able to communicate and ask when these errors happen.
[04:03] But test everything as you make changes and save your work.
[04:08] And then finally, number four, enhancement is iterative, right?
[04:12] It is a fluid as you go process.
[04:15] Start with those essential things.
[04:18] Then add, you know, it'd be nice to have this.
[04:20] Like, it's not imperative, but the nice to have,
[04:22] so you know, make a list and you can add those over time.
[04:25] And then get that feedback.
[04:27] Use it, demo it, get a small group to test it out, right?
[04:31] And then take that real world usage
[04:33] and then apply iterations and updates to make it even better.
[04:37] Let's take a look at what we're going to learn today
[04:40] in this overview from module three.
[04:42] So we're going to, we kind of already have,
[04:45] identify what needs to be improved.
[04:48] Again, what Cloud gave you for your challenge?
[04:51] Maybe very different from what it gave me for my challenge.
[04:54] So all of this, obviously, pare it to whatever workflow
[04:58] you have set up that Cloud gave to you.
[05:01] We're going to look at techniques for enhancing the workflows,
[05:04] how to test those edge cases,
[05:06] and then how to make those workflows production ready.
