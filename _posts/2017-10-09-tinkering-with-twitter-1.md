\-\-- layout: post title: \'Tinkering with Twitter: Twitter and the
Search API\' date: \'2017-10-09T19:38:00.001-04:00\' author: T.J. Maher
tags: - Java - Twitter - API modified\_time:
\'2017-11-04T16:40:22.797-04:00\' thumbnail:
https://i.ytimg.com/vi/7YcW25PHnAA/default.jpg blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-7124610876458838433
blogger\_orig\_url:
http://www.tjmaher.com/2017/10/tinkering-with-twitter-1.html \-\--
Let\'s say you are an automation developer and your boss gives you a new
assignment: **Test the search functionality for Twitter**, how would you
do it?\
\
You *could* cobble together a Selenium WebDriver framework, one that
spun up a browser, identified where the search bar was on
[Twitter.com](http://twitter.com/), typed in a search keywords, and
scraped the screen when the results appeared\...\
\
\... The problem with this approach? You aren\'t actually testing the
search functionality. You are testing how the web application handles
the search functionality. Why not the search functionality itself?\
\
Like the MBTA website we explored back in February, [Are You Sure the
Bus Line is Listed? Gathering data using REST APIs and REST
Assured](http://www.tjmaher.com/2017/02/are-you-sure-bus-line-still-listed.html),
much of the data is extracted from an API, an *application programming
interface*.\
\
With this series of blog articles we will be walking through:\
\
1) Setting up a development environment:\

-   **IntelliJ** as the integrated development environment (IDE)
-   We will be using a programming library called **Twitter4J** to
    interact with Twitter\'s API.
-   Since the Test4J programming library is in Java, we will be using
    that as a programming language.
-   Maven handling the third-party dependencies.

2\) Coming up with test data and posting it to Twitter.\
\
3) Searching for that test post we created.\
\
Let\'s begin!\
\
[]{#more}\
\

<div>

Wait! What is an API?
---------------------

\"An application program interface (API) is a set of
[routines](http://www.webopedia.com/TERM/R/routine.html),
[protocols](http://www.webopedia.com/TERM/P/protocol.html), and tools
for building [software
applications](http://www.webopedia.com/TERM/A/application.html).
Basically, an API specifies how software components should interact.
Additionally, APIs are used when programming graphical user interface
([GUI](http://www.webopedia.com/TERM/G/Graphical_User_Interface_GUI.html))
components. A good API makes it easier to develop a
[program](http://www.webopedia.com/TERM/P/program.html) by providing all
the building blocks. A
[programmer](http://www.webopedia.com/TERM/P/programmer.html) then puts
the blocks together\". * - Webopedia, [What is an
API](http://www.webopedia.com/TERM/A/API.html)?*

</div>

<div>

Instead of having someone needing to update information by hand on a
website, or pull data directly from a database, you can pull live data
in real time using the API, all throughout the slowness of going through
a user interface.

</div>

<div>

\
For more information, watch the following video\...\
**[\
]{.underline}[WebConcepts: Rest API Concepts and Examples]{.underline}**

</div>

\

<div>

*<https://youtu.be/7YcW25PHnAA>*\
\
\
Many different companies offer public APIs so developers can incorporate
their data into third-party applications. You can find a whole list of
them at [The Programmable Web](https://www.programmableweb.com/).\
\
One of the companies that allows you to access their data? **Twitter**!\
\

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://2.bp.blogspot.com/-5A1rQ4G1WOY/WdwABHi8jaI/AAAAAAAAMG0/PW1miTZcx90uF8fsMLexnyR8LHZTno0YACLcBGAs/s320/Twitter-logo.jpg){width="320" height="167"}](https://2.bp.blogspot.com/-5A1rQ4G1WOY/WdwABHi8jaI/AAAAAAAAMG0/PW1miTZcx90uF8fsMLexnyR8LHZTno0YACLcBGAs/s1600/Twitter-logo.jpg)
                                                                                                Find documentation for their API at [https://developer.twitter.com](https://developer.twitter.com/)
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

\
\
Twitter offers to the general public many APIs such as: 

</div>

<div>

-   **Twitter Search API:** Search for Tweets posted in the last seven
    days
-   **Twitter Ads API:**  Set up Ad Campaigns
-   **Engagments API:** \"\[R\]equests take an array of Tweet IDs, an
    array of engagement types, and a simple description of how you want
    the output arranged\".
-   **Direct Message API:** Send DMs to people. 

<div>

\... All of this and more can be found on
[Developer.Twitter.Com](https://developer.twitter.com/).\
\
**Want to Keep Tabs on Changes to Twitter\'s API?**\
\

-   If you want to see what changes are taking place with Twitter\'s
    API, Follow [\@TwitterAPI](https://twitter.com/TwitterAPI)

</div>

</div>

<div>

**How Do We Interact With Twitter\'s API?**\
\

</div>

<div>

There are many ways to interact with an API. On Adventures in
Automation, we\'ve used [Apache\'s HTTP
Components](http://www.tjmaher.com/2016/02/coming-up-how-to-work-with-rest-apis.html),
we\'ve used
[Postman](http://www.tjmaher.com/2016/07/introduction-to-api-testing-with.html),
we\'ve used the Java library
[Rest-Assured](http://www.tjmaher.com/2017/02/are-you-sure-bus-line-still-listed.html),
and now we are going to use Twitter4J.\
\
Shall we begin?\
\

</div>

<div>

Wait! What the heck is Twitter4J?
---------------------------------

\
Twitter4J is a Java library created by [Yusuke
Yamamoto](http://linkedin.com/in/yusuke/), a Java developer in Japan and
a one-time Developer Advocate at Twitter. 

</div>

<div>

\

-   Official Website: <http://twitter4j.org/en/>
-   Github site: <https://github.com/yusuke/twitter4j>

\
Twitter4J bills itself as \"an unofficial Java library for the [Twitter
API](https://dev.twitter.com/docs). With Twitter4J, you can easily
integrate your Java application with the Twitter service.\
\

</div>

<div>

\"Twitter4J is featuring:\
✔ \"100% Pure Java - works on any Java Platform version 5 or later\
✔ \"[Android](http://code.google.com/android/) platform and [Google App
Engine](http://code.google.com/appengine/) ready\
✔ \"Zero dependency : No additional jars required\
✔ \"Built-in OAuth support\
✔ \"Out-of-the-box gzip support\
✔ \"100% Twitter API 1.1 compatible\"

</div>

\
All you need to do is add Twitter4J to your project, and set up the
OAUTH Credentials, either by setting up a Properties file, using a
ConfigurationBuilder class, or feeding the credentials in through the
command line when launching a program that uses Twitter4J. You can read
more about it on Twitter4J\'s [Configuration
Page](http://twitter4j.org/en/configuration.html).\
\

> debug=true
> oauth.consumerKey=\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*
> oauth.consumerSecret=\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*
> oauth.accessToken=\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*
> oauth.accessTokenSecret=\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*

\

**What is OAUTH?**
------------------

When you or I sign in using out username and password to our Twitter ,
we are using User Level Authentication. How do Applications connect to
Twitter? OAUTH.\
\
OAuth is a way Twitter created back in 2009 to grant websites or
applications access to their information without giving them the
passwords.\
\
According to [Kevin Makice](http://archive.oreilly.com/pub/au/3514) in
[Twitter API: Up and Running](http://oreilly.com/catalog/9780596154615/)
(2009):\
\"In February 2009, Twitter released its first implementation of OAuth
as a closed beta to developers on the [Google discussion
group](http://groups.google.com/group/twitter-development-talk). A few
hours after this release, [Inuda](http://inuda.com/), a web application
design firm, quickly showed a proof of concept with Twitter's
code.\[[63](http://archive.oreilly.com/pub/a/web-services/excerpts/9780596154615/meet-twitter-api.html#ftn.id2726282)\]
Within a week, successful tests and sample code existed for PHP, Python,
and Ruby. A growing list of OAuth resources is available on the [Twitter
API wiki](http://apiwiki.twitter.com/OAuth-Examples).\
\
\"Among those efforts was a sample script from Abraham Williams
(\@poseurtech).\[[64](http://archive.oreilly.com/pub/a/web-services/excerpts/9780596154615/meet-twitter-api.html#ftn.id6878346)\]
Williams' solution follows a straightforward process to authenticate
with Twitter's OAuth. OAuth functions by managing multiple pairs of
tokens: the tokens for the specific user request, and the ones used to
allow the application to later access parts of that user's Twitter
account. There is also an initial pair used to register the application.
\[\...\] Each application will first need to be registered with
Twitter\".\

<div>

\
Applications use \"Application-only Authentication\".\
**\
**\

<div>

**What is Application-only authentication?**

</div>

\
\"[Application-only
authentication](https://dev.twitter.com/oauth/application-only) is a
form of authentication where an application makes API requests on its
own behalf, without a user context. API calls are still rate limited per
API method, but the pool each method draws from belongs to the entire
application at large, rather than from a per-user limit. API methods
that support this form of authentication will contain two rate limits in
their documentation, one that is per user (for application-user
authentication) and the other is per app (for this form of
application-only authentication). Not all API methods support
application-only authentication, because some methods require a user
context (for example, a Tweet can only be created by a logged-in user,
so user context is required for that operation)\".\

<div>

\

</div>

<div>

::: {style="text-align: right;"}
\- [Developer.Twitter.Com / Docs / Basics /
Authentication](https://developer.twitter.com/en/docs/basics/authentication/overview/oauth)
:::

\

<div>

<div>

\

</div>

<div>

**How do we get our own OAUTH credentials for Twitter?**

</div>

<div>

\

</div>

<div>

To be able to access Twitter APIs, you need to:

</div>

<div>

\

</div>

<div>

1\) Create a Twitter Account: 

</div>

<div>

-   Go to [Twitter.com](http://twitter.com/) and create an account for
    yourself. 

<div>

2\) Create a **Twitter App** to use the Twitter API

</div>

</div>

<div>

-   Go to <https://apps.twitter.com/> and choose to **Create a new
    app**.
-   Come up with a name and a description of how your project will be
    using the Twitter APIs. I called mine: \"Tinkering With Twitter\".
-   Are you creating a full blown app that will interact with a website
    you are creating? Enter it here. If not, enter a placeholder URL. 
-   Your app will be accessible
    from[ https://apps.twitter.com/](https://apps.twitter.com/)

</div>

<div>

3\) Find your new OATH Credentials.

</div>

<div>

-   Go to <https://apps.twitter.com/>
-   Select the link on the Dashboard to enter your Twitter App.
-   Next to \"Consumer Key and Access Key\" select the link for \"manage
    keys and access tokens\". 

<div>

There, you will see your:

</div>

</div>

<div>

-   Consumer Key
-   Consumer Secret
-   Access Token
-   Access Secret

<div>

Record these values, but don\'t share them, especially the secrets! You
will be inputting them in a properties file once we set up the project. 

</div>

</div>

<div>

\

</div>

<div>

\

</div>

What can I search for using the Twitter Search API?
---------------------------------------------------

<div>

\

</div>

<div>

Using the Twitter Search API, you can search all Tweets in the past
seven days by:

</div>

<div>

-   When a Tweet was **created\_at**
-   The Twitter **id** of a particular Tweet
-   The **text** of a Tweet.
-   If there is anything truncated in the Tweet
-   If there are any hashtags, symbols, user mentions, or URLs in the
    text. 
-   If the Tweet was **in\_reply\_to\_status\_id**, user id, or screen
    name. 
-   If the Tweet is favorited and retweted, the retweet\_count, and the
    favorite\_count
-   The language of the Tweet

</div>

<div>

\... And a lot more! 

</div>

<div>

\

</div>

<div>

> \"[The Twitter API platform currently offers a few different options
> for programmatically searching the index of Tweets. These options
> range from the standard 7-day Search API (search/tweets) to the
> enterprise Full-Archive Search API. Each option offers a varying level
> of access and query
> capabilities\" ]{style="background-color: white; color: #657786; font-family: "helvetica neue lt" , "helvetica neue" , "helvetica" , "arial" , sans-serif; font-size: 15.96px;"}

::: {style="text-align: right;"}
-Twitter Docs, [Search
API](https://developer.twitter.com/en/docs/tweets/search/overview) 
:::

Advanced Search Parameters
--------------------------

<div>

Want to up your searching game for Twitter? Read the Twitter article,
[Advanced TweetDeck
Features](https://support.twitter.com/articles/20170322#search), the
Search section. 

</div>

\
\"After you run a search, you will be given the option to customize your
results even further. You can alter your search in several ways,
including: \'showing,\' \'matching,\' \'excluding,\' \'written in,\' and
\'Retweets.\' You will find these filters by opening the filter option
at the top of the column.\
\
\"Examples:\

1.  \"To search for Tweets mentioning \'\#SanFrancisco\' that link to
    news stories, type the following in the search box: \#SanFrancisco
    filter:news
2.  \"To exclude a search term, use a negative filter type
    (\'-filter:type\') in your search query. 
3.  \"To search for mentions of \#space from verified accounts,
    excluding Retweets, type the following in the search box: \#space
    filter:verified -filter:nativeretweets
4.  \"To search for mentions of either \'red\' or \'black\', with
    mentions of either \'cold\' or \'hot\', with at least twenty
    Retweets, but excluding mentions of \'\#thedress\', and linking to
    news sources, type the following in the search box: (red OR black)
    AND (cold OR hot) min\_retweets:20 filter:news -\#thedress\"

<div>

You can also:

</div>

<div>

-   Search for hashtags, such as \"\#QA\"
-   See news articles: \"filter:news\"
-   Combine them! Is there any news in the past seven days about QA?
    \"filter:news \#QA\"
-   What\'s new from a user such as Ministry of Testing -
    Boston, \@MoT\_Boston? \"from:MoT\_Boston\"

</div>

 How Will I Know When Something Goes Wrong?
-------------------------------------------

<div>

It\'s not just Searching and Posting that can be done through the API,
you can also see details when things go wrong!\
\
If you attempt to connect to a Twitter API and something goes wrong, it
will return an HTTP Status Codes, such as HTTP Status Code 404: Not
Found, HTTP Status Code 401: Unauthorized and many others\... See
Twitter\'s Chart, listed
on <https://developer.twitter.com/en/docs/basics/response-codes>\

-   200: OK - Success!
-   304: Not Modified \-- There was no new data to return. 
-   400: Bad Request  \-- The request was invalid or cannot be otherwise
    served. An accompanying error message will explain further. Requests
    without authentication are considered invalid and will yield this
    response. 
-   401: Unauthorized \-- Missing or incorrect authentication
    credentials. This may also returned in other undefined
    circumstances.
-   403: Forbidden \-- The request is understood, but it has been
    refused or access is not allowed. An accompanying error message will
    explain why. This code is used when requests are being denied due to
    [update
    limits](https://support.twitter.com/articles/15364-about-twitter-limits-update-api-dm-and-following)
    . Other reasons for this status being returned are listed alongside
    the response codes in the table below. 
-   404: Not found \-- The URI requested is invalid or the resource
    requested, such as a user, does not exist. 
-   406: Not Acceptable \-- Returned when an invalid format is specified
    in the request. 
-   410: Gone \-- This resource is gone. Used to indicate that an API
    endpoint has been turned off. 
-   420: Enhance Your Calm: Returned when an application is being [rate
    limited](https://developer.twitter.com/en/docs/basics/rate-limiting.html)
    for making too many requests. 
-   422: Unprocessable Entity: Returned when the data is unable to be
    processed (for example, if an image uploaded to [POST account /
    update\_profile\_banner](https://developer.twitter.com/en/docs/accounts-and-users/manage-account-settings/api-reference/post-account-update_profile_banner.html)
    is not valid, or the JSON body of a request is badly-formed). 
-   429: Too Many Requests: Returned when a request cannot be served due
    to the application's rate limit having been exhausted for the
    resource. See [Rate
    Limiting](https://developer.twitter.com/en/docs/basics/rate-limiting.html). 
-   500: Internal Server Error \-- Something is broken. This is usually
    a temporary error, for example in a high load situation or if an
    endpoint is temporarily having issues. Check in the [developer
    forums](https://twittercommunity.com/) in case others are having
    similar issues, or try again later. 
-   502: Bad Gateway: Twitter is down, or being upgraded. 
-   503: Service Unavailable: The Twitter servers are up, but overloaded
    with requests. Try again later. 
-   504: Gateway timeout\" The Twitter servers are up, but the request
    couldn't be serviced due to some failure within the internal stack.
    Try again later. 

\
\... Um, they have a 420 Error Status? [I wonder what that
means](http://www.snopes.com/language/stories/420.asp)?\
\
There are also numerous error
codes: <https://developer.twitter.com/en/docs/basics/response-codes>\

-   32: Could not authenticate you: Corresponds with HTTP 401. There was
    an issue with the authentication data for the request. 
-   34: Sorry, that page does not exist: Corresponds with HTTP 404. The
    specified resource was not found. 
-   36: You cannot report yourself for spam. Corresponds with HTTP 403.
    You cannot use your own user ID in a report spam call. 
-   44: attachment\_url parameter is invalid: Corresponds with HTTP 400.
    The URL value provided is not a URL that can be attached to this
    Tweet. 
-   50: User not found. Corresponds with HTTP 404. The user is not
    found. 
-   63: User has been suspended. The user account has been suspended and
    information cannot be retrieved. 

\
Next time, we will walkthrough setting up a sample project with
Twitter4J using IntelliJ.\
\
One more time\... [How do you get credentials for Twitter and set up the
Twitter4J properties
file](http://www.tjmaher.com/2017/10/tinkering-with-twitter-2_29.html)?

</div>

</div>

<div>

\
\
\
Happy Testing!\
\
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

</div>

</div>

</div>

</div>
