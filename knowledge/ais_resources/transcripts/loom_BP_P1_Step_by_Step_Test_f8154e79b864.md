# Loom Transcript · BP_P1_Step_by_Step_Test

**Source video ID:** f8154e79b864484ea6d0a591a7139c46
**Loom URL:** https://www.loom.com/share/f8154e79b864484ea6d0a591a7139c46
**Detected language:** en (probability 1.00)
**Duration:** 582.1s

---

[00:00] Okay, now we're going to cover a few topics where lots of people generally make mistakes.
[00:05] In this section, we're going to cover three things.
[00:08] One, why automation is the last step?
[00:12] Because you cannot automate a process that you have not defined appropriately.
[00:15] Two, we'll see the logic extraction, which is how you write down a sequential list of instructions
[00:21] for what I call a mental habit.
[00:24] And finally, we're going to learn the instruction manual test, which is a filter that tells
[00:29] you if a process is actually ready to be automated or not.
[00:32] Okay, let's get started.
[00:34] Why is automation the last step?
[00:37] Here's where most people go wrong.
[00:39] They find a task that annoys them, they open an 8n or whatever automation tool they use,
[00:45] they start building, and then they get stuck.
[00:48] They realize that they don't actually know all the steps.
[00:52] They heed edge cases that they didn't anticipate, they need to rebuild, they end up troubleshooting
[00:58] the logic, and sometimes they need to start over.
[01:02] So the problem here is not building an automation, but it's actually knowing what to build.
[01:07] Because most automation failures happen before you even open a single tool like an 8n.
[01:14] They generally happen when you try to automate a process that you have an actually defined.
[01:19] So the core principle of this lesson is you cannot automate a process that you haven't defined.
[01:25] This is why automation is just the last step that's the final execution.
[01:29] The real work is actually extracting the logic from your processes first.
[01:34] So how do we extract the logic?
[01:36] Every task that you do, even the ones that feel automatic, they all follow a sequence of steps.
[01:42] The problem is that you probably done them so many times that they have become mental habits.
[01:47] You don't even think how to do them that you just do them automatically.
[01:52] You don't even think how to do them.
[01:53] You're not even conscious that you're doing them.
[01:56] You just do them.
[01:58] But to automate something, you need to reverse engineer your mental habit into a sequential
[02:03] list of instructions.
[02:04] And here's how we're going to do it.
[02:06] First you're going to pick a task from your time inventory.
[02:09] This time inventory is the list of tasks that we created in previous videos after you audited
[02:15] yourself.
[02:16] Step two, the next time you do this task, I want you to slow down and try to document
[02:22] every single step.
[02:24] Try to be very mindful of what you're doing and try to document everything.
[02:28] Three, you're going to write it down as if you're explaining it to someone who's never done
[02:33] it before.
[02:34] And for this, in step number four, you're also going to include decisions, not just the actions.
[02:39] The decisions are, for example, the logic.
[02:42] If something happens, do this.
[02:43] If not, do that.
[02:45] And finally, you're also going to note where you look up for information where you're copy
[02:50] pasting or where you're switching between tools.
[02:53] I want you to document everything.
[02:55] Let me give you an example here.
[02:58] Let's say the task is send weekly project update to a client.
[03:01] The step one could be we are opening the project management tool, which is notion.
[03:07] This step is an action and it's the first step.
[03:11] Then for the second step, we're also going to do an action, which is copy completed task
[03:15] from this week.
[03:17] Then we have to check if if there are blockers, no them write them down.
[03:22] If not, we can skip.
[03:24] This is not an action.
[03:25] This is actually a decision.
[03:26] This is part of our logic.
[03:28] So instead of classifying this as an action, we're going to classify it as a decision.
[03:33] Next, we're going to paste this info into an email template.
[03:37] Again, this is an action.
[03:39] Then we're going to add next week's priorities from the task list.
[03:42] And finally, we're going to send the email to our client's main contact.
[03:46] And in this case, we're going to be using Gmail to do this.
[03:49] And this is how we can extract the logic of one of our processes, of one of our tasks.
[03:54] We've basically audited this task and wrote down every single step that is needed in order
[04:01] to complete that task.
[04:02] Once we have written down our steps, like we've done here, we're going to apply this
[04:07] filter.
[04:08] If a human cannot follow your notes, then a machine cannot either, or at least they may not
[04:13] do it correctly 100% of the times.
[04:16] So if your instructions have gaps, assumptions, or required judgment calls that you haven't
[04:21] documented, it probably is not ready to automate yet.
[04:25] Because if a person who was not able to follow your instructions, how is a computer supposed
[04:30] to do it correctly?
[04:31] I mean, we could use an LLAM that could guess and try to act accordingly, but you're basically
[04:36] gambling on it.
[04:37] That's not going to be a reliable automation.
[04:40] So some common failures that I see people do when writing down the logic is for example writing
[04:46] down things like, check if it looks right.
[04:50] Okay, but what does it mean?
[04:52] What does right mean?
[04:53] You need to define your criteria.
[04:55] What does right actually mean?
[04:57] Or they could also write down, send to the appropriate person.
[05:01] Who's appropriate?
[05:02] What's the logic for deciding who is appropriate here or not?
[05:06] Another example could be, handle any issues.
[05:09] What issues?
[05:10] Give some examples and what's the handling process for each one of them?
[05:14] And finally, a very common one, especially when using LLAMs.
[05:19] Sometimes they write down, use your judgment, but judgment based on what rules.
[05:23] Again, try to give examples and try to cover all possible scenarios.
[05:28] The more information and the more detail, the better.
[05:30] So if you find yourself writing vague stuff like this, that's a sign that you need to go deeper
[05:35] and keep working on your logic extraction exercise.
[05:38] Let's see an example where we can see what we should not be doing and what we should be
[05:42] doing.
[05:43] So let's say that the task is process new lead inquiries.
[05:47] Maybe your first attempt to write down the logic steps could be check email for new inquiries,
[05:54] set them up them to the CRM and send a follow up.
[05:58] And as you can see, these are actually three vague steps.
[06:02] If you give this to someone else to an assistant, for example, they're probably going to have
[06:07] a lot of questions and they're probably not going to be able to follow through without
[06:10] even asking you something or without making mistakes.
[06:14] So how can we do this correctly with more information, making it more precisely?
[06:20] Instead of saying check email for new inquiries, we can say in a very detailed way, open Gmail
[06:26] where specifying the tool and check for emails with contact form in the subject.
[06:32] Then instead of just saying up them to the CRM, we can say for each email extract the
[06:38] sender's name, the email, the company, and message.
[06:42] Then go to half spot CRM again, we're specifying the tool search if the contact already exists
[06:49] by email.
[06:50] If it exists and here we're actually adding logic, which we didn't even mention here.
[06:55] So if it exists update the existing record with new inquiry date, if new create a new contact
[07:00] with name email company, set lead source to website contact form, compose a follow up email
[07:07] using template A, if they're asking about service X, template B, if service Y, personalize
[07:12] the greeting with their first name, log the follow up in the CRM activity template.
[07:17] So we can actually see how we went from three simple steps to actually defining in a very
[07:23] detailed way each single step, the tools that we're using, the logic that is involved.
[07:29] So if we give this list of actions to an assistant, for example, they're definitely going to be
[07:34] able to follow along without making mistakes in comparison to sending them this list of
[07:41] actions.
[07:42] And it's actually okay, if you're first attempts, it's something like this, it does actually
[07:47] very common until you get used to going more deeply and more in a more detailed way into
[07:53] every single one of your steps.
[07:56] Just make sure that you take this into account so that with practice and over time, you're
[08:00] going to be writing down an extraction logic and having full steps of actions like this.
[08:06] But what if you are not sure if what you're doing, your logic extraction looks more like this
[08:11] than this one exercise that we can do is called the delegation dry run.
[08:17] You're basically going to pick one task from your list that you think is ready to automate.
[08:21] You're going to write down every step as we've been doing.
[08:24] For example, thinking that you're training a new employee who knows nothing about the subject,
[08:29] and you're going to include every decision point and logic behind each decision.
[08:33] You're going to know where you reference other information templates or tools.
[08:37] And with this list, you're going to have someone else follow your instructions.
[08:42] And while they are trying to follow this instruction step by step, you're going to mark every place
[08:48] every step where they either had to ask you a question or where they could not follow the
[08:54] instruction well enough.
[08:56] For example, they made a mistake, they used the wrong tool or they used the wrong template.
[09:02] And once they finish this test, if there were no question marks, no mistakes, no errors,
[09:07] then congratulations.
[09:08] That's wonderful news.
[09:09] That means a human was able to follow along your logic, which means you've got a process
[09:14] that's ready to be automated.
[09:16] And if there are gaps or questions or any errors, that's actually great too.
[09:21] Because now you know exactly what needs to be defined and improved before you start building.
[09:27] So remember automation is actually the last step.
[09:30] First you need to extract the logic, document the steps, and make sure a human could understand
[09:35] them without any gaps or any questions.
[09:38] And only then I suggest that you start building your automation.
