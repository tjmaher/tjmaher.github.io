\-\-- layout: post title: Code Review Request, Please! Automated Test
Framework in Selenium WebDriver / Java date:
\'2016-01-30T07:36:00.004-05:00\' author: T.J. Maher tags: - Java - code
review request - WebDriver modified\_time:
\'2016-04-29T16:14:47.765-04:00\' blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-2769190029275709556
blogger\_orig\_url:
http://www.tjmaher.com/2016/01/code-review-request-please-automated.html
\-\-- Hello! Thank you for stopping by! I have a favor to ask, if you
don\'t mind\...\
\

### Code Review Request

\
Are you familiar with writing a test automation framework in Selenium
WebDriver / Java? If so, I was wondering if I could please ask a favor
from you?\
[]{#more}\
**Automate Amazon**:\

-   [Introduction](/2015/12/next-week-automating-amazon-how-i-am.html)
-   Part One: [Development Environment
    Setup](/2015/12/automate-amazon-development-environment.html)
-   Part Two: [Sketch Out a Use
    Case](/2015/12/automate-amazon-sketch-out-use-case.html)
-   Part Three: [CommonUtils, methods and
    exceptions](/2015/12/automate-amazon-commonutils-methods-and.html)
-   Part Four: [Writing a Sign In
    Test](/2015/12/automate-amazon-writing-sign-in-test.html)
-   Part Five: [Product Enums and Product
    Objects](/2016/01/automate-amazon-productenums-and.html)
-   Part Six: [Initializing Login and
    Cart](/2016/01/automate-amazon-initializing-login-and.html)
-   Part Seven: [Writing a Shopping Cart
    Test](/2016/01/automate-amazon-writing-shopping-cart.html)
-   Part Eight: [Data Driven Tests with TestNG
    XML](/2016/01/automate-amazon-sketch-of-possible-data.html)
-   Part Nine: [Code Review Request,
    please! ](/2016/01/code-review-request-please-automated.html)
-   Source Code: <https://github.com/tjmaher/automate-amazon/>

*A sample project in order to practice designing automated tests. *\

1.  I\'d like to request a Code Review for my project [Automate
    Amazon](https://github.com/tjmaher/automate-amazon), a practice
    Selenium WebDriver test automation framework that I wrote during my
    Christmas Break, attempting to use what I have learned at
    Fitbit-Boston. 
2.  After, could you leave gentle constructive criticism in the comments
    section at the end of this page?
3.  Over the next few weeks I will be blogging about my refactoring
    efforts. I\'ll make sure to quote or paraphrase your contribution as
    I talk about the refactoring effort.  

\

### About My Project 

\
You see\...\
\
\... I\'ve been working as an automation developer for about a year,
now, working with the team writing an automated test framework in
Selenium WebDriver / Java for Fitbit\'s online shopping cart.\
\
Over Christmas Break, I decided to take what I have learned so far and
write a practice framework versus Amazon.com\'s shopping cart. I have
spent a few days writing it and the past few weeks blogging about it.\
\
You can see what I have so far on my GitHub account at
<https://github.com/tjmaher/automate-amazon>.\
\

### About My Background

\
Although I have fifteen years of software testing experience, I\'m still
new at being an automation engineer with only a year of experience.\
\
Grad school for me? It took place before Agile really took off.\
\
Back then? We were still using Java 2 or 3\... So I have spent MANY
nights and weekends trying to make up for lost time as you can see from
this blog\'s table of contents.\
\
Or you could see it from the stuff on my Kindle and in bookcase. It\'s
filled with stuff by Robert C. \"Uncle Bob\" Martin, Martin Fowler,
Michael Feathers, Andrew Hunt, some Head First stuff, a certain piece
from The Gang of Four\.... And one from by my favorite [online
instructor](http://compendiumdev.co.uk/page.php?title=seleniumwebdrivercourse),
Alan Richardson\'s [Java for Testers](http://javafortesters.com/).\
\

### About Software Design Principles Used

\
Some software design principles are so cut and
[DRY](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself) that they
were easy to incorporate into designing this automation framework. We
have layers of abstraction in order to make sure we Don\'t Repeat
Yourself:\
\

-   **Test Classes**: Tests should only go in a test class. 
-   **Page Object classes**: Is there a page such as a LoginPage, or a
    ShoppingCartReviewPage? Make sure that selectors for all radio
    buttons, dropdown lists, text boxes, buttons, and other web
    elements, and other elements that touch the web document are
    contained here. 
-   **Common Utilities library**: Wrap all Selenium / Java calls to
    handle any and all failures. Only at this level should this base
    page object make Selenium calls to touch the page. 
-   **Actions classes**: Need to log into a page? That module would be
    stored in an actions classes. Try to only call these components into
    tests, to make them modular. The action classes should call only
    Page Objects. 

\
Some, though, I really don\'t have down
[SOLID](https://en.wikipedia.org/wiki/SOLID_(object-oriented_design))
enough to incorporate into the Java automation framework. An explanation
on how the SOLID principles pertains to the automated test framework I
have attempted to create would be very helpful!\
\

### And We Have Problems!

\
There are problems, though, with the Automate Amazon test framework\...
It doesn\'t exactly work.\
\
It\'s the DriverUtils class. It\'s my first time writing one on my own.\
\
Running a single test, it\'s fine.\
\
I tried to add on functionality to support [data driven tests in
TestNG\'s XML
format](/2016/01/automate-amazon-sketch-of-possible-data.html), and
tests just couldn\'t run in parrallel once they were set up.\
\
So, if you happen to be free, could you review my code and leave your
comments below?\
\
Thank you so much! :) Thank you for doing this.\
\
Happy Reviewing!\
\
[-T.J.
Maher]{style="background-color: white; color: #222222; font-family: "calibri"; font-size: 15.4px; line-height: 21.56px;"}\
* Sr. QA Engineer, Fitbit*\
* Boston, MA*\
*\
// Automated tester for \[ 11 \] month and counting!*\
*\
Please note: \'Adventures in Automation\' is a personal blog about
automated testing. It is not an official blog
of [Fitbit.com](http://www.fitbit.com/). *\
\
