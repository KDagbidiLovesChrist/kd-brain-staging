# Loom Transcript · BP_AZ_APIs_HTTP_Requests_Overview

**Source video ID:** d3db0e10586a45ee9090e68bfd354029
**Loom URL:** https://www.loom.com/share/d3db0e10586a45ee9090e68bfd354029
**Detected language:** en (probability 1.00)
**Duration:** 637.7s

---

[00:00] Okay, the scariest thing for beginners and when I got started what was the scariest thing to me was APIs and HTTP requests and I'm going to today at a high level, we're going to talk about what they are and how they work.
[00:15] And then later on when you go to set up your first one in any then or Zapier or make or whatever you use to send off your HTTP requests will be much much much easier.
[00:28] There's all these things you might see like API keys, header authentication, JSON body, it's intimidating. I completely hear you. I remember like I said in the JSON video that I almost started just crying because I was like, what is this, but it's really, really not too bad.
[00:43] You just have to get over that hump.
[00:45] And I just wanted to say that because everyone feels that way when they first look at API documentation. But anyways, we're going to get into it today because it's the most important thing to learn.
[00:54] Without APIs, you can't really do anything because API stands for application programming interface and it essentially allows two different software applications to communicate.
[01:06] So imagine I'm trying to talk to you. We can't see each other. Okay, so we're both blind deaf and can't feel how would we communicate.
[01:22] So if something has an API that basically means they can see they can hear they can feel if they don't then there's really no way to talk to it.
[01:30] And so when things have APIs and you can use an HTTP request which would be like my voice or sign language or me touching you, that's my HTTP request to your API.
[01:43] So that's the way to think about it. And we're going to visualize it. It's going to be easy. But essentially at a high level, if you ask me what's an API in one sentence, I would say it allows two services to talk to each other.
[01:54] So that could be any then talking to Gmail. That could be Gmail talking to Claude. That could be any then talking to HubSpot. It's just they're just talking.
[02:04] And they use JSON to talk, by the way, just so we all know anyways.
[02:09] So an API is a protocol and it standardizes the way that things talk to each other.
[02:17] There is some hidden complexity, but they're digital connectors. You can see these two monitors are shaking hands. They're talking.
[02:23] I don't want to explain it that way because that's confusing. So I like to use this restaurant analogy where you're the customer.
[02:30] The waiter is the API. The kitchen is the server. The food is the response. And that's a little confusing to think about, but I want to visualize it. So this is a lot easier way to think about it. So we go to a restaurant. This is us right here.
[02:45] When we go to this restaurant, we know that we want food. The restaurant has different options of food that we can get.
[02:52] And so in order for us to understand what we can get from the restaurant or the kitchen, we have to look at the menu.
[02:59] We look at the menu first and then we talk to the waiter. So we tell the waiter, hey, I looked at this menu and it looks like you guys offer chicken parm.
[03:09] So I have looked at this menu and I'm going to tell the waiter, hey, I want the chicken parm.
[03:14] The waiter is going to say, okay, cool. Let me tell that to the kitchen. So it takes our request to the kitchen.
[03:20] And then the kitchen is, okay, the person ordered chicken parm. I'm going to grab chicken parm. And now I'm going to give the chicken parm back to the waiter and the waiter is going to give the chicken parm back to the person.
[03:30] So without us looking at the menu, we wouldn't know what food to request. They might not have it.
[03:39] And without the kitchen giving us back the food, we wouldn't get it.
[03:44] So let's say we requested something that they didn't have. We requested something up here and there's nothing up here.
[03:51] So then the waiter would come back and say, hey, that's not there. Maybe read the menu again and try again, okay.
[03:57] So just to put this into a little bit more technical terms, let's say we have an AI agent and the agent wants to get data from our CRM.
[04:06] So this could be the person's name, the person's email, the person's phone number.
[04:10] In order to talk to the CRM and get the right data back, it has to read the API documentation or the menu.
[04:16] This menu API documentation lets our agent know what to tell the waiter or the HTTP request. So the agent said, okay, I want data.
[04:25] Let's just say this is data A and this is data B. The agent read the menu and said, okay, Mr. HTTP request, I want data A.
[04:33] HTTP request says, okay, Mr. Endpoint or the server, the user or this agent wants data A.
[04:41] The endpoint grabs data A, brings it back, gives it to the HTTP request and HTTP request gives it back to our agent.
[04:48] So it's reading and understanding what is available giving it to an HTTP request to give it to the server and then the server gives it back to the HTTP request, which gives it back to us.
[05:00] So high level, I hope that that visualization worked. After this, I'm going to plug a video where I kind of dive into this process, but also I start to understand, I start to show you guys like how this works and end it in at a very high level and connecting to one and end end, which is really simple the way you read the documentation and then you put it in and you have like your API keys and stuff, but this is agent zero, this is the beginning, this is just getting a high level understanding, okay.
[05:28] So anyways, hopefully that makes sense and these are all over weather apps, you know, your phone, when you look at the weather, it's basically sending a request to the weather channel or to Apple map or Apple weather or whatever you use and then it comes back and if you type in, okay, right now I'm in Chicago cool, what if I want to see the weather in LA, I will type in LA, which is sending a request to the weather server, it's getting LA's weather and sending it back to me.
[05:54] So that's an API, social login, you go to a platform and you log in with Google and you're sending a request between those two services, PayPal, you're on Etsy and you want to pay someone with PayPal, you're making that request to PayPal server and it's coming back, right so APIs are everywhere, it's the magic that powers services to talk to each other.
[06:16] Now, don't get too hung up on this, but there's different elements that go up into your requests, you typically have an endpoint, which is basically what restaurant do I want or what service am I trying to talk to that's usually the end points, as you can see here API dot weather dot com current, this is the destination and then this is the end point so let's say I want it to McDonald's, this would basically be McDonald's and then this would be like fries.
[06:42] So you're just kind of specifying what you want. The method get post put delete, you pretty much using post most of the time, everyone's not always get, but I hardly ever use put and delete so I'm not going to dive into this right now, but there's different methods headers is going to be your API key or your password, so
[07:01] When you go to McDonald's and you make that request to McDonald's and you ask for fries, you have to pay. And so you give them a credit card and that's basically an API key password something that says, okay, this person has this money here or this is this person's account, we will then authorize them to use our service or to buy our friends rise.
[07:20] And then you have a body, which is kind of like action information, so maybe I want them extra crispy, maybe I don't want salt, maybe I'm gluten free, whatever, just sending over more details on the body.
[07:32] And once again, we will actually apply this and we will actually set up requests later, this is just high level.
[07:38] Now we sent something off, the server retrieves it and the server returns a response and then we see it, it's just that process happens every time.
[07:47] And then we usually get back from the server, a JSON response, and we kind of looked at this earlier in the JSON lesson, but once again, let's say I said, okay, I'm on my weather app and I type in Chicago.
[08:04] The server would get back a request, a response that says, okay, location, what's Chicago temperature is 72 conditions are sunny humidity is 45 and then it would just display that in a nice looking way for us.
[08:16] But the server is actually getting back JSON, once again, we talked about authentication, this is for security access control usage tracking and billing, so when you go to a server, you'll typically get a API key to set up and that's why it's unique to you.
[08:34] And so that's why on YouTube, I won't show my API keys or if I do I'll delete them later, so you guys couldn't just run me dry of my accounts with my money stuff like that.
[08:44] Just think of it as a unique password that gives you access to your billing information, if the service isn't free, so don't share your API keys.
[08:53] You wouldn't share your password, don't share API keys.
[08:56] And just to wrap up, why is this important, it lets us link AI to systems or systems to systems, it lets us access real time data because without real time data, it's going to be horrible.
[09:10] We can have triggers so we can have web hooks or things in different events, we can have things automatically trigger things, so on my on my old website, for example, this is my old website up at AI, let's say I went to get started and someone fills out a form because they want to work with me.
[09:26] As soon as they hit submit, this would basically send a request to my end and workflow and it would capture name email project details and end and workflow would put it in a database and shoot me an email, like stuff like that.
[09:38] But it's because I'm allowed to, I'm able to, sorry, it's because I'm able to link them and have this triggered from one source to the other.
[09:49] It's consistent protocol standards so that chat models can help us I can help you everyone understands how to set this up and then for scalability.
[09:58] So the bottom line is understanding how to set this stuff up gives you unlimited abilities in an end or make or Python whatever you want to use.
[10:08] You have to understand APIs in order to make scalable systems that work.
[10:15] So once again, if you feel like you still couldn't go to a website read the API documentation and then set up an end and request that's fine, but now you understand these pieces and you understand how it works, which is the, that was the takeaway from this lesson, that was the goal that I had set up for you guys after the end of this 10 minute video.
[10:33] So thanks for the attention. I will see you guys in the community.
