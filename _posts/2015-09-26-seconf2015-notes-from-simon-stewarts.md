\-\-- layout: post title: \" SeConf2015: Notes from Simon Stewart\'s
Keynote Address about WebDriver\" date:
\'2015-09-26T10:52:00.006-04:00\' author: T.J. Maher tags: - conference
- industry - WebDriver - Simon Stewart modified\_time:
\'2016-04-29T16:16:31.672-04:00\' thumbnail:
https://i.ytimg.com/vi/EWpjw0nDR2A/default.jpg blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-714770672031411042
blogger\_orig\_url:
http://www.tjmaher.com/2015/09/seconf2015-notes-from-simon-stewarts.html
\-\-- *Looking to see the latest trends in automated software testing?
The Selenium Conference 2015 ( 9/10/2015 - 9/12/2015 ), held in
Portland, Oregon, has placed online most of the speaker\'s notes and
slides. <http://confengine.com/selenium-conf-2015/schedule>. T.J. Maher
will be reviewing them over then next couple of weeks and blogging about
them.*\
*\
\
*\

Selenium Conference 2015: Notes from watching Simon Stewart\'s \"State of the Union\" keynote address
-----------------------------------------------------------------------------------------------------

\
Right now, I am too focused on turning myself from a manual software
tester of fifteen years, into a junior level Java developer writing
automated tests for eCommerce application at work to even think about
becoming a Selenium WebDriver Committer, one of the people who help
build out the open source tool.\
\
[]{#more}\
\
I\'ve made great strides in the past six months, going from being a
Software Quality Assurance Engineer who tests software with written
testcases I have developed, pointing, clicking and typing with a mouse
and a keyboard, into a junior level Java developer, writing tests with
Selenium WebDriver, setting up Jenkins jobs to schedule and kick off our
Continuous Integration test suite, and Selenium Grid and Sauce Labs to
spin up virtual images of Chrome and Firefox and Internet Explorer.\
\
Contributing to the Selenium project, learning as I go, is where I want
to be. If only there were more hours in a day! After [blogging about the
talk in
February](http://adventuresinautomation.blogspot.com/2015/02/seconf2014-q-with-selenium-committers.html),
discovering the [SeConf2014 Program
Schedule](http://confengine.com/selenium-conf-2014/schedule) and
listening to most of their talks, I thought they sounded like a fun
group of people. I have been looking forward to these talks all year!\
\
\
**[SeConf2015: State of the Union]{.underline}**\
*Simon Stewart, Facebook*\
\

\
\

### The Web: Then vs Now

\
Simon Stewart mentioned that it\'s a much different world when Selenium
RC Test Runner was first released by Jason Huggins while Jason and Simon
were back at
[Thoughtworks](https://en.wikipedia.org/wiki/ThoughtWorks) (a big
sponsor of the agile development movement), where Simon was working on
his project HTMLUnit. Both projects became merged into Selenium
WebDriver.\
\
The web has changed since WebDriver was first released. People don\'t
just use desktops to surf the web; they use mobile devices, the
[Internet of Things](https://en.wikipedia.org/wiki/Internet_of_Things),
web accessibility in everything, with JavaScript being placed in
everything.\
\
You aren\'t constrained to a browser to access the web. Apps can do it,
too. Simon pointed out there is a struggle for your attention, between
Web Apps and Native Apps. When accessing Facebook, how do you access it
most of the time? Do you go to the web site on your Desktop? Or do you
view it on your phone through the Mobile App? People are accessing the
web not simply through a web page on their computer. Mobile devices have
expanded into every part of people\'s life.\
\
When WebDriver was first launched, they found the web elements to
interact and manipulate by traversing the **DOM** (Document Object
Model).\

> *The Document Object Model (DOM) is the model that describes how all
> elements in an HTML page, like input fields, images, paragraphs etc.,
> are related to the topmost structure: the document itself. By calling
> the element by its proper DOM name, we can influence it.  *

> *-QuirksMode, [Intro to
> DOM](http://www.quirksmode.org/dom/intro.html) *

\
Now, Simon says, we don\'t just have a DOM. We have ***Shadow DOM***, we
have ***web components***. It is now a battle between Web vs Native
apps. Things like ***getUserMedia***, and ***Web Works*** are competing
with Native apps on their own turf.\
 \
**[Shadow DOM:]{.underline}**\
\

-   When designing a page, there is always a struggle to separate the
    content from the design. The Shadow DOM is a way to do that. There
    is an old tutorial I found on [Shadow DOM
    101](http://www.html5rocks.com/en/tutorials/webcomponents/shadowdom/) *(12/2013)*
    where with HTML5 and Cascading Style Sheets

> *Shadow DOM refers to the ability of the browser to include a subtree
> of DOM elements into the rendering of a document, but not into the
> main document DOM tree. *

> *\[\...\] Browser developers realized that coding the appearance and
> behavior of HTML elements completely by hand is a) hard and b) silly.
> So they sort of cheated.\
> They created a boundary between what you, the Web developer can reach
> and what's considered implementation details, thus inaccessible to
> you. The browser however, can traipse across this boundary at will.
> With this boundary in place, they were able to build all HTML elements
> using the same good-old Web technologies, out of the divs and spans
> just like you would. *

> *- [Dimitri
> Glazkov](http://glazkov.com/2011/01/14/what-the-heck-is-shadow-dom/)
> (1/2011)* 

\
**[Web Components:]{.underline}**\
\

-   Dr. Axel Rauschmayer has an article \"[What happened to Web
    Components](http://www.2ality.com/2015/08/web-component-status.html)?\"
    *(8/2015)*, the Google project to make it easier for web developers
    to design pages that other browser manufacturers are integrating. 

\
\

### How does WebDriver Stay Relevant?

\
In order for WebDriver to stay relevant, Selenium needs to be able to
test Mobile Apps. Native applications have the tree/ node setup in the
DOM. Since mobile apps aren\'t going to go away, WebDriver needs to
learn how to use it.\
\
A few points Simon made in his slides need investigation:\
\
*\"React Native may give us breathing room\"*\
\

-   **React** is a JavaScript library that Facebook has developed to
    build user interfaces. <http://facebook.github.io/react/> and
    at <https://code.facebook.com/projects/176988925806765/react/>
-   **React Native,** introduced** **in January of 2015 at the ReactJS
    conference** ***(
    [video](https://code.facebook.com/videos/786462671439502/react-js-conf-2015-keynote-introducing-react-native-/)
    )*** **is built on top of React to make Android and IOS
    applications <https://facebook.github.io/react-native/>
-   Both are built on top of **Node JS **<https://nodejs.org/en/>

\
*\"JSON Wire Protocol is being extended\"*\
\

-   Simon directed us to Johnathan Lipps talk on **The Mobile JSON Wire
    Protocol** at the conference.

\

> ***Jonathan Lipps**:\
> The JSON Wire Protocol (JSONWP) is the version of the WebDriver spec
> currently implemented by all the Selenium clients. It defines an HTTP
> API that models the basic objects of web automation\-\--sessions,
> elements, etc\... The JSON Wire Protocol is the magic that powers
> Selenium\'s client/server architecture, enables services like Selenium
> Grid or Sauce Labs to work, and gives you the ability to write your
> test scripts in any language.* 

> *The JSONWP has served Selenium faithfully for a number of years, but
> the future of automated testing lies beyond the borders of the web
> browser. Mobile automation is an essential ingredient in any build,
> and tools like Appium or Selendroid have made it possible to run tests
> against mobile apps using the JSONWP. The JSONWP\'s current
> incarnation isn\'t enough to automate all the new behaviors that
> mobile apps support, however. Complex gestures, multiple device
> orientations, airplane mode, and the ability to use both native and
> web contexts, for example, are all essential to mobile automation.* 

> *For this reason the leaders of the Selenium project, in concert with
> other Selenium-based projects like Appium and Selendroid, met to
> discuss the future of the JSONWP. We\'ve been working on its next
> version, called the \"Mobile JSON Wire Protocol\" (MJSONWP). Appium
> and Selendroid already implement much of the MJSONWP spec. In this
> talk I\'ll dive into the specifics of the MJSONWP extensions, how they
> relate to the original JSONWP, and how the Selenium clients have begun
> to implement them.
> ( [video](https://www.youtube.com/embed/wjvAh4yjwtI?feature=oembed), [slides](https://speakerdeck.com/player/295dd56cb45d45a8847a32cad609beed?feature=oembed) )*

\

### Hurdle \#1: Automating iOS Mobile Devices

\
Simon mentioned that iOS is still problematic to automated. Getting
automation for any iPhone or iPad to work is difficult because the UI
Automation framework currently used was designed only for basic
interaction. It keeps breaking when you try to use it for automation\...
\"And there is a one second sleep command with whatever interaction you
do\".\
\
**WebDriverAgent: **As a solution at Facebook, Simon Stewart has a tool
called WebDriverAgent:\
\

-   Runs in the simulator of the device
-   WebDriver server for iOS
-   Able to run across apps, testing opening apps from yours
-   Written in Objective C and runs alongside the app
-   Removes middle layers, making it faster
-   IOS 7 - 9 supported
-   [github.com/facebook/WebDriverAgent](http://github.com/facebook/WebDriverAgent)

\
\... Facebook is working to make this tool OpenSource. The name
WebDriverAgent may change.\
\
**FBSimulatorControl: **Another tool Simon talked about is
FBSimulatorControl:\
\

-   iOS Simulator Management
-   Runs multiple IOS simulators on your Mac at once
-   Handles cleaning simulator, installing apps, changing locale,
    setting up general settings
-   With WebDriverAgent, you\'re able to test force quitting your app
    and re-opening it.

\
\
Simon made the whole audience chuckle by demoing these two tools,
showing three apps running at once on the same screen, and saying in a
sincere voice:\

> \"If you aren\'t familiar with this, this is the Facebook application.
> I suggest downloading it and clicking on some ads?\"

\

### Hurdle \#2: End-to-End Testing

\
End-to-End testing is unstable. How do we set up test data? How do we
simulate the backend? End to End testing is slow, so we set up parallel
tests with Selenium Grid and setting up your own virtual machines, or
have other virtual machiens set up for you, such as Sauce Labs, and
BrowserStack.\
\
With Selenium WebDriver, we can move beyond testing. It can be use it to
monitor your website.\
\
\

### The Future

\

-   **WebDriver might stop being an open source project**: Having
    Selenium WebDriver as an open source project may be reaching the end
    of its shelf life. The Selenium project can\'t support all the
    features people want to do by the volunteers in the Open Source
    community. There needs to be a major re-write.
-   **WebDriver is becoming a W3C standard**: The W3C is \"hustling
    towards being a recommendation\".
-   **WebDriver is becoming supported by major companies**: Microsoft\'s
    new browser, Edge, supports WebDriver. SauceLabs without any other
    work, could add that to their browser testing suite because it had
    the same model they were used to.
-   **FireFox is implementing WebDriver, too**: Mozilla Firefox is
    coming up with their implementation of WebDriver called Marionette.

\

<div>

\

</div>

\
-T.J. Maher\
 Sr. QA Engineer, Fitbit\
* // Manual tester, 15 years*\
* // Automated tester for \[ 6 \] months and counting*\
\
*Please note: \'Adventures in Automation\' is a personal blog about
automated testing. It is not an official blog
of [Fitbit.com](http://www.fitbit.com/). *
