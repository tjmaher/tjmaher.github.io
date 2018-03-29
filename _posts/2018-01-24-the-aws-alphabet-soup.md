\-\-- layout: post title: The AWS Alphabet Soup date:
\'2018-01-24T20:24:00.002-05:00\' author: T.J. Maher tags: - DevOps -
aws modified\_time: \'2018-01-28T08:44:50.973-05:00\' thumbnail:
https://i.ytimg.com/vi/mZ5H8sn\_2ZI/default.jpg blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-1527189155848623841
blogger\_orig\_url:
http://www.tjmaher.com/2018/01/the-aws-alphabet-soup.html \-\-- AWS.
EC2. S3. S3 Buckets. SQS. SNS. ARN. IAM. Eb. AMI. Cloud Trail. Cloud
Formation. Diving through our product documentation on my first day at
[Threat Stack](http://threatstack.com/), and I couldn\'t understand a
word!\
\
I am getting exposure to **AWS** \-- that is, [Amazon Web
Services](https://aws.amazon.com/) \-- for the first time in my
new Software Development Engineer in Test role. All the companies I have
worked at in the past had their own physical servers hosting whatever
**SaaS** \-- Software as a Service \-- web or mobile product I was
testing.\
\
With SaaS, like the Software as a Service name implies, it\'s like
[Microsoft
Office](https://products.office.com/en-us/compare-all-microsoft-office-products?tab=1):
You can choose to rent the software per month or per year. Yes, you
could purchase the student version, and apply any patches and bug fixes
yourself, but when using SaaS, Microsoft handles everything.\
\
Likewise, the same business model applies for infrastructure and
platforms.\
\
[]{#more}\
\
**[What is AWS - Amazon Web Services?]{.underline}**\

*<https://youtu.be/mZ5H8sn_2ZI>*\
\
According to Amazon\'s \"[Types of Cloud
Computing](https://aws.amazon.com/types-of-cloud-computing/)\" there
is:\

-   **Infrastructure as a Service (IaaS)**: \"Infrastructure as a
    Service, sometimes abbreviated as IaaS, contains the basic building
    blocks for cloud IT and typically provide access to networking
    features, computers (virtual or on dedicated hardware), and data
    storage space\".
-   **Platform as a Service (PaaS)**: \"Platforms as a service remove
    the need for organizations to manage the underlying infrastructure
    (usually hardware and operating systems) and allow you to focus on
    the deployment and management of your applications. This helps you
    be more efficient as you don't need to worry about resource
    procurement, capacity planning, software maintenance, patching, or
    any of the other undifferentiated heavy lifting involved in running
    your application\".

The problem I am finding? There are way too many products. Right now, I
need to focus on just what TLAs (Three Letter Acronyms) are being used
at my workplace.\
\
Let\'s see\... there is\...\
\
**AWS**: Amazon Web Services\
\
**EC2**: [Elastic Compute Cloud](https://aws.amazon.com/ec2):
\"Resizable compute capacity in the cloud\". Shorten boot up time. Scale
up or scale down as needs dictate.\

<div>

\

</div>

<div>

**CloudTrail**: \"[AWS CloudTrail](https://aws.amazon.com/cloudtrail) is
a service that enables governance, compliance, operational auditing, and
risk auditing of your AWS account. With CloudTrail, you can log,
continuously monitor, and retain account activity related to actions
across your AWS infrastructure\".

</div>

<div>

\

</div>

**CloudFormation**: \"[AWS
CloudFormation](https://aws.amazon.com/cloudformation/) provides a
common language for you to describe and provision all the infrastructure
resources in your cloud environment. CloudFormation allows you to use a
simple text file to model and provision, in an automated and secure
manner, all the resources needed for your applications across all
regions and accounts. This file serves as the single source of truth for
your cloud environment\".\

<div>

\

</div>

<div>

**S3**: [Simple Storage Service](https://aws.amazon.com/s3/):
\"Companies today need the ability to simply and securely collect,
store, and analyze their data at a massive scale. Amazon S3 is [object
storage](https://aws.amazon.com/what-is-cloud-object-storage/) built to
store and retrieve any amount of data from anywhere -- web sites and
mobile apps, corporate applications, and data from IoT sensors or
devices\".

</div>

<div>

\

</div>

<div>

**S3 Buckets**: \"Amazon S3 is cloud storage for the Internet. To upload
your data (photos, videos, documents etc.), you first [create a bucket
in one of the AWS
Regions](https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingBucket.html).
You can then upload any number of objects to the bucket. In terms of
implementation, buckets and objects are resources, and Amazon S3
provides APIs for you to manage them. For example, you can create a
bucket and upload objects using the Amazon S3 API. You can also use the
Amazon S3 console to perform these operations. The console internally
uses the Amazon S3 APIs to send requests to Amazon S3\". 

</div>

<div>

\

</div>

<div>

**SQS**: \"Amazon [Simple Queue Service](https://aws.amazon.com/sqs/)
(SQS) is a fully managed message queuing service that makes it easy to
decouple and scale microservices, distributed systems, and serverless
applications. Building applications from individual components that each
perform a discrete function improves scalability and reliability, and is
best practice design for modern applications\". 

</div>

<div>

\

</div>

<div>

**SNS**: \"Amazon [Simple Notification
Service](https://aws.amazon.com/sns/) (SNS) is a flexible, fully managed
[pub/sub messaging](https://aws.amazon.com/pub-sub-messaging/) and
mobile notifications service for coordinating the delivery of messages
to subscribing endpoints and clients. With SNS you can fan-out messages
to a large number of subscribers, including distributed systems and
services, and mobile devices\".

</div>

<div>

\

</div>

<div>

**ARN**: \"[Amazon Resource
Names](https://docs.aws.amazon.com/general/latest/gr/aws-arns-and-namespaces.html)
(ARNs) uniquely identify AWS resources. We require an ARN when you need
to specify a resource unambiguously across all of AWS, such as in IAM
policies, Amazon Relational Database Service (Amazon RDS) tags, and API
calls\".

</div>

<div>

\

</div>

<div>

**IAM**: \"AWS [Identity and Access
Management](https://aws.amazon.com/documentation/iam/) (IAM) is a web
service for securely controlling access to AWS services. With IAM, you
can centrally manage users, security credentials such as access keys,
and permissions that control which AWS resources users and applications
can access\".

</div>

<div>

\

</div>

<div>

**Eb:** \"With [AWS Elastic
Beanstalk](https://aws.amazon.com/elasticbeanstalk/), you can quickly
deploy and manage applications in the AWS Cloud without worrying about
the infrastructure that runs those applications. AWS Elastic Beanstalk
reduces management complexity without restricting choice or control. You
simply upload your application, and AWS Elastic Beanstalk automatically
handles the details of capacity provisioning, load balancing, scaling,
and application health monitoring\".

</div>

<div>

\

</div>

<div>

**AMI**: [Amazon Machine
Image](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/using-features.customenv.html):
\"When you create an AWS Elastic Beanstalk environment, you can specify
an Amazon Machine Image (AMI) to use instead of the standard Elastic
Beanstalk AMI included in your platform configuration\'s solution stack.
A custom AMI can improve provisioning times when instances are launched
in your environment if you need to install a lot of software that isn\'t
included in the standard AMIs\".

</div>

<div>

\

</div>

<div>

**Amazon ElasticCache**: \"[Amazon
ElastiCache](https://aws.amazon.com/elasticache/) offers fully managed
[Redis](https://aws.amazon.com/redis/) and
[Memcached](https://memcached.org/). Seamlessly deploy, operate, and
scale popular open source compatible in-memory data stores. Build
data-intensive apps or improve the performance of your existing apps by
retrieving data from high throughput and low latency in-memory data
stores. Amazon ElastiCache is a popular choice for Gaming, Ad-Tech,
Financial Services, Healthcare, and IoT apps\".

</div>

<div>

\

</div>

<div>

**Redis**: Acronym for [REmote DIctionary
S](https://aws.amazon.com/redis/)[erver](https://aws.amazon.com/redis/).
\"[Redis](https://aws.amazon.com/elasticache/what-is-redis/) is an open
source, in-memory data store that delivers sub-millisecond response
times enabling millions of requests per second to power real-time
applications. It can be used as a fast database, cache, message broker,
and queue. Redis provides a variety of data structures including
strings, lists, sets, sorted sets, hashmaps, hyperloglogs, and
bitmaps\".\
\

<div>

To get more exposure, I signed up for the [AWS Free
Tier](https://aws.amazon.com/free/).\

-   Some services are free for 12 months, provided I do not go over 750
    hrs per month of usage of EC2, and over 5 GB of Storage in Amazon
    EFS or 30 GB of Elastic Block Storage for long term. 
-   [Some services seem to be always
    free.](https://aws.amazon.com/free/#legal)

<div>

\... Pardon me as I mark my Google Calendar to unsubscribe. 

</div>

\
There are also a series of [10 Minute
Tutorials](https://aws.amazon.com/getting-started/tutorials/) on
everything listed above that I need to check out!\
\
Wish me luck! Happy Testing!\
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
