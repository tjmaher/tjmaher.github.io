\-\-- layout: post title: \'Playing with Protractor: The complexities of
testing JavaScript frameworks, according to Vojtěch Jína\' date:
\'2016-09-13T18:03:00.004-04:00\' author: T.J. Maher tags: - JavaScript
- AngularJS - Protractor modified\_time:
\'2016-09-13T18:33:30.932-04:00\' thumbnail:
https://3.bp.blogspot.com/-s8VDA6cU6Og/V9h7OvyQMEI/AAAAAAAALXs/HqbrclSLnuQmrCZJEOJprKxXHp0MEu8oQCLcB/s72-c/thesis.png
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-9156763029875094112
blogger\_orig\_url:
http://www.tjmaher.com/2016/09/playing-with-protractor-complexities-of.html
\-\-- Vojtěch Jína, a Software Engineer at Google, finished his
Master\'s thesis, [JavaScript Test
Runner](https://github.com/karma-runner/karma/blob/master/thesis.pdf),
at the Czech Technical University in Prague in 2013. Vojtěch talked
about, in his thesis, the difficulty developers had when attempting to
write unit tests for their code when using JavaScript.\
\

> *[[\"The language for web applications is JavaScript, which is a very
> dynamic language without static typing. There is no compiler that
> could catch mistakes like misspelling a variable name or calling a non
> existing method on an object - developers have to actually run the
> code to catch these issues. Therefore testing is absolutely
> necessary\"]{style="font-family: "georgia";"}.]{style="font-size: large;"}*

\

::: {style="text-align: center;"}
**JavaScript Test Runner**, by Vojtěch Jína
:::

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://3.bp.blogspot.com/-s8VDA6cU6Og/V9h7OvyQMEI/AAAAAAAALXs/HqbrclSLnuQmrCZJEOJprKxXHp0MEu8oQCLcB/s320/thesis.png){width="248" height="320"}](https://3.bp.blogspot.com/-s8VDA6cU6Og/V9h7OvyQMEI/AAAAAAAALXs/HqbrclSLnuQmrCZJEOJprKxXHp0MEu8oQCLcB/s1600/thesis.png)
                                                                          [*https://github.com/karma-runner/karma/blob/master/thesis.pdf*](https://github.com/karma-runner/karma/blob/master/thesis.pdf)
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

\
[]{#more}\
\

The Problem With JavaScript
===========================

\
Java is a static typed language. You declare the type from the very
beginning, such as *String greeting = \"Hello\"*. To declare a variable
in JavaScript, you can say *var variable = 3*, or *var variable =
\"Hello\"*, or *var variable = false*, and that variable will become an
integer, string, or boolean, depending what value you assign to it. If
you try to assign another value to it, and instead call it \"varble\",
no error will be thrown. A new \"varble\" will simply be created.\
\
Because there is no static typing with JavaScript, it \"makes type
checking and IDEs support hard\".\
\
Back in 2013, \"\[c\]onventions for structure of a project are not
settled yet and therefore projects typically end up with very messy
codebase. Additionally, there are many inconsistencies between different
browsers, especially when it comes to dealing with Document Object Model
(DOM)\".\
\

Karma to the Rescue!
--------------------

\
To help developers out with unit testing their JavaScript code, he
created a new JavaScript Test Runner.\
\
That test runner was called **Karma**\... Well, originally it was called
*\"Testacular\"*\... Yes. Seriously. See [Issue
\#376](https://github.com/karma-runner/karma/issues/376) of Karma\'s
GitHub site.\
\
Anyway\... **Karma** \-- <https://github.com/karma-runner> \-- was to
run the unit tests silently in the background, not distracting the
developer needlessly. \"This workflow significantly improves the
productivity and therefore empowers web developers to rely more on
automated testing\".\

> *[]{style="font-family: "georgia" , "times new roman" , serif; font-size: medium;"}*\
>
> -   [\"IDEs are improving their heuristics for dealing with dynamic
>     languages and bringing refactoring tools for easier coding (eg.
>     [WebStorm](https://www.jetbrains.com/webstorm/) can understand a
>     JavaScript project very well and offers similar features like the
>     ones for statically typed
>     languages).]{style="font-family: "georgia" , "times new roman" , serif; font-size: medium;"}
> -   [\"MVC \[
>     [*Model-View-Controller*](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller)
>     \] frameworks (eg. [AngularJS](https://angularjs.org/),
>     [Ember.Js](http://emberjs.com/)) are helping with overall
>     application structure and rising the level of abstraction by
>     offering bigger building
>     blocks.]{style="font-family: "georgia" , "times new roman" , serif; font-size: medium;"}
> -   [\"New languages that compiles to JavaScript (eg.
>     [CoffeeScript](http://coffeescript.org/),
>     [LiveScript](http://livescript.net/)) are improving the syntax and
>     adding features to the
>     language\".]{style="font-family: "georgia" , "times new roman" , serif; font-size: medium;"}
>
\... I\'m still trying to wrap my mind around different uses of
[Software Design
Patterns](http://www.tjmaher.com/search/label/Design%20Pattern), so I
wasn\'t able to fully understand about how Vojtěch wrote Karma with an
\"Inversion of Control (IoC) pattern\" and using a \"Dependency
Injection (DI) framework\", which he gets into in his thesis.\
\
**Vojta Jina** - Dependency Injection - *NG-Conf*\

***AngularJs Conference**, [ng-conf](http://www.ng-conf.org/), Jan 16,
2014*\
\
\... Okay, that makes Dependency Injection a bit more understandable.
Thank you, Vojta!\
\

It\'s All About The Testing
---------------------------

\
What really caught my eye? There are chapters on this thesis on my
favorite subject of them all: Why you should always test.\
\
Of course, it is more geared towards why developers should use Karma to
unit test their code, but this applies to why every Agile Software
Development team should include an automation developer to add tests to
their browser ui regression test suite.\
\

Why Testing?
------------

\
\

### Proving the Code is Correct:

\
\
Your code is going to be tested one way or another, either by you or
your customer. If you automate your tests, they will run more often,
giving you more confident the code works as you intended.\
\

### Avoiding Regressions: 

> *\"\[a\] Regression bug is a bug that had been fixed in the past and
> then occurred again. Introducing the same bug into the system again
> can happen very easily, because very often we do not see some hidden
> relationships. For instance, we change obviously unrelated piece of
> code and therefore we do not check some old problem, because we do not
> expect that problem to occur again. Once we have an automated test for
> this bug, it will not happen again (at least the probability is very
> low), because we can easily run all the tests, instead of manually
> trying only the parts that are obviously related to the change we
> made. This gives us more confidence when making any changes and
> therefore it makes things like refactoring easier\".*

### Quick Feedback:

> *\"Whenever you make any changes, you want to immediately see the
> result of that change. When writing software the developer makes a
> change and then he needs to wait for compiling the code and then
> running it. That is very slow feedback, slowing the whole development
> process and killing creativity. JavaScript is an interpreted language
> and reloading the browser is usually pretty fast \[\...\] but it could
> be faster. Running unit tests can be way faster than switching context
> from the text editor to the browser and waiting for the page to
> reload. Executing a unit test can happen in a few milliseconds,
> without the developer leaving his text editor at all, creating instant
> feedback from testing\".*

### Safer Refactoring:

\
The software architecture will need to change and adapt as the project
requirements change.\

> *\"The only way to cope with these changes, is to keep refactoring and
> adapting our architecture. Unfortunately, refactoring can be very
> dangerous. It is very easy to break existing code by refactoring and
> therefore people usually do not do it. Testing gives you the
> confidence. Tests prove whether the code still works, even after a
> major refactoring. This confidence is very important, because it
> empowers people to do refactoring and keep the architecture fresh\".*

### Documentation:

> *\"A well written test tells a story - a story about how to use the
> code under test, therefore tests can serve as a documentation. There
> is one big advantage over the classical documentation - this
> documentation will not get stale. As long as the tests are passing,
> the documentation is up to date.\"*

\
\... With tools such as Jasmine you can create documentation that always
reflects the product as it truly is.\
\

::: {#toc-section .toc-section}
**Playing With Protractor:**\

-   **Part One:** [My first exposure to an AngularJS web app: Testing
    using Protractor, Jasmine, and
    JavaScript](http://www.tjmaher.com/2016/09/playing-with-protractor-testing.html)
-   **Part Two:**  [Learning AngularJS with the PhoneCat Tutorial App:
    Installation, Setup, and Running
    Tests](http://www.tjmaher.com/2016/09/playing-with-protractor-learning.html)
-   **Part Three**: [The complexities of testing JavaScript frameworks,
    according to Vojtěch Jína, creator of Karma Test Runner for
    AngularJS](http://www.tjmaher.com/2016/09/playing-with-protractor-complexities-of.html)
:::

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
