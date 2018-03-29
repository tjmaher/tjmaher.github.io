\-\-- layout: post title: \'Setup of Selenium Grid for Beginners: Brace
yourself! We\'\'re Using the Command Line\' date:
\'2016-07-04T19:42:00.003-04:00\' author: T.J. Maher tags: - beginner -
CommandLine - SeleniumGrid modified\_time:
\'2016-07-07T01:38:18.106-04:00\' thumbnail:
https://3.bp.blogspot.com/-KlJlQnwi0x4/V3neq2Z9ouI/AAAAAAAALNo/tTNORooJTOUZyZaB50BnBB6Qrcud0o3bgCLcB/s72-c/grid.png
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-8250833972812549512
blogger\_orig\_url:
http://www.tjmaher.com/2016/07/setup-of-selenium-grid-for-beginners.html
\-\-- Are you a manual tester who really wants to tinker with setting up
Selenium Grid with your automated test framework, but is skittish about
using a Command Line Interface? This blog entry is an attempt to walk
you through it, every step of the way. Is there a detail I missed?
Anything too vague? Please let me know in the comments section, below.
Using the Command Line is tough, but it is something every tester needs
to get used to\... with time, you will have fun using it. (Or that is
what I keep telling myself! :) )\
\

-   Don\'t have an automated test framework set up? Take a look at a
    basic one I have for
    [IntelliJ](http://www.tjmaher.com/2016/05/webdriver-development-environment-setup.html)
    and
    [Eclipse](http://www.tjmaher.com/2016/06/webdriver-development-environment-setup.html).

\
For this example, I will be setting up Selenium Grid a Windows 10 box,
what I use at home. Feel free to set it up on whatever Mac or Linux/
Unix operating system you have. We aren\'t going to be doing a deep dive
on any of the moving parts. That will come later. This article is
focusing on the setup.\
\
Directions can be found on **SeleniumHQ\'s Grid 2 GitHub**
site: <https://github.com/SeleniumHQ/selenium/wiki/Grid2>\
\
[]{#more}\
\

0. Pre-requisites:
------------------

**0.1.  Knowing how to start your Operating System\'s Command Line
Interface:**\

-   PC: If using Windows 10, in the \"Search Windows\" textbox next to
    the Start menu, type in: cmd
-   Mac: Start the \"Terminal\".

**0.2.  Because the Selenium Server is delivered as an Executable Java
Archive file** \-- a JAR file that can be run on your local machine \--
Java needs to be installed on your computer. Find out what Java version
you have.\
\

-    PC & Mac: Type in: java -version

\... If it is a bad command, you need to install Java onto your system.
Go to [Java.com](http://www.java.com/) to install Java.\
\

1. Setup a Directory for Selenium Server
----------------------------------------

\
**1.1.**  **Start your Operating System\'s Command Line Interface:**\
\

-   PC: Shortcut to Command Prompt: If using Windows 10, in the \"Search
    Windows\" textbox next to the Start menu, type in: cmd
-   Mac: Start the \"Terminal\".

\
**1.2.**  **Go to the root directory in the Command Line:**\
\

-   PC: Type in: cd \\
-   Mac: Type in: cd /

\
\
**1.3.**  **Create a folder called \"drivers\" at the root directory.
For this example, this will be the home of Selenium Server.**\

-   PC & Mac: Type in: mkdir drivers

\

2. Download Selenium Standalone Server
--------------------------------------

Set up the Selenium Server to run as a Hub.\
\
**2.1**.  **Get the latest copy of the Selenium Standalone Server, and
place it in a folder that is easily accessible.**\

-   Go to the SeleniumHQ Download Page
    at <http://docs.seleniumhq.org/download/> 
-   The link to the current version to download
    selenium-server-standalone is listed in the Selenium Standalone
    Server paragraph. At the time of this blog the download version is:
    2.53.1 
-   Right click on the link and select \"Save link as\...\" 
-   Save this executable Jar File somewhere easy to remember for now. I
    created for this example a directory called \"drivers\" on my C:
    drive and placed ***selenium-server-standalone-2.53.1.jar*** there. 

**\
2.2  Verify that the file has been created.**\

-   PC: The command \"dir\" shows the directory listing. Type in: dir
    \\drivers
-   Mac: The command \"ls\" shows the list of files in directory. Type
    in: ls /drivers 

Note: These commands will work wherever you are in your directory
structure. \"\\\" for the PC and \"/\" for the Mac acts as shortcuts to
go to the root directories.\
Make sure that the file listed
is: selenium-server-standalone-2.53.1.jar\
\

3. Start the Selenium Server
----------------------------

\
**3.1. Go to the directory where Selenium Server is located:**\

-   PC: Type in: cd \\drivers
-   Mac: Type in: cd /drivers

\
**3.2. Start the Selenium Server:**\
**\
**\

``` {style="background: rgb(240, 240, 240); border: 1px dashed rgb(204, 204, 204); font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; width: 646.469px;"}
 java -jar selenium-server-standalone-2.53.1.jar -role hub
```

<div>

``{style="word-wrap: normal;"}

</div>

That command will start the Selenium Server. Possibly. There may be
errors.\

-   Success: Message: Selenium Grid hub is up and running
-   Failure: Error messages, plus a huge stack trace and a help file.

\
Did you get a message such as Java.net.BindException: Address is already
in use? That\'s what happened to me. I may have accidentally
double-clicked multiple instances of Selenium Server when writing this
documention.\
\
By default, the Selenium Server runs on port 4444. You can shut down a
Selenium Server that failed by running:\

-   <http://localhost:4444/selenium-server/driver/?cmd=shutDownSeleniumServer>

Or, you can just choose another port to use. Take a note of what you are
using, such as port 4445:\
\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 java -jar selenium-server-standalone-2.53.1.jar -role hub -port 4445  
```

\
3.3.  Verify that the Selenium Server has started:\

-   Open up your favorite browser and go to: <http://localhost:4444/>
-   Check that you see:

\"You are using grid 2.53.1\
\"Find help on the official selenium wiki : [more help
here](https://github.com/SeleniumHQ/selenium/wiki/Grid2)\
\"default monitoring page
: [console](http://localhost:4444/grid/console)\"\
\

-   Select the link to the console. 

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://3.bp.blogspot.com/-KlJlQnwi0x4/V3neq2Z9ouI/AAAAAAAALNo/tTNORooJTOUZyZaB50BnBB6Qrcud0o3bgCLcB/s320/grid.png){width="320" height="193"}](https://3.bp.blogspot.com/-KlJlQnwi0x4/V3neq2Z9ouI/AAAAAAAALNo/tTNORooJTOUZyZaB50BnBB6Qrcud0o3bgCLcB/s1600/grid.png)
                                                                                                                   *Congratulations! It\'s a Selenium Hub!*
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

\

4. Setup a Selenium Node
------------------------

\
**4.1  Start Selenium Node**\
\
\

-   Open a new Command Line Interface, go to the drivers directory, and
    enter:

\
\

``` {style="background: rgb(240, 240, 240); border: 1px dashed rgb(204, 204, 204); font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; width: 646.469px;"}
 java -jar selenium-server-standalone-2.53.1.jar -role node -hub http://localhost:4444/grid/register  
```

\
You will see a message that the node is ready for use!\
\
Let\'s verify that:\

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://3.bp.blogspot.com/-0KVhBykTD1g/V3nlXLQ8t-I/AAAAAAAALOA/Enzkv36kgT8JpraY-QAKd3T35JS4X-DewCLcB/s400/console.png){width="400" height="381"}](https://3.bp.blogspot.com/-0KVhBykTD1g/V3nlXLQ8t-I/AAAAAAAALOA/Enzkv36kgT8JpraY-QAKd3T35JS4X-DewCLcB/s1600/console.png)
                                                                                                                              *My Windows 10 Machine*
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Note that the Hub is running on 192.168.1.5, port 5555
(http://192.168.1.5:5555)\
\
These are all the browsers on the machine you are using at the moment.
Since I\'m using as an Operating System Windows 10, that is what is
listed.\
\
Disregard the \"Remote Control (legacy)\" browsers those are for an
earlier version, Selenium RC.\
\
We can spin up three types of browsers for our automated test framework.
Hover your cursor over them to see the browser names. We will need them
later.\
\

Hook Up Selenium Grid with Your Automation Framework
----------------------------------------------------

What? Don\'t have an automated test framework ready to go? Not sure of
what one is? Follow one of these links to walk you through setting up a
new Gradle Java product, the Java Gradle plugin, setting up
dependencies,  creating browser tests in Firefox and Chrome, and how to
match values using Hamcrest:\

-   Using [IntelliJ](http://www.tjmaher.com/2016/05/webdriver-development-environment-setup.html) 
-   Using [Eclipse](http://www.tjmaher.com/2016/06/webdriver-development-environment-setup.html). 

Let\'s write a very quick-and-dirty WebDriver test to get us going:\
\

``` {.brush: .java}
@Test
public void test_FirefoxNavigatesToLoginPage() throws Exception  {
   driver = new FirefoxDriver();
   driver.get("http://the-internet.herokuapp.com/login");
   assertThat(driver.getTitle(), is(equalTo("The Internet")));
}
```

\
The test:\
\

-   Goes to Dave Haeffner\'s test
    site, <http://the-internet.herokuapp.com/login>
-   Opens up a new Firefox browser on your local machine
-   Asserts that the title is \"The Internet\". 

<div>

If we make the driver we are using an instance of RemoteWebDriver
instead of just WebDriver, we get a lot more flexibility. You can open
up browsers on other environments than on your local machine. If you are
on a Mac, you can set up and use browser nodes on a PC or a Linux
machine in your automated tests. All you would need to do is pass along
the location of your Selenium Hub (in this case,
\"http://192.168.1.5:5555/wd/hub\").

</div>

<div>

\

</div>

<div>

You can also set up, once you have the browser nodes, the corresponding
Desired Capabilities, setting up the:

</div>

<div>

-   Browsers: Chrome, Firefox, MS Edge, Android, etc.
-   Browser name, what you want to call the browser configuration you
    are setting up. 
-   Platform, whether generic Windows, Win8, Win10, generic Mac,
    Mountain Lion, El Capitan, etc. 

</div>

\
Remember, unless you are using Sauce Labs preset nodes, you need to have
a machine with the pre-existing capabilities.\
\
See <https://github.com/SeleniumHQ/selenium/wiki/DesiredCapabilities>
for a complete list.\
\
Let\'s do the same test again, but this time, call a RemoteWebDriver in
a setup method and handle the desired capabilities there.\
\

``` {.brush: .java}
public class LoginPageTest {
private RemoteWebDriver driver;

@Before
public void setUp() throws Exception {
   DesiredCapabilities capabilities = DesiredCapabilities.firefox();
   capabilities.setBrowserName("firefox");
   capabilities.setPlatform(Platform.WIN10);
   driver = new RemoteWebDriver(new URL("http://192.168.1.5:5555/wd/hub"), capabilities);
}

@Test
public void test_FirefoxGridNavigatesToLoginPage() throws Exception  {
   driver.get("http://the-internet.herokuapp.com/login");
   assertThat(driver.getTitle(), is(equalTo("The Internet")));
}

@After
public void closeBrowsers() throws Exception {
   driver.quit();
   }
}
```

\... And the test passed!\
\
Coming up in the next few weeks, now that we have the basics, we\'ll
build on that:\
\

-   We covered the [basics of
    Docker](http://www.tjmaher.com/2016/07/setting-up-docker-easy-way-on-mac-or.html),
    and the basics of Selenium Grid. **Next up**: We combine the two!
-   We add Selenium Grid to the automated testing framework w/ Gradle we
    started building
    in [IntelliJ](http://www.tjmaher.com/2016/05/webdriver-development-environment-setup.html) and [Eclipse](http://www.tjmaher.com/2016/06/webdriver-development-environment-setup.html),
    refactoring the DesiredCapabilities into its own library. 
-   We add multi-threading to the automated test framework, so we can
    run tests in parallel.

\
\
Happy Testing, and have a Happy Fourth of July!\
\
-T.J. Maher\
Sr. QA Engineer,\
Fitbit-Boston\
\
*// QA Engineer since Aug. 1996\
// Automation developer for \[ 1.5 \] years and still counting!\
// Check out Adventures in Automation out on
[Facebook](https://www.facebook.com/AdventuresInAutomation/)!*
