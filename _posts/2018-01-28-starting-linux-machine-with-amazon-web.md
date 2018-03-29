\-\-- layout: post title: Starting a Linux Machine with Amazon Web
Services Free Tier date: \'2018-01-28T07:00:00.000-05:00\' author: T.J.
Maher tags: - DevOps - aws modified\_time:
\'2018-01-28T08:42:02.977-05:00\' thumbnail:
https://1.bp.blogspot.com/-plEeunJZYeM/Wmy1OY9AFKI/AAAAAAAAMQY/GfjdN3dkAwUt-hQsaPq0urqKB49U30EVwCLcBGAs/s72-c/instance.png
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-6673402858253828116
blogger\_orig\_url:
http://www.tjmaher.com/2018/01/starting-linux-machine-with-amazon-web.html
\-\-- It\'s my first time working at a [cloud-security
company](http://threatstack.com/) using **Amazon Web Services** (AWS)!
How to get up to speed?\
\
To get up to speed, first, I\'ve attempted to decipher the AWS Alphabet
Soup [in an earlier blog
post](http://www.tjmaher.com/2018/01/the-aws-alphabet-soup.html). Next,
to get more exposure to AWS, I signed up for the [AWS Free
Tier](https://aws.amazon.com/free/). I was a bit leery, since I needed
to punch in my credit card information when I signed up.\

-   Some AWS services are free for 12 months, provided I do not go over
    750 hrs per month of usage of EC2, and over 5 GB of Storage in
    Amazon EFS or 30 GB of Elastic Block Storage for long term. If I go
    over, or accidentally use a service that isn\'t on the free tier, I
    worry I am going to rack up a huge charge.
-   [Some services seem to be always
    free.](https://aws.amazon.com/free/#legal) 

Luckily, I didn\'t have to look far in order to find help!\

-   [Getting Started Resource
    Center](https://aws.amazon.com/getting-started): Mentioned in the
    email received upon sign up.
-   [AWS Documentation](https://aws.amazon.com/documentation/) 
-   AWS [10 Minute
    Tutorials](https://aws.amazon.com/getting-started/tutorials/) on
    everything that you could think of!

\

[]{#more} Launch a Linux Virtual Machine
----------------------------------------

\
The first Ten Minute Tutorial I did was [Launch a Linux Virtual Machine
with
EC2](https://aws.amazon.com/getting-started/tutorials/launch-a-virtual-machine/)
(Amazon Elastic Compute Cloud). It covered:\
\
1) Launching an Instance from the Amazon EC2 console\
\
2) Selecting a Free Tier available Amazon Machine Image (AMI) of a Linux
Machine to run, such as:\
\

-   **Amazon Linux AMI 2017.09.1** (HVM), SSD Volume Type: \"The Amazon
    Linux AMI is an EBS-backed, AWS-supported image. The default image
    includes AWS command line tools, Python, Ruby, Perl, and Java. The
    repositories include Docker, PHP, MySQL, PostgreSQL, and other
    packages\".
-   **SUSE Linux Enterprise Server 12 SP3** (HVM), SSD Volume Type:
    \"SUSE Linux Enterprise Server 12 Service Pack 3 (HVM), EBS General
    Purpose (SSD) Volume Type. Public Cloud, Advanced Systems
    Management, Web and Scripting, and Legacy modules enabled\".
-   **Red Hat Enterprise Linux 7.4** (HVM), SSD Volume Type: \"Red Hat
    Enterprise Linux version 7.4 (HVM), EBS General Purpose (SSD) Volume
    Type\"
-   **Ubuntu Server 16.04 LTS (HVM)**, SSD Volume Type: \"Ubuntu Server
    16.04 LTS (HVM),EBS General Purpose (SSD) Volume Type. Support
    available from Canonical (http://www.ubuntu.com/cloud/services)

\
\
I picked the **Amazon Linux AMI**.\
\
3) Choose an Instance Type\
\
Only the General Purpose t2.micro was available on the Free Tier:
(Variable ECUs, 1 vCPUs, 2.5 GHz, Intel Xeon Family, 1 GiB memory, EBS
only).\
\
4) Review and Launch: Sure you could add more storage, tags, and
security groups, but instead, I pressed the shiny \"Review and Launch\"
button.\
\
Next, all we need to do is set up a key pair!\
\

What does ECU, vCPU, GiB, Instance Storage, EBS Optimized and IPv6 mean?
------------------------------------------------------------------------

\
\"**General purpose instances** provide a balance of compute, memory,
and network resources, and are a good choice for many applications. They
are recommended for small and medium databases, data processing tasks
that require additional memory, caching fleets, and for running backend
servers for SAP, Microsoft SharePoint, and other enterprise
applications\"\
\
\"**T2** instances provide a baseline level of CPU performance with the
ability to burst above the baseline.The baseline and ability to burst
are governed by CPU Credits. The t2.micro receives CPU Credits
continuously at a rate of 6 CPU Credits per hour. To learn more about
Amazon EC2 T2 instances, see the [Amazon EC2 details
page](https://aws.amazon.com/ec2/instance-types/)\". Comes in sized
nano, micro, small, medium, large xlarge, 2xlarge.\
\
**vCPU**: \"The number of virtual CPUs for the instance\".\

<div>

\

</div>

<div>

**Memory** is recorded, in **GiB** (Gibibytes, 1073.741824 Megabytes)
\-- not GB (Gigabytes, 1024 Megabytes). 

</div>

<div>

\

</div>

<div>

**Storage** in the AWS Free Tier is offered in **EBS **\-- the [Amazon
Elastic Block Store](https://aws.amazon.com/ebs/) volume. EBS is for
longer term data storage. 

</div>

<div>

\

</div>

<div>

[According to
Wikipedia](https://en.wikipedia.org/wiki/Block-level_storage),
\"Block-level storage is a concept in cloud-hosted data persistence
where cloud services emulate the behaviour of a traditional block
device, such as a physical hard drive \[\...\] This emulates the type of
behaviour seen in traditional disk or tape storage. Blocks are
identified by an arbitrary and assigned identifier by which they may be
stored and retrieved, but this has no obvious meaning in terms of files
or documents.\

<div>

\

</div>

<div>

\"Amazon EBS (Elastic Block Store) is an example of a cloud block store.
\[\...\] Block-level storage is in contrast to an object store or
\'bucket store\', such as Amazon S3 (Simple Storage Service), or to a
database\". 

</div>

\
**IPv6 support**: Internet Protocol - Version 6:

</div>

-   IPv4 address format: 24.128.21.12
-   IPv6 address format: 2001:CDBA:0000:0000:0000:0000:3257:9652

Only 23% of all networks use this \"new\" 20 year old format for IP
addresses, according to the Internet Society\'s [State of IPv6
Deployment
2017](https://www.internetsociety.org/resources/doc/2017/state-of-ipv6-deployment-2017/).\
\

<div>

Why a Gibibyte?
---------------

<div>

**\
Gibibyte**: Back in 2007 there was a class-action suit \"[against Kodak,
Sandisk, Lexar
Media](https://www.cnet.com/news/gigabytes-vs-gibibytes-class-action-suit-nears-end/),
and other memory card makers alleges that the defendants intentionally
misrepresented the capacity of their flash memory devices by using
decimal definitions, in which a megabyte is 1,000,000 bytes. The suit
says a binary definition is appropriate, meaning that one megabyte
equals 1,048,576 bytes and that the memory card sizes were overstated by
4 percent to 5 percent\".\
\
It doesn\'t matter much in small amounts, according to
CNet\'s [Gigabytes vs. gibibytes class action suit nears
end](https://www.cnet.com/news/gigabytes-vs-gibibytes-class-action-suit-nears-end/).
\"A decimal kilobyte, at 10\^3=1,000 wasn\'t very different from
2\^10=1,024\".

</div>

<div>

\
The problem is when you get into the Gigabyte realm: \"But as capacity
grows, the differences become more significant (technically, the ratio
between the decimal and binary representations increases). This explains
why your new terabyte drive isn\'t as capacious as you hoped it might
be. A 10\^12=1,000,000,000,000 decimal terabyte is roughly 10 percent
smaller than the binary equivalent of 2\^40=1,099,511,627,776\".\
\
\"\[\...\] There actually are terms that avoid all this confusion, and
those include IEEE 1541 terms
[gibibyte](http://en.wikipedia.org/wiki/Gibibyte) (2\^30 bytes =
1,073,741,824 bytes) and
[tebibyte](http://en.wikipedia.org/wiki/Tebibyte) (2\^40bytes =
1,099,511,627,776 bytes, or 1,024 gibibytes)\".\
\
Need even more information? The [Institute of Electrical and Electronics
Engineers](https://www.ieee.org/), founded back in 1965, handles these
types of problems. Read IEEE 1541: [Standard for Prefixes for Binary
Multiples](http://www.ieee802.org/secmail/pdf00106.pdf), which talks
about the Gibibyte.

</div>

<div>

 Let\'s Get Back to Key Pairs! 
-------------------------------

Going back to the [Linux Virtual Machine Ten Minute
Tutorial](https://aws.amazon.com/getting-started/tutorials/launch-a-virtual-machine/):
\"A key pair is used to securely access your Linux instance using SSH.
AWS stores the public part of the key pair which is just like a house
lock. You download and use the private part of the key pair which is
just like a house key.\
\
\"Select Create a new key pair and give it the name MyKeyPair. Next
click the Download Key Pair button.\
\
\"After you download the MyKeyPair key, you will want to store your key
in a secure location. If you lose your key, you won\'t be able to access
your instance. If someone else gets access to your key, they will be
able to access your instance.\
\
\"Windows users: We recommend saving your key pair in your user
directory in a sub-directory called .ssh (ex.
C:\\user\\{yourusername}\\.ssh\\MyKeyPair.pem). Tip: You can\'t use
Windows Explorer to create a folder with a name that begins with a
period unless you also end the folder name with a period. After you
enter the name (.ssh.), the final period is removed automatically\".

</div>

<div>

\

</div>

<div>

\

</div>

What is a PEM Format?
---------------------

\
From Quovadisglobal.com / Support, [What is PEM
Format?](https://support.quovadisglobal.com/kb/a37/what-is-pem-format.aspx)\
\
\
\"PEM or Privacy Enhanced Mail is a Base64 encoded DER certificate. PEM
certificates are frequently used for web servers as they can easily be
translated into readable data using a simple text editor. Generally when
a PEM encoded file is opened in a text editor, it contains very distinct
headers and footers. Below are some examples of different files in PEM
format.\
\
\-\-\-\--BEGIN CERTIFICATE REQUEST\-\-\-\--\
MIIB9TCCAWACAQAwgbgxGTAXBgNVBAoMEFF1b1ZhZGlzIExpbWl0ZWQxHDAaBgNV\
BAsME0RvY3VtZW50IERlcGFydG1lbnQxOTA3BgNVBAMMMFdoeSBhcmUgeW91IGRl\
Y29kaW5nIG1lPyAgVGhpcyBpcyBvbmx5IGEgdGVzdCEhITERMA8GA1UEBwwISGFt\
aWx0b24xETAPBgNVBAgMCFBlbWJyb2tlMQswCQYDVQQGEwJCTTEPMA0GCSqGSIb3\
DQEJARYAMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQCJ9WRanG/fUvcfKiGl\
EL4aRLjGt537mZ28UU9/3eiJeJznNSOuNLnF+hmabAu7H0LT4K7EdqfF+XUZW/2j\
RKRYcvOUDGF9A7OjW7UfKk1In3+6QDCi7X34RE161jqoaJjrm/T18TOKcgkkhRzE\
apQnIDm0Ea/HVzX/PiSOGuertwIDAQABMAsGCSqGSIb3DQEBBQOBgQBzMJdAV4QP\
Awel8LzGx5uMOshezF/KfP67wJ93UW+N7zXY6AwPgoLj4Kjw+WtU684JL8Dtr9FX\
ozakE+8p06BpxegR4BR3FMHf6p+0jQxUEAkAyb/mVgm66TyghDGC6/YkiKoZptXQ\
98TwDIK/39WEB/V607As+KoYazQG8drorw==\
\-\-\-\--END CERTIFICATE REQUEST\-\-\-\--\
\
\"Above is the example of a CSR (certificate signing request) in PEM
format. You can see that PEM has the characteristics of containing a
header, the body (which consists mainly of code) and footer\".\
\

<div>

After you set up your key pair and download it to your hard drive, you
can **Launch the Virtual Machine**!\
\

How to Launch Your Instances!
-----------------------------

\
From Amazon: \"Your instances are launching, and it may take a few
minutes until they are in the running state, when they will be ready for
you to use. Usage hours on your new instances will start immediately and
continue to accrue until you stop or terminate your instances.

</div>

<div>

\
\"Click **View Instances** to monitor your instances\' status. Once your
instances are in the running state, you can connect to them from the
Instances screen. [Find
out](https://docs.aws.amazon.com/console/ec2/instances/connect/docs) how
to connect to your instances.\
\
\"Here are some helpful resources to get you started\

-   \"[How to connect to your Linux
    instance](https://docs.aws.amazon.com/console/ec2/instances/connect/docs)
-   \"[Learn about AWS Free Usage Tier](https://aws.amazon.com/free/)
-   \"[Amazon EC2: User
    Guide](https://docs.aws.amazon.com/console/ec2/launchinstance/status/user-guide)
-   \"[Amazon EC2: Discussion
    Forum](https://forums.aws.amazon.com/forum.jspa?forumID=30)
-   \"While your instances are launching you can also
-   \"Create status check alarms to be notified when these instances
    fail status checks. (Additional charges may apply)
-   \"[Create and attach additional EBS
    volumes](https://us-west-2.console.aws.amazon.com/ec2/v2/home?region=us-west-2#Volumes:)
    (Additional charges may apply)
-   \"[Manage security
    groups](https://us-west-2.console.aws.amazon.com/ec2/v2/home?region=us-west-2#SecurityGroups:)\"

\
\... Oh, I made sure to set up to receive billing reports right away!\

 We Have Running Machine!
-------------------------

</div>

<div>

Yes! We have a running machine! You can see it in the EC2 Dashboard:

</div>

<div>

\

</div>

  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://1.bp.blogspot.com/-plEeunJZYeM/Wmy1OY9AFKI/AAAAAAAAMQY/GfjdN3dkAwUt-hQsaPq0urqKB49U30EVwCLcBGAs/s640/instance.png){width="640" height="163"}](https://1.bp.blogspot.com/-plEeunJZYeM/Wmy1OY9AFKI/AAAAAAAAMQY/GfjdN3dkAwUt-hQsaPq0urqKB49U30EVwCLcBGAs/s1600/instance.png)
                                                                                                          *The EC2 Dashboard, with my Instance ID and IPv4 address blocked out. *
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

<div>

\

</div>

 How to Connect to Your Instance
--------------------------------

<div>

1\) Download Git for Windows, if a Windows User:

</div>

<div>

\

</div>

<div>

For **Windows** Users, they recommend using [Git for
Windows](https://git-scm.com/download). For Macs, they recommend the
**Mac Terminal**. Although I am using a Windows 10 machine at home, I
decided I wanted it installed on the Command Prompt. 

</div>

<div>

\

</div>

<div>

2\) Connect via SSH to the Machine

</div>

<div>

\

</div>

<div>

I [followed the AWS
instructions](https://aws.amazon.com/getting-started/tutorials/launch-a-virtual-machine/):

</div>

\
\"Right click on your Windows desktop (not on an icon or file) and
select **Git Bash Here** to open a Git Bash command prompt\".

</div>

<div>

\

</div>

<div>

Since the fake IP addrerss I am using in this example is \"ec-5678\",
what I entered in the command prompt looked something like\...\
\

<div>

\$ ssh -i \'d:\\Users\\tmaher\\.ssh\\tjmaher.pem\'
ec2-user\@ec2-5678.us-west-2.compute.amazonaws.com

</div>

<div>

\

</div>

<div>

\

</div>

<div>

3\) Bask in Glory!\
\
The Following text appeared in the command line:\
\

</div>

<div>

    Warning: Permanently added 
    'ec2-5678.us-west-2.compute.amazonaws.com,11.222.88.99' (ECDSA) 
    to the list of known hosts.

           __|  __|_  )
           _|  (     /   Amazon Linux AMI
          ___|\___|___|

    https://aws.amazon.com/amazon-linux-ami/2017.09-release-notes/
    1 package(s) needed for security, out of 1 available
    Run "sudo yum update" to apply all updates.
    [ec2-user@ip-12345 ~]$

</div>

<div>

\

</div>

<div>

Destroy Your Servers!
---------------------

</div>

<div>

If experimenting with AWS, do what a co-worker told me to do: Write this
down on a Post-It Note and post it where you can see it:\
\

-   Destroy Your Servers

<div>

If you do not remember to destroy your servers when you get done with
them, you might get charged!

</div>

\
\"Back on the EC2 Console, select the box next to the instance you
created. Then click the Actions button, navigate to *Instance State*,
and click Terminate\".\
\

<div>

One thing\... do you have anything you want saved on the instance? If
you are using just EBS, \[\...O\]n an EBS-backed instance, the default
action is for the root EBS volume to be deleted when the instance is
terminated. Storage on any local drives will be lost\".

</div>

\
\
\
\
\

What\'s Next?
-------------

\
What\'s Next? Who knows! Now you know as much as I do during my second
week of my job!\
\
Happy Testing!\
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

</div>
