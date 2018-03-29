\-\-- layout: post title: \'RESTful Testing with Stripe: Brief
introduction to REST APIs\' date: \'2016-02-16T00:34:00.000-05:00\'
author: T.J. Maher tags: - code examples - Java - Rest API
modified\_time: \'2016-07-24T19:21:20.560-04:00\' blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-7629355498957605598
blogger\_orig\_url:
http://www.tjmaher.com/2016/02/restful-testing-with-stripe-brief.html
\-\--

::: {.tr_bq}
Before launching into a discussion how to test REST APIs such as
Stripe\'s API used to process payments, I wanted to take a step back and
talk about what they are and their early history.\
\
With the RESTful API webservice, software developers allow web apps to
interact with their software products as easily as you and I interact
with a web page.
:::

-   GET Methods: To access **Adventures in Automation**, your browser
    made an HTTP Request to the web server at<http://www.tjmaher.com/>,
    which in turn served you the HTML code that your browser interpreted
    as a web page. 
-   POST Methods: When you enter a message into the Comments textbox at
    the bottom of this page, then hit the \"SHARE\" button, the
    information entered is posted to the web server for processing. 

RESTful APIs are quite common.
[Fitbit](https://dev.fitbit.com/docs/basics/) has one.
[Amazon](https://aws.amazon.com/) has a whole suite of them.  Even
Boston\'s subway system, the [MBTA](http://realtime.mbta.com/portal)
has, one. But where did this idea come from? And what is an API?\

> [\"API (application program interface) is a set of routines,
> protocols, and tools for building software applications. The API
> specifies how software components should interact and APIs are used
> when programming graphical user interface (GUI) components. A good API
> makes it easier to develop a program by providing all the building
> blocks. A programmer then puts the blocks together\".\
> -
> [Webopedia](http://www.webopedia.com/TERM/A/API.html)]{style="font-size: large;"}

\
[]{#more}\
\

### A Quick Overview of SOAP

REST was built to replace what Microsoft had created to interact with
software applications through the web, SOAP, the Simple Object Access
Protocol, 1998. From [SmartBear\'s company API
blog](http://blog.smartbear.com/apis/), [Understanding SOAP and REST
basics](http://blog.smartbear.com/apis/understanding-soap-and-rest-basics/):\
\

> \"SOAP relies exclusively on XML to provide messaging services.
> Microsoft originally developed SOAP to take the place of older
> technologies that don't work well on the Internet such as the
> Distributed Component Object Model (DCOM) and Common Object Request
> Broker Architecture (CORBA). These technologies fail because they rely
> on binary messaging; the XML messaging that SOAP employs works better
> over the Internet.\
> \
> \"After an initial release, Microsoft submitted SOAP to the Internet
> Engineering Task Force (IETF) where it was standardized. SOAP is
> designed to support expansion, so it has all sorts of other acronyms
> and abbreviations associated with it, such as WS-Addressing,
> WS-Policy, WS-Security, WS-Federation, WS-ReliableMessaging,
> WS-Coordination, WS-AtomicTransaction, and WS-RemotePortlets. In fact,
> you can find a whole laundry list of these standards on Web Services
> Standards\".

### The Origin of REST

The idea of REST was introduced when Roy Fielding, one of the founders
of the [The Apache Software Foundation](http://www.apache.org/) and the
principal author of the HTTP specification, published at at University
of California, Irvine his doctoral dissertation  for his Doctor of
Philosophy in Information and Computer Science.\
\
Mr. Fielding, in his paper [Architectural Styles and the Design of
Network-based Software
Architectures](https://www.ics.uci.edu/~fielding/pubs/dissertation/fielding_dissertation.pdf)
*(2000)*, introduces the Representational State Transfer (REST)
architectural style.\
\

\
He describes \"how REST has been used to guide the design and
development of the architecture for the modern Web.\" From the chapter,
[Chapter 6: Experience and
Evaluation](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm):\
\

> [\"REST was originally referred to as the \'HTTP object model,\' but
> that name would often lead to misinterpretation of it as the
> implementation model of an HTTP server. The name \'Representational
> State Transfer\' is intended to evoke an image of how a well-designed
> Web application behaves: a network of web pages (a virtual
> state-machine), where the user progresses through the application by
> selecting links (state transitions), resulting in the next page
> (representing the next state of the application) being transferred to
> the user and rendered for their use\".]{style="font-size: large;"}

Mr. Fielding [described how information is passed to the RESTful
API](https://www.ics.uci.edu/~fielding/pubs/dissertation/evaluation.htm),
through Uniform Resource Identifiers:\
\

> \"Uniform Resource Identifiers (URI) are both the simplest element of
> the Web architecture and the most important. URI have been known by
> many names: WWW addresses, Universal Document Identifiers, Universal
> Resource Identifiers, and finally the combination of Uniform Resource
> Locators (URL) and Names (URN) . Aside from its name, the URI syntax
> has remained relatively unchanged since 1992. However, the
> specification of Web addresses also defines the scope and semantics of
> what we mean by resource, which has changed since the early Web
> architecture. REST was used to define the term resource for the URI
> standard, as well as the overall semantics of the generic interface
> for manipulating resources via their representations\". 

\

### Why Use REST?

Pat Patterson, Principal Developer Evangelist at Salesforce.com, was
interviewed for their blog, [Salesfore APIs - What They Are & When To
Use
Them](https://developer.salesforce.com/blogs/tech-pubs/2011/10/salesforce-apis-what-they-are-when-to-use-them.html)
(Oct 2011), describing why one would pick REST over SOAP:\
\

> \"\[I\]f you just need to make a point-to-point call, in some ways
> SOAP can be overkill. You need an envelope and headers and a whole
> spec that explains how to process these messages. But if you're just
> sending a message from a client to a server and sending back a
> response, you can use something much simpler which is REST \[\...\]

> \"The idea here is that every object in the system is associated with
> a URL. When you perform operations on that URL, you're accessing a
> representation of the state of that object. So if you do a GET on a
> URL representing an account record, you just get back XML or JSON that
> is the state of that account. You can use POST to create a new
> account, DELETE to delete that account. There's a relatively new
> addition to the HTTP methods called PATCH that you can use to update
> that account. What we're doing is passing XML or JSON back and forth
> and leveraging HTTP operations. This makes things much simpler for the
> programmer.\
> \
> \"SOAP messages are all formatted as XML with angle brackets and tags
> and so on. JSON -- which stands for JavaScript Object Notation -- is a
> much more concise data representation than XML. In JSON, the data is
> represented as objects defined in JavaScript. You have property names,
> property values, and you can have nested objects and arrays.\
> \
> \"For example, if you use the REST API to do a query which would be a
> GET on a URL that ends in \'query?q=soql query\' you get back an array
> of records formatted as JSON.\
> \
> \"The nice thing about JSON is that it's a bit more concise and
> lightweight, and there's less data on the wire so it can be a bit
> faster. But from the point of view of the programmer, if you're
> working in JavaScript or Java or PHP or any modern language, there are
> good, high-performance libraries available for parsing JSON. It's very
> easy to work with\".

Now that we have a background of what REST is, we will be taking a
closer look at what it does.\
\
With the next blog entry, we will start looking at how we can
communicate with Stripe\'s  REST API and how it processes payments.\
\
Until then, Happy Testing!\
**NEXT:** [Interacting with Stripe using HTTPS and
cURL](https://www.tjmaher.com/2016/02/restful-testing-with-stripe-interacting.html)\
\

::: {#toc-section .toc-section}
**RESTful Testing with Stripe:**\

-   [Introduction](https://www.tjmaher.com/2016/02/coming-up-how-to-work-with-rest-apis.html)
-   **Part One:** [Intro to REST
    APIs](https://www.tjmaher.com/2016/02/restful-testing-with-stripe-brief.html)
-   **Part Two:** [Interacting with Stripe using HTTPS and
    cURL](https://www.tjmaher.com/2016/02/restful-testing-with-stripe-interacting.html)
-   **Part Three:** [API Keys, Property files, and Initial
    Setup](https://www.tjmaher.com/2016/02/restful-testing-with-stripe-storing-api_23.html)
-   **Part Four:** [UriBuilder, HttpGet and other Apache
    HttpComponents](https://www.tjmaher.com/2016/02/restful-testing-with-stripe-using.html)
-   **Part Five:** [From JSON to Object: HttpEntity and
    GSON](https://www.tjmaher.com/2016/02/restful-testing-with-stripe-from-json.html)
-   **Source Code:** [GitHub, T.J.
    Maher](https://github.com/tjmaher/RESTful_Testing_Using_Stripe)
:::

\
\
[-T.J.
Maher]{style="background-color: white; color: #222222; font-family: "calibri"; font-size: 15.4px; line-height: 21.56px;"}\

<div>

\* Sr. QA Engineer, Fitbit*\
* Boston, MA*\
*\
// Automated tester for \[ 11 \] month and counting!*\
*\
Please note: \'Adventures in Automation\' is a personal blog about
automated testing. It is not an official blog
of [Fitbit.com](http://www.fitbit.com/). *

</div>

\
\
\
\
