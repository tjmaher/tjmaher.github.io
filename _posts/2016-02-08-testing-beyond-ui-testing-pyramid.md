\-\-- layout: post title: \'Testing Beyond the UI: The Testing Pyramid\'
date: \'2016-02-08T00:48:00.001-05:00\' author: T.J. Maher tags: -
intermediate - Rest API modified\_time:
\'2016-04-29T07:38:50.569-04:00\' thumbnail:
https://3.bp.blogspot.com/-i4ZDFL-FXVM/VrgjClfp0WI/AAAAAAAAK58/wanK84l850I/s72-c/Testpyramid.jpg
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-6241834947989097460
blogger\_orig\_url:
http://www.tjmaher.com/2016/02/testing-beyond-ui-testing-pyramid.html
\-\--

### Problems with UI Tests

\
We\'ve been using Selenium WebDriver with Java to write automated
browser tests for our eCommerce application ever since the new
Fitbit-Boston was formed two years ago.\
\
We have tests for our web application emulating how online customers
purchase goods, how customer service agents place orders, such as
\"Create a standard order containing a year long FitStar subscription
and a Fitbit Blaze, with a billing address in the US and a shipping
address in Canada, with overnight shipping, paying with a Discover
Card\".\
\
[]{#more}\
\
We have browser tests that run every time code is merged into master,
tests that run once per hour, and more tests that run just before a
release candidate is deployed to production. We even have a nightly
regression test suite of 320 some-odd tests that covers Firefox, Chrome,
and Internet Explorer from IE9 to Microsoft Edge.\
\
Even though our browser tests are pretty stable, executing on average
with a 98% pass rate, there are some inefficiencies with the process:\
\

-   Let\'s say we want to build a test that pressing the big shiny
    button actually captures a charge on one of our test credit cards,
    we need to go through the motions of placing an order first. If
    anything flaky happens with the web based user interface, the entire
    test fails, initially causing us to believe that maybe something was
    wrong with the capture charge functionality. 
-   Let\'s say we want to build a test that creates a refund. First, we
    need to place an order through the UI, then capture a charge. If
    anything flaky happens with those first two dependencies, the test
    fails. Likewise, we need to do some digging to figure out where the
    actual failure happened.   

\
If a certain test contained components that weren\'t specifically
browser tests, it would be more efficient if we go one level deeper for
those components, interacting with the same code the web browser is
working from. We would work directly with the API (Application
Programming Interface) and the application logic itself. Without a GUI
(Graphical User Interface), these \"headless\" tests would not fail each
time the properties of a web element changed.\
\

### Mike Cohn and the Testing Pyramid

\
Ever since the birth of Agile Software Development, two things were
recognized with the short development cycles:\
\

-   Automation should bear the burden of testing. 
-   Strategies with only UI automation will fail

\
Mike Cohn, author of \"[Succeeding with Agile: Software Development
Using
Scrum](https://www.mountaingoatsoftware.com/books/succeeding-with-agile-software-development-using-scrum)\"
(Nov. 2009) talks about in his book and [later
articles](https://www.mountaingoatsoftware.com/blog/the-forgotten-layer-of-the-test-automation-pyramid)
the concept of a \"testing pyramid\".\
\

::: {.separator style="clear: both; text-align: center;"}
[![](https://3.bp.blogspot.com/-i4ZDFL-FXVM/VrgjClfp0WI/AAAAAAAAK58/wanK84l850I/s1600/Testpyramid.jpg)](https://3.bp.blogspot.com/-i4ZDFL-FXVM/VrgjClfp0WI/AAAAAAAAK58/wanK84l850I/s1600/Testpyramid.jpg)
:::

\
\
From [The Forgotten Layer of the Test Automation
Pyramid](https://www.mountaingoatsoftware.com/blog/the-forgotten-layer-of-the-test-automation-pyramid) *(12/17/2009):*\

> \"Even before the ascendancy of agile methodologies like Scrum, we
> knew we should automate our tests. But we didn't. Automated tests were
> considered expensive to write and were often written months, or in
> some cases years, after a feature had been programmed. One reason
> teams found it difficult to write tests sooner was because they were
> automating at the wrong level. An effective test automation strategy
> calls for automating tests at three different levels, as shown in the
> figure below, which depicts the test automation pyramid \[\...\]

> \"Automated user interface testing is placed at the top of the test
> automation pyramid because we want to do as little of it as possible.
> Suppose we wish to test a very simple calculator that allows a user to
> enter two integers, click either a multiply or divide button, and then
> see the result of that operation. To test this through the user
> interface, we would script a series of tests to drive the user
> interface, type the appropriate values into the fields, press the
> multiply or divide button, and then compare expected and actual
> values. Testing in this manner would certainly work but would be
> brittle, expensive, and time consuming. Additionally, testing an
> application this way is partially redundant---think about how many
> times a suite of tests like this will test the user interface. Each
> test case will invoke the code that connects the multiply or divide
> button to the code in the guts of the application that does the math.
> Each test case will also test the code that displays results. And so
> on. Testing through the user interface like this is expensive and
> should be minimized.\"

\

### Martin Fowler and the Testing Pyramid

Martin Fowler agrees. Martin, according to his [employee
profile](https://www.thoughtworks.com/profiles/martin-fowler)  at
ThoughtWorks, \"I\'m an author, speaker... essentially a loud-mouthed
pundit on the topic of software development. I\'ve been working in the
software industry since the mid-\'80s where I got into the then-new
world of object-oriented software. I got a call from ThoughtWorks in
1999 to consult on one of their projects and they rapidly became my
favorite client. Within a year I was an employee\".\
\
From Martin\'s blog article,
[TestPyramid](http://martinfowler.com/bliki/TestPyramid.html)(5/1/2012):\

> \"For much of my career test automation meant tests that drove an
> application through its user-interface. Such tools would often provide
> the facility to record an interaction with the application and then
> allow you to play back that interaction, checking that the application
> returned the same results. Such an approach works well initially.
> It\'s easy to record tests, and the tests can be recorded by people
> with no knowledge of programming. 

> \"But this kind of approach quickly runs into trouble, becoming an
> ice-cream cone. Testing through the UI like this is slow, increasing
> build times. Often it requires installed licences for the test
> automation software, which means it can only be done on particular
> machines. Usually these cannot easily be run in a \"headless\" mode,
> monitored by scripts to put in a proper deployment pipeline. 

> \"Most importantly such tests are very brittle. An enhancement to the
> system can easily end up breaking lots of such tests, which then have
> to be re-recorded\".

An automated browser test suite has gone much farther than
record-and-playback, as with Selenium IDE, but the problems remain:\
\
When something fails, is it a problem with the functionality of the
application itself? Or is it a problem with the browser? Do the browser
tests need updating (again!) because a web element was modified
slightly? Using more API tests would alleviate this problem.\
\

### An API Example

Take a look at the documentation for the online payment processor,
Stripe at <https://stripe.com/docs/api/> as an example as an Application
Program Interface.\
\
Want to create a new charge order? Get a list of previous charges?
Process a return? No need to go through some type of user interface to
interact with the system. You can use:\
\

-   A programming language such as
    [Java](https://stripe.com/docs/api/java#authentication). Download
    their Stripe-Java module in their
    [library](https://stripe.com/docs/libraries) to interact with their
    system.
-   Http calls to interact with their RESTful (representational state
    transfer) library. ( See Stripe\'s [documentation with
    cURL](https://stripe.com/docs/api/curl#authentication).)

\
If we wanted to perform an API Test for Stripe, we could:\
\

-   Create a new charge using certain parameters, and pass it to the
    Stripe API, returning a charge id.
-   Get the parameters of the charge created from the Stripe API using
    the charge id returned. 
-   Assert that the actual parameters match the expected parameters,
    failing the test if they do not match. 

<div>

No browser needs to be spun up for a Selenium WebDriver test, making it
faster. There aren\'t any text fields or buttons or drop downs that
needed to be pressed or selected. We don\'t need to worry about slow
loading pages, or web elements that may or may not be there. We can
focus just on the application itself. 

</div>

<div>

\

</div>

<div>

And how exactly do we apply this to our shopping cart tests?\...

</div>

<div>

\

</div>

<div>

\... I dunno. We are still working on that! :)

</div>

<div>

\

</div>

\
[-T.J.
Maher]{style="background-color: white; color: #222222; font-family: "calibri"; font-size: 15.4px; line-height: 21.56px;"}\

<div>

\* Sr. QA Engineer, Fitbit*\
* Boston, MA*\
*\
// Automated tester for \[ 11 \] month and counting!*\
*\
Please note: \'Adventures in Automation\' is a personal blog about
automated testing. It is not an official blog
of [Fitbit.com](http://www.fitbit.com/). *

</div>

\

<div>

\

</div>

<div>

\

</div>

\
\
\
\
\
