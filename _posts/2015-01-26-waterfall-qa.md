\-\-- layout: post title: Waterfall + QA date:
\'2015-01-26T09:44:00.000-05:00\' author: T.J. Maher tags: - manual - qa
- waterfall modified\_time: \'2016-04-29T08:02:48.887-04:00\'
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-493753395644904620
blogger\_orig\_url: http://www.tjmaher.com/2015/01/waterfall-qa.html
\-\--\
Take the product owners, product managers, and business analysts who
come up with business requirements for a software product that customers
might need. Take a bunch of software architects who design the
blueprints of the software product. Add the designers and user
experience people to sketch the look-and-feel of the software product.
Software developers to construct the product. Quality assurance
engineers to test the product. How does the team work together to build,
test, and launch the product?\
\
That is the **software development process**.\
\
[]{#more}\
\
The next few blog posts will describe how software development
methodologies have evolved, and with that how the role of Software
Quality Assurance has changed since I started working in the industry.\
\
Let me start with the first method that I encountered back in the
mid-1990s\...\
\

### The Waterfall Method

\
When I first started my Software Quality Assurance career as a
consultant at Oracle back in 1996, the method that was most common for
developing software was the waterfall method, which has been in use
since the 1970s and 1980s.\
\
With the waterfall method, the software development process was broken
up into different phases: Requirements, Design, Implementation,
Verification and Maintenance. If you diagrammed it, it would be
described as a waterfall. During each phase of the project, artificats
and deliverables such as project plans, technical specs and database
design documents would cascade down to the next phase of the project.\
\
The business analysts in the **Requirements** phase would draft
documents detailing the requirements of the software product they would
build, the purpose of the product, a software requirements specification
detailing a checklist of business requirements, a high level description
of the system.\
\
This would be handed off to the software architects who in the
**Design** phase would write the blueprints of the product. Each
software component would be sketched out, the data structure of the
database would be designed.\
\
In the **Implementation** phase, the software developers would construct
the software product.\
\
With the **Verification** phase, the software testers would create test
plans to describe a high level approach on how to test, and once
approved, test cases detailing more on what would be tested, and once
approved they would generate test scripts listing step-by-step how they
would go about testing the product. Hopefully, by the time the product
was ready for testing, the test plans, test cases, and test scripts
would all be written.    \
\
With the **Maintenance** phase, the software product would be released
into the wild. The customers would use the product, and any questions,
complaints, and other feedback would be gathered to help improve the
next version of the product.\
\
There were many problems Quality Assurance encountered with this
method.\
\
\

-   What if the reason a bug occured was because the spec or the design
    of the software product was unclear? As a QA Engineer, you could try
    to independently read through all the previous stages deliverables
    on your own as they were released, to try to get a feel for the
    purpose of the software product \... but QA wasn\'t actively
    involved until the project was almost finished. 
-   What happens if all the preceeding stages took longer than what was
    scoped out? It would always be easier for the time allotted for QA
    to be scaled back than to push back the release date. Sometimes the
    best you could do was tp record all bugs found, triage them, and try
    to get them fixed in the next iteration of the product. 
-   What if there were last minute change orders? Are the test plans,
    test cases, and test scripts still valid when the official
    validation period starts? 
-    Development and Quality Assurance were not integrated with one
    another, fostering in some places that I had worked as a consultant
    an \"Us vs Them\" mentality. Some QA Managers saw the QA Engineers
    as a rubber stamp to okay everything the developers did. Some would
    claim that their job was to act as a roadblock to the developers. 

\
\
The relationship between DEV and QA shouldn\'t be the relationship
between an Artist and an Art Critic. It should be more like a Writer and
a Copyeditor, where everyone knows that they are on the same team,
helping make a quality product.\
\
\
-T.J. Maher\
* Sr. QA Engineer*\
* Quincy, MA*
