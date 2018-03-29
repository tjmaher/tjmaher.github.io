\-\-- layout: post title: \'Learning Appium Desktop: Find the Desired
Capabilities: appPackage and appActivity. Bug in AAPT if giving just
appName\' date: \'2017-04-20T07:26:00.000-04:00\' author: T.J. Maher
tags: - appium modified\_time: \'2017-05-15T23:58:20.208-04:00\'
thumbnail: https://i.ytimg.com/vi/RDjNPnuyA00/default.jpg blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-1477560175674725764
blogger\_orig\_url:
http://www.tjmaher.com/2017/04/learning-appium-desktop-find-desired.html
\-\-- *This is Part 5 of 6. Care to [go back to the
beginning](http://www.tjmaher.com/2017/04/learning-appium-what-is-appium-server.html)?
Come back in a few days to see the next part!*\
*\
*When I tried running Appium Desktop, I came across some problems. I
decided on using as a sample Android app, a pre-compiled one referred to
me by an Introduction to Appium using Ruby by Dave
Haeffner. <https://github.com/appium/ruby_lib/blob/master/android_tests/api.apk>\
First, I started an emulator using Android Studio. Then, I started
Appium Desktop.\
Then I pressed: Select Start Server v1.6.4-beta -\> Select Start New
Session\
\
For Desired Capabilities:\

-   platformName:      Android
-   deviceName: emulator-5554
-   app:
    <https://github.com/appium/ruby_lib/blob/master/android_tests/api.apk>

<div>

Appium can interact with a mobile app in a few ways:

</div>

<div>

-   Is the app already on the emulator or actual device? You need to
    find the package name and the activity name of the app you want to
    run, and pass that into the DesiredCapabilities.
-   You can pass the .apk into the app field of the DesiredCapabilities,
    and Appium will install the app itself. You won\'t have to:  *adb -s
    emulator-5554 install myapp.apk*

</div>

<div>

That didn\'t work. I noticed a few errors when looking at the Appium
Server.

</div>

<div>

\
[]{#more}\

</div>

<div>

Everything started off okay. Appium fed the desired capabilities into a
new AndroidDriver session. Checked that ADB was in
/Library/Android/sdk/platform-tools/adb. It saw that one device,
emulator-5554 was present. It download the app to an internal folder,
installing it to the emulator, and started setting up the device. 

</div>

<div>

\

</div>

<div>

Then an error happened:

</div>

\

::: {style="background-color: white; color: #222222; font-family: arial, sans-serif; font-size: 12.8px;"}
::: {style="background-color: #222222; box-sizing: border-box; color: #cccccc; font-family: inconsolata, "lucida console", monaco, monospace; font-size: 12px; margin: 0px; padding: 0px; white-space: pre-wrap;"}
[Appium\] Welcome to Appium v1.6.4]{style="box-sizing: border-box;"}
:::

::: {style="background-color: #222222; box-sizing: border-box; color: #cccccc; font-family: inconsolata, "lucida console", monaco, monospace; font-size: 12px; margin: 0px; padding: 0px; white-space: pre-wrap;"}
[]{.m_1737616286037327527gmail-ServerMonitor__icon___mfiRx
.m_1737616286037327527gmail-anticon
.m_1737616286037327527gmail-anticon-info-circle
style="box-sizing: border-box; display: inline-block; font-size: 0.9em; line-height: 1; margin-right: 8px; text-align: center; vertical-align: baseline; width: 10px;"}[\[Appium\]
Appium REST http interface listener started on
[0.0.0.0:4723](http://0.0.0.0:4723/)]{style="box-sizing: border-box;"}
:::

::: {style="background-color: #222222; box-sizing: border-box; color: #cccccc; font-family: inconsolata, "lucida console", monaco, monospace; font-size: 12px; margin: 0px; padding: 0px; white-space: pre-wrap;"}
[]{.m_1737616286037327527gmail-ServerMonitor__icon___mfiRx
.m_1737616286037327527gmail-anticon
.m_1737616286037327527gmail-anticon-info-circle
style="box-sizing: border-box; display: inline-block; font-size: 0.9em; line-height: 1; margin-right: 8px; text-align: center; vertical-align: baseline; width: 10px;"}\
:::

::: {style="background-color: #222222; box-sizing: border-box; color: #cccccc; font-family: inconsolata, "lucida console", monaco, monospace; font-size: 12px; margin: 0px; padding: 0px; white-space: pre-wrap;"}
[]{.m_1737616286037327527gmail-ServerMonitor__icon___mfiRx
.m_1737616286037327527gmail-anticon
.m_1737616286037327527gmail-anticon-message
style="box-sizing: border-box; display: inline-block; font-size: 0.9em; line-height: 1; margin-right: 8px; text-align: center; vertical-align: baseline; width: 10px;"}[\[AndroidDriver\]
AndroidDriver version: 1.17.1]{style="box-sizing: border-box;"}
:::

::: {style="background-color: #222222; box-sizing: border-box; color: #cccccc; font-family: inconsolata, "lucida console", monaco, monospace; font-size: 12px; margin: 0px; padding: 0px; white-space: pre-wrap;"}
[. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
. . . . . . .]{style="box-sizing: border-box;"}
:::

::: {style="background-color: #222222; box-sizing: border-box; color: #cccccc; font-family: inconsolata, "lucida console", monaco, monospace; font-size: 12px; margin: 0px; padding: 0px; white-space: pre-wrap;"}
[]{.m_1737616286037327527gmail-ServerMonitor__icon___mfiRx
.m_1737616286037327527gmail-anticon
.m_1737616286037327527gmail-anticon-exclamation-circle
style="box-sizing: border-box; display: inline-block; font-size: 0.9em; line-height: 1; margin-right: 8px; text-align: center; vertical-align: baseline; width: 10px;"}\
:::

::: {style="background-color: #222222; box-sizing: border-box; color: #cccccc; font-family: inconsolata, "lucida console", monaco, monospace; font-size: 12px; margin: 0px; padding: 0px; white-space: pre-wrap;"}
\
:::

::: {style="background-color: #222222; box-sizing: border-box; color: #cccccc; font-family: inconsolata, "lucida console", monaco, monospace; font-size: 12px; margin: 0px; padding: 0px; white-space: pre-wrap;"}
[]{.m_1737616286037327527gmail-ServerMonitor__icon___mfiRx
.m_1737616286037327527gmail-anticon
.m_1737616286037327527gmail-anticon-message
style="box-sizing: border-box; display: inline-block; font-size: 0.9em; line-height: 1; margin-right: 8px; text-align: center; vertical-align: baseline; width: 10px;"}[\[AndroidDriver\]
Parsing package and activity from app
manifest]{style="box-sizing: border-box;"}
:::

::: {style="background-color: #222222; box-sizing: border-box; color: #cccccc; font-family: inconsolata, "lucida console", monaco, monospace; font-size: 12px; margin: 0px; padding: 0px; white-space: pre-wrap;"}
[]{.m_1737616286037327527gmail-ServerMonitor__icon___mfiRx
.m_1737616286037327527gmail-anticon
.m_1737616286037327527gmail-anticon-info-circle
style="box-sizing: border-box; display: inline-block; font-size: 0.9em; line-height: 1; margin-right: 8px; text-align: center; vertical-align: baseline; width: 10px;"}[\[ADB\]
Checking whether aapt is present]{style="box-sizing: border-box;"}
:::

::: {style="background-color: #222222; box-sizing: border-box; color: #cccccc; font-family: inconsolata, "lucida console", monaco, monospace; font-size: 12px; margin: 0px; padding: 0px; white-space: pre-wrap;"}
[]{.m_1737616286037327527gmail-ServerMonitor__icon___mfiRx
.m_1737616286037327527gmail-anticon
.m_1737616286037327527gmail-anticon-info-circle
style="box-sizing: border-box; display: inline-block; font-size: 0.9em; line-height: 1; margin-right: 8px; text-align: center; vertical-align: baseline; width: 10px;"}[\[ADB\]
Using aapt from
/Users/ventmahe/Library/Android/sdk/build-tools/23.0.1/aapt]{style="box-sizing: border-box;"}
:::

::: {style="background-color: #222222; box-sizing: border-box; color: #cccccc; font-family: inconsolata, "lucida console", monaco, monospace; font-size: 12px; margin: 0px; padding: 0px; white-space: pre-wrap;"}
[]{.m_1737616286037327527gmail-ServerMonitor__icon___mfiRx
.m_1737616286037327527gmail-anticon
.m_1737616286037327527gmail-anticon-info-circle
style="box-sizing: border-box; display: inline-block; font-size: 0.9em; line-height: 1; margin-right: 8px; text-align: center; vertical-align: baseline; width: 10px;"}[\[ADB\]
Extracting package and launch activity from
manifest]{style="box-sizing: border-box;"}
:::

::: {style="background-color: #222222; box-sizing: border-box; color: #cccccc; font-family: inconsolata, "lucida console", monaco, monospace; font-size: 12px; margin: 0px; padding: 0px; white-space: pre-wrap;"}
[]{.m_1737616286037327527gmail-ServerMonitor__icon___mfiRx
.m_1737616286037327527gmail-anticon
.m_1737616286037327527gmail-anticon-close-circle
style="box-sizing: border-box; display: inline-block; font-size: 0.9em; line-height: 1; margin-right: 8px; text-align: center; vertical-align: baseline; width: 10px;"}[\[ADB\]
Error: packageAndLaunchActivityFromManifest failed. Original error:
Command \'/Users/ventmahe/Library/Android/sdk/build-tools/23.0.1/aapt
dump badging
/var/folders/0h/hf79m7zj1xz1hdk0m3t091v8221rx6/T/2017315-9300-iudoh3.0zthyhw7b9/appium-app.apk\'
exited with code 1]{style="box-sizing: border-box;"}
:::
:::

\
\
Huh? What the heck is AAPT? What is a \"Manifest\"? What the heck is
\"Dump Badging\"?\
\
For this blog post, we will start attempting to troubleshoot these
errors.\
\

### The Android Asset Packaging Tool

There are many steps to create a **Android Application Package** (APK).\

> *\"aapk stands for **Android Asset Packaging Tool**. This tool is part
> of the SDK (and build system) and allows you to view, create, and
> update Zip-compatible archives (zip, jar, apk). It can also compile
> resources into binary assets. Build scripts and IDE plugins utilize
> this tool to package the apk file that constitutes an Android
> application\". - ELinux.org:
> [Android\_aapt](http://elinux.org/Android_aapt)*

By typing aapt, I was supposed to see:\

<div>

\

</div>

<div>

``` {style="background-color: #f9f9f9; border: 1px solid rgb(221, 221, 221); font-family: monospace, Courier; font-size: 14px; line-height: 1.3em; padding: 1em;"}
$ aapt
Android Asset Packaging Tool

Usage:
 aapt l[ist] [-v] [-a] file.{zip,jar,apk}
   List contents of Zip-compatible archive.

 aapt d[ump] [--values] WHAT file.{apk} [asset [asset ...]]
   badging          Print the label and icon for the app declared in APK.
   permissions      Print the permissions from the APK.
   resources        Print the resource table from the APK.
   configurations   Print the configurations in the APK.
   xmltree          Print the compiled xmls in the given assets.
   xmlstrings       Print the strings of the given compiled xml assets.
```

\
\... But whenever I entered in the Mac Terminal: *aapt*\
\
aapt: Command Not Found

</div>

<div>

\

</div>

<div>

\... I even tried going into the directory where it was supposed to
be: *cd \~/Library/Android/sdk/build-tools/23.0.1/aapt \...* and run the
command there. Command not found. 

</div>

<div>

\

</div>

<div>

Hrm\... there seemed to be three versions of build tools:

</div>

<div>

-   23.0.1 (where Appium insisted on pointing to)
-   23.0.3
-   25.0.0
-   25.0.1
-   25.0.2

<div>

\... And if I go into 25.0.2, it still says: aapt, command not found. 

</div>

\
What is supposed to happen? Contents of the Android Application Package,
should be listed:

</div>

<div>

\

</div>

<div>

``` {style="background-color: #f9f9f9; border: 1px solid rgb(221, 221, 221); font-family: monospace, Courier; font-size: 14px; line-height: 1.3em; padding: 1em;"}
$ aapt list SpareParts.apk 
META-INF/MANIFEST.MF
META-INF/CERT.SF
META-INF/CERT.RSA
AndroidManifest.xml
classes.dex
res/drawable-hdpi/app_icon.png
```

\... But the tool does not seem to be found.\
\
If the tool could be found, aapt would unpack and decode the APK, then
read AndroidManifest.xml in plaintext.

</div>

<div>

\

</div>

### What is the Android Manifest.xml?

<div>

*From **Android Developers: App Manifest**
Page: <https://developer.android.com/guide/topics/manifest/manifest-intro.html>*\

<div>

\

</div>

\"Every application must have an AndroidManifest.xml file (with
precisely that name) in its root directory. The manifest file provides
essential information about your app to the Android system, which the
system must have before it can run any of the app\'s code.\
\
\"Among other things, the manifest file does the following:\

-   \"It names the Java package for the application. The package name
    serves as a unique identifier for the application.
-   \"It describes the components of the application, which include the
    activities, services, broadcast receivers, and content providers
    that compose the application. It also names the classes that
    implement each of the components and publishes their capabilities,
    such as the
    [Intent](https://developer.android.com/reference/android/content/Intent.html)
    messages that they can handle. These declarations inform the Android
    system of the components and the conditions in which they can be
    launched.
-   \"It determines the processes that host the application components.
-   \"It declares the permissions that the application must have in
    order to access protected parts of the API and interact with other
    applications. It also declares the permissions that others are
    required to have in order to interact with the application\'s
    components.
-   \"It lists the
    [Instrumentation](https://developer.android.com/reference/android/app/Instrumentation.html)
    classes that provide profiling and other information as the
    application runs. These declarations are present in the manifest
    only while the application is being developed and are removed before
    the application is published.
-   \"It declares the minimum level of the Android API that the
    application requires.
-   \"It lists the libraries that the application must be linked
    against\".

\... If it can\'t:\
\

-   Extract the pieces of the manifest from the AndroidManifest.xml 
-   Find the package name that needs to be run
-   Find the activity that needs to be started

<div>

\... Then the app can not launch, whether it is on an actual device, or
installed in an emulator. 

</div>

\

###  Maybe there is hope?

After spending the past three days on this problem, I found a bug
report, [**What do you do when "Command aapt dump badging exits with
code
1"?**](https://discuss.appium.io/t/what-do-you-do-when-command-aapt-dump-badging-exits-with-code-1/9966)\
\
\"[This is a bug within aapt itself, and as you can tell from the build
tools version, the bug is also apparent in the next stable release of
the build tools. Here is some links showing that the bug has been around
for quite a
while:]{style="background-color: #fafafa; color: #222222; font-family: "helvetica" , "arial" , sans-serif; font-size: 14px;"}\

1.  [http://stackoverflow.com/questions/17008364/aapt-error-getting-androidname-attribute-attribute-is-not-a-string-value[9]{.badge
    .badge-notification .clicks
    style="background-color: #e4e4e4; border-radius: 10px; border: none; color: #7a7a7a; display: inline-block; font-size: 11px; line-height: 1; margin-left: 2px; padding: 4px 5px 2px; position: relative; text-align: center; top: -1px; vertical-align: middle; white-space: nowrap;"
    title="9 clicks"}](http://stackoverflow.com/questions/17008364/aapt-error-getting-androidname-attribute-attribute-is-not-a-string-value)
2.  [https://code.google.com/p/android/issues/detail?id=46311[6]{.badge
    .badge-notification .clicks
    style="background-color: #e4e4e4; border-radius: 10px; border: none; color: #7a7a7a; display: inline-block; font-size: 11px; line-height: 1; margin-left: 2px; padding: 4px 5px 2px; position: relative; text-align: center; top: -1px; vertical-align: middle; white-space: nowrap;"
    title="6 clicks"}](https://code.google.com/p/android/issues/detail?id=46311)

::: {style="background-color: #fafafa; color: #222222; font-family: Helvetica, Arial, sans-serif; font-size: 14px;"}
\"This bug will affect you if certain manifest elements\' attributes
refer to XML string resources using
the `@string/string_name`{style="background: rgb(248, 248, 248); color: #333333; font-family: Consolas, Menlo, Monaco, "Lucida Console", "Liberation Mono", "DejaVu Sans Mono", "Bitstream Vera Sans Mono", "Courier New", monospace; font-size: 1em;"} format.
Some example manifest elements where this bug can occur
are `<meta-data ...>`{style="background: rgb(248, 248, 248); color: #333333; font-family: Consolas, Menlo, Monaco, "Lucida Console", "Liberation Mono", "DejaVu Sans Mono", "Bitstream Vera Sans Mono", "Courier New", monospace; font-size: 1em;"} and `<category ...>`{style="background: rgb(248, 248, 248); color: #333333; font-family: Consolas, Menlo, Monaco, "Lucida Console", "Liberation Mono", "DejaVu Sans Mono", "Bitstream Vera Sans Mono", "Courier New", monospace; font-size: 1em;"}.
:::

::: {style="background-color: #fafafa; color: #222222; font-family: Helvetica, Arial, sans-serif; font-size: 14px;"}
\"In any case, this bug can cause Appium to fail because Appium needs
aapt to retrieve the package name and launch activity from the APK.\[1\]
:::

::: {style="background-color: #fafafa; color: #222222; font-family: Helvetica, Arial, sans-serif; font-size: 14px;"}
\"My workaround for this bug is to explicitly tell Appium which
application package and activity to launch, so Appium does not need to
run `aapt dump badging`{style="background: rgb(248, 248, 248); color: #333333; font-family: Consolas, Menlo, Monaco, "Lucida Console", "Liberation Mono", "DejaVu Sans Mono", "Bitstream Vera Sans Mono", "Courier New", monospace; font-size: 1em;"}.
As an example in Java code:
:::

``` {style="background-color: #fafafa; color: #222222; font-family: Consolas, Menlo, Monaco, "Lucida Console", "Liberation Mono", "DejaVu Sans Mono", "Bitstream Vera Sans Mono", "Courier New", monospace; font-size: 14px; overflow: auto;"}
caps.setCapability(AndroidMobileCapabilityType.APP_PACKAGE, "com.example.app");
caps.setCapability(AndroidMobileCapabilityType.APP_ACTIVITY, ".MainActivity");
```

\
\... Okay\... all we need to do is set the Desired Capabilities
appPackage and appActivity.\
\

### How to Find the Desired Capabilites: App Package and App Activity?

\
**ADB Commands- How to find App Package & App Activity for Android
App?**\

[*https://youtu.be/RDjNPnuyA00*](https://youtu.be/RDjNPnuyA00)\
\
\
\"**Method 1:**  adb shell \"dumpsys window windows \| grep -E
\'mCurrentFocus \| mFocusedApp\'\"

</div>

<div>

\
\"**Method 2:** aapt dump badging AppApkName.apkOR./ aapt dump badging
AppApkName.apk ***(UGH!!!)***

</div>

<div>

\
\"**Method 3**: APK
Info: <https://play.google.com/store/apps/details?id=com.intelloware.apkinfo&hl=en>\
\
Okay, now we might be getting somewhere! Let\'s try Method 1.\
**\
Step One**: Check to see if there are any Android devices running. If
not, start an emulator or an actual Android device\

-   My Samsung Galaxy S7 Edge that already has Developer Options turned
    on. I connected it to my MacBook via USB. 
-   On the Mac Terminal, enter: avd devices 
-   It showed that in the list of devices attached, there was device:
    412327b5 

**Step Two:** On the Android device or emulator, run the app you want to
inspect.\

-   Okay! Let\'s run the Calculator app!

**\
Step Three:** Run the app on the device and find the appPackage and
appActivity.\

-   Let\'s say the magic words to take all the system properties on the
    device, grab just what is running in the current window on the app,
    what is in focus, and dump those properties onto the screen. 
-   This will be a call to the adb shell, i.e. the device that is
    connected to adb. 
-   Type in the Mac Terminal: adb shell \"dumpsys window windows \| grep
    -E \'mCurrentFocus \| mFocusedApp\'\" 

\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 $adb shell "dumpsys window windows | grep -E 'mCurrentFocus | mFocusedApp'"  
   
mFocusedApp=AppWindowToken{d0d077a06 
token = Token { fc44ce1 ActivityRecord{4158648 u0 
com.sec.android.app.popupcalculator/.Calculator t352}}}  
```

\

-   This shows that the appPackage is
    *com.sec.android.app.popupcalculator*
-   This also shows that the appActivity is *.Calculator*

\
**Step Four**: Start up Android Desktop\
\

-   Click on the Appium Desktop icon
-   Leaving everything at default, let\'s select: Start Server v1.6.4 on
    the main page
-   Once we see the server is running, let\'s: Start New Session
-   Now we see that the desired capabilities are showing.

\
**Step Five:** Enter Desired Capabilities and Save Them\
\

-   platformName: Android
-   deviceName: 412327b5
-   appPackage: com.sec.android.app.popupcalculator
-   appActivity: .Calculator

\
Let\'s select \"Save As\...\" and save it as \"Calculator\".\
\
**Step Six**: Start the New Session!\
\

-   Select: Start Session

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://2.bp.blogspot.com/-prLNYAWBjKg/WPMjdZlFU3I/AAAAAAAALvE/tmKyBcpqyA8PLdmvlkiExGzVfIV55ddXwCLcB/s640/Screen%2BShot%2B2017-04-16%2Bat%2B3.52.25%2BAM.png){width="640" height="332"}](https://2.bp.blogspot.com/-prLNYAWBjKg/WPMjdZlFU3I/AAAAAAAALvE/tmKyBcpqyA8PLdmvlkiExGzVfIV55ddXwCLcB/s1600/Screen%2BShot%2B2017-04-16%2Bat%2B3.52.25%2BAM.png)
                                                                                                                                                                        *It\'s Alive!!!!*
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

\
\
Now that we have everything working, we can start using Appium Desktop
to start inspecting how to interact with this app!\
\
Whew! This one took three days to research! I need to take a break and
focus on finishing off my
next [TechBeacon](http://techbeacon.com/contributors/thomas-maher) article
by Monday. Check back here next Wednesday, and we can finish this one
off. Until next time!\
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
\
Happy Testing!\
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
