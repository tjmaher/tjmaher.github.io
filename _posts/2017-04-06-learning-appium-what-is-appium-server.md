\-\-- layout: post title: \'Learning Appium Desktop: What is Appium
Server and How Do You Start It Through Appium Desktop?\' date:
\'2017-04-06T08:00:00.000-04:00\' author: T.J. Maher tags: - appium
modified\_time: \'2017-04-25T09:04:15.130-04:00\' thumbnail:
https://1.bp.blogspot.com/-lgIjJB-Ursc/WOWRrM4qVXI/AAAAAAAALuI/Lb6r\_CFIDJ4qj6-TwCh-auvwj9nsyOiygCLcB/s72-c/screen-start-simple.png
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-6599584601025782397
blogger\_orig\_url:
http://www.tjmaher.com/2017/04/learning-appium-what-is-appium-server.html
\-\--

<div>

I\'ve been asking myself the same question for the past two years, ever
since I first became an automation developer: I wonder if I can figure
out how to create a mobile automation framework? We already started
covering the basic building blocks:\
\
**[Learning Serenity
BDD](http://www.tjmaher.com/2017/03/serenity-bdd-automation-framework-that.html):**\

-   Serenity BDD with Cucumber, formats tests to be in an easy-to-read
    Given / Then / When format for feature files, which then can be
    broken down into step definitions. This is what is already being
    used in my current position.
-   Serenity BDD gives us easy-to-read reports. Picture the Given / Then
    / When as a summary report where you can drill down in the report to
    see the individual steps, how they were carried out, and which
    individual step passed or failed.

<div>

This section will cover **Learning Appium Desktop**:

</div>

<div>

-   Appium Desktop is a web based product used to inspect iOS and
    Android apps so I can determine a locator strategy for my eventual
    mobile automation test framework I will be building.
-   Appium Desktop comes with Appium 1.6.4-beta as the server. We will
    be covering basic concepts of Appium, and doing a deep-dive on many
    of the Android Command Line Tools used.
-   Although Appium allows both OS and Android, I was going to focus
    just on Android first, configuring both physical and virtual
    devices. 
-   I will be setting everything up on my Macbook. Why? I really like
    the Mac Terminal as a Command Line Interface. 

</div>

\
If you need more of an introduction to what is Appiun, Appium Docker,
and what Appium can do, view:\
\

-   [Webinar Notes: Appium, Prime Cuts, by Dan
    Cuellar](http://www.tjmaher.com/2017/03/notes-from-dan-cuellars-webinar-appium.html)
-   [Webinar Notes: An Introduction to Appium Desktop by Johnathan
    Lipps.](http://www.tjmaher.com/2017/04/webinar-notes-introduction-to-appium.html)
-   [SeConf2017: Rethinking Appium's Code Base,
    Notes](http://www.tjmaher.com/2017/04/even-though-i-have-been-qa-engineer-for.html)
-   [SeConf2017: Security Testing, Dockerizing Tests using Appium,
    Notes](http://www.tjmaher.com/2017/04/seconf2017-security-testing-dockerizing.html)
-   [SeConf2017: Microsoft is automating Windows, Intuit automating Mac
    Apps, all with
    Appium!](http://www.tjmaher.com/2017/04/seconf2017-microsoft-is-automating.html)

::: {.post-header style="background-color: white; color: #222222; font-family: Calibri; font-size: 14.4px; line-height: 1.6; margin: 0px 0px 1.5em;"}
::: {.post-header-line-1}
:::
:::

###  

### What is Appium?

*From Appium History: <http://appium.io/history.html>*\
\
\"[Dan Cuellar](https://twitter.com/thedancuellar) was the Test Manager
at Zoosk in 2011, when he encountered a problem. The length of the test
passes on the iOS product was getting out of hand. Less testing was an
option, but would come with additional risk, especially with it taking
several days to get patches through the iOS App Store Review process. He
thought back to his days working on websites and realized automation was
the answer.\
\
\"Dan surveyed the existing landscape of tools, only to find that all of
them hand major drawbacks. The tool supplied by Apple, UIAutomation,
required tests to be written in JavaScript, and did not allow for real
time debugging or interpretation. It also had to be executed inside the
Xcode profiling tool, Instruments. Other 3rd-party tools used private
APIs and required SDKs and HTTP Servers to be embedded into the
application. This seemed highly undesirable.\
\
[]{#more}\
\
\"Unsatisfied with the existing options, Dan asked his manager for some
additional time to see if he could find a better way. He spent 2 weeks
poking and prodding around to see if there was a way to use approved
Apple technologies to automate an iOS application. The first
implementation he tried used AppleScript to send messages to Mac UI
elements using the OS X accessibility APIs. This worked to some degree,
but would never work on real devices, not to mention other drawbacks.\
\
\"So he thought, what if I could get the UIAutomation framework to run
in real time like an interpreter? \[ [READ
MORE](http://appium.io/history.html) \]\
\
Jason Huggins, who created the first version of Selenium at Thoughtworks
,then teamed up with Simon Stewart at Google to make Selenium WebDriver,
founded a company where if you were doing software test automation, you
could use their devices-in-a-cloud to test on. That company was Sauce
Labs. 

</div>

<div>

\

</div>

<div>

Jason was inspired by Dan Cuellar\'s talk at Selenium Conference 2012,
and talked Jason into making his code open-source. They dubbed the
product Appium: Selenium for Apps. It was re-written based on the web
server framework Node.js in 2013, and Appium 1.0 was released in 2014.
 Appium was donated to the non-profit JS Foundation late in 2016. 

</div>

<div>

\

</div>

<div>

Dan still works with the Appium team. A few weeks ago he demoed Appium
Desktop. 

</div>

<div>

-   [Notes from Dan Cueller\'s webinar: Appium, Prime
    Cuts](http://www.tjmaher.com/2017/03/notes-from-dan-cuellars-webinar-appium.html)
-   [Notes from Johnathan Lipps\' demo of Appium
    Desktop](http://www.tjmaher.com/2017/04/webinar-notes-introduction-to-appium.html)

</div>

<div>

\

</div>

<div>

<div>

### Appium Concepts

*Taken from <http://appium.io/slate/en/master/?java#appium-concepts>*\
**[\
]{.underline}**

</div>

<div>

**[From Client/Server Architecture]{.underline}: **\
\"Appium is at its heart a webserver that exposes a REST API. It
receives connections from a client, listens for commands, executes those
commands on a mobile device, and responds with an HTTP response
representing the result of the command execution. The fact that we have
a client/server architecture opens up a lot of possibilities: we can
write our test code in any language that has a http client API, but it
is easier to use one of the [Appium client
libraries](http://appium.io/downloads). We can put the server on a
different machine than our tests are running on. We can write test code
and rely on a cloud service like [Sauce
Labs](https://saucelabs.com/mobile) to receive and interpret the
commands\".\
**[\
Session]{.underline}**\
\"Automation is always performed in the context of a session. Clients
initiate a session with a server in ways specific to each library, but
they all end up sending a POST /session request to the server, with a
JSON object called the \'desired capabilities' object. At this point the
server will start up the automation session and respond with a session
ID which is used for sending further commands\".\
\
**[Desired Capabilities]{.underline}**\
\"Desired capabilities are a set of keys and values (i.e., a map or
hash) sent to the Appium server to tell the server what kind of
automation session we're interested in starting up. There are also
various capabilities which can modify the behavior of the server during
automation. For example, we might set the platformName capability to iOS
to tell Appium that we want an iOS session, rather than an Android or
Windows one. Or we might set the safariAllowPopups capability to true in
order to ensure that, during a Safari automation session, we're allowed
to use JavaScript to open up new windows. See the [capabilities
doc](http://appium.io/slate/en/master/?java#caps.md) for the complete
list of capabilities available for Appium\".\
\
**[Appium Server]{.underline}**\
\"Appium is a server written in Node.js\".\
\
**[Appium Clients]{.underline}**\
\"There are client libraries (in Java, Ruby, Python, PHP, JavaScript,
and C\#) which support Appium's extensions to the WebDriver protocol.
When using Appium, you want to use these client libraries instead of
your regular WebDriver client. You can view the full list of
libraries [here](http://appium.io/slate/en/master/?java#appium-clients.md)\".

</div>

</div>

<div>

\

### Do You Have Java 8?

</div>

<div>

For this project, you need to see if you have at least Java 8. 

</div>

<div>

-   Open the Mac Terminal and type: *java -version*
-   If you have Java 7 or lower, go to [the Java downloads
    page](http://www.oracle.com/technetwork/java/javase/downloads/index.html),
    select the Java Platform (Java Development Kit) to go to that
    section.
-   Scroll down to the Java SE (Standard Edition) Development Kit,
    Accept the License Agreement, and choose the version for your
    operating system, such as the one for Mac OS X for my Macbook. 
-   Install Java using the defaults. 

</div>

<div>

### 

### Appium Desktop

\
Appium Desktop is a web-based tool used to inspect an iOS or Android
application. It an open source app for Mac, Windows, and Linux\
\
Appium Desktop does not run mobile automation, itself. It uses the
Appium server and iOS and Android emulators to run and inspect app, so
that an automation developer can investigate various strategies to
locate app elements such as text boxes, dropdown lists, etc. If you have
a Sauce Labs account, or Test Object, you could substitute the emulators
there.\
\
It provides, according to the GitHub Site:
<https://github.com/appium/appium-desktop>\

-   \"A graphical interface for the Appium Server. You can set options,
    start/stop the server, see logs, etc\... You also don\'t need to use
    Node/NPM to install Appium, as the Node runtime comes bundled with
    Appium Desktop\".
-   \"An Inspector that you can use to look at your app\'s elements, get
    basic information about them, and perform basic interactions with
    them. This is useful as a way to learn about Appium or as a way to
    learn about your app so you can write tests for it\".

\
You can read more in the documentation about:\

-   Advanced Settings
-   Server Presets
-   Start new sessions via Sauce Labs, Test Objects, or for custom
    servers. 

\... for now, we are going to focus on getting an Android app up and
running with Appium Desktop so we can start inspecting it. 

</div>

<div>

###  Warning: Appium Desktop is Not Appium

\
\"Appium Desktop is a graphical frontend to Appium with additional
tools. Appium Desktop is released on its own cadence and has its own
versioning system. If you are reporting an issue with Appium Desktop,
always be sure to include both the version of Appium Desktop and the
version of the Appium Server which is in use (see below).\
\
\"If you\'re on macOS, you will need to install Appium Desktop by
copying the app from the downloaded DMG file to your own file system
(the best place is the \"Applications\" folder). Running Appium from in
side the attached DMG itself is not supported, and will not work\".\
\

### How to Install Appium Desktop on the Mac

\
1) Find the latest Release on
<https://github.com/appium/appium-desktop/releases>\
\
2) Download the version written to your operating system, such as
[appium-desktop-1.0.0-beta.6.dmg](https://github.com/appium/appium-desktop/releases/download/v1.0.0-beta.6/appium-desktop-1.0.0-beta.6.dmg)\
\
3) Double-click on the Disk Image (\*.dmg) file to open it, and drag the
\"Appium\" icon to the \"Applications\" folder.\
\
4) Go into \"Launchpad\", search for \"Appium\", and double-click it.
Select that, even though Appium is an application downloaded from the
internet, that you want to \"Open\" it.

</div>

<div>

\

</div>

<div>

### How to Start Appium Desktop

\
You can read more in the documentation about:\

-   Advanced Settings
-   Server Presets
-   Start new sessions via Sauce Labs, Test Objects, or for custom
    servers. 

\
\... for now, we are going to focus on getting an Android app up and
running with Appium Desktop so we can start inspecting it.\
\
After launching Appium Desktop, you will see the start window:\

::: {style="background-color: white; color: #333333; font-family: arial, sans-serif; font-size: 14px; margin-top: 10px; padding: 0px;"}
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://1.bp.blogspot.com/-lgIjJB-Ursc/WOWRrM4qVXI/AAAAAAAALuI/Lb6r_CFIDJ4qj6-TwCh-auvwj9nsyOiygCLcB/s640/screen-start-simple.png){width="640" height="624"}](https://1.bp.blogspot.com/-lgIjJB-Ursc/WOWRrM4qVXI/AAAAAAAALuI/Lb6r_CFIDJ4qj6-TwCh-auvwj9nsyOiygCLcB/s1600/screen-start-simple.png)
                                                                                                                                        *Behold, the Start Screen!*
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

\
:::

\
\
\"When you open Appium Desktop, you are greeted with the server start
window. The basic option is to start an Appium server with all its
defaults and the ability to modify the host and port. The start button
will also let you know which version of the Appium server you are
running, which can be useful when reporting issues to the Appium team\".
(From the [GitHub site](https://github.com/appium/appium-desktop))\
\
For our purposes, let\'s keep it simple, and select \"**Start Server
v1.6.4-beta**\", leaving the host at \"0.0.0.0\" and the Port at
\"4723\".\
\

::: {.separator style="clear: both; text-align: center;"}
[![](https://2.bp.blogspot.com/-EJ48P-0SgEc/WOWSn_RnxnI/AAAAAAAALuQ/_plLNnsemqo3Y36ea4yHW4FsRZPEJZSJgCLcB/s640/screen-logs.png){width="640"
height="596"}](https://2.bp.blogspot.com/-EJ48P-0SgEc/WOWSn_RnxnI/AAAAAAAALuQ/_plLNnsemqo3Y36ea4yHW4FsRZPEJZSJgCLcB/s1600/screen-logs.png)
:::

\
\
We then are presented with the **server console output window**.\
\
In the next blog post, we will be going over:\
\

-   Adding Android emulators onto our system from the Android SDK
    (Software Development Kit)
-   Setting up Desired Capabilities in Android Desktop 
-   Finding an app to test against
-   Starting a news session with Appium Desktop. 

\

::: {#toc-section .toc-section}
**Learning Appium**\

-   **Part One:** [What is Appium Server and How Do You Start It With
    Appium
    Desktop](http://www.tjmaher.com/2017/04/learning-appium-what-is-appium-server.html)
-   **Part Two:**  [How to Connect To Your Android Device Using the
    Android SDK, the Android Command Line Tools, and the Android Debug
    Bridge](http://www.tjmaher.com/2017/04/learning-appium-desktop-how-to-connect.html)
-   **Part Three:**  [Setting up remote devices through
    WiFi](http://www.tjmaher.com/2017/04/learning-appium-desktop-setting-up_18.html)
-   **Part Four:**  [Setting up Android Emulators with Android Virtual
    Device Manager (avd), choosing the Android operating system
    version](http://www.tjmaher.com/2017/04/learning-appium-desktop-setting-up.html)
-   **Part Five:**  [Find the Desired Capabilities: appPackage and
    appActivity. Bug in AAPT if giving just
    appName](http://www.tjmaher.com/2017/04/learning-appium-desktop-find-desired.html)
-   **Part Six:**  [Inspecting an Android app using Appium
    Desktop](http://www.tjmaher.com/2017/04/learning-appium-inspecting-app-with.html)
:::

\
\... Until then, Happy Testing!\
\

</div>

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
