# Loom Transcript · BP_P2_Data_Sources_and_Transformation

**Source video ID:** 01985ef83615445b964e25c2698f2c76
**Loom URL:** https://www.loom.com/share/01985ef83615445b964e25c2698f2c76
**Detected language:** en (probability 1.00)
**Duration:** 619.9s

---

[00:01] So I've been hammering home data data data and effective process mapping requires clear identification of where data comes from and where it needs to go.
[00:09] Like I said, we're just moving data from node to node and that is what a workflow is.
[00:15] So identifying data sources, it can enter our end and end workflows from multiple places.
[00:20] It can be a user input in the form of a form submission, a chat interaction or manual entries.
[00:25] It can be a system event, meaning a notification from some sort of application that we've integrated into our workflow.
[00:31] It can be a database, it can be records retrieved from existing data stores or, you know, a vector database or a SQL database that you have, whatever it is, files, content documents, spreadsheets, media files or APIs where we're pulling it from some sort of external service.
[00:52] So once we understand the data sources, we also understand, we also need to understand the data structure.
[00:57] So for each source, the process maps should document, what is the format?
[01:01] Does this come to me in JSON or CSV or binary, especially if it's binary?
[01:06] You guys will see there's a lot of stuff that happens with binary that you need to kind of change the logic a little bit more if it is binary.
[01:14] Required fields, specific data elements needed, optional fields, additional data that may be available.
[01:20] I had this as a tile size because it's like not always, but there are some use cases where you do need to understand some things are required, some things are not.
[01:30] Data types, you need to understand if they're text, numbers, dates or Boolean values, and we've talked about these data types before.
[01:38] And then we have to have volume considerations, meaning how much data is going to come through what's that size like and the frequency of how often data is going to be flowing through the system.
[01:48] From there, we talk about, you know, we understand the sources, we understand what it's going to look like.
[01:54] Now we have to talk about how does it transform?
[01:56] So the way that the data changes through the workflow could look like field extraction, meaning we're going to get back a ton of JSON from a file.
[02:08] But we only want like the invoice number and the amount, so we're going to extract that data out.
[02:14] Or maybe we're converting it, so we're changing it from binary to JSON, which we do a lot to actually be able to work with it.
[02:21] Or maybe we are enriching it, so we're adding more information in, so like we're pulling in a customer's record, we're getting that in JSON, we're going to use a sales call transcript to enrich it.
[02:34] And then we're going to absurd it back into the CRM on that customer's record and like there's going to be more information now in other fields.
[02:43] Calculations, maybe we need to do operations and performs a sort of analysis or aggregation where we're combining multiple data items together and then spitting them out somewhere else.
[02:53] And that's when we need to identify the destinations.
[02:56] So sometimes we process data and just in the back end and it goes into something else. Sometimes we're processing data and we're sending off an email.
[03:03] What does that look like? Is it going to be stored somewhere? Are we pushing it into external systems? Are we sending notifications?
[03:09] Or are we doing some sort of dashboard report, visualization, anything like that? What are we doing with the data?
[03:16] So those are like the four main steps, right? So practical example here is lead enrichment.
[03:21] So the data source, this is going to come in through the form of a form of response. This comes in as a JSON payload through a web hook.
[03:28] So just it's coming through as JSON and we're getting it from a form submission.
[03:31] We have key fields like name, email, company, phone number, interest area, and that is the trigger.
[03:37] Then we're going to transform it. So we're going to standardize all this. We're going to convert the name to first and last name components.
[03:43] We're going to format the phone number to a standardized way so we can always work with it consistently.
[03:48] And we're going to convert the interest area to an internal category code. So that's like we're transforming the data.
[03:54] Once we've transformed that data, then we move into a data source lookup. So we're going to check if the email exists in the CRM.
[04:00] If it does, we're going to return the contact ID, the account ID, and the last activity.
[04:04] And to do this lookup to access this data source, we know we need a Salesforce API because we need to authenticate into that external service in order to get more data.
[04:15] From there, we're going to do some sort of transformation and enrichment, meaning we're going to make an API call to the company information database somewhere.
[04:23] We're going to add in the fields of company size industry and location.
[04:27] And there's some sort of airing here where maybe the API fails, we could boot back and try again.
[04:32] But if it fails three times, we're just going to keep on going through the rest of the flow, which would be now we enter a decision point.
[04:39] So we see if the contact exists, we're going to update that record.
[04:44] But if it doesn't exist, we're going to create a new record.
[04:47] We have a data destination, meaning those two records, we're either going to update or create, we're doing that in our CRM.
[04:53] So we need once again an API key to CRM, we're going to do it in Salesforce, we're going to update the fields and then we're going to map on the enriched fields in the CRM schema, meaning like name, email, company info, interest area, all this, it's going to map on the right columns.
[05:10] And then another data destination is we also want to receive some sort of notification.
[05:15] So sending it to Slack, we'll need to credential ourselves, authorize ourselves into Slack, we will send a new lead message, and then we'll format that in some sort of JSON payload likely to send over to Slack.
[05:27] And that's like the full journey of the data sources, the transformations, the credentials we need, how the data flows through and then what it does, like what is the final destination of, okay, the workflow is done.
[05:41] And so as you can see, like this is a very clear process, and it shows how the data is accessed, transformed and then delivered, it just moved from left to right across the whole process, across the whole flow.
[05:51] So to define these processes steps and logic, we're just breaking down complex processes into discrete steps, and this is essential for successful automation.
[06:03] So breaking down complex processes, we have single responsibility, which is one function per step, logical sequence, which is they follow a natural order, input, output clarity, meaning each step, well, the process is a whole, the workflow is a whole, but also granularly each step should have an input and an output, and then exception handling anticipate and manage these errors because there will be errors.
[06:31] We also have identifying required actions and transformations, so for each step, is this going to be, you know, what is the action here, are we retrieving, are we creating, are we updating, are we deleting, what are the tools we need, so is this going to be, can we do this in N and N, like where are we just converting data in N and N, or do we need to go to Slack to do something.
[06:51] You input requirements and the output requirements, and then potential failures.
[06:56] And then we have mapping the decision logic, so we have condition, which would be what triggers each of these branches, if it goes off this way or this way, like what is that decision point, we have branch identification, which means if it goes up this way, what happens next, or if it goes down this way, what happens next.
[07:14] We have merging logic, so if it splits into the two paths, do they ever come back together, like an example we saw earlier with that flow chart, or do they just kind of like go down their own paths and definitely.
[07:25] Identifying that type of stuff could be a good indicator that maybe we want to send these off to sub workflows rather than keeping it all on one workflow, not every time, but that could be a good indicator at sometimes.
[07:35] And then just default behavior, if none of those criteria are met that branch off into the two, but what happens maybe it's just a third path, or maybe there's a default branch it will go down something like that.
[07:46] So any that has nodes like if switch and filter and these nodes let you branch and use logic to send things off to different paths, and then at the end you can use the merge node in N and N to bring everything back together in one line.
[08:00] So another practical example here, we have a document generation process, so we're going to take an action, which is collecting data, we're going to retrieve data, we're going to do that with an HTTP request, we know the input we're sending over, which is I want data from this date range.
[08:17] The output is going to be the data and then we have air handling like try three times, but if you fail on the third time, then we're just going to keep going or actually know in this case, we wouldn't even be able to keep going because we don't have any data.
[08:29] So we would try three times, otherwise, we would probably just send a notification like hey, we failed, I'm trying in later.
[08:36] Then with that data, we have a transformation step, so we're going to calculate KPIs, we would use a function or code node, we would input the raw performance data, we would output the KPIs, and then we would also have air handling of course.
[08:49] Then we reach a decision point, so are any of these metrics below 80% of target, we would use an if and just say basically like if below, or sorry, if, yeah, if below 80% do this, if not do this, and so we would have like different branches, right, so we have these two branches, we would then have to decide what happens for each branch.
[09:10] Now we have an action step, we're going to generate a document and we would use a create PDF report, we would have the tool to do so, we are giving it the process data and a template, we are expecting an output of a PDF document, and then we have air handling.
[09:26] We have our decision point with delivery method, which is who's the recipient is going to go to an executive department head or a team member, and based on which branch, we have a different way we're delivering it, and then finally an action step is a notification.
[09:39] Setting an email notification or slack notification, as you can see, so hopefully I didn't like go too much there as far as like said the same thing over and over, but it's really important to understand each step and the different things that could happen at each step, because then like I said, this is where complexities may pop up in your mind that you hadn't thought of earlier, and this will help you actually get into a workflow builder.
[10:10] You can build it out right the first time, or at least as close as right that you can be on the first try, so yeah.
