\-\-- layout: post title: \'Security Testing with Kali Linux: Intro and
Installation\' date: \'2015-04-22T17:35:00.003-04:00\' author: T.J.
Maher tags: - code examples - security - setup - Kali Linux
modified\_time: \'2016-04-29T16:22:34.963-04:00\' thumbnail:
https://i.ytimg.com/vi/\_yuU2\_oHrDI/default.jpg blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-6009090276552906693
blogger\_orig\_url:
http://www.tjmaher.com/2015/04/security-testing-with-kali-linux-intro.html
\-\-- [I\'ve always been intrigued by security testing. I was part of a
security testing team at my last position, tinkering with a [security
testing
guide](https://www.owasp.org/index.php/OWASP_Testing_Guide_v3_Table_of_Contents)
written by [The Open Web Application Security Project
(OWASP) ]{style="background-color: white; font-size: 14px; line-height: 22.3999996185303px;"}to
review our web and mobile apps, so when I came across a security testing
group, I had to attend! ]{style="font-family: inherit;"}\
[\
The organizer of the Boston Kali Linux Users Group suggested before the
[Beginners Kali Linux w/
Railsgoat](http://www.meetup.com/Boston-Kali-Linux-Users/events/221286230/)
 event participants should have a running virtual machine with Kali
Linux installed on it. To help us, the organizer Apollo Clark created a
tutorial for both [Mac](https://www.youtube.com/watch?v=_yuU2_oHrDI)
 and [Windows](https://www.youtube.com/watch?v=Ug7cR-4lWGI). It\'s a
good thing, too. I have tinkered with Red Hat Linux, but not for many
years. ]{style="font-family: inherit;"}\
[]{style="font-family: inherit;"}\
[]{#more}[\
]{style="font-family: inherit;"}\

### [What is Kali Linux?]{style="font-family: inherit;"}

*[According to the
[Kali.Org](http://docs.kali.org/introduction/what-is-kali-linux) site: ]{style="font-family: inherit;"}*\

> [\"Kali Linux is a Debian-based Linux distribution aimed at advanced
> Penetration Testing and Security Auditing. Kali contains several
> hundred tools aimed at various information security tasks, such as
>  Penetration Testing, Forensics and Reverse Engineering. Kali Linux is
> developed, funded and maintained by Offensive Security, a leading
> information security training
> company. ]{style="font-family: inherit;"}

> [\
> \"Kali Linux was released on the 13th March, 2013 as a complete,
> top-to-bottom rebuild of BackTrack Linux, adhering completely to
> Debian development standards\". ]{style="font-family: inherit;"}

[\
*According to
[Wikipedia](http://en.wikipedia.org/wiki/Kali_Linux): *]{style="font-family: inherit;"}\
[\
]{style="font-family: inherit;"}\

> [\"Kali Linux \[\...\] is maintained and funded by Offensive Security
> Ltd. It was developed by Mati Aharoni and Devon Kearns of Offensive
> Security through the rewrite of BackTrack, their previous forensics
> Linux distribution. ]{style="font-family: inherit;"}

> [\
> \"Kali Linux is preinstalled with over 600 penetration-testing
> programs, including nmap (a port scanner), Wireshark (a packet
> analyzer), John the Ripper (a password cracker), Aircrack-ng (a
> software suite for penetration-testing wireless LANs), Burp suite and
> OWASP ZAP (both web application security scanners).\[3\]\[4\] Kali
> Linux can run natively when installed on a computer\'s hard disk, can
> be booted from a live CD or live USB, or it can run within a virtual
> machine\".]{style="font-family: inherit;"}

[\
]{style="font-family: inherit;"}\

### [How did Kali Linux come about?]{style="font-family: inherit;"}

[\
*From [Behind the app: The Story of Kali
Linux](http://lifehacker.com/behind-the-app-the-story-of-kali-linux-1666168491):*]{style="font-family: inherit;"}\

> [\"Where did the idea for Kali come from? Were you trying to solve a
> problem you\'d experienced, or did the inspiration come from somewhere
> else?\" ]{style="font-family: inherit;"}

> [\
> **Mati Aharoni:** \"The idea for a Live Linux distribution which
> contains a bunch of security tools was born out of necessity many
> years ago, when I faced a perplexing dilemma on a security engagement.
> I was not allowed to bring any hardware to the engagement---and
> what\'s more, I was only allowed to use onsite computers on the
> condition that I would not touch their hard disks or modify them in
> any way. (I actually was allowed to bring a laptop onsite, however it
> would be taken on exit).\
> \"After thinking long and hard, I figured that these seemingly
> impossible work conditions could be met by adding a few tools to an
> existing bootable Live Linux CD (Knoppix 2.0, to those familiar with
> ancient history). Once created, I would be able to bring in the CD to
> the engagement, boot an onsite computer with the CD, and work directly
> out of RAM. At the end of the engagement, I would be able to destroy
> the CD without too much heart-ache. And so I started a Linux Security
> based Distribution, ten years ago!\"]{style="font-family: inherit;"}

### [What is VirtualBox? ]{style="font-family: inherit;"}

[\
*According to
[Wikipedia](http://en.wikipedia.org/wiki/VirtualBox):*]{style="font-family: inherit;"}\

> [\"VirtualBox was initially offered by Innotek GmbH from Weinstadt,
> Germany under a proprietary software license, making one version of
> the product available at no cost for personal or evaluation use,
> subject to the VirtualBox Personal Use and Evaluation License (PUEL).
> In January 2007, based on counsel by LiSoG, Innotek GmbH released
> VirtualBox Open Source Edition (OSE) as free and open-source software,
> subject to the requirements of the GNU General Public License (GPL),
> version 2. ]{style="font-family: inherit;"}

> [\
> \"Innotek GmbH also contributed to the development of OS/2 and Linux
> support in virtualization\[14\] and OS/2 ports\[15\] of products from
> Connectix which were later acquired by Microsoft. Specifically,
> Innotek developed the "additions" code in both Microsoft Virtual PC
> and Microsoft Virtual Server, which enables various host-guest OS
> interactions like shared clipboards or dynamic viewport
> resizing. ]{style="font-family: inherit;"}

> [\"Sun Microsystems acquired Innotek in February
> 2008. ]{style="font-family: inherit;"}

> [\"Oracle Corporation acquired Sun in January 2010 and re-branded the
> product as \'Oracle VM VirtualBox\'
> \".]{style="font-family: inherit;"}

### [Installation instructions for Kali Linux on a MacBook]{style="font-family: inherit;"}

<div>

[Below is a brief overview of the Mac Installation video Apollo Clark
posted on YouTube. I found the overview to be too fast-paced since I am
more familiar with Windows and Macs than with Unix / Linux, so I have
outlines a few of the steps. ]{style="font-family: inherit;"}

</div>

<div>

[\
]{style="font-family: inherit;"}

</div>

<div>

**[[Step 1: ]{style="font-family: inherit;"}]{.underline}**

</div>

<div>

-   [Download, Install, and Configure Oracle\'s VirtualBox and Extension
    Pack from http://virtualbox.org/wiki/Downloads according to the
    video. ]{style="font-family: inherit;"}

</div>

<div>

[\
]{style="font-family: inherit;"}

</div>

<div>

**[[Step 2: ]{style="font-family: inherit;"}]{.underline}**

</div>

<div>

[\
]{style="font-family: inherit;"}

</div>

<div>

-   [Make sure in the BIOS that you have enabled
    AMD]{style="font-family: inherit;"}

</div>

<div>

[\
]{style="font-family: inherit;"}

</div>

<div>

[**[Step 3:]{.underline}** ]{style="font-family: inherit;"}

</div>

<div>

-   [Download the Kali Linux 64 bit Torrent from
    http://www.kali.org/downloads/ . This is going to take a
    while. ]{style="font-family: inherit;"}

</div>

\

\
[\
**[Step 4: ]{.underline}**]{style="font-family: inherit;"}\
[\
]{style="font-family: inherit;"}\

-   [The tutorial doesn\'t mention that you need to then open up the
    Torrent file in a program such as UTorrent at
    http://www.utorrent.com/ \... when you download uTorrent, watch to
    make sure you aren\'t accidentally agreeing to change your Yahoo
    Search bar or install any extra toolbars you really don\'t
    want. ]{style="font-family: inherit;"}

[\
]{style="font-family: inherit;"}[\
**[Step 5:]{.underline}**  ]{style="font-family: inherit;"}\
[\
]{style="font-family: inherit;"}\

-   [Once you have uTorrent or another Torrent program, you will see the
    directory \"kali-linux-1.1.0-amd64\" that contains the file
    \"kali-linux-1.1.0-amd64.iso\" that will be booted up when the
    virtual machine starts up. By the way, [[PAE/NX stands
    for ]{style="color: black; line-height: normal;"}Physical Address
    Extension (PAE) and NX processor bit
    (NX).]{style="color: #505050; line-height: 20px;"}]{style="font-family: inherit;"}

[\
]{style="font-family: inherit;"}[\
[[**[Step
6: ]{.underline}**]{style="line-height: 20px;"}]{style="color: #505050;"}]{style="font-family: inherit;"}\
[\
]{style="font-family: inherit;"}\

-   [Install Kali Linux on your new Debian virtual machine configuring
    the network, setting the root password and time zone, and
    partitioning the hard drive for the virtual machine. The GRUB
    Bootloader is the program that is based on the old GRand Unified
    Bootloader. ]{style="font-family: inherit;"}

[\
]{style="font-family: inherit;"}[\
**[Step 7: ]{.underline}**]{style="font-family: inherit;"}\
[\
]{style="font-family: inherit;"}\

-   [Reboot the machine, choosing to boot up Kali GNU / Linux, with
    Linux 3.18.0-kali1-amd64 . After logging in as root, you install
    VirtualBox Guest additions for Kali
    Linux. ]{style="font-family: inherit;"}

[\
]{style="font-family: inherit;"}[\
]{style="font-family: inherit;"}[Not familiar with Linux? Here\'s a
brief description of the commands used in this
section: ]{style="font-family: inherit;"}\
[\
**sudo**: Super \"do\": ]{style="font-family: inherit;"}\

> [**sudo**[ allows a permitted user to execute
> a ]{style="background-color: white; color: #333333; line-height: 18px;"}*command*[ as
> the superuser or another user, as specified in
> the ]{style="background-color: white; color: #333333; line-height: 18px;"}*sudoers*[ file.
> The real and effective uid and gid are set to match those of the
> target user as specified in the passwd file (the group vector is also
> initialized when the target user is not root). By
> default, ]{style="background-color: white; color: #333333; line-height: 18px;"}**sudo**[ requires
> that users authenticate themselves with a
> password (*From [Linux.About.com](http://linux.about.com/od/commands/l/blcmdl8_sudo.htm)*)]{style="background-color: white; color: #333333; line-height: 18px;"}]{style="font-family: inherit;"}

[\
**apt-get:**]{style="font-family: inherit;"}\

> [[The ]{style="background-color: white; color: #252525; line-height: 22.3999996185303px;"}**Advanced
> Package Tool**[,
> or ]{style="background-color: white; color: #252525; line-height: 22.3999996185303px;"}**APT**[,
> is
> a ]{style="background-color: white; color: #252525; line-height: 22.3999996185303px;"}[free
> software](http://en.wikipedia.org/wiki/Free_software "Free software")[ ]{style="background-color: white; color: #252525; line-height: 22.3999996185303px;"}[user
> interface](http://en.wikipedia.org/wiki/Front_and_back_ends "Front and back ends")[ that
> works
> with ]{style="background-color: white; color: #252525; line-height: 22.3999996185303px;"}[core
> libraries](http://en.wikipedia.org/wiki/Library_(computing) "Library (computing)")[ to
> handle the installation and removal of software on
> the ]{style="background-color: white; color: #252525; line-height: 22.3999996185303px;"}[Debian](http://en.wikipedia.org/wiki/Debian "Debian")[ ]{style="background-color: white; color: #252525; line-height: 22.3999996185303px;"}[GNU/Linux
> distribution](http://en.wikipedia.org/wiki/GNU/Linux_distribution "GNU/Linux distribution"){.mw-redirect}[ and
> its
> variants.]{style="background-color: white; color: #252525; line-height: 22.3999996185303px;"}^[\[3\]](http://en.wikipedia.org/wiki/Advanced_Packaging_Tool#cite_note-manpage-3)^[ APT
> simplifies the process of managing software
> on ]{style="background-color: white; color: #252525; line-height: 22.3999996185303px;"}[Unix-like](http://en.wikipedia.org/wiki/Unix-like "Unix-like")[ computer
> systems by automating the retrieval, configuration and installation
> of ]{style="background-color: white; color: #252525; line-height: 22.3999996185303px;"}[software
> packages](http://en.wikipedia.org/wiki/Package_(package_management_system) "Package (package management system)")[,
> either from precompiled files or
> by ]{style="background-color: white; color: #252525; line-height: 22.3999996185303px;"}[compiling](http://en.wikipedia.org/wiki/Compiling "Compiling"){.mw-redirect}[ source
> code.
> (*From [Wikipedia](http://en.wikipedia.org/wiki/Advanced_Packaging_Tool)*)]{style="background-color: white; color: #252525; line-height: 22.3999996185303px;"}]{style="font-family: inherit;"}

**[nano:]{style="font-family: inherit;"}**\

> [**nano**[ is
> a ]{style="background-color: white; color: #252525; line-height: 22.3999996185303px;"}[text
> editor](http://en.wikipedia.org/wiki/Text_editor "Text editor")[ for ]{style="background-color: white; color: #252525; line-height: 22.3999996185303px;"}[Unix-like](http://en.wikipedia.org/wiki/Unix-like "Unix-like")[ computing
> systems or operating environments using
> a ]{style="background-color: white; color: #252525; line-height: 22.3999996185303px;"}[command
> line
> interface](http://en.wikipedia.org/wiki/Command_line_interface "Command line interface"){.mw-redirect}[.
> It emulates
> the ]{style="background-color: white; color: #252525; line-height: 22.3999996185303px;"}[Pico](http://en.wikipedia.org/wiki/Pico_(text_editor) "Pico (text editor)")[ text
> editor, part of
> the ]{style="background-color: white; color: #252525; line-height: 22.3999996185303px;"}[Pine](http://en.wikipedia.org/wiki/Pine_(email_client) "Pine (email client)")[ email
> client, and also provides additional
> functionality.]{style="background-color: white; color: #252525; line-height: 22.3999996185303px;"}^[\[1\]](http://en.wikipedia.org/wiki/GNU_nano#cite_note-1)^[ In
> contrast to Pico, nano is licensed under
> the ]{style="background-color: white; color: #252525; line-height: 22.3999996185303px;"}[GNU
> General Public
> License](http://en.wikipedia.org/wiki/GNU_General_Public_License "GNU General Public License")[ (GPL)
> (*From [Wikipedia](http://en.wikipedia.org/wiki/GNU_nano)*) ]{style="background-color: white; color: #252525; line-height: 22.3999996185303px;"}]{style="font-family: inherit;"}

[\... So, sudo nano /etc/apt/sources.list means to open as a super user,
in the text-editor called nano, open
[Sources.List](https://wiki.debian.org/SourcesList). ]{style="font-family: inherit;"}\
[\
**Iceweasel**: A rebranded version of
Firefox:]{style="font-family: inherit;"}\

> [[Mozilla Foundation owns the trademark
> \"Firefox\"]{style="background-color: white; color: #252525; font-size: 14px; line-height: 22.3999996185303px;"}^[\[5\]](http://en.wikipedia.org/wiki/Mozilla_Corporation_software_rebranded_by_the_Debian_project#cite_note-5)^[ and
> claims the right to deny the use of the name and other trademarks to
> unofficial
> builds.]{style="background-color: white; color: #252525; font-size: 14px; line-height: 22.3999996185303px;"}^[\[6\]](http://en.wikipedia.org/wiki/Mozilla_Corporation_software_rebranded_by_the_Debian_project#cite_note-MozillaTrademarkPolicy-6)^[ The ]{style="background-color: white; color: #252525; font-size: 14px; line-height: 22.3999996185303px;"}[Debian
> Free Software
> Guidelines](http://en.wikipedia.org/wiki/Debian_Free_Software_Guidelines "Debian Free Software Guidelines")[ are
> used by the Debian project to determine whether a license is a free
> license, which in turn is used to determine whether something can be
> included in Debian. As the logo did not meet these requirements, it
> could not be used by software which was to be included in Debian. This
> effect of the Mozilla trademark policy led to a long debate within
> the ]{style="background-color: white; color: #252525; font-size: 14px; line-height: 22.3999996185303px;"}[Debian
> Project](http://en.wikipedia.org/wiki/Debian_Project "Debian Project"){.mw-redirect}[ in
> 2004 and 2005. During this debate, the name \"Iceweasel\" was coined
> to refer to rebranded versions of Firefox.
> ([Wikipedia](http://en.wikipedia.org/wiki/Mozilla_Corporation_software_rebranded_by_the_Debian_project))]{style="background-color: white; color: #252525; font-size: 14px; line-height: 22.3999996185303px;"}]{style="font-family: inherit;"}

[\
]{style="font-family: inherit;"}[**[Step
8:]{.underline}** ]{style="font-family: inherit;"}\
[\
]{style="font-family: inherit;"}\

-   [Installing Kernel Headers: Uses the documentation
    at http://pantuts.com/2013/03/14/how-to-install-kernel-headers/]{style="font-family: inherit;"}

[\
**[Step 9: ]{.underline}**]{style="font-family: inherit;"}\
[\
]{style="font-family: inherit;"}\

-   [Get off Guest Additions CD the
    VBoxLinuxAdditions]{style="font-family: inherit;"}
-   [sudo chmod 775
    VBoxLinuxAdditions.run]{style="font-family: inherit;"}

[\
**[Step 10: ]{.underline}**]{style="font-family: inherit;"}\
[\
]{style="font-family: inherit;"}\

-   [In VirtualBox, set up a shared clipboard and shared
    drag-and-drop. ]{style="font-family: inherit;"}

[\
**[Step 11:]{.underline}** ]{style="font-family: inherit;"}\
[\
]{style="font-family: inherit;"}\

-   [Set up a shared folder. ]{style="font-family: inherit;"}

[\
Now, when you start up Kali Linux, you can go to Applications -\> Kali
Linux and see the Top Ten Security Tools, Information Gathering, Stress
Testing, and others. ]{style="font-family: inherit;"}\
[\
**[Step 12: ]{.underline}**]{style="font-family: inherit;"}\
[\
]{style="font-family: inherit;"}\

-   [Take a snapshot with VirtualBox of the system once it is freshly
    installed. ]{style="font-family: inherit;"}

[\
]{style="font-family: "arial" , "helvetica" , sans-serif;"}-T.J. Maher\
* Sr. QA Engineer, Fitbit*\
* Boston, MA*\
*\
// Automated tester for \[ 1 \] month and counting!*\
*\
Please note: \'Adventures in Automation\' is a personal blog about
automated testing. It is not an official blog
of [Fitbit.com](http://www.fitbit.com/). *
