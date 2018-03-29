\-\-- layout: post title: \'Building a Test Framework: With Gradle,
everything is Groovy\' date: \'2016-06-15T01:19:00.001-04:00\' author:
T.J. Maher tags: - test framework - Gradle - Groovy modified\_time:
\'2016-06-15T01:19:17.791-04:00\' thumbnail:
https://3.bp.blogspot.com/-Jw2rrRuNWp0/V1-ZwqLPKCI/AAAAAAAALK4/6gB70d3Pd30s8FS\_OlfIARhSItLJeSBNwCLcB/s72-c/groovy.png
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-3548513135289399329
blogger\_orig\_url:
http://www.tjmaher.com/2016/06/building-test-framework-with-gradle.html
\-\-- So far, we\'ve seen how to set up the build dependencies in an
automated test framework, using Gradle in both
[IntelliJ](http://www.tjmaher.com/2016/05/webdriver-development-environment-setup.html)
and
[Eclipse](http://www.tjmaher.com/2016/06/webdriver-development-environment-setup.html).
Gradle is more than just a tool to set up build dependencies between
third-party software and the Selenium WebDriver framework.  And with the
hands-on learning you get from free courses that Gradle, Google, and
Udacity put together, you can learn about how Gradle configures tasks,
interacts with the file system, handles logging, works with
repositories, and sets up tests.\
\
I am really loving how Jeremy Silver explains things in the [Gradle for
Android and
Java](http://www.tjmaher.com/2016/06/free-udacity-course-gradle-for-android.html)
course he created on Udacity! Go
[here](https://www.udacity.com/course/gradle-for-android-and-java--ud867)
to sign up for the free course.\
\
Although I studied it in college and grad school, I have not spent much
day-to-day work as a coder until the past year. I love how he walks us
through, step-by-step how to follow along with the Gradle exercises he
has written, and how Gradle has been integrated with Groovy, a Domain
Specific Language (DSL).\
\

::: {.separator style="clear: both; text-align: center;"}
[![](https://3.bp.blogspot.com/-Jw2rrRuNWp0/V1-ZwqLPKCI/AAAAAAAALK4/6gB70d3Pd30s8FS_OlfIARhSItLJeSBNwCLcB/s1600/groovy.png)](https://3.bp.blogspot.com/-Jw2rrRuNWp0/V1-ZwqLPKCI/AAAAAAAALK4/6gB70d3Pd30s8FS_OlfIARhSItLJeSBNwCLcB/s1600/groovy.png)
:::

\
[]{#more}\
\
**[Sample Video: [Gradle for Android and
Java](https://www.udacity.com/course/gradle-for-android-and-java--ud867)]{.underline}:
Groovy Fundamentals:**

\
\

> *\"Gradle build scripts are written in Groovy. Groovy is a language
> that runs on the JVM that fills a hole for Java developers who need a
> scripting language. It\'s terse, expressive, interoperates extremely
> well with Java, and has some special features that make it ideally
> suited for creating domain specific languages.\
> \
> \"While we don\'t need to know a ton of Groovy to write Gradle build
> scripts, it helps a lot to experiment a bit with the basics. Gradle
> provides its own Groovy distribution, so we don\'t even need to
> install Groovy to get started. We can just put our Groovy code in a
> build.gradle file, and then ask Gradle to do anything that requires
> reading the build script\". - Jeremy Silver*

\
If you want to learn more about Gradle:\

-   [Subscribe](https://www.udacity.com/course/gradle-for-android-and-java--ud867) to
    the course
-   [Download](https://github.com/udacity/ud867) the example files
-   Install a simple text editor, such as [Sublime
    3](https://www.sublimetext.com/) to practice the exercises
-   Once you have a text editor, you can edit the example source code in
    the text editor, and run the code in your Command Line Interface,
    such as the MS-Dos Prompt or Mac Terminal.

\

About Gradle
------------

\
As near as I can figure out, Groovy was first mentioned on August 2003,
in the blog of the inventor, J[ames Strachan\'s
Weblog](http://radio-weblogs.com/0112098/2003/08/29.html#a399).\

> *\"So I\'ve been musing a little while if its time the Java platform
> had its own dynamic language designed from the ground up to work real
> nice with existing code; creating/extending objects normal Java can
> use and vice versa. Python/Jython\'s a pretty good base - add the nice
> stuff from Ruby and maybe sprinkle on some AOP features and we could
> have a really Groovy new language for scripting Java objects, writing
> test cases and who knows, even doing real development in it.\
> \
> \"I\'m finding that most of the time spent in a TDD style development
> model is actually coding the unit tests. There\'s typically lots of
> unit test code for little application code. Also there does seem to be
> some baggage when writing unit tests in java. This seems a great
> opportunity for using a concise & powerful dynamically typed language.
> So the initial idea was to make a little dynamic language which
> compiles directly to Java classes and provides all the nice (alleged)
> productivity benefits of python / ruby but allows you to reuse,
> extend, implement and test your existing Java code - and use that to
> write your unit tests. Add a little groovy maven plugin and hey
> presto, we\'ve boosted the TDD development cycle and created a nice
> dynamically-typed alternative to Java along the way.\
> \
> \"After some IRC chats with bob a new groovy language for the JVM has
> started to take shape, called Groovy. Its still very early days and
> much of this just exists on the GroovyWiki though bob\'s started work
> on the lexer & I\'ve started hacking some GroovyTests (unit tests in
> groovy) together to test the Groovy language implementation whenever
> we get the compiler/runtime working\".*

According to
[Wikipedia](https://en.wikipedia.org/wiki/Groovy_(programming_language)),
after winning the JAX 2007 innovation award, it was purchased by Pivotal
Software. By 2015 it was adopted by Apache.\
\
[Groovy programming language thrives under
Apache](http://www.infoworld.com/article/2997086/java/groovy-programming-language-thrives-under-apache.html)\
Infoworld, *Oct 26, 2015*\
\
*\"Moving over to the Apache Software Foundation has been good for the
Groovy language, with downloads more than doubling inside of six
months.*\
*\
\"Orphaned by Pivotal in March, the dynamic language for the Java
Virtual Machine was picked up by Apache. Since then, downloads have
boomed. \'After Groovy joined the Apache Foundation, the monthly
downloads doubled to 1.3 million per month. That\'s a massive increase
in less than six months,\' said project lead Guillaume Laforge, in a
blog post on Restlet.com. *\
*\
\"Under the jurisdiction of Apache, the project is independent of any
one company, Laforge noted. \'By putting the project at the Apache
Foundation, it\'s a stamp saying that the project is here to stay for
the long run.\'*\
*\
\"\[\...\] The language has niches in tasks like scripting for
automating tasks on servers and building of domain-specific languages
for business rules. Released in January, Groovy 2.4 added support for
Android development. \'Mobile developers have the choice to use Groovy
instead of Java for developing mobile applications on the Android
platform\' Laforge said. \"We are definitely seeing quite some usage
there.\' \"*\
\

**About Apache Groovy:**
------------------------

*\"Apache Groovy is a powerful, optionally typed and dynamic language,
with static-typing and static compilation capabilities, for the Java
platform aimed at improving developer productivity thanks to a concise,
familiar and easy to learn syntax. It integrates smoothly with any Java
program, and immediately delivers to your application powerful features,
including scripting capabilities, Domain-Specific Language authoring,
runtime and compile-time meta-programming and functional
programming\". *\
\
\

-   **Official Site of Apache Groovy**: <http://www.groovy-lang.org/>
-   **GitHub for Apache Groovy**: <https://github.com/apache/groovy>

\
\
According to the [Groovy Language
Documentation](http://www.groovy-lang.org/single-page-documentation.html),
Groovy...​\
\

-   is an agile and dynamic language for the Java Virtual Machine
-   builds upon the strengths of Java but has additional power features
    inspired by languages like Python, Ruby and Smalltalk
-   makes modern programming features available to Java developers with
    almost-zero learning curve
-   provides the ability to statically type check and statically compile
    your code for robustness and performance
-   supports Domain-Specific Languages and other compact syntax so your
    code becomes easy to read and maintain
-   makes writing shell and build scripts easy with its powerful
    processing primitives, OO abilities and an Ant DSL
-   increases developer productivity by reducing scaffolding code when
    developing web, GUI, database or console applications
-   simplifies testing by supporting unit testing and mocking
    out-of-the-box
-   seamlessly integrates with all existing Java classes and libraries
-   compiles straight to Java bytecode so you can use it anywhere you
    can use Java

\
\

Gradle and Jenkins
------------------

\
The main reason why I want to learn Gradle and Groovy is because of
Jenkins Pipeline. With Jenkins\' new Pipeline, instead of of spending an
hour or more setting and resetting configurations of the Jenkins jobs
that run your automated tests, you can set up Jenkins\' jobs
programatically.\
\
We just started experimenting with that at work, and I\'m trying to
learn the basics before it rolls out. And the tools and programming
languages they are using is Gradle and Groovy.\
\
**[Gary Hale: Managing Jenkins with Gradle:]{.underline}**

\

> *\"Recently, Jenkins has brought the \'Jenkins Workflow\' plugin into
> the core of Jenkins Continuous Integration pipeline automation and
> renamed it the \'Pipeline Plugin\'. Pipeline allows users of Jenkins
> to script automations using the Groovy programming language. This talk
> does not specifically address these newest features, rather we use the
> term workflow more generically to describe build automation pipelines
> defined in Gradle and how to integrate that with Continuous
> Integration in Jenkins.\
> \
> \"With scripts solutions, again, these are a way to run Groovy scripts
> within Jenkins that modify the environment. They're extremely
> powerful. What you're really doing is modifying the objects within the
> running Jenkins instance, and making changes that way. As if you were
> making those changes through the Gooey. It does require significant
> understanding of the Jenkins model, right. You have to understand to
> make this change to this particular attribute, or this job, what are
> the objects that I have to traverse to get to that particular change.
> What you find yourself doing is ultimately, there's not a lot of good
> information on this. You ultimately end up going out and pulling down
> the Jenkins source, and looking through all of that. That becomes a
> little tedious. If I'm only changing one thing, you know, do I really
> want to spend 20 minutes looking through source code trying to figure
> out how to do it. It is written Groovy, so it does leverage our
> existing skill set.\"*

It always surprises me just how much information there is out there:
Free courses. Free tutorial videos. Free documentation. It is easy for
me to get ahead of myself, spending a weekend learning a tool that I
don\'t end up using on the job. It\'s good to find an online course that
pertains to the work that I am doing.\
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
