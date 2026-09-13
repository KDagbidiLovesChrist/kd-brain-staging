# Loom Transcript · BP_AZ_Data_What_is_JSON

**Source video ID:** 50b2a602d6104e87851f342b1e6d8636
**Loom URL:** https://www.loom.com/share/50b2a602d6104e87851f342b1e6d8636
**Detected language:** en (probability 1.00)
**Duration:** 659.4s

---

[00:01] Okay, so in this one, we're going to be talking about Json.
[00:05] So by the end of this video, you'll understand how you can code agents with Json.
[00:11] I'm just kidding. We're not going to learn how to code.
[00:13] Json may sound intimidating, but it's really, really simple.
[00:16] And that's the idea of this video is just to get you familiar with first of all,
[00:20] what Json is and understanding why it's important to understand.
[00:23] And like I said, it's really, really simple.
[00:26] The way that I like to think about it and how I learned it was I just think about filters.
[00:30] As in when you are ordering food online or you're ordering clothes online,
[00:36] you can have filters, you know, like what restaurant do you want it from?
[00:39] What side do you want or what color do you want?
[00:42] What size? What style? It's just filters. It's really, really simple.
[00:46] And the reason why it's so important is because it is the universal standard for internet communication.
[00:53] So when you want to build an agent that talks to Gmail, that's Json.
[00:57] When you want to build a system that researches information that's going to be using Json,
[01:02] both in what type of request you're sending out and then the data you get back,
[01:06] that's all going to be Json.
[01:08] And so it stands for JavaScript object notation.
[01:10] It's super simple to understand and the good news about it is if you don't understand what you're looking at,
[01:16] you can just give it to chat to be tea, claw, Gemini, Groc, whatever you want.
[01:20] Because it's so universal that all of these models were trained on it so well and they understand it so well.
[01:25] So it's nothing to be intimidated by. This video is going to be super high level.
[01:30] But by the end of it, you should understand what you're looking at and how to read Json really well.
[01:34] It's super easy.
[01:36] So why does it matter? Like I said, it is universal exchange of data.
[01:41] It's simple and readable. It's lightweight and fast.
[01:43] And it is the foundation of automation.
[01:45] Without knowing what you're looking at when you see Json, you will not have a great time automating things.
[01:50] So like I said, it's filters and it's super, super simple.
[01:53] You just think of it as key value pairs.
[01:55] So if you looked at this, you could tell me exactly what this is telling us, right?
[02:00] It's telling us that a person, their name is Sarah.
[02:04] They air their age is 28.
[02:06] And the city they live in is New York.
[02:08] That's super simple. It's English. It's basically, hey, here's the key.
[02:11] And here's our value.
[02:12] So your key could be, or I guess let's say mine would be name, Nate, age, 23 city, Chicago.
[02:19] It's that simple.
[02:20] The reason why it looks a little bit intimidating sometimes is because you have these curly braces that have to like wrap it up.
[02:25] And then you've got like colons and commas.
[02:28] But it's really easy, right?
[02:29] So the key is always a string in double quotes on this left hand side.
[02:32] It always has double quotes.
[02:34] The colon separates the key from the value.
[02:36] And then the value can be any data type.
[02:38] So right here, we have a string.
[02:40] And strings are wrapped in double quotes right here.
[02:42] We have a number.
[02:43] No double quotes right here.
[02:44] We have another string wrapped in double quotes.
[02:47] Okay, so I know I want a little fast there, but we will be looking at this a little bit differently.
[02:52] And also you would have just came from a video watching data types in general.
[02:56] So you understand like what a string is, what an integer is, what a Boolean is.
[02:59] And now we're just kind of talking about how they're represented differently in JSON.
[03:03] So like I said, a string is enclosed in double quotes.
[03:07] So we've got first name is John double quotes.
[03:10] A number, which is an integer or a decimal will not have quotes.
[03:15] So if you ever see, let's say 25 right here was wrapped in double quotes.
[03:20] That means that the computer or the agent or the service thinks that this is a string.
[03:25] And so sometimes you could have numbers coming through as a string.
[03:28] For example, sometimes dates come through a string.
[03:30] It's like April 19th in double quotes.
[03:32] That's a string or two thousand twenty five dash nine dash whatever.
[03:38] That could also be formatted as a string.
[03:41] And so being able to just understand, OK, there's no double quotes.
[03:44] So the computer knows as a number.
[03:47] Not going to get too technical here, but that's important because let's say you wanted to add together.
[03:51] Or you wanted to take the average of everyone's names.
[03:54] You cannot take the average of strings.
[03:56] So you may be getting an error and you would, OK, I need to convert all of these ages to numbers.
[04:01] And then I can take, you know, I can do summarizations or calculations with it.
[04:05] So hopefully that's resonating.
[04:07] Bullions are, they look like strings, but there's no double quotes.
[04:11] And you'll typically only see true or false.
[04:13] So if you ever see true or false with no double quotes, it's a Boolean.
[04:18] Then we have nulls, which will also just be no double quotes, and it will literally just say null.
[04:21] So that's super easy.
[04:23] And then work, it's a little complex is when you think about objects or arrays.
[04:29] So what object is when you have a big list of key value pairs and they're wrapped up by curly braces.
[04:36] Like we saw up here in this example, this would be an object.
[04:40] And in that object, we have the name, which is a string.
[04:43] We have age, which is a number and we have city, which is a string.
[04:46] And that's all in one object that represents this person.
[04:50] Now, that's an object.
[04:51] You know, in your object, you could have strings, bullions, numbers, all of them.
[04:54] You could have whatever.
[04:55] But now you have an array.
[04:57] And in an array, it's an ordered list of values.
[05:00] So you could have a shopping list.
[05:02] And in that array of shopping list, you could have apples, bananas, grapes, meat, potatoes.
[05:08] Or you could have an array of numbers.
[05:12] You could have one, two, five, seven, twelve, one, six.
[05:16] And that could be an array.
[05:17] It's just a list.
[05:19] And that is represented by square brackets.
[05:24] You could have an array within an object as well.
[05:29] So that's why it may seem like it gets complicated.
[05:31] Again, if you can't look at it and read it and understand it with natural language,
[05:36] copy and paste it into chat and say, what am I looking at?
[05:39] And it will tell you exactly what you're looking at.
[05:41] You can even say, hey, define which ones of these are strings and which are numbers.
[05:44] It'll tell you.
[05:45] So here are some real world examples.
[05:48] Right here, what do we have?
[05:49] We have an object.
[05:50] And we know it's an object because curly braces.
[05:54] Within this first object, which is the order ID here, we have a string.
[05:59] And there's numbers in it, but there's double quotes around it so we know it's a string.
[06:03] Now what you see here is we have an object within an object.
[06:06] So we have an order ID.
[06:08] Right.
[06:09] And then we have a customer object because these values relate to customer.
[06:13] So first name relates to customer age relates to customer.
[06:16] And it is premium member relates to the customer.
[06:19] We have a string in Emma.
[06:20] We have a number in 29 and we have a Boolean in true.
[06:25] So hopefully that'll make sense just let it kind of soak in there.
[06:27] Different data types objects can be an objects.
[06:30] There can be a raise in objects.
[06:33] All this kind of stuff.
[06:34] Now here we have an item list.
[06:39] And in this item list, we have a object.
[06:42] We've got a product name, which is headphones.
[06:44] We've got a quantity, which is one.
[06:47] And then we have a price, which is this number.
[06:52] We also have the order total.
[06:54] And so this would be a list of different items that we have.
[06:57] As you can see, so.
[07:02] If that didn't resonate or click or you don't feel like you've mastered Jason.
[07:06] That's fine.
[07:07] This was just to get you kind of like a prerequisite to going into this chorus about automation.
[07:12] Or then when you're looking at it, you at least understand what's there.
[07:16] So it's really important to understand for a automation because as you transfer variables between nodes.
[07:21] We make requests to different services.
[07:23] You'll be using Jason.
[07:24] Like I said.
[07:25] So retrieve data, process data, take action, all going to be using Jason.
[07:30] For example.
[07:35] Let's say you're setting up an HTTP request, which there'll be a video after this about API's and what HTTP requests are at a high level.
[07:41] But basically let's say.
[07:44] I am having my agent send a request to my CRM.
[07:50] This is basically saying, OK, Mr or Mrs CRM here's what I want you to do.
[07:56] The action I want you to take is the create user action.
[08:00] Here's the user data.
[08:01] It's an object of this user.
[08:03] This person is named Sarah Davis.
[08:06] This person's email is Sarah at company.com.
[08:10] That was my user data object.
[08:12] Now I have a notification object.
[08:14] In here, I'm saying, OK, send welcome email true or false.
[08:18] We're going to say true.
[08:20] And so basically in natural language, I would be telling you.
[08:23] Hey, go create a user in the database for Sarah Davis, her email is Sarah at company.com and then send her a welcome email.
[08:29] That's all that's going on right here in this Jason.
[08:32] Now, once we send that off, if I told you to do that as a human, you would probably come back and say, OK, I made the user.
[08:38] Here's the ID.
[08:39] I, you know, the next steps are to do this.
[08:42] And that's exactly what the service sends back.
[08:44] OK, success equals true user ID equals here.
[08:49] The message is that user was created.
[08:52] And we have our next steps, which are to this is a list, by the way, you can see this is an array.
[08:56] There's two next steps send a welcome email and then add to calendar.
[09:00] So hopefully that like real example makes sense of the way that we send it and receive it and what we're looking at here.
[09:06] So the rules.
[09:10] Just to come back to later, there are certain little tiny things that will break your Jason.
[09:15] If you have double quotes.
[09:19] Used wrong.
[09:20] It will break.
[09:21] If you have trailing commas, it will break.
[09:23] If you have certain comments, it will break.
[09:26] Unique keys, you can have two, the same keys.
[09:28] And you have to have proper nesting.
[09:30] And I just wanted to highlight this because Jason can be frustrating and confusing if you get a message that says, hey, that's not correct or hey, this doesn't work.
[09:39] Because there's tiny, tiny little things that will break it.
[09:42] All you need to do is copy and paste your Jason into chat or cloud or Gemini and say, hey, my Jason's not working.
[09:48] What's wrong?
[09:49] It'll say, oh, you missed a comma here, or you missed a space here, or you have a double quote here.
[09:54] So it's really, really simple.
[09:55] And when I have my Jason breaking, if I can't identify right away because I see a comma or whatever, I'll drop it into chat and I'll ask and then I bring it back into n and n.
[10:03] So hopefully this gave you a good understanding of Jason and makes you understand just not to be intimidated by it.
[10:11] The more you look at it, the easier to get.
[10:13] The more you use validators, like literally if you go to Jason validator, if you type that in Google, there's tons of websites that help you validate it, or you can use chat to be to your cloud.
[10:21] And then just start building, you know, throughout this challenge or throughout the course that you're taking.
[10:26] It's going to make sense because you're just going to start to see it more.
[10:29] And it's all about reps, it's all about exposure.
[10:31] When I first got into Jason and API requests, API calls, I wanted to cry.
[10:36] I remember looking at the computer like, what is this?
[10:40] And now it's like, it comes right away.
[10:43] I don't even have to think about it twice. It becomes a second language.
[10:46] So if you guys are feeling like that right now a little bit overwhelmed.
[10:50] You're almost there. Just keep climbing. You'll get there.
[10:53] And then it's all downhill after that. So thanks for the attention. I'll see you guys in the community.
