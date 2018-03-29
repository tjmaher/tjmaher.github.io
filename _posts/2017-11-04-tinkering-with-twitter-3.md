\-\-- layout: post title: \'Tinkering with Twitter: Setting up an API
Testing environment with Twitter4J\' date:
\'2017-11-04T01:53:00.003-04:00\' author: T.J. Maher tags: - Twitter
modified\_time: \'2017-11-04T16:37:17.557-04:00\' thumbnail:
https://1.bp.blogspot.com/-aWaBQMQeGXQ/Wf1Npz0id6I/AAAAAAAAMIA/piD0PlYnMFEba\_fISTU7qWIOwMkvQKKnwCLcBGAs/s72-c/twit-1.png
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-367633116165148204
blogger\_orig\_url:
http://www.tjmaher.com/2017/11/tinkering-with-twitter-3.html \-\-- *This
is Part Three of a multi-part blog series on putting together a basic
API test framework for the Twitter Search API. [Care to go back to the
beginning](http://www.tjmaher.com/2017/10/tinkering-with-twitter-1.html)? *\
\
The last few posts we covered a lot of ground:\

-   [An overview of the Twitter
    API](http://www.tjmaher.com/2017/10/tinkering-with-twitter-1.html),
    and Twitter4J, which we will be using to access the Twitter API
-   How to do [Advanced
    Searches](http://www.tjmaher.com/2017/10/tinkering-with-twitter-1.html)
    using Twitter
-   [HTTP Status
    Codes](http://www.tjmaher.com/2017/10/tinkering-with-twitter-1.html)
    and Possible Error Codes
-   [How to generate credentials such as the Consumer Key and Access
    Token.](http://www.tjmaher.com/2017/10/tinkering-with-twitter-2_29.html)

\
For this entry, we will be walking a user through setting up an API
development environment with IntelliJ, Java, and Twitter4J.\
\
[]{#more}\
\
**Step One: Download and Install IntelliJ IDEA**\
\

-   Download and Install the [free Community
    Version](https://www.jetbrains.com/idea/download/) of IntelliJ for
    your Mac or PC

\
**Step Two: Set Up a New Project**\
\

-   Run IntelliJ IDEA. The main splash screen should appear.

\

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://1.bp.blogspot.com/-aWaBQMQeGXQ/Wf1Npz0id6I/AAAAAAAAMIA/piD0PlYnMFEba_fISTU7qWIOwMkvQKKnwCLcBGAs/s400/twit-1.png){width="400" height="291"}](https://1.bp.blogspot.com/-aWaBQMQeGXQ/Wf1Npz0id6I/AAAAAAAAMIA/piD0PlYnMFEba_fISTU7qWIOwMkvQKKnwCLcBGAs/s1600/twit-1.png)
                                                                                                                           *The IntelliJ IDEA splash screen*
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

\
\

-   From the splash screen, select \"Create Project\".
-   This time, let\'s create a  Maven project. Select \"Maven\" in the
    left-hand menu, make sure that Java 1.8 is selected, and hit
    \"Next\".

\

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://2.bp.blogspot.com/-4i_O3YXtw5I/Wf1OiIU30SI/AAAAAAAAMII/gu6YlAxm0KQeeqSEmPuapBx4LILbHhwDgCLcBGAs/s400/twitter-2.png){width="400" height="316"}](https://2.bp.blogspot.com/-4i_O3YXtw5I/Wf1OiIU30SI/AAAAAAAAMII/gu6YlAxm0KQeeqSEmPuapBx4LILbHhwDgCLcBGAs/s1600/twitter-2.png)
                                                                                                                   *Select Maven, the Java 1.8 SDK, and choose \"Next\". *
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

<div>

-   What do you want to use as a group id? Since I have my website
    \"tjmaher.com\", I used that as a package name: com.tjmaher. 
-   What do you want to call the project? I selected
    TinkeringWithTwitter as a name. Select \"Next\". 

\

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://3.bp.blogspot.com/-FDbH7VGRUxA/Wf1O4AN04aI/AAAAAAAAMIQ/MDhuXOPMdhMzB_bWpxSmR2MTAtaBbO4QgCLcBGAs/s400/twitter-3.png){width="400" height="307"}](https://3.bp.blogspot.com/-FDbH7VGRUxA/Wf1O4AN04aI/AAAAAAAAMIQ/MDhuXOPMdhMzB_bWpxSmR2MTAtaBbO4QgCLcBGAs/s1600/twitter-3.png)
                                                                                                  *Enter a group id, artifact id, and keep the default snapshot version. Select \"Next\". *
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

\

<div>

-   Select \"Finish\" on the next screen. 
-   Your Java project is now set up!

</div>

</div>

<div>

**\
Step Three: Set up the Twitter4J Dependencies in the POM.Xml file**

</div>

<div>

-   Review the \"Maven Integration\" section on the main page for
    Twitter4J on <http://twitter4j.org/en/index.html>
-   Go to the pom.xml file that was created automatically in the root
    folder of the project.
-   If it is not there already, after the group id, artifact id, and
    version, add the dependency block, placing the group id, artifact
    id, and version for Twitter4J inside it. It will look something like
    this: 

</div>

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
   <dependencies>  
     <dependency>  
       <groupId>org.twitter4j</groupId>  
       <artifactId>twitter4j-core</artifactId>  
       <version>[4.0,)</version>  
     </dependency>  
     <dependency>  
       <groupId>org.testng</groupId>  
       <artifactId>testng</artifactId>  
       <version>6.8</version>  
       <scope>test</scope>  
     </dependency>  
   </dependencies>  
```

\

-   The Twitter4J Java Library should automatically download. 
-   We will include the test framework TestNG.

\
**Step Four: Set up the Twitter credentials for Twitter4J to use**\
\

-   Once you are at the root folder of the project, create a new file by
    going to the horizontal menu, and select File -\> New -\> File.
-   Create a new file \"twitter4j.properties\".
-   Copy and paste the following code into the twitter4j.properties:

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 debug=true  
 oauth.consumerKey=****************  
 oauth.consumerSecret=****************  
 oauth.accessToken=****************  
 oauth.accessTokenSecret=****************  
```

\

-   Did you create a new Twitter account, create a Twitter app, and get
    credentials that this project could use? If not, [follow the
    instructions](http://www.tjmaher.com/2017/10/tinkering-with-twitter-2_29.html).
-   Cut-and-paste the consumer key, consumer secret, access token, and
    access token secret into the file, replacing the asterisks. 

\
\... Now, our project is all set! Next, we will work through posting
Tweets to your Twitter account using Twitter4J!\
\
\
\
Happy Testing!\
\

<div>

::: {#toc-section .toc-section}
**Tinkering With Twitter**\

-   **Part One**: [Twitter and the Twitter Search
    API](http://www.tjmaher.com/2017/10/tinkering-with-twitter-1.html)
-   **Part Two**: [Getting the Twitter credentials: Consumer Keys and
    Access
    Tokens](http://www.tjmaher.com/2017/10/tinkering-with-twitter-2_29.html)
-   **Part Three:** [Setting up an API Testing Environment with
    Twitter4J](http://www.tjmaher.com/2017/11/tinkering-with-twitter-3.html)
-   **Part Four:** [Post a Tweet Using Twitter4J To Interact With the
    Twitter
    API](http://www.tjmaher.com/2017/11/tinkering-with-twitter-4.html)
-   **GitHub**: [Review the source code for the
    project](https://github.com/tjmaher/tinkeringWithTwitter/).
:::

</div>

\
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
