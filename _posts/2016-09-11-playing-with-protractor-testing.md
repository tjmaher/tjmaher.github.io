\-\-- layout: post title: \'Playing with Protractor: Testing an
AngularJS application with Protractor, Jasmine, and JavaScript\' date:
\'2016-09-11T01:05:00.001-04:00\' author: T.J. Maher tags: - WebDriver -
AngularJS - Protractor modified\_time: \'2016-09-13T18:07:10.690-04:00\'
thumbnail:
https://4.bp.blogspot.com/-vzwxwEgozfY/V9TUZESqp6I/AAAAAAAALWQ/L5XAm00Bc5MlkWfVFyFukP-2L80x43gRQCLcB/s72-c/angular.png
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-9063819873717393073
blogger\_orig\_url:
http://www.tjmaher.com/2016/09/playing-with-protractor-testing.html
\-\-- Yesterday was a lot of fun! I was given an automation development
assignment a few days ago in preparation for an upcoming job interview:\
\
Using any technology I'd like, as long as it could be run using freely
available software, after filling out a questionnaire given on the
company\'s healthcare web app and writing a test journal post, I was to
produce automated checks for the following:\

-   An "Assessment Complete" badge appears on the dashboard
-   The journal entry created is present on the journal page.
-   The personality type displayed on the dashboard matches the one
    given to me in the assessment

<div>

What the instructions *didn\'t* say was that before each test, you had
to navigate a login procedure:

</div>

<div>

[]{#more}\

</div>

<div>

-   Go to the first login page. Enter your email. Wait for the animation
    to be done, then select the Continue button.
-   On the next page, wait for another animated graphic to load. 
-   After loading, enter the given password. Wait for the animation to
    be done, then select the Login button.
-   Only *then* can you navigate to the dashboard. 

<div>

Hrm, this was going to be trickier than it had initially sounded\...

</div>

</div>

 *My First Attempt*: Selenium WebDriver with Java and JUnit 4
-------------------------------------------------------------

<div>

\

</div>

<div>

I immediately started sketching out how to assemble the framework:

</div>

<div>

-   Code the assignment in Selenium WebDriver in Java using JUnit 4 as a
    testing framework, exactly as I have been doing these past few
    years. 
-   I was going to place the tests in a Test Class, the common elements
    of the test in a TestActions class, the web elements in PageObjects,
    and wrap all Selenium WebDriver elements in try / catch blocks \...
    but that would take time\...  

<div>

After checking with the company, I found out that they were just looking
for basic Selenium coding\...\
\
\... Can I select web elements? Navigate a site? They were looking for
things like that. Proof that I could get *something* written on the
first day.\
\
I hacked out something in a couple of hours. There was minor difficulty
since it was a slow-loading site, and I had to wait for some animations
to load up, and some other elements were nested deeply in the DOM, where
I had to find the selector of the parent element, and then go into the
secondary element, but it was fun to play around with
[Firefox](https://www.mozilla.org/)\'s plugins
[Firebug](http://getfirebug.com/) and
[Firepath](https://addons.mozilla.org/en-US/firefox/addon/firepath/).\
\
I submitted the test code to the company ahead of the deadline, but I
realized it wasn\'t as elegant a solution as I could have made it. I
went back to the app, and looked at the source code\... what was this?
\... AngularJS? I\'ve heard of that JavaScript framework, but never had
come across it before\...\
\
\... I wondered\... was there a special way to test AngularJS
applications?\
\

*My Second Attempt*: Protractor, JavaScript, and Jasmine
--------------------------------------------------------

</div>

</div>

It took me seconds on Google to find out that AngularJS applications
were built to be tested: unit tested, component tested, and browser
tested!\

### AngularJS {#angularjs style="text-align: center;"}

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://4.bp.blogspot.com/-vzwxwEgozfY/V9TUZESqp6I/AAAAAAAALWQ/L5XAm00Bc5MlkWfVFyFukP-2L80x43gRQCLcB/s400/angular.png){width="375" height="400"}](https://4.bp.blogspot.com/-vzwxwEgozfY/V9TUZESqp6I/AAAAAAAALWQ/L5XAm00Bc5MlkWfVFyFukP-2L80x43gRQCLcB/s1600/angular.png)
                                                                                                                        *Website: <https://angularjs.org/>*
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

\

-   **Official Website**: <https://angularjs.org/>
-   **GitHub Site**: <https://github.com/angular/angular.js>
-   **Official Tutorial**: The PhoneCat
    app: <https://docs.angularjs.org/tutorial>
-   **Free course**: <https://www.codeschool.com/pages/angular-1-vs-2>

<div>

\

</div>

### Protractor {#protractor style="text-align: center;"}

\

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://4.bp.blogspot.com/-FpJ7pWHCtjo/V9TUZLclkjI/AAAAAAAALWY/aS0frSPSrNwyIGDMVmJZk4gW1hlTbwEDACEw/s320/protractor.png){width="320" height="311"}](https://4.bp.blogspot.com/-FpJ7pWHCtjo/V9TUZLclkjI/AAAAAAAALWY/aS0frSPSrNwyIGDMVmJZk4gW1hlTbwEDACEw/s1600/protractor.png)
                                                                                                                      *Website: <http://www.protractortest.org/>*
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

\
Protractor sits on top of the JavaScript binding of Selenium WebDriver.
It allows you to code with the ease of JavaScript.\

-   **Official Website**: <http://www.protractortest.org/>
-   **GitHub Site**: <https://github.com/angular/protractor>
-   **Official Tutorial**: <http://www.protractortest.org/#/tutorial>
-   **Protractor Cheat
    Sheet**: <https://gist.github.com/javierarques/0c4c817d6c77b0877fda>

\
\

### Jasmine {#jasmine style="text-align: center;"}

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://1.bp.blogspot.com/-A-DRaKkjS6M/V9TZSrl3bxI/AAAAAAAALWw/h2lKlSsq85c4cmqoAgBLni2QLG0dbfSAACLcB/s320/jasmine.png){width="320" height="315"}](https://1.bp.blogspot.com/-A-DRaKkjS6M/V9TZSrl3bxI/AAAAAAAALWw/h2lKlSsq85c4cmqoAgBLni2QLG0dbfSAACLcB/s1600/jasmine.png)
                                                                                                                       *Website: <http://jasmine.github.io/>*
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

\
Jasmine allows you to build up tests quickly.\

-   **Official Website**: <http://jasmine.github.io/>
-   **GitHub Site**: <https://github.com/jasmine/jasmine>
-   **Documentation**: <http://jasmine.github.io/2.5/introduction.html>

\
\... You may wonder why I always list the GitHub site of an open-source
product in these blog entries?\
\
This is because I have found that the classes you take are not enough to
understand what these tools are doing. The official documentation is not
enough, either.\
\
You only truly know the product if you can look at the code that created
it. There are more methods to find a selector than what is listed in a
Selenium WebDriver class. Developers I have worked with don\'t wait
until a training class is available. They look at the docs of a product.
They play around with it on their own. They look at the source code that
is available, learn how the product really works, and also learn the
style of the authors, making them a better coder.\
\

### JavaScript {#javascript style="text-align: center;"}

\
**JavaSscript CodeSchool Site**: <https://www.javascript.com/>\
\

-   **JavaScript Road
    Trip**: <https://www.codeschool.com/courses/javascript-road-trip-part-1>
-   **JavaScript Resources**: <https://www.javascript.com/resources>

\
\

How to Set Up Your System To Run Protractor Tests
-------------------------------------------------

\
Note: You can easily set up Protractor on Mac, Linux, and Windows
environments. I set it up on my Windows 10 machine at home \... and I am
utterly, utterly surprised it worked out.\
\

-   Set up **Node.js** on your system:
    <https://nodejs.org/en/download/> 
-   We will be using the Node Package Manager (**npm**) to install tools
-   Open up a Command Line tool such as Terminal
-   Install **Protractor**: *npm install -g protractor*
-   Make sure that Protractor is working: *protractor \--version* 
-   Update WebDriver Manager: *webdriver-manager update*
-   Start up a Selenium server: *webdriver-manager start*
-   See if the Selenium server is running: Go to
    <http://localhost:4444/wd/hub> in a browser and see if the UI is
    displayed. This acts like a Selenium Grid.

Protractor will automatically install Jasmine, a BDD tool used to write
the tests. Learn more about Jasmine:
<http://jasmine.github.io/2.5/introduction.html> \...\
\
It\'s slightly different than TestNG or JUnit. Jasmine handles all
\"asserts\" as \"expects\", but it is pretty similar.\
\

Protractor Code Samples
-----------------------

\
I produced two files for the automated tests: A **conf** file that
stored the configurations, and a **spec** file which specified the test.
Here\'s what I came up with:\
\
**[Conf.js]{.underline}**\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 // conf.js  
 exports.config = {  
  framework: 'jasmine',  
  seleniumAddress: 'http://localhost:4444/wd/hub',  
  specs: ['spec.js']  
 }  
```

\
The test code I came up with below, I changed the username, password,
and the URL the test is connecting to, just to be safe. Heck, I don\'t
want you actually changing my personality test results!\
\
**[Spec.js]{.underline}**\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
1:  describe('Fake Site Test', function() {  
2:    
3:   var stressProfileUrl = "https://fake-site/dashboard#/stress-profile";  
4:   var journalUrl = "https://fake-site/dashboard#/journal";  
5:    
6:   function navigateToLoginPageAndLoginAsTJ(){  
7:    browser.get('https://fake-site/auth/login');  
8:    
9:    expect(browser.getTitle()).toEqual('Login | Fake Site');  
10:     
11:    element(by.model('login_data.email')).sendKeys('test@test.com');  
12:    element(by.css('.animate-switch.ng-scope > button')).click();  
13:    
14:    var EC = protractor.ExpectedConditions;  
15:    var passwordGraphic = element(by.css("[src='/symfony/img/auth/password.png']"));  
16:    browser.wait(EC.visibilityOf(passwordGraphic), 20);  
17:    
18:    element(by.model('login_data.password')).sendKeys('12345');  
19:    element(by.css('.animate-switch.ng-scope > button')).click();  
20:    
21:    expect(browser.getTitle()).toEqual('My Dashboard | Fake Site');  
22:   }   
23:    
24:   it('should have the Assessment Complete badge and "Problem Solver" on Stress Profile, and the Test Entry in the journal', function() {  
25:    navigateToLoginPageAndLoginAsTJ();  
26:    browser.get(stressProfileUrl);  
27:    
28:    var badgeAssessmentElement = element(by.css("[alt='complete badge']"));  
29:    expect(badgeAssessmentElement.isDisplayed());  
30:    
31:    var personalityNameElement = element(by.css(".personality > .personality-box > h3 > .ng-binding"));  
32:    expect(personalityNameElement.getText()).toBe('Problem Solver');  
33:    
34:    browser.get(journalUrl);  
35:    
36:    var listHeaders = element.all(by.css('p.journal-entry-txt.ng-binding')).each(function(element, index) {  
37:     element.getText()   
38:    });  
39:    
40:    var isTestHeaderDisplayed = false;  
41:    var testHeader = 'This is a test';  
42:    
43:    for (i = 0; i < listHeaders; i++) {  
44:     if (listHeaders.get(i) === testHeader) {  
45:      isTestHeaderDisplayed = true;  
46:      break;  
47:     }  
48:    }  
49:    
50:    expect(isTestHeaderDisplayed);  
51:    
52:   });  
53:  });  
```

\
Notice the little differences between Selenium WebDriver / Java / JUnit
and Protractor / JavaScript / Jasmine. WebDriver / Java would use:\
\

-   Assert.assertEquals, instead of expect
-   WebDriverWait(driver,
    20).until(ExpectedConditions.visibilityOfElementLocated(By.cssSelector(\...)
-   WebElement passwordTextbox =
    driver.findElement(By.id(\"password\"));
-   Assert.assertTrue(driver.getCurrentUrl().contains(\"journal\"));
-   List\<WebElement\> journalEntries =
    driver.findElements(By.cssSelector(\"p.journal-entry-txt.ng-binding\"));

\

How to Run The Tests
--------------------

\

-   Create a new directory
-   Place conf.js and spec.js in the new directory 
-   Open the Command Line and go that directory.
-   Run the test: *protractor conf.js*

\
\... Of course, the test will error out. I faked the URL, username, and
password, to give the company a bit of privacy.\
\

Results of the Test
-------------------

\
C:\\Users\\tmaher\\Documents\\code\\MeQ\>protractor conf.js\
\[00:44:37\] I/hosted - Using the selenium server at
http://localhost:4444/wd/hub\
\[00:44:37\] I/launcher - Running 1 instances of WebDriver\
Started\
..\
\
1 spec, 0 failures\
Finished in 16.464 seconds\
\[00:44:57\] I/launcher - 0 instance(s) of WebDriver still running\
\[00:44:57\] I/launcher - chrome \#01 passed\
\

Where to Go From Here? 
-----------------------

Down the line, maybe later I can build off this with:\
\
**The Grunt Protractor Runner:**
<https://www.npmjs.com/package/grunt-protractor-runner> as a way to run
tools from the command line.\
\

-   If I could figure out how to stand up a Jenkins server, a job
    normally handled by DevOps, I could config a Jenkins job to use
    Grunt to make tests like these run as part of a Continuous
    Integration suite. The tests could run once per hour, just after
    code is deployed, or overnight at a certain time. 

\
**Page Objects**:
<https://github.com/angular/protractor/blob/master/docs/page-objects.md> \...
Group elements on a page in the same class, to have better organized
code.\
\
Until Then, Happy Testing!\
\

::: {#toc-section .toc-section}
**Playing With Protractor:**\

-   **Part One:** [My first exposure to an AngularJS web app: Testing
    using Protractor, Jasmine, and
    JavaScript](http://www.tjmaher.com/2016/09/playing-with-protractor-testing.html)
-   **Part Two:**  [Learning AngularJS with the PhoneCat Tutorial App:
    Installation, Setup, and Running
    Tests](http://www.tjmaher.com/2016/09/playing-with-protractor-learning.html)
-   **Part Three**: [The complexities of testing JavaScript frameworks,
    according to Vojtěch Jína, creator of Karma Test Runner for
    AngularJS](http://www.tjmaher.com/2016/09/playing-with-protractor-complexities-of.html)
:::

\
\
-T.J. Maher\
Sr. QA Engineer\
\
*// Software QA Engineer since 1996.\
// Working with Selenium WebDriver since 2014.\
// Follow Adventures in Automation and Like us on
[Facebook](https://www.facebook.com/AdventuresInAutomation/)!*
