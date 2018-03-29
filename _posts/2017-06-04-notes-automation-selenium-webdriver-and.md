\-\-- layout: post title: \'Notes: Automation, Selenium WebDriver, and
PageObjects with AndrewBoyer (5/31/2017)\' date:
\'2017-06-04T19:48:00.002-04:00\' author: T.J. Maher tags:
modified\_time: \'2017-06-16T19:51:18.395-04:00\' thumbnail:
https://2.bp.blogspot.com/-MYclkvY4UUA/WTOW-8iIvMI/AAAAAAAAL1A/Tf3nmzvgtA4-kGDNrg4iGgdT6\_KKRRwbgCLcB/s72-c/andrew.jpg
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-2448221521569093619
blogger\_orig\_url:
http://www.tjmaher.com/2017/06/notes-automation-selenium-webdriver-and.html
\-\-- Have you ever wanted to learn about Automated Testing but wasn\'t
sure where to start?\

<div>

\

</div>

<div>

Members of the [Ministry of Testing -
Boston](https://www.meetup.com/ministry-of-testing-boston/events/239039001/)
met last week to listen and bring questions to **Andrew Boyer**, a
Software Developer in Test who has worked at both Google and Amazon.
Andrew talked with us Wednesday, May 31st, 2017 about Functional Web
Automation using Selenium WebDriver. 

</div>

<div>

\

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://2.bp.blogspot.com/-MYclkvY4UUA/WTOW-8iIvMI/AAAAAAAAL1A/Tf3nmzvgtA4-kGDNrg4iGgdT6_KKRRwbgCLcB/s200/andrew.jpg){width="200" height="200"}](https://2.bp.blogspot.com/-MYclkvY4UUA/WTOW-8iIvMI/AAAAAAAAL1A/Tf3nmzvgtA4-kGDNrg4iGgdT6_KKRRwbgCLcB/s1600/andrew.jpg)
                                                                                                                               *Andrew Boyer, SDET*
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

<div>

### About the Speaker:

Andrew Boyer has worked in the software industry for more than twenty
years, for companies as small as ten people, and as large as Google and
Amazon. Working at times as a developer, tester, or even a sales
engineer, he focuses now on process improvements and creating automation
frameworks. He believes good automation is accessible to all job roles,
and improves not just the quality of the shipping product, but also the
velocity of the engineering organization.\
\
LinkedIn: <https://www.linkedin.com/in/andrew-boyer-4a00685/>\
[](https://draft.blogger.com/null){#more}\
[]{#more}\
\

###  Where The Talk Was Held:

\
The event was held at iZotope's office
[https://www.izotope.com](https://www.izotope.com/), an eleven minute
walk from the Kendall / MBTA Red Line stop. Thank you so much iZotope
for letting our ragtag group crash your place of business twice a month
since Janauary 2017!\
\
iZotope is looking for an Automation Engineer! \"We are seeking an
experienced Quality Assurance (QA) Automation Engineer to join our Test
Automation Services team focused on enhancing and testing iZotope's
customer-facing web and desktop applications. The right candidate will
possess demonstrable experience developing automated tests and testing
software products, has the ability to work within different scripting
languages, has fluency in critiquing requirements and writing test
plans, and has experience working with Agile software development\". For
more about the position, see:
<http://izotope.applytojob.com/apply/sazsDc7U8l/QA-Automation-Engineer>\

###  About the Talk: Automation, Selenium WebDriver, and PageObjects 

Andrew is an amazing speaker! I have had the pleasure of working with
him back when I was at Intralinks. When I was interviewing for a
position at Amazon last summer (which I [completely botched not counting
on the whiteboard
tests](https://techbeacon.com/how-pass-coding-interview-automation-developer))
he helped prep me for the interview. And when our group needed a speaker
to talk about the basics, Andrew created this presentation in just under
a month.\
\

::: {.separator style="clear: both;"}
[![](https://lh3.googleusercontent.com/-TuSbASYuAGM/WTTYYpHoybI/AAAAAAAAL1Q/YnEXHTqgWUwilxoOlvi4N1iJDNgRPYgGgCHM/s640/blogger-image--574205399.jpg)](https://lh3.googleusercontent.com/-TuSbASYuAGM/WTTYYpHoybI/AAAAAAAAL1Q/YnEXHTqgWUwilxoOlvi4N1iJDNgRPYgGgCHM/s640/blogger-image--574205399.jpg)
:::

\
Thank you Andrew! It perfectly summed up everything that I have learned
in the past two years in my little Adventures in Automation.\
\
\... Andrew has graciously shared the slides of his presentation on
Slideshare.Net. Feel free to click through the slides below.\
\

\

::: {style="margin-bottom: 5px;"}
**[Automation, Selenium Webdriver and Page
Objects](https://www.slideshare.net/AndrewBoyer3/automation-selenium-webdriver-and-page-objects "Automation, Selenium Webdriver and Page Objects")**
from **[Andrew Boyer](https://www.slideshare.net/AndrewBoyer3)**
:::

\
*Just in case any of these topics are new to the reader, I have either
added links to the official toolsets Andrew mentions, or have added
links as footnotes to various parts of **Adventures in Automation** that
explores these topics in a bit more depth. - T.J. Maher*\
\
With Automation Development, Andrew mentioned, we have long passed the
point where a few tests can solve a problem.\
\

::: {.separator style="clear: both;"}
[![](https://lh3.googleusercontent.com/-VCGhJUFiUNg/WTTYaHfKk1I/AAAAAAAAL1Y/GpZXNJwfXf4xHZrG28hIWbYEkz57qoZUwCHM/s640/blogger-image--1120692128.jpg)](https://lh3.googleusercontent.com/-VCGhJUFiUNg/WTTYaHfKk1I/AAAAAAAAL1Y/GpZXNJwfXf4xHZrG28hIWbYEkz57qoZUwCHM/s640/blogger-image--1120692128.jpg)
:::

\
What we are doing with automation nowadays is *developing software*.
Automation code is Production code. A few tips:\

-   Get dev buy-in to help extend and maintain framework. You can
    leverage them, workign on developing tests they need.
-   Pick a language that developers want to code in. You may like Visual
    Basic, but if nobody wants to use it\... Or if a language is too
    specialized, it might be tough to find people who can code in it.
-   Use good software development practices (which he gets into later in
    his talk), 
-   Show the benefit of test automation. Show how bugs can be found by
    the tests that you have created.  
-   Unless developers come from a TDD ([Test Driven
    Development](http://www.guru99.com/test-driven-development.html))
    background writing their own unit or integration tests, they may not
    know the value of having good quality tests!

\

### 

### Good development practices

\
What did Andrew mean by good software development practices?\

-   Object Oriented design.
-   Don't Repeat Yourself. (Dry)
-   Launch and iterate. Don't just wait for for it to be pretty. Get it
    out there.
-   Yagni: You ain't gonna need it

\
[Object Oriented Design]{.underline}: You are going to want to study
about to model a process using objects. Terms such as *encapsulation*,
and *inheritance.* When to make a method *public, private,* or
*protected.*\
*[\
]{.underline}*[Don\'t Repeat Yourself (DRY):]{.underline} Don\'t Repeat
Yourself has been a maxim since the early days of the Agile Development
movement. Don\'t just copy-and-paste code throughout your software.
Bundle it up into a method that you can easily reuse. Learn how to
refactor your code. *\[Originating from Andy Hunt and Dave Thomas\' [The
Pragmatic
Programmer](https://pragprog.com/the-pragmatic-programmer/extracts/tips)\]*\
\
[Launch and iterate]{.underline}: Don\'t come up with the perfect
solution. Get what is just good enough, get it out there, show it to
others, see if it is what they need, learn from their feedback, and make
changes accordingly.\
\
[YAGNI]{.underline}:\

> *\"Often you will be building some class and you'll hear yourself
> saying \'We're going to need...\' Resist that impulse, every time.
> Always implement things when you actually need them, never when you
> just foresee that you need them.\
> \"The best way to implement code quickly is to implement less of it.
> The best way to have fewer bugs is to implement less code. You're not
> gonna need it!\" ---[Blog
> post](http://ronjeffries.com/xprog/articles/practices/pracnotneed/)by
> [Ron Jeffries](https://twitter.com/RonJeffries)*

###  Other Tips By Andrew: 

Don't do UI automation before the User Interface is ready for it.\

-   When the web developers are still changing what the web or mobile
    interface is supposed to look like, it isn\'t ready to write
    automated tests. 

Code every day.\

-   Learning to code is like learning a foreign language. You need to
    use it every day. You need to put in the investment to learn it. 

\
You also may need to learn domain expertise:\

-   \... Especially for big data and machine learning. It is not enough
    to learn how to write automation. You need to really learn the
    product you are testing. How do all the back end systems work? How
    can you test at that level? 
-   To write good automation, you need to know the product. What is a
    good test? What is good test data? You need to really know the
    product to determine if a test truly passes or fails.

### 

### Fluent Testing

  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://lh3.googleusercontent.com/-FvZVI6hy6f0/WTTmhiWzq1I/AAAAAAAAL1o/qa2PNQVXUb0EPrOQ8niA-rDiQp5yZbaxQCHM/s640/blogger-image-154870894.jpg){width="640" height="480"}](https://lh3.googleusercontent.com/-FvZVI6hy6f0/WTTmhiWzq1I/AAAAAAAAL1o/qa2PNQVXUb0EPrOQ8niA-rDiQp5yZbaxQCHM/s640/blogger-image-154870894.jpg)
                                                                                                                                                      *Fluent Programming*
  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

\
Compare the code...\
\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 HomePage page = driver.load(HOME_PAGE);  
 page.setUser(user);  
 page.setPassword(password);  
 page.clickLogin()l  
 ProfilePage profile = page.openProfile():  
```

\
\... with\...\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 ProfilePage page = HomePage  
      .login(user, password)  
      .openProfile():  
```

\
\... Which looks more readable? Which style of framework would you get a
DEVs buy-in?\
\
*\[The steps of the test are being chained together using
behind-the-scenes a Builder pattern. [See T.J.\'s
blog](http://www.tjmaher.com/2016/05/addressbuilder-builder-pattern-example.html).\]*\

###  What Test Runner Do You Want To Use?

\
Maybe you want to use JUNit or TestNG. Maybe you want to do Spock. Maybe
you want to do BDD and use Cucumber \...\
\
Or maybe you want to get a little weird and use Exploratory testing
model which tests around the edges of your model.\
\
For most tests, automate after the UI stabilizes.\
*\
\[ Read the official documentation about [JUnit](http://junit.org/),
[TestNG](http://testng.org/doc/documentation-main.html), and the [Spock
Framework](http://spockframework.org/)! \]*\
\

### Driver Classes

When designing a framework, make sure to separate out your own Driver
class. You should not see in your test anything relating to the driver.
You can also put in your own custom elements.\
\
... Use custom extensions that you can design yourself such as one
Andrew likes, isPresentNoWait, with a default timeout to be zero. Is the
element not on the page immediately? Fail and move on.\
\
Driver classes are a good place to put your Actions.perform methods ...
moving the mouse. Hover here, move there, etc.\
\
*\[ See [Keyboard and Mouse Actions with
ActionClass](http://www.guru99.com/keyboard-mouse-events-files-webdriver.html)
at Guru99 \]*\

###  Page Objects

\
Page Objects represent a single page. It consists of locators, elements,
and operations you need to interact with a web page.\
\
The Page Object handles Synchronizations, how long to wait for a slow
loading element. Don\'t add it to the test, waiting for an element to
show up. Add it to the public method.\
\
And make sure to use Object Oriented principles. Do you have a lot of
common elements between your many page objects? Refactor out the common
elements, put them in abstract base pages, and have each Page Object
extend from that.\
*\
\[ Read [SeleniumHQ\'s article on Page
Objects](https://github.com/SeleniumHQ/selenium/wiki/PageObjects) \]*\
*\
*\

### Locators

<div>

\

</div>

Before, it use to be css selectors vs xpath. Are you looking for text in
a link name? XPath may be good.  But in Andrew\'s opinion:\
\

-   ID \> CSS \> XPath

\
Steer away from generators that claim to create locators for you. They
tend to create poor locators. Try the Google Web Toolkit (GWT). It adds
good tags you can use.\
\
Generators also create poor XPATH. It always is too complex. See if you
can simplify it.\
\
What about common elements such as headers, footers, menu bars? Extract
these objects out into its own object.\
*\
\[ Go to the official [Google Web Toolkit](http://www.gwtproject.org/)
page\]\[ Read T.J.\'s [blog about CSS
Selectors](http://www.tjmaher.com/2015/04/how-selenium-webdriver-uses-css.html)
\]*\
\

### Synchronization

Bad synchronization is the most common cause for flaky tests. With
Dynamic HTML you now can have page elements which do not yet appear on
the page.\
\
How do you handle that? Thread.sleep? NO. This is building unnecessary
lag into the system.\
\
Imagine if you wait arbitrarily for a button to appear, say, ten
seconds. What if the button appears in just five? That is five seconds
of lag. You now are unnecessarily waiting explicitly too long. It would
be better to have an implicit wait. Use a WebdriverWait that checks if
the element is there every 100 milliseconds, then times out, failing
after ten seconds. You are implicitly waiting for the button to pop up.\
\

### PageFactory

\
The Page Factory initializes web element for you. This hands you a page
object that is ready to use. You call it right after opening a page in a
browser.\
\
*\[ Read [SeleniumHQ\'s article about Page Factory
pattern](https://github.com/SeleniumHQ/selenium/wiki/PageFactory) \]*\
*\[ See a demo of the Page Factory with [T.J.\'s Basic Appium
Framework](http://www.tjmaher.com/2017/05/basic-appium-framework-part-four.html)
\]*\
\

### Test Classes

\

-   Should rarely call driver functions. 
-   Avoid explicit waits, where you arbitrarily sleep for 10 seconds.
-   Use Implicit Waits: Wait for ten seconds (checking in 100
    millisecond increments) until this Expected Condition is shown.
-   You want your tests to fail fast. Test one thing. No point in using
    25 assertions in one test. 

### Asserts

\

-   Asserts should not be buried in the code. They should live in the
    Test Class.
-   If you wish, you can verify that multiple items on a page, such as a
    receipt with a softAssert. Remember, though, this all takes time.
    You don\'t want do check the same thing in multiple tests. 

\
\
**What Went Wrong?**\
\
\

-   Did something go wrong? What is it? Is this a test failure or is
    this a Broken test?
-   Did your automated test throw a Null pointer exception? It should
    not be considered a test failure... it is a broken test. It is an
    -error-. An unhandled case that popped up. 

\
When do you say a test is stable enough to put into production? You
don't want developers to turn of your test. You want the framework to be
rock solid and any failures are rock solid.\
\

### Hamcrest Matchers

\

-   More human readbale conditions.
-   Increased logical complexity, such as X or y but not c... you can do
    that with Hamcrest matchers.

\
*\[ See a [tutorial on
Hamcrest](http://www.vogella.com/tutorials/Hamcrest/article.html) \]*\
\

### Additional Pieces:

###  Test Case Management System

There are many ways to show traceability:\
\

-   TestRail
-   Zephyr
-   SerenityBDD

<div>

\... Keeps track of what passed, what failed, and reports results over
time.

</div>

\
\

### Reporting

\

-   Andrew writes all results to a sql database, and then figures out
    how to do the reporting he wants.

\

###  Tagging and Grouping tests

\

-   What kind of test is it? Is it a smoke test, a regression test?
-   How can your system run a single test?

\

###  Build Tools You Can Use:

\

-   Apache Ant
-   Apache Maven
-   Make
-   Gradle

*\[ Read in T.J.\'s [blog about a Free Course in
Gradle](http://www.tjmaher.com/2016/06/free-udacity-course-gradle-for-android.html)
\]*\

###  Continuous Integration / Deployment 

\

-   How do you want to set it up for tests to run each how, or each time
    code is deployed on a QA Server?
-   Do you want to use Jenkins, Bamboo, TeamCity?

\

### Version Control 

\

-   Your automated test framework is code. 
-   Where do you want to store it? Git? SVN? Perforce?

\
\
Static Inspections:\
\

-   FindBugs, Checkstyle

\
\

### Hypothetical

How would you handle promotion testing when a new feature replaces an
old feature, and the automation for each is incompatible?\
\
When you want to run production tests vs production environments?\
\
You can hide feature behind a feature flag!\
\

### Dependency Injection

\

-   If you add dependency injection with spring, you can  go to Mock
    credit card system instead of the real thing.

\
\

### Networking Testing 

\

-    RFCs, Charles Proxy, Wireshark.

\
\

### Tips on How to Start

  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://lh3.googleusercontent.com/-Izm9OrqWYeo/WTTYZO75oQI/AAAAAAAAL1U/aZ1pCxxBrgIV5KPjBLt7jF6sVxhZA9ErwCHM/s640/blogger-image--153233727.jpg)](https://lh3.googleusercontent.com/-Izm9OrqWYeo/WTTYZO75oQI/AAAAAAAAL1U/aZ1pCxxBrgIV5KPjBLt7jF6sVxhZA9ErwCHM/s640/blogger-image--153233727.jpg)
                                                                      *A Quote from Michael C. Feathers, [Working Effectively With Legacy Code](https://www.amazon.com/Working-Effectively-Legacy-Michael-Feathers/dp/0131177052)*
  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Andrew talked about a certain chapter in Michael C. Feather\'s
\"[Working Effectively With Legacy
Code](https://www.amazon.com/Working-Effectively-Legacy-Michael-Feathers/dp/0131177052)\"
(2004), which talks about how easy it is to get overwhelmed when a job
seems to big. There are too many parts. When that feeling creeps in, one
way to deal with it is to try to connect with others. Other developers
in the same situation. Thanks, Andrew for doing that with us!\
\
A few final tips Andrew expressed:\

-   Start small, with Selenium IDE then export
-   Take classes in [Codeacademy.com](http://codeacademy.com/). They
    have courses in HTML, Java ,Python. You need to become fluent in the
    language before we writing good automation.

\
\
\
Until next time, Happy Testing!

</div>

</div>

<div>

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
