\-\-- layout: post title: What happens behind the scenes as Appium
installs and launches an Android app? Examining and footnoting a log
file. date: \'2017-06-05T23:24:00.002-04:00\' author: T.J. Maher tags: -
appium modified\_time: \'2017-06-16T20:19:38.982-04:00\' thumbnail:
https://1.bp.blogspot.com/-DoBx61s9wHY/WSDm1f-9bQI/AAAAAAAAL0I/Ghpx7UXZCXE6COTYuw9h859jzv0uJM6GQCPcB/s72-c/Appium%2BConsole.png
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-5781459829025354288
blogger\_orig\_url:
http://www.tjmaher.com/2017/06/behind-the-scenes-install-launch-appium.html
\-\-- *This is part seven of of a seven-part blog series. Care to
go [back to the
beginning](http://www.tjmaher.com/2017/05/basic-appium-framework-part-one.html)?*\
*\
*Have you ever wondered what is happening behind-the-scenes as Appium
launches an app? Well, there is one way to find out\...\
\
Today, we will be taking a look at the log files captured in the Appium
console, generated after I launch the APIDemos-debug.apk Android app,
with the help of Appium, onto an Android emulator.\
\
\... Actually, this blog article wasn\'t written in a day. It took more
than a few weekends to thoroughly research everything\... and I do mean
everything!\
\
There are possible errors or questions on the inner workings on Appium,
with insightful statements such as \... \"Huh? What\'s this?\" \... They
are **[*highlighted in red*]{style="color: red;"}**.\
\
Is there anything I am wrong about? Please let me know! I am a complete
novice when it comes to Appium (although, I have [been hideously
busy](http://www.tjmaher.com/p/programming-projects.html)).  I only
started learning it in March of 2017. The reason I am blogging about
this is because I actually *want* you to comment if I am completely
off-base, or if I am error about the inner workings of Appium or the
world of Android development.\
\
[]{#more}\
\
\
What is an APK?\
\

-   APK stands for Android Application Package

\
*\"Android Package Kit (APK) is the package file format used by the
Android operating system for distribution and installation of mobile
apps and middleware \[\...\] To make an APK file, a program for Android
is first compiled, and then all of its parts are packaged into one file.
An APK file contains all of that program\'s code \[\...\] resources,
assets, certificates, and [manifest
file](https://en.wikipedia.org/wiki/Manifest_file). As is the case with
many file formats, APK files can have any name needed, provided that the
file name ends in \".apk\" \[\...\] APK files are a type of archive
file, specifically in zip format packages based on the [JAR file
format](https://en.wikipedia.org/wiki/JAR_(file_format)), with .apk as
the [filename
extension](https://en.wikipedia.org/wiki/Filename_extension). The [MIME
type](https://en.wikipedia.org/wiki/Internet_media_type) associated with
APK files is application/vnd.android.package-archive.\]\" - [Wikipedia,
Android Package
Kit.](https://en.wikipedia.org/wiki/Android_application_package) *\

<div>

\
When you first start the Appium console, Appium patiently waits in the
background\...\
\
[\[Appium\] Welcome to Appium v1.6.4\
\[Appium\] Appium REST http interface listener started
on 0.0.0.0:4723]{style="background-color: #eeeeee;"}\
\
\... but when you feed a set of Desired Capabilites to it, and Appium
finds an emulator matching them, a flurry of activity happens as it
installs the app on the emulator. It will use a series of Android
command line tools to inspect the emulator, find Android application
packages that are running, and inspect these APKs, check if there are
any special settings, and Appium will launch them.\
\
How does the Appium Server start?\

> *It works the similar way as
> common [ChromeDriver](https://selenium.googlecode.com/git/docs/api/java/org/openqa/selenium/chrome/ChromeDriver.html), [InternetExplorerDriver](https://selenium.googlecode.com/git/docs/api/java/org/openqa/selenium/ie/InternetExplorerDriver.html) of
> Selenium project
> or [PhantomJSDriver](http://cdn.ivandemarino.me/phantomjsdriver-javadoc/org/openqa/selenium/phantomjs/PhantomJSDriver.html).
> They use subclasses of
> the [DriverService](https://selenium.googlecode.com/git/docs/api/java/org/openqa/selenium/remote/service/DriverService.html).\
> This feature provides abilities and options of the starting of a local
> Appium node server. End users still able to open apps as usual. -
> Appium Java Client Docs, [The Starting of an App Using Appium Node
> Server](https://github.com/appium/java-client/blob/master/docs/The-starting-of-an-app-using-Appium-node-server-started-programmatically.md).*

\
\

::: {.separator style="clear: both; text-align: center;"}
[![](https://1.bp.blogspot.com/-DoBx61s9wHY/WSDm1f-9bQI/AAAAAAAAL0I/Ghpx7UXZCXE6COTYuw9h859jzv0uJM6GQCPcB/s640/Appium%2BConsole.png){width="640"
height="590"}](https://1.bp.blogspot.com/-DoBx61s9wHY/WSDm1f-9bQI/AAAAAAAAL0I/Ghpx7UXZCXE6COTYuw9h859jzv0uJM6GQCPcB/s1600/Appium%2BConsole.png)
:::

\
\
\
Let\'s review what is happening, section by section\...\
\

### What Are We Feeding That Thing?

For this example, we are sending to Appium the code:\
\

``` {style="background: rgb(240, 240, 240); border: 1px dashed rgb(204, 204, 204); font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; width: 646.469px;"}
 final String URL_STRING = "http://127.0.0.1:4723/wd/hub";
 URL url = new URL(URL_STRING);

 File app = new File("ApiDemos-debug.apk");  
 DesiredCapabilities caps = new DesiredCapabilities();  
 caps.setCapability(MobileCapabilityType.DEVICE_NAME, "emulator-5554");  
 caps.setCapability(MobileCapabilityType.APP, app.getAbsolutePath());  
 caps.setCapability(MobileCapabilityType.PLATFORM_NAME, MobilePlatform.ANDROID);  
 AndroidDriver driver = new AndroidDriver(url, caps);  
```

-   Appium Server is listening on 127.0.0.1.
-   The Android emulator is on emulator-555-4, and if we use *adb
    devices*, we will see it in the list
-   The code above sets a String constant URL\_STRING and a url variable
    the value of our old friend localhost, the Home IP, 127.0.0.1. 
-   /wd/hub is our old friend, the Selenium Hub, part of the Selenium
    Grid. 
-   When a new instance of AndroidDriver is created, we are setting it
    to the Selenium Hub and Appium Server listening in at 127.0.0.1, and
    passing along the DesiredCapabilities. Appium will be connected to
    the Selenium Grid. 

\
*\"What is
Selenium-Grid?[](http://www.seleniumhq.org/docs/07_selenium_grid.jsp#what-is-selenium-grid)\
\
\"Selenium-Grid allows you run your tests on different machines against
different browsers in parallel. That is, running multiple tests at the
same time against different machines running different browsers and
operating systems. Essentially, Selenium-Grid support distributed test
execution. It allows for running your tests in a distributed test
execution environment.\
\
\"When to Use
It[](http://www.seleniumhq.org/docs/07_selenium_grid.jsp#when-to-use-it)\
\
\"Generally speaking, there are two reasons why you might want to use
Selenium-Grid.*\

-   *\"To run your tests against multiple browsers, multiple versions of
    browser, and browsers running on different operating systems.*
-   *\"To reduce the time it takes for the test suite to complete a test
    pass.*

*\"Selenium-Grid is used to speed up the execution of a test pass by
using multiple machines to run tests in parallel\". - [Selenium HQ Docs,
Selenium Grid](http://www.seleniumhq.org/docs/07_selenium_grid.jsp)*\
\
[\[HTTP\] \--\> POST /wd/hub/session
{\"desiredCapabilities\":{\"app\":\"/Users/ventmahe/code/basic\_appium\_framework/ApiDemos-debug.apk\",\"platformName\":\"Android\",\"deviceName\":\"emulator-5554\"}}]{style="background-color: #eeeeee;"}\

-   The desired capabilities are being posted via HTTP, to the Selenium
    Grid that Appium is connected to, much as if you were submitting a
    web form, POST-ing it to another service. 

[\
\[MJSONWP\] Calling AppiumDriver.createSession() with args:
\[{\"app\":\"/Users/ventmahe/code/basic\_appium\_framework/ApiDemos-debug.apk\",\"platformName\":\"Android\",\"deviceName\":\"emulator-5554\"},null,null,null,null\]]{style="background-color: #eeeeee;"}\

<div>

\

</div>

<div>

-   Next, we have the Mobile JSON Wire Protocol calling the Appium
    Driver Method, create session with the arguments we passed into the
    DesiredCapabilites: where the app is located (the absolute path),
    the platform name (Android), and the deviceName (emulator-5554). 
-   *See official documentation [on the JSON Wire
    Protocol](https://github.com/SeleniumHQ/selenium/wiki/JsonWireProtocol).*
-   *See the [Mobile JSON Wire errors that can be
    thrown](https://github.com/appium/appium-base-driver/blob/master/docs/mjsonwp/errors.md) in
    the Appium Base Driver on Appium\'s GitHub site. *

**The Mobile JSON Wire Protocol**

[*https://youtu.be/wjvAh4yjwtI*](https://youtu.be/wjvAh4yjwtI)\

<div>

\
\
\
[\[BaseDriver\] Event \'newSessionRequested\' logged at 1495296256238
(12:04:16 GMT-0400 (EDT))]{style="background-color: #eeeeee;"}\
\

-   The Appium Base Driver registers when the new session was requested
    in Greenwich Mean Time (-400) since I am in Quincy, MA when the
    request was made. Eastern Daylight Time.
-   What is the Appium base driver? 

> *\"This is the parent class that
> all [appium](https://github.com/appium/appium-base-driver/blob/master/lib/basedriver/appium.io) drivers
> inherit from. Appium drivers themselves can either be started from the
> command line as standalone appium servers, or can be included by
> another module (appium) which then proxies commands to the appropriate
> driver based on [Desired
> Capabilities](https://github.com/appium/appium/blob/master/docs/en/writing-running-appium/caps.md).\
> \"An appium driver is a module which processes [Mobile Json Wire
> Protocol](https://code.google.com/p/selenium/source/browse/spec-draft.md?repo=mobile) commands
> and controls a device accordingly. The commands can either come in
> over HTTP as json api requests, or they can be passed to the driver
> object programmatically as already-parsed json object (without the
> HTTP headers and junk).\
> \"The appium Base driver already includes
> the [mjsonwp](https://github.com/appium/appium-base-driver/blob/master/lib/mjsonwp/README.md) module,
> which is the HTTP server that converts incoming requests into json
> objects that get sent to the driver programmatically.\
> \"The appium Base driver already has all the REST api routes,
> validation, and error codes supplied
> by [mjsonwp](https://github.com/appium/appium-base-driver/blob/master/lib/mjsonwp/README.md).\
> \"Appium drivers are designed to have a single testing session per
> instantiation. This means that one Driver object should be attached to
> a single device and handle commands from a single client. - [Github /
> Appium / Appium-Base-Driver /
> lib](https://github.com/appium/appium-base-driver/tree/master/lib/basedriver) /
> basedriver*

<div>

*\
*

</div>

[*\
*]{style="background-color: #eeeeee;"}[\[Appium\] Creating new
AndroidDriver (v1.17.1) session]{style="background-color: #eeeeee;"}\

<div>

[\[Appium\] Capabilities:]{style="background-color: #eeeeee;"}\
[\[Appium\] app:
\'/Users/ventmahe/code/basic\_appium\_framework/ApiDemos-debug.apk\']{style="background-color: #eeeeee;"}\
[\[Appium\] platformName:
\'Android\']{style="background-color: #eeeeee;"}\
[\[Appium\] deviceName:
\'emulator-5554\']{style="background-color: #eeeeee;"}\
\

-   Rather boring, isn\'t it? Watching the same values we already know
    pass from one service to another to another? But Appium is about to
    spin up a new AndroidDriver\... it read that the platformName is
    \"Android\".

\
[\[AndroidDriver\] AndroidDriver version:
1.17.1]{style="background-color: #eeeeee;"}\
[\[BaseDriver\] Session created with session id:
4bc8afe6-7aa5-4ac8-a42b-55890e777f6d]{style="background-color: #eeeeee;"}\
[\[AndroidDriver\] Getting Java
version]{style="background-color: #eeeeee;"}\
[\[AndroidDriver\] Java version is:
1.8.0\_121]{style="background-color: #eeeeee;"}\
\

-   Here we see that the Android Driver has finally been created! And
    the Appium Base Driver created a new session for it! 

[\
]{style="background-color: #eeeeee;"}[\[ADB\] Checking whether adb is
present]{style="background-color: #eeeeee;"}\
[\[ADB\] Using adb from
/Users/ventmahe/Library/Android/sdk/platform-tools/adb]{style="background-color: #eeeeee;"}\

<div>

\

</div>

-   What\'s ADB? It\'s the \"**Android Debug Bridge**!\", part of the
    command line tools in the Android Software Development Kit. I
    installed it as a package deal with [Android
    Studio](https://developer.android.com/studio/index.html). Yes,
    technically you can download platform tools as a standalone toolset,
    but the Android Developers peoplr throw warning after warning that
    it is not and will not be supported\...

> *\"When you start an adb client, the client first checks whether there
> is an adb server process already running. If there isn\'t, it starts
> the server process. When the server starts, it binds to local TCP port
> 5037 and listens for commands sent from adb clients---all adb clients
> use port 5037 to communicate with the adb server.\
> \
> \"The server then sets up connections to all running devices. It
> locates emulators by scanning odd-numbered ports in the range 5555 to
> 5585, the range used by the first 16 emulators. Where the server finds
> an adb daemon (adbd), it sets up a connection to that port \[\...\]\
> \
> \"Once the server has set up connections to all devices, you can use
> adb commands to access those devices. Because the server manages
> connections to devices and handles commands from multiple adb clients,
> you can control any device from any client (or from a script).\
> \
> \"\[\...\] To use adb with a device connected over USB, you must
> enable USB debugging in the device system settings, under Developer
> options. \[\...\] On Android 4.2 and higher, the Developer options
> screen is hidden by default. To make it visible, go to Settings \>
> About phone and tap Build number seven times. Return to the previous
> screen to find Developer options at the bottom\". - [Android Studio,
> ADB](https://developer.android.com/studio/command-line/adb.html)*

<div>

\

</div>

\
[\[AndroidDriver\] Retrieving device
list]{style="background-color: #eeeeee;"}\
[\[ADB\] Trying to find a connected android
device]{style="background-color: #eeeeee;"}\
[\[ADB\] Getting connected
devices\...]{style="background-color: #eeeeee;"}\
[\[ADB\] 1 device(s) connected]{style="background-color: #eeeeee;"}\
[\[AndroidDriver\] Using device:
emulator-5554]{style="background-color: #eeeeee;"}\
\

-   Oh! Good! It found my Android device, an Android emulator! 
-   It is as if it entered from the command line,  *adb devices*

\
[\[ADB\] Checking whether adb is
present]{style="background-color: #f3f3f3;"}\
[\[ADB\] Using adb from
/Users/ventmahe/Library/Android/sdk/platform-tools/adb]{style="background-color: #f3f3f3;"}\
[\[ADB\] Setting device id to
emulator-5554]{style="background-color: #f3f3f3;"}\
\

-   Now, it is setting the device id it found, using adb. 
-   Hrm. Can it be assumed that if adb was there a split second ago,
    that adb is still present? 

\
[\[BaseDriver\] Using local app
\'/Users/ventmahe/code/basic\_appium\_framework/ApiDemos-debug.apk\']{style="background-color: #eeeeee;"}\
[\[AndroidDriver\] Checking whether app is actually
present]{style="background-color: #eeeeee;"}\
[\[AndroidDriver\] Starting Android
session]{style="background-color: #eeeeee;"}\
\

-   The Appium Base Driver takes from the Desired Capabilities the path
    and name of the Android app, passes it to the Android Driver, which
    checks if the app is truly there.
-   It\'s there? Awesome! Android Driver starts a new Android session!

\
[\[ADB\] Running
\'/Users/ventmahe/Library/Android/sdk/platform-tools/adb\' with args:
\[\"-P\",5037,\"-s\",\"emulator-5554\",\"wait-for-device\"\]]{style="background-color: #eeeeee;"}\
\

-   What are those args? Those arguments? 
-   -P: port. -s: serial\_number.
-   Wait-for-device waits only as long as the arg daemon has properly
    started, then exists. 
-   ADB clients all listen to TCP Port 5037 to communicate with a server
    request.

\
[\[ADB\] Getting connected
devices\...]{style="background-color: #f3f3f3;"}\
[\[ADB\] 1 device(s) connected]{style="background-color: #f3f3f3;"}\
[\[ADB\] Running
\'/Users/ventmahe/Library/Android/sdk/platform-tools/adb\' with args:
\[\"-P\",5037,\"-s\",\"emulator-5554\",\"shell\",\"echo\",\"ping\"\]]{style="background-color: #f3f3f3;"}\
\

-   Is there a device still connected? *Yes?*
-   If so, let\'s start adb running, listening in at Port 5037 for any
    incoming Appium server messages, once again. 
-   \"Shell\" starts a remote interactive shell in the target device.
    From here, you can start various shell
    commands: https://developer.android.com/studio/command-line/adb.html\#shellcommands

\
\
[\[Logcat\] Starting logcat
capture]{style="background-color: #eeeeee;"}\

> *\"Logcat is a command-line tool that dumps a log of system messages,
> including stack traces when the device throws an error and messages
> that you have written from your app with
> the [Log](https://developer.android.com/reference/android/util/Log.html) class
> \[\...\]\
> \"You can run logcat as an adb command or directly in a shell prompt
> of your emulator or connected device. To view log output using adb,
> navigate to your SDK platform-tools/ directory and execute\":*

</div>

<div>

``` {.prettyprint style="background: rgb(247, 247, 247); border: 1px solid rgb(221, 221, 221); color: #006600; font-family: consolas, "liberation mono", menlo, monaco, courier, monospace; font-size: 13px; font-stretch: normal; line-height: 18px; margin-bottom: 1em; overflow: auto; padding: 1em;"}
adb logcat
```

> *\-- [Developer.Android.Studio / Command Line /
> LogCat](https://developer.android.com/studio/command-line/logcat.html)*

\
\
[\[AndroidDriver\] Pushing settings apk to
device\...]{style="background-color: #eeeeee;"}\
\

-   Do we have any special settings to go with the apk? 

\
\
[\[ADB\] Getting install status for
io.appium.settings]{style="background-color: #eeeeee;"}\
\

-   IO.Appium.Settings is \"a small and simple Android application that
    deals with the system settings. Then the application shuts down.
    \[\...\] Toggle settings in Android device or emulator\".
-   Official docs are https://github.com/appium/io.appium.settings

[\
]{style="background-color: #eeeeee;"}[\[ADB\] Getting connected
devices\...]{style="background-color: #eeeeee;"}\
[\[ADB\] 1 device(s) connected]{style="background-color: #eeeeee;"}\
[\[ADB\] Running
\'/Users/ventmahe/Library/Android/sdk/platform-tools/adb\' with args:
\[\"-P\",5037,\"-s\",\"emulator-5554\",\"shell\",\"pm\",\"list\",\"packages\",\"io.appium.settings\"\]]{style="background-color: #eeeeee;"}\
[\[ADB\] App is installed]{style="background-color: #eeeeee;"}\
\

-   Once again, we are getting connected devices. 
-   We are going to run the Android Debug Bridge from where Android
    Studio installed it on my local machine. 
-   What are the arguments? The port is 5037, where Appium has been set
    up to listen in. 
-   The serial number is set to emulator 5554, our emulator we have
    running. 
-   This time, though, as we go into the shell in the emulated device,
    we are going to make a call to the ADB Package Manager (pm) to list
    all packages. We want to see if io.appium.settings are there. 
-   *Need help? Read Android Central and [Ten Basic Android Commands You
    Should
    Know](https://www.androidcentral.com/android-201-10-basic-terminal-commands-you-should-know). *

<div>

From [Developer.Android.Com /
ADB](https://developer.android.com/studio/command-line/adb.html): 

</div>

> \
> \"Within an adb shell, you can issue commands with the package manager
> (pm) tool to perform actions and queries on application packages
> installed on the device. While in a shell, the syntax is:\[\...\]  *pm
> command*\
> \"You can also issue a package manager command directly from adb
> without entering a remote shell. For example:\[\...\] adb shell pm
> uninstall com.example.MyApp

\

> list packages \[options\] filter: Prints all packages, optionally only
> those whose package name contains the text in filter.\
> \
> Options:\
> -f: See their associated file.\
> -d: Filter to only show disabled packages.\
> -e: Filter to only show enabled packages.\
> -s: Filter to only show system packages.\
> -3: Filter to only show third party packages.\
> -i: See the installer for the packages.\
> -u: Also include uninstalled packages.\
> \--user user\_id: The user space to query.\
> \

[\[ADB\] Getting package info for
io.appium.settings]{style="background-color: #eeeeee;"}\
[\[ADB\] Getting connected
devices\...]{style="background-color: #eeeeee;"}\
[\[ADB\] Checking whether aapt is
present]{style="background-color: #eeeeee;"}\
[\[ADB\] Using aapt from
/Users/ventmahe/Library/Android/sdk/build-tools/23.0.1/aapt]{style="background-color: #eeeeee;"}\
[\[ADB\] 1 device(s) connected]{style="background-color: #eeeeee;"}\
\

-   AAPT is the Android Asset Packaging Tool. 

<div>

``` {style="background-color: #f9f9f9; border: 1px solid rgb(221, 221, 221); color: #222222; font-family: monospace, Courier; font-size: 14px; line-height: 1.3em; padding: 1em;"}
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

</div>

-   \"This tool is part of the SDK (and build system) and allows you to
    view, create, and update Zip-compatible archives (zip, jar, apk). It
    can also compile resources into binary assets\".
    - [ELinux.org](http://elinux.org/Android_aapt)
-   After getting the package info, checking it is there in the above
    step, we are going to use this tool to spy inside the package. 

\
[\[ADB\] Running
\'/Users/ventmahe/Library/Android/sdk/platform-tools/adb\' with args:
\[\"-P\",5037,\"-s\",\"emulator-5554\",\"shell\",\"dumpsys\",\"package\",\"io.appium.settings\"\]]{style="background-color: #eeeeee;"}\
[\[ADB\] Cannot read version codes of
/Applications/Appium.app/Contents/Resources/app/node\_modules/appium/node\_modules/io.appium.settings/app/build/outputs/apk/settings\_apk-debug.apk
and/or io.appium.settings. Assuming correct app version is already
installed]{style="background-color: #eeeeee;"}\
\

-   **[*Hrm\... settings\_apk-debug.apk and/or[ io.appium.settings could
    not be found. I don\'t think I set up anything special. Maybe they
    can\'t be found because they are not
    there?]{style="background-color: white;"} *]{style="color: red;"}**
-   Once again, we are using the Android Debug Bridge to go to the
    shell, and use the Android shell commands to investigate what is
    going on inside the emulator that is running. 

\"**Dumpsys System Diagnostics**. \[\...\] The dumpsys tool runs on the
device and provides information about the status of system services.
\[\...\] If you run *adb shell dumpsys*, you'll get diagnostic output
for all system services, which is usually more than you want. For more
manageable output, specify the service you would like to examine. For
example, the following command:\

::: {.devsite-article-body .clearfix itemprop="articleBody" style="box-sizing: inherit; margin: 0px; padding: 0px;"}
``` {style="box-sizing: inherit; font-stretch: normal; line-height: 20px; margin-bottom: 16px; margin-top: 16px; overflow-x: auto; padding: 8px; position: relative;"}



"$ adb shell dumpsys input
```

\"provides system data for input components such as touchscreens or
built-in keyboards\". [- Source.Android.Com /
DumpSys](https://source.android.com/devices/tech/debug/dumpsys)\
\
\
:::

[\[ADB\] Getting connected
devices\...]{style="background-color: #eeeeee;"}\
[\[ADB\] 1 device(s) connected]{style="background-color: #eeeeee;"}\
[\[ADB\] Running
\'/Users/ventmahe/Library/Android/sdk/platform-tools/adb\' with args:
\[\"-P\",5037,\"-s\",\"emulator-5554\",\"shell\",\"getprop\",\"ro.build.version.sdk\"\]]{style="background-color: #eeeeee;"}\
[\[ADB\] Device API level: 25]{style="background-color: #eeeeee;"}\
\

-   First step\... make sure a connected device is running. 
-   Next step? Let\'s shell into the running emulator, entering it by
    port 5037, the Appium server, choosing emulator-5554.
-   This time, we are using the adb shell command \"getprop\" to
    investigate \"ro.build.version.sdk\". 

\
\... Each Android device and emulator has a list of \"build
properties\".\
\
\"Android has a single text file named \'build.prop\' that determines
lots of various system-wide settings on your device. You need root
access to edit this file, since it's stored on the system
partition---but the various lines of codes it contains are actually easy
to interpret and modify\".\
\
\... Here, we are grabbing the root property \"build version sdk\",
meaning, what version of operating system?\
\
\... It\'s API 25.\
\
[\[ADB\] Getting connected
devices\...]{style="background-color: #eeeeee;"}\
[\[ADB\] 1 device(s) connected]{style="background-color: #eeeeee;"}\
[\[ADB\] Running
\'/Users/ventmahe/Library/Android/sdk/platform-tools/adb\' with args:
\[\"-P\",5037,\"-s\",\"emulator-5554\",\"shell\",\"dumpsys\",\"package\",\"io.appium.settings\"\]]{style="background-color: #eeeeee;"}\
[\[ADB\] Getting connected
devices\...]{style="background-color: #eeeeee;"}\
[\[ADB\] 1 device(s) connected]{style="background-color: #eeeeee;"}\
[\[ADB\] Running
\'/Users/ventmahe/Library/Android/sdk/platform-tools/adb\' with args:
\[\"-P\",5037,\"-s\",\"emulator-5554\",\"shell\",\"pm\",\"dump\",\"io.appium.settings\"\]]{style="background-color: #eeeeee;"}\
\

-   Still have an emulator? If so, let\'s do another adb shell script
    \"dumpsys\", looking for the particular package
    \"io.appium.settings\". 
-   Still have a emulator? If so let\'s use the adb shell script command
    package manger to do a \"dumpsys\" to take a look at the input
    output settings for Appium and throw it onto the screen. 

<div>

io.appium.settings is a \"A small and simple Android application that
deals with the system settings. Then the application shuts down.\"
according to https://github.com/appium/io.appium.settings\
[\
]{style="background-color: #eeeeee;"}

</div>

\
[\[ADB\] Getting connected
devices\...]{style="background-color: #eeeeee;"}\
[\[ADB\] 1 device(s) connected]{style="background-color: #eeeeee;"}\
[\[ADB\] Running
\'/Users/ventmahe/Library/Android/sdk/platform-tools/adb\' with args:
\[\"-P\",5037,\"-s\",\"emulator-5554\",\"shell\",\"pm\",\"grant\",\"io.appium.settings\",\"android.permission.WRITE\_SETTINGS\",\";\",\"pm\",\"grant\",\"io.appium.settings\",\"android.permission.ACCESS\_MOCK\_LOCATION\",\";\"\]]{style="background-color: #eeeeee;"}\
\

-   Is the Android device connected? Here is where it gets good! 
-   This time, we are going to go to the device and use the shell script
    package manager to do something quite different\... we are going to
    get READ AND WRITE PERMISSIONS! Are you excited? I\'m excited! The
    Appium Server is now going to grant us permission to read and write
    files on the device. 

<div>

See all
the [WRITE\_SETTINGS](https://developer.android.com/reference/android/Manifest.permission.html#WRITE_SETTINGS):
Appium could have made our phone vibrate, answer a call, leave a
voicemail, whatever. 

</div>

<div>

\

</div>

<div>

Instead we are going to grant to io.appium.settings to
ACCESS\_MOCK\_LOCATION:

</div>

-   \"Create mock location sources for testing or install a new location
    provider. This allows the app to override the location and/or status
    returned by other location sources such as GPS or location
    providers\".* - [Android
    Permissions](http://androidpermissions.com/permission/android.permission.ACCESS_MOCK_LOCATION)*

<div>

\... I know it has been a while\... but I want to mention that the only
way the Android Debug Bridge (\"adb\") has this power over our emulator
or physical Android device because we gave it to *adb*.

</div>

<div>

\

</div>

<div>

::: {style="background-color: white; color: rgba(0, 0, 0, 0.68); font-family: Roboto, sans-serif; font-size: 14px; margin-bottom: 12px;"}
\"To use adb with a device connected over USB, you must enable **USB
debugging** in the device system settings, under **Developer options**.
:::

::: {style="background-color: white; color: rgba(0, 0, 0, 0.68); font-family: Roboto, sans-serif; font-size: 14px; margin-bottom: 12px;"}
\"On Android 4.2 and higher, the Developer options screen is hidden by
default. To make it visible, go to **Settings \> About phone** and
tap **Build number**seven times. Return to the previous  screen to
find **Developer options** at the bottom.
:::

::: {style="background-color: white; color: rgba(0, 0, 0, 0.68); font-family: Roboto, sans-serif; font-size: 14px; margin-bottom: 12px;"}
\"On some devices, the Developer options screen might be located or
named differently.
:::

::: {style="background-color: white; color: rgba(0, 0, 0, 0.68); font-family: Roboto, sans-serif; font-size: 14px; margin-bottom: 12px;"}
\"You can now connect your device with USB. You can verify that your
device is connected by
executing `adb devices`{style="-webkit-font-smoothing: subpixel-antialiased; color: #006600; font-family: Consolas, "Liberation Mono", Menlo, Monaco, Courier, monospace; font-size: 13px; font-stretch: normal; line-height: 18px;"} from
the`android_sdk/platform-tools/`{style="-webkit-font-smoothing: subpixel-antialiased; color: #006600; font-family: Consolas, "Liberation Mono", Menlo, Monaco, Courier, monospace; font-size: 13px; font-stretch: normal; line-height: 18px;"} directory.
If connected, you\'ll see the device name listed as a \'device.\'\"
- [Developer.Android.Com /
ADB](https://developer.android.com/studio/command-line/adb.html)
:::

</div>

<div>

\

</div>

\
\
[\[ADB\] Running
\'/Users/ventmahe/Library/Android/sdk/platform-tools/adb\' with args:
\[\"-P\",5037,\"-s\",\"emulator-5554\",\"shell\",\"pm\",\"grant\",\"io.appium.settings\",\"android.permission.WRITE\_SETTINGS\",\";\",\"pm\",\"grant\",\"io.appium.settings\",\"android.permission.ACCESS\_MOCK\_LOCATION\",\";\"\]]{style="background-color: #eeeeee;"}\
\

-   **[*And we are going to do the exact same thing we did before\...
    huh? *]{style="color: red;"}**

\
\
[\[AndroidDriver\] Pushing unlock helper app to
device\...]{style="background-color: #eeeeee;"}\
\

-   Appium has a helper app to unlock and \"wake up\" a device.
    See [https://github.com/appium/unlock\_apk ](https://github.com/appium/unlock_apk)
-   Since Appium now has been given read and write permissions, it can
    install the unlock helper app to your device, no problem. 

\
\
[\[ADB\] Running
\'/Users/ventmahe/Library/Android/sdk/platform-tools/adb\' with args:
\[\"-P\",5037,\"-s\",\"emulator-5554\",\"install\",\"/Applications/Appium.app/Contents/Resources/app/node\_modules/appium/node\_modules/appium-unlock/bin/unlock\_apk-debug.apk\"\]]{style="background-color: #eeeeee;"}\
\

-   There it goes! After being pushed onto your device, the helper app,
    unlock\_apk-debug.apk, is now being installed.

\
\
[\[ADB\] Running
\'/Users/ventmahe/Library/Android/sdk/platform-tools/adb\' with args:
\[\"-P\",5037,\"-s\",\"emulator-5554\",\"install\",\"/Applications/Appium.app/Contents/Resources/app/node\_modules/appium/node\_modules/appium-unlock/bin/unlock\_apk-debug.apk\"\]]{style="background-color: #eeeeee;"}\
\

-   ***[Um, and there it goes again, attempting to install
    appium-unlock? But it was just done!]{style="color: red;"}***

\
[\[ADB\] Application
\'/Applications/Appium.app/Contents/Resources/app/node\_modules/appium/node\_modules/appium-unlock/bin/unlock\_apk-debug.apk\'
already installed. Continuing.]{style="background-color: #eeeeee;"}\
\

-   Yes, we know it was already installed. Next! 

\
[\[ADB\] Device API level: 25]{style="background-color: #eeeeee;"}\
[\[ADB\] Getting connected
devices\...]{style="background-color: #eeeeee;"}\
[\[ADB\] 1 device(s) connected]{style="background-color: #eeeeee;"}\
[\[ADB\] Running
\'/Users/ventmahe/Library/Android/sdk/platform-tools/adb\' with args:
\[\"-P\",5037,\"-s\",\"emulator-5554\",\"shell\",\"appops\",\"set\",\"io.appium.settings\",\"android:mock\_location\",\"allow\"\]]{style="background-color: #eeeeee;"}\
\

-   Before, we had to get permissions to use MOCK\_LOCATION? Now, we are
    setting it, with an Android adb shell script program called
    \"appops\". 
-   We had \"pm\", the package manager allows you to install and
    uninstall software \"packages\" (such as out Android apps).
-   Now, we have \"appops\" the App Operations manager that allows us to
    set the Android property \"io.appium,.settings\" mock location to
    \"allow\".  

*\"Create mock location sources for testing or install a new location
provider. This allows the app to override the location and/or status
returned by other location sources such as GPS or location
providers\". - [Android
Permissions](http://androidpermissions.com/permission/android.permission.ACCESS_MOCK_LOCATION)*\
\

<div>

\

</div>

\

<div>

</div>

[\[ADB\] Getting device platform
version]{style="background-color: #eeeeee;"}\
[\[ADB\] Getting connected
devices\...]{style="background-color: #eeeeee;"}\
[\[ADB\] 1 device(s) connected]{style="background-color: #eeeeee;"}\
[\[ADB\] Running
\'/Users/ventmahe/Library/Android/sdk/platform-tools/adb\' with args:
\[\"-P\",5037,\"-s\",\"emulator-5554\",\"shell\",\"getprop\",\"ro.build.version.release\"\]]{style="background-color: #eeeeee;"}\
\

-   What is the device platform version? First, let\'s check if we can
    get the connected device. It\'s all good?
-   Let\'s use the adb command, part of the Android Command Line tools,
    installed on our local computer as a packaged deal when I installed
    \"Android Studio\", the only way the Android Developers wanted it. 
-   We are going to communicate through port 5037 with our emulator,
    attached at \"emulator-5554\" and shell into the emulator.
-   The shell command Appium is using this time? Getprop. We are getting
    the Android emulator\'s root property build version release.

\
\
[\[ADB\] Getting connected
devices\...]{style="background-color: #eeeeee;"}\
[\[ADB\] 1 device(s) connected]{style="background-color: #eeeeee;"}\
[\[ADB\] Running
\'/Users/ventmahe/Library/Android/sdk/platform-tools/adb\' with args:
\[\"-P\",5037,\"-s\",\"emulator-5554\",\"shell\",\"wm\",\"size\"\]]{style="background-color: #eeeeee;"}\
\

-   Same thing as above! We are using the shell program \"wm\" to get
    the size. \"wm\" is the windows manager. (Want to read more? See the
    section on
    \"[Display](https://developer.android.com/reference/android/view/Display.html)\"
    in Developer.Android.Com

\
\
[\[ADB\] Getting connected
devices\...]{style="background-color: #eeeeee;"}\
[\[ADB\] 1 device(s) connected]{style="background-color: #eeeeee;"}\
[\[ADB\] Running
\'/Users/ventmahe/Library/Android/sdk/platform-tools/adb\' with args:
\[\"-P\",5037,\"-s\",\"emulator-5554\",\"shell\",\"getprop\",\"ro.product.model\"\]]{style="background-color: #eeeeee;"}\
[\[ADB\] Current device property \'ro.product.model\': Android SDK built
for x86]{style="background-color: #eeeeee;"}\
\

-   And now, Appium is checking through ADB the root product model. 
-   It finds the Android Software Development Kit was built for the x86
    architecture, that is Intel\'s x86 (as apposed to the AMD chipset)

\
[\
]{style="background-color: #eeeeee;"}[\[ADB\] Getting connected
devices\...]{style="background-color: #eeeeee;"}\
[\[ADB\] 1 device(s) connected]{style="background-color: #eeeeee;"}\
[\[ADB\] Running
\'/Users/ventmahe/Library/Android/sdk/platform-tools/adb\' with args:
\[\"-P\",5037,\"-s\",\"emulator-5554\",\"shell\",\"getprop\",\"ro.product.manufacturer\"\]]{style="background-color: #eeeeee;"}\
[\[ADB\] Current device property \'ro.product.manufacturer\':
unknown]{style="background-color: #eeeeee;"}\
\

-   Who manufactured the device that is running? It is listed as unknown
    because it is an emulator. 

\
[\[AndroidDriver\] Parsing package and activity from app
manifest]{style="background-color: #eeeeee;"}\
\

-   **What is a package?** \"A package is a namespace that organizes a
    set of related classes and interfaces. Conceptually you can think of
    packages as being similar to different folders on your computer. You
    might keep HTML pages in one folder, images in another, and scripts
    or applications in yet another. Because software written in the Java
    programming language can be composed of hundreds or thousands of
    individual classes, it makes sense to keep things organized by
    placing related classes and interfaces into packages\". - [Java
    Tutorials, What is a
    Package?](https://docs.oracle.com/javase/tutorial/java/concepts/package.html)
-   **What is an activity? **\"An activity is a single, focused thing
    that the user can do. Almost all activities interact with the user,
    so the Activity class takes care of creating a window for you in
    which you can place your UI
    with [setContentView(View)](https://developer.android.com/reference/android/app/Activity.html#setContentView(android.view.View)).
    While activities are often presented to the user as full-screen
    windows, they can also be used in other ways: as floating windows
    (via a theme
    with [windowIsFloating](https://developer.android.com/reference/android/R.attr.html#windowIsFloating) set)
    or embedded inside of another activity
    (using [ActivityGroup](https://developer.android.com/reference/android/app/ActivityGroup.html)).\" *- [Developer.Android.Com
    /
    Activity](https://developer.android.com/reference/android/app/Activity.html) *
-   **What is the app manifest?**

\
According to [Developer.Android.Com /
Manifest-Intro:](https://developer.android.com/guide/topics/manifest/manifest-intro.html)\
\

> \"Every application must have an AndroidManifest.xml file (with
> precisely that name) in its root directory. The manifest file provides
> essential information about your app to the Android system, which the
> system must have before it can run any of the app\'s code.\
>
> -   \"Among other things, the manifest file does the following:
>
> <!-- -->
>
> -   \"It names the Java package for the application. The package name
>     serves as a unique identifier for the application.
>
> <!-- -->
>
> -   \"It describes the components of the application, which include
>     the activities, services, broadcast receivers, and content
>     providers that compose the application. It also names the classes
>     that implement each of the components and publishes their
>     capabilities, such as
>     the [Intent](https://developer.android.com/reference/android/content/Intent.html) messages
>     that they can handle. These declarations inform the Android system
>     of the components and the conditions in which they can be
>     launched.
>
> <!-- -->
>
> -   \"It determines the processes that host the application
>     components.
>
> <!-- -->
>
> -   \"It declares the permissions that the application must have in
>     order to access protected parts of the API and interact with other
>     applications. It also declares the permissions that others are
>     required to have in order to interact with the application\'s
>     components.
>
> <!-- -->
>
> -   \"It lists
>     the [Instrumentation](https://developer.android.com/reference/android/app/Instrumentation.html) classes
>     that provide profiling and other information as the application
>     runs. These declarations are present in the manifest only while
>     the application is being developed and are removed before the
>     application is published.
>
> <!-- -->
>
> -   \"It declares the minimum level of the Android API that the
>     application requires.
>
> <!-- -->
>
> -   \"It lists the libraries that the application must be linked
>     against\".

\
[\[ADB\] Checking whether aapt is
present]{style="background-color: #eeeeee;"}\
\

-   Is the Android Asset Packaging Tool there? This aapt tool will help
    you view, create, and update your APKs.

\
[\[ADB\] Using aapt from
/Users/ventmahe/Library/Android/sdk/build-tools/23.0.1/aapt]{style="background-color: #eeeeee;"}\
[\[ADB\] Extracting package and launch activity from
manifest]{style="background-color: #eeeeee;"}\
\

-   Now we are going to examine the manifest for the package and launch
    activity.

\
[\[ADB\] badging package:
io.appium.android.apis]{style="background-color: #eeeeee;"}\
[\[ADB\] badging act:
io.appium.android.apis.ApiDemos]{style="background-color: #eeeeee;"}\
\

-   In order to launch a package, we are going to need to know two
    things: The name of app package, and the app activity, just as when
    we were attempting to [launch and app via Appium
    Desktop](http://www.tjmaher.com/2017/04/learning-appium-desktop-find-desired.html).

\
[\[AndroidDriver\] Parsed package and activity are:
io.appium.android.apis/io.appium.android.apis.ApiDemos]{style="background-color: #eeeeee;"}\
[\
]{style="background-color: white;"}[Found
it!]{style="background-color: white;"}\
\

-   App package: io.appium.android.apis
-   App Activity: io.appium.android.apis.ApiDemos

\
[\[AndroidDriver\] Remote apk path is
/data/local/tmp/29649242b53e9a67ba855b067422713c.apk]{style="background-color: #eeeeee;"}\
\

-   Appium is going to take where APIDemos-debug.apk is located in our
    local computer, and upload it to our Android device (our emulator in
    this case) somewhere in a temporary directory. 
-   ADB has an \"install\" command which installs an apk onto a device. 

\
[\[ADB\] Getting connected
devices\...]{style="background-color: #eeeeee;"}\
[\[ADB\] 1 device(s) connected]{style="background-color: #eeeeee;"}\
[\[ADB\] Running
\'/Users/ventmahe/Library/Android/sdk/platform-tools/adb\' with args:
\[\"-P\",5037,\"-s\",\"emulator-5554\",\"shell\",\"ls\",\"/data/local/tmp/29649242b53e9a67ba855b067422713c.apk\"\]]{style="background-color: #eeeeee;"}\
\

-   Adb now going to check that it is there, accessing the emulator
    through port 5037, on device emulator-5554, using the Unix shell
    command \"ls\", listing the directory, and checking that the apk is
    there.  

\
[\[AndroidDriver\] Checking if app is
installed]{style="background-color: #eeeeee;"}\
[\[ADB\] Getting install status for
io.appium.android.apis]{style="background-color: #eeeeee;"}\
[\[ADB\] Getting connected
devices\...]{style="background-color: #eeeeee;"}\
[\[ADB\] 1 device(s) connected]{style="background-color: #eeeeee;"}\
[\[ADB\] Running
\'/Users/ventmahe/Library/Android/sdk/platform-tools/adb\' with args:
\[\"-P\",5037,\"-s\",\"emulator-5554\",\"shell\",\"pm\",\"list\",\"packages\",\"io.appium.android.apis\"\]]{style="background-color: #eeeeee;"}\
[\[ADB\] App is installed]{style="background-color: #eeeeee;"}\
\

-   As a belt-and-suspenders approach, Appium is checking if the app is
    truly installed by shelling into the emulator-5554 using the package
    manager to list all packages to make sure that
    io.appium.android.apis is listed on the device. And it is! 

\[[AndroidDriver\] Apk is already on remote and installed, resetting\
\[AndroidDriver\] Running fast reset (stop and clear)\
\[ADB\] Getting connected devices\...\
\[ADB\] 1 device(s) connected\
\[ADB\] Running
\'/Users/ventmahe/Library/Android/sdk/platform-tools/adb\' with args:
\[\"-P\",5037,\"-s\",\"emulator-5554\",\"shell\",\"am\",\"force-stop\",\"io.appium.android.apis\"\]]{style="background-color: #eeeeee;"}\
\

-   ***[Something must be wrong with the Appium code. It looks like the
    app is installed and running twice? ]{style="color: red;"}***
-   For the second instance we are doing a \"force-stop\", stopping the
    app from running. 

\
[\
]{style="background-color: #eeeeee;"}[\[ADB\] Getting connected
devices\...]{style="background-color: #eeeeee;"}\
[\[ADB\] 1 device(s) connected]{style="background-color: #eeeeee;"}\
[\[ADB\] Running
\'/Users/ventmahe/Library/Android/sdk/platform-tools/adb\' with args:
\[\"-P\",5037,\"-s\",\"emulator-5554\",\"shell\",\"pm\",\"clear\",\"io.appium.android.apis\"\]]{style="background-color: #eeeeee;"}\
\

-   Now, we are going to clear the app\'s cache using the Package
    Manager. The app data has been stored in the cache for easy
    retrieval, and must be erased.

\
[\[AndroidDriver\] Extracting strings from apk
/Users/ventmahe/code/basic\_appium\_framework/ApiDemos-debug.apk
undefined
/var/folders/0h/hf79m7zj1xz1hdk0m3t091v8221rx6/T/io.appium.android.apis]{style="background-color: #eeeeee;"}\
\

-   Now, we are extracting strings in the manifest xml. ***[Not sure
    what this means]{style="color: red;"}***. 

\
\
[\[ADB\] Extracting strings for language:
default]{style="background-color: #eeeeee;"}\
[\[ADB\] Device API level: 25]{style="background-color: #eeeeee;"}\
[\[ADB\] Getting connected
devices\...]{style="background-color: #eeeeee;"}\
[\[ADB\] 1 device(s) connected]{style="background-color: #eeeeee;"}\
[\[ADB\] Running
\'/Users/ventmahe/Library/Android/sdk/platform-tools/adb\' with args:
\[\"-P\",5037,\"-s\",\"emulator-5554\",\"shell\",\"getprop\",\"persist.sys.locale\"\]]{style="background-color: #eeeeee;"}\
[\[ADB\] Current device property
\'persist.sys.locale\':]{style="background-color: #eeeeee;"}\
\

-   As we start extracting the contents of the manifest.xml file, we
    found that the language has been set to be \"default\" and the
    operating system is API level 25.

What is locale? How can you set it through the command line?\
\
From [ProfWeb / Setting the
Locale:](http://wiki.pcampbell.profweb.ca/index.php/Set_the_locale_in_Android)\

> \"The locale (language and country) may be set using the Settings
> button in the Launcher, choose Language & Input it will immediately
> change the interface language \[\...\]\
> \"Note: You can only do this if you are either using an AVD or you
> have rooted your device \[\...\]\
> Modification can only be done if you have root access so on an AVD or
> a rooted device. To see the current information:\
>
> -   \"getprop persist.sys.language
> -   \"getprop persist.sys.country\"

\
\
[\[ADB\] Getting connected
devices\...]{style="background-color: #eeeeee;"}\
[\[ADB\] 1 device(s) connected]{style="background-color: #eeeeee;"}\
[\[ADB\] Running
\'/Users/ventmahe/Library/Android/sdk/platform-tools/adb\' with args:
\[\"-P\",5037,\"-s\",\"emulator-5554\",\"shell\",\"getprop\",\"ro.product.locale\"\]]{style="background-color: #eeeeee;"}\
[\[ADB\] Current device property \'ro.product.locale\':
en-US]{style="background-color: #eeeeee;"}\
\

-   Now, we are using adb for grabbing from root the value of the root
    property, product locale. It is listed as \"en-US\".
-   \"en-US\" is the language code for \"English - United States\" given
    by the [Internet Engineering
    Task Force ](https://www.ietf.org/about/)(IETF) language tag.

<div>

Note that we can have:

</div>

-   en-GB: British English
-   en-US: American English
-   en-CA: Canadian English
-   en-IN: Indian English

\... Each has its own pronunciations, spellings.

</div>

<div>

*\
*

</div>

<div>

*Want to drown in information? Read [BP47: Tags for Identifying
Languages](https://tools.ietf.org/html/bcp47), on IETF.org.*\
\
\
[\[ADB\] No strings.xml for language \'en\', getting default
strings.xml]{style="background-color: #eeeeee;"}\
\

-   **[*Why would there be no strings.xml? What does this
    mean? *]{style="color: red;"}**

\
[\[ADB\] Reading strings from converted
strings.json]{style="background-color: #eeeeee;"}\
\

-   **[*Eh?*]{style="color: red;"}**

\
\
[\[ADB\] Running
\'/Users/ventmahe/Library/Android/sdk/platform-tools/adb\' with args:
\[\"-P\",5037,\"-s\",\"emulator-5554\",\"push\",\"/var/folders/0h/hf79m7zj1xz1hdk0m3t091v8221rx6/T/io.appium.android.apis/strings.json\",\"/data/local/tmp\"\]]{style="background-color: #eeeeee;"}\
\

-   The app activity is at
    /var/folders/0h/hf79m7zj1xz1hdk0m3t091v8221rx6/T/io.appium.android.apis
-   We are going to push this into a temporary file /data/local/tmp. 

\
\"Use the pull and push commands to copy files to and from an device.
Unlike the install command, which only copies an APK file to a specific
location, the pull and push commands let you copy arbitrary directories
and files to any location in a device\". - [Developer.Android.Com /
ADB](https://developer.android.com/studio/command-line/adb.html)

</div>

<div>

-   ***[Why does Appium do it this way, with a \"push\" of the
    directories, instead of an \"adb install
    TheApk.apk\"?]{style="color: red;"}***

\
[\[AndroidBootstrap\] Watching for bootstrap
disconnect]{style="background-color: #eeeeee;"}\
\
Next, we are going to talk about AppiumBootstrap.\

<div>

-   If you want to create a really quick Android app, you can
    use **AndroidBootstrap** at <http://www.androidbootstrap.com/>,
    whose sourcecode is at <https://github.com/AndroidBootstrap>

</div>

\

-   Android Bootstrap uses Appium-ADB
    \< <https://github.com/appium/appium-adb> \> which defaults to
    port 4724. It allows us to perform all adb operations on android
    device and then some.

\
\
[\[ADB\] Forwarding system: 4724 to device:
4724]{style="background-color: #eeeeee;"}\
[\[ADB\] Running
\'/Users/ventmahe/Library/Android/sdk/platform-tools/adb\' with args:
\[\"-P\",5037,\"-s\",\"emulator-5554\",\"forward\",\"tcp:4724\",\"tcp:4724\"\]]{style="background-color: #eeeeee;"}\
\

-   Here, we are setting up port forwarding, for appium to listen to
    what is happening on the emulator.
-   Readying Android Bootstrap! 
-   Appium-Android-Bootstrap according to [Appium\'s GitHub
    documentation](https://github.com/appium/appium-android-bootstrap),
    is a \"JavaScript interface, and Java code, for interacting with
    Android UI Automator. The system allows ad hoc commands to be sent
    to the device, which are executed using
    Android\'s [UIAutomator](http://developer.android.com/tools/testing-support-library/index.html#UIAutomator) testing
    framework\".

[\[UiAutomator\] Starting
UiAutomator]{style="background-color: #eeeeee;"}\
\
From [Developer.Android.Com / Testing-Libraries / UI
Automator](https://developer.android.com/topic/libraries/testing-support-library/index.html#UIAutomator):\
\

> \"The UI Automator testing framework provides a set of APIs to build
> UI tests that perform interactions on user apps and system apps. The
> UI Automator APIs allows you to perform operations such as opening the
> Settings menu or the app launcher in a test device. The UI Automator
> testing framework is well-suited for writing black box-style automated
> tests, where the test code does not rely on internal implementation
> details of the target app.\
> \"The key features of the UI Automator testing framework include:\
>
> -   A viewer to inspect layout hierarchy. For more information,
>     see [UI Automator
>     Viewer](https://developer.android.com/topic/libraries/testing-support-library/index.html#uia-viewer).
>
> <!-- -->
>
> -   An API to retrieve state information and perform operations on the
>     target device. For more information, see [Access to device
>     state](https://developer.android.com/topic/libraries/testing-support-library/index.html#uia-device-state).
>
> <!-- -->
>
> -   APIs that support cross-app UI testing. For more information,
>     see [UI Automator
>     APIs](https://developer.android.com/topic/libraries/testing-support-library/index.html#uia-apis) .
>
> <!-- -->
>
> -   Requires Android 4.3 (API level 18) or higher.

\
[\[UiAutomator\] Moving to state
\'starting\']{style="background-color: #eeeeee;"}\
[\[UiAutomator\] Parsing uiautomator
jar]{style="background-color: #eeeeee;"}\
[\[UiAutomator\] Found jar name:
\'AppiumBootstrap.jar\']{style="background-color: #eeeeee;"}\
\

-   UIAutomator signals that it is starting on your local machine. 
-   It is searching through the UIAutomator java archive file (like a
    zip file, but for Java).
-   It is looking for AppiumBootstrap\'s jar file. 

\
[\[ADB\] Running
\'/Users/ventmahe/Library/Android/sdk/platform-tools/adb\' with args:
\[\"-P\",5037,\"-s\",\"emulator-5554\",\"push\",\"/Applications/Appium.app/Contents/Resources/app/node\_modules/appium/node\_modules/appium-android-bootstrap/bootstrap/bin/AppiumBootstrap.jar\",\"/data/local/tmp/\"\]]{style="background-color: #eeeeee;"}\
\

-   We are now pushing the directory structure and files for Appium
    Bootstrap onto the emulator, using ADB into the /data/local/tmp
    temporary file on the emulator. The UIAutomator will now run, one
    instance on the emulator or actual device, and one on the computer
    where Appium Server is running.

\
[\
]{style="background-color: #eeeeee;"}[\[ADB\] Attempting to kill all
uiautomator processes]{style="background-color: #eeeeee;"}\
\
[\[ADB\] Getting all processes with
uiautomator]{style="background-color: #eeeeee;"}\
[\[ADB\] Getting connected
devices\...]{style="background-color: #eeeeee;"}\
[\[ADB\] 1 device(s) connected]{style="background-color: #eeeeee;"}\
[\[ADB\] Running
\'/Users/ventmahe/Library/Android/sdk/platform-tools/adb\' with args:
\[\"-P\",5037,\"-s\",\"emulator-5554\",\"shell\",\"ps\"\]]{style="background-color: #eeeeee;"}\
[\[ADB\] No uiautomator process found to kill,
continuing\...]{style="background-color: #eeeeee;"}\

-   ADB is making sure no other uiautomator processes are running on the
    emulator or actual device it just pushed the UIAutomator to. If
    there are leftovers from previous attempts run, we don\'t want them
    interfering. 

From [Developer.Android.Com / Testing-Libraries / UI
Automator](https://developer.android.com/topic/libraries/testing-support-library/index.html#UIAutomator):
\"The UI Automator testing framework provides
a [UiDevice](https://developer.android.com/reference/android/support/test/uiautomator/UiDevice.html) class
to access and perform operations on the device on which the target app
is running. You can call its methods to access device properties such as
current orientation or display size.
The [UiDevice](https://developer.android.com/reference/android/support/test/uiautomator/UiDevice.html) class
also let you perform actions such as:\

-   \"Change the device rotation
-   \"Press a D-pad button
-   \"Press the Back, Home, or Menu buttons
-   \"Open the notification shade
-   \"Take a screenshot of the current window\"

\
[\[UiAutomator\] Starting UIAutomator\
\[ADB\] Creating ADB subprocess with args:
\[\"-P\",5037,\"-s\",\"emulator-5554\",\"shell\",\"uiautomator\",\"runtest\",\"AppiumBootstrap.jar\",\"-c\",\"io.appium.android.bootstrap.Bootstrap\",\"-e\",\"pkg\",\"io.appium.android.apis\",\"-e\",\"disableAndroidWatchers\",false,\"-e\",\"acceptSslCerts\",false\]]{style="background-color: #eeeeee;"}\
\

-   Did it work? Did pushing UIAutomator and Appium Boostrap work? Can
    we now, finally, have the Appium Server controlling what is on the
    actual Android device or (in this case) emulator?
-   We are going to connect to the emulator once again, using adb shell,
    but this time we are connecting with \"uiautomator\", running the
    uiautomator command, \"runtest\".

<div>

\

</div>

\
From [Stuff.MIT.edu /
UIAUTOMATOR](https://stuff.mit.edu/afs/sipb/project/android/docs/tools/help/uiautomator/index.html):
\"To run your testcases on the target device, you can use the adb shell
command to invoke the uiautomator tool. The syntax is:\

<div>

``` {.prettyprint style="background: rgb(247, 247, 247); border: 1px solid rgb(221, 221, 221); color: #006600; font-family: "courier new", courier, monospace; font-size: 14px; font-stretch: normal; line-height: 1.5; margin-bottom: 1em; overflow: auto; padding: 1em;"}
adb shell uiautomator runtest <jar> -c <test_class_or_method> [options]
```

::: {style="background-color: #f9f9f9; color: #222222; font-family: Roboto, sans-serif; font-size: 14px; margin-bottom: 15px;"}
:::

\"Here's an example:\

``` {.prettyprint style="background: rgb(247, 247, 247); border: 1px solid rgb(221, 221, 221); color: #006600; font-family: "courier new", courier, monospace; font-size: 14px; font-stretch: normal; line-height: 1.5; margin-bottom: 1em; overflow: auto; padding: 1em;"}
adb shell uiautomator runtest LaunchSettings.jar -c com.uia.example.my.LaunchSettings
```

\
\
\
\
\
\"Command-line Options:\
\"The following table describes the subcommands and options for
uiautomator.\
\
\
\"Table 1. Command-line options for uiautomator

</div>

<div>

\"*runtest \<jar\>*\
\
\"Required. The \<jar\> argument is the name of one or more JAR files
that you deployed to the target device which contain your uiautomator
testcases. You can list more than one JAR file by using a space as a
separator.\
\
\"-c \<test\_class\_or\_method\>: Required. The
\<test\_class\_or\_method\>argument is a list of one or more specific
test classes or test methods from the JARs that you want uiautomator to
run.\
\
\"Each class or method must be fully qualified with the package name, in
one of these formats:\

-   package\_name.class\_name 
-   package\_name.class\_name\#method\_name 

\
\"You can list multiple classes or methods by using a space as a
separator.\
\
\"\--nohup: Runs the test to completion on the device even if its parent
process is terminated (for example, if the device is disconnected).\
\
\
\"-e \<NAME\> \<VALUE\>: Specify other name-value pairs to be passed to
test classes. May be repeated. Note: The -e options cannot be combined;
you must prefix each option with a separate -e flag\".\
\

</div>

\... UIAutomator is passing along via AndroidBootstrap
that[ disableAndroidWatchers\",false,\"-e\",\"acceptSslCerts\",false.]{style="background-color: white;"}\
\
\
[\[UiAutomator\] Moving to state
\'online\']{style="background-color: #eeeeee;"}\
[\[AndroidBootstrap\] Android bootstrap socket is now
connected]{style="background-color: #eeeeee;"}\
\

-   AndroidBootstrap lives! 
-   The appium-android-bootstrap module provides \"an AndroidBootstrap
    class, which is instantiated with an instance
    of [appium-adb](https://github.com/appium/appium-adb), a system port
    (defaults to 4724) and an optional web socket\".* - [GitHub of
    appium-android-bootstrap](https://github.com/appium/appium-android-bootstrap)*.
-   The \"socket\" is of the Java class \"ServerSocket\". *( [See Java
    Documentation](http://docs.oracle.com/javase/7/docs/api/java/net/ServerSocket.html) )*
-   *\"A socket is one endpoint of a two-way communication link between
    two programs running on the network. A socket is bound to a port
    number so that the TCP layer can identify the application that data
    is destined to be sent to\"*. - [Java Tutorials / What is a
    Socket?](https://docs.oracle.com/javase/tutorial/networking/sockets/definition.html)

\
[\[ADB\] Getting connected
devices\...]{style="background-color: #eeeeee;"}\
[\[AndroidBootstrap\] \[BOOTSTRAP LOG\] \[debug\] json loading
complete.]{style="background-color: #eeeeee;"}\
[\[AndroidBootstrap\] \[BOOTSTRAP LOG\] \[debug\] Registered crash
watchers.]{style="background-color: #eeeeee;"}\
[\[AndroidBootstrap\] \[BOOTSTRAP LOG\] \[debug\] Client
connected]{style="background-color: #eeeeee;"}\
\

-   Just in case of problems, Bootstrap in debug mode, explaining things
    in detail. 

[\[ADB\] 1 device(s) connected]{style="background-color: #eeeeee;"}\
[\[ADB\] Running
\'/Users/ventmahe/Library/Android/sdk/platform-tools/adb\' with args:
\[\"-P\",5037,\"-s\",\"emulator-5554\",\"shell\",\"dumpsys\",\"window\"\]]{style="background-color: #eeeeee;"}\
[\[AndroidDriver\] Screen already unlocked, doing
nothing]{style="background-color: #eeeeee;"}\
\

-   If the screen were locked, we could have the screen unlocked it
    here. 

\
\
[\[ADB\] Device API level: 25]{style="background-color: #eeeeee;"}\
[\[ADB\] Getting connected
devices\...]{style="background-color: #eeeeee;"}\
[\[ADB\] 1 device(s) connected]{style="background-color: #eeeeee;"}\
[\[ADB\] Running
\'/Users/ventmahe/Library/Android/sdk/platform-tools/adb\' with args:
\[\"-P\",5037,\"-s\",\"emulator-5554\",\"shell\",\"am\",\"start\",\"-W\",\"-n\",\"io.appium.android.apis/io.appium.android.apis.ApiDemos\",\"-S\"\]]{style="background-color: #eeeeee;"}\
\

-   What Android operating system is it? API 25? Check! Device
    connected? Check! Bring on the next adb shell command, \"am\", the
    \"activity manager\"!

\
\"Within an adb shell, you can issue commands with the activity manager
(am) tool to perform various system actions, such as start an activity,
force-stop a process, broadcast an intent, modify the device screen
properties, and more. While in a shell, the syntax is: \[\...\] *am
command *\
\
\"You can also issue an activity manager command directly from adb
without entering a remote shell. For example:\

<div>

``` {.no-pretty-print style="background-attachment: initial; background-clip: initial; background-image: initial; background-origin: initial; background-position: initial; background-repeat: initial; background-size: initial; border: 1px solid rgb(221, 221, 221); font-stretch: normal; line-height: 18px; margin-bottom: 1em; overflow: auto; padding: 1em;"}
adb shell am start -a android.intent.action.VIEW
```

\
\"Table 2. Available activity manager commands\"\
\"*start \[options\] intent*\
\
\"Start an
[Activity](https://developer.android.com/reference/android/app/Activity.html)
specified by intent. See the [Specification for intent
arguments](https://developer.android.com/studio/command-line/adb.html#IntentSpec).\
\
\"Options are:\
\"-D: Enable debugging.\
\"-W: Wait for launch to complete.\
\"\--start-profiler file: Start profiler and send results to file.\
\"-P file: Like \--start-profiler, but profiling stops when the app goes
idle.\
\"-R count: Repeat the activity launch count times. Prior to each
repeat, the top activity will be finished.\
\"-S: Force stop the target app before starting the activity.\
\"\--opengl-trace: Enable tracing of OpenGL functions.\
\"\--user user\_id \| current: Specify which user to run as; if not
specified, then run as the current user\".\
- [Developer.Android.Cpm / ADB /
AM](https://developer.android.com/studio/command-line/adb.html#am)

</div>

-   So, we are using adb to launch the activity manager, start an
    activity, and wait for the launch to complete for APIDemos, our
    app\'s activity! Just in case it already happens to running, we are
    going to (-S) force stop it first, so we start of fresh.  

\
[\[ADB\] Waiting for pkg: \'io.appium.android.apis\' and activity:
\'io.appium.android.apis.ApiDemos\' to be
focused]{style="background-color: #eeeeee;"}\
\

-   Yes, yes, yes! Yes! \... ApiDemos, the app we installed onto the
    emulator is running and launched! 
-   We are just waiting for the main window to gain the focus of the
    Android emulator. 

<div>

*\
*

</div>

<div>

*\... At this point? The app launched and opened up on the emulator I
had running! \... *

</div>

<div>

*\
*

</div>

<div>

\

</div>

\
[\[ADB\] Possible activities, to be checked:
io.appium.android.apis.ApiDemos,
io.appium.android.apis.io.appium.android.apis.ApiDemos]{style="background-color: #eeeeee;"}\
[\[ADB\] Getting focused package and
activity]{style="background-color: #eeeeee;"}\
[\[ADB\] Getting connected
devices\...]{style="background-color: #eeeeee;"}\
[\[ADB\] 1 device(s) connected]{style="background-color: #eeeeee;"}\
[\[ADB\] Running
\'/Users/ventmahe/Library/Android/sdk/platform-tools/adb\' with args:
\[\"-P\",5037,\"-s\",\"emulator-5554\",\"shell\",\"dumpsys\",\"window\",\"windows\"\]]{style="background-color: #eeeeee;"}\
\

-   Let\'s see\... does our Android app running on the emulator,
    ApiDemos, have the focus? 
-   Grab from the Android device whatever is the main focus, the app
    that is running in the foreground. 
-   We are going to do a system dump and throw what is there in a
    window\... is it what we hoped?

\
\
[\[ADB\] Found package: \'io.appium.android.apis\' and fully qualified
activity name :
\'io.appium.android.apis.ApiDemos\']{style="background-color: #eeeeee;"}\
\

-   We now have proof that the ApiDemos program is running! 

\
\
[\[Appium\] New AndroidDriver session created successfully, session
4bc8afe6-7aa5-4ac8-a42b-55890e777f6d added to master session
list]{style="background-color: #eeeeee;"}\
\

-   We just successfully installed UIAutomator, set up a connection
    between the Appium Server running on your computer and one on the
    Android device or emulator. We pushed our app\'s directories onto
    the emulator. We launched the app\'s activity. And we proved that
    the app now was up and running and had the focus!
-   Do you remember when \"\[BaseDriver\] Session created with session
    id: 4bc8afe6-7aa5-4ac8-a42b-55890e777f6d\"? Well, it\'s now added to
    the master list! It\'s about time! 

\
[\[BaseDriver\] Event \'newSessionStarted\' logged at 1495296265108
(12:04:25 GMT-0400 (EDT))]{style="background-color: #eeeeee;"}\
\

-   Yay! A new session with Appium\'s base driver, all logged in! \... 

<div>

Remember: 

</div>

<div>

*\"An appium driver is a module which processes [Mobile Json Wire
Protocol](https://code.google.com/p/selenium/source/browse/spec-draft.md?repo=mobile) commands
and controls a device accordingly. The commands can either come in over
HTTP as json api requests, or they can be passed to the driver object
programmatically as already-parsed json object (without the HTTP headers
and junk). \[\...\] The appium Base driver already includes
the [mjsonwp](https://github.com/appium/appium-base-driver/blob/master/lib/mjsonwp/README.md) module,
which is the HTTP server that converts incoming requests into json
objects that get sent to the driver programmatically.\
\"The appium Base driver already has all the REST api routes,
validation, and error codes supplied
by [mjsonwp](https://github.com/appium/appium-base-driver/blob/master/lib/mjsonwp/README.md).
\[\...\] Appium drivers are designed to have a single testing session
per instantiation. This means that one Driver object should be attached
to a single device and handle commands from a single client. - [Github /
Appium / Appium-Base-Driver /
lib](https://github.com/appium/appium-base-driver/tree/master/lib/basedriver) /
basedriver*

</div>

<div>

\

</div>

\
\
[\[MJSONWP\] Responding to client with driver.createSession() result:
{\"platform\":\"LINUX\",\"webStorageEnabled\":false,\"takesScreenshot\":true,\"javascriptEnabled\":true,\"databaseEnabled\":false,\"networkConnectionEnabled\":true,\"locationContextEnabled\":false,\"warnings\":{},\"desired\":{\"app\":\"/Users/ventmahe/code/basic\_appium\_framework/ApiDemos-debug.apk\",\"platformName\":\"Android\",\"deviceName\":\"emulator-5554\"},\"app\":\"/Users/ventmahe/code/basic\_appium\_framework/ApiDemos-debug.apk\",\"platformName\":\"Android\",\"deviceName\":\"emulator-5554\",\"deviceUDID\":\"emulator-5554\",\"platformVersion\":\"7.1.1\",\"deviceScreenSize\":\"1440x2560\",\"deviceModel\":\"Android
SDK built for
x86\",\"deviceManufacturer\":\"unknown\",\"appPackage\":\"io.appium.android.apis\",\"appWaitPackage\":\"io.appium.android.apis\",\"appActivity\":\"io.appium.android.apis.ApiDemos\",\"appWaitActivity\":\"io.appium.android.apis.ApiDemos\"}]{style="background-color: #eeeeee;"}\
\

-   Okay! We have the Mobile JSON Wire Protocol reporting back with the
    results of the Appium Driver createSession() command.
-   The default driver session is of the Linux platform, does not have
    web storage, takes screenshots, has JavaScript enabled along with
    network connectivity.
-   It also has the DesiredCapabilities we passed in. 
-   It also records the stats of the emulator or Android device we are
    working on. 

\
\
[\[HTTP\] \<\-- POST /wd/hub/session 200 8885 ms -
868]{style="background-color: #eeeeee;"}\
[\
]{style="background-color: white;"}[**\... All of this? \... It took
only under nine seconds to do everything from kickoff to now!
\....**]{style="background-color: white;"}\
\
[\[HTTP\] \--\> POST
/wd/hub/session/4bc8afe6-7aa5-4ac8-a42b-55890e777f6d/timeouts/implicit\_wait
{\"ms\":30000}]{style="background-color: #eeeeee;"}\

-   Do you remember when \"\[BaseDriver\] Session created with session
    id: 4bc8afe6-7aa5-4ac8-a42b-55890e777f6d\"? The session id is now
    being used as a session index for the implicit wait timeouts. 

\... Remember\... all we are doing here is having Appium install and
launch the app. After thirty seconds without a command, we are going to
time out.\
[\[MJSONWP\] Calling AppiumDriver.implicitWait() with args:
\[30000,\"4bc8afe6-7aa5-4ac8-a42b-55890e777f6d\"\]]{style="background-color: #eeeeee;"}\
[\[BaseDriver\] Set implicit wait to
30000ms]{style="background-color: #eeeeee;"}\
\
\... Let\'s put 30 seconds on the clock\...\
\... And the clock starts\... now!\
\... So, how are you doing? Have you enjoyed this? \... I mean not,
enjoyed as in you enjoy blowing bubbles on a summer day. But have you
enjoyed learning along with me? \...\
\... This was really fun for me the first ten hours I started
researching this\...\
\... I lost count how long this blog entry took after twenty hours of
research\...\
\... Why am I doing this, spending countless hours crafting a blog entry
not many people will read?\...\
\... Well, I am trying to learn as much as I can as fast as I can. I
want to be the best Appium developer I can be\... I just started
learning about it in March of 2017. Four months so far and [look at the
many Appium
projects](http://www.tjmaher.com/p/programming-projects.html) I have
done! \... If I get caught in yet another layoff, I want to make it as
painless for me as possible to get another job! \...\
\... Okay, I think that has been thirty seconds\... Let\'s see how the
app is doing\...\
\
\
[\[MJSONWP\] Responding to client with driver.implicitWait() result:
null]{style="background-color: #eeeeee;"}\
[\[HTTP\] \<\-- POST
/wd/hub/session/4bc8afe6-7aa5-4ac8-a42b-55890e777f6d/timeouts/implicit\_wait
200 8 ms - 76]{style="background-color: #eeeeee;"}\
\

-   After 30 seconds, the time ran out on the implicit wait. 
-   We are sending that data back to the Appium server running on our
    local machine.

\
[\[HTTP\] \--\> DELETE
/wd/hub/session/4bc8afe6-7aa5-4ac8-a42b-55890e777f6d
{}]{style="background-color: #eeeeee;"}\
\

-   The call comes over the wire\... Delete the session id! 

\
[\[MJSONWP\] Calling AppiumDriver.deleteSession() with args:
\[\"4bc8afe6-7aa5-4ac8-a42b-55890e777f6d\"\]]{style="background-color: #eeeeee;"}\
[\[BaseDriver\] Event \'quitSessionRequested\' logged at 1495296265360
(12:04:25 GMT-0400 (EDT))]{style="background-color: #eeeeee;"}\
[\[AndroidDriver\] Shutting down Android
driver]{style="background-color: #eeeeee;"}\
\

-   Our Appium Driver got the message from the Appium Server! Delete the
    session! Call the deleteSession() method!
-   The Appium base driver logs the quitSessionRequested, and the
    Android Driver announces it is shutting down. 

\
\
[\[ADB\] Getting connected
devices\...]{style="background-color: #eeeeee;"}\
[\[ADB\] 1 device(s) connected]{style="background-color: #eeeeee;"}\
[\[ADB\] Running
\'/Users/ventmahe/Library/Android/sdk/platform-tools/adb\' with args:
\[\"-P\",5037,\"-s\",\"emulator-5554\",\"shell\",\"am\",\"force-stop\",\"io.appium.android.apis\"\]]{style="background-color: #eeeeee;"}\
\

-   Are we connected still? Yes? Good! Let\'s use the adb shell command
    Activity Manager \"am\" to do a force-stop on our application. 

\
[\[ADB\] Pressing the HOME button]{style="background-color: #eeeeee;"}\
\

-   Our app is scheduled to recede into the background\... 

\
[\[ADB\] Getting connected
devices\...]{style="background-color: #eeeeee;"}\
[\[ADB\] 1 device(s) connected]{style="background-color: #eeeeee;"}\
[\[ADB\] Running
\'/Users/ventmahe/Library/Android/sdk/platform-tools/adb\' with args:
\[\"-P\",5037,\"-s\",\"emulator-5554\",\"shell\",\"input\",\"keyevent\",3\]]{style="background-color: #eeeeee;"}\
\

-   Are we connected still? Yes? Good! Let\'s use the adb shell command
    called \"input\", where we are going to simulate a keyevent, 3,
    which is simulating pressing the HOME key. 

<div>

Some event\_codes according to [this event\_code discussion on Stack
Overflow](https://stackoverflow.com/questions/7789826/adb-shell-input-events):

</div>

<div>

\

</div>

<div>

</div>

\

``` {.default .prettyprint .prettyprinted style="background-color: #eff0f1; border: 0px; color: #393318; font-family: Consolas, Menlo, Monaco, "Lucida Console", "Liberation Mono", "DejaVu Sans Mono", "Bitstream Vera Sans Mono", "Courier New", monospace, sans-serif; font-size: 13px; font-stretch: inherit; font-variant-numeric: inherit; line-height: inherit; margin-bottom: 1em; max-height: 600px; overflow: auto; padding: 5px; vertical-align: baseline; width: auto; word-wrap: normal;"}
1 -->  "KEYCODE_MENU" 
2 -->  "KEYCODE_SOFT_RIGHT" 
3 -->  "KEYCODE_HOME" 
4 -->  "KEYCODE_BACK" 
5 -->  "KEYCODE_CALL" 
6 -->  "KEYCODE_ENDCALL" 
7 -->  "KEYCODE_0" 
8 -->  "KEYCODE_1" 
9 -->  "KEYCODE_2" 
10 -->  "KEYCODE_3" 
11 -->  "KEYCODE_4" 
12 -->  "KEYCODE_5" 
13 -->  "KEYCODE_6" 
14 -->  "KEYCODE_7" 
15 -->  "KEYCODE_8" 
16 -->  "KEYCODE_9" 
17 -->  "KEYCODE_STAR" 
18 -->  "KEYCODE_POUND" 
19 -->  "KEYCODE_DPAD_UP" 
20 -->  "KEYCODE_DPAD_DOWN" 
21 -->  "KEYCODE_DPAD_LEFT" 
22 -->  "KEYCODE_DPAD_RIGHT" 
23 -->  "KEYCODE_DPAD_CENTER" 
24 -->  "KEYCODE_VOLUME_UP" 
25 -->  "KEYCODE_VOLUME_DOWN" 
26 -->  "KEYCODE_POWER" 
27 -->  "KEYCODE_CAMERA" 
28 -->  "KEYCODE_CLEAR" 
```

\

-   Now, our app receded into the background. 

\
\
[\[AndroidBootstrap\] Sending command to android:
{\"cmd\":\"shutdown\"}\
\[AndroidBootstrap\] Received command result from bootstrap\
\[UiAutomator\] Shutting down UiAutomator\
\[UiAutomator\] Moving to state
\'stopping\']{style="background-color: #eeeeee;"}\
\

-   Android Bootstrap sends the final groups of messages to UI Automator
    through the wormhole\... I mean the socket. The command? Shutdown. 
-   UI Automator moves to the \"Stopping\" state. 

\
\
[\[AndroidBootstrap\] \[BOOTSTRAP LOG\] \[debug\] Got data from client:
{\"cmd\":\"shutdown\"}]{style="background-color: #eeeeee;"}\
[\[AndroidBootstrap\] \[BOOTSTRAP LOG\] \[debug\] Got command of type
SHUTDOWN]{style="background-color: #eeeeee;"}\
[\[AndroidBootstrap\] \[BOOTSTRAP LOG\] \[debug\] Returning result:
{\"status\":0,\"value\":\"OK, shutting
down\"}]{style="background-color: #eeeeee;"}\
[\[AndroidBootstrap\] \[BOOTSTRAP LOG\] \[debug\] Closed client
connection]{style="background-color: #eeeeee;"}\
\

-   Android Bootstrap, in full on Debug mode closes the connection. 

\
[\
]{style="background-color: #eeeeee;"}[\[AndroidBootstrap\] \[UIAUTO
STDOUT\] INSTRUMENTATION\_STATUS:
numtests=1]{style="background-color: #eeeeee;"}\
[\[AndroidBootstrap\] \[UIAUTO STDOUT\] INSTRUMENTATION\_STATUS:
stream=.]{style="background-color: #eeeeee;"}\
[\[AndroidBootstrap\] \[UIAUTO STDOUT\] INSTRUMENTATION\_STATUS:
id=UiAutomatorTestRunner]{style="background-color: #eeeeee;"}\
[\[AndroidBootstrap\] \[UIAUTO STDOUT\] INSTRUMENTATION\_STATUS:
test=testRunServer]{style="background-color: #eeeeee;"}\
[\[AndroidBootstrap\] \[UIAUTO STDOUT\] INSTRUMENTATION\_STATUS:
class=io.appium.android.bootstrap.Bootstrap]{style="background-color: #eeeeee;"}\
[\[AndroidBootstrap\] \[UIAUTO STDOUT\] INSTRUMENTATION\_STATUS:
current=1]{style="background-color: #eeeeee;"}\
[\[AndroidBootstrap\] \[UIAUTO STDOUT\] INSTRUMENTATION\_STATUS\_CODE:
0]{style="background-color: #eeeeee;"}\
[\[AndroidBootstrap\] \[UIAUTO STDOUT\] INSTRUMENTATION\_STATUS:
stream=]{style="background-color: #eeeeee;"}\
[\[AndroidBootstrap\] \[UIAUTO STDOUT\] Test results for
WatcherResultPrinter=.]{style="background-color: #eeeeee;"}\
[\[AndroidBootstrap\] \[UIAUTO STDOUT\] Time:
2.578]{style="background-color: #eeeeee;"}\
[\[AndroidBootstrap\] \[UIAUTO STDOUT\] OK (1
test)]{style="background-color: #eeeeee;"}\
[\[AndroidBootstrap\] \[UIAUTO STDOUT\] INSTRUMENTATION\_STATUS\_CODE:
-1]{style="background-color: #eeeeee;"}\
\

-   In one last flurry of activity, Android Bootstrap talks about how it
    ran one test, the UiAutomatorTestRunner. 
-   The watch it set before, it is stopped. 2.578 seconds.
-   There are no more tests to be run. Android Bootstrap is done. 

\
\
[\[UiAutomator\] UiAutomator shut down
normally]{style="background-color: #eeeeee;"}\
[\[UiAutomator\] Moving to state
\'stopped\']{style="background-color: #eeeeee;"}\
\

-   So long, UiAutomator!

\
[\[ADB\] Attempting to kill all uiautomator
processes]{style="background-color: #eeeeee;"}\
[\[ADB\] Getting all processes with
uiautomator]{style="background-color: #eeeeee;"}\
[\[ADB\] Getting connected
devices\...]{style="background-color: #eeeeee;"}\
[\[ADB\] 1 device(s) connected]{style="background-color: #eeeeee;"}\
[\[ADB\] Running
\'/Users/ventmahe/Library/Android/sdk/platform-tools/adb\' with args:
\[\"-P\",5037,\"-s\",\"emulator-5554\",\"shell\",\"ps\"\]]{style="background-color: #eeeeee;"}\
\

-   [***Is this an error? Or is this a safety measure, such as a
    \"Double Tap\" in the
    movie, [Zombieland](http://www.imdb.com/title/tt1156398)? ***]{style="color: red;"}

\
\
[\[ADB\] No uiautomator process found to kill,
continuing\...]{style="background-color: #eeeeee;"}\
[\[UiAutomator\] Moving to state
\'stopped\']{style="background-color: #eeeeee;"}\
\

-   **[*Goodbye, zombie UIAutomator! \... I am sorry, but I need to
    report you as a bug to the Android Developers. I am a QA Engineer
    after all!*]{style="color: red;"}**

\
\
[\[Logcat\] Stopping logcat
capture]{style="background-color: #eeeeee;"}\
\

-   And goodbye logcat!

\
\
[\[ADB\] Getting connected
devices\...]{style="background-color: #eeeeee;"}\
[\[ADB\] 1 device(s) connected]{style="background-color: #eeeeee;"}\
[\[ADB\] Running
\'/Users/ventmahe/Library/Android/sdk/platform-tools/adb\' with args:
\[\"-P\",5037,\"-s\",\"emulator-5554\",\"shell\",\"am\",\"force-stop\",\"io.appium.unlock\"\]]{style="background-color: #eeeeee;"}\

-   Once again we are using ADB, the Android Debug Bridge to go to the
    device on port 5037, to the emulated Android device, and entering a
    shell script. 
-   am: The Activity Manager. 
-   force-stop: Everything halted.

\
[\[AndroidDriver\] Not cleaning generated files. Add
\`clearSystemFiles\` capability if
wanted.]{style="background-color: #eeeeee;"}\
\

-   ***[Hrm. Should the generated files be cleaned up? Is this a
    bug?]{style="color: red;"}***

\
\
[\[Appium\] Removing session 4bc8afe6-7aa5-4ac8-a42b-55890e777f6d from
our master session list]{style="background-color: #eeeeee;"}\

-   Remember that session we added to the master session list, adding it
    by session id? Parting is such sweet sorrow!

[\[BaseDriver\] Event \'quitSessionFinished\' logged at 1495296266614
(12:04:26 GMT-0400 (EDT))]{style="background-color: #eeeeee;"}\
\

-   Now, the Appium Base Driver has left the stage. 
-   All we have left is the Appium Server. 

\
[\[MJSONWP\] Received response:
null]{style="background-color: #eeeeee;"}\
[\[MJSONWP\] But deleting session, so not
returning]{style="background-color: #eeeeee;"}\
[\[MJSONWP\] Responding to client with driver.deleteSession() result:
null]{style="background-color: #eeeeee;"}\
[\[HTTP\] \<\-- DELETE
/wd/hub/session/4bc8afe6-7aa5-4ac8-a42b-55890e777f6d 200 1260 ms -
76]{style="background-color: #eeeeee;"}\
\

-   \"All Quiet on the Western Front\".
-   \"The Rest \... is Silence\". 

<div>

\... Thank you for sticking with me on this amazing journey!\
\
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
Happy Testing!

</div>

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
Automation](http://www.tjmaher.com/) on [Facebook](https://www.facebook.com/AdventuresInAutomation/)!\"*

</div>

</div>

</div>

</div>
