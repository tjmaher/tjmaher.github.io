\-\-- layout: post title: \'Learning Serenity: Studying BDD using The
Cucumber Book and BDD in Action\' date:
\'2017-03-27T20:21:00.001-04:00\' author: T.J. Maher tags:
modified\_time: \'2017-04-02T12:57:44.345-04:00\' blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-9039239769421678938
blogger\_orig\_url:
http://www.tjmaher.com/2017/03/learning-serenity-studying-bdd-using.html
\-\-- It's been a productive two weeks here at
[Ahold](https://www.aholddelhaize.com/en/home/) in Quincy, MA. They are
the the holding company for [Stop & Shop](https://stopandshop.com/),
Giant Foods, and Martin's, where I am testing mobile applications for
the iPhone, iPad and Android.\
\
Although I'm mostly focused on manual testing as I am attempting to get
to know the business, I've been trying to get myself up to speed with
the automation framework they are using, Serenity BDD. I have a long
term goal of combining their current Serenity BDD test suite with
Appium, so when we start developing a regression test suite, I can
possibly automate it.\

<div>

\
As I Tweeted a few days ago... Oh, this is going to take a while!\

> ::: {dir="ltr" lang="en"}
> [\@tjmaher1](https://twitter.com/tjmaher1)
> [\@AppiumDevs](https://twitter.com/AppiumDevs)
> [\@reactnative](https://twitter.com/reactnative)
> [\@Android](https://twitter.com/Android) You might want to see how
> integration with Serenity Screenplay could work, it might be faster.
> :::
>
> --- Serenity BDD (\@serenitybdd) [March 25,
> 2017](https://twitter.com/serenitybdd/status/845523395089481728)

\
\
Hrm... thank you, [Serenity BDD](https://twitter.com/serenitybdd)! I
need to look into that.\
\
Oh, and thank you very much, John Smart, for your words of encouragement
on this blog series:\

> An excellent introduction to Serenity BDD by
> [\@tjmaher1](https://twitter.com/tjmaher1) : <https://t.co/WXzk7wmLe8>
> [\#bdd](https://twitter.com/hashtag/bdd?src=hash)
> [\#SerenityBDD](https://twitter.com/hashtag/SerenityBDD?src=hash)
>
> --- John Ferguson Smart (\@wakaleo) [March 29,
> 2017](https://twitter.com/wakaleo/status/846969210911817728)

\
\
For now, since I am studying how to implement Serenity using a testing
framework invented by Aslak Hellesoy called \"Cucumber\".\

###  BDD and The Cucumber Book

For those who were wondering, the "BDD" in Serenity BDD stands for
"*Behavior Driven Development*". I first encountered BDD when I was
supervising an offshore testing team attempting to translate my manual
mobile test scripts into Cucumber / Ruby automation using Calabash-IOS.
That is when I first encountered Matt Wynne's "**The Cucumber Book:
Behaviour-Driven Development for Testers and Developers**" (2012), which
was quite helpful describing BDD.\

> *"[Matt Wynne](https://www.linkedin.com/in/mattwynne/) and [Aslak
> Hellesøy](https://www.linkedin.com/in/aslak/) \[the creator of
> Cucumber\] show you how to express your customers' wild ideas as a set
> of clear, executable specifications that everyone on the team can
> read. You'll learn how to feed those examples into Cucumber and let it
> guide your development. You'll build just the right code to keep your
> customers happy, and not a line more. Although it was born in the Ruby
> community, you can use Cucumber to test almost any system, from a
> simple shell script or Perl script, to web applications written in
> PHP, Java, or any platform". - [The Cucumber
> Book](https://pragprog.com/book/hwcuc/the-cucumber-book), The
> Pragmatic Bookshelf *

### About the Authors

\
Note: The Cucumber Book [now a second
edition](https://www.amazon.com/Cucumber-Book-Behaviour-Driven-Development-Developers/dp/1680502387/ref=pd_sbs_14_t_2?_encoding=UTF8&psc=1&refRID=GX1E3BZJSNG24E852W74),
released on February 27, 2017.

</div>

<div>

\
"**Matt Wynne** is a long-standing member of the Cucumber core team,
fascinated by the challenge of helping tech and business to understand
one another. He\'s one of the co-founders of Cucumber Ltd., the company
behind Cucumber. He lives on the west coast of Scotland on an old farm
with his family, two cats, their dog, and some ducks. Matt tweets from
[\@mattwynne](https://twitter.com/mattwynne) and
[\@cucumberbdd](https://twitter.com/cucumberbdd).\
\
"**Aslak Hellesoy** is the creator of Cucumber. During his career Aslak
has worked with both small and large organizations in industries such as
telecom, trading, insurance, car manufacturing, education, and
government. Aslak is a co-founder of Cucumber Ltd, the company behind
Cucumber. He tweets from \@aslak\_hellesoy and
[\@cucumberbdd](https://twitter.com/cucumberbdd).\
\
\"**Steve Tooke** is a programmer, trainer, and coach who is dedicated
to improving his craft and helping others improve theirs. He\'s a
co-founder of Cucumber Ltd. Steve tweets from
[\@tooky](https://twitter.com/tooky) and
[\@cucumberbdd](https://twitter.com/cucumberbdd)".\
\
\

### Oh, and Why Is It Called \"Cucumber\"?

Why the name \"Cucumber\"? Read [Aslak Hellesoy\'s answer on
Quora](https://www.quora.com/Why-is-the-Cucumber-tool-for-BDD-named-as-such),
how he asked his fiancee, Patty for naming suggestions:\
\
*\"Patty, I need a name for this new tool I just started hacking on. I
want it to have a catchy, non-geeky sounding name.\
\
\"She paused for a few seconds, then said: Cucumber!\
\
\"And I thought: Cucumber? Really? Well, it\'s a lot better than Stories
- so [I\'ll go with that for
now](https://github.com/cucumber/cucumber-ruby/commit/a9398c13d5a53b71e582050de92ae49e3524412c).
I\'ll rename it again when I come up with something better\".*\
\

### What is an Acceptance Test for a Feature?

\
Here's an example Matt Wynne lists in The Cucumber Book:\
\
**Feature**: Sign up\
     Sign up should be quick and friendly.\
**Scenario**: Successful sign up\
New users should get a confirmation email and be greeted personally by
the site once signed in.\
**Given** I have chosen to sign up\
**When** I sign up with valid details\
**Then** I should receive a confirmation email\
**And** I should see a personalized greeting message\
\
... This is an example of what is called an **acceptance** test.
*"Instead of a business stakeholder passing requirements to the
development team without much opportunity for feedback, the developer
and stakeholder collaborate to write automated tests that express the
outcome that the stakeholder wants. We call them acceptance tests
because they express what the software needs to do in order for the
stakeholder to find it acceptable. The test fails at the time of
writing, because no code has been written yet, but it captures what the
stakeholder cares about and gives everyone a clear signal as to what it
will take to be done".*\
\
The Product Owner, a business analyst representing the customer's wants
and needs on an Agile Software Development project can express a
client's wishes and expectations in an easy-to-read format. They can be
expressed in terms of **behavior** wanted in the finished product.\
\
As Matt Wynne mentions, "Acceptance tests written in this style become
more than just tests; they are executable specifications \[...\]\

> *"For many teams, they become the definitive source of truth as to
> what the system does. Having a single place to go for this information
> saves a lot of time that is often wasted trying to keep requirements
> documents, tests, and code all in sync. It also helps to build trust
> within the team, because different parts of the team no longer have
> their own personal versions of the truth". - [The Cucumber
> Book](https://www.amazon.com/Cucumber-Book-Behaviour-Driven-Development-Programmers/dp/1934356808)*

### 

### How Do Features Get Turned Into Steps and Step Definitions?  

But how does it work?\

> *"When you run \[Cucumber\], it reads in your specifications from
> plain-language text files called features, examines them for scenarios
> to test, and runs the scenarios against your system. Each scenario is
> a list of steps for Cucumber to work through. So that Cucumber can
> understand these feature files, they must follow some basic syntax
> rules. The name for this set of rules is Gherkin. Along with the
> features, you give Cucumber a set of step definitions, which map the
> business-readable language of each step into Ruby code to carry out
> whatever action is being described by the step. In a mature test
> suite, the step definition itself will probably just be one or two
> lines of Ruby that delegate to a library of support code, specific to
> the domain of your application, that knows how to carry out common
> tasks on the system. Normally that will involve using an automation
> library, like the browser automation library Capybara, to interact
> with the system itself". - The Cucumber Book*

### Does Serenity BDD Still Use Features Files and Step Definitions? 

\
If you are using Serenity BDD with Cucumber, it will follow the same
exact steps.\
\

-   **Narratives** describe the story you want to tell.
-   **Feature file**s describe the features of the product, breaking it
    down into scenarios outlining how the feature will be used.
-   **Step definitions** walk through step-by-step how to execute the
    code.

\

> *"Step definitions sit right on the boundary between the business's
> domain and the programmer's domain. \[...\] Their responsibility is to
> translate each plain-language step in your Gherkin scenarios into
> concrete actions in \[...\] code".*

### What is the difference between Steps and Step Definitions?

> *"Each Gherkin scenario is made up of a series of steps, written in
> plain language. On its own, a step is just documentation; it needs a
> step definition to bring it to life. A step definition is a piece of
> Ruby code that says to Cucumber, 'If you see a step that looks like
> this..., then here's what I want you to do....' When Cucumber tries to
> execute each step, it looks for a matching step definition to execute.
> So, how does Cucumber match a step definition to a step\"*

> *"Gherkin steps are expressed in plain text. Cucumber scans the text
> of each step for patterns that it recognizes, which you define using a
> regular expression. If you haven't used regular expressions before,
> then just think of them like a slightly more sophisticated version of
> the wildcards you'd use to search for a file". - The Cucumber Book*

\

### What is the Difference Between BDD and ATDD?

To answer this questions, let\'s jump to a sidebar in "[BDD in
Action](https://www.manning.com/books/bdd-in-action)" written by John
Ferguson Smart, the creator of Serenity BDD.\
\
"**BDD by any other name**\
\
"Many of the ideas around BDD are not new and have been practiced for
many years under a number of different names. Some of the more common
terms used for these practices include Acceptance-Test-Driven
Development, Acceptance Test-Driven Planning, and Specification by
Example. To avoid confusion, let's clarify a few of these terms in
relation to BDD.\
\
"*Specification by Example* describes the set of practices that have
emerged around using examples and conversation to discover and describe
requirements. In his seminal book of the same name,14 Gojko Adzic chose
this term as the most representative name to refer to these practices.
Using conversation and examples to specify how you expect a system to
behave is a core part of BDD, and we'll discuss it at length in the
first half of this book.\
\
"*Acceptance-Test-Driven Development* (ATDD) is now a widely used
synonym for Specification by Example, but the practice has existed in
various forms since at least the late 1990s. Kent Beck and Martin Fowler
mentioned the concept in 2000,15 though they observed that it was
difficult to implement acceptance criteria in the form of conventional
unit tests at the start of a project. But unit tests aren't the only way
to write automated acceptance tests, and since at least the early 2000s,
innovative teams have asked users to contribute to executable acceptance
tests and have reaped the benefits\
\
"*Acceptance-Test-Driven Planning* is the idea that defining acceptance
criteria for a feature leads to better estimates than doing a task
breakdown".\
\

### What is the Goal of BDD?

> *"One of the key goals of BDD is to ensure that everyone has a clear
> understanding of what a project is trying to deliver, and of the
> underlying business objectives of the project. This, in itself, goes a
> long way toward ensuring that the application actually meets these
> objectives.*

> *"You can achieve this by working with users and other stakeholders to
> define or clarify a set of high-level business goals for the
> application. These goals should provide a concise vision of what you
> need to build. Business goals are about delivering value, so it's
> common to see them expressed in terms of increasing or protecting
> revenue, or of decreasing costs". - BDD in Action*

\
Now that the research has been done, we can start assembling a new
Serenity BDD project..\

::: {.m_-1345518176849079807gmail-p2 style="background-color: white; color: #222222; font-family: arial, sans-serif; font-size: 12.8px;"}
\
:::

Until then, Happy Testing!\
\
\

::: {#toc-section .toc-section}
**Learning Serenity BDD**\

-   **Part One:** [Serenity BDD: An Automation Framework That Uses
    Specification by Example
    (SBE)](http://www.tjmaher.com/2017/03/serenity-bdd-automation-framework-that.html)
-   **Part Two:** [What is the Difference Between TDD and
    BDD?](http://www.tjmaher.com/2017/03/the-differences-between-bdd-and-tdd-is.html)
-   **Part Three:** [Studying BDD using The Cucumber Book and BDD in
    Action](http://www.tjmaher.com/2017/03/learning-serenity-studying-bdd-using.html)
-   **Part Four:** [Scaffolding a new project using Maven
    Archetypes](http://www.tjmaher.com/2017/03/learning-serenity-scaffolding-new.html)
-   **Part Five:** [Reviewing The Serenity Screenplay
    Tutorial](http://www.tjmaher.com/2017/04/learning-serenity-screenplay-tutorial.html)
:::

\
-T.J. Maher\
[Twitter](https://twitter.com/tjmaher1) \| [LinkedIn](https://www.linkedin.com/in/tjmaher1) \| [GitHub](https://github.com/tjmaher)\
\
*// Sr. QA Engineer, Software Engineer in Test, Software Tester since
1996.\
// Contributing Writer
for [TechBeacon.](http://techbeacon.com/contributors/thomas-maher)\
// \"Looking to move away from manual QA? Follow [Adventures in
Automation](http://www.tjmaher.com/) on
[Facebook](https://www.facebook.com/AdventuresInAutomation/)!\"*

</div>
