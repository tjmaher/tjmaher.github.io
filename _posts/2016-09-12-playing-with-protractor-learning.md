\-\-- layout: post title: \'Playing with Protractor: Learning AngularJS
by setting up the PhoneCat Tutorial App\' date:
\'2016-09-12T00:15:00.001-04:00\' author: T.J. Maher tags: - AngularJS -
Protractor modified\_time: \'2016-09-13T18:07:36.317-04:00\' thumbnail:
https://4.bp.blogspot.com/-9ECtXTBEi88/V9WHMRfcrHI/AAAAAAAALXM/urNSXNC4dCwu3RY8VS0KQyrTmkkb68xSACLcB/s72-c/phones.png
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-1486739194335340985
blogger\_orig\_url:
http://www.tjmaher.com/2016/09/playing-with-protractor-learning.html
\-\-- Normally, when investigating new automation tools and
technologies, my *modus operandi* is to take a good two or three hours
to figure out who created the tool, how the tool evolved, if it was
based on earlier work, etc. After all that is done, I spend another hour
or so formatting my research notes into a pretty blog entry.\
\
This time around, I wanted to do something different\...\
\
Instead of starting with researching which Google employees made
AngularJS and Protractor, what projects they both were based on, and how
they are used, I wanted to continue what I did the previous blog entry
about [Protractor, AngularJS, JavaScript and
Jasmine](http://www.tjmaher.com/2016/09/playing-with-protractor-testing.html),
and dive right into the code itself.\
\
This blog is geared towards the manual tester who is attempting to learn
automation, exactly where I was back in December 2014. You can read more
about that transition in my TechBeacon article, [Switching Careers in
QA: From Manual Testing to Automation
Development](http://techbeacon.com/switching-careers-qa-manual-testing-automation-development).\
\
For this blog entry, I\'ll walk you through installing the **PhoneCat
Tutorial App** at <https://docs.angularjs.org/tutorial>. If you aren\'t
familiar working every day with **Git** or the **Command Line
interface**, and haven\'t tinkered with using **Node.js** or the **Node
Package Manager** (npm), every extra bit of instruction helps.\
\
Once you have everything set up, you can go at your own pace through
Google\'s tutorial.\
\
[]{#more} \

What is the PhoneCat App Tutorial? 
-----------------------------------

\
To teach developers how to build AngularJS applications, Google created
an [AngularJS Tutorial](https://docs.angularjs.org/tutorial) that walks
the reader through the code of a pre-built Phone Catalog web
application. You can search for phones, sort through newest and oldest
models, see pictures of the products, and click through to their
products page.\

> \"A great way to get introduced to AngularJS is to work through this
> tutorial, which walks you through the construction of an Angular web
> app. The app you will build is a catalog that displays a list of
> Android devices, lets you filter the list to see only devices that
> interest you, and then view details for any device\".

\... Also, it walks the developer through how to create unit tests with
**Karma**, and browser tests with **Protractor**, the tool [we were
looking at
before](http://www.tjmaher.com/2016/09/playing-with-protractor-testing.html).\
\
I will be developing this app on my Windows 10 machine at home just to
see if it can be done.\
\
Developing code at work, I  use a MacBook Pro, but I would rather not
clutter it up with this project.\
\

Installation and Setup
----------------------

\
We will need many tools installed to run this tutorial:\
\
**[Git-SCM]{.underline}**: <https://git-scm.com/download>\
\

-   Helps you copy the source code of the PhoneCat application to your
    workstation by using \"git clone\".
-   See if you have Git on your computer. Type: *git \--version*
-   Don\'t have Git? Download and install it. 
-   Want to read more blog entries about Git? (
    [link](http://www.tjmaher.com/search/label/GIT) ) 

\
Any code I tinker with, I usually place in C:\\Users\\tmaher\\code.\
\
I opened a Windows Command Prompt, since I am using Windows 10. I
changed the directory to \"cd c:\\Users\\tmaher\\code, and ran the
following command that I saw in the [AngularJS
tutorial](https://docs.angularjs.org/tutorial):\
\
[git clone \--depth=16
https://github.com/angular/angular-phonecat.git]{style="font-family: "courier new" , "courier" , monospace;"}\
\
\... This downloads the PhoneCat project, and the previous 16 commits to
the \"code\" directory. It creates a new directory,
\"angular-phonecat\". To go into that directory, you can:\
\
[cd
angular-phonecat]{style="font-family: "courier new" , "courier" , monospace;"}\
\
Their Angular tutorial assumes that you are in this directory from this
point on.\
**\
[Node.js]{.underline}**: <https://nodejs.org/en/download/>\
\
\

-   Node.JS uses JavaScript to set up the server stuff. AngularJS uses
    JavaScript to set up the browser user interface stuff. 
-   Do you already have Node.js on your system? What version? Check by
    running: *node \--version*
-   Don\'t have Node.js? Go to <https://nodejs.org/en/download/> to
    install it. 

\
Are you now in the angular-phonecat directory?\
\
Check, using *ls* for Unix/ Mac or *dir* for Windows. If you are, we can
use the **Node Package Manager** (npm) to install all dependencies into
the node-modules directories.\
\

-   **Bower** - client-side code package manager: <http://bower.io/>
-   **Http-Server** - simple local static web server:
    <https://github.com/nodeapps/http-server>
-   **Karma** - unit test runner: <https://karma-runner.github.io/>
-   **Protractor** - end-to-end (E2E) test runner:
    <https://github.com/angular/protractor>

\
This means that we have some npm helper scripts the PhoneCat project
provided:\
\

-   *npm start*: Start a local development web server.
-   *npm test*: Start the Karma unit test runner.
-   *npm run protractor*: Run the Protractor end-to-end (E2E) tests.
-   *npm run update-webdriver*: Install the drivers needed by
    Protractor.

\

Run the PhoneCat Web Application
--------------------------------

\
Okay! Let\'s see if it works! Let me check to make sure I am in the
correct directory, C:\\Users\\tmaher\\code\\angular-phonecat.\
\
Let\'s start up a web server with: *npm start*\
*\
*\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 npm start  
```

*\
*We can see in the command line output that it runs:\

-   npm start
-   prestart C:\\Users\\tmaher\\code\\angular-phonecat
-   npm install
-   postinstall C:\\Users\\tmaher\\code\\angular-phonecat
-   bower install
-   start C:\\Users\\tmaher\\code\\angular-phonecat
-   http-server ./app -a localhost -p 8000 -c-1

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 Starting up http-server, serving ./app  
 Available on: http://localhost:8000  
 Hit CTRL-C to stop the server  
```

\
Let\'s see what happens if I go to <http://localhost:8000/index.html> ?\
\

::: {.separator style="clear: both; text-align: center;"}
[![](https://4.bp.blogspot.com/-9ECtXTBEi88/V9WHMRfcrHI/AAAAAAAALXM/urNSXNC4dCwu3RY8VS0KQyrTmkkb68xSACLcB/s400/phones.png){width="400"
height="163"}](https://4.bp.blogspot.com/-9ECtXTBEi88/V9WHMRfcrHI/AAAAAAAALXM/urNSXNC4dCwu3RY8VS0KQyrTmkkb68xSACLcB/s1600/phones.png)
:::

\
\
We have a web app!\
\
\... And it took me only a good 30 minutes to install everything and
type up this walkthrough.\
\
Odd. This Phone Catalog app, created by Google doesn\'t have listed any
Apple products, like iPhones, or iPads. Just Google Android devices\...
Funny, eh?\
\

Run the Unit Tests
------------------

\
Let\'s open up a new Command Line interface, since the last one is still
running the web server. I needed to make sure I went to the correct
directory:\
\
[cd
c:\\Users\\tmaher\\code\\angular-phonecat]{style="font-family: "courier new" , "courier" , monospace;"}\
\
\... Or you are going to see things fail and wonder why, then realize
that you forgot to go to the correct directory.\
\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 npm test  
```

\
The command line output shows what is running:\

-   pretest C:\\Users\\tmaher\\code\\angular-phonecat
-   npm install
-   postinstall C:\\Users\\tmaher\\code\\angular-phonecat
-   bower install
-   test C:\\Users\\tmaher\\code\\angular-phonecat
-   karma start karma.conf.js

Then the output starts looking weird to me:\
\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 11 09 2016 11:29:55.969:WARN [karma]: No captured browser, open http://localhost:9876/  
 11 09 2016 11:29:55.987:INFO [karma]: Karma v0.13.22 server started at http://localhost:9876/  
 11 09 2016 11:29:55.996:INFO [launcher]: Starting browser Chrome  
 11 09 2016 11:29:56.016:INFO [launcher]: Starting browser Firefox  
 11 09 2016 11:30:02.543:INFO [Chrome 52.0.2743 (Windows 10 0.0.0)]: Connected on socket /#_ofxzrh2BSzFW2CSAAAA with id 43260207  
 11 09 2016 11:30:17.534:INFO [Firefox 48.0.0 (Windows 10 0.0.0)]: Connected on socket /#6vN7edkY8Obzwa8HAAAB with id 1091306  
 Chrome 52.0.2743 (Windows 10 0.0.0): Executed 1 of 5 SUCCESS (0 secs / 0.027 secChrome 52.0.2743 (Windows 10 0.0.0): 
  Executed 2 of 5 SUCCESS (0 secs / 0.052 secChrome 52.0.2743 (Windows 10 0.0.0): 
  Executed 3 of 5 SUCCESS (0 secs / 0.061 secChrome 52.0.2743 (Windows 10 0.0.0): 
  Executed 4 of 5 SUCCESS (0 secs / 0.067 secChrome 52.0.2743 (Windows 10 0.0.0): 
  Executed 5 of 5 SUCCESS (0 secs / 0.071 secChrome 52.0.2743 (Windows 10 0.0.0): Executed 5 of 5 SUCCESS (0.093 secs / 0.071
 Chrome 52.0.2743 (Windows 10 0.0.0): Executed 5 of 5 SUCCESS (0.093 secs / 0.071
 Chrome 52.0.2743 (Windows 10 0.0.0): Executed 5 of 5 SUCCESS (0.093 secs / 0.071 secs)  
 Chrome 52.0.2743 (Windows 10 0.0.0): Executed 5 of 5 SUCCESS (0.093 secs / 0.071 secs)  
 Chrome 52.0.2743 (Windows 10 0.0.0): Executed 5 of 5 SUCCESS (0.093 secs / 0.071 secs)  
 Chrome 52.0.2743 (Windows 10 0.0.0): Executed 5 of 5 SUCCESS (0.093 secs / 0.071 secs)  
 Chrome 52.0.2743 (Windows 10 0.0.0): Executed 5 of 5 SUCCESS (0.093 secs / 0.071 secs)  
 Chrome 52.0.2743 (Windows 10 0.0.0): Executed 5 of 5 SUCCESS (0.093 secs / 0.071 secs)  
 Firefox 48.0.0 (Windows 10 0.0.0): Executed 5 of 5 SUCCESS (0.087 secs / 0.058 secs)  
 TOTAL: 10 SUCCESS  
```

\
\... Okay, what the heck just happened?\

> \"This will start the Karma unit test runner. Karma will read the
> configuration file karma.conf.js, located at the root of the project
> directory. This configuration file tells Karma to:\
> \
>
> -   \"Open up instances of the Chrome and Firefox browsers and connect
>     them to Karma.
> -   \"Execute all the unit tests in these browsers.
> -   \"Report the results of these tests in the terminal/command line
>     window.
> -   \"Watch all the project\'s JavaScript files and re-run the tests
>     whenever any of these change.
>
> \"It is good to leave this running all the time, in the background, as
> it will give you immediate feedback about whether your changes pass
> the unit tests while you are working on the code\".

\
Ah! Thank you, [PhoneCat
documentation](https://docs.angularjs.org/tutorial/)!\
\

Updating Selenium Grid
----------------------

\
Now, let\'s open a third Command Line interface. One is running the web
app. One is running the unit tests.\
\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 npm run update-webdriver  
```

\
This will update selenium-server-standalone, chromedriver and anything
else that needs updating\
\
**Want more information about Selenium Grid? **\
\

-   Check out the blog listings
    [here](http://www.tjmaher.com/search/label/SeleniumGrid) to cycle
    through all posts
-   Need something more basic? Check out my post: [Selenium Grid for
    Beginners: Brace yourself! We\'re Using the Command
    Line](http://www.tjmaher.com/2016/07/setup-of-selenium-grid-for-beginners.html)

\
\

Running the end-to-end tests
----------------------------

\
Make sure your server is running: *npm start*\
\
To kick off the browser tests, run:\
\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 npm run protractor  
```

\
The command line output shows what is running:\
\

-   npm run protractor
-   npm run update-webdriver
-   npm install
-   bower install
-   webdriver-manager update
-   \>\> *selenium standalone is up to date.*
-   \>\> *chromedriver is up to date.*
-   protractor e2e-tests/protractor.conf.js

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 [11:46:23] I/local - Starting selenium standalone server...  
 [11:46:23] I/launcher - Running 1 instances of WebDriver  
 [11:46:28] I/local - Selenium standalone server started at http://192.168.56.1:52033/wd/hub  
 Started  
 .......  
 7 specs, 0 failures  
 Finished in 17.946 seconds  
 [11:46:51] I/local - Shutting down selenium standalone server.  
 [11:46:51] I/launcher - 0 instance(s) of WebDriver still running  
 [11:46:51] I/launcher - chrome #01 passed  
```

\

Have Fun Exploring!
-------------------

\
Have fun exploring the rest of Google\'s Angular tutorial! I know I sure
will!\
\
T**able of contents** of the official tutorial:\
\
[Tutorial](https://docs.angularjs.org/tutorial)\
0 - [Bootstrapping](https://docs.angularjs.org/tutorial/step_00)\
1 - [Static Template](https://docs.angularjs.org/tutorial/step_01)\
2 - [Angular Templates](https://docs.angularjs.org/tutorial/step_02)\
3 - [Components](https://docs.angularjs.org/tutorial/step_03)\
4 - [Directory and File
Organization](https://docs.angularjs.org/tutorial/step_04)\
5 - [Filtering Repeaters](https://docs.angularjs.org/tutorial/step_05)\
6 - [Two-way Data Binding](https://docs.angularjs.org/tutorial/step_06)\
7 - [XHR & Dependency
Injection](https://docs.angularjs.org/tutorial/step_07)\
8 - [Templating Links &
Images](https://docs.angularjs.org/tutorial/step_08)\
9 - [Routing & Multiple
Views](https://docs.angularjs.org/tutorial/step_09)\
10 - [More Templating](https://docs.angularjs.org/tutorial/step_10)\
11 - [Custom Filters](https://docs.angularjs.org/tutorial/step_11)\
12 - [Event Handlers](https://docs.angularjs.org/tutorial/step_12)\
13 - [REST and Custom
Services](https://docs.angularjs.org/tutorial/step_13)\
14 - [Animations](https://docs.angularjs.org/tutorial/step_14)\
[The End](https://docs.angularjs.org/tutorial/the_end)\
\
\
Happy Testing!\
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
-T.J. Maher\
Sr. QA Engineer\
\
*// Software QA Engineer since 1996.\
// Working with Selenium WebDriver since 2014.\
// Follow Adventures in Automation and Like us on
[Facebook](https://www.facebook.com/AdventuresInAutomation/)!*
