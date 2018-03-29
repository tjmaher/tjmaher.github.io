\-\-- layout: post title: \'Learning Serenity: Scaffolding a new project
with Maven Archetypes \' date: \'2017-03-31T00:39:00.003-04:00\' author:
T.J. Maher tags: - Angie Jones modified\_time:
\'2017-11-03T09:00:41.181-04:00\' blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-656466098013294545
blogger\_orig\_url:
http://www.tjmaher.com/2017/03/learning-serenity-scaffolding-new.html
\-\-- Imagine that you are starting a new job, where you encounter yet
another new [automated
toolset](http://www.tjmaher.com/2017/03/serenity-bdd-automation-framework-that.html)
you haven\'t heard of before. It means that you have:\
\

-   Even [more documentation](http://www.thucydides.info/docs/serenity/)
    to read, and research notes to compile. 
-   Code for another [open-source automation
    toolset](https://github.com/serenity-bdd/serenity-core) on GitHub to
    figure out. 
-   Yet another proof-of-concept you want to put together. 

\
This is why I blog: The only way to keep my head on straight is to take
copious amounts of research notes. This blog is where I store them.\
\
Am I struggling with a concept that I just can\'t get? I\'ve befriended
a few experts in my very short time as an automation developer (Hi,
Alan, Dave, Joe, Jim, James M, Joon, Lark, Martin, James V, Bas, and
Angie!) who really enjoy helping out beginners like me out. If I blog
about a problem I am having, and point to the post on Twitter, I get
excellent feedback from the automation community. Thank you all so
much!\
\
[]{#more}\
\
Take a look at January 2016\'s project, [Automate
Amazon](http://www.tjmaher.com/2015/12/automate-amazon-development-environment.html).
You have:\
\

-   Build Configuration file, written as either with Apache
    [Maven](http://www.tjmaher.com/search?q=Maven) pom.xml file or a
    [Gradle](http://www.tjmaher.com/search/label/Gradle) build.gradle
    file to set up all the third party dependencies. 
-   Test script classes written in frameworks such as
    [JUnit,](http://www.tjmaher.com/search/label/JUnit)
    [TestNG](http://www.tjmaher.com/search/label/TestNG) or
    [Spock](http://www.tjmaher.com/search?q=Spock) to execute the
    tests. 
-   Page Object classes that encapsulate the functionality on the page
    such as dropdown list boxes, radio buttons and text boxes. Public
    methods are created to, say, investigate the header text, or enter
    text into a textbox. 
-   Action classes that bundle the page object methods together, such as
    when you want to loginAs(String username, String password), and want
    to combine methods to enter usernames, passwords, and click on Login
    buttons. 
-   Driver classes that set up the browser you are going to run the web
    user interface test on. 

\
There are so many pre-conditions and moving parts, how the heck can
anyone keep it all straight!\
\
Luckily, there are scaffolding tools: Software tools that build out a
skeleton of a project, sample working code, and the folder structure.
Some tools, such [as this Yeoman
generator](http://www.tjmaher.com/2016/10/testing-internet-with-geb-groovy-spock.html),
are written by fans of the product. Some, though, are written by the
author of the automation toolset, itself!\
\
For this blog post, we will be taking a look at **Maven Archetypes**,
especially the ones that John Ferguson Smart, is the founder and lead
developer of Serenity BDD created.\
\

### What Is Apache Maven

From the Apache Maven Project: [What is
Maven](https://maven.apache.org/what-is-maven.html)?\
\
\"Maven, a [Yiddish word](https://en.wikipedia.org/wiki/Maven) meaning
accumulator of knowledge, was originally started as an attempt to
simplify the build processes in the Jakarta Turbine project. There were
several projects each with their own Ant build files that were all
slightly different and JARs were checked into CVS. We wanted a standard
way to build the projects, a clear definition of what the project
consisted of, an easy way to publish project information and a way to
share JARs across several projects.\
\
\"The result is a tool that can now be used for building and managing
any Java-based project. We hope that we have created something that will
make the day-to-day work of Java developers easier and generally help
with the comprehension of any Java-based project\".\

###  What Is A Maven Archetype

From the Apache Maven Project: [What is an
Archetype](https://maven.apache.org/archetype/index.html):\
\

<div>

\"In short, Archetype is a Maven project templating toolkit. An
archetype is defined as an original pattern or model from which all
other things of the same kind are made. The names fits as we are trying
to provide a system that provides a consistent means of generating Maven
projects. Archetype will help authors create Maven project templates for
users, and provides users with the means to generate parameterized
versions of those project templates.\
\
\"Using archetypes provides a great way to enable developers quickly in
a way consistent with best practices employed by your project or
organization. Within the Maven project we use archetypes to try and get
our users up and running as quickly as possible by providing a sample
project that demonstrates many of the features of Maven while
introducing new users to the best practices employed by Maven. In a
matter of seconds a new user can have a working Maven project to use as
a jumping board for investigating more of the features in Maven. We have
also tried to make the Archetype mechanism additive and by that we mean
allowing portions of a project to be captured in an archetype so that
pieces or aspects of a project can be added to existing projects. A good
example of this is the Maven site archetype. If, for example, you have
used the quick start archetype to generate a working project you can
then quickly create a site for that project by using the site archetype
within that existing project. You can do anything like this with
archetypes\".\
\

### How Do We Use A Maven Archetype?

From a Command Line utility, such a Mac Terminal, you start off calling
an archetype like so:

</div>

<div>

[\
]{.pln
style="font-family: "monaco" , "menlo" , "consolas" , "courier new" , monospace; font-size: 13px; white-space: pre-wrap;"}

</div>

<div>

[mvn archetype]{.pln
style="font-family: "monaco" , "menlo" , "consolas" , "courier new" , monospace; font-size: 13px; white-space: pre-wrap;"}[:]{.pun
style="color: #666600; font-family: "monaco" , "menlo" , "consolas" , "courier new" , monospace; font-size: 13px; white-space: pre-wrap;"}[generate]{.pln
style="font-family: "monaco" , "menlo" , "consolas" , "courier new" , monospace; font-size: 13px; white-space: pre-wrap;"}

</div>

<div>

\
.. And follow it by the [Maven Archetype
Plugin](http://maven.apache.org/archetype/maven-archetype-plugin/usage.html)
you want. For example, if you take a look at Serenity\'s GitHub page,
you will find
<https://github.com/serenity-bdd/serenity-maven-archetypes>\
\
[serenity-cucumber-archetype](https://github.com/serenity-bdd/serenity-maven-archetypes/tree/master/serenity-cucumber-archetype)\
[serenity-jbehave-archetype](https://github.com/serenity-bdd/serenity-maven-archetypes/tree/master/serenity-jbehave-archetype)\
[serenity-junit-archetype](https://github.com/serenity-bdd/serenity-maven-archetypes/tree/master/serenity-junit-archetype)\
[serenity-junit-screenplay-archetype](https://github.com/serenity-bdd/serenity-maven-archetypes/tree/master/serenity-junit-screenplay-archetype)\
\
There are so many choices! Which one should I pick?\

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
Okay! I will start with the Screenplay pattern! Thank you, Serenity BDD
for your help!\
\
You can see it stored in the Maven Repository
at <https://mvnrepository.com/artifact/net.serenity-bdd/serenity-junit-screenplay-archetype> and
see that it was updated January 2017.\
\

-   Open up a Mac Terminal 
-   Enter the following: *mvn archetype:generate
    serenity-junit-screenplay-archetype*

\
What happens next? Take a look at **Serenity BDD\'s Screenplay
Tutorial**
at <http://serenity-bdd.info/docs/articles/screenplay-tutorial.html>\
\

::: {.listingblock style="background-color: white; box-sizing: border-box; color: rgba(0, 0, 0, 0.8); direction: ltr; font-family: "Noto Serif", "DejaVu Serif", serif; font-size: 16px; margin: 0px 0px 1.25em; padding: 0px;"}
::: {.content style="box-sizing: border-box; direction: ltr; margin: 0px; padding: 0px; position: relative;"}
``` {style="background: rgb(247, 247, 248); border-radius: 4px; box-sizing: border-box; color: rgba(0, 0, 0, 0.901961); direction: ltr; font-family: "Droid Sans Mono", "DejaVu Sans Mono", monospace; font-size: 1em; line-height: 1.45; padding: 1em; text-rendering: optimizeSpeed; white-space: pre-wrap; word-wrap: break-word;"}
Choose archetype:
1: remote -> net.serenity-bdd:serenity-junit-screenplay-archetype (Serenity automated acceptance testing project using Screenplay, Selenium 2 and JUnit)
Choose a number or apply filter (format: [groupId:]artifactId, case sensitive contains): :
```
:::
:::

\"This will (after downloading list all of the available Serenity
screenplay archetypes. For this tutorial, we will be working with JUnit,
so enter the number corresponding to the
net.serenity-bdd:serenity-junit-screenplay-archetypeentry (\"1\" in the
example shown here).\
\
\"You will then be prompted to enter a groupId, artifactId, and version
for your project, and a root package for your classes\"

</div>

<div>

.\

::: {.listingblock style="background-color: white; box-sizing: border-box; color: rgba(0, 0, 0, 0.8); direction: ltr; font-family: "Noto Serif", "DejaVu Serif", serif; font-size: 16px; margin: 0px 0px 1.25em; padding: 0px;"}
::: {.content style="box-sizing: border-box; direction: ltr; margin: 0px; padding: 0px; position: relative;"}
``` {style="background: rgb(247, 247, 248); border-radius: 4px; box-sizing: border-box; color: rgba(0, 0, 0, 0.901961); direction: ltr; font-family: "Droid Sans Mono", "DejaVu Sans Mono", monospace; font-size: 1em; line-height: 1.45; padding: 1em; text-rendering: optimizeSpeed; white-space: pre-wrap; word-wrap: break-word;"}
Choose a number or apply filter (format: [groupId:]artifactId, case sensitive contains): : 1
Define value for property 'groupId': : net.serenitybdd.tutorials
Define value for property 'artifactId': : todomvctests
Define value for property 'version':  1.0-SNAPSHOT: : 1.0.0-SNAPSHOT
Define value for property 'package':  net.serenitybdd.tutorials: :
Confirm properties configuration:
groupId: // Entered com.tjmaher.com.serenity-archetype-generated
artifactId: // Entered serenity-archetype-generated

version: 1.0.0-SNAPSHOT
package: [Default]
 Y: : Y
```
:::
:::

\"Maven will now generate a project skeleton for you\":

</div>

<div>

\
\

::: {.paragraph style="background-color: white; box-sizing: border-box; color: rgba(0, 0, 0, 0.8); direction: ltr; font-family: "Noto Serif", "DejaVu Serif", serif; font-size: 16px; margin: 0px; padding: 0px;"}
:::

\

::: {.listingblock style="-webkit-text-stroke-width: 0px; background-color: white; box-sizing: border-box; color: rgba(0, 0, 0, 0.8); direction: ltr; font-family: "Noto Serif", "DejaVu Serif", serif; font-size: 16px; font-style: normal; font-variant-caps: normal; font-variant-ligatures: normal; font-weight: normal; letter-spacing: normal; margin: 0px 0px 1.25em; orphans: 2; padding: 0px; text-align: start; text-indent: 0px; text-transform: none; white-space: normal; widows: 2; word-spacing: 0px;"}
::: {.content style="box-sizing: border-box; direction: ltr; margin: 0px; padding: 0px; position: relative;"}
``` {style="background: rgb(247, 247, 248); border-radius: 4px; box-sizing: border-box; color: rgba(0, 0, 0, 0.901961); direction: ltr; font-family: "Droid Sans Mono", "DejaVu Sans Mono", monospace; font-size: 1em; font-weight: 400; line-height: 1.45; margin: 0px; padding: 1em; text-rendering: optimizeSpeed; white-space: pre-wrap; word-wrap: break-word;"}
Y: : Y
[INFO] ----------------------------------------------------------------------------
[INFO] Using following parameters for creating project from Archetype: serenity-junit-screenplay-archetype:1.1.19
[INFO] ----------------------------------------------------------------------------
[INFO] Parameter: groupId, Value: net.serenitybdd.tutorials
[INFO] Parameter: artifactId, Value: todomvctests
[INFO] Parameter: version, Value: 1.0.0-SNAPSHOT
[INFO] Parameter: package, Value: net.serenitybdd.tutorials
[INFO] Parameter: packageInPathFormat, Value: net/serenitybdd/tutorials
[INFO] Parameter: package, Value: net.serenitybdd.tutorials
[INFO] Parameter: version, Value: 1.0.0-SNAPSHOT
[INFO] Parameter: groupId, Value: net.serenitybdd.tutorials
[INFO] Parameter: artifactId, Value: todomvctests
[INFO] project created from Archetype in dir: /Users/john/Projects/OpenSource/serenity/serenity-articles/screenplay-tutorial/sample-code/screenplay-tutorial
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time: 04:52 min
[INFO] Finished at: 2016-02-15T09:16:05+00:00
[INFO] Final Memory: 16M/309M
[INFO] ------------------------------------------------------------------------
```
:::
:::

Want to examine the sample code? I uploaded the code [to my GitHub
repository.](https://github.com/tjmaher/serenity-archetype-generated)\
\

### What does the Sample Project Do?

Under src/main/java:\
**\
[Page Objects Generated:]{.underline}**\
**[\
]{.underline}**Imagine if you were going to automate
[Wiktionary.com](https://en.wiktionary.org/wiki/Wiktionary:Main_Page),
encapsulating the functionality of the page into a Page Object. How
would you do that? Here is how Jon Smart did it:\
\
[DictionaryPage.java](https://github.com/tjmaher/serenity-archetype-generated/blob/master/src/main/java/com/tjmaher/serenity-archetype-generated/pages/DictionaryPage.java):
An abstraction of the Wiktionary page.\

-   The annotation \@DefaultUrl points to the web address of the page. 
-   The class is set to extend Serenity\'s Page Object class.
-   Using the PageFactory implementation and \@FindBy annotations, it
    maps out the search textbox and the go button as \"searchTerms\" and
    \"lookupButton\". 
-   Declares public methods \"enter\_keywords(String keyword)\" and
    \"lookup\_terms\". First method uses the WebDriver \"type\" method
    to enter keyword data into \"searchTerms\", and the second uses the
    WebDriver \"click\" method to press the button. 
-   It uses the Serenity class WebElementFacade to create a definition
    list. 
-   It uses ch.lambdaj.Lambda.convert to convert the text to Strings.

\
Under src/test/java:\
\
**Requirements: Application.java**\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 public class Application {  
   @Feature  
   public class Search {  
     public class SearchByKeyword {}  
     public class SearchByMultipleKeywords {}  
   }  
 }  
```

\... Need a Search feature? Here one is!\
\
**Steps: See EndUserSteps.java**\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 import static ch.lambdaj.Lambda.join;  
 import static org.hamcrest.MatcherAssert.assertThat;  
 import static org.hamcrest.Matchers.containsString;  
 import static org.hamcrest.Matchers.hasItem;  
 public class EndUserSteps extends ScenarioSteps {  
   DictionaryPage dictionaryPage;  
   @Step  
   public void enters(String keyword) {  
     dictionaryPage.enter_keywords(keyword);  
   }  
   @Step  
   public void starts_search() {  
     dictionaryPage.lookup_terms();  
   }  
   @Step  
   public void should_see_definition(String definition) {  
     assertThat(dictionaryPage.getDefinitions(), hasItem(containsString(definition)));  
   }  
   @Step  
   public void is_the_home_page() {  
     dictionaryPage.open();  
   }  
   @Step  
   public void looks_for(String term) {  
     enters(term);  
     starts_search();  
   }  
 }  
```

\
Jon Smart is using:\
\

-   Lamda join to make magic. 
-   Hamcrest\'s *assertThat* to make things more readable. 
-   It uses the methods we declared with the DictionaryPage page object
    to interact with the web page itself. 
-   Note that all these methods are set as variables. These steps can be
    reused again and again to search for different keywords, such as
    \"apple\" or \"banana\". 

\
And last but not least, we have\...\
\
**Story: SearchByKeywordStoryTest.java**\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 @Story(Application.Search.SearchByKeyword.class)  
 @RunWith(ThucydidesRunner.class)  
 public class SearchByKeywordStoryTest {  
   @Managed(uniqueSession = true)  
   public WebDriver webdriver;  
   @ManagedPages(defaultUrl = "http://en.wiktionary.org/wiki/Wiktionary")  
   public Pages pages;  
   @Steps  
   public EndUserSteps endUser;  
   @Issue("#WIKI-1")  
   @Test  
   public void searching_by_keyword_apple_should_display_the_corresponding_article() {  
     endUser.is_the_home_page();  
           endUser.looks_for("apple");  
     endUser.should_see_definition("A common, round fruit produced by the tree Malus domestica, cultivated in temperate climates.");  
   }  
   @Test  
   public void searching_by_keyword_banana_should_display_the_corresponding_article() {  
     endUser.is_the_home_page();  
           endUser.looks_for("pear");  
           endUser.should_see_definition("An edible fruit produced by the pear tree, similar to an apple but elongated towards the stem.");  
   }  
   @Pending @Test  
   public void searching_by_ambiguious_keyword_should_display_the_disambiguation_page() {  
   }  
 }   
```

\
This puts everything together! In this Story it:\
\

-   Creates an Actor called \"endUser\".
-   The actor can use methods declared in EndUserSteps Jon Smart created
    such as \"looks\_for\" and \"should\_see\_definition\".

<div>

These actors are part of the abstract concept Jon Smart calls \"The
Screenplay Pattern\". The next blog entry, we will look into Jon\'s
Screenplay Tutorial
at <http://serenity-bdd.info/docs/articles/screenplay-tutorial.html>

</div>

\
\
\
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
-T.J. Maher

</div>

<div>

\
[Twitter](https://twitter.com/tjmaher1) \|
[LinkedIn](https://www.linkedin.com/in/tjmaher1) \|
[GitHub](https://github.com/tjmaher)\
\
*// Sr. QA Engineer, Software Engineer in Test, Software Tester since
1996.\
// Contributing Writer
for [TechBeacon.](http://techbeacon.com/contributors/thomas-maher)\
// \"Looking to move away from manual QA? Follow [Adventures in
Automation](http://www.tjmaher.com/) on
[Facebook](https://www.facebook.com/AdventuresInAutomation/)!\"*

</div>
