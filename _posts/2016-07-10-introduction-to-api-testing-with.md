\-\-- layout: post title: Introduction to API Testing with Postman and
Newman date: \'2016-07-10T00:06:00.000-04:00\' author: T.J. Maher tags:
- Jenkins - Gradle - Postman - API modified\_time:
\'2016-09-09T07:42:23.494-04:00\' thumbnail:
https://3.bp.blogspot.com/-rid\_WKidlDc/V4EAoRdUI2I/AAAAAAAALQw/lST2be0QS-kbPDo3A6FSMOkebqrz-epwwCLcB/s72-c/postman-logo%252Btext-320x132.png
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-1577832499625741565
blogger\_orig\_url:
http://www.tjmaher.com/2016/07/introduction-to-api-testing-with.html
\-\-- **Postman** ( <https://www.getpostman.com/> ) is tool they use at
work to test APIs\... along with [Swagger](http://swagger.io/),
[Pact](https://github.com/realestate-com-au/pact), and Java with [Apache
HTTPComponents](https://hc.apache.org/). Postman comes in two versions
\... as a Chrome app or a Mac app. They seem similiar, except the Mac
app \"is packaged with add-ons that make request capturing and cookie
handling seamless\" according to Postman\'s documentation.\
\

::: {.separator style="clear: both; text-align: center;"}
[![](https://3.bp.blogspot.com/-rid_WKidlDc/V4EAoRdUI2I/AAAAAAAALQw/lST2be0QS-kbPDo3A6FSMOkebqrz-epwwCLcB/s1600/postman-logo%252Btext-320x132.png)](https://3.bp.blogspot.com/-rid_WKidlDc/V4EAoRdUI2I/AAAAAAAALQw/lST2be0QS-kbPDo3A6FSMOkebqrz-epwwCLcB/s1600/postman-logo%252Btext-320x132.png)
:::

 What is an API?
----------------

\"Application program interface (API) is a set of routines, protocols,
and tools for building software applications. An API specifies how
software components should interact and APIs are used when programming
graphical user interface (GUI) components. A good API makes it easier to
develop a program by providing all the building blocks. A programmer
then puts the blocks together\". -
[Webopedia](http://www.webopedia.com/TERM/A/API.html)\
\
Need to get up to speed on APIs?\
\
**[REST API Concept and Examples:]{.underline}**\

\
\
\
Brought to you by JelledTV\'s W[ebConcepts YouTube
channel](https://www.youtube.com/user/jelledTV), \"This video introduces
the viewer to some API concepts by making example calls to Facebook\'s
Graph API, Google Maps\' API, Instagram\'s Media Search API, and
Twitter\'s Status Update API.\
\

-   \"Youtube\'s Facebook Page [via the Facebook Graph
    API](http://graph.facebook.com/youtube)  
-   \"Google Maps [Geocode API call for the city of
    Chicago](http://maps.googleapis.com/maps/api/geocode/json?address=Chicago)  
-   \"Apigee[ Instagram API
    console](https://apigee.com/console/instagram)  
-   \"[HTTP Request
    Methods](http://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol#Request_methods) 
-   Twitter\'s [Status Update
    documentation](https://dev.twitter.com/docs/api/1.1/post/statuses/update).
     

If you want to find many other sites that use APIs, go
to[ProgrammableWeb.com](http://www.programmableweb.com/).\
\
\... They also mention how to use this new tool that came out\...
**Postman**: <https://www.getpostman.com/>\
\
\
\
[]{#more}\
\

Learn Tools From the Creators 
------------------------------

\
It\'s very important as a new automation developer to learn how to teach
yourself the various toolsets you use day-to-day.\
\
Don\'t wait for one-on-one instruction from a senior member of the
automation team to show you all the ins-and-outs of a tool. Don\'t wait
for the company to send you on an expensive training class.\
\
We are living in a great time to be a software developer. The
open-source movement that I first heard about as a Computer Science
undergrad in the 1990s bore great fruit. If you are trying to learn a
new tool, you can go right to the source\... and find the source code
the tool is built on, stored in GitHub: <http://www.github.com/>.
Seminars, Webinars, and instructional YouTube videos usually can all be
found on the Internet, available for free. And to the new creators of
these tools we use: Documentation matters. Instructions on how to use
the tool matter. You don\'t need another third-party website peddling
courses telling you how to use a tool. You can get the information from
the creators themselves.\
\
\... Okay, sorry for getting on my soap box. :) Back to the regularly
scheduled blog.\

 Installing and Using Postman
-----------------------------

\
Postman documentation is available
at <https://www.getpostman.com/docs/>.\
And yes, Postman Labs does have a GitHub
site. <https://github.com/postmanlabs>.\
\
\
**[Postman: Installation and Setup]{.underline}**\

\
\
**[How to use Postman API Response Viewer:]{.underline}**\

\

-   *Want more videos? Go to the \"Postman How-To\" [series on
    YouTube](https://www.youtube.com/playlist?list=PLM-7VG-sgbtD8qBnGeQM5nvlpqB_ktaLZ). *

<div>

\

</div>

Working with APIs, the Java Way
-------------------------------

\
Back in February, we talked about RESTful Testing, using as an example
Stripe, a credit card processor.\
**\
RESTful Testing with Stripe:**\
\

-   [Brief introduction to REST
    APIs](http://www.tjmaher.com/2016/02/restful-testing-with-stripe-brief.html) 
-   [Interacting with Stripe using HTTPS and
    cURL](http://www.tjmaher.com/2016/02/restful-testing-with-stripe-interacting.html) 
-   [Using UriBuilder, HttpGet and other Apache
    HttpComponents](http://www.tjmaher.com/2016/02/restful-testing-with-stripe-using.html) 

\
\
Working with Apache HttpComponents, you could work with APIs, but it
ain\'t pretty. You had to know Java. You had to know how to use GSON to
convert the JSON file data into a Java object you could use. You needed
a lot of exception handling. A quick-start tool, it was not.\
\
Even if you know how to read a JSON file (JavaScript Notation), Postman
does have a bit of a learning curve, but it does seem easier.\
\
Let\'s continue using Stripe as the API Endpoint we are going to test
against. I really love the documentation in the Stripe API
Reference! <https://stripe.com/docs/api>\
\

Testing APIs the Postman Way
----------------------------

Let\'s go to the Stripe API.\
\

-   Go to the URL: <https://api.stripe.com/v1/charges>
-   When we see the Login popup, let\'s hit cancel. 
-   It should not allow you to log in.
-   It should throw an error that looks like:

\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 {  
  "error": {  
   "type": "invalid_request_error",  
   "message": "You did not provide an API key. 
   You need to provide your API key in the Authorization header, 
   using Bearer auth (e.g. 'Authorization: Bearer YOUR_SECRET_KEY'). 
   See https://stripe.com/docs/api#authentication for details, or we 
   can help at https://support.stripe.com/."  
  }  
 }  
```

\
If we do the same thing in Postman, entering into
GET: <https://api.stripe.com/v1/charges> and hitting the SEND
button without setting up any authorization, we should get the same
result:\
\

::: {.separator style="clear: both; text-align: center;"}
[![](https://1.bp.blogspot.com/-muPdJC8vpVU/V4EVbzahrQI/AAAAAAAALRI/YWaPD62N2sQheX_-KJ3C4b31VAAyYZF6gCLcB/s400/401.png){width="400"
height="235"}](https://1.bp.blogspot.com/-muPdJC8vpVU/V4EVbzahrQI/AAAAAAAALRI/YWaPD62N2sQheX_-KJ3C4b31VAAyYZF6gCLcB/s1600/401.png)
:::

\
Note that the HTTP Status Code returned is \"401 Unauthorized\".\
\
Hit SAVE:\

-   **Request Name**: Call the test something like:
    \"accessStripeApiWithoutLoggingIn\"
-   Create new **Collection** called: StripeAPI. 

\
Now, let\'s create a test to make sure that you cannot log into the API
without proper authorization:\

-   Select the \"Tests\" tab.
-   Under \"Snippets\" we can scroll down until we see a code snippet
    similar to what we are looking at. 
-   Select: Status code: Code is 200 (this means everything is okay). 
-   Alter the JavaScript pre-generated from \"200\" to \"401\" and SAVE.

\
*Need  list of Status Codes?
See <https://en.wikipedia.org/wiki/List_of_HTTP_status_codes>*\
\

::: {.separator style="clear: both; text-align: center;"}
[![](https://3.bp.blogspot.com/-DQOWZrAa2X4/V4EdwVGWEaI/AAAAAAAALRg/GYEV_fUFdV8sllsQrvFT4iV-sPGi6ildwCLcB/s400/Unauthorized.png){width="400"
height="156"}](https://3.bp.blogspot.com/-DQOWZrAa2X4/V4EdwVGWEaI/AAAAAAAALRg/GYEV_fUFdV8sllsQrvFT4iV-sPGi6ildwCLcB/s1600/Unauthorized.png)
:::

\
The test code now reads:\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 tests["Status code is 401"] = responseCode.code === 401;  
```

\

::: {.separator style="clear: both; text-align: center;"}
[![](https://3.bp.blogspot.com/-MIqMizeZNl4/V4E3IMsSYWI/AAAAAAAALR4/ui38tDBxs2YN46eb3ifVoJazmVIELDcwgCLcB/s400/run.png){width="400"
height="308"}](https://3.bp.blogspot.com/-MIqMizeZNl4/V4E3IMsSYWI/AAAAAAAALR4/ui38tDBxs2YN46eb3ifVoJazmVIELDcwgCLcB/s1600/run.png)
:::

Now, when you go to the Runner (the Collection Runner) select START
TEST, you can see everything is green! It passes. You ran your first API
test!\
\
We now have one test in a Collection called StripeAPI. Let\'s create a
new folder called \"Authentication\" so we can group the test in
something easily understandable.\

 Export and Downloading the API Test
------------------------------------

\
Following Postman\'s documentation on Collections:
<http://www.getpostman.com/docs/collections>\
\
\"Collections can be downloaded as a JSON file which you can share with
others or shared through your Postman account. You can also share
collections anonymously but it is strongly recommended to create a
Postman account when uploading collections. This will let you update
your existing collection, make it public or delete it later\".\
\
Let\'s Export the collection:\

-   Under the Collections tab, next to StripeAPI, select the \"\...\"
-   Select \"Export\", and chose to save it as Collections version 2. 

\
\

::: {.separator style="clear: both; text-align: center;"}
[![](https://2.bp.blogspot.com/--e6bpnuWvew/V4E-Bbdj-mI/AAAAAAAALSQ/sFTRLM2awN8M7U7yKqAaR6N0LobqSQp8gCLcB/s400/export.png){width="400"
height="270"}](https://2.bp.blogspot.com/--e6bpnuWvew/V4E-Bbdj-mI/AAAAAAAALSQ/sFTRLM2awN8M7U7yKqAaR6N0LobqSQp8gCLcB/s1600/export.png)
:::

\
You can see a file called \"StripeAPI.postman\_collection\" has been
created. Let\'s save it under our root folder, in a directory called
\"api\" and a subfolder called \"stripe\".
*/api/stripe/StripeAPI.postman\_collection*.\
\
Opening **StripeAPI.postman\_collection**, the file we just created, you
can see that the entire test is a JSON file.\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 {  
      "variables": [],  
      "info": {  
           "name": "StripeAPI",  
           "_postman_id": "7f318f47-9848-4333-057c-58fcaf7ae8d0",  
           "description": "",  
           "schema": "https://schema.getpostman.com/json/collection/v2.0.0/collection.json"  
      },  
      "item": [  
           {  
                "name": "Authentication",  
                "description": "",  
                "item": [  
                     {  
                          "name": "accessStripeApiWithoutLoggingIn",  
                          "event": [  
                               {  
                                    "listen": "test",  
                                    "script": {  
                                         "type": "text/javascript",  
                                         "exec": "tests[\"Status code is 401\"] 
                                                   = responseCode.code === 401;"  
                                    }  
                               }  
                          ],  
                          "request": {  
                               "url": "https://api.stripe.com/v1/charges",  
                               "method": "GET",  
                               "header": [],  
                               "body": {  
                                    "mode": "formdata",  
                                    "formdata": []  
                               },  
                               "description": ""  
                          },  
                          "response": []  
                     }  
                ]  
           }  
      ]  
 }  
```

\
We wrote our API test. We exported it as a file. How would we run it?\
\
\... Oh, hello Newman.\
\
Yes, it is a Seinfeld reference. The postman that Jerry Seinfeld did not
like was called \"Newman\".\

 Running the API Test
---------------------

**Newman GitHub Sit**e: <https://github.com/postmanlabs/newman>\
\
Let\'s walkthrough setting up an environment to run Postman\'s API
tests.\
\
**Precondition:** Node.js. Newman is built on Node.js, and we install
Newman using Node.js\'s Package Manager called NPM, so Node.js will need
to be installed.\
\
*What is Node.js?*\

> \"Node.js is an open-source, cross-platform runtime environment for
> developing server-side Web applications. Although Node.js is not a
> JavaScript framework,\[3\] many of its basic modules are written in
> JavaScript, and developers can write new modules in JavaScript. The
> runtime environment interprets JavaScript using Google\'s V8
> JavaScript engine \[\...\] Node.js was originally written in 2009 by
> Ryan Dahl. The initial release supported only Linux. \[\...\] In 2011,
> a package manager was introduced for the Node.js environment called
> npm. The package manager makes it easier for programmers to publish
> and share source code of Node.js libraries and is designed to simplify
> installation, updating and uninstallation of libraries \[\...\] In
> June 2011, Microsoft and Joyent implemented a native Windows version
> of Node.js. The first Node.js build supporting Windows was released in
> July 2011\". - [Wikipedia](https://en.wikipedia.org/wiki/Node.js)

\
Do you have Node on your system? Open a command prompt and type: *node
\--version*\
\
The current version of Node is 4.4.7. If you have below version 4, go
to <https://nodejs.org/en/download/> and download install the Windows or
Mac version that you need.\
\
Once Node.js is installed, we need to install Newman by running in the
Command Line:\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 npm install -g newman  
```

\
\

-   *Having problems installing Newman on
    Windows? <http://blog.getpostman.com/2015/04/09/installing-newman-on-windows/>*

\
\
Let\'s run Newman, execute the test, then store the results in an output
file called \"outputfile.txt\".\
\

-   Go to the directory where Newman was installed. Since I use Windows
    at home, newman was installed at
    C:\\User\\tmaher\\AppData\\Roaming\\npm\\. To use newman, I can
    either go to that directory or go into the Windows Environment
    Properties and [add that to the Path
    variable](http://betanews.com/2015/11/23/windows-10-finally-adds-a-new-path-editor/).
-   Run on the Command Line: 

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 newman -c C:\api\stripe\StripeAPI.postman_collection.json -o outputfile.json  
```

::: {.separator style="clear: both; text-align: center;"}
[![](https://1.bp.blogspot.com/-KhnspPdqebs/V4FuO4iLGOI/AAAAAAAALSo/PcArX7EyQSkFt56YqLzQ-UzdnEsSgRM-QCLcB/s400/screen.png){width="400"
height="107"}](https://1.bp.blogspot.com/-KhnspPdqebs/V4FuO4iLGOI/AAAAAAAALSo/PcArX7EyQSkFt56YqLzQ-UzdnEsSgRM-QCLcB/s1600/screen.png)
:::

\
Success! The test ran from the command line. It went to the Stripe API,
attempted to log in without authorization, just as expected!\
\
Examining the output, we see one huge JSON file. What if I want to see
what things look like at a glance?\
\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 newman -c C:\api\stripe\StripeAPI.postman_collection.json – H Reports.html   
```

\

::: {.separator style="clear: both; text-align: center;"}
[![](https://3.bp.blogspot.com/-oYcC-frK_A8/V4FxxPNMOMI/AAAAAAAALS8/KZoFVIUOxkQaduexzZnl1RhsB7HtjYKgQCLcB/s640/report.png){width="640"
height="305"}](https://3.bp.blogspot.com/-oYcC-frK_A8/V4FxxPNMOMI/AAAAAAAALS8/KZoFVIUOxkQaduexzZnl1RhsB7HtjYKgQCLcB/s1600/report.png)
:::

\
\... Okay, that is more like it!\
\

Where to Go From Here?
----------------------

### **Use Newman in Docker!**

-   Newman has its own Docker Image in Docker
    Hub! <https://github.com/postmanlabs/newman-docker>

\

<div>

\

</div>

-   *Not familiar with Docker? Read more about [Docker on this
    blog](http://www.tjmaher.com/search/label/Docker)!*
-   *Not familiar with Jenkins? Read more about [Jenkins on this
    blog](http://www.tjmaher.com/search/label/Jenkins)!*

**\
\
**\

### **Connect Newman with Jenkins:**

\
<https://www.getpostman.com/docs/integrating_with_jenkins>\
\
Want to run your API test:\

-   After every new code change is added to your project, such as with a
    smoke test?
-   Once an hour?
-   On a QA Environment resembling your production environment to test
    the release candidate? 

<div>

Couple Postman + Newman + Jenkins.\
\

-   Not familiar with Jenkins? Read[about it on my
    blog](http://www.tjmaher.com/2015/03/lecture-customizing-jenkins-sitespect.html).
-   Want to set up Jenkins with Newman? Enter what we used on the
    Command Line to run continuously on
    Jenkins: <http://blog.getpostman.com/2015/09/03/how-to-write-powerful-automated-api-tests-with-postman-newman-and-jenkins/>

</div>

### 

### Add Node and Newman to Your Build Script

Want to run your tests from your Build.Gradle file? Take a look at the
**Gradle-Node-Plugin**: <https://github.com/srs/gradle-node-plugin>. \"Releases
of this plugin are hosted at [Bintray](http://bintray.com/) and is part
of the [jCenter](https://bintray.com/bintray/jcenter) repository\".\
\
The site provides sample code for you to:\
\

-   Configure the plugin:

\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 plugins {  
  id "com.moowork.node" version "0.13"  
 }  

  apply plugin: 'com.moowork.node'
```

\

-   Configure Node:

\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 node {  
  // Version of node to use.  
  version = '0.11.10'  
  // Version of npm to use.  
  npmVersion = '2.1.5'  
  // Base URL for fetching node distributions (change if you have a mirror).  
  distBaseUrl = 'https://nodejs.org/dist'  
  // If true, it will download node using above parameters.  
  // If false, it will try to use globally installed node.  
  download = true  
  // Set the work directory for unpacking node  
  workDir = file("${project.buildDir}/nodejs")  
  // Set the work directory where node_modules should be located  
  nodeModulesDir = file("${project.projectDir}")  
 }  
```

\
Feel free to take a look!\
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
