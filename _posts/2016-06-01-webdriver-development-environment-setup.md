\-\-- layout: post title: WebDriver development environment setup with
Eclipse, Gradle, Hamcrest, and ChromeDriver date:
\'2016-06-01T19:56:00.001-04:00\' author: T.J. Maher tags: - code
examples - JUnit - setup - WebDriver - Gradle - Eclipse - Hamcrest
modified\_time: \'2016-07-03T17:21:53.294-04:00\' thumbnail:
https://1.bp.blogspot.com/-4dwXe-Iuzzo/V09q280TUjI/AAAAAAAALFc/iw86sUIWvYAh4p16y\_4f-1Zl5CRpqK6XgCKgB/s72-c/0\_eclipse.png
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-6643772519121615243
blogger\_orig\_url:
http://www.tjmaher.com/2016/06/webdriver-development-environment-setup.html
\-\-- We started writing at work a new way of configuring an automated
test framework. The original idea I had was that I could just bang out a
simple automated test framework as practice, refactoring what I already
have written in the past. When I started researching the new toolset,
and my research notes were piling up, I then had the brilliant idea that
this topic would make a lovely blog post.\
\
I wrote about using IntelliJ. A reader asked me, *What about an Eclipse
version?*\
\
With this blog post, I will walk you through downloading **Eclipse IDE
for Java Developers**, installing **Buildship** (the official Gradle
plugin for Eclipse), setting up your Java environment, configuring
**Gradle**, installing **ChromeDriver**, and creating quick-and-dirty
WebDriver JUnit Tests, making assertions in the tests using
**Hamcrest**, and refactoring those tests when we come across duplicate
code.\
\
This is a different setup than programming projects I have done before.
We are using:\

-   **Eclipse ** with **Buildship** will be the Integrated Development
    Environment (IDE).
-   **Gradle** to handle our dependencies, instead of Maven
-   **JUnit 4.11** as a test framework instead of TestNG.
-   **Hamcrest** to handle the asserts, instead of the usual AssertTrue
    or AssertFalse found in JUnit or TestNG.

[]{style="text-align: center;"}\

<div>

[[\
]{style="text-align: center;"}]{style="text-align: center;"}

</div>

[]{style="text-align: center;"}\

::: {.separator style="clear: both; text-align: center;"}
[[![](https://1.bp.blogspot.com/-4dwXe-Iuzzo/V09q280TUjI/AAAAAAAALFc/iw86sUIWvYAh4p16y_4f-1Zl5CRpqK6XgCKgB/s320/0_eclipse.png){width="320"
height="74"}](https://1.bp.blogspot.com/-4dwXe-Iuzzo/V09q280TUjI/AAAAAAAALFc/iw86sUIWvYAh4p16y_4f-1Zl5CRpqK6XgCKgB/s1600/0_eclipse.png)]{style="text-align: center;"}
:::

[]{style="text-align: center;"}\

<div>

[[\
]{style="text-align: center;"}]{style="text-align: center;"}

</div>

[]{style="text-align: center;"}\

<div>

[[\
]{style="text-align: center;"}]{style="text-align: center;"}

</div>

[Please Note: You don\'t need an Integrated Development Environment
(IDE) to code, just as you don\'t need Microsoft Word or any other word
processing program in order to write a research paper. It is just easier
to those who are more used to working with a Graphical User
Interface.]{style="text-align: center;"}\
\
If you want to be seen as a programming rock-star, learn to code in
*vim* or *emacs* on a Unix command line. Me, I am more of a visual
person and need the crutch of an IDE while coding.\
\
[]{#more}

 
-

About Our Tools
---------------

### Eclipse IDE for Java Developers:

-   **Home**: <https://eclipse.org/>
-   **GitHub**: <https://github.com/eclipse>
-   **Tutorials**: <http://help.eclipse.org/mars/index.jsp>
-   **Latest version**: Mars

\
**How we are using it:**\

-   What we will be using to write, organize, and refactor our code.

### Buildship, a Gradle Plugin:

<div>

-   **Home**: <http://projects.eclipse.org/projects/tools.buildship>
-   **GitHub**: https://github.com/eclipse/buildship
-   **Tutorials**: <http://www.vogella.com/tutorials/EclipseGradle/article.html>

<div>

*\"Buildship is a collection of Eclipse plug-ins that provide support
for building software using Gradle. Buildship aims to provide a deep
integration of Gradle into Eclipse. Buildship also aims to make the
Eclipse IDE more powerful by allowing the user to do more from within
the IDE. Buildship 1.0 is targeted towards Gradle users. Later versions
will target Gradle build masters\".*

</div>

</div>

### JUnit 4:

-   **Home**: <http://junit.org/junit4/>
-   **GitHub**: <https://github.com/junit-team/junit4>
-   **Tutorials:**
    <https://github.com/junit-team/junit4/wiki/Getting-started>
-   *Have Java 8? JUnit 5.0.0-ALPHA was released on February 1st, 2016
    <http://junit.org/junit5/>*

\
**How we are using it:**\
\

-   What we will be using to annotate our test methods, declaring if a
    certain method is a \@Test itself, if the method should be run
    \@Before or \@After each and every individual test is run.

\
**History:**\

-   JUnit is the once and future test framework. First written by Kent
    Beck and Erich Gamma back in 2000, it received an major update,
    JUnit4, in 2005.  Because the next version, JUnit5, still in it's
    Alpha release we haven't adopted it yet at work.

\
**Examples:**\

-   \@BeforeClass: Static methods run once before all the \@Tests in
    TestClass.java is run
-   \@Before: Good for setUp() methods. Runs before each and
    every \@Test.
-   \@Test: It\'s our \@Test Method.
-   \@After: Good for tearDown() methods. Runs after each and
    every \@Test.
-   \@AfterClass: Static methods run once after all the \@Tests in
    TestClass.java is run

\

### Hamcrest:

-   **Home**: <http://hamcrest.org/>
-   **GitHub**: <https://github.com/hamcrest/JavaHamcrest>
-   **Tutorial**:
    <https://code.google.com/archive/p/hamcrest/wikis/Tutorial.wiki>

\
\
**How we are using it:**\

-   We are evaluating the actual conditions of what is happening in the
    test against the conditions of the test. For example, we
    \"assertThat(actualString, is(equalTo(expectedString)))\" or
    \"assertThat(actualBooleanValue, is(true))" or \"assertThat(1,
    greaterThan(3))\".

\
\
**History:**\
\
*\"Hamcrest evolved out of the library JMock, being used to write
specialized constraints on what you expected to happen to a Mock object
when standing in for a real implementation. A more fluent assertion
syntax arose from these constraints which allowed you to chain together
main constraint calls under a single assertThat method. Later JMock\'s
author, Joe Walnes, refactored the constraint API out into its own
library that he called Hamcrest as people became interested in using it
outside of a testing framework for all kinds of different things. He
also started calling the constraints 'matchers\' though they can go by
both names or, in some circles, 'predicates.\' Other testing frameworks
and even JUnit, notorious for not requiring any dependencies and staying
conceptually small, have picked it up". - [What is
Hamcrest](https://www.captechconsulting.com/blogs/What-is-Hamcrest),
from CaptechConsulting Blogs *\
\
With most of our browser tests, we take a piece of text we find on a
page such as a page title, a heading, or a price, place it in a String,
and compare it with the String value we were expecting.\
\
**Examples: **\

-   assertThat(actualString, is(equalTo(expectedString)));
-   assertThat(actualString, is(not(equalTo(expectedString))));
-   assertThat(actualValue(), is(not(nullValue())));
-   assertThat(actualString, containsString(expectedString));
-   assertThat(1, greaterThan(3));
-   assertThat(actualBooleanValue, is(true));
-   assertThat(actualBooleanValue, is(false));

\

How To Setup Automation Environment
-----------------------------------

Step 1A: Download Eclipse IDE for Java Developers
-------------------------------------------------

-   Go to <https://eclipse.org/downloads/> and download Eclipse. It
    should direct you automatically to the Mac or a PC version.
-   Once the Zip file is downloaded, extract all to where you wish the
    program to be installed, such as in C:\\\\Program Files.
-   Go into the new Eclipse folder and double-click the icon to run the
    program.

Step 1B: Install Buildship
--------------------------

-   In Eclipse\'s top menu, go to Help -\> Marketplace, and search for
    the keyword \"Buildship\". Check to see if it is installed. If not,
    press the Install button.

::: {.separator style="clear: both; text-align: center;"}
[![](https://2.bp.blogspot.com/-0m9btpDlnzQ/V09q24wCkjI/AAAAAAAALGM/6S6L82HL9zUN9nwZJq--mpBp6a05QnEzgCKgB/s400/1_marketplace.png){width="253"
height="400"}](https://2.bp.blogspot.com/-0m9btpDlnzQ/V09q24wCkjI/AAAAAAAALGM/6S6L82HL9zUN9nwZJq--mpBp6a05QnEzgCKgB/s1600/1_marketplace.png)
:::

\

**Step 2:** Setup a New Java Gradle Project
-------------------------------------------

\
1) **Start up Eclipse**\
\
**2) Create a New Project**\

-   Go to File -\> New -\> Project
-   On the Select a Wizard screen, choose Gradle -\> Gradle Project.

::: {.separator style="clear: both; text-align: center;"}
\
:::

::: {.separator style="clear: both; text-align: center;"}
[![](https://2.bp.blogspot.com/-K_oD4oTSreY/V09q3H29tlI/AAAAAAAALGM/G8J7ECxHEQQ5o9UM2upW70FnGym0h-jbQCKgB/s400/3_New%2BGradle%2BProject.png){width="400"
height="381"}](https://2.bp.blogspot.com/-K_oD4oTSreY/V09q3H29tlI/AAAAAAAALGM/G8J7ECxHEQQ5o9UM2upW70FnGym0h-jbQCKgB/s1600/3_New%2BGradle%2BProject.png)
:::

::: {.separator style="clear: both; text-align: center;"}
\
:::

\
**3) On the New Gradle Project screen:**\
\
What would you like to call your project, and where would you like to
put it?\
\
I am always juggling multiple projects, switching from Java (both with
and without WebDriver) and Python.\
\
I created in my Home Directory (C:\\Users\\tmaher in Windows) a folder
called \"code\". In that folder are the subfolders \"java\" and
\"python\". And under each of those are subfolders called \"selenium\",
since I have been attempting to write testing frameworks with Selenium
WebDriver bindings in both Java and Python.\
\

::: {.separator style="clear: both; text-align: center;"}
[![](https://2.bp.blogspot.com/-MR_SFoJSwUU/V09q3KIIf_I/AAAAAAAALGM/OZIxGo56cNMFmI7f6LQ83DELf1ZIxNDFACKgB/s400/34_New%2BGradle%2BProject.png){width="400"
height="381"}](https://2.bp.blogspot.com/-MR_SFoJSwUU/V09q3KIIf_I/AAAAAAAALGM/OZIxGo56cNMFmI7f6LQ83DELf1ZIxNDFACKgB/s1600/34_New%2BGradle%2BProject.png)
:::

\
\
So, for this project:\

-   Project name: multiplebrowsers
-   Project location:
    C:\\Users\\tmaher\\code\\java\\selenium\\multiplebrowsers
-   Select FINISH

\
**7) View Automatically Created Folders**\

::: {.separator style="clear: both; text-align: center;"}
\
:::

You will see that much has been created for you in the Maven style:\

-   src/main/java folder: The home for our main codebase.
-   src/test/java folder: Historically, the home for our unit tests that
    check our main codebase.

::: {.separator style="clear: both; text-align: center;"}
[![](https://2.bp.blogspot.com/-4g5vLYaj6JA/V09q3aor1eI/AAAAAAAALGM/fid4x4N8gHwVKhwJ1CShi5zGg04er6chQCKgB/s320/5_Created%2Bfolders.png){width="205"
height="320"}](https://2.bp.blogspot.com/-4g5vLYaj6JA/V09q3aor1eI/AAAAAAAALGM/fid4x4N8gHwVKhwJ1CShi5zGg04er6chQCKgB/s1600/5_Created%2Bfolders.png)
:::

Step 3: Review the Build.Gradle file
------------------------------------

What is Gradle?\
\
\"Gradle is a general-purpose build tool. It can build pretty much
anything you care to implement in your build script. Out-of-the-box,
however, it doesn\'t build anything unless you add code to your build
script to do so.\
\
\"Most Java projects are pretty similar as far as the basics go: you
need to compile your Java source files, run some unit tests, and create
a JAR file containing your classes. It would be nice if you didn\'t have
to code all this up for every project. Luckily, you don\'t have to.
Gradle solves this problem through the use of plugins. A plugin is an
extension to Gradle which configures your project in some way, typically
by adding some pre-configured tasks which together do something useful.
Gradle ships with a number of plugins, and you can easily write your own
and share them with others. One such plugin is the Java plugin. This
plugin adds some tasks to your project which will compile and unit test
your Java source code, and bundle it into a JAR file\". - The Gradle.org
UserGuide, [Java Projects Tutorial, Chapter
44](https://docs.gradle.org/current/userguide/tutorial_java_projects.html).\
\
Let\'s take a look at what was added automatically to the
**build.gradle** file:\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
/*
 * This build file was auto generated by running the Gradle 'init' task
 * by 'tmaher' at '6/1/16 6:44 PM' with Gradle 2.9
 *
 * This generated file contains a sample Java project to get you started.
 * For more details take a look at the Java Quickstart chapter in the Gradle
 * user guide available at https://docs.gradle.org/2.9/userguide/tutorial_java_projects.html
 */

// Apply the java plugin to add support for Java
apply plugin: 'java'

// In this section you declare where to find the dependencies of your project
repositories {
    // Use 'jcenter' for resolving your dependencies.
    // You can declare any Maven/Ivy/file repository here.
    jcenter()
}

// In this section you declare the dependencies for your production and test code
dependencies {
    // The production code uses the SLF4J logging API at compile time
    compile 'org.slf4j:slf4j-api:1.7.13'

    // Declare the dependency for your favourite test framework you want to use in your tests.
    // TestNG is also supported by the Gradle Test task. Just change the
    // testCompile dependency to testCompile 'org.testng:testng:6.8.1' and add
    // 'test.useTestNG()' to your build script.
    testCompile 'junit:junit:4.12'
}
```

\
\...Let\'s swap out the text \"jcentral()\" to \"mavenCentral()\". Er, I
am more used to Maven Central.\
\
According to **Gradle\'s [Java Projects
Tutorial](https://docs.gradle.org/current/userguide/tutorial_java_projects.html):**\
\
**Apply Plugin: \'Java\':**\
\
\"This is all you need to define a Java project. This will apply the
Java plugin to your project, which adds a number of tasks to your
project.\
\
\"Gradle expects to find your production source code under
*src/main/java* and your test source code under *src/test/java*. In
addition, any files under *src/main/resources* will be included in the
JAR file as resources, and any files under *src/test/resources* will be
included in the classpath used to run the tests. All output files are
created under the build directory, with the JAR file ending up in the
build/libs directory\".\
**\
Repositories: Maven Central:**\
\
\"Usually, a Java project will have some dependencies on external JAR
files. To reference these JAR files in the project, you need to tell
Gradle where to find them. In Gradle, artifacts such as JAR files, are
located in a repository. A repository can be used for fetching the
dependencies of a project, or for publishing the artifacts of a project,
or both. For this example, we will use the public Maven repository\".\
\
The **Maven Central Repository** is at <http://search.maven.org/>. You
can also search a much more user friendly
site, <http://mvnrepository.com/>.\
\

Step 4: Add Dependencies to Gradle
----------------------------------

We are going to add to the dependencies: The Selenium-Java bindings for
WebDriver, and Hamcrest\
\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 dependencies {  
   testCompile group: 'junit', name: 'junit', version: '4.12'  
   compile group: 'org.seleniumhq.selenium', name: 'selenium-java', version: '2.53.0'  
   compile group: 'org.hamcrest', name: 'java-hamcrest', version: '2.0.0.0'  
 }  
```

\
How did we know what to put in the dependencies? Take a look at
MVNRepository. It shows what to use as dependencies in Maven, Gradle, or
other systems.\
\

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://4.bp.blogspot.com/-Xfy3zQwu8X8/V0x9omHNK_I/AAAAAAAALEM/Mt5cFJEtiacHmclz7Eg6vpiWEK6mhJmhACKgB/s400/6_mvnrepo.png){width="400" height="255"}](https://4.bp.blogspot.com/-Xfy3zQwu8X8/V0x9omHNK_I/AAAAAAAALEM/Mt5cFJEtiacHmclz7Eg6vpiWEK6mhJmhACKgB/s1600/6_mvnrepo.png)
                                                                                                                     [MVNRepository.com](http://mvnrepository.com/)
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

\

-   Go to <http://mvnrepository.com/>
-   Search for \"selenium-java\".
-   You can see
    at <http://mvnrepository.com/artifact/org.seleniumhq.selenium/selenium-java>
    that the latest version is **2.53.0**. Select that links. 
-   When you are
    at <http://mvnrepository.com/artifact/org.seleniumhq.selenium/selenium-java/2.53.0> select
    the \"Gradle\" tab. 

***Want more training in Gradle?* Go
to** <https://gradle.org/udacity-gradle-for-android-and-java-training/> \...
Although the course is for Java AND Android development, the first part
is a good introduction to the tool.\
\

Step 5: Using Firefox Driver
----------------------------

Firefox is built into WebDriver. No need to download anything else. No
need to set up System Properties to tell us where the Windows executable
(\*.exe) file is located. All you need to do is write the test.\

-   In the Project pane of Eclipse, go to src/test/java.
-   Highlight the \"java\" folder and right click on it.
-   Go to New -\> Java class 
-   Create a new class, call it TestClass, and select OK.

<div>

Copy and paste the following class. 

</div>

<div>

\

</div>

<div>

**TestClass.java**

</div>

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 import org.junit.Test;  
 import org.openqa.selenium.WebDriver;  
 import org.openqa.selenium.firefox.FirefoxDriver;  
   
 import static org.hamcrest.CoreMatchers.is;  
 import static org.hamcrest.MatcherAssert.assertThat;  
 import static org.hamcrest.core.IsEqual.equalTo;  
   
 public class TestClass {  
   @Test  
   public void testFirefoxDriver() {  
   
     WebDriver driver = new FirefoxDriver();  
     driver.get("http://the-internet.herokuapp.com/login");  
     assertThat(driver.getTitle(), is(equalTo("The Internet")));  
     driver.quit();  
   }   
 }  
```

\
There are two ways (or more) ways to execute this test:\

-   Run all tests in TestClass.java by selecting outside the
    testFirefoxDriver test block, right click, and select \"Run As\" -\>
    \"JUnit Test\". 
-   Going to the panel, \"Outline\", selecting the individual test,
    right clicking on it, and selecting \"Run As\" -\> \"JUnit Test\". 

<div>

This test when run will then:

</div>

<div>

-   Open a new Firefox browser.
-   Go to Dave Haefner\'s test site, The-Internet, in his test login
    page at <http://the-internet.herokuapp.com/login>.
-   Using the Hamcrest matching library, it will a) Get the Title
    displayed in the Firefox WebDriver b) Check that it is equal to
    \"The Internet\". If it is okay, it will pass, showing Green. If it
    fails, it will give an error message.
-   The browser will then quit. 

</div>

  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://3.bp.blogspot.com/-K6HZkrMGWvw/V0913kWWYMI/AAAAAAAALHk/srPQgMxJLfEAn0qmztN_WPXslxvtUqtzgCLcB/s400/multiple.png){width="400" height="193"}](https://3.bp.blogspot.com/-K6HZkrMGWvw/V0913kWWYMI/AAAAAAAALHk/srPQgMxJLfEAn0qmztN_WPXslxvtUqtzgCLcB/s1600/multiple.png)
                                                                                                   *What the Outline Panel will look like after all browser tests are constructed.*
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

\

Step 6: Test Using Chromedriver
-------------------------------

If we want to test how a page looks in Chrome, we are going to have to
download and install
Chromedriver. <https://sites.google.com/a/chromium.org/chromedriver/>.\
\
But if you install Chromedriver, where would you like to put it?\
\
Personally, I like placing it in my Users directory, under my name. I
use it across all WebDriver / Java projects I do, so I have it in:\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 /Users/tmaher/code/java/selenium/drivers/chromedriver.exe  
```

\
Following Google\'s Chromedriver [Getting
Started](https://sites.google.com/a/chromium.org/chromedriver/getting-started)
section:\

-   [Download](https://sites.google.com/a/chromium.org/chromedriver/downloads)
    Chromedriver.
-   Open the ZIP file, extracting wherever you want to install it. 
-   Install it wherever you want, such as
    in [/Users/{YOUR\_NAME}/code/java/selenium/drivers/]{style="background-color: #f0f0f0; font-family: "arial"; font-size: 12px; line-height: 20px;"}

Now, we can write the ChromeDriver test!\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
   @Test  
   public void testChromeDriver() {  
     System.setProperty("webdriver.chrome.driver", "/Users/tmaher/code/java/selenium/drivers/chromedriver.exe");  
     WebDriver driver = new ChromeDriver();  
     driver.get("http://the-internet.herokuapp.com/login");  
     assertThat(driver.getTitle(), is(equalTo("The Internet")));  
     driver.quit();  
   }  
```

\
\... Of course, make sure in that second parameter, replace the
\"tmaher\" with wherever you installed ChromeDriver.\
\
Hrm\... I am not liking this\... there is a lot of code that seems to be
duplicated. This violates the biggest principle of software development:
**DRY** (Don\'t Repeat Yourself).\
\
\... Let\'s remember to refactor after.\
\
If you run TestClass.java, you first should see Firefox, then Chrome run
the test.\
\

Step 7: Test Using Microsoft Internet Explorer
----------------------------------------------

With Internet Explorer, the test will look pretty much like the others:\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
   @Test  
   public void testIE11Driver() {  
   
     WebDriver driver = new InternetExplorerDriver();  
     driver.get("http://the-internet.herokuapp.com/login");  
     assertThat(driver.getTitle(), is(equalTo("The Internet")));  
     driver.quit();  
   }  
```

\
\... And there\'s too much code duplication. Although we have written
unit tests, and they all pass, proving that our environment was set up
correctly, let\'s refactor the code, making it a bit more clean.\
\

Bonus Step: Refactoring the Unit Tests
--------------------------------------

1\. Make sure everything passes: Run all Unit Tests\
\
Let\'s run TestClass.java again, making sure we have a good baseline.\
\

-   In the top Eclipse menu, select **Run** -\> **Run TestClass**.
-   After the browser unit tests pass, verify that they are all Green.

  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://1.bp.blogspot.com/-8Up0LQIs8H4/V09zmshHidI/AAAAAAAALHQ/O-olRkA_sI4ndgh2HuaamhFXFjj8sr47QCLcB/s400/junit.png){width="400" height="206"}](https://1.bp.blogspot.com/-8Up0LQIs8H4/V09zmshHidI/AAAAAAAALHQ/O-olRkA_sI4ndgh2HuaamhFXFjj8sr47QCLcB/s1600/junit.png)
                                                                                                                             *Yes! They All Pass!*
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

\
\
2. Create an \@After method in JUnit, to be run after every single
test.\
\
Let\'s pull the *driver.quit()* out of each test method and in a
JUnit \@After tag. To do that, before the test methods, we need to
instantiate a new WebDriver class. Let\'s call it \"*driver*\".\
\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 private WebDriver driver;  
 . . .  
 . . .  
  @After  
   public void tearDown() throws Exception {  
     driver.quit();  
   }  
```

\
Here, again, are all the JUnit annotations we would use in a TestClass:\

-   \@BeforeClass: Would run once before all the \@Tests in
    TestClass.java is run
-   \@Before: Good for setUp() methods. Runs before each and
    every \@Test.
-   \@Test: It\'s our \@Test Method.
-   \@After: Good for tearDown() methods. Runs after each and
    every \@Test.
-   \@AfterClass: Would run once after all the \@Tests in TestClass.java
    is run

\
**TestClass.java**:\

``` {.brush: .java}
import org.junit.After;
import org.junit.AfterClass;
import org.junit.Test;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.firefox.FirefoxDriver;
import org.openqa.selenium.ie.InternetExplorerDriver;

import static org.hamcrest.CoreMatchers.is;
import static org.hamcrest.MatcherAssert.assertThat;
import static org.hamcrest.core.IsEqual.equalTo;

/**
 * Created by tmaher on 5/30/2016.
 */
public class TestClass {

    private WebDriver driver;

    @Test
    public void testFirefoxDriver() {

        driver = new FirefoxDriver();
        driver.get("http://the-internet.herokuapp.com/login");
        assertThat(driver.getTitle(), is(equalTo("The Internet")));
    }

    @Test
    public void testChromeDriver() {
        System.setProperty("webdriver.chrome.driver", "/Users/tmaher/code/java/selenium/drivers/chromedriver.exe");
        driver = new ChromeDriver();
        driver.get("http://the-internet.herokuapp.com/login");
        assertThat(driver.getTitle(), is(equalTo("The Internet")));
    }

    @Test
    public void testIE11Driver() {

        driver = new InternetExplorerDriver();
        driver.get("http://the-internet.herokuapp.com/login");
        assertThat(driver.getTitle(), is(equalTo("The Internet")));
    }

    @After
    public void closeBrowsers() throws Exception {
        driver.quit();
    }
}
```

Right now, we have just the basic installation. We still have a long way
to go when it comes to setting up a full-blown automation test
framework.\
\

-   We aren\'t yet using RemoteDriver.
-   We need to set a browser\'s Capabilities.
-   We aren\'t using PageObjects or any utility or helper methods. 

\
\... But at least we have a pretty detailed walkthrough on
installation.\
\
We\'ll use this in the coming weeks, when we convert  June 2015\'s
 project <https://github.com/tjmaher/WebDriver_TheInternet_Advanced> into
this new style.\
\
In the meantime\... Feel free to look at the source code
at <https://github.com/tjmaher/InitialWebDriverSetup_GradleJunitChromeDriver>\
\
Happy Testing!\
\
-T.J. Maher\
Sr. QA Engineer,\
Fitbit-Boston\
\
*// QA Engineer since Aug. 1996\
// Automation developer for \[ 1 \] year and still counting!\
// Check us out on
[Facebook](https://www.facebook.com/AdventuresInAutomation/)!*
