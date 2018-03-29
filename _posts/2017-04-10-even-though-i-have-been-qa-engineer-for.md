\-\-- layout: post title: \'SeConf2017: Rethinking Appium's Code Base,
Notes\' date: \'2017-04-10T08:48:00.003-04:00\' author: T.J. Maher tags:
- appium modified\_time: \'2017-04-17T08:17:46.623-04:00\' thumbnail:
https://i.ytimg.com/vi/epine\_rT4yE/default.jpg blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-8623961504986488615
blogger\_orig\_url:
http://www.tjmaher.com/2017/04/even-though-i-have-been-qa-engineer-for.html
\-\-- Even though I have been a QA Engineer for quite some time, I am
rather new to automation development. Lately, I\'ve been trying to
figure out [how to use the open-source tool,
Appium](http://www.tjmaher.com/search/label/appium), to automate the
mobile test suites that I have been writing for my current position.\
\
Luckily for me, the Selenium Conference 2017 has just posted [videos of
its lectures
online](http://www.tjmaher.com/2017/04/couldnt-attend-last-weeks-selenium.html),
with many of them providing good background information about Appium.\
**\
Rethinking Appium's Code Base**\

<div>

Moiz Virani -- Software Engineer, Sauce Labs\

\
<https://youtu.be/epine_rT4yE>\
\
Moiz Virani ( \@moizjv ), a Software Engineer at Saucelabs and
contributor on the Appium project talked a bit about how the Appium
project was re-written and restructured. They took a monolithic project
and converted it into smaller microservices.\
\
More that iOS and Android, they now have drivers for Windows and
UIDriver, helping you automate your TV apps. It still uses the [JSON
Wire
protocol](https://confengine.com/selenium-conf-2015/proposal/1319/the-mobile-json-wire-protocol),
still iis open source and always will be open source.\
\
[]{#more}\
\
Originally it was written in Node.js with very hard to read logs,
difficult to read developer documentation. They have rewritten the
[JavaScript](http://www.tjmaher.com/search/label/JavaScript), updating
it to E6 and E7, the current version of JavaScript, limiting the scope
of variables with *let* and *const*.\
\
Prior to 1.5, they had a Client which then talked to a Main Appium
Controller then branched off into either the IOS driver or Android
driver. Then it went into iOS UIAutomation or Android UIAutomator. There
would always be redundant code.\
\
When it came to test organization, there were not many unit tests The
test suites were hard to run, hard to set up, and didn't have good told
to talk about test coverage. If you wanted to run all the tests they
had, it took a whole day.\
\
They wanted in the re-write strong encapsulation, well defined
interfaces, explicit dependencies. One selenium package, two appium
packages, a IOS package, Android packages. Every repo to have a good
README.\
**[\
]{.underline}[How to contribute to the project?]{.underline}**\
\
Appium has a [contribution
page](http://how%20to%20contribute/?%20%20Appium%20has%20a%20contribution%20page.%20There%20is%20sprint%20plannign%20with%20a%20zoom%20channel.%20Report%20bugs.%20appium/appium/blob/master/CONTRIBUTING).
There is sprint planning session with a zoom channel. You can report
bugs. Fix bugs. Be a contributor!\
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
