\-\-- layout: post title: \'Using Docker + Jenkins for Continuous
Integration: Assorted Links\' date: \'2016-07-09T08:55:00.000-04:00\'
author: T.J. Maher tags: - SeleniumGrid - Docker - Jenkins
modified\_time: \'2016-07-09T09:00:12.675-04:00\' blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-7726909560811918389
blogger\_orig\_url:
http://www.tjmaher.com/2016/07/using-docker-jenkins-for-continuous.html
\-\-- So much to do! So little time! There are so many pieces I need to
add to my new little automated test framework,
**Test\_TheInternet\_2.0** found at
<https://github.com/tjmaher/Test_TheInternet_2.0>. You can see what is
on my \"wish list\" at the end of this blog post.\
\
But what I really want to do is experiment with setting up my own
[Jenkins](https://jenkins.io/) environment on my home system, something
DevOps does at my workplace. I create, at work, Jenkins jobs to run
tests, but it is not the same thing as being able to tinker with
[Jenkins Plugins](https://wiki.jenkins-ci.org/display/JENKINS/Plugins),
set up the system, etc.\
\
I found out the other day that on Docker Hub, **Jenkins has its own
Docker image**! <https://hub.docker.com/_/jenkins/>! That is definitely
something I really want to tinker with.\
\
\

-   *Not familiar with Docker? Read more about [Docker on this
    blog](http://www.tjmaher.com/search/label/Docker)!*
-   *Not familiar with Jenkins? Read more about [Jenkins on this
    blog](http://www.tjmaher.com/search/label/Jenkins)!*

\
\
Instead, here are some links that I was planning on checking out that I
wanted to share with you. I probably won\'t be able to get to this for
another few months or so, at the rate I am going:\
\

-   Access **The State of Docker, Jenkins and Continuous Delivery**
    survey infographic:
    <https://pages.cloudbees.com/rs/083-PKZ-512/images/Docker-Jenkins-Survey-Infographic.pdf>
-   Get the whitepaper **Jenkins, Docker and DevOps: The Innovation
    Catalysts: **<https://pages.cloudbees.com/Website_Docker-Jenkins.html?lsd=WebsiteForm_DockerJenkins>
-   Learn more about **Continuous delivery with Docker**:
    <https://www.cloudbees.com/continuous-delivery/jenkins-docker>
-   Watch the webinar **Continuous Delivery with Jenkins Pipeline and
    Docker
    Explained: **<https://pages.cloudbees.com/2016-0120-Jenkins-Workflow-Explained-Registration-Landing-Page.html>

\
The plan is to finish off the automated test framework we started:
**Test\_TheInternet\_2.0**. You can see the source code
at <https://github.com/tjmaher/Test_TheInternet_2.0>\

-   **RemoteWebDriver: **Taking
    our [DesiredCapabilities](https://github.com/SeleniumHQ/selenium/wiki/DesiredCapabilities) we
    touched upon, and expand it. 
-   **Docker Compose**: <https://docs.docker.com/compose/>: Bundle
    together scaling up or down Selenium Grid browser nodes, downloading
    Selenium Grid, starting up a Hub, and starting up various nodes.
-   **MicrosoftWebDriver**:
    ( [Link](https://www.microsoft.com/en-us/download/details.aspx?id=48212) ):
    How to incorporate Microsoft Edge into your tests.
-   **Microsoft Virtual
    Images**: <https://developer.microsoft.com/en-us/microsoft-edge/tools/vms/> add
    IE8, IE9, IE10, IE11 on Windows 7 or IE 11 and Microsoft Edge to
    Windows 10 nodes to your Selenium Hub! Just use VirtualBox, Vagrant,
    HyperV (Windows), VMWare, or Parallels (Mac). Take a snapshot of the
    images because the originals are only good for 90 days. *(What, no
    Docker solution? Gee, Microsoft, do you always have to be
    different?)*
-   **Selenium Grid
    Extras**: <https://github.com/groupon/Selenium-Grid-Extras>

\... I also want to check out what Sauce Labs has for its own sample
test framework in
Java-Junit-Selenium: <https://github.com/saucelabs-sample-test-frameworks/Java-Junit-Selenium>\
\
As always, Happy Testing!\
\
-T.J. Maher\
Sr. QA Engineer,\
Fitbit-Boston\
\
*// BSCS, MSE, and QA Engineer since Aug. 1996\
// Automation developer for \[ 1.5 \] years and still counting!\
// Check out Adventures in Automation and Like us on
[Facebook](https://www.facebook.com/AdventuresInAutomation/)!*
