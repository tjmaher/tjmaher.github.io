\-\-- layout: post title: \'DevOps and Dynatrace: Notes from the March
7th Lean Coffee, Ministry of Testing-Boston\' date:
\'2017-03-08T08:38:00.000-05:00\' author: T.J. Maher tags:
modified\_time: \'2017-03-08T08:38:06.257-05:00\' thumbnail:
https://i.ytimg.com/vi/zr\_kfm4D\_bA/default.jpg blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-2640777374282516491
blogger\_orig\_url:
http://www.tjmaher.com/2017/03/devops-and-dynatrace-notes-from-march.html
\-\-- Last night, the new software testing group, the Ministry of
Testing - Boston Meetup, hosted its [second Lean Coffee
Meetup](https://www.meetup.com/ministry-of-testing-boston/events/237592529/) at
the Panera Bread in Porter Square, Cambridge, MA. We switched locations
from [February\'s Lean
Coffee](http://www.tjmaher.com/2017/02/software-testing-lean-coffee-john.html),
going from a reserved section of a noisy brewpub to a
coffee-and-sandwich shop where it was nerve-wracking for me to attempt
holding enough tables for all of the attendees. For April\'s Lean
Coffee, I\'ll make a reservation back at John Harvard\'s.\
\
Going from beer to coffee seemed to be less of a draw, which seemed to
work in the group\'s favor. After the first ten minutes of free-flowing
conversation between us four, we voted to eschew the usual Lean Coffee
ceremony of writing discussion topics on Post-It notes, then voting on
the priority and how many minutes we as a group should discuss a topic.
We were all having too much fun just talking!\
\
One of the attendees, [Andreas
Grabner](https://www.linkedin.com/in/grabnerandi/), a Technology
Strategist at [Dynatrace](https://www.dynatrace.com/), stopped in after
meeting with some clients. Poor guy! What was meant to be a Lean Coffee
turned into our own personal Dynatrace Q & A session, with us peppering
him with questions for two full hours, interrogating him about their
software development process, their automation process, and everything
in between.\
\
For those who missed last night, you can see Andreas speak tonight!
Andreas will be giving a talk at the **Boston Jenkins Area Meetup**  on
\"[**Metric Driven DevOps with
Jenkins**](https://www.meetup.com/Boston-Jenkins-Area-Meetup/events/236896653/)\".\
\
\

Of all the things Andreas said, the most shocking thing was this:
Dynatrace did away with a separate tester role at their company.\
\
As I said to him, \"That statement just sent chills up my spine! \... So
you have just developers do the testing?\"\
\
Yes. Everything is automated. It did take a big culture shift. They
spent years re-organizing the company. When you shift testers into more
of a developer role, it can help them both. Coders taught testers how to
code and testers taught coders how to write better tests.\
\
I had to interrupt: \"But who catches things such as typos? Bad
graphics? Wrong copy uploaded? Not everything can be automated\".
Andreas mentioned that it is the customer that catches them.\
\
Andreas went on to explain that Dynatrace spent incredible amounts of
brainpower how to automate everything: Not just the code deployments,
but the delivery mechanism itself. Developers could deploy whenever they
wanted. But since changes went straight into production, it forced them
to take ownership of production. They had to make sure not just that
they didn\'t break the build, but also that they weren\'t pushing errors
into Production, because the customers would see it. Dynatrace forced
developers to interact directly with their customers, which forced them
to become more responsive to the customer.\
\
A funny thing happened. Without any filter between developers and the
customer, it made the developer more in tune to the customer\'s needs.
Yes, they heard negative feedback, as they always had, but it also
allowed them to hear positive feedback from the customers using the
product. When they fixed issues promptly due to the fast feedback, or
put in a new piece of functionality that customers liked, they heard
about it, unfiltered.\
\
I\'ll share more of Andreas\' insights in the next blog post. In the
meantime, check out the talk Andreas gave last August at DevOpsDays
Boston 2016! ( [Official
site](https://www.devopsdays.org/events/2016-boston/welcome/) ).\
**\
[Andreas Grabner](https://www.linkedin.com/in/grabnerandi/) gives his
talk to DevOpsDays Boston 2016**\

*\"How can we detect a bad deployment before it hits production? By
automatically looking at the right architectural metrics in your CI/CD
and stop a build before its too late. Lets hook up your test automation
with app metrics and use them as quality gates to stop bad builds
early!\"*

<div>

*\
*

</div>

<div>

*\
*\
Happy Testing!\
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

</div>
