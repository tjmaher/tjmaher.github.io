\-\-- layout: post title: A Brief Overview of Gauge, a BDD Automation
Framework, brought to you by Thoughtworks! date:
\'2018-01-30T07:00:00.001-05:00\' author: T.J. Maher tags: - bdd - Gauge
- Ruby modified\_time: \'2018-01-30T07:00:26.588-05:00\' thumbnail:
https://1.bp.blogspot.com/-jq1nZq7\_Dk0/Wm\_FhIKWbUI/AAAAAAAAMQo/VzbjxnmDAyc\_3YQggxDSUuPMyIeQnI3GQCLcBGAs/s72-c/out.png
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-3148387508351234563
blogger\_orig\_url:
http://www.tjmaher.com/2018/01/a-brief-overview-of-gauge-bdd.html \-\--
When it comes to automation toolsets, I am up for learning anything!
I\'m always eager to adopt whatever toolset a company is already using.
Right after my first automation gig, I would attempt to lobby the team
to use what I knew already, not confident in my own ability to drill
down into the details with a new tool. Now that I have had a few years
of experience of learning toolsets on the job \-- [and with this
blog](http://www.tjmaher.com/p/programming-projects.html) \-- I am more
confident in my ability to do Just-In-Time Learning.\
\
After a bit of quibbling \-- we are doing BDD? [Why not
Cucumber](http://cucumber.io/)? Why
[Ruby](https://www.ruby-lang.org/en/)? \-- I hunkered down and try to
learn what they were already using at my new job: **Gauge**, a BDD
automation framework brought to you by [Thoughtworks -
India](https://www.thoughtworks.com/).\
\
\
**Gauge: **\

-   **Website**: <https://gauge.org/>
-   **Official GitHub**: <https://github.com/getgauge>
-   **Gauge Community**: <https://github.com/getgauge-contrib>
-   **Twitter**: [\@GetGauge](https://twitter.com/getgauge)
-   **Google Group**: <https://groups.google.com/forum/#!forum/getgauge>
-   **Feedback Page**: <https://github.com/getgauge/gauge/issues/493>
-   **Reference Documentation**: <https://docs.gauge.org/index.html>

\
\
[]{#more}\
Gauge first debuted as open-source in January 2015.\
\
By August 2015, the product was demoed at a ThoughtWorks sponsored
software testing conference in  Hyderabad, a city in the state of
Telangana, in south-central India. Devoted to knowledge sharing, the
motto of vodQA \-- Value Oriented Discussion about Quality Analysts \--
is \"Come Learn Something New\"!\

<div>

\

\

::: {style="margin-bottom: 5px;"}
**[Gauge your BDD Test (vodQA
Hyderabad)](https://www.slideshare.net/mahendrakariya/gauge-your-bdd-test-vodqa-hyderabad "Gauge your BDD Test (vodQA Hyderabad)")**
from **[Mahendra Kariya](https://www.slideshare.net/mahendrakariya)**
:::

\
\
Right now, Gauge is up to version 0.9.6, released [December 18, 2017,
according to the release
notes](https://github.com/getgauge/gauge/releases/tag/v0.9.6).\

<div>

 How is Gauge Different Than Other BDD Frameworks? 
---------------------------------------------------

\
Deepthi Chandramouli back in 2/12/2015 wrote [outlined five main
points](https://groups.google.com/forum/#!topic/getgauge/WP_ANQ0D8mQ) on
the Gauge Google Groups:\
\
\"1. Gauge is a single product that supports multiple language across
different platforms. This ensures a uniformity and consistency
irrespective of which language and IDE you use to write your tests.\
\
\"2. Gauge uses Markdown as the markup to author specifications. This
makes it feature rich from an execution and documentation point of
view.\
\
\"3. Gauge's architecture is plugin based which makes it highly
extensible. This means that the core product can be enhanced by adding
in support for a new language, a new IDE, a customised report, external
tool integration etc. all as plugins. What this means is that any
features added to Gauge core automatically scale to all the supported
languages.\
\
\"4. Gauge has first class refactoring support both on command line and
IDE. We feel that this is the extremely important to maintain a large
test suite.\
\
\"5. Gauge has first class parallelisation support as a core feature(in
development), which applies to all supported languages\".\
\
Oh, I immediately noticed that they have a [Gauge Test Automation
Cookbook using
Chef](https://github.com/getgauge-contrib/gauge-cookbook).\
\

Installing Gauge and Setting Up a Project
-----------------------------------------

Since I am using Windows 10 at home, I followed that version of the
[Getting Started](https://gauge.org/get-started.html) instruction,
downloading the 64 bit version. I already have the [Windows version of
Ruby installed on my machine using
RubyInstaller](https://rubyinstaller.org/):\
\

-   Downloaded the Gauge 0.9.7 version. 
-   Started the Install Wizard. 
-   Chose the Ruby language plugins with HTML reporting. 
-   Finished the installation. 
-   Opened up a Windows Command Prompt typed in \"gauge version\" and
    pressed Return. Yep, it is installed. 

<div>

Now, to create a project!

</div>

<div>

\

</div>

<div>

Since I like installing my coding project in D:\\Users\\tmaher\\code, I
navigated to that directory and typed: *gauge init ruby*

</div>

<div>

-   It copied the Gauge template \"ruby\" to the current directory. 
-   It fetched all metadata from http://rubygems.org/
-   It installed, ast, bundler, method\_source, os, parser, test-unit,
    parser, power\_assert, ruby\_protocol\_buffers, and many other Ruby
    gems.

<div>

I then ran the command: *bundle exec gauge run specs*

</div>

</div>

<div>

\

</div>

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://1.bp.blogspot.com/-jq1nZq7_Dk0/Wm_FhIKWbUI/AAAAAAAAMQo/VzbjxnmDAyc_3YQggxDSUuPMyIeQnI3GQCLcBGAs/s640/out.png){width="640" height="122"}](https://1.bp.blogspot.com/-jq1nZq7_Dk0/Wm_FhIKWbUI/AAAAAAAAMQo/VzbjxnmDAyc_3YQggxDSUuPMyIeQnI3GQCLcBGAs/s1600/out.png)
                                                                                                                    *A project was run right out of the box!*
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

<div>

\

</div>

\
The sample code that Gauge produced I uploaded to a Git repository:
[tjmaher /
gauge\_0.9.7\_default\_code](https://github.com/tjmaher/gauge_0.9.7_default_code)
for your viewing pleasure!\
\
\... Let\'s see what we have here by default, right out of the box\....\
\
**Env/ Default**: Where you set the environment variables with a
*sample\_key = sample\_value* format.\
\

-   [default.properties](https://github.com/tjmaher/gauge_0.9.7_default_code/tree/master/env/default):
    Set the gauge reports directory, if you want to overwrite reports,
    or if you want a new time-stamped directory each time the report is
    run, a screenshot on failure, multithreading enabled, and whether
    you want objects cleared by suite, spec, or scenario.

<div>

**Reports**: Stores the css, fonts, images, js, and specs for reports.\
\
**Specs:**

</div>

<div>

-   [example.spec](https://github.com/tjmaher/gauge_0.9.7_default_code/blob/master/specs/example.spec):
    \"an executable specification file. This file follows markdown
    syntax.Every heading in this file denotes a scenario. Every bulleted
    point denotes a step\". In the screenshot above, \"Specification
    Heading\" is the heading, with the two steps written in it. You can
    tag the test, simply by using the keyword \"tags\". There can also
    be a data-driven element, with various \"words\" and the expected
    \"vowel count\" fed into the test. 

\... Do you know Cucumber? It\'s like a feature file. 

</div>

<div>

\

<div>

**Step\_Implementations: **

</div>

<div>

-   [step\_implementations.rb](https://github.com/tjmaher/gauge_0.9.7_default_code/blob/master/step_implementations/step_implementation.rb):
    It\'s a regular Ruby file, requiring and including libraries. This
    one relies on test/unit and Test::Unit::Accessories. It parses the
    plain English in the spec with the actual code, step by step. In
    this, it counts the vowels in the word, and does an assert\_equal
    that the expected count in an integer format equals the actual
    calculated count. 

</div>

</div>

<div>

The **Spec** lists out the test in plain English, in the language of the
business. 

</div>

<div>

\

</div>

<div>

The **Step Implementations** pair the tests with the code.\
\
Coming up next week, we\'ll be exploring Dave Haeffner\'s Selenium
Guidebook with Ruby, to see if we can write browser tests for
[The-Internet Login Page](http://the-internet.herokuapp.com/login). 

</div>

\
\
Happy Testing!\
\
-T.J. Maher\
Sr. QA Engineer, Software Engineer in Test\
Meetup Organizer, [Ministry of Testing -
Boston](http://bit.ly/mot_boston)\
\
[Twitter](https://twitter.com/tjmaher1) \|
[YouTube](http://bit.ly/tj_youtube)
\| [LinkedIn](https://www.linkedin.com/in/tjmaher1) \|
[Articles](http://bit.ly/tj_techbeacon)

</div>

</div>
