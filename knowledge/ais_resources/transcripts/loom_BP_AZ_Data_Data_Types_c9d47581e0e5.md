# Loom Transcript · BP_AZ_Data_Data_Types

**Source video ID:** c9d47581e0e54c72afe45103fb967666
**Loom URL:** https://www.loom.com/share/c9d47581e0e54c72afe45103fb967666
**Detected language:** en (probability 1.00)
**Duration:** 685.7s

---

[00:00] types within NADN or just in general data types.
[00:04] So it's an important thing to understand up front
[00:07] because there are some complications
[00:08] that could arise in your workflows
[00:09] if you're getting certain errors
[00:11] or if things aren't moving through correctly.
[00:14] So just wanted to sort of set up the foundations here
[00:16] with data types in case it's sort of a new concept to you.
[00:19] So in NADN data flows through workflows
[00:22] in a structured format and often these
[00:24] are represented as JSON objects.
[00:26] So a whole other section will be kind of about JSON
[00:30] and how to understand the key value pairs.
[00:32] It's really not too difficult once you look at it.
[00:33] And after watching this video,
[00:35] it'll probably make more sense as well.
[00:37] But the core data types that you're gonna be encountering
[00:40] are strings, most of all, which are just text.
[00:44] Strings are words, phrases, paragraphs,
[00:46] but this is just basically the different distinctions
[00:49] of how the computer understands what type of data
[00:52] is flowing through.
[00:53] So if it's a string, it's going to be text.
[00:56] Then we have numbers, pretty self explanatory.
[00:59] Numbers are, there's a lot of ways
[01:02] that they can be sort of distinguished,
[01:03] but the main two you're gonna see are integers and floats
[01:06] within NADN, you'll really just see it as a number.
[01:08] But an integer is gonna be a whole number
[01:10] and then a float is a decimal.
[01:12] It stands for like floating point number
[01:14] or floating point decimal or something.
[01:16] But a float's a decimal and integers a whole number.
[01:19] Then we've got Boolean variables.
[01:21] So this is when a key could be set to either true or false.
[01:25] Or like yes or no, basically there's only one
[01:28] or the other answer.
[01:29] So it's pretty black and white, Boolean is true or false.
[01:33] And we've got arrays which are lists of information.
[01:37] It could be, you know, we have an array of products.
[01:39] It would be product one is this, product two is this,
[01:41] product three, but that's an array.
[01:44] And sometimes those can be kind of confused with objects
[01:46] because objects are also sort of like a,
[01:50] almost like a list of things,
[01:51] but rather than just being product product,
[01:55] something product, something product, something product,
[01:56] something, an object is like a container
[01:59] of different key value pairs.
[02:01] So I'll show an example down below
[02:03] or we'll look at what it actually looks like in N&N,
[02:05] in JSON, in the schema format, whatever it is.
[02:08] But sometimes a risk, a risk.
[02:10] Sometimes arrays and objects can be a little confused.
[02:13] So we'll break that down.
[02:15] And then finally we have Noles,
[02:16] which also can be confused with,
[02:20] I probably shouldn't have wrote empty values here.
[02:23] Let's change this to values that don't exist.
[02:29] So there's a difference between something that's null
[02:32] and something that's like an empty string.
[02:34] So we'll look at that as well,
[02:35] but just some important things to keep in mind.
[02:37] So we're just gonna break down each of these data types
[02:41] to find them real quick, show an example,
[02:43] and then we're gonna look at N&N
[02:46] when you're looking at inputs and outputs.
[02:48] So you've got your node in the middle,
[02:49] on the left you've got your input, on the right,
[02:51] you've got your output.
[02:52] You can select different ways to view this data.
[02:55] So you've got your table view,
[02:57] which will be like, I don't know why I didn't include
[03:00] a picture of it.
[03:01] But anyways, your table view will kind of just be like a table.
[03:03] It'll look like Google Sheets with your headers up top
[03:06] and then your values and your rows and all that kind of stuff.
[03:09] Then we've got what I have down here,
[03:13] this first one right here, this is JSON,
[03:15] and then this one is the schema view.
[03:17] I like to stick in schema view typically
[03:19] because it makes the drag and drop really nice and easy.
[03:22] It's easy to have arrows for collapsible items
[03:26] so you can collapse things and get around
[03:28] what to where you need to be.
[03:29] So I like schema, but sometimes you want to flip
[03:31] into JSON or table depending on the use case.
[03:33] Anyways, here we have two strings, right?
[03:36] We have the key here is a name,
[03:40] and then the actual value of the name is a string
[03:42] called John Doe, and then the email,
[03:44] which is johnandexample.com.
[03:46] Here's what it comes through as JSON.
[03:48] So as you can see, I talked about key value pairs,
[03:51] where the key is sort of like,
[03:53] if you were thinking about an Excel spreadsheet,
[03:55] you've got your columns, you have your fields.
[03:58] So the fields are those headers basically,
[04:01] and then your actual values are all the cells
[04:03] that are within that column that have meaning.
[04:06] So the key is name, the values John Doe,
[04:09] and as you can see, it's in quotation marks,
[04:12] it's in quotations, it's purple, so we know it's a string,
[04:15] and then similarly on the right side,
[04:16] we know it's a string because the schema
[04:18] shows that there's an A next to the field called name.
[04:22] So the A is a letter, so that just means
[04:24] that this data type is a string.
[04:27] Okay, so now we have a number.
[04:28] A number is obviously numeric values, integers, floats.
[04:31] Here we have age equals 30, and then in the JSON
[04:34] that we get this pulled into when we're using numbers in NADN,
[04:38] there's not gonna be quotes around it.
[04:39] So as you can see, age is just 30,
[04:41] the key is age, the value's 30, it's green, no quotes,
[04:45] and then on the right side with the schema view,
[04:46] we would have a pound sign, which kind of represents numbers.
[04:51] Okay, so then from there, we have Boolean.
[04:53] So I was just in a set node, and I was setting these different things.
[04:56] So up here I set name to John Doe,
[04:58] and I pushed it through the string, here I put,
[05:00] I set age to 30, pushed it through as a number,
[05:03] and now I'm setting the field is active to true.
[05:06] And so when I set the type of data,
[05:08] I want this to come through as, and I choose Boolean.
[05:10] As you can see, we have a drop down menu
[05:12] of only two options, true or false, we couldn't enter anything in.
[05:15] So we couldn't type in true, we couldn't type in false,
[05:18] we have to actually select these two checkbox items.
[05:22] And we can see in the schema view,
[05:23] that this is going to be a check mark, a checkbox,
[05:26] rather than like a letter for a string,
[05:28] even though true, looks like it could be a string,
[05:30] as you can see on the left hand side, and the JSON,
[05:32] there's no quotes around it.
[05:33] So that's how we can see that this is a Boolean variable.
[05:36] And a lot of times it'll just make sense,
[05:38] like is active, has subscription, you know,
[05:44] is it an adult, or is it a child, true or false?
[05:48] That kind of thing.
[05:50] So now arrays, arrays are lists of values,
[05:53] like I talked about earlier with the products,
[05:54] and here's a list of products.
[05:56] In this case, we have tags.
[05:58] So lists can be any data type.
[06:01] So as you can see here, we have tags,
[06:03] which are, we put through as AI, automation, and NADN.
[06:09] And those will be shown within square brackets.
[06:13] So when I'm setting this in that set field,
[06:16] or the set node, I set the value, the key to tags,
[06:19] and then in the value section, I had to put two square brackets,
[06:23] and then I had to put commas in between each of the list items.
[06:27] And then it output this as AI, automation, and NADN.
[06:31] And it's important to notice here in the schema,
[06:33] we've got a list, and you can see this is where I talked about
[06:35] the collapsible, you could bring these all up
[06:37] if you didn't want to see them all.
[06:38] But you can see it's coming through as one item,
[06:40] even though it may seem like we have three items,
[06:42] because there's three tags coming through.
[06:44] It's just one item, because the item is the array.
[06:46] Within the array, we have tags 0, as AI, tag 1, as automation,
[06:50] and tag 2 is NADN.
[06:53] And then moving on to objects.
[06:54] So like I said, can be confusing, because they look similar,
[06:58] because it's basically like one item,
[07:02] where you can collapse it up or down,
[07:04] and then there's going to be more items underneath.
[07:06] But the difference here is that we have key value pairs
[07:08] rather than just tags.
[07:10] So within the object called user,
[07:14] we have an ID, which is 101, a name, which is Sarah,
[07:18] and an email, which is Sarah at example.com.
[07:21] So here we have our number variable, or data type,
[07:25] and then two string data types, same thing over here,
[07:30] a number, two strings, all within that user object.
[07:34] And once again, it's one item, because the item we're counting
[07:36] here is the object.
[07:38] And yeah, I hope that you can understand this difference.
[07:41] These are all tags, and they count up,
[07:43] and these are key value pairs, so each one's kind of different.
[07:46] So that's objects versus arrays.
[07:49] Then moving into null values.
[07:52] So null means that it's like, I'm not going to get a rid of empty.
[07:56] So null is missing data.
[07:58] So in this case, we were looking for someone's phone number.
[08:01] It wasn't provided, so it literally comes through in the JSON
[08:04] as null and red.
[08:06] Not a string, null, no quotes.
[08:09] Same thing in the scheme of view, it comes through as null
[08:14] with the two square brackets around it.
[08:15] But if you push it through and you just set something to nothing,
[08:20] like in this case, I set the key phone as a string,
[08:23] and I just didn't fill in value, and I pushed it through.
[08:26] What we get here is an empty string.
[08:27] So this is, as you can see, two quotation marks around nothing,
[08:31] which means it's just an empty value.
[08:32] And then in the scheme of view, we're not getting the word null back.
[08:36] We're not up here when this is actually a null value.
[08:38] We're not getting that down here in schema,
[08:40] because it's just an empty string.
[08:42] So hopefully you don't have to deal with that issue too much.
[08:45] But when it comes down to setting routes
[08:49] based on does this field exist?
[08:52] In this case, yes, phone does exist.
[08:54] And so it would get pushed through.
[08:56] And because if you wanted to filter out responses
[09:00] where there was no phone number provided,
[09:01] this would get filtered out if you set phone equals not
[09:05] exist route them off this way.
[09:07] But technically here, the key phone and the value
[09:12] does exist because it's an empty string.
[09:14] So just got to watch out for that.
[09:17] So as far as how data types impact workflow logic,
[09:21] not diving too deep into here, just
[09:22] wanted to give a good understanding of what
[09:24] they are, the differences between them.
[09:27] Boolean values can be really useful for if nodes
[09:29] when you're checking conditional logic.
[09:31] Arrays will help with looping through things.
[09:33] So if you've got a list of 17 different topics
[09:36] you wanted to research on, you could sort of loop through each item
[09:39] in that list individually.
[09:40] Numbers are useful for calculations, of course.
[09:42] And then objects are good for structured data storage.
[09:46] So user details is a great example.
[09:48] If you had a web hook of form responses coming through,
[09:50] and you had different objects for each response,
[09:53] and it would have in this response, we've got name, this,
[09:56] email, this, phone number, this, form submission, this,
[10:00] and then you have that's object one.
[10:02] And then object two is a whole different person
[10:03] with all those different key value pairs.
[10:06] So final thoughts is always inspect your data
[10:08] in the output panel when it's coming through.
[10:11] You may run into times where you're
[10:12] trying to send data between different workflows,
[10:13] and you might get an error like expected object,
[10:16] but got a string, and that kind of stuff.
[10:17] So that's why you want to be aware of data types
[10:19] and how they're coming through.
[10:21] Use the right operators and your if nodes,
[10:23] convert types where necessary to avoid unexpected behavior,
[10:26] sort of like the error I just mentioned.
[10:27] You can use these different nodes to sort of clean and form
[10:32] out your data, and obviously the function
[10:34] is the legacy name.
[10:35] So basically set in code nodes to clean and form out
[10:38] your data and your data types, and then test
[10:41] with different inputs, empty null members
[10:44] text to ensure robustness.
[10:47] And then one more final thought to, of course,
[10:49] is just be aware of null slash actually just an empty string
[10:55] or an empty value.
[10:56] So like zero.
[10:58] If it's a number form, if it's a number data type,
[11:01] and something's coming through to zero,
[11:03] so like let's say how many sales that we have today,
[11:05] zero or null, like that's going to make a difference,
[11:08] even though they both technically represent nothing,
[11:12] it's a big difference in the actual world of data,
[11:15] zero versus null.
[11:16] So just keep that in mind, hope this helped.
[11:19] And if you want to look at this PDF,
[11:22] it'll be attached into this post as well.
[11:23] So thanks guys.
