\-\-- layout: post title: \'Build a Basic Appium Framework: Install and
Launch an App Using Desired Capabilities\' date:
\'2017-05-20T11:28:00.000-04:00\' author: T.J. Maher tags: -
DesiredCapabilities - appium modified\_time:
\'2017-06-16T20:13:50.251-04:00\' thumbnail:
https://1.bp.blogspot.com/-lgIjJB-Ursc/WOWRrM4qVXI/AAAAAAAALuM/ZvUm4yCjNIoucjtNtIaup6GGhCSG1l4jACPcB/s72-c/screen-start-simple.png
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-8768776985584962784
blogger\_orig\_url:
http://www.tjmaher.com/2017/05/build-basic-appium-framework-install.html
\-\-- *This is part three of of a seven-part blog series. Care to go
[back to the
beginning](http://www.tjmaher.com/2017/05/basic-appium-framework-part-one.html)?*\
*\
INTERLUDE: Overheard at my workplace\... *\
*\
*\"Now, type on the next line, Capital-D, DesiredCapabilities, one word!
Then space, the word \'caps\', space, equals sign, the word \'new\',
Capital-D DesiredCapabilities, one word! Open-parentheses, then
close-parentheses, semi-colon.\
\
\"\... On the right side of the equation, we just declared a new
instance of the class DesiredCapabilities, part of the Selenium
WebDriver library. To the left of the equation, we are placing that
value in a variable we are calling \"caps\", and declaring that also to
be of type DesiredCapabilities\...\
\
\"\... Why is the word DesiredCapabilities underlined in red in our
editor? We haven\'t imported the library into our \'Smoketest.java\'
class. On the MacBook, it is CTRL+Enter to import. Press those keys at
the same time right after you see the DesiredCapability IntelliJ
tooltip. That is IntelliJ IDEA\'s \'Intellisense\' feature\...\"\
\
So far, I have spent two half-hour pair-programming sessions attempting
to train a manual tester on my team how to do automation development.
It\'s not exactly the blind-leading-the-blind, but it is pretty darned
close.\
\
I\'ve only been doing automation development [for the past two
years](https://techbeacon.com/coding-key-test-automation-career-are-you-prepared),
hopping around from Selenium WebDriver + Java [at
Fitbit](https://techbeacon.com/switching-careers-qa-manual-testing-automation-development),
Nightwatch Js + JavaScript + NodeJs [for a few
months](https://techbeacon.com/how-pass-coding-interview-automation-developer)
at Good Start Genetics. And I only have been teaching myself Appium
since March since I signed up for this six month contract at Stop &
Shop\'s parent company, where we are designing the next generation of
mobile apps for Stop & Shop, Giant Food, and Martin\'s.\
\
I have been working really hard to prove my worth over the past three
months as a contractor:\

-   Checking to see if we can used a favored automation tool used at
    this company,
    [SerenityBDD](http://www.tjmaher.com/2017/03/serenity-bdd-automation-framework-that.html),
    for mobile apps. (Answer? There really isn\'t that much
    documentation or support on it). 
-   Exploring [Appium
    Desktop](http://www.tjmaher.com/2017/04/learning-appium-what-is-appium-server.html),
    using that as a teaching tool to explain setting up an Appium
    environment
-   Putting together the [basic Appium
    framework](https://github.com/tjmaher/basic_appium_framework) 

\
My latest pet project is seeing if through one-on-one training I can get
a manual testers to be able to design their first automated test, then
add it to my basic test framework in a pull request\... all in just ten
half-hour sessions.\
\
One roadblock, besides the fact I only started teaching myself Appium +
Java in March when I was hired for this contract position? I can\'t
shake this cold I caught two weeks ago, and I keep on losing my voice.
My voice is a bullfrog croak and end up shouting in my trainee\'s ear
too loudly as I try to excitedly improvise a lesson for my first test
subject, a former SysAdmin who now is a manual tester on our project. He
has some tinkering in Java, but not much.\
\
\"Okay \-- brace yourself! This next code block will contain a lot of
typing\...\"\
\
**Rule Number One**: Trainees have to type everything out. Every
semi-colon. Every statement. Every code block.\
\
**Rule Number Two**: No wizards except the first one to set up the
initial project. I walked him through creating a new Gradle + Java
project with IntelliJ IDEA with the New Project Wizard. How to create a
new directory off of the root directory called \"src\". How to create a
sub-directory called \"test\". And another one called \"java\".\
**\
Rule Number Three**: Trainees have to do their own searching. Do we need
to import a new Java library into our project? I tell the trainee to
Google the word \"Maven Repository\". I describe to him how to go to and
search the [Mvnrepository.com](http://mvnrepository.com/) site for a
third party dependency for Appium\'s Java-Client library. I tell him to
copy-and-paste the code from the \"Gradle\" tab and back into our
build.gradle file, in the \'Dependencies\' code block.\
**\
Rule Number Four**: I saw on Twitter recently this question by a
beginning programmer:\
\

-   Is it okay to copy-and-paste code? 
-   To copy? Yes. To paste? No.

\... I am trying to have the trainee follow this dictum.\
\
\... Okay, enough about work. Let\'s get back to learning about
DesiredCapabilities, where we match the Appium Server that is running
with the Android emulator that is running. Three questions though\...\
\
\

### []{#more} How to Launch the App With Desired Capabilities?

\

-   Do you have the Appium server running, such as with Appium Desktop? 
-   Do you [have an Android emulator
    running](http://www.tjmaher.com/2017/05/launch-android-emulator.html)? 
-   Did you go to the Mac Terminal and type in \"adb devices\" to see
    the list of devices? Hopefully, you set up Android SDK in your
    bash.profile. If so, you should be able to launch \"adb\", and see
    the list of devices, such as *emulator-5554*. 

If so, running the following test will install and launch
**APIDemos-debug.apk** on your emulator.\
\
**[src/test/java/Smoketest.java]{.underline}**\

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

   @Test  
   public void DesiredCapabilities() throws MalformedURLException {  
     final String URL_STRING = "http://127.0.0.1:4723/wd/hub";  
     URL url = new URL(URL_STRING);  
     File app = new File("ApiDemos-debug.apk");  
     DesiredCapabilities caps = new DesiredCapabilities();  
     caps.setCapability(MobileCapabilityType.DEVICE_NAME, "emulator-5554");  
     caps.setCapability(MobileCapabilityType.APP, app.getAbsolutePath());  
     caps.setCapability(MobileCapabilityType.PLATFORM_NAME, MobilePlatform.ANDROID);  
     AndroidDriver driver = new AndroidDriver(url, caps);  
     driver.manage().timeouts().implicitlyWait(30, TimeUnit.SECONDS);  
   }  
```

\
With this article we will go over what all this code means, and how to
set up this test.\
\
\
To get this Java code to run, there are two things you need in your root
directory:\
\

-   A build.gradle file (or POM.xml file) to handle downloading and
    installing all third-party dependencies with Gradle (or Maven). You
    can see what I used in my repository
    [basic\_appium\_framework](https://github.com/tjmaher/basic_appium_framework) in
    the
    [build.gradle](https://github.com/tjmaher/basic_appium_framework/blob/master/build.gradle)
    file. 
-   You need to go to the sample app provided by the Appium project, in
    their java-client subsection, in
    [APIDemos-debug.apk](https://github.com/appium/java-client/blob/master/src/test/java/io/appium/java_client/ApiDemos-debug.apk)
    and select the Download button to download it to your local
    computer. Then, copy it, and paste it in the root directory of your
    project.

\... What? You don\'t know what Gradle is? [Let me tell you where you
can attend free courses on
Gradle](http://www.tjmaher.com/2016/06/free-udacity-course-gradle-for-android.html)!
It is what I am using for build configuration to handle my third party
dependencies.\

<div>

\

</div>

<div>

Twenty years ago, we would be using Unix\'s *makefile*. Ten years ago,
we may have used [Apache Ant](http://c2.com/cgi/wiki?ApacheAnt). Five
years ago (or now) we may have used Apache Maven. Now? I like using
[Gradle](http://gradle.org/). It\'s what they use in Android Studio.\

<div>

\

<div>

\
Here is what this code is doing\...\
\
**[\@Test ]{.underline}**\
\
This TestNG annotation is declaring this block of code as a \@Test with
TestNG, a testing framework much like JUnit. What is the difference?
Read *\"[JUnit vs TestNG: Which Testing Framework Should You
Choose?](http://blog.takipi.com/junit-vs-testng-which-testing-framework-should-you-choose/)\"*
by [Alex Zhitnitsky](http://blog.takipi.com/author/alexzhitnitsky/) -
*September 7, 2016*\
\
**[public void DesiredCapabilities() throws MalformedURLException
{ ]{.underline}**\
\
We are setting up in this Java class we are calling **Smoketest.java**
this public method we are calling DesiredCapabilities.\
\

-   It is void because we are not returning any values from running this
    method. 
-   It is setting this method to throw the URL Exception
    MalformedURLException if there are any errors with the URL. By using
    the URL class, it forces us to set the method up this way. 
-   *Read \"[Controlling Access to Members of a
    Class](https://docs.oracle.com/javase/tutorial/java/javaOO/accesscontrol.html)\", from
    Oracle Java Documentation: The Java Tutorials. *
-   *Read \"[How to Throw
    Exceptions](https://docs.oracle.com/javase/tutorial/essential/exceptions/throwing.html)\"
    from Oracle Java Documentation: The Java Tutorials. *

\
**[final String URL\_STRING =
\"http://127.0.0.1:4723/wd/hub\"; ]{.underline}**\
\
With this line, we are creating a **String constant** of the most famous
IP Addresses in the world:\
\

-   127.0.0.1: *There\'s no place like home! There\'s no place like
    home! *

<div>

What is 127.0.0.1? This is the IP Address of your local machine. This is
the Internet Protocol number of your *localhost*. 

</div>

<div>

\

</div>

<div>

Do you remember setting up Appium Desktop? We set the Host to be
\"0.0.0.0\", also the localhost, and the port to be 4723. 

</div>

\
\

::: {.separator style="clear: both; text-align: center;"}
[![](https://1.bp.blogspot.com/-lgIjJB-Ursc/WOWRrM4qVXI/AAAAAAAALuM/ZvUm4yCjNIoucjtNtIaup6GGhCSG1l4jACPcB/s640/screen-start-simple.png){width="640"
height="624"}](https://1.bp.blogspot.com/-lgIjJB-Ursc/WOWRrM4qVXI/AAAAAAAALuM/ZvUm4yCjNIoucjtNtIaup6GGhCSG1l4jACPcB/s1600/screen-start-simple.png)
:::

When we pressed that Start Server button, it launched Appium Server.\
\

::: {.separator style="clear: both; text-align: center;"}
[![](https://1.bp.blogspot.com/-EJ48P-0SgEc/WOWSn_RnxnI/AAAAAAAALuU/s5G_hP9tA6U__B4QhRYiS016h6OMlHyrgCPcB/s640/screen-logs.png){width="640"
height="595"}](https://1.bp.blogspot.com/-EJ48P-0SgEc/WOWSn_RnxnI/AAAAAAAALuU/s5G_hP9tA6U__B4QhRYiS016h6OMlHyrgCPcB/s1600/screen-logs.png)
:::

\
\
\
\
If **Appium Desktop** is still running on your machine, **Appium
Server** is quietly running in the background, listening, waiting for
you to send information its way.\
\
\... And what is listening at **http://127.0.0.1:4723/wd/hub**? It\'s
our old friend, the Selenium WebDriver Hub, just waiting to launch a
test on the Emulator node that is connected to it via *adb*.\
\

-   *Read HowToGeek\'s [What is Localhost IP
    127.0.0.1?](https://www.howtogeek.com/126304/why-is-the-localhost-ip-127.0.0.1/)*
-   *Read[on this blog about
    SeleniumGrid.](http://www.tjmaher.com/search/label/SeleniumGrid)*

\
\
So, with \"URL url = new URL(URL\_STRING);\" we are declaring a new
String constant, a string that can never be changed, URL\_STRING, to be
your localhost. Note that it is tradition to have constants to be in
ALL\_CAPS.\
**[\
]{.underline}[URL url = new URL(URL\_STRING)]{.underline}**\
\
We are declaring that String value to be a new URL (universal resource
locator class), aka a \"web address\". Built into this class, we need to
make sure we catch the possibility that the URL could possibly be parsed
incorrectly.\
\

-   *Read about [Catching and Throwing Exceptions in
    Java](https://docs.oracle.com/javase/tutorial/essential/exceptions/throwing.html)*

\
\
[**File app = new File(\"ApiDemos-debug.apk\");**]{.underline}\
Using Java\'s built in I/O (Input / Output) library, we are creating a
new instance of the File object, setting it up to match the
APIDemos-debug.apk file we have in our root directory. Once we declare a
new variable, \"app\" of type \"File\", we can use the methods contained
in the File class.\
\
Note: We could have called this variable anything we wanted. I usually
like my instance variables short, simple, and descriptive, to help not
just others, but myself when I am maintaining my own code three months
from now.\
\
Take a look at [TutorialsPoint\'s lesson on the Java
Class](https://www.tutorialspoint.com/java/java_file_class.htm). Now
that we have the app variable we could investigate the file such as:\
\

-   app.getName(): To get the name of the APIDemos-debug.apk
-   app.getPath(): To get the abstract path of the file
-   app.getAbsolutePath(): To get the absolute path of the file. 

\
\... That file? It is not technically just at the root directory of the
project, at \"APIDemos-debug.apk\". That is just the relative path when
compared to the root of the project.\
\
Technically, it is at
/Users/tmaher/code/smoketest\_poc/APIDemos-debug.apk, the absolute path
of the file on my MacBook.\
\
**[DesiredCapabilities caps = new
DesiredCapabilities(); ]{.underline}**\
\
Here, we are declaring a new instance of Selenium WebDriver\'s
DesiredCapabilities, and calling it the variable name, caps. We are
setting up the DEVICE\_NAME, the APP (using the absolute path), and the
PLATFORM\_NAME.\
\
*caps.setCapability(MobileCapabilityType.DEVICE\_NAME,
\"emulator-5554\"); caps.setCapability(MobileCapabilityType.APP,
app.getAbsolutePath());
caps.setCapability(MobileCapabilityType.PLATFORM\_NAME,
MobilePlatform.ANDROID); *\
\
If you take a look at the Java-Client Library on the
MobileCapabilityType, you can see t[here are many capabilities you can
set
up](https://appium.github.io/java-client/io/appium/java_client/remote/MobileCapabilityType.html)!
APP, APPIUM\_VERSION, ORIENTATION, such as portrait or landscape mode.\
\
Why are these in all caps? Tradition. These values are String Constants.
Constants are in ALL CAPS.\
\
**[\
]{.underline}[AndroidDriver driver = new AndroidDriver(url,
caps); ]{.underline}**\
\
Here, we are instantiating a new AndroidDriver, giving it the properties
of what we set up as a url, and the DesiredCapabilities.\
\
**A sidenote about clean code: **Imagine if we had called the
DesiredCapabilities variable, \"capabilites\"\... and we decided not to
use the URL class. Then this line would have looked like:\
\
[AndroidDriver driver = new AndroidDriver(new
URL(\"http://127.0.0.1:4723/wd/hub\"),
capabilities);]{style="background-color: #fafafa; color: #222222; font-family: "helvetica" , "arial" , sans-serif; font-size: 14px;"}\
\
\... Writing it the way we did was a bit cleaner, no?\
\
See, most of Java Programming is just personal preference\... or at
least, it\'s the personal preference of the most senior developers on
the team. Heck, they are the ones reviewing your code, the ones who have
to approve it before you merge it into the master codebase!\
\
When all code is written to an agreed upon standard, all with the same
format, it becomes more readable \-- which helps when trying to diagnose
in a hurry why your automated test failed. The first question developers
ask themselves is, *\"What in bloody hell does this code do again? I
haven\'t looked at it in months!\"* Readability of code is really,
really important.\
*\
\... back to the DesiredCapabilities! \...*\
\
Note: This will *possibly* link the Appium Server and our emulator to
our code. It will give its best shot.\
\
It will go to where we have designated the Selenium Hub, which was set
to **127.0.0.1/wd/hub**, where our Appium Server is waiting patiently,
running in the background of our computer.\
\
It will go to *avd*, and see which mobile devices are attached. Then it
will attempt to compare and contrast those devices and the desired
capabilites.\
\

-   Do we have an Android device? 
-   Do we have an app at the absolute path given?
-   Do we have an emulator called *emulator-5554*? 

\
\... If all those conditions are met, Appium will:\
\

-   Install the app on the emulator
-   Launch the app on the emulator

\
\... But what happens if you forget you have a physical device set up in
adb, and aren\'t using an emulator? Then, if it is a clear-cut decision,
such as only one Android device, a physical one running, Appium will
take that as the closest match, and use that instead.\
\
If the decision is not clear cut, the process will fail.\
\
Now, if we run the test\...\
\

::: {.separator style="clear: both; text-align: center;"}
[![](https://1.bp.blogspot.com/-DGyLB0o4tL0/WRUpLwIIMdI/AAAAAAAALyA/6YLKm4rPC1kRxGAjT0ZzHHqwdTBnOX_cQCPcB/s640/1.%2BAPI%2BDemo%2BApp.png){width="388"
height="640"}](https://1.bp.blogspot.com/-DGyLB0o4tL0/WRUpLwIIMdI/AAAAAAAALyA/6YLKm4rPC1kRxGAjT0ZzHHqwdTBnOX_cQCPcB/s1600/1.%2BAPI%2BDemo%2BApp.png)
:::

\
\... The app launches!\
\
\
\
Next, we will cover setting up PageObjects and PageFactories, and from
that, we will be able to write our first test!\
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
\
\
Whoa! \... As usual, after I publish a new blog article, I [advertised
this blog entry](https://twitter.com/tjmaher1/status/865956056240926723)
on my Twitter account, [\@tjmaher1](https://twitter.com/tjmaher1).
Within a few minutes, I received an email that someone had retweeted my
post\...\

<div>

\

  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://4.bp.blogspot.com/-VEcuVaOVg9M/WSBrn7kg6TI/AAAAAAAALz0/jq90yhPo55ADbInO7qe_poOThG07HHkqQCLcB/s640/Tweet.png){width="640" height="136"}](https://4.bp.blogspot.com/-VEcuVaOVg9M/WSBrn7kg6TI/AAAAAAAALz0/jq90yhPo55ADbInO7qe_poOThG07HHkqQCLcB/s1600/Tweet.png)
                                                                                                        *[Jason Huggins](https://twitter.com/hugs) retweeted my post! *
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Jason Huggins\...\
\... The man who [first created Selenium at
ThoughtWorks](https://testing.googleblog.com/2007/09/seleniums-inventor.html) developing
it to be Selenium RC \...\
\... Who joked that since this free toolset could help people get away
from Mercury Interactive ( designers of LoadRunner, QuickTest
Professional, now owned by HP ), they should call the free toolset
Selenium, since the element Selenium cures mercury poisoning \...\
\... Who worked with Simon Stewart [to create Selenium
WebDriver.](https://en.wikipedia.org/wiki/Selenium_(software))..\
\... Who was [one of the founders and CTO of Sauce
Labs](https://en.wikipedia.org/wiki/Sauce_Labs), the company who has
been sponsoring Appium, growing and developing it\...\
\
\... He just retweeted a link to this backwater blog (which is basically
my unedited research notes as I try to learn new tools and technologies
on-the-job).\
\
Wow.\
\
Hi, \@hugs! Happy Testing!

</div>

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

</div>

</div>

</div>
