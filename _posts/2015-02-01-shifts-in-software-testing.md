\-\-- layout: post title: Shifts in Software Testing date:
\'2015-02-01T10:31:00.000-05:00\' author: T.J. Maher tags: - industry -
manual to automation - qa modified\_time:
\'2016-04-29T16:20:26.844-04:00\' blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-2777120156466049006
blogger\_orig\_url:
http://www.tjmaher.com/2015/02/shifts-in-software-testing.html \-\-- You
might not have recognized this if you have worked at the same job for
the past couple of years, but the software testing industry has shifted.
There is less demand for traditional QA Engineers. You may know the
entire software development process, both Waterfall and Agile. You may
be very skilled at working with business analysts examining the business
requirements to make sure they are clear and concise. You may be quite
good at coming up with great testing scenarios. But there are many new
standards, practices and technologies that future employers are going to
need from you, most which were unheard of just two or three years ago.\
\
[]{#more}\
\
Let me tell you, I\'ve been finding all of this out the hard way! I
started casually examining the state of the software testing industry
six months ago. This casual research became a mad scramble when I found
myself on the wrong side of a layoff at the company I had been at for
over four years. With the countless numbers of phone screenings and two
or three face-to-face interviews a week I have had since early December,
it is like I have enrolled in a crash course about the state of the
software industry.\
\
I have observed that there are three things that have converged in the
past few years to completely change software testing as we know it:\
\

### Sources of Change in the Software Testing Industry: 

<div>

\

</div>

#### 1) Agile has officially become the new standard 

\
The good news is that with the Agile Software Methodology the Software
Quality Assurance team is now fully integrated into the entire software
development process. \[*Read more about it
[here](http://adventuresinautomation.blogspot.com/2015/01/agile-software-development.html)*\]\
\
The bad news is that the DEV and QA team only has two weeks at a time to
build, unit test, do code reviews, and create and execute test scripts.\
\
The worse news is that because of the short time frame, all the
regression testing you need to do just before the release of the
software product to make sure that the old functionality still works
while you were building in new features into the software product \...
well, the time also has been rapidly condensed. The only way to keep up
with the pace is to automate all the regression tests. Which means that
as a QA Engineer, you are now expected to code. Fluently.\
\

#### 2) Automated testing tools are now cheap or free 

\
Companies in the past that wished to introduce  automated testing into
their quality assurance department had to purchase expensive software
packages such as Rational Rose, the Mercury Toolset or Segue Software\'s
Silk Test. This would involve enrolling the entire QA team in expensive
courses and training to get them up to speed. Now, with the introduction
of free tools such as Selenium, companies can focus on either getting
their old QA team up to speed or hiring a new QA team with the desired
skillsets.\
\
Selenium went from the Selenium IDE, a cute little Firefox plugin
offered for free in 2006, to Selenium WebDriver, a heavy duty code
library backed by Google in 2011. Selenium WebDriver can work with Java,
Python, Ruby, or C\# to interact directly with any web application
through the Firefox, Chrome, or Internet Explorer browser and it is all
offered for free. With libraries such as the [Appium](http://appium.io/)
or [Selendroid](http://selendroid.io/) libraries, you can even write
Selenium automated tests on the iPhone, iPad, or Android mobile
devices.\
\

#### 3) Companies match Google\'s standards    

<div>

\

</div>

Google has set the bar high, and other software companies have followed.
Starting with the book, \"**How Google Tests Software**\" \[*Read more
about
it [here](http://www.tjmaher.com/2015/01/how-google-test-software.html)*\],
Google has introduced the concept of filling up the ranks of the
Software Quality Assurance team with software developers, either
creating test automation frameworks or writing the automated tests
themselves. Whether it is writing code in Selenium with Java, Python,
Ruby or C\#, or working with Continuous Integration tools such as
[Jenkins](http://jenkins-ci.org/), companies which follow Google\'s high
standards, coding skill has been the new focus in software testing, so
you better make sure to get prepared.\
\
Continuous integration is the process of automatically merging the
developer\'s working copies of code into the main body of code several
times a day.\
\

### Changes to the Hiring Process of a QA Engineer

\
With QA departments now looking to add programming knowledge to its
ranks, there are new methods of screening potential candidates, new job
requirements, and new interview techniques.\
\

#### New Methods of Screening Candidates    

<div>

\

</div>

Before the initial phone interview with the hiring manager is even
scheduled, you may need to submit a programming assignment to the
company if it involves any automated testing. It is past the time when
companies are willing to train a new hire on the job. Right now, they
are hard at work getting their current employees up to speed. With any
new position, they need proof that the minimum coding requirements are
met. If you cannot figure out how to solve their programming assignment,
they can\'t start the interview process with you.\
\
Here are a few coding assignments I have been given:\
\

-   \"Write an efficient, well documented program in the language of
    your choice that will return the first n prime numbers\" \[*My
    solution, in both
    [Java](https://github.com/tjmaher/find_primes_java) and
    [Python](https://github.com/tjmaher/Find_Primes_Python)*\]
-   \"Write a program where a user can choose an input file that
    contains a table, the program reads the table, sorts it by the
    column name the user chooses, and places the new sorted table in an
    output file\". \[*My solution,
    in [Python](https://github.com/tjmaher/Sort_By_Columns)*\]

<div>

\

</div>

\

#### New Job Requirements

<div>

\

</div>

When you are looking for your next job, even if the job requirements do
not mention automation testing, you may find that they are going to ask
you:\

-   Do you have experience in automated testing? Do you know Selenium? 

<!-- -->

-   How much programming experience do you have? How much recent
    on-the-job experience do you have? Do you know both a programming
    language like Java and a scripting language like Python? 

Even if it what you think will be a manual testing position, you are
going to be asked about:\
\

-   If you know Selenium WebDriver with either Java or Python

<!-- -->

-   If you have tested using any APIs, and if you are familiar with XML
    feeds and JSON notation.

<!-- -->

-   If you have any experience in Javascript, Angular.js, and Node.js.
    If you say that you know Javascript, remember, they will quiz you on
    it. 

<!-- -->

-   If you know about Continuous Integration with tools such as Jenkins.

\

#### New interview techniques

<div>

\

</div>

If you have not had a position where coding is part of your day-to-day
activity, it is going to be very tough for you\... and it is going to
get tougher. If you are going for an automated testing position you will
have to demonstrate programming examples on the whiteboard during a
technical interview.\
\
If you do not have experience coding, or your coding skills are quite
rusty, like mine have been, you are going to have a lot of work to do. I
may have earned a Masters of Software Engineering, but it has been six
years since I coded on a regular basis\...\
\
\... Which is why exactly I started this blog! :)\
\
Hopefully, we can all catch up to the new standard together.\
\
Here\'s to the new standards in software testing!\
\
-T.J. Maher\
* Sr. QA Engineer*\
* Quincy, MA*
