\-\-- layout: post title: \'Build a Basic Appium Framework: Set up the
Page Objects, Page Factories and Tests\' date:
\'2017-05-30T22:08:00.000-04:00\' author: T.J. Maher tags: - Page Object
- appium - Page Factory modified\_time:
\'2017-06-16T20:15:12.440-04:00\' blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-8642775153972070703
blogger\_orig\_url:
http://www.tjmaher.com/2017/05/basic-appium-framework-part-four.html
\-\-- *This is part four of of a seven-part blog series. Care to
go [back to the
beginning](http://www.tjmaher.com/2017/05/basic-appium-framework-part-one.html)?*\
\
Now, let\'s wrap things up by setting up a few **Page Objects**, add the
**Page Factory pattern** to these building blocks we are creating, and
then compose the test we designed all the way in [Part
Two](http://www.tjmaher.com/2017/05/basic-appium-framework-part-two.html).\
\

### BeforeSuite and AfterSuite Annotations

\
First things first\... Remember how we made in the last chapter
installing and launching the app itself the test?\
\
Let\'s change that, placing it in a **\@BeforeSuite** annotation from
TestNG.\
\
[]{#more}\
\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 import io.appium.java_client.android.AndroidDriver;  
 import io.appium.java_client.remote.MobileCapabilityType;  
 import io.appium.java_client.remote.MobilePlatform;  
 import org.openqa.selenium.remote.DesiredCapabilities;  
 import org.testng.annotations.AfterSuite;  
 import org.testng.annotations.BeforeSuite;  
 import org.testng.annotations.Test;  
   
 import utils.*;  
   
 import java.io.File;  
 import java.net.MalformedURLException;  
 import java.net.URL;  
 import java.util.concurrent.TimeUnit;  
   
 public class SmokeTest {  
   
   private static AndroidDriver driver;   
   
   @BeforeSuite  
   public void DesiredCapabilities() throws MalformedURLException {  
     final String URL_STRING = "http://127.0.0.1:4723/wd/hub";  
   
     URL url = new URL(URL_STRING);  
   
     File app = new File("ApiDemos-debug.apk");  
     DesiredCapabilities caps = new DesiredCapabilities();  
     caps.setCapability(MobileCapabilityType.DEVICE_NAME, "emulator-5554");  
     caps.setCapability(MobileCapabilityType.APP, app.getAbsolutePath());  
     caps.setCapability(MobileCapabilityType.PLATFORM_NAME, MobilePlatform.ANDROID);  
   
     driver = new AndroidDriver(url, caps);  
   
   }  
```

\
It\'s the same code we had before, with the same import statements,
except we are saying we want to set up the driver before the test suite
runs.\
\
Let\'s pair the **\@BeforeSuite** annotation that creates an instance of
the Android driver with **\@AfterSuite** that tears down the driver.\
\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
   @AfterSuite  
   public void tearDownAppium() throws Exception {  
     System.out.println("\nTearing Down Driver.");  
     driver.quit();  
   }  
```

\
Frustrated with what Cédric Beust saw as too many limitations with JUnit
3, he created what he thought of as the Next Generation of Java Test
Runner Frameworks, with new sets of annotations in what he dubbed
**TestNG**, such as **\@BeforeSuite** and **\@AfterSuite**.** **\
\
\... JUnit 4 and JUnit5 (used with Java 8) then integrated much of the
new functionality into its own test framework, so it really doesn\'t
matter if you use:\
\

-   **JUnit**: <http://junit.org/>
-   **TestNG**: <http://testng.org/>

\
\... JUnit calls its annotations **\@BeforeClass** and **\@AfterClass**
\... but in my experience, it doesn\'t really matter. Nowadays, they are
pretty interchangeable, but it is good to learn both.\
\
Personally, I favor TestNG. Let\'s say that a more advanced automation
developer than I has already crafted a multi-threaded automation
framework, ready for me to use, I can then add code such as:\
\
*\<suite name=\"My suite\" parallel=\"tests\" thread-count=\"20\"\>*\
\
\... And we then can have twenty tests running in parallel\... We can
also bundle up tests, setting different tests to use different XML
configuration files TestNG then can use.\

<div>

\

</div>

<div>

That appears to be the only difference when it comes to using either
TestNG ot JUnit as test runners for automation frameworks.\
\
This Before and After blocks separate out code from the main test.
Picture twenty tests, all running at the same time. Every single test
needs to have an Android driver declared in the beginning, and torn down
in the end. 

</div>

###  Constructing the Building Blocks: Page Objects

<div>

</div>

<div>

When we were first sketching out the three pages we were going to
interact with in this test, we had the HomeScreenPage, the
InnerApiDemosPage, and the LogTextBoxPage. If we created a Java class
for each page we would interact with, they would look like:\

-   [HomeScreenPage.java](https://github.com/tjmaher/basic_appium_framework/blob/master/src/test/java/pages/HomeScreenPage.java):
    The first screen of the app that displayed
-   [InnerApiDemosPage.java](https://github.com/tjmaher/basic_appium_framework/blob/master/src/test/java/pages/InnerApiDemosPage.java):
    The second screen of the app.
-   [LogTextBoxPage.java](https://github.com/tjmaher/basic_appium_framework/blob/master/src/test/java/pages/LogTextBoxPage.java):
    The page we really wanted to get to! 

\... Here, we are organizing the code that Appium will use to manipulate
the mobile elements on each page into each separate Java class. If a
selector value on the Home Screen, such as the value of the button
labeled \"Text\" changes, we could know exactly where to go to make the
change for the page. 

</div>

\
\
*\"**Page Object** is a Design Pattern which has become popular in test
automation for enhancing test maintenance and reducing code duplication.
A page object is an object-oriented class that serves as an interface to
a page of your AUT (Application Under Test). The tests then use the
methods of this page object class whenever they need to interact with
the UI of that page. The benefit is that if the UI changes for the page,
the tests themselves don\'t need to change, only the code within the
page object needs to change. Subsequently all changes to support that
new UI are located in one place.*\
\
*\"The Page Object Design Pattern provides the following advantages*\
*\
\"1. There is a clean separation between test code and page specific
code such as locators (or their use if you\'re using a UI Map) and
layout.\
\
\"2. There is a single repository for the services or operations offered
by the page rather than having these services scattered throughout the
tests.\
\
\"In both cases this allows any modifications required due to UI changes
to all be made in one place. Useful information on this technique can be
found on numerous blogs as this \'test design pattern\' is becoming
widely used. We encourage the reader who wishes to know more to search
the internet for blogs on this subject. Many have written on this design
pattern and can provide useful tips beyond the scope of this user
guide\".*  - [Selenium HQ, Test Design
Considerations](http://www.seleniumhq.org/docs/06_test_design_considerations.jsp)\

<div>

\
With these Page Objects, let\'s use the **PageFactory** pattern, as
detailed in <https://github.com/SeleniumHQ/selenium/wiki/PageFactory>\
\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 public class HomeScreenPage {  
   
   private AndroidDriver driver;  
   
   @AndroidFindBy(id = "android:id/action_bar")  
   private MobileElement header;  
   
   @AndroidFindBy(accessibility = "Text")  
   private MobileElement textButton;  
   
   public HomeScreenPage(AndroidDriver driver) {  
     this.driver = driver;  
     PageFactory.initElements(new AppiumFieldDecorator(driver, 30, TimeUnit.SECONDS), this);  
   }  
   
   public void verifyHeader(){  
     System.out.println("HOME_SCREEN_PAGE: Verifying Header appears.");  
     WebDriverWait wait = new WebDriverWait(this.driver, 30);  
     wait.until(ExpectedConditions.visibilityOf(header));  
   }  
   
   public void selectTextButton(){  
     WebDriverWait wait = new WebDriverWait(driver, 30);  
     wait.until(ExpectedConditions.elementToBeClickable(this.textButton));  
   
     System.out.println("HOME_SCREEN_PAGE: Selecting [TEXT] button.\n");  
     this.textButton.click();  
   }  
 }  
```

\
We are creating two public methods that can be used in our main \@Test.
If someone instantiates this HomeScreenPage, they can use these methods
to:\
\

-   Verify the header appears
-   Select the button labelled \"Text\" with Appium using WebDriver\'s
    \"click\" method. 

<div>

Remember how we investigate the APIDemos-debug.apk and found the
locators of the two mobile elements we are interacting with? We are
capturing those values in the private variables \"header\" and
\"textButton\". 

</div>

<div>

\

</div>

<div>

Why private? We don\'t want a test to interact with those mobile
elements directly. What if the locators change? 

</div>

<div>

\

</div>

<div>

We are using an Object Oriented Principal called **Encapsulation**. 

</div>

\
*\"Encapsulation in Java is a mechanism of wrapping the data (variables)
and code acting on the data (methods) together as a single unit. In
encapsulation, the variables of a class will be hidden from other
classes, and can be accessed only through the methods of their current
class. Therefore, it is also known as data hiding.\
\
\"To achieve encapsulation in Java −*\

-   *\"Declare the variables of a class as private.*
-   *\"Provide public setter and getter methods to modify and view the
    variables values\".*

\- [TutorialsPoint, Java,
Encapsulation](https://www.tutorialspoint.com/java/java_encapsulation.htm)\
\

### Creating Constructors

What about the following code? What does it do?\

``` {style="background: rgb(240, 240, 240); border: 1px dashed rgb(204, 204, 204); font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; width: 646.469px;"}
   public HomeScreenPage(AndroidDriver driver) {  
     this.driver = driver;  
     PageFactory.initElements(new AppiumFieldDecorator(driver, 30, TimeUnit.SECONDS), this);  
   } 
```

\
\... This is called a **constructor**.\
\
*\"A class contains constructors that are invoked to create objects from
the class blueprint. Constructor declarations look like method
declarations---except that they use the name of the class and have no
return type\". - Oracle\'s [Java Tutorials -
Constructors](https://docs.oracle.com/javase/tutorial/java/javaOO/constructors.html)*\
\
If in our test we create a new instance of the HomePageScreen and pass
an AndroidDriver to it, it will automatically initialize all mobile
elements on the page, waiting up to thirty seconds if need be before
failing this step.\
\
Next, we call AppiumFieldDecorator. It is the \"Default decorator for
use with PageFactory. Will decorate 1) all of the WebElement fields and
2) List of WebElement that have \@AndroidFindBy, \@AndroidFindBys, or
\@iOSFindBy/\@iOSFindBys annotation with a proxy that locates the
elements using the passed in ElementLocatorFactory\".\
\
\... What does that mean? **I honestly have no clue.**\
\
I know that it is part of the [Decorator Design
Pattern](https://sourcemaking.com/design_patterns/decorator).
[TutorialsPoint
says](https://www.tutorialspoint.com/design_pattern/decorator_pattern.htm)
it \"allows a user to add new functionality to an existing object
without altering its structure. This type of design pattern comes under
structural pattern as this pattern acts as a wrapper to existing class.
This pattern creates a decorator class which wraps the original class
and provides additional functionality keeping class methods signature
intact\".\
\
\... I am guessing it allows the FindBy\'s, whether of type IOS, Android
or Web to be initialized with the same code.\
\
**Object Oriented Programming Design Patterns** have always made my eyes
cross, ever since grad school.
See <http://www.tjmaher.com/2015/06/meetup-how-to-study-design-patterns.html>
in order to make your head spin.\
\
Let\'s skip over the code walkthrough of the InnerApiDemos page. It
looks almost exactly like the HomeScreenPage. That brings us to\...\
\

### LogTextBoxPage

\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 public class LogTextBoxPage {  
   
   private AndroidDriver driver;  
   
   @AndroidFindBy(id = "android:id/action_bar")  
   private MobileElement header;  
   
   @AndroidFindBy(accessibility = "Add")  
   private MobileElement addButton;  
   
   @AndroidFindBy(id = "io.appium.android.apis:id/text")  
   private MobileElement panel;  
   
   public LogTextBoxPage(AndroidDriver driver) {  
     this.driver = driver;  
     PageFactory.initElements(new AppiumFieldDecorator(driver, 30, TimeUnit.SECONDS), this);  
   }  
   
   public void verifyHeader(){  
     System.out.println("LOG_TEXT_BOX_PAGE: Verifying Header appears.");  
     WebDriverWait wait = new WebDriverWait(this.driver, 30);  
     wait.until(ExpectedConditions.visibilityOf(header));  
   }  
   
   public void selectAddButton(){  
     WebDriverWait wait = new WebDriverWait(driver, 30);  
     wait.until(ExpectedConditions.elementToBeClickable(this.addButton));  
   
     System.out.println("LOG_TEXT_BOX_PAGE: Selecting [ADD] button.\n");  
     this.addButton.click();  
   }  
   
   public String getPanelText(){  
     return this.panel.getText();  
   }  
 }  
```

\
\... Here, we have a new public method, getPanelText. Appium is using
Selenium WebDriver\'s getText() method to grab the text appearing, and
return it as a String.\

###  Putting Together a Smoke Test 

Now that we have all these building blocks constructed, we can put
together our first test!\
\
We need to add to the BeforeSuite:\
\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 public class SmokeTest {  
   
   private static AndroidDriver driver;  
   private HomeScreenPage homeScreen;  
   private InnerApiDemosPage innerApiDemoScreen;  
   private LogTextBoxPage logTextBoxPage;  
   
   @BeforeSuite  
   public void DesiredCapabilities() throws MalformedURLException {  
     final String URL_STRING = "http://127.0.0.1:4723/wd/hub";  
   
     URL url = new URL(URL_STRING);  
   
     File app = new File("ApiDemos-debug.apk");  
     DesiredCapabilities caps = new DesiredCapabilities();  
     caps.setCapability(MobileCapabilityType.DEVICE_NAME, "emulator-5554");  
     caps.setCapability(MobileCapabilityType.APP, app.getAbsolutePath());  
     caps.setCapability(MobileCapabilityType.PLATFORM_NAME, MobilePlatform.ANDROID);  
   
     driver = new AndroidDriver(url, caps);  
     homeScreen = new HomeScreenPage(driver);  
     innerApiDemoScreen = new InnerApiDemosPage(driver);  
     logTextBoxPage = new LogTextBoxPage(driver);  
   }  
   
```

\
\... We are declaring the three Page Objects, then declaring three new
instances, placing them in their respective page object variables,
*homescreen, innerApiDemosScreen*, and *logTextBoxPage*. They are now
all ready to be used for our test!\
\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 @Test  
   public void test_login() throws Exception {  
     driver.manage().timeouts().implicitlyWait(30, TimeUnit.SECONDS);  
   
     homeScreen.verifyHeader();  
     homeScreen.selectTextButton();  
   
     innerApiDemoScreen.verifyHeader();  
     innerApiDemoScreen.selectLogTextBoxButton();  
   
     logTextBoxPage.verifyHeader();  
     logTextBoxPage.selectAddButton();  
   
     String expectedPanelText = "This is a test";  
     String actualPanelText = logTextBoxPage.getPanelText();  
   
     System.out.println("Checking panel text...");  
   
     TestUtils.outputIfMatchPassOrFail(expectedPanelText, actualPanelText);  
     assertThat(actualPanelText,containsString(expectedPanelText));  
   }  
```

\
\
\... After all of the clicking on buttons and verifying the headers
load, the true test is:\
\

-   Selecting the Add Button.
-   Grabbing the text from the display panel.
-   Comparing the actual text with the text we expect. 
-   Assert that the actual and expected text matches. 

\
Running the test we get\....\
\

``` {style="background-color: #f6f8fa; border-radius: 3px; box-sizing: border-box; color: #24292e; font-family: SFMono-Regular, Consolas, "Liberation Mono", Menlo, Courier, monospace; font-size: 13.6px; font-stretch: normal; line-height: 1.45; margin-bottom: 16px; overflow: auto; padding: 16px; word-wrap: normal;"}
HOME_SCREEN_PAGE: Verifying Header appears.
HOME_SCREEN_PAGE: Selecting [TEXT] button.

INNER_API_DEMOS_PAGE: Verifying Header appears.
INNER_API_DEMOS_PAGE: Selecting [LogTextBox] button.

LOG_TEXT_BOX_PAGE: Verifying Header appears.
LOG_TEXT_BOX_PAGE: Selecting [ADD] button.

Checking panel text...
Verifying Expected Value Matches Actual Value:
 * Expected Value: This is a test
 * Actual Value: This is a test

===> (PASS)

Tearing Down Driver.
```

\
Whew!\
\
Next blog post, I will walk you through how to download the source code
and run the tests on your local machine.\
\
\

<div>

::: {#toc-section .toc-section}
**Build a Basic Appium Framework**\

-   **Part One:** [Review How to Inspect Mobile Apps with Appium
    Desktop](http://www.tjmaher.com/2017/05/basic-appium-framework-part-one.html)
-   **Part Two:**  [Design a Basic Test, Examining Mobile Elements with
    Appium
    Desktop](http://www.tjmaher.com/2017/05/basic-appium-framework-part-two.html)
-   **Part Three:**  [Install and Launch an App Using Desired
    Capabilities](http://www.tjmaher.com/2017/05/build-basic-appium-framework-install.html)
-   **Part Four:**  [Set up the Page Objects, Page Factories and
    Tests](http://www.tjmaher.com/2017/05/basic-appium-framework-part-four.html)
-   **Part Five:**  [Download the tests and run them on your own
    MacBook!](http://www.tjmaher.com/2017/05/basic-appium-framework-part-five.html)
-   **Part Six:  **[How to create and launch an Android emulator from
    Android
    Studio](http://www.tjmaher.com/2017/05/launch-android-emulator.html)
-   **Part Seven**: [What happens behind the scenes as Appium installs
    and launches an Android app? Examining and footnoting a log
    file](http://www.tjmaher.com/2017/06/behind-the-scenes-install-launch-appium.html).
-   **GitHub: **[Review the source code for the
    project.](https://github.com/tjmaher/basic_appium_framework) 
:::

\
Happy Testing!

</div>

<div>

\

</div>

\
-T.J. Maher\

<div>

[Twitter](https://twitter.com/tjmaher1) \| [LinkedIn](https://www.linkedin.com/in/tjmaher1) \| [GitHub](https://github.com/tjmaher)\
\
*// Sr. QA Engineer, Software Engineer in Test, Software Tester since
1996.\
// Contributing Writer
for [TechBeacon.](http://techbeacon.com/contributors/thomas-maher)\
// \"Looking to move away from manual QA? Follow [Adventures in
Automation](http://www.tjmaher.com/) on
[Facebook](https://www.facebook.com/AdventuresInAutomation/)!\"*

</div>

</div>
