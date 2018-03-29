\-\-- layout: post title: \'Notes: Introduction to Artifactory, build
tools, binary files, and binary repositories\' date:
\'2016-07-09T00:26:00.000-04:00\' author: T.J. Maher tags:
modified\_time: \'2016-07-09T00:42:13.830-04:00\' thumbnail:
https://i.ytimg.com/vi/iYzD4TNJFSE/default.jpg blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-4752094351476325250
blogger\_orig\_url:
http://www.tjmaher.com/2016/07/notes-introduction-to-artifactory-build.html
\-\-- With this blog post, I wanted to talk about a tool we are using at
work, JFrog **Artifactory**, <https://www.jfrog.com/artifactory/>  to
store our dependencies and our binary files. Whenever I start learning a
new tool, I always search for online demos of the new tool, introductory
YouTube videos, and free training classes and webinars. Sometimes, I am
pleasantly surprised\...\
\
If you are a newly minted automation developer, you might not know that
there is a lot more to the software development process than just
writing code:\

-   A Selenium WebDriver / Java test depends on the Java bindings for
    Selenium (the selenium-java library) to be downloaded and usable for
    your Selenium / Java project. 
-   The tests need to be built and compiled into some type of form
    before they can be run. Build artifacts, such as JAR (Java Archive)
    files, need to stored somewhere until they are ready to be used.

\
**Artifactory** helps by providing a way to store both the dependencies
and the files produced. And their webinar might help put technical
concepts in context, things that a manual tester may not be familiar
with: build tools, Maven, Gradle, binary files, blobs, diff tools, and
source control systems.\
**\
Build Tools** \-- such as **Maven** and **Gradle** \-- automate the
creation of executable applications from source code. The build process
incorporates downloading dependencies \-- such as Selenium-Java in a
Selenium WebDriver / Java project \-- compiling, linking and packaging
the code into a usable or executable form \-- such as a JAR (\*.jar)
file in a Java project.\
\
[]{#more}\
\

-   *See examples of setting up Selenium-Java with [Maven and
    POM](http://www.tjmaher.com/2015/12/automate-amazon-development-environment.html)
    (project object model) files.* 
-   *See examples of setting up a Selenium-Java project [using
    Gradle](http://www.tjmaher.com/2016/05/webdriver-development-environment-setup.html). *
-   *Travel back in time to the
    [WikiWikiWeb](http://www.tjmaher.com/2016/06/time-capsule-ward-cunninghams-wiki-wiki.html)
    to read about Apache Ant, and Apache Maven.*

\
\
What is produced from the build process is a **binary file**.  It is no
longer human readable source code. Well, you might be able to make out
any META tags. Maybe the header. Or a word or two. But it is not the
same as when you were writing the original source code.\
\
You can\'t just use a **diff tool** anymore to compare and contrast the
changes of *two different versions* of a binary file. You can\'t fire up
your command line interface, whether Unix or Mac Terminal, and type in:\

-    *diff file1.txt file2.text*

<div>

\... and see line by line what the difference is between, say, the
source code on your local branch on your computer in your working
directory, and what has been checked into master. 

</div>

\
\
[**Introduction to JFrog Artifactory Webinar**
(*YouTube*):]{.underline}\

\
\
**Artifactory: **<https://www.jfrog.com/artifactory/>\
**Artifactory
Wiki:** <https://www.jfrog.com/confluence/display/RTF/Using+Artifactory>\
\
Artifactory isn\'t just a place to store binary files. It provides
**versioning** (applying a version control system) to them.\
\
Have you explored **GitHub**? Software developers who are passionate
about sharing their source code, such as the [SeleniumHQ
project](https://github.com/SeleniumHQ/selenium) that produced Selenium
WebDriver, post their code in public code repositories. If you know the
Java programming language, the code is more (or less) readable.\
\
You can use **source control systems**, such as Git, to manage of
changes to documents, the source code of computer programs, large web
sites, and other collections of information.\
\
Artifactory is of the opinion that binary files should not go into a
source control system:\
\

-   Sources are text files. Binaries are blobs, built from sources.
-   Sources are diffable. Binaries are not.
-   Sources are versioned by content. Binaries are versioned by name.

\
A \"blob\" is a **Binary Large Object**\... a \"collection of binary
data stored as a single entity in a database management system. Blobs
are typically images, audio or other multimedia objects, though
sometimes binary executable code is stored as a blob\". [According to
Wikipedia](https://en.wikipedia.org/wiki/Binary_large_object), a
database architect in the 1960s immediately thought of the movie when
trying to describe a large chunk of data, and what the B.L.O.B. actually
stands for has been reinvented more than a few times.\
\
Let\'s say you commit a text file into the source control system the
piece of text: \"Mary had a little lamb\". Then you committed the piece
of text: \"Then she had some mashed potatoes\". The two **commits** are
stored in two separate files, the original, then the changes (the
\"delta\").\
\
With a source control system, once the piece of text or code is
committed and merged into the master branch, everyone can pull the new
changes onto their system. Every developer has a clone of the entire
code repository on their local computer.\
\
If you store a really large file, such as a binary file (like a JAR file
or ZIP file) each developer has to store a copy of the increasingly
large repo on their machine. The solution just does not scale. Large
files clog up a Git repository.\
\

-   *Read [more about
    Git](http://www.tjmaher.com/2015/04/git-fest-april-24-2015-600-pm.html). *

\
What of you want to store binaries on a File Server? It also doesn\'t
scale. Artifactory makes the pitch: Think of the possible requirements
for storing binary files. You might want to search the binary repository
by Name, context, and content.\
\
What if you want to manage the artifact lifecycle? What if you want to
maintain and clean up your snapshots each time your retention policy
changes or is triggered? What if you want to optimize your storage size?
You cannot compress your binary and reduce the size.\
\
A fileserver does not give you REST API access to your artifacts. If you
want to fetch and deploy your artifact in an automated fashion, you need
exposure to the REST APIs.Artifactory is a Binary Repository that
fulfills all these requirements.\
\
With Artifactory, artifacts are not deleted on the fly. It picks up
orphan binaries with garbage collection, usually once per day, but can
be changed to once a week depending on your retention policy.\
\

### Problems with Binary Files: Too Large!

\
Back in 2001 Agile binaries were very small. With the advent of
Continuous Integration and Continuous Delivery, things got bigger. Then
DevOps and Microservices took over, and file sizes got bigger still.
Then Docker containerizing everything: The size of the binaries
exploded.\
\
According to Artifactory, you need to know where the binaries are being
stored, where they are being used, and if the binary is for a release
candidate. What if you want to track the binary back to the source?
Which binary did you want to push to production?\
\
Artifactory adds Metadata automatically, and with custom metadata
tagging, such as QA  PASS, QA Fail, and various platforms. It also adds
implicit metadata such as size, download stats, author, etc. It also
tells you where the build URL is coming from.\
\
Need to write queries to search for data? You can write queries on the
metadata with the Artifactory Query Language.\

<div>

\

</div>

<div>

\... All in all, I really liked their introductory video. It helped put
terms in context, ones that I hadn\'t heard of since grad school,
putting me in the shoes of other software developers and the problems
they may face.\
\
They even provide a Gradle build script, such as with their Gradle
Plugin
at <https://www.jfrog.com/confluence/display/RTF/Gradle+Artifactory+Plugin>\
\

::: {.code .panel .pdl style="background-color: white; border-radius: 5px; border: 1px dashed rgb(187, 187, 187); color: #333333; font-family: Arial, sans-serif; font-size: 14px; line-height: 20px; margin: 10px 0px; overflow: auto; padding: 0px;"}
::: {.codeHeader .panelHeader .pdl style="background: rgb(245, 245, 245); border-bottom-color: rgb(204, 204, 204); border-bottom-style: solid; border-bottom-width: 1px; border-top-left-radius: 5px; border-top-right-radius: 5px; line-height: 1em; margin: 0px; overflow: hidden; padding: 5px 15px; position: relative;"}
**Build script snippet for use in all Gradle versions**
:::

::: {.codeContent .panelContent .pdl style="background-attachment: initial; background-clip: initial; background-image: initial; background-origin: initial; background-position: initial; background-repeat: initial; background-size: initial; border-bottom-left-radius: 3px; border-bottom-right-radius: 3px; margin: 0px; overflow: hidden; padding: 0px;"}
::: {style="margin: 0px; padding: 0px;"}
::: {#highlighter_592997 .syntaxhighlighter .nogutter .text style="font-size: 1em !important; margin: 0px !important; overflow: auto !important; padding: 0px; position: relative !important; width: 561px;"}
+-----------------------------------------------------------------------+
| ::: {.container style="background: none !important; border-radius: 0p |
| x !important; border: 0px !important; bottom: auto !important; box-si |
| zing: content-box !important; float: none !important; height: auto !i |
| mportant; left: auto !important; margin: 15px 0px 0px !important; min |
| -height: auto !important; outline: 0px !important; overflow: visible  |
| !important; padding: 0px 0px 15px !important; position: relative !imp |
| ortant; right: auto !important; top: auto !important; vertical-align: |
|  baseline !important; white-space: pre-wrap !important; width: auto ! |
| important;" title="Hint: double-click to select code"}                |
| ::: {.line .number1 .index0 .alt2 style="background-attachment: initi |
| al !important; background-clip: initial !important; background-image: |
|  none !important; background-origin: initial !important; background-p |
| osition: initial !important; background-repeat: initial !important; b |
| ackground-size: initial !important; border-radius: 0px !important; bo |
| rder: 0px !important; bottom: auto !important; box-sizing: content-bo |
| x !important; float: none !important; height: auto !important; left:  |
| auto !important; margin: 0px !important; min-height: auto !important; |
|  outline: 0px !important; overflow: visible !important; padding: 0px  |
| 1em 0px 0px !important; position: static !important; right: auto !imp |
| ortant; top: auto !important; vertical-align: baseline !important; wh |
| ite-space: nowrap !important; width: auto !important;"}               |
| `buildscript {`{.text .plain                                          |
| style="background: none !important; border-radius: 0px !important; bo |
| rder: 0px !important; bottom: auto !important; box-sizing: content-bo |
| x !important; color: rgb(0, 0, 0) !important; float: none !important; |
|  font-family: Consolas, "Bitstream Vera Sans Mono", "Courier New", Co |
| urier, monospace !important; height: auto !important; left: auto !imp |
| ortant; margin: 0px !important; min-height: auto !important; outline: |
|  0px !important; overflow: visible !important; padding: 0px !importan |
| t; position: static !important; right: auto !important; top: auto !im |
| portant; vertical-align: baseline !important; width: auto !important; |
| "}                                                                    |
| :::                                                                   |
|                                                                       |
| ::: {.line .number2 .index1 .alt1 style="background-attachment: initi |
| al !important; background-clip: initial !important; background-image: |
|  none !important; background-origin: initial !important; background-p |
| osition: initial !important; background-repeat: initial !important; b |
| ackground-size: initial !important; border-radius: 0px !important; bo |
| rder: 0px !important; bottom: auto !important; box-sizing: content-bo |
| x !important; float: none !important; height: auto !important; left:  |
| auto !important; margin: 0px !important; min-height: auto !important; |
|  outline: 0px !important; overflow: visible !important; padding: 0px  |
| 1em 0px 0px !important; position: static !important; right: auto !imp |
| ortant; top: auto !important; vertical-align: baseline !important; wh |
| ite-space: nowrap !important; width: auto !important;"}               |
| `  `{.text .spaces                                                    |
| style="background: none !important; border-radius: 0px !important; bo |
| rder: 0px !important; bottom: auto !important; box-sizing: content-bo |
| x !important; float: none !important; font-family: Consolas, "Bitstre |
| am Vera Sans Mono", "Courier New", Courier, monospace !important; hei |
| ght: auto !important; left: auto !important; margin: 0px !important;  |
| min-height: auto !important; outline: 0px !important; overflow: visib |
| le !important; padding: 0px !important; position: static !important;  |
| right: auto !important; top: auto !important; vertical-align: baselin |
| e !important; width: auto !important;"}`repositories {`{.text         |
| .plain                                                                |
| style="background: none !important; border-radius: 0px !important; bo |
| rder: 0px !important; bottom: auto !important; box-sizing: content-bo |
| x !important; color: rgb(0, 0, 0) !important; float: none !important; |
|  font-family: Consolas, "Bitstream Vera Sans Mono", "Courier New", Co |
| urier, monospace !important; height: auto !important; left: auto !imp |
| ortant; margin: 0px !important; min-height: auto !important; outline: |
|  0px !important; overflow: visible !important; padding: 0px !importan |
| t; position: static !important; right: auto !important; top: auto !im |
| portant; vertical-align: baseline !important; width: auto !important; |
| "}                                                                    |
| :::                                                                   |
|                                                                       |
| ::: {.line .number3 .index2 .alt2 style="background-attachment: initi |
| al !important; background-clip: initial !important; background-image: |
|  none !important; background-origin: initial !important; background-p |
| osition: initial !important; background-repeat: initial !important; b |
| ackground-size: initial !important; border-radius: 0px !important; bo |
| rder: 0px !important; bottom: auto !important; box-sizing: content-bo |
| x !important; float: none !important; height: auto !important; left:  |
| auto !important; margin: 0px !important; min-height: auto !important; |
|  outline: 0px !important; overflow: visible !important; padding: 0px  |
| 1em 0px 0px !important; position: static !important; right: auto !imp |
| ortant; top: auto !important; vertical-align: baseline !important; wh |
| ite-space: nowrap !important; width: auto !important;"}               |
| `    `{.text .spaces                                                  |
| style="background: none !important; border-radius: 0px !important; bo |
| rder: 0px !important; bottom: auto !important; box-sizing: content-bo |
| x !important; float: none !important; font-family: Consolas, "Bitstre |
| am Vera Sans Mono", "Courier New", Courier, monospace !important; hei |
| ght: auto !important; left: auto !important; margin: 0px !important;  |
| min-height: auto !important; outline: 0px !important; overflow: visib |
| le !important; padding: 0px !important; position: static !important;  |
| right: auto !important; top: auto !important; vertical-align: baselin |
| e !important; width: auto !important;"}`jcenter()`{.text              |
| .plain                                                                |
| style="background: none !important; border-radius: 0px !important; bo |
| rder: 0px !important; bottom: auto !important; box-sizing: content-bo |
| x !important; color: rgb(0, 0, 0) !important; float: none !important; |
|  font-family: Consolas, "Bitstream Vera Sans Mono", "Courier New", Co |
| urier, monospace !important; height: auto !important; left: auto !imp |
| ortant; margin: 0px !important; min-height: auto !important; outline: |
|  0px !important; overflow: visible !important; padding: 0px !importan |
| t; position: static !important; right: auto !important; top: auto !im |
| portant; vertical-align: baseline !important; width: auto !important; |
| "}                                                                    |
| :::                                                                   |
|                                                                       |
| ::: {.line .number4 .index3 .alt1 style="background-attachment: initi |
| al !important; background-clip: initial !important; background-image: |
|  none !important; background-origin: initial !important; background-p |
| osition: initial !important; background-repeat: initial !important; b |
| ackground-size: initial !important; border-radius: 0px !important; bo |
| rder: 0px !important; bottom: auto !important; box-sizing: content-bo |
| x !important; float: none !important; height: auto !important; left:  |
| auto !important; margin: 0px !important; min-height: auto !important; |
|  outline: 0px !important; overflow: visible !important; padding: 0px  |
| 1em 0px 0px !important; position: static !important; right: auto !imp |
| ortant; top: auto !important; vertical-align: baseline !important; wh |
| ite-space: nowrap !important; width: auto !important;"}               |
| `  `{.text .spaces                                                    |
| style="background: none !important; border-radius: 0px !important; bo |
| rder: 0px !important; bottom: auto !important; box-sizing: content-bo |
| x !important; float: none !important; font-family: Consolas, "Bitstre |
| am Vera Sans Mono", "Courier New", Courier, monospace !important; hei |
| ght: auto !important; left: auto !important; margin: 0px !important;  |
| min-height: auto !important; outline: 0px !important; overflow: visib |
| le !important; padding: 0px !important; position: static !important;  |
| right: auto !important; top: auto !important; vertical-align: baselin |
| e !important; width: auto !important;"}`}`{.text                      |
| .plain                                                                |
| style="background: none !important; border-radius: 0px !important; bo |
| rder: 0px !important; bottom: auto !important; box-sizing: content-bo |
| x !important; color: rgb(0, 0, 0) !important; float: none !important; |
|  font-family: Consolas, "Bitstream Vera Sans Mono", "Courier New", Co |
| urier, monospace !important; height: auto !important; left: auto !imp |
| ortant; margin: 0px !important; min-height: auto !important; outline: |
|  0px !important; overflow: visible !important; padding: 0px !importan |
| t; position: static !important; right: auto !important; top: auto !im |
| portant; vertical-align: baseline !important; width: auto !important; |
| "}                                                                    |
| :::                                                                   |
|                                                                       |
| ::: {.line .number5 .index4 .alt2 style="background-attachment: initi |
| al !important; background-clip: initial !important; background-image: |
|  none !important; background-origin: initial !important; background-p |
| osition: initial !important; background-repeat: initial !important; b |
| ackground-size: initial !important; border-radius: 0px !important; bo |
| rder: 0px !important; bottom: auto !important; box-sizing: content-bo |
| x !important; float: none !important; height: auto !important; left:  |
| auto !important; margin: 0px !important; min-height: auto !important; |
|  outline: 0px !important; overflow: visible !important; padding: 0px  |
| 1em 0px 0px !important; position: static !important; right: auto !imp |
| ortant; top: auto !important; vertical-align: baseline !important; wh |
| ite-space: nowrap !important; width: auto !important;"}               |
| `  `{.text .spaces                                                    |
| style="background: none !important; border-radius: 0px !important; bo |
| rder: 0px !important; bottom: auto !important; box-sizing: content-bo |
| x !important; float: none !important; font-family: Consolas, "Bitstre |
| am Vera Sans Mono", "Courier New", Courier, monospace !important; hei |
| ght: auto !important; left: auto !important; margin: 0px !important;  |
| min-height: auto !important; outline: 0px !important; overflow: visib |
| le !important; padding: 0px !important; position: static !important;  |
| right: auto !important; top: auto !important; vertical-align: baselin |
| e !important; width: auto !important;"}`dependencies {`{.text         |
| .plain                                                                |
| style="background: none !important; border-radius: 0px !important; bo |
| rder: 0px !important; bottom: auto !important; box-sizing: content-bo |
| x !important; color: rgb(0, 0, 0) !important; float: none !important; |
|  font-family: Consolas, "Bitstream Vera Sans Mono", "Courier New", Co |
| urier, monospace !important; height: auto !important; left: auto !imp |
| ortant; margin: 0px !important; min-height: auto !important; outline: |
|  0px !important; overflow: visible !important; padding: 0px !importan |
| t; position: static !important; right: auto !important; top: auto !im |
| portant; vertical-align: baseline !important; width: auto !important; |
| "}                                                                    |
| :::                                                                   |
|                                                                       |
| ::: {.line .number6 .index5 .alt1 style="background-attachment: initi |
| al !important; background-clip: initial !important; background-image: |
|  none !important; background-origin: initial !important; background-p |
| osition: initial !important; background-repeat: initial !important; b |
| ackground-size: initial !important; border-radius: 0px !important; bo |
| rder: 0px !important; bottom: auto !important; box-sizing: content-bo |
| x !important; float: none !important; height: auto !important; left:  |
| auto !important; margin: 0px !important; min-height: auto !important; |
|  outline: 0px !important; overflow: visible !important; padding: 0px  |
| 1em 0px 0px !important; position: static !important; right: auto !imp |
| ortant; top: auto !important; vertical-align: baseline !important; wh |
| ite-space: nowrap !important; width: auto !important;"}               |
| `    `{.text .spaces                                                  |
| style="background: none !important; border-radius: 0px !important; bo |
| rder: 0px !important; bottom: auto !important; box-sizing: content-bo |
| x !important; float: none !important; font-family: Consolas, "Bitstre |
| am Vera Sans Mono", "Courier New", Courier, monospace !important; hei |
| ght: auto !important; left: auto !important; margin: 0px !important;  |
| min-height: auto !important; outline: 0px !important; overflow: visib |
| le !important; padding: 0px !important; position: static !important;  |
| right: auto !important; top: auto !important; vertical-align: baselin |
| e !important; width: auto !important;"}`classpath "org.jfrog.buildinf |
| o:build-info-extractor-gradle:4.4.0"`{.text                           |
| .plain                                                                |
| style="background: none !important; border-radius: 0px !important; bo |
| rder: 0px !important; bottom: auto !important; box-sizing: content-bo |
| x !important; color: rgb(0, 0, 0) !important; float: none !important; |
|  font-family: Consolas, "Bitstream Vera Sans Mono", "Courier New", Co |
| urier, monospace !important; height: auto !important; left: auto !imp |
| ortant; margin: 0px !important; min-height: auto !important; outline: |
|  0px !important; overflow: visible !important; padding: 0px !importan |
| t; position: static !important; right: auto !important; top: auto !im |
| portant; vertical-align: baseline !important; width: auto !important; |
| "}                                                                    |
| :::                                                                   |
|                                                                       |
| ::: {.line .number7 .index6 .alt2 style="background-attachment: initi |
| al !important; background-clip: initial !important; background-image: |
|  none !important; background-origin: initial !important; background-p |
| osition: initial !important; background-repeat: initial !important; b |
| ackground-size: initial !important; border-radius: 0px !important; bo |
| rder: 0px !important; bottom: auto !important; box-sizing: content-bo |
| x !important; float: none !important; height: auto !important; left:  |
| auto !important; margin: 0px !important; min-height: auto !important; |
|  outline: 0px !important; overflow: visible !important; padding: 0px  |
| 1em 0px 0px !important; position: static !important; right: auto !imp |
| ortant; top: auto !important; vertical-align: baseline !important; wh |
| ite-space: nowrap !important; width: auto !important;"}               |
| `  `{.text .spaces                                                    |
| style="background: none !important; border-radius: 0px !important; bo |
| rder: 0px !important; bottom: auto !important; box-sizing: content-bo |
| x !important; float: none !important; font-family: Consolas, "Bitstre |
| am Vera Sans Mono", "Courier New", Courier, monospace !important; hei |
| ght: auto !important; left: auto !important; margin: 0px !important;  |
| min-height: auto !important; outline: 0px !important; overflow: visib |
| le !important; padding: 0px !important; position: static !important;  |
| right: auto !important; top: auto !important; vertical-align: baselin |
| e !important; width: auto !important;"}`}`{.text                      |
| .plain                                                                |
| style="background: none !important; border-radius: 0px !important; bo |
| rder: 0px !important; bottom: auto !important; box-sizing: content-bo |
| x !important; color: rgb(0, 0, 0) !important; float: none !important; |
|  font-family: Consolas, "Bitstream Vera Sans Mono", "Courier New", Co |
| urier, monospace !important; height: auto !important; left: auto !imp |
| ortant; margin: 0px !important; min-height: auto !important; outline: |
|  0px !important; overflow: visible !important; padding: 0px !importan |
| t; position: static !important; right: auto !important; top: auto !im |
| portant; vertical-align: baseline !important; width: auto !important; |
| "}                                                                    |
| :::                                                                   |
|                                                                       |
| ::: {.line .number8 .index7 .alt1 style="background-attachment: initi |
| al !important; background-clip: initial !important; background-image: |
|  none !important; background-origin: initial !important; background-p |
| osition: initial !important; background-repeat: initial !important; b |
| ackground-size: initial !important; border-radius: 0px !important; bo |
| rder: 0px !important; bottom: auto !important; box-sizing: content-bo |
| x !important; float: none !important; height: auto !important; left:  |
| auto !important; margin: 0px !important; min-height: auto !important; |
|  outline: 0px !important; overflow: visible !important; padding: 0px  |
| 1em 0px 0px !important; position: static !important; right: auto !imp |
| ortant; top: auto !important; vertical-align: baseline !important; wh |
| ite-space: nowrap !important; width: auto !important;"}               |
| `}`{.text .plain                                                      |
| style="background: none !important; border-radius: 0px !important; bo |
| rder: 0px !important; bottom: auto !important; box-sizing: content-bo |
| x !important; color: rgb(0, 0, 0) !important; float: none !important; |
|  font-family: Consolas, "Bitstream Vera Sans Mono", "Courier New", Co |
| urier, monospace !important; height: auto !important; left: auto !imp |
| ortant; margin: 0px !important; min-height: auto !important; outline: |
|  0px !important; overflow: visible !important; padding: 0px !importan |
| t; position: static !important; right: auto !important; top: auto !im |
| portant; vertical-align: baseline !important; width: auto !important; |
| "}                                                                    |
| :::                                                                   |
|                                                                       |
| ::: {.line .number9 .index8 .alt2 style="background-attachment: initi |
| al !important; background-clip: initial !important; background-image: |
|  none !important; background-origin: initial !important; background-p |
| osition: initial !important; background-repeat: initial !important; b |
| ackground-size: initial !important; border-radius: 0px !important; bo |
| rder: 0px !important; bottom: auto !important; box-sizing: content-bo |
| x !important; float: none !important; height: auto !important; left:  |
| auto !important; margin: 0px !important; min-height: auto !important; |
|  outline: 0px !important; overflow: visible !important; padding: 0px  |
| 1em 0px 0px !important; position: static !important; right: auto !imp |
| ortant; top: auto !important; vertical-align: baseline !important; wh |
| ite-space: nowrap !important; width: auto !important;"}               |
| `apply plugin: "com.jfrog.artifactory"`{.text .plain                  |
| style="background: none !important; border-radius: 0px !important; bo |
| rder: 0px !important; bottom: auto !important; box-sizing: content-bo |
| x !important; color: rgb(0, 0, 0) !important; float: none !important; |
|  font-family: Consolas, "Bitstream Vera Sans Mono", "Courier New", Co |
| urier, monospace !important; height: auto !important; left: auto !imp |
| ortant; margin: 0px !important; min-height: auto !important; outline: |
|  0px !important; overflow: visible !important; padding: 0px !importan |
| t; position: static !important; right: auto !important; top: auto !im |
| portant; vertical-align: baseline !important; width: auto !important; |
| "}                                                                    |
| :::                                                                   |
| :::                                                                   |
+-----------------------------------------------------------------------+
:::
:::
:::
:::

</div>

\
\... Not familiar with JCenter? \...\
\
**Using Bintray\'s JCenter for Gradle resolution:**\

\
\
You can set up Vagrant, Maven, Gradle, Docker and other types of
repositories in \"minutes\" with them.\
\

-   See other Screencasts by
    JFrog: <https://www.jfrog.com/video/one-minute-artifactory/>

\
As always, Happy Testing!\
\
-T.J. Maher\
Sr. QA Engineer,\
Fitbit-Boston\
\
*// BSCS, MSE, and QA Engineer since Aug. 1996\
// Automation developer for \[ 1.5 \] years and still counting!\
// Check out Adventures in Automation and Like us on
[Facebook](https://www.facebook.com/AdventuresInAutomation/)!*
