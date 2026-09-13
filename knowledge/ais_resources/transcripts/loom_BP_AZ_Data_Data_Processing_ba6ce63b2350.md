# Loom Transcript · BP_AZ_Data_Data_Processing

**Source video ID:** ba6ce63b2350414a9a1b08de5a7927b8
**Loom URL:** https://www.loom.com/share/ba6ce63b2350414a9a1b08de5a7927b8
**Detected language:** en (probability 1.00)
**Duration:** 452.2s

---

[00:00] Okay, so data processing, I don't want to go super, super in depth, right?
[00:05] This is just kind of a foundational course is to get you familiar with certain terminology
[00:09] and certain aspects of workflow automation, but data processing is super important.
[00:14] I've said many times and I will continue to say like data in, data out, data is the most
[00:18] important thing we can give our agents and our workflows, context is everything.
[00:22] Data is king, but in order for that to be true, the data has to be formatted correctly
[00:28] and predictably so we can say, hey, agent, this is what you're going to get, this is what
[00:33] you do with it.
[00:34] And it's really simple once we get that, that figured out.
[00:37] And so it's just about what sort of automated pipeline do we have to give to our data in
[00:42] order for it to actually like make sense when it's looking at it, doing something with
[00:45] it and outputting more data.
[00:47] So why this matters is we need first of all, parse format and clean the data, which are
[00:52] like the three main things really, so that it becomes structured, reliable, and ready
[00:56] for analysis or automation.
[00:58] And just kind of doing an intro of like what that means, the challenge of this is that
[01:02] businesses have tons and tons of data, and it's often like not stored somewhere centrally.
[01:09] So in order to actually access it, we'd have to go to these, you know, we have to get everything
[01:12] from your Slack, everything from your Google Drive, everything from your SharePoint, everything
[01:16] from your Dropbox, everything from your CRM.
[01:19] And we want to basically have that more centrally located so all your automations can plug into
[01:22] it.
[01:23] But besides that, it's going to be unstructured and inconsistently formatted, which makes
[01:27] it really hard to predict, like, you know, a lot of times the problem is like we have
[01:31] to tell people, we're going to set this pipeline up, but like in the future we need you to do
[01:37] this with your data.
[01:38] It can't just be like sometimes the company or the client or you has to change the way
[01:43] that you're currently storing things, because sometimes you store for the immediate quick
[01:49] transfer of like, okay, got this done, don't have to worry about it.
[01:54] But then later, you're going to be thinking, oh, where did I leave that?
[01:58] And, you know, how do I get that, or you're going to have to ping one of your co-workers
[02:03] on teams and say, where did we drop that dock?
[02:05] And it's like a big problem I read this study about like, a lot of times spent is work
[02:12] about work, meaning reaching out to people, wasting their time, wasting your time, trying
[02:17] to find where documents live, all that kind of stuff, huge time waste, but we want to set
[02:21] up these pipelines to take care of that.
[02:23] Anyways, a little bit of tangent, but their data is filled with errors or irrelevant information,
[02:28] it has white space, it has null values, whatever it is.
[02:31] We want to clean it, parse it, process it, and then we're going to go, right?
[02:35] So for example, an e-commerce website may send product data in HTML format, which has
[02:42] unnecessary tags and code, and it's not been cleaned and it's not been structured, so it's
[02:46] hard to use without that preparation.
[02:48] It's hard to analyze, it's hard to automate.
[02:51] So data processing is parsing, which means extracting and converting data from one form
[02:55] to another, formatting, which means we just standardize how it looks, and cleaning is fixing
[03:00] errors and inconsistencies.
[03:03] So like I said, those are the three pillars.
[03:05] Parsing means we kind of like extract, we transform, we organize, and we can actually
[03:12] access it.
[03:13] An example here would be scanning a driver's license to extract the name, date of birth,
[03:18] and address in two different form fields.
[03:21] And that means we're scanning the driver's license, and we can put their name in the name
[03:27] field, and we can give them a customer ID, and we can put their date of birth there.
[03:31] And so now we have it in an Excel structured format that we could later query all of the driver's
[03:36] license we've scanned and get information back quickly, rather than having to go, oh, okay,
[03:40] we just store these as pictures.
[03:42] And now we have to go look through these pictures to understand where is Stan Smith's driver's
[03:46] license, rather than just being able to query for Stan Smith and find his driver's license
[03:51] details.
[03:53] But obviously they can be stored as tables, databases, e-mails, social media posts, or the
[03:58] semi-structured JSON HTML XML.
[04:01] From there, it's about formatting.
[04:04] So this just means that we organize and present it in a consistent structure and appearance.
[04:08] So that would just be the aspect of we send it into this table every time with these values
[04:13] being passed over.
[04:14] So it ensures consistency and proves the readability, promotes compatibility across different
[04:19] tools.
[04:20] Like if we got everything into JSON format or an ability for it to be pulled in and worked
[04:25] with JSON format, that's perfect.
[04:28] So this could do certain things in like some of this is nitpicky, but you probably want all
[04:31] of your dates to be standardized.
[04:34] If you're having everything in the month, month, day, day, year, year, year, year, then you
[04:39] want everything in that format.
[04:41] It just wouldn't make sense to have like all the dates just differently, or all the dollar
[04:46] amounts differently, or all of the addresses formatted differently.
[04:50] Number formats, splitting and combining text, meaning do you want to have a first name
[04:54] in a last name field, or do you want there just to be a field called full name?
[04:59] Not saying which one is right or wrong, but you need that to be consistent.
[05:05] And there are tons of stuff you can do with no code formatting.
[05:08] So hotspot workflows, you can format names, calculate values, change text case, air table,
[05:13] Google sheets, browser bear, these offer like drag and drop formatting and transformation
[05:17] options, or like functions within the actual air table or Google sheets itself.
[05:22] So there are ways to do this like not in NADN, and sometimes you want to do that in your
[05:26] external service first before you send data into NADN, or you can have NADN send data into
[05:30] that platform, and then it will do it from there.
[05:33] But I guess the point is, there's a lot of functionality for this because it's important,
[05:40] like there's a reason that stuff exists.
[05:42] And then finally, data cleaning, also called data scrubbing, but that's just identifying
[05:46] the errors and fixing those and fixing the inconsistencies, whether that's missing values
[05:50] or duplicate records, outdated stuff, typos, extra punctuation, that's just getting rid
[05:56] of that sort of stuff, which helps accuracy, it helps save time, it's going to improve the
[06:02] quality of your actual data.
[06:05] And if there's any regulations that you need to be compliant with, you want to help make
[06:09] sure that the data is actually clean for those regulations.
[06:14] So just a high level parse when you're extracting instruction information from a raw or messy
[06:20] source, and you're getting what you want out of it, so like scanned invoice, you want to
[06:25] get the actual information you're looking for, which would be like the date, the company,
[06:30] the invoice amount, the invoice ID, whatever it is.
[06:34] And then once you have that, you're going to format it some way.
[06:36] So every time you're getting this stuff from the invoice is you want to format it somewhere
[06:39] and put it somewhere.
[06:41] And then cleaning would just be like, we're going to run it through this data cleaning flow
[06:43] just to make sure there's no null or white space or typos, stuff like that.
[06:51] Anyways, just real quick best practices, start simple, document your steps, reuse your workflows,
[06:56] validate, and then iterate.
[06:58] And then once you continuously do that and you have different formats of data passing through
[07:01] your workflow, that's what we call like a data pipeline, an automated data pipeline, where
[07:08] we can then effectively throw any form of data in there, and it's going to go through the
[07:13] process of basically cleaning and standardizing and formatting, and then we're going to get
[07:16] something on the other side that we can use for our AI agents, and that's like the end goal.
[07:21] Because then from there, it's really cool.
[07:23] You can staff these automations on top of each other because they'll have access to company
[07:26] data.
[07:27] So that is data processing at a high level.
