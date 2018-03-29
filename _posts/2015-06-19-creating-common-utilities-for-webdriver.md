\-\-- layout: post title: \'The-Internet: Common Utilities: methods,
exceptions and logging\' date: \'2015-06-19T19:38:00.001-04:00\' author:
T.J. Maher tags: - code examples - beginner - test framework - Dave
Haeffner modified\_time: \'2016-04-29T07:56:56.994-04:00\' blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-9081163430034408435
blogger\_orig\_url:
http://www.tjmaher.com/2015/06/creating-common-utilities-for-webdriver.html
\-\-- *This post is second in a series of six. Need to go [back to the
beginning](/2015/06/simple-manipulation-of-login-page.html)?*\
\
*Rewriting the automated test code we use at work to test against Dave
Haeffner\'s mock site, The-Internet: [Login
Page](https://the-internet.herokuapp.com/login).*\
*\
*\
Please note: I have been an automated tester only since March 2015. This
is only my best guess on how to translate what we use at work. I am
writing this blog to deepen my own understanding of automated testing.
If there are any glaring errors about Java, OO, WebDriver, or anything
else please let me know in the **Comments** section!\
\
[]{#more}\

**Part Two**: Drafting the Common Utilities Library
---------------------------------------------------

\
The Selenium WebDriver API provides the basic methods to manipulate a
brower to perform actions, such as navigating to a web page, but it
doesn\'t have all the functionality we would need. What if we wanted to
add in exception handling, such as if the web page was not found? What
if we wanted to throw a customized error to a log file when the page was
not found? What if, even upon a success, we wanted to write a message to
the log?\
\
A Common Utilities library, such as one they are using at the moment at
my workplace, can be developed to handle these cases. Each Selenium API
method is wrapped in try / catch / throw blocks for exception handling,
built-in with logging functionality. When things go wrong, clear and
concise error messages will save a lot of time debugging if the issue
was with the server, with the code of the site, or the tests
themselves.\
\
*If you want to skip ahead to see an example of a CommonUtils library,
you can view one
 at: [test/java/utils/CommonUtils.java](https://github.com/tjmaher/WebDriver_TheInternet_Advanced/blob/master/src/test/java/utils/CommonUtils.java),
which closely resembles the one drafted by the automation test team at
work.*\
\
For this project, we will test against **The-Internet**.\

### About The-Internet

\
Dave Haeffner wrote a test site called **The-Internet** (
<https://the-internet.herokuapp.com/> ) that entry level automated
testers could use to test against. For this blog post, I will be
examining his [Login Page](https://the-internet.herokuapp.com/login)
example. *If you want more information about Dave, you can [view my blog
entry about
him](http://adventuresinautomation.blogspot.com/2015/06/spotlight-on-dave-haeffner.html).*\

### 

### Automated Test Suite code to test The-Internet

\
To deepen my understanding of automation test suites, over the next
month or so I will be examining and rewriting code to test against
**The-Internet**. Feel free to follow along, make suggestions, and ask
questions about the code I am writing in the Comments section of this
blog! I have only been writing code on-the-job since March, so there are
bound to be errors of interpretation.\
\
All code I develop will be uploaded to my GitHub account at
<https://github.com/tjmaher>.\
\

<div>

-   **[WebDriver\_TheInternet\_Basics](https://github.com/tjmaher/WebDriver_TheInternet_Basics)**:
    Quick-and-dirty code to test the basics of **The-Internet** login
    page with SimpleManipulationWebElements.java 

<!-- -->

-   [**WebDriver\_TheInternet\_Advanced**:](https://github.com/tjmaher/WebDriver_TheInternet_Advanced) The
    beginnings of the test suite for **The-Internet**.

</div>

### Creating Methods to Navigate to a Web Page

Navigating to **The-Internet**\'s Login page is pretty simple with
WebDriver. All it takes is one driver.get statement in order to navigate
to the login page:\

``` {.brush: .javafx}
  
    driver.get("http://the-internet.herokuapp.com/login");
```

\
But what if you wanted to add functionality to write to the log console
every time you use WebDriver to navigate to a web page? This means you
would have to enter two lines of code per driver.get statement.\

``` {.brush: .javafx}
   
    System.out.println("Navigating to: http://the-internet.herokuapp.com/login");
    driver.get("http://the-internet.herokuapp.com/login");
```

\
Let\'s say you also wanted to add even more:\

-   Logging functionality when an action is performed
-   Catch any errors if the action failed
-   Throw an error to the logs detailing if an error ever happened
-   Document the Thread ID, useful when dealing with multithreaded
    systems that are running many Selenium WebDriver tests in parallel. 
-   Include any wait statements, if a page is known to be slow loading. 

\
To satisfy all these new requirements, at work they came up with the
following method for their CommonUtils
library, [navigateToURL]{style="font-family: "courier new" , "courier" , monospace;"}[:]{style="font-family: inherit;"}[ ]{style="font-family: "courier new" , "courier" , monospace;"}\
\

``` {.brush: .javafx}
  
     public void navigateToURL(String URL) {
        System.out.println("Navigating to: " + URL);
        System.out.println("Thread id = " + Thread.currentThread().getId());

        try {
            _driver.navigate().to(URL);
        } catch (Exception e) {
            System.out.println("URL did not load: " + URL);
            throw new TestException("URL did not load");
        }
     }
```

\
[To use this method, we can use this method in a test, passing in the
URL as a String:]{style="font-family: inherit;"}\
[\
]{style="font-family: inherit;"}[navigateToURL(\"http://the-internet.herokuapp.com/login\");]{style="font-family: "courier new" , "courier" , monospace;"}\
[\
]{style="font-family: inherit;"}[Now imagine if you had a whole library
where all the Selenium WebDriver functions are wrapped in try / catch /
throw blocks, logging functionality is added, threads have
identification numbers listed, and any optional wait statements are
included.]{style="font-family: inherit;"}\

### [Methods in the CommonUtils Library]{style="font-family: inherit;"}

[\
]{style="font-family: inherit;"}

\
[These are the methods in the CommonUtility we can
use:]{style="font-family: inherit;"}\
\

-   [[navigateToURL]{.pl-en
    style="background-color: white; box-sizing: border-box; line-height: 16.7999992370605px; white-space: pre;"}[(]{style="background-color: white; line-height: 16.7999992370605px; white-space: pre;"}[String]{.pl-smi
    style="background-color: white; box-sizing: border-box; line-height: 16.7999992370605px; white-space: pre;"}[
    ]{style="background-color: white; line-height: 16.7999992370605px; white-space: pre;"}[URL]{.pl-smi
    style="background-color: white; box-sizing: border-box; line-height: 16.7999992370605px; white-space: pre;"}[)]{style="background-color: white; line-height: 16.7999992370605px; white-space: pre;"}]{style="font-family: inherit;"}

<!-- -->

-   [[getPageTitle]{.pl-en
    style="box-sizing: border-box; line-height: 16.7999992370605px;"}[()]{style="line-height: 16.7999992370605px;"}]{style="background-color: white; font-family: inherit; line-height: 16.7999992370605px; white-space: pre;"}

<!-- -->

-   [[[getElement]{.pl-en
    style="box-sizing: border-box; line-height: 16.7999992370605px;"}[(]{style="line-height: 16.7999992370605px;"}[By]{.pl-smi
    style="box-sizing: border-box; line-height: 16.7999992370605px;"}[
    ]{style="line-height: 16.7999992370605px;"}[selector]{.pl-v
    style="box-sizing: border-box; line-height: 16.7999992370605px;"}[)]{style="line-height: 16.7999992370605px;"}]{style="font-family: inherit; line-height: 16.7999992370605px;"}]{style="background-color: white; line-height: 16.7999992370605px; white-space: pre;"}

<!-- -->

-   [[[[sendKeys]{.pl-en
    style="box-sizing: border-box; line-height: 16.7999992370605px;"}[(]{style="line-height: 16.7999992370605px;"}[By]{.pl-smi
    style="box-sizing: border-box; line-height: 16.7999992370605px;"}[
    ]{style="line-height: 16.7999992370605px;"}[selector]{.pl-v
    style="box-sizing: border-box; line-height: 16.7999992370605px;"}[,
    ]{style="line-height: 16.7999992370605px;"}[String]{.pl-smi
    style="box-sizing: border-box; line-height: 16.7999992370605px;"}[
    ]{style="line-height: 16.7999992370605px;"}[value]{.pl-v
    style="box-sizing: border-box; line-height: 16.7999992370605px;"}[)]{style="line-height: 16.7999992370605px;"}]{style="font-family: inherit; line-height: 16.7999992370605px;"}]{style="line-height: 16.7999992370605px;"}]{style="background-color: white; line-height: 16.7999992370605px; white-space: pre;"}

<!-- -->

-   [[[[[clearField]{.pl-en
    style="box-sizing: border-box; line-height: 16.7999992370605px;"}[(]{style="line-height: 16.7999992370605px;"}[WebElement]{.pl-smi
    style="box-sizing: border-box; line-height: 16.7999992370605px;"}[
    ]{style="line-height: 16.7999992370605px;"}[element]{.pl-v
    style="box-sizing: border-box; line-height: 16.7999992370605px;"}[)]{style="line-height: 16.7999992370605px;"}]{style="font-family: inherit; line-height: 16.7999992370605px;"}]{style="line-height: 16.7999992370605px;"}]{style="line-height: 16.7999992370605px;"}]{style="background-color: white; line-height: 16.7999992370605px; white-space: pre;"}

<!-- -->

-   [[[[[[click]{.pl-en
    style="box-sizing: border-box; line-height: 16.7999992370605px;"}[(]{style="line-height: 16.7999992370605px;"}[By]{.pl-smi
    style="box-sizing: border-box; line-height: 16.7999992370605px;"}[
    ]{style="line-height: 16.7999992370605px;"}[selector]{.pl-v
    style="box-sizing: border-box; line-height: 16.7999992370605px;"}[)]{style="line-height: 16.7999992370605px;"}]{style="font-family: inherit; line-height: 16.7999992370605px;"}]{style="line-height: 16.7999992370605px;"}]{style="line-height: 16.7999992370605px;"}]{style="line-height: 16.7999992370605px;"}]{style="background-color: white; line-height: 16.7999992370605px; white-space: pre;"}

<!-- -->

-   [[[[[[[waitForElementToBeClickable]{.pl-en
    style="box-sizing: border-box; line-height: 16.7999992370605px;"}[(]{style="line-height: 16.7999992370605px;"}[By]{.pl-smi
    style="box-sizing: border-box; line-height: 16.7999992370605px;"}[
    ]{style="line-height: 16.7999992370605px;"}[selector]{.pl-v
    style="box-sizing: border-box; line-height: 16.7999992370605px;"}[
    )]{style="line-height: 16.7999992370605px;"}]{style="font-family: inherit; line-height: 16.7999992370605px;"}]{style="line-height: 16.7999992370605px;"}]{style="line-height: 16.7999992370605px;"}]{style="line-height: 16.7999992370605px;"}]{style="line-height: 16.7999992370605px;"}]{style="background-color: white; line-height: 16.7999992370605px; white-space: pre;"}

<!-- -->

-   [[[[[[[[waitForElementToBeVisible]{.pl-en
    style="box-sizing: border-box; line-height: 16.7999992370605px;"}[(]{style="line-height: 16.7999992370605px;"}[By]{.pl-smi
    style="box-sizing: border-box; line-height: 16.7999992370605px;"}[
    ]{style="line-height: 16.7999992370605px;"}[selector]{.pl-v
    style="box-sizing: border-box; line-height: 16.7999992370605px;"}[)]{style="line-height: 16.7999992370605px;"}]{style="font-family: inherit; line-height: 16.7999992370605px;"}]{style="line-height: 16.7999992370605px;"}]{style="line-height: 16.7999992370605px;"}]{style="line-height: 16.7999992370605px;"}]{style="line-height: 16.7999992370605px;"}]{style="line-height: 16.7999992370605px;"}]{style="background-color: white; line-height: 16.7999992370605px; white-space: pre;"}

You can view all the methods
in: <https://github.com/tjmaher/WebDriver_TheInternet_Advanced/blob/master/src/test/java/utils/CommonUtils.java>\

### How to use the Methods:

\
Selectors can be found By Id or By CSS Selector. If we wanted to grab
the Username textbox, the Password textbox, or the Login button, we
could:\
\
\

-   Username: getElement(By.cssSelector(\"\[name=\'username\'\]\")
-   Password: getElement(By.cssSelector(\"\[name=\'password\'\]\")
-   Login Button:
    getElement(By.cssSelector(\"[\"\[type=\'submit\'\]\[class=\'radius\'\]\"]{style="background-color: white; color: green; font-family: "courier new"; font-size: 9pt; font-weight: bold;"}\")

\
\
\... And wherever these CommonUtils methods are used, we need to make
sure to:\
\

``` {style="background-color: white; font-family: 'Courier New';"}
import utils.CommonUtils;
```

**NEXT:** [Storing Constanst: public final vs
enums](/2015/07/how-java-stores-constants-static-final.html)\
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
of [Fitbit.com](http://www.fitbit.com/). *\
\
