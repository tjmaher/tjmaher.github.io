\-\-- layout: post title: Learning JavaScript date:
\'2016-10-02T01:55:00.001-04:00\' author: T.J. Maher tags: - JavaScript
- AngularJS - Protractor modified\_time:
\'2016-10-05T00:14:49.396-04:00\' thumbnail:
https://1.bp.blogspot.com/-\_\_oYvauS3sg/V\_FCmeHiH7I/AAAAAAAALeY/iV1p1O91-Qo3VOOP5dbXb7K9p4O3Fj5DgCLcB/s72-c/axel\_head.jpg
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-5005333658767438917
blogger\_orig\_url:
http://www.tjmaher.com/2016/10/learning-javascript.html \-\-- I want to
become fluent in JavaScript.\
\
Not that I am fluent in Java yet, mind you. I found out the hard way
that [knowing how to use Selenium WebDriver with
Java](http://www.tjmaher.com/2015/12/next-week-automating-amazon-how-i-am.html)
and [being able to sketch out Java code on a
whiteboard](http://techbeacon.com/how-pass-coding-interview-automation-developer)
are two different things. But I have been getting better.\
\
Why tackle JavaScript before solidifying what a [Software Development
Engineer in Test](http://www.tjmaher.com/search?q=SDET) working with
Java might need to learn?\
\
Web application development is shifting from heavy-weight or \"high
ceremony\" languages like Java, to Node.js style JavaScript frameworks.
Automation development is racing to catch up.\
\

-   [NightWatch.JS](http://nightwatchjs.org/) was launched by Andrei
    Rusu from Oslo, Norway. 
-   Google\'s [AngularJS](https://angularjs.org/) project constructed
    Protractor
-   SeleniumHQ released a Node.JS and [JavaScript implementation of
    Selenium
    WebDriver](https://github.com/SeleniumHQ/selenium/tree/master/javascript/node/selenium-webdriver)

\
Back when I spent my 2014 Christmas break taking Alan Richardson\'s
[famous online course on Selenium WebDriver with
Java](http://compendiumdev.co.uk/page.php?title=seleniumwebdrivercourse) and
dreaming about [switching from being a manual to an automated
tester](http://techbeacon.com/switching-careers-qa-manual-testing-automation-development),
the rule of thumb was to pair the automated test framework (*what used
to be called a \"test harness\" ten years ago*) with the web
application.\
\
[]{#more}\
\
You see, Coding and
[QA](https://www.linkedin.com/pulse/what-qa-engineer-thomas-f-t-j-maher-jr-)
are [two different
disciplines](http://techbeacon.com/first-days-automation-developer-take-my-advice-balancing-dev-qa),
even though in the [past two
years](https://www.linkedin.com/pulse/shifts-software-testing-industry-thomas-f-t-j-maher-jr-) the
lines between them have been severely blurred with the triple threat of
[Agile Software
Development](https://www.linkedin.com/pulse/agile-qa-engineer-automated-testing-thomas-f-t-j-maher-jr-),
[Selenium
WebDriver](https://www.linkedin.com/pulse/bit-selenium-automation-thomas-f-t-j-maher-jr-),
and [Continuous
Integration](http://www.tjmaher.com/2015/03/lecture-customizing-jenkins-sitespect.html).\
*\
*The people writing the automated tests have a concentration on writing
good quality and robust tests, not writing code. It helps having senior
people nearby who know the nuance of the programming language to help
them write the automated test framework.\

-   Ruby applications were paired with the Ruby bindings of Selenium
    WebDriver or Watir for setting up automated browser tests to check
    the web-based user interface.
-   Java applications were paired with the Java bindings of Selenium
    WebDriver.
-   C\# applications were paired with C\# bindings for Selenium
    WebDriver.
-   Using Selenium WebDriver with
    [Python](http://seleniumhq.github.io/selenium/docs/api/py/index.html)
    was also a logical choice. Manual testers without a history of
    coding seem to find Ruby or Python easier to pick up than Java or
    C\#. 

\
With the popularity of [Node.js](https://nodejs.org/),
[AngularJS](http://www.tjmaher.com/2016/09/playing-with-protractor-learning.html)
and other JavaScript frameworks, there have been a push to pair Selenium
WebDriver, an automated browser testing library, with JavaScript. Out of
the twelve companies I obtained on-site interviews within the past three
months:\
\

-   Almost half paired Selenium WebDriver with Java 8.
-   Two paired [Geb](http://www.gebish.org/manual/current/) with the
    Java based scripting language,
    [Groovy](http://www.tjmaher.com/2016/06/building-test-framework-with-gradle.html). 
-   One paired testing their AngularJS / PHP application with Composer.
    I was attempting to see if I could come up with a [Protractor /
    JavaScript /
    Jasmine](http://www.tjmaher.com/2016/09/playing-with-protractor-testing.html)
    solution for them. Protractor connects to Selenium WebDriver\'s API
    directly.
-   Four used [Nightwatch.js](http://nightwatchjs.org/), which also
    connects with Selenium WebDriver\'s API. 
-   Absolutely Zero mentioned just using Selenium HQ\'s [official
    JavaScript
    bindings](https://github.com/SeleniumHQ/selenium/tree/master/javascript/node/selenium-webdriver)\...
    they always Selenium with a wrapper\... I was wondering, why? Are
    the official JavaScript bindings too new? Why weren\'t they getting
    adopted? \... It could be that they are, but I just had a very small
    sample size. 

\
So, the next thing I need to tackle: Learning JavaScript. Two problems
though:\

-   I haven\'t coded in JavaScript since I took a grad school course in
    it ten years ago.
-   JavaScript sure has changed quite a bit since then, with ECMAScript
    6, or ES6. 

Luckily, Alex Rauschmayer, a JavaScript expert, has published two books
on the subject, [Speaking JavaScript](http://speakingjs.com/),
and [Exploring ES6](http://exploringjs.com/), negotiating with O\'Reilly
publishing that the HTML versions are completely free.\

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://1.bp.blogspot.com/-__oYvauS3sg/V_FCmeHiH7I/AAAAAAAALeY/iV1p1O91-Qo3VOOP5dbXb7K9p4O3Fj5DgCLcB/s200/axel_head.jpg){width="200" height="200"}](https://1.bp.blogspot.com/-__oYvauS3sg/V_FCmeHiH7I/AAAAAAAALeY/iV1p1O91-Qo3VOOP5dbXb7K9p4O3Fj5DgCLcB/s1600/axel_head.jpg)
                                                                                                     [*Thank you, Alex Rauschmayer!*]{style="font-size: small; text-align: start;"}
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

\
Alex Rauschmayer\'s free HTML version of his book **[Speaking
JavaScript](https://www.amazon.com/Speaking-JavaScript--Depth-Guide-Programmers/dp/1449365035)** *(3/12/2014)*
found at <http://speakingjs.com/es5/> can help answer some questions we
might be asking ourselves\...\
\

Why is JavaScript Called ECMAScript? 
-------------------------------------

> *\"ECMAScript is the official name for JavaScript. A new name became
> necessary because there is a trademark on JavaScript (held originally
> by Sun, now by Oracle). At the moment, Mozilla is one of the few
> companies allowed to officially use the name JavaScript because it
> received a license long ago. For common usage, these rules apply:
> \[\...\] JavaScript means the programming language. \[\...\]
> ECMAScript is the name used by the language specification. Therefore,
> whenever referring to versions of the language, people say
> ECMAScript\". - [**Speaking JavaScript, Chapter
> 01**](http://speakingjs.com/es5/ch01.html).*

\
Note: **Speaking JavaScript**, a good introductory book for coders who
know Java, PHP, C++, Ruby, etc is ECMAScript 5.\
\

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://4.bp.blogspot.com/-6JW9qMrtlIg/V_E-R3zSKHI/AAAAAAAALeE/SOy4hT0ZxF8EjCeLWnpxBrYy39smYLo6ACLcB/s320/speaking_javascript.jpg){width="243" height="320"}](https://4.bp.blogspot.com/-6JW9qMrtlIg/V_E-R3zSKHI/AAAAAAAALeE/SOy4hT0ZxF8EjCeLWnpxBrYy39smYLo6ACLcB/s1600/speaking_javascript.jpg)
                                                                                                                                       *<http://speakingjs.com/es5/>*
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

\
If I really love the work of an author, even though online free versions
may be available, I prefer to purchase a copy of the softcover book. I
now own a copy of **Speaking JavaScript**.\
\
ECMAScript 6, which came out last year is covered by his next book,
**Exploring ES6**. Technically, this brand new version of JavaScript has
been redubbed \"ECMAScript 2015\".\
\
Yes, Alex provides a free HTML version of Exploring ES6 online, at
<http://exploringjs.com/es6/> \... but if you want to support his work,
you can purchase a copy at LeanPub. As of this blog article, the book is
98% complete! Purchase it at <https://leanpub.com/exploring-es6/>.\
\

Who Created JavaScript?
-----------------------

\

> *\"JavaScript's creator, Brendan Eich, had no choice but to create the
> language very quickly (or other, worse technologies would have been
> adopted by Netscape). He borrowed from several programming languages:
> Java (syntax, primitive values versus objects), Scheme and AWK
> (first-class functions), Self (prototypal inheritance), and Perl and
> Python (strings, arrays, and regular expressions).*\
> *\
> \"JavaScript did not have exception handling until ECMAScript 3, which
> explains why the language so often automatically converts values and
> so often fails silently: it initially couldn't throw exceptions. On
> one hand, JavaScript has quirks and is missing quite a bit of
> functionality (block-scoped variables, modules, support for
> subclassing, etc.). On the other hand, it has several powerful
> features that allow you to work around these problems. In other
> languages, you learn language features. In JavaScript, you often learn
> patterns instead\". - [**Speaking JavaScript, Chapter
> 1**](http://speakingjs.com/es5/ch01.html).*

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://3.bp.blogspot.com/-AvBiGWeBiYc/V_E-lGDsSAI/AAAAAAAALeI/Qlz3tpYuKQMuqX-QAJpPo-IDXKOCQPKIQCLcB/s200/Brendan_Eich_Mozilla_Foundation_official_photo.jpg){width="200" height="200"}](https://3.bp.blogspot.com/-AvBiGWeBiYc/V_E-lGDsSAI/AAAAAAAALeI/Qlz3tpYuKQMuqX-QAJpPo-IDXKOCQPKIQCLcB/s1600/Brendan_Eich_Mozilla_Foundation_official_photo.jpg)
                                                                                                                                                              *Brendan Eich, Official Mozilla photo*
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

\
You can read a lot more about how and why Netscape and Sun Microsystems
back in 1995 created JavaScript in Alex Rauschmayer\'s [**Speaking
JavaScript, Chapter 4**](http://speakingjs.com/es5/ch04.html), and how
ECMAScript versions 1 thru 6 came about in [Chapter
5](http://speakingjs.com/es5/ch05.html) of the book.\
\

How Has JavaScript Evolved?
---------------------------

\
I never really knew JavaScript back in the mid 1990s.\
\
We were never formally introduced until grad school around 2001 or so.
It was a whirlwind introduction. We talked about JavaScript in the same
breath as Perl and CGI Programming when talking about Dynamic HTML.\
\
Sure, I bumped into JavaScript on the job, every now and then, mostly
used to sniff out what type of browser a person was using, and
displaying the appropriate page. But it really didn\'t hit the big time
until much later.\
\
Alex Rauschmayer goes into much more detail, in **[Speaking JavaScript,
Chapter 6](http://speakingjs.com/es5/ch06.html) **about JavaScript\'s
rise to fame, from Dynamic HTML in 1997 to:\
\

-   **2001**: Douglas Crockford invents [JSON](http://json.org/),
    JavaScript Object Notation, a lightweight alternative to passing
    data through XML. 
-   **2005**: Ajax (Asynchronous JavaScript and XML), debuted in Google
    Maps, where pages can be dynamically changed on-the-fly. Sometimes
    slowly\... Which then fails my Selenium WebDriver / Java browser
    tests.\
    \... Yes, I put in a *wait* statement.\
    \... Yes, I made sure that the wait statement isn\'t just
    *Thread.sleep()*.\
    \... Yes, the wait statement I put in is polling the DOM every 10
    seconds, waiting for that slow-loading component to load up.\
    \... No, I can\'t set the wait more than 10 or so seconds\... if I
    do that then Sauce Labs automatically fails the test due to timeouts
    after 90 seconds.\
    \... No, it\'s not the test that is flaky. The test is compensating
    for a web app component being slow.\
    \
    \... Be right back. I need to go lie down. It\'s been a long day at
    work.
-   **2008**: [V8](https://developers.google.com/v8/): \"When Google
    introduced its Chrome web browser, one of its highlights was a fast
    JavaScript engine called V8. It changed the perception of JavaScript
    as being slow and led to a speed race with other browser vendors
    from which we are still profiting. V8 is open source and can be used
    as a standalone component whenever you need a fast embedded language
    that is widely known\".
-   **2009**: [Node.js](https://nodejs.org/): \"Node.js lets you
    implement servers that perform well under load. To do so, it uses
    event-driven, nonblocking I/O and JavaScript (via V8)\". Created by
    Ryan Dahl.

<div>

**[Get Started With NPM]{.underline}**\

\
Other changes that happened:

</div>

<div>

**2009**: ECMAScript 5 standardized.

**2010**: [AngularJS](https://angularjs.org/), a web application
framework built by Google released. To test and measure Angular apps,
Google releases [Protractor](http://www.protractortest.org/).

**2010**: The Node Package Manager (npm) appeared. A Must Read: \"[What
is NPM](https://docs.npmjs.com/getting-started/what-is-npm)?\".
Developers submit their Node.js applications
to <https://www.npmjs.com/>. If you wish to use their application, to
install it, you can run from the command line (Mac Terminal or Windows
Command Prompt) the command: *npm install -g (or \--global)*, and add
whatever program you want to install, whether it is: 

\

-   *[npm install angular](https://www.npmjs.com/package/angular) *to
    use Google\'s AngularJS to create web-based front-end systems
-   [*npm install protractor*](https://www.npmjs.com/package/protractor)
    to install the end-to-end testing tool created just for AngularJS
-   *[npm install
    selenium-webdriver](https://www.npmjs.com/package/selenium-webdriver) *to
    download the Official Selenium JavaScript bindings.
-   [*npm install
    nightwatch*](https://www.npmjs.com/package/nightwatch), Andrei
    Rusu\'s browser testing solution which combines Node.js, accesses
    the Selenium WebDriver API directly, and wraps tests using the Mocha
    test runner.
-   [*npm install
    geckodriver*](https://www.npmjs.com/package/geckodriver) if you want
    to run Firefox 47+ with your browser test suite. 
-   [*npm install mocha*](https://www.npmjs.com/package/mocha), a simple
    way to set up JavaScript tests that allows you to retry tests,
    dynamically create tests.  
-   [*npm install grunt*](https://www.npmjs.com/package/grunt), a
    JavaScript Task runner

\
\

**2011**: New version of JavaScript, in beta, to be version 6, code
named \"[Harmony](http://wiki.apache.org/harmony/)\". ( Read about it
in Alex Rauschmayer\'s [**Exploring ES6, Chapter
1**](http://exploringjs.com/es6/ch_about-es6.html#ecmascript-history),
to be released [soon](https://leanpub.com/exploring-es6/) )

**2011**: [Mocha, a JavaScript Test Runner](https://mochajs.org/)
released. 

**2013**: Vojtěch Jína writes about the [complexities of testing
JavaScript
frameworks](http://www.tjmaher.com/2016/09/playing-with-protractor-complexities-of.html),
introducing the Karma Test Runner in his Masters thesis. 

**2015**: ECMAScript 6 is standardized. Maybe it should be called ECMA
2015? And have yearly releases? Darn, ECMAScript 6 stuck.

**2016**? \... ECMAScript2016, formerly ECMA 7, should come out? 

</div>

So, Should We Not Learn ECMAScript 5? 
--------------------------------------

<div>

\

</div>

Alex Rauschmayer says, no, ECMAScript 5 is still useful:\

-   \"ECMAScript 6 is a superset of ECMAScript 5 -- new JavaScript
    versions must never break existing code. Thus, nothing you learn
    about ECMAScript 5 is learned in vain.
-   \"There are several ECMAScript 6 features that kind of replace
    ECMAScript 5 features, but still use them as their foundations. It
    is important to understand those foundations. Two examples: classes
    are internally translated to constructors and methods are still
    functions (as they have always been).
-   \"As long as ECMAScript 6 is compiled to ECMAScript 5, it is useful
    to understand the output of the compilation process. And you'll have
    to compile to ES5 for a while (probably years), until you can rely
    on ES6 being available in all relevant browsers.
-   \"It's important to be able to understand legacy code\".
    **-*[Exploring ES6, Chapter
    2](http://exploringjs.com/es6/ch_faq.html)***

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://2.bp.blogspot.com/-ITsv1wlCkVA/V_E-6eCIHVI/AAAAAAAALeM/CUtLFrMxqG4KlOjgpO-H4AwnN-_iiVU6wCLcB/s320/exploring_es6.jpg){width="225" height="320"}](https://2.bp.blogspot.com/-ITsv1wlCkVA/V_E-6eCIHVI/AAAAAAAALeM/CUtLFrMxqG4KlOjgpO-H4AwnN-_iiVU6wCLcB/s1600/exploring_es6.jpg)
                                                                                                                                  *<http://exploringjs.com/>*
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

<div>

I don\'t yet own a copy of this. I want to wait until it is absolutely
finished before buying a softcover copy.\
\

</div>

What Spurred JavaScript Updates Such As ECMAScript 2015?
--------------------------------------------------------

\
For that answer, we can go to Nicholas Zakas and his brand new book
**[Understanding ECMAScript
6](https://www.amazon.com/Understanding-ECMAScript-Definitive-JavaScript-Developers/dp/1593277571)**,
which was just published September 3, 2016. The free version, as the
book was being developed, is still on LeanPub,
at <https://leanpub.com/understandinges6/>\
\

> ::: {dir="ltr" lang="en"}
> In case you missed it: the print version of Understanding ECMAScript 6
> is now available. <https://t.co/oWwCnhZt8J>
> :::
>
> --- Nicholas C. Zakas (\@slicknet) [September 6,
> 2016](https://twitter.com/slicknet/status/773178719821193220)

From [**Understanding ECMAScript 6**: Introduction: *The Road to
ECMAScript
6*](https://leanpub.com/understandinges6/read#leanpub-auto-the-road-to-ecmascript-6):\

> \"In 2007, JavaScript was at a crossroads. The popularity of Ajax was
> ushering in a new age of dynamic web applications, while JavaScript
> hadn't changed since the third edition of ECMA-262 was published in
> 1999. TC-39, the committee responsible for driving the ECMAScript
> development process, put together a large draft specification for
> ECMAScript 4. ECMAScript 4 was massive in scope, introducing changes
> both small and large to the language. Updated features included new
> syntax, modules, classes, classical inheritance, private object
> members, optional type annotations, and more.\
> \
> \"The scope of the ECMAScript 4 changes caused a rift to form in
> TC-39, with some members feeling that the fourth edition was trying to
> accomplish too much. A group of leaders from Yahoo, Google, and
> Microsoft created an alternate proposal for the next version of
> ECMAScript that they initially called ECMAScript 3.1. The \'3.1\' was
> intended to show that this was an incremental change to the existing
> standard.\
> \
> \"ECMAScript 3.1 introduced very few syntax changes, instead focusing
> on property attributes, native JSON support, and adding methods to
> already-existing objects. Although there was an early attempt to
> reconcile ECMAScript 3.1 and ECMAScript 4, this ultimately failed as
> the two camps had difficulty with the very different perspectives on
> how the language should grow.\
> \
> \"In 2008, Brendan Eich, the creator of JavaScript, announced that
> TC-39 would focus its efforts on standardizing ECMAScript 3.1. They
> would table the major syntax and feature changes of ECMAScript 4 until
> after the next version of ECMAScript was standardized, and all members
> of the committee would work to bring the best pieces of ECMAScript 3.1
> and 4 together after that point into an effort initially nicknamed
> ECMAScript Harmony.\
> \
> \"ECMAScript 3.1 was eventually standardized as the fifth edition of
> ECMA-262, also described as ECMAScript 5. The committee never released
> an ECMAScript 4 standard to avoid confusion with the now-defunct
> effort of the same name. Work then began on ECMAScript Harmony, with
> ECMAScript 6 being the first standard released in this new
> \'harmonious\' spirit.\
> \
> \"ECMAScript 6 reached feature complete status in 2015 and was
> formally dubbed "ECMAScript 2015." (But this text still refers to it
> as ECMAScript 6, the name most familiar to developers.) The features
> vary widely from completely new objects and patterns to syntax changes
> to new methods on existing objects. The exciting thing about
> ECMAScript 6 is that all of its changes are geared toward solving
> problems that developers actually face\".

Can\'t wait to read the rest of the book!\
\

How Does JavaScript and Selenium WebDriver Intersect?
-----------------------------------------------------

To talk about how JavaScript and Selenium WebDriver intersect, let\'s
jump to a different source, Dave Haeffner and his [Selenium
Guidebook](https://seleniumguidebook.com/).\
\

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://2.bp.blogspot.com/-Md-RRAV3Vzw/V_E8QsNXEcI/AAAAAAAALd4/uzn0Ml05NIgPC08kc5zk293AihCEuWSUACLcB/s320/bookcover.png){width="246" height="320"}](https://2.bp.blogspot.com/-Md-RRAV3Vzw/V_E8QsNXEcI/AAAAAAAALd4/uzn0Ml05NIgPC08kc5zk293AihCEuWSUACLcB/s1600/bookcover.png)
                                                                                                                                *The Selenium Guidebook*
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

\
\
I [wrote about Dave last
year](http://www.tjmaher.com/2015/06/spotlight-on-dave-haeffner.html),
covering his free blog [Elemental Selenium and its Archive of
Tips](http://elementalselenium.com/tips) ( see the
[sourcecode](https://github.com/tourdedave/elemental-selenium-tips)),
his countless numbers of free instructional videos on YouTube, his
wonderful site, [The-Internet](http://the-internet.herokuapp.com/),
which I used when I was demoing the first automation test framework in
Java [that I had
encountered](http://www.tjmaher.com/2015/06/simple-manipulation-of-login-page.html),
and his guidebook, now written for Java, Ruby, Python, C\#, and
JavaScript.\

> ::: {dir="ltr" lang="en"}
> [\@tjmaher1](https://twitter.com/tjmaher1) Thanks! Wish I had a better
> answer for the username other than \"I thought it sounded clever\".
> :::
>
> --- Dave Haeffner (\@TourDeDave) [June 8,
> 2015](https://twitter.com/TourDeDave/status/608010880308113410)

I purchased his [Selenium Guidebook](https://seleniumguidebook.com/) -
JavaScript Version. The current price of just the Handbook alone seems a
bit expensive at \$59.00 for an e-Book, but since I am using his free
material all the time, I might as well *finally* pay for some of his
work. The e-Book is published in many different types, includes
JavaScript code examples, and a copy of the Automated Visual Checker
guide.\
\
Dave Haeffner\'s target audience seems to be for us Quality Assurance
Engineers, who may or may not really be familiar with coding. Alex
Rauschmayer\'s work in [Speaking JavaScript](http://speakingjs.com/)
might be just slightly over our heads? Dave\'s walkthrough for manual
testers covers:\

-   The Officially Supported [Selenium JavaScript
    bindings](https://github.com/SeleniumHQ/selenium/tree/master/javascript/node/selenium-webdriver). 
-   How to set up [Node.js](https://nodejs.org/en/) on a Mac, Windows,
    or Linux machine. 
-   How to use
    [NPM](https://docs.npmjs.com/getting-started/what-is-npm), the Node
    Package Manager
-   How to use [Mocha](https://mochajs.org/), a test runner
-   How to use [Grunt](http://gruntjs.com/), a task runner which can run
    tasks in parallel
-   Links to sites such as Mozilla\'s \"[Introductions to Object
    Oriented
    JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Introduction_to_Object-Oriented_JavaScript)\"
-   How to use Page Object patterns with JavaScript

<div>

Officially Supported [Selenium JavaScript
bindings](https://github.com/SeleniumHQ/selenium/tree/master/javascript/node/selenium-webdriver): [API
documentation](http://seleniumhq.github.io/selenium/docs/api/javascript/).\
\
\... I\'ve always wondered about [**The Selenium
Guidebook**](https://seleniumguidebook.com/): **The Complete Package**
and what it was like\...\
\
I\'ve only ever looked at just the books, first the Java version last
year, and the JavaScript version this year. To get around the fact that
I didn\'t purchase the pre-packaged videos, I subscribe to free [Sauce
Labs Webinars](https://saucelabs.com/resources/webinars) that feature
him, then see if he has anything [new on
YouTube](https://www.youtube.com/results?search_query=dave+haeffner).\
\
Most of all, I wonder about the **Selenium Guidebook: The Complete
Package** and the 10 seat license, currently \$799. (\$80 per person for
a group, rather than \$299 per person)\
\
I\'ve run meetings, such as bug tracking triage sessions. I\'ve hosted
very informal training sessions. I\'ve given many an end-of-sprint
product demo session.\
\
What I would really love to do is join a team of software testers \-- a
good mixture of mostly manual testers, a few automated testers, and
maybe a Sr. JavaScript coder since I only know Java \-- and see if we
can break the material down into separate sessions for self-study, where
I can act more as a moderator trying to find the answers out with the
team, than a lead with all of the answers.\
\
If the group gets stuck on something, we could just email or send a
tweet to Dave Haeffner for help.\
\
Dave Haeffner also allows people to contact him for help, personally, in
30 minute increments, with his Office Hours at
<https://www.sohelpful.me/tourdedave> \...\
\
I had been looking for Lead positions\... I need to make sure to pitch
this as an idea\...\
\

</div>

<div>

\

</div>

What To Use To Write JavaScript Code?
-------------------------------------

<div>

Dave Haeffner writes in his Selenium Guidebook, about what Text Editor
to use when coding in JavaScript.  

</div>

> \"In order to write Node.js code, you will need to use a text editor.
> Some popular ones are
> [Vim](http://www.vim.org/), [Emacs](http://www.gnu.org/software/emacs/),
> and [Sublime Text](https://www.sublimetext.com/3).\
> \
> \"There\'s also the option of going for an IDE (Integrated Development
> Environment) like
> [WebStorm](https://www.jetbrains.com/webstorm/). It\'s not free, but
> there is a free 30-day trial.\
> \
> \"It\'s important to pick an editor that works for you and makes you
> productive. So if you\'re new to programming and text editors then
> it\'s probably best to go with something more intuitive like Sublime
> Text or WebStorm. If you end up using WebStorm be sure to check out
> the documentation on using it with Mocha
> ([link](https://www.jetbrains.com/help/webstorm/2016.2/running-mocha-unit-tests.html?search=mocha))\".
> - *Dave Haeffner, **Selenium Guidebook**, JavaScript Edition*

Personally, I like Sublime Text, which is now up to version 3.\
\
Want to build and run your JavaScript programs inside **Sublime Text
3**? Here is a walkthrough of what I have found:\
\

-   Check to see if you have Node already installed. Open a Command
    Prompt on a Windows machine or the Terminal on the Mac, and type:
    *node \--version*. Doesn\'t work? Go to <https://nodejs.org/> \...
    current version is 4.6.0. I like installing it globally so I can use
    node commands from any directory. 
-   Take a look at Pawel Grzybek\'s article [JavaScript console in
    Sublime Text
    3](https://pawelgrzybek.com/javascript-console-in-sublime-text/). It
    shows how to create a new Sublime Text build system you can call
    \"JavaScript\". On my Windows 10 system at home I used *\"cmd\" :
    \[\"node\", \"\$file\"\]* and *\"selector\": \"source.js\"* to the
    new file, which I called \"JavaScript.sublime-build\".  
-   Need to find exactly where Node has been installed? Try from the
    command line: *which node* or *where node*. 
-   Not familiar with the Command Line? Need help? See [my post last
    year](http://www.tjmaher.com/2015/05/learning-command-line-interface.html).

\
\

What Thought Leaders Could We Follow?
-------------------------------------

<div>

Read the new TechBeacon article written by Mitchell Long, [41 JavaScript
Experts to Follow on
Twitter](http://techbeacon.com/javascript-leaders-you-should-follow-twitter) published
9/30/2016.\
\
\

</div>

What If We Need More Hands-On Instruction on JavaScript?
--------------------------------------------------------

\
I am still attempting to find good (and free) online starter courses in
JavaScript that are not woefully outdated. The mission of this blog is
to help fellow software testers to be able to switch from manual to
automated testing, so I would love to find courses where previous coding
experience isn\'t required.\
**[\
]{.underline}[Lynda.com]{.underline}**\
**[\
]{.underline}**Check to see if your local library or local university
have free subscriptions to [Lynda.com](https://www.lynda.com/), an
online learning site. If you are a member of the [Boston Public
Library](https://www.bpl.org/kbl/2015/12/08/lynda-com-is-live/), you can
sign up for a free subscription. Lynda has one course on ES6, but most
of their courses are years and years out of date.\
\
**[ModernJavaScript]{.underline}**\
\
From AngularClass, there is a free JavaScript course called
[ModernJavaScript](http://courses.angularclass.com/p/modern-javascript).
Good information. Some typos on the slides. Good video walkthrough of
the language.\
\
**[NodeSchool]{.underline}**\
\
[NodeSchool.io](http://nodeschool.io/#workshoppers) provides open-source
tutorials leading from JavaScript all the way up to Node. You need to
have Node.js installed on your machine, so you can used the Node Package
Manager.\
\

-   [JavaScripting](https://github.com/sethvincent/javascripting)
-   [LearnYouNode](https://github.com/workshopper/learnyounode)
-   [GitIt](https://github.com/jlord/git-it)
-   [HowToNPM](https://github.com/npm/how-to-npm)
-   [Functional JavaScript
    Workshop](https://github.com/timoxley/functional-javascript-workshop):
    Old E5 version

<div>

\... There are many other tutorials!

</div>

\
**[Udacity:]{.underline}**\
\
[JavaScript
Basics](https://www.udacity.com/course/javascript-basics--ud804) is part
of Udacity\'s Front-End Web Developer nanodegree program put together by
AT&T, Google, GitHub, and Hack Reactor. Udacity has many a free course!
Go to <https://www.udacity.com/courses/all> and check off \"Free
Courses\" and \"JavaScript\" to see what they have.\
\
Each course does not teach you in a vacuum. You work towards building
your own application, such as with the [JavaScript
Promises](https://www.udacity.com/course/javascript-promises--ud898)
course, you can build a Public Transportation app.\
\
\
**[W3Schools]{.underline}**\
\
Although W3Schools [appears to have a bad
reputation](https://www.google.com/search?q=w3schools+bad), I have
always enjoyed their free courses. They do have [one on
JavaScript](http://www.w3schools.com/js/default.asp) that may be
promising.\
\
\
[**You Don\'t Know JS**]{.underline}\
Kyle Simpson\'s book series **You Don\'t Know JS** started off as a
[Kickstarter
Campaign](https://www.kickstarter.com/projects/getify/you-dont-know-js-book-series) back
in 2013. Recently, it is being updated with the ES6 functionality.\
\

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://1.bp.blogspot.com/-RWr8MVnGUUE/V_HRsDicIiI/AAAAAAAALeo/JVlifY_uvjcj4A5jhvH89rgS-D7Hm77AwCLcB/s400/you_don%2527t.png){width="400" height="293"}](https://1.bp.blogspot.com/-RWr8MVnGUUE/V_HRsDicIiI/AAAAAAAALeo/JVlifY_uvjcj4A5jhvH89rgS-D7Hm77AwCLcB/s1600/you_don%2527t.png)
                                                                                            *The [Kickstarter Campaign](https://www.kickstarter.com/projects/getify/you-dont-know-js-book-series)!*
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

With each book, it drills down into the specifics. This information is
also offered for free, on Kyle Simpson\'s GitHub site
at <https://github.com/getify/You-Dont-Know-JS>. The books cover:\
\

-   [Up and
    Going](https://github.com/getify/You-Dont-Know-JS/blob/master/up%20&%20going/README.md#you-dont-know-js-up--going):
    An introduction to get you up and going. 
-   [Scopes &
    Closures](https://github.com/getify/You-Dont-Know-JS/blob/master/scope%20&%20closures/README.md#you-dont-know-js-scope--closures):
    Lexical and Block Scope. Hoisting. Scope Closures.
-   [this & Object
    Prototypes](https://github.com/getify/You-Dont-Know-JS/blob/master/this%20&%20object%20prototypes/README.md#you-dont-know-js-this--object-prototypes):
     Objects, Prototypes, and E6\'s *class*
-   [Types and
    Grammar](https://github.com/getify/You-Dont-Know-JS/blob/master/types%20&%20grammar/README.md#you-dont-know-js-types--grammar):
    Types, Values, Natives, Coercion, Grammar
-   [ASync &
    Performance](https://github.com/getify/You-Dont-Know-JS/blob/master/async%20&%20performance/README.md#you-dont-know-js-async--performance):
    Callbacks, Promises, Generators, Benchmarking, Tuning
-   [ES6 &
    Beyond](https://github.com/getify/You-Dont-Know-JS/blob/master/es6%20&%20beyond/README.md#you-dont-know-js-es6--beyond):
    ES6, Syntax, Organization, Async Flow, Collections

\
\... Please note, the [entire e-Book
series](http://shop.oreilly.com/category/get/kyle-simpson-kit.do) is
being sold for \$37.60. The entire print series is \$68.\
\
\
Know of any free started JavaScript courses? Feel free to list them in
the comments!\
\

Need some side-by-side comparison of E6 with older versions of JavaScript?
--------------------------------------------------------------------------

\
If you already know JavaScript, and you want to see the exact
differences, side-by-side, go to[E6
Features.Org](http://es6-features.org/)\
\

  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://2.bp.blogspot.com/-jtY1k8ETLdI/V_EKgDWxdqI/AAAAAAAALdo/w-kIKS_8nlAZzjUPRVaR7ccfJUoD6wCsQCLcB/s400/e6.png){width="400" height="306"}](https://2.bp.blogspot.com/-jtY1k8ETLdI/V_EKgDWxdqI/AAAAAAAALdo/w-kIKS_8nlAZzjUPRVaR7ccfJUoD6wCsQCLcB/s1600/e6.png)
                                                                                                          [*http://es6-features.org/*](http://es6-features.org/)
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

\

Want to See What New Stuff Happened In the JavaScript World, Summer of 2016?
----------------------------------------------------------------------------

Are you completely drowning in information?\
\
Less than a month ago, someone posted the following question to
[Reddit\'s /r/JavaScript room](https://www.reddit.com/r/javascript/):\
\

> [\"[Could someone give me a quick synopsis of the last 3 months in the
> JS
> world?](https://www.reddit.com/r/javascript/comments/523yik/could_someone_give_me_a_quick_synopsis_of_the/){.title
> .may-blank}\"]{style="background-color: white; color: #551a8b; font-family: "verdana" , "arial" , "helvetica" , sans-serif; font-size: large; margin-bottom: 1px; margin-right: 0.4em; outline: none; overflow: hidden; padding: 0px; text-decoration: none;"}

\... You could spend days attempting to footnote the responses!\
\
[*https://www.reddit.com/r/javascript/comments/523yik/could\_someone\_give\_me\_a\_quick\_synopsis\_of\_the/*](https://www.reddit.com/r/javascript/comments/523yik/could_someone_give_me_a_quick_synopsis_of_the/)\
\

Want Even More?
---------------

\
Read \"How it Feels To Learn JavaScript in 2016\" by Jose Aguinaga.\
\

> I just published "How it feels to learn Javascript in 2016"
> <https://t.co/eLc8g704LQ>
>
> --- Jose Aguinaga (\@jjperezaguinaga) [October 3,
> 2016](https://twitter.com/jjperezaguinaga/status/782962239468867586)

\
Happy Testing!\
\
-T.J. Maher\
[Twitter](https://twitter.com/tjmaher1) \| [LinkedIn](https://www.linkedin.com/in/tjmaher1) \| [GitHub](https://github.com/tjmaher)\
\
*// Sr. QA Engineer since 1996, Automation Developer\
// Contributing Writer
for [TechBeacon.](http://techbeacon.com/contributors/thomas-maher)\
// \"Looking to move away from manual QA? Follow [Adventures in
Automation](http://www.tjmaher.com/) on
[Facebook](https://www.facebook.com/AdventuresInAutomation/)!\"*
