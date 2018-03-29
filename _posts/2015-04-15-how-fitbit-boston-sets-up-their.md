\-\-- layout: post title: How Fitbit - Boston sets up an automation
development environment date: \'2015-04-15T09:56:00.000-04:00\' author:
T.J. Maher tags: - Fitbit-Boston modified\_time:
\'2016-04-29T00:03:20.789-04:00\' blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-1636163908959214445
blogger\_orig\_url:
http://www.tjmaher.com/2015/04/how-fitbit-boston-sets-up-their.html
\-\-- Without actually having an automation developer position, it was
very difficult for me to figure out what tools I needed to learn in
order to make the switch from being a manual tester to doing
automation.\
\
Here, in this post, I\'ll highlight a bit of of the tools and
technologies Fitbit - Boston uses for automated testing.\
\
[]{#more}\
\

### Development Platform

<div>

-   MacBook Pro with OS X Yosemite (10.10)

</div>

<div>

My first day at Fitbit was like Christmas. A new job, new colleagues,
new Fitbit swag, and a brand new MacBook Pro with the plastic wrapping
still on it. It was amazing to unbox and set it up. Fitbit was the first
company where my my primary work computer was from Apple. Even though my
position for the past four years at my last company was mobile IOS
testing and I knew my way around a Macbook in general, it is completely
different making a Macbook my primary machine. 

</div>

<div>

\

</div>

<div>

As a manual tester, the tester works with the web application exactly
like the end-user would, operating the web app in a browser with a
keyboard and a mouse testing the user interface. Testing graphical user
interfaces \-- how the web app looks and feels \-- locks you in that
mindset.\
\
As an automated tester, I find I am more like software developer, really
needing to know my way around a Unix Command Line Interface. I have had
some familiarity with Mac\'s Terminal and the basic Unix commands when
kicking off and running the mobile automation scripts at my last
position, and back during grad school, but it wasn\'t something I have
used all the time, so it is a bit of a learning curve. 

</div>

<div>

\

</div>

### Software Testing Framework

<div>

-   Selenium WebDriver w/ Java 8 
-   TestNG

</div>

<div>

When I was job interviewing, I found that although some companies were
using Selenium WebDriver with Python, one of them was using Selenium
WebDriver with Ruby, most of them seemed to pair the Selenium WebDriver
API with the latest version of the Java programming language, Java 8..

</div>

<div>

\

</div>

<div>

If you are a manual tester who is unfamiliar with programming, make sure
to take a course in Java. You won\'t need to know the language as well
as if you were developing software, but you will need to know *if*
statements, the basics of object oriented programming, methods, lists,
etc in Java. Online courses are offered everywhere. Since Advanced
Programming in Java 1 & 2 was almost ten years ago for me, those and
Alan Richardson\'s book [Java for
Testers](http://www.javafortesters.com/) was a good resource to get back
in the swing of things. 

</div>

<div>

\

</div>

<div>

The biggest help for me in regards to Selenium WebDriver instruction was
Alan Richardson\'s online course [Selenium 2 WebDriver with
Java](http://courses.compendiumdev.co.uk/courses/selenium-2-webdriver-with-java).
Although it is \$299, it is well worth the money. I\'ve gone back to
this course many times since I first purchased it on Udemy.com back in
Christmas 2013. I find that I review them again and again. This course
won \"Best Tutorial\" when it was co-presented by Alan and Simon Stewart
\-- the creator of WebDriver \-- back at the [EuroSTAR Software Testing
Conference of
2012](http://conference.eurostarsoftwaretesting.com/event/2012/selenium-clinic/).\
\
For unit testing, Fitbit uses TestNG instead of JUnit to set up *\@Test*
but the two are similar enough in how it is used for automated testing. 

</div>

<div>

\

</div>

### IDE

<div>

-   IntelliJ Ultimate Edition

</div>

<div>

\

</div>

<div>

For an Integrated Development Environment (IDE) Fitbit - Boston uses
IntelliJ\'s Ultimate Edition. [IntelliJ Community
Edition](https://www.jetbrains.com/idea/) is just as good, and is free.
The Ultimate Edition seems to integrate database support into the tool. 

</div>

<div>

\

</div>

<div>

For those who are not familiar with working with an IDE, writing code
with an IDE is like writing a thesis paper with Microsoft Word. Yes, you
can use a simple text editor to write code, but there is something to be
said for all the tools such as the auto-complete features and tools to
help you refactor code. 

</div>

<div>

\

</div>

<div>

If you need help getting started and setting up IntelliJ with Selenium
WebDriver, there is a free course on Alan Richardson\'s site, Selenium
Simplified, [Get Started With Selenium WebDriver Using Maven, IntelliJ
and Java](http://seleniumsimplified.com/get-started/), which can walk
you through setting up your testing environment. 

</div>

<div>

\

</div>

<div>

Another top IDE I have come across being used in automated software
testing: [Eclipse](https://eclipse.org/downloads/). As a coding novice
who hasn\'t done much professional software development as of yet, they
seem pretty similar. This was used in my last position.  \
\

### Source Control

\
When many people are working on a project at the same time, it helps
organize the process to use Source Control. What is it? According to
[Git-SCM](http://git-scm.com/book/en/v2/Getting-Started-About-Version-Control):\
\

> What is "version control", and why should you care? Version control is
> a system that records changes to a file or set of files over time so
> that you can recall specific versions later. \[Y\]ou \[\...\] use
> software source code as the files being version controlled, though in
> reality you can do this with nearly any type of file on a
> computer.[ ]{style="background-color: transparent;"}

> If you are a graphic or web designer and want to keep every version of
> an image or layout (which you would most certainly want to), a Version
> Control System (VCS) is a very wise thing to use. It allows you to
> revert files back to a previous state, revert the entire project back
> to a previous state, compare changes over time, see who last modified
> something that might be causing a problem, who introduced an issue and
> when, and more. Using a VCS also generally means that if you screw
> things up or lose files, you can easily recover. In addition, you get
> all this for very little overhead.

\
At my last company, we used TortoiseSVN to check code in and out of
Subversion, a code repository site.\
\
At Fitbit we use [Git](http://git-scm.com/docs/) to check code into and
out of Stash, an Atlassian product, the makers of Jira (for bug
reporting) and Confluence (a document repository).\
\
If you are not familiar with Git or source control, feel free to read
[Git-SCM: Getting Started: Git
Basics.](http://git-scm.com/book/en/v2/Getting-Started-Git-Basics)

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

<div>

-T.J. Maher\
* Sr. QA Engineer, Fitbit*\
* Boston, MA*

</div>

<div>

  

</div>
