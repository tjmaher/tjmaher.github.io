\-\-- layout: post title: \'The-Internet: Simple Manipulation of a Login
Page\' date: \'2015-06-12T00:17:00.003-04:00\' author: T.J. Maher tags:
- code examples - beginner - test framework - Login - Dave Haeffner
modified\_time: \'2016-04-29T07:57:34.418-04:00\' thumbnail:
https://1.bp.blogspot.com/-HaIntSdGA7g/VXj4pPUCthI/AAAAAAAAKlo/w29MLJha9Ec/s72-c/login.png
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-7077168503793851630
blogger\_orig\_url:
http://www.tjmaher.com/2015/06/simple-manipulation-of-login-page.html
\-\-- Beginning coders in Selenium WebDriver need simple websites to
test against. For that purpose, Dave Haeffner
( [\@TourDeDave](https://twitter.com/TourDeDave) ), author
of [ElementalSelenium.com](http://elementalselenium.com/) and
the [SeleniumGuidebook.com](http://seleniumguidebook.com/), wrote
the-internet.\
\
\... No, not \"The Internet\".
The-Internet: <https://the-internet.herokuapp.com/>. It assembles a
collection of Web Elements such as dropdowns, checkboxes, and a login
page that automated testers can test against.\
\
For today\'s blog post, I will speed automated testers through some
basic Selenium / Java sample code I quickly hacked together: how a
tester can interact with the various page elements of a login screen.
The code tests what needs to be tested, it successfully runs\... but it
ain\'t pretty.\
\
[]{#more}\
\
After the basics are covered, with the next blog post I will get to the
topic that I actually wanted to talk about: Refactoring the code to fit
 some of the style they use at Fitbit-Boston\'s automation department
\-- storing locator variables in Enums, storing methods interacting with
the DOM in Page Object Classes, and inserting Utility classes that add
logging functionality.\
\

### Setting Up the Development Environment

\
If you are curious to know the setup I have been using at Fitbit-Boston
for the past three months to write automated tests, and what I use on my
home system:\
\

-   **Platform and Operating System**: Macbook Pro at work. Home:
    Windows 7.
-   **Integrated Development
    Environment** (IDE):[ IntelliJ](https://www.jetbrains.com/idea/).
    Although we use the Enterprise Edition at work, the only difference
    between that and the free Community version is extra features for
    database integration.  
-   **Test Framework**: We use [TestNG](http://testng.org/) at work. At
    home I can experiment writing tests in [JUnit](http://junit.org/) on
    my home system, bring the code to work, swap the importing of JUnit
    to the importing of TestNG and it works fine. 
-   **Dependencies Management**: Even though at work we
    use [Gradle](https://gradle.org/), and at home I
    use [Maven](https://maven.apache.org/), I really haven\'t seen many
    differences. I don\'t interact with either of them on a daily
    basis. 
-   **Browsers**: Both at work and at home to inspect page elements, I
    use the [Firefox
    browser](https://www.mozilla.org/) plugins [Firebug](http://getfirebug.com/) and [Firepath](https://addons.mozilla.org/eN-US/firefox/addon/firepath/) to
    examine the web document. Even though Fitbit tests its site in
    Chrome, Firefox and IE8, for this rudimentary example of Selenium
    code, I will be just sticking with Firefox since that is the
    standard Selenium WebDriver browser included with WebDriver.

\
\
If you need help getting IntelliJ, setting up Maven, setting up
your *pom.xml* file or JUnit, or installing Firefox, Firebug or
Firepath, there is a free introduction on Alan Richardson\'s
page, **Start Using Selenium
WebDriver** at <http://seleniumsimplified.com/get-started/>.\
\
If you are looking for more material, Alan Richardson has an extensive
course on **Selenium 2 WebDriver with
Java** at <http://courses.compendiumdev.co.uk/courses/selenium-2-webdriver-with-java> which
helped me immensely preparing for my current position.\
\
Make sure to go to the official **SeleniumHQ** site
at <http://docs.seleniumhq.org/docs/> or visit their new documentation
that is still in progress at <https://seleniumhq.github.io/docs/>.\
\

### Examining the Login Page

\
If you go to The-Internet\'s login page
at <http://the-internet.herokuapp.com/login>, the following screen is
shown:\
\

  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  [![](https://1.bp.blogspot.com/-HaIntSdGA7g/VXj4pPUCthI/AAAAAAAAKlo/w29MLJha9Ec/s400/login.png){width="400" height="322"}](http://1.bp.blogspot.com/-HaIntSdGA7g/VXj4pPUCthI/AAAAAAAAKlo/w29MLJha9Ec/s1600/login.png)
  <http://the-internet.herokuapp.com/login>
  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

The title of the page is called \"The Internet\".\
\
Note that according to the description of the Login page:\
\

-   username = \"tomsmith\"
-   password = \"SuperSecretPassword!\"

When you enter the username and password into the correct textboxes, and
select the Login button, you are taken to the next page.\
\
The next page, <http://the-internet.herokuapp.com/secure>, is also
called \"The Internet\". If you click on the Logout button on that page,
you are successfully logged out. \
\

### Inspecting the Web Elements

\
If you have the Firefox plugins Firebug and Firepath installed, if you
select the username textbox, right click on it, and select \"Inspect in
Firepath\", you will see the properties of the web element you selected.
You can let Selenium WebDriver know what web element you are choosing by
these selectors.\
\
**Username textbox**:\
[\
]{style="font-family: "courier new" , "courier" , monospace; text-align: center;"}[\<]{style="font-family: "courier new" , "courier" , monospace; text-align: center;"}[input]{.nodeTag
style="font-family: "courier new" , "courier" , monospace; text-align: center;"}[ [id]{.nodeName}=\"[username]{.nodeValue}\"]{.nodeAttr
style="font-family: "courier new" , "courier" , monospace; text-align: center;"}[ [type]{.nodeName}=\"[text]{.nodeValue}\"]{.nodeAttr
style="font-family: "courier new" , "courier" , monospace; text-align: center;"}[ [name]{.nodeName}=\"[username]{.nodeValue}\"]{.nodeAttr
style="font-family: "courier new" , "courier" , monospace; text-align: center;"}[/\>]{.nodeBracket
.insertBefore
style="font-family: "courier new" , "courier" , monospace; text-align: center;"}\

::: {.panelNode .panelNode-firepath .contextUID=7 active="true"}
::: {.io-box-container}
::: {.nodeBox .emptyNodeBox .repIgnore}
[[\
]{style="font-family: "courier new" , "courier" , monospace;"}]{.nodeLabelBox
.repTarget}[\... For a selector, WebDriver can select for this web
element by the id called \"username\". ]{style="font-family: inherit;"}\
[\
]{style="font-family: inherit;"}[**Password
textbox:**]{style="font-family: inherit;"}\
[\
]{style="font-family: "courier new" , "courier" , monospace; text-align: center;"}[\<]{style="font-family: "courier new" , "courier" , monospace; text-align: center;"}[input]{.nodeTag
style="font-family: "courier new" , "courier" , monospace; text-align: center;"}[ [id]{.nodeName}=\"[password]{.nodeValue}\"]{.nodeAttr
style="font-family: "courier new" , "courier" , monospace; text-align: center;"}[ [type]{.nodeName}=\"[text]{.nodeValue}\"]{.nodeAttr
style="font-family: "courier new" , "courier" , monospace; text-align: center;"}[ [name]{.nodeName}=\"[password]{.nodeValue}\"]{.nodeAttr
style="font-family: "courier new" , "courier" , monospace; text-align: center;"}[/\>]{.nodeBracket
.insertBefore
style="font-family: "courier new" , "courier" , monospace; text-align: center;"}
:::
:::
:::

\
\
\... For a selector, WebDriver can select for this web element by the id
called \"password\". 

<div>

\

</div>

<div>

**Login button**:

</div>

<div>

\

</div>

<div>

Finding a selector for this web element is trickier. If you right click
on the Login button and \"Inspect in Firepath\" you see:

</div>

<div>

\

</div>

::: {.separator style="clear: both; text-align: center;"}
[![](https://3.bp.blogspot.com/-x9CrIlQdlxI/VXkBZEPMtQI/AAAAAAAAKl8/DufuqnvQtX8/s400/login_firepath.png){width="400"
height="366"}](http://3.bp.blogspot.com/-x9CrIlQdlxI/VXkBZEPMtQI/AAAAAAAAKl8/DufuqnvQtX8/s1600/login_firepath.png)
:::

::: {.separator style="clear: both; text-align: center;"}
[\
]{style="font-family: "courier new" , "courier" , monospace;"}
:::

::: {.separator style="clear: both; text-align: center;"}
[\
]{style="font-family: "courier new" , "courier" , monospace;"}
:::

::: {.separator style="clear: both; text-align: center;"}
[\<]{style="font-family: "courier new" , "courier" , monospace;"}[button]{.nodeTag
style="font-family: "courier new" , "courier" , monospace;"}[ [class]{.nodeName}=\"[radius]{.nodeValue}\"]{.nodeAttr
style="font-family: "courier new" , "courier" , monospace;"}[ [type]{.nodeName}=\"[submit]{.nodeValue}\"]{.nodeAttr
style="font-family: "courier new" , "courier" , monospace;"}[\>]{.nodeBracket
.insertBefore
style="font-family: "courier new" , "courier" , monospace;"}
:::

::: {.panelNode .panelNode-firepath .contextUID=7 active="true"}
::: {.io-box-container}
::: {.nodeBox .containerNodeBox .repIgnore}
::: {.nodeLabel style="text-align: center;"}
\

::: {style="text-align: left;"}
\... With this element, you cannot select by id, since an id is not
given. You can select by ***CSS Selector***, which I mention [in an
earlier blog
post](http://adventuresinautomation.blogspot.com/2015/04/how-selenium-webdriver-uses-css.html).
 
:::
:::

::: {.nodeLabel}
\
:::

::: {.nodeLabel}
If you select the FirePath tab, and select the CSS dropdown, entering
the following code into the CSS textbox in FirePath and selecting
\"Enter\" should have the Login button outlined:
:::

::: {.nodeLabel}
\
:::

::: {.nodeLabel}
``` {style="background-color: white; font-family: 'Courier New'; font-size: 9pt; text-align: center;"}
[type='submit'][class='radius']
```
:::

::: {.nodeLabel}
[\
]{.nodeLabelBox .repTarget}
:::

::: {.nodeLabel}
[You have just validated that using the above CSS Selector will select
the Login button. ]{.nodeLabelBox .repTarget}
:::

### [Writing the Test in Selenium / Java]{.nodeLabelBox .repTarget}

::: {.nodeLabel}
[\
]{.nodeLabelBox .repTarget}[Now that we examined the pages, mapping out
the workflow, and figured out how to select the web elements *by
id* and *by css selector*, we can begin writing the
test. ]{.nodeLabelBox .repTarget}\
[\
]{.nodeLabelBox .repTarget}
:::

::: {.nodeLabel}
[To make the test more readable, I separated the driver instantiation in
the [setUp()]{style="font-family: "courier new" , "courier" , monospace;"} method,
the actual test
in [test\_Login()]{style="font-family: "courier new" , "courier" , monospace;"},
and closing and quitting the browser in
a [tearDown()]{style="font-family: "courier new" , "courier" , monospace;"}method.
For those three methods, I used JUnit to tag what I wanted to run
\@Before the test, what was the actual \@Test and what I was going to be
running \@After the test. ]{.nodeLabelBox .repTarget}\
[\
]{.nodeLabelBox .repTarget}[\
]{.nodeLabelBox .repTarget}[\
]{.nodeLabelBox .repTarget}[\
]{.nodeLabelBox .repTarget}
:::

\

::: {.nodeLabel}
[\
]{.nodeLabelBox .repTarget}
:::

::: {.nodeLabel}
[For even more readability, I added logging functionality by capturing
information in ]{.nodeLabelBox
.repTarget}[System.]{style="background-color: white; font-family: "courier new"; font-size: 9pt;"}[out]{style="color: #660e7a; font-family: "courier new"; font-size: 9pt; font-style: italic; font-weight: bold;"}[.println(\"\...\") ]{style="background-color: white; font-family: "courier new"; font-size: 9pt;"}statements.
:::

::: {.nodeLabel}
\
:::

::: {.nodeLabel}
Just in case there were any synchronization errors, if any page elements
were slow to load, a few wait statements were added.\
\

### Console Output

\
The following text is outputted to the console, suitable for a Jenkins
log file:\
\
[\"C:\\Program
Files\\Java\\jdk1.8.0\_40\\bin\\java\"]{style="font-family: "courier new" , "courier" , monospace;"}\
[Navigating to:
http://the-internet.herokuapp.com/login]{style="font-family: "courier new" , "courier" , monospace;"}\
[Waiting for page to
load\...]{style="font-family: "courier new" , "courier" , monospace;"}\
[The title of the page is: The
Internet]{style="font-family: "courier new" , "courier" , monospace;"}\
[Entering
username\...]{style="font-family: "courier new" , "courier" , monospace;"}\
[Entering
password\...]{style="font-family: "courier new" , "courier" , monospace;"}\
[Selecting the submit
button.]{style="font-family: "courier new" , "courier" , monospace;"}\
[Waiting for page to
load\...]{style="font-family: "courier new" , "courier" , monospace;"}\
[The title of the page is: The
Internet]{style="font-family: "courier new" , "courier" , monospace;"}\
[The current url is:
http://the-internet.herokuapp.com/secure]{style="font-family: "courier new" , "courier" , monospace;"}\
[Waiting for logout button to
load\...]{style="font-family: "courier new" , "courier" , monospace;"}\
[Selecting the logout
button.]{style="font-family: "courier new" , "courier" , monospace;"}\
\

### Problems with this Approach:

There are many problems with this iterative approach:\
\

-   You have the tests themselves, the Selenium code that interacts with
    the DOM, and the logging functionality all jumbled up together.
-   The code handling the Login Page and the code handling the Secure
    page are also jumbled together.
-   All of this code is just to select web elements and navigate through
    just two pages. What happens if the selectors for the page elements
    change? You would have to scan the entire codebase, make changes,
    and hope that you covered all the instances of that web element. 
-   What if the test changes? How can you add or subtract from the tests
    if you don\'t know where exactly they are?

\

### Next Steps

\
With my next post, I will discuss refactoring this into something a bit
more professional looking, more in line with what we use at Fitbit.\
\
Please note: I have been an automated tester only since March 2015. This
is only my best guess on how to translate what we use at work. I am
writing this blog to deepen my own understanding of automated testing.
If there are any glaring errors about Java, OO, WebDriver, or anything
else please let me know in the **Comments** section!\
:::

**NEXT:** [Drafting Common
Utilities](/2015/06/creating-common-utilities-for-webdriver.html)\
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
// Automated tester for \[ 3 \] month and counting!*\
*\
Please note: \'Adventures in Automation\' is a personal blog about
automated testing. It is not an official blog
of [Fitbit.com](http://www.fitbit.com/). *
:::
:::
:::
