# YouTube Transcript · zA9r5zTllx4

**Video ID:** zA9r5zTllx4
**Source:** https://www.youtube.com/watch?v=zA9r5zTllx4

---

[00:00] what's the biggest lie in web
[00:01] development that those websites you know
[00:04] the ones that win awards are impossible
[00:06] to build alone that it takes a team of
[00:09] 50 developers and probably some dark
[00:11] magic to make it happen they want you to
[00:13] believe that those insane animations
[00:15] those mindbending interactions and those
[00:18] perfectly smooth transitions they're out
[00:20] of your league reserved for elite
[00:22] agencies with massive teams but not
[00:25] today because today you'll build an
[00:27] award-winning website you've always
[00:28] dreamed of the of site that makes both
[00:31] apple and SpaceX designers take
[00:33] screenshots and I ain't joking seriously
[00:36] this isn't just another landing page
[00:38] tutorial or a basic website guide this
[00:40] is everything you've been searching for
[00:42] in those 3 a.m. Googling sessions every
[00:45] butter smooth animation technique every
[00:47] design hack every how did it do that
[00:49] moment explained in a detailed
[00:51] step-by-step course teaching you how to
[00:53] build a zentry inspired site a Gaming
[00:56] website that won a s of the day award
[00:59] I'm referring to entry.com a metagame
[01:01] platform that has a super unique website
[01:04] this course will teach you how to build
[01:05] some of the parts from their website and
[01:07] while building it I'm sure you'll want
[01:08] to play some games so check them out and
[01:10] thanks for the inspiration zentry decom
[01:12] you'll recreate this stunning website
[01:14] using react and tailn CSS featuring an
[01:17] animated floating nav bar with music
[01:19] animations a hero section playing a full
[01:21] screen video with an amazing hover
[01:23] effect transition switching to the next
[01:25] and next video which then expands in
[01:27] full screen a butter smooth about
[01:29] section showing animated text with an
[01:31] image transition as we scroll down the
[01:33] website see how smooth it is immediately
[01:35] after we have a trendy Bento grid design
[01:38] with a card tilt effect as you move your
[01:40] cursor this is coded completely from
[01:42] scratch trust me no external libraries
[01:45] used with yet another cool section with
[01:47] animated text with images in a
[01:49] completely different shape thanks to CSS
[01:51] magical properties with a nice hover
[01:54] effect and finally a nice little cold to
[01:56] action section with different images
[01:58] with different Cool Shapes and a minimal
[02:00] footer everything is neatly done and
[02:02] super responsive working as expected on
[02:05] every device with no performance issues
[02:07] this video is for everyone who's been
[02:09] told that's too advanced for a single
[02:11] developer or you need an agency to build
[02:13] something like that because after today
[02:15] the only thing standing between you and
[02:17] your first Awards nomination is
[02:19] continuing to watch this video and the
[02:21] first step in building our app is
[02:23] setting up our hosting you can think of
[02:24] this project as a career asset designed
[02:27] to Showcase everything you're capable of
[02:28] making you an attractive candidate for
[02:30] any job or freelance opportunity I
[02:32] highly recommend hostinger for hosting
[02:34] this app especially since they're
[02:35] running the biggest Black Friday sale
[02:37] ever I'll go for the Premium plan as it
[02:39] allows us to host a 100 websites with
[02:41] free SSL for https security a free email
[02:44] for that professional touch and even a
[02:46] free domain name to give your website a
[02:48] good name and because I partnered with
[02:49] hostinger you get an even bigger
[02:51] discount click the special link in the
[02:52] description click claim deal and add to
[02:55] card here we have to choose the period
[02:56] of our hosting I'll choose 48 months to
[02:58] save the most enter your JavaScript
[03:00] Mastery coupon code and check out once
[03:02] you're done with the purchase we're
[03:03] ready to set everything up starting with
[03:05] the hostinger guided setup I'll just
[03:06] skip create a website we'll build a
[03:08] website from scratch so we can just say
[03:10] empty right here and right here you can
[03:12] choose a domain name or it's possible
[03:14] that you don't yet know what you want
[03:15] your website to be called so you can use
[03:17] a temporary domain name right here but
[03:18] in this case I'll say awardwinning
[03:21] website.com let's see if that is
[03:22] available oh would you look at that it
[03:24] actually is I'll choose it and click
[03:26] next here you can choose where your
[03:27] audience is located and that's it the
[03:29] setup can begin and since I already
[03:31] chose a domain the SSL certificate is
[03:33] immediately getting installed we'll
[03:34] return to this dashboard at the end of
[03:36] the course so once you build your
[03:37] website you can deploy it with that said
[03:39] let's dive straight into the
[03:48] code hello hello hello and welcome to
[03:51] the start of another amazing build since
[03:54] we are recreating an award-winning
[03:56] website I'll start from bare Beginnings
[03:58] by creating a new folder on my desktop
[04:01] and I'll call it Awards once you create
[04:04] it open it up within your favorite code
[04:06] editor in this case I'll be using the
[04:09] webstorm IDE which as of recently is
[04:12] completely free for non-commercial use
[04:14] so once you open up the folder on your
[04:16] code editor open up an integrated
[04:18] terminal within it run mpm create V add
[04:23] latest. slash which will create a new V
[04:26] application right within our current
[04:28] folder it's asking us whether you want
[04:31] to install the Ved installer so say why
[04:34] yes in my case it says that the current
[04:36] directory is not empty that's totally
[04:39] okay we can say remove everything that
[04:41] is on there and continue we're starting
[04:43] from scratch after that it's going to
[04:45] ask you for the framework of your choice
[04:47] in this case we'll proceed with
[04:50] react it's going to ask you for your
[04:53] flavor of the JavaScript language if you
[04:55] like typescript feel free to proceed
[04:57] with that in this case I'll go with just
[04:59] JavaScript script and that's it after
[05:01] that you can run mpm install and then
[05:03] mpm runev to run the app within the
[05:06] browser that's going to spin it up
[05:07] incredibly quickly on Local Host 5173 so
[05:11] let's click it and here it is V plus
[05:14] react empty starter repo now we ready to
[05:17] start turning this into something that
[05:20] looks a little more like this with crazy
[05:23] animations and more and to make it
[05:26] happen we'll use react the library for
[05:29] web and native user interfaces but of
[05:31] course feel free to replicate this using
[05:33] any other library or framework of your
[05:35] choice everything that I show here with
[05:38] a little bit of knowledge and tweaking
[05:40] you should be able to fit just the
[05:42] framework language or technology that
[05:44] you prefer of course we'll build it
[05:46] using Tailwind CSS which is a CSS
[05:49] framework that allows you to very
[05:50] quickly style your applications while
[05:53] making them completely custom I'll also
[05:55] show you a couple of simple looking but
[05:57] quite effective tools like this CSS
[06:00] clipmaker that's going to bring our app
[06:01] to life once we integrate 3D and GP
[06:04] animations into it and once we're done
[06:06] building it I'll teach you how to host
[06:08] it on your custom domain name using
[06:10] hostinger and I just got to mention that
[06:13] every single technology you'll use to
[06:15] build this project is completely free so
[06:18] you don't have to worry that you'll be
[06:19] stuck behind some kind of a pay wall or
[06:21] that you'll be required to pay something
[06:23] it is completely free to build the only
[06:25] thing you need are your skills oh and
[06:27] since I'm telling you about all the cool
[06:29] stuff that I'm using a lot of people ask
[06:31] me what kind of browser is this where
[06:33] there's no top bar with a lot of icons
[06:35] and everything this is called Arc and
[06:37] it's a browser with a collapsible left
[06:40] sidebar that allows you to focus on the
[06:42] main content but of course it still has
[06:44] everything you might need for debugging
[06:46] and networking as it's based on chromium
[06:48] to get it you can just go to ar.net
[06:50] again not affiliated just wanted to
[06:52] share this cool thing with you as always
[06:54] but with that said let's go ahead and
[06:56] explore the file and folder structure
[06:58] that was gener ated for us when we
[07:01] installed a Ved application starting
[07:03] from the source folder which is the most
[07:05] important folder you'll notice that we
[07:07] have a lot of stuff which we might not
[07:08] need right now such as the app CSS index
[07:11] CSS and a lot of boiler blade code
[07:14] within the app jsx so let's go ahead and
[07:18] clean up this app file by simply
[07:21] removing everything and running our
[07:24] afce this stands for react Arrow
[07:27] function export component which just
[07:29] creates creates a simple functional
[07:30] react component and if that didn't work
[07:32] for you you might need to head over to
[07:34] plugins or extensions and then install
[07:37] any kind of a react Snippets package
[07:39] with that said let's also clean up the
[07:42] index and app.css since we won't be
[07:44] needing them now that we have a bit of a
[07:47] cleaner working environment let's go
[07:49] ahead and set up Tailwind CSS I don't
[07:51] want to just give you the commands I
[07:52] want to teach you how you can do it in
[07:54] your future applications by following
[07:56] the docs so head over to tailin css.com
[08:00] and go over to get started you can
[08:02] scroll down to see the installation
[08:04] steps and the first thing you'll have to
[08:05] do is install detailin CSS as a Dev
[08:10] dependency but just to make sure let me
[08:12] go to search and see if this is the
[08:15] installation for vit for react if you
[08:18] scroll down right here you'll notice
[08:20] here it's a bit different we also need
[08:22] post CSS and auto prefixer so make sure
[08:25] to head over to the docs page where you
[08:27] have to install Tailwind with beat so
[08:30] I'll copy this command open up my
[08:32] terminal I'll actually create a new tab
[08:35] and then paste it mpm install DD
[08:39] Tailwind CSS postcss Auto prefixer and
[08:42] then MPX Tailwind CSS in it- P this will
[08:46] initialize a new tailin config within
[08:49] your project so as the second part
[08:51] you'll have to override that tailin
[08:53] config by adding these two parts into
[08:56] the content again you can just copy it
[08:59] and override it right
[09:01] here next you'll have to add tailin CSS
[09:04] directives to our CSS so let's copy it
[09:08] let's create a new file within the
[09:11] source folder and let's call it
[09:13] index.css within which we can import
[09:17] those Stalin CSS
[09:19] directives after that you can head over
[09:21] to your
[09:22] app.jsx and we can turn this div into a
[09:24] main
[09:26] tag and create an H1 that it's going to
[09:29] say something like welcome to Awards
[09:33] I'll give it a class name equal to text-
[09:36] 5xl to be extra large text- orange
[09:43] d500 and font dbol now head over to your
[09:46] first terminal stop it from running by
[09:49] pressing contrl C and then rerun it
[09:51] again with mpm run Dev if you do that
[09:53] and head back to Local Host 5173 you'll
[09:56] be able to see this large orange H1 that
[10:00] says welcome to Awards so congrats that
[10:03] means that we have set up our react
[10:05] application successfully and also
[10:07] successfully added tailin CSS to
[10:11] it let's continue setting up our project
[10:14] by first setting up the font families
[10:17] which we'll use within our landing page
[10:18] you'll notice that there's quite a few
[10:20] we have this interesting one where some
[10:22] elements like the n in this case or the
[10:25] a has this very interesting element to
[10:27] it then we have this one
[10:29] and overall everything is just
[10:31] completely custom made including the
[10:33] fonts I took some time to gather all of
[10:35] these fonts and I'll give them to you so
[10:37] you can put them right here instead of
[10:39] this empty public folder so go ahead and
[10:42] delete the existing one and also delete
[10:45] the assets folder because everything
[10:47] will be inside of the public folder now
[10:50] head over to the description of this
[10:51] video and find a link pointing to a
[10:54] GitHub repository containing the code
[10:56] for this entire project below the code
[10:59] you'll be able to see a readme file
[11:01] which contains all of the information
[11:03] about this project as well as a link
[11:06] pointing to the assets head over there
[11:08] click it download it unzip it and then
[11:11] simply drag and drop it to the root of
[11:13] your
[11:14] directory it's going to look something
[11:16] like this and it'll contain the audio
[11:18] which we want to use in our website as
[11:20] well as the fonts which I was telling
[11:22] you about as well as some images and
[11:24] even videos which are going to make our
[11:26] landing page that much more dynamic so
[11:30] now that we have those fonts let's
[11:31] actually use them within the index.css
[11:34] file here you can use a tailan CSS layer
[11:38] property and Define the base base is
[11:41] used for defining some basic properties
[11:44] like the font faces so we can Define the
[11:47] first font face by specifying a font
[11:50] family and making it equal to
[11:53] Circular Das web this is the name of one
[11:56] of our fonts once you define it you'll
[11:59] you also have to pass a source pointing
[12:01] to URL where it's contained in our case
[12:04] it's going to be under SL fonts SL
[12:08] circular
[12:10] web-book do
[12:13] W2 which is the format and you can exit
[12:16] the URL and Define the format by saying
[12:20] W2 you might get a red scly line saying
[12:24] that the file doesn't exist but don't
[12:26] worry about it because it's right here
[12:28] under fonts and make sure you have a
[12:30] double and not a triple F right here
[12:32] because that's the correct name of the
[12:34] format let's also add all of the other
[12:36] font Faces by saying add font
[12:40] face this one will be a
[12:42] font-family of general and it'll have a
[12:45] source equal to URL pointing to SL fonts
[12:51] slen Dot and then the same type of the
[12:53] font with a format being the same format
[12:56] we can add one more font face
[13:00] and this one will have a
[13:02] font-family equal to Robert Das medium
[13:07] what an interesting font name it's going
[13:09] to have a source equal to URL which is
[13:12] going to point to for SL fonts SL Robert
[13:16] DM medium. woof and we're going to have
[13:19] a format of woof as well or should I say
[13:23] woof woof as it's a wa 2 format and
[13:26] finally we're going to have another font
[13:28] face the last one in our application
[13:31] with a font family equal to Robert D
[13:35] regular that's going to be within a
[13:37] string and it's going to have a source
[13:39] equal to URL pointing to for SL fonts SL
[13:44] Robert D regular. woof and a format of
[13:49] woof and yep you got JavaScript Mastery
[13:51] barking on the channel before GTA 6 was
[13:54] released but with that said now that we
[13:56] have those font faces right here let's
[13:58] actually use them within our Tailwind
[14:00] config so you can head over to Tailwind
[14:04] Doc config.js
[14:05] and let's add them to our theme by
[14:09] extending it and then extending the font
[14:12] family specifically with all of those
[14:14] fonts first we want to add zentry which
[14:17] is going to be equal to the name of
[14:20] zentry and it's going to be a Sans serif
[14:23] font after that we want to add a general
[14:26] font which is going to be same thing
[14:29] General Sans serif then we want to add a
[14:32] circular Das web which is going to be
[14:36] once again a similar thing circular web
[14:38] Sans serif after that we're going to
[14:41] have a Robert DM medium which is going
[14:45] to be Robert DM medium Sans serif and
[14:48] finally Robert regular Sans serif so
[14:52] this way we'll be able to use these
[14:54] fonts within our application let's just
[14:56] make sure that we have all five right
[14:58] here and yep we do now for just a second
[15:01] let's head back over to index. CSS I'll
[15:04] collapse this layer and at the top of it
[15:07] I'll modify my body by giving it a font
[15:10] family equal to General Sans and Sans
[15:15] serif like this just to make sure that
[15:18] every element unless specified otherwise
[15:21] uses this general font we can also
[15:24] specify a width of the body to be equal
[15:26] to 100 d VW and dvw is actually a new
[15:32] CSS property that is very similar to
[15:35] regular VW which stands for vertical
[15:38] width but it solves the classic scroll
[15:41] bar problem that happens when the page
[15:43] has a vertical scroll bar while we're
[15:45] here let's also give it a background
[15:49] color to make sure that our application
[15:51] looks great that's going to be hash DF
[15:56] d0 that's the color I want to use and
[15:59] I'll give it the Overflow X of hidden so
[16:03] we don't get any unnecessary scroll bars
[16:06] and I just realized that I'm in the CSS
[16:08] file not in JavaScript so we don't have
[16:10] to wrap it in string signs so now what
[16:12] do you say that we test out some of
[16:14] these fonts by heading over to our app
[16:18] and giving it to this H1 by saying font
[16:21] Dash and now we can choose anyone you
[16:23] like in this case I'll go with font
[16:25] circular web and you can see that it
[16:27] immediately changed in the same way you
[16:30] can do font D Robert DM medium and I
[16:33] think it's a bit different either way
[16:36] let's remove this font for now because
[16:38] we have more important stuff to focus on
[16:41] which are the colors specifically the
[16:44] color theme which we'll be using within
[16:46] our application in the same way we have
[16:48] extended the fonts now we want to extend
[16:51] colors if you check out the finished
[16:53] application you'll notice that we'll use
[16:55] some of the colors often like this
[16:58] purple one maybe even this black one or
[17:01] this yellow one on this button so
[17:03] instead of every time saying something
[17:05] like text Dash and then in square
[17:07] brackets manually specifying the color
[17:09] like what I'm doing here and then
[17:11] imagine if one changes it would just be
[17:13] a mess because it would have to change
[17:15] it across all the files in this case
[17:17] we'll just create a list of predefined
[17:20] colors and then you can say text- blue
[17:23] -50 which is immediately going to give
[17:25] you that custom variant of a color and
[17:28] just recently I do deep into setting up
[17:30] a tailin CSS theme for every application
[17:33] no matter which one it is in my next GS
[17:35] course here I dive deep into telling you
[17:38] exactly what you have to do from scratch
[17:41] and even how to extract those colors and
[17:43] fonts from a figma design so if you've
[17:45] been wanting to dive into nextjs a bit
[17:47] deeper for quite some time now well I
[17:49] really do think now is the chance so go
[17:52] to JS mastery. proo and join the course
[17:54] it'll be a great thing for you to do
[17:56] after you watch this video but with that
[17:58] said I still want to teach you how you
[18:00] would go about adding custom colors so
[18:02] if you go over below the font family
[18:05] still within the extend you can say
[18:07] colors and then specify different
[18:09] variations such as blue within blue you
[18:13] can create different shades of blue such
[18:16] as a 50 version of Blue which can be DFD
[18:20] F0 I use a Color Picker and then pick
[18:23] this color from another website we have
[18:26] about five or seven colors to add so
[18:28] with me and let's add them together the
[18:31] 75 variation of the blue will be hash
[18:35] DFD
[18:37] ff2 we have a 100 variation which will
[18:40] be hash F0
[18:44] f2fa next we have a 200 which is going
[18:47] to be hash 1 1 0 1 0 that's going to be
[18:52] a black color and finally a 300 which is
[18:55] going to be hash 4f B7 DD that's going
[19:00] to be this primary blue color that we'll
[19:03] use throughout the
[19:04] website we can also create a variation
[19:07] of violet specifically a 300 variation
[19:10] which is going to be hash
[19:13] 5724 FF and finally below Violet we'll
[19:18] have a 100 variation of yellow which is
[19:20] going to be hash 8 e
[19:24] 983 F and another one will be a 300
[19:29] which is going to be hash Ed
[19:33] ff66 this is going to be a bright yellow
[19:35] as you can see here on the left side
[19:37] where we can open up the Color Picker
[19:39] great now let's test out this violet
[19:42] color by going back to our H1 and saying
[19:46] text-
[19:47] Violet Dash I believe it was 300 right
[19:51] and there we go that works like a charm
[19:54] this means that you have successfully
[19:55] set up both the fonts and the color
[19:57] theme which are the two most important
[20:00] parts of a tailin
[20:01] config so with that in mind immediately
[20:04] in the next lesson we'll be able to dive
[20:07] into the hero section so let's do that
[20:09] next exciting stuff coming
[20:12] up to get started with a hero section
[20:16] let's go ahead and create a new folder
[20:18] in the source folder and let's call it
[20:22] components within the components folder
[20:25] I can create a new file which I'll call
[20:27] hero
[20:29] jsx and within it I'll run rafc a react
[20:34] Arrow function component now that I have
[20:37] it I'll simply import it at the top of
[20:39] the app so let's go over here and within
[20:43] the main instead of this H1 I will now
[20:45] render the hero section don't forget to
[20:49] import it from that/ components slh hero
[20:53] and while we're here let's also give a
[20:56] class name to this main tag which which
[20:58] is going to be equal to relative Min dh-
[21:02] screen so this way the minimum height of
[21:05] the screen will be 100% of the view
[21:08] height we can do the same thing for the
[21:11] width W screen and overflow dx- hidden
[21:16] so we don't get those ugly scroll bars
[21:19] now I can head over to the hero and we
[21:22] can start implementing it but first I've
[21:24] opened up my browser on Local Host 5173
[21:27] so we can see the changes that we make
[21:29] in our editor live on the right side
[21:32] let's start by giving this div a class
[21:34] name equal to
[21:36] relative h-d vertical height and once
[21:40] again if this DV height or dvw are a bit
[21:44] weird because they're completely new
[21:46] well the d stands for dynamic the sizes
[21:49] of the dynamic Viewpoint percentage
[21:51] units are not stable even while the
[21:53] viewport itself is unchanged using these
[21:56] can cause the content to resize in this
[21:58] case this is exactly what we want which
[22:00] is why we're using them I'll also define
[22:03] a w screen which is going to give it a
[22:05] full width and finally the Overflow X of
[22:09] hidden within it I'll create another div
[22:12] and that div will play the video
[22:15] remember that huge video which plays in
[22:17] full screen well yes this is the div
[22:19] that will contain it so let's give it an
[22:21] ID equal to video- frame and let's give
[22:25] it a class name equal to relative Z of
[22:29] 10 so it appears above other content h-
[22:33] dvh W screen overflow Das hidden rounded
[22:40] dlg and BG blue of 75 within it we can
[22:44] display another div and within that div
[22:47] we'll have another div that will have a
[22:49] class name equal to mask Das clip Das
[22:56] path now what is this
[22:59] is this some kind of a tailin property
[23:01] is this a tailin CSS class well not
[23:04] really because we cannot see anything if
[23:06] we have our over it or select it so this
[23:09] means that this is a special class name
[23:11] which we have to write and to be able to
[23:13] reuse some tailin CSS classes for
[23:16] example see how we type the same thing
[23:18] here and on the homepage it's very
[23:21] similar imagine if you could just say
[23:24] something like Max width and this would
[23:27] automatically apply all of these classes
[23:29] both here and here we can do that by
[23:33] expanding our index.css file so if you
[23:37] head over here right below the base you
[23:39] can actually Define another add layer
[23:43] but this time for utility classes and
[23:45] within it you can say something like
[23:47] absolute Das Center and then you can say
[23:51] add apply and you can apply whatever
[23:54] class name you want like absolute top-1
[23:57] over2 and and so on and then you can use
[24:00] this class name within your code there's
[24:03] going to be plenty of classes which
[24:05] we're going to write throughout this
[24:06] video so I want to provide some of them
[24:09] to you to make her life a bit easier so
[24:11] in the same GitHub repo where you found
[24:13] the assets you can also find a complete
[24:16] index.css
[24:17] so simply copy it and override whatever
[24:21] you have here you'll notice that it
[24:23] includes some class names for images
[24:25] headings and even some fonts as well as
[24:28] the font once we wrote at the start now
[24:30] if you hover over the mask clip path
[24:32] it'll actually know that it is a special
[24:34] class within the index. CSS which
[24:37] applies a specific polygon I'll explain
[24:40] exactly how I got to this later on but
[24:42] for now let's get something showing
[24:44] within that div we can continue by
[24:46] giving it another class name of absolute
[24:49] Das Center which will Center it we can
[24:51] give it a position of absolute a z of 50
[24:54] so it appears on top a size of 64
[24:58] a cursor of pointer overflow of hidden
[25:03] and rounded dlg within it we'll create
[25:06] another div which will actually be a
[25:09] mini video
[25:11] player there we go you can see it here
[25:13] in the middle and it is clickable what
[25:15] this actually is is this video player
[25:18] that allows you to change the background
[25:20] or the video playing in the background
[25:22] just by clicking on it it's a pretty
[25:24] cool feature and I'm so excited to show
[25:26] you how it works so let's first first
[25:28] get that video playing and then once the
[25:30] user clicks on it we can show it in the
[25:32] background as well to do that we have to
[25:34] start adding some functionality so I'll
[25:36] Define a new function const handle mini
[25:42] VD video click so this is going to be
[25:45] the mini video player
[25:47] click we have to know when a user has
[25:50] clicked something and we also have to
[25:52] keep track of which video is playing or
[25:55] the index of that video so let's define
[25:58] a couple of use State Fields I'll say
[26:01] use State and I'll use the use State
[26:03] snippet to quickly create it I'll call
[26:06] the first state current index as well as
[26:09] Set current index and at the start it'll
[26:11] be set to one let's not forget to import
[26:14] use state from react alongside the
[26:18] current index I also want to know
[26:20] whether the user has clicked anything so
[26:22] at the start I'll create another use
[26:24] State snippet which will have a name of
[26:27] has clicked and the set has clicked at
[26:31] the start equal to false by the way see
[26:33] how it actually tells me what this
[26:35] variable here does like it says use
[26:37] State's first parameter is actually for
[26:40] its initial state in the last video many
[26:42] of you asked me how did I add that what
[26:44] kind of package is it well this is
[26:46] actually a feature built right into
[26:48] webstorm so I didn't have to do anything
[26:50] to add it I'll also add another use
[26:53] State snippet and I'll call this one is
[26:56] loading and set is loading at the start
[26:59] set to
[27:01] true because the video typically does
[27:03] take some time to load at the start and
[27:06] finally I'll create another use State
[27:09] for the number of videos that has loaded
[27:11] so I'll say loaded videos which at the
[27:15] start will be equal to zero we can also
[27:18] Define the number of Total videos which
[27:20] you want to play in this case I'll set
[27:22] it to four and we need to define a
[27:25] reference which will allow us to then
[27:27] switch between those videos or to Target
[27:29] the player within which will play the
[27:32] videos to do that we can say const next
[27:36] VD video ref is going to be equal to use
[27:41] ref which we have to import from react
[27:45] and at the start it'll be set to null in
[27:48] react you use a ref whenever you want to
[27:51] Target a specific Dom element like the
[27:54] iframe or like the div within which we
[27:57] want to play that video you can see here
[28:00] this div has an ID of video frame now
[28:03] once we click on this mini player we
[28:05] want to set has clicked to be equal to
[28:09] true and we also want to set the current
[28:11] index to be equal to a function where we
[28:15] get the previous index and then we
[28:16] simply say prev index plus one so we're
[28:20] always incrementing that index with a
[28:22] new one now we can handle this mini
[28:25] video click right here once we click
[28:27] this div now to actually be able to see
[28:30] what's happening let's continue
[28:31] implementing this div by giving it a
[28:34] class name of origin Dash Center but
[28:38] before I start adding more classes let's
[28:40] actually implement the video right
[28:42] within it I will render an HTML 5
[28:46] self-closing video tag and give it a ref
[28:49] equal to next video ref and you know
[28:53] what I actually don't like shortening
[28:55] things like VD who knows whether that's
[28:57] a video or something else so I will
[29:00] rename it to next video ref always a bit
[29:04] better to be a bit more descriptive than
[29:06] to shorten it out and now I will say
[29:08] next video ref and a video component
[29:12] also needs a source a source to the
[29:15] video to be played so right here above
[29:18] the return let's create a new const get
[29:22] video Source equal
[29:25] to a function where we get the index and
[29:29] then it automatically returns a path of
[29:33] videos slash hero Dash dynamically
[29:37] render the index.
[29:40] MP4 and let's properly spell videos
[29:43] again this is pretty cool even though
[29:44] this is not an error notice how webstorm
[29:47] notice that there's a typo in the word
[29:49] videos so I will definitely fix that and
[29:53] this is giving us the path of each
[29:55] specific video source so let's say
[29:57] source is equal to get video source to
[30:01] which we can pass the current index +
[30:05] one so why is it plus one well because
[30:09] we have this large video and then once
[30:12] we click on the inner one it actually is
[30:15] going to play it on the big screen so
[30:17] this smaller one always has to be one in
[30:19] front of the main video player next
[30:21] let's make sure that this video Loops so
[30:24] we're going to give it a loop as well as
[30:26] a muted property and the ID equal to
[30:29] current Das video and we can give it a
[30:31] class name of size-
[30:35] 64 origin Das Center scale of
[30:40] 150 object D cover and object Das Center
[30:44] finally we can also render the onloaded
[30:48] data which is a special Handler that
[30:50] allows us to call a function once data
[30:52] loads and here we can call a handle
[30:56] video load function
[30:58] this is a new function which we can
[31:00] create right here at the top let's call
[31:03] it hand const handle video load and it's
[31:09] going to be equal to an arrow function
[31:11] that will simply set loaded videos to be
[31:14] equal to prev loaded videos plus one
[31:18] like this now we can scroll down and we
[31:21] can provide additional class names to
[31:23] this div containing this video player so
[31:26] let's give it a class name of scale of
[31:29] 50 to make it a bit smaller at the start
[31:32] let's give it opacity of zero because at
[31:34] the start it should not be present but
[31:38] transition all meaning that we can
[31:39] animate some properties throughout a
[31:42] duration of 500
[31:45] milliseconds ease in and we're going to
[31:47] animate it on Hover so on Hover we're
[31:50] going to change the scale back to 100
[31:53] and the opacity to 100 now if I hover
[31:56] over it check this out it appears as if
[31:59] we're trying to get into this video so
[32:03] it's similar right here there we go what
[32:07] is missing is that once we click it we
[32:09] actually show it in the background now
[32:11] if you click on this video it'll
[32:13] actually switch it to the next one and
[32:15] the next one and the next one Until It
[32:17] Breaks because we're always going one
[32:20] more right here but once we pass the
[32:22] number three then we're lost we have no
[32:25] four five six or so on so we can use a
[32:29] special trick we can be very smart about
[32:31] it and we can only try to go up to three
[32:34] but then if it's more than that we need
[32:36] to go back to zero and start all over
[32:39] again that is the perfect use case for
[32:41] the modula operator it Returns the
[32:44] remainder of the division of one number
[32:46] being divided by another so for example
[32:48] if you divide 5 by two you're going to
[32:51] get one because 5 / 2 will be 2 * 2 and
[32:55] then the remainder will be 1 in our case
[32:58] if you try to divide 1 by 4 which is the
[33:01] total number of videos you're going to
[33:03] actually get one because you cannot
[33:05] divide it so let me show you how we can
[33:07] implement it in our case to make sure
[33:09] that we can only go up to the last video
[33:11] and not any further I'll create a new
[33:14] variable called const upcoming video
[33:18] index and that's going to be equal to
[33:21] current index modulo Total
[33:25] videos and then I'll wrap it in
[33:27] parentheses
[33:28] and give it A+ one so what this will do
[33:31] is it will try to divide 1 by 4 or
[33:35] rather 0 by four at the start where the
[33:37] remainder is going to be zero to that
[33:40] zero we will add one so 0 + 1 will end
[33:43] up being one after that it will try to
[33:47] divide one by four which will leave us
[33:50] the remainder of one so it's going to go
[33:52] to two and in this case I should
[33:54] actually be putting the modul operator
[33:56] instead of the division because it's a
[33:59] remainder operation after that we'll try
[34:01] to divide 2 by 4 which is going to leave
[34:04] 2 + 1 is 3 and finally it's going to do
[34:07] 3 by 4 which will give us four which is
[34:10] the last index so finally once you do
[34:12] that last modular operator the remainder
[34:14] will be zero and we once again start
[34:17] from one isn't that beautiful that's
[34:20] just some math right here so now we can
[34:23] set the current index to be equal to up
[34:27] upcoming video index great now if we
[34:32] reload you can keep pressing and we
[34:34] actually have three videos so one is
[34:37] extra right here so for now I will just
[34:40] put the total number of videos to be
[34:41] three if we do that you can naturally
[34:45] switch between all of these videos this
[34:47] is great now let's continue right below
[34:50] this video and Below two more divs
[34:53] because now is the time to create
[34:55] another video component which will be
[34:57] our primary background video player
[34:59] it'll have a ref equal to next video ref
[35:03] and a source equal to get video Source
[35:07] but this time we're not passing the
[35:09] upcoming index we're passing the current
[35:12] index oh and here we no longer have to
[35:14] use the current index plus one we can
[35:16] just use the upcoming video index
[35:19] because we have created a variable out
[35:20] of
[35:21] that so check this out you can click it
[35:24] and it actually changes on this top
[35:26] video player this is pretty amazing like
[35:28] check this out we have this scene with
[35:31] this rock and buildings I click it it
[35:33] shows up here we have this scene with
[35:36] this boy and we click it shows up at the
[35:38] top we have this woman right here we
[35:40] click it shows up at the top I mean this
[35:43] is pretty cool I got to say but it's
[35:45] going to be so much cooler once we
[35:47] actually implement the video player so
[35:49] that it shows up and you go into the
[35:52] scene you enter it so to continue
[35:55] working on this amazing hero section
[35:57] let's let's give this video a loop
[35:59] property let's make it muted let's give
[36:02] it the ID equal to next video and let's
[36:05] give it a class name equal to Absolute
[36:09] Das Center let's also give it
[36:11] invisible I'll give it the absolute
[36:14] positioning zindex of 20 size of
[36:18] 64 object D cover and object Das Center
[36:23] and onload the data I'll give it the
[36:25] handle video load so right now you
[36:28] cannot really see the big video just yet
[36:31] but you will be able to see it soon we
[36:33] just have to animate it the reason why
[36:35] this video is initially hidden is
[36:37] because we have to apply the animation
[36:38] where we have that zoom in effect as you
[36:41] can see it slowly Zooms in so just below
[36:44] this video player which will have that
[36:46] zoom in effect we can go below and we
[36:49] can create another video player which
[36:51] will have a source equal to get video
[36:54] source and to it we'll check if the
[36:57] current index is triple equal to the
[37:00] total videos minus one that means that
[37:03] we're at the last index and in that case
[37:05] we want to reset it to one else we're
[37:08] going to set it to the current index now
[37:10] we can see that again let's give it a
[37:12] property of autoplay I'll also give it
[37:15] Loop muted and a class name of
[37:20] absolute left- Z top- 0 size- full
[37:27] object - cover and object Das Center and
[37:31] there we go now we're starting to dive
[37:33] into the
[37:34] world and check this out I click it and
[37:37] now it actually
[37:39] plays this is pretty crazy I got to say
[37:43] looking great again we must not forget
[37:47] that this looks even better on desktop
[37:50] and I mean this video on its own is
[37:52] looking amazing these designers and
[37:55] animators have done such a phenomenal
[37:57] job but again keep in mind we will turn
[37:59] this into an actual High performing
[38:02] website as well so for the time being
[38:04] I'll go back to mobile view and I will
[38:06] also give this video an on load a data
[38:09] property to handle video load finally we
[38:12] can go one div below and we can create
[38:14] an H1 with a class name equal to
[38:19] special- font hero dading and we can say
[38:24] something like gaming I think that's
[38:26] what it says right here at the bottom of
[38:28] the original website as well but check
[38:30] this one thing out the a in gaming is
[38:34] special it has this line in
[38:36] between so we can change it by putting
[38:39] it in bold signs like this gaming let's
[38:44] also style it further by giving it a
[38:46] position of
[38:47] absolute bottom of five right of 5 Z of
[38:53] 40 and text- blue of 75 and check this
[38:57] out we have this gaming text right here
[39:00] at the bottom right right below the H1
[39:03] let's create a div and this div will
[39:06] have a class name equal to
[39:11] Absolute left- Z top- Zer Z of 40 and
[39:17] size of full and right now we're
[39:20] creating this top part of the website
[39:22] with a redefined title a subheading and
[39:25] a call to action button so within it
[39:27] let's render another div that's going to
[39:29] have a class name of margin top of 24
[39:34] padding X of five and on small devices
[39:37] padding X of 10 within it we can finally
[39:40] render an
[39:42] H1 that'll say
[39:45] redy and then I'll put the n in the Bold
[39:49] signs and then I'll say e at the
[39:52] end because this will make sure that the
[39:54] end has that special flare so I'll give
[39:57] it a class name equal to special- font
[40:01] hero- heading and text-
[40:06] blue-00 there we go that's much better
[40:09] right below the H1 let's render a P tag
[40:12] that'll have a class name equal to
[40:16] margin bottom of five Max DW of
[40:20] 64 font D Robert D regular and text-
[40:25] bl-100
[40:27] and it can say enter the
[40:31] metagame
[40:33] layer I'll put a break right here
[40:36] because we want to show something in a
[40:37] new line and I'll say unleash the play
[40:42] economy okay that's pretty cool we have
[40:44] some kind of a subheading right there
[40:46] and below it we want to render a button
[40:49] now this button will be a completely
[40:52] custom component which will reuse in
[40:55] many other places within our application
[40:57] so let me actually cover this video for
[40:59] the time being as the video can be a bit
[41:01] distracting while we're coding and let's
[41:03] create a custom button component by
[41:05] going to components and creating a new
[41:08] button. jsx I'll run
[41:12] rafc and I'll import it right here
[41:15] within the hero below the P tag by
[41:18] rendering a new self-closing button
[41:21] component and if I go back here you
[41:23] should be able to see a button for the
[41:25] time being I will stop the video from
[41:27] playing by heading over to videos and
[41:30] remove the autoplay from one of these
[41:32] videos so if I reload it will not
[41:34] autoplay later on we can uncommon this
[41:37] to just be amazed at the great animation
[41:39] for now let's pass some props into this
[41:42] button so we can differentiate it from
[41:44] some other buttons I'll give it an ID of
[41:47] watch- trailer a title of Watch
[41:52] trailer a left icon equal to and now
[41:56] this is the first first time we're ever
[41:57] using icons in this application so we
[42:00] actually want to install a package that
[42:02] allows us to use many different icons
[42:04] and that's of course react icons it
[42:07] allows you to pick any icon Library you
[42:09] want and immediately use icons from it
[42:11] we can install it through mpm by simply
[42:14] saying mpm install react Das ions so
[42:17] this is exactly what I'll do and once it
[42:20] gets installed I'll simply call it TI
[42:24] location Arrow coming from react
[42:28] ions there we go and finally I'll pass
[42:31] some container class to this button of
[42:35] BG yellow 300 Flex Das Center and a gap
[42:40] of one if I do that and go
[42:43] back I can now go into this button
[42:46] accept those props and then create this
[42:49] reusable button component so that we can
[42:51] reuse it across the page to accept the
[42:54] props you can just get the props here
[42:56] and then say something like props do
[43:01] title I think it was that's now going to
[43:03] say Watch trailer what you can also do
[43:06] is destructure the props by
[43:09] destructuring the props you don't have
[43:11] to say props do something every time you
[43:14] just use it like this it still works but
[43:17] it's a bit easier so let's destructure
[43:19] all of the other properties as well such
[43:21] as ID right icon left icon and the
[43:26] container our class once you get them we
[43:28] can start creating our button by first
[43:32] wrapping everything in a button
[43:33] component we can give it an ID equal to
[43:36] ID a class name equal
[43:39] to
[43:41] group
[43:43] relative Z of 10 W of fit cursor of
[43:49] pointer overflow of hidden rounded Das
[43:53] full background of violet
[43:57] 50 padding X of s padding y of three and
[44:03] text-
[44:05] black and it'll render the left icon
[44:08] there we go you can see it right here
[44:10] and we can also make this class name
[44:12] Dynamic by turning it into a dynamic
[44:14] template string just like so and then we
[44:17] can render the container class as well
[44:20] right at the end of the other classes if
[44:22] you do that and continue writing the
[44:24] text it'll also apply these additional
[44:27] class names such as BG yellow 300 Flex
[44:30] Center and a gap of one so let's create
[44:33] a span within this button with a class
[44:36] name equal to relative
[44:39] inline-flex
[44:41] overflow Das hidden font
[44:45] dgeneral text- extra small and
[44:50] uppercase within it we can create a div
[44:54] that'll render the title that says one
[44:57] Watch trailer and right outside of this
[44:59] pan we can render the right icon if
[45:02] there is any this is looking good to me
[45:04] but it looks like the BG yellow 300
[45:07] class name is not actually getting
[45:09] passed container class container class
[45:12] right here hm that's interesting what if
[45:16] I remove this BG Violet will it be
[45:19] passed then oh yeah it is passed so that
[45:22] means that this class for some reason is
[45:24] taking over what we could do is use
[45:28] something known as a clsx which will
[45:30] allow us to more appropriately mix
[45:32] different classes but we could also just
[45:36] add an exclamation mark at the start of
[45:38] this one which will make it more
[45:40] important so this is looking good to me
[45:42] now we can go below that button and
[45:45] Below three more divs 1 2 3 here we're
[45:49] going to put a replica of the H1 that
[45:52] says gaming this one right here so let's
[45:55] copy it paste it right here and instead
[45:58] of text- blue 75 we'll put a text black
[46:03] now why are we doing this right now it
[46:06] seems that it's completely hiding this
[46:08] one right well not really on this one I
[46:10] will remove the z40 because it doesn't
[46:13] have to appear on top it's actually
[46:15] going to appear at the bottom check this
[46:17] out as I'm scrolling see how when the
[46:20] video is moving there's this new gaming
[46:23] that appears below the video I mean this
[46:25] is just amazing
[46:27] so we'll Implement that animation very
[46:30] soon but with that in mind we have a
[46:33] fully functional video player and if you
[46:35] click in the middle sometimes it skips
[46:38] you notice how I clicked but it didn't
[46:40] actually play that video but other times
[46:43] it is working incredibly well especially
[46:45] if I turn on the autoplay so now if I
[46:49] move over and keep clicking it's going
[46:52] to keep switching the videos again one
[46:54] time it doesn't do it but don't worry
[46:56] about that we'll fix that very soon
[46:58] together but for now what do you say
[47:00] that we go ahead and Implement some
[47:03] animations it feels like we don't need
[47:05] them right but check this out animations
[47:07] will be happening on scroll this is
[47:11] pretty crazy like the video shows up as
[47:13] it's a part of the screen and then it
[47:15] animates that's not the only animation
[47:18] we want to add though it's this one that
[47:20] we want to add First Once you click on
[47:23] the video it zooms in and it looks like
[47:26] you're end entering into that different
[47:28] world on our version of the application
[47:30] that's not really happening it just
[47:32] immediately jumps out of course and we
[47:34] have that bug as well so what do you say
[47:37] that we Implement that animation where
[47:39] you slowly dive into that world to
[47:43] implement it I'll scroll up right here
[47:45] and we'll want to start doing the
[47:47] animations but wait how can we actually
[47:50] animate stuff on the web with GP of
[47:52] course a widely robust JavaScript
[47:54] animation Library built for
[47:56] professionals and as you can see they
[47:58] have been a side of the day as well but
[48:00] in this video You're rebuilding a side
[48:02] of the month if I'm not mistaken so gup
[48:05] allows you to effortlessly animate
[48:07] anything JavaScript can touch delivering
[48:10] silky smooth performance and unmatched
[48:12] support I like what they're saying I'm
[48:14] already sold so what do you say that we
[48:17] start adding Gap to our application I'll
[48:20] show you how simple it is to install it
[48:22] we'll just head back to our
[48:24] codebase and run mpm install
[48:27] add Gap SL react and the gsap library
[48:32] itself once you install it you'll be
[48:35] able to use the use Gap hook that looks
[48:38] something like this use gap which you
[48:40] have to import the top from at gsap
[48:43] react to it you have to pass a callback
[48:45] function and then you have to pass some
[48:47] dependencies on when that function will
[48:49] run that has to be done as the second
[48:52] parameter to the function where you can
[48:53] say that it'll be executed whenever the
[48:56] current index changes and we can also
[48:59] add another property called revert on
[49:03] update and set it to true because we
[49:05] want to revert it to the start every
[49:07] time and current index will actually be
[49:09] set to dependencies like this there we
[49:12] go so now we can start defining the
[49:14] function so we can say if has clicked
[49:18] that means that we have entered this new
[49:20] world and if that is the case we can
[49:24] call the Gap which is the base Library
[49:27] which you have to import from Gap dot
[49:30] set and as the first parameter to the
[49:32] set you pass the ID or the identifier to
[49:36] the element which you want to animate so
[49:38] we can say animate the next
[49:40] video by setting the visibility to
[49:44] visible next we also want to set gap.
[49:48] 2 next- video so we're animating the
[49:52] next video to the following set of
[49:55] animations also called
[49:57] twins we can set the
[50:00] transform origin to be equal to Center
[50:04] Center we can give it a scale of
[50:07] one a width of 100% a height of 100% as
[50:14] well duration of one is
[50:18] of power 1 do
[50:21] inout and on start we want to call a
[50:25] callback function that we set the next
[50:27] video ref do
[50:29] current. playay so it'll actually play
[50:32] the next video we also want to animate
[50:35] from so right below we can say
[50:38] gap. from current
[50:41] video so what are we going to animate
[50:43] that well we can give it a transform
[50:46] origin of Center Center as well with a
[50:50] scale of
[50:52] zero a duration of
[50:55] 1.5 and and the ease of power one. inout
[51:01] I found this one to work the best and
[51:03] since we're inside of an object here you
[51:05] have to close it with a comma not a
[51:07] semicolon if I do this and reload and
[51:10] press right here you'll notice that
[51:12] something seems to have
[51:14] broken why is that well it says Gap is
[51:18] not defined so let's make sure to import
[51:21] Gap from The Gap library at the top by
[51:25] saying import gsap app from
[51:28] gsap that's going to look something like
[51:30] this now if you go back click and then
[51:34] click again you'll start noticing the
[51:36] animation up here and this time it
[51:39] actually fixed the error that we had
[51:42] it's animating you see now we are in
[51:44] this world if I click on this boy now we
[51:47] can see the boy it animates and here we
[51:50] have this woman walking if I click it we
[51:52] can see it right
[51:54] here so this is a beautiful animation
[51:57] that I'm so glad to see in action but
[52:00] now we have just this single hero
[52:03] section and I mean just ending the video
[52:05] right here and calling it a day would be
[52:08] I think already pretty good right if so
[52:10] drop a like and leave a comment down
[52:12] below as well but of course we want to
[52:15] take it a step further and replicate a
[52:17] couple more sections such as when you
[52:19] scroll down we actually want to show
[52:21] this gaming text in this very cool way
[52:24] and this video will actually collapse
[52:26] into some kind of a rectangle right here
[52:29] at the top as you can see pretty cool
[52:32] effect so I'll teach you how to
[52:33] replicate that as well so to achieve
[52:36] that let's add another use Gap hook
[52:39] where we have a callback function and
[52:41] within this one we don't have to add the
[52:43] dependencies I can just call gap. set
[52:47] and we're going to set a video frame to
[52:50] a specific clip path now bear with me
[52:53] this is going to be pretty cool you see
[52:55] the clip path in this final application
[52:57] you see how it's some kind of a
[52:59] rectangle right here well you can
[53:01] generate your own clip path by using
[53:03] this CSS clip path maker I think using a
[53:06] trapezoid might make sense but you can
[53:08] choose whatever shape you like and then
[53:11] you can simply copy this clip path code
[53:14] go back and add it right here clip path
[53:18] is going to be equal to in this case a
[53:21] string of polygon with these specific
[53:24] values and check this out even though we
[53:26] didn't get scroll we have this
[53:29] effect you can try playing with
[53:31] percentages a bit I found 14 to work
[53:34] very nice and then zero and then we can
[53:36] have something like
[53:38] 72 and maybe we can have a bit less on
[53:41] the bottom as well like 90 and then 90
[53:45] here as well there we go I think this is
[53:47] looking pretty cool now this bottom text
[53:49] is actually visible but now we only want
[53:51] to apply this on scroll so let's
[53:54] actually give it a border radius to to
[53:56] round the borders a bit of 0 0 40% 10%
[54:02] there we go this is giving it a pretty
[54:03] cool effect and now I'm going to animate
[54:06] the Gap from so this is the starting
[54:09] animation from where we want to start
[54:12] it's going to be the same video frame
[54:14] element and we want to start from a clip
[54:19] path that is actually a full polygon so
[54:22] we don't have any cut Corners yet so to
[54:26] achieve that you can just copy this
[54:28] polygon paste it here change the first
[54:32] percentage to
[54:34] zero and change all of the other ones to
[54:37] 100 at least the ones that have some
[54:39] values this will actually turn it into a
[54:42] square or a rectangle now we can also
[54:45] reset the Border radius right here by
[54:48] setting it to four zeros we can give it
[54:51] an ease of power one do in
[54:57] out and we can also give it some kind of
[54:59] a scroll trigger to know when the
[55:01] animation should happen so we can say
[55:03] scroll
[55:04] trigger is going to be equal to an
[55:08] object where the trigger is the video
[55:11] frame the start is the center Center the
[55:16] end is the bottom center and the scrub
[55:22] will be set to true so it will animate
[55:24] as we scroll through it or scrub Dr
[55:26] through it now you can notice at the
[55:28] start if you reload it kind of goes from
[55:30] this full screen to this smaller
[55:34] rectangle but of course we want to
[55:36] implement that on scroll so how can we
[55:38] actually mock that well if I head over
[55:40] to the app below the hero let's try to
[55:44] add a section a self-closing section
[55:47] with a class name of z0 Min AG screen
[55:52] and a BG blue 500 if I save this and go
[55:56] back we're going to get a full blue
[55:58] screen which kind of allows us to scroll
[56:01] to test our animation so far it seems
[56:04] that the animation isn't actually
[56:06] animating so let's see what else do we
[56:08] have to do to make it happen first of
[56:10] all I noticed that we didn't yet put our
[56:11] loading or loaded videos to use
[56:14] sometimes it might take a bit longer so
[56:16] it's always good to handle that at the
[56:17] start just so we don't forget so I'll go
[56:20] to the top of our jsx
[56:23] part and right here above the video
[56:26] frame I'll say if loading is true so if
[56:31] is loading is true in that case we can
[56:34] render a
[56:36] div this div will actually be a loader
[56:39] div So within it I will render another
[56:42] div with a class name equal to three
[56:46] body you'll see soon enough why we're
[56:48] calling it that way it's going to be
[56:50] three little dots that are spinning
[56:51] around each other and I can also create
[56:54] three divs with a class name equal to 3
[56:59] bodycore
[57:01] Dot and duplicate them two more times if
[57:05] I do that and turn the loading to True
[57:08] right here by default which it is we can
[57:11] see the loading right here at the top
[57:13] left corner but of course we want to be
[57:15] able to position it a bit better so
[57:17] let's give this outside div a class name
[57:21] equal to flex Das Center
[57:24] absolute Z of one 100 h of
[57:28] dvh w
[57:31] screen overflow Das hidden and BG Violet
[57:36] all 50 if I save this now we have a nice
[57:39] looking loading which actually takes
[57:40] over the entire screen until our videos
[57:44] load but how are we going to know if
[57:47] they have loaded successfully well we
[57:49] can create a use effect so right here
[57:52] above this use Gap I'll create a use
[57:54] effect where I'm going to check for the
[57:57] dependencies of loaded videos so
[58:00] whenever loaded videos change we can
[58:02] then recall this use effect and check if
[58:05] loaded videos is triple equal to Total
[58:08] videos minus one then we can set is
[58:11] loading to false and of course use
[58:14] effect has to be imported from react so
[58:16] this is the third react hook that we're
[58:18] using in this hero section so now if you
[58:20] reload you'll see the loading for a
[58:22] second but then immediately the video
[58:24] will appear oh but I just remembered you
[58:26] know why our animation is being
[58:28] triggered immediately and not on scroll
[58:30] scroll trigger is actually a plugin
[58:33] within gsap so you have to enable it
[58:35] right at the top to be able to use it
[58:38] you do that by saying
[58:39] gap. register plugin and specifically
[58:43] we'll use the scroll trigger plugin this
[58:47] scroll trigger is going to come from
[58:50] import scroll trigger from Gap SL all
[58:55] there we go now if we save it we have a
[58:58] full screen video which is looking
[59:00] amazing and if you scroll down check
[59:02] this out we're actually animating it
[59:05] again you don't really notice it because
[59:07] you're already all the way down once it
[59:09] happens but still it is there right
[59:12] these animations or micro animations
[59:14] don't have to be big but once you see
[59:16] them in action they really change the
[59:18] way that you experience this website and
[59:21] in this case it's still super super
[59:23] optimized so this is is looking great
[59:27] and gets a big pass from my side and
[59:29] with that I think we're more or less
[59:31] done with the hero section which is
[59:32] looking amazing we have the text on top
[59:35] left and bottom right just to make some
[59:37] space for the video that's appearing in
[59:38] the middle and for users to discover the
[59:42] ability to enter into the world of a
[59:44] different video so we have this one and
[59:48] this one as if there are three different
[59:50] stories oh but wait it seems like we
[59:53] currently only have two do I have to
[59:55] update the total videos to four 1 2 3
[59:58] there we go yeah that's it we had to
[60:00] have four to actually show all three
[60:02] videos this is looking amazing now what
[60:06] do you want to do next I'm asking as if
[60:08] I can hear you or as if you can tell me
[60:10] what to do next but we have two options
[60:12] we can either design the Navar which is
[60:15] looking pretty simple at the start but
[60:17] then actually disappears and then
[60:19] reappears once you scroll up because it
[60:21] means you're lost and you want to find
[60:23] something so it's pretty cool or the
[60:26] next section you want to do is this one
[60:27] a piece of text and an image that
[60:30] animates into a third section to be
[60:33] completely honest I would wait on the
[60:34] Navar just a tiny bit more to implement
[60:37] this second very interesting
[60:41] section this is technically an about
[60:45] section typically about sections on
[60:47] different websites look boring but here
[60:49] hey we're diving into a whole another
[60:52] world so we can start implementing it by
[60:55] creating a new component in the
[60:57] components folder and let's call it
[60:59] about. jsx run rafc right within it and
[61:05] then import it and use it right here
[61:07] instead of this blue section we will no
[61:10] longer need it because now we will have
[61:13] our about
[61:14] section if you add
[61:16] it and go back for now you will just see
[61:19] a simple about text right here but we
[61:22] will turn it into the whole about
[61:24] section so let's start start with the
[61:26] jsx part first and then we'll focus on
[61:28] the animations let's give it an ID equal
[61:30] to about just so we can scroll to it and
[61:33] animate it as well as a class name equal
[61:36] to Min dh- screen and w- screen so it
[61:40] takes the full height and width if we do
[61:42] that you can now see that all of this
[61:44] black space is our about screen and for
[61:47] the time being I will put it to mobile
[61:49] view just so we can see what's happening
[61:51] within this div I'll create another div
[61:54] that'll have a class last name equal to
[61:58] relative margin bottom of eight margin
[62:01] top of
[62:02] 36 Flex
[62:05] flex-all items D Center and a gap of
[62:09] five within it I'll render an H2 and
[62:12] give it a class name equal to font dgen
[62:17] text
[62:18] DSM uppercase and on medium devices
[62:22] text- 10 pixels so now inside of there
[62:25] we can say welcome to zentry there we go
[62:29] that's looking cool right below this H2
[62:31] we'll render a div with a class name
[62:35] equal to margin top of five to divide it
[62:38] a bit from the top text Dash Center to
[62:41] center it text das4 Excel so it's going
[62:44] to be super large uppercase leading Dash
[62:51] 0.8 like this and on medum devices text
[62:55] Dash six Ram within it we can render a
[62:58] piece of text such as discover the
[63:03] world's largest shared Adventure there
[63:07] we go this is looking pretty amazing but
[63:09] if we go into the finished website and
[63:12] if you zoom in you'll notice that the O
[63:14] here and a couple of other letters like
[63:16] the a have that special character design
[63:19] so we have to wrap them in Bold
[63:21] characters I'll do that with this o
[63:23] right here so that's going to be B for
[63:25] both
[63:26] same thing here and we'll do that with
[63:28] the a right here near the end under
[63:30] largest there we go this is looking good
[63:33] and let's also add a Break Tag after
[63:36] worlds so we put that in a new line
[63:38] there we go for now it's looking like
[63:41] this but trust me soon enough it will
[63:42] look much different below this div I'll
[63:45] create another div with a class name
[63:49] equal to about Das subtext that'll
[63:53] render the P tag and say the Game of
[63:57] Games begins that sounds exciting and
[64:00] then we can say your life now an epic
[64:04] MMO RPG this zentry game really sounds
[64:07] amazing I might even give it a try after
[64:09] we code this website out and I'll leave
[64:11] the link in the description anyway to
[64:13] credit them for such an amazing design
[64:15] and development of this app right below
[64:17] it let's create another P tag this P tag
[64:20] will say something like
[64:22] zentry unites every player from
[64:26] countless games and platforms I think
[64:30] this is going to be good and now we can
[64:31] see that text right here let's go a bit
[64:33] down so that's going to be two divs down
[64:36] and create another div that'll have a
[64:39] class name equal to h- dvh and w- screen
[64:45] as well as an ID equal to
[64:47] clip within it we can create another div
[64:51] with a class name equal to mask dclip
[64:55] Dash path and it's going to have a class
[64:58] name of about image within which we can
[65:01] render a self-closing image tag with a
[65:04] source of IMG
[65:07] slab. webp it's going to have an ALT tag
[65:11] of
[65:12] background as well as a class name equal
[65:15] to Absolute left- Z top- Z size- full
[65:22] and object D cover now you cannot see it
[65:26] just yet and that's because we have to
[65:27] animate it so I'll scroll up a
[65:30] bit and use the used gep
[65:34] hook we'll have a function right here a
[65:37] callback function and within it I'll say
[65:40] ca clip animation is equal to gap.
[65:45] timeline so this is the first time we're
[65:47] creating a timeline which allows us to
[65:49] more precisely create a trigger a start
[65:52] and an end we're going to work with
[65:53] triggers right here as you already know
[65:55] no so we can do a scroll
[65:58] trigger and we're going to trigger it
[66:01] once a user reaches a clip which is
[66:04] going to be this part of the page here
[66:07] once it reaches that part we can Define
[66:09] the start of the trigger which is going
[66:12] to be Center Center we can also Define
[66:15] the end which is going to be this is
[66:17] pretty interesting so pay attention plus
[66:20] equal to
[66:22] 800 and Center so it'll trigger 800
[66:25] pixels after it passes the center we can
[66:28] also do a scrub of 0.5 and scrub simply
[66:31] refers to how we're moving through the
[66:33] animation on scroll we can also do a PIN
[66:37] to true and pin spacing to true as well
[66:40] and if you want to learn more about any
[66:42] of these properties just go to gsap and
[66:45] maybe search for pin or pin spacing if
[66:47] you do that and go to the docs of the
[66:50] scroll trigger animation and search for
[66:52] pin or pin spacing you can immediately
[66:56] see what it does now with that said
[66:58] let's try to apply this
[67:01] animation by going a bit down and saying
[67:04] Clip animation. 2 mask clip path and
[67:10] we're going to give it a
[67:11] width of about 100
[67:14] VW a height of about 100 VH and a border
[67:20] radius of zero what is this Mass clip
[67:23] path well I think we have it right right
[67:25] here see Mass clip
[67:28] path so this will actually show that
[67:30] image that I was telling you about now
[67:32] of course we have to import use Gap and
[67:35] we also have to import the gsap library
[67:37] Itself by saying import Gap from
[67:41] Gap and don't forget we also have to
[67:44] turn on or register the plugin for
[67:47] scrolling so we need to say
[67:50] import scroll trigger coming from Gap
[67:55] all and then we can say
[67:57] gap. register plugin of scroll trigger
[68:01] now we're back in action and if you
[68:03] scroll check this out we have discovered
[68:05] the world's largest shared adventure and
[68:07] if I scroll the image actually does
[68:10] something like an animates to the bottom
[68:13] this is pretty cool not yet what we want
[68:16] but we're getting there and how does it
[68:18] look like on
[68:19] desktop oh oh it's kind of jumping
[68:22] around as you can see we'll definitely
[68:24] fix that oh oh no I reloaded and now
[68:27] it's better so you can see how it goes
[68:30] right here and then it
[68:32] expands I'm noticing some characters
[68:35] right here VH so it means that I didn't
[68:38] properly write the style somewhere oh
[68:40] here it is looks like I took it out of
[68:43] the class name it was supposed to be h
[68:46] dvh w screen so now it's a bit better so
[68:49] now you can see how first it looks like
[68:51] this and then as you scroll down it
[68:54] actually expands to the full width now
[68:56] even though this is looking great for
[68:58] the about section we have to do
[69:00] something about this piece of text it
[69:02] definitely doesn't look like this and
[69:04] the text itself in some cases can be
[69:06] animated now it's not in this section
[69:08] but later on we're using similar pieces
[69:10] of text and we'll be able to animate
[69:13] what it does as you can see here so it's
[69:15] better to turn it into a reusable
[69:17] component immediately so we can then
[69:19] animate it as you can see here and reuse
[69:22] it across other sections so let me
[69:24] collapse this head over to our working
[69:26] version of the application which doesn't
[69:28] look that good and we can create a new
[69:30] component called animated
[69:33] title. jsx run
[69:36] RFC and we can import it right here
[69:40] where we have this div so I'll import
[69:43] the animated title and for the time
[69:47] being I will copy this div and put it
[69:49] into the animated title so far it might
[69:52] look like the same thing with some extra
[69:54] steps but trust me will soon turn this
[69:56] into a properly animated title which
[69:59] we'll be able to reuse across many
[70:01] different sections so let's do that
[70:05] next to get started creating our custom
[70:08] animated title let's actually expand on
[70:11] this div let's first make it Dynamic and
[70:13] reusable through props to these props we
[70:16] can pass the title and the container
[70:19] class so now you can take this discover
[70:23] the world's largest shared Adventure
[70:25] copy it and we'll pass it into the
[70:27] animated title as a title string that's
[70:31] going to look something like this and we
[70:33] can do the same thing with the container
[70:34] class by saying container class is equal
[70:37] to margin top of
[70:40] five and exclamation mark text- black
[70:45] and text- center now if you head into
[70:48] the animated title instead of rendering
[70:50] the text right here we can say title.
[70:53] spit and we're going to split it based
[70:55] on the Break Tag to create some space
[70:58] that's going to look like this and then
[71:00] we can map over all of these pieces of
[71:02] the title by getting each individual
[71:05] line in the index of that
[71:07] line for each line I will return another
[71:11] div and this div of course we have to
[71:14] close it I'll give it a key equal to
[71:16] index since we're mapping over it and a
[71:20] class name equal to flex Das Center Max
[71:25] w- full flex-wrap gap of two padding X
[71:31] of 10 and then medium devices a gap of
[71:35] three within it we can simply render the
[71:39] line but I'll also split it by spaces so
[71:43] I'll say
[71:44] line.it based on Spaces like this and of
[71:49] course let's make sure to properly close
[71:51] it right here there we
[71:53] go once we split we're going to get each
[71:56] individual word so we can say map word
[72:00] and the index we can call it just I and
[72:03] we're going to map over each word itself
[72:05] by giving it a
[72:07] span with a key equal to
[72:10] I a class name equal to animated word
[72:15] and we're going to call a dangerously
[72:17] set inner HTML where we're going to set
[72:20] thecore HTML variable which is going to
[72:22] be underscore uncore HTML to be equal to
[72:25] the contents of that word and we can
[72:27] make this span self closing I know this
[72:30] might be a bit weird right now but
[72:32] you'll see how great it looks when you
[72:34] can animate each word on its own you can
[72:36] see it right here so for now it looks
[72:39] like I didn't properly close all those
[72:41] divs so I have to end and close right
[72:44] here there we go we're good I will
[72:47] indent this a bit more so we can see it
[72:49] better and now we should be able to see
[72:50] some kind of a title right here at least
[72:52] we will when we add a container class to
[72:55] this class name so let's actually fix
[72:57] these class names by giving it a class
[73:00] name of animated Das
[73:02] tile and we can also render a dynamic
[73:07] container class like this but of course
[73:10] to do that we have to wrap it in a
[73:12] template string so that's going to look
[73:14] something like this if I do that we
[73:16] cannot see the title just yet and now we
[73:18] have to actually animate it so scroll a
[73:21] bit up and create a new ref const
[73:24] container ref is equal to use ref coming
[73:28] from react and at the start it'll be set
[73:31] to null once we have this ref we can
[73:34] actually attach it to this container div
[73:36] by saying ref is equal to container ref
[73:40] and this will now allow us to start
[73:42] animating it so let's create a new use
[73:45] effect hook which allows us to perform
[73:48] some actions whenever things on the page
[73:50] change specifically in this case we want
[73:53] to make it happen initially as soon as
[73:56] the page loads not on any kind of
[73:58] changes which is why we'll leave the
[74:00] dependency array empty within here we
[74:03] can define a gep context to ensure the
[74:06] animations and selectors are scoped to
[74:08] this instance of a component so let's
[74:11] say const CTX short for context is equal
[74:15] to
[74:16] gap. context and we can Define it within
[74:19] a callback function and then as the
[74:21] second parameter we can pass the ref in
[74:24] this case it's going to be container ref
[74:26] now we first have to import Gap from
[74:29] gsap so let me say import Gap from
[74:33] gsap there we go and now we can start
[74:35] creating some animations and timelines
[74:37] of animations within this context by
[74:40] saying const title animation is equal to
[74:45] gap. timeline so we're creating a new
[74:48] timeline with a scroll trigger as before
[74:52] the trigger will happen once once we
[74:55] reach a container ref. current and it'll
[74:59] start on 100 pixels and the bottom of
[75:02] that
[75:03] container and it'll end in the center of
[75:07] that container and the bottom of that
[75:10] container when it comes to top and
[75:12] bottom finally we can toggle some
[75:14] actions such as play none none reverse
[75:18] you can look into these actions and of
[75:20] course this is something we can look
[75:21] into by Gap docs so if you head over to
[75:24] toggle actions Gap scroll trigger and
[75:28] then search for toggle actions you can
[75:30] see that it says if you want an
[75:31] animation only to play once when
[75:33] scrolling forward and never get reset or
[75:36] replayed then you can set it to once but
[75:39] you can also set toggle actions to play
[75:42] none none none in this case we have play
[75:45] none none reverse but it approaches a
[75:47] very similar thing and there we go here
[75:49] it says toggle actions control four
[75:51] distinct toggle places on enter on leave
[75:54] on enter back and on leave back in that
[75:57] order so in this case we say on enter
[76:00] play on leave none on enter back none
[76:04] but on leave back reverse the animation
[76:06] you'll see what cool effect this will
[76:08] give us with that in mind let's animate
[76:11] the title Now by saying title animation
[76:14] do2 do animated word so we're going to
[76:18] animate to this class by setting the
[76:20] opacity to one by setting the transform
[76:25] to translate 3D 0 0 0 rotate y to 0
[76:32] degree as well as rotate X to 0 degre as
[76:37] well so we're kind of resetting the
[76:39] animation right here we can also put an
[76:41] ease of power two. inout and a stagger
[76:46] of 0.02 in between the different words
[76:50] and finally since we're within a use
[76:51] effect at the end we have to clean that
[76:54] use effect up by creating a new callback
[76:57] function where we say context CTX do
[77:00] revert which will clean it up on
[77:03] unmounting of this component now if you
[77:05] scroll down you can see something
[77:08] appearing right here but it's not really
[77:10] in position it's not really in place
[77:12] same thing if we go here this isn't
[77:15] really looking good is it let's try to
[77:16] fix it together if I head over here I
[77:20] think my rotation X is not getting
[77:21] applied or the transform for that matter
[77:24] because I have this comma here we should
[77:26] just have an empty space in between all
[77:28] of these properties so if we do that you
[77:30] can now see discover the the let's fix
[77:33] that double d right here I think it's
[77:35] going to be in the about there we go
[77:39] discover the world's largest shared
[77:42] Adventure this is much better and check
[77:44] this out if I scroll down it will slowly
[77:48] start animating and again take a look
[77:51] it's animating as you're barely seeing
[77:54] it so it's it's not the goal that you're
[77:55] seeing the white screen while it's
[77:56] animating immediately you're here and it
[77:59] appears and shows up for you so you
[78:01] don't have to wait at all but you still
[78:03] see it and then as we scroll back it is
[78:05] still here this is great so now we have
[78:08] an animated title right here and then we
[78:11] scroll down and enter a new
[78:13] world perfect with that in mind you have
[78:16] developed the animated title so let's go
[78:19] back the about and with it I think the
[78:22] about section is now done before we
[78:24] continue with the upcoming sections I
[78:26] think it's about damn time that we
[78:28] implement the navigation bar right now
[78:30] it's looking a bit empty right here and
[78:32] we don't have the ability to quickly
[78:34] scroll to another section on the page
[78:36] which is always welcomed so let's head
[78:38] back to the app open up the components
[78:41] folder and create a new file called
[78:44] navbar jsx run
[78:47] RFC and then import it right here above
[78:50] the hero section by calling a
[78:53] self-closing NV bar functional component
[78:56] you should be able to see it right here
[78:58] at the top which means that we are ready
[79:00] to start implementing
[79:03] it let's get started with implementing
[79:06] our navbar to do that I'll put my
[79:08] browser to the left side and my code
[79:10] Editor to the right that way we can
[79:12] better see what's happening here and
[79:14] I'll also head over to our home and stop
[79:17] the autoplay of the
[79:19] video just so we don't have to see it
[79:21] repeat every time and then I'll reload
[79:24] great this is better we can turn it back
[79:27] on later on and just so we can see the
[79:29] nav links because they're going to be
[79:30] white for the time being I will just add
[79:33] a background color to our main BG zinc
[79:37] of 600 it's a darkish color that will
[79:40] allow us to see our Navar elements great
[79:44] so with that said let's get started with
[79:46] creating it first things first I'll wrap
[79:49] everything in a div component and this
[79:51] div will actually later on be animated
[79:53] so I will immediately create a ref for
[79:55] it by saying const nav container ref is
[80:00] equal to use ref at the start equal to
[80:03] null and of course we'll have to import
[80:05] it from
[80:06] react by saying use
[80:09] ref now we can give it that ref by
[80:12] saying nav container ref as well as we
[80:15] can start giving it some class names in
[80:18] this case let's give it a fixed because
[80:20] it'll be fixed to the top inser X of
[80:23] zero
[80:25] top of four Z of 50 so it appears above
[80:29] other elements h of 16 for the height
[80:33] border - none transition Das all
[80:37] duration of 700 for the animation and
[80:40] then small devices ins set of X of
[80:45] six now you cannot see it just yet
[80:47] because we have nothing in it but within
[80:49] there we can add a header component this
[80:53] header will have a class name equal to
[80:57] Absolute top-1 /2 this will give it a
[81:01] top 50% W full for full width and minus
[81:07] translate
[81:08] dy-1
[81:10] /2 within it we can develop a nav
[81:14] element this nav will have a class name
[81:19] equal to flex size- full items D Center
[81:24] justify Dash between so they show on the
[81:26] left and the right side and a padding of
[81:29] four and within it we can start creating
[81:32] the left side of our navbar where we're
[81:34] going to have our logo and the product
[81:36] button so let's create a div with a
[81:39] class name of flex items Das Center and
[81:44] a gap of seven and right within it I'll
[81:47] create an image with a source equal to/
[81:51] IMG SL logo.png
[81:55] with an Al tag of logo and a class name
[81:58] of
[81:59] W10 and now we can see the little logo
[82:02] on the top left right below it we can
[82:04] also render a button coming from our
[82:08] reusable components it'll be a
[82:11] self-closing button component to which
[82:14] we can pass a couple of props such as
[82:16] the ID of a product button a title equal
[82:20] to products right icon in this case will
[82:24] be TI location Arrow so it can be a
[82:29] self-closing component there we go and
[82:32] we can also pass some container classes
[82:35] such as container class is equal to BG
[82:40] blue of 50 that's going to change its
[82:44] color next we can do on medium devices
[82:47] Flex so it nicely looks like this
[82:50] typically it's going to be hidden items
[82:53] Das Center justify Dash Center and a gap
[82:57] of one in between the elements and this
[82:59] is going to make it look very nice now
[83:02] we're moving to the right side of the
[83:04] nav bar so below this div where we're
[83:07] going to have another div for the
[83:08] navigation links and the audio button
[83:12] yep we'll be able to play music within
[83:14] our page we can give this div a class
[83:16] name of flex age- fo and items Das
[83:21] Center and within it we can create
[83:23] another div
[83:25] and this div will typically be hidden on
[83:27] smaller devices so we can give it a
[83:30] class name of hidden but on medium
[83:33] devices it'll be block meaning visible
[83:36] on medium and larger within it we can
[83:39] map over our nav items what you could do
[83:42] is just declare an array of different
[83:44] objects uh with title home link but you
[83:47] can see that this can start getting
[83:48] messy very soon so instead of doing that
[83:51] we can Define our nav items just at the
[83:53] top by saying const nav items is equal
[83:58] to and then here you can have home about
[84:00] Services product and so on but in the
[84:03] case of our great gaming application we
[84:06] can have something like Nexus or we can
[84:09] have Volt or we can have prologue and
[84:12] finally we have the about as well as the
[84:15] contact these are some different items
[84:18] again feel free to change them as you
[84:20] will now if we go down we can say nav
[84:23] items do map where we map over each
[84:27] individual item and we can automatically
[84:29] return an anchor tag for each one make
[84:32] sure to put just a regular parenthesis
[84:34] here and not a curly brace because we're
[84:36] doing an automatic return now within
[84:38] this anchor tag we can simply render an
[84:41] item if you do that you can see those
[84:43] different items appear right here and on
[84:46] small devices they completely disappear
[84:48] but on medium we can see them now let's
[84:51] style this anchor tag by giving it a
[84:54] class name of nav hover
[84:58] BTN just like so and now as you hover it
[85:02] we have this little effect happening
[85:04] right here if you want to check this out
[85:06] in action you can search it and then
[85:09] check it out within index.css
[85:12] basically we're applying a margin inline
[85:15] start of 2.5 R so it basically has
[85:18] enough space in between other elements
[85:20] we're changing the text to small to
[85:22] uppercase to changing the the text color
[85:25] and then what we're doing is applying
[85:28] the Border bottom and then we're
[85:30] animating it by a couple of pixels and
[85:33] changing its color so if you check this
[85:35] out you can see that this border
[85:37] animates I think I found this little
[85:39] animation in the web and then I just put
[85:41] it here you can find many of these
[85:43] animations on the web you don't
[85:46] necessarily have to code everything
[85:48] sometimes it's good not to reinvent the
[85:49] wheel and basically grab these cool
[85:52] little animations whenever you can with
[85:53] that in mind mind we also need to give
[85:55] each anchor tag a key in this case it'll
[85:58] be equal to item because each item is
[86:00] different and finally an ATF 2 ATF will
[86:04] point to
[86:06] Hash item. to lower case like this so if
[86:11] you click Nexus It'll point to Nexus
[86:13] volt prologue and so on you can see
[86:16] about already works it points us to the
[86:18] about section this is great now I think
[86:21] I can remove the background color from
[86:23] the app because it's no longer needed
[86:26] there we go so if I go here and click
[86:28] about it nicely Scrolls to about now
[86:31] with that in mind we can go back to the
[86:34] nav and we can scroll a bit down below
[86:37] this div that's wrapping the navigation
[86:39] items but still within this St and there
[86:42] we can create a button that allows us to
[86:44] play the audio yep you will be able to
[86:47] play some music believe it or not so
[86:49] I'll create a new button this time we'll
[86:52] just use a regular button and I'll give
[86:54] it a class name equal to margin left of
[86:58] 10 to divide it a bit from the nav items
[87:01] Flex items Das Center and a space X of
[87:06] 0.5 to just give it a bit of extra space
[87:09] now we need to create a new function
[87:11] that will allow us to play music so
[87:14] let's create it by saying const toggle
[87:17] audio
[87:19] indicator and that's going to be equal
[87:21] to an arrow function and we can also
[87:25] create a new ref that will allow us to
[87:26] attach audio to this element by saying
[87:29] const audio element ref is equal to use
[87:35] ref and the start set to null make sure
[87:38] to call it audio element
[87:39] ref there we go now if I scroll down to
[87:43] this button we can give it an onclick
[87:47] equal to toggle audio indicator and
[87:51] within it I will render the audio
[87:53] element El I'll give it a ref equal to
[87:57] audio element ref a class name of hidden
[88:01] typically with a source equal to SL
[88:05] audio SL loop. MP3 so this is an MP3
[88:10] file that I provided for you in the
[88:11] source and then we can give it a loop
[88:14] property which will Loop the audio once
[88:16] it finishes playing and now this is a
[88:18] pretty cool feature while it is playing
[88:20] we also want to show some audio lines
[88:23] move up and down down to indicate that
[88:25] the audio is playing and that we can
[88:27] stop it so you can achieve that by
[88:30] mapping over one 2 3 4 these are just
[88:34] numbers but they will act as our line
[88:36] bars and then we can say do map over
[88:39] each individual bar and for each bar we
[88:42] will return a div this div will have a
[88:46] key equal to bar and it'll also have a
[88:49] class name equal to indicator Das line
[88:53] and then we can also give it another
[88:55] class which is going to be dynamic so I
[88:57] have to turn this into a template string
[88:59] and we'll have to check whether the
[89:00] audio is playing so for that we can
[89:03] create a new use State at the top by
[89:06] saying const is audio playing set is
[89:12] audio playing and that's going to be
[89:14] equal to the use State element at the
[89:17] start set to false of course we have to
[89:20] import the use state right here from
[89:23] react
[89:25] once you do that based on this is audio
[89:27] playing we can also Define another use
[89:30] State and that'll be is indicator active
[89:33] so we can say is indicator active and
[89:37] set is indicator active at the start set
[89:39] to false so now if we scroll down right
[89:43] here I can check if is indicator active
[89:47] then we will apply an active class else
[89:50] we will apply just an empty string now
[89:52] you cannot see it yet as we're not yet
[89:54] playing music but we'll do that soon and
[89:57] we can also give this div which is by
[89:59] the way a self-closing div because we
[90:01] won't put anything in it it's just going
[90:02] to be a line we can give it a style
[90:05] property where we can define an
[90:07] animation delay and say the delay will
[90:10] be dependent on the bar we're on so if
[90:13] we're on the first bar we want to
[90:14] multiply that by 0.1 seconds for the
[90:18] second bar it's going to be 0.2 seconds
[90:21] and so on hopefully this makes sense
[90:23] you'll see in action very very soon and
[90:25] I think this is a good chance to put our
[90:27] Editor to the left side and the browser
[90:29] to the right so we can see what's
[90:31] happening now we can scroll up and we
[90:33] can implement the logic for playing the
[90:35] music we have all the states and all the
[90:37] necessary refs and functions to be able
[90:39] to play it first things first in the
[90:41] toggle audio indicator I will set is
[90:44] audio
[90:45] playing to be equal to a previous
[90:48] version of that state and which is going
[90:50] to toggle it off or on so if the
[90:52] previously it has been set to true now
[90:54] we're going to set it to false and I
[90:56] want to do the same thing with is
[90:58] indicator active so set is indicator
[91:02] active is going to be the previous
[91:03] version of that specific State now that
[91:06] we have that we can create a use effect
[91:09] as you know to use effect you have to
[91:11] pass a callback function and a
[91:13] dependency array and we want to recall
[91:15] it every time that the is audio playing
[91:18] variable changes so let's say if is
[91:22] audio playing is true then we can set
[91:25] the audio element ref. current. playay
[91:30] and else if it's not true we can set it
[91:33] to
[91:34] pause great but now how can we actually
[91:37] toggle the music on like there's no
[91:39] button that we see well if you scroll
[91:42] down right here you can see that we are
[91:44] hiding the audio field and typically we
[91:47] have to hide it because it looks very
[91:48] bad we don't want that MP3 bar to show
[91:51] right here we just want some very nice
[91:54] song indicators so to achieve that we
[91:56] can actually close the audio property
[91:59] right here and then show these
[92:01] indicators after the audio prop so
[92:04] they're completely divided first we have
[92:06] this and then we have the indicators
[92:08] which act as the button to play it now
[92:11] on the top right you should be able to
[92:12] see these four different line indicators
[92:16] I think I can zoom it in a bit more
[92:18] there we go so you can see it right here
[92:20] and now if you click it they should
[92:22] start playing theic music there we go I
[92:25] can hear it in my headphones the
[92:27] recording is not picking it up which is
[92:29] totally fine but it should start playing
[92:31] for you as well we have some very
[92:33] uplifting music right here and if you
[92:36] click it it stops I just found a
[92:39] copyright free music which I thought
[92:41] would work very well but of course you
[92:43] can put any kind of MP3 right here that
[92:45] you want in public audio loop. MP3
[92:49] that's it super simple and then the
[92:52] music plays and these four different
[92:55] lines Jump Around very nicely beautiful
[92:59] so with that in mind I'll zoom out I'll
[93:01] check how it looks on mobile currently
[93:04] we're hiding all the elements and we're
[93:06] just letting the users enjoy the actual
[93:08] website on mobile but on desktop we have
[93:11] a top knv but now what's happening if I
[93:13] scroll down but as you can notice some
[93:15] of our background sections are
[93:17] completely white which means that the
[93:18] elements get lost right here which is
[93:21] exactly why we'll actually turn it into
[93:24] a black rectangle that appears when you
[93:26] scroll basically what we do is this if
[93:29] you scroll down the now is going to be
[93:32] hidden but then let's say you're
[93:34] scrolling you're enjoying the website
[93:35] right but then you start scrolling back
[93:38] that typically means that the user is
[93:40] lost and that he's trying to find
[93:42] something when you start scrolling back
[93:45] the Navar will slowly appear in its
[93:47] black form and then it will allow you to
[93:51] go to whatever section you want to go to
[93:53] great so let's Implement that animation
[93:56] allowing you to visit different sections
[93:58] of the site to implement that effect
[94:00] where we figure out when we want to
[94:02] bring the knv bar back when the user
[94:04] Scrolls back we'll have to know the
[94:06] scroll position of the user and for that
[94:08] I'll use the react use Library which has
[94:11] more than 41,000 stars on GitHub it is
[94:14] super simple to install mpmi react use
[94:18] so I'll simply add it to my second
[94:20] terminal and once you do that we can
[94:23] import something out of it and that
[94:25] something will be import use window
[94:29] scroll coming from react use next we can
[94:33] actually get the Y property of the
[94:35] user's current scroll and we can do that
[94:38] by saying
[94:39] const destructure the Y and rename it to
[94:43] current scroll Y and make it equal to
[94:48] the use window scroll Hook Once We have
[94:52] that we can Define find a new use effect
[94:55] that's going to change depending on the
[94:57] current scroll y but we also have to
[95:00] keep track of the last scroll y right
[95:03] this is pretty cool so let's actually
[95:05] create a new use State snippet and call
[95:09] it last scroll
[95:11] y this will allow us to know when a user
[95:14] starts going back and at the start it'll
[95:17] be set to zero and we can also create
[95:20] another state so use State snippet and
[95:25] it's going to be called is nav visible
[95:27] because we have to toggle the visibility
[95:29] of the nav on or off and at the start
[95:32] it'll be set to do true I'll expand this
[95:35] just a bit so we can see it a bit better
[95:37] and I'll start implementing this use
[95:40] effect where at the start we want to
[95:42] check if the
[95:45] current scroll y position is equal to
[95:48] the zero which it most likely is if
[95:51] we're the top that is the top most
[95:53] position and there we want to show the
[95:55] nav bar without the floating bar element
[95:58] what is the floating bar well the dark
[96:00] screen let me show you if I go here here
[96:04] we have that dark screen that allows you
[96:06] to see the white text elements on the
[96:08] white background but at the top we
[96:11] completely remove it because the
[96:13] elements are still visible as we have
[96:15] this video playing right here so here we
[96:17] can set is nav visible to true but we
[96:21] can say the nav container ref
[96:24] current. class list. remove floating
[96:29] dnav pretty cool right we can remove a
[96:32] specific class based on a position of
[96:34] the scroll very
[96:37] useful now we can also have an else if
[96:40] and check if the current scroll Y is
[96:42] greater than the last scroll Y which
[96:45] means that the user is just scrolling
[96:47] down okay so they're not scrolling up
[96:50] which means they're lost in this case we
[96:52] can completely hide the navigation bar
[96:55] and we can add the floating nav class
[96:58] else if the current scroll
[97:01] Y is lower than the last scroll Y in
[97:06] that case we want to set is nav visible
[97:09] to
[97:10] true and we also want to add the
[97:13] floating nav so not remove rather add
[97:16] and how we're going to keep track of the
[97:18] last scroll well we're going to set it
[97:20] right here set last scroll Y is equal to
[97:22] the current scroll y finally we can
[97:25] apply a slight Gap animation by saying
[97:29] use effect and it's going to change
[97:31] whenever the Navar visibility changes so
[97:34] if is nav visible in that case we can
[97:37] call the Gap which of course we have to
[97:40] import from the top by saying import Gap
[97:43] from gsap and then we can say gap. 2 so
[97:48] we want to animate 2 nav container ref
[97:52] and we want to give it specific
[97:53] variables of Y if is nav visible then
[97:57] we're going to set it to zero else we're
[97:59] going to set it to minus 100 you'll see
[98:02] why soon then same thing for opacity if
[98:06] is nav visible is true then it can be
[98:08] set to one else it'll be set to zero and
[98:12] we can set the duration to something
[98:14] like
[98:15] 0.2 now if you save this you can see
[98:18] that exactly what I said was true here
[98:21] we only see the text elements if you
[98:22] start scroll down you can start seeing
[98:25] the dark element right
[98:27] here but at some point it should
[98:29] actually disappear right and then if you
[98:32] start scrolling up it should appear but
[98:34] for us it is always visible which is not
[98:37] necessarily a bad thing you can keep it
[98:38] like this but I prefer to hide it just
[98:41] so we can enjoy the full screen assets
[98:44] of this beautifully designed website so
[98:46] let's see why we're not hiding it I
[98:47] think that's because we're not recalling
[98:49] this use effect whenever the last scroll
[98:52] position changes so cannot properly
[98:54] decide when the last is lower than the
[98:56] current so if I add it right here we can
[98:59] see it it appears oh no that didn't do
[99:02] it that makes me think that this use
[99:04] effect is to blame we're properly
[99:07] changing the Y position and the opacity
[99:10] oh but here too we have to say nav
[99:12] container ref. current to properly point
[99:15] to that element if you do that you
[99:17] notice it gets hidden it's nowhere to be
[99:19] seen But as we start scrolling up it
[99:22] appears back and then it gets to its
[99:24] first initial position this is working
[99:28] wonderfully well it is such a great
[99:30] looking Navar with those added
[99:33] additional functionalities of hiding it
[99:36] showing it and then even it has multiple
[99:38] shown positions such as this initial one
[99:41] where it's very minimal and then we have
[99:43] this one where it appears if we scroll
[99:45] up where you can very clearly see
[99:47] different elements where you want to go
[99:49] and then not to mention that we have the
[99:51] ability to play the music that's
[99:55] great and I like that the music is not
[99:57] actually playing at this start you can
[99:59] actually maybe ask the user if you want
[100:01] to turn it on at the start with some
[100:03] kind of an alert or something feel free
[100:05] to implement that functionality because
[100:07] sometimes it might be easy to just miss
[100:09] this button at the top right but with
[100:11] that said the navigation bar has been
[100:13] implemented which means that we're ready
[100:15] to implement a section below this one
[100:17] and that's going to be this dark section
[100:20] where we're going to have this some sort
[100:21] of a Bento grid with these different
[100:23] animated Elements which look amazing so
[100:26] let me actually collapse the browser to
[100:28] the right side there we go looks amazing
[100:32] can't wait to start implementing this I
[100:34] will close all of the currently open
[100:36] files and I'll create another component
[100:40] called features right here below the
[100:43] source run
[100:45] rafc and then render those features
[100:48] right here below the about if you do
[100:52] that and go back back to the website
[100:54] you'll notice that now it says features
[100:55] right here at the bottom which means
[100:57] that we are ready to start developing it
[100:59] I think this is maybe the second most
[101:01] interesting section after the hero of
[101:03] course even though the Navar was pretty
[101:05] cool you got to admit so take a bit of a
[101:08] pause and we can continue right
[101:12] away to get started working on the
[101:14] featur section let's first turn it into
[101:17] just that a section section is an HTML 5
[101:21] semantic div which denotes that
[101:23] something new is happening in this part
[101:24] of the screen next we can give it a
[101:27] class name equal to BG Das black and
[101:31] padding bottom of 52 if you do that we
[101:35] get this nice black rectangle right
[101:37] below it let's render a div and that div
[101:41] will have a class name of container
[101:44] margin X of Auto padding X of 3 and on
[101:48] medium devices padding X off 10 within
[101:51] it let's create another div just used
[101:53] for some positioning with a class name
[101:56] equal to padding X of five for
[101:58] horizontal padding and padding y of 32
[102:02] for vertical padding within it we can
[102:04] create a new P tag and this P tag can
[102:07] say into the metagame layer you cannot
[102:10] see it just yet as it is dark but we can
[102:12] now style it by giving it a class name
[102:15] of font Das circular D web text- LG and
[102:21] text- blue 50 which is basically a white
[102:25] variant below this P tag we can create
[102:28] another P tag that can say a bit of a
[102:31] longer text maybe something like immerse
[102:34] yourself in a rich and ever expanding
[102:36] Universe where a vibrant array of
[102:39] products converge into an interconnected
[102:41] overlay experience on your world it's a
[102:44] long one I know you don't have to type
[102:46] it exactly like this one you can just
[102:48] type any kind of a longer piece of text
[102:51] so we can see it on the screen you could
[102:52] also to the Finish site right here and
[102:55] then copy it from there I think that's
[102:56] going to be the easiest way to do it
[102:58] I'll link it somewhere below we can then
[103:00] give it a class name equal to Max dw- MD
[103:06] font D circular web text- LG and text-
[103:11] blue 50 with an opacity of 50 and now we
[103:16] have this piece of text right here let's
[103:18] go below this P tag and Below one more
[103:20] div to create another div this this will
[103:23] be the start of our Bento grid Yep this
[103:26] part right here so let's give this div a
[103:30] class name equal to border D
[103:35] hsla if you search for this you'll see
[103:37] that it simply applies a border white
[103:39] property which you can immediately see
[103:41] right here and then we're going to also
[103:43] give it a relative positioning with a
[103:45] margin bottom of seven height of 96
[103:49] which is going to basically turn it into
[103:50] its own
[103:52] section W of full overflow of hidden so
[103:56] we don't have that ugly scroll rounded
[103:59] DMD to round up the corners and on
[104:01] medium devices h of 65 VH within it we
[104:06] want to render a Bento card now as you
[104:09] know we're going to have a couple of
[104:11] these Bento cards like this one this one
[104:13] this one they're all different Bento
[104:15] cards so instead of Simply recreating a
[104:18] card from scratch every time what do you
[104:21] say that we develop a Bento card
[104:23] reusable component that's going to be
[104:26] much much better so let's render the
[104:29] first Bento card right here by calling
[104:32] it like this Bento card as a
[104:35] self-closing
[104:36] component and to it we can pass a couple
[104:39] of props such as a source in terms of
[104:42] which video will it play so it can be
[104:45] videos
[104:47] feature-1 MP4 we can also pass a title
[104:51] which is going to be an empty react
[104:53] fragment inside of which we can say
[104:56] radiant like this but in this case we
[104:59] can make the N bolded which is going to
[105:01] look something like this you're already
[105:03] used to doing that right perfect and
[105:06] alongside the title we can also give it
[105:08] a description and this description can
[105:11] maybe be copied from this finished
[105:13] website I'll copy this description from
[105:16] here by saying a cross platform metagame
[105:19] app turning your activities across web 2
[105:22] and web through games into a rewarding
[105:23] Adventure finally some of these features
[105:26] will be coming soon so if it is coming
[105:28] soon we can apply this is coming soon
[105:30] prop by default if you don't provide an
[105:33] equal sign and then value it'll be set
[105:36] to True automatically so this is coming
[105:39] soon is equal
[105:40] to true now that we have this card let's
[105:44] actually create it above this section
[105:47] and why are we creating it above and not
[105:49] in a custom component because this is
[105:52] the only place where we'll use it so
[105:54] I'll say const Bento card is equal to
[105:59] and I'm going to accept all of those
[106:00] props such as a source title
[106:04] description is coming soon and we can
[106:08] open up a new functional component for
[106:11] now I will simply return a div and I
[106:14] will render the title if I do that and
[106:17] come
[106:18] back you should be able to see well
[106:21] something that looks like this is Bento
[106:23] card but there we go it is hidden
[106:25] because the text is actually dark on the
[106:28] dark background we actually have to turn
[106:29] it to White so let's continue styling
[106:32] this Bento grid by giving this div a
[106:36] class
[106:37] name equal to relative and size- full
[106:42] within it we can immediately play the
[106:44] video by saying video and it'll be a
[106:47] self-closing component to it we can pass
[106:50] a source equal to source which we can
[106:53] also pass
[106:54] Loop we can make it muted because we
[106:57] don't need the sound we can make it
[106:59] autoplay and we can give it a class name
[107:02] equal to Absolute left- z top- z size
[107:08] Das full object D cover and object D
[107:12] Center if you do this you can see this
[107:15] beautiful video playing right here in
[107:17] between the card and believe it or not
[107:19] when you're seeing this highly animated
[107:21] websites in many cases they just have
[107:24] very good video assets so basically web
[107:28] development and web design are sometimes
[107:30] a combination of art with these 3D
[107:32] artists or illustration artists that
[107:35] produce for you these assets that you
[107:37] can then put onto your websites it's not
[107:39] necessary but it sure as hell helps
[107:42] below this video Let's create a div and
[107:45] that div will have a class
[107:48] name equal to
[107:50] relative Z of 10 to appear above the
[107:53] video Flex size- full
[107:58] flex-all justify Dash between padding of
[108:01] five and text- blue of 50 and within it
[108:05] I will render an empty
[108:08] div within which I'll put an H1 which
[108:11] will then render the title so we no
[108:13] longer need this fake title right here
[108:16] and now we can actually style this H1 by
[108:19] giving it a class name of Bento Das tile
[108:23] there we go that's a bit better and we
[108:25] can give it a special Dash font so now
[108:29] it applies that n to it right here
[108:32] beautiful finally some cards will not
[108:35] have a description and some will so if a
[108:37] description exists only then do we
[108:40] render a P tag that renders the
[108:43] description let's style it by giving it
[108:45] a class name of margin top of three to
[108:49] divide it from the title max DW of 64
[108:52] four we can give it a text extra small
[108:56] and the medium devices text Dash base
[109:00] there we go so this is now looking like
[109:02] a real card and some of these cards will
[109:04] have this is coming soon button but
[109:07] considering that most of these features
[109:09] are coming soon and we have a card right
[109:11] here that says more coming soon I don't
[109:14] actually think we'll need it so for now
[109:16] I will just remove the is coming soon
[109:18] prop and I'll also remove it from here
[109:21] when we're passing it to it this is
[109:22] already looking good enough for me not
[109:25] even good enough it's looking amazing
[109:27] now you can see how on the final
[109:28] application there is some additional
[109:30] space on the left and on the right so
[109:32] the card is more in the middle whereas
[109:34] here it seems like almost it's touching
[109:36] the corners well I think I made a small
[109:39] mistake right here I closed this div
[109:42] right here too soon so actually I should
[109:46] have closed it here after the second
[109:48] paragraph which is going to push it a
[109:50] bit up and then the other div can be
[109:52] closed all the way at the bottom right
[109:55] here there we go so now this is going to
[109:58] make it look just a bit better it's
[109:59] going to give it some more breathing
[110:00] room now we can go below this first
[110:03] Bento card and below this div as well
[110:06] and we can create another
[110:08] div this div will have a class name
[110:12] equal to grid
[110:15] h-135 vertical height VH with a grid of
[110:20] calls 2 and grid Das
[110:24] rs-3 with a gap of seven in between the
[110:27] elements of that grid this will allow us
[110:29] to create a very interesting UI such as
[110:32] if you go on the finished website it's
[110:34] going to look something like this where
[110:36] we have one big one on the left and two
[110:38] smaller ones on the right now within
[110:40] this div we'll create another div and
[110:43] that div will have a class name equal to
[110:47] bentto das tilt uncore one row- span-1
[110:52] on medium devices call-
[110:55] span-1 and on medium devices row- span
[110:59] D2 so now we're working on Dynamic
[111:02] positioning dependent on different
[111:04] screen sizes and within it we can render
[111:07] another Bento card because now it's
[111:10] going to be super simple the only thing
[111:11] we have to do is pass the right props
[111:15] such as a source of videos
[111:19] feature-2 MP4 and immediate we can see
[111:23] this video playing we can also give it a
[111:26] title in this case it'll be equal to an
[111:31] empty react
[111:32] fragment within which we can put a test
[111:36] of zigma I think that's what they have
[111:39] on the final website there we go zigma
[111:41] and then we can copy this description
[111:43] text as well by saying description and
[111:46] make it equal to this thing right here
[111:49] it looks like the m is a special
[111:51] character in this case so I will just
[111:53] wrap the m in a bolt tag to give it that
[111:56] special effect there we go that's much
[111:58] better and you'll notice that on desktop
[112:00] devices this will actually take two rows
[112:03] which is perfect and then as you
[112:05] collapse it notice this it's going to
[112:07] drop to a single column and a single Row
[112:11] for that matter that's because of this
[112:12] grid that we implemented now we can go
[112:15] below this div and create another
[112:18] div that'll have a class name equal to
[112:21] Bento - tilt
[112:24] underscore 1 row- span-1 ms of 32 and
[112:30] this Ms is not something that we often
[112:32] used but basically it applies a margin
[112:34] inline start of about 128 pixels on
[112:38] medium devices call- span-1 and on
[112:41] medium devices there's going to be no
[112:44] inline
[112:45] start zero so you can see that this will
[112:48] actually push it a bit to the right to
[112:50] create this interesting visual effect
[112:52] but is going to be even more apparent
[112:53] once we add the Beno grid within it so
[112:56] let's render another Beno card by
[113:00] indenting it properly and giving it a
[113:03] source equal to videos SL feature D3 MP4
[113:10] there we go this is a pretty cool one
[113:12] minimalistic yet effective I'll give it
[113:15] a title equal to again I'll make it a
[113:18] react fragment and within it we can say
[113:21] something like Nexus with the E this
[113:25] time being the special letter so let me
[113:27] render e within the bold bold tax Nexus
[113:31] there we go pretty cool we can also give
[113:34] it a
[113:35] description by copying it from the
[113:38] finished site it's going to look like
[113:40] this so if I go back and give it a
[113:44] description it is looking great this
[113:47] text is a bit harder to read sometimes
[113:49] we can definitely tweak that later on or
[113:51] apply some kind of a background over the
[113:52] text so it's a bit easier to consume
[113:55] that is one thing that you have to keep
[113:57] in mind with these highly animated
[113:58] websites and that is just overall
[114:00] usability you don't want to make
[114:02] everything so flashy that it's hard to
[114:05] get to the gist or to the primary point
[114:07] of your website the website is only
[114:09] there to serve a specific purpose like
[114:11] getting the user to play the game or
[114:13] getting the user to purchase a product
[114:15] if you flash your game or flash your
[114:18] product too much to the user they're
[114:20] going to be lost and they're not gonna
[114:22] do what they came up here to do instead
[114:24] they're just going to Simply start
[114:25] sharing this website to all of their
[114:27] friends because how cool it is but
[114:29] nobody will be playing the game as all
[114:30] of them will be just watching the
[114:31] website with that in mind we can
[114:33] duplicate this entire div with the Bento
[114:37] card and I'll just paste it right here
[114:39] below because we're going to implement
[114:41] something very similar for the next card
[114:43] we're going to have the same thing Bento
[114:45] tilt one but I'll remove the rest of the
[114:47] classes and I'll add me of 14 which is
[114:52] actually going to apply a margin inline
[114:54] end this time on medium devices call-
[114:59] span-1 and the medium devices me of zero
[115:03] which is going to push it at the start
[115:05] Bento grid will render the feature 4
[115:07] videos and it's going to say something
[115:10] like Azul which is the name of I guess
[115:13] one of the games that they have with the
[115:15] U being a special character so I'll put
[115:18] it within the Bold characters like this
[115:22] per perfect we can also copy its text
[115:25] right here and modify it and with that
[115:27] we can move to the two last cards which
[115:29] are not really cards they're just little
[115:31] elements one that says more coming soon
[115:34] and another one which plays the inline
[115:36] video so we can do it by going below the
[115:39] card and Below one more div and we'll
[115:42] create a final div with a class name of
[115:47] Bento Das
[115:49] tilt 2 that'll render another div inside
[115:53] of it with a class name equal to
[115:56] flex size- full
[116:00] flex-all justify Dash between BG Violet
[116:05] 300 and a padding of five there we go so
[116:07] now we're creating this card right here
[116:09] it's going to have an H1 right inside of
[116:11] it that's going to say something like
[116:14] more coming soon and you can choose to
[116:18] make whatever characters you want
[116:19] special like let's go with the O right
[116:21] here
[116:22] I'll make it bold and we can go with
[116:24] some other characters maybe m in the
[116:27] middle that's going to be bolded as well
[116:29] and maybe one of the O's at the end
[116:31] coming soon there we go if I do that and
[116:33] save we have to properly close all the
[116:36] Bold tags I think this one is wrong
[116:40] there we go and now we can see more
[116:41] coming soon which looks awful but once
[116:44] you apply a class name to it equal to
[116:47] Bento Das tile and then apply a special
[116:51] font now we can see the differences and
[116:54] Max DW of
[116:57] 64 as well as text- black if you zoom it
[117:00] in or if you get close to it you can
[117:02] start noticing how cool these custom
[117:04] characters look like right below this H1
[117:06] we can have a TI location Arrow to which
[117:11] we can pass a class name of M of5 for
[117:14] margin scale of a number five and self
[117:19] end so it can align itself to the end
[117:22] looking good now we can go two divs down
[117:25] and we can create that additional card
[117:28] with a class name equal to Bento D
[117:33] tilt 2 that'll render a video with a
[117:36] source equal to videos feature-- 5. MP4
[117:42] it'll Loop it'll be muted it'll
[117:46] autoplay and it'll have a class name of
[117:49] size- full object d cover and object
[117:54] Dash
[117:55] Center there we go that's more like it
[117:57] so now this is looking great and just by
[118:01] itself this section is already looking
[118:03] amazing especially given how we get into
[118:06] it like we are on the light section we
[118:08] see this image and we don't think
[118:10] anything of it but then we start diving
[118:13] into that image which is pretty cool we
[118:15] get turned into a new dark world where
[118:18] we can see this Bento grid right here
[118:20] already it is looking amazing with these
[118:22] mini videos playing within each one of
[118:25] course fully mobile responsive but we're
[118:27] going to take it even a step further by
[118:30] adding a tilt effect to these cards
[118:33] check this out if I move this cursor
[118:36] over the card it's going to tilt as if
[118:38] I'm hovering over it in different places
[118:41] same thing for this one this one too
[118:44] they're kind of like interactable you
[118:46] almost feel like you can take it in your
[118:47] hand which is a perfect effect for
[118:49] collectible card games but it looks
[118:51] great great here as well so let me show
[118:53] you how you can implement it I'll go
[118:56] back to the mobile mode you'll see how
[118:59] great it looks like on mobile as well
[119:02] and and I'll create a new component
[119:04] right here at the top above the Bento
[119:07] card and I'll call it Bento tilt it's
[119:11] going to take in the children which we
[119:13] want to tilt and it's going to take in a
[119:16] class name which by default will be set
[119:18] to an empty string finally we can return
[119:20] the Tilt so for now let's simply return
[119:24] a
[119:25] div and this div will render the
[119:28] children so we don't want to do anything
[119:30] yet we just want to show the cards
[119:32] themselves and then later on we'll add
[119:34] additional functionalities here so what
[119:36] I want to do now is replace all these
[119:40] divs that wrap the Bento cards with a
[119:43] Bento tilt component like this this is
[119:46] the first time with these Bento tilt
[119:49] there we go then we have another one
[119:51] which grabs the card Bento tilt then we
[119:54] have another one Bento tilt we have
[119:57] another one right here Bento tilt and
[120:00] finally we have this one Bento tilt 2
[120:03] and the last one is the Bento tilt for
[120:05] the video now this completely broke the
[120:08] view because we lost all of the class
[120:10] names we're passing to it so to fix it
[120:13] we just have to pass the class names to
[120:15] the div by saying class name is equal to
[120:18] class name and everything is back to
[120:20] where we were but now we can start
[120:22] implementing the Tilt itself let's do it
[120:24] by creating a new Ed State field which
[120:28] is going to be called
[120:30] transform style and set transform style
[120:33] at the start set to an empty string we
[120:37] also need a ref to be able to move those
[120:39] elements around so I'll say const item
[120:42] ref is equal to use ref coming from
[120:46] react we'll also have a function const
[120:50] handle Mouse move which will give us the
[120:53] move event like this and it'll be
[120:56] executed once we move our Mouse on top
[120:58] of that element and we have to have the
[121:00] same thing for handle Mouse leave which
[121:04] will happen once we leave the card which
[121:06] is when we want to set the transform
[121:08] style back to an empty string now that
[121:11] we have all of these elements we can
[121:12] pass it to this
[121:14] div such as a ref equal to item ref we
[121:19] can pass the on Mouse move to be equal
[121:22] to the on Mouse move function we created
[121:25] we can also pass the on Mouse leave
[121:29] which is going to be equal to the handle
[121:31] Mouse leave and I should have done the
[121:33] same thing here handle Mouse move on
[121:36] Mouse move that's generally a good
[121:38] practice to have the Handler attached to
[121:41] the specific on event functionality so
[121:44] on Mouse move you handle the mouse move
[121:48] and finally we can pass it the style
[121:50] which is going to be equal to trans form
[121:52] is going to be set through the transform
[121:54] style which is at the start set to
[121:57] nothing an empty string so now if I
[122:00] hover over it nothing is happening but
[122:02] check this out if I go into the handle
[122:04] Mouse move I want to figure out which
[122:07] card we're interacting with so if there
[122:10] is no card so if no item r that current
[122:13] I'll just exit the function and not
[122:14] change anything but if we are modifying
[122:17] something I can then set this new
[122:20] transform
[122:21] style to be equal to a new style like
[122:24] maybe I can apply whatever co-pilot is
[122:27] assisting with me
[122:29] here okay this is interesting so by
[122:31] itself it applied some kind of a tilt
[122:33] right here but it doesn't work very well
[122:36] but you get the point once we go into
[122:37] the card we can play with it like this I
[122:40] will not take this rather I'll teach you
[122:42] how to create a much better tilt on your
[122:44] own and keep in mind there's some
[122:45] packages that do this so you could
[122:47] technically go to mpm and find a package
[122:49] that does it for you but in this case
[122:51] I'll teach you how to to do it from
[122:52] scratch first we want to get the
[122:54] properties of the position of the card
[122:56] by saying const destructuring the left
[123:00] the top the width and the height by
[123:03] saying equal to item ref. current. getet
[123:07] bounding client wrecked how does this
[123:09] work well it works because it finds the
[123:12] current reference to the element we're
[123:14] clicking and then it gets as its
[123:16] positions once we have the positions we
[123:18] want to get the relative X and relative
[123:21] y
[123:22] properties I mean the card relative to
[123:25] the cursor right so we can say event.
[123:28] client X which is the position of the
[123:31] cursor minus
[123:34] left divided by the width so this is
[123:36] going to give us a relative position of
[123:38] our Mouse to the position of the card
[123:40] and we can repe the same thing for the Y
[123:43] positions I called the event in this
[123:45] case just the E so we can switch it over
[123:47] to
[123:48] e and we want to do the same thing with
[123:51] the tilt so now that we have the
[123:52] relative difference between our mouse
[123:54] cursor and the card itself we can say
[123:57] const tilt X is equal to relative
[124:03] y -
[124:05] 0.5 * 5 I found this value to work the
[124:09] best and you can do the same for the
[124:10] Tilt y by setting it to relative x - 0.5
[124:14] * -5 I'll show you how we can switch
[124:17] those values later on but for now we can
[124:19] set this new transformation by saying
[124:22] neutrons form is equal to a string where
[124:24] we take in the perspective of 700 pixels
[124:29] and then we rotate the X position I have
[124:32] to turn off this autocomplete because
[124:34] it's not doing me any favors okay I
[124:36] think I at least decreased the number of
[124:38] suggestions being given so on the rotate
[124:41] X we want to actually set it to be equal
[124:44] to the dynamic property of tilt X and
[124:48] then give it de as in degrees of course
[124:51] we need to turn this into a dynamic
[124:53] template string for these degrees to be
[124:55] counted which is going to look something
[124:57] like this perspective is 700 rotate X is
[125:01] set to tilt X De and then I think you
[125:04] can guess it we can then set the rotate
[125:07] y to be set to tilt y degrees and we can
[125:11] also change the scale of the card a bit
[125:13] to allow us to rotate in if we set it to
[125:16] 111 it's going to be the same but we can
[125:19] maybe decrease it to 0.95
[125:21] to make it a bit smaller to allow us to
[125:24] move it around a bit and we can set the
[125:26] transform style to be equal to new
[125:29] transform if I save this and reload
[125:32] nothing is happening just yet and I
[125:33] think that's because I missed the
[125:35] closing parentheses right here on rotate
[125:37] X De if I add it now this is considered
[125:40] a real transformation and it'll actually
[125:43] be applied so now we can see it moves if
[125:46] you want to increase it we can change
[125:48] this maybe over to 10 times which will
[125:51] make it much more pronounced or maybe we
[125:53] could go with something like
[125:55] 50 and now we can see that it really
[125:58] moves a lot but this is starting to look
[126:00] a bit trippy so I prefer to keep it at a
[126:02] lower level at like five there we go
[126:06] just little and subtle and we also don't
[126:08] have to decrease the size that much we
[126:10] can maybe just decrease it a bit by
[126:12] setting it to 98 maybe but still give us
[126:14] a bit of space to move it around like if
[126:17] we reduce the size of it once we enter
[126:19] it it feels like we can do something you
[126:21] see that there we go and then we can
[126:24] start moving it around to explore the
[126:26] screen this is looking
[126:30] great and with that we have added those
[126:33] hover animations and tilt animations to
[126:35] those cards and of course this is
[126:37] looking so much better on a larger
[126:38] screen because you have so much more
[126:40] space to actually move it around this
[126:43] effect is actually designed for larger
[126:45] screens because if you go all the way to
[126:47] this corner the card will be very tilted
[126:50] as you can see but on mobile you cannot
[126:53] actually move around within each card a
[126:55] lot so you don't have a lot of tilt what
[126:58] you could do is play a bit with those
[127:00] values and then if we're in Mobile you
[127:02] could then increase the Tilt amounts but
[127:04] for now I'm more than happy with this
[127:07] and with that we came to the end of the
[127:09] feature section one of the very exciting
[127:11] sections of this project I mean I know
[127:13] that I keep saying that for every single
[127:15] one including the Navar but that's just
[127:17] because I'm so excited for this project
[127:20] and all of these sections are indeed
[127:22] very cool now for the next section we're
[127:24] going to focus on this one right here
[127:26] where we have this title which you might
[127:29] already remember from before it is the
[127:31] animated title we have created and then
[127:34] we have this card that you can move
[127:36] around a bit and explore inside of the
[127:38] realm again the whole idea of this site
[127:40] is to go inside of different worlds
[127:43] portal and Realms and explore them with
[127:45] your mouse so let's do that
[127:49] next the story of hidden realm the story
[127:53] is exactly the next section we'll
[127:55] Implement so let's go back to our
[127:57] application head over to the components
[127:59] folder and create a new file called
[128:02] story. jsx run
[128:06] rafc import it right below the features
[128:09] and let's head into it to start
[128:11] implementing it I'll collapse the
[128:13] browser and damn is it looking good here
[128:15] as well and let's turn it into its own
[128:17] section with an ID of story a class name
[128:21] equal to Min dh-
[128:25] dvh w- screen BG black and text- blue of
[128:31] 50 there we go that's better let's also
[128:35] within it render another div that'll
[128:38] have a class name equal to flex a size
[128:42] of full flex-all so the elements appear
[128:45] one below another items Das Center to
[128:48] center it padding y of 10 and padding
[128:52] bottom of 24 within it we can render a P
[128:55] tag that'll say the
[128:59] multiversal IP World whatever that means
[129:03] and we can give it a class name set to
[129:06] font Das General text- small
[129:11] uppercase and on medium devices text
[129:14] dash 10 pixels like this that's going to
[129:18] look something like this and within it
[129:20] we can start creating the animated title
[129:23] so let's go below the p and let's create
[129:26] a div that's going to have a class name
[129:29] of relative with a size- full and right
[129:33] within it I'll create an animated title
[129:37] to which we can now pass a title equal
[129:41] to the story of a hidden
[129:45] realm there we go that looks amazing but
[129:49] let's also make some of these characters
[129:51] B did like the O in the story just like
[129:54] this let's also add a break after the of
[129:58] and let's make the M right here bolded
[130:00] as well and we can also give it a
[130:02] section ID of hash story so we can
[130:05] scroll to it and a container class equal
[130:09] to margin top of five to divide it a bit
[130:11] from the rest a pointer-events d none so
[130:15] we cannot interact with it mix blend
[130:20] difference this is is to blend it with
[130:22] the image that's going to come below it
[130:25] relative and a z of 10 now as you scroll
[130:29] it simply says the story but if you
[130:31] reload it'll say the story of a hidden
[130:33] realm and it will very nicely animate as
[130:36] you scroll through it now just below it
[130:38] still within the same div we can render
[130:41] the container for the image that will
[130:43] appear right here so it'll have a class
[130:46] name equal to story- IMG Das container
[130:51] ER and we'll have another div right here
[130:54] that will have a class name of story-
[130:57] IMG
[130:59] dmask and finally the last div that'll
[131:02] have a class name equal to story- IM
[131:08] g-content and within it we can put the
[131:10] actual
[131:12] image this image will have a source
[131:15] equal to SL image SL entrance. web key
[131:22] if I save it you can see it right here
[131:24] it has been pre-cut to properly fit the
[131:26] screen right here I'll also give it an
[131:28] Al tag equal to entrance and a class
[131:32] name equal
[131:33] to
[131:36] object Dash contain but now of course we
[131:39] have to animate it on Hover so for that
[131:42] reason I'll give it a ref equal to frame
[131:45] ref and I'll create that frame ref right
[131:48] here at the top by saying const frame
[131:52] ref is equal to use ref coming from
[131:56] react at the start set to of course a
[132:00] string of null we can also Define a new
[132:04] function con handle Mouse leave which is
[132:09] going to be a function that's going to
[132:10] handle the event once the mouse leaves
[132:12] but in our case also enters into this
[132:14] image because on Mouse leave we're going
[132:17] to call the handle Mouse leave but we're
[132:20] going to do the same thing on Mouse up
[132:22] and mouse enter so let's say on Mouse up
[132:25] is equal to handle Mouse leave and the
[132:29] same things goes for on Mouse enter
[132:32] we'll also call it the handle Mouse
[132:35] leave the only one that will be
[132:37] different is going to be on Mouse move
[132:40] so while we're moving we can actually
[132:42] implement the handle Mouse move
[132:45] functionality so let's create that
[132:47] function right here at the top right
[132:50] below the handle Mouse leave const
[132:53] handle Mouse move and the effect we're
[132:55] trying to achieve is something like this
[132:58] similar to the tilt of the card that we
[133:00] had before but a bit different because
[133:03] it moves a bit less on this side and a
[133:05] bit more on this side and it also goes
[133:07] over the text it'll be very very similar
[133:10] to what we have implemented in our Beno
[133:12] cards once we move them but we just
[133:15] slight differences so let's implement
[133:17] the handle Mouse move first first we
[133:20] want to destructure Ure the client X
[133:22] position and the client y position from
[133:25] the event meaning our Mouse then we can
[133:28] get the element by saying frame ref.
[133:31] current that is the element we're
[133:33] hovering over then if we don't have an
[133:36] element so if no element we're going to
[133:39] Simply exit out of the function but if
[133:42] we do have it we'll try to get its
[133:44] rectangular Properties by saying
[133:46] element. getet bounding client wct and
[133:49] then we can extract the X position and
[133:52] the Y position by saying const X is
[133:55] client x minus re left and Y position is
[133:59] client y minus W top we're doing that to
[134:03] calculate the center of the image by
[134:06] saying const Center X is equal to re.
[134:11] width ided by two and Center Y is re.
[134:15] height ided by two as well finally we
[134:17] can calculate the rotation values based
[134:20] on the mouse position
[134:21] relative to the center by saying const
[134:24] rotate X is equal to
[134:28] Yus Center
[134:30] y divided by Center
[134:34] y times and then you can put any kind of
[134:37] a magnifier like minus 10 in this case
[134:40] and we can do the same thing for rotate
[134:42] X that's going to be X position minus
[134:44] Center x / Center x * 10 finally we can
[134:48] use gep to animate it by saying gap. 2
[134:53] of course you want to import gsap from
[134:55] the top by saying import Gap from
[134:58] Gap and then you can say gap. 2 we want
[135:02] to pass it the element in this case and
[135:05] pass the properties such as duration is
[135:07] going to be set to 0.3 and then we want
[135:10] to pass the rotate X property set to
[135:13] rotate X rotate y property set to rotate
[135:17] y also the
[135:19] transform perspective property set to
[135:23] 500 which is going to give us a 3d
[135:26] effect and finally the ease which is
[135:28] going to be power one. in out if I do
[135:32] that we get this beautiful
[135:35] effect like we're moving within a 3D
[135:37] realm and you can also notice that it
[135:40] goes right here below the text we of
[135:43] course we'll have to change the text as
[135:45] it interacts with this image now if we
[135:48] leave the element we want to reset the
[135:51] positioning which we can do right here
[135:54] on handle Mouse SLE so I'll say gp. 2
[135:58] and I'll paste it here we also need to
[136:00] get the element from the frame r.
[136:03] current and instead of setting it to New
[136:06] rotation values I'll simply set the
[136:08] rotate X as well as rotate y properties
[136:12] to zero and remove the transform
[136:14] perspective that's it so now if you
[136:16] enter we're there we can move it you
[136:18] exit it gets back to normal
[136:21] great now notice how we have these very
[136:24] pointy Corners in our case that then
[136:27] move which doesn't look that good but in
[136:30] the final website it's looking much more
[136:32] organic it seems more like a card than
[136:34] like a rectangle we can achieve those
[136:36] rounded Corners by using an SVG filter
[136:39] within components you can create a new
[136:42] file called
[136:45] rounded
[136:47] corners. jsx you can run rafc
[136:51] and within it you will paste an SVG that
[136:55] I will give to you you can find it in
[136:56] the description of the code repository
[136:59] of this video here we're applying the
[137:01] invisible to the corners of this element
[137:03] don't worry I didn't write this code by
[137:05] myself I just found it on the internet
[137:07] so now we can add it right here two divs
[137:10] down below the image and I'll call it
[137:14] rounded corners and just call it like
[137:17] this if you do that you can notice that
[137:19] now the corners are going to be
[137:21] completely
[137:22] rounded this is a very cool 3d effect it
[137:25] feels like we're in there now when it
[137:27] comes to this text we want to mix it
[137:29] with the image and right now it's not
[137:32] getting mixed it is just white here
[137:34] we're applying a mix blend difference
[137:37] and I think I misspelled the difference
[137:39] right here so if I spell it properly and
[137:42] go back you can see that now this makes
[137:43] it even better because you can properly
[137:45] read the text given that it's completely
[137:48] white on the black background giving you
[137:50] Max maximum contrast but it's also
[137:52] contrasting the image so you can still
[137:55] see it and this even adds to the effect
[137:58] that we're trying to make great now we
[138:01] can go a bit below right here and add
[138:03] this piece of text and the button we can
[138:05] do that by hitting below these rounded
[138:08] corners and going two divs down so we're
[138:11] almost at the last div I'll create
[138:14] another div that'll have a class name
[138:18] equal to minus margin top all 80 Flex w-
[138:24] full justify Das Center on medium
[138:27] devices minus margin top of 64 on medium
[138:31] devices me of 44 and on medium devices
[138:36] justify Dash end we're just creating a
[138:39] position for where this element will
[138:41] appear next we can render another div
[138:44] right within it that will act as the
[138:46] container for the text that will have a
[138:48] class name of flex h- full w- fit
[138:56] flex-all items D Center and the medium
[138:59] devices items Das start and there we can
[139:03] render a piece of text that's going to
[139:05] be a paragraph I can copy the text from
[139:08] the final code oh I cannot get to it
[139:10] because of the image it's actually below
[139:12] the image but if I start a bit down I
[139:15] can get to it there we go and I will
[139:17] paste it right here and remove what we
[139:20] don't need that's going to be where
[139:23] Realms converge lies zentry oh that
[139:26] sounds exciting so now if we go back we
[139:28] can style it further by giving this P
[139:31] tag a class name of margin top of
[139:35] three max DW of small text- Center font
[139:41] D circular D web text- Violet
[139:46] 50 and on medium
[139:48] devices text- start
[139:52] there we go that's more like it and
[139:55] below it we can render a button the
[139:58] button that we have already created
[139:59] that's a reusable button component
[140:02] that'll have an ID of Realm button a
[140:06] title of discover prologue and a
[140:09] container class equal to margin top of
[140:13] five there we go we have our button
[140:15] right
[140:16] here now we're almost done with this
[140:19] section but it seems to me
[140:21] that it's not exactly the same as what
[140:23] we have here here it has a bit more
[140:25] rounded Corners even on the right side
[140:28] whereas ours right now is kind of going
[140:30] all the way out right here it's jumping
[140:32] out so let's see where we messed up some
[140:35] Styles right here where we had the image
[140:37] I think it's just right here where I
[140:39] said story image cotent instead of
[140:42] content if I fix this the right Styles
[140:45] will be applied and this will look so
[140:47] much better providing more space for
[140:49] this text right here to come
[140:51] and of course we must not forget that
[140:53] this is completely tablet as well as
[140:56] mobile responsive on mobile we have this
[140:59] effect right here as we don't want it to
[141:00] go over the text and then we nicely show
[141:02] the subtitle in the center but again
[141:05] even on tablet devices we have this cool
[141:07] effect here and on all sizes in between
[141:11] with that in mind the next section we'll
[141:13] Implement is this one right here it
[141:15] looks great even on mobile where the
[141:18] image jumps across different sections
[141:21] it's a contact us section where we have
[141:23] a call to action button and right below
[141:25] it we have the footer so let me head
[141:28] back over to the app and create another
[141:31] section called contact. jsx run
[141:36] rafc and you know what I'll immediately
[141:38] do the footer as well by creating a
[141:40] footer. jsx running
[141:44] RFC and now we can add the contact as
[141:47] well as the footer right here to the
[141:50] bottom and they should immediately
[141:53] appear on the
[141:55] page if we do that go back you can see
[141:58] the contact and the footer which means
[142:00] that we are ready to start implementing
[142:02] it great job coming this far into this
[142:05] video the last two sections are
[142:07] definitely a bit simpler than the
[142:08] previous ones so you won't have any
[142:11] problems coming to the end of this
[142:12] amazing build and soon enough you'll be
[142:15] able to deploy
[142:17] it to get started with implementing men
[142:20] in the contact Section let's first give
[142:23] this div an ID of contact so we can
[142:25] easily scroll to it from the navigation
[142:27] bar and let's also give it a class name
[142:31] equal to margin y of 20 to give it some
[142:34] space m-h of 96 to give it much more
[142:38] space as well as a w screen for full
[142:41] width and a padding X of 10 to create
[142:44] some space on the left and right sides
[142:47] let's also create another div right
[142:48] within it with a class last name of
[142:51] relative rounded
[142:54] dlg BG black and a padding way of 24
[142:59] with text blue of 50 and then small
[143:02] devices overflow of hidden there we go
[143:06] now we have this inner dark rectangle
[143:09] let's have another div inside of here
[143:11] inside of which we'll have images so
[143:14] I'll give it a class name of absolute
[143:16] minus left D20 top zero typically it'll
[143:21] be hidden with a full
[143:24] height W of 72 overflow of hidden but on
[143:29] small devices it'll be block meaning
[143:32] we'll show it and on large devices we're
[143:34] going to do a left of 20 and on large
[143:37] devices a w of 96 this is to make it
[143:40] responsive finally within it we can
[143:43] render an
[143:44] image specifically it'll be a div
[143:48] that'll have a class name equal
[143:51] to contact dclip Das
[143:55] path-1 and within it we can render an
[143:58] image with a source equal to image
[144:03] contact D1 webp now we cannot yet see it
[144:07] here but if we expand you'll be able to
[144:10] see this image which will make more
[144:12] sense on the final version of the
[144:13] application we're now creating these
[144:16] right here on mobile only the big one
[144:18] will keep showing now we we actually
[144:20] have to create another image clip so
[144:22] what I'll do is I'll copy this part
[144:25] right here and turn it into a reusable
[144:27] component called
[144:29] image clip box which is going to be a
[144:33] function with an immediate return that's
[144:35] going to return the same div but we will
[144:37] actually destructure the source and the
[144:40] clip
[144:42] class so now when we call it here the
[144:45] image clip box we can pass the clip
[144:49] class equal to this class right here
[144:52] clip contact clip path one and we can
[144:56] pass a source equal to this Source right
[144:59] here then we can just get the source
[145:02] from the props and we can also get the
[145:05] class name from the props as well by
[145:07] referring to the clip class property if
[145:11] you do that it's still here but now that
[145:14] allows us to duplicate it very easily
[145:16] right here below change the contact clip
[145:20] path to two give it a property of on
[145:22] large devices
[145:25] translate by 40 in the y direction and
[145:30] translate
[145:32] y60 typically and let's change the image
[145:35] to contact to if you do that you cannot
[145:37] see it just yet but we will be able to
[145:39] see it once we add the text this will
[145:41] add this second image right here now we
[145:44] can scroll a bit down and exit this div
[145:48] but we can create another div to
[145:49] absolutely position a second image so
[145:52] what I'll do is copy this initial div
[145:54] that we had paste it properly close it
[145:57] and we can change it from minus left
[146:01] 20 to minus top 40 and left- 20 we'll
[146:07] remove the H full and the hidden
[146:10] property make it w of 60 remove all of
[146:15] these
[146:16] overflows and I'll apply some additional
[146:18] properties to make it look good on other
[146:20] Dev devices like on small devices top
[146:22] will be 1 over two on medium devices
[146:26] left will be Auto on medium devices
[146:28] right will be 10 on large devices top
[146:32] will be 20 and on large devices W will
[146:35] be 80 and I think right here in this one
[146:38] I forgot to provide the Top Value this
[146:40] right here was supposed to be top zero
[146:42] there we go now it looks a bit better
[146:44] now within this one we can apply two new
[146:47] image clip boxes so let's copy it and
[146:50] let me put the source first so it's
[146:52] easier to see what we're rendering and
[146:55] change the image path to
[146:58] swordman swordman DP partial
[147:02] webp and change the class name to
[147:05] Absolute on medum devices scale of
[147:10] 125 there we go you can start seeing it
[147:13] right here and I will duplicate it below
[147:16] I'll change the image to swordman this
[147:18] one will not be partial and I'll enter
[147:21] the class name of Sword dasman
[147:25] dclip Das path and a medium devices
[147:29] scale of
[147:30] 125 so now we'll be able to see it even
[147:33] on smaller devices where it will appear
[147:36] as a full image great now we can go
[147:40] below this div wrapping these two image
[147:42] clip boxes and we can render another div
[147:45] which will contain the text so let's
[147:47] give it a class name equal to flex
[147:52] flex-all items - Center text- Center and
[147:57] within it I'll render a P tag with a
[148:00] class name equal to font
[148:03] dgen text- 10
[148:06] pixels and uppercase and within it I'll
[148:09] say join zentry so this is the final
[148:12] call to action there we go below it I'll
[148:15] render another P tag which will
[148:18] say let's build build the new era of
[148:23] gaming together like this but of course
[148:26] we can make it much more exciting so let
[148:29] me put it here and give it a class name
[148:32] equal to
[148:34] special- font margin top of 10 w- full
[148:39] font D zentry text d5xl so very large
[148:45] leading Das
[148:48] 0.9 on devices text- 6 REM like this and
[148:54] now it's huge we can also apply some
[148:57] brakes like right here after the word
[148:59] the we're going to add a break and maybe
[149:03] also before the word gaming we can apply
[149:06] another break this is looking good we
[149:09] can also use those special characters it
[149:11] would be a shame not to use them because
[149:13] this text is so big so let's do it on
[149:15] the U in build there we go I'll add a
[149:19] bold
[149:20] let's also do it right here under a in
[149:23] gaming not too much just on a couple of
[149:25] different
[149:27] characters and we can add it an o in the
[149:29] word together so as you know I'm just
[149:31] Bolding the characters in order to
[149:33] achieve that special character look
[149:35] let's build the new era of gaming
[149:38] together great finally below the P tag
[149:41] we can have a button that'll have a
[149:44] title equal to contact us a container
[149:48] class of margin top of of 10 and a class
[149:52] of
[149:53] cursor Das
[149:56] pointer there we go that's much better
[149:59] now if you check this in full screen
[150:01] it's going to look absolutely amazing
[150:04] and if you collapse it a bit you can see
[150:07] here we are going a bit over the text I
[150:09] agree you could do some additional fixes
[150:12] but if you collapse it further you can
[150:14] notice that it looks great on mobile as
[150:16] well and the last thing we have to do is
[150:18] implement the footer section
[150:20] so I'll close this one and head over
[150:23] into the footer and trust me this will
[150:25] be the simplest section of them all
[150:27] where we'll turn this into an HTML 5
[150:30] semantic footer tag with a class name
[150:34] equal to w- screen and we'll use a bit
[150:37] of a different color here BG of violet
[150:41] 300 with a padding y of 4 and text Das
[150:46] black there we go we see it at the
[150:48] bottom within it I'll Rend the a div
[150:51] that'll have a class name equal to
[150:54] container margin X of Auto Flex
[150:59] flex-all items Das Center justify Dash
[151:03] between gap of four padding X of four
[151:07] and in medium devices Flex of
[151:10] row and then we can render a P tag
[151:12] that's going to say something like what
[151:14] we can copy from the final website at
[151:17] Nova 2024 All Rights Reserved and I
[151:21] think you can do that copy by saying the
[151:24] and copy sign that's a bit of a more
[151:28] proper way to do it so you use the and
[151:30] copy and then semicolon which will
[151:33] render the copyright sign we can give
[151:35] this p a class name of text- Center
[151:39] text-
[151:40] small font d
[151:43] light or no let's keep it normal and on
[151:46] medium devices we want to left align it
[151:48] so text
[151:50] Dash
[151:52] left great but now what matters more are
[151:55] the actual links that we want to show
[151:57] pointing to the socials of all of our
[151:59] different platforms so I'll create a div
[152:02] that'll act as the container for those
[152:03] links so I can give it a class name of
[152:07] flex justify Dash Center gap of four and
[152:13] on medium devices justify Dash start now
[152:16] we need to create an array with all of
[152:18] these different links which we can do by
[152:20] saying const links is equal to an array
[152:24] of objects where we have an atra
[152:26] pointing to that link which for now can
[152:29] be something like https
[152:32] col
[152:34] discord.com and then we can say
[152:36] something like
[152:38] icon is going to be fa Discord coming
[152:43] from react icons fa and then we can
[152:46] duplicate this over for different social
[152:48] platforms that you like for example
[152:49] example we can do it for let's do
[152:53] another hre for maybe Twitter all kind
[152:56] of platforms have different Twitter
[152:58] icons have different Twitter socials so
[153:01] we can say icon is going to be fa
[153:04] Twitter coming from react icons fa and
[153:08] you could do GitHub if you want to so
[153:10] I'll add fa GitHub and maybe one more
[153:14] let's see what our AI comes up with now
[153:17] it's saying GitHub again but we're going
[153:19] to change this over to maybe something
[153:21] like twitch as this is a gaming platform
[153:24] so fa twitch perfect now we can map over
[153:29] these links by saying links. map where
[153:32] we get each individual link and for each
[153:35] link we can automatically return by just
[153:38] putting an anchor
[153:39] tag and properly closing it it'll render
[153:42] the link.
[153:44] icon so now you should be able to see
[153:47] four different icons at the bottom but
[153:49] to make them clickable we have to give
[153:51] it a key equal to
[153:53] link we have to give it an href equal to
[153:57] link. href we have to give it a target
[154:01] of underscore blank which will open it
[154:04] up in a new screen and whenever you add
[154:06] that you also need to add a re of no
[154:08] opener and no
[154:11] referer and we can give it a class name
[154:14] equal to text- Black transition dasc
[154:18] colors with a duration of 500 E in out
[154:24] and on Hover we can change the text to
[154:26] White so this will give us this cool
[154:28] effect that when you hover it appears
[154:31] clickable great finally below this div
[154:35] we can create a final anchor tag that'll
[154:38] have an href pointing to our hash
[154:41] privacy Das policy and it'll have a
[154:44] class name equal to text- Center text-
[154:48] small on Hover we're going to do an
[154:51] underline and on meeting devices we'll
[154:54] position it to the right side and here
[154:57] we can simply say privacy policy there
[155:00] we go looks great on mobile devices but
[155:02] as I expand it everything is nicely
[155:05] positioned and aligned with the start of
[155:07] this rectangle and the end of the
[155:09] rectangle that's exactly what you want
[155:11] to do and with that in mind believe it
[155:13] or not we are done with this amazing
[155:16] unique almost one-of aind I would say
[155:19] build we can scroll to the top and I
[155:21] think it's the right time to start
[155:23] playing the video remember that we
[155:24] turned it off at the start so I'll head
[155:27] over to the hero section and I will
[155:29] uncomment this autoplay feature right
[155:32] here and reload and we get a new video
[155:36] playing we have a great looking
[155:38] navigation bar which if you want to you
[155:40] can make it point to different sections
[155:42] like it is right now and as you know we
[155:44] have this great portal which if you
[155:46] click into it you will dive into another
[155:48] world or another video as you scroll
[155:51] this container will kind of get smaller
[155:53] and then we have this animated title
[155:55] where you enter into another world that
[155:58] is completely dark I think this was
[156:00] supposed to say radiant not rent so if I
[156:03] head over to features to our first Bento
[156:06] grid right here or Bento card I'll say
[156:10] rad ant there we
[156:13] go that's better we have this beautiful
[156:16] section that allows us to kind of uh
[156:18] tilt the cards around to make it feel
[156:20] like we're holding them in our hand and
[156:22] finally we have the story of a hidden
[156:23] realm section then there's this very
[156:26] prominent cold to action button that
[156:28] just invites us to contact them and
[156:31] finally a simple footer and I don't have
[156:33] to show you how it looks like on mobile
[156:35] because you've seen it many many times
[156:37] so far and we have developed it mobile
[156:39] first by first developing the mobile UI
[156:41] anyway so with that in mind we are ready
[156:44] to get it
[156:46] deployed so let's go back to our code
[156:49] base one more time open up an empty
[156:51] terminal and run mpm run build this will
[156:55] allow us to create an optimized
[156:57] production build of our application
[156:59] immediately you'll see a new folder
[157:01] called this appear right here at the top
[157:04] so right click it and click open in
[157:06] finder or in file explorer if you're in
[157:09] Windows once you do that head back over
[157:11] to your hostinger dashboard to the
[157:13] hosting that you bought for this project
[157:15] and head over to the file manager once
[157:17] you're here enter the public h HTML
[157:19] folder and delete the default PHP
[157:22] finally open up the disc and then drag
[157:25] and drop all the files within the disc
[157:27] folder right here it's going to say
[157:30] uploading 30 files but trust me it'll
[157:32] happen in a matter of seconds so let's
[157:34] pause for a second and I'll be right
[157:36] back once the files are uploaded and
[157:38] there we go the files are here head back
[157:41] over to your dashboard and click on the
[157:43] domain name you chose that'll open up in
[157:46] the browser but this time on the web you
[157:49] can see the nice loading that happens
[157:50] for the first time when you run the
[157:52] application and then we see this nice
[157:54] video play with all of the great
[157:56] features that we previously explored
[157:57] such as entering different scenes
[157:59] scrolling down to see these great
[158:01] animations this little C tilt effect and
[158:04] more this was such an interesting build
[158:07] where we got a chance to explore the
[158:09] intricacies of micro animations so with
[158:12] that said huge congratulations on coming
[158:14] to the end of this video I hope you
[158:16] enjoyed watching it as much I enjoyed
[158:18] teaching it he and if that really is the
[158:20] case which would make me very happy then
[158:22] the only thing that makes sense next is
[158:24] for you to get the ultimate next GS
[158:26] course I mean you watched and enjoyed
[158:28] more than two hours of this educational
[158:30] YouTube video so you're going to love
[158:32] what I do in the next GS course there I
[158:35] teach you how to use nygs in the way
[158:37] that it has been envisioned for you to
[158:39] use it but right now the majority of
[158:41] devs still use it as plain old react
[158:44] which gives us performance that looks
[158:46] like this thankfully that won't be the
[158:48] case with you as you will have a whole
[158:50] new approach to learning with server and
[158:53] client components boosting your
[158:54] website's performance discovering all
[158:57] the latest react 19 and Nyx gs15 plus
[159:00] features and so much more with deep dive
[159:03] to understand the theory of how
[159:05] everything works behind the scenes and
[159:07] then a build and deploy of a very
[159:10] complex app with active lessons that
[159:13] allow you to simulate the process of
[159:15] learning and actually make you develop
[159:17] stuff before you just watch these videos
[159:19] like Netflix you will have to put things
[159:22] into practice so if that sounds exciting
[159:24] check it out the link is down in the
[159:26] description with that said once again
[159:28] congrats on coming to the end of this
[159:30] course and I'll see you in the next one
[159:33] have a wonderful day
