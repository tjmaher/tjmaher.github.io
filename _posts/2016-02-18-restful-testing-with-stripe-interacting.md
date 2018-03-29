\-\-- layout: post title: \'RESTful Testing with Stripe: Interacting
with Stripe using HTTPS and cURL\' date:
\'2016-02-18T15:35:00.001-05:00\' author: T.J. Maher tags: - code
examples - Java - cURL - Rest API modified\_time:
\'2016-04-29T07:37:29.796-04:00\' thumbnail:
https://4.bp.blogspot.com/-Fuw\_2ZSdXp4/VsVEUn1svJI/AAAAAAAAK6w/nlH6FVxeSNQ/s72-c/stripe%2Bdoc.png
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-1816250590752185938
blogger\_orig\_url:
http://www.tjmaher.com/2016/02/restful-testing-with-stripe-interacting.html
\-\-- *This post is second in a series of six. Need to go [back to the
beginning](/2016/02/coming-up-how-to-work-with-rest-apis.html)?*\
\
With our last couple of blog post, we talked about how automation [needs
to be more than simply browser
tests](http://www.tjmaher.com/2016/02/testing-beyond-ui-testing-pyramid.html),
and we covered the [early history of RESTful
APIs](http://www.tjmaher.com/2016/02/restful-testing-with-stripe-brief.html).
Before diving into writing a framework from which we can build automated
API tests, I wanted to go over their basic interactions.\
\
Interacting with a RESTful API such as Stripe\'s is as simple as
interacting with a web page:\

-   GET Methods, such as what automatically happens when you go to a
    website like <http://www.tjmaher.com/> \... Your browser accesses
    the HTML code returned, and interprets it as a web page. You are
    getting information from the endpoint. 
-   POST Methods, such as when you fill out a form on the web or send
    data such as a Comment. You are sending data to the endpoint. 

We will be interacting in a rudimentary way with RESTful API\'s such as
Stripe:\
\

-   To GET, we will be using simple HTTPS calls
-   To POST, we will be using a program called cURL.

\
\
[]{#more}\

### What is Stripe?

::: {style="text-align: left;"}
From **GrowthHackers.com**, \"How Stripe Marketed to Developers So
Effectively\"
:::

*<https://growthhackers.com/growth-studies/how-stripe-marketed-to-developers-so-effectively%C2%A0>*\

> \"In 2007, Y Combinator connected Patrick and John Collison with
> Harjeet and Kulveer Taggar, and the auction-management service startup
> Auctomatic was born. The following year, when Patrick was just 19 and
> John was only 17, Auctomatic was acquired by the Canadian domain name
> business Live Current Media (formerly Communicate.com) for \$5M. As
> part of the acquisition deal, the brothers relocated to Vancouver to
> work for Live Current Media.\
> \
> \"While Patrick was at MIT and John was at Harvard, the brothers began
> working on their next business venture in early 2010---a time when, as
> the company explains, \'On almost every front, it was becoming easier
> to build and launch an online business.\'  One area in which this was
> decidedly not the case was payments, which, as they knew well from
> their previous experience with eBay and other online retailers,
> \'remained dominated by clunky legacy players.\' The legacy players
> were difficult to work with both on the business and development ends.
> From the business side, getting setup and approved as a merchant on
> the platforms was time consuming and dominated by manual processes
> such as paper-based applications, phone audits and more.\
> \
> \"The developer-side was even more cumbersome--the companies lacked
> modern code bases, and things like APIs, client libraries and
> documentation were virtually non-existent. The tools available to
> developers were so limited that the checkout experience for end users
> lacked the intuitive elegance of other core user experience areas.
> Taken together, it was clear to Patrick and John that there was a need
> for a developer-friendly payment company. That was the motivation for
> the company that ultimately became Stripe. The startup was initially
> called /dev/payments and then officially incorporated as
> SLASHDEVSLASHFINANCE after learning that the state of Delaware doesn't
> allow corporate names to have leading slashes. Yet the name resulted
> in innumerable misspellings---such as SLASHDEV/SLASHFINANCE, for
> example---and wasn't as respectable as they would've liked.\
> \
> \"As CTO Greg Brockman explains on Quora, \'Imagine being in talks
> with a very serious banker from a very serious bank and then telling
> them you worked at \"Slash Dev Slash Finance\". It's not a great way
> to build trust.\' \[
> [MORE](https://growthhackers.com/growth-studies/how-stripe-marketed-to-developers-so-effectively%C2%A0)
> \]\"

*\
*\
Take a look at Stripe\'s extensive API documentation
at <https://stripe.com/docs/api#intro>. The documentation for their API
is so well written that I was able to quickly start writing code to
interact with Stripe.\
\

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://4.bp.blogspot.com/-Fuw_2ZSdXp4/VsVEUn1svJI/AAAAAAAAK6w/nlH6FVxeSNQ/s400/stripe%2Bdoc.png){width="400" height="227"}](https://4.bp.blogspot.com/-Fuw_2ZSdXp4/VsVEUn1svJI/AAAAAAAAK6w/nlH6FVxeSNQ/s1600/stripe%2Bdoc.png)
                                                      [*Their great [documentation](https://stripe.com/docs/api#intro) has helped me out of many a jam.*]{style="font-size: small;"}
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Stripe\'s payment processor allows software developers to integrate
their eCommerce shopping cart software directly with their application
via Ruby, Python, PHP, Java, Node, Go, or even through their REST API.\
\

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://4.bp.blogspot.com/-qLijptUx2MI/VsVF0sdx1wI/AAAAAAAAK68/iRRpkrCY070/s400/stripe%2Bgithub.png){width="400" height="237"}](https://4.bp.blogspot.com/-qLijptUx2MI/VsVF0sdx1wI/AAAAAAAAK68/iRRpkrCY070/s1600/stripe%2Bgithub.png)
                                                               *They even have a [GitHub](https://github.com/stripe/stripe-java) site for popular bindings, such as Stripe Java.*
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

The best part is that they have issued a general public use API key, so
developers can tinker with their product before buying it.\
\

### GETting Information From Stripe

\
Getting data, such as the last charge used by your API account key is as
easy as entering a web address into a browser.\
\

-   Stripe\'s API is located at *https://api.stripe.com*. Note the
    HTTPS.
-   The API Version is */v1*
-   To get charges, we add */charges*
-   We add a \'*?*\' after the call to indicate that we will be sending
    parameters in the query
-   Since we are getting the last charge, the first set of parameters
    will be *limit=1*.
-   When sending multiple parameters, we separate them by an ampersand
    \'*&\'*
-   The API Key is **sk\_test\_BQokikJOvBiI2HlWgH4olfQ2. **
-   If we didn\'t care about the security of our system, and didn\'t
    mind people spying on the URL swiping our private Stripe API keys
    and making unauthorized transactions to our payment system, we could
    add as a parameter, *key=sk\_test\_BQokikJOvBiI2HlWgH4olfQ2*. Note,
    we are doing this only because this general purpose keys are widely
    available. Please don\'t do this with your own secure keys you get
    from Stripe. 

Putting it all together, to get the last three charges from Stripe we
can cut-and-paste the following line of text in a browser window:\
\

``` {.hljs .language-bash style="background: rgb(39, 43, 45); border-radius: 5px; border: 0px; color: #d0d0d0; direction: ltr; font-family: 'Source Code Pro', Menlo, monospace; font-size: 13px; line-height: 1.5em; outline: 0px; padding: 20px 40px; tab-size: 4; vertical-align: baseline; white-space: pre-wrap; word-break: normal;"}
https://api.stripe.com/v1/charges?limit=3&key=sk_test_BQokikJOvBiI2HlWgH4olfQ2
```

\

#### Reading a JSON File

The HTTPS call to the Stripe API returns information about the last
charge in a JSON (JavaScript Object) file format.\

The JSON File returned lists that:\
\

-   Customer: Harold Hamburger from 414 Grant Street, Pittsburgh, PA 
-   Charge: ID: ch\_17fwmG2eZvKYlo2CdW87ZPMj
-   He used his VISA ending in 1111 (12/2022 exp) 
-   Amount charged was \$50.01 USD

\

::: {width="50%"}
``` {style="background: rgb(240, 240, 240); border: 1px dashed rgb(204, 204, 204); height: auto; overflow: auto; padding: 0px; text-align: left; width: 50%;"}
 {  
  "object": "list",  
  "data": [  
   {  
    {
      "id": "ch_17fwmG2eZvKYlo2CdW87ZPMj",
      "object": "charge",
      "amount": 5001,
      "amount_refunded": 0,
      "application_fee": null,
      "balance_transaction": "txn_17fwmG2eZvKYlo2CnPB4hZUw",
      "captured": true,
      "created": 1455821124,
      "currency": "usd",
      "customer": null,
      "description": "User: 679. Events: 1070. Total Tickets: 1.",
      "destination": null,
      "dispute": null,
      "failure_code": null,
      "failure_message": null,
      "fraud_details": {},
      "invoice": null,
      "livemode": false,
      "metadata": {
        "user_id": "679",
        "seller_id": "906",
        "events": "PHPUNIT Demo",
        "event_ids": "1070"
      },
      "order": null,
      "paid": true,
      "receipt_email": null,
      "receipt_number": null,
      "refunded": false,
      "refunds": {
        "object": "list",
        "data": [],
        "has_more": false,
        "total_count": 0,
        "url": "/v1/charges/ch_17fwmG2eZvKYlo2CdW87ZPMj/refunds"
      },
      "shipping": null,
      "source": {
        "id": "card_17fwmG2eZvKYlo2C5mWgfWkj",
        "object": "card",
        "address_city": "Pittsburgh",
        "address_country": "US",
        "address_line1": "414 Grant St",
        "address_line1_check": "pass",
        "address_line2": null,
        "address_state": "PA",
        "address_zip": "15219",
        "address_zip_check": "pass",
        "brand": "Visa",
        "country": "US",
        "customer": null,
        "cvc_check": "pass",
        "dynamic_last4": null,
        "exp_month": 12,
        "exp_year": 2022,
        "fingerprint": "tiDP36QdYA6X7km8",
        "funding": "unknown",
        "last4": "1111",
        "metadata": {},
        "name": "Harold Hamburger",
        "tokenization_method": null
      },
      "statement_descriptor": null,
      "status": "succeeded"
    },
  "has_more": true,  
  "url": "/v1/charges"  
 }  
```
:::

\
JSON Syntax Rules are:\

-   Data is in name/value pairs
-   Data is separated by commas
-   Curly braces hold objects
-   Square brackets hold arrays

<div>

*If you want to learn more about JSON, you can take a look at the
W3Schools.com [free online course on
JSON](http://www.w3schools.com/json/). *

</div>

\
Each individual charge\'s parameters are stored in a Charge object, with
each charge given a unique id, prefixed by \"ch\_\". Under \"data\",
Charges are returned in an array of objects, such as:\

-   \[ { ChargeObject1 }, { ChargeObject2 }, { ChargeObject3 } \]

You can find more about the Charge Object and what all the fields mean
at <https://stripe.com/docs/api#charge_object>\

#### Working with Currency 

\
Note that the amount is an integer stored in cents \--  4999 \-- and not
\$49.99.\
\
From **Stripe Support**: [Zero Decimal
Currency](https://support.stripe.com/questions/which-zero-decimal-currencies-does-stripe-support)\

> \"Stripe supports a number of currencies. To create a charge in any of
> these currencies, you need to provide the amount in the smallest
> common currency unit. For most, this is the amount in cents (or pence,
> or similarly named unit). For example, to create a charge for €1.00,
> you would set amount=100 (100 cents).\
> \
> \"For zero-decimal currencies, we use the regular denomination. For
> example, to charge ¥1, you should set amount=1 (1 JPY), since ¥1 is
> the smallest currency unit\".

<div>

From **StackOverflow.com**: [Why Not Use Double Or Float To Represent
Currency](http://stackoverflow.com/questions/3730019/why-not-use-double-or-float-to-represent-currency)\

> \"\[F\]loats and doubles cannot accurately represent the base 10
> multiples we use for money. This issue isn\'t just for Java, it\'s for
> any programming language that uses native floating-point types, as it
> stems from how computers handle floating-point numbers by default
> \[\...\]\
> \
> \"Representing money as a double or float will probably look good at
> first as the software rounds off the tiny errors, but as you perform
> more additions, subtractions, multiplications and divisions on inexact
> numbers, you\'ll lose more and more precision as the errors add up.
> This makes floats and doubles inadequate for dealing with money, where
> perfect accuracy for multiples of base 10 powers is required.\
> \
> \"A solution that works in just about any language is to use integers
> instead, and count cents. For instance, 1025 would be \$10.25. Several
> languages also have built-in types to deal with money. Among others,
> Java has the BigDecimal class \[..\]\" \[ [Read the whole
> answer](http://stackoverflow.com/questions/3730019/why-not-use-double-or-float-to-represent-currency)
> \] 

</div>

\

### POSTing information to Stripe

To compose the POST statement to Stripe\'s API Endpoint, we will be
using cURL.\
\
According to Wikipedia, \"cURL is a computer software project providing
a library and command-line tool for transferring data using various
protocols. The cURL project produces two products, libcurl and cURL. It
was first released in 1997. The name originally stood for \"see URL\".\
\
It was originally written by Daniel Stenberg, who now works as [Sr.
Network Engineer at
Mozilla](https://www.linkedin.com/in/danielstenberg) on the Firefox
browser, and is maintained by Haxx, a team of four developers.\
\

  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://3.bp.blogspot.com/-vr7nV6MF9ig/VsYiB8yRSmI/AAAAAAAAK7U/6EB0qMH1kXM/s400/haxx.png){width="318" height="400"}](https://3.bp.blogspot.com/-vr7nV6MF9ig/VsYiB8yRSmI/AAAAAAAAK7U/6EB0qMH1kXM/s1600/haxx.png)
                                                                  [cURL](https://curl.haxx.se/), brought to you by [Haxx](https://www.haxx.se/who.html)!
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

\
cURL is probably already bundled on your Windows 10 or MacBook. To find
out, open your Console or Command Prompt and type in:\
\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 curl example.com  
```

\
You should then see scroll across your screen the HTML sourcecode for
the http://www.example.com/ webpage.\
\
If you want to play around with cURL and explore further:\

-   The main website is <https://curl.haxx.se/>
-   Their GitHub site is at <https://github.com/curl/curl>

Let\'s say we want to update a charge on Stripe. According to [their
documentation](https://stripe.com/docs/api#update_charge), we need to
create a POST statement, like so:\
\

``` {.language-bash style="background: rgb(39, 43, 45); border-radius: 5px; border: 0px; color: #d0d0d0; direction: ltr; font-family: 'Source Code Pro', Menlo, monospace; font-size: 13px; line-height: 1.5em; outline: 0px; padding: 20px 40px; tab-size: 4; vertical-align: baseline; white-space: pre-wrap; word-break: normal;"}
POST https://api.stripe.com/v1/charges/{CHARGE_ID}
```

\
To do it in cURL, let\'s take their example\...\
\

``` {.hljs .language-bash style="background: rgb(39, 43, 45); border-radius: 5px; border: 0px; color: #d0d0d0; direction: ltr; font-family: 'Source Code Pro', Menlo, monospace; font-size: 13px; line-height: 1.5em; outline: 0px; padding: 20px 40px; tab-size: 4; vertical-align: baseline; white-space: pre-wrap; word-break: normal;"}
curl https://api.stripe.com/v1/charges/ch_17fMZR2eZvKYlo2CB0L7A7LC \
   -u sk_test_BQokikJOvBiI2HlWgH4olfQ2: \
   -d description="Charge for test@example.com"
```

\
\... and let\'s tinker with it. Let\'s switch it up:\

-   Harold Hamburger\'s charge id was ch\_17fwmG2eZvKYlo2CdW87ZPMj.
    Let\'s use that.
-   Let\'s change the description to say, \"Charge for TJMaher.com\". 
-   My MS-DOS CMD line on my Windows machine hates the \"\\\" which
    stands for new lines. Let\'s erase them.
-   My instance of cURL says there is an SSL certificate problem, and to
    get around this, we can enter the switch, \"-k\".

We then get\...\

``` {.hljs .language-bash style="background: rgb(39, 43, 45); border-radius: 5px; border: 0px; color: #d0d0d0; direction: ltr; font-family: 'Source Code Pro', Menlo, monospace; font-size: 13px; line-height: 1.5em; outline: 0px; padding: 20px 40px; tab-size: 4; vertical-align: baseline; white-space: pre-wrap; word-break: normal;"}
curl https://api.stripe.com/v1/charges/ch_17fwmG2eZvKYlo2CdW87ZPMj -u sk_test_BQokikJOvBiI2HlWgH4olfQ2: -d description="Charge for TJMaher.com" -k
```

<!-- -->

<!-- -->

After we cut and paste this into the Command Prompt and run it, we get
back:\
\

::: {.separator style="clear: both; text-align: center;"}
[![](https://3.bp.blogspot.com/-nW5oAuPZHdc/VsYo6BBySNI/AAAAAAAAK7o/1WGZ2UZFVC0/s400/charge.png){width="400"
height="171"}](https://3.bp.blogspot.com/-nW5oAuPZHdc/VsYo6BBySNI/AAAAAAAAK7o/1WGZ2UZFVC0/s1600/charge.png)
:::

\
\... The description has been changed!\
\
\
And that is how you can send information to an API Endpoint!\
\
Happy Testing!\
\
**NEXT:** [API Keys, Property files, and Initial
Setup](/2016/02/restful-testing-with-stripe-storing-api_23.html)

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
