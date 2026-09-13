# Loom Transcript · BP_AZ_RAG_Real_World_Applications

**Source video ID:** 91a6a24735c84551ab1b5aacaf66567f
**Loom URL:** https://www.loom.com/share/91a6a24735c84551ab1b5aacaf66567f
**Detected language:** en (probability 1.00)
**Duration:** 616.5s

---

[00:00] Okay, so when it comes to sort of diving into vector databases,
[00:03] I think something that's really important to understand
[00:05] is the actual practical applications
[00:08] of why we want to use this kind of stuff.
[00:10] Why it's important?
[00:12] Because sometimes AI can be thought of as like magic
[00:16] and there's lots of buzzwords,
[00:18] so are we over complicating it
[00:21] and using vector databases because it's the cool new trend?
[00:24] Or is it actually important to you?
[00:27] So that's what we're going to talk about real quick today
[00:30] and we'll see why it's so important.
[00:31] We'll get into some actual real world examples
[00:33] because you probably are noticing vector databases,
[00:36] we're not noticing, but there's probably vector database
[00:38] applications within your life every single day.
[00:40] You just don't notice it.
[00:41] So before we sort of dive into those specific examples
[00:45] that you see here, you've got these 10 examples
[00:48] that we'll go through very briefly,
[00:49] but essentially I understand why we want to use these
[00:52] why they're pivotal in the fields of AI
[00:55] and the fields of machine learning.
[00:58] Traditional databases like Excel obviously are
[01:00] great at storing structured data, numbers, dates, text,
[01:05] where a row is sort of an identifier
[01:07] for the whole row of data.
[01:10] And then obviously with more modern AI
[01:14] and machine learning models,
[01:17] they're going to be working with high dimensional data
[01:21] on these representations are kind of the ones
[01:23] that are known as like our vector embeddings.
[01:25] So anyways, why use vector databases?
[01:29] So some key advantages.
[01:31] The first one is that it's for handling high dimensional data,
[01:34] AI models are going to output vectors obviously
[01:36] and these represent complex data relationships.
[01:40] So because these relationships are complex,
[01:42] vector databases are designed to way more efficiently store,
[01:47] query, and retrieve these high dimensional vectors
[01:51] unlike in traditional databases
[01:52] which are going to be not as optimized
[01:54] for this type of task.
[01:56] They're going to be better for certain tasks,
[01:58] but not sort of like these similarity searches
[02:00] as you can see moving into our next point
[02:03] because these AI applications a lot of times
[02:05] are lying on searching for similar items.
[02:10] This is going to be a concept you hear repeated
[02:11] probably throughout this vector database deep dive,
[02:14] but searching through to find similar items
[02:17] like a similar document, a similar image,
[02:20] similar meanings of what we're looking for.
[02:23] Because vector databases are able to use their algorithms
[02:26] in order to quickly sort of compute,
[02:29] we won't really get into the actual math
[02:30] that's taking place computing different points
[02:32] and the different dimensions between
[02:34] to find those relations, but that's basically what's going on.
[02:37] And so because of this, it's very scalable.
[02:41] These AI systems are often going to be dealing
[02:43] with massive, massive data sets
[02:45] and because vector databases are built for scale,
[02:49] Excel has, I forget the number,
[02:51] but I ran into this one time at work
[02:53] where I hit the maximum amount of rows on Excel
[02:57] and I don't know if it is like a quarter of a million
[02:59] or what, but I was like, man, the sucks
[03:02] because now we have to split up this data
[03:04] and also the sheet, let's say we wanted to search for it,
[03:09] search through it, pull data through it.
[03:11] We would basically have to, maybe I'm wrong here,
[03:13] but you would be loading in the entire sheet
[03:16] and then you're able to query through it
[03:18] and it's just not very efficient.
[03:19] So because we're able to do things like splitting up
[03:21] and using metadata and if you're using pi and count
[03:23] with your namespaces, it's going to be more efficient,
[03:26] build for scale, which will ultimately result
[03:29] in faster retrieval, faster processing,
[03:31] even when you get up to millions and millions of vectors.
[03:36] And then finally here we've got, they really integrate well
[03:39] with our AI workflows, with our AI models.
[03:42] They're going to enable advanced functionalities
[03:44] like we talked about with the semantic search,
[03:46] recommendation systems, retrieval augmented generation,
[03:49] of course, for these AI applications.
[03:52] And so some of the more broad use cases
[03:55] when we talk about AI and machine learning,
[03:57] the first thing to understand is natural language processing.
[04:01] You'll see a lot of times it's called NLP,
[04:03] which is just like it sounds, processing the way
[04:06] that we would ask a question in natural language
[04:09] to actual like SQL queries to filtering within something
[04:14] like that, but we can just use natural language, which is huge,
[04:17] because a lot of people don't have the coding background.
[04:21] I've got some SQL background.
[04:23] I've got a little bit of Python, but I don't want
[04:26] to be writing that all day.
[04:27] So anyways, natural language processing
[04:30] allows us to store and query for these specific word embeddings
[04:33] or just embeddings.
[04:37] And we can do this through something
[04:38] by just talking to an AI agent.
[04:40] And it's able to turn our language into some sort of query.
[04:46] And then we have like computer vision.
[04:47] So managing these vectorized representations of images
[04:51] for similarity searches, for tagging,
[04:54] for being able to intelligently recognize
[04:56] what's going on within that image.
[04:59] We've got personalization systems.
[05:01] Obviously, recommendation systems is a huge part
[05:04] of vector databases, recommendation engines,
[05:07] like Google.
[05:09] We'll get into that in an example, but also music,
[05:13] recommendations on Netflix, sort of just based
[05:16] on the way the user's interacting, the user's preferences.
[05:20] Real-time decision making, which will enable certain systems
[05:23] like fraud detection or cyber security,
[05:27] because this could really, really change the game
[05:29] when it comes to cyber security.
[05:30] But anyways, looking at like threat analysis
[05:32] by retrieving that relevant data way quicker.
[05:36] And then hybrid AI systems, supporting RAG,
[05:40] where AI combines stored knowledge with generative models
[05:44] in order to provide more accurate and context-aware responses.
[05:47] So hopefully that at least made a little bit of sense.
[05:51] Let's look at some of these real-world examples.
[05:52] So the first one we have here is, like I said,
[05:55] recommendation systems.
[05:56] And this first one we're talking about is Spotify.
[05:59] So Spotify leverages vector databases
[06:02] to analyze audio features and to analyze your listening habits.
[06:08] Spotify Rats, I just got that today,
[06:10] or actually that was yesterday, but my Spotify Rats,
[06:14] that kind of stuff, like cool things, right?
[06:16] But anyways, if like a user is listening to a mix of jazz
[06:22] and blues, the system is going to identify songs
[06:26] with, you know, those similar instrument properties,
[06:30] acoustic properties, themes, even if the user hasn't actually
[06:34] searched for that type of song.
[06:35] So you'll get like your Spotify day lists
[06:39] or your Spotify recommended mixes, stuff like that.
[06:42] And that's based on what you're listening to.
[06:44] So fraud detection, for example, PayPal.
[06:49] PayPal's fraud prevention.
[06:54] They have their transactions, right?
[06:55] And those transactions are being stored as vectors,
[06:58] which contain details like how much the transaction was,
[07:01] the location, all the kind of stuff.
[07:03] And in this vector database, they can find patterns
[07:06] and they can find things that deviate
[07:07] from your normal user activity,
[07:10] which would flag your account for potential fraud
[07:13] or if you're probably like, if your card's gotten declined
[07:16] because you're in a different location than normal,
[07:19] it's because it's off of the pattern.
[07:23] Once again, we're going more with some more recommendations.
[07:25] So Amazon's product recommendations,
[07:27] at this point, you probably understand the theme.
[07:29] They use vector database as to analyze purchase history,
[07:33] browsing habits, product attributes, all that kind of stuff,
[07:38] especially when you're checking out with something in your cart
[07:41] and it will show like the things frequently bought together,
[07:44] that kind of stuff.
[07:46] Obviously with Google semantic search,
[07:49] Google is going to interpret your queries
[07:51] and if you're searching for something
[07:54] like tallest building in New York,
[07:57] you're going to see Empire State Building,
[07:58] you're going to see the One World Trade Center
[08:02] because it understands the query intent
[08:05] rather than explicitly only searching for tallest building
[08:07] in New York, it's understanding the meaning
[08:09] of what you're searching for.
[08:10] So geospatial data analysis with Uber,
[08:15] Uber uses the vector databases and geospatial data
[08:18] to, for your information like pick up and drop off coordinates,
[08:23] source as vectors so that it'll optimize the routes,
[08:26] it'll pop up for the drivers that are in the specific areas
[08:29] and just basically to improve their operational efficiency
[08:32] with an Uber.
[08:35] So then also we have our image and video recognition
[08:40] with Instagram.
[08:42] So Instagram probably uses these vector databases
[08:44] to represent images, stores them, embeds them,
[08:48] and then when you upload a photo,
[08:49] the system will automatically tag it
[08:51] based on visual similarities
[08:53] with other existing content that is similar,
[08:56] which is going to help Instagrams, what's it called?
[09:00] Algorithm, when it comes to searchability
[09:02] and like recommendations.
[09:03] So, and then talking about like natural language processing
[09:06] applications, companies will use vector databases
[09:09] obviously to store and retrieve word embeddings
[09:12] for chatbots to obviously respond,
[09:14] improve the quality of interactions
[09:17] or the rag that we have probably are most familiar with.
[09:21] Healthcare data management, using vector databases
[09:25] to analyze patient records, cybersecurity,
[09:28] threat detection kind of touched on that
[09:30] and scientific research data analysis,
[09:34] using vector databases for genomic research
[09:37] that represents DNA sequences as vectors,
[09:40] which according to my research,
[09:42] enable scientists to quickly identify patterns
[09:44] or similarities that would otherwise take a lot of resources,
[09:49] a lot of computational querying, stuff like that.
[09:53] So, yeah, it's okay if that really didn't make a ton of sense.
[09:58] The idea here was just to open your eyes on,
[10:02] you know, this isn't like a new concept.
[10:03] This sort of similarity search, semantics search,
[10:05] vector databases, embeddings, it's been around for a while
[10:08] and it's been utilized all over
[10:09] and you probably just don't realize it.
[10:10] So, that's gonna be it for this one.
[10:12] We will see in the next module.
