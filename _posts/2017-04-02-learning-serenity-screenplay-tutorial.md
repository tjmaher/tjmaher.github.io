\-\-- layout: post title: \'Learning Serenity: The Screenplay Tutorial\'
date: \'2017-04-02T12:50:00.001-04:00\' author: T.J. Maher tags:
modified\_time: \'2017-04-02T12:59:27.636-04:00\' thumbnail:
https://1.bp.blogspot.com/-2v-khU2LqqM/WOErjn5kPfI/AAAAAAAALtU/7RsCS5swEC82Xsy0ZkQ0TiPGSccscid5gCLcB/s72-c/screenplay.png
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-4289552301649508149
blogger\_orig\_url:
http://www.tjmaher.com/2017/04/learning-serenity-screenplay-tutorial.html
\-\--

::: {.tr_bq}
We\'ve covered a lot with Serenity BDD over the past few weeks!
:::

-   [The Background and History of Serenity
    BDD](http://www.tjmaher.com/2017/03/serenity-bdd-automation-framework-that.html)
-   [How Behavior Driven Design grew out of Test Driven
    Development](http://www.tjmaher.com/2017/03/the-differences-between-bdd-and-tdd-is.html)
-   [Studying BDD using The Cucumber Book and BDD in
    Action](http://www.tjmaher.com/2017/03/learning-serenity-studying-bdd-using.html)
-   [How to Generate Sample Projects with Maven
    Archetypes](http://www.tjmaher.com/2017/03/learning-serenity-scaffolding-new.html)

\
This has all prepared us for John Ferguson Smart\'s tutorial on the
Serenity BDD Screenplay Pattern. See
<http://serenity-bdd.info/docs/articles/screenplay-tutorial.html>\

###   Why Replace the Page Object Pattern with The Screenplay Pattern? 

\
\
Personally, I am trying to learn Serenity BDD and the Screenplay pattern
because it is already the toolset and techniques we are already using
where I am assigned as a contractor. I just started my career in
automated testing two years ago.\
\
Why does John Ferguson Smart and his group recommend this pattern they
created? From [Page Objects Refactored: SOLID steps to the Screenplay /
Journey
Pattern](https://ideas.riverglide.com/page-objects-refactored-12ec3541990) (2/11/2016):\

> *\"PageObjects have been the staple of automated web testing for over
> seven years. Simon Stewart wrote the original [Selenium PageObject
> wiki entry](http://bit.ly/rg-pageobject) in 2009. The concept was
> introduced to help test-developers reduce maintenance issues that, for
> many, resulted in flaky tests. Some mistook this as issues with
> Selenium, rather than with their own coding practices. While
> PageObjects can act as training wheels and be a good place to start,
> in this article we show you issues inherent to PageObjects and the
> benefits of refactoring them using SOLID OO principles. We then
> introduce the Screenplay Pattern, an alternative approach that could
> save you the trouble\".*

\... I also heard that the Screenplay pattern has Appium built in as a
way to kick off mobile automation. I\'ll be investigating that, next!\
\

### How to Get Started

Following the instructions on [Writing automated acceptance tests using
Serenity and the Screenplay
Pattern](http://serenity-bdd.info/docs/articles/screenplay-tutorial.html):\
\

<div>

\"The easiest way to create a project skeleton for a Serenity Screenplay
project is to use the Maven Archetype Plugin. To do this, run the [mvn
archetype:generate]{style="font-family: Courier New, Courier, monospace;"}
command (with a filter to reduce the number of artifacts Maven proposes)
as shown here:\"

::: {.listingblock style="background-color: white; box-sizing: border-box; color: rgba(0, 0, 0, 0.8); direction: ltr; font-family: "Noto Serif", "DejaVu Serif", serif; font-size: 16px; margin: 0px 0px 1.25em; padding: 0px;"}
::: {.content style="box-sizing: border-box; direction: ltr; margin: 0px; padding: 0px; position: relative;"}
``` {style="background: rgb(247, 247, 248); border-radius: 4px; box-sizing: border-box; color: rgba(0, 0, 0, 0.901961); direction: ltr; font-family: "Droid Sans Mono", "DejaVu Sans Mono", monospace; font-size: 0.90625em; line-height: 1.45; padding: 1em; text-rendering: optimizeSpeed; white-space: pre-wrap; word-wrap: break-word;"}
$ mvn archetype:generate -Dfilter=screenplay
...
[INFO] No archetype defined. Using maven-archetype-quickstart (org.apache.maven.archetypes:maven-archetype-quickstart:1.0)
Choose archetype:
1: remote -> net.serenity-bdd:serenity-junit-screenplay-archetype (Serenity automated acceptance testing project using Screenplay, Selenium 2 and JUnit)
Choose a number or apply filter (format: [groupId:]artifactId, case sensitive contains): :
```
:::
:::

\"\[\...\] You will then be prompted to enter a groupId, artifactId, and
version for your project, and a root package for your classes
\[\...\]\".\

::: {.paragraph style="background-color: white; box-sizing: border-box; color: rgba(0, 0, 0, 0.8); direction: ltr; font-family: "Noto Serif", "DejaVu Serif", serif; font-size: 16px; margin: 0px; padding: 0px;"}
:::

\

::: {.listingblock style="-webkit-text-stroke-width: 0px; background-color: white; box-sizing: border-box; color: rgba(0, 0, 0, 0.8); direction: ltr; font-family: "Noto Serif", "DejaVu Serif", serif; font-size: 16px; font-style: normal; font-variant-caps: normal; font-variant-ligatures: normal; font-weight: normal; letter-spacing: normal; margin: 0px 0px 1.25em; orphans: 2; padding: 0px; text-align: start; text-indent: 0px; text-transform: none; white-space: normal; widows: 2; word-spacing: 0px;"}
::: {.content style="box-sizing: border-box; direction: ltr; margin: 0px; padding: 0px; position: relative;"}
``` {style="background: rgb(247, 247, 248); border-radius: 4px; box-sizing: border-box; color: rgba(0, 0, 0, 0.901961); direction: ltr; font-family: "Droid Sans Mono", "DejaVu Sans Mono", monospace; font-size: 0.90625em; font-weight: 400; line-height: 1.45; margin: 0px; padding: 1em; text-rendering: optimizeSpeed; white-space: pre-wrap; word-wrap: break-word;"}
Choose a number or apply filter (format: [groupId:]artifactId, case sensitive contains): : 1
Define value for property 'groupId': : net.serenitybdd.tutorials
Define value for property 'artifactId': : todomvctests
Define value for property 'version':  1.0-SNAPSHOT: : 1.0.0-SNAPSHOT
Define value for property 'package':  net.serenitybdd.tutorials: :
Confirm properties configuration:
groupId: net.serenitybdd.tutorials
artifactId: todomvctests
version: 1.0.0-SNAPSHOT
package: net.serenitybdd.tutorials
 Y: : Y
```
:::
:::

\"You will find your new project in the screenplay-tutorial
directory\".\

::: {.paragraph style="background-color: white; box-sizing: border-box; color: rgba(0, 0, 0, 0.8); direction: ltr; font-family: "Noto Serif", "DejaVu Serif", serif; font-size: 16px; margin: 0px; padding: 0px;"}
:::

\

::: {.listingblock style="-webkit-text-stroke-width: 0px; background-color: white; box-sizing: border-box; color: rgba(0, 0, 0, 0.8); direction: ltr; font-family: "Noto Serif", "DejaVu Serif", serif; font-size: 16px; font-style: normal; font-variant-caps: normal; font-variant-ligatures: normal; font-weight: normal; letter-spacing: normal; margin: 0px 0px 1.25em; orphans: 2; padding: 0px; text-align: start; text-indent: 0px; text-transform: none; white-space: normal; widows: 2; word-spacing: 0px;"}
::: {.content style="box-sizing: border-box; direction: ltr; margin: 0px; padding: 0px; position: relative;"}
``` {style="background: rgb(247, 247, 248); border-radius: 4px; box-sizing: border-box; color: rgba(0, 0, 0, 0.901961); direction: ltr; font-family: "Droid Sans Mono", "DejaVu Sans Mono", monospace; font-size: 0.90625em; font-weight: 400; line-height: 1.45; margin: 0px; padding: 1em; text-rendering: optimizeSpeed; white-space: pre-wrap; word-wrap: break-word;"}
$ cd screenplay-tutorial
$ mvn clean verify
```
:::
:::

\... And the tests should run!\
\
Explore the tutorial to learn more about all the moving parts as shown
below:\
\

::: {.separator style="clear: both; text-align: center;"}
[![](https://1.bp.blogspot.com/-2v-khU2LqqM/WOErjn5kPfI/AAAAAAAALtU/7RsCS5swEC82Xsy0ZkQ0TiPGSccscid5gCLcB/s640/screenplay.png){width="640"
height="316"}](https://1.bp.blogspot.com/-2v-khU2LqqM/WOErjn5kPfI/AAAAAAAALtU/7RsCS5swEC82Xsy0ZkQ0TiPGSccscid5gCLcB/s1600/screenplay.png)
:::

\
Enjoy!\
\
And thank you for Learning Serenity with me! Happy Testing!\
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
