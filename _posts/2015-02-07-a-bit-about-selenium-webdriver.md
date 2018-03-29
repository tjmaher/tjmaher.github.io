\-\-- layout: post title: A bit about Selenium WebDriver date:
\'2015-02-07T00:22:00.001-05:00\' author: T.J. Maher tags: - beginner -
WebDriver modified\_time: \'2016-04-29T16:18:04.138-04:00\' blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-6515118165563641366
blogger\_orig\_url:
http://www.tjmaher.com/2015/02/a-bit-about-selenium-webdriver.html \-\--
Software companies attempting to become more sensitive to the immediate
needs of their customers now measure their software development cycle in
months instead of years. The time allowed for Software Quality Assurance
to perform **regression testing** \-- testing that the new features of
the web and mobile apps being built haven\'t broken the old
functionality \-- has been drastically shortened. For software testers
this has caused frantic twelve hour days and weekend work in the last
two weeks before the product is supposed to go out the door. Selenium
WebDriver is a free open source tool that has become the new industry
standard in automated testing that can try to alleviate this problem.\
\
[]{#more}\
\
Originating at [ThoughtWorks](http://www.thoughtworks.com/) \-- an early
proponent of Agile software development \-- and adopted by Google,
Selenium WebDriver has filled the niche once occupied by pricey
commercial automation test suites such as Rational Software\'s Rational
Rose, Segue Software\'s SilkTest, or Mercury Interactive\'s TestDirector
and QuickTestPro. For a software company to get started with automated
testing just five or ten years ago, the company would have had to
purchase an expensive commercial software package from a vendor such as
from Mercury Interactive to get Mercury TestDirector for  test
management, and QuickTestPro (QTP) for automated testing. As an antidote
for this, Selenium was built.\
\
Selenium WebDriver supports many programming languages and their
frameworks that help you organize your tests: Java and its frameworks
JUnit and TestNG, Python with unittest and Nose, C\# and its framework
NUnit. Ruby even has its own version of WebDriver, Watir. From what I
can tell, the combination employers are looking for is: Selenium
WebDriver / Java / TestNG.\
\

-   [Selenium HQ](http://www.seleniumhq.org/projects/webdriver/):
    Selenium WebDriver\'s official site
-   [SeleniumHQ Documentation](http://www.seleniumhq.org/docs/): All
    about WebDriver, Selenium Grid, and some cheat sheets to locate web
    elements in your DOM (Document Object Model)
-   [Google Groups: Selenium
    Users](https://groups.google.com/forum/#!forum/selenium-users):
    Looking for an answer to a question on using Selenium? Search for it
    here!
-   [Google Groups:
    WebDriver](https://groups.google.com/forum/#!forum/webdriver): For
    those who were looking for a more technical discussion on
    WebDriver. 
-   [Code.Google.Com](https://code.google.com/p/selenium/) Selenium
    Wiki: If you wish to get a deeper understanding of the source code,
    you can go here to get the Javadocs, Rubydocs, or Python docs. They
    even have a [5 Minute Getting Started
    Guide](https://code.google.com/p/selenium/wiki/GettingStarted) and
    a [FAQ](https://code.google.com/p/selenium/wiki/FrequentlyAskedQuestions). 
-   [Blogs: [Official Selenium
    Blog](https://seleniumhq.wordpress.com/), [Official SauceLabs
    Blog](http://sauceio.com/), [Jim Evans - Ranting of a Selenium
    Contributor](http://jimevansmusic.blogspot.com/), ]{style="font-family: inherit;"}
-   [[JUnit.org](http://junit.org/): The official site provides a list
    of [Frequently Asked
    Questions](http://junit.org/faq.html#overview_1) ]{style="font-family: inherit;"}
-   [[TestNG Official Site](http://testng.org/doc/index.html): Contains
    downloads for the
    product, [documentation](http://testng.org/doc/documentation-main.html),
    and
    Selenium [examples](http://testng.org/doc/selenium.html).  ]{style="font-family: inherit;"}
-   [[Google Groups:
    TestNG]{style="font-family: inherit;"}](https://groups.google.com/forum/#!forum/testng-users)

\

::: {style="color: #4d4f51; line-height: 24px; margin-bottom: 30px;"}
[Selenium WebDriver came about when it was decided at the [Google Test
Automation
Conference](https://developers.google.com/google-test-automation-conference/) that
the first version of Selenium (2004) should merge with WebDriver (2007)
\-- two products originating from ThoughtWorks \-- to become Selenium
WebDriver (Selenium 2, 2009). Jason Huggins
( [Twitter](https://twitter.com/hugs) ), creator of the first version of
Selenium, had joined Google two years previously from ThoughtWorks along
with Simon Stewart ( [blog](http://blog.rocketpoweredjetpants.com/) ),
creator of WebDriver. Jason Huggins went on to co-found [Sauce
Labs](https://saucelabs.com/), offering cloud-hosted devices that
companies can use for web and mobile application testing. Sauce Labs is
also a backer of the open-source mobile testing
framework [Appium.IO](http://appium.io/). Simon Stewart, though at
Facebook, still also works on Selenium WebDriver, and is attempting to
get the WebDriver API endorsed by the [World Wide Web
Consortium](http://www.w3.org/) so that how it is implemented across
browsers is standardized
( [link](https://w3c.github.io/webdriver/webdriver-spec.html) to
paper ). ]{style="font-family: inherit;"}
:::

::: {style="color: #4d4f51; line-height: 24px; margin-bottom: 30px;"}
[Selenium WebDriver uses various drivers to send commands to Google
Chrome, Internet Explorer, Firefox, and other browsers and retrieves the
results. Once you install the proper drivers, you can write code to find
and interact with various web elements in the browser such as selecting
links, sending text to a textbox, and clicking on a button\... exactly
as a user of your web or mobile application would do. Add the Selenium
Grid toolset, and you can run browser tests on multiple machines
simultaneously.]{style="font-family: inherit;"}\
[\
]{style="font-family: inherit;"}
:::

::: {style="color: #4d4f51; line-height: 24px; margin-bottom: 30px;"}
[Although the shift from manual to automated test frameworks such as
Selenium WebDriver can potentially save software testers from frantic
twelve hour days and weekend work doing regression testing, in my case
it has turned my life into frantic twelve hour days and a lot of weekend
work as I attempt to update my skill
set. ]{style="font-family: inherit;"}
:::

::: {style="color: #4d4f51; line-height: 24px; margin-bottom: 30px;"}
[Here are a few links that may be helpful if you, like me, are
attempting to become more familiar with automated
testing:]{style="font-family: inherit;"}
:::

::: {style="color: #4d4f51; line-height: 24px; margin-bottom: 30px;"}
**[Selenium WebDriver]{style="font-family: inherit;"}**
:::

::: {style="color: #4d4f51; line-height: 24px; margin-bottom: 30px;"}
**[Automation Framework:]{style="font-family: inherit;"}**
:::

::: {style="color: #4d4f51; line-height: 24px; margin-bottom: 30px;"}
[Selenium code \-- whether written in Java, Python or C\# \-- is
stateless. A developer can not pick and choose what will be executed
first and what test should be executed second. Because of this, Selenium
WebDriver is partnered with an Automated Test Framework like JUnit
(2001), initially be built so developers could perform preliminary
testing on the modules they were developing with various unit tests
before the code is tested by a QA Engineer. TestNG (2004) was designed
to extend that functionality.]{style="font-family: inherit;"}
:::

::: {style="color: #4d4f51; line-height: 24px; margin-bottom: 30px;"}
[JUnit is a unit testing framework for the Java written by Kent Beck
(Creator of the precursor of Agile, Extreme Programming) and Erich Gamma
(Author of **[Design Patterns: Elements of Reusable Object-Oriented
Software](http://www.amazon.com/Design-Patterns-Elements-Reusable-Object-Oriented/dp/0201633612/)**).
It allows Selenium developers to use methods to tag areas of their code
like as \@Before (where you can launch a browser before the test is run)
\@Test (detailing individual tests) and \@After (Cleanup of the tests,
closing the browser).  ]{style="font-family: inherit;"}
:::

::: {style="color: #4d4f51; line-height: 24px; margin-bottom: 30px;"}
[TestNG (Test Next Generation), was created by Cédric Beust
( [blog](http://beust.com/weblog/) ), a software engineer at Google to
extend JUnit\'s functionality.  ]{style="font-family: inherit;"}
:::

[\
]{style="font-family: inherit;"}\

<div>

-T.J. Maher\
* Sr. QA Engineer*\
* Quincy, MA*

</div>
