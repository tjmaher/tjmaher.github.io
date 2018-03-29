\-\-- layout: post title: \'The-Internet: Writing the Automated Test\'
date: \'2015-07-29T00:57:00.000-04:00\' author: T.J. Maher tags: - code
examples - beginner - Page Object - test framework - Dave Haeffner
modified\_time: \'2016-04-29T19:57:54.342-04:00\' thumbnail:
https://4.bp.blogspot.com/-HaIntSdGA7g/VXj4pPUCthI/AAAAAAAAKls/lWJrC8dz1K8/s72-c/login.png
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-2020940994985996581
blogger\_orig\_url:
http://www.tjmaher.com/2015/07/the-internet-writing-automated-test.html
\-\-- *Writing automated test code to test against Dave Haeffner\'s mock
site, The-Internet: [Login
Page](https://the-internet.herokuapp.com/login).*\
\
*This post is second in a series of six. Need to go [back to the
beginning](/2015/06/simple-manipulation-of-login-page.html)?*\
\
We have covered a lot of ground in this series of blog posts.\
\
The sixth and final part, writing the automated test, is kind of
anti-climactic after all that effort.\
\
[]{#more}\
\
**[LoginTest.java]{.underline}**\
\

Now that we have encapsulated the web elements in the page objects, most
of the web document and logging in common utilities, and locators in
enums, we have a test that is quite readable. You can see what page the
test interacts with, and by using descriptive method names, you can
guess what actions will be taken before the Firefox browser ever opens
up the Login page.\
\
\

  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://4.bp.blogspot.com/-HaIntSdGA7g/VXj4pPUCthI/AAAAAAAAKls/lWJrC8dz1K8/s320/login.png){width="320" height="258"}](http://4.bp.blogspot.com/-HaIntSdGA7g/VXj4pPUCthI/AAAAAAAAKls/lWJrC8dz1K8/s1600/login.png)
                                                                                               Welcome to **The-Internet**!
  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

When you kick off the test:\

-   A new Firefox browser window opens up, if there wasn\'t one open
    already. 
-   The automated test navigates to the login
    page: https://the-internet.herokuapp.com/login
-   The automated test asserts that the header text appears.
-   etc, etc.

<div>

A very important part is what gets written to the logs. Descriptive text
detailing what section the test is in and what it is doing is very
important, especially when the test failed and you need to quickly
diagnose what when wrong. Was it a problem with the new test you added?
Is it a problem with the server? Or is it a real, honest to goodness
problem with the web application itself? 

</div>

<div>

\

</div>

<div>

Well written logs are quite important, indeed! 

</div>

<div>

\
**Recap**:

</div>

<div>

-   **Part One**: We sketched out the [simple manipulation of a login
    page](http://www.tjmaher.com/2015/06/simple-manipulation-of-login-page.html) using
    the login page provided by Dave Haeffner and his test site. 
-   **Part Two**: We began drafting [a set of common
    utilities](http://www.tjmaher.com/2015/06/creating-common-utilities-for-webdriver.html),
    refactoring the initial code, modelling it on what my workplace
    currently uses. 
-   **Part Three**: We talked about the different ways of storing
    constants: [public final vs
    enums](http://www.tjmaher.com/2015/07/how-java-stores-constants-static-final.html). 
-   **Part Four**: We talked about storing [locators in
    enums](http://www.tjmaher.com/2015/07/storing-locators-for-web-elements.html). 
-   **Part Five**: We talked briefly about the [Page Object Design
    Pattern](http://www.tjmaher.com/2015/07/the-internet-page-object-model-examples.html). 

</div>

\

<div>

\

</div>

<div>

### What these blog posts didn\'t cover

</div>

<div>

There are many topics in the code that I didn\'t cover in these six blog
posts about \"Testing The-Internet\". Most of the topics I did not cover
because, well, I am still quite new at being an automated tester. I\'ve
only been allocated at 100% to the automation department a bit less than
the past two months. I have imitated the style of some of the following
items that we use at work without fully understanding them, so I am not
sure if I have mimicked them correctly. Know of a better way to do
things? Let me know in the **Comments**!\
\
**[Structuring the Automated Test Suite:]{.underline}**\
\
Is this the best way to structure the test suite? Is there a better way?
Who knows! But this is how I did it in
[**WebDriver\_TheInternet\_Advanced**](https://github.com/tjmaher/WebDriver_TheInternet_Advanced/tree/master/src/test/java),
which you can access on my GitHub account.\
\
Below is the folder structure I used, imitating what we use at work. The
Java classes are linked back to the sample source code I come up for
these introductory examples, hosted on Github.com.\
\
**base:**\
==\>
[DriverFactory.java](https://github.com/tjmaher/WebDriver_TheInternet_Advanced/blob/master/src/test/java/base/DriverFactory.java)\
\
**enums:**\
==\>
[PageHeaderEnums.java](https://github.com/tjmaher/WebDriver_TheInternet_Advanced/blob/master/src/test/java/enums/PageHeaderEnum.java)\
==\>
[UserEnums.java](https://github.com/tjmaher/WebDriver_TheInternet_Advanced/blob/master/src/test/java/enums/UserEnum.java)\
\
**interfaces:**\
==\>
[ISelector.java](https://github.com/tjmaher/WebDriver_TheInternet_Advanced/blob/master/src/test/java/interfaces/ISelector.java)\
\
**pages:**\
==\>
[LoginPage.java](https://github.com/tjmaher/WebDriver_TheInternet_Advanced/blob/master/src/test/java/pages/LoginPage.java)\
==\>
[SecureArea.java](https://github.com/tjmaher/WebDriver_TheInternet_Advanced/blob/master/src/test/java/pages/SecureArea.java)\
\
**tests:**\
==\>[LoginTest.java](https://github.com/tjmaher/WebDriver_TheInternet_Advanced/blob/master/src/test/java/tests/LoginTest.java)\
\
**utils:**\
==\>
[CommonUtils.java](https://github.com/tjmaher/WebDriver_TheInternet_Advanced/blob/master/src/test/java/utils/CommonUtils.java)\
==\>
[DriverUtils.java](https://github.com/tjmaher/WebDriver_TheInternet_Advanced/blob/master/src/test/java/utils/DriverUtils.java)\
\
**[\
]{.underline}[\
]{.underline}[Base.DriverFactory.java]{.underline}**\
\
This is an example of me imitating something I have seen at work but
still don\'t fully understand, mostly because I am still new to software
development design patterns, and I am still unsure of the [Factory
Design
pattern](https://en.wikipedia.org/wiki/Factory_(object-oriented_programming)).\
\
The *factory method* is an object that creates other objects. By
instantiating this class in your test and passing a driver to it with
the following code:\
\

> *DriverFactory df = new DriverFactory(DriverUtils.getDriver());*

\
\... You are also creating an new instance of the LoginPage object and
SecureArea object. This means that to call a page object and use a
method, you just need to add the variable *df* as a prefix.\

> *df.login.navigateToLoginPage();* 

> *df.secure.logOutOfSecureArea();*

</div>

**[\
]{.underline}[\
]{.underline}[Utils.DriverUtils.java]{.underline}**\
\
At my workplace, this utility class contains a lot of material I didn\'t
need for this simple example:\
\

-   **Desired Capabilities:** For this example, we are only using
    Firefox. I didn\'t need to set up a separate Firefox profile,
    Chromebrowser, Internet Explorer, Android, or Phantom JS. We also
    didn\'t need to set any ChromeOptions.
-   **Selenium Grid**: Since we aren\'t running this test in parallel
    with other tests, we didn\'t need to set up Selenium Grid, or set up
    and start a RemoteWebDriver. 
-   **SauceLabs**: Since we aren\'t using SauceLabs to outsource our
    Selenium Grid, we didn\'t need any methods for getting or setting a
    Sauce session.
-   **TestRail**: These tests are not data driven, so we don\'t need to
    get the value populating a \"Browser\" dropdown in TestRail, setting
    the capabilities. 

<div>

\

</div>

<div>

\... Quite frankly, I am not sure I even set up
[DriverUtils](https://github.com/tjmaher/WebDriver_TheInternet_Advanced/blob/master/src/test/java/utils/DriverUtils.java)
up correctly. All I know is that it seems to open a browser, go to the
right page, and tear down the browser correctly. 

</div>

<div>

\

</div>

<div>

I hope you had as much fun reading about what I have picked up in the
past two months as an automated tester as I have with writing about it!\
\
\

::: {#toc-section .toc-section}
**Testing The-Internet:**

-   **Part One:** [Sketching out the simple manipulation of a login
    page](/2015/06/simple-manipulation-of-login-page.html)
-   **Part Two:** [Drafting Common
    Utilities](/2015/06/creating-common-utilities-for-webdriver.html)
-   **Part Three:** [Storing Constanst: public final vs
    enums](/2015/07/how-java-stores-constants-static-final.html)
-   **Part Four:** [Storing locators in
    enums](/2015/07/storing-locators-for-web-elements.html)
-   **Part Five:** [Page Object
    Model](/2015/07/the-internet-page-object-model-examples.html)
-   **Part Six:** [Writing the Automated
    Test](/2015/07/the-internet-writing-automated-test.html)
-   **Source Code:** [GitHub, T.J.
    Maher](https://github.com/tjmaher/WebDriver_TheInternet_Advanced)
:::

\
\
-T.J. Maher\
* Sr. QA Engineer, Fitbit*\
* Boston, MA*\
*\
// Automated tester for \[ 4 \] month and counting!*\
*\
Please note: \'Adventures in Automation\' is a personal blog about
automated testing. It is not an official blog
of [Fitbit.com](http://www.fitbit.com/). *

</div>

\

<div>

</div>
