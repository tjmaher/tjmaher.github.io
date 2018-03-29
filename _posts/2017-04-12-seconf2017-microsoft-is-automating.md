\-\-- layout: post title: \'SeConf2017: Microsoft is automating Windows,
Intuit automating Mac Apps, all with Appium!\' date:
\'2017-04-12T08:00:00.000-04:00\' author: T.J. Maher tags: - appium
modified\_time: \'2017-04-17T08:16:08.549-04:00\' thumbnail:
https://i.ytimg.com/vi/aWo6aOWbCsc/default.jpg blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-2294804662234386053
blogger\_orig\_url:
http://www.tjmaher.com/2017/04/seconf2017-microsoft-is-automating.html
\-\-- **Star-Driver: Appium for the Future with Dan Cuellar**\
[Joe
Colantonio](https://www.youtube.com/channel/UC1IuOajCAtHvLyZgkIK47dQ),
[Test Talks](http://testtalks.com/)\

\
<https://youtu.be/aWo6aOWbCsc>\
\
\"Apr 7, 2017 - It was an honor to finally meet one of my open-source
heroes Dan Cuellar the creator of Appium. We had a quick chat at
Selenium Conference 2017 in Austin and Dan was cool enough to let me
interview him on camera. Dan shared his vision for Appium to be able to
automate all things not just mobile apps\".\
\
[]{#more}\
\
**\
Automate Windows And Mac Apps With The WebDriver Protocol **\

<div>

Dan Cuellar, FOODIt\

<https://youtu.be/MgBRvQOZhec>\
\
See Dan Cuellar talk about his vision, the Star-Driver vision, where
Appium can be used to automate all the things! Not just a WebDriver. Not
just an App Driver. But an all-the-things driver!\
\
**[Special Guests:]{.underline}**\
\
**Yosef Durr**, Senior Lead Program Manager from Microsoft: Microsoft is
getting on board the open-source train with WinAppDriver. Use whatever
scripting language or ecosystem you want, and pair it with Appium to
test Windows apps. Yosef has been working on this for the past two
years. A year ago, they launched WinDriver for the PC, still in beta.\
\
Yosef uses Visual Studio, C\#, Nougat + a tool called "Inspect" to pull
meta-data you wish to use in your automation. He is also making sure you
can use Appium Desktop. The goal? Test any app with this toolset! Yosef
demoed the Windows Calculator to run some tests, and automate a VB 6
app, MS Paint (a classic Windows 32 app). It also tests touch-click-drag
for Microsoft Edge on touchscreen devices.\
\
You might want to find other elements such as logs, or test apps like
Cortana.\
\
This is almost out of beta! They need to fix a few performance bugs they
still have.\
\
What is next?\
\

-   PC Version needs to get out of beta in the next month or two.
-   Appium Desktop needs to finish integration.
-   Add Windows Pen and Touch.
-   Add Windows Mobile and X-Box.
-   Should Microsoft open source the WinAppDriver itself?

\
See <http://github.com/Microsoft/WinAppDriver> for more information.\
\
The goal is to have vendors themselves creating WebDriver and Appium
implementations. Microsoft was not always this way. Jim Evans can talk
all about this.\
\
\
**Stuart Russell**, Senior Software Engineer from Intuit, joined Dan
Cuellar on stage to talk about their adventure with Appium for Mac, a
proof-of-concept, back in 2013. Last year, Intuit contacted Dan. They
have been using Appium for Mac for the past three years, and they wanted
to contribute back to the project.\
\
With WebDriver, you have a WebDriver Client sending HTTP requests and
waits, and WebDriver Server taking action and responding. In between is
the JSON wire protocol a HTTP REST API. Normally, the servers are web
browsers. Appium for Mac replaces it with the native part of Mac OS
interface.\
\
Application runs with Objective C + Xcode + CocoaHTTPServer.\
\
Bill Cheeseman donated his product PFAssistive Framework to the MacOS
project royalty-free, hiding all the Accessibility APIs that get quite
confusing, with differences between versions of the Mac OS.\

> *\"Quechee Software is the name under which Bill Cheeseman develops
> macOS applications for Macintosh computers in Objective-C and Swift
> using Apple\'s Cocoa frameworks, as well as AppleScript and GUI
> Scripting projects. Most of Quechee Software\'s work is devoted to the
> frameworks, developer utilities and other applications sold or
> distributed by PreForm Assistive Technologies, LLC\" - [Quechee
> Software](http://www.quecheesoftware.com/), Queechee, Vermont*

\
Stuart demoed a test for TestEdit, writing, editing and dragging text in
a sentence.\
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
