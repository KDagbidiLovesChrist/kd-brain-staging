# Loom Transcript · BP_AZ_Data_What_is_Data

**Source video ID:** 1e1dedde2a724417916e8fe0c19a5319
**Loom URL:** https://www.loom.com/share/1e1dedde2a724417916e8fe0c19a5319
**Detected language:** en (probability 1.00)
**Duration:** 542.9s

---

[00:00] Okay, so what is data?
[00:04] And obviously, we all know what data is, but there are some elements of data that are
[00:09] going to be really important to understand when we get into the actual world of automations.
[00:14] And I'm sure you've heard me say before, but the data is the most important thing besides
[00:20] probably the prompt, but it's the most important thing that we need, like foundationally, that
[00:25] we need to create automations that actually integrate seamlessly and actually produce high
[00:31] quality outputs and actually adopt the tone of the subject matter expertise of what
[00:39] we need to do here.
[00:41] So you've heard data in is data out, so garbage in is garbage out.
[00:47] Data is really important.
[00:48] Anyways, at its core, data is just a collection of facts, statistics, information, and it can
[00:54] be used for many things.
[00:56] And the reason it's important to talk about is because it can come in many forms, and
[01:00] with our automations, a lot of times we need to understand how is it going to come in and
[01:04] then how is it going to come out?
[01:06] And the more predictable the better, but sometimes it's not always going to be predictable, and
[01:10] we kind of have to work our systems to adjust for that.
[01:13] So it can be numbers, text, images, sounds, sensor readings, anything that represents any form
[01:17] of information that is data.
[01:20] And when we really get into it, if you're not coming from like a data analytics background,
[01:24] it may not have heard what a string is, or what a Boolean is, or an integer, or a float.
[01:31] That's why we need to talk about it, because that's kind of how more it's referenced within
[01:36] something like NIDN.
[01:38] But it's pretty universal.
[01:39] So anyways, just in general, a string is like a word.
[01:43] It's text, float, integer, numbers, Boolean is like a true or false.
[01:48] So we'll get into that.
[01:49] Anyways, data is everywhere, it powers everything.
[01:52] So why are we learning about data?
[01:54] Because as automation builders, we define the path that data follows.
[01:57] That is basically our job, is we are moving data from one end of the workflow along the path
[02:03] into the other end.
[02:04] Obviously, if it's an agent, it's a little different, because it's a not deterministic.
[02:07] We don't know exactly how the data is going to flow, but we do know we're going to get some,
[02:10] and we need to do something with it.
[02:12] But when it comes to workflows, we are basically holding its hand and setting up the guardrails
[02:17] of you are staying in this path, and you're basically just going to go down the logic.
[02:21] And we're setting data, and we're just moving it along.
[02:25] So we need to know where it enters, how it's processed, and then what happens next.
[02:30] Over time, we'll have to make sure that we can handle unstructured or messy data, convert
[02:34] data between different formats, and integrate with external APIs, which is going to be a different
[02:38] module.
[02:39] But APIs, you know, that's where the magic actually happens, because we're in an end end.
[02:45] We want to automate something, and even it's not an end end.
[02:48] We're in something, and we want to automate processes.
[02:50] But we're not that powerful, unless we can talk to external services.
[02:54] So end-end itself cannot do anything in your calendar, your email, your CRM, your database.
[03:00] We have to send some sort of connection in order to access those different things.
[03:04] And sending these connection requests, and connecting to different services, that's another transfer
[03:10] of data, from end-end to your Google suite, or from end-end to your Slack.
[03:16] That's a transfer of data, so we have to understand that.
[03:19] And by mastering data, that's how we're actually going to be able to turn our ideas of what
[03:23] processes we want to automate into actual automations that unlock the full power of these systems.
[03:29] So one first thing to understand is there's structured data, and there's unstructured data.
[03:35] Structured data, most typically in the real world when you're thinking of structured data,
[03:39] it is a Excel sheet, or a Google sheet, because it neatly fits into rows and columns.
[03:44] It's a lot more predictable.
[03:45] It can be SQL queried, if you don't understand SQL, it's basically just a programming language.
[03:51] It's really more of a querying language, because you have all the structured data, and you know
[03:56] what the rows and columns look like, you can basically say, find me, what was our total
[04:05] sales in March, and then basically you could query, you could write a query that would pull
[04:11] every single row where the sale equaled March something, and then you could say, okay,
[04:18] for all those rows, let's sum up all of the sales.
[04:20] And so it's just like doing analytics on data that fits into these rows and columns, because
[04:26] that's predictable.
[04:27] Anyways, easy searchable, stored in relational databases, and you can manage it using SQL
[04:32] queries.
[04:33] Examples would be spreadsheets with employee details, customer contact databases, financial
[04:38] transaction logs, inventory records, sales data, customer, I don't know, I took a database
[04:45] management course in college, and one of the examples was always just like, when it comes
[04:54] relational databases, you've got a student database, which would have my full name, student's
[05:00] full name, student ID, and maybe their birthday, or something.
[05:04] And then you would have like different course databases, so it would be like the course,
[05:09] and then you'd see all the student IDs that are enrolled in that course, and maybe their grades
[05:13] and whatever it is.
[05:15] And you would use that student ID to say, okay, student 12 is in this course, let's look up
[05:20] student 12 when our student database, and we can say student 12 is Nathan Herkelman, here's
[05:25] his birthday, here's his information, here's his email, whatever it is.
[05:28] So that's like you can have these relations between different databases on some sort of foreign
[05:31] or primary key, not going to get too into the weeds, but hopefully that at least makes
[05:35] sense.
[05:37] So then we have unstructured data.
[05:40] Unstructured data is irregular, and it lacks a fixed schema.
[05:43] And most of the world's data, even though if you're operating in the world of spreadsheets,
[05:47] you think everything's a spreadsheet, most of the world's data is unstructured, because
[05:52] this can come in the form of, I guess, you know, there's kind of a, we talk about here
[05:56] like structured, semi-structured data, but so much stuff is like a PDF or an SOP document
[06:03] or it's just a wall of text or it's an email or it's, you know, information in your CRM
[06:08] or whatever it is, social media posts, photos and videos, audio recordings, like I said,
[06:14] this is just messy data that doesn't have a predictable fixed schema, makes up 80 to 90%
[06:19] of all data in the world.
[06:22] Yeah, especially because everything is like online nowadays.
[06:26] So anyways, then we have text versus numerical data.
[06:29] So text data is qualitative.
[06:31] It means that it describes qualities or categories and it's usually not measured with numbers.
[06:35] So this could be names of people or places, product descriptions, customer feedback, emails
[06:41] or chat logs, text-based SOPs, and these have meaning, right?
[06:46] Like it's different than numbers, numbers have like meaning as far as like which ones higher.
[06:51] But text has different meaning as far as what does the context of these three words put together?
[06:55] What does that mean?
[06:57] And then we have numerical data, which is quantitative.
[06:59] This measures actual quantities and it can either be discrete or continuous.
[07:03] So something discrete means like how many products have you sold 12?
[07:08] That's not like a continuous value that goes on indefinitely.
[07:12] Like you don't sell 12.1 products or 12.125 products, you sell 12 or 13.
[07:18] Continuous is something that's measurable, like temperature.
[07:22] You could never really drill down on like an exact temperature.
[07:24] It could be 73.125, 6.9 degrees, but that's like an infinite amount of like measurable continuous
[07:32] numbers.
[07:33] But okay, now I'm just kind of, I'm rambling there.
[07:35] But anyways, age is measurable.
[07:38] It's continuous.
[07:39] Price is discrete.
[07:42] Product ratings, income, website traffic, like you have all these different ways that numerical
[07:45] data can be represented, represented, represented, but at the end of the day, it's all quantitative
[07:50] because it tells us about some sort of quantity.
[07:53] And then we have semi-structured data.
[07:55] So this is like kind of sits between structured and unstructured.
[07:58] A little bit of a gray area here.
[08:00] But like things can still be sort of tagged in some sort of structured way.
[08:04] Like emails can be like, okay, you know, who did this come?
[08:07] Who's the sender?
[08:09] Who is the recipient?
[08:11] Who was CSEED?
[08:12] What labels are this in?
[08:13] What label is this in in your inbox?
[08:15] Log files, JSON files.
[08:18] But typically the main distinction I make is does this fit cleanly and predictably into what
[08:22] a table, an excel sheet, or does it not?
[08:26] And that's like when I would say structured versus unstructured.
[08:29] So anyways, the reason why this matters is because each data type requires a different approach
[08:33] for your storage, for your processing, for your analysis.
[08:38] Don't want to get into the weeds here, but it's really important to understand what does
[08:43] this data look like and how do we want to query this data?
[08:47] Because that's going to help you actually understand the data pipeline and the automation
[08:50] that you're going to build out to handle it.
[08:52] So it's going to be really important for working in AI, data science, or automation.
[08:57] But anyways, that's going to be it for this one, and I'll see you guys in the next one.
