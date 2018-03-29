\-\-- layout: post title: Thoughts on the Second Annual \'State of
Testing\' Survey Results released by Sauce Labs date:
\'2016-02-04T00:23:00.001-05:00\' author: T.J. Maher tags: - industry -
Test Talks - Joe Colantonio - Sauce Labs modified\_time:
\'2016-04-29T07:40:34.521-04:00\' thumbnail:
https://4.bp.blogspot.com/-wfINruaejtI/VrLecZbvIiI/AAAAAAAAK4E/VTsi68t2eGY/s72-c/deployment.png
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-6953058296301228503
blogger\_orig\_url:
http://www.tjmaher.com/2016/02/problems-with-second-annual-state-of.html
\-\-- What is the relationship at your company between DEV and QA like:\

-   **Artist** and **Art Critic**?
-   Or **Writer** and **Copyeditor**?

\
According to Sauce Labs\' *Second Annual \'State of Testing Survey\'*
released a few days ago, testers are more than likely to find the latter
instead of the former.\
\
Why? In a word: **Agile**.\
\
[]{#more}\
\

### What is Waterfall and Agile?

\
Back when I first started my career in the software testing industry, we
used what was known as the **Waterfall Method** to develop software.
 Teams of business analysts figured out the requirements and design the
architecture of the product, who would hand it off to the designers who
would hand their work to the developers, who would then send their
finished work to the testers. Some companies looped in the testers in
their planning meetings, involving them into the meetings. Some did not,
making the tester\'s life quite interesting.\
\
That changed with the **Agile Software Development Methodology**.
Testers, developers, and designers scoped out, as a team, how to
implement every two weeks the business requirements the product owner
suggested.\
\

-   Read more about Agile on [my
    blog](/2015/01/agile-software-development.html)  

\

### Agile Pros and Cons

\
Agile Software Development became a mixed blessing for testers:\

-   **PROS**: Testers are now a valued member of the software
    development team.
-   **CONS**: No time to carefully draft and execute suites of
    regression test plans, verifying that adding the new stuff that the
    old stuff didn\'t break. 

\
Just before releasing an updated version of the web application, I\'d
lead the QA team in executing the extensive browser testing suite I
drafted. We\'d use a mouse and keyboard to point-and-click their way
through the series of tests again, and again, and again, and again with
Chrome, Firefox, Microsoft Internet Explorer version and all its
versions from IE8 to IE10. It would be a very tedious one or two weeks.\
\
Automated testing fixes this: Develop an automated test suite for the
various browsers and platforms using tools such as Selenium WebDriver\
\

-   **PROS**: Goodbye manual regression test suite!
-   **CONS**: Hello configuring all the browser and platforms in your
    testing environment!

\

### How Sauce Labs Helps Agile

\
Sauce Labs provides automation developers with an online suite of
browsers, operating systems, and mobile devices where they can execute
their automated tests. Sauce Labs is very active in the testing
community from running their own testing blog,
[SauceIO](http://sauceio.com/) and sponsoring software testing podcasts
such as *Test Talks with Joe Colantonio* at
<http://joecolantonio.com/testtalks/>.\
\

### Sauce Labs and the \'State of Testing\'

**Press Release**: *Sauce Labs Releases Second Annual 'State of Testing'
Survey Results*\
<https://saucelabs.com/press-room/press-releases/sauce-labs-releases-second-annual-state-of-testing-survey-results>\
\

> *\"SAN FRANCISCO -- Jan. 26, 2016 - Sauce Labs, Inc., provider of the
> world's largest cloud-based platform for automated testing of web and
> mobile applications, today announced the results of an independent
> survey titled, [\'Testing Trends in 2016: A Survey of Software
> Professionals\'](https://saucelabs.com/resources/white-papers/sauce-labs-state-of-testing-report-2016.pdf).
> The survey, conducted by Dimensional Research, reveals that while 88
> percent of organizations say they have adopted agile development, only
> one in five have fully implemented the five best software testing
> practices typically associated with a mature agile development
> process.*\
> \
> *\"The report, commissioned by Sauce Labs, represents the company's
> second annual \'State of Testing\' research report, and is designed to
> better understand current trends in delivering high quality web and
> mobile applications. Covering topics such as agile software
> development, modern testing techniques, Continuous Integration (CI),
> and cross-browser test coverage, the report stems from a survey
> conducted in December 2015\".* (Read
> [MORE](https://saucelabs.com/press-room/press-releases/sauce-labs-releases-second-annual-state-of-testing-survey-results))

\
**Whitepaper**: *Testing Trends in 2016: A Survey of Software
Professionals*\
\
The document, \"*Testing Trends in 2016: A Survey*\", is at
<https://saucelabs.com/resources/white-papers/sauce-labs-state-of-testing-report-2016.pdf.>
(12 pages)\
\

\

### About the Whitepaper

\
Dimensional Research interviewed 520 \"software professionals
responsible for the quality of web applications. The goal of this global
survey was to understand current trends in testing online environments.
Certain questions were repeated from a similar survey conducted to the
same audience one year ago to allow for trend analysis\".\
\
Two things jumped out at me after reading Sauce Labs\' survey:\
\

-   Agile is the way to go for us Software Quality Assurance Engineers,
    since \"86% report development and QA teams think of themselves as
    partners\"
-   Sauce Labs has a darned high bar with what they think of as
    \"embracing Agile\".

<div>

\

</div>

<div>

Once you have an automated test suite, you can set up:

</div>

<div>

-   A small sample of tests to run against new code as soon as
    developers check in their code. 
-   A larger set of tests to run against hourly builds to a testing
    environment that is similar to production, but with the dependencies
    scaled back. 
-   Just before a release to the production environment, the code can
    then be deployed and tested against an exact clone of the production
    environment.    

</div>

Think of it as a bug filtration system. First you perform a sanity
check. Then you  putting the code through its initial paces. Then you
test it on a close a simulation on the live environment we can get.\
\

  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://4.bp.blogspot.com/-wfINruaejtI/VrLecZbvIiI/AAAAAAAAK4E/VTsi68t2eGY/s640/deployment.png){width="640" height="264"}](http://4.bp.blogspot.com/-wfINruaejtI/VrLecZbvIiI/AAAAAAAAK4E/VTsi68t2eGY/s1600/deployment.png)
                              *According to the [Survey](https://saucelabs.com/resources/white-papers/sauce-labs-state-of-testing-report-2016.pdf), people do weekly builds, but they wish for daily.*
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

\
If you have the automated deployment and testing system uses a Release
Engineer who examines the results of the test before deployment, it is
**Continuous Development**. If it goes right on through to Production,
in is **Continuous Integration**.\
\

  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://4.bp.blogspot.com/-BFr8AdR9iLE/VrLdD_Y10tI/AAAAAAAAK34/vSK-0I3L4jw/s640/How%2BHas%2BTesting%2BChanged.png){width="640" height="256"}](http://4.bp.blogspot.com/-BFr8AdR9iLE/VrLdD_Y10tI/AAAAAAAAK34/vSK-0I3L4jw/s1600/How%2BHas%2BTesting%2BChanged.png)
                                                              *Taken from Sauce Labs \'[State of Testing](https://saucelabs.com/resources/white-papers/sauce-labs-state-of-testing-report-2016.pdf)\' Report*
  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

\
\
As far as I knew, Continuous Integration was a supplement to the Agile
Development Process. Agile was about co-workers being able to take
charge of their own work schedule, contributing to a team.\
\

::: {style="text-align: -webkit-center;"}
:::

::: {style="text-align: right;"}
[**\"Individuals and interactions over processes and
tools.**]{style="font-size: large;"}
:::

::: {style="text-align: right;"}
[**Working software over comprehensive
documentation.**]{style="font-size: large;"}
:::

[]{style="font-size: large;"}\

::: {style="text-align: right;"}
[**Customer collaboration over contract
negotiation.**]{style="font-size: large;"}
:::

[]{style="font-size: large;"}\

::: {style="text-align: right;"}
[**Responding to change over following a
plan. **]{style="font-size: large;"}\
[**That is, while there is value in the items on [**the
right, **]{style="font-size: large;"}**]{style="font-size: large;"}\
[**[**we value the items on the left
more\"**]{style="font-size: large;"}.**]{style="font-size: large;"}
:::

[]{style="font-size: large;"}\

::: {style="text-align: right;"}
\- The [Agile Manifesto](http://www.agilemanifesto.org/) (2001)
:::

\
\
\... Agile isn\'t about any particular *toolset*. It\'s about a
**mindset**.\
\
This is why I found the survey results a bit odd. The survey claims that
there are certain Agile best practices that they believe should be
followed to achieve \"agile testing maturity\". Some points, I agree
with. Some, not so much. The survey found:\
\

-   *\"23% fix bugs right away*
-   *\"24% iterate small testable requirements rather than waiting for
    features to be completed*
-   *\"26% have more automated testing than manual*
-   *\"77% of the development and QA teams communicate in real-time*
-   *\"86% report development and QA teams think of themselves as
    partners\"*

<div>

With Agile, DEV and QA are equal partners \-- finally! We are on the
same team. We attend the same quick ten minute morning meetings that we
call scrum\... just a quick huddle to talk about what we worked on
yesterday, what we were working on today, and if there are any
roadblocks. 

</div>

<div>

\

</div>

### Bugs Should Be Fixed Right Away, Else It Ain\'t Agile?

<div>

\

</div>

<div>

But why the heck should all bugs be fixed right away? Who determined
this was a *\"best practice\"* in Agile?\
\

::: {.separator style="clear: both; text-align: center;"}
[![](https://2.bp.blogspot.com/-eOnMTDcuDOI/VrLf33gsz9I/AAAAAAAAK4Q/OgKYQnat8-s/s400/bugs%2Bfixed.png){width="400"
height="195"}](http://2.bp.blogspot.com/-eOnMTDcuDOI/VrLf33gsz9I/AAAAAAAAK4Q/OgKYQnat8-s/s1600/bugs%2Bfixed.png)
:::

\

</div>

<div>

\

</div>

<div>

When triaging a bug, it is important to measure two quantities to
perform a risk assessment:

</div>

<div>

-   A\) **Severity**: How disastrous to the business would it be if the bug
    happened? (Score 1 to 5)
-   B\) **Frequency**: What are the chances of the bug happening?  (Score 1
    to 5)

<div>

A \* B = Risk Score. This determines the **priority**.  

</div>

</div>

<div>

\

</div>

<div>

If there is a very slim chance of a disastrous bug happening, or there
is a bug that always happens with, say, by a small subset of the number
of users of the web or mobile app, it shouldn\'t get a high priority.
Yes, we should record the exact steps to reproduce the problem. Yes, we
should get the system conditions when the bug happened. But there may be
bigger fish to fry. Not all bugs can get fixed immediately. It
completely depends on the team\'s bandwidth, and the risk score of the
bug. 

</div>

<div>

\

</div>

### Testing Should Be Highly Automated, Else It Ain\'t Agile?

<div>

\

</div>

<div>

I hate to break it to Sauce Labs, since I love how they are supporting
our testing community, but I think they are completely wrong on this
point. 

</div>

<div>

\

</div>

<div>

Automation is not the end-all-and-be-all. It can\'t be. The code that is
an automated test should be treated like production code. It takes time
to analyze it, refactor it, clean it up, and have a peer review process
as some type of code review. 

</div>

<div>

\

</div>

<div>

When new functionality is built into a product, we need a nimble team of
manual testers to spearhead the testing process, brainstorming right
along with the developers, exploring all technical aspects of what is
being built. As the developers are asking *\"How the heck do a BUILD
this?\"* the QA Team needs to ask *\"How the heck do I TEST this?\".*
The automated testers can also ask, *\"\... And how do I automated these
tests?\"* getting the information straight from the sources, but I think
it is a mistake to start developing code when the manual test team is
still attempting to decide on an approach. 

</div>

<div>

\

</div>

<div>

As an automation developer, I believe it is my job to take the largest
pain points away from the manual test team. What is the most mundane,
routine tests that are lengthy, boring, and repetitive, thus the most
prone to human error? The answer to that question should determine what
should be automated. 

</div>

<div>

\

</div>

<div>

Automation can not solve everything: It can\'t tell if the User
Interface is intuitive or not, or if it is well designed, or what the
User Experience is like. An automated test can only find if A, B, or C
is working. A trained manual tester can find the unknowns using user
profiles, knowledge of the system, and instinctive hunches and guesses
to test the system. 

</div>

<div>

\

</div>

<div>

   

</div>

<div>

[-T.J.
Maher]{style="background-color: white; color: #222222; font-family: "calibri"; font-size: 15.4px; line-height: 21.56px;"}\
* Sr. QA Engineer, Fitbit*\
* Boston, MA*\
*\
// Automated tester for \[ 11 \] month and counting!*\
*\
Please note: \'Adventures in Automation\' is a personal blog about
automated testing. It is not an official blog
of [Fitbit.com](http://www.fitbit.com/). *

</div>
