\-\-- layout: post title: Getting to Know GitLab and How They Test the
UI date: \'2018-03-17T17:55:00.004-04:00\' author: T.J. Maher tags: -
GitLab - Capybara - Gauge - Ruby modified\_time:
\'2018-03-17T17:56:45.754-04:00\' thumbnail:
https://i.ytimg.com/vi/rj0QrccYqGw/default.jpg blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-7350903387267348382
blogger\_orig\_url:
http://www.tjmaher.com/2018/03/getting-to-know-gitlab-and-how-they.html
\-\-- The past three years as an automation developer, I have worked
with many different continuous integration platforms such as Jenkins,
TeamCity, and CircleCI, hooking up my automation to it so the tests can
be run once an hour, nightly, or every single time is checked in.\
\
[Threat Stack](httpp://gitlab.com) uses [GitLab](http://gitlab.com/) for
its Continuous Integration / Continuous Deployment (CI / CD) pipeline.
Why? You should ask [Pete Cheslock](https://pete.wtf/), head of DevOps.
He is currently writing about his experience in our company blog:\

-   [How Threat Stack Does DevOps (Part I): Best Practices in the
    Wild](https://www.threatstack.com/blog/how-threat-stack-does-devops-part-i-best-practices-in-the-wild/)
    (March 14, 2018)
-   [How Threat Stack Does DevOps (Part II): Engineering for Rapid
    Change](https://www.threatstack.com/blog/how-threat-stack-does-devops-part-ii-engineering-for-rapid-change/)
    (March 16, 2018)

<div>

With GitLab, I am more concerned with finding out what it does in
general. Lucky for me, they give YouTube tours such as this one shot
back in November 2017, [Idea to Production with
GitLabs](https://youtu.be/rj0QrccYqGw).\
\

\
This video gives you a good idea of using GitLab to do issue tracking,
planning, committing to the repo, testing with CI, debugging in the
terminal, deploying to production, scaling an application and
application performance monitoring.\
\

The History of GitLab
---------------------

According to <https://about.gitlab.com/history/>\
\
\"**2011:** Our CTO Dmitriy needed an great tool to collaborate with his
team. He wanted something efficient and enjoyable so he could focus on
his work, not the tools. He created GitLab from his house in Ukraine. It
was a house without running water but Dmitriy perceived not having a
great collaboration tool as a bigger problem than his daily trip to the
communal well. \[\...\] So together with Valery, he started to build
GitLab as a solution for this. [This
commit](https://gitlab.com/gitlab-org/gitlab-ce/commit/9ba1224867665844b117fa037e1465bb706b3685)
was the very start of GitLab.

</div>

<div>

\"**2012**: GitLab.com: Sid saw GitLab for the first time and thought it
was natural that a collaboration tool for programmers was an open source
so you could contribute to it. Being a Ruby programmer he checked out
the source code and was impressed with the code quality of GitLab after
more than 300 contributions in the first year. He [asked Hacker
News](https://news.ycombinator.com/item?id=4428278) if they were
interested in using GitLab.com and hundreds of people signed up for the
beta. In November 2012, Dmitriy made the [first version of GitLab
CI](https://gitlab.com/gitlab-org/gitlab-ci/commit/52cd500ee64a4a82b9ff6752ee85028cd419fcbe)\".\
\

Wait a Second\... GitLab Uses Ruby?
-----------------------------------

Oh, that is interesting! GitLab is coded using Ruby! The Test
Engineering  team picked the Ruby language for its automation framework
because Chef and Test Kitchen use Ruby. As a Ruby Newbie, I have been
finding it helpful to review the great work the
[Gauge.org](http://gauge.org/) people have done creating examples [using
their BDD framework with
Capybara](https://github.com/getgauge-examples/gauge-example-ruby).\
\
What I find more fortunate is that it appears that GitLab uses for its
UI tests what I am attempting to use: Capybara + Ruby + Headless
Chrome.\
\
I need to check out [Mike
Greiling](https://about.gitlab.com/team/#mikegreiling)\'s article,
\"[How GitLab switched to Headless Chrome for
testing](https://about.gitlab.com/2017/12/19/moving-to-headless-chrome/)**:
A detailed explanation with examples of how GitLab made the switch to
headless Chrome**\".\
\
As Mike put it, last year, \"[news
spread](https://news.ycombinator.com/item?id=14101233) that Chrome 59
would support a [native, cross-platform headless
mode](https://www.chromestatus.com/features/5678767817097216). It was
previously possible to simulate a headless Chrome browser in CI/CD
[using virtual frame
buffer](https://gist.github.com/addyosmani/5336747), but this required a
lot of memory and extra complexities. A native headless mode is a game
changer. It is now possible to run integration tests in a headless
environment on a real, modern web browser that our users actually use!\
\
\"Soon after this was revealed, Vitaly Slobodin, PhantomJS\'s chief
developer, announced that the project [would no longer be
maintained](https://github.com/ariya/phantomjs/issues/15105#issuecomment-322850178)\".\
\
And all of the source code for [GitLab\'s Community Edition is stored on
GitLab](https://gitlab.com/gitlab-org/gitlab-ce/). Awesome!\
\
At my job there are so many things that are new to me:\
\

-   I am new to Gauge.org
-   I am new to Ruby
-   I am new to Capybara
-   I am new to GitLab
-   I am new to Headless Chrome. 

<div>

\... For the last week, since I was placed on Threat Stack\'s UI team,
I\'ve written a few UI tests, but they all run locally, on my own
computer, but I was stumped when it came to using CI with GitLab. I\'ve
been searching for a model to base my new framework on.

</div>

<div>

\

</div>

<div>

Looks like I found one. This should be fun! 

</div>

\
\
Happy Testing!\
\
-T.J. Maher\
Sr. QA Engineer, Software Engineer in Test\
Meetup Organizer, [Ministry of Testing -
Boston](http://bit.ly/mot_boston)\
\
[Twitter](https://twitter.com/tjmaher1) \|
[YouTube](http://bit.ly/tj_youtube)
\| [LinkedIn](https://www.linkedin.com/in/tjmaher1) \|
[Articles](http://bit.ly/tj_techbeacon)

</div>
