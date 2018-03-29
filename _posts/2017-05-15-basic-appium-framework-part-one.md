\-\-- layout: post title: \'Build a Basic Appium Framework: Review How
to Inspect Mobile Apps with Appium Desktop\' date:
\'2017-05-15T07:43:00.000-04:00\' author: T.J. Maher tags: - Java -
appium - Android modified\_time: \'2017-06-16T20:05:14.927-04:00\'
thumbnail:
https://1.bp.blogspot.com/-lgIjJB-Ursc/WOWRrM4qVXI/AAAAAAAALuM/ZvUm4yCjNIoucjtNtIaup6GGhCSG1l4jACPcB/s72-c/screen-start-simple.png
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-4418103800361051719
blogger\_orig\_url:
http://www.tjmaher.com/2017/05/basic-appium-framework-part-one.html
\-\-- For this next blog series, we will be building a basic Appium
Framework built on top of the information gathered in the [Learning
Appium
Desktop](http://www.tjmaher.com/2017/04/learning-appium-what-is-appium-server.html)
series. This basic mobile automation test framework we will be
constructing will consist of:\
\

-   **Appium Desktop**: To investigate the app we will be writing
    automated tests for, and to start up an Appium server on our local
    machine. ( [Official GitHub
    site](https://github.com/appium/appium-desktop) ) 
-   **An Android Emulator**: Created by Android Studio and the Android
    Virtual Machine (AVM) Manager, connected to your local computer with
    the Android Debug Bridge (\"adb\"). ([Official Developer.Android.Com
    site on
    emulators](https://developer.android.com/studio/run/emulator.html) )
-   The code will be written in the **Java Client** version of
    **Appium** using a **MacBook** and **IntelliJ** as an Integrated
    Development Environment (IDE). Although Android Studio, IntelliJ,
    and Android .apk files run on both Windows and Macs, the next
    version of this project will consist of emulated iPhones, iPads and
    Apple .ipa files use XCode, which (as far as I know) doesn\'t work
    on Windows machines. ( Official [Github for
    appium/java-client](https://github.com/appium/java-client) )
-   Tests will be kicked off using **TestNG**. I like the annotations
    and the built in ability to have parallel tests running. We won\'t
    explore it in this particular series, but we will later. ( See the
    [official TestNG site](http://testng.org/doc/) ).  
-   It will use **Hamcrest,** a Java matcher program in order to create
    very readable tests. (Official site for <http://hamcrest.org/> )

I will be attempting to finish code walkthrough over the next two weeks
on a Monday / Wednesday / Friday publishing schedule.\
\
[]{#more}\
\
Want to get to the good stuff? I already have the code all written that
we will be exploring! You can access it
at <https://github.com/tjmaher/basic_appium_framework>\
\
Please feel free to use any IDE you wish to code in:
[vim](http://www.vim.org/download.php),
[emacs](https://www.gnu.org/software/emacs/),
[nano](https://www.nano-editor.org/), [Sublime Text
Editor](https://www.sublimetext.com/),
[IntelliJ](https://www.jetbrains.com/idea/) or
[Eclipse](https://eclipse.org/). You could even use [Android
Studio](https://developer.android.com/studio/index.html), built on top
of IntelliJ. I prefer IntelliJ IDEA, first introduced to it when I was
working through Alan Richardson\'s [Selenium WebDriver with
Java](http://unow.be/at/webdriverapi) course back in 2013.\
\
Disclaimer: Coding in Appium is still brand-new to me. I only first
started a month ago, slowly working my way through two online courses.
[Learning Appium
Desktop](http://www.tjmaher.com/2017/04/learning-appium-what-is-appium-server.html),
the initial setup, took so much longer than I thought it was going to!\
\
Because it was so complex, even though we just covered all this content
month ago, you might need a review\... I sure did! Last week, when I was
ramping up a co-worker on setting up Appium Desktop on his machine
(\"Hi, Rahul!\") I had to refer back to the notes on my blog many, many
times.\

###  Review: How Do I Inspect Mobile Apps on Appium Desktop, Again? 

If you have never set up Appium Desktop before, I suggest you go through
my notes on [Learning
Appium](http://www.tjmaher.com/2017/04/learning-appium-what-is-appium-server.html).
It\'s tricky! My notes should spell it all out for you. Here are seven
steps to get yourself up and running, referring back to the notes.\
\
**[Step 1:]{.underline}**  Install Java, [if need be, and install and
launch Appium
Desktop](http://www.tjmaher.com/2017/04/learning-appium-what-is-appium-server.html)\
\

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://1.bp.blogspot.com/-lgIjJB-Ursc/WOWRrM4qVXI/AAAAAAAALuM/ZvUm4yCjNIoucjtNtIaup6GGhCSG1l4jACPcB/s640/screen-start-simple.png){width="640" height="624"}](https://1.bp.blogspot.com/-lgIjJB-Ursc/WOWRrM4qVXI/AAAAAAAALuM/ZvUm4yCjNIoucjtNtIaup6GGhCSG1l4jACPcB/s1600/screen-start-simple.png)
                                                                                                                           *Behold, the Appium Desktop start screen lives again!*
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

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
\
\
\
\
\
\
\... Then, start a new Server by pressing the \"Start Server
v.16.4-beta\" button. Let\'s leave the host at 0.0.0.0 (your local host,
Home) and the port at 4723 for now.\
\

  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://1.bp.blogspot.com/-EJ48P-0SgEc/WOWSn_RnxnI/AAAAAAAALuU/s5G_hP9tA6U__B4QhRYiS016h6OMlHyrgCPcB/s640/screen-logs.png){width="640" height="595"}](https://1.bp.blogspot.com/-EJ48P-0SgEc/WOWSn_RnxnI/AAAAAAAALuU/s5G_hP9tA6U__B4QhRYiS016h6OMlHyrgCPcB/s1600/screen-logs.png)
                                                                                                 *Appium is running in the background, listening for commands to be sent to 0.0.0.0:4723.*
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

\
\
\
**[Step 2:]{.underline}  **[Install Android Studio, which comes with the
both Android Software Development Kit (SDK), and Android Command Line
Tools](http://www.tjmaher.com/2017/04/learning-appium-desktop-how-to-connect.html)
such as the Android Debug Bridge (ADB) to connect your physical Android
device via USB. Make sure to set up ANDROID\_HOME!\
\
**[Step 3:]{.underline}** Connect your physical Android device [via
WiFi, if you
wish](http://www.tjmaher.com/2017/04/learning-appium-desktop-setting-up_18.html).
This project will use Android emulators, but physical devices will work,
too.\
\
[**Step 4:**]{.underline} Set up an Android emulator [using Android
Studio's AVD (Android Virtual
Device)](http://www.tjmaher.com/2017/04/learning-appium-desktop-setting-up.html)
Manager. Run the emulator.\
**\
[Step 5]{.underline}**: [Find the appPackage and appActivity for the
App](http://www.tjmaher.com/2017/04/learning-appium-desktop-find-desired.html):
Install the .apk you will be testing against by downloading the .apk,
then dragging and dropping the .apk onto an Android emulator to install
it. Me, I will be using **ApiDemos-debug.apk** for this chapter.\
\

-   Go to [Appium\'s
    Java-Client](https://github.com/appium/java-client/tree/master/src/test/java/io/appium/java_client)
    page.
-   Right-click on
    [ApiDemos-debug.apk](https://github.com/appium/java-client/blob/master/src/test/java/io/appium/java_client/ApiDemos-debug.apk) and
    select \"Save Link As\". Save it onto your Desktop.
-   Drag-and-drop it from your Desktop, your Download folder, or
    wherever you saved it, onto your running emulator. 
-   Double-click the \"ApiDemos\" folder to launch the program on the
    emulator. 

\
\

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://2.bp.blogspot.com/-beQ9ncjQRPQ/WRTVnf5_DTI/AAAAAAAALxM/CU2EZltdNf85sT8CJvW33yyzkLRIylcLgCLcB/s640/1.%2BAPI%2BDemo%2BApp.png){width="388" height="640"}](https://2.bp.blogspot.com/-beQ9ncjQRPQ/WRTVnf5_DTI/AAAAAAAALxM/CU2EZltdNf85sT8CJvW33yyzkLRIylcLgCLcB/s1600/1.%2BAPI%2BDemo%2BApp.png)
                                                                                                                              *The ApiDemos-debug.apk app we will be automating.*
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

\
\
While [the app is
running](http://www.tjmaher.com/2017/04/learning-appium-desktop-find-desired.html):\
\

-   Open your Mac Terminal. 
-   Copy-and-paste the following code into your Mac Terminal.

\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 adb shell "dumpsys window windows | grep -E 'mCurrentFocus | mFocusedApp'"  
```

\
\... This code uses the Android Debug Bridge to go into the app running,
and grab either the currentFocus or FocusedApp, and dump the output.\
\
This showed me:\
\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 mFocusedApp=AppWindowToken{2693b97 token=Token{ec7ff31 
ActivityRecord{10a4fd8 u0 io.appium.android.apis/.ApiDemos t254}}}  
```

\
\
\
**[\
]{.underline}[Step 6:]{.underline}**  Enter [the Desired Capabilities,
save the
Capability](http://www.tjmaher.com/2017/04/learning-appium-desktop-find-desired.html)
Set\
\

-   Going back to Appium Desktop, select \"Start New Session\". 
-   Fill out the Desired Capabilities

\

::: {.separator style="clear: both; text-align: center;"}
[![](https://2.bp.blogspot.com/-OXfHlPMFfEU/WRTV1rPGUEI/AAAAAAAALxQ/ru3DD7Ziwb4bkGAFX1QuqjGhWXgXRQZQACLcB/s640/2.%2BAppium%2BDesktop%2BSetup.png){width="640"
height="394"}](https://2.bp.blogspot.com/-OXfHlPMFfEU/WRTV1rPGUEI/AAAAAAAALxQ/ru3DD7Ziwb4bkGAFX1QuqjGhWXgXRQZQACLcB/s1600/2.%2BAppium%2BDesktop%2BSetup.png)
:::

\
\
\
\
platformName: Android\
\
deviceName: emulator-5554\
\
appPackage: io.appium.android.apis\
\
appActivity: .ApiDemos\
\
\

-   Select the \"Save As\...\" button, and save it as something such as
    \"ApiDemos\".

\... When we finally run automated tests, setting up Desired
Capabilities, we will find that instead of appPackage, and appActivity,
we can just use the appName. If we did that with Appium Desktop, like I
did in my first attempt, I would be hit by [a known bug in one of the
Android Command Line
Tools](http://www.tjmaher.com/2017/04/learning-appium-desktop-find-desired.html)
and it would not work.\
\
\
**[Step 7:]{.underline}** Press the [Start Session
button](http://www.tjmaher.com/2017/04/learning-appium-inspecting-app-with.html).
Three horizontal panels will appear.\
\

  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://2.bp.blogspot.com/-qWZlJE_MxTk/WRTWAcOq4jI/AAAAAAAALxU/QN5EjqvsKSMozmd7lZNxE_Qbl_63UblhACLcB/s640/3.%2BApi%2BDemos%2BPage.png){width="640" height="336"}](https://2.bp.blogspot.com/-qWZlJE_MxTk/WRTWAcOq4jI/AAAAAAAALxU/QN5EjqvsKSMozmd7lZNxE_Qbl_63UblhACLcB/s1600/3.%2BApi%2BDemos%2BPage.png)
                                                                                                                             *Now that Appium Desktop is up and running, Inspect away!*
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

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
Left panel: A reflection of the app or virtual device\
Middle panel: The app source, much like the DOM of a web page.\
Right Panel: The properties of the selected element.\
\
For example, if we select the API Demos area on the first screen that
pops up, you can see that:\
\

-   ID: android:id/action\_bar

\
Now that we have Appium Desktop and an Android emulator up and running,
tomorrow we will be inspecting the mobile elements of this app and
designing a basic test.\
\
Stop by tomorrow, and we [can examine the app to see what we can do for
a basic
test](http://www.tjmaher.com/2017/05/basic-appium-framework-part-one.html)\...\
\
\
\

<div>

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
