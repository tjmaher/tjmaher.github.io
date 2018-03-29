\-\-- layout: post title: Introduction to the Learn Chef Rally! date:
\'2018-01-31T06:53:00.001-05:00\' author: T.J. Maher tags: - Chef -
DevOps - KitchenCI modified\_time: \'2018-01-31T06:53:54.486-05:00\'
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-3640640334483692907
blogger\_orig\_url:
http://www.tjmaher.com/2018/01/introduction-to-learn-chef-rally.html
\-\-- Need to automate configurations for Amazon Web Services? One way
to do it is with [Chef.io](http://chef.io/).\
\
Chef does the \"cooking\" metaphor to the hilt! Configurations are
\"recipes\", written in the Ruby programming language, which are stored
in a \"cookbook\". We covered this in early January with [The Ruby
Behind Chef](http://www.tjmaher.com/2018/01/the-ruby-behind-chef.html).\
\
This metaphor continues: To automate all of this, you use the product
\"Test Kitchen\".\
\
Seems complicated? To help you out, Chef create the most amazing set of
documentation I have ever seen: The **Learn Chef Rally**.\
\
From [Getting Started With Chef in
Learn.Chef.io](https://learn.chef.io/modules/getting-started-with-lcr#/):\
\
\"If you\'re new to Chef, just know that Chef lets you automate all the
things---infrastructure, applications, compliance and more. Learn Chef
Rally will teach you how. It\'s the hub for Chef and DevOps related
resources that will build your skills.\
\
\"The Learn Chef Rally curriculum is organized by tracks. A track groups
related learning activities.\
\
\"We call each learning activity a module. Modules include a mix of
hands-on labs, articles, and videos. Our hands-on labs help you get
started quickly on the platform that you care about most.\
\
\"When you finish a module, you\'ll see a few quiz questions at the end.
Answering these questions correctly gives you credit for having
completed the module. You can track your progress on the home page\".\
\
Since my job will be automating Amazon Web Service tests, spinning up
and tearing down environments, I\'m starting the module on [Test
Kitchen](https://kitchen.ci/): \"Infrastructure Code Deserves Tests
Too\".\
\
[]{#more}\
\
\

What is Kitchen?
----------------

In the last blog entry, \"What Is the DevOps toolset \"Test Kitchen\"
and Where Did It Come Come from? Fletcher Nicol at ChefConf 2014\" we
covered a bit about the DevOps tool Test Kitchen.\
\
\"Kitchen provides a test harness to execute infrastructure code on one
or more platforms in isolation.\
\
\"A driver plugin architecture is used to run code on various cloud
providers and virtualization technologies such as Vagrant, Amazon EC2,
and Docker. [Read more](https://kitchen.ci/docs/drivers)\
\
\"Many testing frameworks are supported out of the box including
[InSpec](https://www.inspec.io/), [Serverspec](https://serverspec.org/),
and [Bats](https://github.com/sstephenson/bats)\
\
\"For Chef workflows, cookbook dependency resolution via
[Berkshelf](https://docs.chef.io/berkshelf.html/) or
[Policyfiles](https://docs.chef.io/config_rb_policyfile.html) is
supported or include a cookbooks/ directory and Kitchen will know what
to do.\
\
\"Kitchen is used by all [Chef-managed community
cookbooks](https://kitchen.ci/github.com/chef-cookbooks/) and is the
integration testing tool of choice for cookbooks\".\
\
All of this is taught in the **Learn Chef Rally** track, [Infrastructure
Automation](https://learn.chef.io/tracks/infrastructure-automation#/),
which consists of four modules:\
\
1) **[Learn the Chef
Basics](https://learn.chef.io/modules/learn-the-basics):** \"Get started
by using Chef to keep your servers in line with the configuration
policies you describe. You\'ll set up a web server and serve a basic
home page on your own virtual machine or one that we provide\".\
\
2) **[Manage a node with Chef
server](https://learn.chef.io/modules/manage-a-node-chef-server)**:
\"Learn how the Chef server acts as a central repository for your
cookbooks and for information about your servers, or nodes\".\

<div>

\
3) [**Get Started With Test
Kitchen**](https://learn.chef.io/modules/local-development): Learn how
to speed up the development process by using Test Kitchen to apply your
infrastructure code from your workstation.\
\
4) [**Go Beyond the
Basics**](https://learn.chef.io/modules/beyond-the-basics): Learn what
happens behind the scenes when chef-client runs.\
\
\... I cannot believe how well organized this all is! 

</div>

<div>

\

</div>

<div>

Other tracks I am also interested in:

</div>

<div>

-   [Chef on AWS](https://learn.chef.io/tracks/chef-on-aws#/): \"Looking
    for AWS on the menu? Place your order here and you\'ll get a hang
    for the Chef basics, manage your first node, test Chef cookbooks on
    temporary cloud instances, and deploy changes to a production-like
    environment, all on AWS\".
-   [Continuous Automation with Chef
    Automate](https://learn.chef.io/tracks/continuous-automation#/):
    \"Hungry for continuous automation? Satisfy your appetite with Chef
    Automate, the platform for continuous development, and learn how it
    can provide visibility into your infrastructure. Also discover how
    to deploy a cookbook using the Chef Automate pipeline\". 

\
This looks quite interesting! I think I have everything I need to keep
me busy the next couple of months!\
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
