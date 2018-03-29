\-\-- layout: post title: Stories of Software Testing during the 1990s
Dot.Com Boom date: \'2017-08-16T08:00:00.000-04:00\' author: T.J. Maher
tags: modified\_time: \'2017-08-17T08:19:08.986-04:00\' blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-853143281386866990
blogger\_orig\_url:
http://www.tjmaher.com/2017/08/qa-department-on-its-own-software.html
\-\-- I\'ve heard it said, by [Gerald
Weinberg](http://joecolantonio.com/testtalks/100-testing-harder-developing-gerald-weinberg/),
when forming  the first team dedicated to quality and testing for NASA's
Project Mercury in the late 1950s as Manager of Operating Systems
Development, that every person on his quality team was a computer
programmer. The software quality assurance engineer role as we now know
it was never meant to be a non-coding one\... Decades after, it just
happened that way out of necessity.\
\
Although it may be fitting, then, that the lines between development and
QA are blurring together, as witnessed by developments at such companies
as Microsoft, Google and Spotify, this provides little solace for us QA
engineers who once again must navigate a new landscape that market
forces have blown together, and confront the new job requirements.\
\
[]{#more}\
\

-   *Read about how Google has been influencing the software industry
    here in the United States with free chapters of **How Google Tests
    Software** (2012), on Google Books, "[Chapter 2: The Software
    Engineer in
    Test](http://books.google.com/books?id=VrAx1ATf-RoC&pg=PA15)\" and
    "[Chapter 3: The Test
    Engineer](http://books.google.com/books?id=VrAx1ATf-RoC&pg=PA75)"*
-   *Listen to Paul Gerrard on the Test Talks podcast talk about
    developers having to tackle testing in "[Shift Left - A New Model
    For
    Testing](http://joecolantonio.com/testtalks/42-paul-gerrard-shift-left-a-new-model-for-testing/)
    (March 2015)"*

The good thing is that this time around, Dev and QA work are working
side-by-side and learning from each other. That wasn\'t always the
case.\
\
\

Dev and QA: Literally Worlds Apart in the 1990s
-----------------------------------------------

\
Back in 1996  I started out working as a contract consultant in the
software industry to see how I might apply my computer science degree.
It was the year after \"dot coms\" and the investors irrationally
supporting them entered the fray. I instantly fell in love with software
testing as a QA engineer. I loved carefully reading the requirements for
the project I was on, and seeing if there were any gaps as I manipulated
the web-based product through the browser. It was intriguing, seeing if
I could figure out an unplanned path through the system, causing the
program to act in unexpected ways or even crash.\
\
Coding was not a job requirement.\
\
Demand for coders had far surpassed the supply. It would have been quite
expensive at the time to have teams of developers on standby to
investigate how a web-based product operated in Netscape Navigator,
Internet Explorer, Opera, and Safari for the Mac and PC. And new browser
versions with new features were being released at a rapid pace as
Netscape and Microsoft competed to see who would have their way of doing
things recognized as the new standard.\
\
To be a QA Engineer, you had to be technologically savvy, smart,
diligent, and methodical. You didn\'t have to have a Computer Science
degree. A candidate with an English degree or a history degree involving
research did nicely. You had to examine the business requirements and
turn them into test plans, sketching out what needed to be tested, test
cases that could be reviewed, and then manual test scripts other junior
level QA Engineers could execute.\
Dev and QA operated quite differently than they do now.\

-   DEV and QA didn\'t work side-by-side. Each discipline operated
    inside its own department, communicating mainly through the
    bug-tracking system. QA was a team apart. Months would go by and you
    might not see a developer. 
-   During this time, QA was a department without a history. Outside
    training and networking were for developers, not for QA. 
-   Most of DEV and QA were not privvy to the early discussions on what
    the software product was supposed to look like or how it was
    supposed to behave.

The main problem was that although projects grew smaller, the
development process became too cumbersome. During each phase of the
project --- Requirements, Design, Implementation, Verification and
Maintenance --- artifacts and deliverables such as project plans,
technical specs and database design documents would cascade down to the
next phase of the project in a linear fashion, without the DEV or QA
teams being able to give their input. This was dubbed the \"Waterfall
Method\" of Software Development.\

Waterfall introduced new problems for QA 
-----------------------------------------

\
In the waterfall approach to development, business analysts in the
requirements phase would draft documents detailing the requirements of
the software product they would build, the purpose of the product, a
software requirements specification detailing a checklist of business
requirements, a high-level description of the system.\
\
This would be handed off to the software architects who in
the Design phase would write the blueprints for the product. Each
software component would be sketched out, and the data structure of the
database would be designed.\
\
In the Implementation phase, the software developers would construct the
software product.\
\
Then, in the Verification phase, software testers would create test
plans to describe a high-level approach on how to test. Once approved,
test cases detailing more on what would be tested, and once those were
approved testers would generate test scripts listing step-by-step how
they would go about testing the product. Hopefully, by the time the
product was ready for testing, the test plans, test cases, and test
scripts would all be written.  \
\
In the Maintenance phase, the software product would be released into
the wild. The customers would use the product, and any questions,
complaints, and other feedback would be gathered to help improve the
next version of the product.\
\
There were many problems Quality Assurance encountered with this
method.\

-   What if the reason a bug occurred was because the spec or the design
    of the software product was unclear? As a QA Engineer, you could try
    to independently read through all the previous stages deliverables
    on your own as they were released, to try to get a feel for the
    purpose of the software product \... but QA wasn\'t actively
    involved until the project was almost finished. 
-   What happens if all the preceding stages took longer than what was
    scoped out? It would always be easier for the time allotted for QA
    to be scaled back than to push back the release date. Sometimes the
    best you could do was to record all bugs found, triage them, and try
    to get them fixed in the next iteration of the product. 
-   What if there were last minute change orders? Are the test plans,
    test cases, and test scripts still valid when the official
    validation period starts? 

Development and Quality Assurance were not then integrated with one
another, fostering in some places that I had worked as a consultant an
\"Us vs Them\" mentality.\

Agile: Bringing DEV and QA together
-----------------------------------

\
Life became better for the QA Engineer under the [Agile Software
Development
Methodology](https://techbeacon.com/agility-beyond-history%E2%80%94-legacy%E2%80%94-agile-development).
The same system that was developed to empower software engineers helped
empower QA Engineers.\

-   Whether we are examining the size and scope of our two week sprints,
    examining each story we need to complete, or talking in our scrum
    about what we did yesterday, what we are planning on working on
    today, we are working side-by-side with developers. 
-   Working side-by-side, DEV and QA can appreciated each others skill
    sets, and learn from each other, seeing exactly what it takes to
    code, and what it takes to test. 

As I wrote in [How to pass a coding interview as an automation
developer](https://techbeacon.com/how-pass-coding-interview-automation-developer),
I have personally seen the bar being raised for QA positions. Perhaps
we, DEV and QA, can help each other prepare for this future together.\
\
\
Happy Testing!\
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
