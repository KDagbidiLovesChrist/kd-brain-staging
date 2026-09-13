# Loom Transcript · CC_P2_1.7_Skills

**Source video ID:** 7a364982c57d4ab580654a040984e0ae
**Loom URL:** https://www.loom.com/share/7a364982c57d4ab580654a040984e0ae
**Detected language:** en (probability 1.00)
**Duration:** 334.1s

---

[00:00] In this video, we're going to learn about skills.
[00:03] Skills are one of the most popular features for making your workflows consistent and efficient.
[00:08] By the end of this video, you're going to understand what they are, why they matter,
[00:12] and how to get a Cloud code to build them for you.
[00:14] So, what are skills?
[00:16] If you've been paying attention to the WAT framework, skills are going to be very familiar
[00:21] because fundamentally skills are workflows.
[00:24] It's basically the same idea.
[00:25] It's a markdown file with natural language that tells Cloud what to do.
[00:29] The difference is how they are triggered and where they live.
[00:33] A skill lives in a special folder within the Cloud slash skills directory.
[00:38] And it will become a slash command.
[00:40] If you're not familiar with slash command yet,
[00:42] don't worry, we're going to see a full example
[00:44] and how to create them in the next video.
[00:46] But they're basically reusable commands that anyone or a cloud can invoke
[00:50] and run that workflow in just one command.
[00:53] And just like workflows, skills can reference tools.
[00:56] Tools are Python scripts that do the actual work.
[00:59] An example of this could be a web search tool, a scraping tool, a document generator tool.
[01:05] So, you can see that the WAT framework is actually fully intact underneath.
[01:10] Skills are just a more advanced and more reusable way
[01:13] to package the W layer, the workflows layer.
[01:17] So, a quick note on how skills work in Cloud code.
[01:20] Skills live in the Cloud skills directory.
[01:23] Each skill is going to be a folder with a skill mark down file within each one.
[01:28] So, the brand voice skill is going to have a skill file within the skills directory.
[01:34] If it sounds too complex, don't worry, it's actually not.
[01:37] And we're going to see a full example in the next video.
[01:39] What's important to understand here is the file structure,
[01:42] which is going to be a bit different from the WAT framework.
[01:45] So far, we've been using the workflows directory for instructions.
[01:49] And here, we're going to be using the skills directory for instructions or skills.
[01:54] Both approaches work, they're both the same idea.
[01:57] The only difference is that the WAT framework uses the workflows directory
[02:01] to keep things explicit and easy to see.
[02:04] While the skills is Cloud code's native home for skills and slash commands.
[02:09] As you get more advanced, you're probably going to store your reusable workflows as skills.
[02:13] But for now, just know that they are the same concept under different locations.
[02:18] And why do skills matter?
[02:20] Skills help us keep consistency.
[02:22] You can run the same process every time without having to re-explain.
[02:26] It's going to help us save tokens because skills are loaded on demand.
[02:30] Cloud code is only going to load the full instructions
[02:32] when you invoke the slash command or that specific skill.
[02:36] So, having 20, 50 skills is not going to load your context
[02:40] in comparison to having all these skills in Cloud MD file, for example.
[02:44] If we had every instruction and every requirement in Cloud MD file,
[02:48] that would be loaded into context in every session.
[02:51] And that would load our context.
[02:53] They are easier to share.
[02:54] We can share these across our team so everyone can use the same workflow
[02:58] and they also make our project more reliable.
[03:01] If any of the instructions are too complex
[03:03] or we may forget the steps on how to achieve that goal,
[03:06] you could wrap those instructions and those steps into a skill
[03:09] and there will be no need for you to remember them.
[03:11] You can just delegate and forget about them.
[03:14] And what is great about Cloud Code is that you don't even really need to understand
[03:18] what a skill or how to create them.
[03:20] You can just tell Cloud Code what you want and it's going to build a skill for you.
[03:24] Just describe the workflow and say that you want to turn it into repeatable slash command or skill.
[03:29] For example, hey, Cloud, I want to create a skill called meeting summary.
[03:33] When I use it, read the file I pass as an argument,
[03:35] extract the key decisions, action items with owners and discussion points.
[03:40] Then as an output, I want a document in the temporary folder.
[03:43] And in the next video, we're going to see a very similar prompt to create our very first skill
[03:48] and how to call it as a slash command.
[03:50] And finally, when should we use skills versus when should we just type what we want?
[03:56] We want to use a skill whenever we see that we have a workflow that we keep calling repeatedly,
[04:00] whenever consistency matters so we can wrap all that logic all that workflow within one skill.
[04:06] And that same skill is going to be called every single time whenever we have complex instructions
[04:12] and we may forget about them or we may prompt them differently every time
[04:16] or whenever we need to share the skill within our team.
[04:19] And when should we just type instead of creating skills?
[04:23] Whenever we have a one off task, a task that's not repeated ever,
[04:26] a task that we only want to do it once.
[04:28] We could just type if we are still experimenting, if we are new to Cloud Code
[04:33] and we want to test it out without adding too much complexity, then I would just type.
[04:38] And finally, I would just type and avoid skills if maybe the task or the instruction is simple enough
[04:43] that you can describe it in a sentence and maybe creating a skill would be an overkill for that.
[04:49] And finally, when should we add instructions in the Cloud MD file versus when should we add them as skills?
[04:55] The Cloud MD file should only mention the rules that are going to be used on every single session.
[05:01] It should explain what the project is for, what's the main goal
[05:05] and what framework it should follow like the WT framework,
[05:09] but it should not contain the instructions for each single skill,
[05:13] because that's going to be a very easy way to blow your context window.
[05:17] So you want to use Cloud MD file for rules that are going to apply to every single session
[05:22] and you would create a skill whenever you would create a workflow or a set of instructions for a specific task.
[05:28] In the next video, we're going to go into Cloud Code
[05:31] and we're going to start building our first skill.
