\-\-- layout: post title: \'Exploring Applitools, a visual testing tool
for web, mobile and Mac / Windows desktop applications. \' date:
\'2017-11-15T16:21:00.002-05:00\' author: T.J. Maher tags: - Applitools
modified\_time: \'2017-11-15T16:21:19.836-05:00\' thumbnail:
https://i.ytimg.com/vi/zSG9dXUdfAA/default.jpg blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-3301005036108620293
blogger\_orig\_url:
http://www.tjmaher.com/2017/11/exploring-applitools-visual-testing.html
\-\-- The life of a software tester can be difficult.\
\
Performing browser testing, comparing and contrasting all screens you
need to test on for just a single web page, the look-and-feel for all
the different combinations and permutations of browsers and platforms
can be even more difficult.\
\
Performing *regression testing* on an entire web site, confirming that
what once passed still passes, checking that each visual element, image,
font size, font style, font color, copyright date in the footer, privacy
policy link, and graphic, no matter how small, has the same
look-and-feel across all browsers, is its own special type of hell\...
Especially if it the regression tests have to be rerun, say, every two
weeks. This is why it is better to offload the repetitive tasks to a
system which performs visual testing.\
\
Why can regression testing the UI be difficult for a team of software
testers?\
\
[]{#more}\
\
**Repetition Fogs the Brain**:\

-   It\'s easy to get confused, when something looks off \... did this
    visual element actually change? Is it a bug or a feature? What did
    this page look like on Safari for the Mac last week and two weeks
    before? 

**It\'s Time Consuming**:\

-   Let\'s say that we want to test a five page web application in MS
    Edge on the PC, Chrome & Firefox on the PC and Mac, and Safari on
    the Mac. That\'s five different pages with six different browsers (
    5 \* 6), which is thirty screens to review. 
-   If the entire web application is ***responsive***, changing its look
    depending on the size of the screen, such as the width of a large
    desktop, a tablet, or a mobile phone, that becomes (5 \* 6 \* 3)
    ninety screens to review. 
-   Performing this full range of testing on four similar sites, such as
    [Stop & Shop](https://stopandshop.com/),
    [Giant-Carlisle](https://giantfoodstores.com/),
    [Giant-Landover](https://giantfood.com/), and
    [Martin\'s](https://martinsfoods.com/), and all (5 \* 6 \* 3 \* 4)
    three hundred and sixty will drive you mad! 

<div>

**Don\'t Test Everything? Details Will Get Missed:**

</div>

-   There is no way that one person can stay coherent checking that
    three hundred and sixty screens each and every time regression
    testing is performed. 
-   Once you divide up work, or try to scale back the tests to fit the
    time allotted for regression testing, as hard as you try, details
    will get missed.

<div>

</div>

\
**Archiving Test Results: A Bookkeeping Nightmare!**\

-   After executing these tests, where to put all the screenshots taken
    to prove that the look-and-feel of the product, the images, hasn\'t
    changed? 

<div>

**Your Testers\' Creativity Is Being Under-utilized:**

</div>

-   Skilled software testers doesn\'t want to follow a pre-programmed
    path, running the same tests over and over again. They want to do
    exploratory testing: Do a deep dive of the web application,
    exploring it, and find how it truly operates, take notes, make
    assumptions on how they think the system should work, and try them
    out. They want to break new ground, not trod down pre-determined
    paths. 

By forcing a tester to perform the same test over and over again,
checking if everything is *still* okay, after it already has been tested
thoroughly, you are forcing the tester to be like a machine. Why not
off-load all the repetition to some piece of software, and let the
software tester focus on the fun stuff?\
\
With this article, we are going to explore a tool that does just that,
**Applitools Eyes**, with the help of Justin Ison, (
[\@isonic1](https://twitter.com/isonic1) ) a Senior Success Engineer at
[Applitools](https://applitools.com/).\
\

What is Applitools?
-------------------

> \"Applitools was founded by software developers on a mission to
> shorten the release cycles of their product. Despite having good unit
> test coverage and automated end-to-end functional tests, a full manual
> regression of the UI, covering multiple operating systems, web
> browsers, screen resolutions and localizations, took days to
> complete.\
> \
> \"Back at the time, there were plenty of excellent commercial and
> open-source tools that allowed you to test the functionality of your
> app through the UI, but there were no tools that allowed you to
> automatically test the look & feel and user experience of your app.
> That is, verifying that each UI element in each page appears in the
> right color, shape, position and size, and that it does not overlap or
> hide other UI elements.\
> \
> \"After years of hard work carried out by experts, we successfully
> built a vast tech-stack that solved the automated visual testing
> problem\". *- [Applitools.com / About
> Applitools](https://applitools.com/about)*

\
[Back in May 2017, Moshe
Milman](http://www.tjmaher.com/2017/06/notes-on-moshe-milmans-talk-advanced.html),
the COO of Applitools gave the [Ministry of Testing -
Boston](https://www.meetup.com/ministry-of-testing-boston/events/239823300/) a
tour of their product. Although a recording of the presentation we
received wasn\'t recorded, the one given a week before in San Francisco
was, thanks to [Sauce
Labs](https://www.youtube.com/channel/UCzUaF3G8L5rfoh9xR6a51kg).\
\
**[View Moshe Milman Demo Applitools at Selenium Meetup]{.underline}**\
*\"Advanced Test Automation Techniques for Responsive Apps and Sites\"*\
*May 16, 2017*\

\
[*https://youtu.be/zSG9dXUdfAA*](https://youtu.be/zSG9dXUdfAA)\
\
\... Building on what Moshe Milman had presented us, I contacted
Applitools to see if I could schedule a further demo to see if it could
help out my client, [Ahold-Delhaize](https://www.aholddelhaize.com/),
test out their web sites.\
\

Our Guide To Applitools Eyes: Justin Ison
-----------------------------------------

\

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://2.bp.blogspot.com/-icdZEZOhX48/WgvHI_vxONI/AAAAAAAAMJw/8HIRF4JDPWc4dnlR4OsMOXy5Ewk5kofKQCLcBGAs/s200/justin.jpg){width="200" height="200"}](https://2.bp.blogspot.com/-icdZEZOhX48/WgvHI_vxONI/AAAAAAAAMJw/8HIRF4JDPWc4dnlR4OsMOXy5Ewk5kofKQCLcBGAs/s1600/justin.jpg)
                                                                                                                                     *Justin Ison*
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Justin Ison, a Senior Success Engineer at Applitools, has been working
in the software testing field for the past seventeen years, working not
just on Quality Assurance, but also Software and Automation development,
and managing teams of Software Engineers in Test.\
**[\
]{.underline}What Is a \"Senior Success Engineer\"?**\
\
\"Essentially an automation engineer to help onboard new clients and
assist you as you progress\". Justin helps clients with tools,
techniques, and best practices not just in Applitools Eyes. Justin also
helps out in automation.\
\
**What frameworks do you use to test Applitools?**\
\
Although Justin uses Ruby, because he comes from a Ruby background, he
really uses everything! \"Since I joined Applitools, I have been doing a
lot of Java, since it\'s our most popular SDK *\[Software Development
Kit\]*, and we tend to get a lot of questions around that.\" Justin
pointed out that Applitools support almost every major language.\
\

How To Get Started?
-------------------

To get started with Applitools, register for a [free individual trial
account](https://applitools.com/users/register), which comes with an API
key. That API Key is used each time the automation code you write
interacts with the Applitools product.\
\
Authentication Keys can be either for an individual or for a team. There
is also a Public API key a \"View Key\", which you can use to download
your images, such as the baseline images and changes Applitools
captures, and compare them yourself.\
*\
Unsure what an API is? Feel free to review from **Adventures in
Automation**:*\
\

-   [*Interacting with Twitter using
    Twitter4J*](http://www.tjmaher.com/2017/10/tinkering-with-twitter-1.html)
-   [*REST Assured, a Java
    library*](http://www.tjmaher.com/2017/02/are-you-sure-bus-line-still-listed.html)
-   [*API Testing with
    Postman*](http://www.tjmaher.com/2016/07/introduction-to-api-testing-with.html)
-   [*RESTful Testing with Apache HTTP
    Components*](http://www.tjmaher.com/2016/02/restful-testing-with-stripe-brief.html)

\
If you are looking for information about Applitools and how it works,
the first two ways Justin recommends exploring are:\
\

-   The **[Resources Library](https://applitools.com/resources/)** for a
    general overview
-   The Applitools **[GitHub
    repository](https://github.com/applitools)** to dive right into the
    code

<div>

For much more advances usage, you can view:

</div>

-   The [Applitools
    Wiki](https://applitools.atlassian.net/wiki/spaces/Java/overview),
    which contains [**the SDK
    guide**](https://applitools.atlassian.net/wiki/spaces/Java/pages/1540852/SDK+Guide),
    to dive right into each and every method Applitools uses. It also
    gives examples on how to initialize Applitools Eyes, create visual
    validation checkpoints, end tests, enabling logs, working & merging
    with branches, auto-saving on failures, forcing full page
    screenshots, hide scroll bars, setting scale ratios, and configuring
    proxy settings in the [Selenium -
    Ruby](https://applitools.atlassian.net/wiki/spaces/Java/pages/1540753/Selenium+-+Ruby),
    [Appium -
    Java](https://applitools.atlassian.net/wiki/spaces/Java/pages/1540331/Appium+-+Java),
    or [QTP /
    UFT](https://applitools.atlassian.net/wiki/spaces/Java/pages/1540511/QTP+UFT).

You can even search for answers to questions you may have at:\
\

-   The [**Applitools Support Center**](http://support.applitools.com/)
    portal. Type in a question, and get an answer! It also has a list of
    more FAQs, docs, and a Live Chat feature. 

\
\

About The Applitools Resource Library 
--------------------------------------

The Applitools **[Resources
Library](https://applitools.com/resources/)** is located
at [Applitools.com -\> Resources](https://applitools.com/resources/). It
contains:\

-   **Posts**, such as the one [from automation consultant Dave
    Haeffner](http://testautomation.applitools.com/post/105435804567/how-to-do-visual-testing-with-selenium),
    on how to automate with Applitools
-   **Documentation** on how to get started
-   [Webinars](http://testautomation.applitools.com/post/148047224072/webinar-recording-advanced-test-automation)
-   [Blog Posts](http://testautomation.applitools.com/)

\... It even has [Tutorials](https://applitools.com/resources/tutorial)
on how to install Applitools Eyes in four easy steps.\
**[\
]{.underline}**\

About The GitHub Examples
-------------------------

\
For even more detail, Applitools also has its own **GitHub page**
at <https://github.com/applitools> with code examples on how to
integrate with languages such as Java with some [Java
Examples](https://github.com/applitools/java-examples/tree/master/src/test/java)
on:\
\

-   Using Sauce Labs, and Browser Stack
-   Using Perfecto Mobile 
-   Testing in Parallel 
-   Using Crossbrowsertesting.com or a local Selenium grid.

\
These are the examples Justin sends to clients since, as he put it,
\"They are simple and straightfoward enough to get you going\".\
\
Justin pointed out that Applitools is *language and toolset agnostic*.
Your automation project doesn\'t have to be in Java. It can be paired
with Selenium or Appium in Java, JavaScript, C\#, PHP, Python, or Ruby.
It can be paired with other web automation tools such as Capybara,
Protractor or UFT / QTP. And it can be paired with mobile automation
tools such as XCUI (using Objective C or Swift) or Espresso. *( [View
More](https://applitools.com/resources/tutorial/) )*\
\
If you have a framework you like using, one that can take screenshots,
you can integrate it with the Applitools SDK. By using their [Images
SDK](http://support.applitools.com/customer/en/portal/articles/2170383-how-to-use-applitools-eyes-images-sdk-with-python-and-ruby)
you can upload your screenshots so Applitools can be used. They also
have tools such as as ***CLI*** so you can do all of this from the
command line.\
\

> [\"With dozens of SDKs targeting all major programming languages and
> test frameworks, it takes minutes to enhance your existing tests with
> visual assertions that validate entire application pages at a time
> with a single line of code. We support web, mobile and desktop apps as
> well as PDF files and raw screenshots\". *- [Applitools
> site](https://applitools.com/)*]{style="background-color: white; color: #2c2c2c; font-family: "poppins" , sans-serif; font-size: 16px;"}

\
It is not limited to Selenium, Appium, or Espresso.\
\

Get Started in Four Easy Steps 
-------------------------------

Let\'s say you wanted to test a site such as \"Hello World\":\

<div>

\

</div>

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://2.bp.blogspot.com/-yw930Rlsfh4/Wgyi_L3R1tI/AAAAAAAAMKA/QRqzuFrxwn8ms4KEa4aW-AzfVzDqb9nzQCLcBGAs/s400/Screen%2BShot%2B2017-11-15%2Bat%2B3.26.20%2BPM.png){width="400" height="196"}](https://2.bp.blogspot.com/-yw930Rlsfh4/Wgyi_L3R1tI/AAAAAAAAMKA/QRqzuFrxwn8ms4KEa4aW-AzfVzDqb9nzQCLcBGAs/s1600/Screen%2BShot%2B2017-11-15%2Bat%2B3.26.20%2BPM.png)
                                                                                                                                                            *Demo site: <https://applitools.com/helloworld>*
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

<div>

\

-   Go to the tutorial at <https://applitools.com/resources/tutorial/> 
-   Just click on the link for Selenium Java
-   Install the sdk and its dependencies into your own project by adding
    it to your Maven project pom.xml configuration file.

<div>

[\<[dependency]{.hljs-name
style="border: 0px; box-sizing: border-box; color: #000088; font-family: inherit; font-size: inherit; font-stretch: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; line-height: inherit; margin: 0px; padding: 0px; vertical-align: baseline;"}\>]{.hljs-tag
style="border: 0px; box-sizing: border-box; font-family: "consolas" , "monaco" , monospace; font-size: 14px; font-stretch: inherit; line-height: inherit; margin: 0px; padding: 0px; vertical-align: baseline; white-space: pre;"}[
]{style="background-color: #f9f9f9; font-family: "consolas" , "monaco" , monospace; font-size: 14px; white-space: pre;"}[\<[groupId]{.hljs-name
style="border: 0px; box-sizing: border-box; color: #000088; font-family: inherit; font-size: inherit; font-stretch: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; line-height: inherit; margin: 0px; padding: 0px; vertical-align: baseline;"}\>]{.hljs-tag
style="border: 0px; box-sizing: border-box; font-family: "consolas" , "monaco" , monospace; font-size: 14px; font-stretch: inherit; line-height: inherit; margin: 0px; padding: 0px; vertical-align: baseline; white-space: pre;"}[com.applitools]{style="background-color: #f9f9f9; font-family: "consolas" , "monaco" , monospace; font-size: 14px; white-space: pre;"}[\</[groupId]{.hljs-name
style="border: 0px; box-sizing: border-box; color: #000088; font-family: inherit; font-size: inherit; font-stretch: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; line-height: inherit; margin: 0px; padding: 0px; vertical-align: baseline;"}\>]{.hljs-tag
style="border: 0px; box-sizing: border-box; font-family: "consolas" , "monaco" , monospace; font-size: 14px; font-stretch: inherit; line-height: inherit; margin: 0px; padding: 0px; vertical-align: baseline; white-space: pre;"}[
]{style="background-color: #f9f9f9; font-family: "consolas" , "monaco" , monospace; font-size: 14px; white-space: pre;"}[\<[artifactId]{.hljs-name
style="border: 0px; box-sizing: border-box; color: #000088; font-family: inherit; font-size: inherit; font-stretch: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; line-height: inherit; margin: 0px; padding: 0px; vertical-align: baseline;"}\>]{.hljs-tag
style="border: 0px; box-sizing: border-box; font-family: "consolas" , "monaco" , monospace; font-size: 14px; font-stretch: inherit; line-height: inherit; margin: 0px; padding: 0px; vertical-align: baseline; white-space: pre;"}[eyes-selenium-java3]{style="background-color: #f9f9f9; font-family: "consolas" , "monaco" , monospace; font-size: 14px; white-space: pre;"}[\</[artifactId]{.hljs-name
style="border: 0px; box-sizing: border-box; color: #000088; font-family: inherit; font-size: inherit; font-stretch: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; line-height: inherit; margin: 0px; padding: 0px; vertical-align: baseline;"}\>]{.hljs-tag
style="border: 0px; box-sizing: border-box; font-family: "consolas" , "monaco" , monospace; font-size: 14px; font-stretch: inherit; line-height: inherit; margin: 0px; padding: 0px; vertical-align: baseline; white-space: pre;"}[
]{style="background-color: #f9f9f9; font-family: "consolas" , "monaco" , monospace; font-size: 14px; white-space: pre;"}[\<[version]{.hljs-name
style="border: 0px; box-sizing: border-box; color: #000088; font-family: inherit; font-size: inherit; font-stretch: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; line-height: inherit; margin: 0px; padding: 0px; vertical-align: baseline;"}\>]{.hljs-tag
style="border: 0px; box-sizing: border-box; font-family: "consolas" , "monaco" , monospace; font-size: 14px; font-stretch: inherit; line-height: inherit; margin: 0px; padding: 0px; vertical-align: baseline; white-space: pre;"}[RELEASE]{style="background-color: #f9f9f9; font-family: "consolas" , "monaco" , monospace; font-size: 14px; white-space: pre;"}[\</[version]{.hljs-name
style="border: 0px; box-sizing: border-box; color: #000088; font-family: inherit; font-size: inherit; font-stretch: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; line-height: inherit; margin: 0px; padding: 0px; vertical-align: baseline;"}\>]{.hljs-tag
style="border: 0px; box-sizing: border-box; font-family: "consolas" , "monaco" , monospace; font-size: 14px; font-stretch: inherit; line-height: inherit; margin: 0px; padding: 0px; vertical-align: baseline; white-space: pre;"}[]{style="background-color: #f9f9f9; font-family: "consolas" , "monaco" , monospace; font-size: 14px; white-space: pre;"}[\</[dependency]{.hljs-name
style="border: 0px; box-sizing: border-box; color: #000088; font-family: inherit; font-size: inherit; font-stretch: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; line-height: inherit; margin: 0px; padding: 0px; vertical-align: baseline;"}\>]{.hljs-tag
style="border: 0px; box-sizing: border-box; font-family: "consolas" , "monaco" , monospace; font-size: 14px; font-stretch: inherit; line-height: inherit; margin: 0px; padding: 0px; vertical-align: baseline; white-space: pre;"}

</div>

-   After all the dependencies are installed, you can start running
    tests.

After you set your API key, you can embed Applitools with your own code
by:\
\

-   Initializing the Eyes class.
-   Starting the tools with Eyes.open

<div>

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 // Open a Chrome browser.  
     WebDriver driver = new ChromeDriver();  
     // Initialize the eyes SDK and set your private API key.  
     Eyes eyes = new Eyes();  
     eyes.setApiKey("YOUR_API_KEY");  
```

</div>

-   Passing in your driver objects the parameters that defines the
    baseline.

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
     try{  
       // Start the test and set the browser's viewport size to 800x600.  
       eyes.open(driver, "Hello World!", "My first Selenium Java test!",  
           new RectangleSize(800, 600));  
       // Navigate the browser to the "hello world!" web-site.  
       driver.get("https://applitools.com/helloworld");  
       // Visual checkpoint #1.  
       eyes.checkWindow("Hello!");  
       // Click the "Click me!" button.  
       driver.findElement(By.tagName("button")).click();  
       // Visual checkpoint #2.  
       eyes.checkWindow("Click!");  
       // End the test.  
       eyes.close();  
     }  
```

\
Notice that with eyes.open, we are passing in the WebDriver instance,
the app we are testing, and the Viewport size, along with the browser
version (Chrome or Firefox), and Operating System (OSX, Windows 7,
etc).\
\
The code above would:\

-   Initialize a new Selenium WebDriver browser
-   Open a new browser window, 800 by 600 pixels
-   Go to <https://applitools.com/helloworld>
-   Check the window, \"Hello\"
-   Click on the \"Click Me\" button
-   Check what the results were.

<div>

\... A Results Object would be returned at the end of the test.\
\
Once this baseline has been set, it will be compared with all following
instances this script is run. Screenshots will be stored in the
Applitools cloud-based **Applitools Eyes Test Manager**. Sign into your
Applitools account to access it.\
\
\

</div>

**Getting started with the Applitools Eyes Test Manager**

*<https://youtu.be/dGwxD6OWLAI>*\
\

Why Does a Viewport Size Matter?
--------------------------------

Take a look at the Responsive Website,
[StopAndShop.com](http://stopandshop.com/), that our Ahold - Chicago
team released in May 2017. Many different breakpoints have been set:\
\

-   Full screen, the **Register** and **Sign In** button are separate.
-   Narrow the screen a bit more, emulating the viewable screen of a
    tablet, and the buttons merge into a **Menu** button. 
-   Narrow it a bit more, such as on a Phone / Tablet (\"Phablet\"), the
    page changes a bit more. 
-   Narrow it all the way, and the entire screen adjusts to what it
    would look like in Mobile Chrome on an Android device, or Safari on
    an iPhone. 

\
To test a responsive site like this in Applitools, set your viewport
size every time you run your test. By performing a \"checkWindow\" you
are capturing the browser window you have defined.\
\
You can also pass in a method to take a full screenshot, or narrow it
down to a \"checkRegion\", such as a header or a footer:\
\

-   Go to [StopAndShop.com](http://stopandshop.com/), making the screen
    wide
-   Scroll all the way down the page.
-   See if you can find the links for \"**Terms of Service**\" and
    \"**Privacy Policy**\"

\
This footer element for [Stopandshop.com](http://stopandshop.com/) can
easily be forgotten when checking to see if everything is okay with the
page layout. Once you set up and capture the baseline, that baseline
will be matched exactly in later iterations.\
\
Other features:\
\

-   Create multiple baselines for different viewport sizes.
-   Capture all visual image changes, such as to any paragraph image,
    buttons, and colors!
-   Although it is not recommended, you can also leave the algorithm
    that compares and contrasts screenshots to be ***strict***. Strict
    means comparing each image pixel by pixel. 
-   Since you are just comparing screenshots to do visual checking, you
    don\'t have to update your page objects each time an image element
    changes. 

\
\

How To View More Information About Applitools Classes and Methods?
------------------------------------------------------------------

\
For more in-depth information regarding Applitools Classes and Methods,
go to the Applitools Wiki in t[he SDK
Guide](https://applitools.atlassian.net/wiki/spaces/Java/pages/1540852/SDK+Guide).\

-   Want to capture an entire page, you just want to capture that region
    such as a footer, and you are not sure about the checkRegion method,
    and you are using Selenium WebDriver + Java? Go to the [Visual
    Validation
    section](https://applitools.atlassian.net/wiki/spaces/Java/pages/1540312/Selenium+-+Java#Selenium-Java-visualvalidationjava)!

> \"Check region method works in a similar way to check window, except
> for the fact that it takes a screenshot of the HTML element specified
> as its input (by means of a WebDriver \"By\" selector) instead of a
> screenshot of the entire web page. The check region command will take
> a snapshot of the specific object, regardless of where it appears in
> the page, and will perform smart visual comparison of that region with
> the baseline. In case this is a new region that does not exist in the
> baseline, this region will be added as a new region to the baseline\".
> *- [Applitools Wiki / Selenium / Java / Visual
> Validation](https://applitools.atlassian.net/wiki/spaces/Java/pages/1540312/Selenium+-+Java#Selenium-Java-visualvalidationjava)*

::: {.code .panel .pdl .conf-macro .output-block data-hasbody="true" data-macro-id="b80fb5c5-af71-4e68-8d85-7aebd8246d62" data-macro-name="code" style="background-color: white; border-radius: 3px; border: 1px solid rgb(204, 204, 204); color: #333333; font-family: -apple-system, system-ui, "Segoe UI", Roboto, "Noto Sans", Ubuntu, "Droid Sans", "Helvetica Neue", sans-serif; font-size: 14px; margin: 10px 0px; overflow: auto; padding: 0px;"}
::: {.codeContent .panelContent .pdl style="background-attachment: initial; background-clip: initial; background-image: initial; background-origin: initial; background-position: initial; background-repeat: initial; background-size: initial; border-bottom-left-radius: 3px; border-bottom-right-radius: 3px; line-height: 20px; margin: 0px; overflow: hidden; padding: 0px;"}
::: {style="margin: 0px; padding: 0px;"}
::: {#highlighter_4078 .syntaxhighlighter .sh-confluence .nogutter .java style="font-size: 1em; margin: 0px; overflow: auto; padding: 0px; position: relative; width: 417px;"}
+-----------------------------------------------------------------------+
| ::: {.container style="background: 0px center; border-radius: 0px; bo |
| rder: 0px; bottom: auto; box-sizing: content-box; float: none; height |
| : auto; left: auto; line-height: 20px; margin: 15px 0px 0px; min-heig |
| ht: inherit; outline: 0px; overflow: visible; padding: 0px 0px 15px;  |
| position: relative; right: auto; top: auto; vertical-align: baseline; |
|  white-space: pre-wrap; width: auto;" title="Hint: double-click to se |
| lect code"}                                                           |
| ::: {.line .number1 .index0 .alt2 style="background: 0px center; bord |
| er-radius: 0px; border: 0px; bottom: auto; box-sizing: content-box; f |
| loat: none; height: auto; left: auto; line-height: 20px; margin: 0px; |
|  min-height: inherit; outline: 0px; overflow: visible; padding: 0px 1 |
| em 0px 0px; position: static; right: auto; top: auto; vertical-align: |
|  baseline; white-space: nowrap; width: auto;"}                        |
| `eyes.checkRegion(selector);`{.java .plain                            |
| style="background: 0px center; border-radius: 0px; border: 0px; botto |
| m: auto; box-sizing: content-box; float: none; font-family: Consolas, |
|  "Bitstream Vera Sans Mono", "Courier New", Courier, monospace; heigh |
| t: auto; left: auto; line-height: 20px; margin: 0px; min-height: inhe |
| rit; outline: 0px; overflow: visible; padding: 0px; position: static; |
|  right: auto; top: auto; vertical-align: baseline; width: auto;"}     |
| :::                                                                   |
|                                                                       |
| ::: {.line .number2 .index1 .alt1 style="background: 0px center; bord |
| er-radius: 0px; border: 0px; bottom: auto; box-sizing: content-box; f |
| loat: none; height: auto; left: auto; line-height: 20px; margin: 0px; |
|  min-height: inherit; outline: 0px; overflow: visible; padding: 0px 1 |
| em 0px 0px; position: static; right: auto; top: auto; vertical-align: |
|  baseline; white-space: nowrap; width: auto;"}                        |
| `eyes.checkRegion(selector, stitchContent);`{.java .plain             |
| style="background: 0px center; border-radius: 0px; border: 0px; botto |
| m: auto; box-sizing: content-box; float: none; font-family: Consolas, |
|  "Bitstream Vera Sans Mono", "Courier New", Courier, monospace; heigh |
| t: auto; left: auto; line-height: 20px; margin: 0px; min-height: inhe |
| rit; outline: 0px; overflow: visible; padding: 0px; position: static; |
|  right: auto; top: auto; vertical-align: baseline; width: auto;"}     |
| :::                                                                   |
|                                                                       |
| ::: {.line .number3 .index2 .alt2 style="background: 0px center; bord |
| er-radius: 0px; border: 0px; bottom: auto; box-sizing: content-box; f |
| loat: none; height: auto; left: auto; line-height: 20px; margin: 0px; |
|  min-height: inherit; outline: 0px; overflow: visible; padding: 0px 1 |
| em 0px 0px; position: static; right: auto; top: auto; vertical-align: |
|  baseline; white-space: nowrap; width: auto;"}                        |
| `eyes.checkRegion(selector, matchTimeout, tag);`{.java .plain         |
| style="background: 0px center; border-radius: 0px; border: 0px; botto |
| m: auto; box-sizing: content-box; float: none; font-family: Consolas, |
|  "Bitstream Vera Sans Mono", "Courier New", Courier, monospace; heigh |
| t: auto; left: auto; line-height: 20px; margin: 0px; min-height: inhe |
| rit; outline: 0px; overflow: visible; padding: 0px; position: static; |
|  right: auto; top: auto; vertical-align: baseline; width: auto;"}     |
| :::                                                                   |
|                                                                       |
| ::: {.line .number4 .index3 .alt1 style="background: 0px center; bord |
| er-radius: 0px; border: 0px; bottom: auto; box-sizing: content-box; f |
| loat: none; height: auto; left: auto; line-height: 20px; margin: 0px; |
|  min-height: inherit; outline: 0px; overflow: visible; padding: 0px 1 |
| em 0px 0px; position: static; right: auto; top: auto; vertical-align: |
|  baseline; white-space: nowrap; width: auto;"}                        |
| `eyes.checkRegion(selector, matchTimeout, tag, stitchContent);`{.java |
| .plain                                                                |
| style="background: 0px center; border-radius: 0px; border: 0px; botto |
| m: auto; box-sizing: content-box; float: none; font-family: Consolas, |
|  "Bitstream Vera Sans Mono", "Courier New", Courier, monospace; heigh |
| t: auto; left: auto; line-height: 20px; margin: 0px; min-height: inhe |
| rit; outline: 0px; overflow: visible; padding: 0px; position: static; |
|  right: auto; top: auto; vertical-align: baseline; width: auto;"}     |
| :::                                                                   |
|                                                                       |
| ::: {.line .number5 .index4 .alt2 style="background: 0px center; bord |
| er-radius: 0px; border: 0px; bottom: auto; box-sizing: content-box; f |
| loat: none; height: auto; left: auto; line-height: 20px; margin: 0px; |
|  min-height: inherit; outline: 0px; overflow: visible; padding: 0px 1 |
| em 0px 0px; position: static; right: auto; top: auto; vertical-align: |
|  baseline; white-space: nowrap; width: auto;"}                        |
| `eyes.checkRegion(selector, tag);`{.java .plain                       |
| style="background: 0px center; border-radius: 0px; border: 0px; botto |
| m: auto; box-sizing: content-box; float: none; font-family: Consolas, |
|  "Bitstream Vera Sans Mono", "Courier New", Courier, monospace; heigh |
| t: auto; left: auto; line-height: 20px; margin: 0px; min-height: inhe |
| rit; outline: 0px; overflow: visible; padding: 0px; position: static; |
|  right: auto; top: auto; vertical-align: baseline; width: auto;"}     |
| :::                                                                   |
|                                                                       |
| ::: {.line .number6 .index5 .alt1 style="background: 0px center; bord |
| er-radius: 0px; border: 0px; bottom: auto; box-sizing: content-box; f |
| loat: none; height: auto; left: auto; line-height: 20px; margin: 0px; |
|  min-height: inherit; outline: 0px; overflow: visible; padding: 0px 1 |
| em 0px 0px; position: static; right: auto; top: auto; vertical-align: |
|  baseline; white-space: nowrap; width: auto;"}                        |
| `eyes.checkRegion(selector, tag, stitchContent);`{.java .plain        |
| style="background: 0px center; border-radius: 0px; border: 0px; botto |
| m: auto; box-sizing: content-box; float: none; font-family: Consolas, |
|  "Bitstream Vera Sans Mono", "Courier New", Courier, monospace; heigh |
| t: auto; left: auto; line-height: 20px; margin: 0px; min-height: inhe |
| rit; outline: 0px; overflow: visible; padding: 0px; position: static; |
|  right: auto; top: auto; vertical-align: baseline; width: auto;"}     |
| :::                                                                   |
|                                                                       |
| ::: {.line .number7 .index6 .alt2 style="background: 0px center; bord |
| er-radius: 0px; border: 0px; bottom: auto; box-sizing: content-box; f |
| loat: none; height: auto; left: auto; line-height: 20px; margin: 0px; |
|  min-height: inherit; outline: 0px; overflow: visible; padding: 0px 1 |
| em 0px 0px; position: static; right: auto; top: auto; vertical-align: |
|  baseline; white-space: nowrap; width: auto;"}                        |
| `eyes.checkRegion(region);`{.java .plain                              |
| style="background: 0px center; border-radius: 0px; border: 0px; botto |
| m: auto; box-sizing: content-box; float: none; font-family: Consolas, |
|  "Bitstream Vera Sans Mono", "Courier New", Courier, monospace; heigh |
| t: auto; left: auto; line-height: 20px; margin: 0px; min-height: inhe |
| rit; outline: 0px; overflow: visible; padding: 0px; position: static; |
|  right: auto; top: auto; vertical-align: baseline; width: auto;"}     |
| :::                                                                   |
|                                                                       |
| ::: {.line .number8 .index7 .alt1 style="background: 0px center; bord |
| er-radius: 0px; border: 0px; bottom: auto; box-sizing: content-box; f |
| loat: none; height: auto; left: auto; line-height: 20px; margin: 0px; |
|  min-height: inherit; outline: 0px; overflow: visible; padding: 0px 1 |
| em 0px 0px; position: static; right: auto; top: auto; vertical-align: |
|  baseline; white-space: nowrap; width: auto;"}                        |
| `eyes.checkRegion(region, matchTimeout, tag);`{.java .plain           |
| style="background: 0px center; border-radius: 0px; border: 0px; botto |
| m: auto; box-sizing: content-box; float: none; font-family: Consolas, |
|  "Bitstream Vera Sans Mono", "Courier New", Courier, monospace; heigh |
| t: auto; left: auto; line-height: 20px; margin: 0px; min-height: inhe |
| rit; outline: 0px; overflow: visible; padding: 0px; position: static; |
|  right: auto; top: auto; vertical-align: baseline; width: auto;"}     |
| :::                                                                   |
|                                                                       |
| ::: {.line .number9 .index8 .alt2 style="background: 0px center; bord |
| er-radius: 0px; border: 0px; bottom: auto; box-sizing: content-box; f |
| loat: none; height: auto; left: auto; line-height: 20px; margin: 0px; |
|  min-height: inherit; outline: 0px; overflow: visible; padding: 0px 1 |
| em 0px 0px; position: static; right: auto; top: auto; vertical-align: |
|  baseline; white-space: nowrap; width: auto;"}                        |
| `eyes.checkRegion(element);`{.java .plain                             |
| style="background: 0px center; border-radius: 0px; border: 0px; botto |
| m: auto; box-sizing: content-box; float: none; font-family: Consolas, |
|  "Bitstream Vera Sans Mono", "Courier New", Courier, monospace; heigh |
| t: auto; left: auto; line-height: 20px; margin: 0px; min-height: inhe |
| rit; outline: 0px; overflow: visible; padding: 0px; position: static; |
|  right: auto; top: auto; vertical-align: baseline; width: auto;"}     |
| :::                                                                   |
|                                                                       |
| ::: {.line .number10 .index9 .alt1 style="background: 0px center; bor |
| der-radius: 0px; border: 0px; bottom: auto; box-sizing: content-box;  |
| float: none; height: auto; left: auto; line-height: 20px; margin: 0px |
| ; min-height: inherit; outline: 0px; overflow: visible; padding: 0px  |
| 1em 0px 0px; position: static; right: auto; top: auto; vertical-align |
| : baseline; white-space: nowrap; width: auto;"}                       |
| `eyes.checkRegion(element, stitchContent);`{.java .plain              |
| style="background: 0px center; border-radius: 0px; border: 0px; botto |
| m: auto; box-sizing: content-box; float: none; font-family: Consolas, |
|  "Bitstream Vera Sans Mono", "Courier New", Courier, monospace; heigh |
| t: auto; left: auto; line-height: 20px; margin: 0px; min-height: inhe |
| rit; outline: 0px; overflow: visible; padding: 0px; position: static; |
|  right: auto; top: auto; vertical-align: baseline; width: auto;"}     |
| :::                                                                   |
|                                                                       |
| ::: {.line .number11 .index10 .alt2 style="background: 0px center; bo |
| rder-radius: 0px; border: 0px; bottom: auto; box-sizing: content-box; |
|  float: none; height: auto; left: auto; line-height: 20px; margin: 0p |
| x; min-height: inherit; outline: 0px; overflow: visible; padding: 0px |
|  1em 0px 0px; position: static; right: auto; top: auto; vertical-alig |
| n: baseline; white-space: nowrap; width: auto;"}                      |
| `eyes.checkRegion(element, matchTimeout, tag);`{.java .plain          |
| style="background: 0px center; border-radius: 0px; border: 0px; botto |
| m: auto; box-sizing: content-box; float: none; font-family: Consolas, |
|  "Bitstream Vera Sans Mono", "Courier New", Courier, monospace; heigh |
| t: auto; left: auto; line-height: 20px; margin: 0px; min-height: inhe |
| rit; outline: 0px; overflow: visible; padding: 0px; position: static; |
|  right: auto; top: auto; vertical-align: baseline; width: auto;"}     |
| :::                                                                   |
|                                                                       |
| ::: {.line .number12 .index11 .alt1 style="background: 0px center; bo |
| rder-radius: 0px; border: 0px; bottom: auto; box-sizing: content-box; |
|  float: none; height: auto; left: auto; line-height: 20px; margin: 0p |
| x; min-height: inherit; outline: 0px; overflow: visible; padding: 0px |
|  1em 0px 0px; position: static; right: auto; top: auto; vertical-alig |
| n: baseline; white-space: nowrap; width: auto;"}                      |
| `eyes.checkRegion(element, matchTimeout, tag, stitchContent);`{.java  |
| .plain                                                                |
| style="background: 0px center; border-radius: 0px; border: 0px; botto |
| m: auto; box-sizing: content-box; float: none; font-family: Consolas, |
|  "Bitstream Vera Sans Mono", "Courier New", Courier, monospace; heigh |
| t: auto; left: auto; line-height: 20px; margin: 0px; min-height: inhe |
| rit; outline: 0px; overflow: visible; padding: 0px; position: static; |
|  right: auto; top: auto; vertical-align: baseline; width: auto;"}     |
| :::                                                                   |
|                                                                       |
| ::: {.line .number13 .index12 .alt2 style="background: 0px center; bo |
| rder-radius: 0px; border: 0px; bottom: auto; box-sizing: content-box; |
|  float: none; height: auto; left: auto; line-height: 20px; margin: 0p |
| x; min-height: inherit; outline: 0px; overflow: visible; padding: 0px |
|  1em 0px 0px; position: static; right: auto; top: auto; vertical-alig |
| n: baseline; white-space: nowrap; width: auto;"}                      |
| `eyes.checkRegion(element, tag);`{.java .plain                        |
| style="background: 0px center; border-radius: 0px; border: 0px; botto |
| m: auto; box-sizing: content-box; float: none; font-family: Consolas, |
|  "Bitstream Vera Sans Mono", "Courier New", Courier, monospace; heigh |
| t: auto; left: auto; line-height: 20px; margin: 0px; min-height: inhe |
| rit; outline: 0px; overflow: visible; padding: 0px; position: static; |
|  right: auto; top: auto; vertical-align: baseline; width: auto;"}     |
| :::                                                                   |
|                                                                       |
| ::: {.line .number14 .index13 .alt1 style="background: 0px center; bo |
| rder-radius: 0px; border: 0px; bottom: auto; box-sizing: content-box; |
|  float: none; height: auto; left: auto; line-height: 20px; margin: 0p |
| x; min-height: inherit; outline: 0px; overflow: visible; padding: 0px |
|  1em 0px 0px; position: static; right: auto; top: auto; vertical-alig |
| n: baseline; white-space: nowrap; width: auto;"}                      |
| `eyes.checkRegion(element, tag, stitchContent);`{.java .plain         |
| style="background: 0px center; border-radius: 0px; border: 0px; botto |
| m: auto; box-sizing: content-box; float: none; font-family: Consolas, |
|  "Bitstream Vera Sans Mono", "Courier New", Courier, monospace; heigh |
| t: auto; left: auto; line-height: 20px; margin: 0px; min-height: inhe |
| rit; outline: 0px; overflow: visible; padding: 0px; position: static; |
|  right: auto; top: auto; vertical-align: baseline; width: auto;"}     |
| :::                                                                   |
| :::                                                                   |
+-----------------------------------------------------------------------+
:::
:::
:::
:::

\
Pass in the footer element to a checkRegion, and you can set a baseline
for just that region.\
\
\

Since Appium Can Test Desktop Apps, Applitools Can Test Desktop Apps!
---------------------------------------------------------------------

We\'ve mentioned **Appium**, the mobile testing tool for Android and IOS
mobile devices, quite frequently [here on Adventures in
Automation](http://www.tjmaher.com/search?q=appium).\
\
Back in April 2017, Dan Cuellar, the creator of Appium announced at
Selenium Conf Austin 2017 that with Microsoft\'s and Intuit\'s
contributions, [Appium can automate both Windows and Mac Desktop
applications](http://www.tjmaher.com/2017/04/seconf2017-microsoft-is-automating.html)!\
\
Justin Ison pointed out that since Applitools is fully integrated with
Appium, Applitools can perform visual checking on Mac and Windows
Desktop Apps!\
\

Applitools Does Layout Testing 
-------------------------------

Take a look at the responsive website [Stop &
Shop](https://stopandshop.com/), [Giant-Carlisle](https://giantfoodstores.com/), [Giant-Landover](https://giantfood.com/),
and [Martin\'s](https://martinsfoods.com/), opening each site in a
separate tab.\
\
If you flip back-and-forth between the sites, you notice that the sites
have basically the same functionality, except for each site\'s unique
brand.\
\
If you wanted to compare and contrast each site, you can set the Match
Level of the comparison algorithms to \"Layout\".\
\
**How to Configure Match Level \[Advanced Visual Test Automation
Techniques\]**

*<https://youtu.be/DzO-uzOLjUY>*\
\
In the same way, a tester can perform **localization testing**:\
\

-   Pull up a site using English as a language
-   Pull up the same site using Spanish
-   The layout should pretty much be the same.

\
\... But if we use German, where a word can be quite lengthy, the whole
layout could potentially be thown off. If it does break, that will be
caught!\
\
These match levels can be set either in the Test Manager, or when
setting up the Eyes driver instance.\

 Applitools Does Accessibility Testing
--------------------------------------

Want to check if your website has potential accessibility problems?\
\

-   Go to WAVE, the Web Accessibility Evaluation tool at
    <http://wave.webaim.org/>
-   Punch in the web address of a site you want to check out, such as
    FamilySearch.org. 

<div>

WAVE searches to see if each element have ARIA tags. What is Aria?

</div>

\
\"Accessible Rich Internet Applications (ARIA) defines ways to make Web
content and Web applications (especially those developed with Ajax and
JavaScript) more accessible to people with disabilities. For example,
ARIA enables accessible navigation landmarks, JavaScript widgets, form
hints and error messages, live content updates, and more.\
\
\"ARIA is a set of special accessibility attributes which can be added
to any markup, but is especially suited to HTML. The roleattribute
defines what the general type of object is (such as an article, alert,
or slider). Additional ARIA attributes provide other useful properties,
such as a description for a form or the current value of a progressbar.\
\
\"ARIA is implemented in most popular browsers and screen readers.
However, implementations vary and older technologies don\'t support it
well (if at all). Use either \'safe\' ARIA that degrades gracefully, or
ask users to upgrade to newer technology\". *- [Developer.Mozilla.Org /
ARIA](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA)*\
*\
*With Selenium WebDriver, we can follow the same exact steps we
performed, checking with Applitools all the way!\
\
For a code sample, see [Applitools / java-examples /
accessibilityTesting.java](https://github.com/applitools/java-examples/blob/master/src/test/java/accessibilityTesting.java)\
\

 Applitools Uses Machine Learning To Organize Errors 
-----------------------------------------------------

\
The more screens you compare and contrast, the more technical debt you
can accumulate. You need to give a thumbs up or thumbs down to train
your system if you truly care about the diffetrence, or if it is below
your threshold. They do have aq machine learning algorithm. It can sort
different error images into different categories, and you can compare
them all at once.\
\
With these visual comparisons, you don\'t have to find the locaters for
each object, compare the expected values and the actual values. Just set
up that initial baseline!\
\
As your site changes, you don\'t need to update page objects to check
for the new design elements. You can just create a new baseline image.\
\

Applitools Does JIRA!
---------------------

Applitools integrates with JIRA, a commonly used bug reporting tool.\
\
**[Applitools Eyes JIRA Integration]{.underline}**\

[*https://youtu.be/wvVZxgoXx8c*](https://youtu.be/wvVZxgoXx8c)\
\
\
Let\'s say there was an error that was important enough to keep track of
over time to see if it keeps happening? You can mark errors, create
tickets, or set the checking algorithm to snooze.\
\
All information, such as operating system, browser, and viewport is
captured automatically and can be placed in the JIRA ticket.\
\
Thank you so much, Justin, for the amazing walkthrough!\
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
[Facebook](https://www.facebook.com/AdventuresInAutomation/)!\"*

</div>
