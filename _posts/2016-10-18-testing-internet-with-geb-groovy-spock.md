\-\-- layout: post title: \'Testing The-Internet with Geb + Groovy +
Spock: About Yeoman, scaffolding, and other build tools\' date:
\'2016-10-18T01:26:00.001-04:00\' author: T.J. Maher tags: - Geb -
Yeoman - Gradle - Groovy - Spock modified\_time:
\'2016-11-18T23:00:14.389-05:00\' thumbnail:
https://1.bp.blogspot.com/-BrWQMYL4COI/WAW0v9CcvkI/AAAAAAAALgQ/V11cKn9uh08zCB9T\_RkMNm-Cxk7wdUGjgCLcB/s72-c/yeoman.png
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-8571836304471222768
blogger\_orig\_url:
http://www.tjmaher.com/2016/10/testing-internet-with-geb-groovy-spock.html
\-\-- Have you ever needed to set up a brand-new project but were not
sure where to start? I am like that right now!\
\
For the past week, I have been trying to figure out how I wanted to set
up the file and folder structure for a new **Geb** + **Groovy** +
**Gradle** + **Spock** project. I was going to go back to Dave
Haeffner\'s test site, The-Internet
( [link](https://the-internet.herokuapp.com/login) ) and take a look at
writing a test for his login page:\
\

-   [Geb](http://www.gebish.org/manual/current/) (pronounced \"jeb\") is
    a mash-up of [jQuery](http://jquery.com/), Selenium
    [WebDriver](http://code.google.com/p/selenium/), with the Page
    Object Model,
    [Reporting](http://www.gebish.org/manual/current/api/geb/report/Reporter.html),
    and taking Snapshots built in. 
-   [Groovy](http://groovy-lang.org/) is a scripting language language
    that I [covered before in my
    blog](http://www.tjmaher.com/search/label/Groovy), specifically when
    talking about using Gradle for build.gradle configurations. 
-   [Gradle](https://gradle.org/) does a lot more than handle installing
    third-party dependencies such as
    [Chromedriver](https://sites.google.com/a/chromium.org/chromedriver/)
    when you want to spin up a new Chrome browser on your local machine.
    With Gradle, you can set up tests to be kicked off on the command
    line, just waiting to be fed into a continuous integration
    environment such as [Jenkins](https://jenkins.io/).  
-   The [Spock Framework](http://spockframework.org/) follows a Given /
    Then / When / Expect framework found in
    [Cucumber](https://cucumber.io/)\'s [Gherkin
    language](https://github.com/cucumber/cucumber/wiki/Gherkin) format
    that is usually paired with [Ruby](https://www.ruby-lang.org/). 

<div>

But how do I set all these tools up if I want to test ? How to get them
all to work together?

</div>

\
Should I just repurpose Sauce Labs Test Framework,
**Groovy-Geb-Spock-Selenium**
at <https://github.com/saucelabs-sample-test-frameworks/Groovy-Geb-Spock-Selenium>?\
\
A new co-worker of mine referred me to a tool he had heard of at a
previous job that may help: **Yeoman.io**.\
\

::: {.separator style="clear: both; text-align: center;"}
[![](https://1.bp.blogspot.com/-BrWQMYL4COI/WAW0v9CcvkI/AAAAAAAALgQ/V11cKn9uh08zCB9T_RkMNm-Cxk7wdUGjgCLcB/s200/yeoman.png){width="200"
height="200"}](https://1.bp.blogspot.com/-BrWQMYL4COI/WAW0v9CcvkI/AAAAAAAALgQ/V11cKn9uh08zCB9T_RkMNm-Cxk7wdUGjgCLcB/s1600/yeoman.png)
:::

\
\

-   **Official Site of Yeoman**: <http://yeoman.io/>
-   **GitHub Site**: <https://github.com/yeoman>
-   **Official tutorial**: a
    Codelab: <http://yeoman.io/codelab/index.html>

\
In the next blog article, we will be borrowing heavily from \"[Let\'s
Scaffold a Web App](http://yeoman.io/codelab/index.html)\" written by
Mehdy Dara ( Github: [zckers](https://github.com/zckrs) ) to walk
through setting up your Mac or PC for Yeoman. We will also walk through
installing a **Geb Generator** for Yeoman created by Chris Hluchan
( [LinkedIn](https://www.linkedin.com/in/chris-hluchan-3a473413) ), a
Software Engineer at Google, formerly at Oracle. This will set up the
project\'s **scaffolding**.\
\
Later articles will talk about about:\
\

-   Diving into the scaffolding code that has been generated, figuring
    out how it works
-   How to set up the Gradle configuration file to be able to run tests
    in parallel
-   Customizing the scaffolding to work with a login page
-   How Geb works with Selenium WebDriver: entering text, clicking
    buttons, and capturing web elements in page objects. 

<div>

This blog article will talk a bit about the history of the Yeoman tool. 

</div>

\
\
[]{#more}\
\

What is Scaffolding?
--------------------

\
According to
[Wikipedia](https://en.wikipedia.org/wiki/Scaffold_(programming)):\

> ***\"Scaffolding** is a technique supported by
> some [model--view--controller](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller "Model–view–controller") [frameworks](https://en.wikipedia.org/wiki/Software_framework "Software framework"),
> in which the programmer can specify how the application database may
> be used.
> The [compiler](https://en.wikipedia.org/wiki/Compiler "Compiler") or
> framework uses this specification, together with pre-defined code
> templates, to generate the final code that the application can use
> to [create, read, update and
> delete](https://en.wikipedia.org/wiki/Create,_read,_update_and_delete "Create, read, update and delete") database
> entries, effectively treating the templates as a
> \'[scaffold](https://en.wikipedia.org/wiki/Scaffolding "Scaffolding")\'
> on which to build a more powerful application.\
> \
> \"Scaffolding is an evolution of database code generators from earlier
> development environments, such as Oracle\'s CASE Generator, and many
> other [4GL](https://en.wikipedia.org/wiki/Fourth-generation_programming_language "Fourth-generation programming language") client-server
> software development products.\
> \
> \"Scaffolding was made popular by the [Ruby on
> Rails](https://en.wikipedia.org/wiki/Ruby_on_Rails "Ruby on Rails") framework.
> It has been adapted to other software frameworks\" *

According to
[Yeoman.io](http://yeoman.io/codelab/scaffold-app.html), \"Scaffolding,
in the Yeoman sense of the word, means **generating files for your web
app based on your specific configuration requests**. In this step,
you\'ll see how Yeoman can generate files specifically for your favorite
library or framework --- with options for using other external libraries
like [Webpack](https://webpack.github.io/), [Babel](https://babeljs.io/)
and [SASS](http://sass-lang.com/) --- with minimal effort\". -
*Yeoman\'s [Codelab for the
Scaffold-app](http://yeoman.io/codelab/scaffold-app.html)*.\
\
\

About Yeoman and other Build Tools
----------------------------------

\
**Yeoman.io** is an open-source project sponsored by the [Google Chrome
Developer
Relations](https://www.quora.com/What-is-it-like-to-work-at-Google-in-their-Developer-Relations-team)
team, such as Addy Osmani ( [blog](https://addyosmani.com/blog/) ), Paul
Irish ( [blog](https://www.paulirish.com/) ). Can\'t find a way to
generate the exact combination you need to scaffold your software
project, or web application? You can use their toolset to write your
own! Yeoman has [1.3 million](http://www.npm-stats.com/~packages/yo)
total installs and [1635](http://yeoman.io/generators/) community
generators.\
\
Yeoman was first rolled out at Google I/O 2012.\
\
Google I/O, **Better Web App Development Through Tooling**\
Paul Irish, June 28, 2012\

*48 minutes*\
\
\"Building a solid webapp is a challenge for all developers, but a
plethora of tools have emerged recently to assist you. From starting
boilerplates, to performance tuning and build tools, you\'ll get a full
overview of the tooling ecosystem. In this session, you\'ll learn which
mature and valuable open source projects can save you time as well as
get answers to common questions in building a webapp\".\
\
\... Please note: Google moves so fast that the above video is posted
more as a history lesson than anything else.\
\
If you want something a bit more recent, there is\...\
\
**Totally Tooling Tips**:\
Build Processes (S2, Ep 2), *Nov 25, 2015*\
Addy Osmani & Matt Gaunt\

\
*6:00 minutes*\
\
\"A build process is vital to any web front end project, it saves you
time, implements best practice with ease and is easy to set up with all
the existing boilerplate projects. Matt & Addy discuss the main projects
and how they use a build process on a day to day basis\".\
\
In the next few blog entries, we will install Yeoman from the Node
Package Manager, set up a Geb generator, and examine the code produced.\
\
\

::: {#toc-section .toc-section}
**Testing The-Internet with Geb + Groovy + Spock:**\

-   **Part One:** [About Yeoman, scaffolding, and other tooling
    applications](http://www.tjmaher.com/2016/10/testing-internet-with-geb-groovy-spock.html)
-   **Part Two:**  [A Step-By-Step Process: Installing and Configuring
    Yeoman and Chris Hluchan\'s Geb
    Generator](http://www.tjmaher.com/2016/10/testing-internet-with-geb-groovy-spock_19.html)
-   **Part Three**:  [Running the built-in tests from the command line,
    and examining how they have been set up with
    Gradle](http://www.tjmaher.com/2016/11/testing-internet-with-geb-groovy-spock.html)
-   **Part Four**:   Examining the Geb + Groovy + Spock code
    automatically generated
-   **Part Five**:   Modifying the Geb + Groovy + Spock Code to fit our
    needs
-   **Source Code:** [Initial source code generated out-of-the-box by
    the Yeoman Geb
    generator](https://github.com/tjmaher/geb_project_generated_by_yo)
:::

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
