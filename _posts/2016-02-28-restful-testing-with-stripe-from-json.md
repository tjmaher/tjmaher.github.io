\-\-- layout: post title: \'RESTful Testing with Stripe: From JSON to
Object using GSON\' date: \'2016-02-28T14:26:00.000-05:00\' author: T.J.
Maher tags: - code examples - Java - intermediate - Rest API
modified\_time: \'2016-04-29T07:36:51.733-04:00\' blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-9034726755254727625
blogger\_orig\_url:
http://www.tjmaher.com/2016/02/restful-testing-with-stripe-from-json.html
\-\-- *This post is fifth in a series of six. Need to go [back to the
beginning](/2016/02/coming-up-how-to-work-with-rest-apis.html)?*\
\
With RESTful Testing with Stripe: Using UriBuilder, HttpGet and other
Apache HttpComponents, we focused on laying groundwork for communicating
with the Stripe API endpoint, sending messages and retrieving data.\

-   JSON response was retrieved
-   JSON was converted it into a JSON string
-   Google\'s GSON library was used to place it in a data object we
    created.

\... But how exactly did this process happen?\
\
Let\'s simplify things and set all the charge object data to *null* in
our JSON file.\
[]{#more}\
**JSON:**\

``` {.language-json style="background: rgb(39, 43, 45); border-radius: 5px; border: 0px; direction: ltr; font-family: 'Source Code Pro', Menlo, monospace; font-size: 13px; line-height: 1.5em; outline: 0px; padding: 20px 40px; tab-size: 4; vertical-align: baseline; white-space: pre-wrap; word-break: normal;"}
{
  "object": "list",
  "url": "/v1/charges",
  "has_more": false,
  "data": null
}
```

\
We want to take this data and place it into our Data Object:\
**\
CollectionOfCharges.java**\

``` {.brush: .javafx}
 public class CollectionOfCharges {  
   String object;  
   Object[] data;  
   boolean has_more;  
   String url;  
```

\
To get from what the JSON file would look like to the Data object would
only take a few lines of code:\
\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 CollectionOfCharges chargesRetrieved = new CollectionOfCharges();  
 Gson gson = new Gson();
 . . .  
 HttpResponse response = client.execute(httpGet);  
 . . .  
 String json = EntityUtils.toString(response.getEntity());  
 chargesRetrieved = gson.fromJson(json, CollectionOfCharges.class);  
```

\
\... We\'ve simplified it from the previous section, removing the logic
that makes sure that everything was OK with a response code of \"200\"
so we can focus on the JSON bits. If you really want to, you can view
our project [source code on
GitHub](https://github.com/tjmaher/RESTful_Testing_Using_Stripe/blob/master/src/test/java/libraries/StripeUtils.java).\
\
Let\'s take a step back and take a look at HTTP Entities and GSON.\
\

### What is an HTTP Entity?

According to the W3C\'s [documentation of HTTP
1.1](https://www.w3.org/Protocols/rfc2616/rfc2616-sec7.html), on section
7.1, the response returned can have many parts, if it was successful:\
\
[Entity Header:]{.underline} Section 7.1:\
\

    entity-header  = Allow                    
                          | Content-Encoding         ; Section 14.11
                          | Content-Language         ; Section 14.12
                          | Content-Length           ; Section 14.13
                          | Content-Location         ; Section 14.14
                          | Content-MD5              ; Section 14.15
                          | Content-Range            ; Section 14.16
                          | Content-Type             ; Section 14.17
                          | Expires                  ; Section 14.21
                          | Last-Modified            ; Section 14.29
                          | extension-header

    extension-header = message-header

\
Let\'s compare this with the HTTP Response we received from Stripe\'s
API.\
**\
HTTP Response:**\

``` {style="background: rgb(240, 240, 240); border: 1px dashed rgb(204, 204, 204); font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; width: 646.469px;"}
 HttpResponseProxy{HTTP/1.1 200 OK [Server: nginx,   
  Date: Mon, 22 Feb 2016 20:53:54 GMT,   
  Content-Type: application/json,   
  Content-Length: 3697,   
  Connection: keep-alive,   
  Access-Control-Allow-Credentials: true,   
  Access-Control-Allow-Methods: GET, POST, HEAD, OPTIONS, DELETE,   
  Access-Control-Allow-Origin: *,   
  Access-Control-Max-Age: 300,   
  Cache-Control: no-cache, no-store,   
 Request-Id: req_7xLNUIt90gVZ9t,   
 Stripe-Version: 2016-02-22,   
 Strict-Transport-Security: max-age=31556926; includeSubDomains]   
 ResponseEntityProxy{  
  [Content-Type: application/json,  
   Content-Length: 3697,  
   Chunked: false]}}  
```

\
\... Originally, the entire block of text was all squeezed onto one
line. It was unreadable, so I added newlines.\
\
**[Entity Body]{.underline}**: Section 7.2:\
\
\"The entity-body (if any) sent with an HTTP request or response is in a
format and encoding defined by the entity-header fields.\
\

           entity-body    = *OCTET

\
\"An entity-body is only present in a message when a message-body is
present, as described in section 4.3. The entity-body is obtained from
the message-body by decoding any Transfer-Encoding that might have been
applied to ensure safe and proper transfer of the message\".\
\

### What is GSON?

> \"Gson is a Java library that can be used to convert Java Objects into
> their JSON representation. It can also be used to convert a JSON
> string to an equivalent Java object. Gson can work with arbitrary Java
> objects including pre-existing objects that you do not have
> source-code of.\
> \
> \"There are a few open-source projects that can convert Java objects
> to JSON. However, most of them require that you place Java annotations
> in your classes; something that you can not do if you do not have
> access to the source-code. Most also do not fully support the use of
> Java Generics. Gson considers both of these as very important design
> goals.\
> \
> \"Gson Goals: \[\...\] Provide simple toJson() and fromJson() methods
> to convert Java objects to JSON and vice-versa\". - [GSON\'s
> GitHub](https://github.com/google/gson)

With GSON you can serialize an object, turning it into JSON code, or you
can deserialize an object, turning the JSON code into an object. Let\'s
say we wanted to serialize then deserialize a string such as \"abcd\".\
*\
Taken from the [GSON User
Guide](https://github.com/google/gson/blob/master/UserGuide.md): *\

-   Serialization: gson.toJson(\"abcd\");       *// ==\> \"abcd\"*
-   Deserialization: String str = gson.fromJson(\"\\\"abcd\\\"\",
    String.class);

*From Wikipedia about
[Serialization](https://en.wikipedia.org/wiki/Serialization)*:\

> \"In computer science, in the context of data storage, serialization
> is the process of translating data structures or object state into a
> format that can be stored (for example, in a file or memory buffer, or
> transmitted across a network connection link) and reconstructed later
> in the same or another computer environment\".

Think of *deserialization* as inflating an object like a beach ball, so
we can properly use it.\
\
Think of *serialization* as deflating the object back to a format such
as a text file or a JSON file so the raw data can be stored and possibly
transmitted.\
\
GSON was an internal tool that Google used, released to the public in
2008.\
\
GSON was co-created by Inderjeet Singh (
[inder123](https://github.com/inder123) ). According to his
[website](http://www.singhinderjeet.com/) , \"I grew up in India but
have been calling Silicon Valley home for the last 18 years. Currently,
I am the Engineering VP and Chief Software Architect at a late-stage Bay
Area startup, Peel Technologies. I joined Peel through the acquisition
of Trymph Inc., a mobile multiplayer platform company where I was the
founder and CEO. Before Trymph, I worked at Google and Sun Microsystems
on products and platforms related to Android, payments, J2EE and other
server-side technologies\".\
\

### Walkthrough 

\
Here is a step-by-step walkthrough what is happening:\
\
1) **Instantiate new CollectionOfCharges:**  The new instance of the
object, *chargesRetrieved*, has all of its values initialized.\
\

``` {style="background: rgb(240, 240, 240); border: 1px dashed rgb(204, 204, 204); font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; width: 646.469px;"}
CollectionOfCharges chargesRetrieved = new CollectionOfCharges(); 
```

> **CollectionOfCharges**:\
>
> -   String object: *null*
> -   Object\[\] data: *null*
> -   boolean has\_more: *false*
> -   String url: *null*

\
2) **Instantiate new GSON object**: We are going to instantiate a new
GSON object, and call it *gson*.\
\

``` {style="background: rgb(240, 240, 240); border: 1px dashed rgb(204, 204, 204); font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; width: 646.469px;"}
Gson gson = new Gson();
```

\
3) **HttpResponse is captured**:\
\

``` {style="background: rgb(240, 240, 240); border: 1px dashed rgb(204, 204, 204); font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; width: 646.469px;"}
HttpResponse response = client.execute(httpGet);
```

\
The response held in the HttpResponse class looks like:\
\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 HttpResponseProxy{HTTP/1.1 200 OK [Server: nginx, Date: Mon, 22 Feb 2016 20:53:54 GMT, Content-Type: application/json, Content-Length: 3697, Connection: keep-alive, Access-Control-Allow-Credentials: true, Access-Control-Allow-Methods: GET, POST, HEAD, OPTIONS, DELETE, Access-Control-Allow-Origin: *, Access-Control-Max-Age: 300, Cache-Control: no-cache, no-store, Request-Id: req_7xLNUIt90gVZ9t, Stripe-Version: 2016-02-22, Strict-Transport-Security: max-age=31556926; includeSubDomains] ResponseEntityProxy{[Content-Type: application/json,Content-Length: 3697,Chunked: false]}}  
```

\
\... You can scroll up a bit to see what the response looks like with
newline characters inserted to improve readability.\
\
4) **Get the Entity from the Response**: Instead of combing steps, we
probably could have written to make it more readable:\
\

-   \"HttpEntity entity = response.getEntity\"

\
[HttpEntity](https://hc.apache.org/httpcomponents-core-ga/httpcore/apidocs/org/apache/http/HttpEntity.html)
is another one of Apache\'s Http Components that we covered in the last
blog post.\
\
It will hold the entity body which consists of the JSON file that was
returned.  We are using Apache\'s HttpResponse method, called getEntity,
to extract from the response the entity body, and place it in the
HttpEntity class.\
\
Using the JSON example we first introduced, the entity body would look
like:\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 {  
  "object": "list",  
  "url": "/v1/charges",  
  "has_more": false,  
  "data": null  
 }  
```

\
5) **Convert Response to String**:\
\

``` {style="background: rgb(240, 240, 240); border: 1px dashed rgb(204, 204, 204); font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; width: 646.469px;"}
String json = EntityUtils.toString(response.getEntity());  
```

\
Use EntityUtils to convert the response to a String.\
\
We could have just as easily hardcoded a string to look like:\
\
String json = \"*{\\n \"object\": \"list\", \\n  \"url\":
\"/v1/charges\",   \\n \"has\_more\": false,   \\n \"data\": null }*\"\
\
\
6) **Insert String to Object**: We are using the GSON method calls
fromJson to take the String called JSON and feed it into
CollectionOfCharges.class.\
\

``` {style="background: rgb(240, 240, 240); border: 1px dashed rgb(204, 204, 204); font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; width: 646.469px;"}
chargesRetrieved = gson.fromJson(json, CollectionOfCharges.class); 
```

\
\... And there you have it!\
\
What, you want me to go into detail about GSON on how the fromJSON
method actually works?\
\
**GitHub for GSON, the toJSON Method:**\

``` {.brush: .javafx}
  /**  
   * This method deserializes the specified Json into an object of the specified class. It is not  
   * suitable to use if the specified class is a generic type since it will not have the generic  
   * type information because of the Type Erasure feature of Java. Therefore, this method should not  
   * be used if the desired type is a generic type. Note that this method works fine if the any of  
   * the fields of the specified object are generics, just the object itself should not be a  
   * generic type. For the cases when the object is of generic type, invoke  
   * {@link #fromJson(String, Type)}. If you have the Json in a {@link Reader} instead of  
   * a String, use {@link #fromJson(Reader, Class)} instead.  
   *  
   * @param <T> the type of the desired object  
   * @param json the string from which the object is to be deserialized  
   * @param classOfT the class of T  
   * @return an object of type T from the string. Returns {@code null} if {@code json} is {@code null}.  
   * @throws JsonSyntaxException if json is not a valid representation for an object of type  
   * classOfT  
   */  
  public <T> T fromJson(String json, Class<T> classOfT) throws JsonSyntaxException {  
   Object object = fromJson(json, (Type) classOfT);  
   return Primitives.wrap(classOfT).cast(object);  
  }  
  /**  
   * This method deserializes the specified Json into an object of the specified type. This method  
   * is useful if the specified object is a generic type. For non-generic objects, use  
   * {@link #fromJson(String, Class)} instead. If you have the Json in a {@link Reader} instead of  
   * a String, use {@link #fromJson(Reader, Type)} instead.  
   *  
   * @param <T> the type of the desired object  
   * @param json the string from which the object is to be deserialized  
   * @param typeOfT The specific genericized type of src. You can obtain this type by using the  
   * {@link com.google.gson.reflect.TypeToken} class. For example, to get the type for  
   * {@code Collection<Foo>}, you should use:  
   * <pre>  
   * Type typeOfT = new TypeToken&lt;Collection&lt;Foo&gt;&gt;(){}.getType();  
   * </pre>  
   * @return an object of type T from the string. Returns {@code null} if {@code json} is {@code null}.  
   * @throws JsonParseException if json is not a valid representation for an object of type typeOfT  
   * @throws JsonSyntaxException if json is not a valid representation for an object of type  
   */  
  @SuppressWarnings("unchecked")  
  public <T> T fromJson(String json, Type typeOfT) throws JsonSyntaxException {  
   if (json == null) {  
    return null;  
   }  
   StringReader reader = new StringReader(json);  
   T target = (T) fromJson(reader, typeOfT);  
   return target;  
  }  
```

*Found on
[GSON.java](https://github.com/google/gson/blob/master/gson/src/main/java/com/google/gson/Gson.java).*\
*\
\...* No, I don\'t understand it either, even with the Javadoc comments
included! :)\
\
If you are unfamiliar with Javadocs, the short answer is that these
comments create [this
page](https://google-gson.googlecode.com/svn/trunk/gson/docs/javadocs/com/google/gson/Gson.html#fromJson(java.lang.String,%20java.lang.Class)).\
\
Coming from a QA Engineer background, I know that there are times when
things are best left as a black box, containing a great unknown.\
\
And that concludes our series! Hope you had as much fun as I had! :)\
\
Happy testing!\
\
\

::: {#toc-section .toc-section}
**RESTful Testing with Stripe:**\

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

::: {style="background-color: white; color: #222222; font-family: Calibri; font-size: 15.4px; line-height: 21.56px;"}
[-T.J.
Maher]{style="font-family: "calibri"; font-size: 15.4px; line-height: 21.56px;"}\

::: {style="font-size: 15.4px; line-height: 21.56px;"}
\* Sr. QA Engineer, Fitbit*\
* Boston, MA*
:::

::: {style="font-size: 15.4px; line-height: 21.56px;"}
*\
*
:::

::: {style="font-size: 15.4px; line-height: 21.56px;"}
*// Automated tester for \[ 11 \] month and counting!*\
*\
Please note: \'Adventures in Automation\' is a personal blog about
automated testing. It is not an official blog
of [Fitbit.com](http://www.fitbit.com/). *
:::

<div>

*\
*

</div>
:::

\
\
\
\
\
