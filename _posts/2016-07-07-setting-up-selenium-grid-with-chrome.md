\-\-- layout: post title: Setting Up Selenium Grid with Chrome and
Firefox browser nodes from Docker-Selenium date:
\'2016-07-07T01:29:00.000-04:00\' author: T.J. Maher tags: -
SeleniumGrid - Docker modified\_time: \'2016-07-09T08:38:39.970-04:00\'
thumbnail:
https://4.bp.blogspot.com/-AF\_oR1OvVIQ/V3yCH1sMeLI/AAAAAAAALOw/76RyyVMJZbk3iHQVEk5IXkf8wnJSJFrpgCKgB/s72-c/dockericon.png
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-3795391781966419195
blogger\_orig\_url:
http://www.tjmaher.com/2016/07/setting-up-selenium-grid-with-chrome.html
\-\-- *Please Note: This blog post will be using the official
SeleniumHQ\'s
[Docker-Selenium](https://github.com/SeleniumHQ/docker-selenium)
project, not Leo Gallucci\'s [Docker-Selenium
project](https://github.com/elgalu/docker-selenium)*\
\
We will be experimenting, in this blog post, with installing
Docker, deploying Selenium HQ\'s various Chrome and Firefox Docker
images, regular versions, and using them with their Docker image of
Selenium Hub.\

::: {.separator style="clear: both; text-align: center;"}
[![](https://4.bp.blogspot.com/-AF_oR1OvVIQ/V3yCH1sMeLI/AAAAAAAALOw/76RyyVMJZbk3iHQVEk5IXkf8wnJSJFrpgCKgB/s400/dockericon.png){width="400"
height="135"}](https://4.bp.blogspot.com/-AF_oR1OvVIQ/V3yCH1sMeLI/AAAAAAAALOw/76RyyVMJZbk3iHQVEk5IXkf8wnJSJFrpgCKgB/s1600/dockericon.png)
:::

Later on, we will tie this in with my
[BasicWebDriverFramework\_Gradle](https://github.com/tjmaher/BasicWebDriverFramework_Gradle),
including into the project our work with
[PageFactories](http://www.tjmaher.com/2016/06/page-factories-setting-up-creating-them.html),
and adding RemoteWebDriver and DesiredCapabilities functionality. In the
post after this, we will build on this information, using Docker Compose
to scale Selenium Grid.\
\
**Docker**: <https://www.docker.com/>\
**SeleniumHQ Images**: <https://hub.docker.com/u/selenium/>\
**Docker-Compose**: <https://docs.docker.com/compose/>\

-   Want to tinker a bit with setting up a virtual environment with
    [VirtualBox, Vagrant, and
    Docker](http://www.tjmaher.com/2016/05/setting-up-virtual-dev-environment-with.html)
    first? 
-   Want a practice exercise [setting up
    Docker](http://www.tjmaher.com/2016/07/setting-up-docker-easy-way-on-mac-or.html)?
-   Unfamiliar with the command line? Want a practice exercise [setting
    up Selenium
    Grid](http://www.tjmaher.com/2016/07/setup-of-selenium-grid-for-beginners.html)? 

Why install Selenium Grid in a container system like Docker? Docker is
built to help make configuring systems easier, helpful if you are
setting up Selenium Grid with one Selenium Hub and multiple Chrome and
Firefox nodes.\
\
Normally, to set up Grid, you would:\
\

-   Download Selenium-StandAlone-Server
-   Start up the Selenium Hub: *java -jar
    selenium-server-standalone-2.53.0.jar -role hub*
-   Start up various nodes: *java -jar
    selenium-server-standalone-2.53.0.jar -role node -hub
    http://localhost:4444/grid/register -browser
    browserName=firefox,maxInstances=2 -browser
    browserName=chrome,maxInstances=2*

<div>

*\...* Then the Selenium Grid would be ready to use at
http://localhost:4444. 

</div>

<div>

\

</div>

<div>

With Docker, it is still that same three step process\... except we can
bundle all of those three steps into one with Docker Compose. That is
for later blog posts. First, though, let\'s talk about Docker\...

</div>

\
\
[]{#more}\

1.  Install Docker
------------------

\
**Docker** is similar to a virtual machine, but more lightweight. With a
virtual machine, the operating system also needs to be included. With
Docker, the Docker Engine is separate from the Docker images you can
pull from **Docker Hub** <https://hub.docker.com/> running the images on
your system. System errors? You can blow away the Docker image on your
system and pull in a fresh image.\

###  1.1.  **Download and Install Docker Toolbox**

\
Install **Docker
Toolbox**: <https://www.docker.com/products/docker-toolbox>. To run
Docker commands, you need to run the Docker Quickstart Terminal. Check
and install everything. We will need Docker Compose later, and
VirtualBox needs to be installed inside Docker. Oracle\'s VirtualBox is
bundled with the Toolbox. Note: Quickstart is NOT quick the first time
around.\

-   Docker\'s GitHub site: <https://github.com/docker/docker>
-   Need more info? See the Guide to [setting up Docker
    Toolbox](http://www.tjmaher.com/2016/07/setting-up-docker-easy-way-on-mac-or.html)

\
Once it (finally) installed, you should see this:\

::: {.separator style="clear: both; text-align: center;"}
[![](https://3.bp.blogspot.com/-LT8S7Ui44J8/V3zp5prdbAI/AAAAAAAALPQ/IfcUkzlKFeQOtgO_TljzxtWZ9Arq74r0QCLcB/s400/docker.png){width="400"
height="116"}](https://3.bp.blogspot.com/-LT8S7Ui44J8/V3zp5prdbAI/AAAAAAAALPQ/IfcUkzlKFeQOtgO_TljzxtWZ9Arq74r0QCLcB/s1600/docker.png)
:::

\
Note that Docker is configured to use your default machine with the IP
Address: 192.168.99.100.\

###  1.2.  Verify Docker is Working

\
Type in the Terminal window:\

-   docker version

\... Hopefully, you will see information for the Docker version you are
running. \
\
Want to see other Docker Commands? Go
to <https://docs.docker.com/engine/reference/commandline/cli/>\
\

2. Install SeleniumHQ Docker Images 
------------------------------------

\

### **2.1.  Review the Images from Docker Hub**

\
The Docker images we will be installing are
at **SeleniumHQ: **<https://hub.docker.com/u/selenium/> \... you can
click on these individual images to see how you can interact with them.\
\
For a description of what these images do, we can go to the Selenium HQ
Selenium Docker GitHub site at
<https://github.com/SeleniumHQ/docker-selenium>:\

-   **selenium/hub**: Image for running a Selenium Grid Hub
-   **selenium/node-chrome**: Selenium node with Chrome installed, needs
    to be connected to a Selenium Grid Hub
-   **selenium/node-firefox**: Selenium node with Firefox installed,
    needs to be connected to a Selenium Grid Hub
-   **selenium/standalone-chrome**: Selenium standalone with Chrome
    installed
-   **selenium/standalone-firefox**: Selenium standalone with Firefox
    installed
-   **selenium/standalone-chrome-debug**: Selenium standalone with
    Chrome installed and runs a VNC server
-   **selenium/standalone-firefox-debug**: Selenium standalone with
    Firefox installed and runs a VNC server
-   **selenium/node-chrome-debug**: Selenium node with Chrome installed
    and runs a VNC server, needs to be connected to a Selenium Grid Hub
-   **selenium/node-firefox-debug**: Selenium node with Firefox
    installed and runs a VNC server, needs to be connected to a Selenium
    Grid Hub

\
You can build your own Docker images using the base images, run one
standalone browser at a time on port 4444 with the standalone versions,
use the headless versions of the browser to run the tests, or use the
debug versions to see exactly what the test is doing on your screen.\
\

### **2.2.  Run the Selenium/ Hub**

\
**2.2.1.  Go to Docker Hub and select the Selenium/ Hub Docker image for
instructions.  **\
\
Go to **Selenium HQ\'s** Selenium repository on the Docker Hub at
<https://hub.docker.com/r/selenium/> and select the Docker image called
\"Selenium/ Hub\". All Docker Images list instructions on how the image
is run. More thorough information is
on <https://github.com/SeleniumHQ/docker-selenium>.\
\
\
**2.2.2.  Launch a container from the Docker image.**\
\
To run the selenium/hub  Docker
image, <https://hub.docker.com/r/selenium/hub/> enter the following into
the Docker Terminal:\

``` {style="background: rgb(240, 240, 240); border: 1px dashed rgb(204, 204, 204); font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; width: 646.469px;"}
 docker run -d -p 4444:4444 --name selenium-hub selenium/hub:2.53.0  
```

\

-   Run a Container based on a Docker Image. If the image cannot be
    found, pull it down from the Docker Hub: *docker run*
-   Start the container in detached mode, as opposed to foreground mode,
    so the console won\'t become attached to input, output, and standard
    error streams: *-d*
-   Map the Host Port to the Container Port. Remember, the IP address is
    192.168.99.100. Let\'s use HOSTPORT 4444 and CONTAINERPORT 4444: *-p
    4444:4444*
-   Set the name of the container as selenium-hub (much easier than the
    UUID Long and Short Identifier): *\--name selenium-hub*
-    Run the image called \"selenium/hub\" but specify a version of the
    image with the tag \"2.53.0\": *selenium/hub:2.53.0*

<div>

\... Need more information? 

</div>

<div>

-   Examine the Dockerfile for this image
    at <https://hub.docker.com/r/selenium/hub/~/dockerfile/> to see the
    default environment values set up for the Jetty server setting up
    the Selenium Grid. 
-   See the **Docker Run Reference**
    at <https://docs.docker.com/engine/reference/run>

</div>

\
**2.2.3  Verify the images have been installed**\
\
Type into the Docker Terminal:\

-   docker images

**\
2.2.4.  Verify that the Selenium Grid is running.**\
\
Selenium Grid will be running on your local host. Go to it and make sure
you are using the version of selenium-standalone-server that you
designated, 2.53.0: <http://192.168.99.100:4444/>\

> \"You are using grid 2.53.0\
> \"Find help on the official selenium wiki : [more help
> here](https://github.com/SeleniumHQ/selenium/wiki/Grid2)\"default
> monitoring page : [console](http://192.168.99.100:4444/grid/console)\"

Select \"console\". Notice that there are no nodes yet running.\
\

::: {.separator style="clear: both; text-align: center;"}
[![](https://1.bp.blogspot.com/-weTeufZIXOw/V33WaHpKk3I/AAAAAAAALPo/ReQ1xbmsiJMUeOPQ-1mJcN-2VP_2eyTqQCLcB/s400/grid%2Bno%2Bnode.png){width="400"
height="167"}](https://1.bp.blogspot.com/-weTeufZIXOw/V33WaHpKk3I/AAAAAAAALPo/ReQ1xbmsiJMUeOPQ-1mJcN-2VP_2eyTqQCLcB/s1600/grid%2Bno%2Bnode.png)
:::

\
\

2.3.  Setup Chrome and Firefox Nodes
------------------------------------

\
We are going to set up the Docker images for Chrome and Firefox, and add
them to the already running Selenium Hub.\
**\
2.3.1.  Run from the Docker Engine *node-chrome* and *node-firefox*.**\
\
**For Chrome:**\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 docker run -d --link selenium-hub:hub selenium/node-chrome:2.53.0  
```

\
**For Firefox:**\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 docker run -d --link selenium-hub:hub selenium/node-firefox:2.53.0  
```

\
\
**2.3.2.  Verify that nodes are now set up in the Selenium Grid.**\
\
Go to the Selenium Grid console, at
<http://192.168.99.100:4444/grid/console>\
\

  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://2.bp.blogspot.com/-zh4udgHiphk/V33b-mf6sII/AAAAAAAALQA/KbmI_7rNIk4Nm9MIxxVeZTIGPWxhlmyegCLcB/s640/grid%2Bnode.png){width="640" height="196"}](https://2.bp.blogspot.com/-zh4udgHiphk/V33b-mf6sII/AAAAAAAALQA/KbmI_7rNIk4Nm9MIxxVeZTIGPWxhlmyegCLcB/s1600/grid%2Bnode.png)
                                                                                                                          *Congratulations, it\'s a Grid Console!*
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

You will be able to connect to this Selenium Grid just as if it were
running on your local machine instead of in a container.\
\
Ignore the \"Remote Control\" instance of each browser. That is used in
Selenium RC.\
\
Hover your cursor over the browser instances in your \"WebDriver\"
sections. You can see what you can set up in RemoteWebDriver for Desired
Capabilities:\
\

-   browserName: \"chrome\" or \"firefox\".
-   maximum numbers of instances that can run: 1
-   platform: LINUX.

<div>

You can easily scale up or down the number of instances. Don\'t scale up
to more than you think you might need\... each instance of a browser
running on your machine chews up a lot of memory!  

</div>

<div>

\

</div>

\
WARNING! These Docker images are not meant to be like virtual machines,
always running in the background.\
\
*\"Note: Since a Docker container is not meant to preserve state and
spawning a new one takes less than 3 seconds you will likely want to
remove containers after each end-to-end test with \--rm command. You
need to think of your Docker containers as single processes, not as
running virtual machines.\" -[Docker-Selenium,
GitHub](https://github.com/SeleniumHQ/docker-selenium)*\
\

2.4. Future plans.
------------------

\
\

### 2.4.1. Scaling Selenium Grid

\
Next blog post, we will look at using **Docker Compose** at
<https://docs.docker.com/compose/overview/> to set up a YAML (\*.yml)
file, so we can easily bring up all hubs and nodes, spin up more nodes,
or stop all services, all with one command line\... and a lengthy
configuration file. \
\

### 2.4.2. RemoteWebDriver and DesiredCapabilities

\
Following that, we will be finally adding RemoteWebDriver and
DesiredCapabilities to finally, after all the work we have done to
prepare for Docker-Selenium, hook up our browser tests up with the
Selenium Grid.\
\
Rough Test to Demonstrate Docker-Selenium Hookups:\

``` {.brush: .java}
@Test
public void test_FirefoxDockerGridNavigatesToLoginPage() throws Exception  {
   DesiredCapabilities capabilities = DesiredCapabilities.firefox();
   capabilities.setBrowserName("firefox");
   capabilities.setPlatform(Platform.LINUX);
   driver = new RemoteWebDriver(new URL("http://192.168.99.100:4444/wd/hub"), capabilities);
   driver.get("http://the-internet.herokuapp.com/login");
   assertThat(driver.getTitle(), is(equalTo("The Internet")));
}
```

\
\... If you run this individual test, it takes the DesiredCapabilities,
and attempts to find a node at whatever URL you give it to run the test.
Here, we have listed the Linux version of Firefox, what we have listed
as a property of our WebDriver instance of Firefox.\

2.5.  Docker Commands
---------------------

\
**See Docker images:** Want to see what Docker images you have on your
system?\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 docker images  
```

**\
**\

::: {.separator style="clear: both; text-align: center;"}
[![](https://2.bp.blogspot.com/-DIbfUrpQsok/V33h8rUZnII/AAAAAAAALQY/SxonuBJKWgwIJD9cmmlKlUrMrFGg1xuIACLcB/s640/docker%2Bimages.png){width="640"
height="73"}](https://2.bp.blogspot.com/-DIbfUrpQsok/V33h8rUZnII/AAAAAAAALQY/SxonuBJKWgwIJD9cmmlKlUrMrFGg1xuIACLcB/s1600/docker%2Bimages.png)
:::

\
**See Running Containers**: Show us only Docker containers that are
currently running:\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 docker ps  
```

\
**See ALL containers**: Show us ALL of the Docker containers, even those
not running.\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 docker ps -a  
```

\
**Logs:** Want to see the log files of selenium-hub? *(Reference:
[logs](https://docs.docker.com/engine/reference/commandline/logs/))*\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 docker logs -f selenium-hub  
```

\
\... Make sure to CTRL-C out of the logfile.\
\
**Stop an individual container**, like selenium-hub, from running
*(Reference:
[stop](https://docs.docker.com/engine/reference/commandline/stop/))*:\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 docker stop selenium-hub  
```

\
**Stop ALL containers** from running:\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 docker stop $(docker ps -a -q)  
```

\
**Get help:**\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 docker help  
```

\
**Get help on a command**, such as \"ps\":\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 docker help --ps  
```

\
**Remove the Docker image**, selenium-hub, after stopping the container
from running *(Reference:
[rmi](https://docs.docker.com/engine/reference/commandline/rmi/)):*\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 docker rmi selenium-hub  
```

\
\

Coming Up\...
-------------

Future blog posts will cover:\
\

-   **RemoteWebDriver:** Taking our
    [DesiredCapabilities](https://github.com/SeleniumHQ/selenium/wiki/DesiredCapabilities)
    we touched upon, and expand it. 
-   **Docker Compose**: <https://docs.docker.com/compose/>: Bundle
    together scaling up or down Selenium Grid browser nodes, downloading
    Selenium Grid, starting up a Hub, and starting up various nodes.
-   **MicrosoftWebDriver**: (
    [Link](https://www.microsoft.com/en-us/download/details.aspx?id=48212)
    ): How to incorporate Microsoft Edge into your tests.
-   **Microsoft Virtual Images**:
    <https://developer.microsoft.com/en-us/microsoft-edge/tools/vms/> add
    IE8, IE9, IE10, IE11 on Windows 7 or IE 11 and Microsoft Edge to
    Windows 10 nodes to your Selenium Hub! Just use VirtualBox, Vagrant,
    HyperV (Windows), VMWare, or Parallels (Mac). Take a snapshot of the
    images because the originals are only good for 90 days. 
-   **Selenium Grid
    Extras**: <https://github.com/groupon/Selenium-Grid-Extras>

\
\
Until the next time I find four spare hours to research and write up
more documentation\... Happy Testing!\
\
-T.J. Maher\
Sr. QA Engineer,\
Fitbit-Boston\
\
*// BSCS, MSE, and QA Engineer since Aug. 1996\
// Automation developer for \[ 1.5 \] years and still counting!\
// Check out Adventures in Automation and Like us on
[Facebook](https://www.facebook.com/AdventuresInAutomation/)!*
