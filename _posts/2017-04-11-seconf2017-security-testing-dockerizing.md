\-\-- layout: post title: \'SeConf2017: Security Testing, Dockerizing
Tests using Appium, Notes\' date: \'2017-04-11T08:00:00.000-04:00\'
author: T.J. Maher tags: - appium modified\_time:
\'2017-04-17T08:17:09.680-04:00\' thumbnail:
https://i.ytimg.com/vi/3k922FTnGb8/default.jpg blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-8072465295451645790
blogger\_orig\_url:
http://www.tjmaher.com/2017/04/seconf2017-security-testing-dockerizing.html
\-\-- **Security Test Driven Development (STDD) Using Selenium /
Appium**\
Surendran Ethiraj\

\
<https://youtu.be/3k922FTnGb8>\
\
Although many people think security testing is important, there aren't
many people implementing it sprint-by-sprint. To really help, security
tests need to be easy to run, and they should be automated. Security
should be in the DEV cycle, not waiting until the product is done.\
\
**Slides**:
<https://www.slideshare.net/ATASlides/atagtr2017-security-test-driven-development-stdd>\
\
Surendran is using OWASP ZAP (the [Zed Attack
Proxy](https://www.owasp.org/index.php/OWASP_Zed_Attack_Proxy_Project)
Project ) , FindBugs, and TestNG to set up security tests in the video.\
\
[]{#more}\
\
\
**FindBugs, **a project out of University of Maryland,** **uses static
analysis to look for bugs in Java code.\
\

-   **Eclipse**: Plugin <https://github.com/findbugsproject/findbugs> 
-   **IntelliJ**: FindBugs-IDEA
    <https://plugins.jetbrains.com/plugin/3847-findbugs-idea> 

\
ZAP is used as a proxy, but you can use
[BurpSuite](https://portswigger.net/burp/),
[WireShark](https://www.wireshark.org/), etc.\
\
Surendran demoed a Jenkins project, he created called Project STDD. Code
is deployed locally using Tomcat. Tests are run from Maven.\
\
Note: ZAP can give you false positives. They thought of: What is more
important? Detecting cross-site scripting? Or X-Frames? They filter what
bugs they want to find.\
\
Using [XPansion](http://en.soft-xpansion.eu/) after running the job can
be shown so you can submit bugs directly to developers.\
\

-   You can also see the complete ZAP report.
-   You cannot find Cross Site Scripting until you add Dynamic Testing.
-   Some of theses tools can be used on not just the web and Selenium,
    but with mobile and Appium.

\
\
ZAP is a good starting point. It is updated every three years, testing
for the OWASP Top Ten. He recommends moving on from there to Wireshark.\
\
For Forensic Analysis, use [Splunk](https://www.splunk.com/) as a a
tool, to see if there are any passwords getting leaked.\
\
\
**Test Inside Containers: Dockerize Appium Tests**\
Srinivasan Sekar -- Senior Consultant, ThoughtWorks\

<https://youtu.be/jGW6ycW_tTQ>\
**[\
]{.underline}[Virtual Machine vs Docker:]{.underline}**\
\
VMs use a Hypervisor to simulate hardware, with each application needing
its own guest operating system. Docker is more lightweight, with only a
Docker Engineer and the operating system between the apps and the
infrastructure. You can spin up three or four thousand containers up in
seconds. A virtual machine can take five or six minutes to spin up.\
\
We've [tinkered with
Docker](http://www.tjmaher.com/search?q=docker)before in this blog, but
haven't really gone beyond that. Docker is an open platform for
developing, shipping, and running applications. As we've seen, Docker is
a client / server architecture, where the client can do:\
\

-   *docker build*
-   *docker pull*
-   *docker run*

\
This interacts with the REST API on DOCKER\_HOST to create a docker
image. With this docker image, we can spin up thousands of images.\
\
The challenge when mobile testing is that there are so many devices you
need to test on, it takes a long time to execute a test, it takes time
to get good test coverage, and a few of the tests may themselves be
unreliable.\
\
The tests may work fine on Samsung Galaxy 6, but do the tests run on the
earlier Marshmallow operating system?\
\
Appium is an open source, cross-platform test automation tool for
native, hybrid and mobile web are mobile apps. Installing earlier
versions of Appium was a pain. It also has many dependencies: Node.js,
Java, Apple Developer tools, Xcode, Android, setup, etc. You needed to
install all the emulators. So much configuration!\
\
What if you could download one Docker image which had everything already
set up, and could be ready to start developing products within seconds?
A Docker Container has an application plus all dependencies, libraries,
other binaries, and configuration files needed to run it all in one
package. The container is a portable runtime environment. Imagine if you
could even put emulators in the containers? If you want to see what is
running, have a [RealVNC](https://www.realvnc.com/) server up and
running to see what is happening in the container.\
\
All the instructions are set up in a **DockerFile**. You can do this for
both Android and IOS, though to do iOS you need a Mac for development.
It sizes 1.8 GB for a docker image to be up and running.\
\
*Some of the sample code, from what I could see\...*\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 Public class DockerizeAppium extends BaseAndroidTest {  
   
 @Test  
 public void horizontalSwipingTest() trows Exception {  
   login();  
   driver.findElementByAcessibilityId(“slider”).click  
   MobileElement slider = [MobileElement];  
   driver.findElementByAccessibilityID( “slider”);  
   Dimension size = slider.getSize();  
   
   TouchAction swipe = new TouchAction(driver).press(slider, 0, size.height / 2).waitAction(2000)  
   .moveTo(slider, size.width / 2, size.height / 2).release();  
   swipe.perform;  
   
 private void login() {  
   New WebDriverWait(driver…  
```

\
\
Appium can be running in the Docker machine. You give IP address of the
Docker machine where the tests are and point them to the environment.\
\
Let's say we want to run Docker and mount a device so that the test can
be run on a real Android device.\
*docker run -d -P ---privileged -v /dev/bus/usb1/dev/hub/usb ---name
appium appium*\
\
In his example, to find what port it is running:\
\
*Docker ps -a*\
\
==\> Port 0.0.0.0:32769-\>4723, 0.0.0.0.:32768-\>5900/tcp\
\
docker-machine ip\
\
==\> 192.168.99.103\
\
We need to copy the React Native app:\
*docker cp /Users/ssekar/IdeaProjects/DockerAppium/VodQA.apk
Appium:/opt*\
*docker logs Appium*\
\
You can pull up the logs to see what is happening in the Docker
container, such as if Appium is running. You can also switch inside the
container.\
\
*docker exec -t appium /bin./sh*\
\
Any real devices connected?\
\
*\#adb devices // No, none.*\
*\#exit*\
\
Let's say we want to switch from Android to IOS:\
Remove the Appium docker container: *docker rm -f appium*\
\
Docker has also Docker Compose where you can group up things such as:\
\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 appium-android:  
   image: appium  
   privileged: true  
   container_name: appium  
   volumes:  
     - /dev/bus/usb:/dev/bus/usb  
     - ./VodQA.apk:/opt/VodQA.apk  
   ports:  
      - 4723:4723  
 java-maven:  
   image: javamvn  
   container_name: javamvn  
   volumes:  
     - ./:/home  
   command: mvn clean test  
  links:  
   - appium-android: localhost  
```

\
This means the tests are also containerized. Another container has java
maven.\
\
Now, we just need:\
*docker-compose up*\
\
It runs two containers:\
\

-   Creating Appium
-   Creating javamvn
-   Attaching to Appium, javamvn
-   It downloads all dependencies

\
\
References:\
\

-   <https://github.com/appium/appium-docker-android/tree/master/Appium>
-   <https://github.com/appium/appium-docker-android>
-   <https://github.com/SeleniumHQ/docker-selenium>
-   <https://github.com/appium>
-   <https://github.com/SrinivasanTarget/awesome-appium>
-   <https://github.com/saikrishna321/AppiumTestDistribution>

\
\
\
\
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
