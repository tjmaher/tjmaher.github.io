\-\-- layout: post title: \'Selenium can be slow: When could we use API
testing? \' date: \'2016-09-09T07:46:00.003-04:00\' author: T.J. Maher
tags: modified\_time: \'2016-09-09T07:46:41.317-04:00\' blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-8486646357436795980
blogger\_orig\_url:
http://www.tjmaher.com/2016/09/selenium-can-be-slow-when-could-we-use.html
\-\-- A Selenium WebDriver test can be slow. Imagine running a test for
a login screen:\
\
\... *waiting, waiting, waiting*\... Surprise, **it\'s a browser!** \...
*waiting, waiting, waiting*\... It\'s a login screen! \... *waiting for
SendKeys to enter the username and password into the proper
textboxes*\... *and for the Login button to be clicked*.\
\
\
[]{#more}\
\
Now, let\'s examine a few tests you can perform on a Login screen:\

-   Enter a valid email address as a username with a correct password,
    and you are taken to the basic landing page. 
-   Enter a username missing an \'@\' or a \".\" and an alert message
    appears: \"Usernames must be an email address\" 
-   Use the email address of someone not registered as a user: \"Either
    the email address or password is invalid. Please try again\". 
-   Use a valid email but an invalid password: \"Either the email
    address or password is invalid. Please try again\". 

<div>

That first bullet point might make a good Selenium WebDriver test. 

</div>

<div>

\

</div>

<div>

The second bullet point might make a good test. 

</div>

<div>

\

</div>

<div>

Every other bullet pointed test might be better suited as a test of the
*webservices* underlying the Login page, i.e. the place you feed the
username and password data to, for processing. 

</div>

<div>

\

</div>

<div>

With the first test, we are checking that we can enter data using the
browser as a user interface. We are checking that we can feed data **to
the webservice**.

</div>

<div>

\

</div>

<div>

With the second test, we are checking that we can get the response from
the webservice, and output it **to the browser**.  

</div>

<div>

\

</div>

<div>

The third and fourth test is essentially a duplication of the second
test, checking that:

</div>

<div>

-   browser input -\> data is fed into webservice -\> webservice has
    output -\> output to browser\'s alert message. 

<div>

Over the past few months, I have experimented with testing at the API
Level:\
\

-   Using [Apache HTTP
    Components](http://www.tjmaher.com/2016/02/coming-up-how-to-work-with-rest-apis.html)
-   Using
    [Postman](http://www.tjmaher.com/2016/07/introduction-to-api-testing-with.html)

<div>

\... Maybe I need to look into [Swagger.io](http://swagger.io/)? 

</div>

</div>

</div>

<div>

\

</div>

\
Happy Testing!\
\
-T.J. Maher\
Sr. QA Engineer\
\
*// Software QA Engineer since 1996.\
// Working with Selenium WebDriver since 2014.\
// Follow Adventures in Automation and Like us on
[Facebook](https://www.facebook.com/AdventuresInAutomation/)!*
