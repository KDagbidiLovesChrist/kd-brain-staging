# Loom Transcript · CC_P3_1.6_Masterclass_Scheduled_Research_Agent

**Source video ID:** 62ee531babec42439011b0008aefccc3
**Loom URL:** https://www.loom.com/share/62ee531babec42439011b0008aefccc3
**Detected language:** en (probability 1.00)
**Duration:** 1125.9s

---

[00:00] All right, let's get into the masterclass portion of the training always the really fun stuff
[00:05] But we're going to start with our scheduled research agent. That's what we'll be building right now
[00:11] We're going to get sugar.dev as a task that runs every morning on a cron schedule
[00:16] It's going to research a fixed topic using fire crawl and it's going to write a structured summary row into our Google sheets
[00:24] And it's going to run without us every day on the schedule
[00:28] So let's double check before we start. We have our GitHub repository connected
[00:34] Our trigger dev account is connected the mcp server is installed into cloud code
[00:40] And we've initialized the project if you've been following along
[00:43] You should have all these things done
[00:46] We set up our environmental variables on the trigger dev dashboard and then we have the fire crawl mcp server installed and
[00:53] the API key ready. Okay, so from that last slide, and I was reading those thinking of myself
[00:58] You know what we need to double check that we have the fire crawl mcp setup and cloud code
[01:04] You may have that from phase two or not. I don't in this case
[01:07] So I just ask cloud just to be sure. Hey, do you have access to the fire crawl mcp server says no
[01:13] It's not configured here is what I do have so I said please set it up
[01:18] The API key look at asking for me API. I don't tell it. It's like hey, it's in the EMV file
[01:23] It went through okay fire crawl mcp is installed and connected so we're ready to proceed
[01:29] Further now. Okay, so back into our step. So step one we need to plan in plan mode
[01:35] We're going to give it this prompt. I want to build a trigger dev schedule task to run completely unattended every morning
[01:42] It takes a fixed topic searches with fire crawl synthesize this findings and writes a row to Google sheets
[01:49] No care no clarifying questions handle errors without crashing log every step help me plan this so
[01:55] Cloud might ask us some things it might ask me different things that it doesn't ask you, right?
[02:01] So remember just read follow the instructions
[02:04] It's going to probably ask us what's the topic about how many sources do I mean to look up
[02:10] What information do me to put in the columns of that row and then what do I do if no results found?
[02:16] Those are all logical choices that cloud can make so let's go pace this into cloud code and get it going all right
[02:23] So I paste that in we're going to remember to go to plan mode and
[02:27] Enter and as always as cloud that has things pop up and has meaningful things for me to show you I will come back and show you at that time
[02:38] Okay, so cloud has come up with plan. I need to move over here. I think all right
[02:43] So let's review a really fast plan morning research schedule task
[02:48] Build an on it's in the daily trigger
[02:51] schedule text that searches hard code a topic via fire crawl synthesize its findings with cloud and writes a row and Google sheets
[02:58] All right
[03:01] It created a new file which is morning dash research
[03:05] Yes, that's the entire implementation in one file
[03:10] No changes to the existing files
[03:13] Step one would be to install packages
[03:16] It looks like fire crawl and topic in Google
[03:24] Environmental variables
[03:27] They're already in the trigger dev dashboard. So it's going to pull those from there
[03:32] Google sheets prerequisites manual one time right we did already set this up
[03:39] Create a sheet tab named sheet one with a header row date topic summary sources set
[03:44] So it's giving us the topic. So it didn't even ask us what we wanted. So that's interesting
[03:48] And now we could obviously go back like hey, these are the topics I want to have
[03:53] Share the sheet with the service account email editor access
[03:58] Paints the JSON key as Google service account JSON
[04:03] Let's see
[04:06] Create it's going to then create everything
[04:10] It looks pretty straightforward deploy and verify
[04:16] After deploy go to trigger dot dot dashboard schedules manual trigger and then we'll press test to to run a test and yeah
[04:23] So I am going to look back up here at one more thing
[04:28] Because I think with our variables we are doing the OAuth
[04:37] So let me just tell cloud that not service account
[04:50] And that's the only thing we need to update
[04:54] I think that's it. So let's hit enter see how it changes that and then we should be good to go
[05:02] Okay, so it came up with the updates for authorization
[05:08] I'm going to hit accept and then while it's going to start going through this we need to create these
[05:15] Rows in our Google sheet. So I'm going to hit accept
[05:19] I'm going to go back and find where
[05:24] We want to them
[05:26] What they what we wanted them to say
[05:30] All right, so we have date topic summary. So we'll go date
[05:35] topic
[05:36] Summary in the last three or last two resources and status
[05:42] Status okay super easy
[05:44] It's the sheet is sheet one, which is what it's asking for perfect now again
[05:49] This can all be customized for whatever you're wanting it to be
[05:55] Okay, so that's done
[05:58] We go over here. We have a new morning dash research type script file. Here is everything contained in one
[06:05] Let's do before employing we need to make sure that the variables are added to the trigger dashboard, which we've done
[06:13] Your fire call API or anthropic API and these for from Google and so the one that you might not have is this Google refresh token
[06:23] Which it says here you do a one-time Google OAuth setup if you don't have a research
[06:28] Refresh token yet you go to this website here developers.google.com slash OAuth Playground
[06:34] And then you authorize
[06:36] This URL and you exchange it for refresh token. You'll put in your ID and secrets. I'll go and just show you that really fast
[06:44] So we'll hit this gear right here
[06:47] Down here at the bottom. We'll check this box to use your own OAuth credentials here
[06:51] You'll paste in your client ID
[06:53] Here you'll put in your secrets then over here in this list. You're gonna go down to google sheets
[07:00] Click this arrow and then down here we'll find
[07:04] Google
[07:07] Google apis.com slash auth slash spreadsheets. We've got that checked
[07:13] We will put in
[07:15] Our information there and then you'll hit authorize apis. So let me jump over and grab
[07:22] My codes here
[07:25] All right, so we've got our ID in there our client secret and we've clicked Google apis.com slash auth spreadsheets. We'll click authorize
[07:32] And
[07:34] Then I get this error access blocked. This apps request is invalid. It gives me this error here. So all right
[07:42] So because that method was not working for me. I went back to cloud code and was like hey, it's not working. How can I do that?
[07:48] so
[07:49] Give me this other way to which is kind of crazy cool, but
[07:54] Make sure your client ID and the secret are set up and your in v file and then I want you to run this in
[07:59] In your terminal. It's going to
[08:02] Output an authorization URL. You click it to open it in your browser
[08:06] Once you authorize
[08:08] it's going to
[08:10] Put the refresh token in the terminal you copy it and then you'll paste that in your e and v file and then you want to make sure and paste that
[08:18] into
[08:20] Your environmental variables here
[08:25] All right, so back to where we were
[08:28] We had to just get all that stuff set up. So we've set up our spreadsheet with the column headers
[08:34] We have our environmental variables in the dot e and v file and we have them set up on our
[08:41] trigger.dev
[08:43] environmental variables there
[08:46] And yeah, so the next thing would be
[08:49] To deploy and says after you deploy you go to the dashboard schedules and then manually trigger a test run
[08:56] Develop because obviously if it's a schedule
[08:59] I mean
[09:00] We can't wait till 9 a.m tomorrow to check so running it this way would be able to do that
[09:05] So the last thing it says here is change topic at the top of the file to whatever subject you want tracked so
[09:13] Third probably be a lot of different ways you could choose what subject would be tracked
[09:17] But this is one way which is just kind of hard coded in there if we click on the morning dash research ts file
[09:23] up here
[09:25] At the top right here the hard coded topic is AI agents and autonomous LLM
[09:32] Systems cool. I'm gonna do something a little more unrelated just so it's very different from what we have here
[09:41] like
[09:45] The innovations of car washes
[09:49] It's a very
[09:51] Very different. So we'll save that. Okay. This will be interesting. All right. So we are ready to
[09:58] Deploy this. All right, so it's called hey, let's run it. So we're gonna start with our bash commands. It's going to
[10:06] Look for the workers and then deploy. We just got a bunch of files over here
[10:12] Okay, so it's deployed it successfully now. It's going to trigger the task before we do that. Let's just jump over
[10:18] Trigger.dev so
[10:19] You'll notice if I go back over to production
[10:22] We have in production there the morning dash research
[10:27] right there
[10:30] So do you want to proceed? So now log code is going to actually trigger it. So we're going to trigger the test from here
[10:37] Go to runs
[10:39] Looks like this one's executing right now. You can see it's the morning research one
[10:43] So what we want if we click on this we can see it in real time as things are going
[10:47] So there we go. It's still thinking it's on attempt one on the run
[10:57] We have not even got to this task started yet
[11:01] We're gonna look for any errors to make sure everything set up correctly
[11:07] Okay, so looks like we do have an error
[11:11] Here step one fire crawl search failed
[11:16] So I'm going to move myself kind of down here out of the way
[11:19] And we're gonna have cloud code help us kind of figure out what
[11:23] Happen here
[11:27] Can't really see this. Let's see error fire car return success equals false
[11:33] Web at url car wash management future car wash trend. So it looks like it's trying to it's pulling on
[11:40] url
[11:45] Okay
[11:47] interesting
[11:48] Um, and then we get here it skipped because it's saying there's no there was no results, but we saw something so
[11:58] That's interesting
[11:59] I'm gonna jump over to Google sheets just to show you that it did
[12:04] Have access to Google sheets. So it's putting in the date
[12:08] The topic the summary and no sources because it said it didn't pull in and partial so um
[12:16] That is working
[12:17] So now we need to go in and just double check
[12:22] What's going on with this part here? I'm gonna copy this error right
[12:27] Here I'm gonna go back to cloud code
[12:30] Um, maybe we have to let it complete so it always needs I think the
[12:36] Two or three to get it going, but uh, there's always this last one which is completing it
[12:41] And then we're gonna get the run details which
[12:43] Maybe it will already have access to the error that was output and let's see what it's going to say about
[12:49] Air that we did receive
[12:52] Okay, so sure enough the error handling worked exactly as design
[12:56] Fire crawl failed since this was skipped but step three still wrote a partial row and your sheets right it did
[13:02] So because remember in the beginning we said we didn't want it to fail like even if
[13:06] Fire crawl didn't work
[13:07] We wanted to go all the way through and still add something to the sheet. So that's great
[13:12] So the issue is step one fire crawl took around 29 seconds than aired
[13:17] most likely cause
[13:19] Is the fire call apk isn't in your production variables or the key isn't valid
[13:24] Okay, this could be an easy fix so the trigger dot dev dashboard project settings environment variables confirm the apk is set for production environment
[13:32] So we'll go and check that right now really fast. So environmental variables um
[13:38] Fire crawl apk key it is there. It's for development and for production so that I can get a new key and just check that
[13:48] um
[13:49] Full error message open
[13:52] The run and dashboard and click step one it'll show the exact error
[13:57] Logged there once keys confirmed reach your girl steps and it should go green the sheet right already works as we saw that there
[14:03] So let's double check my api and on we'll check it out again
[14:08] All right, so after looking at this I my api keys were fine
[14:12] So what I did was I went to the step two it said full error message remember when
[14:16] We were here
[14:18] I went over here and I copied this to my clipboard and I paced it and hey here here's the error
[14:22] So that gives club code a chance to really look at this. So
[14:26] I said fire crawl returned with results
[14:28] But in a web property instead of data and the success was false. So
[14:34] The SDK search response shape differs from what we assumed the fixes straightforward
[14:38] So it looks like it's wanting to now make changes to our typescript for the moaning research project
[14:44] So I'm going to say yes, so it looks like
[14:47] the initial code it had is
[14:51] What's caused this issue? So it's going to redeploy with the changes and then
[14:57] If I check the api key we'll run it again and see if we can't get some
[15:02] really fancy news about car washes
[15:06] I first split second thought it was the topic but
[15:10] I mean they've got to be doing some innovations with that right
[15:14] So we'll see okay, so it's deployed the update now it's going to trigger it again
[15:17] It's going to automatically run it again. So we're going to hit yes for that
[15:23] Yes to complete so that means it's already which is it was much faster than last time last time it was around 30 seconds
[15:29] Remember so I'm going to tab over to this real quick
[15:32] So it runs we should have a second one there it is. It's executing right now
[15:37] Okay, there it's going. It's started
[15:41] It looks like we've got eight results now
[15:43] It status is success this time
[15:47] And
[15:48] Let's go to our spreadsheet
[15:51] And let's wrap this
[15:53] It's not pretty, but it did what we wanted it to
[16:01] Geek out on spreadsheets real quick. Okay, there we go
[16:04] So daily briefing, car innovation, smart certints
[16:07] The car wash industry is rapid
[16:09] Technological evolution with AI systems. What
[16:14] Who would have thought now at the forefront automatically scanning vehicles to adjust water pressure soap distribution and
[16:21] drying cycles for optimized personal cleaning experiences
[16:24] Wow
[16:26] Um, I did it just as fun, you know, but hey, we're we're learning a lot today
[16:32] Wow, so AI and car washers who you heard it here first. Okay, so that's working. That's great
[16:38] and remember the coolest part about this is that
[16:42] We go to schedule
[16:44] Now remember there was nothing before we now see
[16:48] Our morning research is scheduled. There's our cron at 8 a.m
[16:54] So remember zero so zero minutes eight hours. So every eight hours
[16:59] And then we've got every day and so on so
[17:04] Um, that is working great and to tell you when the next run is so that would be tomorrow at 8 a.m
[17:11] and
[17:12] Back to our tasks we see
[17:15] Both of them there ready to go so um
[17:19] Have that little hiccup, but again, you know, Claude will make mistakes
[17:22] It might do code one way expecting to get those results like it did from fire crawl
[17:27] Fire crawl got there like hey, here's what I found, but it didn't link up so you know back in 8 a.m
[17:34] We'd be trying to figure out, you know how to connect and that sort of thing
[17:38] So it's kind of similar in that regard. So
[17:40] Very cool. It seems to be working. You can search for whatever topic you want at this point
[17:45] And it's gonna do it for you and then you can go in and change, you know, if you didn't want it to be
[17:52] And this you know, this is probably not the best way to get
[17:57] Information into the sheet, but this is a good way to log
[18:01] Somewhere external that everyone has access to but you could come in and change where you want it to output and so on
[18:08] Super awesome powerful
[18:11] Okay, so let's we've done a whole lot in this video. Let's take a look back real quick. Um, we
[18:17] Built
[18:18] We plan built and then deployed this
[18:21] reoccurring
[18:23] Research um, we tested it
[18:26] Three times more than that really um, it has the crown schedule baked into it
[18:31] So it's very easy to version of control and then we were watching the traces in the dashboard
[18:36] When something went wrong and then went all the things went right and then we double checked everything
[18:41] Everything's connected everything's working great and yeah, we're ready to continue
