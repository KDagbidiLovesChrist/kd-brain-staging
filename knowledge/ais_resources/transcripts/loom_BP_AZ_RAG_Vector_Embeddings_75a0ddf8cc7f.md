# Loom Transcript · BP_AZ_RAG_Vector_Embeddings

**Source video ID:** 75a0ddf8cc7f4e8182c745b895b34f90
**Loom URL:** https://www.loom.com/share/75a0ddf8cc7f4e8182c745b895b34f90
**Detected language:** en (probability 1.00)
**Duration:** 427.4s

---

[00:00] Okay, so we just talked about vector databases and now when you want to get information you know data into a vector database
[00:07] It has to be embedded and also sort of has to be properly loaded and then embedded
[00:11] And so I would have talked about this a lot in my NIN and master class video or in the AI agent master class video
[00:17] specifically within NIN about AI nodes, but
[00:20] We'll talk more about embeddings and also before I get into this full transparency here
[00:25] I'm not an expert on these embeddings
[00:27] I understand them enough to get my agents to run and that's I think that's what's most important at this point
[00:33] but definitely a good thing to look into a little bit more, but
[00:36] for my use case I pretty much always do
[00:39] I always do text embedding three small and I set up my vector databases the same way and
[00:44] That's just sort of how I've been getting tons of text big walls of text for the AI to read and it's more confined
[00:52] But let's get into vector embedding so
[00:55] This is basically the way that the AI
[00:59] It's the way that we help the AI and computer understand the different types of data coming into the vector database
[01:05] So text images audio once again
[01:08] We'll break it down with a couple simple examples so that it's easier to understand why embeddings are
[01:14] essential so
[01:15] basically
[01:17] Imagine vector embeddings as these numbers that represent the complex data that we're putting into it
[01:23] These numbers capture the unique qualities of the item the characteristics so it helps the AI recognize that the the word cat is similar to the word kitten
[01:31] And it's more similar to the word kitten than it is to the word car even though car
[01:36] looks more similar to cat so
[01:39] That one image of a beach is more similar to a different image of
[01:43] You know a water compared to different image of a mountain so okay that was a bit of a tangent that was bad anyways types of vector embeddings
[01:52] So we have tons of different types and like I said, I mainly just have been doing text for my use cases with my product seven working onto my agents
[01:59] But text embeddings the purpose is to capture the meaning of sentences or you know documents or numbers
[02:04] There's different ways you can split up, you know character recursive splitter token splitter
[02:10] And that's just the different ways you want to
[02:13] Basically split up the text so that it can keep context or if you want to split based on punctuation that sort of stuff
[02:19] But the process uses different models to turn the text and the vectors with similar meetings in the vector space
[02:26] And so obviously one uses for chatbots search engines recommendation systems
[02:31] And then we have image embeddings of course which represent visual features of the images so
[02:36] Similar images have similar vectors like I just talked about with that horrible example where I said
[02:42] Comparing images of beaches and mountains and that sort of stuff
[02:44] But that would be like when you're searching on Google and you get all these related images
[02:49] In your search results. So
[02:51] That seems pretty straight forward. We've got audio embeddings
[02:55] Which is going to sort of encode and transcribe the sound like voices or music so that the AI can recognize patterns in this audio
[03:04] Some are way that it has like the the model that goes in there and turns the sounds into vectors based on the patterns and frequencies
[03:10] But you know, you don't want to use this for voice recognition
[03:14] Music recommendations audio classification stuff like that
[03:18] Video embeddings also of course, which will kind of do both
[03:22] Images and motion in the videos where it'll process these frames and add
[03:27] Temporal data to show changes over time and then compare like what's going on you would use this for
[03:33] Pretty similar to to image use case where you want to sort of identify some of the content
[03:38] We have multimodal embeddings which are going to combine different data types like text images, PDFs, binary data all into one vector
[03:47] So we have to sort of figure out how to link text images and integrate multiple data sources into one embedding and then put that in there
[03:54] So this is going to be more for like very complex searches complex use cases where we need to find maybe an image on a text description sort of thing
[04:02] So it's going to combine two elements and we've got graph embeddings
[04:07] This is going to represent entities and relationships and networks like social media or specific graphs or more numerical representations
[04:16] Visualizations of data
[04:18] Which would be good for like predicting
[04:21] You know different connections and social networks or I don't know
[04:25] I think that would be a good use of
[04:27] When you're being recommended
[04:29] Different people on social media or like maybe on YouTube being recommended different YouTube videos
[04:34] And I may be way off there
[04:35] But that's at least the way that sort of my brain first thought about that
[04:39] But anyways tabular
[04:42] Represent structure structure data so this is going to be more similar to the way that you have your relational schemas in a sequel warehouse or something where you've got data and tables
[04:51] And you've got different keys that align to each other and that's how you can see how stuff relates and you can see each row is one
[04:59] I guess family like each rows correlated and the next was correlated
[05:04] You could use that for predictive modeling and also once again recommendation systems and structure data a lot of these vector data
[05:10] bases are very good for recommendation type things because it's looking at relations obviously
[05:15] And then now going back to what I was saying about
[05:19] My specific use cases my experience with vector embeddings
[05:23] I've pretty much always set up my vector databases as text embedding three small and so this is like you know in open AI's case
[05:30] They have two different versions or actually no more than two
[05:32] But it's text embedding three small text embedding three large or the two that I look at and I basically
[05:37] Understand them enough to always use text embedding three small and it's been working well
[05:42] With my use cases so far
[05:43] But here's how they sort of differ the small one is going to be faster and using like fewer resources
[05:49] So lower-dimensional vectors good for you know general purpose quick lookups
[05:56] Most of the time like it's still a massive amount of data going in a massive amount of text and it doesn't check
[06:01] But then you know obviously for the for the large model
[06:05] We want to use that for more detailed
[06:08] With higher-dimensional vectors capturing you know
[06:11] All the little information subtle information perfect for you know very complex in-depth searches of
[06:18] You know very specific data I would say so if you need basic matching the small model works well for applications
[06:24] That you need really deep meeting really deep types I would probably recommend using the large model
[06:28] But you can also play around and see the type of answers you're getting back
[06:32] But yeah, that's basically it hopefully um that at least makes a little more sense
[06:36] I really think that's something like vectors and maybe all these token splitters are good to understand a basic grasp on
[06:42] But I don't think you need to be an expert in order to get your agents to run the way you want them to
[06:46] Because you know pretty much in summary. It's just turning different data types
[06:50] Into these you know magic vector numbers that put them into the vector database
[06:55] Just embedding them so that they're the AI is able to find relations and
[06:59] Grab exactly what it needs. So that is embeddings. Thanks guys
