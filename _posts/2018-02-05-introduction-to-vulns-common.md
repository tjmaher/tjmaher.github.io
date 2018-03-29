\-\-- layout: post title: Introduction to Vulns, Common Vulnerabilities
and Exposures, the CVE List, and the National Vulnerability Database
date: \'2018-02-05T23:10:00.000-05:00\' author: T.J. Maher tags: - vulns
- cve - nvd modified\_time: \'2018-02-05T23:10:02.602-05:00\' thumbnail:
https://2.bp.blogspot.com/-fxfqJO6AQvE/WnkO2QacciI/AAAAAAAAMQ8/haaDAfI3h-MIBBp3fVbG6R98MB0CGuTfwCLcBGAs/s72-c/cve\_page.png
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-4169348937524472542
blogger\_orig\_url:
http://www.tjmaher.com/2018/02/introduction-to-vulns-common.html \-\--
Whenever I find a software testing position in a field in which I am
unfamiliar, I try rounding up all resources I can. In my security
testing research, I found a syllabus for Tufts University\'s [**COMP
116: Introduction to Computer
Security**](https://tuftsdev.github.io/DefenseAgainstTheDarkArts/) course
offered Spring of 2018. Just my luck! The instructor for the course
posted the entire syllabus and required reading material online,
including a copy of a wonderful slide deck for a presentation on
an [Introduction to CVE, CWE, and the Top
25](https://tuftsdev.github.io/DefenseAgainstTheDarkArts/readings/schristeycoley-20151029.pdf) given
by Steve Christey Coley, creator of the term, **CVE \-- Common
Vulnerabilities and Exposures**.\
\

What is a Vulnerability?
------------------------

According [to CVE.MITRE.org, in their terminology
section](https://cve.mitre.org/about/terminology.html), \"a
vulnerability is a weakness in the computational logic (e.g., code)
found in software and some hardware components (e.g., firmware) that,
when exploited, results in a negative impact to confidentiality,
integrity, OR availability. Mitigation of the vulnerabilities in this
context typically involves coding changes, but could also include
specification changes or even specification deprecations (e.g., removal
of affected protocols or functionality in their entirety).\
\
\"Examples of vulnerabilities include:\

-   \"phf (remote command execution as user \"nobody\")
-   \"rpc.ttdbserverd (remote command execution as root)
-   \"world-writeable password file (modification of system-critical
    data)
-   \"default password (remote command execution or other access)
-   \"denial of service problems that allow an attacker to cause a Blue
    Screen of Death
-   \"smurf (denial of service by flooding a network)\"

MITRE, a not-for-profit in Bedford, MA, maintains the [Common
Vulnerabilities and Exposures (CVE)](https://cve.mitre.org/cve/)® List.\
\
[]{#more}\
\
By the way? MITRE is not an acronym. James McCormack, who helped draft
the charter wanted \"a name that was meaningless and without
connotations, but with an attractive feel\", according to [MITRE\'s
Media Resources section](https://www.mitre.org/news/media-resources).
\"Some thought the word MITRE was based on the word for joining or
fitting together. Others believed the name came from combining industry
names and keywords. McCormack, however denied all these explanations\".\
\
MITRE operates [federally funded research and development
centers](https://www.mitre.org/centers/we-operate-ffrdcs) for the
federal United States government.\
\

Where Did The CVE List Originate? 
----------------------------------

David E. Mann and Steven M. Christey published a paper back in Jan.
1999, [**Towards a Common Enumeration of
Vulnerabilities**](https://cve.mitre.org/docs/docs-2000/cerias.html),
which can be accessed on MITRE\'s website in HTML format. Originally,
CVE stood for \"Common Vulnerability Enumeration\", but was renamed
**Common Vulnerabilities and Exposures**.\
\

  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://2.bp.blogspot.com/-fxfqJO6AQvE/WnkO2QacciI/AAAAAAAAMQ8/haaDAfI3h-MIBBp3fVbG6R98MB0CGuTfwCLcBGAs/s640/cve_page.png){width="640" height="405"}](https://2.bp.blogspot.com/-fxfqJO6AQvE/WnkO2QacciI/AAAAAAAAMQ8/haaDAfI3h-MIBBp3fVbG6R98MB0CGuTfwCLcBGAs/s1600/cve_page.png)
                                                                                                        *[Read the paper online!](https://cve.mitre.org/docs/docs-2000/cerias.html)*
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

\
\
The MITRE Corporation, an \"independent, not-for profit company working
in the public interest that provides technical support to the
government\" used many different network assessments and Intrusion
Detection Systems (IDS) from different vendors. When MITRE receives
vulnerability information, how do they know that the problem has already
been tracked? Every tool had:\
\

-   Its own naming system for vulnerabilities
-   Its own way of listing the vulnerability
-   Its own assessment tools
-   Its own database storing the vulnerabilities

<div>

It was hard to check to see if you had three different vulnerabilities
or just the same *vuln* in different forms. 

</div>

<div>

\

</div>

<div>

According to a later paper, [**The Development of a Common Enumeration
of Vulnerabilities and
Exposures**](https://cve.mitre.org/docs/docs-2001/Development_of_CVE.html),
published in September 1999, \"CVE development was broadened by creating
a CVE Editorial Board, which includes information security community
representatives from tool vendors, research and educational
organizations, MITRE, and others. The CVE Editorial Board is currently
enumerating a large number of vulnerabilities, while simultaneously
attempting to capture and codify the decision-making process. When a
significant number of vulnerabilities are validated and verified, an
initial version of CVE will be released to the public\".

</div>

<div>

\

</div>

<div>

\... By then, CVE was renamed \"Common Enumeration of Vulnerabilities
and Exposures\". \
\

Why a CVE List? Wouldn\'t It Be a Resource For Hackers?
-------------------------------------------------------

</div>

<div>

According to [The Development of a Common Enumeration of Vulnerabilities
and
Exposures](https://cve.mitre.org/docs/docs-2001/Development_of_CVE.html),
the rewards for listing **publicly** known security vulnerabilities
outweighs the risks.\
\
\"Certainly, any public discussion of vulnerability information may help
a hacker to compromise a system. However, for the following reasons the
benefits of a publicly available CVE would outweigh its risks:\

-   \"CVE is restricted to publicly known vulnerabilities.
-   \"Sharing information is more difficult within the information
    security community than it is for hackers (e.g., commercially funded
    databases have copyright issues precluding their use).
-   \"It takes much more work for an organization to protect its
    networks and eliminate all possible security holes than for a hacker
    to find a single vulnerability, exploit it, and compromise the
    network.
-   \"Community opinion is shifting towards sharing information, as
    reflected in the fact that the CVE Editorial Board includes key
    organizations in the community.

</div>

<div>

\"A widely accepted common enumeration would enhance tool
interoperability, enable effective communication, and create a more
cohesive security posture, thus reducing the overall risk of
compromise\".\
\

What is the CVE List?
---------------------

</div>

<div>

\"CVE® is a dictionary of publicly disclosed cybersecurity
vulnerabilities and exposures that is free to search, use, and
incorporate into products and services, per the [terms of
use](https://cve.mitre.org/about/termsofuse.html).\
\
\"The CVE List is built by [CVE Numbering
Authorities](https://cve.mitre.org/cve/cna.html) (CNAs). Every [CVE
Entry](https://cve.mitre.org/cve/identifiers/index.html) added to the
list is assigned by a CNA.\
\
\"The CVE List feeds the U.S. National Vulnerability Database (NVD) ---
[learn
more](https://cve.mitre.org/about/cve_and_nvd_relationship.html)\".

</div>

<div>

\

</div>

<div>

There are, at the time this blog was written, 96,028 CVE Entries. The
list isn\'t designed like a vulnerability database. As Steve Coley put
it in [Introduction to CVE, CWE, and the Top
25](https://tuftsdev.github.io/DefenseAgainstTheDarkArts/readings/schristeycoley-20151029.pdf),
it is a dictionary, not a database. For example, in [the Search Tips
section of the CVE.MITRE.org
site](https://cve.mitre.org/find/search_tips.html), it mentions:

</div>

<div>

-   Use very specific keywords, such as Sendmail, wu-ftp and other
    application names, not general ones such as \"Unix\" or by operating
    system since the results will be incomplete. 

How is a CVE Added To The CVE List? 
------------------------------------

\"The process of creating a CVE Entry begins with the discovery of a
potential security vulnerability or exposure. The information is then
assigned a CVE ID by a [CVE Numbering
Authority](https://cve.mitre.org/cve/cna.html) (CNA), a
[Description](https://cve.mitre.org/about/faqs.html#cve_entry_descriptions_created)
and
[References](https://cve.mitre.org/about/faqs.html#cve_entry_references)
are added by the CNA, and then the CVE Entry is posted on the CVE
website by the Primary CNA\". - [*CVE List /
Identifiers*](https://cve.mitre.org/cve/identifiers/index.html)\
\
There are many [CNA
participants](https://cve.mitre.org/cve/request_id.html#cna_participants),
such as Adobe, Airbus, Alibaba, Android, Apache, Apple, etc.\
\

What is a CVE ID?
-----------------

\"A CVE ID is the number portion of a [CVE
Entry](https://cve.mitre.org/about/faqs.html#what_is_cve_entry), for
example, \'CVE-1999-0067\', \'CVE-2014-12345\', and
\'CVE-2016-7654321\'.\
\
\"CVE IDs are used by cybersecurity product/service vendors and
researchers as a standard method for [identifying
vulnerabilities](https://cve.mitre.org/about/faqs.html#what_is_cve) and
for
[cross-linking](https://cve.mitre.org/about/faqs.html#what_types_of_products_use_cve)
with other repositories that also use CVE IDs.\
\
\"\[\...\] CVE ID syntax defines the ID number component of a [CVE
Entry](https://cve.mitre.org/cve/identifiers/index.html#defined), for
example, \"CVE-2014-9999999\", which includes the CVE prefix + year +
sequence number digits.\
\
\"With the new syntax, CVE IDs can now have 4 or more digits in the
sequence number portion of the ID. For example, CVE-YYYY-NNNN with 4
digits in the sequence number, CVE-YYYY-NNNNN with 5 digits in the
sequence number, CVE-YYYY-NNNNNNN with 7 digits in the sequence number,
and so on\".\
\
CVEs can be Reserved, Disputed, or Rejected.

</div>

<div>

\

</div>

<div>

Note, there isn\'t any information listed in the CVE List on how to fix
the problem. That is the purpose of the [U.S. National Vulnerability
Database](https://nvd.nist.gov/), which also supplies [vulnerability
metrics and severity scores](https://nvd.nist.gov/vuln-metrics/cvss),
also known as CVSS. 

</div>

<div>

\

</div>

<div>

For an example of how the CVE is listed, take a look at the list on
Twitter of [\@CVEnew](https://twitter.com/CVEnew/), a Twitter feed of
newly reported entries. 

</div>

<div>

\

</div>

<div>

At the time of this blog entr lists **CVE-2018-6654**, which can be
shown on <https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2018-6654>:

</div>

<div>

\

</div>

  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://1.bp.blogspot.com/-Agv81CFwljc/WnkilN6OwrI/AAAAAAAAMRM/EwgyfKEcRzcTrenXbD9mJ2YMJb2PwoIugCLcBGAs/s400/cve_list.png){width="400" height="340"}](https://1.bp.blogspot.com/-Agv81CFwljc/WnkilN6OwrI/AAAAAAAAMRM/EwgyfKEcRzcTrenXbD9mJ2YMJb2PwoIugCLcBGAs/s1600/cve_list.png)
                                                                                                      [*CVE-2018-6654*](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2018-6654)
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

<div>

-   **Description**: \"The Grammarly extension before 2018-02-02 for
    Chrome allows remote attackers to discover authentication tokens via
    an \'action: \"user\"\' request to iframe.gr\_-ifr, because the
    exposure of these tokens is not restricted to any specific web
    site\".
-   **References**: See
    [Bugs.Chromium.Org](https://bugs.chromium.org/p/project-zero/issues/detail?id=1527&desc=2).

\

<div>

More training [is listed on the CVE.MITRE.org
site](https://cve.mitre.org/about/training.html):

</div>

1.  \"[About CVE
    Entries](https://cve.mitre.org/cve/identifiers/index.html) - a
    high-level overview of CVE Entries including creation, states, and
    more.
2.  \"[CVE Entry
    Basics](https://cve.mitre.org/about/faqs.html#cve_entries) - answers
    to basic frequently asked questions about CVE Entries.
3.  \"[CVE List
    Basics](https://cve.mitre.org/about/faqs.html#cve_list_basics) -
    answers to basic frequently asked questions about the CVE List.
4.  \"[Using the CVE
    List](https://cve.mitre.org/about/faqs.html#using_the_cve_list) -
    answers to frequently asked questions about using the CVE List.
5.  \"[CVE List Search
    Tips](https://cve.mitre.org/find/search_tips.html) - tips for
    searching or viewing the CVE List.
6.  \"[Updating Information in CVE
    Entries](https://cve.mitre.org/cve/update_cve_entries.html) -
    instructions for how to request updates to entries on the CVE
    List\".

<div>

\

</div>

What is NVD, the National Vulnerability Database?
-------------------------------------------------

<div>

\
According to [NVD.Nist.Gov](https://nvd.nist.gov/), \"The NVD is the
U.S. government repository of standards based vulnerability management
data represented using the Security Content Automation Protocol (SCAP).
This data enables automation of vulnerability management, security
measurement, and compliance. The NVD includes databases of security
checklist references, security-related software flaws,
misconfigurations, product names, and impact metrics.

</div>

<div>

\
\"\[\...\] The NVD is the CVE dictionary augmented with additional
analysis, a database, and a fine-grained search engine. The NVD is a
superset of CVE. The NVD is synchronized with CVE such that any updates
to CVE appear immediately on the NVD.

</div>

\

How does the NVD assign vulnerability severity scores?
------------------------------------------------------

</div>

<div>

\

</div>

<div>

The NVD uses the Common Vulnerability Scoring System [(CVSS) Version
2](https://www.first.org/cvss/v2/guide), which is is an open standard
for assigning vulnerability impacts that is used by a variety of
organizations. [NISTIR 7946 - CVSS Implementation
Guidance](http://nvlpubs.nist.gov/nistpubs/ir/2014/NIST.IR.7946.pdf)
describes methodologies developed by the NVD for using CVSS, and along
with Appendix B describes the NVD's entire vulnerability assessment
process.\
\

How should I use the CVSS scores provided by the NVD?
-----------------------------------------------------

</div>

<div>

\

</div>

<div>

\"The NVD analysis process provides a Base metric vector and associated
score as calculated using the CVSS Base Equation. Organizations can use
this information, along with additional Temporal and Environmental
vectors and scores, to determine an overall score. This score can then
be used to assist in ranking the severity of vulnerabilities associated
with the organization's computer network, which can help determine
mitigation strategies. For more information on CVSS metrics, vectors,
and scores, please refer to the [CVSSv2 Complete
Documentation](https://www.first.org/cvss/v2/guide)\".

</div>

<div>

\

How can my organization use the NVD data within our own products and services?
------------------------------------------------------------------------------

</div>

<div>

\

</div>

<div>

\"All NVD data is freely available from our XML Data Feeds. There are no
fees, licensing restrictions, or even a requirement to register. All
NIST publications are available in the public domain according to Title
17 of the United States Code. Acknowledgment of the NVD when using our
information is appreciated. In addition, please email <nvd@nist.gov> to
let us know how the information is being used.\
\

How often is the NVD updated?
-----------------------------

</div>

<div>

\

</div>

<div>

\"The NVD is updated whenever a new vulnerability is added to the CVE
dictionary of vulnerabilities. The vulnerabilities are then
[analyzed](http://nvlpubs.nist.gov/nistpubs/ir/2014/NIST.IR.7946.pdf)by
NVD analysts and augmented with vulnerability attributes (e.g.
vulnerable versions) within two-business days excluding [Federal
Holidays](https://www.opm.gov/policy-data-oversight/snow-dismissal-procedures/federal-holidays/)\".

</div>

<div>

\

</div>

<div>

\

</div>

How is the CVSS Scored? 
------------------------

<div>

\"CVSS is owned and managed by FIRST.Org, Inc. (FIRST), a US-based
non-profit organization, whose mission is to help computer security
incident response teams across the world. FIRST reserves the right to
update CVSS and this document periodically at its sole discretion. While
FIRST owns all right and interest in CVSS, it licenses it to the public
freely for use\". - [Common Vulnerability Scoring System
v3.0:Specification
Document](https://www.first.org/cvss/cvss-v30-specification-v1.8.pdf).\
\
\"The Common Vulnerability Scoring System (CVSS) is an open framework
for communicating the characteristics and severity of software
vulnerabilities. CVSS consists of three metric groups: Base, Temporal,
and Environmental. The Base group represents the intrinsic qualities of
a vulnerability, the Temporal group reflects the characteristics of a
vulnerability that change over time, and the Environmental group
represents the characteristics of a vulnerability that are unique to a
user\'s environment. The Base metrics produce a score ranging from 0 to
10, which can then be modified by scoring the Temporal and Environmental
metrics. A CVSS score is also represented as a vector string, a
compressed textual representation of the values used to derive the
score\".\
\
For more information on how the CVSS is scored, read \"A Complete Guide
to the Common Vulnerability Scoring System: Version 2.0\"
at <https://www.first.org/cvss/v2/guide>\
\
\
Happy Testing!

</div>

<div>

\
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
