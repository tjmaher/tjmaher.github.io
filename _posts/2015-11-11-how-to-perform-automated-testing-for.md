\-\-- layout: post title: How to perform automated testing for an
eCommerce application? date: \'2015-11-11T19:27:00.003-05:00\' author:
T.J. Maher tags: - beginner - setup - test framework modified\_time:
\'2016-04-29T07:56:17.093-04:00\' blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-6657419161227610126
blogger\_orig\_url:
http://www.tjmaher.com/2015/11/how-to-perform-automated-testing-for.html
\-\-- Are you an automated tester writing tests for the eCommerce
application at your company?\

<div>

\

</div>

<div>

If so\... Do you feel like comparing notes? I\'m new to the world of
automation. I\'ve only been doing it since March of this year, and I
would love to compare and contrast what your world is like. 

</div>

<div>

\
[]{#more}\

</div>

<div>

For automation, at work we use:

</div>

<div>

\

</div>

<div>

#### **Automation Framework**: 

> [Selenium WebDriver 2](/2015/02/a-bit-about-selenium-webdriver.html):
> A library that opens browsers, inspect web elements such as text
> boxes, dropdown listboxes, radio buttons, alert messages, buttons, and
> manipulated them. Easy to learn. 

#### **Programming Language**: 

> [Java](/2015/03/learning-java.html) 7 (soon upgrading to Java 8).
> Using Object Oriented Programming design to make sure that the tests
> and test framework
> is [DRY](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself)? A bit
> harder to learn.
> [YAGNI](https://en.wikipedia.org/wiki/You_aren%27t_gonna_need_it)?
> Easy. [SOLID](https://en.wikipedia.org/wiki/SOLID_(object-oriented_design))?
> Much harder to learn. 

#### **Test Framework:** 

> Test NG

</div>

<div>

#### **Continuous Integration System**: 

> [Jenkins](/2015/03/lecture-customizing-jenkins-sitespect.html)

</div>

<div>

#### **Virtual Test Machines**: 

> [Sauce Labs](/2015/06/testallthethings.html)

</div>

<div>

### **Software Development Methodology:** 

> [Agile](/2015/01/agile-software-development.html), two week sprints

</div>

<div>

#### **Integrated Development Environment (IDE)**: 

> IntelliJ, Enterprise Edition

</div>

<div>

#### **What we are Automating:**

> We developed our own shopping cart and admin portal so we can be more
> in tune with our business needs. If anything goes wrong with our order
> system, we can do a very quick turnaround time fixing any problems. 

</div>

<div>

#### **How we work with the Development Team:** 

> Excellent!!

</div>

<div>

> The software testing team is embedded in the eCommerce team, both
> automation and manual. The entire eCommerce team attends the same
> sprint planning, daily scrum, and sprint retrospective, keeping us
> aligned with the entire team.   

> Automation has its own Sprint, a secondary sprint planning, with the
> QA Manager as the Product Owner, grooming, prioritizing, and adding
> stories to our backlog. This helps keep both testing teams aligned. 

#### **Our Test Development Process**:

\

-   **TestRail**: Our entire automation test suite is data driven, from
    our hourly tests to our full regression test suite. Each test is a
    row that can be dragged-and-dropped into different categories. 
-   **Automated Tests**: Each test is linked in our Java codebase to a
    TestNG \@Test annotated with the JIRA ticket number. Each test is
    comprised of actions to navigate to certain pages, groups of actions
    to get and compare data, and assert statements on what we are
    testing. Asserts should only go in the actual automated test. 
-   **Actions classes**: Need to Login()? FillAnOrder()?
    FillBillingAndShipping()? We have actions for that. If you are doing
    something special the first time around, it may be fine if you keep
    it in the \@Test class, but if you are doing the same series of
    steps more than once, refactor it all out and put it in the actions
    class. 
-   **Page Objects**: Each page of our site has its own Java class, a
    [Page
    Object](/2015/07/the-internet-page-object-model-examples.html),
    making the locators of each and every web element, from dropdown
    listboxes to textboxes and buttons easy to find. This should be the
    only place where we interact with a web page, from the Document
    Object Model (DOM).
-   **Web Elements:** We use CSS Selectors to find the elements on a web
    page. We found that Ids can change easily. The position of a web
    element also can change, ruling out XPath. To help us in our
    automation, we have web elements embedded with a value called
    \"data-qa\". Need to find that Free Shipping Level Radio button? It
    is at the very top of the corresponding page object and is:

> [private final By **FREE\_SHIPPING\_LEVEL** =
> By.*cssSelector*(\"\[data-qa=\'shipping-level-free\'\]\");]{style="font-family: "courier new" , "courier" , monospace;"}

#### **Future Plans for the Automation Team**:

\
With only three people on the automation team, we are finding that we
can barely keep up with the backlog of automating new stuff just added
to the regression test suite, and at the same time refactoring our old
stuff, making the tests more robust. Maybe we could build on the actions
classes and use Cucumber-JVM, so other developers and other QA Engineers
can can build the individual tests, while our team focuses on building
out tools? Or should we go the keyword driven approach?\
\
I joked with my manager\... if only we could contact Amazon and see what
automation tools and techniques they use to test their eCommerce
application. He mentioned\... well, there is LinkedIn and Twitter!\
\
\... So, do you test an eCommerce application, such as a shopping cart?
What is your automation team like where you work? What tools do you use?
How are tests structured? And have you gone the Behavior Driven route,
such as with Cucumber? Or did you opt for a more Keyword driven
approach?\

<div>

\

</div>

</div>

> ::: {dir="ltr" lang="en"}
> [\@TourDeDave](https://twitter.com/TourDeDave) Now, if only you could
> write an automated test article on modelling a shopping cart for an
> eCommerce application
> [\@FitbitBoston](https://twitter.com/FitbitBoston).
> :::
>
> --- T.J. Maher (\@tjmaher1) [November 12,
> 2015](https://twitter.com/tjmaher1/status/664612055849111552)

\

<div>

\

</div>

> ::: {dir="ltr" lang="en"}
> [\@tjmaher1](https://twitter.com/tjmaher1)
> [\@FitbitBoston](https://twitter.com/FitbitBoston) I\'m a fan of this
> post on the subject <https://t.co/guf4zHd7Qy> cc:
> [\@noahsussman](https://twitter.com/noahsussman)
> :::
>
> --- Dave Haeffner (\@TourDeDave) [November 12,
> 2015](https://twitter.com/TourDeDave/status/664617836288065536)

\
\

### More Fitbit-Boston related articles on this blog:

\

-   [My new position: Sr. QA Engineer @ Fitbit
    Boston](/2015/04/my-new-position-sr-qa-engineer-fitbit.html)
-   [How Fitbit - Boston sets up an automation development
    environment](/2015/04/how-fitbit-boston-sets-up-their.html)
-   [Live Blog: Fitbit Boston @
    BostonTechJam](/2015/06/live-blog-fitbit-boston-bostontechjam.html)

\
\
\
-T.J. Maher\
 Sr. QA Engineer, Fitbit\
* // Manual tester, 15 years*\
* // Automated tester for \[ 9 \] months and counting*\
\
*Please note: \'Adventures in Automation\' is a personal blog about
automated testing. It is not an official blog
of [Fitbit.com](http://www.fitbit.com/). *\
\

<div>

\

</div>
