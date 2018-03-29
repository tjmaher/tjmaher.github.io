\-\-- layout: post title: \'New automation framework released to test
APIs: Introducing Karate, by Intuit India\'\'s Peter Thomas\' date:
\'2017-03-26T20:06:00.000-04:00\' author: T.J. Maher tags: - Rest API
modified\_time: \'2017-03-26T21:34:58.160-04:00\' thumbnail:
https://i.ytimg.com/vi/yKRR1j0A9Q4/default.jpg blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-5879728229394375695
blogger\_orig\_url:
http://www.tjmaher.com/2017/03/new-automation-framework-released-to.html
\-\-- After spending the past month attempting to finish blogging about
the API testing framework, REST Assured, I came across today the
following item that had been retweeted:\
\

> ::: {dir="ltr" lang="en"}
> I\'m super excited to release via
> [\@IntuitIN](https://twitter.com/IntuitIN) a new open-source framework
> for web-service API testing called Karate: <https://t.co/NVudQpTlCn>
> :::
>
> --- Peter Thomas (\@ptrthomas) [February 8,
> 2017](https://twitter.com/ptrthomas/status/829375137132736512)

\
\
According to Peter Thomas\' [LinkedIn
profile](https://www.linkedin.com/in/ptrthomas/), he has been an
architect in Intuit, working for Intuit India (
[\@Intuit.In](https://twitter.com/IntuitIN) ) since 2012 and lives
in the Bengaluru Area, India.\
\
Peter even has Google Doc he posted about on March 20, 2017 comparing
and contrasting [Karate vs REST
Assured](https://docs.google.com/document/d/1ETTrdMVcBXaPjdKY-_67zCWBsi2Ctc5DIQUIfr02H7A/edit).\
\
\*sigh\* Sometimes it is so hard to keep up.\
\
Here is some information from around the web about this new automation
framework. During my next lull in work, I need to tinker with this!\
\

### Karate: Web-Services Testing Made Simple

\
From Peter Thomas\' Medium article, **[Karate: Web-Services Testing Made
Simple](https://medium.com/blueprint-by-intuit/karate-web-services-testing-made-simple-366e8eb5adc0#.nnns6oxtn)**,
posted on BLUEPrint by Intuit\'s Medium.com account:\
\
*\"Intuit has open-sourced 'Karate', a framework that makes the tall
claim that the business of testing web-APIs can actually be --- fun.\
\
\"I know what you must be thinking. There's no way that making HTTP
requests and navigating the forest of data that is returned could be
fun.\
\
\"But really, that's what developers who tried Karate had to say. It
actually didn't surprise us. Because Karate was born out of a strong
dis-satisfaction with the current state of solutions that exist. And a
lot of thought went into Karate to keep it simple and elegant, to allow
the user to focus on the functionality instead of boiler-plate, and to
keep things concise.\
\
\"Karate strives to reduce the entry barrier to writing a test and more
importantly --- reduces the friction to maintain a test, because of how
readable tests become \[ [Read
More](https://medium.com/blueprint-by-intuit/karate-web-services-testing-made-simple-366e8eb5adc0#.nnns6oxtn)
\]\".*\

###  Karate\'s GitHub Site

From <https://github.com/intuit/karate>:\
\
*\"Karate enables you to script a sequence of calls to any kind of
web-service and assert that the responses are as expected. It makes it
really easy to build complex request payloads, traverse data within the
responses, and chain data from responses into the next request.
Karate\'s payload validation engine can perform a \'smart compare\' of
two JSON or XML documents without being affected by white-space or the
order in which data-elements actually appear, and you can opt to ignore
fields that you choose.\
\
\"Since Karate is built on top of
[Cucumber-JVM](https://github.com/cucumber/cucumber-jvm), you can run
tests and generate reports like any standard Java project. But instead
of Java - you write tests in a language designed to make dealing with
HTTP, JSON or XML - **simple**\".*\
\

### Peter\'s Hello World Example

``` {style="background-color: #f6f8fa; border-radius: 3px; box-sizing: border-box; color: #24292e; font-family: SFMono-Regular, Consolas, "Liberation Mono", Menlo, Courier, monospace; font-size: 13.6px; font-stretch: normal; line-height: 1.45; overflow: auto; padding: 16px; word-break: normal; word-wrap: normal;"}
Feature: karate 'hello world' example
Scenario: create and retrieve a cat

Given url 'http://myhost.com/v1/cats'
And request { name: 'Billie' }
When method post
Then status 201
And match response == { id: '#notnull', name: 'Billie' }

Given path response.id
When method get
Then status 200
```

\
On the site, Peter talks about how to get started, variables and
expressions, data types, primary HTTP keywords, tips, and examples such
as data driven tests, and how to use it with \*.feature files.\
\
Over ten demos are on the Karate Demo Page:
<https://github.com/intuit/karate/tree/master/karate-demo>\
\

### Watch Joe Colantonio Talk About \"Karate a Rest Test Tool -- Basic API Testing\"

Joe Colantonio, creator of the [Test Talks](http://www.tjmaher.com/)
podcast, just published on March 23rd an article, [Karate a Rest Test
Tool -- Basic API
Testing](https://www.joecolantonio.com/2017/03/23/rest-test-tool-karate-api-testing/),
which includes a mini tutorial:\
\

[*https://www.youtube.com/watch?v=yKRR1j0A9Q4*](https://www.youtube.com/watch?v=yKRR1j0A9Q4)\
\
You can get more instruction
from <https://www.joecolantonio.com/2017/03/23/rest-test-tool-karate-api-testing/>\
\

### Follow Karate DSL on Twitter!

And, yes, you can follow Karate on Twitter:\

> ::: {dir="ltr" lang="en"}
> [\#KarateDSL](https://twitter.com/hashtag/KarateDSL?src=hash) crosses
> 100 stars on GitHub in just 3 weeks - thanks to all stargazers !
> <https://t.co/wxaDxdtgHh>
> :::
>
> --- Karate DSL (\@KarateDSL) [March 2,
> 2017](https://twitter.com/KarateDSL/status/837160104021618689)

\

### Watch a Webinar from the Creator, Peter Thomas

TechGig published a webinar, \"[Karate: DSL for writing web service API
acceptance tests,
BDD](https://www.techgig.com/webinar/Karate-DSL-for-writing-web-service-API-acceptance-tests-BDD-1042)\":\

<div>

\
\"In this session, Peter will walk through the features of Karate,
demonstrate how it handles manners of HTTP aspects such as file-uploads
and cookies, and also explain how it can be extended via
custom-functions in either JavaScript or Java. Karate\'s innovative
plug-in mechanism for HTTP-header management makes integrating any kind
of authentication and sign-in flow extremely simple. You get to hear
straight \[from\] the creator of 'Karate' the motivations for creating
this framework in the first place, how it differs the competition, and
how it helps accelerate the development and quality-assurance of
web-services of kinds, be it REST, SOAP or GraphQL.\
\
\"Key points of discussion:\

-   \"Why Karate was created, and what problems it solves well.
-   \"Examples and demos of real-life web-service API tests using
    Karate.
-   \"The architecture of Karate and how it combines technologies such
    as Cucumber, JsonPath and Nashorn.
-   \"Insights into what goes into open-sourcing and releasing a public
    Java project\".

\

[*https://vimeo.com/209699865*](https://vimeo.com/209699865)\
\
Happy Testing!\
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
