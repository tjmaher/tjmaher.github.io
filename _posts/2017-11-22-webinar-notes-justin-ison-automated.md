\-\-- layout: post title: \'Webinar Notes: Justin Ison, \"Automated
Exploratory Testing\": Crawlers and Data Gatherers\' date:
\'2017-11-22T17:46:00.001-05:00\' author: T.J. Maher tags:
modified\_time: \'2017-12-04T15:25:01.027-05:00\' thumbnail:
https://i.ytimg.com/vi/s5k0XZtYTSU/default.jpg blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-6639401181897363678
blogger\_orig\_url:
http://www.tjmaher.com/2017/11/webinar-notes-justin-ison-automated.html
\-\-- Imagine if you could write an app that would handle the monotony
of gathering all the screenshots when performing user interface testing
on web, mobile and desktop apps. It could randomly crawl though the app
under test and collect screenshots that compared and contrasted
differences between:\
\

-   Browsers and platforms, such as IE9, IE10 & IE11 on the PC, Safari
    on the Mac, Chrome, Firefox, Safari on the iPhone, and Chrome on an
    Android device. 
-   Mobile devices such as a variety of Samsung Android devices,
    iPhones, and tablets.
-   Various screen resolutions and breakpoints for web & mobile apps
    that have a responsive web design. 
-   Various orientations, such as portrait and landscape. 
-   Localization Testing: How the site keeps (or doesn\'t keep) its
    layout when the text is changed to Spanish, German (with its much
    longer words), Russian (with its Cyrillic alphabet), Arabic, or
    Hindi. 
-   How mobile apps behave if you do taps, presses, long presses, or
    swipes. 

<div>

**Justin Ison** \< [\@isonic1](https://twitter.com/isonic1) \>, Senior
Success Engineer at Applitools, did just that! 

</div>

<div>

\

</div>

<div>

\
If his name sounds familiar, it is because I wrote in Mid-November
[about attending an Applitools Eyes training
session](http://www.tjmaher.com/2017/11/exploring-applitools-visual-testing.html)
that he gave me.

</div>

<div>

[]{#more}

Automated Exploratory Testing
-----------------------------

</div>

<div>

-   *A [Software Testing
    Pro](https://www.softwaretestpro.com/training/automated-exploratory-testing/)
    webinar*
-   November 22, 2017 @ 12:00 noon EST

</div>

\
\
Agile Software Development moves fast.\
\
The time to market gets shorter and shorter.\
\
More and more companies are using QA-Less companies, relying on what
Justin \-- a former Microsoft employee \-- refers to
as [telemetry](http://www.zdnet.com/article/windows-10-telemetry-secrets/)
(analytics).\
\
\... What is a QA Engineer at one of these companies to do?\
\
The problem with relying on solely analytics instead of a QA Engineer?\
\

-   You don't see design flaws  
-   You aren\'t catching UI issues
-   You are opening up your company to poor opinions about the quality
    of your product and your company. 

Take the **Testing Pyramid,** a testing component model [Adventures in
Automation blogged about
before](http://www.tjmaher.com/2016/02/testing-beyond-ui-testing-pyramid.html).
It consisted of, as Justin saw it, of:\
\

-   Automated Gui Tests: Used sparingly
-   Automated API Tests
-   Automated Integration Tests
-   Automated Component Tests
-   Automated Unit tests: All testing rests on this

What if Justin could create an app that covered what he thought of
\"**Automated Exploratory Tests**\" (**AET)**, a bot that would randomly
explore an app, hunting, gathering, and storing data for later analysis
by a trained QA Engineer? That AET could rest on top of the pyramid with
the graphical user interface testing.\
\
Justin goal was to do the best he could to figure out a way to do
automated exploratory testing,  shortening the release and testing
time.\

 Gathering Data Is Time Consuming
---------------------------------

<div>

\
In my own personal experience, gathering all the data, the screenshots,
and comparing and contrasting is a very risk-prone activity. The more
data gathered, the more details get missed due to tester fatigue.\

-   Let\'s say that we want to test a five page web application in MS
    Edge on the PC, Chrome & Firefox on the PC and Mac, and Safari on
    the Mac. That\'s five different pages with six different browsers (
    5 \* 6), which is thirty screens to review. 
-   If the entire web application is responsive, changing its look
    depending on the size of the screen, such as the width of a large
    desktop, a tablet, or a mobile phone, that becomes (5 \* 6 \* 3)
    ninety screens to review. 
-   Performing this full range of testing on four similar sites, such as
    [Stop & Shop](https://stopandshop.com/),
    [Giant-Carlisle](https://giantfoodstores.com/),
    [Giant-Landover](https://giantfood.com/), and
    [Martin\'s](https://martinsfoods.com/), and all (5 \* 6 \* 3 \* 4)
    three hundred and sixty will drive you mad!

Let\'s say a tester only spends five minutes per page to check: 

</div>

<div>

-   The basic layout
-   The text, from the font color, font text and font size
-   The images and their quality 
-   Every aspect, from the header text, to all the content and text
    down, down, down below the fold, all the way to the footer
    navigation

\... Five minutes \* 360 screens divided by 60: That is 30 person hours
to test everything sufficiently! 

</div>

<div>

\

</div>

<div>

Now, imagine doing this every two weeks\...

</div>

<div>

\

</div>

<div>

Welcome to the wonderful world of regression testing! 

</div>

<div>

\

</div>

<div>

Welcome to my world! \... Now you know how I became so gung-ho on
automation development.

</div>

 Should \"Automated Exploratory Testing\" Get a New Name?  
-----------------------------------------------------------

<div>

\
While I was listening to Justin talk about what he called \"Automated
Exploratory Testing\", I cringed a bit, worrying that by describing his
screenshot collection bot using those words, Automated Exploratory
Testing, that he may have accidentally opened up a can of worms. 

</div>

<div>

\

</div>

<div>

You see\... I\'ve found in the software industry a mistaken belief that
with automated testing as part of a continuous integration environment
and paired with DevOps, all Quality Assurance Engineers can be shoved
out the door. 

</div>

<div>

\

</div>

<div>

The Quality Assurance field started shoving back. 

</div>

<div>

\

</div>

<div>

There exists a school of thought called [Rapid Software
Testing](http://www.satisfice.com/info_rst.shtml) by [James
Bach](https://twitter.com/jamesmarcusbach) of [Satisfice,
Inc](http://www.satisfice.com/) and [Michael
Bolton](https://twitter.com/michaelbolton) of
[DevelopSense](http://www.developsense.com/) that has drawn a line in
the sand on how QA Engineers \-- excuse me \-- \"software testers\" \--
describe how they talk about the work they do. 

</div>

<div>

-   Michael Bolton put a stake in the ground with his November 2017
    article \"[The End of Manual
    Testing](http://www.developsense.com/blog/2017/11/the-end-of-manual-testing/)\"
    arguing against ever using the term \"manual testing\" to describe
    testing not involving coding. 
-   James Bach in March 2013 wrote \"[Testing and Checking
    Refined](http://www.satisfice.com/blog/archives/856)\" arguing that
    ONLY human beings can learn \"by experimenting, including study,
    questions, modeling, observation, inference, etc\", therefore
    automation should NEVER be called \"automated testing\". 
-   James Bach also advised people use the simpler term \"Tester\"
    instead of \"Software Quality Assurance Engineer\" or \"QA
    Engineer\", in his 2013 blog entry, \"[To The New
    Tester](http://www.satisfice.com/blog/archives/958)\". It\'s
    actually a misnomer, since as Michael Bolton once asked me, \"How
    can one assure quality\"?

<div>

When I started getting active in the online software testing community
outside my local community back in January, I quickly realized I\'d
accidentally start a flame war on the internets if I used the commonly
used words in the Boston software field \-- terms that I adopted when I
first joined the software testing world two decades ago and still
identify with \-- \"*automated testing*\", \"*QA*\", \"*Quality
Assurance*\". 

</div>

</div>

<div>

\

</div>

<div>

\... My experience butting against this has been hideously stressful.
What would their reaction be when they saw Justin use the phrase
\"exploratory testing\" linked with automation? 

</div>

<div>

\

</div>

Capabilities of the Crawler
---------------------------

<div>

\
With the bot Justin was using, the automation did not actually replace
the exploratory testing. The automation simply gathers the data,
screenshots, and metrics. You still would need a trained QA engineer to
analyze and make sense out of the data.

</div>

<div>

The crawler bot captured elements for every unique view:

</div>

<div>

-   For every reslotion 
-   For every orientation 

It found: 

</div>

<div>

-   A solution for everyone to easily see the current app state, even if
    they didn\'t have the image in front of them,
-   Language and localization issues 
-   Performance data 
-   Unique telemetry data, randomizing testing

</div>

<div>

It also could replay a crawl after a code fix.\
\
**[UI Checking:]{.underline}**\

-   What does it look like on a tablet? Do the images look stretched? 
-   Accessibility detection: Do all elements have accessibility labels?
    You can map it to the UI.

</div>

<div>

\
\
**[Performance Testing: ]{.underline}**

</div>

<div>

\

</div>

<div>

What Justin terms a "Forgotten Test".  

</div>

<div>

-   "It is imperative to know more about what's happening under-the-hood
    of your mobile application".
-   You are \"monitoring the memory, cpu and application size."
-   You could get this information. Store it. Benchmark it. See if
    performance is getting better or worse.

\
[**Language Detection:**]{.underline}

</div>

<div>

Justin dug into all the open source translation libraries. There were
seven in them he found \... but none of them worked the way he wanted,
so he relented and used a paid service: **Google Translate**.

</div>

<div>

\

</div>

<div>

It provided the best results compared to any open source tools he tried.
To save costs, he didn't do it every time, just before every release.\
\
**[Log Monitoring:]{.underline}**\
\
"When performing exploraory testing, it's very important to monitor the
logs at the same time\".

</div>

<div>

\

</div>

<div>

Many errors go unnoticed in the UI such as the network API or memory
errors.\

 Future Plans? The Crawler Will Be Converted to an Open Source Project!
-----------------------------------------------------------------------

\
Coming soon, the crawler he created will be released to GitHub.com! It
consists of:

</div>

<div>

-   Operating from a Command Line 
-   Integrated with Appium
-   Rules where it can and can\'t go is written in
    [TOML](https://github.com/toml-lang/toml). 

 Parting Words? Creating His Tool Has Had Its Ups and Downs
-----------------------------------------------------------

<div>

\
Justin has been somewhere between \"Hrm\" and \"Hey!!!!\" \... Thank you
Justin for sharing your experience!

</div>

<div>

\

</div>

::: {.separator style="clear: both; text-align: center;"}
[![](https://1.bp.blogspot.com/-0ZyVG5jK5-o/WhX9zMRj5zI/AAAAAAAAMKc/H5rERrtdkhkVsu6ITquObh_lUugBt1R5wCLcBGAs/s640/GoToWebinar%2B001.png){width="640"
height="465"}](https://1.bp.blogspot.com/-0ZyVG5jK5-o/WhX9zMRj5zI/AAAAAAAAMKc/H5rERrtdkhkVsu6ITquObh_lUugBt1R5wCLcBGAs/s1600/GoToWebinar%2B001.png)
:::

<div>

\

</div>

<div>

\

</div>

<div>

\

</div>

\
\
\
\
\
\
\
\
\
\
\
Happy Testing!\
\
-T.J. Maher\
[Twitter](https://twitter.com/tjmaher1) \| [LinkedIn](https://www.linkedin.com/in/tjmaher1) \| [GitHub](https://github.com/tjmaher)\
\
*// Sr. QA Engineer, Software Engineer in Test, Software Tester since
1996.\
// Contributing Writer
for [TechBeacon.](http://techbeacon.com/contributors/thomas-maher)\
// \"Looking to move away from manual QA? Follow [Adventures in
Automation](http://www.tjmaher.com/) on
[Facebook](https://www.facebook.com/AdventuresInAutomation/)!\"*\

</div>
