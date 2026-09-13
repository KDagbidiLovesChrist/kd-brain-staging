# Loom Transcript · CC_P4_1.2_Mental_Model_to_Building_Apps

**Source video ID:** d71e3a15b2754f19be1b798b1fabc8d4
**Loom URL:** https://www.loom.com/share/d71e3a15b2754f19be1b798b1fabc8d4
**Detected language:** en (probability 1.00)
**Duration:** 240.6s

---

[00:00] Okay, before we start building, we need to work on our mental model for how to build web
[00:05] apps that actually work.
[00:07] If you've been building automations and workflows, you may notice that apps work a bit different.
[00:12] There are users, there are interfaces, and there's a back and forth between what people see
[00:17] and what happens behind scenes.
[00:20] So the goal of this video is to give you the vocabulary and the mental model to make everything
[00:25] else in the following videos make sense.
[00:28] We're going to be talking a lot about the front end and the back end.
[00:31] So let's explain them a little bit in case you're not familiar with them.
[00:34] So what is the front end?
[00:36] Let's think about your home banking, for example.
[00:38] The front end is going to be everything that you see.
[00:41] When you navigate to your bank website, you're going to see buttons, you're going to see
[00:45] different sections, you're going to see maybe images, you're going to see forms, text.
[00:50] It is basically everything that a user sees when they navigate to a website.
[00:54] All of these run in the user's browser.
[00:57] So let's say you open Google Chrome, everything you see on that website is going to be different
[01:01] end.
[01:02] So what about the back end?
[01:03] The back end is going to run on a server.
[01:05] This is where your workflow with all the logic, all the HTTP requests, all the API calls,
[01:11] all the connections to the different databases.
[01:13] This is where all of that is going to be located.
[01:16] That's why it's called the back end because a regular user is not aware or doesn't care
[01:21] what the HTTP request looks like or what's the structure of the database.
[01:27] All they care is if the website makes sense, if the website is easy to navigate or if
[01:32] it's too complex, if the phones are easy to read or if the size of the font is too small,
[01:38] all of that is going to be part of the front end.
[01:41] So let's say, for example, your website has a form.
[01:44] When someone submits a form on your app, here's what actually happens.
[01:47] The user is going to click a button, this is going to be in the front end.
[01:51] Once that button is clicked, a request is going to be sent to your server.
[01:55] This is in your back end.
[01:56] The server is going to process the request, maybe it's going to save data, it's going
[01:59] to call an API, or it's going to run some logic, and then the server is going to send a response
[02:04] back.
[02:05] And the front end is going to update the UI with a result.
[02:08] This is basically how every web app works.
[02:10] You don't need to fully understand all the technical details, but it's important to understand
[02:15] this mental model and to understand the differences between front end and back end because we're
[02:20] going to be talking about it a lot.
[02:21] Let's now talk about why apps are a bit different from regular workflows.
[02:26] So in phases one, two, three, everything we built would run in the background.
[02:30] We would have workflows triggered, we would have scripts run, data was moved, but most likely
[02:35] all of this happened while you were doing something else.
[02:38] In most of these cases, the goal was to have these workflows run while you were doing something
[02:43] else.
[02:44] There was no need for you to be watching what was going on.
[02:46] And in many cases, the workflows would be triggered automatically without you even knowing.
[02:51] But now we're going to be working with apps.
[02:53] And there are going to be some differences here because we're going to be building web apps.
[02:57] And with web apps, we're going to have people, we're going to have users looking at the screen.
[03:01] They're going to look at the design of our website, they're going to be clicking buttons, and
[03:05] they're going to be waiting for responses.
[03:07] So we're going to have to pay attention to a couple of things.
[03:10] The first thing that we need to take into account is that design matters.
[03:14] We're going to be having people watching in real time.
[03:16] And people are going to expect clean and easy to navigate websites.
[03:20] If the design doesn't make any sense, or it's too complicated for people to understand,
[03:24] they're probably just going to close the app and not use your app.
[03:27] The same is going to apply to speed with web apps, speed matters.
[03:32] Imagine navigating to a website, maybe you are trying to log into home banking and you
[03:36] have this progress bar moving around for 10, 20, 30 seconds.
[03:40] That's not acceptable.
[03:41] People are just going to close the app thinking that it doesn't work.
[03:44] And finally, one of the major and most important differences is security.
[03:49] You're now going to be dealing with users.
[03:51] This means you're going to have real people sharing their personal information.
[03:55] So we'll also have to be very careful in terms of security.
