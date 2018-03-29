\-\-- layout: post title: \'Free Udacity Course: Gradle for Android and
Java\' date: \'2016-06-12T00:51:00.003-04:00\' author: T.J. Maher tags:
- courses - Java - test framework - Gradle modified\_time:
\'2016-06-13T00:01:05.820-04:00\' thumbnail:
https://3.bp.blogspot.com/-0rRlco6AdKA/V1xEBqna9QI/AAAAAAAALKg/W6IxVSplc2kDmsMvP0z4eqIpIA7CC\_LvgCLcB/s72-c/welcome.png
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-8829541353061203328
blogger\_orig\_url:
http://www.tjmaher.com/2016/06/free-udacity-course-gradle-for-android.html
\-\-- Want to more about Gradle? Sign up for a free course on Udacity!\
\
**Gradle for Android and Java **\
<https://www.udacity.com/course/gradle-for-android-and-java--ud867>\
\

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://3.bp.blogspot.com/-0rRlco6AdKA/V1xEBqna9QI/AAAAAAAALKg/W6IxVSplc2kDmsMvP0z4eqIpIA7CC_LvgCLcB/s400/welcome.png){width="400" height="327"}](https://3.bp.blogspot.com/-0rRlco6AdKA/V1xEBqna9QI/AAAAAAAALKg/W6IxVSplc2kDmsMvP0z4eqIpIA7CC_LvgCLcB/s1600/welcome.png)
                                                                     [*https://www.udacity.com/course/gradle-for-android-and-java\--ud867*](https://www.udacity.com/course/gradle-for-android-and-java--ud867)
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

\
\
When putting together an automation framework using Selenium WebDriver
and Java, you need a way to store the dependencies. This is so you
don\'t have to end up downloading every single third-party component,
piece-by-piece. When I was taking a course in [Selenium WebDriver 2 with
Java](http://compendiumdev.co.uk/page.php?title=seleniumwebdrivercourse),
I was introduced to a tool called Maven to do this for me.\
\
Maven was a pretty simple tool to set up. Gradle, though, is a bit more
complex.\
\
We have been using Gradle at my workplace ever since I first started my
job as an automation engineer. It never was my job description to set up
all the initial dependencies, the reporting and logging, design the
build process, or set up the tasks, so Gradle was just another buzzword
to me.\

<div>

\

</div>

<div>

Lately, though, the senior members of the team have been using a lot
more of its functionality. This is why, all of a sudden, blog posts on
Gradle start appearing, such as:\

-   [WebDriver development environment setup with IntelliJ, Gradle,
    Hamcrest, and
    ChromeDriver](http://www.tjmaher.com/2016/05/webdriver-development-environment-setup.html)
-   [WebDriver development environment setup with Eclipse, Gradle,
    Hamcrest, and
    ChromeDriver](http://www.tjmaher.com/2016/06/webdriver-development-environment-setup.html)
-   [A Quick Gradle Overview: Setting Dependencies and Running
    Tests](http://www.tjmaher.com/2016/06/a-quick-gradle-overview-setting.html)

### 

A Free Course in Gradle!
------------------------

\
I was referred to a free course on Gradle
through [Gradle.org](http://gradle.org/) and its tutorial section.\
\
The course was put together by Mark Viera, Core Engineer at Gradle, and
Jeremy Silver, a Udacity course developer.\

-   Looking just for Gradle Information for your Selenium / Java
    automation framework? Take the first part of [Gradle for Android and
    Java](https://www.udacity.com/course/gradle-for-android-and-java--ud867).
-   Looking to build Android apps? Take Udacity\'s free course:
    [Developing Android Apps: Android
    Fundamentals](https://www.udacity.com/course/developing-android-apps--ud853). 

\
[]{#more}\
\
[](https://www.blogger.com/null){#more}\

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://1.bp.blogspot.com/-0Jv6CRat7Cs/V1w51I33tZI/AAAAAAAALKI/o5Us92jPlZInUklURXAGMKeGTMv_iR2VgCLcB/s400/welcome.png){width="400" height="215"}](https://1.bp.blogspot.com/-0Jv6CRat7Cs/V1w51I33tZI/AAAAAAAALKI/o5Us92jPlZInUklURXAGMKeGTMv_iR2VgCLcB/s1600/welcome.png)
                                                                                                                           Udacity\'s Welcome to Gradle!
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

\

Why Gradle? And Why This Course? 
---------------------------------

\
When building a Java project, it\'s easy to build a small project. You
compile the source file to create the classes. You bundle them into Jar
(Java Archive) files for easy distribution.\
\
But what if you want to generate documentation out of the code,
assembling Javadocs? What if you wish to place the Jar files in a
repository? Integrate unit tests, integration tests, or acceptance tests
for a project?\
\
For a large project, such as a Selenium WebDriver / Java automation
framework, things get hairy.\
\
\
**[Udacity's Why Gradle?]{.underline}**\

\
\
\
Why does building software matter? And why Gradle?\
\
It used to be that builders just compiled and packaged their source
code. Now builds run tests, generate documentation, publish applications
and manage dependencies. The build has become the software factory that
processes the software.\
\
Google wanted to find an all-in-one tool that did all that for their
Android Studio. That is why they selected Gradle as the built-in build
processor.\
\
**[Udacity\'s Command Line Gradle]{.underline}**\

\
\
**[Installing Gradle:]{.underline}**\
\
Gradle knows how to install itself. All it needs is a shell script \--
The Gradle Wrapper \-- and a small JAR file \-- *gradle.jar* \-- to
install itself. If Gradle is installed already, it will simply pass
along the Gradle command command. If not, Gradle will install itself.\
\
There are two types of Gradle wrappers:\
\

-   gradlew: Wrapper for Mac / Linux
-   gradlew.bat: Wrapper for Windows

\
\
To run the grade wrapper:\
*./gradlew*\
\
Gradle then contacts <http://services.gradle.org/distributions/> \... in
the video, you can see it is grabbing and downloading
gradle-2.3-bin-zip.\
\

Tips Given Through the Course
-----------------------------

\
Gradle takes a while to start up because it spins up an entire instance
of the Java Virtual Machine. Using the Gradle Daemon speeds up this
process. This daemon process is started, and continuously runs in the
background, keeping the JVM instance alive. Later Gradle runs can use
the same instance.\
\
If you are using Android Studio, it is always explicitly running. From
the command line, you have to explicitly enable it.\
\

Free Homework Assignments!
--------------------------

\
This Udacity course even has coding exercises on GitHub at
<https://github.com/udacity/ud867> Jeremy Silver, the course developer
for Udacity we were introduced to in the first video of the course, has
over fifty exercises you can do.\
\
Can\'t figure out the solution? Jeremy has included the answer in
a *solution.gradle* folder.\
\
Speaking from experience, the only way to truly learn the material is by
doing the work yourself.\
\
Have fun, and happy Testing!\
\
-T.J. Maher\
Sr. QA Engineer,\
Fitbit-Boston\
\
*// QA Engineer since Aug. 1996\
// Automation developer for \[ 1 \] year and still counting!\
// Check out Adventures in Automation on
[Facebook](https://www.facebook.com/AdventuresInAutomation/)!*

</div>
