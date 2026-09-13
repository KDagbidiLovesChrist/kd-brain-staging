# Loom Transcript · BP_AZ_RAG_What_is_RAG

**Source video ID:** 049b65f8d6294468b7919e442e39e37e
**Loom URL:** https://www.loom.com/share/049b65f8d6294468b7919e442e39e37e
**Detected language:** en (probability 1.00)
**Duration:** 420.2s

---

[00:00] So, rag, retrieval, augmented, generation, I'm sure by now you've heard the term,
[00:04] if you've watched some of my N and N agent videos you've seen, you know, we have to use rag,
[00:09] we've had a rag agent, we've had, you know, an email agent where we use rag to get contact
[00:13] information from a vector database, stuff like that. So, if you're starting off in AI automation or
[00:18] even if you're not starting off, it's important to know. So, let's break it down in a simple way.
[00:25] It's basically just a smart way of combining AI's ability to understand language. It takes
[00:30] in your query and then we give it the method to go find that specific information on demand,
[00:35] very flexibly because when you're making something like an AI chatbot, something like that,
[00:41] you give it knowledge base, you give it training data. And so, if the AI is limited to, you know,
[00:48] ask it a question and the answer is not in the training data, it will either say it can't find it or
[00:52] it will hallucinate and give you some random answer that is not good, obviously. So, rag is a
[00:58] powerful ability to expand their knowledge base sort of thing. So, let's break it down a little bit.
[01:02] So, what is rag? It stands for retrieval, augmented generation, obviously, so it combines pretty much
[01:08] two parts. The first one is like the retrieval, so it's kind of the library part. It's the information
[01:14] that the agent's looking for. This is where the AI finds this was information from a huge set of data
[01:20] documents, contact data, company data, policies, that sort of thing. And then the second part is
[01:26] generation, which is sort of like the storyteller part where it uses the language skills that it has
[01:32] as an AI model and it understands the question and then once it gets the information, it responds naturally.
[01:39] That's the generating part because it has to transform the information it found into like an actual
[01:43] sentence, a response to your original question. So, combining these parts gives the agent sort of like
[01:49] the super power to always have accurate information because it finds relevant facts that generate
[01:55] response. So, why is rag useful? Basically, it's useful when the AI needs specific and accurate
[02:05] information because that always isn't included in the training data and especially it's not always
[02:10] up to date. So, that's one of the huge parts about like a vector database. Something like that is
[02:14] that you can continuously have it updated, so it's always accurate, but basically like a customized
[02:18] response system. The AI can quickly look up details from a dedicated source rather than from
[02:25] just guessing based on what it knows. This is how it can hallucinate and if you don't know, hallucination
[02:30] basically is when the AI has to bridge the gap because it doesn't understand or doesn't know the answer,
[02:36] so it'll sort of predict what it should be or it will just kind of go with something that sounds
[02:43] right. It just hallucinates basically and a big part of prompting is making sure that your agent
[02:47] doesn't hallucinate, which we'll talk about at some point too, but yeah. So, for example,
[02:52] say you have a customer support agent. The rag system will pull specific details from the companies
[02:59] website, information, documents, FAQs, or the manual and it will help the customer answer questions.
[03:06] It could also look up that specific customer who's calling, it could look up their profile and see
[03:11] information relevant to them based on the rag aspect. And then also healthcare, it can retrieve the
[03:16] latest information from medical documents, and this is super important in something like healthcare,
[03:21] of course, because you need to provide accurate answers about treatments or medicine or whatever
[03:26] it may be, and you don't want them to hallucinate there for sure. And then we have education and
[03:31] research. Rag can help students and researchers and teachers find answers directly from textbooks,
[03:37] papers, making it a great learning tool, something that I definitely enjoyed when I was wrapping up
[03:43] my college classes. So, the rag in textbook and papers was definitely helpful for me. But anyways,
[03:49] it's just a system that lets the agent tap into specialized knowledge bases to give better answers.
[03:55] So, how does rag work? Basically, three steps to break it down as simple as possible. So,
[04:02] first one is that I understand the question. So, you ask agent a question. Rag starts by analyzing
[04:07] what you're asking for because it needs to understand what information it needs to go get. So, in the case
[04:12] of NADN building agents, the query comes in, the agent thinks, you know, like, what do I need to do
[04:17] here? What am I looking for? Which tool is the one that I can access to get this information? So,
[04:22] let's say we're looking for contact information, it'll go to the contact database, and then the second
[04:26] part is to retrieve the information. So, the AI is in this database now, and now it has to look through
[04:31] this huge set of data, huge relational database if it's a vector, and it has to find similar facts,
[04:37] similar keywords from this database, and it has to get the information it needs. And then it's
[04:42] going to go back to the agent, and now that the agent has this information, and it has the query,
[04:47] it can use this to form natural language answer to what it was specifically asked in the first place,
[04:53] and basically help out the user. So, that process is going to happen pretty instantly. It's going to
[04:59] feel like a direct answer, and it's really just that three step process that allows the AI to pull
[05:03] the information you need, and get your answer. So, rag and action, imagine you're chatting with
[05:08] a AI chatbot, and you ask it, what is the return policy for this item? The AI agent wasn't trained on
[05:15] every item's every return policy, in this case. So, it has to use rag because it knows you can go check
[05:21] policy documents, and retrieve the details, and then provide an accurate answer, which is something like
[05:26] you can return this specific item within 30 days for full refund. So, then moving on finally,
[05:31] why is it important? I'm sure by now you've understood why it's important, but it allows the AI to be
[05:35] more accurate, more reliable, very tailored to specific tasks, more flexible, because you don't have
[05:41] to train a new model with every piece of knowledge. You can just train the model with like a prompt.
[05:46] This is what you need to do. This is how you access different things. This is your role.
[05:52] And then the AI can actually use the information, or sorry, use the tools it was given to
[05:56] respond faster, based on the up-to-date, accurate information. More trust for the answers,
[06:01] obviously, because we're going and getting it from the data source. And then it's just flexible,
[06:05] because it can handle tons of different questions, it's being asked, tons of different topics, tons
[06:09] of different details. So, it's super important. And finally, just take aways, you know, rag,
[06:16] retrieval, augment, and generation, you're just giving the AI the power to find information,
[06:22] and then generate answers based on information. So, whether you're interested in AI for business,
[06:27] for education, for personal stuff, it's a powerful approach in setting up agents,
[06:32] it's something that you need to understand for sure. It's not magic, by any means, but it's just a clever
[06:36] way of searching and answering. So, sort of like when you search Google to answer someone on this
[06:42] question. So, yeah, we're taking AI to a whole new level of accuracy and knowledge with rag,
[06:47] really expensive capabilities, and yeah, we should probably now get into stuff like
[06:52] vector databases, which get a little more complicated, but still not too bad. So, let's get into vector
[06:57] databases.
