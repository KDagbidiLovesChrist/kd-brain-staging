# Loom Transcript · CC_P1_1.5_n8n_Skills

**Source video ID:** b7c56c8882984f8ea2e13cae4310ddc4
**Loom URL:** https://www.loom.com/share/b7c56c8882984f8ea2e13cae4310ddc4
**Detected language:** en (probability 1.00)
**Duration:** 181.1s

---

[00:00] Let's take a look now at inadein skills and begin setting it up within Cloud Code.
[00:05] So what are skills?
[00:07] So the skill files are the documentation that teach Cloud how to use inadein.
[00:13] So what types of nodes there are, what are some of the best practices, what are common patterns to be used,
[00:18] so that Cloud has a great understanding of how to start building workflows for you, and why it's as important, right?
[00:24] Cloud needs to know how they work.
[00:26] We don't, it's supposed to be easier in Cloud doing the hard stuff and not us.
[00:31] So what parameters are available, the best way to structure workflows,
[00:35] what's going to work, what's not going to work, and with skills, it's going to tell Cloud all about how that works.
[00:42] So to install this, it's very similar to the MCP.
[00:45] In fact, it is exactly the same, other than the URL that we're providing being different.
[00:49] So we're going to literally tell Cloud Code, hey,
[00:52] clone this repository and set it up and provide the link with it.
[00:55] And then Cloud's going to do just what they did with the MCP server, it'll clone it, organize the files and reference them automatically.
[01:03] All right, once the skills have been updated, remember following those prompts,
[01:06] allowing it access, giving permission to install that, we need to make sure that Cloud has updated the markdown file
[01:14] to make sure that has access to the inadein documentation.
[01:18] So we're going to tell it update Cloud MD to note you have access to the inadein documentation now, the skills, right?
[01:26] Then we're going to restart Cloud and then let's do another test.
[01:29] Let's verify, hey, do you have access to this inadein documentation?
[01:33] And then we'll pick one like a Gmail sugar node.
[01:35] Hey, okay, tell me about the Gmail sugar node.
[01:37] And if it does have access, it's going to break down specific details on how the node works.
[01:43] So back in VS Code, we can literally type the first one.
[01:46] Hey, update the cloud that MD file to note you have access to in inadein documentation.
[01:52] It's going to go through all of those.
[01:56] Once it's finished, it'll open up the MD file.
[01:59] I don't actually as highlighted that specific part for us.
[02:02] So inadein documentation access has direct access to official documentation through the MCP server.
[02:07] So great, that's perfect.
[02:09] That's ready to go.
[02:11] Okay, one last thing, if your MCP server isn't showing up after install, don't try to troubleshoot it yet.
[02:16] Just restart Cloud Code to let it register nine times out of 10.
[02:21] That's what the problem is.
[02:22] Now, let's do that test to make sure as a backup, right?
[02:26] So tell me about the Gmail sugar.
[02:33] Okay, so now Cloud is going to go pull from its knowledge base that we've installed.
[02:37] Yes, we'll give it permission.
[02:40] So now it's searching nodes for Gmail trigger.
[02:45] It's found it.
[02:46] And now it's giving me summary what it does.
[02:48] Pulls Gmail, I set interval, structure, workflow, whenever new emails arrive.
[02:53] It goes through configuration, all the filters you have access to in that node and then other nodes.
[02:58] So I'd say it's ready to go.
