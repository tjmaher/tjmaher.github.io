\-\-- layout: post title: \'Lecture: Customizing Jenkins @ SiteSpect \'
date: \'2015-03-12T02:16:00.004-04:00\' author: T.J. Maher tags: -
Meetup - CI - Jenkins modified\_time: \'2016-04-29T16:21:25.632-04:00\'
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-1833854859345025840
blogger\_orig\_url:
http://www.tjmaher.com/2015/03/lecture-customizing-jenkins-sitespect.html
\-\--

<div>

What happens when a favorite open-source tool is stretched beyond its
limit and needs severe customization? Two automation engineers at
[SiteSpect](http://www.sitespect.com/), Dustin Masterson and Josh
Shapiro, talked Wednesday evening at the [AutoTestCentral -
Boston](http://www.meetup.com/Automated-Testing-Boston/events/220784337/)
meetup about the problems they faced \-\-- and solution they came up
with \-- when forcing Jenkins to run 350+ functional test scenarios
comprising over 550,000 tests.

</div>

<div>

\

</div>

<div>

The following is compiled from my hastily scribbled notes, and a heck of
a lot of late night last minute independent research. Please let me know
in the comments section what needs to be fixed. 

</div>

<div>

\
[]{#more}\

</div>

### History of Jenkins

<div>

\

</div>

For those who don\'t know about Jenkins, here is what I found out
through some independent research: Jenkins \-- initially called
\"Hudson\" \-- is a continuous integration (CI) tool that allows
software developers to continuously check-in code to the main build
after the code is examined with a series of pre-automated tests.
Initially developed back in 2004 by Kohsuke Kawaguchi while at Sun
Microsystems, it was a community-driven open source project from its
beginning. When Oracle and Sun \-- creator of Java and an early backer
of MySQL \-- finally merged after a lengthy process, the Hudson
open-source movement voted back in January 2011 to change its name to
Jenkins when Oracle trademarked the original \"Hudson\" name.\

<div>

\

</div>

**Related Links: **\

-   Kohsuke.org: [Kohsuke Kawaguchi\'s Blog](http://kohsuke.org/)

<!-- -->

-   Wikipedia: [Sun Acquisition By
    Oracle](http://en.wikipedia.org/wiki/Sun_acquisition_by_Oracle)

<!-- -->

-   Jenkins-CI.Org: [Jenkins changes its
    name](http://jenkins-ci.org/content/jenkins) *(2011-01-29*)

\

<div>

<div>

<div>

\

</div>

### What SiteSpect Does

<div>

Josh Shapiro started off the Automated Testing Meetup talk by
introducing SiteSpect. According to my notes, SiteSpect allows
businesses acts as a [reverse web
proxy](http://www.sitespect.com/frequently-asked-questions#question3) letting
business perform A/ B website testing. SiteSpect provides software that
sits between the website and the users. Let\'s say that a business
wanted to see what generated a better click-through rate \-- an icon in
the shape of either A) picture of an actual carrot or B) a picture of a
stuffed carrot. Their software could use inject some Javascript into the
HTML code so that a select group of people would get A and the rest of
the people would get B, and then collect enormous amounts of data to
measure and analyze the results. 

</div>

</div>

<div>

\

</div>

### Creating a Test Harness

<div>

\

</div>

<div>

To get a better handle on all the tests, they used a test harness
operating a \"headless browser\" \-- one that doesn\'t have a graphical
user interface in order to provide the content of web pages to other
software programs. They use module called WWW::Mechanize ( [GitHub
link](https://github.com/petdance/test-www-mechanize)) programmed in the
Perl programming language. They had good automated testing coverage of
the product, but the job was so enormous a full test run of the
SiteSpect product took *7.5 hours*.\
\
Jenkins did have a lot of good features. SiteSpect uses a lot of the
popular [Atlassian](https://www.atlassian.com/)toolset: JIRA for
collaboration of issue tracking, Confluence for a knowledge base, and
Hipchat for a message board / instant messeging service, and Crucible to
find bugs and improve code quality through peer-review. Jenkins has
plugins to work with it all. Jenkins can integrate
into [Hipchat](http://www.hipchat.com/) to sent messages to developers
on the successes and failures of test runs.\
\
With Jenkins, SiteSpect could set up custom jobs and distribute them to
multiple machines. Even though Jenkins uses JUnit and SiteSpect uses
Perl, these tools can still could work together. Users of Jenkins can
modify Jenkins\' behavior with various plug-ins, such as one that allows
Jenkins users to create a project in the computer language Groovy.

</div>

<div>

\

</div>

<div>

Jenkins can act as an SSH (Secure Shell) server (
[more](https://wiki.jenkins-ci.org/display/JENKINS/Jenkins+SSH) ) where
users can register their public keys to Jenkins to make it more secure,
disallowing imposters to pretend to be the server. SiteSpect uses SSH to
push Java archive ( jar ) files between the master where Jenkins issues
out the tasks and worker nodes which run the tasks ( [even
more](https://wiki.jenkins-ci.org/display/JENKINS/Distributed+builds)
). 

</div>

<div>

-   Nodes can have labels such as whether they are tests of type GeoIP
    allowing webmasters to gather data about the location of their
    visitors, or IOS tests for Apple mobile devices. 
-   Nodes can be placed in clusters so multiple nodes can work on the
    same job.
-   Nodes can have different states such as \"Ready to Run\" or \"Needs
    to be configured\". 

<div>

According to the automation engineers, Dustin & Josh, Jenkins jobs can
be run on either the master or the worker. They recommend to push as
much work onto the worker nodes in order to be efficient. With Jenkins,
everything is distributed. The master controls all queuing jobs which
get set up with the test harness. The worker nodes process the work. 

</div>

</div>

<div>

\

</div>

<div>

There are problems when you overload Jenkins: 

</div>

<div>

-   So much work gets processed that Jenkins\' built-in reporting tool
    can\'t handle the workload. SiteSpect had to create its own custom
    static HTML reports.
-   Only one worker node can go to Jenkins, so the automation engineers
    had to figure out a solution where twenty-four other worker nodes
    had to be chained together. 
-   Jenkins stores data from its test runs as XML files, too long to
    sort through if you are trying to analyze data from them. This is
    why they built a system which feeds the results into a mySQL
    database mirroring the results. 

</div>

### Kicking Off a Test Harness Run

<div>

\

</div>

<div>

A Test Harnesses can be kicked off in two ways:

</div>

<div>

-   Subversion (SVN), what SiteSpect uses for version control, polls for
    commits to the trunk, constantly checking to see if there are any
    new additions which need to be added to the main body of code. 
-   Software developers can request a new run. 

<div>

\

</div>

\... From there, you can map multiple repositories to a single job. At
 SiteSpect, half of their jobs are kicked off from automatic polling,
and half are from jobs being manually started. 

</div>

<div>

\

</div>

<div>

On a sidenote: SiteSpect mentioned that because they are using an older
version of the Linux operating system as a company standard, they cannot
use tools like Chef or Puppet, two popular and competing configuration
management tool that are currently used.

</div>

<div>

\

</div>

**Related Links:**\
\

-   Puppet Labs: [What is
    Puppet?](https://puppetlabs.com/puppet/what-is-puppet) 

<!-- -->

-   Chef.io: [What is
    Chef](https://www.chef.io/solutions/configuration-management/)? 

\
\

<div>

When first setting up the master and worker jobs, it is important to
test it out with *one* worker node first, to see if there are any
errors. Then, if everything passes, they configure the rest of the
workers. 

</div>

<div>

\

</div>

### A Few Jenkins Plugins

<div>

\

</div>

<div>

**Matrix Project Plugin:** ( [Jenkins
Wiki](https://wiki.jenkins-ci.org/display/JENKINS/Matrix+Project+Plugin)
): 

</div>

<div>

Problem:  Jenkins is built around testing, but it wants to do ONE test
in ONE unique environment. What if you need to do this is similar
customized environments? There is a Matrix Project Plugin for Jenkins,
but the automation developers believe, quote, \"It\'s a trap!\",
endquote. The problem with that plugin that if one machine happens to be
down, since it is a static list, it stalls out, waiting for that one
machine to come back up.  

</div>

<div>

\

</div>

<div>

**NodeLabel Parameter Plugin** ( [Jenkins
Wiki](https://wiki.jenkins-ci.org/display/JENKINS/NodeLabel+Parameter+Plugin) ): 

</div>

<div>

\

</div>

<div>

This Jenkins plugin allows all workers to be labelled such as \"Harness
Labs\". A Groovy script can be used to tie all the nodes together.

</div>

<div>

\

</div>

### More About The Test Runs

<div>

Each test is optimized so that it takes no longer than seven minutes to
run a test. Why? They just chose that number, and it seems to work so
far. 

</div>

<div>

\

</div>

<div>

As tests run, results are added into their mySQL database. The person
who made the commit gets an email. 

</div>

<div>

\

</div>

<div>

Each test run can consist of:

</div>

<div>

-   A GeoIP test run which provides information about the location of
    users on the web, or on mobile devices using technology such as such
    as WURFL.js (Wireless Universal Resource FiLe). 
-   iOS testing with OS X worker nodes. 
-   Appium testing with the iOS simulator using the software product
    backed by Sauce Labs. 
-   Virtual Machine Setup Tables, for those not familiar with the
    command line interface. 

</div>

<div>

\

</div>

<div>

**Related Links:**

</div>

<div>

-   Wurfl.io: [Device Detection with WURFL.js](http://web.wurfl.io/)

</div>

<div>

\

</div>

### Learning Curves and Workaround

<div>

\

</div>

<div>

This new process was designed, tested, and when unveiled \... it started
crashing all the time. The CPU resources on the machines involved would
be maxxed out. Jenkins is very good with a small setup. SiteSpect\'s
setup was large. There needed to be a lot of trial and error when it
came to customization. Heap memory consumption would easily go through 6
gigabytes of memory. The master had to be restarted every day, and still
would crash. The problem that there was a runaway restart call chewing
up the CPU. They use a CLI (Command Line Interface) connect instead. 

</div>

<div>

\

</div>

<div>

Nodes can be labelled with names such as harness\_tests, harnass\_lab,
harnass\_lab\_all\_jobs. testing\_jobs. Developers can even customize
their own jobs. Jenkins won\'t let you customize their \"All\" tab.
Their workaround is to create a tab named \"All\", then delete Jenkins\'
original \"All\" tab.

</div>

<div>

\

</div>

<div>

With the amount of jobs they have, they can\'t use the user interface of
the reports that come shipped with Jenkins. There are so many jobs to
keep track of that opening the reports or dashboards would cause Jenkins
to crash. As part of a Hackathon project, they came up with customized
HTML pages showing results. 

</div>

<div>

\

</div>

<div>

The test runs need to be optimized. When running jobs in parallel, the
jobs that take longer need to be started first, with the shortest job
being run at the end of the cycle. 

</div>

<div>

\

</div>

### Conclusions

<div>

\

</div>

<div>

All in all, the automation engineers at SiteSpect thinks that Jenkins is
a good tool. With their custom implementation of Jenkins they were able
to get it from taking almost eight hours to complete their tests to
**only thirty minutes per run**.

</div>

<div>

\

</div>

<div>

Jenkins is powerful, flexible, and quirky. Some of the components you
can add to Jenkins may have memory leaks. Make sure to perform Google
searches on them and review the Jenkins forums before implementation. 

</div>

<div>

\

</div>

<div>

\

</div>

### Sidenotes

<div>

-   Only failures are saved. SiteSpect save the successful results. 
-   Who writes the tests? In theory, developers write the tests. QA just
    examines the quality of the tests.
-   My keen powers of observation picked up that SiteSpect is hiring. I
    deduced this from the announcement the HR Recruiter made before the
    lecture, the sign that was placed next to the neat stack of business
    cards and other tchotchkes they were giving away. Pens, mugs, USB
    chargers, all with their name on the items. Good luck guys! I hope
    find people! 

<div>

\

</div>

<div>

\... Personally, I thought the lecture was amazing. I could not believe
that a company would be so transparent to tell forty strangers all their
triumphs and tragedies, and at such an in-depth level. 

</div>

<div>

\

</div>

<div>

Good luck, SiteSpect! I wish you well! And thank you very much for the
pizza.    

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

-T.J. Maher\
* Sr. QA Engineer, Fitbit*\
* Boston, MA*

</div>
