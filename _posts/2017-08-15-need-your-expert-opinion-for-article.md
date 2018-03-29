\-\-- layout: post title: \'Need your expert opinion for an article:
What happens to the QA Role in a Continuous Deployment environment?\'
date: \'2017-08-15T19:29:00.001-04:00\' author: T.J. Maher tags:
modified\_time: \'2017-08-21T21:33:46.935-04:00\' blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-5191756623420877302
blogger\_orig\_url:
http://www.tjmaher.com/2017/08/need-your-expert-opinion-for-article.html
\-\-- Hello, Dear Reader! I need your expert opinion on a TechBeacon
article I am working on\... Mind if I quote you?\
\
**I\'m trying to research what happens to the QA Engineer role in
software companies that use Continuous Deployment. What does the QA role
morph into, and what skills would the QA Engineer need to develop in
order to survive there? **\
\
In business, there is always an urge to do more with less. Save money.
Reduce headcount. Increase the bottom line. Improve quality. Trim
bloated processes\... And as with all businesses, so goes the software
business. The problem is that here in Boston I worry that the \"bloated
process\" is interpreted as the role of QA Engineer\...\
\
Back in March 2017 at a Ministry of Testing - Boston Meetup, [I bumped
into Andreas Grabner from
Dynatrace](http://www.tjmaher.com/2017/03/how-to-signal-that-build-is-broken-look.html),
who mentioned something regarding Continuous Deployment that as a QA
Engineer for twenty years sent shivers up my spine\...\
\
[]{#more}\
1) Andreas\' company, Dynatrace\... it didn\'t have a QA Department.
According to him, they didn\'t need one. It took a lot of time and
effort, but they engineered it that way. The QA Engineers had been given
thorough training in development,  focusing the quality of their unit
and integration tests. Now, as he put it, if something fails, it is the
individual contributor\'s job to to catch it. If they don\'t catch it,
there is no QA buffer, they hear about it directly from the customer
\... Talk about getting fast feedback!\
\
2) They don\'t just use Continuous Integration, where a release engineer
guided deployments to Production. Dynatrace used the next stage:
**Continuous Deployment**. All code, after passing a battery of
carefully written automatically run unit and integration tests, is
pushed directly into Production.\
\
For more information about this process Dynatrace went through, Andreas
sent this to
me https://www.devopsdays.org/events/2017-toronto/program/andreas-grabner/\
\
To me, unit tests, integration tests, and 100% code coverage couldn\'t
*possibly* be enough. Here\'s why:\
\
Although the quality of the software product is everyone\'s job, to me,
the QA Engineer embedded in an Agile team is the shepherd of the the
quality assurance process, an end-user advocate whose job description is
explicitly tied to creating a mental model of the customer through
examining use cases, each and every feature requirement, and making sure
each acceptance criteria is there in the product.\
\
To me, there is no way for a developer to churn out high-quality
peer-reviewed code with close to 100% code coverage involving the unit
and integration tests, and to *also* test all the different ways the
customer will interact with the product through the many different web
and mobile interfaces.  \
\
Here\'s the thing: I may know how they *used* to do QA before Continuous
Deployment. I don\'t know how companies are doing it *now,* especially
since I have only been an automation developer only for the past two
years. So, I am not certain what to tell members of the [Ministry of
Testing, Boston
chapter](https://www.meetup.com/ministry-of-testing-boston/), where I am
an Organizer, members who are looking to survive the pressures of the
current local job market.\

 **My Questions to You**
------------------------

<div>

\

</div>

Does your company do Continuous Deployment? If so:\

-   Do you think 100% code coverage of unit tests and integration tests
    is enough in environments using Continuous Deployment? What do you
    use as supplements in your testing efforts?
-   How has the QA Engineer role survived as you push to Continuous
    Deployment? Has it? 
-   How has the QA role changed and morphed as you go from CI
    (Continuous Integration, with a Release Engineer) to CD (Look, ma, I
    am pushing to production)? 
-   Does your company still employ traditional manual testers in
    environments with Continuous Deployment is used?

\
Please let me know! And let me know if you mind being quoted for the
article.\
\
Thank you so much!\
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
