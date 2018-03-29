\-\-- layout: post title: \'Notes: Selenium 3, the Spec, and Onwards by
Simon Stewart\' date: \'2016-05-25T19:44:00.003-04:00\' author: T.J.
Maher tags: - W3C - WebDriver - Simon Stewart modified\_time:
\'2016-05-25T20:21:03.842-04:00\' blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-3213427995350275986
blogger\_orig\_url:
http://www.tjmaher.com/2016/05/notes-selenium-3-spec-and-onwards-by.html
\-\-- **Title**: Selenium 3, the Spec, and Onwards\
**Speaker**: Simon Stewart, Selenium Project Lead\
**Host**: Applitools\
**Date**: Wed. May 25, 2016 @ 1:00 PM EDT\
**Duration**: 60 minutes\
\
Summing up Simon\'s Webinar:\

-   Selenium 3 (*no release date given*) will be a removal of all old
    Selenium RC code into a legacy library called \"leg-RC\".
-   Selenium 4 will move closer to the new W3C WebDriver Protocol they
    have been pushing for.
-   Selenium 5 will be the full W3C WebDriver.

\
Before that information was given at the end of the talk, Simon took a
long walk down Memory Lane\...\
\
[]{#more}\

How Selenium Started
--------------------

\
Jason Huggins ( [\@hugs](https://twitter.com/hugs) ) at the consulting
company, ThoughtWorks, was in Tech Support working on a new web
application to track time and expenses. Jason would fix one bug only to
have it appear in another browser. He saw Ward Cunningham FIT
([Framework for Integrated Test](http://fit.c2.com/)). Jason took this
idea and realized that all browsers handled HTML differently, but all
browsers used Javascript. Perhaps this could be leveraged?\
\

-   *See Paul Hammant\'s Thoughtworks article [Happy 10th Birthday,
    Selenium!](https://www.thoughtworks.com/insights/blog/happy-10th-birthday-selenium),
    Oct 22, 2014*

\
Selenium Core was created. It could manipulate the DOM (Document Object
Model), simulate clicks.\
\
Tests, like with FIT, were was based on HTML tables. Selenium Remote
Control (RC) was a good tool to start automating tests. He worked with
Paul Hammant to add new functionality to it, where people could use the
programming language of their choice.\
\
Two years after Jason stated, Simon Stewart was using HTTPUnit for
browser testing... and the web browser was rubbish (See the [official
home for HTTP Unit](http://httpunit.sourceforge.net/)). HTTPUnit was in
a gross violation of object oriented programming. Someone mentioned that
people should put in wrappers around the functionality. He did this
through six or seven iterations.\
\
Simon borrowed the word WebDriver from another project. He wrote a fresh
version, a "clean room" version of what he did before. At the time he
though he would be done, back in 2007, and he thought he would be done
in a year. Maybe two.\
\
Jason and Simon met up when they both moved on to Google. At the time,
AJAX was becoming popular. The problem was that you couldn't just
simulate a click. You had to emulate the mouse down and mouse up. As web
application were becoming more sophisticated, it became harder to
emulate what needed to be done.\
\
Simon foolishly he said, wrote versions of WebDriver tightly coupled to
the browser. Paul Hammant, Simon said, called him an idiot for doing
this. The product became branded Selenium 2.0.\
\

What is Selenium 3?
-------------------

\
Simon once announced three years ago they would release the next version
of Selenium WebDriver by Christmas\... Luckily, Simon joked, he didn't
say *what Christmas*.\
\
\"What is in Selenium 3 and why are we bumping in a version number?\"\
\
Only the current Selenium WebDriver API will be there. All outdated
Selenium Core code will be taken out.\
\
With the Python and Ruby bindings, there will be practically be no
changed. Java though... it will be breaking up into three separate
libraries:\
\
**Selenium-Java:**\

-   Just the WebDriver classes. 

\
**Selenium 3 Server: **\

-    Lightweight command line compatible remote server. 

\
**leg-rc:**\

-   The old Selenium client-side classes.
-   WebDriverBackedSelenium.
-   Remote end point for SEL server. 

\
\... As Simon said, "This is why the team doesn't let me name things
very often. I like a bad pun".\
\
If you are still using Selenium RC, there will be upgrade paths. New
implementation of HTML table runner. All of this work is placed in for
those who made a huge investment with Selenium RC.\
\
\

W3C Spec:
---------

\
**From the World Wide Web Consortium\'s WebDriver Page:**\
<https://www.w3.org/TR/webdriver/>\

> *\"WebDriver is a remote control interface that enables introspection
> and control of user agents. It provides a platform- and
> language-neutral wire protocol as a way for out-of-process programs to
> remotely instruct the behaviour of web browsers.\
> \
> \"Provided is a set of interfaces to discover and manipulate DOM
> elements in web documents and to control the behaviour of a user
> agent. It is primarily intended to allow web authors to write tests
> that automate a user agent from a separate controlling process, but
> may also be used in such a way as to allow in-browser scripts to
> control a --- possibly separate --- browser\".*

\
\"In conjunction with the browser venders, we have been working up a W3C
spec for WebDriver\". Opera, the browser company, suggested in the first
Selenium conference to take the API and use that as a spec. At the time
people were timid about adopting and using open source software. By
having a W3C spec, each company could do a complete clean room
implantation without using open source code.\
\
**Selenium 4**: They will ship a variant of the web driver protocol for
the W3C. Simon mentioned that the WebDriver project grew organically, so
things aren\'t as organized as they would like. As they have been
standardizing things, they have been making changes to the codebase.\
\
Selnium 3.0 client should be able to talk to the 4.0 server. And
Selenium 4.0 client should be able to talk to the 3.0 server. Selenium
5, though, will be just the W3C Standard, leaving just W3C WebDriver.\
\
With the W3C Spec, browser vendors own the drivers. Responsibility for
maintaining these switch from the open source enthusiasts currently
working on the project, volunteering their time to the browser companies
themselves.\
\
Example Simon listed: [Opera was able to add
Presto](https://github.com/operasoftware/operaprestodriver).\
\
ChromeDriver is a simple binary that knows how to start Chrome in a
special mode.  \
\
By allowing browser venders to own their own browser drivers, they are
able to hook into the browser with more efficiency thhan the WebDriver
could.\
\

Becoming Mobile:
----------------

\
In the early days of WebDriver, the concept of the web on the mobile
phone only started back with Steve Jobs and the iPhone.\
\
Mobile devices have different limitations and different controls than on
desktop. If you look at how modern mobile operating systems build their
UI, it is much like HTML, telling how to traverse the tree structure.
You can use the same tree style navigation that WebDriver uses in order
to automate it.\
\
Appium, IOS Driver (Facebook) all use the same API style to control
mobile devices. They work the same on devices and simulators and
emulators.\
\
If you want to see what is being done, Simon talked about how we should
check out
[gTECH](https://www.google.com/intl/us/about/careers/lifeatgoogle/gtech-software-engineering.html),
Google does some interesting talks to see what they have been doing.\
\
W3C WebDriver Level 2. There are some things that are completely awful
to automate, such as Coathangers: When an advanced functionality such as
geolocation, drops down asking for permission to use your location. It
would be very difficult to handle this with WebDriver. They are delaying
adding this work.\
\
Access to the [Shadow DOM](https://www.w3.org/TR/shadow-dom/) hasn't
been set up yet.\
\
Other considerations: They are still trying to figure out: How do we
integrate Siri, or other voice activated commands?\
\
Simon hopes you are using WebDriver wrapped up in Page Objects, so you
can swap out old Selenium RC methods, if you are still working on them.\
\
He then reiterated:\
\
**Selenium WebDriver 3.0:** Old Selenium RC code base removed and
separated.\
**Selenium WebDriver 4.0:** Start using the W3C WebDriver protocol.\
\
***Sidenote**: This is the 100th post at Adventures in Automation! *\
\
Happy Testing!\
\
-T.J. Maher\
Sr. QA Engineer,\
Fitbit-Boston\
\
*// QA Engineer since Aug. 1996\
// Automation developer for \[ 1 \] year and still counting!*
