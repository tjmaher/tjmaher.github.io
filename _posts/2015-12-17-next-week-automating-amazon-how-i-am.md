\-\-- layout: post title: \'Next Week: Automating Amazon : How I Am
Spending My Christmas Vacation \' date:
\'2015-12-17T07:34:00.000-05:00\' author: T.J. Maher tags: - code
examples - Java - intermediate - WebDriver - test framework
modified\_time: \'2016-04-29T07:46:07.729-04:00\' blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-1609290693465465382
blogger\_orig\_url:
http://www.tjmaher.com/2015/12/next-week-automating-amazon-how-i-am.html
\-\--

### Automating Amazon:* *How I Am Spending My Christmas Vacation: 

\
For the past few years, I have been coming up with little side projects
during my Christmas break to help deepen my knowledge of the software
testing industry.\
\

-   **December 2012**: Examining the book [How Google Tests
    Softwar](/2015/01/how-google-test-software.html)e
-   **December 2013**: Taking Alan Richardson\'s excellent online course
    [Selenium 2 WebDriver with
    Java](http://courses.compendiumdev.co.uk/courses/selenium-2-webdriver-with-java)
-   **December 2014**: I was quite busy! I retook Alan Richardson\'s
    course, spent time creating this blog, and I finally created a
    GitHub account storing Java and Python code samples I could show to
    prospective employers as I interviewed for automation development
    positions. Quite handy when I was caught up in a surprise layoff and
    was searching for automation positions this time last year.

This Christmas, I was going to carry on the tradition!\
\
[]{#more}\
\
Starting next week, there will be new blog entries posted to
**Adventures in Automation** every* Tuesday* and *Thursday* for the next
couple of weeks.\
\
I will be attempting to develop automated tests for the Amazon.com site
using the knowledge I have gained since I joined Fitbit-Boston in March
2015.\
\
I will be:\
\

-   Blogging my thought process as I attempt to automate Amazon.com
-   Talking about setting up various automation development environments
    and the tools used to test.
-   Modeling the automated tests on how we are currently designing
    automated tests for the Fitbit.com shopping cart. 
-   Sharing my sourcecode on [GitHub.com](https://github.com/tjmaher)

<div>

\

</div>

<div>

Concepts we will be talking about:

</div>

<div>

\

</div>

<div>

-   Using TestNG to create tests
-   Page Objects to organize the methods on how to interact with the
    elements on the particular page
-   Wrappers for commonly used Selenium WebDriver functions
-   Actions classes grouping up commonly used methods, so tests are
    easier to create
-   Plain Ole Java Objects (pojos) to gather up and group together
    parameters of test objects, so we can pass one object into a method,
    instead of five or six parameters. 

</div>

<div>

\

</div>

<div>

Please note: I haven\'t been doing automation on-the-job for very long.
I have less than a year\'s worth of experience developing automated
tests in Selenium WebDriver. Although I can describe how we do things at
Fitbit, please don\'t take anything that I am doing as the industry
standard. 

</div>

<div>

\

</div>

<div>

If you do have knowledge of the industry standard of automated testing,
please feel free to correct me! I will be eagerly monitoring the
comments section for any advice or wisdom. 

</div>

<div>

\

</div>

<div>

And no, I don\'t actually know how Amazon develops their automated
tests. I will only be taking my best shot at it.

</div>

<div>

\

</div>

<div>

I\'m looking forward to it! 

</div>

\
**Update 1/7/2016**:\

> ::: {dir="ltr" lang="en"}
> [\@tjmaher1](https://twitter.com/tjmaher1) is writing a good 8 part
> case study of automating a web GUI using
> [\#Java](https://twitter.com/hashtag/Java?src=hash) and
> [\#Selenium](https://twitter.com/hashtag/Selenium?src=hash)
> [\#WebDriver](https://twitter.com/hashtag/WebDriver?src=hash)
> <https://t.co/ylnF64pFnh>
> :::
>
> --- Alan Richardson (\@eviltester) [January 7,
> 2016](https://twitter.com/eviltester/status/685025609156788224)

\
**NEXT:** [Setup of a Development Environment
\>\>](/2015/12/automate-amazon-development-environment.html)\
\
-T.J. Maher\
 Sr. QA Engineer, Fitbit-Boston\
\
*// Manual tester, 15 years*\
* // Automated tester for \[ 8 \] months and counting*\
\
*Please note: \'Adventures in Automation\' is a personal blog about
automated testing. It is not an official blog
of [Fitbit.com](http://www.fitbit.com/). *\
\

::: {#toc-section .toc-section}
**Automate Amazon**:\

-   [Introduction](/2015/12/next-week-automating-amazon-how-i-am.html)
-   **Part One:** [Environment
    Setup](/2015/12/automate-amazon-development-environment.html)
-   **Part Two:** [Sketch Use
    Case](/2015/12/automate-amazon-sketch-out-use-case.html)
-   **Part Three:** [CommonUtils, methods,
    exceptions](/2015/12/automate-amazon-commonutils-methods-and.html)
-   **Part Four:** [Write Sign In
    Test](/2015/12/automate-amazon-writing-sign-in-test.html)
-   **Part Five:** [Product Enums and
    Objects](/2016/01/automate-amazon-productenums-and.html)
-   **Part Six:** [Initializing Login and
    Cart](/2016/01/automate-amazon-initializing-login-and.html)
-   **Part Seven:** [Writing Shopping Cart
    Test](/2016/01/automate-amazon-writing-shopping-cart.html)
-   **Part Eight:** [Data Driven Tests with TestNG
    XML](/2016/01/automate-amazon-sketch-of-possible-data.html)
-   **Part Nine:** [Code Review Request,
    please! ](/2016/01/code-review-request-please-automated.html)
-   **Source Code:** [GitHub, T.J.
    Maher](https://github.com/tjmaher/automate-amazon/)
:::

\
\
