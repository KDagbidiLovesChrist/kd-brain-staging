# Loom Transcript · CC_P4_1.6_Stripe_Payments

**Source video ID:** 67557f9e98314908a20c5403e213b97f
**Loom URL:** https://www.loom.com/share/67557f9e98314908a20c5403e213b97f
**Detected language:** en (probability 1.00)
**Duration:** 621.8s

---

[00:00] Okay, it is time now to add payments into our app.
[00:03] So far, we built an app with login and authentication.
[00:06] This allowed us to control who would use our app.
[00:10] But so far, we are giving free access to our users.
[00:13] Even though they signed up,
[00:14] we know who they are and we are controlling,
[00:16] who is logging into our app.
[00:18] Our app right now allows our users
[00:20] to analyze as many leads as they want.
[00:23] If they want to research 200 leads,
[00:25] they are going to be calling our Anthropic API key 200 times.
[00:29] So what we are going to do in this video,
[00:31] we're going to add payments with Stripe
[00:33] so that our users can pay a subscription
[00:35] to be able to use our app.
[00:36] So by the end of this video,
[00:38] you will basically have built a SaaS.
[00:40] You would have built a full app,
[00:41] the front end, the back end,
[00:42] you would have integrated the login authentication
[00:44] and now you're going to be integrating payments
[00:47] so that people pay you to use your app.
[00:49] So we have moved from building just an automation, a workflow,
[00:53] to building a full app that can turn into money.
[00:55] For this, we're going to go back to VS Code.
[00:57] This is our project from our previous video.
[01:00] We're going to go to Cloud Code.
[01:01] We're going to switch to plan mode
[01:03] and we're going to tell Cloud,
[01:05] I want to add Stripe payments to the AI lead qualifier.
[01:08] The free tier gets two lead qualifications per day.
[01:11] So we're going to allow users to run our workflow twice per day.
[01:15] But after that, they need to subscribe, they need to pay.
[01:17] The pay tier is going to be 29 a month
[01:20] and it's going to give them unlimited qualifications.
[01:22] I want to use Stripe for the payment flow.
[01:25] We're going to hit Enter
[01:26] and Cloud Code is going to analyze our project
[01:29] and it's going to come up with a plan
[01:30] on how to integrate Stripe.
[01:32] Okay, after a few minutes, it has finished working
[01:34] and it came up with this plan to integrate Stripe payments.
[01:38] I'm going to take a look at it.
[01:39] The context we have an AI lead qualifier currently
[01:42] has no usage limits or monetization.
[01:44] Any authenticated user can run unlimited qualifications,
[01:47] which incurs Cloud API calls on every request.
[01:51] This plan adds a free new model, free tier
[01:53] or two qualifications per day
[01:54] and a pro tier 29 a month unlimited using Stripe checkout.
[01:58] Okay, it got what we want to do.
[02:00] Implementation is going to solve some packages,
[02:04] environment variables, database,
[02:07] Stripe server clients.
[02:09] These all looks good.
[02:11] It's going to create new pages.
[02:12] It's going to update the navigation bar.
[02:14] Okay, and we have a summary of the plan here.
[02:18] It looks good to me
[02:19] so I'm going to go ahead and auto accept.
[02:22] And now it's going to start working
[02:23] and creating all the files in order
[02:25] to integrate Stripe into our app.
[02:28] Okay, it's been working for a few minutes.
[02:29] Now I actually had to pause the video
[02:31] because it took around pre four minutes.
[02:33] But after that, it finished working
[02:35] and it came up with all these files
[02:36] and it modified these files.
[02:38] So all the configuration files, all the new pages
[02:42] should be here in our code.
[02:43] But let's say I've never done this before.
[02:45] Let's say I've never had a Stripe account.
[02:47] I don't know how to create a new product
[02:49] and I don't know how to connect this into
[02:51] Versel or Superbase.
[02:53] So I'm going to start with a new conversation
[02:55] and I'm going to tell Claude help me set up
[02:58] my Stripe account with a new product
[03:01] and connect Stripe into Versel or Superbase.
[03:05] Guide me step by step.
[03:08] I'm going to hit Enter
[03:09] and I'm going to let Claude guide me
[03:11] and tell me how to set up a new product in Stripe
[03:13] and how to connect Stripe
[03:14] and to guide me in case there's also something
[03:17] to be set up in Versel or Superbase
[03:19] regarding to Stripe.
[03:21] So we're going to start following these steps.
[03:23] Step one, create a Stripe account and product.
[03:26] So we're going to go to Stripe.com
[03:28] and start in Test Mode.
[03:29] So here we are on Stripe.
[03:32] I am on my sandbox, which is Test Mode.
[03:34] But once you're done testing
[03:36] and you want to switch to production,
[03:37] you're going to have to do all these steps
[03:39] that we're going to do right now
[03:40] and you're going to have to do them in your live account.
[03:43] So once we are here on Stripe,
[03:45] we're going to go to Product Catalog.
[03:48] We're going to create a new product.
[03:50] We're going to name it AI Lead Qualifier Pro.
[03:57] It's going to be a recurring.
[03:58] It's going to be a monthly subscription.
[04:00] It's going to cost $29.
[04:03] And we're going to add the product.
[04:05] We're going to save this.
[04:06] OK, once we are done with that, let's go back to Claude.
[04:10] And next step would be to copy our price ID
[04:13] and get our API keys.
[04:15] For this, we're going to click on the product.
[04:17] We just created.
[04:19] And we're going to go to the pricing.
[04:22] And we're going to copy the price ID.
[04:24] I'm going to save these price ID in a node pad
[04:27] because I'm going to be using it shortly.
[04:28] In the next couple of minutes,
[04:29] we're going to be copy and pasting API keys and IDs.
[04:33] So I suggest you start a new document, nodes or something
[04:36] where you can be copy pasting this information.
[04:39] OK, next step was we need to get our Stripe API keys.
[04:44] So in Stripe, we're going to go to Developers API keys
[04:47] and we're going to get these two keys.
[04:50] So we are on Stripe.
[04:51] We're going to go over here to Developers API keys.
[04:55] We're going to get the publishable and the secret key.
[04:59] OK, once we are done with this,
[05:00] we are going to go to step number two.
[05:02] We need to set up the Stripe webhook.
[05:05] So we basically need to connect Stripe with Versel.
[05:08] We're going to go to Developers webhooks at endpoint.
[05:11] And we're going to be creating a new endpoint
[05:13] where our URL is going to be our versatile domain.
[05:16] Slash API slash Stripe webhook.
[05:19] And we're going to be listening to these three events.
[05:23] So let's go to Stripe.
[05:24] We're going to go to Developers webhooks.
[05:28] We're going to create a new destination.
[05:31] Here we're going to select the events
[05:33] that Cloud Code told us to add.
[05:35] This was checkout session complete customer subscription
[05:41] updated and customer subscription deleted.
[05:46] We're going to continue webhook.
[05:50] We're going to set our endpoint.
[05:53] For these, we need our versatile URL.
[05:56] So we're going to copy this.
[05:59] We're going to paste it here.
[06:00] And we're going to add slash API Stripe webhook.
[06:05] I got the full URL from Cloud Code.
[06:07] It's not like I'm making it up.
[06:09] I'm going to go back to Cloud.
[06:10] And it is now telling me that I need to copy the webhook secret.
[06:14] First, I'm going to copy the environment name.
[06:17] I'm going to paste it in my notepad.
[06:20] I'm going to go back to Stripe.
[06:21] I'm going to copy this secret.
[06:24] And I'm going to paste it in my notes.
[06:27] I'm going to go back to Cloud to continue with the instructions.
[06:31] I'm going to skip this part to avoid testing twice in this video.
[06:34] I'm going to be testing directly in Versel.
[06:37] So I don't want to test it locally.
[06:38] And I'm going to go ahead and go to Step 3, where I basically
[06:42] need to go to Superbase and create a new subscription stable.
[06:46] I don't need to create it manually.
[06:47] I just have to go to Stripe Migration SQL.
[06:50] I need to copy this script.
[06:53] And this script is going to create the new table in Superbase.
[06:57] So let's go to Superbase.
[06:58] I'm going to go to my project.
[07:00] I'm going to go to SQL Editor.
[07:03] I'm going to close this one.
[07:05] And I'm going to paste the script over here.
[07:08] I'm going to run the script.
[07:11] And we see the success message.
[07:13] And we should be able to see that our subscriptions table
[07:17] has been created.
[07:19] We can see it over here.
[07:20] We got a new table for subscriptions.
[07:23] So let's go back to Cloud Code and see the next step.
[07:26] And finally, we're going to be connecting Stripe to Versel.
[07:30] We're going to go to Versel.
[07:31] We're going to create new environment variables.
[07:33] And we're going to paste the keys, the secret keys,
[07:36] that we have been copying into our notepad.
[07:39] So let's go to Versel.
[07:40] We're going to go to Settings, Environment Variables,
[07:46] Add New Environment Variable.
[07:49] We need to create the Stripe secret key.
[07:52] Next, we're going to add our Stripe public key.
[07:56] Next, our Stripe Product Price ID.
[07:59] And finally, we're going to add our Stripe webhook secret.
[08:03] If you don't remember where we got any of these keys,
[08:06] feel free to go back a few minutes into this video.
[08:08] And go to the part where we created a new product
[08:10] in Stripe.
[08:11] And this one, we got it when we created a new webhook in Stripe.
[08:14] So these four keys are all from Stripe.
[08:17] OK, we're going to hit Save.
[08:19] We're going to redeploy so that we can see our updates
[08:23] in the website.
[08:24] And we can go ahead and test it.
[08:26] So we can go to Deployments.
[08:28] We can see that it's still building.
[08:29] It's not ready yet.
[08:31] So we're going to give it a few seconds.
[08:33] OK, now it's ready.
[08:35] So I'm going to click over here.
[08:37] And I'm going to open the app.
[08:39] And we can see that now we have a new section called pricing.
[08:42] In the previous video, we had created our history page
[08:45] and logging and sign out.
[08:46] But now we've also added pricing.
[08:48] We have over here the free tier, which is our current plan,
[08:52] is going to give the users two lead qualifications per day.
[08:55] And now we also have the pro plan, which is 29 a month,
[08:58] where users get unlimited qualifications.
[09:01] So if we go to subscribe, we should be
[09:04] able to see the Stripe Checkout page.
[09:06] And it's now sent us to the Stripe Checkout page.
[09:09] I'm going to select card.
[09:11] I'm going to type the test card information that Stripe
[09:15] gives developers to test this stuff.
[09:18] As long as you add any date in the future like October 27,
[09:22] any security code is fine, full name.
[09:25] We're going to go to subscribe.
[09:27] And we can see that now we are subscribed.
[09:29] So we are not on the free tier anymore.
[09:32] This is actually our current plan, the pro plan.
[09:34] And we can now see that our subscription has been activated.
[09:37] And if we go to super base, subscription's table,
[09:41] we're going to see that now we have a new role,
[09:43] which means we have a new subscriber.
[09:45] So this is how you integrate Stripe Payments into Europe.
[09:49] So now in addition to having more control over who
[09:52] can use Europe by adding authentication
[09:54] as we did in the previous video, we now
[09:56] have a login sign up.
[09:57] And in this video, we have added payments.
[09:59] So you can now have users pay to use your workflows.
[10:03] So you don't have just a workflow anymore.
[10:05] You actually now have a full app.
[10:07] Users can go to your website as long as they have the URL.
[10:10] They can sign up.
[10:11] They can log in, log out.
[10:13] They can see their own history of which leads they
[10:16] have researched before.
[10:17] And you can now get paid anytime a user
[10:19] subscribes to use your app.
