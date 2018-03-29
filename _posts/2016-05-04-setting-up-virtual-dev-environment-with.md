\-\-- layout: post title: Setting up a Virtual DEV Environment with
VirtualBox, Vagrant, and Docker date: \'2016-05-04T01:58:00.002-04:00\'
author: T.J. Maher tags: - VirtualBox - GIT - Docker - Vagrant
modified\_time: \'2016-05-04T02:06:25.066-04:00\' thumbnail:
https://1.bp.blogspot.com/-0n6CAk2Ybfo/VymPPoz4V7I/AAAAAAAAK\_E/PLNe6Hwm-IgOtpw-B8xDKqfoDRNBAb\_1gCLcB/s72-c/vm.png
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-6144044782324972934
blogger\_orig\_url:
http://www.tjmaher.com/2016/05/setting-up-virtual-dev-environment-with.html
\-\--

The Source Material: Test-Driven Java Development
-------------------------------------------------

\
We will be covering in this blog post setting up a virtual development
environment that has Ubuntu, Docker, and Mongo DB installed. We will
using VirtualBox and Vagrant to set up the virtual machine.\
\
Are most of the technologies I mention in the previous paragraph new to
you? Me, too! I\'m a software tester by trade, not a developer or a
SysOps guy. We\'ll just have to figure out this stuff together!\
\
As a guide, I purchased a copy of Viktor Farcic\'s [Test-Driven Java
Development](https://www.packtpub.com/application-development/test-driven-java-development),
printed by [PACKT Publishing](http://www.packtpub.com/). We will be
using **Chapter 2: Tools, Frameworks and Environments** as source
material.\
\
Since I am doing this on my system at home, I will be setting it up on
my Windows 10 machine. Feel free to use whatever operating system you
have at home.\
\
[]{#more}\
\

The Publisher: PACKT Publishing
-------------------------------

\
[PACKT Publishing](http://www.packtpub.com/) is a print-on-demand
publishing company based in India and the UK, focusing on tutorials for
Open Source technologies. When learning a new technology, sometimes I
just don\'t want to read off a computer screen; I want the information
pre-packaged, in a print copy or a nicely formatted e-Book. Be warned:
If you purchase one of their books: Source code is not guaranteed to be
100% correct, and the books have many typos in them\... Then again, I
find that if you are paying only ten or so dollars for a book, you
don\'t mind a few errors.\
\
I do especially like Packt\'s [Deal of the
Day](https://www.packtpub.com/books/deal-of-the-day). Each day they give
away a new eBook in PDF, ePub, Mobi, or Kindle format, free!\
\

The Authors: Farcic & Garcia
----------------------------

\
Viktor Farcic ( [\@vfarcic](https://twitter.com/vfarcic) \|
[Blog](https://technologyconversations.com/) ) is a Senior Consultant at
[CloudBees](https://www.cloudbees.com/) and a member of the [Docker
Captains](https://www.docker.com/community/docker-captains) group.\
\
Alex Garcia ( [LinkedIn](https://www.linkedin.com/in/alexgace) ) is a
Solutions Analyst for Everis, a management consulting company.\
\

Why set up a Virtual Development Environment?
---------------------------------------------

\
From Test-Driven Java Development:\

> \"By using this kind of procedure, we are able to reproduce a
> full-stack environment in the blink of an eye. You may be wondering if
> this is as awesome as it sounds. The answer is yes, it is. Vagrant and
> Docker allow developers to focus on what they are supposed to do and
> forget about complex installations and tricky configurations.
> Furthermore, we made an extra effort to provide you with all necessary
> steps and resources to reproduce and test all the code examples and
> demonstrations in this book\".

From [Intertech](https://twitter.com/intertechinc)\'s Blog, [Tips for a
Virtual Development
Environment](http://www.intertech.com/Blog/tips-for-a-virtual-development-environment/):\

> \"What value does setting up a virtual development environment
> provide?\
>
> -   \"**Fast Setup for New Developers**: On my project, we had a new
>     developer up and coding in a couple hours \[\...\]
> -   **Environment Consistency:** No more choices about where to
>     install software or what versions were being used. You can sit
>     down with any developer and things are where they should be.
>     (...for the most part)
> -   \"**Fast Recovery:** As developers, we like to play with stuff.
>     New tools, versions, configurations, etc. With a virtualized
>     environment, there is no risk anymore. You can try out things and
>     easily revert back to a good state, or start with the latest image
>     again\".

\

Tools and Technologies
----------------------

\
**VirtualBox:** According to
[Wikipedia](https://en.wikipedia.org/wiki/VirtualBox), \"Oracle VM
VirtualBox (formerly Sun VirtualBox, Sun xVM VirtualBox and Innotek
VirtualBox) is a free and open-source hypervisor for x86 computers from
Oracle Corporation. Developed initially by Innotek GmbH, it was acquired
by Sun Microsystems in 2008 which was in turn acquired by Oracle in 2010
\[\...\] VirtualBox may be installed on a number of host operating
systems, including: Linux, OS X, Windows, Solaris, and OpenSolaris
\[\...\] It supports the creation and management of guest virtual
machines running versions and derivations of Windows, Linux, BSD, OS/2,
Solaris, Haiku, OSx86 and others\".\
\
**Vagrant**: From [VagrantUp.com](https://www.vagrantup.com/about.html):
\"Vagrant is a tool for building complete development environments. With
an easy-to-use workflow and focus on automation, Vagrant lowers
development environment setup time, increases development/production
parity, and makes the \'works on my machine\' excuse a relic of the past
\[\...\] Vagrant was started in January 2010 by Mitchell Hashimoto. For
almost three years, Vagrant was a side-project for Mitchell, a project
that he worked on in his free hours after his full-time job. During this
time, Vagrant grew to be trusted and used by a range of individuals to
entire development teams in large companies \[\...\] In November 2012,
HashiCorp was formed by Mitchell to back the development of Vagrant
full-time. HashiCorp builds commercial additions and provides
professional support and training for Vagrant\".\
\
**Vagrant cachier**: A Vagrant plugin that reduces network usage and
speeds up local Vagrant-based provisioning, improving Virtual Machine
provisioning times.\
\
**Docker**: From [What is Docker?](https://www.docker.com/what-docker),
on the official site: \"Docker allows you to package an application with
all of its dependencies into a standardized unit for software
development \[\...\] Docker containers wrap up a piece of software in a
complete filesystem that contains everything it needs to run: code,
runtime, system tools, system libraries -- anything you can install on a
server. This guarantees that it will always run the same, regardless of
the environment it is running in\".\
\
**Ubuntu**: From [About
Ubuntu](http://www.ubuntu.com/about/about-ubuntu) on the official site:
\"Linux was already established as an enterprise server platform in
2004, but free software was not a part of everyday life for most
computer users. That's why Mark Shuttleworth gathered a small team of
developers from one of the most established Linux projects --- Debian
--- and set out to create an easy-to-use Linux desktop: Ubuntu \[\...\]
The vision for Ubuntu is part social and part economic: free software,
available to everybody on the same terms, and funded through a portfolio
of services provided by Canonical\".\
\
**Ubuntu/Trusty64**: Vagrant provides free online vagrant boxes for the
general public to use on their HashiCorp site at
<https://atlas.hashicorp.com/boxes/search>. The official Ubuntu box is
called \"Trusty64\", since it is the 64-bit version of Ubuntu.\
\
**MongoDB**: From MongoDB\'s [company
site](https://www.mongodb.com/company): \"MongoDB was founded in 2007 by
the people behind DoubleClick, ShopWiki and Gilt Groupe. At DoubleClick,
the site could never be down and there were daily challenges with
processing, storing, and scaling data, forcing them to write their own
software to handle specific problems. It was in these trenches that the
team had the insight for MongoDB. They asked themselves, \'What do we
wish we had while at DoubleClick?\' \[\...\] The company was founded to
harness the power of the cloud for more efficiency, to scale
horizontally, and to make operations easier for scale at development.
Today, MongoDB boasts more than 10 million downloads, thousands of
customers, and more than 1,000 partners\".\
\
**Git**: According to
[Wikipedia](https://en.wikipedia.org/wiki/Git_(software)), \"Git is a
version control system that is widely used for software development and
other version control tasks. It is a distributed revision control system
with an emphasis on speed, data integrity, and support for distributed,
non-linear workflows. Git was initially designed and developed in 2005
by Linux kernel developers (including Linus Torvalds) for Linux kernel
development\".\
\
**Bitbucket:** Purchased by Atlassian ( owner of JIRA, Confluence, and
HipChat) in 2010, is yet another place for code storage. While GitHub
focuses on Open Source technologies, with free storage only for public
projects, Bitbucket focuses on private enterprise software.\
\
Now that we have been introduced to the cast of characters, we may now
begin!\
\

Downloads and Installations
---------------------------

\
**Git-SCM**:\

-   Go to <https://git-scm.com/downloads> and download the correct
    version for your local computer.
-   If you need help installing Git, read Pro Git\'s chapter [Getting
    Started - Installing
    Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)

*\... Note: If you want to learn all the ins-and-outs of Git, read the
free book on Git, [Pro Git](https://git-scm.com/book/en/v2), by Scott
Chacon and Ben Straub.*\
\
**VirtualBox**:\

-   Go to
    [http://https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)
    and download and install the correct version for your local
    computer. For Windows machines, it will be \"VirtualBox 5.0.20 for
    Windows hosts\" -\> x86/amd64

\
**Vagrant**:\

-   Go to <https://www.vagrantup.com/downloads.html> and download and
    install the correct version for your local computer.

\
**Vagrant cachier**:\

-   Once you have Vagrant installed, go to the Terminal if you are using
    a Mac or the Command Prompt if you are using a PC
-   Type the following: vagrant plugin install vagrant-cachier
-   The plugin will be automatically installed.

\
\

What is a Vagrantfile?
----------------------

\
A *Vagrantfile* is a configuration file for Vagrant. From VagrantUp\'s
[Vagrantfile](https://www.vagrantup.com/docs/vagrantfile/) page:\

> *\"The primary function of the Vagrantfile is to describe the type of
> machine required for a project, and how to configure and provision
> these machines. Vagrantfiles are called Vagrantfiles because the
> actual literal filename for the file is Vagrantfile (casing does not
> matter unless your file system is running in a strict case sensitive
> mode).\
> \
> \"Vagrant is meant to run with one Vagrantfile per project, and the
> Vagrantfile is supposed to be committed to version control. This
> allows other developers involved in the project to check out the code,
> run vagrant up, and be on their way. Vagrantfiles are portable across
> every platform Vagrant supports.\
> \
> \"The syntax of Vagrantfiles is Ruby, but knowledge of the Ruby
> programming language is not necessary to make modifications to the
> Vagrantfile, since it is mostly simple variable assignment\".*

\

Review Farcic\'s Vagrantfile
----------------------------

\
To help us configure the virtual machine, we will clone, using Git, a
copy of configuration file the author Viktor Farcic has graciously set
up in his Atlassian Bitbucket account.\
\
**Vagrantfile**\

``` {.brush: .ruby}
# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"
 
  config.vm.network "forwarded_port", guest: 27017, host: 27017

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"
  end

  config.vm.provision "docker" do |d|
    d.run "mongoDB", image: "mongo:2", args: "-p 27017:27017"
  end

  if Vagrant.has_plugin?("vagrant-cachier")
    config.cache.scope = :box
  end

end
```

\

-   Go to
    <https://bitbucket.org/vfarcic/tdd-java-ch02-example-vagrant/src>
-   Select **Vagrantfile** to view the source code.
-   Select in the Left Hand Menu, under **Actions** the word **Clone**.
-   Copy the URL and paste it into a text editor. We will be making
    adjustments to the text.

\
*Need help? You can review Atlassian\'s **How to clone a repository**:
<https://confluence.atlassian.com/bitbucket/clone-a-repository-223217891.html>.*\
\
The piece of text we now have in our text editor is:\

-   git clone
    https://bitbucket.org/vfarcic/tdd-java-ch02-example-vagrant.git

\
Let\'s say that we want to store \"tdd-java-ch02-example-vagrant.git\"
into a new folder called \"tdd\", and calling the file
\"tdd-java-ch02-example-vagrant\". We would edit the text in our text
editor to read:\

-   git clone
    https://bitbucket.org/vfarcic/tdd-java-ch02-example-vagrant.git
    tdd/tdd-java-ch02-example-vagrant

\
We could copy and paste this code into the Command Prompt of your
machine like so:\
\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 C:\>git clone https://bitbucket.org/vfarcic/tdd-java-ch02-example-vagrant.git tdd/tdd-java-ch02-example-vagrant  
```

\
Once everything is done copying over to your local computer, you can
change directory first to the new directory \"tdd\", then
\"tdd-java-ch02-example-vagrant\".\
\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 C:\>cd tdd  
 C:\tdd>cd tdd-java-ch02-example-vagrant   
```

\

Vagrant Up!
-----------

\
Whether you want to start the virtual machine, go to the directory you
placed the Vagrantfile, and type in:\
\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 vagrant up  
```

\
\
**Initial Installation:**\
\

-   The first time you Vagrant Up, it finds and install virtualbox and
    \"ubuntu/trusty64\" at atlas.hashicoep.com/ubuntu/trusty64. As
    Viktor Farcic writes, \"Be patient until the execution is finished.
    Once done, you\'ll have a new virtual machine with Ubuntu. Docker
    and one MongoDB instance up and running. The best part is that all
    this was accomplished with a single command\".

\
**Vagrant Commands within a PC\'s Command Prompt / Mac Terminal:**\

-   vagrant up: Brings up the Virtual Machine
-   vagrant status: Shows the status of the VM
-   vagrant halt: Stops the virtual machine

\
\... If you feel better with a Graphic User Interface to start or stop
the VM, you can always just fire up the VirtualBox app on your PC or
Mac\... but that might be cheating. I keep telling myself, I will never
get used to the Command Line Interface if I always go to the GUI.\
\

  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://1.bp.blogspot.com/-0n6CAk2Ybfo/VymPPoz4V7I/AAAAAAAAK_E/PLNe6Hwm-IgOtpw-B8xDKqfoDRNBAb_1gCLcB/s400/vm.png){width="400" height="297"}](https://1.bp.blogspot.com/-0n6CAk2Ybfo/VymPPoz4V7I/AAAAAAAAK_E/PLNe6Hwm-IgOtpw-B8xDKqfoDRNBAb_1gCLcB/s1600/vm.png)
                                                                                                                        .*.. But I like the GUI! *
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

\
\

Connecting to the Ubuntu box
----------------------------

\
To start the new Ubuntu box once the VM is up and running, type in:\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 vagrant ssh  
```

\
Let\'s now stop the Ubuntu OS from running.\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 exit  
 vagrant halt  
```

\
\
Let\'s start the VM back up, connect to Ubuntu, and this time start the
MongoDB container and see what processes have started:\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 vagrant up
 vagrant ssh
 docker start mongoDB  
 docker ps  
```

\
Congratulations! It\'s a Virtual Development Environment!\
\
\... We will return to this down the road, as I cover more of Viktor
Farcic\'s book.\
\
Until then, Happy Testing!\
\
-T.J. Maher\
Sr. QA Engineer,\
Fitbit-Boston\
\
*// QA Engineer since Aug. 1996\
// Automation developer for \[ 1 \] year and still counting!*
