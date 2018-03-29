\-\-- layout: post title: What is Your Strategy for Writing an Automated
Test Framework? date: \'2016-09-15T00:18:00.001-04:00\' author: T.J.
Maher tags: modified\_time: \'2016-09-15T00:18:37.101-04:00\'
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-804878397000307343
blogger\_orig\_url:
http://www.tjmaher.com/2016/09/what-is-your-strategy-for-writing.html
\-\-- I have been giving this particular question a lot of thought in
the past couple of months. The question is:\

> [*\"What is Your Strategy for Writing an Automated Test
> Framework?\" *]{style="font-family: "georgia" , "times new roman" , serif; font-size: large;"}

There are a lot of moving parts when it comes to assembling an automated
test language:\
\
A way to write and execute the tests, such as TestNG or JUnit in a
Selenium WebDriver / Java based framework. A way to display to display
what passed and failed. Detailed logging telling what the test is
actually doing. A way to rerun failing tests. A way to run tests in a
continuous fashion, whether once a day, or once an hour, or anywhere it
between. A way to spin up multiple browsers and platforms\...\
\
You can easily spend a good six months putting the perfect framework in
place and not have time to create a single test\... and that is the
problem.\
\
How can you tell if your automation framework is fitting the needs of
the people who are using it: The manual testers trying to figure out
what tests are covered with the automation regression test suite, the
developers who need to see what the automation finds, the QA Manager who
is attempting to assess what the tests are covered by automation and
where manual testers should fill in the gaps?\
\
If you are trying to build a testing framework that fits the needs of so
many stakeholders\... why not use the same process that you are using to
construct the web app you are building: Use Agile.\
\
Make it an iterative process:\
\

-   **[Sprint 1]{.underline}**: Bad code. Good tests. Run from local
    browser. No CI/ CD.
-   **[Sprint 2]{.underline}**: Good code. Good tests. Run from local
    Selenium Grid. Investigate setting up CI/CD locally.
-   **[Sprint 3]{.underline}**: Better code. Better tests. Good building
    blocks for tests assembled? More tests, faster! Work with DevOps to
    get Selenium Grid and Jenkins server remotely.

\
\... What is your strategy for building an Automation Test Framework?
Leave comments below!\
\
Happy Testing!\
\
-T.J. Maher\
Sr. QA Engineer\
\
*// Software QA Engineer since 1996.\
// Working with Selenium WebDriver since 2014.\
// Follow Adventures in Automation and Like us on
[Facebook](https://www.facebook.com/AdventuresInAutomation/)!*
