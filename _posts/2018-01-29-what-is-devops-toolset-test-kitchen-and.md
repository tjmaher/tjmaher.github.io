\-\-- layout: post title: What Is the DevOps toolset \"Test Kitchen\"
and Where Did It Come Come from? Fletcher Nicol at ChefConf 2014 date:
\'2018-01-29T07:00:00.000-05:00\' author: T.J. Maher tags: - Chef -
DevOps - KitchenCI modified\_time: \'2018-01-29T07:46:27.468-05:00\'
thumbnail: https://i.ytimg.com/vi/YzlCHAbJ7KM/default.jpg blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-3175927972127537554
blogger\_orig\_url:
http://www.tjmaher.com/2018/01/what-is-devops-toolset-test-kitchen-and.html
\-\-- When learning and investigating a new open-source tool or
technology, I find YouTube to be an amazing resource!\
\
Beyond the many tutorials, presentations, and instructional videos, I
try to see how the creators of the tool introduces and talks about it to
the open-source community. What was the creator trying to achieve? What
problem was to be solved? And, most importantly, how can I take the
creator\'s message and transfer it to the work that I am doing?\
\
Right now, I\'m trying to get up to speed on **Test Kitchen**
\< [kitchen.ci](http://kitchen.ci/), 
[\@kitchenci](https://twitter.com/kitchenci) []{#goog_1725328508}[](https://draft.blogger.com/)[]{#goog_1725328509}\>,
the product we use at work, combined with [Chef.io](http://chef.io/), to
automate spinning up and tearing down different Amazon Web Services
environments.\
\
With the \"[Learning Chef Rally](https://learn.chef.io/#/)\", it is
going to take me a few weeks to finally get to the part I need, learning
exactly how the DevOps tool spins up environments, so I was also seeking
alternate sources to tide me over.\
\
Luckily, I found this, introduced at ChefConf 2104, a conference about
Chef\...\
\
**\#ChefConf 2014: Fletcher Nichol, \"Test Kitchen: One Year Later and
the Future**\

<div>

*Fletcher Nicol, 2014*\

\
[*https://youtu.be/YzlCHAbJ7KM*](https://youtu.be/YzlCHAbJ7KM)\
\
[]{#more}\
\
\"After one year of active development and real world use, Test Kitchen
1.0 was released on December 1, 2013. And this is only the beginning. In
this session we will cover an introduction to Test Kitchen, its
ecosystem, some common (and crazy) usage patterns in the wild, and ways
to extend and bend the framework to your will. If you want a good
insight into where Test Kitchen is going, then this talk is for you\".\
\
According to Fletcher, Test Kitchen is \"a test harness tool to execute
your configured code on one or more platforms in isolation\". It helps
you run Chef code in isolation. 

</div>

<div>

\

</div>

<div>

**Initial Goals for Test Kitchen 1.0: **

</div>

<div>

-   Simple workflow. 
-   Declarative static configuration, so they went with a YAML file
    instead of the Ruby code that sets it up. They didn\'t want
    programming, necessarily to do set up. ( [Care to read way too much
    on what a YAML file is?](https://learn.getgrav.org/advanced/yaml) )
-   Speed in development
-   Optimizes for freshness of code, such as deleting Chef code and
    re-installing it so that there aren\'t any caching problems. 

<div>

\"Kitchen converges with provisioners and runs specific suites on target
platforms called instances using drivers\". 

</div>

</div>

<div>

-   **Platform**: Operating system or target environment. 
-   **Suite**: A Chef configuration, a run-list and node attributes
-   **Instance**: A platform + suite with auto-generated name
-   **Driver**: Implementation of instance actions: create, converge,
    setup, verify, destroy. Need one? Write one! They are Ruby Gem
    plugins. 
-   **Provisioner**: Implementation of infrastructure automation tool or
    framework. Runs your Chef code. Yes, you can write one\... but in
    2014 Fletcher was not quite sure if you should yet.
-   **Busser**: A Ruby gem, prepares instances for test suites and runs
    them. 

</div>

<div>

Fletcher pointed to the **Kitchen.ci Getting Started
guide**: [https://kitchen.ci/docs/getting-startedhttps://kitchen.ci/docs/getting-started](https://kitchen.ci/docs/getting-started).
Currently it walks people through Installing, Creating a Cookbook, the
.kitchen.yml, writing a recipe, manually verifying it, writing a test,
adding a platform, adding a feature, adding a suite, a test, adding
a recipe, etc. 

</div>

<div>

\

</div>

<div>

He also talked about Usage Patterns:

</div>

<div>

-   Detangling cookbook dependencies. For example, when you run recipes
    by themselves, you might find that a cookbook runs fine on one Linux
    distribution but not on another. Java never was explicitly
    installed, so code on CentOS did not run. 
-   Test Chef upgrades: Test to see if your stuff still works. You can
    test different versions of Chef Omnibus. 

<div>

Tip:

</div>

</div>

<div>

-   Don\'t type out very long instance names. There is **fuzzy
    matching**, so you can do \"kitchen destroy\". It will either follow
    the exact name, the regular expression. No parameter? It will
    destroy all. \"kitchen list all\" and \"kitchen list\" is the same
    command. How does this work? It is being passed in as a Ruby regular
    expression. 

<div>

Biggest takeaway, Fletcher was excited about back in 2014? 

</div>

</div>

<div>

-   **kitchen diagnose**: \"Originally used for support. It makes all
    implicit configuration explicit. Kitchen gives you a shopping list
    of configuration tunables that you can mess with\". If you find
    yourself in YAML Hell, not sure what is being loaded, use this
    command. 
-   kitchen diagnose \--loader

</div>

<div>

Fletcher also mentioned the **Chef Zero Provisioner**, written by John
Keiser, \"the fakest Chef server ever\". Runs in Ruby, spins up quickly,
and is great for testing! There is also the chef\_zero, the fakest
chef-client run. It supports \"data bags encrypted secrets,
environments, nodes & clients\".

</div>

<div>

\

</div>

<div>

That\'s it for now! Happy Testing!\
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
