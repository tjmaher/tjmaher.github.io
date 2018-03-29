\-\-- layout: post title: Are You a Gauge Expert? How Do You Graft On a
Fluent Selenium-Ruby Framework? date: \'2018-02-12T22:21:00.002-05:00\'
author: T.J. Maher tags: - bdd - WebDriver - Gauge - Ruby
modified\_time: \'2018-02-24T09:59:26.487-05:00\' blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-7478172122560222414
blogger\_orig\_url:
http://www.tjmaher.com/2018/02/are-you-gauge-expert-how-do-you-graft.html
\-\-- Are you an expert in [Gauge, the BDD
framework](http://www.tjmaher.com/2018/01/a-brief-overview-of-gauge-bdd.html)? (
See a [Brief Overview of
Gauge](http://www.tjmaher.com/2018/01/a-brief-overview-of-gauge-bdd.html)
).\

<div>

\

</div>

<div>

I have a question: How do you work with **selenium-ruby**?\
\
I was planning on working towards what Dave Haeffner has in
[ElementalSelenium.com](http://elementalselenium.com/) creating a
library of:\

-   Using [Base Page
    Objects](http://elementalselenium.com/tips/9-use-a-base-page-object)
    to wrap Selenium Ruby calls with proper waits.
-   Using [Page
    Objects](http://elementalselenium.com/tips/7-use-a-page-object), so
    that when locators inevitably change, I know where exactly to fix
    them.
-   Making the [tests
    data-driven](http://elementalselenium.com/tips/19-data-driven-testing)
-   Adding [Rescue
    exceptions](http://elementalselenium.com/tips/44-exception-handling)
    to avoid weeding through Stack traces.
-   Maybe [JQuery Growl for better
    logging](http://elementalselenium.com/tips/53-growl), and [Wrapped
    Selenium Tests](http://elementalselenium.com/tips/55-wrapper)

I am brand-new to Gauge and using Selenium-Ruby. So far I only have used
Selenium-Java.\
\
It looks like Gauge [strongly advocates against page
objects](https://blog.getgauge.io/are-page-objects-anti-pattern-21b6e337880f)
calling them an Anti-Pattern. Er\... Um\... burying a page\'s locators
in code, as they do in the blog makes me worried. I am looking for other
solutions.\

<div>

[]{#more}To figure out this new automation framework we are using at my
workplace, I ripped off code from Gauge\'s example project,
[ruby-selenium](https://github.com/getgauge-examples/ruby-selenium), and
tried to get it to point to Dave Haeffner\'s site,
[The-Internet](https://the-internet.herokuapp.com/login), so I could
better attempt to understand this BDD framework I am encountering for
the first time.\
\
I created a little project that I
called: [gauge-selenium-ruby-first-draft](https://github.com/tjmaher/gauge-selenium-ruby-first-draft).
([View it on
GitHub!](https://github.com/tjmaher/gauge-selenium-ruby-first-draft)).
It contains:\

#### **env/default:**

-   [default
    properties](https://github.com/tjmaher/gauge-selenium-ruby-first-draft/blob/master/env/default/default.properties):
    Points to where the reports and logs are, chooses Chrome to be the
    default browser, and chooses whether or not you should overwrite
    reports, capture screenshots on failure, enable multithreading. You
    can also choose when you want the objects to be cleatred\... after
    execution of suite, spec, or scenario.
-   [user
    properties](https://github.com/tjmaher/gauge-selenium-ruby-first-draft/blob/master/env/default/user.properties):
    Points to the APP\_URL, and chooses if you want the tests to be
    headless or not.

**specs**\

-   [UserAction.spec](https://github.com/tjmaher/gauge-selenium-ruby-first-draft/blob/master/specs/UserActions.spec):
    Heavily ripped off of the Gauge sample project,
    [ruby-selenium](https://github.com/getgauge-examples/ruby-selenium),
    this is the \"executable specification file. This file follows
    markdown syntax. Every heading in this file denotes a scenario.
    Every bulleted point denotes a step\". Contains \"Login as username
    and \", \"Check if the user is logged in\" and \"Log out\". Also
    contains a data table for username and passwords.
-   [concepts/Authentication.cpt](https://github.com/tjmaher/gauge-selenium-ruby-first-draft/blob/master/specs/concepts/Authentication.cpt):
    Specs can refer to these concepts, \"Check if the user is logged
    in\" and \"Log out\", breaking them down.

**step\_implementations**\

-   [authentication.rb](https://github.com/tjmaher/gauge-selenium-ruby-first-draft/blob/master/step_implementations/authentication.rb):
    Contains the selenium-ruby code that acts out the steps \"Give an
    option to Log Out\", \'Give an option to Log In\' and a logout
    method.
-   [user\_login](https://github.com/tjmaher/gauge-selenium-ruby-first-draft/blob/master/step_implementations/user_login.rb):
    Contains the step \"Login as username and \", which uses
    selenium-ruby to send text to the username and password textbox, and
    presses the Login button.

[](https://github.com/tjmaher/gauge-selenium-ruby-first-draft#specs)[](https://github.com/tjmaher/gauge-selenium-ruby-first-draft#step_implementation_utils)**step\_implementation\_utils**\

-   [driver.rb](https://github.com/tjmaher/gauge-selenium-ruby-first-draft/blob/master/step_implementations/utils/driver.rb):
    Contains the setup and teardown methods, creating the driver and
    quitting the driver. Also sets up the driver with:

</div>

<div>

``` {style="border-radius: 3px; box-sizing: border-box; line-height: 1.45; margin-bottom: 16px; overflow: auto; padding: 16px; word-wrap: normal;"}
options = Selenium::WebDriver::Chrome::Options.new
@@driver = Selenium::WebDriver.for :chrome, options: options
options.add_argument('--headless')
options.add_argument('--disable-gpu')
```

-   [find\_message](https://github.com/tjmaher/gauge-selenium-ruby-first-draft/blob/master/step_implementations/utils/find_messages.rb):
    Any messages that you need to check for? There is this method that
    Gauge\'s ruby-selenium has, \"Show a message \".
-   [screengrabber.rb](https://github.com/tjmaher/gauge-selenium-ruby-first-draft/blob/master/step_implementations/utils/screengrabber.rb):
    Provides a wrapper for
    driver.save\_screenshot(\'/tmp/screenshot.png\')
-   [site\_launcher](https://github.com/tjmaher/gauge-selenium-ruby-first-draft/blob/master/step_implementations/utils/site_launcher.rb):
    Contains the step \"Navigate to the login page\", which then does:

``` {lang="driver.navigate.to" style="background-color: #f6f8fa; border-radius: 3px; box-sizing: border-box; color: #24292e; font-family: SFMono-Regular, Consolas, "Liberation Mono", Menlo, Courier, monospace; font-size: 13.6px; line-height: 1.45; margin-bottom: 16px; overflow: auto; padding: 16px; word-wrap: normal;"}
  assert_equal 'The Internet', driver.title
```

Examine the code I hacked together
at <https://github.com/tjmaher/gauge-selenium-ruby-first-draft>, based
on the ruby-selenium sample project.

</div>

<div>

\

</div>

<div>

Happy Testing!\
-T.J. Maher\
Sr. QA Engineer, Software Engineer in Test\
Meetup Organizer, [Ministry of Testing -
Boston](http://bit.ly/mot_boston)\
\
[Twitter](https://twitter.com/tjmaher1) \|
[YouTube](http://bit.ly/tj_youtube)
\| [LinkedIn](https://www.linkedin.com/in/tjmaher1) \|
[Articles](http://bit.ly/tj_techbeacon)

</div>

</div>
