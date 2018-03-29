\-\-- layout: post title: Learn a Programming Language by Contributing
to an Open Source Project! One trick to remember if working on an old
Maven project. date: \'2016-11-05T16:48:00.003-04:00\' author: T.J.
Maher tags: modified\_time: \'2016-11-05T16:51:15.169-04:00\'
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-701046009880251205
blogger\_orig\_url:
http://www.tjmaher.com/2016/11/when-running-old-open-source-maven.html
\-\-- I just started a new job as a **Software Engineer in Test** three
weeks ago. The main task right now is to try to get to know the product
as a whole where our SET team will be writing an automated test
framework.\
\

What I Have Been Doing For Work
-------------------------------

\
I\'ve been spending the past few weeks executing huge stack of manual
test scripts, asking the QA Engineers for help executing the test steps,
getting to know both the system, how the system is being manually
tested, and the system\'s documentation at the same time. I\'ve also
been creating onboarding documentation for any other new SET hires that
come after me. If being an Software Engineer in Test doesn\'t work out
(*heaven forbid!*) and every single manual QA job is phased out, I can
start my third career in the software industry as a tech writer.\
\
What I haven\'t been doing yet is coding. The team narrowed down the
automation stack to be Geb + Groovy + Spock, so I have been trying to
learn that during my nights and weekends with little side projects.\
\

My Ongoing Side Projects: Learn Geb + Groovy + Spock
----------------------------------------------------

\

### **[Side Project \#1]{.underline}: Investigating Yeoman**

\

-   Looking into [Yeoman, scaffolding, and other tooling
    application](http://www.tjmaher.com/2016/10/testing-internet-with-geb-groovy-spock.html) to
    figure out how a [Geb + Spock + Groovy project could be
    generated](http://www.tjmaher.com/2016/10/testing-internet-with-geb-groovy-spock_19.html).
-    I still need to take a look at the Gradle setup, how it sets up
    automated tests, and figure out how to modify the code to, say, test
    the functionality of a Login screen

\... This might take me another week to finish up.\
\

### **[Side Project \#2]{.underline}: Contributing Geb + Groovy Tests to Open Source project**

<div>

-   Contributing to someone else\'s open-source automation project. I
    noticed there are automation examples in Java, Ruby, and sometimes
    C\#\... but there aren\'t any in Geb + Groovy + Spock. I wonder if I
    could learn that tech stack by helping out? 

\... Why this side project? \... 

</div>

<div>

\

</div>

Why Contributing to an Open Source Project is a Great Learning Tool \-- Code Reviews!
-------------------------------------------------------------------------------------

<div>

\

</div>

<div>

As an automation developer, the real learning begins\...

</div>

<div>

\

</div>

<div>

\... Not when I am researching how to code the first draft of an
assignment\...

</div>

<div>

\... Not when I am actually writing the code to get the darned thing to
compile\...

</div>

<div>

\... It happens during the **code review**\...

</div>

<div>

\

</div>

<div>

Imagine writing a research paper. You spend a few days gathering
research materials. You sketch out an outline. You spend four or five
hours writing a good rough draft, and submit it to the teacher for
review\... and it is returned to you, covered with annotations and
corrections written in red ink. After the first, second and third draft,
you find out all about incorrect grammar, poor sentence structure, etc.
But through the process you become a better writer.

</div>

<div>

\

</div>

<div>

The same exact process happens when coding. The first time someone
reviews your code, you might be getting more lines of comments than
there are lines of code! It may be painful to go through, having to
re-write everything again and again, but it is helping you up your game.
 

</div>

<div>

\

</div>

<div>

I\'ve spent the past two years being paid to contribute to a
closed-source automated test framework for an eCommerce platform
accessible worldwide. I\'ve made hundreds of contributions to that
project and, let me tell you, going through a code review is never is
easy. Over time it becomes easier. It is all about trying to meet the
team\'s wants and expectations. Over time, you learn. 

</div>

<div>

\

</div>

<div>

This will be my first time contributing to an open-source project. If
you want to learn how to do the same, I have written up instruction
on,\...

</div>

<div>

\

Setting Up an Open Source Project On Your Local Machine 
--------------------------------------------------------

</div>

\
Let\'s say you found on [GitHub](http://www.github.com/) an open-source
project looking for contributors, and you want to contribute:\
\

-   Sign up for an [account on GitHub](https://github.com/join). Me? My
    account is [\@tjmaher](https://github.com/tjmaher).
-   Are you familiar with the command line interface? If not, install
    [GitHub for
    Desktop](https://help.github.com/desktop/guides/getting-started/installing-github-desktop/). 
-   Not familiar with GitHub, repositories, branches, committing changes
    or pull requests? Follow this [Hello World
    walkthrough](https://guides.github.com/activities/hello-world/) that
    GitHub has created.
-   Not familiar with forking other people\'s repositories into your own
    GitHub repository? GitHub has a [forking
    tutorial](https://help.github.com/articles/fork-a-repo/), too. 
-   Go to the GitHub project and [create a fork of their
    project](https://guides.github.com/activities/forking/), copying it
    to your own account on GitHub. 
-   Go to your local computer. Pick a folder or directory to download
    the open source project. I created a subfolder called \"code\" in my
    Home directory, so on my Windows 10 PC, I download everything into
    **C:\\Users\\tmaher\\code** 
-   Clone or Download the project. Set it up to download it using GitHub
    for Desktop. 
-   Think about what micro-additions or subtractions you want to make
    the project. [Make a new branch for that
    project](https://guides.github.com/introduction/flow/). Are you done
    with that small task? Commit your code for that branch. Want to do
    another task? Commit that code, too.
-   Done with the contribution? [Create a pull request for your
    branch](https://help.github.com/articles/about-pull-requests/). It
    will start the code review process.
-   You will start hearing corrections, both major and minor, from other
    contributors. Listen to what they are saying, and learn from them. 

\

So, I Tried Opening The Project In IntelliJ\...
-----------------------------------------------

<div>

I love using **IntelliJ** as an IDE! It has a free Community Edition,
suitable for any Groovy, Gradle, or plain ole Java project. If you want
you can download it
[here](https://www.jetbrains.com/idea/#chooseYourEdition). I have the
latest version, IntelliJ IDEA version **2016.3**.

</div>

\
The project I wanted to contribute to was a few years old, still written
using Apache Maven to handle all the dependencies ( [Read
More](https://maven.apache.org/what-is-maven.html)). When I opened the
project in IntelliJ, and tried to set the project up to recognize the
pom.xml file that was handling all the dependencies\... I found out that
I couldn\'t! Maven just didn\'t exist in IntelliJ! I couldn\'t figure it
out! And I couldn\'t download it as a plugin\...\
\
What the heck? Did IntelliJ switch over completely to
[Gradle](https://docs.gradle.org/current/userguide/introduction.html)?\
\
Oh\... wait a minute\... I found the answer\...\
\
Here is a little Public Service Announcement:\
\

> ::: {dir="ltr" lang="en"}
> PSA: Downloaded new version of
> [\@IntellijIdea](https://twitter.com/intellijidea) 2016.2? Trying to
> run old [\#Maven](https://twitter.com/hashtag/Maven?src=hash) project
> but can\'t? Settings-\>Plugins-\>Maven may be unchecked.
> :::
>
> --- T.J. Maher (\@tjmaher1) [November 5,
> 2016](https://twitter.com/tjmaher1/status/794928315278692353)

\

> ::: {dir="ltr" lang="en"}
> PSA: Running old Maven project in
> [\@IntellijIdea](https://twitter.com/intellijidea)? After adding
> Settings-\>Plugins-\>Maven, right-click on pom.xml and add as a Maven
> project.
> :::
>
> --- T.J. Maher (\@tjmaher1) [November 5,
> 2016](https://twitter.com/tjmaher1/status/794930155030454273)

\
Happy Coding!\
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
