\-\-- layout: post title: \'SeConf2014: Q&A with Selenium Committers\'
date: \'2015-02-13T14:22:00.002-05:00\' author: T.J. Maher tags: -
conference - Jim Evans - WebDriver - Simon Stewart modified\_time:
\'2016-04-29T16:19:03.114-04:00\' thumbnail:
https://i.ytimg.com/vi/0vnkI1IEFaA/default.jpg blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-8000103879763620676
blogger\_orig\_url:
http://www.tjmaher.com/2015/02/seconf2014-q-with-selenium-committers.html
\-\-- The Fourth Annual Selenium Conference was held between September 4
to September 6, 2014 in Bangalore, India.\
\
By going to the [Program
Schedule](http://confengine.com/selenium-conf-2014/schedule) on their
[Official 2014 Selenium Conference
Site](http://www.seleniumconf.org/2014/index.html) you can see:\
\

-   The times each talk had been held
-   Bios of each speaker
-   Slides shown and handouts that were given out at the time
-   Descriptions of each talk
-   YouTube links of the talk given that you can watch. 

\
[]{#more}\
\

::: {.separator style="clear: both; text-align: center;"}
:::

<div>

They have many HOWTO talks such as building Selenium WebDriver pages,
scaling and managing Selenium Grid, the Allure framework, Clojure for
mobile app testing, Appium for Mobile testing, how to incorporate
JavaScript into your Selenium tests for stability \-- Everything that I
am trying to learn right now. But my favorite talks were when the main
Selenium Contributors talked about their experiences working with the
Selenium Project.

</div>

<div>

\

</div>

<div>

Here are a few of my favorite talks that I have watched on YouTube about
the conference:\
\

</div>

### Embrace and Extend: How the Selenium Project Convinced the World\'s Largest Closed-Source Company (Microsoft) to Participate

::: {.separator style="clear: both; text-align: center;"}
\
:::

\

<div>

\

</div>

<div>

Jim Evans, the person who designed the IE Driver for Selenium WebDriver,
talks about his career at Microsoft and how attempting to keep on
finding better and better ways of testing things led him to be a
contributor to the Selenium Project. It gives a good retrospective on
the challenges QA Engineers have faced since the mid-1990s, automated
test strategies he learned, and how he joined the Selenium WebDriver
project.  (58 minutes)\
\
\

### Q & A with the Selenium Commitee

\

\
The Q & A with the Selenium Committers is hosted by the main developers
of the Selenium Project.\
\

-   Simon Stewart, creator of WebDriver and lead on the Selenium
    Project. 
-   Jim Evans, now at Salesforce, owns the IE Drivers.
-   Andreas Tolfsen  ( [blog](http://sny.no/) )  wrote initial Opera
    Driver. Now working at Mozilla.  They are coming up with a
    replacement for Firefox that also works on devices. More information
    on the Marionette project is on the [Mozilla Developers
    Network](https://developer.mozilla.org/en-US/docs/Mozilla/QA/Marionette). 
-   Dima Kovalenko, from Groupon 
-   Julian Harty, testing and documenting Selenium, working at eBay. 
-   Santiago Suarez Ordoñez, at Sauce Labs. 

\
Here is just a sample of what was discussed during the hour and a half
session:\
\

#### **Q) When would Selenium 3 be coming out? Many customers who are driving developers to use Selenium are wondering when the next version will come out.** 

\
**A)** Selenium\'s API\'s, according to Simon Stewart, has been
remarkable stable since 2011. Selenium 3 will be mainly cleaning up the
old Selenium-RC code. Selenium 4 will also have these same APIs. Because
it is an open source project, there can\'t be a set release schedule.
Selenium 3 will be backwards and forwards compatible with Selenium 2
(WebDriver) and Selenium 4, so you can do a slow stage migration with
any tests you have created.\
\

#### **Q) Why doesn\'t Selenium WebDriver open a new tab in Firefox when it starts up. Why does it open a whole new window? **

\
**A)** Simon confessed:\
\

> \"The reason it does it in Firefox Driver is because I couldn\'t
> figure out how to switch to a different tab when they introduced
> tabs\... and so I made it open a new window\... if someone wants to
> send me a patch to make it less lame, I would really, really
> appreciate that!\". 

\

#### **Q) Why can Selenium sometimes be so slow?**

\
**A)**  Slowness can be because of all the HTTP calls that Selenium
WebDriver makes. Simon mentioned that they are going to be coming up
with a new ActionsAPI suggested by Mozilla where actions will be clumped
together, and then sent \"over the wire\" in one lump.\
\
Andreas Tolfsen added that they were looking to add that feature because
of instances when Selenium is being run on mobile devices. Mobile
devices have slow CPUs.\
\
Santiago Suarez Ordoñez mentioned that a new feature coming up: Status
dumps where it will give a report of how long each process took, and
what was executed, along with HTTP status codes.\
\

> \"Writing Selenium tests is easy, but debugging them when they break
> is really really hard, and this will give us the visibility we
> need\". 

\

#### **Q) Where can one find more information about how the drivers work? **

\
**A)** If you ever have questions, take a look at the [Selenium
Wiki](https://code.google.com/p/selenium/w/list) on
Code.Google.Com. There you can see a description of platforms in
Selenium Grid, How the Firefox Driver works, about the Internet Explorer
driver, Ruby & Python bindings, and Selenium\'s setup of Continuous
Integration. It also gives tips on how developers can work with the
WebDriver codebase.\
\
There are a lot of developer facing tools on the Wiki.\
\
After looking there, you can review the [official user
group](https://groups.google.com/forum/#!forum/selenium-users) on Google
Groups.\
\
After that, you can pop into their IRC (Internet Relay Chat) channel
on on \#selenium at Freenode (irc.freenode.net).\
\

#### **Q) How does Selenium grow the number of contributors to their open source project?  **

\
**A)** According to Simon, that is the purpose of the conferences and
workshops they run. Bugs are also marked on their [Bug
Tracker](https://code.google.com/p/selenium/issues/list) on
Code.Google.Com as \"Get Involved\". If you don\'t have a huge amount of
experience but you are interested in sinking your teeth into the
project, you can get involved that way. Selenium also moved away from
Selenium to Git and mirrored themselves onto Github. They did this to
enhance the number of contributions by the public.\
\
Simon Stewart said: \"Moving up a level, one of the things we have is
user group evenings in quite a few cities around the world. I know there
is one in San Francisco, there is one in London \[\...\] I think there
is one in Berlin as well\".  If they are in town and there is a local
Selenium group moving they like popping in, to check in with the local
community.\
\
Yes, it would be nice if there was a developer evangelist who walked
around explaining it if they were a company\... but they are not a
company. They are people who do this in their free time. Some of them
are lucky that they work at companies that sponsor their work.\
\
Because of the open source nature of the work, they have some money, but
that is used to put on conferences, not hire evangelists. \"You are
never going to get rich doing it\".\
\
Dima Kovalenko brought up:\

> \"Some people keep on prefixing their question with \'I\'m not a
> developer, I\'m QA\'. That\'s what I used to do and I still do because
> I am not a developer \... but .. there is no reason for you not to try
> top fix a bug. A year ago I didn\'t know Java. I hated it \... I still
> hate it. I didn\'t know it. Now I know it a little bit. I needed to
> fix a very frustrated bug that I found and I decided that I would just
> go and learn it. On one hand I am contributing to the project and
> making the project which is great and on the other hand I am padding
> my resume for a nice job\... so I am just throwing it out there!\" 

\

#### **Q) What kind of roadmap do you have on the mobile automation side? **

\
Simon says:\

> \"So, from the Selenium Project itself, the main thing we are doing to
> help the roadmap with mobile is \[..\] that we are hosting the work to
> do to specify how our mobile implementation of WebDriver should work.
> That is available among the subprojects. If you just go to the
> Selenium Google.Code.Com and take a look at the source code you can
> find that.   

> \"Ultimately that work will probably lead to a specification, but that
> is somewhere down the track. That\'s the main thing we are doing as a
> project for mobile. That is because the mobile implementations are
> hosted by Appium, by Selendriod, and IOS Driver and Blackberry. These
> guys have more time or energy and more enthusiasm for solving the
> problems of the particular platforms they are targeting rather than
> the Selenium Project which tends to do a lot of desktop stuff. 

> \"Now this doesn\'t mean we aren\'t interested in mobile, it just
> means we think that those guys are adding all the value we would want
> to be adding ourselves and going in there and stealing their thunder
> and going, \'Now, and the OFFICIAL way of doing Android is THIS way\'
> isn\'t helping anyone. We want to grow a community. We want to grow a
> suite of related sister projects who get along well and where it is
> possible to flip an implementation if it is not quite right\". 

\
Julian Harty added that Chrome now works on KitKat, version 4.4 of the
Android operating system. FireFox has some plans for mobile as well. The
mobile browser people also have an opportunity to add those
implementations.\
\
Andreas Tolfsen mentioned that Mozilla is in the early stages of having
[Marionette](https://developer.mozilla.org/en-US/docs/Mozilla/QA/Marionette)
working on real devices\
\
You can check out information about the Marionette project, their
version of the Selenium project, but on mobile devices, at the Mozilla
Developer Network at
https://developer.mozilla.org/en-US/docs/Mozilla/QA/Marionette\
\
The Selenium Project also has been attempting to submit their WebDriver
spec to W3C (World Wide Web Consortium). The Level 1 spec is not desktop
specific. Once that is accepted, then they were thinking of adding
extensions to the spec for things like receiving notifications,
geotagging and managing a full screen, but first they need to get the
initial spec accepted.\
\
Because the Selenium Project is an open source project and everyone
works for different companies which may have different priorities, they
don\'t have an official roadmap.\
\

#### Lightning Round

The panel was asked a series of questions and were told they should try
to answer the questions in a word or two. My favorite questions and
their responses were:\
\

#### Q) What is a common question you wish people would stop asking you?

\
Simon Stewart: \'When?\'\
\
Jim Evans: \'Can I have status codes please?\'\
\
Andreas Tolfsen: \'Selenium IDE? Can I use it?\'\
\
Dima Kovalenko: \'Can you help me write a bot that will play with money
at this casino website? \'\
\
Julian Harty: \'Can you fix my problem? Full stop\'.\
\

#### Q) What is the worst idea anyone ever suggested on the Selenium project?

\
Simon Stewart: The worst idea?! \... \'Just one more drink\'.\
\
Jim Evans: \'Http status codes?\'\
\
Andreas Tolfsen: Replacing the entire WebDriver API with something
that\'s modelled in Object oriented format DOM.\
\
Dima Kovalenko: \'We need to test on IE 5\'.\
\
Julian Harty: \'Can you just help with the Python bindings?\' in 2007.\
\

#### Q) What is your favorite programming language?

\
Simon Stewart: It depends\... Java with a good IDE or English.\
\
Jim Evans: I should go really nerdy and say Fortran or COBOL\... but,
no, I am a big fan of C\# actually.\
\
Andreas Tolfsen: I believe in the right tool for the right job, but if I
had to pick today, I think it\'s probably Go. \-- I should say RUST
because I work for Mozilla. But not really. Shhh!\
\
Dima Kovalenko: Toss up between Visual Basic and Power Shell? No? Uh,
just shell bash script. Never understimate what you can accomplish with
a simple bash script.\
\
Julian Harty: I can write some Java so I will say Java.\
\
Santiago Suarez Ordoñez: I will NOT say Java\... Python!\
\

#### Q) What do you hate about Selenium? 

\
Simon Stewart: I thought I\'d be done by early 2008. It seems to be
dragging on a bit.\
\
Jim Evans: I hate feeling like I am not doing a good enough job. (Simon
asked Jim, \"Do you need a hug?\" \"Not at the moment, but I will take a
raincheck\")\
\
Dima Kovalenko (joking): I will jump in and say \'The Bearded One\'
\[Simon\]\
\
Julian Harty: Not contributing enough, really. Love to do more.\
\
Dima Kovalenko added: Let me change it! The fact that companies that
will spend \$17,000 for a professional tool per computer are not
donating the money to the project instead.\
\

### Other tidbits:

\
If you have problems with attempting to run automation tests with Opera,
the fault doesn\'t lie with the Selenium Project. Opera switched their
rendering engine from their own one to the one by Chromium called
\"Blink\", and when they did that it was a step back in how easy it was
to automate Opera. Opera is fixing it.\
\
With Safari\'s driver, it is a plug-in extension to Safari, a flawed
approach. Once the Selenium spec gets accepted by the W3C, they are
hoping that Apple does their own implementation.\
\
-T.J. Maher\
* Sr. QA Engineer*\
* Quincy, MA*

</div>
