\-\-- layout: post title: \'Meetup: How to Study Design Patterns\' date:
\'2015-06-02T11:40:00.003-04:00\' author: T.J. Maher tags: - Java -
Meetup - Design Pattern modified\_time:
\'2016-04-29T20:01:21.991-04:00\' blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-7742830177319305335
blogger\_orig\_url:
http://www.tjmaher.com/2015/06/meetup-how-to-study-design-patterns.html
\-\--

::: {.tr_bq}
**Boston Software Craftmanship**
:::

::: {.tr_bq}
Brightcove, 290 Congress Street, Boston, MA
:::

<http://www.meetup.com/Boston-Software-Craftsmanship/events/222541015/>\
*Monday, June 1st, 2015 @ 6:30 pm*\

> *\"Design Patterns have been a divisive topic in the programming
> community. Some consider them indispensable, while others find them
> harmful when intentionally applied. * 

> *\"In the game of Go, there exists a similar divide around the concept
> of Joseki. They\'ve had more time to wrestle with this conflict,
> though, and Toshiro Kageyama has made an attempt at reconciling these
> factions. In his seminal book \'Lessons in the Fundamentals of Go\',
> there is a chapter titled \"How to Study Joseki\". We will be applying
> this approach to studying Design Patterns. * 

> *\"If you own Design Patterns, please bring it; only one is necessary,
> but additional copies will help it go more smoothly\". - From the
> [Meetup
> site](http://www.meetup.com/Boston-Software-Craftsmanship/events/222541015/)*

\
[]{#more}\

### Announcements

\

-   Zach Shaw, the founder of the Boston Software Craftmanship Meetup,
    announced that the Meetup celebrated its fifth anniversary this past
    April. 
-   The motto of the group is \"*Improvement through practice\"*. If you
    have any ideas for any training sessions in software development,
    talk to Zach. 

\

### Design Patterns

\
The idea of this session on Design Patterns originated from a blog post
of the person presenting the session, Colin Williams.
 <http://blog.colinwilliams.name/blog/2015/03/14/how-to-study-design-patterns/>\
\
The book *Design Patterns: Elements of Reusable Object-Oriented
Software* \-- which I talk about in an earlier [blog
post](http://adventuresinautomation.blogspot.com/2015/05/page-objects-and-design-patterns-in.html) of
mine \-- famously popularized the idea of design patterns into the
software development community.\
\
Colin asked the audience: How many people have actually read the book,
Design Patterns? Not many hands went up. How many people tried to read
the book, Design Patterns? How many people have read at least 25% of the
book? Now the hands go up.\
\
It is hard to get through the book, Colin said. The knowledge is
valuable, but it is very dry. There is also criticism: Design patterns
are a controversial topic in the software development community:\
\

-   Blindly applying patterns can damage your code. 
-   There are many complex patterns that can be difficult to study.

\
\

### Studying Go: Joseki and Design Patterns

\
Colin switched topics:\
\
With the Go, the Chinese game over two thousand years old, there is a
method called *joseki \--* agreed upon sequences of moves that are
mutually beneficial to both players. Go is all about patterns. The
criticism is that:\
\
\

-   Blindly applying patterns damages you game
-   There are many complex patterns that can be difficult to study. 

\
Toshiro Kageyama, a professional Go player, explained these patterns
found in Go in his book, [Lessons in the Fundamentals of
Go](http://www.amazon.com/Lessons-Fundamentals-Beginner-Elementary-Books/dp/4906574289), originally
published in 1978. In it he has a chapter, \"How to Study Joseki\":\

> **The Proper Way to Study Joseki:** 

> 1\. Don\'t think that all you have to do is learn the moves. That is not
> studying joseki.  

> 2\. Every stone played by both sides in a joseki is the best move, so it
> is important to know the reason for it \-- its content, its meaning. If
> you can convince yourself as to why the stone is played where it is and
> why it is a good move, then you have done some studying.  

> 3\. Joseki moves are always the best moves on a local scale, but they
> sometimes become the worst moves in relation to the surrounding
> positions. This is what keeps go from becoming dull, what makes it
> interesting.  

> The above can be condensed into a single phrase: \'Josekis are not to
> be learned, but to be created\'. \[\...\]  

> *- From Kageyama\'s book, \"Lessons in the Fundamentals of Go\". *

\
Likewise, according to Colin, these lessons can be applied to studying
design patterns.\
\

> **The Proper Way to Study Design Patterns: **

> \"Don't just read the pattern, a deeper understanding is required to
> apply it correctly. 

> \"Each pattern is intended to solve a specific problem. Examine every
> line of an idealized implementation and contemplate the implications
> of every conceivable variation. 

> \"Consider how surrounding context can influence the needs of the
> pattern. A variation isn't necessarily invalid if external factors
> introduce additional needs\".\
> - *From Colin\'s [blog
> post](http://blog.colinwilliams.name/blog/2015/03/14/how-to-study-design-patterns/),
> How to Study Design Patterns*

Don\'t just learn the pattern. That is not studying.\
\
Each section in the book Design Patterns has a consequences section.
Don\'t read it at first. Try to see if you can guess the implementation
of the design pattern.\
\

### What Pattern to Study First?

There are many design patterns. What of the twenty-three design patterns
in the book to look at first?\
\
\

  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](http://ptgmedia.pearsoncmg.com/imprint_downloads/informit/IMAGES/figure1-1.bmp){width="272" height="320"}](http://ptgmedia.pearsoncmg.com/imprint_downloads/informit/IMAGES/figure1-1.bmp)
                                                                     Figure 1.1: Design Pattern Relationships, *Design Pattens*
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

\
Notice that you don\'t need to know any other design pattern to
understand the **Factory Method**. Once you know this pattern, it can be
the basis of other pattens such as the Template Method.\
\
\

::: {style="text-align: center;"}
**Download the slides for this lecture at
<http://github.com/lackita/DesignPatterns>.**
:::

\
\
With the Factory Method you have this class relationship with an
Application and a Document. You don\'t know what kinds of document you
are going to create.\
\

### Breakout into Groups 

###  [Attendees of the Meetup session broke into groups to review the sample code Colin had written. The sample code can be seen on his GitHub site at ]{style="font-size: small; font-weight: normal;"}[[<https://github.com/lackita/DesignPatterns/>.]{style="font-weight: normal;"}]{style="font-size: small;"}

### 

### Review of Factory Methods

\
The group broke out into teams to discuss code samples Colin had
provided to show examples of the Factory Method with Application.jabe,
Document.java, FactoryTest.jave, MyApplication.java and MyDocument.java
at <https://github.com/lackita/DesignPatterns/tree/master/Factory>\
\
\

::: {style="background: #ffffff; border-width: .1em .1em .1em .8em; border: solid gray; overflow: auto; padding: .2em .6em; width: auto;"}
+-----------------------------------+-----------------------------------+
| ``` {style="line-height: 125%; ma | ``` {style="line-height: 125%; ma |
| rgin: 0;"}                        | rgin: 0;"}                        |
|  1                                | import java.util.ArrayList;       |
|  2                                |                                   |
|  3                                | public abstract class Application |
|  4                                |  {                                |
|  5                                |  private ArrayList<Document> docs |
|  6                                | ;                                 |
|  7                                |                                   |
|  8                                |  public Application() {           |
|  9                                |   docs = new ArrayList<Document>( |
| 10                                | );                                |
| 11                                |  }                                |
| 12                                |                                   |
| 13                                |  public abstract Document createD |
| 14                                | ocument();                        |
| 15                                |                                   |
| 16                                |  public void newDocument() {      |
| 17                                |   Document doc = createDocument() |
| 18                                | ;                                 |
| ```                               |   docs.add(doc);                  |
|                                   |   doc.open();                     |
|                                   |  }                                |
|                                   |                                   |
|                                   | }                                 |
|                                   | ```                               |
|                                   |                                   |
|                                   | ``` {style="line-height: 125%; ma |
|                                   | rgin: 0;"}                        |
|                                   | https://github.com/lackita/Design |
|                                   | Patterns/blob/master/Factory/Appl |
|                                   | ication.java                      |
|                                   | ```                               |
+-----------------------------------+-----------------------------------+
:::

\
Groups performed a group code review of all the classes
in <https://github.com/lackita/DesignPatterns/tree/master/Factory> trying
to answer the following questions:\
\
*\... When should this pattern be used?*\
\
*\... When is it a bad idea to use this pattern?*\
\
*\... What broader context would change this pattern?*\
\

### Summary of Group Discussions on Factory Method

\
A participant mentioned that the software development community used to
overuse this ten years ago.  There used to be a time that there wasn\'t
an application where the Factory Method was used whether it was needed
or not. As software developers started using inheritance more,
developers steered more away from this.\
\
Zach, the founder of the group, mentioned that as long as you are
dealing with types or interfaces for inheritance the factory pattern is
both useful and broad. Sometimes you want to declare instantiation
better.  Let\'s say you wanted to handle in a software application MS
Word documents. Using the Factory design pattern would be perfect for
this. The Factory could handle the MS Word, licence key, how to open
documents, how to read documents, etc. You are hooking into an
abstraction of document management.\
\
Colin mentioned that there is a case where the Factory method is an
*antipattern*, when it hides the fact that a software developer has come
up with a too complicated data structure. Instead of cleaning up the
code, the code can be hidden in this pattern. Instead of breaking up 99
versions of the same field, people can simply stuff it in a pattern.\
\

### Review of Template Method

\
Next, participants were asked to review Colin\'s code dealing with the
Template Pattern,
at <https://github.com/lackita/DesignPatterns/tree/master/Template>.\
\
During the group discussion portion, a Fitbit co-worker of mine talked
about how he had just used this design pattern in the Fitbit app:\
\
Let\'s say you have goals in the Fitbit app. Each goal is similar. You
can create goal type objects, controlling them with a Parent GoalView
controller class. You can create template for the logic. Go get the data
that you need, and the parent class can show how to display it. Parent
class knows how to save the data, too.\
\
The downsides are that it makes things more abstract. As soon as you
deviate from the Template method, coming up with lists of exceptions to
the Template, you start wondering how much you are actually gaining by
using the Template and how much is over-engineering it.\
\

### My Thoughts

\
I really enjoyed this Meetup session. As someone who is just getting
into writing Java code on-the-job for the first time, I really enjoyed
getting exposure to topics that are more advanced than what I am used
to. I last programmed in Java ten years ago, during my courses for my
Masters of Software Engineering. Back then, we touched upon the Gang of
Four\'s Design Pattern book but didn\'t cover any design patterns in
depth.\
\
My only complaint was that the session relied too much on discussion
within your groups. If I didn\'t happen to have a co-worker of mine
sitting with me, who was very willing to talk about his experience using
design patterns and pitching them to my level, it could have been a very
bad experience for me.\
\
\
-T.J. Maher\
* Sr. QA Engineer, Fitbit*\
* Boston, MA*\
*\
// Automated tester for \[ 3 \] month and counting!*\
*\
Please note: \'Adventures in Automation\' is a personal blog about
automated testing. It is not an official blog
of [Fitbit.com](http://www.fitbit.com/). *\
