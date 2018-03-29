\-\-- layout: post title: \'Learning Serenity BDD: An Automation
Framework That Uses Specification by Example (SBE)\' date:
\'2017-03-03T15:23:00.002-05:00\' author: T.J. Maher tags: - SerenityBDD
modified\_time: \'2017-04-17T08:23:39.267-04:00\' thumbnail:
https://3.bp.blogspot.com/-bkrK9r2bG1M/WLia3L590xI/AAAAAAAALp4/q990RYKc9q8CpCx0-2mpGX8ggqJcYxtJwCLcB/s72-c/basic-concepts-detailed-test-count.png
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-7110408938462919688
blogger\_orig\_url:
http://www.tjmaher.com/2017/03/serenity-bdd-automation-framework-that.html
\-\-- When someone is demoing a new automation toolset for the very
first time, so many questions in my mind start bubbling to to the
surface:\

-   This is an open-source tool? What grad student created it? What was
    the student attempting to achieve with this tool? What problems were
    they trying to solve?
-   Is the tool on GitHub? Unit tests and code samples provided for us
    novices learning the tool? 
-   What company supports it and sponsors it? Is the tool popular enough
    for a community to have built itself around the tool? 
-   Is the tool still being maintained? When was the last time code was
    checked into the GitHub repository? How many are watching and have
    starred the GitHub repository?

<div>

Although the contract position I start on Monday, begins as a manual
testing position \-- the best way to learn the system under test \--
it\'ll move to an automation position using the tool **Serenity BDD**. 

</div>

<div>

\

</div>

<div>

*Note: BDD stands for Behavior Driven Development. Read more about it
in [Introducing BDD](https://dannorth.net/introducing-bdd/) ( Mar. 2006)
by **Dan North**, the creator of [JBehave](http://jbehave.org/), or on
**Martin Fowler**\'s blog entry,
[GivenWhenThen](https://martinfowler.com/bliki/GivenWhenThen.html) (Aug.
2013).*

</div>

<div>

\
Also, note: I haven\'t actually downloaded or installed the tool yet, or
even tinkered with it. This is just me, an automation developer,
attempting to do online researching, and compiling what I have found. I
cannot make any recommendations about this tool and how easy or
difficult to use. This is just gathering the initial research.\
\
[]{#more}\

</div>

Serenity BDD Stats
------------------

\
**Created by**: John Ferguson Smart (
[Website](https://johnfergusonsmart.com/) \|
[Medium](https://medium.com/@wakaleo) \| [LinkedIn](https://www.linkedin.com/in/john-ferguson-smart/) \|
[\@Wakeleo](https://twitter.com/wakaleo) )\
**Original name**: Thucydides (See [original
blog](https://thucydides-webtests.com/2011/09/), first post on Sept 2011
\| Old [GitHub repo](https://github.com/thucydides-webtests/thucydides)
)\
**Date created**: Thucydides (*2011*) Serenity BDD (*Nov. 2014*)\
**Currently being maintained?** Yes!\
**GitHub**: <https://github.com/serenity-bdd/serenity-core>\

-   [Serenity-Core](https://github.com/serenity-bdd/serenity-core):
    Watchers: 56, Starred: 182. 
-   Last commit, 3 days before this blog post
-   [According to this
    graph](https://github.com/serenity-bdd/serenity-core/graphs/contributors),
    committers are still quite active on this project
-   [Main repo](https://github.com/serenity-bdd) has much documentation,
    examples, demos, and tutorials, along with [integration with
    JIRA](http://serenity-bdd.info/docs/serenity/#_integrating_with_jira)
    with various [plugins for
    JIRA](https://github.com/serenity-bdd/serenity-jira). 

<div>

**Official documentation: **The [Serenity Reference
Manual](http://serenity-bdd.info/docs/serenity/), v. 1.0.1.1

</div>

\
**Build systems**:
[Gradle](http://serenity-bdd.info/docs/serenity/#_building_serenity_projects_in_gradle),
[Apache
Maven](http://serenity-bdd.info/docs/serenity/#_building_serenity_projects_in_maven),
and even [Apache
Ant](http://serenity-bdd.info/docs/serenity/#_building_serenity_projects_in_ant)\
**Compatible frameworks:**\

-   Serenity with
    [JBehave](http://serenity-bdd.info/docs/serenity/#_serenity_with_jbehave)
-   Serenity with
    [Cucumber](http://serenity-bdd.info/docs/serenity/#_serenity_with_cucumber)
-   Serenity with
    [JUnit](http://serenity-bdd.info/docs/serenity/#_serenity_with_junit)
-   Serenity with John\'s new [Screenplay
    Pattern](http://serenity-bdd.info/docs/serenity/#_serenity_and_the_screenplay_pattern)

**Running tests remotely**: [Selenium
Grid](http://serenity-bdd.info/docs/serenity/#_running_tests_against_a_selenium_grid_server),
[Sauce
Labs](http://serenity-bdd.info/docs/serenity/#_running_tests_on_saucelabs),
[Browser
Stack](http://serenity-bdd.info/docs/serenity/#_running_tests_on_browserstack)\
**Tests that can be run**: Web-based UI tests, [API tests with REST
Assured](http://serenity-bdd.info/docs/serenity/#_testing_rest_with_serenity_bdd),
and [mobile tests with
Appium](http://serenity-bdd.info/docs/serenity/#_running_tests_on_mobile_devices_with_appium)\
\
Serenity now comes in two flavors:\

-   The original Java, [Serenity
    BDD](http://serenity-bdd.info/) ( [GitHub](https://github.com/serenity-bdd) )
    by John Ferguson Smart 
-   A new JavaScript
    flavor, [Serenity/JS](http://serenity-js.org/) ( [GitHub](https://github.com/jan-molak/serenity-js) )
    by Jan Molak  

Information on Jan
Molak: [\@JanMolak](https://twitter.com/JanMolak), [Medium](https://janmolak.com/), [LinkedIn](https://www.linkedin.com/in/janmolak/)\
\

Who is John Ferguson Smart? 
----------------------------

\
According to [John\'s website](https://johnfergusonsmart.com/about/):\

<div>

\

</div>

<div>

*\"John is an international speaker, consultant, author and trainer well
known in the Agile community for his many books, articles and
presentations, particularly in areas such as BDD, TDD, test automation,
software craftsmanship and team collaboration. \[\...\] John helps
organisations and teams around the world deliver better software sooner
through more effective collaboration and communication techniques, and
through better technical practices.\
\
\"John is the author of the best-selling [BDD in
Action](https://johnfergusonsmart.com/about/#), as well as [Jenkins: The
Definitive Guide](https://johnfergusonsmart.com/about/#) and [Java Power
Tools](https://johnfergusonsmart.com/about/#).\
\
\"Very active in the Open Source community, John also leads development
on the innovative Serenity BDD test automation library, described as the
\'best opensource selenium webdriver framework\'\". *\

<div>

\

</div>

<div>

\... John earned a Bachelor of Computer Science from Australia\'s
University of Newcastle in 1991 and a PhD in Computer Science in 1995
from Aix-Marseille University in France.\

<div>

\
John has published many articles on
[LinkedIn](https://www.linkedin.com/in/john-ferguson-smart/recent-activity/posts/), [Medium](https://medium.com/@wakaleo),
and [his own blog](https://johnfergusonsmart.com/blog/), relating to
BDD, Serenity BDD, and his new idea of a screenplay pattern:\

-   [BDD, Microservices, and Serenity
    BDD](https://johnfergusonsmart.com/bdd-and-microservices/)
-   [Feature Mapping -- a simpler path from stories to executable
    acceptance
    criteria](https://johnfergusonsmart.com/feature-mapping-a-simpler-path-from-stories-to-executable-acceptance-criteria/)
-   [Generating focused reports with Serenity
    BDD](https://johnfergusonsmart.com/serenity-focused-reporting/)
-   [Better Automated Acceptance Tests With Serenity
    Screenplay](https://johnfergusonsmart.com/better-automated-acceptance-tests-serenity-screenplay/)

What Is The Philosophy of Serenity BDD?
---------------------------------------

\
From reading the documentation, tutorials, and watching many videos of
Serenity BDD in action, it seems that the tool is all about one thing:
**Readability**.\

-   Readability of what, exactly the tests are doing.
-   Readability of the results of the tests, after they are run. 

As an automation developer, is very easy to get mired down in the code
when using an automation framework. Is the automation code DRY (*Don\'t
Repeat Yourself*), is it easy to maintain, and is it readable? How is
the automation framework structured, is the architecture as good as it
could be?\
\
Most of the software development team, though, are ***not*** coders. How
can you show the business analysts, the product owners about what the
tests actually do, and what it means when the tests pass or fail?\
\
John Ferguson Smart\'s solution was to use **Specification By
Example**.\
\

<div>

What Is Specification By Example?
---------------------------------

<div>

\

</div>

<div>

Specification by example is a subject we have talked about in this blog
back in January, mentioned by Agile Coach **Greg Tutunjian** when
he [spoke at a Ministry of Testing - Boston
Meetup](http://www.tjmaher.com/2017/01/test-automation-and-specification-by.html). 

</div>

<div>

\

</div>

<div>

Greg Tutunjian, [during his
talk](http://www.tjmaher.com/2017/01/test-automation-and-specification-by.html),** **defined **Specification
by Example**: (SBE) as \"A collaboration method for specifying
requirements and tests, Acceptance Test Driven Development (ATDD) and
Behavior Driven Development (BDD)\". 

</div>

<div>

\

</div>

<div>

The term was first seen in Martin Fowler\'s
blog [SpecificationByExample](https://martinfowler.com/bliki/SpecificationByExample.html) dated
March 2004, 

</div>

<div>

> *\"I was attending a workshop at XP/Agile Universe in 2002 when the
> phrase \'Specification By Example\' struck me as a way to describe one
> of roles of testing
> in [XP](https://martinfowler.com/articles/newMethodology.html#xp) \[\...\]\
> \"Specification By Example isn\'t the way most of us have been brought
> up to think of specifications. Specifications are supposed to be
> general, to cover all cases. Examples only highlight a few points, you
> have to infer the generalizations yourself. This does mean that
> Specification By Example can\'t be the only requirements technique you
> use, but it doesn\'t mean that it can\'t take a leading role.\
> \"\[\...\] One of the great things about specification by example is
> that examples are usually much easier to come up with, particularly
> for the non-nerds who we write the software for\".*

</div>

<div>

\

</div>

What Is Serenity BDD?
---------------------

<div>

\
Originally called Thucydides, named after the Ancient Greek historian
who wrote [History of the Peloponnesian
War](https://www.amazon.com/History-Peloponnesian-War-Thucydides/dp/0140440399),
Serenity BDD is an integrated test automation framework. From [The
Serenity Reference Manual,
Introduction](http://serenity-bdd.info/docs/serenity/):

</div>

<div>

\

</div>

<div>

*\"Serenity BDD is an open source library that aims to make the idea of
[living
documentation](http://en.wikipedia.org/wiki/Specification_by_example) a
reality.\
\
\"Serenity BDD helps you write cleaner and more maintainable automated
acceptance and regression tests faster. Serenity also uses the test
results to produce illustrated, narrative reports that document and
describe what your application does and how it works. Serenity tells you
not only what tests have been executed, but more importantly, what
requirements have been tested.\
\
\"One key advantage of using Serenity BDD is that you do not have to
invest time in building and maintaining your own automation framework.\
\
\"Serenity BDD provides strong support for automated web tests using
[Selenium 2](http://docs.seleniumhq.org/projects/webdriver), though it
also works very effectively for non-web tests such as tests that
exercise web services or even call application code directly.\
\
\"The aim of Serenity is to make it easy to quickly write
well-structured, maintainable automated acceptance criteria, using your
favorite BDD or conventional testing library. You can work with
Behavior-Driven-Development tools like Cucumber or JBehave, or simply
use JUnit. You can integrate with requirements stored in an external
source (such as JIRA or any other test cases management tool), or just
use a simple directory-based approach to organize your requirements\".*

</div>

\
\

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://3.bp.blogspot.com/-bkrK9r2bG1M/WLia3L590xI/AAAAAAAALp4/q990RYKc9q8CpCx0-2mpGX8ggqJcYxtJwCLcB/s640/basic-concepts-detailed-test-count.png){width="527" height="640"}](https://3.bp.blogspot.com/-bkrK9r2bG1M/WLia3L590xI/AAAAAAAALp4/q990RYKc9q8CpCx0-2mpGX8ggqJcYxtJwCLcB/s1600/basic-concepts-detailed-test-count.png)
                                                                                                                       Screenshot used in the [Serenity Reference Guide](http://serenity-bdd.info/docs/serenity/).
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

\

Serenity BDD Demo:
------------------

\
**Serenity BDD - Tutorial 1**\
John Ferguson Smart, May 2016\

\
\
\
**Serenity BDD Tutorial \#2 - Introducing Screenplay**\
John Ferguson Smart, *May 2016*\

\

What is the ScreenPlay Pattern?
-------------------------------

\
From \"[Beyond Page Objects: Next Generation Test Automation with
Serenity and the Screenplay
Pattern](https://www.infoq.com/articles/Beyond-Page-Objects-Test-Automation-Serenity-Screenplay)\"
by John Ferguson Smart (March 2016)\
\
*\"The Screenplay Pattern (formerly known as [the
J](http://www.slideshare.net/RiverGlide/a-journey-beyond-the-page-object-pattern)[ourney
Pattern](http://www.slideshare.net/RiverGlide/a-journey-beyond-the-page-object-pattern))
is the application of SOLID design principles to automated acceptance
testing, and helps teams address these issues. It is essentially what
would result from the merciless refactoring of Page Objects using SOLID
design principles. It was first devised by Antony Marcano between 2007 -
2008, refined with thinking from Andy Palmer from 2009. It didn't
receive the name \'the Journey Pattern\' until Jan Molak started working
with it in 2013. Several people have written about it under this name
already, however, the authors now refer to it as the Screenplay
Pattern.\
\
\"The Screenplay Pattern is an approach to writing high quality
automated acceptance tests based on good software engineering principles
such as the [Single Responsibility
Principle](http://www.butunclebob.com/ArticleS.UncleBob.PrinciplesOfOod),
and the [Open-Closed
Principle](http://www.butunclebob.com/ArticleS.UncleBob.PrinciplesOfOod).
It favours composition over inheritance, and employs thinking from
[Domain Driven
Design](http://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/ref=sr_1_1?ie=UTF8&qid=1454881151&sr=8-1&keywords=domain+driven+design)
to reflect the domain of performing acceptance tests, steering you
towards the effective use of layers of abstraction. It encourages good
testing habits and well-designed test suites that are easy to read, easy
to maintain and easy to extend, enabling teams to write more robust and
more reliable automated tests more effectively\".*\
*\
***ScreenPlay: the next stage in automated acceptance testing**

</div>

<div>

John Smart/Jan Molak, *Nov 2016*

\
*<https://www.youtube.com/watch?v=4eODK3WS6cM>*\

Need Personalized Training?
---------------------------

\
Receive Personalized Training By The People Who Developed The Software!
Advertised on John Ferguson Smart\'s site is [Serenity BDD Mentoring
Packages](http://johnfergusonsmart.com/serenity-bdd-mentoring/):\
\
\"Our tailored mentoring packages ensure that you get the most out of
your Serenity BDD test automation suite, whether you are already a test
automation veteran or you are entirely new to test automation in Java.\
\
\"Each mentoring package includes:\

-   Support for up to 2 people for the smaller packages, and up to 4
    people for the larger packages
-   An initial onsite visit to review the current tests and work with
    the team members
-   Regular remote pairing/mentoring sessions working on your production
    tests with up to 2 people working together on the same session
-   A monthly webinar covering Serenity best practices, news and updates
-   Exclusive access to premium training videos and resources
-   High priority email support for questions between mentoring sessions

\"Above all, this program gives you a privileged access to the most
authoritative source of information about Serenity BDD - the framework
authors themselves, John Ferguson Smart and [Jan
Molak](http://janmolak.com/).\
\
\"Wakaleo Consulting can provide both training and full enterprise
support for your Serenity BDD test framework, including help with
installation, configuration and usage guidelines, as well as feature
requests and custom integration work. We offer yearly support contracts
backed with a service level agreement\".\

<div>

\

</div>

Need Even More Paid Training?
-----------------------------

<div>

\

</div>

<div>

There is what John Smart calls a \"[Serenity
Dojo](https://johnfergusonsmart.com/serenity-dojo/)\", where over the
course of nine months students of his dojo can scale a belt system,
going from a white belt to black belt first by getting a personalized
training packages from the library of fifty online videos, training
workshops, and mentors.

</div>

<div>

\

</div>

**\"Onboarding:** (4 to 6 weeks)\

-   \"Initiation: An initial 1-2 day workshop evaluates the team\'s
    current level and establish a tailored programme suited to the
    team\'s specific needs.
-   \"Preparation: During the period leading up to the first immersion
    (typically around 4-6 weeks), team members become familiar with the
    online course material\".

<div>

**Immersion:** (2 to 12 weeks)\
\
\"This phase uses individual and group workshops, mentoring, and active
learning exercises to draw out the full potential of each team member,
and to help them apply the practices to their own real- world projects.\

-   **\"Workshops**: One full week of face-to- face workshops helps
    participants validate and build on what they learnt during the
    onboarding. Progress is made visible and celebrated with formal
    grading and award ceremonies.
-   **\"Applied coaching**: Assisted by their mentors, team members
    learn to apply what they have learnt to their real-world projects\".

</div>

<div>

**Accompaniment** ( 6 to 9 months)

</div>

\
\"After the immersion ends, teams go back to their routine. But the
learning process doesn\'t stop there!\

-   **\"Remote Mentoring**: Team members continue to benefit from the
    support of their dedicated mentor, in the form of remote coaching
    and mentoring sessions.
-   **\"Followup workshops**: Every 6 months the team members get to
    attend a followup immersion to help them further consolidate and
    expand their skills\".

<div>

\

</div>

<div>

\

</div>

\... Y\'know, f I ever get into consulting, I need to remember this
\"software engineering education as marital arts\" metaphor that I keep
on seeing. Saying that I use Order and Discipline to write code is so
much better than how I usually do things:\

-   Randomly Googling stuff in a panic
-   Spending an evening feeling inferior studying other smarter and
    wiser developer\'s unit tests
-   Spending days trying to get a blasted tool to install on my
    environment
-   Writing code in fits and spurts
-   Searching StackOverflow for edge cases.

</div>

<div>

\... Then again, I only have been coding on-the-job for a bit over two
years. It gets better\... right? Right?\
\
And of course, thank you very much, John Smart for your words of
encouragement!\
\

> ::: {dir="ltr" lang="en"}
> An excellent introduction to Serenity BDD by
> [\@tjmaher1](https://twitter.com/tjmaher1) : <https://t.co/WXzk7wmLe8>
> [\#bdd](https://twitter.com/hashtag/bdd?src=hash)
> [\#SerenityBDD](https://twitter.com/hashtag/SerenityBDD?src=hash)
> :::
>
> --- John Ferguson Smart (\@wakaleo) [March 29,
> 2017](https://twitter.com/wakaleo/status/846969210911817728)

\

<div>

<div>

\
Until Next Time, Happy Testing!\
\
\

::: {#toc-section .toc-section}
**Learning Serenity BDD**\

-   **Part One:** [Serenity BDD: An Automation Framework That Uses
    Specification by Example
    (SBE)](http://www.tjmaher.com/2017/03/serenity-bdd-automation-framework-that.html)
-   **Part Two:** [What is the Difference Between TDD and
    BDD?](http://www.tjmaher.com/2017/03/the-differences-between-bdd-and-tdd-is.html)
-   **Part Three:** [Studying BDD using The Cucumber Book and BDD in
    Action](http://www.tjmaher.com/2017/03/learning-serenity-studying-bdd-using.html)
-   **Part Four:** [Scaffolding a new project using Maven
    Archetypes](http://www.tjmaher.com/2017/03/learning-serenity-scaffolding-new.html)
-   **Part Five:** [Reviewing The Serenity Screenplay
    Tutorial](http://www.tjmaher.com/2017/04/learning-serenity-screenplay-tutorial.html)
:::

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

</div>

</div>

</div>

</div>

</div>
