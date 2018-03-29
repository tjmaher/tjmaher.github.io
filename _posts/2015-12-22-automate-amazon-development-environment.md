\-\-- layout: post title: \'Automate Amazon: Development Environment
Setup\' date: \'2015-12-22T07:45:00.000-05:00\' author: T.J. Maher tags:
- code examples - Java - setup - WebDriver - test framework
modified\_time: \'2016-04-29T07:48:07.454-04:00\' blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-3298705480400932541
blogger\_orig\_url:
http://www.tjmaher.com/2015/12/automate-amazon-development-environment.html
\-\-- *This post is first in a series of nine.*\
\
Back in June 2015, I blogged about how I would write automated tests vs
Dave Haeffner\'s site,
\"[The-Internet](/2015/06/simple-manipulation-of-login-page.html)\".\
\
For this second project, I picked a more difficult site to automate:
Puchasing an order on Amazon.com\'s site.\
\
[]{#more}\
\
*Please note*: I haven\'t been doing automation on-the-job for very
long. I have less than a year\'s worth of experience developing
automated tests in Selenium WebDriver. Please don\'t take anything that
I am doing as the industry standard.\
\
\
If you do have knowledge of the industry standard of automated testing,
please feel free to correct me! I will be eagerly monitoring the
comments section for any advice or wisdom.\
\

### Setting Up the Development Environment

\
For this project I am using:\

-   **Platform and Operating System**: Windows 10.
-   **Integrated Development
    Environment** (IDE):[ IntelliJ](https://www.jetbrains.com/idea/).
    Although we use the Enterprise Edition at work, the only difference
    between that and the free Community version is extra features for
    database integration.  
-   **Test Framework**: [TestNG](http://testng.org/). It is built into
    the latest version of IntelliJ, but you still need to set up the
    dependencies in your pom.xml file.
-   **Dependencies Management**: Even though at work we
    use [Gradle](https://gradle.org/), for this project I am
    using [Maven](https://maven.apache.org/) to add Selenium WebDriver
    and TestNG as dependencies. 
-   **Browsers**: Both at work and at home to inspect page elements, I
    use the [Firefox
    browser](https://www.mozilla.org/) plugins [Firebug](http://getfirebug.com/) and [Firepath](https://addons.mozilla.org/eN-US/firefox/addon/firepath/) to
    examine the web document.

\
If you need help getting IntelliJ, setting up Maven, setting up
your *pom.xml* file or TestNG, or installing Firefox, Firebug or
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
If it helps, below is a sample of my POM.xml file.\
\

``` {style="background-color: white; font-family: 'Courier New'; font-size: 9pt;"}
<?xml version="1.0" encoding="UTF-8"?><project xmlns="http://maven.apache.org/POM/4.0.0"         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.tjmaher.selenium</groupId>
    <artifactId>com.tjmaher.selenium</artifactId>
    <version>1.0-SNAPSHOT</version>
    <dependencies>
        <dependency>
            <groupId>org.seleniumhq.selenium</groupId>
            <artifactId>selenium-java</artifactId>
            <version>2.48.2</version>
        </dependency>
        <dependency>
            <groupId>org.testng</groupId>
            <artifactId>testng</artifactId>
            <version>6.1.1</version>
        </dependency>
    </dependencies>

</project>
```

###   Run Your First Test

Let\'s name the test class **PurchaseOrderTest.java**.\
\
The \@BeforeClass method contains the setUp information that launches
the browser.\
The \@AfterClass method contains the tearDown information that closes
the browser.\
\
They will be executed respectively before the class PurchaseOrderTest,
then after the class is done.\
\

<div>

\

</div>

<div>

\

</div>

\

\
When you run PurchaseOrderTest:\
\

-   The Firefox browser opens up
-   It navigates to Amazon.com
-   The Firefox browser closes.

\
\
\

<div>

Now that we know that tests can be run, with the next installment of
this blog, we can sketch out a quick test.\
\

</div>

<div>

\
**NEXT**: [Sketch Out a Use Case
\>\>](/2015/12/automate-amazon-sketch-out-use-case.html)\
\

</div>

[-T.J.
Maher]{style="background-color: white; color: #222222; font-family: "calibri"; font-size: 15.4px; line-height: 21.56px;"}\
* Sr. QA Engineer, Fitbit*\
* Boston, MA*\
*\
// Automated tester for \[ 8 \] month and counting!*\
*\
Please note: \'Adventures in Automation\' is a personal blog about
automated testing. It is not an official blog
of [Fitbit.com](http://www.fitbit.com/). *\
\

::: {#toc-section .toc-section}
**Automate Amazon**:\

-   [Introduction](/2015/12/next-week-automating-amazon-how-i-am.html)
-   **Part One:** [Environment
    Setup](/2015/12/automate-amazon-development-environment.html)
-   **Part Two:** [Sketch Use
    Case](/2015/12/automate-amazon-sketch-out-use-case.html)
-   **Part Three:** [CommonUtils, methods,
    exceptions](/2015/12/automate-amazon-commonutils-methods-and.html)
-   **Part Four:** [Write Sign In
    Test](/2015/12/automate-amazon-writing-sign-in-test.html)
-   **Part Five:** [Product Enums and
    Objects](/2016/01/automate-amazon-productenums-and.html)
-   **Part Six:** [Initializing Login and
    Cart](/2016/01/automate-amazon-initializing-login-and.html)
-   **Part Seven:** [Writing Shopping Cart
    Test](/2016/01/automate-amazon-writing-shopping-cart.html)
-   **Part Eight:** [Data Driven Tests with TestNG
    XML](/2016/01/automate-amazon-sketch-of-possible-data.html)
-   **Part Nine:** [Code Review Request,
    please! ](/2016/01/code-review-request-please-automated.html)
-   **Source Code:** [GitHub, T.J.
    Maher](https://github.com/tjmaher/automate-amazon/)
:::

\
\
