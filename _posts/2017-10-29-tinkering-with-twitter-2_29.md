\-\-- layout: post title: \'Tinkering with Twitter: Getting credentials,
consumerKey, accessToken\' date: \'2017-10-29T10:21:00.003-04:00\'
author: T.J. Maher tags: - Java - Twitter modified\_time:
\'2017-11-04T16:37:44.900-04:00\' blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-865072945848110136
blogger\_orig\_url:
http://www.tjmaher.com/2017/10/tinkering-with-twitter-2\_29.html \-\--
*This is Part Two of a multi-part blog series on putting together a
basic API test framework for the Twitter Search API. [Care to go back to
the
beginning](http://www.tjmaher.com/2017/10/tinkering-with-twitter-1.html)? *\
\
In order to be able to programmatically interact with Twitter through
their APIs, you need an:\
\

-    OAUTH Consumer Key
-   Consumer Secret
-   Access Token
-   Access Token Secret 

Then, you need to place them in a Twitter4J Properties file.\
\
The file will look something like this:\
\
[]{#more}\
\
**[twitter4J.properties]{.underline}**\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
debug=true oauth.consumerKey=*********************
oauth.consumerSecret=****************************************** 
oauth.accessToken=**************************************************
oauth.accessTokenSecret=******************************************  
```

\
\.... Replace the lines of asterisks with the actual values once you get
them.\
\

<div>

**How do we get our own OAUTH credentials for Twitter?**
--------------------------------------------------------

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

-   Go to [Twitter.com](http://twitter.com/) and create an account for
    yourself. 

<div>

2\) Create a **Twitter App** to use the Twitter API

</div>

</div>

<div>

-   Go to <https://apps.twitter.com/> and choose to **Create a new
    app**.
-   Come up with a name and a description of how your project will be
    using the Twitter APIs. I called mine: \"Tinkering With Twitter\".
-   Are you creating a full blown app that will interact with a website
    you are creating? Enter it here. If not, enter a placeholder URL. 
-   Your app will be accessible
    from[ https://apps.twitter.com/](https://apps.twitter.com/)

</div>

<div>

3\) Find your new OAUTH Credentials.

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

\

<div>

</div>

\

::: {style="-webkit-text-stroke-width: 0px; color: black; font-family: "Times New Roman"; font-size: medium; font-style: normal; font-variant-caps: normal; font-variant-ligatures: normal; font-weight: normal; letter-spacing: normal; orphans: 2; text-align: start; text-decoration-color: initial; text-decoration-style: initial; text-indent: 0px; text-transform: none; white-space: normal; widows: 2; word-spacing: 0px;"}
-   Consumer Key
-   Consumer Secret
-   Access Token
-   Access Secret

<div>

::: {style="margin: 0px;"}
Record these values, but don\'t share them, especially the secrets! You
will be inputting them in a properties file once we set up the project. 
:::

::: {style="margin: 0px;"}
\
:::

::: {style="margin: 0px;"}
With the next blog entry, we will talk about how to search with Twitter.
Or if you want, you can [jump right to the source
code](https://github.com/tjmaher/tinkeringWithTwitter/). 
:::

</div>
:::

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
