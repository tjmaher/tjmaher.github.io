\-\-- layout: post title: \'Notes from Dan Cuellar\'\'s Webinar, Appium:
Prime Cuts\' date: \'2017-03-11T07:39:00.002-05:00\' author: T.J. Maher
tags: - appium modified\_time: \'2017-04-03T20:37:46.480-04:00\'
thumbnail:
https://4.bp.blogspot.com/-jECoAYUXZnY/WMOUhnlGKNI/AAAAAAAALq4/htTIh0HxOYg8WCsHm-Kxs6UmYVA9WpURgCLcB/s72-c/dan.png
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-946082452750022155
blogger\_orig\_url:
http://www.tjmaher.com/2017/03/notes-from-dan-cuellars-webinar-appium.html
\-\-- On Wednesday, March 8th, the creator of Appium, Dan Cuellar, gave
a Webinar, [Appium: Prime Cuts](https://youtu.be/D5MF3ZLds0Q).\
\
**[Dan Cuellar]{.underline}**\

::: {.separator style="clear: both; text-align: center;"}
[![](https://4.bp.blogspot.com/-jECoAYUXZnY/WMOUhnlGKNI/AAAAAAAALq4/htTIh0HxOYg8WCsHm-Kxs6UmYVA9WpURgCLcB/s1600/dan.png)](https://4.bp.blogspot.com/-jECoAYUXZnY/WMOUhnlGKNI/AAAAAAAALq4/htTIh0HxOYg8WCsHm-Kxs6UmYVA9WpURgCLcB/s1600/dan.png)
:::

<div>

**Website:**  [http://cuellarsaur.us](http://cuellarsaur.us/)\
**LinkedIn:** <https://www.linkedin.com/in/dacuellar>\
**Twitter:** <https://twitter.com/thedancuellar>\
*\
*

</div>

<div>

*\"Dan is the creator of the open source mobile automation framework
Appium, and Head of Test Engineering at FOODit in London. Previously, he
headed the test organisation at Shazam in London and Zoosk in San
Francisco, and worked as a software engineer on Microsoft Outlook for
Mac, and other products in the Microsoft Office suite. He is an advocate
of open source technologies and technical software testing. He earned a
Bachelor's degree in Computer Science, with a minor in Music Technology,
from the world-renowned School of Computer Science at Carnegie Mellon
University in Pittsburgh\".* -[TestCon Vilnius
2016](http://www.testcon.lt/2016/teams/dan-cuellar/) Bio\
\

**Description of the Webinar, Posted on YouTube:**
--------------------------------------------------

\
*For the Appium aficionados amongst us, Dan Cuellar, creator of Appium
and Principal Development Manager at FOODIt, will cover some of the more
esoteric pieces of Appium along with tips and tricks he's assembled from
around the world to help you broaden your knowledge of Appium.*\

<div>

*Topics covered in this webinar will include:\
-Windows and Mac desktop app automation support\
-Preview of the new Appium GUI\
-Tips & Tricks from around the World\
-Deep dive into how some specific pieces of Appium work\
-Q&A from the audience*

</div>

\
[]{#more}\
\

Dan Cuellar\'s Webinar Video and Slides
---------------------------------------

\
Did you miss the Webinar? The video has been uploaded to YouTube.com and
had been embedded below.\
\
**Webinar**: **Appium: Prime with Dan Cuellar**\
Sponsored by [Sauce Labs](https://saucelabs.com/)\
*Published on Mar 8, 2017*\

[*https://youtu.be/D5MF3ZLds0Q*](https://youtu.be/D5MF3ZLds0Q)\
\
**Webinar Slides**: Appium: Prime Cuts\

<div>

\

::: {style="margin-bottom: 5px;"}
**[Appium: Prime
Cuts](https://www.slideshare.net/saucelabs/appium-prime-cuts-webinar "Appium: Prime Cuts")**
from **[Sauce Labs](https://www.slideshare.net/saucelabs)**
:::

\

My Notes from Appium: Prime Cuts
--------------------------------

\
Dan has a great sense of humor: \"I see there are 400 people attending
this webinar. Let\'s see if there are 400 at the end of it. I will try
my best!\"\
\
**[Webinar Agenda]{.underline}**\
\

-   Desktop Apps
-   New Appium GUI: Works for Windows, Mac and Linux
-   Advanced Appium

\

### New: Appium Automates: Desktop Apps for the PC!  

\
Selenium is automation for websites. Appium is automation for apps. At
first? \"App\" only meant automation for mobile apps, but now it means
any type of app\... now including Desktop apps!\
\
Dan made one big announcement after another. First it was the
WinAppDriver project, found in
<http://github.com/Microsoft/WinAppDriver>, a project from Microsoft.\
\
Imagine that: Microsoft themselves are supporting an open-source
movement! It would have been unheard of a few years ago. Now, they have
come up with Selenium WebDriver support and now Appium support!\
\
**Microsoft support includes:**\

-   Modern Universal Windows Platform (UWP) apps
-   Win 32 applications (including pre 2000)
-   Windows Presentation Format (WPF) apps
-   Windows Forms apps
-   Webviews (sometimes)
-   Office and Outlook Plugins

<div>

Coming soon from Microsoft:

</div>

-   Pen & Touch support 
-   Windows Mobile Phone support

\

<div>

**[As Dan Cuellar put it, this is remarkable for just putting in one
year of work into it!]{style="font-weight: normal;"}**

</div>

\

<div>

****\
****

</div>

<div>

****Sidenote:****

</div>

**\
What\'s a Universal Windows Platform (UWP) app? **

</div>

<div>

*2/8/2017*

</div>

<div>

[*https://docs.microsoft.com/en-us/windows/uwp/get-started/whats-a-uwp*](https://docs.microsoft.com/en-us/windows/uwp/get-started/whats-a-uwp)\
\
*\"The Universal Windows Platform (UWP) is the app platform for Windows
10. You can develop apps for UWP with just one API set, one app package,
and one store to reach all Windows 10 devices -- PC, tablet, phone,
Xbox, HoloLens, Surface Hub and more. It's easier to support a number of
screen sizes, and also a variety of interaction models, whether it be
touch, mouse and keyboard, a game controller, or a pen. At the core of
UWP apps is the idea that users want their experiences to be mobile
across ALL their devices, and they want to use whatever device is most
convenient or productive for the task at hand. \[ [Read
More](https://docs.microsoft.com/en-us/windows/uwp/get-started/whats-a-uwp)
\]\"*\
**\
Introducing Windows Presentation Foundation**

</div>

<div>

*9/2006*\
<https://msdn.microsoft.com/en-us/library/aa663364.aspx>\
\
*\"Summary: The primary goal of Windows Presentation Foundation (WPF) is
to help developers create attractive and effective user interfaces.
Learn how the WPF unified platform helps make designers active
participants in creating user interfaces, and provides a common
programming model for standalone and browser applications. \[ [Read
More](https://msdn.microsoft.com/en-us/library/aa663364.aspx) \]\"*

</div>

<div>

\
\
The **Appium: Prime Cuts** video also shows a Microsoft manager testing
the Windows Calculator on a Windows box by kicking off BASH, with Appium
and Python.\
\

### New: Appium Automates: Desktop Apps for the Mac! 

Likewise, there is now a new project for Mac Apps!
<http://github.com/appium/appium-for-mac>\
\
Intuit took Dan Cuellar\'s open-source project and ran with it,
automating QuickBook tests, made adjustments, and just checked in code
back into the project a few months ago.\
**\
Stats on the Mac Version:**\
\

-   Currently run separately from Appium
-   Supports OS X 10.7 and higher
-   Supports detailed mouse actions
-   Support Native DOM
-   Does not support WebViews yet

\
\
Screen Shot On Error is now built in, along with action methods such as
\"get\" to launch an app, \"click\" to click on an element, and \"text\"
to find text from an element.\
\
Dan gave a demo for us on Mac Calculator in Python.\
\
You can download the source code from GitHub, and build it in XCode. In
around three weeks, he was going to type up more detail to help users.\
\
**Want more? **\
\
Dan will be giving a talk on the Selenium Conference in Austin, Texas on
April 5, 2017.\
\
**What is XCode?**\
<https://developer.apple.com/xcode/ide/>\
*\
\"The Xcode IDE \[Integrated Development Environment\] is at the center
of the Apple development experience. Tightly integrated with the Cocoa
and Cocoa Touch frameworks, Xcode is an incredibly productive
environment for building apps for Mac, iPhone, iPad, Apple Watch, and
Apple TV\".*\

### Appium has (yet another) (better) New GUI

\
Note: The GUI is still in beta. Dan Graham, an Appium Developer from
Sauce Labs Vancouver came up with a Appium Desktop app running on
Windows, Mac, and Linux. You can run it off of a server of your
choosing, SauceLabs, or TestObject.\
\
The problem is that it takes so long for the Apple Simulator to load up.
In the video above, Dan goes into a solution that Facebook came up
with.\
\

### How do you Speed Up Tests?

\
1) **Avoid XPath. Xpath is slow**. Avoid using it where possible in
Appium. If you do use it, use it it as a sub-search on a more quickly
found element. There is a known problem is how the Appium team
implemented it. They modelled it on exactness, not efficiency.\
\
2) **Implicit timeouts saves code but can slow down tests**. Use
findElements that returns an array, and see if it is zero. Implicit
checks that last 30 seconds and wait for elements.\
\
\
\... Those are all the notes I have!\
\

A Message from the Webinar\'s Sponsor: Sauce Labs
-------------------------------------------------

And now, messages from this Webinar\'s sponsor, Sauce Labs, sent to me
after the webinar, copied here for your enjoyment:\
\
\"During his presentation, Dan referred to a presentation given by
Lawrence Lomax at SeConf London that discussed ways to speed up testing
on iOS simulators - you can access [the video
here](http://go.saucelabs.com/a0100t0b4X0n00pTVBVsdqX).\
\
\"Interested in Appium training? Sauce Labs now offers instructor-led
online courses on [Appium
101](http://go.saucelabs.com/x0X0000s1Wb0tVB0qXdqnT4) and [Appium
201](http://go.saucelabs.com/htqbXdB00X0004XsV010Trn). [Register
now](http://go.saucelabs.com/Y0Xds0sVq004n001tBX0YTb) and enter promo
code B261-4487-8AF0 to save 20% on either course.\
\
\"For access to our past Sauce Labs webinars, visit our [resources
page](http://go.saucelabs.com/R00tdnbB4X0010q0XZTstV0). As always, if
you have any questions, feedback or ideas, email us at
[webinar\@saucelabs.com](http://go.saucelabs.com/Q0tT0nB0X01t40VbX00vdq0).\
\
\"Happy Testing!\
\"--Your Friends at Sauce Labs\
\
\"P.S. Join Dan as he presents at next month\'s [Selenium
Conference](http://go.saucelabs.com/u1V000nBdt0X0w01tq4XTb0) (Austin,
April 3-5) and at
[SauceCon](http://go.saucelabs.com/j4xB0b1tX00dn0qVTX20t00) (San
Francisco, June 6-8). Get your tickets for [SeConf
here](http://go.saucelabs.com/XXt0qyB0V000Ttdn401bX30) (last call now on
sale) and [SauceCon
here](http://go.saucelabs.com/R00tdnbB4X0010q0X4TtzV0). Hope to see you
at one or both events!\"\
\
\... I, myself, could never afford out-of-pocket Appium\'s prices for
classes. There are so many great classes out there\... well, basically
pre-recorded video\... but the cost is prohibitive. That\'s why I
subscribe to Sauce Labs\' blog \< <https://saucelabs.com/blog> \> so I
can know of any free webinars, and attempt to footnote the free stuff.\
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
