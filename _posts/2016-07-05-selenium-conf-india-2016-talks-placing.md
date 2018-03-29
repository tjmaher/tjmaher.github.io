\-\-- layout: post title: \'Selenium Conf India 2016 Talks: Placing
Selenium Grid in a Docker Container\' date:
\'2016-07-05T00:17:00.002-04:00\' author: T.J. Maher tags: - conference
- SeleniumGrid - Docker modified\_time:
\'2016-07-05T00:33:28.001-04:00\' thumbnail:
https://i.ytimg.com/vi/kXlS69PXX68/default.jpg blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-3093311036265265937
blogger\_orig\_url:
http://www.tjmaher.com/2016/07/selenium-conf-india-2016-talks-placing.html
\-\-- Selenium Conference India 2016 was held June 24, 2016 to June 26,
2016 in Bangalore. It\'s like Christmas for me, after every conference
when they release the presentation slides the presenters used, indexing
them all on the schedule at
<https://confengine.com/selenium-conf-2016/schedule>. Simon Stewart,
creator of WebDriver, gives his [State of the
Union](https://confengine.com/selenium-conf-2016/proposal/2584/selenium-state-of-the-union).
Automation developers showcase their work. You get to see what other
automation developers are doing with the tool.\
\
Videos usually are released a few weeks after the event.\
\
I noticed that there were two talks and a workshop that dealt with a
technology I was tinkering with for the past few months: [Setting up
Docker
Containers](http://www.tjmaher.com/2016/05/setting-up-virtual-dev-environment-with.html).
They were pairing Selenium with Docker to help them with testing.\
\
[]{#more}\
\

**Testing as a Container  **
----------------------------

*Using Docker with selenium and friends to ship fast*\
**Presenter**: Irfan Ahmad (
[\@critickarr](https://twitter.com/critickar) ), from Upgrad\
**Website**: <http://critick.io/Testing-as-a-container/>\
\

\

::: {style="margin-bottom: 5px;"}
**[Testing as a
container](https://www.slideshare.net/IRFANAHMAD60/testing-as-a-container "Testing as a container")**
from **[IRFAN AHMAD](https://www.slideshare.net/IRFANAHMAD60)**
:::

\
Irfan talked about the idea of shipping Tests as Docker Containers
instead of code. \"Since Testers are responsible for reliability of
their tests in the same way developers/dev-ops are responsible for their
software but this is usually difficult, time consuming and needs
collaboration with developers. Docker capabilities can help us in
ensuring and enhancing reliability of our tests\".\
\
*( This presentation is also where I first heard about installing Docker
with the **Docker Toolbox**. I was so intrigued, I [started playing
around with
it](http://www.tjmaher.com/2016/07/setting-up-docker-easy-way-on-mac-or.html)\...
)*\
\
He mentions that Docker can reduce the time of test execution, ease the
setup of clean test environments and drastically reduce the differences
between the development, acceptance and production environments leading
to the higher quality of the released software. He gave examples to
containerize entire testing stack together consisting of major
automation tools like selenium.\
\
On his GitHub site, TestStack <https://github.com/irfanah/teststack>,
you can compare how much easier it is to setup his testing environment
with Docker than it is without Docker.\
**[\
]{.underline}[Video of the Demo]{.underline}**:\

\
\
\

Cross-platform, Multi-device Instant Communication Testing in Parallel using Appium and Docker
----------------------------------------------------------------------------------------------

**Presenter**: Vivek Upreti, Hike Messenger\
\
Vivek\'s presentation talks about:\
\
\

-   End-to-End testing on cross-platforms across multiple devices.
-   Driving different testing aspects in parallel.
-   How using Docker you can avoid the overhead of spawning one VM
    (heavy weight & time consuming) per device 

\
Vivek walks users through \"Dockerizing\" his tests in his Appium Docker
Demo at\
<https://github.com/vbanthia/appium-docker-demo>\
\
\... But what I am really looking forward to see what they post is for
the\...\
\

Selenium Grid Workshop
----------------------

**Presenter**: Luke Inman-Semerau, Salesforce\
<https://confengine.com/selenium-conf-2016/proposal/2307/grid-workshop>\
\
According to his notes he walks people through installing Docker and
pulling into it:\

-   Selenium Hub
-   Selenium Node / Firefox 
-   Selenium Node /
    Chrome: <https://gist.github.com/lukeis/81a91d6fd71738d51ba1>
-   Selenium Standalone version of Firefox
-   Selenium Standalone version of Chrome

\
\
He also uses:\

-   VirtualBox: <https://www.virtualbox.org/wiki/Downloads>
-   Microsoft Edge Virtual Machine:  <http://dev.modern.ie/tools/vms>
-   MicrosoftWebDriver:
    <https://developer.microsoft.com/en-us/microsoft-edge/tools/webdriver/>
-   Selenium Grid Extras plugin:
    <https://github.com/groupon/Selenium-Grid-Extras/releases>
-   Selenium Grid
    Scaler: <https://github.com/mhardin/SeleniumGridScaler>

\

Other Projects: Docker-Selenium
-------------------------------

\
There is also a relatively new project SeleniumHQ\'s Docker-Selenium
at <https://github.com/SeleniumHQ/docker-selenium> where they have
Docker images for Chrome nodes, Firefox Nodes. It also walks you through
setting up Selenium Grid Hub, nodes, etc.\
\
Individual Docker images can be found
at <https://hub.docker.com/r/selenium/>\
\
\... This, I definitely need to try out! \... and document \... and blog
about.\
\
Happy Testing!\
\
-T.J. Maher\
Sr. QA Engineer,\
Fitbit-Boston\
\
*// BSCS, MSE, and QA Engineer since Aug. 1996\
// Automation developer for \[ 1.5 \] years and still counting!\
// Check out Adventures in Automation and Like us on
[Facebook](https://www.facebook.com/AdventuresInAutomation/)!*
