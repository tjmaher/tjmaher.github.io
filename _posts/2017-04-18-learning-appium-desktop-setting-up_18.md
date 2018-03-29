\-\-- layout: post title: \'Learning Appium Desktop: Setting up remote
devices through WiFi\' date: \'2017-04-18T07:45:00.000-04:00\' author:
T.J. Maher tags: - appium modified\_time:
\'2017-04-20T07:29:17.331-04:00\' blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-8734711956214823583
blogger\_orig\_url:
http://www.tjmaher.com/2017/04/learning-appium-desktop-setting-up\_18.html
\-\-- *This is Part 3 of 6. Care to [go back to the
beginning](http://www.tjmaher.com/2017/04/learning-appium-what-is-appium-server.html)?
Tune in tomorrow to see the next part!*\
*\
*Yesterday, we talked all about connecting Android devices to your
computer through a USB cable. What we didn't cover was that you can also
do this through WiFi!\
\
Why is this important?\
\
Imagine that you are an automation developer who wants to test on real
devices. Instead of being forced to have each and every device attached
to your computer with a tangle of USB cables, you can have all devices
locked down in a lab.\
\
With an automation test you can:\

-   Install an Android app on a remote device.
-   Start up the Android app
-   Run your test.
-   Uninstall the app.

\
... All while connected to the WiFi!\
\
[]{#more}\
\
How to do this? From Android Developer: ADB:
<https://developer.android.com/studio/command-line/adb.html#wireless>\
\
**\
Step 1**: Connect your Android device and adb host computer to a common
Wi-Fi network accessible to both.\
\
\
**Step 2:** Connect the device to the host computer with a USB cable.\

<div>

\
\
**Step 3**:  Set the target device to listen for a TCP/IP connection on
port 5555.\
\
*adb tcpip 5555*\
\
\
**Step 4**:  Disconnect the USB cable from the target device.\
\
**Step 5**: Find the IP address of the Android device. For example, on a
Nexus device, you can find the IP address at **Settings** \> About
tablet (or About phone) \> **Status** \> IP address\
\
For example, 172.17.208.126\
\
*adb connect device\_ip\_address*\
\
\
**Step 6**:  Connect to the device by its IP address.\
\
You will need to press OK when you receive a popup on your device.\
\
\
**Step 7**:  Confirm that your host computer is connected to the target
device:\
\
\$ adb devices\
\
List of devices attached\
device\_ip\_address:5555 device\
\
\
Example: 

</div>

<div>

\
\$ adb devices\
\
List of devices attached\
[172.17.208.126:5555](http://172.17.208.126:5555/) device\
\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 $ adb devices  
   
 List of devices attached  
 172.17.208.126:5555 device  
```

\
\
Now that we have an actual device attached to our computer, we can test
on this device using **Appium Desktop**!\
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
-   **Part Six:**  Inspecting an Android app using Appium Desktop
:::

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
