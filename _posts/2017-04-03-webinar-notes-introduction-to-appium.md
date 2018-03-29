\-\-- layout: post title: \'Webinar Notes: An Introduction to Appium
Desktop by Johnathan Lipps\' date: \'2017-04-03T19:15:00.002-04:00\'
author: T.J. Maher tags: - appium modified\_time:
\'2017-04-03T19:16:06.039-04:00\' thumbnail:
https://i.ytimg.com/vi/IOSUBda2-g4/default.jpg blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-6599997302313229456
blogger\_orig\_url:
http://www.tjmaher.com/2017/04/webinar-notes-introduction-to-appium.html
\-\--

### About the Webinar

[\
]{.underline}**From Sauce Labs:** [An Introduction to Appium
Desktop](https://saucelabs.com/resources/webinars/an-introduction-to-appium-desktop?mkt_tok=eyJpIjoiTTJVMllqWTVZVE5oTjJWayIsInQiOiJWTU1qVldHcCtlQVNCWit1cnRCTVM0MHVTZEt2TU92WkZwUjlBZTRWeWgzeHpWek9lWFd5UERiK1B2dkxzQzZaeEN6UGl3NnZnS2hHNmplYjNRQnBkYUk1ZDdmQkdsNnVic296NVZcL3I5dnZYaU5BczgwWDE1dU5JTHNrSHF5bHYifQ%3D%3D)** ***(3/29/2017):*\
\
\"Appium Desktop is a new graphical interface for starting an Appium
server and inspecting your app\'s structure via Appium. It\'s recently
been developed by the Appium contributors at Sauce Labs and is currently
in open beta. In this webinar we will take you on a tour of Appium
Desktop and show how it can be used with the goal of making it easier to
write tests for your apps.\
\
\"Join Jonathan Lipps, Appium project lead committer and Director of
Open Source for Sauce Labs, as he covers the following topics:\

-   \"Finding, downloading, and installing Appium Desktop for your
    platform
-   \"Starting an Appium server with both simple and advanced options
-   \"Interpreting Appium server log output
-   \"Starting an inspector session using just Appium Desktop\'s server
-   \"Starting an inspector session using Sauce Labs or TestObject
-   \"Troubleshooting and where to go for help
-   \"Appium Desktop\'s roadmap\"

[**Video**: An Introduction to Appium Desktop]{.underline} (55 minutes)

[*https://youtu.be/IOSUBda2-g4*](https://youtu.be/IOSUBda2-g4)\
\
**Slides:** Introducing Appium Desktop:\

\

::: {style="margin-bottom: 5px;"}
**[An Introduction to Appium
Desktop](https://www.slideshare.net/saucelabs/an-introduction-to-appium-desktop "An Introduction to Appium Desktop")**
from **[Sauce Labs](https://www.slideshare.net/saucelabs)**
:::

\
\

### Who is Johnathan Lipps?

::: {.separator style="clear: both; text-align: center;"}
[![](https://4.bp.blogspot.com/-QtxGAbmyYgY/WOLW3FWpbHI/AAAAAAAALt4/nv6c-Ac2NcQ3vHsxL8HFbmJorFJkKQO2ACLcB/s200/jlipps.jpg){width="200"
height="200"}](https://4.bp.blogspot.com/-QtxGAbmyYgY/WOLW3FWpbHI/AAAAAAAALt4/nv6c-Ac2NcQ3vHsxL8HFbmJorFJkKQO2ACLcB/s1600/jlipps.jpg)
:::

According to his LinkedIn profile, as Director of Open Source at Sauce
Labs: \"I lead open source strategy, developer advocacy, and
technological evangelism for the world\'s largest test cloud. In
addition to ensuring the open source testing ecosystem is healthy, I
lead development of Appium, the mobile automation framework, enabling a
whole new level of automated testing for mobile devices and beyond\".\

<div>

\

</div>

<div>

\...also according to LinkedIn: \"I\'m a software developer, a
passionate leader, a linguist, a philosopher, a writer, a musician, a
rock climber, and a runner\".\

<div>

\
Project Lead for the Appium project.

</div>

<div>

-   Working on Appium for the past four years
-   Can be reached on Twitter, [\@jlipps](https://twitter.com/jlipps).
-   According to his LinkedIn
    Profile: <https://www.linkedin.com/in/jlipps/>, 
-   Website: <http://www.jonathanlipps.com/>

</div>

<div>

\
\
Johnathan Lipps metioned that Appium is Sauce Labs\' biggest project,
and have been working on it for quite some time. \"Appium is the
cross-platform solution for native, web, and hybrid mobile automation.\"
With it, you can automate tests the apps you care about.\
\
The main product in the Appium toolset is the Appium server, an
invisible piece of software, installed by the Node Package Manager (npm)
that sits on top of Node.JS.\
\
The **Appium server** runs as a server on your machine, remotely, or in
the cloud, such as with Sauce Labs, \"enabling you to send requests for
sessions, and within those sessions to send automation commands to
\[\...\] tell your device to do things\".\
\
The **Appium Desktop** (new!) is a point-and-click interface for using
appium and inspecting your app\'s structure. The inspector helps you
find web elements such as a button so you can then make an assertion. It
is basicallt a wrapper for Appium.\
\
Launch the desktop app, which provides a GUI for the exact same messages
you would see in the command line. There used to be appium.app and
appium.exe where you could also use Appium with a point-and-click
interface. They were good applications that fell by the wayside. Appium
Desktop is a \"spiritual successor\".\

###  Differences Between Appium Command Line Interface (CLI) and Appium Desktop:

\

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://2.bp.blogspot.com/-RJtW1E9IjBw/WOLHKacQkRI/AAAAAAAALtk/qnE59qlrNtgN3YBd-V5kCr3aTpI4lruIwCLcB/s640/Screenshot%2B2017-04-03%2Bat%2B6.03.11%2BPM.png){width="640" height="400"}](https://2.bp.blogspot.com/-RJtW1E9IjBw/WOLHKacQkRI/AAAAAAAALtk/qnE59qlrNtgN3YBd-V5kCr3aTpI4lruIwCLcB/s1600/Screenshot%2B2017-04-03%2Bat%2B6.03.11%2BPM.png)
                                                                                                                        *From [Introducing Appium Desktop](https://www.slideshare.net/saucelabs/an-introduction-to-appium-desktop)*
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

### Download and Install Appium Desktop

Appium Desktop is at https://github.com/appium/appium-desktop/releases\
\
You can choose to adjust the port or the host if you need, and you start
a simple server.\
You can also select \"Advanced\" and play around with various options.\
\
Make sure to read the documentation, since this will change how Appium
behaves.\
\
You can run from:\
\

-   Automatic Server
-   Custom Servers
-   Sauce Labs
-   Test Object

\
\
You can also set Desired Capabilities such as platformName : iOS.\
\

### What are Desired Capabilities?

> \
> \"Desired capabilities are a set of keys and values (i.e., a map or
> hash) sent to the Appium server to tell the server what kind of
> automation session we're interested in starting up. There are also
> various capabilities which can modify the behavior of the server
> during automation. For example, we might set the platformName
> capability to iOS to tell Appium that we want an iOS session, rather
> than an Android or Windows one. Or we might set the safariAllowPopups
> capability to true in order to ensure that, during a Safari automation
> session, we're allowed to use JavaScript to open up new windows\". -
> [Appium API
> Reference](https://appium.io/slate/en/master/?ruby#appium-concepts)

\
If you have a huge set of Desired Capabilities you can edit in the GUI
of Appium Desktop and see it in the JSON object that the Appium will
interpret.\
**[\
Appium server capabilities]{.underline}**\

<div>

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  `automationName`{.prettyprint style="background-color: rgba(0, 0, 0, 0.0470588); border-radius: 3px; display: inline-block; font-family: Monaco, "Courier New", monospace; font-size: 12px; padding: 3px 0.5em; white-space: nowrap; word-break: break-word;"}      Which automation engine to use                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        `Appium`{.prettyprint style="background-color: rgba(0, 0, 0, 0.0470588); border-radius: 3px; display: inline-block; font-family: Monaco, "Courier New", monospace; font-size: 12px; padding: 3px 0.5em; word-break: break-word;"} (default) or `Selendroid`{.prettyprint style="background-color: rgba(0, 0, 0, 0.0470588); border-radius: 3px; display: inline-block; font-family: Monaco, "Courier New", monospace; font-size: 12px; padding: 3px 0.5em; word-break: break-word;"}
  `platformName`{.prettyprint style="background-color: rgba(0, 0, 0, 0.0470588); border-radius: 3px; display: inline-block; font-family: Monaco, "Courier New", monospace; font-size: 12px; padding: 3px 0.5em; white-space: nowrap; word-break: break-word;"}        Which mobile OS platform to use                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       `iOS`{.prettyprint style="background-color: rgba(0, 0, 0, 0.0470588); border-radius: 3px; display: inline-block; font-family: Monaco, "Courier New", monospace; font-size: 12px; padding: 3px 0.5em; word-break: break-word;"}, `Android`{.prettyprint style="background-color: rgba(0, 0, 0, 0.0470588); border-radius: 3px; display: inline-block; font-family: Monaco, "Courier New", monospace; font-size: 12px; padding: 3px 0.5em; word-break: break-word;"}, or `FirefoxOS`{.prettyprint style="background-color: rgba(0, 0, 0, 0.0470588); border-radius: 3px; display: inline-block; font-family: Monaco, "Courier New", monospace; font-size: 12px; padding: 3px 0.5em; word-break: break-word;"}
  `platformVersion`{.prettyprint style="background-color: rgba(0, 0, 0, 0.0470588); border-radius: 3px; display: inline-block; font-family: Monaco, "Courier New", monospace; font-size: 12px; padding: 3px 0.5em; white-space: nowrap; word-break: break-word;"}     Mobile OS version                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     e.g., `7.1`{.prettyprint style="background-color: rgba(0, 0, 0, 0.0470588); border-radius: 3px; display: inline-block; font-family: Monaco, "Courier New", monospace; font-size: 12px; padding: 3px 0.5em; word-break: break-word;"}, `4.4`{.prettyprint style="background-color: rgba(0, 0, 0, 0.0470588); border-radius: 3px; display: inline-block; font-family: Monaco, "Courier New", monospace; font-size: 12px; padding: 3px 0.5em; word-break: break-word;"}
  `deviceName`{.prettyprint style="background-color: rgba(0, 0, 0, 0.0470588); border-radius: 3px; display: inline-block; font-family: Monaco, "Courier New", monospace; font-size: 12px; padding: 3px 0.5em; white-space: nowrap; word-break: break-word;"}          The kind of mobile device or emulator to use                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          `iPhone Simulator`{.prettyprint style="background-color: rgba(0, 0, 0, 0.0470588); border-radius: 3px; display: inline-block; font-family: Monaco, "Courier New", monospace; font-size: 12px; padding: 3px 0.5em; word-break: break-word;"}, `iPad Simulator`{.prettyprint style="background-color: rgba(0, 0, 0, 0.0470588); border-radius: 3px; display: inline-block; font-family: Monaco, "Courier New", monospace; font-size: 12px; padding: 3px 0.5em; word-break: break-word;"}, `iPhone Retina 4-inch`{.prettyprint style="background-color: rgba(0, 0, 0, 0.0470588); border-radius: 3px; display: inline-block; font-family: Monaco, "Courier New", monospace; font-size: 12px; padding: 3px 0.5em; word-break: break-word;"}, `Android Emulator`{.prettyprint style="background-color: rgba(0, 0, 0, 0.0470588); border-radius: 3px; display: inline-block; font-family: Monaco, "Courier New", monospace; font-size: 12px; padding: 3px 0.5em; word-break: break-word;"}, `Galaxy S4`{.prettyprint style="background-color: rgba(0, 0, 0, 0.0470588); border-radius: 3px; display: inline-block; font-family: Monaco, "Courier New", monospace; font-size: 12px; padding: 3px 0.5em; word-break: break-word;"}, etc.... On iOS, this should be one of the valid devices returned by instruments with `instruments -s devices`{.prettyprint style="background-color: rgba(0, 0, 0, 0.0470588); border-radius: 3px; display: inline-block; font-family: Monaco, "Courier New", monospace; font-size: 12px; padding: 3px 0.5em; word-break: break-word;"}. On Android this capability is currently ignored, though it remains required.
  `app`{.prettyprint style="background-color: rgba(0, 0, 0, 0.0470588); border-radius: 3px; display: inline-block; font-family: Monaco, "Courier New", monospace; font-size: 12px; padding: 3px 0.5em; white-space: nowrap; word-break: break-word;"}                 The absolute local path *or* remote http URL to an `.ipa`{.prettyprint style="background-color: rgba(0, 0, 0, 0.0470588); border-radius: 3px; display: inline-block; font-family: Monaco, "Courier New", monospace; font-size: 12px; padding: 3px 0.5em; word-break: break-word;"} or `.apk`{.prettyprint style="background-color: rgba(0, 0, 0, 0.0470588); border-radius: 3px; display: inline-block; font-family: Monaco, "Courier New", monospace; font-size: 12px; padding: 3px 0.5em; word-break: break-word;"} file, or a `.zip`{.prettyprint style="background-color: rgba(0, 0, 0, 0.0470588); border-radius: 3px; display: inline-block; font-family: Monaco, "Courier New", monospace; font-size: 12px; padding: 3px 0.5em; word-break: break-word;"} containing one of these. Appium will attempt to install this app binary on the appropriate device first. Note that this capability is not required for Android if you specify `appPackage`{.prettyprint style="background-color: rgba(0, 0, 0, 0.0470588); border-radius: 3px; display: inline-block; font-family: Monaco, "Courier New", monospace; font-size: 12px; padding: 3px 0.5em; word-break: break-word;"} and `appActivity`{.prettyprint style="background-color: rgba(0, 0, 0, 0.0470588); border-radius: 3px; display: inline-block; font-family: Monaco, "Courier New", monospace; font-size: 12px; padding: 3px 0.5em; word-break: break-word;"} capabilities (see below). Incompatible with `browserName`{.prettyprint style="background-color: rgba(0, 0, 0, 0.0470588); border-radius: 3px; display: inline-block; font-family: Monaco, "Courier New", monospace; font-size: 12px; padding: 3px 0.5em; word-break: break-word;"}.   `/abs/path/to/my.apk`{.prettyprint style="background-color: rgba(0, 0, 0, 0.0470588); border-radius: 3px; display: inline-block; font-family: Monaco, "Courier New", monospace; font-size: 12px; padding: 3px 0.5em; word-break: break-word;"} or `http://myapp.com/app.ipa`{.prettyprint style="background-color: rgba(0, 0, 0, 0.0470588); border-radius: 3px; display: inline-block; font-family: Monaco, "Courier New", monospace; font-size: 12px; padding: 3px 0.5em; word-break: break-word;"}
  `browserName`{.prettyprint style="background-color: rgba(0, 0, 0, 0.0470588); border-radius: 3px; display: inline-block; font-family: Monaco, "Courier New", monospace; font-size: 12px; padding: 3px 0.5em; white-space: nowrap; word-break: break-word;"}         Name of mobile web browser to automate. Should be an empty string if automating an app instead.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       \'Safari' for iOS and \'Chrome', \'Chromium', or \'Browser' for Android
  `newCommandTimeout`{.prettyprint style="background-color: rgba(0, 0, 0, 0.0470588); border-radius: 3px; display: inline-block; font-family: Monaco, "Courier New", monospace; font-size: 12px; padding: 3px 0.5em; white-space: nowrap; word-break: break-word;"}   How long (in seconds) Appium will wait for a new command from the client before assuming the client quit and ending the session                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       e.g. `60`{.prettyprint style="background-color: rgba(0, 0, 0, 0.0470588); border-radius: 3px; display: inline-block; font-family: Monaco, "Courier New", monospace; font-size: 12px; padding: 3px 0.5em; word-break: break-word;"}
  `language`{.prettyprint style="background-color: rgba(0, 0, 0, 0.0470588); border-radius: 3px; display: inline-block; font-family: Monaco, "Courier New", monospace; font-size: 12px; padding: 3px 0.5em; white-space: nowrap; word-break: break-word;"}            (Sim/Emu-only) Language to set for the simulator / emulator                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           e.g. `fr`{.prettyprint style="background-color: rgba(0, 0, 0, 0.0470588); border-radius: 3px; display: inline-block; font-family: Monaco, "Courier New", monospace; font-size: 12px; padding: 3px 0.5em; word-break: break-word;"}
  `locale`{.prettyprint style="background-color: rgba(0, 0, 0, 0.0470588); border-radius: 3px; display: inline-block; font-family: Monaco, "Courier New", monospace; font-size: 12px; padding: 3px 0.5em; white-space: nowrap; word-break: break-word;"}              (Sim/Emu-only) Locale to set for the simulator / emulator                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             e.g. `fr_CA`{.prettyprint style="background-color: rgba(0, 0, 0, 0.0470588); border-radius: 3px; display: inline-block; font-family: Monaco, "Courier New", monospace; font-size: 12px; padding: 3px 0.5em; word-break: break-word;"}
  `udid`{.prettyprint style="background-color: rgba(0, 0, 0, 0.0470588); border-radius: 3px; display: inline-block; font-family: Monaco, "Courier New", monospace; font-size: 12px; padding: 3px 0.5em; white-space: nowrap; word-break: break-word;"}                Unique device identifier of the connected physical device                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             e.g. `1ae203187fc012g`{.prettyprint style="background-color: rgba(0, 0, 0, 0.0470588); border-radius: 3px; display: inline-block; font-family: Monaco, "Courier New", monospace; font-size: 12px; padding: 3px 0.5em; word-break: break-word;"}
  `orientation`{.prettyprint style="background-color: rgba(0, 0, 0, 0.0470588); border-radius: 3px; display: inline-block; font-family: Monaco, "Courier New", monospace; font-size: 12px; padding: 3px 0.5em; white-space: nowrap; word-break: break-word;"}         (Sim/Emu-only) start in a certain orientation                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         `LANDSCAPE`{.prettyprint style="background-color: rgba(0, 0, 0, 0.0470588); border-radius: 3px; display: inline-block; font-family: Monaco, "Courier New", monospace; font-size: 12px; padding: 3px 0.5em; word-break: break-word;"} or `PORTRAIT`{.prettyprint style="background-color: rgba(0, 0, 0, 0.0470588); border-radius: 3px; display: inline-block; font-family: Monaco, "Courier New", monospace; font-size: 12px; padding: 3px 0.5em; word-break: break-word;"}
  `autoWebview`{.prettyprint style="background-color: rgba(0, 0, 0, 0.0470588); border-radius: 3px; display: inline-block; font-family: Monaco, "Courier New", monospace; font-size: 12px; padding: 3px 0.5em; white-space: nowrap; word-break: break-word;"}         Move directly into Webview context. Default `false`{.prettyprint style="background-color: rgba(0, 0, 0, 0.0470588); border-radius: 3px; display: inline-block; font-family: Monaco, "Courier New", monospace; font-size: 12px; padding: 3px 0.5em; word-break: break-word;"}                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          `true`{.prettyprint style="background-color: rgba(0, 0, 0, 0.0470588); border-radius: 3px; display: inline-block; font-family: Monaco, "Courier New", monospace; font-size: 12px; padding: 3px 0.5em; word-break: break-word;"}, `false`{.prettyprint style="background-color: rgba(0, 0, 0, 0.0470588); border-radius: 3px; display: inline-block; font-family: Monaco, "Courier New", monospace; font-size: 12px; padding: 3px 0.5em; word-break: break-word;"}
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

::: {.separator style="clear: both; text-align: center;"}
*Go to
<https://github.com/appium/appium/blob/master/docs/en/writing-running-appium/caps.md>
to see more Android and iOS specific Desired Capabilities!*
:::

### 

### How to Use The Inspector:

<div>

\
Start the Session. You need to install Android SDKs of emulators on your
local machine. After seeing the simulator, you can see the inspector
window. What is going on with different elements?\
\
You can navigate the XML source, the response tree. This is how you can
find the id or CSS Selector that you then can call.\
\
\... It is like the Firefox plugin, Firebug and Firepath used to
determine strategies to find locators.\
\
You can perform actions directly from Appium Desktop, such as sending
keys to a textbox.\
\
Note, if you input your Sauce Labs credentials you can use their virtual
emulators of Android or IOS devices.\
\
See any issues? Are the issues with:\
\

-   Appium? https://github.com/appium/appium/issues
-   Appium Desktop? https://github.com/appium/appium-desktop/issues

\

###  Want to See More Webinars from Sauce L?

\

-   You can see more **Sauce Labs Webinars**
    at <https://saucelabs.com/resources/webinars>

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

</div>

</div>
