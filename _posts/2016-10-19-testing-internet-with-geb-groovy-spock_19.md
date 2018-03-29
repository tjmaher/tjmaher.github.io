\-\-- layout: post title: \'Testing The-Internet with Geb + Groovy +
Spock: Installing Yeoman and the Geb Generator\' date:
\'2016-10-19T23:24:00.003-04:00\' author: T.J. Maher tags: - Geb -
Yeoman - Gradle - Groovy modified\_time:
\'2016-11-18T23:03:09.125-05:00\' thumbnail:
https://3.bp.blogspot.com/-co6lCNtjCgw/WAXCw0RFPtI/AAAAAAAALgg/RNQp6BI67-Qbne\_tN9cQ8XPSwPInoMmPQCLcB/s72-c/1%2Byo.png
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-6333541913977102695
blogger\_orig\_url:
http://www.tjmaher.com/2016/10/testing-internet-with-geb-groovy-spock\_19.html
\-\-- *Part 2 of 5. Need to [read from the
beginning](http://www.tjmaher.com/2016/10/testing-internet-with-geb-groovy-spock.html)? *\
*\
*To get more familiar with the **Geb Framework + Groovy Language + Spock
Framework**, I was planning on figuring out how to automate Dave
Haeffner\'s Login page on his test site, The-Internet.\
\
[A few days
ago](http://www.tjmaher.com/2016/10/testing-internet-with-geb-groovy-spock.html),
I talked a bit about scaffolding a project, laying out the basic
groundwork, and the history of Yeoman.io. With this blog post, we will
walk a user through downloading and installing Yeoman through the Node
Package Manager.\
\
The installation will be done on the command line: the Mac\'s Terminal
or the Windows Command Prompt.\
\

-   *Unfamiliar with the Command Line Interface? Read [this blog
    post](http://www.tjmaher.com/search/label/CommandLine)! *
-   *Need a [Quick Gradle
    Overview](http://www.tjmaher.com/2016/06/a-quick-gradle-overview-setting.html)
    to do build configuration and run tests?*

\
We will be using a **Geb Generator** created by Chris Hluchan (
[LinkedIn](https://www.linkedin.com/in/chris-hluchan-3a473413) ), a
Software Engineer at Google, formerly at Oracle.\
\
You can take a look at the generator's source code on GitHub at
<https://github.com/chluchan/generator-geb#readme>\
\
We will be borrowing heavily from \"[Let\'s Scaffold a Web
App](http://yeoman.io/codelab/index.html)\" written by Mehdy Dara (
Github: [zckers](https://github.com/zckrs) ).\
\
Want to see what the boilerplate source code the Geb generator produces?
I have uploaded it to my GitHub site
at <https://github.com/tjmaher/geb_project_generated_by_yo> .\
\
The next few blog posts, we will be comparing that to the official
[Geb](http://www.gebish.org/manual/current/) +
[Groovy](http://www.groovy-lang.org/documentation.html) + [Spock
Framework](http://spockframework.org/spock/docs/1.1-rc-2/index.html) documentation
to figure out how it works.\
\
First, we need to figure out how to install everything.\
\
[]{#more}\
\

Install JDK, Node.js, Update NPM, Git
-------------------------------------

### 

### 1.  Install the Java Development Kit

-   Open up Terminal on the Mac or the Windows Command Prompt and check
    what version of Java is installed:
-   *java -version*

::: {style="padding: 0px;"}
... If there isn't a version number listed, or it is earlier than Java
8, install the latest version of the Java Development Kit
from <http://www.oracle.com/technetwork/java/javase/downloads/>. 
:::

###  {#section-1 style="padding: 0px;"}

### 2. Install Node.js {#install-node.js style="padding: 0px;"}

-   Open up Terminal on the Mac or the Windows Command Prompt  and check
    what version of Java is installed:
-   \* node ---version*

\

::: {style="padding: 0px;"}
... If there isn't a version number listed, install the latest version
of Node.js from <https://nodejs.org/>
:::

\

### 3. Install the latest version of the Node Package Manager

\

-   *npm install \--global npm\@latest*

\

### 4. Install Git {#install-git style="padding: 0px;"}

-   Open up Terminal on the Mac or the Windows Command Prompt and check
    what version of Java is installed:
-   \* git ---version*

\

::: {style="padding: 0px;"}
... If there isn't a version number listed, install the latest version
of Git from <https://git-scm.com/downloads>
:::

::: {style="padding: 0px;"}
\
:::

Install Yeoman and the Geb Generator {#install-yeoman-and-the-geb-generator style="padding: 0px;"}
------------------------------------

###  {#section-2 style="padding: 0px;"}

### 5. Install Yeoman {#install-yeoman style="padding: 0px;"}

::: {style="padding: 0px;"}
:::

-   **Installation:** *npm install \--global yo*
-   Check to see if everything is okay: *yo \--version*

\

### 6. Install the Geb Generator {#install-the-geb-generator style="padding: 0px;"}

::: {style="padding: 0px;"}
:::

<div>

-   View the instructions
    at <https://github.com/chluchan/generator-geb#readme>
-   *npm install -g generator-geb*

</div>

\

Configure the Geb Generator {#configure-the-geb-generator style="padding: 0px;"}
---------------------------

###  {#section-3 style="padding: 0px;"}

### 7. Run the Geb Generator {#run-the-geb-generator style="padding: 0px;"}

::: {style="padding: 0px;"}
:::

-   Go to the directory where you want to install the project and
    type\...
-   *yo geb*

\

::: {.separator style="clear: both; text-align: center;"}
[![](https://3.bp.blogspot.com/-co6lCNtjCgw/WAXCw0RFPtI/AAAAAAAALgg/RNQp6BI67-Qbne_tN9cQ8XPSwPInoMmPQCLcB/s400/1%2Byo.png){width="400"
height="156"}](https://3.bp.blogspot.com/-co6lCNtjCgw/WAXCw0RFPtI/AAAAAAAALgg/RNQp6BI67-Qbne_tN9cQ8XPSwPInoMmPQCLcB/s1600/1%2Byo.png)
:::

::: {style="padding: 0px;"}
\
:::

Let\'s call this:\
\

-   **Name of project:** geb\_project\_generated\_by\_yo
-   Base Package: com.tjmaher

\

::: {.separator style="clear: both; text-align: center;"}
[![](https://1.bp.blogspot.com/-nl2HIFO0HO0/WAXDvC69y9I/AAAAAAAALgk/sguBB97tomwSDWV8I7QD5prrE4iYFhLmwCLcB/s400/2%2Byo.png){width="400"
height="202"}](https://1.bp.blogspot.com/-nl2HIFO0HO0/WAXDvC69y9I/AAAAAAAALgk/sguBB97tomwSDWV8I7QD5prrE4iYFhLmwCLcB/s1600/2%2Byo.png)
:::

\

### 

### 8. Run the out-of-the-box test

\

-   **Mac:** *./gradlew chromeTest -Dprofile=production*
-   **PC, runs on a batch file:*** gradlew chromeTest
    -Dprofile=production *

\
\

The Test Output: What does it Mean?
-----------------------------------

A build configuration file was created, **build.gradle**. This file can
be seen
[here](https://github.com/tjmaher/geb_project_generated_by_yo/blob/master/build.gradle).
It sets up:\
\

-   All the third party dependencies, what versions are needed
-   Sets up the browsers: Firefox, Chrome, and PhantomJS
-   Downloads all dependencies from mavenCentral
-   The Selenium version to be 2.46.0.
-   The built in selenium-chrome-driver and selenium-firefox-driver
-   HTML reporting to be stored in the \"/tests\" subfolder
-   Chromedriver depending on if the OS is Mac or Windows
-   Results in the Build Directory, in the \"test-results\" folder. 
-   Tests: chromeTest, phantomJsTest, or test to run all of them.

<div>

\... It also allows us to set up the base url. 

</div>

\
**\
The command to run the test:**\
\

-   C:\\Users\\tmaher\\Documents\\code\\github\\geb\_project\_generated\_by\_yo\>gradlew
    chromeTest -Dprofile=production

\
\
Dependencies listed in the build.gradle file are downloaded:\
\

-   Downloading
    https://services.gradle.org/distributions/gradle-2.7-bin.zip
-   \<snip\> 
-   Unzipping
    C:\\Users\\tmaher\\.gradle\\wrapper\\dists\\gradle-2.7-bin\\4s0fcuuppw3tjb1sxpzh16mne\\gradle-2.7-bin.zip
    to
    C:\\Users\\tmaher\\.gradle\\wrapper\\dists\\gradle-2.7-bin\\4s0fcuuppw3tjb1sxpzh16mne

<div>

**Compilation tasks are run:**

</div>

-   :compileJava UP-TO-DATE
-   :compileGroovy UP-TO-DATE
-   :processResources UP-TO-DATE
-   :classes UP-TO-DATE
-   :compileTestJava UP-TO-DATE
-   :compileTestGroovy

<div>

**More dependencies are downloaded:**

</div>

-   Download
    https://repo1.maven.org/maven2/org/gebish/geb-spock/0.12.2/geb-spock-0.12.2.pom
-   Download
    https://repo1.maven.org/maven2/org/spockframework/spock-core/1.0-groovy-2.4/spock-core-1.0-groovy-2.4.pom
-   Download
    https://repo1.maven.org/maven2/org/codehaus/groovy/groovy-all/2.4.1/groovy-all-2.4.1.pom
-   Download
    https://repo1.maven.org/maven2/org/gebish/geb-junit4/0.12.2/geb-junit4-0.12.2.pom
-   Download
    https://repo1.maven.org/maven2/com/codeborne/phantomjsdriver/1.2.1/phantomjsdriver-1.2.1.pom
-   Download
    https://repo1.maven.org/maven2/org/gebish/geb-core/0.12.2/geb-core-0.12.2.pom
-   Download
    https://repo1.maven.org/maven2/org/gebish/geb-waiting/0.12.2/geb-waiting-0.12.2.pom
-   Download
    https://repo1.maven.org/maven2/org/gebish/geb-ast/0.12.2/geb-ast-0.12.2.pom
-   Download
    https://repo1.maven.org/maven2/org/gebish/geb-exceptions/0.12.2/geb-exceptions-0.12.2.pom
-   Download
    https://repo1.maven.org/maven2/org/gebish/geb-implicit-assertions/0.12.2/geb-implicit-assertions-0.12.2.pom
-   Download
    https://repo1.maven.org/maven2/org/gebish/geb-spock/0.12.2/geb-spock-0.12.2.jar
-   Download
    https://repo1.maven.org/maven2/org/spockframework/spock-core/1.0-groovy-2.4/spock-core-1.0-groovy-2.4.jar
-   Download
    https://repo1.maven.org/maven2/org/codehaus/groovy/groovy-all/2.4.1/groovy-all-2.4.1.jar
-   Download
    https://repo1.maven.org/maven2/org/gebish/geb-junit4/0.12.2/geb-junit4-0.12.2.jar
-   Download
    https://repo1.maven.org/maven2/com/codeborne/phantomjsdriver/1.2.1/phantomjsdriver-1.2.1.jar
-   Download
    https://repo1.maven.org/maven2/org/gebish/geb-core/0.12.2/geb-core-0.12.2.jar
-   Download
    https://repo1.maven.org/maven2/org/gebish/geb-waiting/0.12.2/geb-waiting-0.12.2.jar
-   Download
    https://repo1.maven.org/maven2/org/gebish/geb-ast/0.12.2/geb-ast-0.12.2.jar
-   Download
    https://repo1.maven.org/maven2/org/gebish/geb-exceptions/0.12.2/geb-exceptions-0.12.2.jar
-   Download
    https://repo1.maven.org/maven2/org/gebish/geb-implicit-assertions/0.12.2/geb-implicit-assertions-0.12.2.jar

<div>

**The final batch of tasks, both pre-installed Gradle tasks and
customized gradle tasks listed in the build.gradle file are run:**

</div>

-   :processTestResources
-   :testClasses
-   :downloadChromeDriver
-   :unzipChromeDriver
-   :chromeTest

\
A Browser will open, and the two tests will run!\
\
Want to look at the source code generated? I uploaded the basic
framework to my GitHub site
at <https://github.com/tjmaher/geb_project_generated_by_yo>\
\
We will dig into the code a bit more in the next blog post.\
\

Need Help with Yeoman?
----------------------

If you ever need any help with Yeoman, you can type into the command
line: *yo*\
*\
*\

::: {.separator style="clear: both; text-align: center;"}
[![](https://1.bp.blogspot.com/-xGa-1gavgSM/WAXPGhOXurI/AAAAAAAALg0/ac0IgsuIuMsVs9G1WSDGoXRRprWU1EFqwCLcB/s640/3%2Byo.png){width="640"
height="145"}](https://1.bp.blogspot.com/-xGa-1gavgSM/WAXPGhOXurI/AAAAAAAALg0/ac0IgsuIuMsVs9G1WSDGoXRRprWU1EFqwCLcB/s1600/3%2Byo.png)
:::

*\
*\
\
With the next blog post, we will be really digging into the scaffolding
code and how the project is set up.\
\
Until then, Happy Testing!\
\
\

::: {#toc-section .toc-section}
**Testing The-Internet with Geb + Groovy + Spock:**\

-   **Part One:** [About Yeoman, scaffolding, and other tooling
    applications](http://www.tjmaher.com/2016/10/testing-internet-with-geb-groovy-spock.html)
-   **Part Two:**  [A Step-By-Step Process: Installing and Configuring
    Yeoman and Chris Hluchan\'s Geb
    Generator](http://www.tjmaher.com/2016/10/testing-internet-with-geb-groovy-spock_19.html)
-   **Part Three**:  [Running the built-in tests from the command line,
    and examining how they have been set up with
    Gradle](http://www.tjmaher.com/2016/11/testing-internet-with-geb-groovy-spock.html)
-   **Part Four**:   Examining the Geb + Groovy + Spock code
    automatically generated
-   **Part Five**:   Modifying the Geb + Groovy + Spock Code to fit our
    needs
-   **Source Code:** [Initial source code generated out-of-the-box by
    the Yeoman Geb
    generator](https://github.com/tjmaher/geb_project_generated_by_yo)
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
