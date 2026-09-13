# Loom Transcript · CC_P1_1.6_Verify_All_Tools_Connected

**Source video ID:** 58a741216bfc41c3bd0a1873bd041fe5
**Loom URL:** https://www.loom.com/share/58a741216bfc41c3bd0a1873bd041fe5
**Detected language:** en (probability 1.00)
**Duration:** 176.0s

---

[00:00] Okay, now that we have most of the connections done,
[00:03] we're gonna do a couple steps of verification.
[00:06] Some of them we've already done,
[00:07] but let's just do them again to be sure
[00:09] that everything is installed correctly.
[00:11] Cloud code has access to everything that it needs.
[00:14] First step we're gonna do is to double check
[00:16] these project files.
[00:17] So we're gonna go to VS code,
[00:19] we're gonna ask Cloud, show me what's in my project directory.
[00:22] We should see that Cloud.MD file,
[00:25] we're gonna see the MCP server files
[00:27] and probably in an advanced skills folder.
[00:30] All right, so back in VS code,
[00:32] we're gonna paste in the first test,
[00:33] show me what's in my project directory.
[00:35] So it's vibing, it's gonna spit it out here in a second.
[00:38] Let's just confirm everything.
[00:42] So we've got Cloud directory,
[00:45] a Cloud.MD, which is our setup instructions.
[00:48] We've got the environmental variables,
[00:50] which is where our API for an ADD in credentials are.
[00:55] We've got Cloud configuration directory.
[00:57] Okay, no workflow files have been created yet.
[00:59] That's great.
[01:01] But the second test we'll do is our MCP connection.
[01:03] We're gonna ask Cloud,
[01:04] can you confirm your connected to my an ADD instance?
[01:09] Cloud should confirm the connection.
[01:11] So we'll go here,
[01:12] can you confirm your connected to my an ADD instance?
[01:14] Let's see what Cloud says.
[01:18] So it does say yes, the connection is confirmed,
[01:19] and healthy, here's a summary,
[01:21] shows the instance, connected,
[01:22] API is configured, tools available,
[01:25] everything's fully operational says.
[01:27] Great, second test is great.
[01:28] All right, test number three.
[01:30] Can it read workflows?
[01:32] So I'm gonna ask it,
[01:33] what workflows do I currently have?
[01:35] Because we want to make sure
[01:35] it can see the list of everything we've got.
[01:38] So it should confirm,
[01:40] or if you've just set up a new an ADD account,
[01:41] you will have no workflows,
[01:43] but it will tell you that.
[01:44] Okay, our third test, what workflows do I currently have?
[01:49] So it says, if you have 17 workflows on your instance,
[01:52] here is an overview, and then boom,
[01:54] it lists all of them,
[01:55] how many nodes are in each,
[01:57] what are active, what are tagged.
[01:58] So it has definitely all of the information.
[02:02] Okay, test number four,
[02:03] tell me about the Gmail Trigger node.
[02:05] I know we just did this, but again,
[02:07] one more time, just to go through
[02:09] to make sure everything is absolutely connected.
[02:11] All right, tell me about the Gmail Trigger node.
[02:14] So it's gonna go back,
[02:15] it's gonna look through the documentation again.
[02:18] It's gonna give us all the details
[02:19] about this Gmail Trigger node.
[02:20] There we go, message received,
[02:22] add a poll interval,
[02:23] what parameters, what filters.
[02:25] Okay, it knows its stuff.
[02:28] Sometimes there will be errors.
[02:29] Here's a couple of things.
[02:30] If the API key is airing,
[02:32] make sure the key is valid.
[02:34] Right, you haven't deleted it.
[02:36] You didn't accidentally delete some of it.
[02:39] Check that.
[02:40] If the MCP's not connecting,
[02:41] try to restart for the server,
[02:44] and then if the in and in authorization failed,
[02:45] just verify your credentials are good.
[02:47] And most importantly, again,
[02:49] ask cloud help diagnose.
[02:50] It can give you specific answer,
[02:52] and it might even give you the solution most of the time.
