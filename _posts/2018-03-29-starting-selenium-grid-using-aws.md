\-\-- layout: post title: Starting a Selenium Grid using AWS +
SeleniumHQ Docker images + Docker Compose date:
\'2018-03-29T09:08:00.002-04:00\' author: T.J. Maher tags:
modified\_time: \'2018-03-29T09:08:47.071-04:00\' blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-3083532744552101704
blogger\_orig\_url:
http://www.tjmaher.com/2018/03/starting-selenium-grid-using-aws.html
\-\-- With this blog post we will be exploring how to start a Selenium
Grid using an Amazon Web Service (AWS) instance the SeleniumHQ Docker
images, Docker and Docker Compose. For this example, I will be using a
Macbook, so the Terminal will be my Command Line Interface.\
\
Need more information? Check out the official Amazon Web Services
documentation:\

-   [What is Docker?](https://aws.amazon.com/docker/)
-   [What is an Amazon Machine Image
    (AMI)](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AMIs.html)
-   [Amazon Linux AMI
    FAQ](https://aws.amazon.com/amazon-linux-ami/faqs/)
-   [Docker overview](https://docs.docker.com/engine/docker-overview/)

We could use the \"[Amazon Elastic Container
Service](https://aws.amazon.com/ecs/)\" and using [AWS
Fargate](https://aws.amazon.com/fargate/) to run containers without
managing servers or clusters \... but since I am tinkering, I want to
make sure that I am using only free services provided by the Amazon Free
Tier that I signed up for last month.\
\
We are going to be starting off by following along with the official
docs by Amazon, [AWS Docker
Basics](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/docker-basics.html).\
[]{#more}\

### Start up an AWS EC2 Instance

First, we are going to go to [AWS.Amazon.Com](http://aws.amazon.com/)
and sign in.\
\
Once on the dashboard, select \"Launch a Virtual Machine\".\
\
[**Choose an Amazon Machine Image (AMI)**]{.underline}\
\
I made sure to check off \"Free Tier Only\" checkbox. I don\'t want to
accidentally incure a bill.\
\
I chose first Amazon Machine Image, Amazon Linux AMI version 2017.09.1
(HVM), SSD Volume Type , 64 bit.\

-   The info for this machine reads: \"The default image includes AWS
    command line tools, Python, Ruby, Perl, and Java. The repositories
    include Docker, PHP, MySQL, PostgreSQL, and other packages.\" 

Press the Select Button.\
\
[**Choose Instance type**]{.underline}\
\
I chose General purpose, t2.micro.\

-   The info for \"General Purpose\": \"General purpose instances
    provide a balance of compute, memory, and network resources, and are
    a good choice for many applications. They are recommended for small
    and medium databases, data processing tasks that require additional
    memory, caching fleets, and for running backend servers for SAP,
    Microsoft SharePoint, and other enterprise applications.\"
-   The info for \"T2\" reads: \"T2 instances provide a baseline level
    of CPU performance with the ability to burst above the baseline.The
    baseline and ability to burst are governed by CPU Credits. The
    t2.micro receives CPU Credits continuously at a rate of 6 CPU
    Credits per hour. To learn more about Amazon EC2 T2 instances, see
    the Amazon EC2 details page\".

\
From here, I selected \"Review and Launch\" and \"Launch\".\
\
[**Creating a key pair**]{.underline}\
\
I chose to create a new key pair, naming it \"tjmaher-test\". Selecting
\"Download Key Pair\", saved the private key tjmaher-test.pem to my
local machine.\
\
\"A key pair consists of a public key that AWS stores, and a private key
file that you store. Together, they allow you to connect to your
instance securely. For Windows AMIs, the private key file is required to
obtain the password used to log into your instance. For Linux AMIs, the
private key file allows you to securely SSH into your instance\".\
\
\"A key pair consists of a public key that AWS stores, and a private key
file that you store. Together, they allow you to connect to your
instance securely. For Windows AMIs, the private key file is required to
obtain the password used to log into your instance. For Linux AMIs, the
private key file allows you to securely SSH into your instance\".\
\
\
\
[**Confirm the AWS Instance is Running**]{.underline}\
\
To view the AMI instance that was created, go to AWS -\> Services -\>
EC2 to get to the EC2 Dashboard, and select the link for \"Running
Instances\"\
\
You can see that it is running. Hrm\... refering to it by instance id
would be a bit much. Let\'s click on the blank space under the name and
call it \"grid\".\
\

### Allow Outside Automation Toolsets to Connect to the Selenium Grid

\
How will outside toolsets access the AWS instance connect to this
Selenium Grid we will be running?\
\
Selenium Grid uses port \"4444\". For this demo, we will be opening that
port for the public IP address.\
\
But how do you find this public  IP address?\

-   On the AWS Console, go to Actions -\> Networking -\> Manage IP
    addresses.

\"You can assign and unassign IPv4 and IPv6 IP addresses on each network
interface. Leave the IP address field blank and an available address
will be assigned or enter an IP address that you want to assign.\
\
\"To add or edit an IPv4 public IP Allocate an Elastic IP to this
instance or network interface\".\
\
It shows two IP addresses:\

-   Private IP: 172.31.26.200 
-   Public IP : 54.201.124.200

\... Note these are not the real IP addresses that were given. As much
as I like my blog readers, I don\'t want you connecting to my Selenium
Grid.\
\
We are going to open up port 4444 on that Public IP by adding a new rule
to that security group to allow inbound traffic.\
\
[**But What Is a Security Group?**]{.underline}\
\
According to [Amazon EC2 Security Groups for Linux
Instances](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-network-security.html):
\"A security group acts as a virtual firewall that controls the traffic
for one or more instances. When you launch an instance, you associate
one or more security groups with the instance. You add rules to each
security group that allow traffic to or from its associated instances.
You can modify the rules for a security group at any time; the new rules
are automatically applied to all instances that are associated with the
security group after a short period. When we decide whether to allow
traffic to reach an instance, we evaluate all the rules from all the
security groups that are associated with the instance.\"\
\
We are going to add a rule that port 4444 is fine for inbound traffic.\
\
Following the instructions for Amazon\'s doc, [Adding Rules to a
Security
Group](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-network-security.html#adding-security-group-rule):\
\
1) Open the Amazon EC2 console at https://console.aws.amazon.com/ec2/\
2) In the navigation pane, choose the Security Groups link.\
3) Select the Inbound tab, choose Edit.\
4) In the dialog, choose Add Rule and do the following:\

-   Type: Custom TCP
-   Protocol: TCP
-   Part Range: 4444
-   Source: My IP
-   Description: Selenium Grid

\
Once the Selenium Grid is up and running, if 54.201.124.200 is the
public facing IP addresss, connecting to
http://54.201.124.200:4444/grid/console will connect to the console.\
\

### How To Connect to Our AWS Instance

\
How do we connect through the command line to this AWS instance we are
creating? To see how, press the \"Connect\" button on the AWS
Dashboard.\
\
\"To access your instance:\
\"Open an SSH client. *(We will be using the Mac Terminal)*\
\"Locate your private key file *(tjmaher-test.pem)*. The wizard
automatically detects the key you used to launch the instance.\
\"Your key must not be publicly viewable for SSH to work. Use this
command if needed:\
\"chmod 400 tjmaher-test.pem\
\
\"Connect to your instance using its Public DNS:\
ec2-1234.compute.amazonaws.com\
\
\"Example: ssh -i \"tjmaher-test.pem\"
ec2-user\@1234.us-west-2.compute.amazonaws.com\
\
\"Please note that in most cases the username above will be correct,
however please ensure that you read your AMI usage instructions to
ensure that the AMI owner has not changed the default AMI username.\
\
\"If you need any assistance connecting to your instance, please see our
connection documentation\".\
\
Following the instructions, we can connect to the AWS instance.\
\
Opening up the Mac Terminal we can ssh into the machine: *ssh -i
\"tjmaher-test.pem\" ec2-user\@1234.us-west-2.compute.amazonaws.com*\
\
\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
     __| __|_ )  
     _| (   /  Amazon Linux AMI  
    ___|\___|___|  
   
 https://aws.amazon.com/amazon-linux-ami/2017.09-release-notes/  
 2 package(s) needed for security, out of 5 available  
 Run "sudo yum update" to apply all updates.  
 [ec2-user@ip-172-31-26-200 ~]$  
```

\
\
Let\'s do that, updating the image: *sudo yum update*\
\

### Install Docker on an Amazon Linux instance

\
Now, let\'s continue following the [AWS guide on Docker
Basics](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/docker-basics.html).\
\
We have completed the first two steps, [launching an AWS
instance](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/launching-instance.html) 
and [connecting to your Linux
instance](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AccessingInstances.html).\
\
Following the Amazon instructions for [Docker
Basics](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/docker-basics.html):\

-   Install Docker on the AWS instance: *sudo yum install -y docker*
-   Start the docker service: sudo service docker start
-   Add the ec-2-user to the Docker group: *sudo usermod -a -G docker
    ec2-user*
-   Close the Mac Terminal and reopen it to reset permissions.

Is Docker installed? We can see\
\
Containers: 0\
Running: 0\
Paused: 0\
Stopped: 0\
Images: 0\
\
How does Docker know how to get something running in its container? It
uses a special file called a Dockerfile. What is a Dockerfile? From the
[Docker Reference:
Builder](https://docs.docker.com/engine/reference/builder/): \"Docker
can build images automatically by reading the instructions from a
Dockerfile. A Dockerfile is a text document that contains all the
commands a user could call on the command line to assemble an image.
Using docker build users can create an automated build that executes
several command-line instructions in succession.\"\

### 

### Start Up a Selenium Grid Using SeleniumHQ Docker Images

\
To start up a Selenium Grid, we are going to use pre-written Docker
images that the Selenium HQ people are already using. They are stored
publicly at Docker Hub at <https://hub.docker.com/u/selenium/>.\
\
We are going to be following along the official SeleniumHQ instructions
from their Docker-Selenium site at
[https://github.com/SeleniumHQ/docker-selenium.](https://github.com/SeleniumHQ/docker-selenium)\
\
For this demo, the Docker images we will be using:\

-   **selenium/hub**: Image for running a Grid Hub. It will expose port
    4444 on the AWS instance so we can connect to the Selenium Grid.
-   **selenium/node-chrome**: Grid Node with Chrome installed, needs to
    be connected to a Grid Hub
-   **selenium/node-firefox**: Grid Node with Firefox installed, needs
    to be connected to a Grid Hub

According to Selenium HQ\'s instructions, you need to create a [Docker
Network](https://docs.docker.com/engine/reference/commandline/network_create/)\
\
*\$ docker network create grid*\
*\$ docker run -d -p 4444:4444 \--net grid \--name selenium-hub
selenium/hub:3.11.0-bismuth*\
*\$ docker run -d \--net grid -e HUB\_HOST=selenium-hub -v
/dev/shm:/dev/shm selenium/node-chrome:3.11.0-bismuth*\
*\$ docker run -d \--net grid -e HUB\_HOST=selenium-hub -v
/dev/shm:/dev/shm selenium/node-firefox:3.11.0-bismuth*\
\
A better way?\

-   Docker Compose: <https://docs.docker.com/compose/overview/>
-   Docker Compose GitHub: <https://github.com/docker/compose>

\
\"Compose is a tool for defining and running multi-container Docker
applications. With Compose, you use a YAML file to configure your
application's services. Then, with a single command, you create and
start all the services from your configuration.\"\
\
Once you have a Docker Compose file, to start and stop the Selenium
Grid.\
\
\$ docker-compose up -d\
\$ docker-compose down\
\
Where would you find such a file? Selenium HQ! The [instructions we have
been reviewing](https://github.com/SeleniumHQ/docker-selenium) has one
for you:\
\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 # To execute this docker-compose yml file use docker-compose -f <file_name> up  
 # Add the "-d" flag at the end for deattached execution  
 version: '2'  
 services:  
  firefox:  
   image: selenium/node-firefox:3.11.0-bismuth  
   volumes:  
    - /dev/shm:/dev/shm  
   depends_on:  
    - hub  
   environment:  
    HUB_HOST: hub  
   
  chrome:  
   image: selenium/node-chrome:3.11.0-bismuth  
   volumes:  
    - /dev/shm:/dev/shm  
   depends_on:  
    - hub  
   environment:  
    HUB_HOST: hub  
   
  hub:  
   image: selenium/hub:3.11.0-bismuth  
   ports:  
    - "4444:4444"  
```

\
\"To stop the grid and cleanup the created containers, run
*docker-compose down*\".\
\
Since we are tinkering, we will have the Hub and Nodes on the same
machine. Note, it does not have to be this way! You can attach any node
to the Hub.\
\

### Install Docker Compose

\
Now that we have Docker, let\'s install Docker Compose on the AWS
instance we have running.\
\
Let\'s use the official documentation for **Install Docker Compose** at
<https://docs.docker.com/compose/install/>\
\
According to the documentation, you can use curl to install it.\
\
*sudo curl -L
https://github.com/docker/compose/releases/download/1.20.1/docker-compose-\`uname
-s\`-\`uname -m\` -o /usr/local/bin/docker-compose*\
\
Let\'s apply executable permissions: *sudo chmod +x
/usr/local/bin/docker-compose*\
Test to see if Docker Compose is working: *docker-compose \--version*\
\
Our output:\

-   docker-compose version 1.20.1, build 5d8c71b

\... Yes, it is working!\
\

### Create the Docker Compose File

\
Now that we have Docker Compose up and running, let\'s create a
docker-compose.yml file out of the text that SeleniumHQ gave us.\

-   Go back to Mac Terminal you have running.
-   Check that you are still ssh\'ed into the AWS instance.
-   Create a new blank file: *touch docker-compose.yml*

Did it work? List what is in the directory: *ls*\
\
Let\'s edit the file in the nano text editor: *nano docker-compose.yml*\

-   Copy and paste the Docker Compose file into this file.
-   \^X (Control + X) will exit Nano.
-   Y to save the file.
-   Enter to close nano.
-   Brought back to to the main command line.

Did it save? Let\'s print the file to the screen: *cat
docker-compose.yml*\
\

### Docker Compose Up! 

\
Now, let\'s type the magic words: *docker-compose up -d*\
\
\... Adding the -d flag runs Docker in detached mode so we can go onto
other things after kicking it off. \
\
When we run this command, all Docker files are being pulled from the
Docker Hub, downloaded, extracted, and installed into Docker on our AWS
instance.\
\
What is being set up?\

-   hub\_1
-   firefox\_1
-   chrome\_1

\
\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 hub_1   | 20:55:49.994 INFO [Hub.start] - Selenium Grid hub is up and running  
 firefox_1 | 2018-03-28 20:55:49.866:INFO::main: Logging initialized @2148ms to org.seleniumhq.jetty9.util.log.StdErrLog  
 chrome_1  | 2018-03-28 20:55:49.879:INFO::main: Logging initialized @2163ms to org.seleniumhq.jetty9.util.log.StdErrLog  
 hub_1   | 20:55:49.994 INFO [Hub.start] 
- Selenium Grid hub is up and running  
 hub_1   | 20:55:49.995 INFO [Hub.start] 
- Nodes should register to http://172.18.0.0:4444/grid/register/  
 hub_1   | 20:55:49.996 INFO [Hub.start] 
- Clients should connect to http://172.18.0.0:4444/wd/hub  
   
 Selenium Server is running  
   
 hub_1   | 20:55:51.787 INFO [DefaultGridRegistry.add] - Registered a node http://172.18.0.0:5555  
 hub_1   | 20:55:51.788 INFO [DefaultGridRegistry.add] - Registered a node http://172.18.0.0:5555  
 chrome_1  | 20:55:51.994 INFO [SelfRegisteringRemote.registerToHub] - The node is registered to the hub and ready to use  
 firefox_1 | 20:55:52.017 INFO [SelfRegisteringRemote.registerToHub] - The node is registered to the hub and ready to use  
```

\
\
Need 5 more instances of Chrome? With Docker you can scale up or down
depending on what you need: *docker-compose scale chrome=5*\
\
Now, all I needed to do is go to http://54.201.124.200:4444/grid/console
to see a perfectly running Selenium Grid!\
\
\... Of course, you wouldn\'t use that. You would access the
selenium-grid console using http://{YOUR\_HOST}:4444/grid/console \...\
\
Next, I need to add Safari to the mix\... anyone know how to do that?\
\
Oh, and before I forget, I need to change the external IP address. I
think I changed the digits of the external IP enough? Not sure. I don\'t
want the world connecting to it.\
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
