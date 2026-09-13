# Loom Transcript · CC_P1_1.4_n8n_MCP_Server

**Source video ID:** 1d3c69501fd341f294d68c838c280814
**Loom URL:** https://www.loom.com/share/1d3c69501fd341f294d68c838c280814
**Detected language:** en (probability 1.00)
**Duration:** 513.2s

---

[00:00] All right, let's take a look at overview of an ADIN and an MCP server.
[00:04] So, an ADIN, for those of you who don't know, is a workflow builder.
[00:07] Loads and no code, you can connect apps, flow data through,
[00:11] build these workflows and automations, integrate the AI, and then connect with
[00:15] external tools using API. So, if I show you quickly kind of what that looks like,
[00:20] you know, you've got Gmail connected and you can integrate the AI here,
[00:24] and it's making decisions, analyzing data, moving it along, you can drag
[00:28] stuff around, very, very low coding and stuff going on here, it's kind of just a visual
[00:33] builder. So, the issue with building manual like that is it's time consuming.
[00:37] I mean, you saw all the nodes and you click and drag, and there's a lot of settings within each
[00:41] of them that you have to configure. It's easy to make a mistake. If you have one wrong space,
[00:45] or something's connected in the wrong spot, you have to manually go in and try to figure out
[00:50] what went wrong, or Google the answer, ask for help, that sort of thing.
[00:54] The solution comes when you have this innate and MCP server integrated into Cloud Code,
[00:59] because that allows Cloud to read all the workflows, create them, to modify them,
[01:04] and then most importantly, test and debug and figure out what's going on, why it's not working,
[01:08] and then to help try to self-heal that. Okay, same thing for my last video. My screen's
[01:14] already going to show some files and configurations from this video. Yours won't look like this,
[01:19] and that's completely fine, it's completely correct. Follow the steps as I show them,
[01:22] and not with sitting specifically on my screen. So, let's begin the installation of this innate and
[01:27] MCP server within Cloud Code. So, it's pretty easy. Just like the vibe coding aspect,
[01:34] we're going to literally just tell Cloud, hey, I want you to clone this repository and set it up.
[01:39] We'll give you the link that you'll use to go with that message, and then it's going to clone it.
[01:44] It's going to set up the files, get everything configured and ready. We're going to clone this repo
[01:48] manually. Do not let Cloud run the NPX install command. If it asks to do it, just say no.
[01:54] The NPX route causes silent failures that are sometimes hard to diagnose and troubleshoot,
[01:59] and then the fixed result will be to rip it out and then install it manually anyway. So,
[02:03] we're going to walk you through how that works, but I wish wanted to bring this up if Cloud offers
[02:07] to do it. Remember, just say no. Literally, clone this repository, set it up. There's the link
[02:12] we'll hit enter, and then it's going to start doing what it needs to do. Now, occasionally,
[02:16] it might have to ask you a question or get your permission about something. A little screen might
[02:21] pop up and ask you questions, and then you have to just make sure you're paying attention like this one
[02:25] here. Do you give it permission to do that? Yes, yes, just for you or no, that sort of thing. Make
[02:31] sure you follow the prompts. If there's any errors, it's generally going to figure it out. Just take
[02:35] your time, read, and get it installed. All right. So, we're setting this up on the project level,
[02:41] and I want to be really clear about that because the global configuration is one of the most common
[02:45] mistakes of this course. If you configure the MCP server globally instead of on a project level,
[02:51] you will get a security warning every time Cloud code restarts. If that happens to you,
[02:56] that's why. The fix is to move the config file into your project folder.
[03:01] Well, the MCP is setting up within Cloud. We need to start gathering our credentials for InADM
[03:07] so that Cloud, even though it's connected to the InADM tools, it needs to connect to our InADM.
[03:12] So we need to be sure we have correct credentials for that. So there's two things we'll need. We'll
[03:17] need our InADM API key and our InADM instance URL. So to get our API key, we're going to go to
[03:24] settings within our InADM account API, and we're going to generate a new API key. So let's do that now.
[03:29] So here within InADM, we're going to go down to the bottom left under settings. You'll see
[03:35] menu pop up. I'll say InADM API. We'll click on that and then we can click Create API key here.
[03:41] Give it a label so you know what it's going to be for, and you can set expiration,
[03:46] 7690 days, custom or no expiration. You can probably do no. And then once you've given a name,
[03:53] hit Save, and then it'll pop up. Now, this is the only time you're going to see this,
[03:59] right? Like most API keys, it shows you the one time you create it, and you will not be able to access
[04:03] this again. And it's very secure. You do not want to give this out to people because it can link to
[04:09] your accounts, your wallet, your money, all of that sort of thing and people can kind of use that.
[04:13] So I suggest clicking to copy this because we'll paste it here in a second. But also,
[04:19] take this, send it through your printer once, write it down on a piece of paper, something so you have
[04:24] a hard copy, somewhere secure that you can reference back if you need to. Now, you can always delete
[04:29] API keys, but it just becomes a hassle if it's not secure. So we'll hit Done. We've got our API key
[04:35] copy to our keyboard. Okay, the second thing we're going to need is our instance URL. Now,
[04:41] within 8in, you've got two choices, right? There's Init and Cloud, which is great for this. There's
[04:46] free trials. If you'd like to try it, you will literally just copy your whole URL. And the orange part
[04:53] here, where it's your instance, depending on what you named it, right, will be different. So just
[04:57] copy the whole URL for that. If you're self-hosted and not the cloud-based, right? You're going to copy
[05:03] either your local host URL or whatever your full custom URL is for that instance URL credential.
[05:10] Okay, one hard rule before we touch any credentials. API keys should go in .env files only,
[05:16] not in .mcpjSons, not anywhere else, not anywhere that cloud can write to. .env is the only place.
[05:23] I'm going to show you where that file is in just a second. I just wanted to bring it up as we get into
[05:28] this. It's a good thing to keep in the top of mind. All right, and then as Cloud is setting up
[05:33] the mcp server, it may ask you for your credentials for Init and but we want to avoid giving it to it via
[05:40] the chat. Doing the chat is not as secure. So we're going to add them to the .env file. We'll go to the
[05:47] .env file from the explorer within VS code. Cloud should have created this when it's setting up the
[05:53] mcp server. If it didn't, I'll walk you through a process now to where we can easily add it,
[05:58] and then add the two credentials to API key and the instance URL, and then we're going to save the file.
[06:04] So back in VS code, it didn't actually create when for me when I did this. So I asked, is there a .env file
[06:10] for my project? It said, no, it's there isn't. Would you like for me to create when I said yes?
[06:16] And then it still prompted me. I told it why I wanted it. It's like, I want it to store the API key
[06:21] in the credentials so it's safer, and it still asks me for it via chat. I was like, no, no, no,
[06:25] I'll do it manually. I'll do it myself. So over here on the left, you see there's a .env file,
[06:32] and here I have just two lines, but two place folders. So my API URL, I will paste right here,
[06:40] and then my API key, which I still have on my clipboard, we'll go right there.
[06:45] So you're going to want to put both of those right here. I'll go and get my URL real quick.
[06:54] There it is, copy that, go back to VS code, and paste over that, and then you save it, and then
[07:00] you're good to go with your credentials. All right, so why do we use .env file? Why don't we just
[07:06] give it to Cloud? Like it was asking, well, again, it's way more secure. You don't want people to have
[07:11] access to any of your API key. So having it saved within the file is a way more secure than sending it
[07:16] through the chat. So out in the history, it's pretty standard practice for most things, and then we can
[07:22] easily just update it later rather than having to scroll through a chat history that probably
[07:26] does not exist anymore. We can just go to the file there it is, copy, paste, to override, and we're
[07:31] good to go. Once Cloud Code confirms that the MCP server is installed, and you save your credentials to
[07:36] the .env file, when you do a system check. Let's double check that everything is connected, as it says
[07:41] it would. So couple of ways to do that. Again, we're just talking through this. Can you start the MCP
[07:47] server now? It's going to run the command. We need to look for the confirmation message.
[07:51] MCP server is running. Connected to the innate and instance. So let's do that right now.
[07:56] Let's do a check. Can you start the MCP server now? Lots thinking about it. Do you want to proceed
[08:09] with the health check? I'll say yes, please proceed. Let me verify the connection to your innate
[08:17] and instance. The MCP is connected and working here to status. Connected to, there's the URL for my
[08:23] innate and instance. The version of the MCP and the API response time, which is great. So if it
[08:30] shows all those things, you're ready to go.
