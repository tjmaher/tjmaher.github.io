\-\-- layout: post title: \'This week at work: The hard part of learning
Nightwatch.js\' date: \'2016-12-15T12:20:00.001-05:00\' author: T.J.
Maher tags: modified\_time: \'2016-12-15T12:21:47.444-05:00\'
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-7167614799253013343
blogger\_orig\_url:
http://www.tjmaher.com/2016/12/this-week-at-work-hard-part-of-learning.html
\-\-- This week, at work, I\'ve been attempting to compose a new
end-to-end test using libraries that other coders at my workplace have
written.\
\
It\'s a simple test: When you process a patient using Component A, and
register them using Component B, in the database you should see status
code C.\
\
A + B = C.\
\
Lucky for me, another developer already wrote libraries of Nightwatch.Js
tests for Component A and Component B. I am just making logical
assumptions on what parts I need and glueing them together, hoping it
all works out. Then, I\'m using the PostgeSQL library that Node.js
provides to get the status code C that I need.\
\
Sometimes, it doesn\'t all work out.\

> ::: {dir="ltr" lang="en"}
> Hard part reading other\'s
> [\@NightwatchJs](https://twitter.com/nightwatchjs): Which is vanilla
> [\#JavaScript](https://twitter.com/hashtag/JavaScript?src=hash)?
> [\#ES6](https://twitter.com/hashtag/ES6?src=hash)?
> [\@NodeJs](https://twitter.com/nodejs)?
> [\#MochaJs](https://twitter.com/hashtag/MochaJs?src=hash)? Third party
> [\#postgreSQL](https://twitter.com/hashtag/postgreSQL?src=hash) or
> in-house library?
> :::
>
> --- T.J. Maher (\@tjmaher1) [December 15,
> 2016](https://twitter.com/tjmaher1/status/809438691030667266)

If something goes wrong, and I need to RTFM, which M should I look at to
increase my understanding of how the code works? Where is the code from?
Is it from:\
\

-   Basic Nightwatch: <http://nightwatchjs.org/guide>
-   The Mocha Test Runner: <https://mochajs.org/>
-   A Node.js library: <https://nodejs.org/en/docs/>
-   Vanilla
    JavaScript: <https://developer.mozilla.org/en-US/docs/Web/JavaScript>
-   ECMAScript2016 (or 2017): <https://tc39.github.io/ecma262/>
-   PostgreSQL: <https://www.postgresql.org/docs/>
-   Node.Js implementation of
    PostgreSQL: <https://www.npmjs.com/package/pg>
-   Or is it an in-house developer\'s library? 

\
Let me tell you, I am having the time of my life trying to figure our
how things fit together! :)\
\
My favorite thing has ***always*** been attempting to figure things out
by burying myself in independent research and taking a hella lot of
notes. And more notes equals more blog entries!\
\
When I come up for air in January, after this month\'s deep dive, expect
to see a lot more projects involving Nightwatch.js, an automated testing
solution geared towards Node.js projects.\
\
Until then, Happy Testing!\
\
\... Wow. I can\'t believe how happy I am at work, with my new position
as a Software Engineer in Test. Great company! Great co-workers! And a
really, really great job. Let\'s hope I can get up to speed quickly.\
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
