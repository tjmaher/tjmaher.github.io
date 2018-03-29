\-\-- layout: post title: Notes on Accelerating DevOps Collaboration
with Sauce Labs & JIRA date: \'2016-05-03T18:14:00.000-04:00\' author:
T.J. Maher tags: - DevOps - JIRA - Sauce Labs modified\_time:
\'2016-05-04T13:00:20.781-04:00\' thumbnail:
https://i.ytimg.com/vi/G0Xz-zadb6k/default.jpg blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-4773736605149456351
blogger\_orig\_url:
http://www.tjmaher.com/2016/05/notes-on-accelerating-devops.html \-\--
**Name**: Accelerating DevOps Collaboration with Sauce Labs & JIRA\
**Date:** *Tuesday, May 3, 2016, 2:00 pm*\
**Webinar Host**: [Sauce Labs](https://saucelabs.com/)\
\

### About the Webinar:

\
\"Software Development teams are looking for ways to speed up their
development process while maintaining high quality applications. In
order to help meet this challenge, Sauce Labs is proud to announce the
release of the first automated test cloud integration with Atlassian\'s
JIRA.\
\
\"The Sauce Labs Plugin for JIRA allows JIRA users to increase the speed
of their development cycles while maintaining quality and reducing cost.
The plugin seamlessly connects the rich testing metadata that Sauce Labs
provides with an organization\'s JIRA instance. Teams who are looking to
adopt DevOps/Continuous Delivery practices for the first time will find
this tool especially compelling\".\
\
[]{#more}\
\

\
*Conference Video:
[YouTube](https://www.youtube.com/embed/G0Xz-zadb6k)*\
\

::: {style="margin-bottom:5px"}
**[Accelerating DevOps Collaboration with Sauce Labs and
JIRA](//www.slideshare.net/saucelabs/accelerating-devops-collaboration-with-sauce-labs-and-jira "Accelerating DevOps Collaboration with Sauce Labs and JIRA")**
from **[Sauce Labs](//www.slideshare.net/saucelabs)**
:::

\

### The Software Journey and DevOps

\
According to the moderator of the webinar, it used to be that Dev, Ops,
and QA were in separate silos, with *Waterfall* and long release cycles.
\"To get people closer to Agile, they might attempt *Fast Waterfall*,
where automated testing begins. Then, Dev, Ops, and QA start to
communicate\".\
\
*Note:*\

-   ***DEV**: The Software Engineers / Software Developers on the team*
-   ***OPS**: Operations team for the Software and Software Environment*
-   ***QA**: Software Quality Assurance, the manual testers*

\
\
The webinar moderator noted that there are too other stages once a
development team moves from Waterfall and Fast Waterfall to become truly
Agile:\
\

-   **Continuous Integration** has a full adoption of Agile. Automated
    tests dominate\... and manual testing is just for debugging. Dev,
    Ops, and QA collaborate closely. 
-   **Continuous Delivery**: Dev, Ops, and QA functions merge into one
    team. Releases are up to almost ten times a day. 

\

<div>

### Automated Testing with Sauce

\

<div>

Jack Moxon, a Product Manager at Sauce Labs for the past four years,
introduced Sauce. Sauce is a Cloud based product 700 different browsers
and platforms. It is easy to configure: There is a Selenium wrapping
script where you can point the script to Sauce Labs to use their cloud
based virtual environment. 

</div>

<div>

\

</div>

<div>

Jack mentioned these virtual environments cover not just varieties of OS
and browsers, but mobile devices, too. The Virtual Machines (VMs) are
\"secure\" and \"pristine\". The Virtual Machine is spun up only when it
is used in a browser or mobile device test, and is destroyed right
after.

</div>

<div>

\

</div>

### Full Disclosure: I Love Sauce Labs!

\

<div>

Full disclosure: I have loved Sauce Labs ever since we started using it
at work last June. I love it and have the T-Shirt. Literally.

</div>

<div>

\

</div>

<div>

Last summer, they had an ad campaign: **testAllTheThings( )!** When I
saw the T-Shirt slogan from my Twitter feed, I knew I had to have that
shirt. I bugged them on Twitter, and they sent me one. 

</div>

<div>

\

</div>

<div>

Why do I love Sauce Labs\' products so much? Because I *hate* regression
testing. Sauce Labs provides a solution to the worst part of software
testing: Running regression tests on the entire browser test suite.

</div>

<div>

\

</div>

<div>

With regression testing, after all the new changes have been deployed to
the final testing environment, the QA Engineers need make sure that the
entire regression test suite works on Chrome, then on  Firefox, then IE
11, then IE 10, IE 9, and even IE 8. You fire up the first test in the
browser, and proceed to follow the manual test case designed. You just
start pointing-and-clicking away, entering in test data just as the
customer will be doing, hoping that you don\'t leave out a step in the
test case and possibly miss a bug. You run all the tests for the PC.
Then run all the steps for the Mac. And it takes a week or so to process
everything, even when doing side-by-side browser testing. 

</div>

<div>

\

</div>

<div>

Sauce Labs isn\'t a magic bullet. Sauce Labs isn\'t \"write once, run
anywhere\" when it comes to writing browser tests. This is more the
fault of ancient browser wars, when Microsoft was still trying to set
the standard \-- not be \"browser standard\" \-- back in the days of
Microsoft Internet Explorer 8, 9, and 10. 

</div>

<div>

\

</div>

<div>

Sauce Labs not only runs all my browser tests, they also shows what
happens when, screenshot by screenshot. Need to see what happened when
the test ran? You can also show a video about exactly what the test was
doing. They do have logs and metadata you can review to diagnose what
went wrong in a test, but I generally find their screenshots the most
helpful, checking to see if there were any error messages that popped up
just before the browser test failed.

</div>

<div>

\

</div>

### New Feature: JIRA Integration 

\

<div>

There is a new free feature Sauce Labs offers: A new [Sauce Labs Plugin
for
JIRA](https://marketplace.atlassian.com/plugins/sauce-jira-integration/cloud/overview).
Once you run the tests, you can combine all the information Sauce Labs
gathered during the test, using [Atlassian
JIRA](https://www.atlassian.com/software/jira) as an output source. 

</div>

<div>

\

</div>

<div>

\... Hrm\... this Sauce Labs plugin is only good for Atlassian Cloud and
JIRA Cloud. I wonder what we use at work?

</div>

<div>

\

</div>

<div>

We use JIRA at work for many thing at my workplace: We track how our
many software projects are going. We keep track the condition of the
sprint: How many tasks are In Progress, how many tasks are Resolved, how
many tasks are To Do. We also use JIRA for bug tracking.

</div>

<div>

\

</div>

<div>

With the Sauce Labs Plugin, you can take all the information collected:
Logs, screenshots, and videos, and collect it and use it in JIRA. 

</div>

<div>

\

</div>

<div>

Jack Moxon gave a demo: If you find in the Sauce Labs Dashboard a
failing test, you can drill into the failing test, examine to see if it
is a bug.  

</div>

<div>

\

</div>

<div>

<div>

When the plugin is installed and set up by the Atlassian manager at your
manager with your Sauce Labs credentials, a new button appears above the
screenshots and videos: \"Create JIRA Issue\".

</div>

<div>

\

</div>

<div>

Within the Sauce Labs application, you can automatically create a new
JIRA ticket: 

</div>

<div>

-   Select from the list of your projects in JIRA.
-   Choose to include Current Screenshots, Videos, Sauce Logs, and
    Selenium Logs. 
-   Set the Issue type such as \"Bug\".
-   Add a Summary.
-   Add a Description.

</div>

<div>

\... As soon as you submit the entry, the JIRA Link is now embedded into
Sauce labs.

</div>

<div>

\

</div>

<div>

Jack was mentioning to do setup on the Sauce Labs master account, so
that sub-accounts can also get permission.  

</div>

<div>

\

</div>

<div>

This plugin is for anybody using JIRA Cloud. The plugins and extensions
are all free. 

</div>

<div>

\

</div>

<div>

You can also follow the same steps when performing manual testing. You
can use their virtual machines to do testing. You can create a new JIRA
task then, too. 

</div>

<div>

\

</div>

<div>

When asked, Jack said that for the first version, you need to create a
new ticket to attach the Sauce Labs artifacts. Later versions, you will
be able to attach them to existing tickets. 

</div>

<div>

\

</div>

### Documentation

\

<div>

Jack mentioned that there is written documentation on Sauce Labs\' Wiki.
You can go to the page **Sending Test Results to JIRA**:
<https://wiki.saucelabs.com/pages/viewpage.action?pageId=63478885>

</div>

<div>

\

</div>

### Have a Suggested Feature? Go to Aha! 

\

<div>

\

</div>

</div>

<div>

<div>

Want to suggest new features for Sauce Labs? Go to Sauce Labs\' AHA!
page at [http://saucelabs.ideas.aha.io](http://saucelabs.ideas.aha.io/)
. 

</div>

<div>

\

</div>

</div>

<div>

<div>

\- T.J. Maher

</div>

<div>

  Sr. QA Engineer, 

</div>

<div>

  Fitbit-Boston

</div>

<div>

\

</div>

<div>

*// QA Engineer since Aug. 1996 *

</div>

<div>

*// Automation developer for \[ 1 \] year and still counting!*

</div>

</div>

</div>

<div>

\

</div>

<div>

\

</div>

<div>

\

</div>
