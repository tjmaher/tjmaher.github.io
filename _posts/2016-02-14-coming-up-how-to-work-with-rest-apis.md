\-\-- layout: post title: \'Coming up: RESTful Testing: How to work with
RESTful API\'\'s using Apache\'\'s HTTPComponents and Java\' date:
\'2016-02-14T13:15:00.000-05:00\' author: T.J. Maher tags: - code
examples - Java - Rest API modified\_time:
\'2016-04-29T07:39:07.560-04:00\' blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-3707102341720929858
blogger\_orig\_url:
http://www.tjmaher.com/2016/02/coming-up-how-to-work-with-rest-apis.html
\-\-- The next series of blog posts will cover my latest project as an
automation developer at Fitbit-Boston: Working with RESTful APIs, such
as the one Stripe uses to process credit card transactions. Stripe
graciously provides the general public a general use key to access their
services. Topics covered:\

-   Walking manual QA Engineers \-- who may have a bit of Java
    programming experience \-- through setting up their development
    environment.
-   Introduction and a brief history of RESTful APIs.
-   Introduction to the Stripe API and walkthrough of their excellent
    documentation.
-   How to interact with Stripe through Apache\'s HTTP Components such
    as HTTP Client, HTTP Post, HTTPGet, and URI Builder and Java.

I covered in my blog about how at work we were having conversations
about [Testing Beyond the UI: The Testing
Pyramid](http://0.0.7.224/02/testing-beyond-ui-testing-pyramid.html).
The work that I am doing is the next step in that process.\
\
Please note: I\'ve only been an automation developer for a bit less than
a year, and I have only been working with HTTP Components for a few
weeks, which makes me this all brand-new to me, too. That is why I am
attempting this project: By forcing myself to explain what I have been
doing, it will deepen my knowledge.\
\
I was wondering, if you are more experienced that I, if you could do a
code review when I am finished? I will be publishing working code on my
GitHub account. Feel free to add any comments or constructive criticism
in the Comments section at the bottom of the page.\
\
These blog posts will be starting this Tuesday, and will be published
every Tuesday and Thursday until the project is complete. Subscribe to
this Blog to get the latest posts via email.\
\
Thank you for stopping by!\
\
Happy Testing!\
\
**NEXT:** [Intro to REST
APIs](/2016/02/restful-testing-with-stripe-brief.html)\

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
*// Automated tester for \[ 11 \] months and counting!*\
*\
Please note: \'Adventures in Automation\' is a personal blog about
automated testing. It is not an official blog
of [Fitbit.com](http://www.fitbit.com/). *
:::
