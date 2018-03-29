\-\-- layout: post title: \'STAREAST Notes: David Dang, \"Open Source
Test Automation: Riding the Second Wave\"\' date:
\'2016-05-18T00:11:00.000-04:00\' author: T.J. Maher tags: - beginner -
STAR East - test framework modified\_time:
\'2016-05-18T01:12:48.665-04:00\' thumbnail:
https://1.bp.blogspot.com/-8RyP0p6zhEg/VzoWayj0hpI/AAAAAAAALAQ/p98sm\_-isgkymhtzR3rHkXCLKpDkQwQKgCLcB/s72-c/david.jpeg
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-6407184545027091169
blogger\_orig\_url:
http://www.tjmaher.com/2016/05/stareast-notes-david-dang-open-source.html
\-\-- David Dang, from [Zenergy
Technologies](http://www.zenergytechnologies.com/), VP of Automation
Solutions, gave a very entertaining and humorous talk on a brief
overview of test automation as it was, how it is now, and points to
consider a company just starting out with test automation should
consider. *[STAR East](https://stareast.techwell.com/) Virtual
Conference, a TechWell Event broadcasted from Orlando, FL, Wednesday May
4th, 2016.*\
\
![](https://1.bp.blogspot.com/-8RyP0p6zhEg/VzoWayj0hpI/AAAAAAAALAQ/p98sm_-isgkymhtzR3rHkXCLKpDkQwQKgCLcB/s320/david.jpeg){width="100"}According
to David\'s STAR East bio, \"For more than seventeen years, David Dang
has been a leader in the test automation industry. As VP of automated
solutions for Greensboro, NC-based Zenergy Technologies, David
spearheads the development of advanced frameworks that emphasize
reusability and reduce maintenance efforts. He is an expert in all major
commercial automation tools as well as open source tools such as
Selenium and Jenkins. On the mobile front, David uses advanced concepts
to design optimal frameworks using mobile automation toolsets including
Perfecto and Appium. In addition to his high-level consulting
engagements for Zenergy's clients, David is in high demand as a
presenter at major software quality assurance and testing
conferences\".\
\
[]{#more}\
\
If you are familiar with test automation, you should know that it is
moving away from the packaged toolset. There was a first wave of test
automation eight or nine years ago that has since fizzled out. We are
now on the second wave\... Should we get on it?\
\
Open source, David stressed, means that there is no licences, and no
maintenance costs, and no fees to use the tool. You share your code with
the community. Right now here are 136 open source test automation
frameworks / tools. What you are relying on with open source is the
community. People go behind it and really build up their products. The
problem with 136 open source test frameworks and tools is.. you don\'t
want to pick the wrong one.\
\
What is the difference between frameworks and tools? Tools are packaged
together. You are using it as a single toolset. A framework is a
component of a tool. Selenium is a framework, a component you can use.
Calabash is another framework.\
\
Why open source? Companies want to do more with less. Because
applications are web-based, frameworks are, too\... but with enterprise
level applications, you can\'t see exactly what is in the browser. The
browser is just the container.\
\

The First Wave
--------------

\
What happened to the first wave? Agile was really hot. Back then,
according to David, they used FitNesse, operating below the user
interface level. The user provided inputs to the application and
determined if the correct results were returned. The problem was that,
according to David you couldn\'t see what was happening from a UI
standpoint, you can\'t trust it.\
\
Then there was Ruby Watir, Ruby libraries used to automated web
browsers, that automated users clicks, button presses, etc.\
\
David Dang made a joke that even though he might reference working as a
mainframe developer and programming in COBOL, he insists he is only
twenty-eight years old.\
\

::: {style="text-align: right;"}
[\"As a consultant I want to keep up with technology, so I spent around
six months learning Ruby, and started coding in Ruby. I became pretty
good at Ruby \[\...\] and I started teaching Ruby Watir \... and then it
just fizzled out\... So, I will never get that six months of my life
back. So, things that I don\'t get back, that\'s why I am twenty-eight
years old. I discount those days\... so, if you think about it \-- I\'m
28! \-- I\'ve discounted a lot of my life\".
]{style="font-size: large;"}
:::

\
And there was Selenium RC, which weote automated web application UI
Tests, before Selenium 2. It used the dreaded record-and-pklayback.\
\
Tools were fragmented. Learning curve was high. Things were too
complex.\
\

The Second Wave
---------------

\
These are tools such as: **Selenium WebDriver**: Emulates a user sending
text to a textbox, clicking buttons or selecting dropdowns.\

-   Laid the foundation for additional tools.
-   Became adopted by the industry: Developed by ThoughtWorks, supported
    by Microsoft who came up with a WebDriver for MS Edge \-- their new
    browser
-   n the works to be adopted by the W3C as the standard for browser
    automation.
-   Convert WebDriver to RemoteWebDriver, and you can add in
    multi-threading.

\
**BDD** ( Behavior driven development ) style such as with Cucumber to
formulate tests and Ruby to write the step definitions. You write the
test first, run the test to watch it fail, then write the code to make
each part of the test pass.\
\
**Robot Framework** is based around a keyword-driven testing apprach,
built around Python.\
\
**Protractor**: Automation framework that helps you automated Angular.js
applications.\
\
**Appium**: is build on top of Selenium to test mobile apps and
browsers.\
\

How to Decide Which Toolset?
----------------------------

\
How do you pick a language for automation? If the application developers
are using Java, or Ruby, it is good to match what they are doing, so you
can ask for help when designing the automation.\
\
The problem with a framework like Selenium is that it does not have all
the features you need. If you want reporting, you need to integrate it
with yet another framework, such as ReportNG or Allure, and add those
tools in.\
\
There are some considerations before you take this leap into open source
automation:\
\
**People:**\

-   Do you have people with technical resources to adopt the framework?
-   Are people comfortable with object-oriented programming?
-   You need resources who understand framework / tool configuration and
    environment setup.
-   You need to be able to diagnose and fix your own technical issues
    without vendor support, or work with the community to fix it.
-   You need to get in the habit with working more closely with the
    development team solving technical issues.

\
\
\... Read more about David and Zenergy at
[zenergytechnologies.com](http://zenergytechnologies.com/).\
\
Happy Testing!\
\
-T.J. Maher\
Sr. QA Engineer,\
Fitbit-Boston\
\
*// QA Engineer since Aug. 1996\
// Automation developer for \[ 1 \] year and still counting!*
