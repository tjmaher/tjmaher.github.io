\-\-- layout: post title: \'Are you sure the bus line is still listed?:
Interacting with the MBTA\'\'s API using REST Assured\' date:
\'2017-03-24T19:42:00.001-04:00\' author: T.J. Maher tags: - Rest API -
REST Assured modified\_time: \'2018-02-27T22:39:38.395-05:00\'
thumbnail:
https://4.bp.blogspot.com/-lFlZLvPfUUg/WKDFiTiKUII/AAAAAAAALno/nDSWYPMBi0oqkhpbwsHTTcc3210yS74-wCLcB/s72-c/T.png
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-1905930021753303033
blogger\_orig\_url:
http://www.tjmaher.com/2017/03/are-you-sure-bus-line-is-still-listed.html
\-\-- *This is the second part of a blog series on REST APIs and the
REST Assured Java library. Did you want to go [back to the
beginning](http://www.tjmaher.com/2017/02/are-you-sure-bus-line-still-listed.html)?*\
\
Let\'s say you are an automation developer on a team developing in Java
a new public transportation web application. The customer base for the
app is located in Southeastern Massachusetts in the United States.\

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://4.bp.blogspot.com/-lFlZLvPfUUg/WKDFiTiKUII/AAAAAAAALno/nDSWYPMBi0oqkhpbwsHTTcc3210yS74-wCLcB/s200/T.png){width="200" height="200"}](https://4.bp.blogspot.com/-lFlZLvPfUUg/WKDFiTiKUII/AAAAAAAALno/nDSWYPMBi0oqkhpbwsHTTcc3210yS74-wCLcB/s1600/T.png)

                                                                                *The MBTA system in Massachusetts controls buses, subways and commuter rail in Boston and its suburbs.\
                    The subway system is collectively known as \"The T\", as in \"Taking the T into Boston\" or \"The T is running slow\... again!\" and is divided into the Red, Green, and Orange Line, with a bus route called the Silver Line. *
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

<div>

\

</div>

<div>

How can you prove that the \#230 bus line, running from the Montello
Commuter Rail in Brockton, MA to Braintree MBTA station all the way to
Quincy Center Station is still listed in the system?

</div>

<div>

\

</div>

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://3.bp.blogspot.com/-qqCWiopKUGo/WKDDrAFWD2I/AAAAAAAALnc/T3gNzwi5vVU6hDiy6L9nV1c0X7eOFh4PgCLcB/s400/MBTA%2BBus%2B230%2Bin%2BQuincy.JPG){width="400" height="300"}](https://3.bp.blogspot.com/-qqCWiopKUGo/WKDDrAFWD2I/AAAAAAAALnc/T3gNzwi5vVU6hDiy6L9nV1c0X7eOFh4PgCLcB/s1600/MBTA%2BBus%2B230%2Bin%2BQuincy.JPG)
                                                                                                                         *Are you sure this bus line is still listed in the system? If not, it\'s a bug.*
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

\
[]{#more}\
\
[With the last blog
entry](http://www.tjmaher.com/2017/02/are-you-sure-bus-line-still-listed.html),
we described why getting this information from the MBTA website
\<<http://www.mbta.com/>\> would not be the best solution. We also
covered how using the MBTA\'s Application Program Interface (API),
MBTA-Realtime \<<http://realtime.mbta.com/Portal/>\>, we can easily get
the information by:\

-   Going to
    <http://realtime.mbta.com/developer/api/v2/routes?api_key=wX9NwuHnZU2ToO7GmGR9uw&format=json>
    to view all routes, and eyeball that \"route\_id : 230\" is still
    there. 
-   The MBTA API team graciously provides a public access key,
    wX9NwuHnZU2ToO7GmGR9uw, that we can use to play around with their
    system. This Public API key can change at any time. If the key no
    longer works, check out the [MBTA Developer Portal
    Download](http://realtime.mbta.com/Portal/Home/Download) section to
    find out the new key. 
-   Of course, if you are creating a web or mobile app for real,
    [Register for a free API
    key](http://realtime.mbta.com/Portal/Account/Register). 

\
But how could we turn this into an automated test?\
\
Last year, we talked about how to interact with RESTful APIs with
[Apache Http
Components](http://www.tjmaher.com/2016/02/restful-testing-with-stripe-brief.html),
or with
[Postman](http://www.tjmaher.com/2016/07/introduction-to-api-testing-with.html).
With this blog post we are going to use **REST Assured**, referred to me
by automation development consultants Alan Richardson and Baz Dijkstra.\
\
**Alan Richardson:**\

> ::: {dir="ltr" lang="en"}
> [\@tjmaher1](https://twitter.com/tjmaher1)
> [\@TourDeDave](https://twitter.com/TourDeDave) I start with
> RestAssured and I use HttpClient. I\'m going to investigate Unirest
> soon.
> :::
>
> --- Alan Richardson (\@eviltester) [October 6,
> 2016](https://twitter.com/eviltester/status/783916918063394816)

**\
Baz Dijkstra:**\

> ::: {dir="ltr" lang="en"}
> [\@tjmaher1](https://twitter.com/tjmaher1) you\'re welcome! Feel free
> to put it to good use :) Would love to hear how your demo went
> :::
>
> --- Bas Dijkstra (\@\_basdijkstra) [November 12,
> 2016](https://twitter.com/_basdijkstra/status/797401612381814784)

\
\

What is REST Assured?
---------------------

REST Assured \<<https://github.com/rest-assured/rest-assured>\> was
developed as a Java library to handle complex interaction with a REST
API simply. According to the REST Assured site at
\<<http://rest-assured.io/>\>:\
\
*\"REST Assured is developed and maintained by [Johan
Haleby](https://twitter.com/johanhaleby) with the help of numerous other
[contributors](https://github.com/rest-assured/rest-assured/contributors)
over the years. Would you like to contribute to the project in any way?
Submit a [pull request](https://github.com/rest-assured/rest-assured) or
contact Johan at [Twitter](https://twitter.com/johanhaleby).*\

<div>

*\
\"Johan started the project when he was working at
[Jayway](https://www.jayway.com/) back in December of 2010. The project
is now sponsored by [Parkster](https://www.parkster.se/)\". *\
\
Johan is currently a [Senior Software Developer and Architect at
Parkster AB in Sweden. REST Assured is up
to ]{style="background-color: white; color: #333333; font-family: inherit; font-size: 16px; font-style: inherit; font-weight: inherit;"}version
3.0.3 released on January 20, 2016.\

::: {#demographics .demographic-info .adr .editable-item style="background-color: white; border: 0px; color: #66696a; font-family: Helvetica, FreeSans, "Liberation Sans", Helmet, Arial, sans-serif; font-size: 13px; font-stretch: inherit; font-variant-numeric: inherit; line-height: 17px; margin: 2px 0px; padding: 0px; text-size-adjust: 100%; vertical-align: baseline;"}
::: {#location-container data-li-template="location" style="border: 0px; font-family: inherit; font-stretch: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; line-height: inherit; margin: 0px; padding: 0px; text-size-adjust: 100%; vertical-align: baseline;"}
:::
:::

\

Need help API Testing with REST Assured? 
-----------------------------------------

\
On REST Assured\'s official site \<<http://rest-assured.io/>\> it this
lists this note, dated June 17, 2016:\

-   *\"[Bas Dijkstra](https://www.linkedin.com/in/basdijkstra) has been
    generous enough to open source his REST Assured workshop. You can
    read more about this
    [here](http://www.ontestautomation.com/open-sourcing-my-workshop-an-experiment/)
    and you can try out, and contribute to, the exercises available in
    [his](https://github.com/basdijkstra/workshops/) github
    repository\".*

According to Bas\' article, [Efficient API testing: How to get started
with REST
Assured](https://techbeacon.com/efficient-api-testing-how-get-started-rest-assured) published
in TechBeacon *(Feb 8, 2017),* there are three main reasons for using
REST Assured, instead of doing it yourself:\

-   *\"It removes the need for writing a lot of boilerplate code
    required to set up an HTTP connection, send a request and receive
    and parse a response*
-   *\"It supports a Given/When/Then test notation, which instantly
    makes your tests human readable*
-   *\"Since REST Assured is a Java library, integrating it into a
    continuous integration / continuous delivery setup is a breeze,
    especially when combined with a Java testing framework such as JUnit
    or TestNG\"*

How Could We Interact With MBTA\'s API With REST Assured?
---------------------------------------------------------

Testing the application through the API \-- and not the web user
interface \-- means that we can test the system quickly and easily
without having to wait for a browser.\
\
We can test that:\
\

-   Entering the public API Key, that we get the HTTP Status Code of
    OK: 200.
    See <http://realtime.mbta.com/developer/api/v2/routes?api_key=wX9NwuHnZU2ToO7GmGR9uw&format=json> 
-   We cannot access the data without the correct API Key:
    See <http://realtime.mbta.com/developer/api/v2/routes?format=json>
-   If we so choose, we can have the data returned to us in a JSON-style
    format, as opposed to XML. 
-   We should receive the data back to us in less than two seconds.
-   Finally, we can test that, yes, the 230 bus line is listed in the
    system. 

<div>

\... And all these tests can be run in **less than three seconds**! 

</div>

<div>

\

</div>

<div>

For these tests, we will be using as resources:

</div>

<div>

-   [Java](https://www.oracle.com/java/index.html) as the main
    programming language. 
-   [TestNG](http://testng.org/doc/) as the test framework, with
    its \@BeforeClass and \@Test annotation to set up pre-conditions for
    tests and run them. (Want to use JUnit instead? Perfectly fine!)
-   The [Java Hamcrest](http://hamcrest.org/JavaHamcrest/) library to
    use the assertThat keyword. I just think it is more readable. You
    could use regular assertTrue or assertEqual if you really wanted
    to. 
-   The Java Utility called TimeUnit to keep track of milliseconds the
    test runs (see JavaWorld\'s [The Highly Useful Java TimeUnit
    Enum](http://www.javaworld.com/article/2074114/core-java/the-highly-useful-java-timeunit-enum.html)). 
-   [REST Assured](http://rest-assured.io/) to handle interacting with
    sending and receiving information from the RESTful endpoint.

Feel free to steal and modify this code! I did! When I was playing
around with the code in Bas\' REST Assured Workshop, I had quite a
difficult time trying to modify it to fit the MBTA\'s API. Thank you so
much for the help, Baz! 

</div>

<div>

\

</div>

<div>

The following tests will kick the tires of the API itself, to see if
everything is in good working order. 

</div>

<div>

\

</div>

<div>

**[Validate that, if selected, data will be formatted to
JSON:]{.underline}**

</div>

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 import static io.restassured.RestAssured.*;  
 import io.restassured.RestAssured;  
 import static org.hamcrest.Matchers.*;  
 import org.testng.annotations.BeforeClass;  
 import org.testng.annotations.Test;  
 import java.util.concurrent.TimeUnit;  
 /**   
  * Based on https://github.com/basdijkstra/workshops/blob/master/rest-assured/RestAssuredWorkshop  
  *  
  * Need to connect to the MBTA API manually?  
  * http://realtime.mbta.com/developer/api/v2/routes?api_key=wX9NwuHnZU2ToO7GmGR9uw&format=json  
  */  
 public class MbtaRoutesTest {  
   @BeforeClass  
   public static void initPath() {  
     RestAssured.baseURI = "http://realtime.mbta.com/developer/api/v2/";  
   }  
   @Test  
   public void checkResponseContentTypeIsJson() {  
     given().  
         param("api_key","wX9NwuHnZU2ToO7GmGR9uw").  
         param("format","json").  
     when().get("routes").  
     then().assertThat().contentType("application/json");  
   }  
```

**[\
]{.underline}[Validate that, if given the correct API key, the HTTP
Status Code will be OK: 200]{.underline}**\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
   @Test  
   public void checkResponseCodeIsOk200() {  
     given().  
         param("api_key","wX9NwuHnZU2ToO7GmGR9uw").  
         param("format","json").  
     when().get("routes").  
     then().assertThat().statusCode(200);  
   }  
```

\
**[Validate that, if not entering the correct API Key, the user cannot
see data:]{.underline}**\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
   @Test  
   public void checkUserCannotAccessApiWithoutKey() {  
     given().  
         param("api_key","invalid-key").  
         param("format","json").  
     when().get("routes").  
     then().assertThat().statusCode(401);  
   }  
```

**[\
]{.underline}[Validate that it will take less than two seconds for data
to be returned:]{.underline}**\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
   @Test  
   public void checkResponseTimeIsLessThan2seconds() {  
     given().  
         param("api_key","wX9NwuHnZU2ToO7GmGR9uw").  
         param("format","json").  
     when().get("routes").  
     then().assertThat().time(lessThan(2000L), TimeUnit.MILLISECONDS);  
   }  
```

\
Next, we can check that, yes, the 230 Bus Route is still listed.\
\
If we manually go to the URL and have the data processed, it will look
like:\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 {  
  "mode": [  
   {  
    "route_type": "0",  
    "mode_name": "Subway",  
    "route": [  
     {  
      ...  
     }  
    ]  
   },  
   {  
    "route_type": "1",  
    "mode_name": "Subway",  
    "route": [  
     {  
      "route_id": "Red",  
      "route_name": "Red Line"  
     .....  
     }  
    ]  
   },  
   {  
    "route_type": "2",  
    "mode_name": "Commuter Rail",  
    "route": [  
     {  
      ....  
     }  
    ]  
   },  
   {  
    "route_type": "3",  
    "mode_name": "Bus",  
    "route": [  
     {  
      ....  
     },  
     {  
      "route_id": "230",  
      "route_name": "230"  
     },  
    ]  
   },  
   {  
    "route_type": "4",  
    "mode_name": "Boat",  
    "route": [  
     {  
      "route_id": "Boat-F4",  
      "route_name": "Charlestown Ferry"  
     }
    ]  
   }  
  ]  
 }  
```

\
**[\
]{.underline}[Validate that the 230 Bus Route Is Listed:]{.underline}**\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
   @Test  
   public void checkThatRoute230isListed() {  
     given().  
         param("api_key","wX9NwuHnZU2ToO7GmGR9uw").  
         param("format","json").  
     when().get("routes").  
     then().assertThat().  
         statusCode(200).  
         body("mode.mode_name", hasItems("Bus"),  
             "mode[3].route.route_name", hasItem("230"));;  
   }  
```

\
If we run all the tests at the same time, we can see that:\

::: {.separator style="clear: both; text-align: center;"}
[![](https://3.bp.blogspot.com/-P_SG1QBfmrE/WNWuEwVKl3I/AAAAAAAALro/lyCsLNJ6ls0BGAOHCeA9etR1iSVLgE54ACLcB/s640/Screen%2BShot%2B2017-03-24%2Bat%2B7.36.18%2BPM.png){width="640"
height="156"}](https://3.bp.blogspot.com/-P_SG1QBfmrE/WNWuEwVKl3I/AAAAAAAALro/lyCsLNJ6ls0BGAOHCeA9etR1iSVLgE54ACLcB/s1600/Screen%2BShot%2B2017-03-24%2Bat%2B7.36.18%2BPM.png)
:::

\

-   All five tests passed!
-   It took less than three seconds for all the tests to run.
-   Yes, Bus \#230 is listed!

\
\
Once again, thank you very much, Bas, for your help with this!\
\
Happy Testing!\
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

\
