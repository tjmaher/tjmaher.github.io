\-\-- layout: post title: \'Build a Basic Appium Framework: Design a
Basic Test, Examining Mobile Elements\' date:
\'2017-05-16T07:42:00.000-04:00\' author: T.J. Maher tags: - Java -
appium - Android modified\_time: \'2017-06-16T20:12:35.634-04:00\'
thumbnail:
https://2.bp.blogspot.com/-DGyLB0o4tL0/WRUpLwIIMdI/AAAAAAAALx8/n\_3vcpP\_UMYwamkIRK5p1tsjFhvBF9elACLcB/s72-c/1.%2BAPI%2BDemo%2BApp.png
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-4540003708113123447
blogger\_orig\_url:
http://www.tjmaher.com/2017/05/basic-appium-framework-part-two.html
\-\-- *This is part two of of a seven-part blog series. Care to go [back
to the
beginning](http://www.tjmaher.com/2017/05/basic-appium-framework-part-one.html)? *\
\
Last blog post, [we reviewed installation and
setup](http://www.tjmaher.com/2017/05/basic-appium-framework-part-one.html).
For this one, let\'s write a simple mobile automation test, for this
app, then investigate all mobile elements involved, with Appium
Desktop.\
\

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://2.bp.blogspot.com/-DGyLB0o4tL0/WRUpLwIIMdI/AAAAAAAALx8/n_3vcpP_UMYwamkIRK5p1tsjFhvBF9elACLcB/s640/1.%2BAPI%2BDemo%2BApp.png){width="388" height="640"}](https://2.bp.blogspot.com/-DGyLB0o4tL0/WRUpLwIIMdI/AAAAAAAALx8/n_3vcpP_UMYwamkIRK5p1tsjFhvBF9elACLcB/s1600/1.%2BAPI%2BDemo%2BApp.png)
                                                                                                                              The app we will be testing, ***ApiDemos-debug.apk***
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

\
**Our Basic Test:**\

-   Fire up the app, make sure the title on the first screen says "API
    Demos"
-   Select the "Text" button. Make sure that "LogTextBox" appears as an
    option.
-   Select "LogTextBox". Make sure that the "Text/LogTextBox" header
    appears.
-   Select the ADD button.
-   Assert that the words "This is a test" appears in the panel.

\
[]{#more}\
\

### What to Call the Pages?

<div>

\
When we fire up the application, we are greeted by a screen called \"API
Demos\". Would that be a good name for this page?\
\
Probably not. If you tap on the Text menu item, it is also called \"API
Demos\". Hrm\... how to tell the two pages apart? How about we call the
first page, the **Home Screen Page**, and the second page, the **Inner
API Demos Page**?\
\
After selecting the LogTextBox menu item, we are taken to a page titled
\"Text/LogTextBox\". Let\'s call it the \"**Log TextBox**\" page.\
\
Each and every page we interact will be treated as its own Java object
for easy reference. This is called the Page Object Model.\
\

### What is the Page Object Model?

\
*\"When you write tests against a web page, you need to refer to
elements within that web page in order to click links and determine
what\'s displayed. However, if you write tests that manipulate the HTML
elements directly your tests will be brittle to changes in the UI. A
page object wraps an HTML page, or fragment, with an
application-specific API, allowing you to manipulate page elements
without digging around in the HTML \[\...\]*

</div>

\
*\"Despite the term \'page\' object, these objects shouldn\'t usually be
built for each page, but rather for the significant elements on a page
[\[1\]](https://martinfowler.com/bliki/PageObject.html#footnote-panel-object).
So a page showing multiple albums would have an album list page object
containing several album page objects. There would probably also be a
header page object and a footer page object. That said, some of the
hierarchy of a complex UI is only there in order to structure the UI -
such composite structures shouldn\'t be revealed by the page objects.
The rule of thumb is to model the structure in the page that makes sense
to the user of the application\". - [MartinFowler.com, Page
Object](https://martinfowler.com/bliki/PageObject.html), Sept 2013*\

<div>

*\
*

</div>

<div>

###  **Home Screen Page**

</div>

<div>

We get to this page by launching the app, then investigating the action
bar \"API Demo\".\
\

</div>

<div>

Remember that the leftmost panel is a reflection mirroring what is on
the app. If you fire up the app, the first page (which we are dubbing
the \"Home Screen Page\") is displayed. Is it not showing up in Appium
Desktop? Select the \"Refresh\" button. 

</div>

<div>

-   Select the action bar, \"API Demos\" to see how we could select that
    mobile element. 

</div>

<div>

\

</div>

  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://3.bp.blogspot.com/-xLmHduyp3ag/WRTXb4qXRHI/AAAAAAAALxY/yjjRpMdBRwUQuXZcETlpNS_qyHQKHeeBQCLcB/s640/3.%2BApi%2BDemos%2BPage.png){width="640" height="336"}](https://3.bp.blogspot.com/-xLmHduyp3ag/WRTXb4qXRHI/AAAAAAAALxY/yjjRpMdBRwUQuXZcETlpNS_qyHQKHeeBQCLcB/s1600/3.%2BApi%2BDemos%2BPage.png)

                                                                                                                                                         \
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

\
\
\
\
\
\
\
\
Properties of the **Action Bar**:\

-   Find By: ID 
-   Selector: android:id/action\_bar. 
-   Header Text is "API Demos". 

\
Properties of the **Text** menu item:\
\
[![](https://1.bp.blogspot.com/-vLnNchxZcy4/WRTXjawCpTI/AAAAAAAALxc/tNXusxKJdIICog-TjUKwQlEvTc4XwzqqQCEw/s640/4.%2BText%2BButton.png)](https://1.bp.blogspot.com/-vLnNchxZcy4/WRTXjawCpTI/AAAAAAAALxc/tNXusxKJdIICog-TjUKwQlEvTc4XwzqqQCEw/s1600/4.%2BText%2BButton.png)\
\

-   Accessibility ID is "Text". 
-   Note that the properties of the button, Clickable: "True". If this
    button had the property clickable: "false", we could not use the
    button.click() property on it. We might have to figure out what the
    boundaries are inside the button and perform an Appium command:
    *driver.tap*. 

<div>

###  Inner Api Demos Page

</div>

We get to this page after launching the app:\

<div>

-   API Demos -\> Selecting Text button -\> Investigating LogTextButton

</div>

<div>

\
[![](https://3.bp.blogspot.com/-dWVZPLA2ZYo/WRTXwtvD8mI/AAAAAAAALxg/2w8JwZYYG6chDF-78V_nHuYoi_yxwrmowCLcB/s640/5.%2BLogTextBox.png)](https://3.bp.blogspot.com/-dWVZPLA2ZYo/WRTXwtvD8mI/AAAAAAAALxg/2w8JwZYYG6chDF-78V_nHuYoi_yxwrmowCLcB/s1600/5.%2BLogTextBox.png)\

<div>

\
\

-   Header selector: android:id/action\_bar. 
-   Text Button: LogTextBox. Note that the accessibility id: LogTextBox,
    and the property of Clickable: "True".

\

### LogTextBox Page

We get to this page by:\

<div>

-   API Demos -\> Selecting the Text Button -\>Selecting  the
    LoginTextBox button

</div>

\
[![](https://2.bp.blogspot.com/-ljC1FphSw3I/WRTYIvIAjJI/AAAAAAAALxo/c-EDaxhomIA702e15Za2q4ktUp_6kMtNACLcB/s640/6.%2BText%2BArea.png){width="640"
height="368"}](https://2.bp.blogspot.com/-ljC1FphSw3I/WRTYIvIAjJI/AAAAAAAALxo/c-EDaxhomIA702e15Za2q4ktUp_6kMtNACLcB/s1600/6.%2BText%2BArea.png)\
\
\
\
Header: id: android:id/action\_bar\
\
ADD button: id = accesibility = \"Add\"\
\
The panel is id = \"io.appium.android.apis:id/text\".\
\
We have all we need!\
\

-   A basic test case that tells us how to traverse the site! 
-   A way to interact with the mobile elements! 

Ready to start coding up our automated test?\
\
\... One more thing we need to cover: How the heck do we launch an app
on our emulator using Appium?\
\
[Come back here
tomorrow](http://www.tjmaher.com/2017/05/build-basic-appium-framework-install.html)
to find out!\
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

<div>

\

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

</div>

</div>
