# Loom Transcript · BP_AZ_RAG_Vector_Dimensions

**Source video ID:** 64da827dfcdd4c85ba198aebd196ea6f
**Loom URL:** https://www.loom.com/share/64da827dfcdd4c85ba198aebd196ea6f
**Detected language:** en (probability 1.00)
**Duration:** 764.6s

---

[00:00] Okay, so dimensions within vectors.
[00:05] Obviously, we're going to talk about, you know, we're going to dive into this.
[00:10] But before we start talking about any of this, I just want you to have the sort of pre-conception
[00:16] of what they are.
[00:18] And so essentially, just think about it as simple as this.
[00:21] Every vector has dimensions.
[00:25] And these dimensions are just a list of numbers.
[00:28] And each number is some sort of attribute.
[00:31] So dimensions give meaning to the vector.
[00:34] They give contextual meaning to a vector.
[00:37] Okay, so just wanted to preface that, but now let's get into it.
[00:40] So quick and true.
[00:42] Agents and Raga agents, they need to understand the vector dimensionality,
[00:47] which is very essential for designing these systems because when you're building out these systems,
[00:52] you need to make sure that they're optimized, which will do three things.
[00:56] Probably more than three things, but three things.
[00:58] It's going to process it, process your data more efficiently, store your data more efficiently,
[01:03] and retrieve your data more efficiently.
[01:05] And I thought of a fourth one, which is probably more cost-effectively too.
[01:09] So whether an AI agent is, you know, being used for recommendations, for Raga,
[01:14] other sorts of, you know, semantic search,
[01:17] the vector representations directly impact speed, accuracy, overall performance.
[01:24] So for example, let's say we have an AI agent that's retrieving similar customer queries
[01:30] to provide accurate responses in the right context.
[01:34] It's relying on these vector dimensions because these dimensions have meaning,
[01:38] and they give each point in this three-dimensional space meaning,
[01:43] so that the agent's able to go find similar things and find information that makes sense,
[01:48] and overall, overall, and ultimately return the correct information.
[01:53] So what are dimensions and vectors, like I said, it's just a numerical representation of data.
[01:59] It's kind of a list of numbers.
[02:01] You can think of this as maybe just a row of numbers, where each number represents a specific feature of the data.
[02:06] So for example, a person's profile might be represented in a vector as,
[02:12] in this case, this is a three-dimensional vector because there's three attributes.
[02:16] We've got their age, their height, their income, and then numerically that could be represented as 25.9.
[02:22] I don't know, 5.9 inches or whatever that is, but then 45,000.
[02:28] So each number corresponds to a specific dimension of the vector,
[02:32] which is a specific feature attribute detail.
[02:36] So what does dimensionality mean?
[02:38] It's just the number of features. That's its dimensionality.
[02:41] So in this case, we said this one was three-dimensional. It has three attributes.
[02:46] And then obviously, as you get more complex data, it could be obviously text, images, audio, whatever it is,
[02:51] as it gets more complex, you need to add more details.
[02:54] You're going to increase the dimensionality, which obviously you can get up to thousands and thousands of dimensions.
[02:59] So not that this image is super relevant, but it's just a cool visualization of something sort of like a three-dimensional space.
[03:11] Obviously, with vectors, it's more of like a scatter plot with points everywhere.
[03:15] But anyways, visualizing dimensions.
[03:18] So low-dimensional space is 1D. It's just one number. Picture a point, just somewhere on a line.
[03:27] And then a plane is two-dimensional. So two points in that vector, a point on a flat surface.
[03:33] And then 3D, three attributes, three points, a point in a multi-dimensional space.
[03:41] And then in your high dimensions, it gets harder to visualize once you get past like 40, but the concept's the same.
[03:47] So each time you add a dimension, it's going to add a new, basically like, direction or plane within this sort of abstract space.
[03:56] So in example, for example, in a 5D space, you're getting five numbers, 2, 4, 6, 8, 10, which represents a point, which is defined by five different coordinates, five different attributes.
[04:07] So why does, why do dimensions matter?
[04:12] The first thing that we're going to talk about is capturing characteristics, obviously.
[04:17] So dimensions represent features or attributes in the data. So an example would be an AI agent is analyzing customer behavior.
[04:24] And it might look at something within a profile of a customer, like their age, their spending, their habits, their region, and obviously you could add on more information.
[04:33] But each dimension there captures some piece of that customer profile.
[04:37] And likely, you know, as you add more dimensions, you're not going to get two identical factors.
[04:43] So complex data also requires higher dimensions. So in these sort of systems, modern AI systems, data like text, images, user behavior, all that kind of stuff can get up to hundreds or even thousands of dimensions.
[04:59] So an embedding for a single word in a language model can have 768 or more dimensions. It can have 1,536 dimensions. It can go more and more.
[05:09] But all of these attributes, as you start to add on more stuff, is going to capture different nuances, like sentiment, topic, and context.
[05:17] And then the third, we have balances key. So think about it like you're writing an email.
[05:24] You need to include all the relevant information, but you want to make it concise enough that the person actually reads through and is able to pick out the action items that you're asking from them.
[05:33] So two few dimensions, you might miss your critical information, critical information.
[05:37] Too many, you could overwhelm the system leading to inefficiencies and harder to analyze data.
[05:44] And then we've got two simple analogies real quick. So hopefully this isn't oversimplifying, but imagine a grocery list. You've got apples, oranges, and milk. Each item represents a dimension.
[05:54] The numbers could tell you either how much of the item you need or each number represents a different item. And the more you have on your grocery list, the more things you need to get.
[06:04] And then describing a friend.
[06:08] So if you were describing a friend, you could describe attributes about them like their height, their age, their hair color, their favorite hobbies. And in this case, that would be six feet, 25, 25 years old, brown, soccer.
[06:21] That's not describing me, by the way, just random person. And each trade obviously adds a dimension to your description, which makes it more specific and more accurate.
[06:29] Although obviously, we know with vectors that this dimension is going to be numerical representation. So it wouldn't say brown or soccer.
[06:36] Okay. And then the importance of dimensionality, I guess, similar to what we just talked about up here with our wider dimensions matter. But for importance, let's just touch on capturing complex patterns within these AI systems. So agents rely on embeddings within their high dimensional vectors, they rely on embeddings.
[06:57] So these embeddings help them sort of encode their complex patterns and their relationships and data. So for example, with a chatbot agent, it could figure out the sentences in the vectors to understand the intent behind the user query.
[07:12] And then from there, it's able to understand the relationship between the different words, subtle differences between sentiments like thrilled or pleased.
[07:22] And then for balancing model performance and efficiency, an agent must balance the need for detail with computational constraints. So we talked about balances key earlier. But obviously more dimensions, richer representation of data, but likely slower processing. And then on the opposite side of the spectrum, fewer dimensions, likely faster processing, but potentially less accurate data.
[07:47] So for example, with like a semantic search agent, it might struggle to retrieve relevant documents, if the embeddings fail to capture enough of the semantic nuances, if the dimensions are too low.
[08:00] And then finally, of the curse of dimensionality, as your dimensions increase, this kind of relates back to balances key. But as dimensions increase, data points become more sparse.
[08:11] Similar points can be harder to distinguish, which can impact AI agent accuracy. So with like a fraud detection agent, might flag a relevant information as fraudulent, which is not what we want. Obviously, we want accurate results. But this could be because there's too much noise going on.
[08:28] So managing dimensionality, you've got feature selection and feature extraction. So feature selection is obviously just retaining the only retaining the most accurate. Sorry, let's start again.
[08:40] Feature selection is retaining only the most relevant features and getting rid of the redundant ones. So being concise, being detailed. A knowledge based AI agent that handles FAQs, its retrieval might reduce the input dimensions by focusing on only the essential keywords, whether that's something specific topic or specific documents.
[09:05] And this won't share faster results without losing the context. So if we, if you guys have watched that AI agent, AI agent prompting masterclass that I did, one of the things I talked about was like the tokenization and I showed that sort of open AI tokenizer where you could basically cut down the amount of tokens, but the context was all kept as far as the AI agent was concerned.
[09:30] So sort of the concept of doing that there, getting rid of certain words certain attributes that don't matter as much. And then feature extraction, which is defined as basically just transforming your original data into a new set of features that summarizes it.
[09:44] So a customer service agent, for example, could use embeddings to reduce text features into more meaningful summaries, which would give us more accurate results and probably quicker results.
[09:56] So converting, like, if you were to convert long documents into short documents, obviously your vectors are getting more dense and they're still keeping the key themes of what's going on.
[10:08] Okay, so to wrap up here, just a few considerations. So first one is about optimizing the agent's efficiency.
[10:19] So you want to use dimensionality to dimensionality reduction, sorry, to enable the actual benefit of what's going on here, which is real time inference. So reducing embeddings, faster response without sacrificing comprehensive comprehension.
[10:35] I feel like a broken record here, but just want to that's like the most important aspect, obviously.
[10:39] You want to avoid overfitting. So get rid of unnecessary dimensions unless get rid of the unnecessary dimensions to ensure that the agent doesn't overfit and there's not too much noise and then it's not going to be inaccurate.
[10:54] And then finally, interpretability. So lower dimensional embeddings are easier to interpret, more concise. It's easier to quickly scan, look at what you need, grab it out and yeah, like a compliance monitoring agent here is the example I wrote.
[11:08] Could benefit from these shorter explainable embeddings that are going to align closer with the sort of regulations that this compliance monitoring agent would be looking at. So yeah, that's that's going to be it for this one I hope that that made sense.
[11:27] It's really like one of those things where the concept is not too difficult, right, but if you really want to get in there and understand what's going on, there are some complexities.
[11:37] But being able to understand what I just talked about in this document here will give you enough to be able to set up your your knowledge base and understand how to get make sure that your agents are getting information back.
[11:51] It's just basically a fundamental concept in vector representations. And I tried to tailor this document towards kind of like AI agents rather than just talking about dimensions with investors in general because when you really want to get into dimensions, there's a lot of like there's a lot of math going on behind the scenes.
[12:06] And I am not smart enough to understand that or to explain that and we also don't need to explain that we don't need to understand that we need to understand dimensions enough to get your stuff to work, which is probably 70 to 80%.
[12:20] Anyways, that's sort of the mindset that I take when some of this stuff gets really complex, you don't have to be an expert in all of it, but if you can make your stuff work, you can understand what works, what doesn't, and how to optimize it, then you've got it down.
[12:34] It's an essential skill for anyone building AI systems, but it's not an essential thing to completely master. So that's it for this one. Thanks guys.
