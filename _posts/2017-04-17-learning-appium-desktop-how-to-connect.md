\-\-- layout: post title: \'Learning Appium Desktop: How to Connect To
Your Android Device Using the Android SDK, the Android Command Line
Tools, and the Android Debug Bridge (adb)\' date:
\'2017-04-17T08:00:00.000-04:00\' author: T.J. Maher tags: - appium
modified\_time: \'2017-04-25T09:03:21.052-04:00\' blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-6465374629735689669
blogger\_orig\_url:
http://www.tjmaher.com/2017/04/learning-appium-desktop-how-to-connect.html
\-\-- *This is Part 2 of 6. Care to [go back to the
beginning](http://www.tjmaher.com/2017/04/learning-appium-what-is-appium-server.html)?
Tune in tomorrow to see the next part!*\
\
Last blog post, we went over how to get the Appium Server running on a
Macbook, through the new Appium Desktop product.\
\
With this post, we are going to cover:\

-   Installing the Android SDK (Software Development Kit) on our Macbook
    through installing Android Studio
-   How to use some command line tools such as adb 
-   How to connect your Android devices wirelessly to your system

### 

### 

### What is the Android SDK?

From [Webotopia](http://www.webopedia.com/TERM/A/Android_SDK.html):
\"A [software](http://www.webopedia.com/TERM/S/software.html)
development kit that enables developers to create
[applications](http://www.webopedia.com/TERM/A/application.html) for the
[Android
platform](http://www.webopedia.com/TERM/A/Android_platform.html). The
Android [SDK](http://www.webopedia.com/TERM/S/SDK.html) includes sample
projects with [source
code](http://www.webopedia.com/TERM/S/source_code.html), development
tools, an [emulator](http://www.webopedia.com/TERM/E/emulator.html), and
required libraries to build Android applications. Applications are
written using the [Java](http://www.webopedia.com/TERM/J/Java.html)
programming language and run on
[Dalvik](http://www.webopedia.com/TERM/D/Dalvik.html), a custom [virtual
machine](http://www.webopedia.com/TERM/V/virtual_machine.html) designed
for embedded use which runs on top of a
[Linux](http://www.webopedia.com/TERM/L/Linux.html) kernel\".\
\
[]{#more}\
\

### What Does the Android SDK Consist Of?

From
[Developer.Android.Com:](https://developer.android.com/studio/command-line/)\

<div>

\"The Android SDK is composed of multiple packages that are required for
app development. This page lists the most important command line tools
that are available, organized by the packages in which they\'re
delivered.\
\
\"You can install and update each package using Android Studio\'s [SDK
Manager](https://developer.android.com/studio/intro/update.html#sdk-manager)
or the
[sdkmanager](https://developer.android.com/studio/command-line/sdkmanager.html)
command line tool. All of the packages are downloaded into your Android
SDK directory\".

</div>

<div>

\

</div>

<div>

Android.com really wants you to use their [Android
Studio](https://developer.android.com/studio/), which comes with an IDE
built on top of IntelliJ IDEA, with the Android SDK and easy ways to
download emulators built in. 

</div>

<div>

\

</div>

<div>

For this proof-of-concept, we are going to try to use the Command Line
tools and steer away from extraneous graphic-user-interfaces besides
Android Desktop. 

</div>

<div>

\

</div>

<div>

Here are some of the packages we will be using, taken
from <https://developer.android.com/studio/command-line/index.html#tools-build>

</div>

\
**[Android SDK Tools]{.underline}: **Located in:
*android\_sdk/tools/bin/*\
\"See also: [SDK Tools release
notes](https://developer.android.com/releases/sdk-tools.html)\
\
\"This package is platform independent and required no matter which
Android platform you are developing on.\
\
\"If you just need these tools because you\'re not using Android Studio,
you can [download the SDK Tools
here](https://developer.android.com/studio/index.html#command-tools).\

<div>

-   \"[avdmanager](https://developer.android.com/studio/command-line/avdmanager.html):
    Allows you to create and manage Android Virtual Devices (AVDs) from
    the command line.
-   \"[sdkmanager](https://developer.android.com/studio/command-line/sdkmanager.html):
    Allows you to view, install, update, and uninstall packages for the
    Android SDK\".

\
**[Android SDK Platform Tools: ]{.underline}**Located in:
*android\_sdk/platform-tools/*\
\"See also: [SDK Platform Tools release
notes](https://developer.android.com/releases/platform-tools.html)\
\
\"These tools are updated for every new version of the Android platform
to support new features (and sometimes more often to fix or improve the
tools), and each update is backward compatible with older platform
versions.\
\
\"In addition to downloading from the SDK Manager, you can [download the
SDK Platform Tools
here](https://developer.android.com/studio/releases/platform-tools.html).

</div>

<div>

-   \"[adb](https://developer.android.com/studio/command-line/adb.html):
    Android Debug Bridge (adb) is a versatile tool that lets you manage
    the state of an emulator instance or Android-powered device. You can
    also use it to install an APK on a device\".

**[Android Emulator: ]{.underline}**Located in:
*android\_sdk/emulator/*\
\"See also: [Android Emulator release
notes](https://developer.android.com/releases/emulator.html)\
\
\"This package is required to use the Android Emulator. It includes the
following:

</div>

<div>

-   \"[emulator](https://developer.android.com/studio/run/emulator-commandline.html):
    A QEMU-based device-emulation tool that you can use to debug and
    test your applications in an actual Android run-time environment\".

### 

### How to Install the Android SDK?

<div>

If we wanted to, we could scroll all the way down to the [bottom of the
Android Studio
page](https://developer.android.com/studio/index.html#Other) where it
says:\

> *\"Get just the command line tools: If you do not need Android Studio,
> you can download the basic Android command line tools below. You can
> use the included
> [sdkmanager](https://developer.android.com/studio/command-line/sdkmanager.html)
> to download other SDK packages. \[\...\] These tools are included in
> Android Studio\".*

\
Instead, let\'s **Download Android Studio**. 

</div>

<div>

\

</div>

<div>

These tools will be all downloaded together. All we would need to do
after is set up our bash\_profile to have the variable \$ANDROID\_HOME
point to the location of the Android SDK, their tools, and their
platform-tools.\
\
\... Why am I setting this up on a Macbook? Because of the Linux system
built into Macbooks.\
\
By getting used to the Mac Terminal, it can get me used to various
SysAdmin type tools I will need to know if I ever want to get into
DevOps (Dev + Ops == System Admin + Dev + QA). It\'s just practice using
the command line.

</div>

### 

### How Do I Install Android Studio?

<div>

-   Go to <https://developer.android.com/studio/index.html> to Download
    Android Studio. 
-   Go to <https://developer.android.com/studio/install.html> and follow
    Android Developer\'s easy to read Installation instructions. 

</div>

###  Once I Install Android Studio, How Do I Find the Path to the Android SDK?

<div>

-   Open up **Android Studio**
-   Go to File -\> Project Structure.
-   See what the path is. It should be something like:
    /Users/tmaher/Library/Android/sdk

###  How Do I Set Up The Terminal to Use These Tools?

The Mac Terminal is running an instance of \"Bash\", the \"Bourne
Again\" shell. We want to add the /Android/sdk/platform-tools and
/Android/sdktools that were placed in your Mac Library by Android Studio
accessible everywhere, not just in the particular directory where the
tools lie.\
\
To set it up, much like we set up JAVA\_HOME, we are going to set up
that location as ANDROID\_HOME for your bash profile.\
\
Note: Want a quick way to Change Directory to your Home Directory via
the Command Line? *cd \~*\
\
a) Open up a Mac Terminal\
b) Go into the text editor called \"nano\", opening up your
.bash\_profile\
\

-   *nano \~/.bash\_profile*

<div>

c\) Add the following:

</div>

<div>

-   *export ANDROID\_HOME=\~/Library/Android/sdk*
-   *export
    PATH=\$PATH:\$ANDROID\_HOME/tools:\$ANDROID\_HOME/platform-tools*

</div>

\
\... That will set the variable, \"\$ANDROID\_HOME\" as the Library
directory off of your home directory, in the Android/sdk subfolder. Once
that variable is set, we can use it to also point to the /tools and the
/platform-tools subdirectory. 

</div>

<div>

\

</div>

<div>

d\) Save and Close nano by entering:

</div>

<div>

-   CNTRL + X (Note: \^ is a shortcut for CNTRL button). 
-   Y to answer \"Yes\" to saving the changes.
-   \[ENTER\] to save changes.

</div>

<div>

\
e) Check that it worked:

</div>

<div>

-   source \~/.bash\_profile 
-   echo \$ANDROID\_HOME

If you had really wanted to be tricky, you could have entered the
following commands on the Command Line:\

-   *echo \"export
    ANDROID\_HOME=\~/Library/Android/sdk\" \>\> \~/.bash\_profile*
-   *echo \"export
    PATH=\$PATH:\$ANDROID\_HOME/tools:\$ANDROID\_HOME/platform-tools\" \>\> \~/.bash\_profile*

\

### What is the Android Debug Bridge?

*From Android Developer's Android Debug Bridge page:
<https://developer.android.com/studio/command-line/adb.html>*

</div>

<div>

"Android Debug Bridge (adb) is a versatile command-line tool that lets
you communicate with a device (an emulator or a connected Android
device). The adb command facilitates a variety of device actions, such
as installing and debugging apps, and it provides access to a Unix shell
that you can use to run a variety of commands on a device. It is a
client-server program that includes three components:\

-   "A **client**, which sends commands. The client runs on your
    development machine. You can invoke a client from a command-line
    terminal by issuing an adb command.
-   "A **daemon** (adbd), which runs commands on a device. The daemon
    runs as a background process on each device.
-   "A **server**, which manages communication between the client and
    the daemon. The server runs as a background process on your
    development machine.

###  How Do Set Up the USB Connection From My Android Device to My Computer?

\
1) Enable USB Debugging, Unhide Developer Options:\

-   Go to your Android phone
-   Go to Settings and scroll down almost to the bottom setting
-   Select About Device. On Build Number, tap seven times. This will
    turn on Developer Mode.
-   Go back to the main Settings screen. There is a new option called
    Developer Options.

\... Once you see this option on screen, if you connect your computer to
your device, you can communicate via USB!\
\
2) Attach a USB Cable from your Android mobile device to your computer.\

-   You may see a popup message on your Android device asking for
    permission to start the connection. Press "OK" to grant it. 
-   Once this is drivers are installed on your system, and the RSA KEY
    is added to your mobile phone. 

\
\
\
3) Confirm that it worked: See the adb devices connected.\
\
Type the following in your Mac Terminal to see if your device is
registered: *adb devices*\
*\
*For the Samsung Galaxy S7 Edge I am using, after setting up Developer
Options, and connecting it via USB, after typing: *adb devices*\
\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 $ adb devices  
 List of devices attached  
 412327b5 device  
```

\
If we had a few emulators attached (which we will do later), we might
see:\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 $ adb devices  
 List of devices attached  
 emulator-5554 device  
 emulator-5555 device  
```

\
\
Remember these names! We will need that name to communicated with the
various real Android devices and the emulators.\
\
\

### Playing Around With ADB

Want more information about the devices? List the long form, by: *adb
android -l*\
*\
*"In response, adb prints this status information for each device:\

-   "Serial number: A string created by adb to uniquely identify the
    device by its port number. Here\'s an example serial number:
    emulator-5554
-   "State: The connection state of the device can be one of the
    following:
-   offline: The device is not connected to adb or is not responding.
-   device: The device is now connected to the adb server. Note that
    this state does not imply that the Android system is fully booted
    and operational because the device connects to adb while the system
    is still booting. However, after boot-up, this is the normal
    operational state of an device.
-   no device: There is no device connected.
-   "Description: If you include the -l option, the devices command
    tells you what the device is. This information is helpful when you
    have multiple devices connected so that you can tell them apart".

\

### How to Install Software to a Device or Emulator

\
Installing an app is simple, once you have it connected. Let's say there
is an Android app, an \*.apk, on the Macbook Desktop called
"helloWorld.apk" that we want to install on an emulator:\
\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 $ adb devices  
   
 List of devices attached  
 emulator-5554 device  
 emulator-5555 device  
   
 $ adb -s emulator-5555 install ~/Desktop/helloWorld.apk  
```

\
\
Remember these Linux shortcuts:\
\
\~ points to your Home Directory, therefore cd \~ takes you home.\
\
Install \~/Downloads/helloWorld.apk would install from a file you
downloaded onto your Mac.\
\
\... There are so many features you can do with adb on the command line.
See <https://developer.android.com/studio/command-line/adb.html> to see
them all! You can:\
\
\

-   Copy files and directories to and from a device pushing and pulling
    files from your device to your computer and back.
-   Install applications, granting run time permissions, allowing test
    packages, installing it on the SD card.
-   Backup all data on the device choosing to back up .apk files or not,
    include system apps or not.
-   Restore all data from a file.
-   Print a bugreport to a zip file.
-   You can start, kill, or reconnect adb.

\
\
Other features we may need\....\
\
\

### Issue ADB shell commands

\
"You can use the shell command to issue device commands through adb,
with or without entering the adb remote shell on the device. To issue a
single command without entering a remote shell, use the shell command".\
\
\

### Call the Package Manager (pm) via Shell

\
Within an adb shell, you can issue commands with the package manager
(pm) tool to perform actions and queries on application packages
installed on the device. While in a shell, the syntax is:\
\
*pm command*\
\
You can also issue a package manager command directly from adb without
entering a remote shell. For example:\
\
*adb shell pm uninstall com.example.MyApp*\
\

### Take a screenshot from the ADB Shell

\
The **screencap** command is a shell utility for taking a screenshot of
a device display. While in a shell, the syntax is:\
\
*screencap filename*\
\
To use the screencap from the command line, type the following:\
\
*adb shell screencap /sdcard/screen.png*\
\
Here\'s an example screenshot session, using the adb shell to capture
the screenshot and the pull command to download the file from the
device:\
\
*\$ adb shell*\
*\
shell@ \$ screencap /sdcard/screen.png*\
*shell@ \$ exit*\
*\
\$ adb pull /sdcard/screen.png*\
\

###  Record a video from the ADB Shell

The screenrecord command is a shell utility for recording the display of
devices running Android 4.4 (API level 19) and higher. The utility
records screen activity to an MPEG-4 file.\
\
Note: Audio is not recorded with the video file.\
\
A developer can use this file to create promotional or training videos.
While in a shell, the syntax is:\
*\
screenrecord \[options\] filename*\
\
To use screenrecord from the command line, type the following:\
\
*adb shell screenrecord /sdcard/demo.mp4*\
\
Stop the screen recording by pressing Control + C, otherwise the
recording stops automatically at three minutes or the time limit set by
\--time-limit.\
\
To begin recording your device screen, run the screenrecord command to
record the video. Then, run the pull command to download the video from
the device to the host computer. Here\'s an example recording session:\
\
*\$ adb shell*\
\
*shell@ \$ screenrecord \--verbose /sdcard/demo.mp4*\
\
(press Control + C to stop)\
*\
shell@ \$ exit*\
*\$ adb pull /sdcard/demo.mp4*\
\
The screenrecord utility can record at any supported resolution and bit
rate you request, while retaining the aspect ratio of the device
display. The utility records at the native display resolution and
orientation by default, with a maximum length of three minutes.\
\
There are some known limitations of the screenrecord utility that you
should be aware of when using it:\
\
Some devices might not be able to record at their native display
resolution. If you encounter problems with screen recording, try using a
lower screen resolution.\
\
\

### List all packages on the device from the ADB Shell:

*\
adb shell pm list packages*\
\

### 

<div>

Next, we will connect our physical Android devices wirelessly to our
computer! See you tomorrow! 

</div>

\
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
\

</div>

<div>

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
