\-\-- layout: post title: \'SeConf2014: Fish Bowl with the Selenium
Committers \' date: \'2015-02-18T22:59:00.000-05:00\' author: T.J. Maher
tags: - conference - Jim Evans - WebDriver - Simon Stewart
modified\_time: \'2016-04-29T16:19:35.505-04:00\' thumbnail:
https://i.ytimg.com/vi/Rh4s6kqOCmc/default.jpg blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-6390704732816639051
blogger\_orig\_url:
http://www.tjmaher.com/2015/02/seconf2014-fish-bowl-with-selenium.html
\-\-- *Did you know that by going to the [Official 2014 Selenium
Conference Site](http://www.seleniumconf.org/2014/index.html) and
selecting the [Program
Schedule](http://confengine.com/selenium-conf-2014/schedule) you can
pull up all the slides, handouts, and video recordings of all the talks
given at the conference which was held back in September 2014 in
Bangalore, India? For the next few blog posts, I will be publishing my
notes on a few of these YouTube captured talks.  *\

<div>

*\
*

</div>

<div>

\
[]{#more}*\
*

</div>

\

\
With this \"Fish Bowl\" discussion, chairs are not just for panelists
\-- they are for the audience members, too! Have a better answer to an
audience question than a panelist? Take the stage and answer the
question.\
\
\
\
The panel consisted of:\
\
\

-   Santiago Suarez Ordoñez, at Sauce Labs. 
-   Dima Kovalenko, from Groupon 
-   Jim Evans, from Salesforce
-   Simon Stewart, creator of WebDriver and lead on the Selenium
    Project, from Facebook. 
-   Julian Harty, testing and documenting Selenium, working at eBay. 

\
Here are a few questions asked during the session and their respective
answers:\
\

#### Q) Why can\'t you run Selenium on an already open browser?

<div>

\

</div>

A\) Jim Evans answered that the reason that it\'s not possible currently
to attach to a running browser instance is that the WebDriver library
has to communicate with a browser somehow. That communication channel is
some sort of TCP/IP port, and the only way you can instruct the browser
to listen on that port is when you launch the browser.\
\
The browser, by itself, doesn\'t have the ability just to listen on
command to the TCP/IP port. With Firefox, we need a profile to do that.
With Chrome, there is a command line switch that the Chrome driver adds
to Chrome to start listening on a port. Jim continued,\
\

> \"Interestingly, with Internet Explorer there is a possibility that
> you -could- in theory connect to an existing browser. I have been
> reluctant to add something like that specifically \-- that is IE
> specific \-- because I believe that our API is and should continue to
> be cross-platform\". 

\
Simon Stewart added,\

> \"So, there is, however, a really easy way to solve this problem,
> which is to not solve it. 

> \"If you put the life cycle of the browser under the control of
> Selenium, like if you start the browser that you are going to use for
> the manual section with WebDriver, then you already have that
> connection up and running. And when you hit the end and it\'s like
> \'Ah! Now I need to be able to poke around in a browser controller\'
> because you have already started a browser session you will be able to
> do that.

> \"If you are using the Selenium Server or something like that you
> could probably use, like, Python to give you a REPL \[
> *read--eval--print loop, language shell - TJ *\] or even Ruby, right?
> \[\...\] You don\'t need to code everything up. You can have a
> completely interactive session\... and that might save you a lot of
> time and effort\... and you could do it today\... and it would work
> for all browsers\".   

\

#### Q) What is your plans for HTML 5 with respect to Selenium WebDriver?

\
A) Simon Stewart mentioned HTML 5 is big beast, composed of a bunch of
moving pieces. CSS3 probably hooks in there \"as well and the 3D
transforms and the horror that that entails\". He continued,\
\

> \"Let\'s break it down into the various bits and pieces: 

> \"HTML 5 is an evolution of the HTML standards, is presented in the
> browsers\... it\'s still got the DOM \[*Document Object Model*\].
> WebDriver will continue to work with those things.  

> \"Then next thing we will probably come across is the fact that it\'s
> got new form elements that people use. We have in the standards \--
> we\'ve had several discussions on how to handle those and we just \--
> \'just\' \-- need to write some new utility standards to make that
> work the way we want it to. But effectively each of the new HTML form
> elements has a sort of string serialization that it sends across the
> wire and we will make it easy so if you do \'SendKeys\' with that
> string serialization the correct thing will happen in the HTML 5 form
> element\".

\

#### Q) Can you talk about the driver implementation for Safari? 

\
They mentioned that a lot of the problems with the Safari driver and how
it doesn\'t work like the others was basically because it was a hack in
Javascript. The driver for Safari doesn\'t really have internal control
of the browser, and can\'t do anything the browser registers as being
insecure, such as the Alert API. If an alert pops up, things just stop.
This is why they are working on the spec to be submitted to the W3C, so
Apple can step up and give the Selenium project their own implementation
of the driver.\
\

#### Q)  Do you have a relationship with the Safari team?

\
When this question was asked, Simon Stewart visibly sighed. He then
explained that Google (who does the Chrome driver) and Mozilla (who does
Firefox) has a very open culture. They are willing and able to
communicate and participate with an open source project such as the
Selenium project. Simon explained:\
\

> \"Microsoft \[has\] over the years has become more and more open and
> are able \-- they come to face-to-face meetings, they discuss things
> with us. They are writing their own implementation \-- which is
> brilliant. They have a corporate culture that is concerned about open
> source for reasons that they\'re worried about, y\'know, if some of it
> gets in and the viral nature of the GBL what happens to their crown
> jewels so they are quite sensibly protecting things in the best way
> \-- the best way they believe is possible.     

> \"The corporate culture of Apple is, ah, a more closed one. You know,
> Apple famously \[doesn\'t\] leak very well. They are a company that
> leaks come from the top. \[\...\] The lower levels in the engineering
> levels of Apple are incredibly disciplined about maintaining the
> strictures they have with their corporate NDAs \[Non-Disclosure
> Agreements\]. So, we talk to the Apple Team, \[\...\] we communicate
> with them, but the culture of the company isn\'t one where they will
> come out and say to us, \"Oh, by the way, we are doing this\'.  

> \"We are following the steps that we are meant to do in order to do
> the right things \[\...\] That\'s just the way the company is, I am
> not saying anything good or bad about them. I think that\'s the way
> their company works. 

> \"My expectation is that Apple \[is\] a company that does a good job
> with standards implementation like Safari \... knocked it out of the
> park when it came out! It was like, Opera had a fantastic standards
> implementation WebKit came out and also did an excellent job. And, you
> know, they are Unix-compliant in OS X, that so they understand
> standards and the importance of it and my expectation and hope is that
> when we get the standard out \-- the specification \-- then there will
> be that concrete thing which allows Apple to participate in the
> browser automation community that I don\'t think we have enabled them
> to do\".   

\

#### Q) \[To Simon\] Can you share with us the Selenium landscape at Facebook? What kind of tests, how many tests do you run?

\
Simon Stewart mentioned that Facebook, where he is a software engineer,
he does not do browser automation. He works on their build tool. He did
set up the end-to-end testing for their mobile IOS and Android product,
but he rolled off that project a year to fourteen months after he first
joined Facebook and he is now (as of September 2014, the recording of
the talk) working on the build tool team. Simon added,\

> \"By the way, the build tool is \'buck\', B-U-C-K, which is open
> source and is on GitHub. It\'s like a next generation build tool. If
> you build any Java, take a look at it. It is blazingly fast\... I will
> stop advertising things now\". \[ [Official
> Site](http://facebook.github.io/buck/), [GitHub
> code](https://github.com/facebook/buck) \]

\

#### Q) What are some challenges do you face working with Selenium?

> *Simon Stewart*: \"For me, Paul Hammond had it right when he called me
> insane \... when I started down the path of tightly integrating with
> the browser instead of doing the JavaScript thing that Selenium RC
> \[\...\] did. And he was entirely and completely correct that it was
> an absolutely bonkers thing to do \-- to have done, and if I had
> realized how hard it was I wouldn\'t have started. But I was young and
> foolish \... and did it anyway\".\
> Jim Evans: \"Big challenge? \[\...\] I think, for me, probably the
> biggest challenge wasn\'t a technical one for me. The biggest
> challenge was simply\... was social on my part, just getting over the
> hump of thinking \'Wow, can I really do this\', am I able, do I have
> the ability to do the things that needed to be done in the project
> \[\...\] and that to me is something that was a real challenge for me
> to overcome to just dig in and do it and start, and if I wasn\'t up to
> it, I wasn\'t up to it\".\
> \
> *Santiago Suarez Ordoñez*: \"I think for me would be \... it was how
> extensive the code base is? Definitely challenging. Every once in a
> while you have to get reminded of the structure of where things are
> and the fact there are \-- six clients? Seven clients? Every code
> change you want to do you have to apply it\... if you go to clients
> \-- seven clients \-- you have to talk to seven people who own them
> and push them through a huge immense crowd of people who will be
> testing them. So, it\'s a big challenge, for sure\".\
> \
> *Dima Kovalenko*: \"For me, it\'s pretty much the same story every
> time you get on a new project that has a Selenium build inside of a
> build tool. And the fact that Selenium build is always the last one to
> run and there is 90% red because there are one or two tests that
> constantly flake out for whatever reason and so it\'s easy to think
> about this as a technical problem how  we need to stabilaize the
> build\... we need to  put these Ajax things in \[\...\]. But in fact,
> a majority of the testability seems to be a cultural problem where the
> developers or the team \-- the QA team \-- whoever \-- do not really
> respect the Selenium build enough to actively maintain it. And so,
> having to convince the whole team, \'Hey guys, this is important.
> It\'s a first class citizen in the build queue\' and once you move it
> up and once it is no longer the last thing that runs and nobody cares
> about and get it to run every single build and then convince the team
> to help you out and root out all the little flakiness and everything
> \... and once you get to a point where it is 99% green \... it takes a
> year or two to complete that cultural shift but once that happens
> it\'s quite an amazing result where the Selenium build fails and
> several developers completely just jump up and freak out \'Whoah,
> whoah! What did I do wrong? What did I do wrong?\' instead of \'Eh! It
> screwed up\' \".

\
\
\
-T.J. Maher\
* Sr. QA Engineer*\
* Quincy, MA*