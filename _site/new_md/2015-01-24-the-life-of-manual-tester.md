\-\-- layout: post title: \'What is a QA Engineer? \' date:
\'2015-01-24T17:06:00.000-05:00\' author: T.J. Maher tags: - industry -
manual - qa modified\_time: \'2016-05-05T16:28:54.894-04:00\'
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-7749046607647248327
blogger\_orig\_url:
http://www.tjmaher.com/2015/01/the-life-of-manual-tester.html \-\--\

# What is a QA Engineer?

You may have noticed on your neighborhood software development team a
few people where coding the product isn't their main role. They aren't
artists, so you know they aren\'t web designers on the User Experience
team designing the user interface. They don\'t usually gather the
initial business requirements, so they aren\'t business analysts. And
every other word they talk about contains the word "test": Test
Matrix, browser testing, test strategies, test cases, test scripts,
regression testing. They are the Software Quality Assurance Engineers.

Yes, quality is everybody\'s job, but the QA Engineers are responsible
for keeping the software testing effort and the SQA process running
smoothly. Quality exists in the minds of all the major stakeholders
vested in the software product everyone is attempting to build.


* They try to keep the wants and needs of the end-user in mind, the
    person who is going to use the product. Is the product usable? Is it
    intuitive? Would it work with all the different browsers, platforms
    and mobile devices required?

* They try to keep the wants and needs of the software company in
    mind: Hitting all the major milestones, attempting to estimate
    testing time correctly, and attempting to fit testing new
    functionality before the two week cycle (if using the Agile method),
    and attempting to finish regression testing on time - testing
    again that adding the new stuff didn't break the old stuff just
    before the product gets shipped. 

* They work directly with the software developers to see if there are
    any technological pitfalls, and with the designers of the user
    interface to make sure that the elements on the screen translate
    well across web browsers and mobile devices. 

The QA Engineer does more than just software testing. They are also
involved in software quality assurance. Software testing is actually
testing the product while software quality assurance is the process of
coming up with and executing software testing.


## What are the types of software testing? 

Let me come up with an example of how an individual can test a program:

Let's say you have your typical Login Screen on a web page. It has a
textbox labelled: "Username", another one labelled "Password", and a
button labelled "Login".

How would you go about testing it?

### You could test the functionality of the page

* What happens if you enter a valid username and password, and select
    the Login button? Does it log you into the system with the correct
    user type (admin, superuser, user), showing you the correct landing
    page? 
*  What happens if you enter an invalid username and password? Does the
    error message show up in red underneath the Login button (if that is
    how it had been designed) or is the error message a clunky popup? 
* Is the username supposed to be an email address? If so, what happens
    if you leave out the @, or .com / .net / .edu / .uk /.io / etc, does
    it clue the user into what is the correct format?  
* Does the username and password text boxes allow enough characters to
    be entered? 
* What happens if you log in and the server is down: Do you inform the
    user, handling the error gracefully, or is there a white page with
    "Error 404"?

### You could perform UI testing

* Does the page layout match exactly what the User Experience team /
    Web Designer has designed? Are you sure? This includes whitespace
    between textboxes, logos, designs. Font sizes, and font colors,
    checking the text on the labels and the text on the buttons.   


### You could perform browser testing

* Does the Login page look the same in Chrome, Firefox, IE 9, Safari
    on the Mac, or when using an iPad, iPhone, or Android mobile
    device? 

### You could do database testing

* Does the database capture \"Last Login Time\" for a user? If so, is
    that field populated with the new data? And is it stored in the
    requested format (YYYY-MM-DD) or in the requested time zone if the
    time of login is also captured? Query the database field in SQL. 

### You could perform security testing:

*  When an attempt to log in fails, you probably don\'t want to tell
    someone that the username is valid, but it is the password failed. 
* What happens if someone attempts to enter SQL code into the username
    textbox such as \"\@DROP TABLES MEMBER\", does the code get
    executed?

\
\

  ---------------------------------------------------------------------------------------------------------------------------------------
   [![](http://imgs.xkcd.com/comics/exploits_of_a_mom.png){width="400" height="122"}](http://imgs.xkcd.com/comics/exploits_of_a_mom.png)
                         [From XKCD.com, <http://xkcd.com/327/>]{style="font-size: xx-small; text-align: start;"}
  ---------------------------------------------------------------------------------------------------------------------------------------


* What happens if someone enters \<script\>alert(\"Cross-Site
    Scripting Test\")\</script\> does a pop up window display? 
* Are successful logins and login failures shown in the website error
    logs? 
* After five or so unsuccessful login attempts, do you lock them out
    of the system and force them to get a new password, if that is the
    security protocol? 

### You could test it according to the spec

* If according to the spec there is supposed to be a "Forgot
    Password" link, and it is not there, it is also a bug.

### You could do Performance Testing:

* How long does it take for the Login screen to display or to be
    logged in?
* What happens if many people are attempting to log in at the same
    time?
* ... All of these tests could be performed as manual testing,
    meaning that you as a software tester could perform all of these
    actions just as an end user would, interacting with the Login screen
    with a browser, a mouse, and a keyboard. No programming necessary.
    You may need to know SQL to do database testing, but you don\'t get
    to practice coding in your day-to-day activity. 


## Now, what is Software Quality Assurance? 

Software Quality Assurance is the part of the process that happens both
before and after the software testing. Quality isn\'t just trying to
figure out whether something works or not. It should meet or exceed the
expectations of all the major stakeholders. It involves:\

* Examining the business requirements of a new piece of functionality
    that the business analyst drafted. Make sure it is clear, concise,
    with each of the requirements being testable. 
* Working with the software developers to see if there are any
    technological pitfalls behind-the-scenes where QA Engineer should
    proceed with caution. 
* Drafting a test plan giving a bird\'s eye view of what is about to
    be tested: Hardware, software, etc, if needed, and get the major
    stakeholders to sign off on it. 
* Drafting a test script in MS Word or MS Excel the testing scenarios
    you are going to cover and what actions the tester needs to do,
    step-by-step. Have a QA peer-review and a team review of the script.
    Integrate the parts of the new functionality into the master test
    script for that component, giving you a regression test script. 
* Performing a smoke test or an acceptance test on any web app
    deployed to the QA Test environment. 
* Manually executing the script on the required browsers, platforms or
    mobile devices. 
* Checking to see if operating the web app seems intuitive enough to
    the end user.
* Writing bug reports if a bug is found: Description of what is found,
    steps how to duplicate the bug, screenshots of any UI issues, or
    error logs uploaded and attached to the bug report. 
* Performing regression testing just before the release of the web
    app: When the new functionality was created, did it damage any of
    the old functionality? Execute all the tests that you have for the
    web app, running all the regression test scripts. 
* Making sure that you hit all milestones and deadlines. If you only
    have two weeks to design, code, and test the new functionality of a
    web app and isn\'t deployed to QA a day before the deadline, you
    have a problem. 

Thank you for stopping by! I'm T.J. Maher, a Senior Quality Assurance
Engineer of fourteen years who -- like most software testers, nowadays
-- is trying to make the switch from being just a manual tester and get
into automation testing.

I started this blog as a way to motivate me to keep on putting in the
hours needed in order to research and study the new technologies that
have been cropping up as the new standard in the software testing
industry these past two years.

That has been my career.

... And just in the past two years, it has changed immensely.

-T.J. Maher
* Sr. QA Engineer
* Quincy, MA
