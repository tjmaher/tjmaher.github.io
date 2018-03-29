\-\-- layout: post title: \'Security Testing Meetup: Beginners Kali
Linux w/ RailsGoat \' date: \'2015-04-23T12:33:00.002-04:00\' author:
T.J. Maher tags: - code examples - security - setup - Kali Linux
modified\_time: \'2016-04-29T16:22:46.447-04:00\' thumbnail:
https://2.bp.blogspot.com/-Accuio0f5LI/VThlIe75DoI/AAAAAAAAKgM/083lerEPcRY/s72-c/Screen%2BShot%2B2015-04-22%2Bat%2B11.18.09%2BPM.png
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-8331544129247291920
blogger\_orig\_url:
http://www.tjmaher.com/2015/04/security-testing-meetup-beginners-kali.html
\-\--

::: {.MsoNormal}
[The Beginners Kali Linux w/ Railsgoat Meetup that I attended Wednesday,
April 22, 2015 had one requirement: Set up Kali Linux running in a
virtual machine.]{style="font-family: inherit;"}
:::

::: {.MsoNormal}
[\
]{style="font-family: inherit;"}
:::

::: {.MsoNormal}
[After tinkering with Kali Linux on-and-off a few days before the
training session, I finally was able to have a [working installation up
and
running](http://adventuresinautomation.blogspot.com/2015/04/security-testing-with-kali-linux-intro.html) in
a virtual machine on my MacBook Pro. It took me a while. Setting up a
Linux distribution is a bit out of my comfort zone, but it was a good
experience. Between listening to the instructional video one of the
organizers, Apollo Clark, had created, and doing a lot of independent
research, I was able to download, install, and set it up using Oracle\'s
VirtualBox. ]{style="color: black; font-family: inherit; font-size: 13.5pt;"}\
[[]{style="color: black; font-family: "arial"; font-size: 13.5pt;"}]{style="font-family: inherit;"}\
[]{#more}[[\
]{style="color: black; font-family: "arial"; font-size: 13.5pt;"}]{style="font-family: inherit;"}\
[Once it is all set up, the desktop looks like
this: ]{style="color: black; font-family: inherit; font-size: 13.5pt;"}\

-   [IceWeasel: Debian Linux\'s version of
    FireFox]{style="font-family: inherit;"}

<!-- -->

-   [Terminal: the Command Line
    Interface. ]{style="font-family: inherit;"}

<!-- -->

-   [[[[NMap]{style="color: blue;"}](http://nmap.org/)]{style="font-family: "times"; font-size: 13.5pt;"}[:
     A free open source Network Mapper that can identify computers on a
    network, and scan for any open
    ports.]{style="font-family: "arial"; font-size: 13.5pt;"}]{style="font-family: inherit;"}

<!-- -->

-   [[[[Metasploit]{style="color: blue;"}](http://www.metasploit.com/)]{style="font-family: "times"; font-size: 13.5pt;"}[:
    a penetration tool used by security testers. Offensive Security, the
    creators of Kali Linux offers a [[free online course about
    Metasploit]{style="color: blue;"}](http://www.offensive-security.com/metasploit-unleashed/Main_Page). ]{style="font-family: "arial"; font-size: 13.5pt;"}]{style="font-family: inherit;"}

<!-- -->

-   [[[[BurpSuite]{style="color: blue;"}](http://portswigger.net/burp/)]{style="font-family: "times"; font-size: 13.5pt;"}[:
     Allows you to inspect and modify traffic between your browser and a
    web or mobile
    application.]{style="font-family: "arial"; font-size: 13.5pt;"}]{style="font-family: inherit;"}

<!-- -->

-   [[[[Wireshark]{style="color: blue;"}](https://www.wireshark.org/)]{style="font-family: "times"; font-size: 13.5pt;"}[:
    A packet sniffer I am only familiar with by
    name. ]{style="font-family: "arial"; font-size: 13.5pt;"}]{style="font-family: inherit;"}

[**Why Kali
Linux?**]{style="color: black; font-family: inherit; font-size: x-small; mso-bidi-font-family: "Times New Roman";"}\

-   [**[Kali Linux is a shared
    platform]{style="font-family: "arial"; font-size: 13.5pt;"}**[. Once
    you have it running in a virtual machine, whether the main computer
    is a Mac, a PC or a Linux box, it is the same
    system. ]{style="font-family: "arial"; font-size: 13.5pt;"}]{style="font-family: inherit;"}

<!-- -->

-   [**[It\'s like a Swiss Army
    knife]{style="font-family: "arial"; font-size: 13.5pt;"}**[. All of
    the security tools are pre-installed, so it provides a good starting
    point. ]{style="font-family: "arial"; font-size: 13.5pt;"}]{style="font-family: inherit;"}

<!-- -->

-   [**[You can put it on a
    thumbdrive]{style="font-family: "arial"; font-size: 13.5pt;"}**[.
    Let\'s say you do not want to add all the security tools to a
    machine that is not your own. You can have a live boot option on a
    USB Flash drive, and boot into Kali
    Linux. ]{style="font-family: "arial"; font-size: 13.5pt;"}]{style="font-family: inherit;"}

<!-- -->

-   [**[It\'s quicker than installing each tool
    individually]{style="font-family: "arial"; font-size: 13.5pt;"}**[.
    As long as it took for me to set it up, it is easier installing one
    huge program than a hundred smaller
    programs. ]{style="font-family: "arial"; font-size: 13.5pt;"}]{style="font-family: inherit;"}

<!-- -->

-   [**[Maintenance becomes someone else\'s
    problem]{style="font-family: "arial"; font-size: 13.5pt;"}**[.
    Offensive Security does the work of bundling and updating the
    system.
     ]{style="font-family: "arial"; font-size: 13.5pt;"}]{style="font-family: inherit;"}

[**[Install
RailsGoat]{style="color: black; font-family: inherit; font-size: 13.5pt;"}**\
For this Meetup, we were testing
against **RailsGoat** ([[http://railsgoat.cktricky.com/]{style="color: blue;"}](http://railsgoat.cktricky.com/)),
a Ruby on Rails application that has been left vulnerable on purpose, so
security testers can practice examining web applications without
actually doing any damage to any actual websites. Once you have Kali
Linux set up, you then can then download and install RailsGoat to your
Kali Linux environment.\
[If this explanation seems a bit \"hand waving\" it is because even
though I have dabbled in testing mobile applications with the Ruby gem
called Calabash-IOS, most of this material was new to
me. ]{style="color: black; font-family: "arial"; font-size: 13.5pt;"}]{style="font-family: inherit;"}\
\
[[\
]{style="color: black; font-family: "arial"; font-size: 13.5pt;"}]{style="font-family: inherit;"}\

::: {.separator style="clear: both; text-align: center;"}
[[![](https://2.bp.blogspot.com/-Accuio0f5LI/VThlIe75DoI/AAAAAAAAKgM/083lerEPcRY/s1600/Screen%2BShot%2B2015-04-22%2Bat%2B11.18.09%2BPM.png){width="400"
height="281"}]{style="font-family: inherit;"}](http://2.bp.blogspot.com/-Accuio0f5LI/VThlIe75DoI/AAAAAAAAKgM/083lerEPcRY/s1600/Screen%2BShot%2B2015-04-22%2Bat%2B11.18.09%2BPM.png)
:::

[\
]{style="color: black; font-family: inherit; font-size: 13.5pt;"}
:::

::: {.MsoNormal}
[[\
]{style="color: black; font-family: "arial"; font-size: 13.5pt;"}]{style="font-family: inherit;"}\
[Note that next to *Applications*, and *Places*, you can see the icons
for a few commonly used
programs.]{style="color: black; font-family: inherit; font-size: 13.5pt;"}\
[\
]{style="font-family: inherit;"}\

<div>

[When you select Applications -\> Kali Linux -\> Top 10 Security Tools
you can see the most commonly used tools by security
testers. ]{style="font-family: inherit;"}

</div>

<div>

[\
]{style="font-family: inherit;"}

</div>

::: {.separator style="clear: both; text-align: center;"}
[[![](https://4.bp.blogspot.com/-lU7HwAbvPpA/VThltX2W2NI/AAAAAAAAKgU/4aFmCcDvT9Y/s1600/Screen%2BShot%2B2015-04-22%2Bat%2B11.18.58%2BPM.png){width="400"
height="287"}]{style="font-family: inherit;"}](http://4.bp.blogspot.com/-lU7HwAbvPpA/VThltX2W2NI/AAAAAAAAKgU/4aFmCcDvT9Y/s1600/Screen%2BShot%2B2015-04-22%2Bat%2B11.18.58%2BPM.png)
:::

<div>

[\
]{style="font-family: inherit;"}

</div>

[\
]{style="font-family: inherit;"}[\
]{style="font-family: inherit;"}[Some of them I used when I was part of
the security testing team at my last
position:]{style="font-family: inherit;"}\

<div>

[\
]{style="font-family: inherit;"}

</div>

[At the Meetup, I asked Apollo and the other organizers: Why not just
download the tools individually, such as your own specific Windows or
Mac version of the
tool? ]{style="color: black; font-family: inherit; font-size: 13.5pt;"}\
[[\
]{style="color: black; font-family: "arial" , "helvetica" , sans-serif; font-size: 13.5pt;"}]{style="font-family: inherit;"}\
[Next, Apollo recommended we install a Ruby on Rails web application
called RailsGoat that beginning security testers can use to practice
their trade. ]{style="font-family: inherit;"}\

<div>

[\
]{style="font-family: inherit;"}

</div>

<div>

::: {.MsoNormal}
[\
]{style="font-family: inherit;"}[\
]{style="font-family: inherit;"}\

::: {.MsoNormal}
[[Instead of going to RailsGoat\'s [[Getting
Started]{style="color: blue;"}](http://railsgoat.cktricky.com/getting_started.html) section
of their website, Apollo wrote a shell script that does this for
us:]{style="color: black; font-family: "arial"; font-size: 13.5pt;"}[]{style="color: black; font-family: "times"; font-size: 13.5pt;"}]{style="font-family: inherit;"}

\
[[\
]{style="color: black; font-family: "arial"; font-size: 13.5pt;"}]{style="font-family: inherit;"}\

::: {.separator style="clear: both; text-align: center;"}
[[![](https://3.bp.blogspot.com/-QdrtyjMlwsU/VThk585OVDI/AAAAAAAAKgE/Zn6u05amsLE/s1600/Screen%2BShot%2B2015-04-22%2Bat%2B10.53.51%2BPM.png){width="400"
height="302"}]{style="font-family: inherit;"}](http://3.bp.blogspot.com/-QdrtyjMlwsU/VThk585OVDI/AAAAAAAAKgE/Zn6u05amsLE/s1600/Screen%2BShot%2B2015-04-22%2Bat%2B10.53.51%2BPM.png)
:::
:::

::: {.MsoNormal}
[\
]{style="font-family: inherit;"}
:::

::: {.MsoNormal}
[[This script goes into the home directory of Kali Linux, uses the Ruby
Version Manager (RVM) to install Ruby version 2.1.5, clone the version
of OWASPs GitHub site, installs
the ]{style="color: black; font-family: "arial"; font-size: 13.5pt;"}[bundle]{style="color: black; font-family: "courier new"; font-size: 13.5pt;"}[ package
(called a \"gem\" in Ruby), installs mySql, sets up the database
with ]{style="color: black; font-family: "arial"; font-size: 13.5pt;"}[rake]{style="color: black; font-family: "courier new"; font-size: 13.5pt;"}[ (a
Ruby version of the Make utility in Unix), starts up the application,
opens up Firefox, and goes to the home directory (127.0.0.1) on port
3000. ]{style="color: black; font-family: "arial"; font-size: 13.5pt;"}]{style="font-family: inherit;"}\
[\
]{style="color: black; font-family: inherit; font-size: 13.5pt;"}[[\
]{style="color: black; font-family: inherit; font-size: 13.5pt;"}[**Steps
to Install RailsGoat using the bash
script: **]{style="color: black; font-family: "arial"; font-size: 13.5pt;"}]{style="font-family: inherit;"}
:::
:::

</div>

<div>

[\
]{style="font-family: inherit;"}

</div>

::: {.MsoNormal}
[**[1) Open the Terminal for Kali
Linux]{style="color: black; font-family: "arial"; font-size: 13.5pt;"}**[]{style="color: black; font-family: "times"; font-size: 13.5pt;"}]{style="font-family: inherit;"}
:::

::: {.MsoNormal}
[\
]{style="font-family: inherit;"}
:::

::: {.MsoNormal}
[[Select the \"\>\_\" icon next to the IceWeasel
icon. ]{style="color: black; font-family: "arial"; font-size: 13.5pt;"}[]{style="color: black; font-family: "times"; font-size: 13.5pt;"}]{style="font-family: inherit;"}
:::

::: {.MsoNormal}
[\
]{style="font-family: inherit;"}
:::

::: {.MsoNormal}
[**[2) Check that Kali Linux has an internet
connection]{style="color: black; font-family: "arial"; font-size: 13.5pt;"}**[]{style="color: black; font-family: "times"; font-size: 13.5pt;"}]{style="font-family: inherit;"}
:::

::: {.MsoNormal}
[\
]{style="font-family: inherit;"}
:::

::: {.MsoNormal}
[[Before we run this script we need to check that we have internet
access. Ideally, it should share the same network connection my MacBook
has. You can open up a new Terminal in Kali Linux by clicking on the
icon marked \"\>\_\" on the top left. In Kali Linux, open a terminal
window and type
in: ]{style="color: black; font-family: "arial"; font-size: 13.5pt;"}[ping
google.com]{style="color: black; font-family: "courier new"; font-size: 13.5pt;"}[ and
made sure that I received an connection connection. Selecting CONTROL-C
will exit out of
Ping.]{style="color: black; font-family: "arial"; font-size: 13.5pt;"}[]{style="color: black; font-family: "times"; font-size: 13.5pt;"}]{style="font-family: inherit;"}
:::

::: {.MsoNormal}
[\
]{style="font-family: inherit;"}
:::

::: {.MsoNormal}
[**[2) Save the installation shell script to the Desktop and run
it]{style="color: black; font-family: "arial"; font-size: 13.5pt;"}**[]{style="color: black; font-family: "times"; font-size: 13.5pt;"}]{style="font-family: inherit;"}
:::

::: {.MsoNormal}
[\
]{style="font-family: inherit;"}
:::

::: {.MsoNormal}
[[In the Terminal type
in ]{style="color: black; font-family: "arial"; font-size: 13.5pt;"}[cd
\~/Desktop]{style="color: black; font-family: "courier new"; font-size: 13.5pt;"}[ to
change the target directory to the Kali Linux
Desktop. ]{style="color: black; font-family: "arial"; font-size: 13.5pt;"}[]{style="color: black; font-family: "times"; font-size: 13.5pt;"}]{style="font-family: inherit;"}
:::

::: {.MsoNormal}
[\
]{style="font-family: inherit;"}
:::

::: {.MsoNormal}
[[Once in the directory for the Desktop, type
in ]{style="color: black; font-family: "arial"; font-size: 13.5pt;"}[wget
http://apolloclark/install\_railsgoat.sh]{style="color: black; font-family: "courier new"; font-size: 13.5pt;"}[ to
get the shell script Apollo wrote and stored on his site, and save it to
the
Desktop. ]{style="color: black; font-family: "arial"; font-size: 13.5pt;"}[]{style="color: black; font-family: "times"; font-size: 13.5pt;"}]{style="font-family: inherit;"}
:::

::: {.MsoNormal}
[\
]{style="font-family: inherit;"}
:::

::: {.MsoNormal}
[[Set the permissions by
entering: ]{style="color: black; font-family: "arial"; font-size: 13.5pt;"}[chmod
777
install\_railsgoat.sh]{style="color: black; font-family: "courier new"; font-size: 13.5pt;"}[]{style="color: black; font-family: "times"; font-size: 13.5pt;"}]{style="font-family: inherit;"}
:::

::: {.MsoNormal}
[[Run the shell
script: ]{style="color: black; font-family: "arial"; font-size: 13.5pt;"}[./install
railsgoat.sh]{style="color: black; font-family: "courier new"; font-size: 13.5pt;"}[]{style="color: black; font-family: "times"; font-size: 13.5pt;"}]{style="font-family: inherit;"}
:::

::: {.MsoNormal}
[\
]{style="font-family: inherit;"}
:::

::: {.MsoNormal}
[[This process will take a good ten or fifteen minutes for everything to
install. ]{style="color: black; font-family: "arial"; font-size: 13.5pt;"}[]{style="color: black; font-family: "times"; font-size: 13.5pt;"}]{style="font-family: inherit;"}
:::

::: {.MsoNormal}
[\
]{style="font-family: inherit;"}
:::

::: {.MsoNormal}
[**[3) Wait for RailsGoat to
open]{style="color: black; font-family: "arial"; font-size: 13.5pt;"}**[]{style="color: black; font-family: "times"; font-size: 13.5pt;"}]{style="font-family: inherit;"}
:::

::: {.MsoNormal}
[\
]{style="font-family: inherit;"}
:::

::: {.MsoNormal}
[Once the installation process is done, a Firefox \-- whoops, I mean
\"IceWeasel\" \-- browser will open displaying the RailsGoat
application.]{style="font-family: inherit;"}\
[\
]{style="font-family: inherit;"}\

::: {.MsoNormal style="mso-margin-bottom-alt: auto; mso-margin-top-alt: auto; mso-outline-level: 3;"}
### **[What information is the most valuable? ]{style="color: black; font-family: inherit; font-size: 13.5pt;"}**
:::

::: {.MsoNormal}
[While waiting for this page to appear, the organizers were talking
about security testing. When it comes to basic security, you need to
create threat
models. ]{style="color: black; font-family: inherit; font-size: 13.5pt;"}\
[[\
]{style="color: black; font-family: "arial"; font-size: 13.5pt;"}[What
data do you need to protect the most? The most valuable data is medical
data. Medical data is worth a good 50 to 60 bucks, it was mentioned,
because it usually provides a person\'s full name, addresses, social
security numbers, and maybe even mother\'s maiden name. Everything
anyone would want to open up new credit accounts. The identities of
people with retirement accounts are valuable. Credit information of
someone with a high credit score is
valuable. ]{style="color: black; font-family: "arial"; font-size: 13.5pt;"}]{style="font-family: inherit;"}\
[[\
]{style="color: black; font-family: "arial"; font-size: 13.5pt;"}[People\'s
accounts and passwords? Not as valuable. Security testers need to know
what threats to protect
against. ]{style="color: black; font-family: "arial"; font-size: 13.5pt;"}[]{style="color: black; font-family: "times"; font-size: 13.5pt;"}]{style="font-family: inherit;"}

\
[\
]{style="color: black; font-family: inherit; font-size: 13.5pt;"}
:::

::: {.MsoNormal style="mso-margin-bottom-alt: auto; mso-margin-top-alt: auto; mso-outline-level: 3;"}
### **[What threats are the most common? ]{style="color: black; font-family: inherit; font-size: 13.5pt;"}**
:::

::: {.MsoNormal}
[\
OWASP, the Open Web Application Security Project is a not-for-profit
organization that focuses on improving the security of software. They
compile a list of the [[OWASP Top
Ten]{style="color: blue;"}](https://www.owasp.org/index.php/Category:OWASP_Top_Ten_Project) every
few years detailing the ten most critical web application security
risks, such as the top ten risks for 2013 in [[PDF format or on a
Wiki]{style="color: blue;"}](https://www.owasp.org/index.php/Category:OWASP_Top_Ten_Project#tab=OWASP_Top_10_for_2013). ]{style="font-family: inherit;"}
:::

[\
Some of them are:]{style="font-family: inherit;"}\

-   [**[SQL
    Injections]{style="font-family: "arial"; font-size: 13.5pt;"}**[ when
    erroneous data is inserted into a
    query.]{style="font-family: "arial"; font-size: 13.5pt;"}]{style="font-family: inherit;"}

<!-- -->

-   [**[Cross-Site
    Scripting ]{style="font-family: "arial"; font-size: 13.5pt;"}**[(XSS)
    where untrusted data can be sent to a web browser without
    validation. ]{style="font-family: "arial"; font-size: 13.5pt;"}]{style="font-family: inherit;"}

<!-- -->

-   [**[Security
    Misconfiguration,]{style="font-family: "arial"; font-size: 13.5pt;"}**[ not
    updating the latest security patches of the
    server. ]{style="font-family: "arial"; font-size: 13.5pt;"}]{style="font-family: inherit;"}

<!-- -->

-   [**[Unvalidated redirects and
    forwards]{style="font-family: "arial"; font-size: 13.5pt;"}**[,
    where victims are taken to phishing or malware
    sites. ]{style="font-family: "arial"; font-size: 13.5pt;"}]{style="font-family: inherit;"}
:::
:::

::: {.MsoNormal}
[\
]{style="font-family: inherit;"}
:::

::: {.MsoNormal}
<div>

[RailsGoat walks the security tester through these various security
risks with internal tutorials a security tester in training can read the
hints and figure out how to test the application using the
exploit. ]{style="font-family: inherit;"}

</div>

<div>

[\
]{style="font-family: inherit;"}

</div>

<div>

[These tutorials can also be accessed on the **RailsGoat** Wiki
at [[https://github.com/OWASP/railsgoat/wiki/tutorials]{style="color: blue;"}](https://github.com/OWASP/railsgoat/wiki/tutorials). ]{style="font-family: inherit;"}

</div>

<div>

[\
]{style="font-family: "arial" , "helvetica" , sans-serif;"}

</div>

<div>

[\
]{style="font-family: "arial" , "helvetica" , sans-serif;"}

</div>

::: {.separator style="clear: both; text-align: center;"}
[![](https://3.bp.blogspot.com/-5nlFTFMP15A/VThqBM5rG6I/AAAAAAAAKgg/c9botYP1po0/s1600/Screen%2BShot%2B2015-04-22%2Bat%2B11.39.51%2BPM.png){width="320"
height="283"}](http://3.bp.blogspot.com/-5nlFTFMP15A/VThqBM5rG6I/AAAAAAAAKgg/c9botYP1po0/s1600/Screen%2BShot%2B2015-04-22%2Bat%2B11.39.51%2BPM.png)
:::

<div>

[\
]{style="font-family: "arial" , "helvetica" , sans-serif;"}

</div>

<div>

\

</div>
:::

::: {.MsoNormal}
[Because this web application is being run locally, you can bang on it
all you want without worrying you will be wrecking someone\'s
site. ]{style="color: black; font-family: inherit; font-size: 13.5pt;"}
:::

::: {.MsoNormal}
[\
]{style="font-family: inherit;"}
:::

::: {.MsoNormal}
[\
]{style="font-family: inherit;"}
:::

::: {.MsoNormal}
**[Sidenote: More RailsGoat
Information: ]{style="color: black; font-family: inherit; font-size: 13.5pt;"}**
:::

::: {.MsoNormal align="center" style="text-align: center;"}
[\
]{style="font-family: "arial" , "helvetica" , sans-serif;"}
:::

\

::: {.MsoNormal}
[\
]{style="font-family: "arial" , "helvetica" , sans-serif;"}
:::

::: {.MsoNormal}
[Ken Johnson (\@cktricky), one of the creators of RailsGoat and former
manager of the LivingSocial application, gave a talk about the program
at the Atlanta Ruby on Rails Users Group back in September
2014.]{style="color: black; font-family: inherit; font-size: 13.5pt;"}\
[[\
]{style="color: black; font-family: "arial"; font-size: 13.5pt;"}]{style="font-family: inherit;"}\

### [Burp Suite Demo ]{style="color: black; font-family: inherit; font-size: 13.5pt;"}

[[\
]{style="color: black; font-family: "arial"; font-size: 13.5pt;"}]{style="font-family: "arial" , "helvetica" , sans-serif;"}\

::: {.separator style="clear: both; text-align: center;"}
[![](https://4.bp.blogspot.com/-VA6JJNk9PFo/VTjVLXxmyPI/AAAAAAAAKgw/hRh1A5rpyTM/s1600/Screen%2BShot%2B2015-04-23%2Bat%2B7.18.32%2BAM.png){width="400"
height="315"}](http://4.bp.blogspot.com/-VA6JJNk9PFo/VTjVLXxmyPI/AAAAAAAAKgw/hRh1A5rpyTM/s1600/Screen%2BShot%2B2015-04-23%2Bat%2B7.18.32%2BAM.png)
:::

[[\
]{style="color: black; font-family: "arial"; font-size: 13.5pt;"}]{style="font-family: "arial" , "helvetica" , sans-serif;"}*[[Official
site of Burp
Suite: ]{style="color: black; font-family: "arial"; font-size: 13.5pt;"}<http://portswigger.net/burp/>]{style="font-family: inherit;"}*\
[\
]{style="font-family: inherit;"}\

-   [[Getting Started with
    BurpSuite]{style="font-family: inherit;"}](https://support.portswigger.net/customer/portal/articles/1783118-getting-started-with-burp-proxy)
-   [[Using
    BurpSuite]{style="font-family: inherit;"}](http://portswigger.net/burp/help/suite_usingburp.html)

[\
]{style="font-family: inherit;"}[[\
]{style="color: black; font-family: "arial"; font-size: 13.5pt;"}[After
RailsGoat was installed on the local machine, Apollo briefly gave the
attendees a demo setting up Burp Suite. He mentioned that 99% of
security testers use this
tool. ]{style="color: black; font-family: "arial"; font-size: 13.5pt;"}It\'s
a proxy server that can be set up to listen to the traffic. You can then
grab and edit the traffic. Other tools out there which do the same thing
are Charles WebProxy and Fiddler.  ]{style="font-family: inherit;"}\
[\
What we are trying to do in security testing is to get the system to
behave in unexpected ways, discovering security
flaws. ]{style="font-family: inherit;"}\
[\
Once we figure out an exploitation with this tool, you can also automate
them on the command line using *bash* and *curl* to run scripts over and
over.]{style="font-family: inherit;"}\
[\
BurpSuite can be accessed in Kali Linux on Applications -\> Kali -\> Top
10 -\> Burpsuite. ]{style="font-family: inherit;"}\
[\
The main problem I had with this Meetup was that I was expecting a
training session, and received a speed
run. ]{style="font-family: inherit;"}\
[\
Apollo raced us through:]{style="font-family: inherit;"}\
[\
]{style="font-family: inherit;"}\

-   [**Setting up Burp Proxy:** Note that RailsGoat is running on
    127.0.0.1 (the HOME address) port 8080. You can change IceWeasel\'s
    network settings for the manula proxy configurations to be 127.0.0.1
    port 8080, removing \"No Proxy\", so Burp will be listening to the
    traffic on your local machine. You can set Burp Proxy to listen in
    and intercept any HTTP calls the web application is sending. Users
    of Burp Proxy can then see all GET, POST. PUT, CREATE or DELETE
    calls. ]{style="font-family: inherit;"}

<!-- -->

-   [**Using RailsGoat**: With RailsGoat you can sign up for a new
    account with a made up email address, such as test\@test.com, see
    what users are on the system, and go to the dashboard.
     ]{style="font-family: inherit;"}

<!-- -->

-   [**Reviewing the HTTP Calls in Burp Proxy**: Using Burp Proxy, you
    can see the */signup*, */users* and */dashboard/home* directories we
    entered. We can also see an encoded password. Using Burp\'s decoder
    we can copy and paste this string and see the exact username and
    password we entered into RailsGoat. If we double-click on the
    username test\@test.com we can make the username blank, submit it,
    and see what we get as a response, and what sign up screen it
    re-directs us too. ]{style="font-family: inherit;"}

<div>

-   [**Performing a rudimentary Cross-Site Scripting example**: If you
    go to the login screen, and enter in, say, the First Name field the
    following piece of JavaScript
    code: \<script\>alert(\"xss\");\</script\> and refresh the page, you
    will see a popup in the web app saying \"XSS\". If you ever get an
    email where someone is pretending to be a bank, providing you with a
    link to go to the bank website to enter your username and password,
    you may be redirected to the actual bank website, but it is
    listening in to what your username and password is. Then, they can
    inject code into the browser to attack the bank\'s site with a valid
    username and password. ]{style="font-family: inherit;"}

</div>

<div>

-   [**Change the user you just created to be an admin:** Let\'s say a
    developer creates a table of the different roles in the database.
    The first account might be an admin account. With RailsGoat, they
    purposely did that, where in the user table, if the \[role\_id\] is
    1, the user will become an admin. If you go to the Profile settings
    in RailsGoat, play around with the settings there, then examine what
    you see in Burp Suite, you can see  the JSON reference
    for user/6.json  and the parameter User\[role\_id\]. In Burp Proxy,
    we can set our test\@test.com account to role\_id to Value: 1. After
    this is done, we see {msg: success}. If we go back to the dashboard
    in RailsGoat, we have a new section that appears: The Admin section.
    We have now changed a regular user to an admin user on
    RailsGoat!]{style="font-family: inherit;"}

### [ ]{style="font-family: inherit;"}

### [Using Curl]{style="font-family: inherit;"}

<div>

[The command \"cURL\" is a recursive acronym of Curl URL Request
Library, like GNU (GNU\'s not Unix) and Nano (Nano\'s ANOther editor).
It\'s Computer Science humor, folks! ]{style="font-family: inherit;"}

</div>

<div>

[\
]{style="font-family: "arial" , "helvetica" , sans-serif;"}

</div>

<div>

[In the Terminal of your MacBook or in Kali Linux, type in:
]{style="font-family: inherit;"}[curl
google.com]{style="font-family: "courier new" , "courier" , monospace;"}[.
]{style="font-family: "arial" , "helvetica" , sans-serif;"}[You
get:]{style="font-family: inherit;"}

</div>

<div>

[\
]{style="font-family: "arial" , "helvetica" , sans-serif;"}

</div>

</div>

\

::: {.p1}
[[\<HTML\>\<HEAD\>\<meta http-equiv=\"content-type\"
content=\"text/html;charset=utf-8\"\>]{style="font-family: "courier new" , "courier" , monospace;"}]{.s1}
:::

<div>

<div>

::: {.p1}
[[\<TITLE\>301
Moved\</TITLE\>\</HEAD\>\<BODY\>]{style="font-family: "courier new" , "courier" , monospace;"}]{.s1}
:::

::: {.p1}
[[\<H1\>301
Moved\</H1\>]{style="font-family: "courier new" , "courier" , monospace;"}]{.s1}
:::

::: {.p1}
[[The document has
moved]{style="font-family: "courier new" , "courier" , monospace;"}]{.s1}
:::

::: {.p1}
[[\<A
HREF=\"http://www.google.com/\"\>here\</A\>.]{style="font-family: "courier new" , "courier" , monospace;"}]{.s1}
:::

::: {.p1}
[[\</BODY\>\</HTML\>]{style="font-family: "courier new" , "courier" , monospace;"}]{.s1}
:::

::: {.p1}
[\
]{.s1}
:::

::: {.p1}
[[This shows that when you tried to get the source code of
\"google.com\", you came across a redirect. If you wanted to get all of
the source code of the Google website, you can type in
]{style="font-family: inherit;"}[curl
www.google.com]{style="font-family: "courier new" , "courier" , monospace;"}[. ]{style="font-family: "arial" , "helvetica" , sans-serif;"}]{.s1}
:::

</div>

<div>

[\
]{style="font-family: "arial" , "helvetica" , sans-serif;"}

</div>

<div>

[Sidenote: ]{style="font-family: inherit;"}

</div>

<div>

-   [**cURL tutorial for emulating a web browser**:
     <http://curl.haxx.se/docs/httpscripting.html>]{style="font-family: inherit;"}
-   [**The cURL
    Manual**: <http://curl.haxx.se/docs/manual.html>]{style="font-family: inherit;"}

</div>

<div>

[\
]{style="font-family: inherit;"}

</div>

<div>

[Apollo mentioned you can use cURL to:]{style="font-family: inherit;"}

</div>

<div>

-   [Grab data from Burp Proxy and place it in a
    file login\_headers.txt and login\_request.txt on his Kali Linux
    Desktop.]{style="font-family: inherit;"}
-   [Alter the file do it only contains the relevant headers such
    as: Host, Accept\_Language, Accept\_Encoding, Context\_Type, x-requested, Referrer, Cookie, Connection, Pragma, Cache\_Control.]{style="font-family: inherit;"}
-   [Change the DOS endline characters that Burp outputted in the text
    file to Unix endline characters by: dos2unix login\_request.txt
    and dos2unix login\_headers.txt. ]{style="font-family: inherit;"}

<div>

[After this was complete, Apollo wrote a complex cURL script and entered
in into the Kali Linux Terminal:]{style="font-family: inherit;"}

</div>

</div>

<div>

[\
]{style="font-family: "arial" , "helvetica" , sans-serif;"}

</div>

<div>

[curl -i -X POST http://127.0.0.1:3000/users/6.json \--data-binary
\@login\_data.txt -v -H \"\$(cat \~/Desktop/login\_headers.txt)\"
\--proxy
127.0.0.1:8080]{style="font-family: "courier new" , "courier" , monospace;"}

</div>

<div>

[\
]{style="font-family: "arial" , "helvetica" , sans-serif;"}

</div>

<div>

[When Apollo executed this cURL script, he was performing exactly what
he did manually:]{style="font-family: inherit;"}

</div>

<div>

-   [It posts to the RailsGoat site]{style="font-family: inherit;"}[
    ([http://127.0.0.1:3000]{style="font-family: "courier new" , "courier" , monospace;"})
    ]{style="font-family: "arial" , "helvetica" , sans-serif;"}[where
    it\'s user data is contained in a JSON file
    ]{style="font-family: inherit;"}[([/users/6.json]{style="font-family: "courier new" , "courier" , monospace;"}).]{style="font-family: "arial" , "helvetica" , sans-serif;"}
-   [It posts the data-binary file
    called]{style="font-family: inherit;"}[
    \"]{style="font-family: "arial" , "helvetica" , sans-serif;"}[login\_data.txt]{style="font-family: "courier new" , "courier" , monospace;"}[\".]{style="font-family: "arial" , "helvetica" , sans-serif;"}
-   [It executes the bash script to execute the Unix command to read
    using cat
    ]{style="font-family: inherit;"}[(]{style="font-family: "arial" , "helvetica" , sans-serif;"}[cat:]{style="font-family: "courier new" , "courier" , monospace;"}[ ]{style="font-family: "arial" , "helvetica" , sans-serif;"}[concatenate)
    the]{style="font-family: inherit;"}[
    ]{style="font-family: "arial" , "helvetica" , sans-serif;"}[login\_headers.txt]{style="font-family: "courier new" , "courier" , monospace;"}[
    ]{style="font-family: "arial" , "helvetica" , sans-serif;"}[file he
    created, connecting through the
    proxy ]{style="font-family: inherit;"}[127.0.0.1:8080.]{style="font-family: "courier new" , "courier" , monospace;"}

</div>

<div>

[With a few text files and this curl script, a security tester can give
the developers working on the products the actual bash code to execute
they can then demo on their Unix
environment. ]{style="font-family: inherit;"}

</div>

### [Other Notes: ]{style="font-family: inherit;"}

<div>

-   [Attendees from Google mentioned that instead of RailsGoat, they use
    a site they created called **Google
    Gruyere**: <https://google-gruyere.appspot.com/> ]{style="font-family: inherit;"}
-   [It was mentioned that there are pentesters that focus on specific
    languages, such as all the ways to test against exploitations in
    Java web apps, or all the exploitations in Ruby web
    apps.]{style="font-family: inherit;"}
-   [Pentesting is actually a small field. If you go to [OWASP
    Boston](https://www.owasp.org/index.php/Boston) group meetings or
    the Boston Application Security Group meetings, you start seeing the
    same people.]{style="font-family: inherit;"}

[\
**What about Certifications? **]{style="font-family: inherit;"}

</div>

<div>

[\
]{style="font-family: inherit;"}

</div>

<div>

[Current knowledge is worth most of all. If you follow the lessons in
RailsGoat or do independent research, it is more worth your while,
according to the organizers of the Meetup. There are certifications such
as:]{style="font-family: inherit;"}

</div>

<div>

[\
]{style="font-family: inherit;"}

</div>

<div>

-   [**CISSP**: Cerified Information Systems Security Professional if
    you want to work with government security this is one of the
    starting
    points: <https://www.isc2.org/cissp/default.aspx%C2%A0>]{style="font-family: inherit;"}
-   [**OSCP**: Offensive Security, creators of Kali Linux, have their
    own certification program. The test is 24 hours in length. It\'s a
    hands on exam where you have to find ways to exploit their test
    site, and also clearly document your work, listing testing
    methodologies. <https://www.offensive-security.com/information-security-certifications/oscp-offensive-security-certified-professional/>]{style="font-family: inherit;"}

</div>

<div>

[The problem with security testing is that there always a new technology
coming out, and applications built in the new technology may have been
pushed out without being adequately tested when it comes with security.
JavaScript, it was mentioned, was originally meant to be executed on the
client side, in a user\'s browser. Now, with node.js, it is operating on
the server side. ]{style="font-family: inherit;"}

</div>

<div>

[\
]{style="font-family: inherit;"}

</div>

<div>

[\... Oh, and why did we install Oracle\'s VirtualBox when VM Mare is a
better way to create virtual machines? VirtualBox is
free. ]{style="font-family: inherit;"}\
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

</div>

</div>
:::
