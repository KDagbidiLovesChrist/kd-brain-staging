# Loom Transcript · BP_AZ_RAG_Tokenization_Text_Processing

**Source video ID:** 7d952a50a8ab41429e605465e3704e1b
**Loom URL:** https://www.loom.com/share/7d952a50a8ab41429e605465e3704e1b
**Detected language:** en (probability 1.00)
**Duration:** 737.8s

---

[00:01] Okay, so this one's going to be about tokenization and text processing.
[00:06] This one, hopefully should be quick, it's, you know, it's definitely something important
[00:10] to understand and obviously we want it to be as simplified as possible.
[00:16] So we talked a little bit about NLP, natural language processing and within natural language
[00:21] processing we have tokenization, which is just basically the process of breaking down text
[00:27] into smaller units, these units are called.
[00:29] This is obviously like when we're in NADN and we're, you know, loading information through
[00:34] the default data loader and then we're splitting it up, we've got like a token splitter.
[00:38] So that's what it is.
[00:40] So tokens can be, you know, words, they can be sub words, they can be characters, they
[00:45] can be punctuation and these are just the foundational elements.
[00:49] Obviously that AI agents will look at, they'll analyze it, they'll understand it in order
[00:52] to sort of generate us back a human response.
[00:55] So anyways, it's really important to have effective tokenization.
[00:59] Especially when we're talking with AI agents for accuracy and efficiency.
[01:04] So yeah, quick introduction there, let's move into different techniques for tokenization.
[01:10] So we've got five main techniques, we've got word, sub word, character, byte pair and
[01:16] then sentence.
[01:17] So word tokenization, splitting text and then into individual words, which is obviously
[01:22] good for languages like English, where we've got clear boundaries.
[01:26] So the sentence AI is transforming industries, becomes AI, becomes AI is transforming industries.
[01:35] Then we got sub word, so dividing words into smaller units, like prefixes, suffixes, syllables.
[01:40] This is going to be good for handling out of vocabulary words and sort of morphological
[01:47] variations.
[01:48] So the word unhappiness could be tokenized into unhappiness.
[01:54] And we've got character tokenization, so this is breaking text into individual characters.
[01:58] This is going to be useful for languages without clear word boundaries, like we talked about
[02:01] with the sort of word tokenization, when we really need to get into detailed text analysis.
[02:07] So AI, which I guess really isn't a word, more of an acronym, but AI becomes AI.
[02:14] And then byte pair encoding, also you may see this just be called BPE, which is an algorithm
[02:19] basically iteratively merges the most frequent pairs of bytes to form your sub unit or sub word
[02:27] units.
[02:28] So the application here would be that it balances vocabulary size and representation efficiency,
[02:36] which is commonly used in something that could be called as like a transformer based model.
[02:42] So the word lower could be split into lower.
[02:47] And then finally, we've got sentence tokenization, a definition of this would be basically segmenting
[02:54] text into individual sentences.
[02:56] So you want to sort of save essential context, I guess.
[03:03] This would be good for like machine translation and summarization.
[03:07] So the example here is the paragraph, AI is evolving, I don't know, paragraph, sorry.
[03:13] The phrase, the sentence is AI is evolving.
[03:15] It impacts many sectors, becomes AI is evolving.
[03:19] It impacts many sectors.
[03:21] OK, so quick example that I wanted to run through here would be sorry, I wanted this to be on its
[03:28] own page.
[03:29] OK, and that might have messed up the rest.
[03:31] OK, anyways, we've got the example of NAN is such a powerful tool with two exclamation
[03:38] marks.
[03:39] So how would this get split up in different ways?
[03:42] We're just looking at word, sub word character, and then sort of how it works with open AI.
[03:48] So in word tokenization, obviously this would get split into NAN is such a powerful tool.
[03:55] And it would also probably keep those punctuation there at the end, which is, I mean, I don't
[04:03] know if it's ideal or not, but in this way, it's usually going to have a punctuation attached
[04:08] to that last word.
[04:10] And then if we went to sub word, which also could be sort of bite pair, but it would split
[04:17] it into NAN because NAN is not a word.
[04:21] Then we have is such a powerful tool.
[04:25] And then we've got that punctuation also split by itself.
[04:29] Character tokenization would be each character is done token.
[04:32] So this is even going to account for spaces and the punctuation.
[04:35] So as you can see here, we've got NAN space, IS space, that's how that one's going to work.
[04:43] And then the way that tokenization is used by AI models like GPT models, it kind of uses
[04:49] like sub word based tokenizer.
[04:52] So this one would be NAN is such a powerful tool.
[04:56] So NAN is treated as a single token if it exists in the vocabulary.
[05:02] So NAN, chat GPT is like aware of what NAN is, so it keeps it as a token, but otherwise
[05:08] it would have been split further.
[05:10] OK, so in fact on embeddings, tokenization directly influences how text is going to be converted
[05:18] into its numerical vectors, which obviously we talked about this earlier is known as embedding.
[05:24] So we have granularity, so word level, sub word level, and character level.
[05:30] These are obviously just different ways that you're going to capture the meaning of the words,
[05:34] the way that you can handle sort of rare and compound words, and then just sort of more
[05:39] detailed representations of words and languages and their meaning.
[05:44] We've got vocabulary size, so large vocabulary is going to require more memory, and therefore
[05:50] more computational resources, but also obviously can represent a wider array of words directly,
[05:57] or a small vocabulary will be more efficient, but may need to represent words as combinations
[06:04] of sub word units, which could infect your infect, which could affect your embedding quality.
[06:10] So I set it a tundering a previous video, but like balance is key, and it's all about finding
[06:16] that balance, and you do this by iterating and refining.
[06:19] So handling out of vocabulary words, sub word and character tokenization basically helps
[06:26] the model to construct these embeddings for unseen words.
[06:31] Like we just talked about with OpenAI, it knows what n8n is, but if it didn't, it would
[06:34] have to split it up further, but anyways, this just enhances the model's ability to sort
[06:38] of generalize things.
[06:41] And then finally, we have sequence length, which has an impact on processing.
[06:46] So finer grain tokenization, I'm trying to think of an example, but this finer grain tokenization
[06:54] is going to result in longer sentences, which can obviously increase the computational load.
[06:59] It can increase the, or not increase, it can infect the model performance, and just obviously
[07:06] stuff like that.
[07:07] So now for pre-processing strategies, basically just preparing your data for vectorization,
[07:14] it's important because you want your data to be clean, you want it to be appropriate, you
[07:17] want it to be optimized for tokenization and inevitably being embedded.
[07:24] So we've got, where did that picture go, okay, sorry, you want this picture up there,
[07:33] okay, there we go, now we're going to go.
[07:35] So we've got text normalization, which is lower casing, converting all text to lower
[07:40] case for consistency, removing punctuation, eliminating punctuation marks.
[07:45] Unless obviously it's, those punctuation carry significant meaning that would affect
[07:49] the way that the agents bring it back, the information.
[07:51] And then expanding contractions, so converting words like, don't into, do not, that's
[08:00] what it's stuff.
[08:03] Because otherwise things could be split, and you could have like, do, okay, in the case
[08:06] of don't, you could have dawn, and then you could have a different token that's like a
[08:11] apostrophe T. So yeah, that's kind of what the idea was there.
[08:16] We've also got stopword removal, which is the picture we're looking at right here.
[08:19] Those are just basically these common words that don't really add significant meaning
[08:23] to the text.
[08:24] Obviously, in some applications, this is essential, so you probably shouldn't remove it,
[08:28] but sometimes you want to get rid of those to make that more efficient.
[08:33] We've got stemming and limitization, so stemming is truncating words to their root form.
[08:39] So running becomes run, and blanking becomes blank, and you know, the root words.
[08:46] And then limitization is reducing words to their base or their dictionary form, obviously
[08:52] considering the context.
[08:53] So, okay, so two more here.
[08:57] We have handling special tokens, we can use padding, which basically just adds special tokens
[09:03] to ensure the uniform sequence length across all your inputs, and then start an end tokens
[09:09] which basically add tokens to signify the beginning and the end of sentences or sequences,
[09:15] which basically aids in stuff like translation.
[09:17] So last one here is dealing with noise, pretty self-explanatory, removing irrelevant information.
[09:29] Like I said here, URLs or HTML tags mark down other non-informative elements, and then correcting
[09:35] spelling errors, obviously standardizing your text, reduces your variability, and improves
[09:40] your accuracy the way that the agent can interpret what's going on.
[09:44] So, and then one of the things that's most important is obviously about the pricing.
[09:49] So these models obviously, we're using APIs, for the most part I've been using like open
[09:56] AIs services, obviously, and when you're doing this, it's important to understand how tokenization
[10:00] affects cost.
[10:01] So I'm in the AI agent prompting masterclass, I showed this thing about tokenization, and
[10:11] I will have this as a section within this sort of course so we can you can look at it,
[10:16] but there's this cool way that you can look at how open AI interprets tokens, and like
[10:22] if you were the example of the video I talked about was prompting.
[10:26] So putting in your prompts and then putting them into this tokenize, you can see how many
[10:30] tokens they are, how much it's going to cost you based on the model, all that kind of stuff.
[10:34] So I'll share that link within this course, but anyways, you have to understand the tokens,
[10:40] so tokens are chunk of text, obviously, and for English, sorry, excuse me, in English a
[10:48] thousand tokens are roughly 750 words, and yeah, so right here we have six tokens, and
[10:58] as you can see like chat GPT is great, it broke down GPT, and then how that relates to
[11:05] pricing structure is a part token billing, so APIs will usually charge based on the number
[11:10] of input and output tokens that you process, and obviously we have the stuff with like the
[11:18] different models, so like I said, for all many is a lot cheaper than for all, I'm not sure
[11:23] how much the other models are, some of the turbo ones are more expensive, I don't know exactly
[11:28] with Claude either, but take a look at the way that your different models are processing
[11:32] this kind of stuff, and you don't want to accidentally run an agent a few times and realize
[11:37] that you were doing, you know, a dollar per call rather than you could have been doing
[11:41] here with many .015 per a thousand input tokens, so yeah, that's going to be it for this one.
[11:51] Like I said, I will make a short video about that tokenizer because I think that's a really
[11:55] cool tool, and also if you are interested in, I found another cool tool that was comparing
[12:03] different models and they're sort of what they are good at, what the pricing looks like,
[12:09] so I'll also do something like that in there, somewhere in this community too, but yeah,
[12:14] that's going to be it for this one, so thanks guys.
