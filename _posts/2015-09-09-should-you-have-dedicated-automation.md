\-\-- layout: post title: Should You Have a Dedicated Automation Team
Within Your QA Department? date: \'2015-09-09T09:48:00.004-04:00\'
author: T.J. Maher tags: - industry - manual to automation - qa
modified\_time: \'2016-04-29T16:24:49.485-04:00\' blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-1392513438052648548
blogger\_orig\_url:
http://www.tjmaher.com/2015/09/should-you-have-dedicated-automation.html
\-\-- To stay in touch with what is happening all around the software
testing community, my weekly diet consists of many a blog. None helps me
more than Sauce Labs and their [Official Sauce Labs
blog](http://sauceio.com/). Sauce Labs was founded by the creator of the
first version of Selenium, before it was Selenium WebDriver. Besides
being a great tool to use, so that you don\'t have to manage yourself
all the browsers, platforms, and environments Selenium Grid can offer
when automated tests are performing browser testing, Sauce Labs also
sponsors the open source product, Appium, used for mobile testing.\

<div>

\
[]{#more}\

</div>

<div>

On \"The Official Sauce Labs Blog\" they have a new entry: 

</div>

<div>

\

</div>

> ***Should You Have a Dedicated Automation Team Within Your QA
> Department?**[September 1st, 2015 by Israel
> Felix](http://sauceio.com/index.php/2015/09/should-you-have-a-dedicated-automation-team-within-your-qa-department/)* 

> *If you've led or managed QA teams that have included an automation
> test team, you've probably been in a situation where you had to decide
> whether you should keep them on board. Normally the decision needs to
> be made when there is a change in leadership, wherein the new
> management comes with a mandate to consolidate groups and reduce
> costs. This situation also tends to arise when working with startups
> or small companies when they are ready to put together or augment
> their QA teams. So should you have a dedicated automation team?* 

> *Typically, there are two camps with regards to dedicated automation
> teams. There are those who believe that we should have dedicated
> automation teams, and those who believe that QA engineers should
> handle manual testing and automation testing. From my experience
> working in QA within both small and large companies, I almost always
> prefer to have a dedicated automation team. However, there are a few
> scenarios where having a QA team that takes on both roles might make
> sense.* 

> ***Time to Market*** 

> *For automation to be done right, it needs to be a full-time job. From
> developing the framework and creating the libraries and scripts for
> different platforms to executing and debugging failures --- it will
> all simply consume too much of an engineer's time and compromise the
> actual testing and release date. As you already know, time to market
> and keeping a release on schedule is top priority, so testing needs to
> get done, no matter what.* 

> *If you don't have a dedicated automation team, automation will most
> likely suffer as a result of engineers being consumed with manual
> testing, and reporting and duplicating bugs for Development to fix. If
> we ask engineers to prioritize automation, manual testing could suffer
> as a result of engineers spending too much time with
> automation-related tasks; therefore, they are unable to complete
> testing on time.*

At my workplace, we have two Software Quality Assurance Teams: Manual QA
and Automation. Both teams are quite new here in Boston \-- The Boston
office only has been around for two years. The QA department in Boston
consisted of a few automation engineers writing automated tests to cover
the basics of placing an order, and writing the initial testing
libraries that wrapped logging error handling functionality around the
basic Selenium WebDriver commands. When I joined my company back in
March 2015, the Manual QA department was just being started. I helped
out with manual testing as I was ramping up to speed in automation. When
I switched over to doing automated testing full-time in June, *that*
department was just being started. From experience, let me tell you,
when you are performing manual testing at the same time as you are
attempting to develop automation scripts, something always suffers.\
\
When you are a manual QA Engineer responsible with testing all the new
functionality that is being developed, basing your test plans and test
cases on brief sketches of software requirements that seem to evolve
minute-by-minute, you don\'t really have time to sit back and mull over
the best way to automate the new functionality before it even has been
developed\... Especially when you are still in the process of building
out your testing framework, and trying to get up to speed and
familiarize yourself with all the previous automated tests, match what
you develop with the existing coding styles, learn Java programming on
the job, etc. etc.\
\
To answer the question raised in the blog, \"Should You Have a Dedicated
Automation Team Within Your QA Department?\" I would say, absolutely
yes!\
\
If you are a manual tester, you need to match your pace with the
developers in the (normally) two week software development sprint. You
are writing quick test plans when developers are developing their code.
You are reviewing testplans when they are reviewing their code. You are
testing their code as soon as it is pushed from their development
environment to your testing environment. It takes a lot of focus to keep
up with the possibility of changing requirements or daily releases to
production each day. Focusing on anything but that may reduce the
quality of the work you are doing.\
\
As an automated tester, I find that my experience helping out with the
manual testing back then has seriously helped me in my automation
efforts now. When writing automated tests for using promotional codes
with our eCommerce application now, it has helped that I was the manual
tester for that functionality  when it was being built months ago. In
spite of the great background I acquired, swapping back and forth
between being a manual tester and an automated tester almost killed me!
I could be considered a junior developer, still getting up to speed in
coding professionally. It takes a lot of time and effort to ramp up.\
\
I am glad for the manual testing experience I acquired in my first three
months at work, but now that I am writing automated tests for the first
time and am helping contribute to the testing framework, manual testing
is thankfully no longer my focus. During the day, I mimic other
automated tests that others have written, modifying them to fit my
needs. During my evenings and weekends, I research Java and the Selenium
documentation, figuring out why the automated tests work the way they
do. If I still wore a manual testing hat, either the automation would
suffer, the manual testing would suffer, or both would suffer.\
\
-T.J. Maher\
 Sr. QA Engineer, Fitbit\
* // Manual tester, 15 years*\
* // Automated tester for \[ 6 \] months and counting*\
\
*Please note: \'Adventures in Automation\' is a personal blog about
automated testing. It is not an official blog
of [Fitbit.com](http://www.fitbit.com/). *\
\