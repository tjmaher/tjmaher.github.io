\-\-- layout: post title: \'Are you sure the bus line is still listed?:
Don\'\'t gather data from the UI. Use a RESTful API endpoint instead!\'
date: \'2017-02-04T20:47:00.002-05:00\' author: T.J. Maher tags: - Rest
API - REST Assured modified\_time: \'2017-03-24T19:51:54.904-04:00\'
thumbnail:
https://4.bp.blogspot.com/-hMu\_AuRb7BY/WJZ3NHLZFnI/AAAAAAAALmM/4oa5YTCASZsuuRlijGGI-4T\_gSJ9Af-TACLcB/s72-c/Screenshot%2B2017-01-28%2Bat%2B6.10.29%2BPM.png
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-5741550981697820928
blogger\_orig\_url:
http://www.tjmaher.com/2017/02/are-you-sure-bus-line-still-listed.html
\-\-- You are an automation developer on a team developing in Java a new
public transportation web application. The customer base for the app is
located in Southeastern Massachusetts.\
\
The MBTA (Massachusetts Bay Transportation Authority) oversees the
subway lines and buses of the Greater Boston area and the surrounding
suburbs. The \#230 bus line stretches across four cities, connecting a
Commuter Rail Station in Brockton, MA (my hometown), a bus terminal for
the Brockton Area Transit\'s BAT bus, and a major subway stop in
Braintree, MA.\
\
You will need in this project to get data from the MBTA for this
particular bus line: bus schedules, bus stops, maybe even bus locations.
But this begs the question:\

-   How do you make sure that the \#230 bus line is still listed?

\

Attempt \#1: Manual Testing: Use the MBTA\'s Web Site
-----------------------------------------------------

The easiest way to test to see if the \#230 bus is still listed by the
MBTA is a visual check through the MBTA\'s website.\
\
1) Go to http://www.mbta.com/\
2) Select the \"Bus\" icon\
\

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://4.bp.blogspot.com/-hMu_AuRb7BY/WJZ3NHLZFnI/AAAAAAAALmM/4oa5YTCASZsuuRlijGGI-4T_gSJ9Af-TACLcB/s400/Screenshot%2B2017-01-28%2Bat%2B6.10.29%2BPM.png){width="400" height="131"}](https://4.bp.blogspot.com/-hMu_AuRb7BY/WJZ3NHLZFnI/AAAAAAAALmM/4oa5YTCASZsuuRlijGGI-4T_gSJ9Af-TACLcB/s1600/Screenshot%2B2017-01-28%2Bat%2B6.10.29%2BPM.png)
                                                                                                                                                      *From the MBTA webstite, <http://www.mbta.com/>*
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

\
**Test \#1:** Assert that the \"230\" entry is in the dropdown for
\"bus\".\
\
3) Choose \"230\" in the dropdown provided.\
\
4) Wait until you are redirected to the schedule for the 230 bus line at
<http://mbta.com/schedules_and_maps/bus/routes/?route=230>.\
\
**Test \#2:** Assert that the schedule appears.\
\

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://1.bp.blogspot.com/-xhdthVgYoAM/WJZ3zF8rGZI/AAAAAAAALmQ/zzu74GIDdd0FUM3QdEGzL-NLVlvQWCESwCLcB/s400/Screenshot%2B2017-01-28%2Bat%2B6.18.08%2BPM.png){width="400" height="250"}](https://1.bp.blogspot.com/-xhdthVgYoAM/WJZ3zF8rGZI/AAAAAAAALmQ/zzu74GIDdd0FUM3QdEGzL-NLVlvQWCESwCLcB/s1600/Screenshot%2B2017-01-28%2Bat%2B6.18.08%2BPM.png)
                                                                                                                                                               *Schedules and maps from MBTA*
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

We can visually check confirm that:\
\

-   Yes, the 230 bus line is listed on the front page
-   Yes, the bus schedule appears\... after a bit.

\
\... But what if we want this to be part of an automated test and just
want a yes or no answer to the question \"Is the Bus Line Listed
Correctly?\"\
\

Problems with Gathering Data from the UI
----------------------------------------

Let\'s say that we use Selenium WebDriver for our test. We write an
automated script to:\
\
1) Go to <http://www.mbta.com/>\
2) Select the \"Bus\" icon\
3) Choose \"230\" in the dropdown provided\
4) Wait until you are redirected to the schedule for the 230 bus line\
\
And we wait\... and wait \... and wait\...\
\
\... and wait \...\
\
\... and you *may* be automatically redirected to the bus schedule, or
you may not.\
\
Automate this with Selenium WebDriver and Java, and, mark my words, you
are going to spend the next month or so trying to get the
synchronization correct so the test doesn\'t time out.\
\
This test will be deemed a \"flaky test\". Woe to anyone attempting to
use this test in their test library.\
\
A better test would be to not go through the web site at all to get this
data, and communicate with a webservice that has this information
instead.\
\

A Better Way to Gather Data: RESTful API Endpoints
--------------------------------------------------

<div>

Luckily for us, like many sites nowadays, the MBTA offers an [MBTA
Developer Portal](http://realtime.mbta.com/Portal/). Developers of
third-party applications can read production data in real time, to see
not just schedules of the buses and trains that the MBTA operates, but
also the positions of the buses and trains in real time. 

</div>

<div>

\

</div>

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://4.bp.blogspot.com/-cPBAu4BJwxc/WJZ8gyk6JEI/AAAAAAAALmg/-QF29hVNup0eawzAwfcMxoLLcQpblcF3ACLcB/s400/Screenshot%2B2017-02-04%2Bat%2B8.14.17%2BPM.png){width="400" height="235"}](https://4.bp.blogspot.com/-cPBAu4BJwxc/WJZ8gyk6JEI/AAAAAAAALmg/-QF29hVNup0eawzAwfcMxoLLcQpblcF3ACLcB/s1600/Screenshot%2B2017-02-04%2Bat%2B8.14.17%2BPM.png)
                                                                                                                                           [*http://realtime.mbta.com/Portal/*](http://realtime.mbta.com/Portal/)
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

<div>

\

</div>

<div>

The MBTA *wants* to share it\'s data with the public. It provides: 

</div>

<div>

-   A public key you can use to test out the system (but make sure to
    subscribe for your own key if you are doing more than monkeying
    around)
-   Documentation on how to set up information queries (See the PDF for
    the [MBTA-Realtime API Quickstart
    Guide](http://realtime.mbta.com/Portal/Content/Documents/MBTA-realtime_APIQuickStart_2016-04-05.pdf) dated
    5/2016)

</div>

 What is the Public API Key?
----------------------------

<div>

\"Below is the current open development API key. It may change at any
time. This key is open for all developers to use in development and
testing. DO NOT go into production using this key! Register for an
account and request a key of your own on
[realtime.mbta.com](http://realtime.mbta.com/). There is no cost. 

</div>

<div>

\

</div>

<div>

\"As of 5/11/13 the open development API key is:
 wX9NwuHnZU2ToO7GmGR9uw\"\

 What Information Can You Lookup?
---------------------------------

According to the QuickStart documentation, part of the items you can
look up are:\
\

-   Stopsbylocation: GPS coordinates, listing latitude and longitude of
    the bus or train
-   Routesbystop: All the stops on the Red, Green, Orange line or bus
    line
-   Predictionsbystop: When will the next train or bus be arriving?
-   Alertheaders: Are there any service alerts?

\
You can see even more information in the MBTA-Realtime API Documentation
(V 2.1.3) dated January 4, 2017. Listed is that you can query routes,
such as bus routes.\
\
If we wanted to manually interact with the API to check if the bus line
\#230 is still active, we can:\
\
1) Go
to <http://realtime.mbta.com/developer/api/v2/routes?api_key=wX9NwuHnZU2ToO7GmGR9uw&format=json> to
view all routes.\
\
2) Search on the page for the numbers \"230\", and we can see:\
\
[[{]{style="font-family: "courier new" , "courier" , monospace;"}]{style="white-space: pre-wrap;"}\
[[ \"route\_id\" : \"230
\",]{style="font-family: "courier new" , "courier" , monospace;"}]{style="white-space: pre-wrap;"}\
[[
\"route\_name\":\"230\"]{style="font-family: "courier new" , "courier" , monospace;"}]{style="white-space: pre-wrap;"}\
[[}]{style="font-family: "courier new" , "courier" , monospace;"}]{style="white-space: pre-wrap;"}\
\
\... And, yes, we can see that the 230 bus line exists!\
\

Coming Up Next Article\...
--------------------------

We have covered a bit about REST APIs before. Last year we covered:\
\

-   [How to use Apache HTTP
    Components](http://www.tjmaher.com/2016/02/restful-testing-with-stripe-brief.html),
    such as HTTP Get, with Java testing the Stripe API
-   [An Introduction to REST
    APIs](http://www.tjmaher.com/2016/07/introduction-to-api-testing-with.html):
    How manual testers can automate using Postman, JSON, and JavaScript

<div>

For this section, we will be covering how to use Java, TestNG and REST
Assured to interact with MBTAs API. 

</div>

\
\
\
Until then, Happy Testing!\
\
\

::: {#toc-section .toc-section}
**Are you sure the bus line is still listed?**\

-   **Part One:** [Don\'t gather data from the UI. Use a RESTful API
    endpoint
    instead!](http://www.tjmaher.com/2017/02/are-you-sure-bus-line-still-listed.html)
-   **Part Two:** [Interacting with the MBTA\'s API using REST
    Assured](http://www.tjmaher.com/2017/03/are-you-sure-bus-line-is-still-listed.html)
-   **Source Code:** [GitHub, T.J.
    Maher](https://github.com/tjmaher/RestAssuredJavaDemo/blob/master/src/test/java/MbtaRoutesTest.java)
:::

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
