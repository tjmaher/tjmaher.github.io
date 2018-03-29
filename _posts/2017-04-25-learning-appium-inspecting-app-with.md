\-\-- layout: post title: \'Learning Appium Desktop: Inspecting an app
with Appium Desktop\' date: \'2017-04-25T08:57:00.000-04:00\' author:
T.J. Maher tags: - appium modified\_time:
\'2017-04-25T09:02:43.138-04:00\' thumbnail:
https://2.bp.blogspot.com/-prLNYAWBjKg/WPMjdZlFU3I/AAAAAAAALvE/tmKyBcpqyA8PLdmvlkiExGzVfIV55ddXwCLcB/s72-c/Screen%2BShot%2B2017-04-16%2Bat%2B3.52.25%2BAM.png
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-1102155347783631313
blogger\_orig\_url:
http://www.tjmaher.com/2017/04/learning-appium-inspecting-app-with.html
\-\-- *This is Part 6 of 6. Care to [go back to the
beginning](http://www.tjmaher.com/2017/04/learning-appium-what-is-appium-server.html)?*\
*\
*So far we have:\

-   Learned [how to install Appium
    Desktop](http://www.tjmaher.com/2017/04/learning-appium-what-is-appium-server.html)
    which bundles Appium with an inspector we can use to inspect our
    applications. 
-   Studied how to connect an Android device via USB through the Android
    Command Line tool adb.
-   Connected to the device via WiFi. 
-   Learned how to set up an emulated Android device.

\
With this blog post we are going to:\

-   Inspect an app with Appium Desktop 
-   Before we need to do that, we need to find an app\'s Desired
    Capabilities!

<div>

\
[]{#more}\

</div>

### What are Desired Capabilities?

\
Taken from <http://appium.io/slate/en/master/?java#appium-concepts>\
\
\"Desired capabilities are a set of keys and values (i.e., a map or
hash) sent to the Appium server to tell the server what kind of
automation session we're interested in starting up. There are also
various capabilities which can modify the behavior of the server during
automation. For example, we might set the platformName capability to iOS
to tell Appium that we want an iOS session, rather than an Android or
Windows one. Or we might set the safariAllowPopups capability to true in
order to ensure that, during a Safari automation session, we're allowed
to use JavaScript to open up new windows. See the [capabilities
doc](http://appium.io/slate/en/master/?java#caps.md) for the complete
list of capabilities available for Appium\".\
\

### How to Set Up Android Desktop?

\
**Step One**: Check to see if there are any Android devices running. If
not, start an emulator or an actual Android device\

-   My Samsung Galaxy S7 Edge that already has Developer Options turned
    on. I connected it to my MacBook via USB. 
-   On the Mac Terminal, enter: avd devices 
-   It showed that in the list of devices attached, there was device:
    412327b5 

**Step Two:** On the Android device or emulator, run the app you want to
inspect.\

-   Okay! Let\'s run the Calculator app!

**\
Step Three:** Run the app on the device and find the appPackage and
appActivity.\

-   Let\'s say the magic words to take all the system properties on the
    device, grab just what is running in the current window on the app,
    what is in focus, and dump those properties onto the screen. 
-   This will be a call to the adb shell, i.e. the device that is
    connected to adb. 
-   Type in the Mac Terminal: adb shell \"dumpsys window windows \| grep
    -E \'mCurrentFocus \| mFocusedApp\'\" 

\

``` {style="background: rgb(240, 240, 240); border: 1px dashed rgb(204, 204, 204); font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; width: 646.469px;"}
 $adb shell "dumpsys window windows | grep -E 'mCurrentFocus | mFocusedApp'"  
   
mFocusedApp=AppWindowToken{d0d077a06 
token = Token { fc44ce1 ActivityRecord{4158648 u0 
com.sec.android.app.popupcalculator/.Calculator t352}}}  
```

\

-   This shows that the appPackage
    is *com.sec.android.app.popupcalculator*
-   This also shows that the appActivity is *.Calculator*

\
**Step Four**: Start up Android Desktop\

-   Click on the Appium Desktop icon
-   Leaving everything at default, let\'s select: Start Server v1.6.4 on
    the main page
-   Once we see the server is running, let\'s: Start New Session
-   Now we see that the desired capabilities are showing.

\
**Step Five:** Enter Desired Capabilities and Save Them\

-   platformName: Android
-   deviceName: 412327b5
-   appPackage: com.sec.android.app.popupcalculator
-   appActivity: .Calculator

\
Let\'s select \"Save As\...\" and save it as \"Calculator\".\
\
**Step Six**: Start the New Session!\

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

### Appium Desktop: Like FireBug, or Google Chrome -\> Inspect, but for Apps!

<div>

Before automating, whether it is for a web or a mobile application, you
need to try to figure out how you are going to interact with the various
elements on the page and the screen. How can you identify one particular
username textbox, and send text to it? How can you identify a Login
button? 

</div>

<div>

\

</div>

<div>

With the Firefox browser, you could download
[Firebug](http://getfirebug.com/) and
[Firepath](https://addons.mozilla.org/en-US/firefox/addon/firepath/) to
see the inner workings of the DOM (Document Object Model).

</div>

<div>

\

</div>

<div>

With the Chrome browser, you could right-click and Inspect, to [examine
a site with Google Developers
Tools](https://developers.google.com/web/tools/chrome-devtools/inspect-styles/). 

</div>

\
With mobile apps, Google Android Developers used to provide a
[UiAutomatorViewer.](http://www.guru99.com/uiautomatorviewer-tutorial.html)\

###  Appium Desktop: A Tool in Three Parts

Appium Desktop has three panes:\
\
**[Left pane:]{.underline}**\

-   Reflection of the actual device or the emulator you are running. 
-   You can attempt to manipulate what is there in the leftmost pane, to
    see what will happen. Select an object, then select \"Tap\" in the
    rightmost pane. 
-   You can move from screen to screen on your running emulator or
    actual device, and select the \"Refresh\" button on the center
    screen.

**[Center pane: ]{.underline}**\

-   Displays the App Source code in an XML format, exactly as shown when
    navigating the DOM of a web page. 
-   **Back**: On the very top of the center pane, you can choose to
    manipulate the reflection in the left pane by choosing the \"Back\"
    button. 
-    **Refresh**: Want to examine another screen? Go to the screen in
    your app or emulator. After selecting \"Refresh\", the screen image
    will appear within three seconds.
-   **Quit**: Closes this three paned view and goes back to the Desired
    Capabilities page.

\
**[Right Pane:]{.underline} **\

-   **Tap**: Interact with whatever object you have selected in the
    leftmost pane. 
-   **Send Keys**: Want to enter text into a textbox selected on the
    leftmost pane? Select the object, press \"Send Keys\" and type up
    text into the popup window.

<div>

The right pane is the one that is the most useful. Select an object in
the left pane, and it will tell you how to find it, either by XPath, Id,
or Class Name. It will also say exactly what locator to use in an
automation test suite.

</div>

<div>

\

</div>

### Different Locating Strategies

*\"Appium is built to implement the Selenium WebDriver JSON Wire
Protocol
[specification](https://code.google.com/p/selenium/wiki/JsonWireProtocol),
extended to enable the automation of mobile devices. By and large, the
extensions to the WebDriver spec are encoded within the draft Mobile
JSON Wire Protocol
[spec](https://github.com/SeleniumHQ/mobile-spec/blob/master/spec-draft.md).
In order to find elements in a mobile environment, Appium implements a
number of locator strategies that are specific to, or adaptations for,
the particulars of a mobile device. Three are available for both Android
and iOS.\" - SauceLabs, [Advanced Locator
Strategies](https://saucelabs.com/blog/advanced-locator-strategies)*[\
]{.underline}[XPath:]{.underline} Unfortunately, XPath may be the most
common way to find a mobile object. If the developers of the mobile app
did not tag each and every mobile object, such as tagging a username
textbox with the id = \'textbox\', you may be dealing with this long
string of backslashes.\

> *\"XPath is defined as XML path. It is a syntax or language for
> finding any element on the web page using XML path expression. XPath
> is used to find the location of any element on a webpage using HTML
> DOM structure\". - Guru99\'s [section on
> XPath](http://www.guru99.com/xpath-selenium.html)*

XPath = //tagName\[\@Attribute=\'Value\'\]\
\
If you follow along with [Guru99\'s section on
XPath](http://www.guru99.com/xpath-selenium.html), you can find out
there are both **Absolute XPath** which traverses the entire DOM
searching for an element.\
\

``` {style="background-color: whitesmoke; border-radius: 4px; border: 1px solid rgba(0, 0, 0, 0.14902); color: #333333; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 13px; line-height: 20px; margin-bottom: 10px; padding: 9.5px; white-space: pre-wrap; word-break: break-all; word-wrap: break-word;"}
html/body/div[1]/section/div[1]/div/div/div/div[1]/div/div/div/div/div[3]/div[1]/div/h4[1]/b
```

\
**There is also the Relative XPath:**\
\

``` {style="background-color: whitesmoke; border-radius: 4px; border: 1px solid rgba(0, 0, 0, 0.14902); color: #333333; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 13px; line-height: 20px; margin-bottom: 10px; padding: 9.5px; white-space: pre-wrap; word-break: break-all; word-wrap: break-word;"}
Relative xpath: //*[@class='featured-box']//*[text()='Testing']
```

<div>

\
\... To skip having to deal with either of these, ask the mobile
developers on your team to tag all the mobile objects they are working
with.\
\
Hrm. Convince mobile developers to take on more work where it will
mainly help QA? Or somehow learn XPath? I am not sure which way would be
easier\...\
\
XPath can be fragile. If a mobile element is placed higher or lower in
the DOM, the XPath will then changes, introducing some brittleness into
the automation, since the mobile element will not be found.\
\
Having an ID, or a classname (if the class is unique) might be easier.\
\
\
**[Class Name]{.underline}**\
*\
\"The class name strategy is a string representing a UI element on the
current view. For iOS it is the full name of a
[UIAutomation](https://developer.apple.com/library/prerelease/tvos/documentation/DeveloperTools/Conceptual/InstrumentsUserGuide/UIAutomation.html)
[class](https://developer.apple.com/library/ios/navigation/#section=Frameworks&topic=UIAutomation),
and will begin with UIA-, such as UIATextField for a text field. A full
reference can be found
[here](https://developer.apple.com/library/ios/navigation/#section=Frameworks&topic=UIAutomation).
For Android it is the fully qualified name of a [UI
Automator](https://developer.android.com/tools/testing-support-library/index.html#UIAutomator)
[class](https://developer.android.com/reference/android/widget/package-summary.html),
such android.widget.EditTextfor a text field. A full reference can be
found
[here](https://developer.android.com/reference/android/widget/package-summary.html).
The client libraries for Appium support getting a single element, or
multiple elements, based on the class name\". - SauceLabs, [Advanced
Locator
Strategies](https://saucelabs.com/blog/advanced-locator-strategies)*\
**[Id:]{.underline}**\
\
*\"In the mobile environment, ids are not, as in WebDriver, CSS ids, but
rather some form of native identifier.*\

-   *\"For iOS the situation is complicated. Appium will first search
    for an accessibility id that matches. If there is none found, a
    string match will be attempted on the element labels. Finally, if
    the id passed in is a localization key, it will search the localized
    string.*
-   *\"For Android, the id is the element\'s android:id\".*

\* - SauceLabs, [Advanced Locator
Strategies](https://saucelabs.com/blog/advanced-locator-strategies)*\
\
\
This concludes our \"Learning Appium Desktop\" series for now! Within
the next couple of weeks we will start:\
\

-   Learning Appium Desktop for the IOS
-   A Coding Project in Appium

\
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
Until then, Happy Testing!\
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
