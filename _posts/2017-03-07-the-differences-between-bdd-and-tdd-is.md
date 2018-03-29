\-\-- layout: post title: What is the Difference Between TDD and BDD?
date: \'2017-03-07T08:10:00.001-05:00\' author: T.J. Maher tags: - bdd -
tdd modified\_time: \'2017-04-02T12:56:50.446-04:00\' blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-6330697441990918810
blogger\_orig\_url:
http://www.tjmaher.com/2017/03/the-differences-between-bdd-and-tdd-is.html
\-\-- Have you ever had someone ask you a question, and in the process
of answering the question, you weren\'t really sure if you were giving
the correct answer?\
\
This happened yesterday where I am working as a contract Sr. QA
Engineer.\
\
**Question: \"What is the Difference Between BDD and TDD? Is it the same
thing?\"**\
\
The answer I gave: No.\
*\
Why?*\
*\
***BDD:** Behavior Driven Development\
**TDD:** Test Driven Development\
\
**BDD** is a way a business analyst and a QA Engineer can fashion the
requirements and the tests.\
**TDD** is a way of software development. Fashion the unit test first,
then the code that supports the test.\
\
**BDD** is using the Given / Then / When format [Dan
North](https://dannorth.net/introducing-bdd/) came up with when working
with **TDD** (Article, Better Software, [Introducing
BDD](https://dannorth.net/introducing-bdd/), March 2006), that [Martin
Fowler](https://martinfowler.com/bliki/GivenWhenThen.html) then echoed
(Blog,
[GivenTHenWhen](https://martinfowler.com/bliki/GivenWhenThen.html), Aug.
2013), that the Cucumber people with their Gherkin-style language ran
away with.\
*\
*That was the answer I gave\... How could I have made my answer
simpler?\
\
- - -\
\
Here is more information that I found while I was doing research:\
*\
Why is the famous BDD tool called Cucumber? [[[Aslak
Hellesøy](https://www.quora.com/profile/Aslak-Helles%C3%B8y) didn\'[[t
want to pick a geeky name. [Read what he said on
Quora](https://www.quora.com/profile/Aslak-Helles%C3%B8y) about why he
picked that
name. ]{style="font-size: 15px;"}]{style="color: #333333; font-family: q_serif, Georgia, Times, Times New Roman, serif;"}]{#__w2_sAsfT7e_link}]{#kjuksA}*\
\
**\
BDD** style had a direct link from Dan North to Aslak Hellsoy, when Dan
donated his rbehave for Ruby to the RSpec project and the RSpec Story
Runner that Aslak Hellsoy came across. Aslak liked it, wanted to improve
it.\
\
**TDD, **using Java, for example, you would first write a bit of code in
the *src/test/java* branch, then the src/main/java branch, then back to
the *src/test/java* branch as code was being developed. Write the first
unit test, run it, and of course it will fail. **RED**. Write the code
to support the test. Everything passes? **GREEN**. Need to combine like
elements, similar elements in the code? **REFACTOR**.\
\
**TDD** had been around for a while before BDD. See Kent Beck\'s [Test
Driven Development: By
Example](https://www.amazon.com/Test-Driven-Development-Kent-Beck/dp/0321146530/)
(2002) or this Wikipedia article
on <https://en.wikipedia.org/wiki/Test-driven_development>\
\
So how did BDD come from TDD? Dan North \< <https://dannorth.net/> \> in
his article **[Introducing BDD](https://dannorth.net/introducing-bdd/)**
writes:\

> *\"While using and teaching agile practices like test-driven
> development (TDD) on projects in different environments, I kept coming
> across the same confusion and misunderstandings. Programmers wanted to
> know where to start, what to test and what not to test, how much to
> test in one go, what to call their tests, and how to understand why a
> test fails.\
> \"The deeper I got into TDD, the more I felt that my own journey had
> been less of a wax-on, wax-off process of gradual mastery than a
> series of blind alleys. I remember thinking "If only someone had told
> me that!" far more often than I thought "Wow, a door has opened." I
> decided it must be possible to present TDD in a way that gets straight
> to the good stuff and avoids all the pitfalls.\
> \"My response is behaviour-driven development (BDD). It has evolved
> out of established agile practices and is designed to make them more
> accessible and effective for teams new to agile software delivery.
> Over time, BDD has grown to encompass the wider picture of agile
> analysis and automated acceptance testing\".*\

Happy Testing!\
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
