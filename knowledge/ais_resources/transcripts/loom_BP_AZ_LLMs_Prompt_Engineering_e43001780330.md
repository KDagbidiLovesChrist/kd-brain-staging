# Loom Transcript · BP_AZ_LLMs_Prompt_Engineering

**Source video ID:** e430017803304f0191cbb2280d8a8bac
**Loom URL:** https://www.loom.com/share/e430017803304f0191cbb2280d8a8bac
**Detected language:** en (probability 1.00)
**Duration:** 611.9s

---

[00:00] All right, so in this video, I'm going to be talking about how to talk to AI and what that means is understanding
[00:06] How you can get more and use them more effectively based on the way that you
[00:10] You know prompt them essentially so prompt engineering
[00:13] I'm sure it's a term that you've heard before but really the idea is that we talked to them in a way where once they become
[00:19] Sentient enough and powerful enough. They don't kill us
[00:22] That was a joke, but actually I did see something about
[00:25] There was a study where if you're rude to chat you be T. It gives you better results
[00:30] Which I thought was really interesting because I got in this habit of saying please before all my requests
[00:33] I'm not sure if you guys can relate but
[00:36] The reason I made that little joke is cuz I just this is kind of creepy to me, but anyways
[00:40] Yeah, it's interesting that
[00:42] Being rude for some reason gives you better results for chat to be used to specifically, but anyways in all seriousness
[00:49] The way that you talk to these models changes their performance drastically
[00:53] especially especially
[00:56] In automation because when you're talking to something like chat you be to your cloud if you don't like its output
[01:00] You can just say hey, I didn't like this do it again
[01:03] But in an automation they're supposed to be hands-off and so you need to get your prompts right so that when you're feeding data through while you're sleeping
[01:09] It calls the right tools. It sends the right types of emails. It does the right lookups and your outputs are nice
[01:14] And so there's not that back-and-forth luxury, which is why the prompting is so important
[01:20] So if you guys can hear that hopefully the microphone is facing the right way enough that it's blocking it all out, but
[01:27] I live on a crazy busy street and
[01:32] It's just a lot of fire trucks and ambulances. So I'm wasting enough time. Let's just get into the video
[01:37] So what is an LLM? We've talked about this right. It's a large language model and
[01:42] At its core it basically just is able to use its training data and use what you give it to
[01:47] Create output and it kind of predicts the next word. So
[01:51] If you said the the dog jumped over the it would understand okay based on
[01:56] The meaning of these tokens that just came in what would make sense to be next and there's all these different words
[02:02] That it kind of chooses from and it just picks it continuously picks like what word comes next so it could say log it could say
[02:09] Frog it could say chair. It doesn't know like you know there's different things I could say but anyways
[02:14] That's what it is at its core without tools without prompting without all of this context. It's they're not very smart
[02:20] They just say they just say things honestly
[02:23] So what is prompt engineering? It is the art and it truly is an art of
[02:27] crafting it effective instructions that tell the AI exactly what you want it to do
[02:32] Meaning how to talk what type of output what tools to call when to do this when to do that
[02:38] And I truly believe we're entering this space where prompts are your IP
[02:43] Workflows are becoming commoditized
[02:46] And it has 6,000 free templates. I have over 150 free templates
[02:50] Other YouTube creators other people have templates and templates and templates that you're giving away for free
[02:56] And the value is not in the templates if they're all being given away for free of course the value is in the prompt
[03:01] And the data that you put in so store your prompts
[03:05] That is your intellectual property
[03:08] If you have a vague request like make me something to eat
[03:11] And this is like I'm thinking like from a human right now
[03:14] If I if I said to you make me something to eat
[03:16] What are you going to make me there?
[03:18] You know it could be anything and then I could be unhappy with that result
[03:21] But if I'm more specific make me a protein rich meal with chicken and vegetables after my workout
[03:25] You know exactly what I'm looking for you know exactly what I'm asking for and you also know it's coming after a workout so you may even throw in
[03:32] Some amino acids or a protein shake or pre-teen whatever I don't know whatever you think I need based on that request
[03:38] Why prompt engineering matters
[03:41] Sometimes I get carried away with this highlighting. I'm sorry
[03:45] So
[03:46] This isn't just theory right like people have obviously been creating these models optimizing these models and then studying how to optimize the results
[03:54] There's a reason why opening eye has put out prompting guides google's put out prompting guides and why I'm making this video about prompting
[03:59] so
[04:00] 70% improvement users report up to 70% better output quality with refined prompts
[04:06] Three times faster while crafted prompts get results in fewer tries and once again when we're talking about automation
[04:12] We only really have one try you could work in some human and the loop logic that retries infinitely until you're happy with the output
[04:19] But for a truly scalable system you don't have the time to manually approve everything
[04:23] You want to be able to sleep or be in a meeting and do whatever and it should just be running and you should trust it
[04:28] And so you need to get your output right on the first try
[04:31] 50% time saved less editing and regenerating responses pretty much the same thing right
[04:36] So
[04:37] Better quality increased efficiency reduced errors and consistency. That's why prompt engineering is so important
[04:44] And so here are four core components to think about now
[04:48] This doesn't go across all types of prompting there's different types of prompting in my mind the two the two main ones are
[04:54] Generative creative prompting or tool calling prompting and I think they're different
[04:58] I'm not going to dive super deep into that right now, but here is my philosophy
[05:03] When I am prompting for generative. So maybe I'm creating
[05:07] I'm prompting an agent that's going to write an email or I'm prompting an agent that's going to create
[05:11] Video prompts for like a Google VO3 or something like that
[05:14] When I'm doing that type of prompting I like to brainstorm with AI and have it help me create the prompts
[05:20] When I'm doing tool calling prompting so for AI agents that have multiple tools
[05:24] I like to handwrite those prompts because I like to keep them concise short and clear
[05:29] The same way that if I was telling you how to do a job. I would just tell you very clearly very simply and
[05:35] There's a difference there and so I just wanted to preface this, but here are like four core things to be thinking about right
[05:42] You have the instruction
[05:43] What are you asking the AI to do? We're asking you to explain a concept to you
[05:47] Are you asking it to go grab information and do research?
[05:49] You're asking it to write a list or you're asking it to compare things summarize things generate things
[05:55] the instruction
[05:57] Then you have the context so any background information that helps the AI understand your situation and your needs
[06:03] Then you have the format. How do you want the response to be back?
[06:06] Do you want bullets? Do you want paragraph form? Do you want it in a code window?
[06:09] Do you want it in JSON? Do you want to step by step guide? What do you want?
[06:15] And then finally, which is usually what I start with actually is like the persona
[06:19] or the role and whenever I'm making an AI agent in an event or I'm talking to a system gpt or a custom gpt that I'm building or something in chat or Claude
[06:30] I always start with like you are a blank you are an expert newsletter writer you are a teacher teaching kindergarten classes you are a
[06:38] Expert YouTube script writer whatever it is just kind of framing the behavior upfront with the persona or with a role
[06:45] So real quick here's some components in action. So bad prompts is tell me about exercise
[06:49] It's not specific. There's no context. There's no you know your personal trainer you can see right here
[06:54] Act as a personal fitness trainer. I'm a complete beginner. That's context who hasn't exercised in years and wants to start building healthy habits more context
[07:02] Here's the output of what I want create a simple two-week workout plan for beginners that I can do at home with no equipment once again more context
[07:09] Format it as a weekly schedule with specific exercises and durations for each day
[07:14] So here's how you can already maybe be thinking about when you're using chat gpt in your day-to-day
[07:19] Other components that you have been missing
[07:21] So we've got the persona once again personal fitness trainer
[07:24] We've got the context of a beginner with no workout equipment
[07:26] We've got the instruction and then we have the format
[07:32] So we've got now some more best practices
[07:34] Which are to be clear and specific
[07:36] Providing relevant context use examples so examples are huge
[07:41] Especially if you realize that you're not getting outputs the way you want
[07:44] You can have all your instructions and everything but say hey here's a good example here's kind of like
[07:49] What I'm looking for and then give it an example
[07:51] Ask one thing at a time
[07:53] Not if you're doing automation if you're working with chat gpt
[07:56] Um, you can break complex requests into separate focus prompts
[08:00] And then specify the format so tell AI how to structure it and then use action verbs
[08:04] So very clear instruction verbs generate analyze summarize explain compare create research etc
[08:13] And one important thing to be thinking about as far as like a mindset is that prompts will never be perfect initially
[08:20] It's the same thing with workflows and agents like you have to build your first proof of concepts your first iteration and then you
[08:28] Get feedback and you build upon it
[08:30] And this is how most things in life work
[08:32] But you have your initial prompts and you send off your request you analyze what do you like what do you not like
[08:37] That's your version one
[08:38] Refine the prompt
[08:40] That's your version two and then do it over and over again
[08:43] And like there are prompts that I've written back in January of this year so
[08:46] Depending on when you're watching this
[08:48] January of 2025
[08:50] And i'm constantly refining them still i've gpt's i'm constantly refining i've agents
[08:54] I'm constantly refining in terms of prompt because also every chat model
[08:59] Interprets props a little differently
[09:00] So clawed opus 4 is going to interpret your prompts different than chat gbt or chat oh three or google flash so
[09:08] There's always room to be improving. I kind of have the mindset of there's no such thing as a finished prompt
[09:14] anyways
[09:16] So before and after examples
[09:17] I want to cook something could be turned into i have chicken breast bell peppers onions and rice
[09:21] I'm cooking for 4 and i need something ready in under 30 minutes suggest a simple recipe with step-by-step instructions
[09:26] I'm not going to read this other one because i think we get it
[09:28] But you can see here we have context
[09:31] We have more context and then we have like
[09:34] The ret uh not the recipe the instruction and the format so i think you guys get it at this point
[09:41] The key takeaways here
[09:44] Start simple
[09:45] Just experiment building and testing things is way better than watching videos
[09:50] Build on top of those responses
[09:52] Save what works and then just be patient just keep working with it prompt engineering is a skill
[09:58] There are people that are taking courses on this people are selling courses on this
[10:01] 20 hours of content just about prompt engineering. It's a it's a skill
[10:04] It's an art and like i said that is kind of where your ip lays. So thanks for your attention. I will see you guys around
