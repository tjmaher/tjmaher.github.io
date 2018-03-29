\-\-- layout: post title: How to create and launch an Android emulator
from Android Studio date: \'2017-05-17T01:06:00.001-04:00\' author: T.J.
Maher tags: - Android Studio - emulator modified\_time:
\'2017-06-16T19:57:09.340-04:00\' thumbnail:
https://2.bp.blogspot.com/-rdbbKEKJfX4/WRuBBz08NPI/AAAAAAAALys/251yak78dPAJCbjMxe9x-8FaTvlDajx2gCLcB/s72-c/1.%2BAndroid%2BDownload.png
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-3273779992938896464
blogger\_orig\_url:
http://www.tjmaher.com/2017/05/launch-android-emulator.html \-\-- Today,
let\'s walk through how to create and launch an Android emulator with
Android Studio.\

###  What does an Android Emulator Consist Of?

\
*\"The Android Emulator runs a full Android system stack, down to the
kernel level, that includes a set of preinstalled apps (such as the
dialer) that you can access from your apps. You can choose which version
of the Android system you want to run in the emulator when creating
AVDs.\
\
\"The Android system images available through the AVD Manager contain
code for the Android Linux kernel, the native libraries, the VM, and the
various Android packages (such as the Android framework and preinstalled
apps)\". - Developer.Android.com, [Run Apps on the Android
Emulator](https://developer.android.com/studio/run/emulator.html)*\
\
\

### Do You Have Android Studio Downloaded?

\
First things first! Do you have Android Studio [downloaded and
installed](https://developer.android.com/studio/index.html)?\
\

::: {.separator style="clear: both; text-align: center;"}
[![](https://2.bp.blogspot.com/-rdbbKEKJfX4/WRuBBz08NPI/AAAAAAAALys/251yak78dPAJCbjMxe9x-8FaTvlDajx2gCLcB/s640/1.%2BAndroid%2BDownload.png){width="640"
height="347"}](https://2.bp.blogspot.com/-rdbbKEKJfX4/WRuBBz08NPI/AAAAAAAALys/251yak78dPAJCbjMxe9x-8FaTvlDajx2gCLcB/s1600/1.%2BAndroid%2BDownload.png)
:::

\

-   Go to <https://developer.android.com/studio/index.html>
-   Press the Download Android Studio button 
-   Go to <https://developer.android.com/studio/install.html> and follow
    Android Developer\'s easy to read Installation instructions. 

\
[]{#more}\
\
Yes, we could just download the standalone Android Command Line Tools,
with:\

-   adb, the [Android Debug
    Bridge](https://developer.android.com/studio/command-line/adb.html)
-   avdmanager, the [Android Virtual Device
    Manager](https://developer.android.com/studio/command-line/avdmanager.html)
-   sdkmanager, the [Android Software Development Kit
    Manager](https://developer.android.com/studio/command-line/sdkmanager.html),
    which allows you to install and update packages. 

\
\... but as I was doing that before, installing the command line tools
as a standalone, I kept on getting warnings messages from the Android
Developer people, that installing them without Android Studio is not
supported by them, and I was on my own by doing it.\
\
Note, we can still used these command line tools via the Mac Terminal
command line. If you open a Mac Terminal and type in to go change into
your home directory, where in your Library in your Home directory, you
can go to the Android SDK Tools directory:\
\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 cd ~/Library/Android/sdk/tools   
```

\
\... You can see the tools there if you do: *ls*\
*\
*\

### Aren\'t The Android OS Versions Named After Candy?

\
Ever since April 2009, when version 1.5 of the Android mobile operating
system was released, the operating systems have been code-named some
type of dessert.\
\
Android supports, at the time of this blog post, Android 6.0
(Marshmallow, API Level 23, Released October 5, 2015), Android 7.0
(Nougat, API Level 24, Released August 22, 2016), and Android 7.1.1
(Nougat, API Level 25, October 4, 2016).\
\
But what devices should we set up? For that, we can go to the **Android
Dashboards** at <https://developer.android.com/about/dashboards/index.html>\
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
Normal screen, hdpi or xhdpi. If we were setting up an automation
framework, it would be good to have an emulator running an older Android
operating system.\
\
\

### Have You Set Android Home?

\
Type in the Mac Terminal:\
\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 echo $ANDROID_HOME  
```

\
\... Is it blank? We need to set up ANDROID\_HOME for your bash
profile.\
\
Note: Want a quick way to Change Directory to your Home Directory via
the Command Line?\
\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 cd ~  
```

\
a) Open up a Mac Terminal\
b) Go into the text editor called \"nano\", opening up your
.bash\_profile\
\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 nano ~/.bash_profile  
```

\
c) Add the following:\
\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 export ANDROID_HOME=~/Library/Android/sdk<br />  
 export PATH=$PATH:$ANDROID_HOME/tools:$ANDROID_HOME/platform-tools<br />  
```

\
\
\... That will set the variable, \"\$ANDROID\_HOME\" as the Library
directory off of your home directory, in the Android/sdk subfolder. Once
that variable is set, we can use it to also point to the /tools and the
/platform-tools subdirectory.\
\
\
d) Save and Close nano by entering:\
\
CNTRL + X (Note: \^ is a shortcut for CNTRL button).\
Y to answer \"Yes\" to saving the changes.\
\[ENTER\] to save changes.\
\
e) Check that it worked:\
\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 source ~/.bash_profile   
 echo $ANDROID_HOME  
```

\
\

### Create an Emulator

\

-   Launch Android Studio
-   Go to Tools -\> Android -\> Android Device Manager

<div>

\

</div>

::: {.separator style="clear: both; text-align: center;"}
[![](https://3.bp.blogspot.com/-fbwGRWotwJc/WRuBR6ps_TI/AAAAAAAALyw/ZDj5wJiXvYAu-FguAJQCfbUYB3wTkyIhQCLcB/s640/2.%2BAndroid%2BVirtual%2BDevice%2BManager.png){width="640"
height="240"}](https://3.bp.blogspot.com/-fbwGRWotwJc/WRuBR6ps_TI/AAAAAAAALyw/ZDj5wJiXvYAu-FguAJQCfbUYB3wTkyIhQCLcB/s1600/2.%2BAndroid%2BVirtual%2BDevice%2BManager.png)
:::

<div>

\

</div>

<div>

\

</div>

<div>

The Android Virtual Device Manager will pop up displaying devices, if
any. 

</div>

<div>

  

</div>

<div>

Select the \"+ Create Virtual Device\...\" button. 

</div>

<div>

\

</div>

::: {.separator style="clear: both; text-align: center;"}
[![](https://2.bp.blogspot.com/-MRuy0TcRLww/WRuBYxxDB7I/AAAAAAAALy0/xXfo-LmYREocfjKWNi5dmkCyaJO0uDXcwCLcB/s640/3.%2BVirtual%2BDevice%2BConfiguration.png){width="640"
height="499"}](https://2.bp.blogspot.com/-MRuy0TcRLww/WRuBYxxDB7I/AAAAAAAALy0/xXfo-LmYREocfjKWNi5dmkCyaJO0uDXcwCLcB/s1600/3.%2BVirtual%2BDevice%2BConfiguration.png)
:::

<div>

\

</div>

<div>

\

</div>

<div>

Here you can select the Hardware you want to emulate, setting up your
Virtual Device Configuration. 

</div>

<div>

\

</div>

<div>

Let\'s try for:

</div>

<div>

-   Phone -\> Pixel (The Google Pixel Phone) 

<div>

\... And select Next. 

</div>

</div>

<div>

\

</div>

<div>

\

</div>

<div>

What operating system do we want to pick? Let\'s try the latest, which
is Android 7.1.1 at the time of this writing. Select the code name
Nougat, API Level 25.

</div>

<div>

\

</div>

<div>

Hit NEXT.

</div>

<div>

\

</div>

<div>

\

</div>

::: {.separator style="clear: both; text-align: center;"}
[![](https://2.bp.blogspot.com/-2Vaw_ad0NF0/WRuOsolHu4I/AAAAAAAALzE/spL1pRcmXWMGmYHFg_lSbSGO0vjqNUv5gCLcB/s640/5.%2BVerify%2BConfiguration.png){width="640"
height="496"}](https://2.bp.blogspot.com/-2Vaw_ad0NF0/WRuOsolHu4I/AAAAAAAALzE/spL1pRcmXWMGmYHFg_lSbSGO0vjqNUv5gCLcB/s1600/5.%2BVerify%2BConfiguration.png)
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

<div>

\

</div>

<div>

\

</div>

<div>

\

</div>

<div>

\

</div>

<div>

\

</div>

<div>

\

</div>

<div>

\

</div>

<div>

\

</div>

<div>

What name to give it? Let\'s change Pixel API 25 to have underscores,
Pixel\_API\_25. 

</div>

<div>

\

</div>

<div>

If you want, select Advanced Settings. You can make it use many
different networks, from Full, HSDPA, UMTS, EDGE. GRPS, HSCSD, and GSM.
You can give it more (or less) RAM, storage space on the SD card, etc. 

</div>

\
\
Select FINISH.\
\
To start up the device, just select the Green Arrow to the right of it.\
\
Wait a few minutes for the phone to boot up.\
\

::: {.separator style="clear: both; text-align: center;"}
[![](https://1.bp.blogspot.com/-N8I8ahs_zXQ/WRuPMy43IdI/AAAAAAAALzM/rujGMrbrDSMgiTaRW9G1J9QtxW1X57d4wCLcB/s640/6.%2BEmulator.png){width="331"
height="640"}](https://1.bp.blogspot.com/-N8I8ahs_zXQ/WRuPMy43IdI/AAAAAAAALzM/rujGMrbrDSMgiTaRW9G1J9QtxW1X57d4wCLcB/s1600/6.%2BEmulator.png)
:::

\
\
\
\
A quick way to install an app on it? Drag-and-drop an .apk on it.\
\

### Does ADB Recognize the Emulator?

Make sure that adb integration is enabled through Android Studio -\>
**Tools** \> **Android** \> **Enable ADB Integration**\
\
\
Go to the Mac Terminal and run: *adb devices*\
\
*List of devices attached*\
*emulator-5554   device*\
\

###  Need More Help?

\
Review:\
\

-   Run Apps on the Android Emulator:
    <https://developer.android.com/studio/run/emulator.html>

\
\

::: {#toc-section .toc-section}
**Build a Basic Appium Framework**\

-   **Part One:** [Review How to Inspect Mobile Apps with Appium
    Desktop](http://www.tjmaher.com/2017/05/basic-appium-framework-part-one.html)
-   **Part Two:**  [Design a Basic Test, Examining Mobile Elements with
    Appium
    Desktop](http://www.tjmaher.com/2017/05/basic-appium-framework-part-two.html)
-   **Part Three:**  [Install and Launch an App Using Desired
    Capabilities](http://www.tjmaher.com/2017/05/build-basic-appium-framework-install.html)
-   **Part Four:**  [Set up the Page Objects, Page Factories and
    Tests](http://www.tjmaher.com/2017/05/basic-appium-framework-part-four.html)
-   **Part Five:**  [Download the tests and run them on your own
    MacBook!](http://www.tjmaher.com/2017/05/basic-appium-framework-part-five.html)
-   **Part Six:  **[How to create and launch an Android emulator from
    Android
    Studio](http://www.tjmaher.com/2017/05/launch-android-emulator.html)
-   **Part Seven**: [What happens behind the scenes as Appium installs
    and launches an Android app? Examining and footnoting a log
    file](http://www.tjmaher.com/2017/06/behind-the-scenes-install-launch-appium.html).
-   **GitHub: **[Review the source code for the
    project.](https://github.com/tjmaher/basic_appium_framework) 
:::

\
Happy Testing!\
\
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
