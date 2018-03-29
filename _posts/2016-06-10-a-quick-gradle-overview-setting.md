\-\-- layout: post title: \'A Quick Gradle Overview: Setting
Dependencies and Running Tests\' date: \'2016-06-10T01:55:00.000-04:00\'
author: T.J. Maher tags: - test framework - Gradle modified\_time:
\'2016-06-10T02:08:50.628-04:00\' thumbnail:
https://1.bp.blogspot.com/-or1BkF5UKtQ/V1o7iKKwJEI/AAAAAAAALJw/XQ1HYEUG9F47kZxGFsuQ8o8h66cAGcFsACLcB/s72-c/gradle.png
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-8332381311337698386
blogger\_orig\_url:
http://www.tjmaher.com/2016/06/a-quick-gradle-overview-setting.html
\-\-- Since January of this year, our little automation department at
work has been trying to re-align itself, getting more in line with what
the other software developers are doing \-- a fantastic (but scary)
learning opportunity for me.\
\
Back in March 2015, I was trying to relearn *for loops* and *foreach
loops* in Java. By September, though, I was helping build out the
automation framework for our Selenium WebDriver browser tests \-- See
[Automate Amazon](https://github.com/tjmaher/automate-amazon) for a
sample. And by January 2016, I thought I was really becoming an
experienced developer, independently writing a framework to handle [Rest
APIs](https://github.com/tjmaher/RESTful_Testing_Using_Stripe). All the
extra work I was putting into learning to code was really paying off.\
\
Now, I feel like I don\'t know *anything*!\
\
We are switching from being an \"Automation Department\" to being a
\"Software Test Engineering\" department, from just running browser
tests to testing APIs and performance testing. I find myself
experimenting with many languages and tools that are brand new to me\...
and one of them is the build management tool,
[Gradle](http://gradle.org/).\
\

Maven and Gradle: Setting Dependencies
--------------------------------------

\
As far as I knew, a build management tool was something you set up once
at the start of the project to handle the dependencies, installing the
tools you needed to create the framework, and then forgot about them.\
\
[]{#more}\
\
I was first introduced to [Apache Maven](https://maven.apache.org/)
during Alan Richardson\'s online course, [Selenium 2 WebDriver with
Java](http://compendiumdev.co.uk/page.php?title=seleniumwebdrivercourse).
Take a look at the [first practice testing
framework](https://github.com/tjmaher/WebDriver_TheInternet_Advanced) I
designed back in July 2015. The **pom.xml** file has nothing but
dependencies for the tools I am using.\
\
**[Pom.xml]{.underline}**\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 <?xml version="1.0" encoding="UTF-8"?>  
 <project xmlns="http://maven.apache.org/POM/4.0.0"  
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  
      xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">  
   <modelVersion>4.0.0</modelVersion>  
   <groupId>WebDriver_TheInternet_Advanced</groupId>  
   <artifactId>WebDriver_TheInternet_Advanced</artifactId>  
   <version>1.0-SNAPSHOT</version>  
   <dependencies>  
     <dependency>  
       <groupId>org.testng</groupId>  
       <artifactId>testng</artifactId>  
       <version>6.1.1</version>  
       <scope>test</scope>  
     </dependency>  
     <dependency>  
       <groupId>org.seleniumhq.selenium</groupId>  
       <artifactId>selenium-java</artifactId>  
       <version>2.46.0</version>  
     </dependency>  
   </dependencies>  
 </project>  
```

\
If you take a look at the poorly named project I
created, [InitialWebDriverSetup\_GradleJunitChromeDriver](https://github.com/tjmaher/InitialWebDriverSetup_GradleJunitChromeDriver),
you can see that I am only using Gradle in this same way. It is just a
quick way for the project to download other libraries I am using in the
project. Take a look at the **build.gradle** file:\
\
**[Build.gradle]{.underline}**\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 group 'com.tmaher'   
  version '1.0-SNAPSHOT'   
  apply plugin: 'java'   
  repositories {   
   mavenCentral()   
  }   
  dependencies {   
   testCompile group: 'junit', name: 'junit', version: '4.11'   
   compile group: 'org.seleniumhq.selenium', name: 'selenium-java', version: '2.53.0'   
   compile group: 'org.hamcrest', name: 'java-hamcrest', version: '2.0.0.0'   
  }   
```

\
\

Gradle Tasks
------------

\
There is a lot more to Gradle than handling dependencies. When creating
a Gradle project with [IntelliJ](https://www.jetbrains.com/idea/), as I
did in the blog post [WebDriver development environment setup with
IntelliJ, Gradle, Hamcrest, and
ChromeDriver](http://www.tjmaher.com/2016/05/webdriver-development-environment-setup.html),
you can see that there are many Gradle tasks that have been set up for
us:\

::: {.separator style="clear: both; text-align: center;"}
[![](https://1.bp.blogspot.com/-or1BkF5UKtQ/V1o7iKKwJEI/AAAAAAAALJw/XQ1HYEUG9F47kZxGFsuQ8o8h66cAGcFsACLcB/s400/gradle.png){width="180"
height="400"}](https://1.bp.blogspot.com/-or1BkF5UKtQ/V1o7iKKwJEI/AAAAAAAALJw/XQ1HYEUG9F47kZxGFsuQ8o8h66cAGcFsACLcB/s1600/gradle.png)
:::

\
These tasks were automatically created as soon as the Java plugin for
Gradle was added to the build.java file. See [Chapter 45: The Java
Plugin](https://docs.gradle.org/current/userguide/java_plugin.html) of
the free **Gradle Users Guide**.\
\
**Gradle: Build Tasks: **\

-   assemble: Assembles all the archives in the project 
-   build: Performs a full build of the project. 
-   buildDependents: Performs a full build of the project and all
    projects which depend on it. 
-   clean: Deletes the project build directory. 

**Gradle: Verification tasks:**\

-   check: Performs all verification tasks in the project. 
-   test: Runs the unit tests using JUnit or TestNG.

We have in the project the following tests saved in a TestClass under
**src/test/java** *(not src.main/java).*\
\

``` {.brush: .java}
public class TestClass {

    private WebDriver driver;

    @Test
    public void testFirefoxDriver() {

        driver = new FirefoxDriver();
        . . . 
    }

    @Test
    public void testChromeDriver() {
        . . . 
    }

    @Test
    public void testIE11Driver() {
        . . . 
    }

    @After
    public void closeBrowsers() throws Exception {
        driver.quit();
    }
}
```

\

Running Tests through IntelliJ
------------------------------

\
When I double-click on *test*:\

-   **Build.Gradle** is reviewed: Since there isn\'t anything explicitly
    saying *test { useTestNG() }* it will use JUnit (3.8.x or 4.x). *See
    Gradle [Test
    configurations](https://docs.gradle.org/current/dsl/org.gradle.api.tasks.testing.Test.html)*.
-   It searched for all the unit tests in **src/test/java.** Since it
    didn\'t see anything in the build.gradle file excluding any tests,
    it ran all the tests we marked \@Test. 
-   After the project is compiled, one by one, the browser tests are
    run. 
-   A report is printed out.

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 Testing started at 1:05 AM ...  
 1:05:14 AM: Executing external task 'test'...  
 :compileJava UP-TO-DATE  
 :processResources UP-TO-DATE  
 :classes UP-TO-DATE  
 :compileTestJava UP-TO-DATE  
 :processTestResources UP-TO-DATE  
 :testClasses UP-TO-DATE  
 :test  
 BUILD SUCCESSFUL  
 Total time: 29.391 secs  
 1:05:43 AM: External task execution finished 'test'.  
```

\

Running Tests through the Command Line
--------------------------------------

\
These tests can also be run in the Command Line Interface (CLI), within
the Mac Terminal or the Windows Command Prompt. Go into the project
folder and run the following from the command line:\
\
**[Mac Terminal]{.underline}**:\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 ./gradlew test  
```

\
**[Windows Command Prompt:]{.underline}**\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 gradlew.bat test  
```

\
This does the same exact thing as above, except it uses the **Gradle
Wrapper** to execute the task called *test*. On the Windows environment,
the wrapper is a batch file (\*.bat) that runs Gradle.\
\

What is the Gradle Wrapper?
---------------------------

\
From [Chapter 5: The Gradle
Wrapper](https://docs.gradle.org/current/userguide/gradle_wrapper.html)
of the **Gradle Users Guide**, Version 2.13\
\
*\"Most tools require installation on your computer before you can use
them. If the installation is easy, you may think that's fine. But it can
be an unnecessary burden on the users of the build. Equally importantly,
will the user install the right version of the tool for the build? What
if they're building an old version of the software?*\
*\
\"The Gradle Wrapper (henceforth referred to as the \'Wrapper\') solves
both these problems and is the preferred way of starting a Gradle build
\[\...\]*\
*\
\"If a Gradle project has set up the Wrapper (and we recommend all
projects do so), you can execute the build using one of the following
commands from the root of the project:*\
\

-   *./gradlew \<task\> (on Unix-like platforms such as Linux and Mac
    OS X)*
-   *gradlew \<task\> (on Windows using the gradlew.bat batch file)*

\
*\"Each Wrapper is tied to a specific version of Gradle, so when you
first run one of the commands above for a given Gradle version, it will
download the corresponding Gradle distribution and use it to execute the
build\".*\
\

What Was Gradle, Again? 
------------------------

It was created mainly by **Hans Doctker** (
[LinkedIn](https://www.linkedin.com/in/hansdockter),
Twitter: [\@hans\_d](https://twitter.com/hans_d) ) the CEO of the Gradle
(formerly Gradleware) company.\
\
From [Wikipedia\'s article on
Gradle](https://en.wikipedia.org/wiki/Gradle):\
\
*\"Gradle is an open source build automation system that builds upon the
concepts of Apache Ant and Apache Maven and introduces a Groovy-based
domain-specific language (DSL) instead of the XML form used by Apache
Maven of declaring the project configuration. Gradle uses a directed
acyclic graph (\'DAG\') to determine the order in which tasks can be
run.*\
*\
\"Gradle was designed for multi-project builds which can grow to be
quite large, and supports incremental builds by intelligently
determining which parts of the build tree are up-to-date, so that any
task dependent upon those parts will not need to be re-executed.*\
*\
\"The initial plugins are primarily focused around Java, Groovy and
Scala development and deployment, but more languages and project
workflows are on the roadmap\".*\
\
**[Gradle Links:]{.underline}**\

-   **Documentation:** Gradle Users Guide
    at <https://docs.gradle.org/current/userguide/userguide.html>
-   **GitHub** site, where you can view its source code,
    at <https://github.com/gradle/gradle>
-   **Free Class** on Udacity: [Gradle for Android and
    Java](https://www.udacity.com/course/gradle-for-android-and-java--ud867)
-   The next **Gradle Summit** <http://www.gradlesummit.com/> is June
    23-24, 2016 in Palo Alto, CA.
-   The **funniest page** in the Gradle Summit site is [How to Convince
    Your Boss](https://gradlesummit.com/convince-your-boss) to go to the
    summit. They even have a hard-sell form letter you can
    copy-and-paste.

\
**Breaking Open: Gradle***: Interview with the author of Gradle*\

\
*Video Description: \"Published on Oct 4, 2012: In our second episode of
Breaking Open, Hans Dockter peels back the curtains on Gradle, the open
source, general purpose, and platform agnostic build system he created
to address the changing landscape and new demands of modern enterprise
automation\".*\
\
**[Gradle Summit 2015 Keynote]{.underline}**: Hans Dockter\
*\"It Used To Be Fun To Make Software\" *\

\
\
\
\... With the next blog post, we\'ll explore the free class offered on
Udacity: [Gradle for Android and
Java](https://www.udacity.com/course/gradle-for-android-and-java--ud867).\
\
Until then, Happy Testing!\
\
-T.J. Maher\
Sr. QA Engineer,\
Fitbit-Boston\
\
*// QA Engineer since Aug. 1996\
// Automation developer for \[ 1 \] year and still counting!\
// Check out Adventures in Automation on
[Facebook](https://www.facebook.com/AdventuresInAutomation/)!*
