\-\-- layout: post title: Notes on Sauce Labs presentation, \"Future
Proof Your Automation\" by QASource date:
\'2017-01-19T08:06:00.000-05:00\' author: T.J. Maher tags:
modified\_time: \'2017-01-19T08:06:58.123-05:00\' thumbnail:
https://2.bp.blogspot.com/-B-Uzuc0dI40/WH-6WoxrADI/AAAAAAAALkk/Brb1aTzXbUM1yVSYz5LqcHt3oqMtPZk2wCLcB/s72-c/Screen%2BShot%2B2017-01-18%2Bat%2B1.55.18%2BPM.png
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-5250123303560679343
blogger\_orig\_url:
http://www.tjmaher.com/2017/01/notes-on-sauce-labs-presentation-future.html
\-\-- **From the Sauce Labs Webinar section:**\
<https://saucelabs.com/resources/webinars/managers-future-proof-your-automation>\
\
\"If you're finding it difficult to automate tests for new features,
and/or a significant number of the bugs your team finds are false
positives, you should consider future-proofing your automation. Join us
for our upcoming webinar, where we\'ll feature presenters from QASource
as they present \'**Managers, Future Proof Your Automation.**\'\
\
\"The webinar will focus on a \'future proof\' automation suite that:\
• \"Has an adaptive framework\
• \"Efficiently automates new features\
• \"Can be easily maintained\
• \"Reduces false positives\
• \"Is long-lasting\
\
\"In this webinar, Rajeev Rai, CEO of QASource, and Rick Rampton, Head
of Client Success at QASource, will share techniques, strategies and
processes that will make your automation future proof\".\
\

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://2.bp.blogspot.com/-B-Uzuc0dI40/WH-6WoxrADI/AAAAAAAALkk/Brb1aTzXbUM1yVSYz5LqcHt3oqMtPZk2wCLcB/s400/Screen%2BShot%2B2017-01-18%2Bat%2B1.55.18%2BPM.png){width="400" height="276"}](https://2.bp.blogspot.com/-B-Uzuc0dI40/WH-6WoxrADI/AAAAAAAALkk/Brb1aTzXbUM1yVSYz5LqcHt3oqMtPZk2wCLcB/s1600/Screen%2BShot%2B2017-01-18%2Bat%2B1.55.18%2BPM.png)
                                                                                                                                   *Presentation given by [QASource](https://www.qasource.com/), an Outsourcing Service for QA*
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 Seven Steps to Future Proof Automation
---------------------------------------

If you wish to future proof your automation, there are seven strategies
you must implement:\
\

-   Automation Scope Review
-   Evaluate Best Suited Tools & Techniques
-   Automation Design Strategy
-   Script Creation Strategy
-   Execution Strategy, Reporting Strategy
-   Maintenance Strategy

\

\

::: {style="margin-bottom: 5px;"}
**[Managers, Future Proof Your
Automation](https://www.slideshare.net/saucelabs/managers-future-proof-your-automation-71158781 "Managers, Future Proof Your Automation")**
from **[Sauce Labs](https://www.slideshare.net/saucelabs)**
:::

\
\

### Automation Scope Review

\
Automation should not be developed to use just once and then sit on a
shelf. It should be used again and again.\
\
Decide:\
\

-   What can and cannot be automated?
-   What should or should not be automated? You cannot automated
    everything.
-   Would it be quicker and more valuable to manually test something?
-   Would this test be run regularly? *Good candidate to automate*. Run
    four times a year? *Not a good candidate*.

\
\

### Evaluate Best Suited Tools & Techniques

\
There needs to be collaboration between DEV and QA to find the best
tool. Pair it with what the developers are using. If automating an
AngularJS front-end, Protractor and JavaScript may be a better tool than
Selenium WebDriver / Java.\
\
Need Mobile applications in the future? Know that Selenium / Java may
not be the best solution since it does not do Mobile.\
\

### Automation Design Strategy

\
You want to decide what you want to use for:\

-   Test Data
-   What type of Global Configs and Test Driver
-   What Page Objects to feed into Test?
-   What is the scheduling?
-   What are the reports going to look like?

\
Note, you want your framework to be:\
\

-   Loosely coupled
-   Customized Actions
-   Global Configurations,
-   Application Independent Utilities
-   Test Data Parameterization: Data independence

\
\
How do you want to identify the web elements you are interacting with?\
\

-   ID? Class? Link? Name? Tag? CSS? Xpath?

\
Also:\
\

-   What is the framework development process?
-   What is your strategy for writing the framework?
-   Building an automation framework is building a software project: How
    to code commit, how to do code reviews, how to develop the
    framework?

\
Create a living document showing your framework development process.\
\

### Script Creation Strategy

\
Remember: A Record and playback is never enough.\

-   Script Mapping strategy.
-   Script Pattern Strategy
-   Script Commenting Strategy
-   Independent tests
-   Unique Test Data
-   Exception Handling
-   Controlled States
-   Tear Down
-   Soft and Hard Assertions

### Execution Strategy

-   You need to take a test suite, break it up into different groups,
    and run these groups of tests in Parallel.
-   You also need a way to re-execute any errors.

\
\
\... What are you capturing in Reports?\
\

### Reporting Strategy

\
Reporting is very important. What type of reporting works in your
organization? Who needs to be informed? How do you frame the report to
answer questions about what is happening with the testing? Are they
looking for a Dashboard, to Drill down as results, to have Analysis?
Should the results be emailable?\
\

::: {.separator style="clear: both; text-align: center;"}
[![](https://3.bp.blogspot.com/-cEFNOZA4Ujg/WH_UdkoaWjI/AAAAAAAALk0/1BEZ8YWmI2wHTazd9gKiKqxKcvEy6-MMQCLcB/s640/Screen%2BShot%2B2017-01-18%2Bat%2B2.37.15%2BPM.png){width="640"
height="444"}](https://3.bp.blogspot.com/-cEFNOZA4Ujg/WH_UdkoaWjI/AAAAAAAALk0/1BEZ8YWmI2wHTazd9gKiKqxKcvEy6-MMQCLcB/s1600/Screen%2BShot%2B2017-01-18%2Bat%2B2.37.15%2BPM.png)
:::

\
\
Note: You cannot improve what you cannot measure. You need good
automation strategies, and find good metrics to work with.\
\

::: {.separator style="clear: both; text-align: center;"}
[![](https://4.bp.blogspot.com/-V8xgVgwGh-w/WH_UsbnphsI/AAAAAAAALk4/EwGRkPHUdvYfwFndFawon237J4tOAojhQCLcB/s640/Screen%2BShot%2B2017-01-18%2Bat%2B2.38.33%2BPM.png){width="640"
height="372"}](https://4.bp.blogspot.com/-V8xgVgwGh-w/WH_UsbnphsI/AAAAAAAALk4/EwGRkPHUdvYfwFndFawon237J4tOAojhQCLcB/s1600/Screen%2BShot%2B2017-01-18%2Bat%2B2.38.33%2BPM.png)
:::

\
\

### Maintenance Strategy

\
How can you maintain your scripts? How do you deal with flaky tests? How
do you know it is not a flaky test, but is instead an error that
sporadically keeps on happening?\
\
Flaky tests: Fails inconsistently wasting developers and QA engineer's
time. It damages the reputation for automation.\
\
Don't turn them off, Isolate the flaky tests into a separate group.\
\

### Checklist: Is Your Automation Future Proof?

-   QASource also publishes a free 22 point checklist which talks about
    the techniques and processes you should follow. It is downloadable
    after subscribing to their mailing list
    at <https://info.qasource.com/checklist/is-your-automation-future-proof>

\

### Want more Webinars from QASource?

See <https://www.qasource.com/webinars>\
\

-   Clean Up Your High Maintenance Test Automation Framework
-   Measuring Your Way To Successful Automation Webinar With Experts
-   Reducing False Positives Webinar With QASource's Webinar

**\
QASource: Reducing False Positives in Automated Testing**\

<https://www.youtube.com/watch?v=bi8hDBoZMPY>\
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
