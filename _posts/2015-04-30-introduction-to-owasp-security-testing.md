\-\-- layout: post title: \'Introduction to OWASP: A Security Testing
Resource\' date: \'2015-04-30T12:39:00.002-04:00\' author: T.J. Maher
tags: - security - Meetup modified\_time:
\'2016-04-29T20:02:39.058-04:00\' blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-6306826068454738604
blogger\_orig\_url:
http://www.tjmaher.com/2015/04/introduction-to-owasp-security-testing.html
\-\-- *[A subset of slides created in order to illustrate a ten minute
tech talk given by me at Fitbit - Boston on security testing resources
that the Open Web Application Security Project
offers.]{style="font-family: inherit;"}*\
[]{style="font-family: inherit;"}\
[]{#more}[\
]{style="font-family: inherit;"}\

::: {style="text-align: center;"}
\
[\
]{style="font-family: inherit;"}\

::: {style="text-align: left;"}
[\
]{style="font-family: inherit;"}
:::

### [What does OWASP Stand for?]{style="font-family: inherit;"} {#what-does-owasp-stand-for style="text-align: left;"}

::: {style="text-align: left;"}
[\
]{style="font-family: inherit;"}
:::

::: {style="text-align: left;"}
[OWASP stands for Open Web Application Security Project.
<https://www.owasp.org/> ]{style="font-family: inherit;"}
:::

::: {style="text-align: left;"}
[\
]{style="font-family: inherit;"}
:::

### [What is your experience with OWASP? ]{style="font-family: inherit;"} {#what-is-your-experience-with-owasp style="text-align: left;"}

::: {style="text-align: left;"}
[\
]{style="font-family: inherit;"}
:::

::: {style="text-align: left;"}
[I worked as part of a security testing team at Intralinks back in 2011
to 2012. The QA Manager at the time wanted to try to integrate security
into the manual tests we had. ]{style="font-family: inherit;"}\
[\
The in-house security consultant would review testing guides with us,
either once a week or every other week breaking off tests we could do in
bite sized chunks each week. I'd capture the meeting notes, sketch out
and perform the basic tests, and put the information their confluence
page.     ]{style="font-family: inherit;"}
:::

### [ ]{style="font-family: inherit;"} {#section style="text-align: left;"}

### [What is OWASP? ]{style="font-family: inherit;"} {#what-is-owasp style="text-align: left;"}

::: {style="text-align: left;"}
[The Open Web Application Security Project (OWASP) is a not-for profit
started in the United States but now is an international organization.
Their tools, documents, forums, and chapters are free and open to anyone
with an interest in improving their application
security.]{style="font-family: inherit;"}
:::

::: {style="text-align: left;"}
[\
]{style="font-family: inherit;"}
:::

### [What does OWASP do?]{style="font-family: inherit;"} {#what-does-owasp-do style="text-align: left;"}

::: {style="text-align: left;"}
[\
]{style="font-family: inherit;"}
:::

::: {style="text-align: left;"}
[The two main documents they produce every few years are a [Testing
Guide](https://www.owasp.org/index.php/OWASP_Testing_Guide_v4_Table_of_Contents)
and the OWASP [Top Ten
Vulnerabilities](https://www.owasp.org/index.php/Category:OWASP_Top_Ten_Project).
Both are made available in either PDF or Wiki
format.]{style="font-family: inherit;"}
:::

::: {style="text-align: left;"}
[\
]{style="font-family: inherit;"}
:::

::: {style="text-align: left;"}
[\... They also have a [developers
guide](https://www.owasp.org/index.php/Category:OWASP_Guide_Project),
that I am unfamiliar with. ]{style="font-family: inherit;"}
:::

::: {style="text-align: left;"}
[\
]{style="font-family: inherit;"}
:::

::: {style="text-align: left;"}
[OWASP also has produced mock web applications you can download from
[GitHub](https://github.com/OWASP) and run locally. They were left
purposely vulnerable so testers could review the web apps, the source
code, and test against it using various security tools. They have a mock
application to test a generic web application, another to test Ruby on
Rails web apps, another to test Node.js applications, among others
 ]{style="font-family: inherit;"}
:::

::: {style="text-align: left;"}
[\
]{style="font-family: inherit;"}
:::

### [What is the OWASP Top Ten? ]{style="font-family: inherit;"} {#what-is-the-owasp-top-ten style="text-align: left;"}

::: {style="text-align: left;"}
[Every few years, OWASP analyzes the [top ten
risks](https://www.owasp.org/index.php/Top_10_2013-Top_10), publishes a
description of these vulnerabilities and how to fix them. The last list
was compiled in 2013. They cover topics such as: SQL Injection, Broken
Authentication, Cross Site Scripting, Insecure Direct Object Readiness,
Security Management, Sensitive Data Exposure. Missing function level
access control. Cross Site Forgery, Using components with known
vulnerabilities, and unvalidated redirects and
forwards. ]{style="font-family: inherit;"}
:::

::: {style="text-align: left;"}
[\
]{style="font-family: inherit;"}
:::

::: {style="text-align: left;"}
[If we go to the link:
<https://www.owasp.org/index.php/Top_10_2013-Top_10> we can see the list
and drill down from the list to see who is at risk, how the attack
happens, and how you can prevent the attack.
  ]{style="font-family: inherit;"}
:::

::: {style="text-align: left;"}
[\
]{style="font-family: inherit;"}
:::

### [Where can you find more detail about each security risk? ]{style="font-family: inherit;"} {#where-can-you-find-more-detail-about-each-security-risk style="text-align: left;"}

::: {style="text-align: left;"}
[\
]{style="font-family: inherit;"}
:::

::: {style="text-align: left;"}
[When you go to the Top Ten Risk page and drill down into a topic such
as **Cross Site Scripting (XSS)**, you are taken to the
<https://www.owasp.org/index.php/Top_10_2013-A3-Cross-Site_Scripting_(XSS)>
Cross site scripting page. ]{style="font-family: inherit;"}
:::

::: {style="text-align: left;"}
[\
]{style="font-family: inherit;"}
:::

::: {style="text-align: left;"}
[Each page has an easy to read color coded grid detailing the threat,
who is at risk, what is the weakness, who it impacts and how it impacts
the business. ]{style="font-family: inherit;"}
:::

::: {style="text-align: left;"}
[\
]{style="font-family: inherit;"}
:::

::: {style="text-align: left;"}
[Sections contained on the page answer questions
like: ]{style="font-family: inherit;"}
:::

::: {style="text-align: left;"}
:::

-   [Am I vulnerable to Cross site scripting? 
    ]{style="font-family: inherit;"}
-   [How do I prevent Cross Site
    Scripting? ]{style="font-family: inherit;"}
-   [Lists example attack scenarios. ]{style="font-family: inherit;"}
-   [List related links.   ]{style="font-family: inherit;"}

### [ ]{style="font-family: inherit;"} {#section-1 style="text-align: left;"}

### [OWASP\'s testing projects]{style="font-family: inherit;"} {#owasps-testing-projects style="text-align: left;"}

[\
]{style="font-family: inherit;"}\

::: {style="text-align: left;"}
[OWASP sponsors test projects such as RailsGoat, a purposely vulnerable
Ruby on Rails web application designed by the people who created the
Living Social web app. ]{style="font-family: inherit;"}\
[\
]{style="font-family: inherit;"}\

::: {style="direction: ltr; margin-bottom: 0pt; margin-left: 0in; margin-top: 0pt; mso-line-break-override: none; punctuation-wrap: hanging; text-align: left; unicode-bidi: embed; word-break: normal;"}
[[OWASP ]{style="color: #2f2b20;"}[RailsGoat]{style="color: #2f2b20;"}[
]{style="color: #2f2b20;"}[test application runs locally from local
computer]{style="color: #2f2b20;"}]{style="font-family: inherit;"}
:::

::: {style="direction: ltr; margin-bottom: 0pt; margin-left: .31in; margin-top: 0pt; mso-line-break-override: none; punctuation-wrap: hanging; text-align: left; text-indent: -.31in; unicode-bidi: embed; word-break: normal;"}
[\
]{style="color: #2f2b20; font-family: inherit;"}
:::

::: {style="direction: ltr; margin-bottom: 0pt; margin-left: .31in; margin-top: 0pt; mso-line-break-override: none; punctuation-wrap: hanging; text-align: left; text-indent: -.31in; unicode-bidi: embed; word-break: normal;"}
[[Official ]{style="color: #2f2b20;"}[page]{style="color: #2f2b20;"}[:
]{style="color: #2f2b20;"}[[https://www.owasp.org/index.php/](https://www.owasp.org/index.php/OWASP_Rails_Goat_Project)]{style="color: #2f2b20;"}[[OWASP\_Rails\_Goat\_Project](https://www.owasp.org/index.php/OWASP_Rails_Goat_Project)]{style="color: #2f2b20;"}]{style="font-family: inherit;"}
:::

::: {style="direction: ltr; margin-bottom: 0pt; margin-left: .31in; margin-top: 0pt; mso-line-break-override: none; punctuation-wrap: hanging; text-align: left; text-indent: -.31in; unicode-bidi: embed; word-break: normal;"}
[[Unofficial page:
]{style="color: #2f2b20;"}[<http://railsgoat.cktricky.com/>]{style="color: #2f2b20;"}[[ ]{style="mso-spacerun: yes;"}]{style="color: #2f2b20;"}]{style="font-family: inherit;"}
:::

::: {style="direction: ltr; margin-bottom: 0pt; margin-left: .31in; margin-top: 0pt; mso-line-break-override: none; punctuation-wrap: hanging; text-align: left; text-indent: -.31in; unicode-bidi: embed; word-break: normal;"}
[[GitHub]{style="color: #2f2b20;"}[:
]{style="color: #2f2b20;"}[[https://github.com/OWASP/](https://github.com/OWASP/railsgoat)]{style="color: #2f2b20;"}[[railsgoat](https://github.com/OWASP/railsgoat)]{style="color: #2f2b20;"}]{style="font-family: inherit;"}
:::
:::

::: {style="text-align: left;"}
[\
]{style="font-family: inherit;"}
:::

::: {style="text-align: left;"}
[ You can use testing tools such as Charles Web Proxy or Burp Proxy to
view, alter and edit the HTTP Get and Post calls, run other security
testing tools against it, and you don't have to worry about damaging a
real site or altering production data. ]{style="font-family: inherit;"}
:::

::: {style="text-align: left;"}
[\
]{style="font-family: inherit;"}
:::

::: {style="text-align: left;"}
[These mock web apps provide real world examples of the OWASP top ten,
such as Injection, Cross site scripting, Broken
Authentication. ]{style="font-family: inherit;"}
:::

::: {style="text-align: left;"}
[\
]{style="font-family: inherit;"}
:::

::: {style="text-align: left;"}
[They give you hints on where to start looking for the
vulnerabilities. You get to discover them
yourself. ]{style="font-family: inherit;"}
:::

::: {style="text-align: left;"}
[\
]{style="font-family: inherit;"}
:::

::: {style="text-align: left;"}
[ Other testing projects other than RailsGoat: WebGoat, iGoat for iPhone
applications, Node JS Goat, WebGoat.Net, GoatDroid. Desktop Goat &
PyGoat is still in the works.   ]{style="font-family: inherit;"}
:::

::: {style="text-align: left;"}
[\
]{style="font-family: inherit;"}
:::

### [Does OWASP meet around Boston?]{style="font-family: inherit;"} {#does-owasp-meet-around-boston style="text-align: left;"}

::: {style="text-align: left;"}
[And, yes, OWASP Boston has a
[Meetup.com](http://www.meetup.com/owaspboston/)
Group! ]{style="font-family: inherit;"}
:::

::: {style="text-align: left;"}
[\
]{style="font-family: inherit;"}
:::

::: {style="text-align: left;"}
[I have never attended any of their meetings before, and I was planning
on crashing it... ]{style="font-family: inherit;"}
:::

::: {style="text-align: left;"}
[\
]{style="font-family: inherit;"}
:::

::: {style="text-align: left;"}
[\... And by crashing ... I mean signing up and RSVPing like a
responsible member of the Meetup
community. ]{style="font-family: inherit;"}
:::

::: {style="text-align: left;"}
[\
]{style="font-family: inherit;"}
:::

::: {style="text-align: left;"}
[Their next Meetup is [Wednesday, May
6th](http://www.meetup.com/owaspboston/events/221696816/), and is being
hosted by Akamai in Kendall Square, only a 2 ½ mile, 40 - 45 minute walk
from Fitbit's office. ]{style="font-family: inherit;"}\
[\
]{style="font-family: inherit;"}[\
]{style="font-family: inherit;"}[\
]{style="font-family: inherit;"}-T.J. Maher\
* Sr. QA Engineer, Fitbit*\
* Boston, MA*\
*\
// Automated tester for \[ 1 \] month and counting!*\
*\
Please note: \'Adventures in Automation\' is a personal blog about
automated testing. It is not an official blog
of [Fitbit.com](http://www.fitbit.com/). *
:::
:::
