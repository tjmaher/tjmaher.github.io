\-\-- layout: post title: \'Learning Appium Desktop: Setting up Android
Emulators with Android Virtual Device Manager, choosing Android
operating system version\' date: \'2017-04-19T08:00:00.000-04:00\'
author: T.J. Maher tags: - appium modified\_time:
\'2017-06-18T09:17:27.758-04:00\' thumbnail:
https://1.bp.blogspot.com/-PJX-lXJtQA8/WPGoUzvi7NI/AAAAAAAALu0/4LRpqyt-1ok\_Q95TSLScZr7lfJcjw4SRACLcB/s72-c/Screen%2BShot%2B2017-04-15%2Bat%2B12.56.01%2BAM.png
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-1154421333040288436
blogger\_orig\_url:
http://www.tjmaher.com/2017/04/learning-appium-desktop-setting-up.html
\-\-- *This is Part 4 of 6. Care to [go back to the
beginning](http://www.tjmaher.com/2017/04/learning-appium-what-is-appium-server.html)?
Tune in tomorrow to see the next part!*\
*\
*Ever since April 2009, when version 1.5 of the Android mobile operating
system was released, the operating systems have been code-named some
type of dessert.\
\
Android supports, at the time of this blog post, Android 6.0
(Marshmallow, API Level 23, Released October 5, 2015), Android 7.0
(Nougat, API Level 24, Released August 22, 2016), and Android 7.1.1
(Nougat, API Level 25, October 4, 2016).\
\
We\'ll be setting up using **Android Virtual Device Manager** two
virtual Android devices.\
\
[]{#more}\
\
But what devices should we set up? For that, we can go to the **Android
Dashboards**
at <https://developer.android.com/about/dashboards/index.html>\
\

::: {.chart style="background-color: white; color: rgba(0, 0, 0, 0.682353); font-family: Roboto, sans-serif; font-size: 14px;"}
::: {.col-5 style="box-sizing: border-box; float: left; margin-left: 0px; min-height: 1px; padding-left: 10px; padding-right: 10px; position: relative; width: 293.75px;"}
Version
:::
:::

Codename

API

Distribution

[2.3.3 -\
2.3.7](https://developer.android.com/about/versions/android-2.3.3.html)

Gingerbread

10

0.9%

[4.0.3 -\
4.0.4](https://developer.android.com/about/versions/android-4.0.html)

Ice Cream Sandwich

15

0.9%

[4.1.x](https://developer.android.com/about/versions/android-4.1.html)

Jelly Bean

16

3.5%

[4.2.x](https://developer.android.com/about/versions/android-4.2.html)

17

5.1%

[4.3](https://developer.android.com/about/versions/android-4.3.html)

18

1.5%

[4.4](https://developer.android.com/about/versions/android-4.4.html)

KitKat

19

20.0%

[5.0](https://developer.android.com/about/versions/android-5.0.html)

Lollipop

21

9.0%

[5.1](https://developer.android.com/about/versions/android-5.1.html)

22

23.0%

[6.0](https://developer.android.com/about/versions/marshmallow/index.html)

Marshmallow

23

31.2%

[7.0](https://developer.android.com/about/versions/nougat/index.html)

Nougat

24

4.5%

[7.1](https://developer.android.com/about/versions/nougat/android-7.1.html)

25

0.4%

::: {.col-8 style="box-sizing: border-box; float: left; margin-right: 0px; min-height: 1px; padding-left: 10px; padding-right: 10px; position: relative; width: 470px;"}
:::

::: {style="background-color: white; clear: both; color: rgba(0, 0, 0, 0.682353); font-family: Roboto, sans-serif; font-size: 14px; margin-bottom: 12px;"}
*Data collected during a 7-day period ending on April 3, 2017.\
Any versions with less than 0.1% distribution are not shown.*
:::

\
\... And it looks like with screen sizes, most people seem to be using a
Normal screen, hdpi or xhdpi.\
\
Let\'s remember that when we create two emulated devices.\
\

### Android Virtual Device Manager

<div>

\

</div>

<div>

Dependencies and prerequisites\

-   Android Studio 2.0 or higher
-   SDK Tools 25.0.10 or higher
-   adb integration enabled through Android Studio \> Tools \>
    Android \> Enable ADB Integration

\
The easiest way to kick this off is through Android Studio:\
\

-   Launch **Android Studio**
-   Go to **Tools** -\> **Android** -\> **AVD Manager**

\
Once we are at the \"Your Virtual Devices\" homescreen, let\'s select
\"Create Virtual Devices\".\
\
Randomly picking two emulators, I chose:\
\

-   Nexus S, with 480 x 800 resolution, to capture the hdpi screen
    type. 
-   Galaxy Nexus, with 720 x 1280 resolution, to capture the xhdpi
    screen type. 

\
When selecting Operating Systems, let\'s choose the updated version of
Nougat, and the updated version of Marshmallow to start. Later on, it
would be wise to also test on Lollipop, since so many seem to be still
using that Android operating system version.\
\
I needed to download the older versions of Marshmallow, and Lollipop.
They were installed by default in *\~/Library/Android/sdk*.\
\
Nexus S, I paired with Marshmallow, Android 6.0, and gave it an AVD Name
of Nexus S Marshmallow.\
Galaxy Nexus, I paired with Nougat, Android 7.1.1, and dubbed it Galaxy
Nexus Nougat.\
*\
Need more help? See Developer.Android\'s section on Create and Manage
Virtual Devices
at <https://developer.android.com/studio/run/managing-avds.html>*\
\
If you go to the Mac Terminal, you will see if you type: *emulator
-list-avds*\
*\
Galaxy\_Nexus\_Nougat*\
*Nexus\_S\_Marshmallow*\
*\
*Now, we can go back to the AVD Manager, and launch the
Nexus\_S\_Marshmallow.\
\

::: {.separator style="clear: both; text-align: center;"}
[![](https://1.bp.blogspot.com/-PJX-lXJtQA8/WPGoUzvi7NI/AAAAAAAALu0/4LRpqyt-1ok_Q95TSLScZr7lfJcjw4SRACLcB/s640/Screen%2BShot%2B2017-04-15%2Bat%2B12.56.01%2BAM.png){width="640"
height="240"}](https://1.bp.blogspot.com/-PJX-lXJtQA8/WPGoUzvi7NI/AAAAAAAALu0/4LRpqyt-1ok_Q95TSLScZr7lfJcjw4SRACLcB/s1600/Screen%2BShot%2B2017-04-15%2Bat%2B12.56.01%2BAM.png)
:::

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
\
\
Going to the Mac Terminal and running: *adb devices*\
\
*List of devices attached*\
*emulator-5554   device*\
\
So, now we have two emulators set up for testing, with one of them
running!\
\

::: {#toc-section .toc-section}
**Learning Appium Desktop**\

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
