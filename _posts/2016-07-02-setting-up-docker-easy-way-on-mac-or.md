\-\-- layout: post title: \'Setting up Docker the \"easy\" way on Mac or
Windows: The Docker Toolbox and the Get Started Guide\' date:
\'2016-07-02T17:57:00.000-04:00\' author: T.J. Maher tags: - VirtualBox
- Docker modified\_time: \'2016-07-03T13:54:03.357-04:00\' thumbnail:
https://2.bp.blogspot.com/-bxAuOwq6eO8/V3fUt0qpyFI/AAAAAAAALME/V176ccnPyBcZUzOM7bwhLNAou5zginDZQCLcB/s72-c/icon.png
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-5077312147258497060
blogger\_orig\_url:
http://www.tjmaher.com/2016/07/setting-up-docker-easy-way-on-mac-or.html
\-\--

  --------------------------------------------------------------------------------------------------------------
   ![Toolbox installer](https://docs.docker.com/toolbox/images/toolbox-installer.png){width="400" height="300"}
       *It\'s the [Docker Toolbox](https://www.docker.com/products/docker-toolbox) for Easy Installation!*
  --------------------------------------------------------------------------------------------------------------

\
I\'ve been on a quest since I became an automation developer,
[documenting everything I have been
doing](http://www.tjmaher.com/2016/07/blogging-about-automated-testing.html)
adding to the automated test framework at my workplace. Because I
didn\'t start at square one, there are things I wonder about\...\
\

The Past: Browser images on Virtual Machines
--------------------------------------------

\
When performing browser testing around a decade ago, I used to use
VMWare to setup numerous virtual machine images for my testing team. The
images contained the multitude of browsers and platforms configurations
we needed. I would configure and place them the shared drive at whatever
company I was working on. If we wanted to see how our web application
looked on a clean install of the now defunct Netscape Navigator and
Windows NT, and compare that with IE6, IE7, and IE8, our entire testing
team could blow away whatever previous virtual machines they had on
their desktop, and copy whatever was needed that day to their computer.\
\
I am on a quest to find that type of ease-of-use.\
\
\
[]{#more}\
\

The Future: Browser images in Containers
----------------------------------------

\
Although I haven\'t documented it in my blog, yet, it is easy to find
tutorials to [download and install Selenium
Grid](http://www.guru99.com/introduction-to-selenium-grid.html), which
provides a small sample of browsers you can hook up your automated test
framework to. My goal is to place my Selenium Grid in a Docker
container, so that when automated testers are running automated tests on
their local machine, they can set up the Docker image and have every
browser and platform they need at their fingertips.\
\
A few months ago, we explored how to set up a virtual machine with
[VirtualBox, Vagrant, and
Docker](http://www.tjmaher.com/2016/05/setting-up-virtual-dev-environment-with.html).
It would have been much too complex for someone just switching from
manual testing to automated testing! Where could we find an easier way
for someone to be able to dive in and set things up?\
\
We are going to be exploring the Docker Toolbox, a tool I heard about as
I was [listening to a video
lecture](https://confengine.com/selenium-conf-2016/proposal/2380/testing-as-a-container-using-docker-with-selenium-and-friends-to-ship-fast)
at Selenium Conf 2016.\
\

What Is a Docker Container?
---------------------------

> \"A container is an entire portable runtime environment: an
> application, plus all its dependencies, libraries and other binaries,
> and configuration files needed to run it, bundled into one package. By
> containerizing the application platform and its dependencies ,all
> differences in OS distributions and underlying infrastructure are
> abstracted away which makes it easy to share and execute anywhere\".\
> *\-- Irfan Ahmad, [Testing as a
> Container](https://confengine.com/selenium-conf-2016/proposal/2380/testing-as-a-container-using-docker-with-selenium-and-friends-to-ship-fast):
> Using Docker with selenium and friends to ship fast*

And What Is Docker, Again?
--------------------------

\
Docker was created by Solomon Hykes while he was working at a company he
founded, dotCloud. Docker was first released back in March 2013, written
in the Google invented language called [Go](https://golang.org/).\
\
The article *[What is Docker](https://www.docker.com/what-docker)?* on
Docker\'s official site mentions that \"Docker containers wrap a piece
of software in a complete filesystem that contains everything needed to
run: code, runtime, system tools, system libraries -- anything that can
be installed on a server. This guarantees that the software will always
run the same, regardless of its environment\".\
\

And What is a Container?
------------------------

\
Containers are lightweight: \"Containers running on a single machine
share the same operating system kernel; they start instantly and use
less RAM. Images are constructed from layered filesystems and share
common files, making disk usage and image downloads much more
efficient\".\
\
Containers are smaller than virtual machines: VMs \"include the
application, the necessary binaries and libraries, and an entire guest
operating system \-- all of which can amount to tens of\" gigabytes.
Containers \"include the application and all of its dependencies \--but
share the kernel with other containers, running as isolated processes in
user space on the host operating system. Docker containers are not tied
to any specific infrastructure: they run on any computer, on any
infrastructure, and in any cloud\".\
\
And, yes, **Docker has a GitHub
site**: <https://github.com/docker/docker>\

> \"Docker containers are both hardware-agnostic and platform-agnostic.
> This means they can run anywhere, from your laptop to the largest
> cloud compute instance and everything in between - and they don\'t
> require you to use a particular language, framework or packaging
> system. That makes them great building blocks for deploying and
> scaling web apps, databases, and backend services without depending on
> a particular stack or provider.\
> \
> \"Docker began as an open-source implementation of the deployment
> engine which powered dotCloud, a popular Platform-as-a-Service. It
> benefits directly from the experience accumulated over several years
> of large-scale operation and support of hundreds of thousands of
> applications and databases\".

The Docker Toolbox
------------------

According to the [Docker Toolbox
Overview](http://docker%20machine%20for%20running%20docker-machine%20commands%20docker%20engine%20for%20running%20the%20docker%20commands%20docker%20compose%20for%20running%20the%20docker-compose%20commands%20kitematic%2C%20the%20docker%20gui%20a%20shell%20preconfigured%20for%20a%20docker%20command-line%20environment%20oracle%20virtualbox/),
the Docker Toolbox contains:\

-   Docker Machine for running docker-machine commands
-   Docker Engine for running the docker commands
-   Docker Compose for running the docker-compose commands
-   Kitematic, the Docker GUI
-   a shell preconfigured for a Docker command-line environment
-   Oracle VirtualBox

::: {.separator style="clear: both; text-align: center;"}
\
:::

\... There is a GUI? Awesome! Don\'t tell anyone, but I really hate
using the command line. It reminds me of working in a musty basement
Mainframe computer lab during my undergrad program. Windows was a
gigantic step towards the great user interface that Apple [already had
stolen from Xerox years
before](http://www.mac-history.net/computer-history/2012-03-22/apple-and-xerox-parc).\
\
You can go to <https://www.docker.com/products/docker-toolbox> to
download the Docker Toolbox for the Mac or the PC. For the PC it
downloads a simple executable file you can run.\
\
You can even go to the [Docker Toolbox GitHub
site](https://github.com/docker/toolbox)to see what is happening
behind-the-scenes.\
\

Installing Docker Toolbox
-------------------------

\
Okay\... that\'s weird\... I downloaded the tool, ran the executable,
and as I was going through the installation process I saw an option that
could be chosen during the installation:\
\

-   *Install VirtualBox with NDIS5 driver \[default NDIS6\]. *

\
What the what? For a a tool that is supposed to be easy, there needs to
be a bit more user prompts to help a user to make a decision.\
\
After a bit of searching I found on [VirtualBox\'s
documentation](https://www.virtualbox.org/manual/ch02.html): \"\"The
user is able to choose between NDIS5 and NDIS6 host network filters
drivers during the installation. This is realized via a command line
parameter NETWORKTYPE. The NDIS6 driver is default for Windows Vista and
later. For older Windows versions, the installer will automatically
select the NDIS5 driver and this cannot be changed. For Windows Vista
and later the user can force to install the (legacy) NDIS5 host network
filter driver using NETWORKTYPE=NDIS5\".\
\
I\'m going to leave that checkbox unchecked. I don\'t think I am going
to need Windows 95, Win98, WinNT, or Windows ME. In case I do, I can set
the parameters through the command line I can use either/ or:\
\
\
\
\

*VirtualBox.exe -msiparams NETWORKTYPE=NDIS5*

``` {.screen style="background-color: white;"}
msiexec /i VirtualBox-<version>-MultiArch_<x86|amd64>.msi NETWORKTYPE=NDIS5
```

\
At the end of the process \-- which seems to involve my copy of Git-SCM
being uninstalled (Huh?) \-- I have two icons in a folder: Docker
Quickstart Terminal and Kitematic.\
\

::: {.separator style="clear: both; text-align: center;"}
[![](https://2.bp.blogspot.com/-bxAuOwq6eO8/V3fUt0qpyFI/AAAAAAAALME/V176ccnPyBcZUzOM7bwhLNAou5zginDZQCLcB/s320/icon.png){width="320"
height="80"}](https://2.bp.blogspot.com/-bxAuOwq6eO8/V3fUt0qpyFI/AAAAAAAALME/V176ccnPyBcZUzOM7bwhLNAou5zginDZQCLcB/s1600/icon.png)
:::

\
Let\'s see what these buttons do: After double-clicking on the Docker
Quickstart Terminal, five minutes later a terminal window appears:\
\

::: {.separator style="clear: both; text-align: center;"}
[![](https://2.bp.blogspot.com/-qGCcl68aGPo/V3fVekPbLnI/AAAAAAAALMM/ebdby8rxsIoQ0SkNVrsgi6Tc6qhiJ2tRACLcB/s400/whale.png){width="400"
height="201"}](https://2.bp.blogspot.com/-qGCcl68aGPo/V3fVekPbLnI/AAAAAAAALMM/ebdby8rxsIoQ0SkNVrsgi6Tc6qhiJ2tRACLcB/s1600/whale.png)
:::

\
\

-   Hrm. That isn\'t too helpful. Let\'s type in **exit** to close the
    window. 
-   When I start Kitematic, it says: \"Error: getaddrinfo ENOTFOUND
    docker.local docker.local:2375\". So far, this doesn\'t seem too
    much easier than working with the command line. 

<div>

Sidenote: MinGW stands for Minimalist GNU for Windows, whose home was at
<http://www.mingw.org/>. Writing Windows apps? MinGW was a bare-bones
Open Source programming toolset porting ObjectiveC to Windows back in
2005, and recreated by OneVision Software.

</div>

<div>

\

</div>

<div>

To the documentation!

</div>

<div>

\

</div>

Get Started With Docker
-----------------------

<div>

The **Get Started With Docker** guide is
at <https://docs.docker.com/engine/getstarted/>

</div>

<div>

\

</div>

\

<div>

\"This tutorial is designed as a getting started with Docker, and works
the same whether you are using Docker for Mac, Docker for Windows,
Docker on Linux, or Docker Toolbox (for older Mac and Windows systems).

</div>

<div>

<div>

\

</div>

<div>

\"If you are using Docker Toolbox, you can use the Docker Quickstart
Terminal to run Docker commands in a pre-configured environment instead
of opening a command line terminal\".

</div>

</div>

<div>

\

</div>

### Step One: Installing Docker

<div>

\

</div>

<div>

According to [Step
One](https://docs.docker.com/engine/getstarted/step_one/), after the
Docker QuickStart terminal starts, we can type in the command:

</div>

<div>

[\$ docker run
hello-world]{style="background-color: whitesmoke; color: #333333; font-family: "consolas" , "liberation mono" , "courier" , monospace; font-size: 13px; line-height: 18.5714px; white-space: pre-wrap;"}

</div>

<div>

\

</div>

::: {.separator style="clear: both; text-align: center;"}
[![](https://2.bp.blogspot.com/-qJjtmxAw6Cc/V3ff-_JmXEI/AAAAAAAALMg/8m6HVimglcI0t7Ls2jHH16muht-375RnACLcB/s400/message.png){width="400"
height="161"}](https://2.bp.blogspot.com/-qJjtmxAw6Cc/V3ff-_JmXEI/AAAAAAAALMg/8m6HVimglcI0t7Ls2jHH16muht-375RnACLcB/s1600/message.png)
:::

\
\"Hello from Docker.\
\"This message shows that your installation appears to be working
correctly.\
\
\"To generate this message, Docker took the following steps:\
\"1. The Docker Engine CLI client contacted the Docker Engine daemon.\
\"2. The Docker Engine daemon pulled the \"hello-world\" image from the
Docker Hub.\
\"3. The Docker Engine daemon created a new container from that image
which runs the\
   executable that produces the output you are currently reading.\
\"4. The Docker Engine daemon streamed that output to the Docker Engine
CLI client, which sent it\
   to your terminal.\
\
\"To try something more ambitious, you can run an Ubuntu container
with:\
\"\$ docker run -it ubuntu bash\
\
\"Share images, automate workflows, and more with a free Docker Hub
account: [https://hub.docker.com](https://hub.docker.com/)\
\
\"For more examples and ideas, visit:
<https://docs.docker.com/userguide/>\"\
\
\... Thank you for the tips, Docker!\

<div>

\

</div>

Let\'s see\... If I want to see all the Docker images on my machine:\
[\$ docker ps
]{style="background-color: whitesmoke; color: #333333; font-family: "consolas" , "liberation mono" , "courier" , monospace; font-size: 13px; line-height: 18.5714px; white-space: pre-wrap;"}[-a]{.hljs-_
style="box-sizing: inherit; color: #333333; font-family: "consolas" , "liberation mono" , "courier" , monospace; font-size: 13px; line-height: 18.5714px; white-space: pre-wrap;"}\
\

-   Image: hello-world Names: sleepy-austin
-   Image kitematic/hello-world-nginx: latest (Lists ports) Names:
    hello-world-nginx

### Step Two: Running Docker Images in Docker Engine

\
[Step Two](https://docs.docker.com/engine/getstarted/step_two/) of the
users guide talks about how we ran in the terminal the command:\
\

-   docker run hello-world

\
Remember, a Docker image is the entire filesystem and parameters we use
at runtime. The container runs the instance of the image.\
\
When we ran \"hello-world\" the Docker Engine started and ran a Docker
container, and attempted to run the hello-world image. Since we didn\'t
have an image, it connected to the Docker Hub
( [https://hub.docker.com](https://hub.docker.com/) ) and downloaded
that image to the container.\
\
Since I eventually want to put Selenium Grid in a container, I might as
well sign up for an account. It\'s free! \... Now I have a Docker Hub
account to add to my collection!\
\

-   Twitter: @[tjmaher1](https://twitter.com/tjmaher1)
-   LinkedIn: [tjmaher1](https://www.linkedin.com/in/tjmaher1)
-   GitHub: [tjmaher](https://github.com/tjmaher)
-   Docker Hub: [tjmaher](https://hub.docker.com/r/tjmaher/)

\
\
\"A Docker image, though, is capable of much more. An image can start
software as complex as a database, wait for you (or someone else) to add
data, store the data for later use, and then wait for the next
person\".\
\

### Step Three: Searching Docker Hub for Docker Images

Cowsay was a Perl program written by Tony Monroe back in 1999 (
[according to Wikipedia](https://en.wikipedia.org/wiki/Cowsay) ). You
could type in:\
\

``` {style="background: rgb(240, 240, 240); border: 1px dashed rgb(204, 204, 204); font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; width: 646.441px;"}
 $ cowsay moo 
```

<div>

``{style="word-wrap: normal;"}

</div>

<div>

`and see:`{style="word-wrap: normal;"}

</div>

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://1.bp.blogspot.com/--a48RcLyQa4/V3fxZR-eUeI/AAAAAAAALM4/BxOgEFL4ZhELeTRsWxTyHUgOqq8C4_pGwCLcB/s320/cowsay.png){width="320" height="196"}](https://1.bp.blogspot.com/--a48RcLyQa4/V3fxZR-eUeI/AAAAAAAALM4/BxOgEFL4ZhELeTRsWxTyHUgOqq8C4_pGwCLcB/s1600/cowsay.png)
                                                                                                                          Linux command: *\$ cowsay moo*
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

<div>

``{style="word-wrap: normal;"}

</div>

With [Step
Three](https://docs.docker.com/engine/getstarted/step_three/) of the
Docker Get Started guide we:\
\

-   Go to the **Docker
    Hub**: [https://hub.docker.com](https://hub.docker.com/)
-   Search for the keyword: \"whalesay\" to search for that Docker image
-   Select **docker/ whalesay**.

Selecting on the image, we are brought to the **docker /
whalesay** repository at <https://hub.docker.com/r/docker/whalesay/>.\
\
There, in plain English, are the instructions on how to use the Docker
image:\
\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 $ docker run docker/whalesay cowsay boo  
```

\
Typing this into the Docker Quickstart Terminal at the command prompt,
it starts downloading, extracting, and installing the Docker Image on
your machine. In the end, you see\...\
\

::: {.separator style="clear: both; text-align: center;"}
[![](https://4.bp.blogspot.com/-T4mQ4x0FkVg/V3fysuBvd1I/AAAAAAAALNA/WoF_l4MkxCgdFWMEE7vo3CcGqRjhXiXrwCLcB/s320/whalesay.png){width="320"
height="174"}](https://4.bp.blogspot.com/-T4mQ4x0FkVg/V3fysuBvd1I/AAAAAAAALNA/WoF_l4MkxCgdFWMEE7vo3CcGqRjhXiXrwCLcB/s1600/whalesay.png)
:::

\

::: {.separator style="clear: both; text-align: left;"}
Hrm\... I wonder what else I can get the whale to say? 
:::

::: {.separator style="clear: both; text-align: left;"}
\
:::

  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://2.bp.blogspot.com/-HnT9pNytyLE/V3fzlNkZwwI/AAAAAAAALNI/V4sF4rdgyMUsYo1wuIyv6vjFx7ZdiEVtgCLcB/s320/whalesay.png){width="320" height="178"}](https://2.bp.blogspot.com/-HnT9pNytyLE/V3fzlNkZwwI/AAAAAAAALNI/V4sF4rdgyMUsYo1wuIyv6vjFx7ZdiEVtgCLcB/s1600/whalesay.png)
                                                                                          You heard the whale! :) [You gotta do it, now](https://www.facebook.com/AdventuresInAutomation/). 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

::: {.separator style="clear: both; text-align: left;"}
You can see in the Docker Hub, it even shows
for <https://hub.docker.com/r/docker/whalesay/> the Dockerfile which
sets everything up. The Dockerfile runs the following Unix commands:
:::

::: {.separator style="clear: both; text-align: left;"}
\
:::

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 apt-get update   
 apt-get install -y cowsay --no-install-recommends   
 rm -rf /var/lib/apt/lists/* \  
 mv /usr/share/cowsay/cows/default.cow /usr/share/cowsay/cows/orig-default.cow  
 # "cowsay" installs to /usr/games  
 ENV PATH $PATH:/usr/games  
 COPY docker.cow /usr/share/cowsay/cows/  
 RUN ln -sv /usr/share/cowsay/cows/docker.cow /usr/share/cowsay/cows/default.cow  
 CMD ["cowsay"]  
```

\
What the heck is APT-GET?\
\
\"\"The apt-get utility is a powerful and free package management
command line program, that is used to work with Ubuntu's APT (Advanced
Packaging Tool) library to perform installation of new software
packages, removing existing software packages, upgrading of existing
software packages and even used to upgrading the entire operating
system\". - [Useful Commands of
APT-GET](http://www.tecmint.com/useful-basic-commands-of-apt-get-and-apt-cache-for-package-management/)\
\
Now, if you run at the command prompt: **\$ docker images** you can see
that docker/ whalesay is now included.\
\
And, yes, with the Quickstart terminal, you can run Unix on your Windows
machine.\
\
\

-   Not familiar with Unix / Linux? See [Learning the Command Line
    Interface](http://www.tjmaher.com/2015/05/learning-command-line-interface.html)

\
\

### Step Four: Build Your Own Docker Image

[Step Four](https://docs.docker.com/engine/getstarted/step_four/) walks
you through how to make a new Unix directory, change into the directory,
use the touch command to create a file, list the items in the directory,
and edit commands.\
\
\
Happy Testing!\
\
-T.J. Maher\
Sr. QA Engineer,\
Fitbit-Boston\
\
*// QA Engineer since Aug. 1996\
// Automation developer for \[ 1.5 \] year and still counting!\
// Check us out on
[Facebook](https://www.facebook.com/AdventuresInAutomation/)!*
