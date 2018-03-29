\-\-- layout: post title: Learning the Command Line Interface date:
\'2015-05-08T20:18:00.003-04:00\' author: T.J. Maher tags: - CommandLine
- courses modified\_time: \'2016-07-03T17:20:14.795-04:00\' thumbnail:
https://1.bp.blogspot.com/-sf0\_pFVkuF4/VUn9zZlYhlI/AAAAAAAAKh0/Fb5J4jrZMXs/s72-c/cli.jpg
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-8328342248290143092
blogger\_orig\_url:
http://www.tjmaher.com/2015/05/learning-command-line-interface.html
\-\-- [When I started my Freshman year at Bridgewater State back on
September 1990 as an eager Computer Science major and computer lab aide,
there were two main platforms that were popular at the time: MS-DOS and
Digital Equipment Corps VAX / VMS system, both which used a command line
inteface (CLI). ]{style="font-family: inherit;"}\
[\
What did they look like?]{style="font-family: inherit;"}\
[\
]{style="font-family: inherit;"}\

-   [The screens had a black
    background. ]{style="font-family: inherit;"}
-   [Green, amber, or white were the font
    colors. ]{style="font-family: inherit;"}

[\
Open up the Terminal on your Mac or Powershell on the PC, maximize the
window to fill the screen, and that is exactly what it was
like. ]{style="font-family: inherit;"}\
[]{style="font-family: inherit;"}\
[]{#more}[\
When I was a computer lab aide, I trained new students using WordPerfect
for MS-DOS, the word processing program we were using at the time. As
clunky as Windows 3.1 was when it came out, I thought it was a great
improvement over the environment we had been using. And when I found a
student job as desktop publisher / graphic artist at the Alumni Center,
and I was able to use a Mac Classic loaded with an early version of
Adobe Photoshop, I thought it was even better. I even loved my Windows
programming class, making a Dungeons and Dragons like game in the style
of Phantasy Star. Once I started using a GUI, I avoided the CLI whenever
possible. When the situation called for it at work, I knew the basics
such as *cd*, *mkdir*, *ls*, etc, but I never became that experienced
with Unix or Linux. ]{style="font-family: inherit;"}\
[\
Recently, I have been brushing up on my CLI skills as part of my quest
to turn myself from a manual tester who can code a bit to being a
Software Engineer in Test. It has certainly takes me back to those early
days!]{style="font-family: inherit;"}\
[\
]{style="font-family: inherit;"}\

### [Not familiar with the Command Line? ]{style="font-family: inherit;"}

[Are you a manual QA Engineer who is more used to the Windows and Mac
environments, but aren\'t really familiar with the Mac Terminal and
it\'s Unix environment? Here are a few good resources I have used to get
a refresher:]{style="font-family: inherit;"}\
[\
**The Command Line Crash Course:**]{style="font-family: inherit;"}\
[[http://cli.learncodethehardway.org/book/]{style="font-family: inherit;"}](http://cli.learncodethehardway.org/book/)\
[\
]{style="font-family: inherit;"}\

::: {.separator style="clear: both; text-align: center;"}
[[![](https://1.bp.blogspot.com/-sf0_pFVkuF4/VUn9zZlYhlI/AAAAAAAAKh0/Fb5J4jrZMXs/s1600/cli.jpg){width="320"
height="260"}]{style="font-family: inherit;"}](http://1.bp.blogspot.com/-sf0_pFVkuF4/VUn9zZlYhlI/AAAAAAAAKh0/Fb5J4jrZMXs/s1600/cli.jpg)
:::

[\
]{style="font-family: inherit;"}\

::: {.separator style="clear: both; text-align: center;"}
:::

[\
\
Brought by the people who wrote \"Learn Python the Hard Way\", this free
e-book guides the complete novice through using the command line
interface on either a Unix / Linux box, or the Mac Terminal. It gives
you basic commands to memorize, and touches upon investigating the file
system, moving files around, and learning to find the built in manuals
to help you. ]{style="font-family: inherit;"}\
[\
\
**Making Flash Cards with Quizlet:**]{style="font-family: inherit;"}\
[[https://quizlet.com/]{style="font-family: inherit;"}](https://quizlet.com/)\
[\
How to sort through all the new terms you may be hearing about for the
first time? After you do the exercises in CLI.LearnCodeTheHardWay.com,
you can use this web based app to create your own set of online flash
cards. ]{style="font-family: inherit;"}\
[\
]{style="font-family: inherit;"}\

::: {.separator style="clear: both; text-align: center;"}
[[![](https://2.bp.blogspot.com/-rO5TvgdU-mI/VU1QoIpVC4I/AAAAAAAAKiw/8ZYftmxnfUw/s320/quizlet.png){width="320"
height="267"}]{style="font-family: inherit;"}](http://2.bp.blogspot.com/-rO5TvgdU-mI/VU1QoIpVC4I/AAAAAAAAKiw/8ZYftmxnfUw/s1600/quizlet.png)
:::

[\
\
There is a corresponding iPhone app for Quizlet. During my morning
commute, I go through the list to see what I remember. You can guess
them from the front view or the back view, flipping them around by
tapping on the screen. ]{style="font-family: inherit;"}\
[\
My favorite way of using the app is to try to remember what Linux
commands to type in. ]{style="font-family: inherit;"}\
[\
]{style="font-family: inherit;"}\

::: {.separator style="clear: both; text-align: center;"}
[[![](https://2.bp.blogspot.com/-4qZkqgwsTTQ/VU1ReoV35dI/AAAAAAAAKi4/C333SdGj8gg/s320/guess.png){width="320"
height="209"}]{style="font-family: inherit;"}](http://2.bp.blogspot.com/-4qZkqgwsTTQ/VU1ReoV35dI/AAAAAAAAKi4/C333SdGj8gg/s1600/guess.png)
:::

[\
\
By the way, the answer is:\> *mv a.txt
b.txt*]{style="font-family: inherit;"}\
[\
\
\
\
**Ryan\'s Tutorials: Linux Tutorial**]{style="font-family: inherit;"}\
[[http://ryanstutorials.net/linuxtutorial/]{style="font-family: inherit;"}](http://ryanstutorials.net/linuxtutorial/)\
[\
]{style="font-family: inherit;"}\

::: {.separator style="clear: both; text-align: center;"}
[[![](https://4.bp.blogspot.com/-kbI6fA9bCxA/VUn9bwOXNNI/AAAAAAAAKhs/Rez1PN0fHn8/s1600/Ryan.jpg){width="320"
height="260"}]{style="font-family: inherit;"}](http://4.bp.blogspot.com/-kbI6fA9bCxA/VUn9bwOXNNI/AAAAAAAAKhs/Rez1PN0fHn8/s1600/Ryan.jpg)
:::

[\
Made it through the beginner\'s lessons? Ryan Chadwick\'s free site can
take you from there. He breaks lessons down into small, easy to manage
steps. At the end of each chapter, he gives you questions you can use as
a springboard to dive deeper into the Linux command
line. ]{style="font-family: inherit;"}\
[\
Chapters involve basic navigation, using files, manual pages,
permissions, searching in files with grep, and shell
scripting.]{style="font-family: inherit;"}\
[\
Ryan even gives a good introduction of the Vi Text
Editor. ]{style="font-family: inherit;"}\
[\
]{style="font-family: inherit;"}\
[\
**The Linux System Administrator\'s
Guide**:]{style="font-family: inherit;"}\
[[http://www.tldp.org/LDP/sag/html/index.html]{style="font-family: inherit;"}](http://www.tldp.org/LDP/sag/html/index.html)\
[\
]{style="font-family: inherit;"}\

::: {.separator style="clear: both; text-align: center;"}
[[![](https://3.bp.blogspot.com/-8i6d2r43rE8/VU1O8MgDbwI/AAAAAAAAKik/i0a63pWjo70/s320/SAG.png){width="320"
height="223"}]{style="font-family: inherit;"}](http://3.bp.blogspot.com/-8i6d2r43rE8/VU1O8MgDbwI/AAAAAAAAKik/i0a63pWjo70/s1600/SAG.png)
:::

[\
Although a bit older, this text-based document written by the [Linux
Documentation Project](http://www.tldp.org/) is a good guide that gives
the user more detailed information such as the directory tree (/etc,
/dev, /usr), init, and system management. The last few chapters, which I
am still working through, might not pertain to a Mac Terminal, but would
be still good to know. ]{style="font-family: inherit;"}\
[\
After this, I just have to wonder\... I am re-learning the Linux Command
Line. \#AmIADeveloperYet?]{style="font-family: inherit;"}\
[\
]{style="font-family: inherit;"}\

> ::: {dir="ltr" lang="en"}
> [\... And I was just given my first non-practice
> [\#Selenium](https://twitter.com/hashtag/Selenium?src=hash)
> [\#WebDriver](https://twitter.com/hashtag/WebDriver?src=hash) /
> [\#Java](https://twitter.com/hashtag/Java?src=hash) assignment at
> Fitbit.
> [\#LearningAutomation](https://twitter.com/hashtag/LearningAutomation?src=hash)
> [\#AmIADeveloperYet](https://twitter.com/hashtag/AmIADeveloperYet?src=hash)?]{style="font-family: inherit;"}
> :::
>
> [--- T.J. Maher (\@tjmaher1) [May 7,
> 2015](https://twitter.com/tjmaher1/status/596397812927037440)]{style="font-family: inherit;"}

\
\
\
\
-T.J. Maher\
* Sr. QA Engineer, Fitbit*\
* Boston, MA*\
*\
// Automated tester for \[ 2 \] month and counting!*\
*\
Please note: \'Adventures in Automation\' is a personal blog about
automated testing. It is not an official blog
of [Fitbit.com](http://www.fitbit.com/). *\
