\-\-- layout: post title: \'Tinkering with Twitter: Post a Tweet Using
Twitter4J to interact the Twitter REST API endpoint\' date:
\'2017-11-04T16:29:00.001-04:00\' author: T.J. Maher tags: - Twitter -
Rest API modified\_time: \'2017-11-04T16:35:55.587-04:00\' thumbnail:
https://2.bp.blogspot.com/-81nFHqPn4WM/Wf3bpDtI-rI/AAAAAAAAMIo/rOPtYan5Z1ACcMGaFKC575Mp8fnRQVA2wCLcBGAs/s72-c/tweet\_worked.png
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-7456240698191339515
blogger\_orig\_url:
http://www.tjmaher.com/2017/11/tinkering-with-twitter-4.html \-\-- *This
is Part Four of a multi-part blog series on putting together a basic API
test framework for the Twitter Search API. [Care to go back to the
beginning](http://www.tjmaher.com/2017/10/tinkering-with-twitter-1.html)? *\
*\
*Now that we have been [introduced to
Twitter4J](http://www.tjmaher.com/2017/10/tinkering-with-twitter-1.html),
a Java library built to interacts with Twitter\'s API, [set up
credentials](http://www.tjmaher.com/2017/10/tinkering-with-twitter-2_29.html)
that authorized Twitter4J to use our test Twitter account, and
[installed the Twitter4J library in a Java
project](http://www.tjmaher.com/2017/11/tinkering-with-twitter-3.html),
we can start writing code that can do three things:\
\

-   Connects to the REST endpoint of the Twitter API.
-   Posts a Tweet to the Twitter account we set up. 
-   Examine how Twitter4J interacts with the Twitter API

To figure out how everything works, we can view:\
\

-   [Code examples](http://twitter4j.org/en/code-examples.html) on the
    Twitter4J official site which tells you how to post a tweet
    ([updateStatus](http://twitter4j.org/en/code-examples.html#updatingStatus))
    and search for tweets
    ([search](http://twitter4j.org/en/code-examples.html#search)).
-   The [Twitter4J javadocs](http://twitter4j.org/javadoc/), more
    detailed documentation of how you can interact with the various
    classed set up. 
-   The source code in the [Twitter4J GitHub
    repository](https://github.com/yusuke/twitter4j).
-   Compare the Java code you see with explanations in the [official
    Java Tutorials](https://docs.oracle.com/javase/tutorial/).
-   Lastly, review the docs for the [Post and Engage Twitter using the
    API](https://developer.twitter.com/en/docs/tweets/post-and-engage/overview).

\
[]{#more}\
\
To truly know how a Java library truly works, don\'t expect to go to any
official site to have everything spelled out. Dive into t[he
JavaDocs](http://twitter4j.org/javadoc/). Feeling more advanced? Dive
right into the source code and start swimming.\
\

Post a Tweet To Your Twitter Account: Creating Sample Code
----------------------------------------------------------

What if we wanted to create a post that:\
\

-   Announces in a Twitter post that we are testing Twitter4J, posting
    to Twitter programmatically. 
-   Tags the official Twitter4J account, \@t4j\_news
-   Includes the link to Twitter4J documentation.

\
Let\'s create a Java class to hold our tests:\
\

-   Go to the File menu in IntelliJ, and go to File -\> New -\> Java
    class.
-   Name it TwitterPostsAndSearchTest, and hit OK. 
-   Copy and paste the sample code I created, below, into the new class
    we created:

The sample code I created based off of [Twitter4J\'s code
examples](http://twitter4j.org/en/code-examples.html).\
\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 import org.testng.annotations.Test;  
 import twitter4j.*;  

 public class TwitterPostsAndSearchTest {  
   @Test  
   public void test_postToTwitterUsingTwitter4J() throws TwitterException {  
     Twitter twitter = TwitterFactory.getSingleton();  
     String message="Testing Twitter4J, posting to Twitter programatically."  
                + " @t4j_news http://twitter4j.org/en/";  
     Status status = twitter.updateStatus(message);  
     System.out.println("Successfully updated the status to [" + status.getText() + "].");  
   }  
 }  
```

\
*Feel free to review the code for this test in my
project, [tinkeringWithTwitter, published on
GitHub](https://github.com/tjmaher/tinkeringWithTwitter/blob/master/src/test/java/TwitterPostsAndSearchTest.java).*\
\

### Deciphering the Java Code:

\
\

<div>

**[Step 1:]{.underline}**

</div>

-   Import into this Java class the **\@Test** annotation supplied by
    TestNG, a framework that kicks off individual tests. We are also
    importing Twitter4J.
-   *Go to [TestNG\'s documentation](http://testng.org/doc/) to read
    more information.*

**[Step 2:]{.underline}**\

-   We declare  a new public class, TwitterPostsAndSearchTest.
-   *Read more about [Java Classes in the Java
    Tutorials](https://docs.oracle.com/javase/tutorial/java/javaOO/classes.html).*

**[Step 3:]{.underline}**\

<div>

-   Create a new public test method, annotating it with the **\@Test
    annotation**, signifying that this will be a test. 
-   Does something go wrong? We want to be able to see any errors
    returned to us by Twitter4J\'s special **TwitterException** class.

<div>

\... If you review the [TwitterException class listed in Twitter4J\'s
Javadocs](http://twitter4j.org/javadoc/twitter4j/TwitterException.html),
you can see that it tests for:

</div>

<div>

-   Rate limit errors: Twitter sets a rate limit on just how many tweets
    can be automatically sent in a certain period of time. If the rate
    limit is exceeded, the Twitter API will return a digit representing
    how many seconds you need to wait to retry the action again. 
-   Network issues.
-   If the REST API we are looking for is not found. 

</div>

<div>

**[Step 4: ]{.underline}**

</div>

-   Declare a new instance of Twitter4J\'s Twitter class, setting up one
    single instance using Twitter4J\'s Twitter Factory class.
-   *Advanced Reading: The Singleton design pattern at [Design Patterns
    Explained
    Simply](https://sourcemaking.com/design_patterns/singleton).*

<div>

**[Step 5:]{.underline}**

</div>

<div>

-   Set up the message we wish to send, storing it in a Java String we
    are calling \"message\".

</div>

**[Step 6:]{.underline}**

</div>

<div>

-   Use Twitter4J\'s pre-defined method \"updateStatus\", passing in the
    message string we set up. Grab the status message that updateStatus
    returns.

<div>

**[Step 7:]{.underline}** 

</div>

-   Finally, print out what was was received back to us.

\
\

How to Run The Test
-------------------

\

-   In the code block for the test, right click.
-   Select \'Run test\_postToTwitterUsingTwitter4J\'
-   Review the debug messages for errors. Check if there is a success
    message printed.
-   Go to <http://twitter.com/>, logging into your account, to see if
    the message is posted. 

\
If everything is successful, you should see an image like the one
below:\
\

  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://2.bp.blogspot.com/-81nFHqPn4WM/Wf3bpDtI-rI/AAAAAAAAMIo/rOPtYan5Z1ACcMGaFKC575Mp8fnRQVA2wCLcBGAs/s1600/tweet_worked.png)](https://2.bp.blogspot.com/-81nFHqPn4WM/Wf3bpDtI-rI/AAAAAAAAMIo/rOPtYan5Z1ACcMGaFKC575Mp8fnRQVA2wCLcBGAs/s1600/tweet_worked.png)
                                                                                                              *We just posted a tweet using the Twitter API!*
  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

\
\... Where did that cute icon come from?\
\
That is what is called a \"Twitter Card\". View the Twitter
documentation for the \"Card Display\"
at <https://developer.twitter.com/en/docs/tweets/optimize-with-cards/guides/getting-started>\
\
This summary card is created right off of the meta keywords the website
developer uses to describe the site, using whatever images are set up.
Read the article \"[Must-Have Social Meta Tags for Twitter, Google+,
Facebook and More](https://moz.com/blog/meta-data-templates-123)\".\
\

What Do The Log Files Mean?
---------------------------

Because we have in our Twitter4J.Properties file the debug flag set to
\"true\", we see the below output:\
\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 [Sat Nov 04 11:07:19 EDT 2017]serialVersionUID: 6175546394599249696  
 [Sat Nov 04 11:07:19 EDT 2017]debug: true  
 [Sat Nov 04 11:07:19 EDT 2017]user: null  
 [Sat Nov 04 11:07:19 EDT 2017]password: null  
 [Sat Nov 04 11:07:19 EDT 2017]httpConf: MyHttpClientConfiguration{httpProxyHost='null', httpProxyUser='null', httpProxyPassword='null', httpProxyPort=-1, httpConnectionTimeout=20000, httpReadTimeout=120000, prettyDebug=false, gzipEnabled=true}  
 [Sat Nov 04 11:07:19 EDT 2017]httpStreamingReadTimeout: 40000  
 [Sat Nov 04 11:07:19 EDT 2017]httpRetryCount: 0  
 [Sat Nov 04 11:07:19 EDT 2017]httpRetryIntervalSeconds: 5  
 [Sat Nov 04 11:07:19 EDT 2017]oAuthConsumerKey: {HIDDEN}  
 [Sat Nov 04 11:07:19 EDT 2017]oAuthConsumerSecret: **************************************************  
 [Sat Nov 04 11:07:19 EDT 2017]oAuthAccessToken: {HIDDEN}  
 [Sat Nov 04 11:07:19 EDT 2017]oAuthAccessTokenSecret: *********************************************  
 [Sat Nov 04 11:07:19 EDT 2017]oAuth2TokenType: null  
 [Sat Nov 04 11:07:19 EDT 2017]oAuth2AccessToken: null  
 [Sat Nov 04 11:07:19 EDT 2017]oAuth2Scope: null  
 [Sat Nov 04 11:07:19 EDT 2017]oAuthRequestTokenURL: https://api.twitter.com/oauth/request_token  
 [Sat Nov 04 11:07:19 EDT 2017]oAuthAuthorizationURL: https://api.twitter.com/oauth/authorize  
 [Sat Nov 04 11:07:19 EDT 2017]oAuthAccessTokenURL: https://api.twitter.com/oauth/access_token  
 [Sat Nov 04 11:07:19 EDT 2017]oAuthAuthenticationURL: https://api.twitter.com/oauth/authenticate  
 [Sat Nov 04 11:07:19 EDT 2017]oAuth2TokenURL: https://api.twitter.com/oauth2/token  
 [Sat Nov 04 11:07:19 EDT 2017]oAuth2InvalidateTokenURL: https://api.twitter.com/oauth2/invalidate_token  
```

\
But what does it all mean?\
**\
Collect the Properties We Need to Pass to the API:**\
1) We start collecting the properties we need to before interacting with
Twitter\'s REST endpoint, such as the OAUTH tokens we are attempting to
use to become authorized to use the endpoint:\
\

-   serialVersionUID: 6175546394599249696
-   debug: true
-   httpConf: MyHttpClientConfiguration{httpProxyHost=\'null\',
    httpProxyUser=\'null\', httpProxyPassword=\'null\',
    httpProxyPort=-1, httpConnectionTimeout=20000,
    httpReadTimeout=120000, prettyDebug=false, gzipEnabled=true}
-   httpStreamingReadTimeout: 40000
-   httpRetryCount: 0
-   httpRetryIntervalSeconds: 5
-   oAuthConsumerKey: {HIDDEN}
-   oAuthConsumerSecret:
    \*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*
-   oAuthAccessToken: {HIDDEN}
-   oAuthAccessTokenSecret:
    \*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*
-   oAuth2TokenType: null
-   oAuth2AccessToken: null
-   oAuth2Scope: null

\
\
2) It creates a list of Twitter endpoints we can interact with using
Twitter4J:\
\

-   oAuthRequestTokenURL: https://api.twitter.com/oauth/request\_token
-   oAuthAuthorizationURL: https://api.twitter.com/oauth/authorize
-   oAuthAccessTokenURL: https://api.twitter.com/oauth/access\_token
-   oAuthAuthenticationURL: https://api.twitter.com/oauth/authenticate
-   oAuth2TokenURL: https://api.twitter.com/oauth2/token
-   oAuth2InvalidateTokenURL:
    https://api.twitter.com/oauth2/invalidate\_token
-   restBaseURL: https://api.twitter.com/1.1/
-   streamBaseURL: https://stream.twitter.com/1.1/
-   userStreamBaseURL: https://userstream.twitter.com/1.1/
-   siteStreamBaseURL: https://sitestream.twitter.com/1.1/
-   uploadBaseURL: https://upload.twitter.com/1.1/
-   dispatcherImpl: twitter4j.DispatcherImpl

\
\
3) How many tests do we want to run at once? Do we want to include how
many people retweeted a post?\
\

-   asyncNumThreads: 1
-   loggerFactory: null
-   contributingTo: -1
-   includeMyRetweetEnabled: true
-   includeEntitiesEnabled: true
-   trimUserEnabled: false
-   includeExtAltTextEnabled: true
-   tweetModeExtended: false
-   includeEmailEnabled: false
-   jsonStoreEnabled: false
-   mbeanEnabled: false
-   userStreamRepliesAllEnabled: false
-   userStreamWithFollowingsEnabled: true

\
\
4) It then catalogs all the various configurations:\
\

-   instances: \[ConfigurationBase{debug=true, user=\'null\',
    password=\'null\',
    httpConf=MyHttpClientConfiguration{httpProxyHost=\'null\',
    httpProxyUser=\'null\', httpProxyPassword=\'null\',
    httpProxyPort=-1, httpConnectionTimeout=20000,
    httpReadTimeout=120000, prettyDebug=false, gzipEnabled=true},
    httpStreamingReadTimeout=40000, httpRetryCount=0,
    httpRetryIntervalSeconds=5 \[\...\]

\
\
5) Since we are using the updateStatus method, The REST API Endpoint
that Twitter4J will hit for us using /statuses/update.json\
\

-   Request: 
-   POST https://api.twitter.com/1.1/statuses/update.json
-   \[Sat Nov 04 11:07:19 EDT 2017\]OAuth base string:
    POST&https%3A%2F%2Fapi.twitter.com%2F1.1%2Fstatuses%2Fupdate.json&include\_entities%3Dtrue%26include\_ext\_alt\_text%3Dtrue%26oauth\_consumer\_key\....

\
\
6) Everything is sent in as a big long URL: Properties, the message,
everything:\
\

-   \%3DBGI2N94oM0r8ceJ7MW3ippBGT%26oauth\_nonce%%26oauth\_signature\_method%3%26oauth\_timestamp%%26oauth\_token%%26oauth\_version%3D1.0%26status%3DTesting%2520Twitter4J%252C%2520posting%2520to%2520Twitter%2520programatically.%2520%2540t4j\_news%2520http%253A%252F%252Ftwitter4j.org%252Fen%252F

\
7) Twitter4J announces itself as the Twitter client you are using:\
\

-   X-Twitter-Client-Version: 4.0.6
-   X-Twitter-Client-URL: http://twitter4j.org/en/twitter4j-4.0.6.xml
-   X-Twitter-Client: Twitter4J
-   User-Agent: twitter4j http://twitter4j.org/ /4.0.6
-   Accept-Encoding: gzip
-   Post Params:
    status=Testing%20Twitter4J%2C%20posting%20to%20Twitter%20programatically.%20%40t4j\_news%20http%3A%2F%2Ftwitter4j.org%2Fen%2F&include\_entities=true&include\_ext\_alt\_text=true

\
8) The information is sent to the Twitter API, and we received an OK -
Success message back!\
\

-   HTTP/1.1 200 OK

\
\
Then, the message we have been looking for prints out:\
\
**Successfully updated the status to \[Testing Twitter4J, posting to
Twitter programatically. \@t4j\_news https://t.co/yH9nCIPnfu\].**\
\
\
While you are on Twitter, drop me a line and say hello! I
am [\@tjmaher1](https://twitter.com/tjmaher1).\
\
With our next entry, we will be talking about how to use the Twitter
Search API.\
\
Until then, Happy Testing!\

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
