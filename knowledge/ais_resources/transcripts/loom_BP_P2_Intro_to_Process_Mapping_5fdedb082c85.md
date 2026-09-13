# Loom Transcript · BP_P2_Intro_to_Process_Mapping

**Source video ID:** 5fdedb082c85413a9a2126016caed19f
**Loom URL:** https://www.loom.com/share/5fdedb082c85413a9a2126016caed19f
**Detected language:** en (probability 1.00)
**Duration:** 677.6s

---

[00:00] All right. Intro to process mapping. Process mapping for AR automations is super important
[00:07] and it's the whole process of like documenting the steps so that, you know, I'm sure you've
[00:13] heard me talking about fire framing, which is something that I like to do before I get
[00:16] into building an automation. But process mapping is like just that all wrapped up in a one,
[00:21] which is basically just being very, very clear about the exact steps that you're going to
[00:26] take so that when you're actually in and it and make whatever, whatever it is, whenever
[00:31] you're in the builder, you can basically just be looking at a guide like we have right
[00:36] here. And you know exactly what to plug in and what goes where and why. If you were trying
[00:44] to build this Lego parrot or a puzzle or whatever it was and you had all the pieces and you
[00:50] knew what the end goal is supposed to look like, but you don't have the instructions there
[00:56] or I guess with a puzzle, maybe it's like you don't know like you don't have the front
[01:00] box that shows you the picture. You could build it and you could get there, but it's just
[01:04] going to take a lot longer than if you already mapped out the entire process and you had a set
[01:09] of instructions like a wireframe. So it's essentially just creating that fundamental or foundational
[01:15] blueprint for building these animations because if you can map out all the steps and first
[01:22] of all, when you map out all the steps, you're probably going to see a lot of the complexities
[01:25] that you hadn't thought of yet. And then you can build those in. So then when you're actually
[01:29] in your workflow, you know, what you want to avoid is you get near the end and then you have
[01:32] to restart because you didn't build it right and it's not scalable or reusable or modular
[01:37] because you didn't map it out. And that's happened to me multiple times in my first couple
[01:42] of projects. I got near the end and I realized that I could have I should have been breaking
[01:45] this down into sub workflows and it just wasn't mess. So anyways, that's why it matters. We're
[01:56] going to talk more about it, but what it is, you know, is listing out every step, even
[02:02] if it's a really small step, just listing out everything in the order that happens. And
[02:08] so this gives us a visualization of the steps, the decisions, the flows, the interactions,
[02:14] the dependencies between, you know, different entities. And this is going to, like basically
[02:19] this is going to make really clear to us a few things. The first one being, where do we
[02:23] need AI? The second one being, is this a workflow or is this a an AI agent? Because do
[02:30] we know how the flow works every time or are there going to be things that are a bit unpredictable
[02:35] and non-deterministic in the sense that we don't know what the tool calling will look
[02:39] like. And then we know, okay, well, we probably need an agent for this process. And then the
[02:45] third one is, what's the tech stack? Because at that point, we'll understand what data do
[02:51] we need? Okay, if we need, if we need this customer's email, we'll have to go look that up. So
[02:55] we'll need to hit our CRM or a contact database. And if we need to, you know, create this sort
[03:01] of brief, what type of internal policies do we need for that? Okay, well, we're going
[03:05] to have to integrate with our Dropbox or with our notion in order to get that data. And so
[03:10] this is going to make it very clear what integrations we need as well. And so the whole theory here,
[03:15] actually, this is very well timed because last night I was reading an article and it pops
[03:21] up right here, Kidlin's Law, which is if you write the problem down clearly, then the
[03:26] matter is half solved. And so a lot of your time should be spent identifying the process,
[03:32] mapping it all out, having all the steps there, potentially creating a wireframe, I would
[03:36] recommend to create a wireframe. And then from there, you get into N&N, you've got one screen
[03:41] right here where you're looking at your wireframe and your process map, and you've got one screen
[03:44] right here where you're looking at the actual N&N workflow, and you're just building and you're
[03:48] just plugging things in. Especially if you're trying to communicate this to a potential client
[03:54] or to your team, you can show that value there because that proves your expertise in the
[04:01] sense of like, this person really knows how to build the system. They just showed me how they
[04:07] would build it, but they haven't done it yet because that would be like, you know, you don't
[04:11] want to build that for free. But you can show them that. And not only is that going to prove
[04:17] value, but that's also going to be a really good opportunity to align with them on what the
[04:22] requirements of this project looks like. I can't tell you how many times we've shown someone
[04:26] a wireframe. And because it's a wireframe and because it's visual and it actually makes
[04:32] sense to them, it's basically, you know, a flow chart because it makes sense to them, rather
[04:37] than like looking at N&N workflow, they're able to communicate, oh, okay, like this is not
[04:42] what we want that to do there. So like that step four right there, we don't need to do that
[04:47] at all. And like that helps you guys align as well, because now you're both visually looking
[04:51] at a process, rather than just speaking about a process with your, with your voices.
[04:56] So there's that value within. There's also the value of let's say you're giving this
[04:59] product to a developer. If you can give them a wireframe of like me and the client aligned
[05:04] on this wireframe, here it is, then it's there. Then the developers also aligned on that
[05:10] vision. And there's no room for the confusion there. So anyways, it's really critical
[05:15] for our animations because it's going to give us clarity and visibility, which means that
[05:18] we can see a clear visual overview of the full process, even if it's like, it's not going
[05:23] to be technical because it's basically just a flow chart. There's going to be boxes and there's
[05:26] going to be arrows and there's going to be, it's very intuitive. You just follow the arrow.
[05:32] bottleneck identification. So when I talked about earlier is like, you'll build this out.
[05:35] And then you'll realize some of the complexities in the system that you may not have thought
[05:39] of if you were building it out in an event step by step. So it'll show us inefficiencies, redundancies,
[05:44] and blockers. And then you're able to sort of like think about those guardrails that you can
[05:48] build before you even have to run into that issue. Error reduction. So kind of same thing here.
[05:55] It helps avoid missing critical steps. Resource optimization. It supports better distribution of
[06:00] automated versus human tasks because you understand like what types of decisions need to be made.
[06:05] And based on those decisions, what's the logic that follows that decision, scalability planning.
[06:10] This is going to be, it's going to make it easier to scale these automations with well structured
[06:13] processes because you're going to be building these things out with the idea that this is a foundation
[06:18] and we're going to build on top of these later. And then you have efficiency because it's going to cut
[06:22] down time spent actually hands on keyboard developing these systems. So a practical example of process
[06:28] mapping would be customer support emails. And this is actually like what we have down here, right?
[06:35] So a new email is received. That is shown with this Gmail trigger. So every time a new email comes in,
[06:41] the Gmail trigger fires off. From there, we're determining if the email is customer support related
[06:47] right here. This text classifier is using an AI node. So this is the AI chat model,
[06:51] which is a large language model. And we are using this AI to read the email and understand customer
[06:58] support. If yes, go this way, if no, go this way. So if yes, it's going to come to this agent. And
[07:05] it's going to look up information needed to answer the request. So it's going to go the pine cone
[07:09] vector store to look up that information. If needed, ask someone internally for missing info.
[07:15] And then what you're going to do is draft a helpful response. Obviously, this agent doesn't have that
[07:18] human in the loop functionality. We could easily work that in. But if needed, ask someone initially
[07:24] internally for missing info. And then you're going to draft a helpful response, which is right here.
[07:28] We're labeling the email. We're drafting the response and we're sending it off. And then you know,
[07:32] so this is a little bit out of order down here. But either way, like that's the steps of this workflow.
[07:36] And that's exactly how we see this happen. So a workflow is a complete automation sequence made
[07:42] of nodes. So from here, all the way to here, that is a workflow and it's made up of steps in between.
[07:48] The node, which is an individual step, can be a trigger, can be sending an email, labeling an
[07:54] email, classifying a node is each action. And that would be basically like each step. And the workflow
[08:00] would be a node. Connections are basically just between step one and two, between step three and four.
[08:06] That's we're just connecting up these things. And that's how you follow the flow all the way down to
[08:10] the end of the workflow. And the general pattern is basically, there's a trigger, there's some data
[08:16] processing, there's tool interactions, and then we get the final output. So email received, we process
[08:21] the data, we take action, and then we get the final email. When you're mapping data, some things to
[08:29] consider would be the input data structure, meaning what's coming in in its format. So because we
[08:34] know we're getting an email, we're able to say, okay, text classifier, you're going to be reading an email,
[08:38] and here's what you do with it. So we identify that, we identify how it's modified, and then what you
[08:44] output. So basically it just outputs the data down one of these paths based on the system prompt that we
[08:49] gave this text classifier and said, hey, you're going to get an email, and you're going to determine if
[08:54] it's customer support or not, customer support emails typically look like this. And we give an
[09:00] example, or we say, these are keywords that may be found in a customer support email, and it will
[09:04] use its brain to figure it out. That's a decision point. So we give it the decision criteria,
[09:12] and that is how it determines the branching. We decide what happens on each route. So it either
[09:18] goes up to customer support, or goes down to other. And if we need to, we can merge those branches
[09:24] back together in this flow or not, but we can. Okay, so a practical example, content approval workflow.
[09:34] The trigger is when someone uploads a new document to Google Drive. We would capture that data,
[09:38] it could be a web hook, it could be whatever, but we're going to capture that data. That's the trigger,
[09:42] that starts the workflow. Then we're going to extract metadata and content from that new document,
[09:47] that's data processing. Then we have a decision point, which is, is the document a blog or a white paper?
[09:53] If it's a blog post, we're going to route to a marketing manager. If it's a white paper,
[09:56] we're going to route to a technical lead. Then we have an external integration, which means we're
[10:01] sending the Slack notification with a document link. We're going to wait for approval from the human,
[10:05] and then we're reaching another decision point, which is if approved, move to the folder and notify
[10:09] the team. If it's rejected, move to a different folder, and notify the author. And then the output is
[10:14] that we update the content tracking spreadsheet with the new status. So here is just basically a wire
[10:19] frame, a flow chart of this process. So new document uploaded, extracting the data, decision point,
[10:26] what type of document? If it's a blog post, we're going to route it to the marketing manager. If it's
[10:31] a wallpaper, we're going to route it to a technical lead. But then the paths kind of come back. So then
[10:35] both of these are going to send a Slack notification and wait for approval. Then we have another
[10:40] decision point, which is is the content approved. If yes, publication folder, notify team, and then
[10:45] update the sheet. If no, move to revision folder, notify author, update the sheet. So hopefully,
[10:50] that kind of paints a picture as like this is kind of a process map. This is a general wire frame of
[10:55] a flow chart of the process. And this is what I can say, hey, you know, this is what we're thinking.
[11:00] Does this align with your vision of this workflow? If yes, we're good. Otherwise, we have to make some
[11:05] changes and iterations here. And then we know we're aligned after sort of like reviewing this
[11:10] document process map, or not document, just process map. Anyways, moving on to the next one.
