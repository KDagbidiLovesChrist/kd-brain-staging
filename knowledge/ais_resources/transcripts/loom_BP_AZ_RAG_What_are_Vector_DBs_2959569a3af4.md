# Loom Transcript · BP_AZ_RAG_What_are_Vector_DBs

**Source video ID:** 2959569a3af4423c8095a9056df4bacc
**Loom URL:** https://www.loom.com/share/2959569a3af4423c8095a9056df4bacc
**Detected language:** en (probability 1.00)
**Duration:** 486.8s

---

[00:00] Okay, so now that we understand RAG, we need to understand how an agent uses retrieval augmented
[00:05] generation to go to a vector database and what exactly a vector database is and sort
[00:10] of how they work.
[00:11] So, I'm wondering about vector databases today.
[00:14] It sounds technical, and at first it might sound like, what is this guy talking about?
[00:18] But break it down into something that's simple and easy to understand.
[00:21] So, imagine it like a unique kind of library that doesn't just store books in like rows
[00:27] and shelves, instead think of it as like it stores items in a way that the AI can understand
[00:32] and make sense of kind of like a memory bank.
[00:35] So, it's like a special library, like I said, it's not using, you know, regular structured
[00:40] type of data with rows and columns like a regular library with rows, tables, shelves.
[00:47] But in a vector database, information is stored in vectors, which are kind of groups of numbers
[00:52] that represent certain things.
[00:55] These numbers don't look like words or pictures.
[00:57] They're more like lists of numbers that represent text, images, sounds in a way that the computers
[01:04] can understand, because it's sort of like a multi-dimensional relational database.
[01:09] So, it's 3D, it's not just like an x-axis y-axis, it's like stuff goes this way, stuff comes
[01:14] this way, it goes all over as you can see in this picture kind of like, you know, it's
[01:18] like relational.
[01:19] So, you'd be looking over here for animals and then the AI is going to find stuff that's related
[01:23] to that stuff.
[01:24] You go over here for fruits, and you've got like, you know, Apple and Google, so it has
[01:28] to use context to understand like where to put them in these dimensions.
[01:31] And as you can see up here, it would be like the vector, the sort of like the number numerical
[01:36] representation of the data.
[01:38] And so, that's how it's going to work as far as like relations.
[01:40] But what exactly is one vector?
[01:43] A vector is the list of numbers that kind of describes the complex object.
[01:47] So a vector might represent the word car, and then there'd be a list of numbers that
[01:51] describe its meaning.
[01:53] So that's the numbers that it uses based on like the characteristics.
[01:58] So in here like, you know, 0.34, 2.35, these kind of represent different aspects of whatever
[02:06] the specific item or the specific text, and then things that have similar number structures
[02:10] are kind of relationally in the same area.
[02:12] So that may have been the worst explanation ever, it may have been great.
[02:17] Let me know hopefully you guys, that makes sense, but we're going to keep diving in and making
[02:20] it a little more simple.
[02:22] So it's basically going to help the AI understand characteristics rather than like specific
[02:27] static hard-coded things in a database.
[02:31] So the magic in this vector database is something called embeddings.
[02:36] So next video, we'll talk more about embeddings, but basically embeddings are a group of vectors
[02:41] that the AI uses to remember things.
[02:43] So it's like turning words or images into numbers, and obviously that's how it matches
[02:47] with relation.
[02:48] But let's go through some fun use cases.
[02:52] So chatbots and language models, by storing relationships between words as vectors, these
[02:59] databases can help chatbots understand the context of the conversation.
[03:02] So if you say, tell me a joke, the AI can understand what you want and respond with humor.
[03:08] Image and video recognition is cool.
[03:09] You can search for similar images on the internet because the vector database allows the AI to recognize
[03:14] similar images and compare them and place the near ones that it already knows.
[03:19] And then like other search recommendations for, if you're looking for a product online,
[03:24] the vector database helps the system suggest similar things based on what you've liked
[03:29] or searched before.
[03:30] So you've had a lot of interaction already with vector databases without even realizing it,
[03:35] you know, because of Google searching, that sort of stuff.
[03:38] Now we're just actually trying to configure them and set them up for our AI agents.
[03:41] So we have to really understand how they work.
[03:44] OK, so now let's talk about the benefits of using one.
[03:48] So three main things I want to point out here is flexibility, scalability, and speed, and performance.
[03:54] Speed and performance kind of together, but flexibility, the database can handle tons of different
[03:59] types of data, text, images, sounds, and you can kind of just embed them in there.
[04:04] You don't need to change them and manipulate them too much.
[04:07] Obviously there's some things as far as optimizing it, but just for today's sake, you don't
[04:12] need to change it too much.
[04:14] Scalability, vector databases can store millions and even probably billions of data points, making
[04:21] them perfect for AI models that need tons of information to work well, which ideally when
[04:26] we're helping out, you know, businesses with implementing some of these agents and these
[04:29] rag aspects, it's going to be a lot of data.
[04:32] So tons of data, super scalable, that's huge.
[04:36] So then also speed and performance, since the data is in number form, AI can search and
[04:42] compare and find relations super, super quick, compared to maybe having to go through thousands
[04:47] of rows in a Excel spreadsheet, which are going to make the processes like responding and
[04:52] getting answers much smoother, much faster.
[04:56] So why are these essential for AI?
[04:59] Think of it as like the AI's memory, the AI needs to answer a question, make a recommendation,
[05:03] keep conversation going, it's going to go pull information from that vector database,
[05:06] so it gives it the power to have context, history, comparisons, all that kind of stuff.
[05:13] And so another big question is when do you actually use one?
[05:16] When would you rather just have stuff in a structured database, an Excel table, air table,
[05:22] compared to wanting to put something in vector stores?
[05:24] So the vector database is best for situations where you want to find similarities or patterns
[05:29] in data that don't really fit neatly into structured database forms like rows and columns.
[05:35] So text images and audio, obviously, I've said that a couple of times, but that's like
[05:39] a great use of it, especially like huge, just reading walls of text and being able to
[05:45] extract stuff really quick is where the vector database is really shine.
[05:49] But the big thing is unstructured data.
[05:52] So if you have information that doesn't go into rows and columns, vector database is going
[05:57] to help by organizing that in a way that the AI can easily compare and search through.
[06:01] It's going to find some of the things that we talked about, text images and audio, say
[06:05] that once again, and then hide dimensional data if it's super complex with many features,
[06:10] it's super easy to measure these similarities and find stuff that you need.
[06:14] So then how our vector database is structured, it's converting each piece of data into a vector,
[06:23] into a numerical form vector or a list of numbers.
[06:27] So each number is going to represent a feature or quality of the data, like I said.
[06:32] So just off the top of my head, let's say we're talking about cars.
[06:36] And you have numbers, numbers, numbers, the first one could be like representing how fast
[06:40] the car can go.
[06:41] The second one can be representing type of engine, third one can be representing the color,
[06:46] this kind of stuff.
[06:48] And so that's how it's going to compare stuff so that you, if you were looking for a vintage
[06:54] blue car with a specific engine, it would be able to find that kind of stuff.
[06:59] And if it wasn't hard coded into the description of the car, if that makes sense.
[07:04] So in summary, basically, it's a powerful tool for finding similar things in complex data.
[07:12] It's going to help the AI understand and remember things, making it very essential for recommendation
[07:17] systems or search engines or any other type of application that might need to recognize
[07:23] patterns from just simple natural language keywords.
[07:27] Yeah, it's just like a smart library, stores information, and it's a database that's really
[07:32] important for AI.
[07:34] For the future of AI, it's going to help all of us create more advanced, you know, use cases,
[07:39] more advanced applications than, I guess, than what we currently would be doing if we were
[07:44] using a Google sheet.
[07:46] So that hopefully broke down, you know, vector databases in a good way.
[07:53] If you were to search for a data database on Google, and you'd see a lot of your relational
[07:59] images, that I think that really helps me sort of grasp the concept.
[08:02] But yeah, we will move on to next module here.
