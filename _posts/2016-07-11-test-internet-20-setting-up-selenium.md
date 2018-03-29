\-\-- layout: post title: \'Test The-Internet 2.0: Setting up Selenium
Grid: RemoteDriver and DesiredCapabilities\' date:
\'2016-07-11T07:00:00.000-04:00\' author: T.J. Maher tags: -
SeleniumGrid - Docker - test framework - RemoteWebDriver modified\_time:
\'2016-07-11T07:27:42.773-04:00\' thumbnail:
https://1.bp.blogspot.com/-td245UgFxwk/V4Jbsmmjp4I/AAAAAAAALTU/f-gNFo25\_YEWrnafKSMl-6ksXb8Pe-nHgCLcB/s72-c/grid.png
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-8453950270468581734
blogger\_orig\_url:
http://www.tjmaher.com/2016/07/test-internet-20-setting-up-selenium.html
\-\-- **Recap**: Since May 2016, we\'ve been blogging about forming a
new **automated test framework** using Dave Haeffner\'s test site,
[The-Internet](http://the-internet.herokuapp.com/login).\
\
Picking **Gradle** as the build tool, we walked through how to create
unit tests, just to make sure everything is still working as we make
changes to the project, setting them up in **JUnit** and **Hamcrest** in
both [IntelliJ](http://www.tjmaher.com/2016/05/webdriver-development-environment-setup.html) and [Eclipse](http://www.tjmaher.com/2016/06/webdriver-development-environment-setup.html).\
\
Like the two frameworks we [built last
year](http://www.tjmaher.com/p/programming-projects.html), we are using
[CSS
Selectors](http://www.tjmaher.com/2015/04/how-selenium-webdriver-uses-css.html)
to find the web elements on a page. We grouped together pages using
the [Page Object Model and
PageFactories](http://www.tjmaher.com/2016/06/page-factories-setting-up-creating-them.html).
After walking through the reader with experimenting with first [Selenium
Grid](http://www.tjmaher.com/2016/07/setup-of-selenium-grid-for-beginners.html)
and then
[Docker](http://www.tjmaher.com/2016/07/setting-up-docker-easy-way-on-mac-or.html),
we set up Selenium Grid using official Docker [images from
Docker](http://www.tjmaher.com/2016/07/setting-up-selenium-grid-with-chrome.html)
Hub.\
\
\... I should call this blog post, \"How I spent my summer vacation\".
Each time we rewrite our test framework, I experiment on this blog with
tools and technologies we are using at work. Instead of spending four
hours reading a technical manual, I\'m spending the same amount of time
getting my hands dirty, taking notes all along the way. It takes no time
at all to turn all that research I collected into a blog post.\
\
With this blog post, we will be using **RemoteWebDriver** to bring in
the browser nodes listed in our **Selenium Grid**, connecting them with
**DesiredCapabilities** to help run our tests.\
\
[]{#more}\
\

Why Use RemoteWebDriver?
------------------------

\
Why use RemoteWebDriver over having each automated tester set up
Selenium Grid up on each local machine?\
\
It\'s not just because of Selenium Grid standardization: If your
automated test framework uses RemoteWebDriver, you can then hook up your
tests
to [SauceLabs](https://saucelabs.com/) or [Browserstack](https://www.browserstack.com/)\'s
Selenium Grid configuration, or even an internal company-wide Docker /
Selenium Grid.\
\

Run Selenium Grid
-----------------

\
Feel free to check my notes on how to setup [Docker
Toolbox](http://www.tjmaher.com/2016/07/setting-up-docker-easy-way-on-mac-or.html)
and [run
Docker-Selenium](http://www.tjmaher.com/2016/07/setting-up-selenium-grid-with-chrome.html) if
you want to run Selenium Grid from a Docker image. We are using
SeleniumHQ\'s Docker-Selenium site
at <https://github.com/SeleniumHQ/docker-selenium> and SeleniumHQ\'s
Docker images on the Docker Hub
at <https://hub.docker.com/u/selenium/>.\
\
There are mainly two ways to set up browsers with your automated test
framework: **Headless** and **within an actual browser**.\
\

-   **[Headless]{.underline}**: If you are diagnosing failures, watching
    WebDriver enter data into the browser in real time is very helpful.
    For every other time, when you just want to see what passed and what
    failed, you can run the tests in a *headless* fashion, i.e. without
    spinning up a browser. We are going to be setting up
    *[selenium/node-chrome](https://hub.docker.com/r/selenium/node-chrome/)*
    and
    *[selenium/node-firefox](https://hub.docker.com/r/selenium/node-firefox/)*
    in this fashion. 
-   **[Locally, in a browser]{.underline}**: Running the test using the
    browsers already installed on your system is the easiest way to
    debug a test. Yes, we can see what is happening by using
    *[selenium/node-chrome-debug](https://hub.docker.com/r/selenium/node-chrome-debug/)* and *[selenium/node-firefox-debug](https://hub.docker.com/r/selenium/node-firefox-debug/)*
    coupled with a  **VNC Viewer** (Virtual Network Computer) such as
    [Real VNC](https://www.realvnc.com/) to spy on what is happening in
    the browser. Or you can use the standalone Docker images of Chrome
    and Firefox. But locally is easier. 

\
Right now, we are going to be running our tests Headlessly, as they
would be set up in a Continuous Integration or Continuous Development
environment with Jenkins. Later, we will add running browsers locally,
and adding logging functionality, but I would rather that those topics
get their own blog entry.\
\
Setup for a Selenium Grid on your local environment is quicker:\

-   View the official SeleniumHQ instructions
    [here](http://www.seleniumhq.org/docs/07_selenium_grid.jsp).
-   Read my [walkthrough of setting up Selenium
    Grid](http://www.tjmaher.com/2016/07/setup-of-selenium-grid-for-beginners.html)
    on your local environment.

\
\... You can still connect that Selenium Grid setup to your automated
tests. You would just need to substitute your IP address and port number
with the one I get from using the Docker Terminal.\

###  How to Run an Existing Docker-Selenium Setup:

\
**Step 1: Blow away Old Docker-Selenium Containers**\
\
It\'s best to start off with a fresh instance of Docker Selenium. Check
for old instances of Docker-Selenium\

-   Start up Docker QuickStart Terminal from the [Docker
    Toolbox](http://www.tjmaher.com/2016/07/setting-up-docker-easy-way-on-mac-or.html) installation
-   Check what containers are running: *docker ps -a*
-   Stop all container from running: *docker stop \$(docker ps -a -q)*
-   Remove all containers: *docker rm \$(docker ps -a -q)*

**\
Step 2: Startup  Docker-Selenium:**\

-   Start up the Selenium Grid Hub and Nodes from the Docker Terminal:

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 docker run -d -p 4444:4444 --name selenium-hub selenium/hub:2.53.0  
 docker run -d --link selenium-hub:hub selenium/node-chrome:2.53.0   
 docker run -d --link selenium-hub:hub selenium/node-firefox:2.53.0   
```

\
**Step 3: Verify that Selenium Grid is Running**\
\
My Selenium Grid is set up to <http://192.168.99.100:4444/wd/>. Go to
the IP address and Port where you set up your Grid.\
\

::: {.separator style="clear: both; text-align: center;"}
[![](https://1.bp.blogspot.com/-td245UgFxwk/V4Jbsmmjp4I/AAAAAAAALTU/f-gNFo25_YEWrnafKSMl-6ksXb8Pe-nHgCLcB/s400/grid.png){width="400"
height="126"}](https://1.bp.blogspot.com/-td245UgFxwk/V4Jbsmmjp4I/AAAAAAAALTU/f-gNFo25_YEWrnafKSMl-6ksXb8Pe-nHgCLcB/s1600/grid.png)
:::

\
Ladies and Gentlemen, we have a Selenium Grid!\

 Run a Headless Firefox Test 
-----------------------------

We set up in the [last Test The-Internet
2.0](http://www.tjmaher.com/2016/07/setting-up-selenium-grid-with-chrome.html) post
a quick and dirty test that used **RemoteWebDriver** and
**DesiredCapabilities** to run a browser node off our Selenium Grid.\
\
Sample Code:\

``` {.brush: .java}
import org.junit.Test;
import org.openqa.selenium.Platform;
import org.openqa.selenium.remote.DesiredCapabilities;
import org.openqa.selenium.remote.RemoteWebDriver;

import java.net.URL;

import static org.hamcrest.CoreMatchers.is;
import static org.hamcrest.MatcherAssert.assertThat;
import static org.hamcrest.core.IsEqual.equalTo;

@Test
public void test_FirefoxDockerGridNavigatesToLoginPage() throws Exception  {
   DesiredCapabilities capabilities = DesiredCapabilities.firefox();
   capabilities.setBrowserName("firefox");
   capabilities.setPlatform(Platform.LINUX);
   driver = new RemoteWebDriver(new 
           URL("http://192.168.99.100:4444/wd/hub"), capabilities);
   driver.get("http://the-internet.herokuapp.com/login");
   assertThat(driver.getTitle(), is(equalTo("The Internet")));
}
```

<div>

\

</div>

Remember, with our setup right now, our test is using a Headless
Browser. We are just focusing on adding RemoteWebDriver functionality
with DesiredCapabilities in this blog entry, so we are only concerned at
the moment if the test passes or fails.\
\
We\'ll add running tests locally, and adding logging functionality with
a later blog post talking about diagnosing failures. For now, let\'s run
the test in IntelliJ (or whatever your favorite IDE is), and check to
see if the test passed:\
\

::: {.separator style="clear: both; text-align: center;"}
[![](https://2.bp.blogspot.com/-BkUJpazxvsQ/V4KiO-dXmYI/AAAAAAAALTs/F7rpzPytSksPw1M_Anhd2S_hbWLpwBzJACLcB/s400/test%2Bruns.png){width="400"
height="77"}](https://2.bp.blogspot.com/-BkUJpazxvsQ/V4KiO-dXmYI/AAAAAAAALTs/F7rpzPytSksPw1M_Anhd2S_hbWLpwBzJACLcB/s1600/test%2Bruns.png)
:::

\
Success! The test passed! Firefox ran the test, opened up Dave
Haeffner\'s [Login Page](http://the-internet.herokuapp.com/login) on his
site, The-Internet, and asserted that yes, the title was \"The
Internet\".\
\
There is a problem, though\...\
\
What is RemoteWebDriver, anyway? And what is DesiredCapabilities?\
\
Right now, we are using Firefox / Linux and Chrome / Linux as browser
nodes. Are we going to cut-and-paste the same code to set up
DesiredCapabilites each and every time?\
\
And should this test be in LoginPageTest? What if we want to expand the
test to be more robust, and you know, actually check to see if logging
in actually passes or fails?\
\
Let\'s go over what RemoteWebDriver is first. For the other concerns we
have, let\'s handle that in the Refactoring section.\

 What Is RemoteWebDriver?
-------------------------

\
RemoteWebDriver is the Java class that the SeleniumHQ people designed to
join their webserver with the automated tests. You can see the source
code of RemoteWebDriver on their GitHub site
at [openqa/selenium/remote/RemoteWebDriver.java](https://github.com/SeleniumHQ/selenium/blob/master/java/client/src/org/openqa/selenium/remote/RemoteWebDriver.java).\
\
With our test, we started a new WebDriver instance, and assigned it a
new **RemoteWebDriver** with the following line of code:\

-   new RemoteWebDriver(new URL(\"http://192.168.99.100:4444/wd/hub\"),
    capabilities);

<div>

That URL needs to match wherever your Selenium Grid is located, from IP
address, to port, to the correct directory. 

</div>

<div>

\

</div>

<div>

If you are running [SauceLabs](https://saucelabs.com/) or
[Browserstack](https://www.browserstack.com/)\'s Selenium Grid
configuration, or an internal Docker / Selenium Grid your entire company
uses, the URL needs to match. 

</div>

<div>

\

</div>

We then set up **DesiredCapabilities**:\

-   Instantiate a new DesiredCapabilities object
-   Declare it to be of method *firefox*
-   Set the browser name to be \"firefox\"
-   Set the platform to be Linux.
-   Make the DesiredCapabilities match exactly what we have running in
    our Selenium Grid.

\... Note, the name of the method is \"desired\" capabilities. A browser
node spun up by RemoteWebDriver may or may not have all those
properties. If you are attempting to use Firefox on a Mac or Windows
platform, and there isn\'t a browser node that is running on that
virtual (or real) platform, the Selenium Grid is going to run the next
best thing.\
\
You can also pass in a list of *RequiredCapabilities* along with the
DesiredCapabilities, but in my past few jobs I just haven\'t seen this
used.\
\
When you instantiate a RemoteWebDriver, that URL pointing to Selenium
Grid becomes the Command Executor. It then tries to:\

-   Start a new client on the Selenium Grid server.
-   Start a new session on the Selenium Grid server. 

With RemoteWebDriver you can use the following properties:\

-   Get and set a session id.
-   Get the W3C Standard Compliance level (an integer value).
-   Get the title, the current url, findElements by id, classname,
    cssSelector, XPath, by name, all the things you can do with a
    regular WebDriver.
-   Like WebDriver, you can also select by windowHandle, useful if there
    is a popup alert or multiple browser windows you need to
    *switchTo()*. 
-   Get the Screenshots taken as Base64 Encoded PNG or other formats by
    executing a DriverCommand.SCREENSHOT.
-   You can see if the browser you are using *isJavascriptEnabled()*.
-   You can setLogLevel by Level. 
-   Hrm\... tagged as \@Beta, there is a method called *setCredentials*,
    where you are passing in a Credentials object
    ([*org.openqa.selenium.security.Credentials*)]{style="background-color: white; color: #333333; font-family: "consolas" , "liberation mono" , "menlo" , "courier" , monospace; font-size: 12px; line-height: 16.8px; white-space: pre;"}.
    I need to look into that\... 

\
After a test has finished you can:\

-   Delete a cookie by name: deleteCookie(Cookie cookie)
-   Delete all cookies: deleteAllCookies();
-   Close the session: Note this just executes to the driver
    DriverCommand.Close: driver.close();
-   Quit the session: This closes the session as above, makes the
    sessionID to be *null*, then stops the client. It\'s much more
    graceful. 

What is DesiredCapabilities?
----------------------------

There are two types of DesiredCapabilities:  Ones for all browsers, and
ones that are browser-specific, such as for Chrome or Firefox.\
\
You can set:\

-   DesiredCapability: Sets the brower node you are hoping to find:
    android, iPad, iPhone, internetExplorer, firefox, chrome, edge
    (Microsoft Edge), operaBlink (
    [Blink](https://en.wikipedia.org/wiki/Blink_(web_engine)) is a
    Chromium based web browser engine that can be used in the Opera
    browser), phantomJS (a headless browser).  
-   BrowserName, Platform, Version (such as IE 9, IE 10, IE 11.
-   isJavaEnabled()

<div>

Are you going to be using SauceLabs?

</div>

<div>

\

</div>

<div>

**SauceLabs** has a new **Platform Configurator** on the Sauce Labs Wiki
at <https://wiki.saucelabs.com/display/DOCS/Platform+Configurator#/>\
\
Let\'s say we want to use Sauce Labs instead of our own Selenium Grid,
we can use their Platform Configurator to chose to set up for WebDriver
the Microsoft Edge on a Windows 10 platform with a screen resolution of
1024 x 768\... and let\'s pick a version of the Edge browser, too. If we
leave it blank, it will automatically search for the latest version.  

</div>

\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 DesiredCapabilities caps = DesiredCapabilities.edge();  
 caps.setCapability("platform", "Windows 10");  
 caps.setCapability("version", "13.10586");  
 caps.setCapability("screenResolution", "1024x768");  
```

\
You can learn more about how their Selenium Test Configurations
at <https://wiki.saucelabs.com/display/DOCS/Test+Configuration+Options>\

 Refactor RemoteWebDriver into a Driver Utilities Class 
--------------------------------------------------------

Let\'s take a look at that browser test we
have, *test\_FirefoxDockerGridNavigatesToLoginPage()*. What if other
tests want to use RemoteWebDriver? We shouldn\'t copy-and-paste that
code into each and every test. Let\'s put that in its own Java class\...
call it DriverUtils.\
\
While we are at it, let\'s move the test to an actual Test class, since
we are going to do more than just stay on the Login page\... we are
going to eventually want to make sure that we end up on the landing
page, SecureArea.\
\

``` {.brush: .java}
public class TestCases {
private static WebDriver driver;

@BeforeClass
public static void setUp() throws Exception {

}

@Test
public void test_FirefoxDockerGridNavigatesToLoginPage() throws Exception  {
   driver = DriverUtils.getGridDriver("firefox");
   LoginPage login = new LoginPage(driver);
   login.navigateToLoginPage(driver);
   assertThat(driver.getTitle(), is(equalTo("The Internet")));
}
@Test
public void test_ChromeDockerGridNavigatesToLoginPage() throws Exception  {
   driver = DriverUtils.getGridDriver("chrome");
   LoginPage login = new LoginPage(driver);
   login.navigateToLoginPage(driver);
   assertThat(driver.getTitle(), is(equalTo("The Internet")));
}
@AfterClass
public static void tearDown(){
   driver.quit();
}
}
```

\
To make the test code display better on the page, I moved everything
over five spaces to the left.\
\
We created a new utility class that I dubbed, \"DriverUtils.java\". In
it is a method I called getGridDriver. Pass in the String \"chrome\" or
\"firefox\", and the RemoteWebDriver and DesiredCapabilities for the
browser in the grid is set up.\
\

``` {.brush: .java}
public class DriverUtils {

public static RemoteWebDriver driver = null;

public static RemoteWebDriver getGridDriver(String browser) {
   System.out.println("Selenium Grid: Starting");
   DesiredCapabilities capabilities = getCapabilities(browser);
   try {
       driver = new RemoteWebDriver(
               new URL("http://192.168.99.100:4444/wd/hub"),
               capabilities);
   } catch (MalformedURLException e) {
       System.out.println("Selenium Grid: ERROR!\n" + e);
       e.printStackTrace();
    }
   return driver;
}

private static DesiredCapabilities getCapabilities(String browser){
   System.out.println("Browser: " + browser);
   DesiredCapabilities capabilities = DesiredCapabilities.firefox();
   if (browser.equals("firefox")) {
       capabilities = DesiredCapabilities.firefox();
   } else if (browser.equals("chrome")) {
       capabilities = DesiredCapabilities.chrome();
   } else {
       System.out.println("Browser not found: " + browser);
       System.out.println("Selecting: Firefox");
   }
   capabilities.setCapability("platform", Platform.LINUX);
   return capabilities;
}
}
```

\
The framework isn\'t perfect. We still haven\'t added:\
\

-   Multithreading, so we can run tests in parallel. 
-   Logging, such as with Log4J, telling what the test is doing. 
-   We can\'t run the test locally if we so chose. It would be nice to
    be able to have different configurations in IntelliJ where we could
    choose to run locally or through Selenium Grid. 

<div>

\... Each bullet point will be a future blog entry.  

</div>

<div>

\

</div>

<div>

More importantly the tests need a lot of work:

</div>

<div>

-   Sure the runs, but it doesn\'t do anything besides go to the Login
    Page! We need to add more to the test. 
-   The Firefox test and the Chrome test looks awfully similar. Maybe we
    can refactor the code, placing common elements of a test in its own
    private method? 

</div>

\
That part will happen in the next \"Test The-Internet 2.0\" themed blog
post.\
\
Until then, Happy Testing!\
\
-T.J. Maher\
Sr. QA Engineer,\
Fitbit-Boston\
\
*// BSCS, MSE, and QA Engineer since Aug. 1996\
// Automation developer for \[ 1.5 \] years and still counting!\
// Check out Adventures in Automation and Like us on
[Facebook](https://www.facebook.com/AdventuresInAutomation/)!*
