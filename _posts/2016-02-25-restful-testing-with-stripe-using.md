\-\-- layout: post title: \'RESTful Testing with Stripe: Using
UriBuilder, HttpGet and other Apache HttpComponents\' date:
\'2016-02-25T00:03:00.000-05:00\' author: T.J. Maher tags: - code
examples - Java - intermediate - Rest API modified\_time:
\'2016-04-29T07:36:21.636-04:00\' blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-5765424463201572531
blogger\_orig\_url:
http://www.tjmaher.com/2016/02/restful-testing-with-stripe-using.html
\-\-- *This post is fourth in a series of six. Need to go [back to the
beginning](/2016/02/coming-up-how-to-work-with-rest-apis.html)?*\
\
Now that we built a skeleton framework to test using the Stripe REST
API, storing and retrieving the API Key, we can perform actions. We are
going to:\

-   Create a method called getListOfCharges in our StripeUtils class,
    where we can pass in how many charges we wish to retrieve. 
-   Create a data object to hold all the information we retrieve.
-   Add functionality that turns the JSON object we get back, and add
    all information into the data object we created, using Google\'s
    GSON library.

### What Our Framework Will Look Like

By the end of this blog post, our automation framework will look like:\
\
[]{#more}\
\
**src/test/java**\

data

-   LoadProperties.java

libraries

-   StripeUtils.java

maps

-   CollectionOfCharges.java

properties

-   qa-properties.properties

testcases

-   Stripe.java

### 

### Design a Simple Data Object

\
Let\'s say we want to get the last Charge object using HTTPS, we would
enter using the public Stripe API Key into our browser:\
\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 https://api.stripe.com/v1/charges?limit=1&key=sk_test_BQokikJOvBiI2HlWgH4olfQ2  
```

\
\... Remembering, of course, that entering a non-public secret API key
into a URL is a completely lousy idea! We will be remedying this later.\
\
If you take a look at the JSON file returned it looks like:\
\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 {  
  "object": "list",  
  "data": [  
   *** LOTS OF CHARGE DATA ***  
  ],  
  "has_more": true,  
  "url": "/v1/charges"  
 }  
```

\
This means we need to create a Data Object to store information, we only
have to worry about  four parameters:\

-   A string named \"object\"
-   Object array named \"data\"
-   A boolean named \"has\_more\"
-   A string named \"url\"

\
Our Data Object will look like\...\
\
stripe.maps.**CollectionOfCharges.java**\

``` {style="background: rgb(240, 240, 240); border: 1px dashed rgb(204, 204, 204); font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; width: 646.469px;"}
 public class CollectionOfCharges {  
  String object;  
  Object[] data;  
  boolean has_more;  
  String url;  
  public String getObject() {  
   return object;  
  }  
  public void setObject(String object) {  
   this.object = object;  
  }  
  public Object[] getData() {  
   return data;  
  }  
  public void setData(Object[] data) {  
   this.data = data;  
  }  
  public boolean isHas_more() {  
   return has_more;  
  }  
  public void setHas_more(boolean has_more) {  
   this.has_more = has_more;  
  }  
  public String getUrl() {  
   return url;  
  }  
  public void setUrl(String url) {  
   this.url = url;  
  }  
 }  
```

\
Next, we need to get the data. We will be doing this with Apache Http
Components.\
\

### Why Use Apache HttpComponents? 

From the Apache [HttpClient
Tutorial](https://hc.apache.org/httpcomponents-client-ga/tutorial/html/):\

> \"The Hyper-Text Transfer Protocol (HTTP) is perhaps the most
> significant protocol used on the Internet today. Web services,
> network-enabled appliances and the growth of network computing
> continue to expand the role of the HTTP protocol beyond user-driven
> web browsers, while increasing the number of applications that require
> HTTP support.\
> \
> \"Although the java.net package provides basic functionality for
> accessing resources via HTTP, it doesn\'t provide the full flexibility
> or functionality needed by many applications. HttpClient seeks to fill
> this void by providing an efficient, up-to-date, and feature-rich
> package implementing the client side of the most recent HTTP standards
> and recommendations.\
> \
> \"Designed for extension while providing robust support for the base
> HTTP protocol, HttpClient may be of interest to anyone building
> HTTP-aware client applications such as web browsers, web service
> clients, or systems that leverage or extend the HTTP protocol for
> distributed communication\".

\
\

\

### What Does Http Client Do?

> \
> \"The most essential function of HttpClient is to execute HTTP
> methods. Execution of an HTTP method involves one or several HTTP
> request / HTTP response exchanges, usually handled internally by
> HttpClient. The user is expected to provide a request object to
> execute and HttpClient is expected to transmit the request to the
> target server return a corresponding response object, or throw an
> exception if execution was unsuccessful.\
> \"Quite naturally, the main entry point of the HttpClient API is the
> HttpClient interface that defines the contract described above\".

\

### Parts of a URI

\
A web address or URL \-- Universal Resource Locator \-- is a type of
Uniform Resource Identifier, one that points to a physical location such
as a server. A URI, though, is more abstract.\
\
There are many parts to a URI as shown below:\
\
[
]{style="background-color: #f9f9f9; font-family: monospace , "courier"; font-size: 14px; line-height: 1.3em; white-space: pre-wrap;"}**scheme**[:\[]{style="background-color: #f9f9f9; font-family: monospace , "courier"; font-size: 14px; line-height: 1.3em; white-space: pre-wrap;"}**//**[\[]{style="background-color: #f9f9f9; font-family: monospace , "courier"; font-size: 14px; line-height: 1.3em; white-space: pre-wrap;"}**user:password@**[\]]{style="background-color: #f9f9f9; font-family: monospace , "courier"; font-size: 14px; line-height: 1.3em; white-space: pre-wrap;"}**host**[\[]{style="background-color: #f9f9f9; font-family: monospace , "courier"; font-size: 14px; line-height: 1.3em; white-space: pre-wrap;"}**:port**[\]\]\[]{style="background-color: #f9f9f9; font-family: monospace , "courier"; font-size: 14px; line-height: 1.3em; white-space: pre-wrap;"}**/**[\]]{style="background-color: #f9f9f9; font-family: monospace , "courier"; font-size: 14px; line-height: 1.3em; white-space: pre-wrap;"}**path**[\[?]{style="background-color: #f9f9f9; font-family: monospace , "courier"; font-size: 14px; line-height: 1.3em; white-space: pre-wrap;"}**query**[\]\[\#]{style="background-color: #f9f9f9; font-family: monospace , "courier"; font-size: 14px; line-height: 1.3em; white-space: pre-wrap;"}**fragment**[\]]{style="background-color: #f9f9f9; font-family: monospace , "courier"; font-size: 14px; line-height: 1.3em; white-space: pre-wrap;"} \
\

**Scheme**: Can be web based (*http* or *https*), Transporting a file
(*ftp*), or even an email (*mailto*). The Internet Assigned Numbers
Authority keeps track of all schemes. (
[LINK](http://www.iana.org/assignments/uri-schemes/uri-schemes.xhtml) ).

**Authority**: 

-   Optional username, or the username & password.
-   **Host**, such as the domain name, registered name or hostname
-   Optional **port** name such as :8088.

**Path:*** *The subdirectory, such as */v1/charges.* 

**Query**: Everything starting with the *?* symbol in the URI is a
query. 

-   URIBuilder then allows you to add names and values to
    **Parameters**, such as *key* and *sk\_test* or *limit* and *3*.

### Get the Last Three Charges

\
Let\'s say you want to retrieve a list of charges from the API is
passing into the getListOfCharges how many charge orders to get. What is
the limit? One? Two? Five? Eight?\
\
If we were manually testing if the API can retrieve the last *three*
charges, we would enter the following code into our web browser to form
the HTTP GET statement\...\
\

``` {.hljs .language-bash style="background: rgb(39, 43, 45); border-radius: 5px; border: 0px; color: #d0d0d0; direction: ltr; font-family: 'source code pro', menlo, monospace; font-size: 13px; line-height: 1.5em; outline: 0px; padding: 20px 40px; vertical-align: baseline; white-space: pre-wrap; word-break: normal;"}
https://api.stripe.com/v1/charges?limit=3&key=sk_test_BQokikJOvBiI2HlWgH4olfQ2
```

\
\... And place the JSON parameters into something such as an Excel
spreadsheet.\
\
Instead we are going to use Apache Http Components to do the work for
us. We are going to:\
\

-    Break the URI into different pieces and validate them with
    **URIBuilder**. 
-   Add the URI into a **HttpGet** class.
-   Instantiate a new **BasicCredentialsProvider** class, and set
    credentials with the Stripe API key. 
-   Create using **HttpBuilder** an HTTP call holding the credentials.
-   Store the call in a **CloseableHttpClient**.
-   Execute the HttpGet statement, storing the results in a
    **HttpResponse** class. 
-   Examine the response\'s status line and status code to see if it the
    status was OK, with a value of \"200\". If not, we are going to
    throw an error. 

\
Got that? \... No? Okay, we are going to walk through this again\... We
went through so many steps, I even lost myself!\

####  URIBuilder

\
We are going to use URI Builder to construct the URI we will be using to
connect to the API:\

-   Set the scheme to be https.
-   Set the host to be api.stripe.com. 
-   Set the path to be /v1/charges.
-   Set the parameter \"limit\" to be whatever limit has been passed.

``` {style="background: rgb(240, 240, 240); border: 1px dashed rgb(204, 204, 204); font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; width: 646.469px;"}
URIBuilder uriBuilder = new URIBuilder();  
     uriBuilder.setScheme("https")  
       .setHost("api.stripe.com")  
       .setPath("/v1/charges")  
       .setParameter("limit", limit.toString();  
```

#### [\...Why use URI Builder instead of feeding the straight URL into the API? Validation:]{style="font-weight: normal;"}

-   If you accidentally have a blank space in the URL, it will tell you
    exactly where there is an Illegal Character. 

#### HttpGet

We are going to try the following:\

-   Build the URI according to the parameters we set up. 
-   Compose an HTTP GET Method based on the URI. 
-   Set up using BasicCrendentialsProvider the
    UsernamePasswordCredentials. We will add the Stripe API Key here. 
-   We then build with HttpClientBuilder and instantiate with
    CloseableHttpClient the credentials. 
-   Finally, we execute the Http Client using the HttpGet statement we
    set up. 

``` {style="background: rgb(240, 240, 240); border: 1px dashed rgb(204, 204, 204); font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; width: 646.469px;"}
URI uri = uriBuilder.build();  
       HttpGet httpGet = new HttpGet(uri);  
       BasicCredentialsProvider credentialsProvider = new BasicCredentialsProvider();  
       credentialsProvider.setCredentials(AuthScope.ANY, new UsernamePasswordCredentials(Stripe.apiKey, ""));  
       CloseableHttpClient client = HttpClientBuilder.create().setDefaultCredentialsProvider(credentialsProvider).build();  
       HttpResponse response = client.execute(httpGet);  
```

\

### 

#### Check Status Code

Are there problems? Is the response anything but 200-OK? We are going to
throw an error.\
\

``` {style="background: rgb(240, 240, 240); border: 1px dashed rgb(204, 204, 204); font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; width: 646.469px;"}
if (statusCode != 200) {  
         String errorMessage = "ERROR: Attempting to Capture Charge: " + statusCode + "\n"  
           + "Reason: " +  
           response.getStatusLine().getReasonPhrase();  
         throw new TestException (errorMessage); 
```

\
\

#### Convert Results into String

If everything is successful, we are going to \

-   Take that response and get the entity. 
-   Convert the entity into a String format, using
    EntityUtils.toString. 

\

``` {style="background: rgb(240, 240, 240); border: 1px dashed rgb(204, 204, 204); font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; width: 646.469px;"}
String json = EntityUtils.toString(response.getEntity()); 
```

\
\

#### Use GSON

\
Once we have the JSON Feed as a String, we are going to use Google\'s
GSON library to take the String and place it in the CollectionOfCharges
class we just created.\
\

``` {style="background: rgb(240, 240, 240); border: 1px dashed rgb(204, 204, 204); font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; width: 646.469px;"}
chargesRetrieved = gson.fromJson(json, CollectionOfCharges.class);
```

\
\... we will go over GSON a few blog posts from now.\

####  Check for Errors

\
If there is anything wrong with:\

-   URI Synatax \... a URI Syntax Exception is thrown.
-   If input or output cannot be read, an IOException is thrown.

A [URISyntaxException](http://docs.oracle.com/javase/6/docs/api/java/net/URISyntaxException.html?is-external=true)
 will tell you what exactly was messed up, returning the String, the
reason for the error, and exactly where the error occurred.\
\
\
\... We are going to print a stack trace so we can figure out what went
wrong.\
\

``` {style="background: rgb(240, 240, 240); border: 1px dashed rgb(204, 204, 204); font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; width: 646.469px;"}
catch (URISyntaxException e) {  
       e.printStackTrace();  
     } catch (IOException e) {  
       e.printStackTrace();  
```

\
Putting it all together, our code looks like: \
Adding  **getListOfCharges** to **StripeUtils.java**.\

``` {style="background: rgb(240, 240, 240); border: 1px dashed rgb(204, 204, 204); font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; width: 646.469px;"}
 public CollectionOfCharges getListOfCharges(Integer limit){  
     CollectionOfCharges chargesRetrieved = new CollectionOfCharges();  
     Gson gson = new Gson();  
     URIBuilder uriBuilder = new URIBuilder();  
     uriBuilder.setScheme("https")  
       .setHost("api.stripe.com")  
       .setPath("/v1/charges")  
       .setParameter("limit", limit.toString());  
     try {  
       URI uri = uriBuilder.build();  
       HttpGet httpGet = new HttpGet(uri);  
       BasicCredentialsProvider credentialsProvider = new BasicCredentialsProvider();  
       credentialsProvider.setCredentials(AuthScope.ANY, new UsernamePasswordCredentials(Stripe.apiKey, ""));  
       CloseableHttpClient client = HttpClientBuilder.create().setDefaultCredentialsProvider(credentialsProvider).build();  
       HttpResponse response = client.execute(httpGet);  
       int statusCode = response.getStatusLine().getStatusCode();  
       if (statusCode != 200) {  
         String errorMessage = "ERROR: Attempting to Capture Charge: " + statusCode + "\n"  
           + "Reason: " +  
           response.getStatusLine().getReasonPhrase();  
         throw new TestException (errorMessage);  
       }  
       String json = EntityUtils.toString(response.getEntity());  
       chargesRetrieved = gson.fromJson(json, CollectionOfCharges.class);  
       client.close();  
     } catch (URISyntaxException e) {  
       e.printStackTrace();  
     } catch (IOException e) {  
       e.printStackTrace();  
     }  
     return chargesRetrieved;  
   }  
```

\
\

### Writing an API Test

\
If you go back to Stripe API Documentation, where it says [List
Charges](https://stripe.com/docs/api#list_charges), you will see the
following:\
\

``` {.language-json style="background: rgb(39, 43, 45); border-radius: 5px; border: 0px; color: #d0d0d0; direction: ltr; font-family: 'Source Code Pro', Menlo, monospace; font-size: 13px; line-height: 1.5em; outline: 0px; padding: 20px 40px; tab-size: 4; vertical-align: baseline; white-space: pre-wrap; word-break: normal;"}
{
  "object": "list",
  "url": "/v1/charges",
```

\
\... The name \"object\" should return the value \"list\". The name
\"url\" should return \"/v1/charges\".\
\
Let\'s make that the test!\
\
First let\'s see if that is what is returned, with a quick little test
we can put in the Stripe.java test class we created in the testcases
folder during our last blog.\
\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 @Test  
   public void test_printCollectionOfChargesParameters(){  
     Integer numberOfChargesReturned = 2;  
     StripeUtils stripe = new StripeUtils(Locale.US);  
     CollectionOfCharges charges = stripe.getListOfCharges(numberOfChargesReturned);  
     System.out.println("Object: " + charges.getObject());  
     System.out.println("URL: " + charges.getUrl());  
   }  
```

\
Running this test we get:\
\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 [TestNG] Running:  
  C:\Users\tmaher\.IdeaIC15\system\temp-testng-customsuite.xml  
 Object: list  
 URL: /v1/charges  
   
 ===============================================  
 Default Suite  
 Total tests run: 1, Failures: 0, Skips: 0  
 ===============================================  
```

\
\... We now can absolutely confirm the output matches the documentation
\-- Always a good thing!\
\
Let\'s changes the print statements to assert statements\...\
\
\... And also refactor the *getObject* to *getObjectType*. The charge
objects are stored in \"data\". It seems to be more of an object type
that an actual object, so let\'s name it as such. With IntelliJ, I can
*Refactor -\> Rename*, and the name of the method gets changed
everywhere in our automated test.\
\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 @Test  
   public void test_returnedCollectionOfChargesParameters(){  
     String expectedObjectType = "list";  
     String expectedUrl = "/v1/charges";  
     Integer numberOfChargesReturned = 2;  
     StripeUtils stripe = new StripeUtils(Locale.US);  
     CollectionOfCharges charges = stripe.getListOfCharges(numberOfChargesReturned);  
     assertEquals(charges.getObjectType(), expectedObjectType);  
     assertEquals(charges.getUrl(), expectedUrl);  
   }  
```

\
Hrm. I still am not happy with it. This test? It\'ll run, and it will
pass or fail depending on if the expected parameters matches what is
actually captured, but I prefer some type of logging explicitly spelling
out exactly:\
\

-   What is the test is supposed to do?
-   What is the expected output?
-   What is the actual mark? 
-   In plain English, does it (PASS) or does it (FAIL)?

\
The assert statement isn\'t enough for me. Let\'s borrow some code I
whipped up in my last project to handle reporting, and place it in the
test class.\
\
**checkMatchingValues:**\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 private boolean checkMatchingValues(String testHeading, Object actualValue, Object expectedValue) {  
     String successMessage = "\t* The Expected and Actual Values match. (PASS)\n";  
     String failureMessage = "\t* The Expected and Actual Values do not match! (FAIL)\n";  
   
     boolean doValuesMatch = false;  
   
     System.out.println(testHeading);  
     System.out.println("\t* Expected Value: " + expectedValue);  
     System.out.println("\t* Actual Value: " + actualValue);  
   
     if (actualValue.equals(expectedValue)) {  
       System.out.println(successMessage);  
       doValuesMatch = true;  
     } else {  
       System.out.println(failureMessage);  
       doValuesMatch = false;  
     }  
     return doValuesMatch;  
   }  
   
```

\
\... Now, I might be able to get the output I like to see.\
\
The new test looks like:\
\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 @Test  
   public void test_returnedCollectionOfChargesParameters(){  
     String expectedObjectType = "list";  
     String expectedUrl = "/v1/charges";  
     Integer numberOfChargesReturned = 2;  
     StripeUtils stripe = new StripeUtils(Locale.US);  
     CollectionOfCharges charges = stripe.getListOfCharges(numberOfChargesReturned);  
   
     String actualObjectType = charges.getObjectType();  
     checkMatchingValues("Verify that the Returned Collection Object types match", actualObjectType, expectedObjectType);  
     assertEquals(actualObjectType, expectedObjectType, "ERROR: The Object types do not match!");  
   
     String actualUrl = charges.getUrl();  
     checkMatchingValues("Verify that the Returned Collection URLs match", actualUrl, expectedUrl);  
     assertEquals(actualUrl, expectedUrl, "ERROR: The urls do not match!");  
   }  
```

\
\... And the output of the test looks like \...\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 [TestNG] Running:  
  C:\Users\tmaher\.IdeaIC15\system\temp-testng-customsuite.xml  
 Verify that the Returned Collection Object types match  
      * Expected Value: list  
      * Actual Value: list  
      * The Expected and Actual Values match. (PASS)  
   
 Verify that the Returned Collection URLs match  
      * Expected Value: /v1/charges  
      * Actual Value: /v1/charges  
      * The Expected and Actual Values match. (PASS)  
   
   
 ===============================================  
 Default Suite  
 Total tests run: 1, Failures: 0, Skips: 0  
 ===============================================  
```

\
Nice output. It\'s clear cut. You know exactly what is being tested.
Call it the manual tester in me, but I get suspicious of positive
results as much as negative results. If everything is spelled out, it is
easier to spot an error.\
\
If you want to examine the code, it can be viewed on GitHub
at <https://github.com/tjmaher/RESTful_Testing_Using_Stripe>.\
\
Next week, we will examine Google GSON more closely, and write a few
more Stripe tests on capturing charges.\
\
![](http://feedburner.google.com/fb/images/pub/feed-icon16x16.png)[  ]{style="background-color: white; color: #222222; font-family: "calibri"; font-size: 15.4px; line-height: 21.56px;"}**Subscribe
to
Blog:**[ ]{style="background-color: white; color: #222222; font-family: "calibri"; font-size: 15.4px; line-height: 21.56px;"}\

-   [](http://feeds.feedburner.com/AdventuresInAutomation)[Via RSS
    Feed](http://feeds.feedburner.com/AdventuresInAutomation)
-   [Via
    Email](https://feedburner.google.com/fb/a/mailverify?uri=AdventuresInAutomation)

\
Until then, happy testing!\
\
**NEXT:** [From JSON to Object: HttpEntity and
GSON](/2016/02/restful-testing-with-stripe-from-json.html)

\
\
\

::: {#toc-section .toc-section}
**RESTful Testing with Stripe:**

-   [Introduction](/2016/02/coming-up-how-to-work-with-rest-apis.html)
-   **Part One:** [Intro to REST
    APIs](/2016/02/restful-testing-with-stripe-brief.html)
-   **Part Two:** [Interacting with Stripe using HTTPS and
    cURL](/2016/02/restful-testing-with-stripe-interacting.html)
-   **Part Three:** [API Keys, Property files, and Initial
    Setup](/2016/02/restful-testing-with-stripe-storing-api_23.html)
-   **Part Four:** [UriBuilder, HttpGet and other Apache
    HttpComponents](/2016/02/restful-testing-with-stripe-using.html)
-   **Part Five:** [From JSON to Object: HttpEntity and
    GSON](/2016/02/restful-testing-with-stripe-from-json.html)
-   **Source Code:** [GitHub, T.J.
    Maher](https://github.com/tjmaher/RESTful_Testing_Using_Stripe)
:::

\
\
[-T.J.
Maher]{style="background-color: white; color: #222222; font-family: "calibri"; font-size: 15.4px; line-height: 21.56px;"}\

::: {style="background-color: white; color: #222222; font-family: Calibri; font-size: 15.4px; line-height: 21.56px;"}
\* Sr. QA Engineer, Fitbit*\
* Boston, MA*
:::

::: {style="background-color: white; color: #222222; font-family: Calibri; font-size: 15.4px; line-height: 21.56px;"}
*\
*
:::

::: {style="background-color: white; color: #222222; font-family: Calibri; font-size: 15.4px; line-height: 21.56px;"}
*// Automated tester for \[ 11 \] month and counting!*\
*\
Please note: \'Adventures in Automation\' is a personal blog about
automated testing. It is not an official blog
of [Fitbit.com](http://www.fitbit.com/). *
:::
