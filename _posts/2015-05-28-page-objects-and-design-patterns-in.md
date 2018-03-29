\-\-- layout: post title: Intro to Page Objects and Design Patterns in
Selenium WebDriver date: \'2015-05-28T13:29:00.003-04:00\' author: T.J.
Maher tags: - code examples - beginner - Page Object - Design Pattern -
test framework - Dave Haeffner modified\_time:
\'2016-04-29T07:53:17.123-04:00\' thumbnail:
https://i.ytimg.com/vi/AVrnBJDQeaI/default.jpg blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-4762067037382142500
blogger\_orig\_url:
http://www.tjmaher.com/2015/05/page-objects-and-design-patterns-in.html
\-\-- When writing automation scripts, object-oriented design patterns
\-- templates on how to structure the classes and objects created in
Python or Java \-- can be quite useful. One of the first design patterns
automation engineers encounter are [Page
Objects](https://code.google.com/p/selenium/wiki/PageObjects), but there
are others. Before introducing the talk, here\'s a quick history lesson
on Patterns.\
\

### 

### Pattern Languages in Object-Oriented Programming

### 

\
As part of the Association for Computing Machinery (ACM), a new group
called OOPSLA (Object-Oriented Programming, Systems, Languages &
Applications) was formed to address the concept of object-oriented
programming which was becoming the dominant programming methodology.\
\
At OOPSLA \'87, the group\'s second conference, Kent Beck \-- the future
originator of \"[Extreme
Programming](http://software2012team23.googlecode.com/git-history/5127389d21813c2bd955c53999f66cede994578b/docs/literature/Extreme_Programming_Explained_Kent_Beck_1999.pdf)\",
the precursor to Agile \-- presented a talk that took the concept of
architectural design patterns detailed in *A Pattern Language: Towns,
Buildings, Construction (1977)* and applied them to software
engineering.\
\
[]{#more}\
\

> \"The search for an appropriate methodology for object-oriented
> programming has seen the usual rehash of tired old ideas, but the fact
> is that OOP is so different that no mere force-fit of structured
> analysis or entity-relationship methods will provide access to the
> potential inherent in OOP. In particular, neither of these methods
> address the user interface design issues that have obviously become of
> paramount importance. In addition, while E-R seems to be
> \"object-oriented\" it is not suited to the dynamic nature of objects
> as in Smalltalk and encourages the use of a global perspective while
> designing, a sure lose in object-oriented programming. 

> \"We propose a radical shift in the burden of design and
> implementation, using concepts adapted from the work of Christopher
> Alexander, an architect and founder of the Center for Environmental
> Structures. Alexander proposes homes and offices be designed and built
> by their eventual occupants. These people, he reasons, know best their
> requirements for a particular structure. We agree, and make the same
> argument for computer programs. Computer users should write their own
> programs. The idea sounds foolish when one considers the size and
> complexity of both buildings and programs, and the years of training
> for the design professions. Yet Alexander offers a convincing
> scenario. It revolves around a concept called a \'pattern language.\'
> \" (*[Abstract of Using Pattern Languages for Object-Oriented
> Programs](http://c2.com/doc/oopsla87.html), 9/17/1987* )

\
**Related Links: **\
\

-   **Oracle\'s Java Tutorials**: Object-Oriented Programming
    Concepts: <http://docs.oracle.com/javase/tutorial/java/concepts/>
-   **Association for Computing Machinery**: <https://www.acm.org/>
-   **OOPSALA History**: <http://www.oopsla.org/oopsla-history/> 

\
\

### Design Patterns: Elements of Reusable Object-Oriented Software 

\
A few years later, at OOPSLA \'91, at a session called \"Towards an
Architecture Handbook\", Kent Beck and his partner in developing the
\"Extreme Programming\" concept, Ward Cunningham, re-introduced to the
attendees the concept of patterns. Four of the attendees, Eric Gamma and
Richard Helm, Ralph Johnson and John Vlissides found they had common
research, and grouped up to write a book, *Design Patterns: Elements of
Reusable Object-Oriented Software* (1994). Listing everyone\'s name was
difficult, so they were dubbed, \"The Gang of Four\".\
\
The book became quite popular, and is still referred to over twenty
years later.\

> \"The first two chapters are an introduction and explain the reasons
> of the existence of design patterns, how they should be used, good and
> bad practices... Design patterns without rules to apply them are
> useless (as the original architectural patterns are useless without
> drawings skills). A practical example is the object of the second
> chapter. 

> \"Design patterns are exposed in a three parts catalog. Each pattern
> each described by a complete explanation, an UML diagram, the
> interactions between the pattern elements, as well as some
> implementation solutions (all solutions cannot be written, as it is
> language-dependent)\"  - *From [Matt Eifelle\'s Book
> Review](http://matt.eifelle.com/2009/04/14/book-review-design-patterns-elements-of-reusable-object-oriented-software/). *

\
**Related Links:**\
\

-   The [ContentCreationWiki](http://c2.com/cgi/wiki) discusses in a
    very loose and informal conversational style
     [SoftwareDevelopment](http://c2.com/cgi/wiki?SoftwareDevelopment) of
    the late 1980s and mid-1990s.
-   The wiki also talks about the
    [HistoryOfPatterns](http://c2.com/cgi/wiki?HistoryOfPatterns),
    [KentBeck](http://c2.com/cgi/wiki?KentBeck),
    [WardAndKent](http://c2.com/cgi/wiki?WardAndKent), the
    [ArchitectureHandBookWorkshop](http://c2.com/cgi/wiki?ArchitectureHandbookWorkshop),
    the [GangOfFour](http://c2.com/cgi/wiki?GangOfFour), their
    [DesignPatternsBook](http://c2.com/cgi/wiki?DesignPatternsBook), and
    the inevitable
    [PatternBacklash](http://c2.com/cgi/wiki?PatternBacklash). 
-   Interesting sections on
    [ObjectOriented](http://c2.com/cgi/wiki?ObjectOriented) programming,
    [ObjectOrientedForDummies](http://c2.com/cgi/wiki?ObjectOrientedForDummies), [EncapsulationForDummies](http://c2.com/cgi/wiki?EncapsulationForDummies)
    can also be found on the wiki. 
-   **Design Patterns: Elements of Reusable Object-Oriented Software**
    on [Amazon.com](http://www.amazon.com/Design-Patterns-Elements-Reusable-Object-Oriented/dp/0201633612/)
-   **Design Patterns: Elements of Reusable Object-Oriented
    Software** in [PDF
    Format](http://www.uml.org.cn/c++/pdf/DesignPatterns.pdf)

\
\

### **The Page Object Design Pattern**

\
*Taken from SeleniumHQ: Test Design Considerations:*\
\

> \"Page Object is a Design Pattern which has become popular in test
> automation for enhancing test maintenance and reducing code
> duplication. A page object is an object-oriented class that serves as
> an interface to a page of your AUT. The tests then use the methods of
> this page object class whenever they need to interact with that page
> of the UI. The benefit is that if the UI changes for the page, the
> tests themselves don't need to change, only the code within the page
> object needs to change. Subsequently all changes to support that new
> UI are located in one place. 

> \"The Page Object Design Pattern provides the following advantages.

> \"1. There is clean separation between test code and page specific
> code such as locators (or their use if you're using a UI map) and
> layout.

> \"2. There is single repository for the services or operations offered
> by the page rather than having these services scattered through out
> the tests.

> \"In both cases this allows any modifications required due to UI
> changes to all be made in one place. Useful information on this
> technique can be found on numerous blogs as this 'test design pattern'
> is becoming widely used. We encourage the reader who wishes to know
> more to search the internet for blogs on this subject. Many have
> written on this design pattern and can provide useful tips beyond the
> scope of this user guide. To get you started, though, we'll illustrate
> page objects with a simple example\" \[
> [MORE](http://docs.seleniumhq.org/docs/06_test_design_considerations.jsp#page-object-design-pattern)
> \].

\

### 

### **Design Patterns beyond the Page Object**

\
Now that the basics are introduced, I can go into the initial reason for
this blog post\...\
\
During last Fall\'s Selenium Conference 2014, there was a talk **Design
Patterns beyond the Page Object** given by Derrick Kearney from Purdue
University that I really enjoyed when I watched it online.\
\
Description of the talk: **Design Patterns beyond the Page Object**\

> \"In an age where the Page Object Pattern and Page Factory Pattern
> dominate web testing conversations, there is still a need to
> understand and apply the design patterns of yesteryear. Ideas from the
> Facade Pattern, Factory Method Pattern, the Iterator Pattern, the
> Object Pool Pattern, and the Decorator Pattern all find their way into
> the Page Objects we build to represent the increasingly complex
> widgets found on today\'s websites. 

> \"In this presentation, we take it back to the old school, looking at
> novel ways to apply classic design patterns, like those developed by
> the Gang of Four and Code Complete, to new screen scraping problems.
> We will investigate three common scenarios where using the typical
> approach to page objects can be inefficient or difficult, including
> filling in a web form, iterating over data in a list, and traversing
> iframes to communicate with widgets. We will explore how to improve
> upon the naive approach to building these page objects through the use
> of classic design patterns. Finally, we will formalize our findings
> into new patterns which can be applied to more general scenarios\". \[
> [MORE](http://confengine.com/selenium-conf-2014/proposal/348/design-patterns-beyond-the-page-object-an-investigation-into-the-design-patterns-used-while-building-page-objects)
> \]

\

::: {style="text-align: center;"}
:::

\

::: {style="text-align: center;"}
*[Slides in PDF
Format](https://github.com/codedsk/seleniumconf2014/blob/master/presentations/seleniumconf2014_20140905_design_patterns_beyond_page_object.pdf) *
:::

::: {style="text-align: center;"}
*[Slides in PPT
format](https://github.com/codedsk/seleniumconf2014/blob/master/presentations/seleniumconf2014_20140905_design_patterns_beyond_page_object.pptx) *
:::

\
The recorded talk skips over the WebForm Design Pattern and jumps to the
ItemList Design Pattern.\
\
Here are one of the patterns covered\...\
\

### ItemList Design Pattern

\
Let\'s say you have a list of items on a web page, such as a list of
products returned from an Amazon.com an eBay search, or a search of
support tickets. You don\'t want to hardcode the locators, but you want
the ability to see the items in order, interact with the items in the
list, and to search through the items.\
\
Picture your search results as being in a Container, and each result as
an item in this container. The items returned are sequential.\
\
For this, you can create a Container class, where you can create
different methods such as returning how many items are in the Container
(num\_items()), iterating from one item to the next ( creating a next()
method ).\
\
You can also create methods to get\_item\_by\_position() and
get\_item\_by\_property() to search through this container.\
\
\
-T.J. Maher\
* Sr. QA Engineer, Fitbit*\
* Boston, MA*\
*\
// Automated tester for \[ 2 \] month and counting!*\
*\
Please note: \'Adventures in Automation\' is a personal blog about
automated testing. It is not an official blog
of [Fitbit.com](http://www.fitbit.com/). *\
