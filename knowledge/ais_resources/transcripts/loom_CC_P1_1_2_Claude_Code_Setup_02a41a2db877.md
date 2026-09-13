# Loom Transcript · CC_P1_1.2_Claude_Code_Setup

**Source video ID:** 02a41a2db8774b3e82c3fb6b06c01123
**Loom URL:** https://www.loom.com/share/02a41a2db8774b3e82c3fb6b06c01123
**Detected language:** en (probability 1.00)
**Duration:** 261.1s

---

[00:00] Okay, let's take a look at getting started, setting up Cloud Code on your device, and also
[00:04] talking about what is Cloud Code exactly.
[00:06] So Cloud is an AI coding assistant that we can have live inside VS Code.
[00:12] So VS Code is a third party, it's a different program, we're going to install for this use
[00:16] case.
[00:17] It's just very easy, keeps things a little easier to manage and to communicate with.
[00:22] But Cloud can read your project files and can write and edit as you saw from the demo previously,
[00:28] you can run terminal commands, and then the power of it comes when you can connect the external
[00:33] tools using an MCP.
[00:36] So real quick, let's, this is a nice slide because it breaks down the difference between
[00:40] what a Cloud subscription is versus a Cloud API.
[00:43] So subscription is what you might pay for, you know, 20 bucks a month, and it's, you know,
[00:48] if you go to the web and you're just chatting with Cloud in your browser or on your phone
[00:52] or even through the app, right, it's all text-based, it's, you know, brainstorming things and
[00:56] you're getting the text back, you can copy, paste that.
[01:00] There's messaging limits.
[01:01] The API side of things is more on the developer things, you're building workflow automations,
[01:06] it's, it's token-based, paper use, really for building those applications.
[01:11] So this is a good just reference to show the difference between those two.
[01:14] Okay, before we get into the setup, let me cover a quick tip that's going to help save
[01:18] some confusion and some money.
[01:19] So Cloud Code works on tokens, not flat messages.
[01:23] Anytime you send a message, Cloud will re-read the entire conversation from the top.
[01:26] That means the longer your session gets, the more expensive each message will become.
[01:31] That also means you want to always be sure to open your dedicated project folder with Cloud
[01:36] Code.
[01:37] You don't ever want to open like a root folder that has multiple folders and projects inside.
[01:41] One folder, procession, that's the mindset we need to think as we continue in today one.
[01:47] Let's begin installing this.
[01:48] First thing we need to do is install VS Code, which is Visual Script Code.
[01:52] Again, it's a third party program.
[01:54] We're going to install to use for this.
[01:56] So we're going to go to the websites and it looks something like this, depending if you're
[02:00] on a PC or a Mac, you're going to click download for whatever device you're on, and you need
[02:05] to get that installed.
[02:06] All right, now we need to install the cloud extension inside VS Code.
[02:10] So we're going to go to our extensions button, we're going to search for Cloud Code and we're
[02:13] going to hit install.
[02:14] So to do that, let's walk through that really quick.
[02:17] Go back to VS Code.
[02:18] Down here on the left side is the extensions, if you click on that, all you have to do is type
[02:23] in Cloud.
[02:24] It'll pop up right there, Cloud Code for VS Code, we'll click on that, and then here you'll
[02:30] or button will look like this, little blue install button, we'll click that and let that start
[02:35] installing.
[02:36] Okay, so once it's installed, you're going to see this little Cloud icon button up there.
[02:40] If you click on that, you're going to see a screen similar to this, and depending on how
[02:45] you want to connect, Cloud subscription, which is what I'd recommend for this or the
[02:49] Android console, which is using the API, we talked about the difference between those two.
[02:53] But if you click on the Cloud AI subscription, it's going to have you verify the connection,
[02:57] it might even have you copy paste like an API key code in there to verify.
[03:03] But then once you're up and running, you'll see this little icon, that is how you get to Cloud
[03:07] Code, you'll see the little icon there in the chat window and we are ready to go.
[03:13] Do a quick navigation tour of Cloud Code, the interface, so we know kind of what we're looking
[03:17] at here.
[03:18] We're going to talk about the chat panel, files for, and the terminal, which we won't really
[03:22] need for this, but just to show you where it's at.
[03:25] Back in VS Code here, on the right side is our chat, right?
[03:28] We have Cloud Code pulled up, you'll know that because it will say Cloud Code has the icon,
[03:32] all this Cloud Code branded.
[03:34] This is the majority of communicating with Cloud, we'll take place right here using the chat
[03:38] bar.
[03:39] On here, we can click through the different modes, which we'll talk about later, which
[03:43] is pretty cool.
[03:45] Then over on the left, we have the file explorer, if we have this button clicked, and this is
[03:49] where we'll look at all the project files that we'll be communicating with here.
[03:55] Then that terminal that I talked about, if you look up here on the top right, you can click
[03:59] these buttons here that configure the windows in different ways.
[04:03] I clicked on that one, which just opens up this bottom portion here, and there's a couple
[04:09] tabs, output, problems, terminal, that sort of thing.
[04:13] I like to keep that off for now, because really all we're going to need is our chat window
[04:16] here for Cloud, and the file structure on the left side there.
