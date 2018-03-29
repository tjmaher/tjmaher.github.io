\-\-- layout: post title: Notes from Zero to Continuous Delivery with
Jenkins Pipeline and Blue Ocean date: \'2017-06-26T00:47:00.003-04:00\'
author: T.J. Maher tags: modified\_time:
\'2017-06-26T00:56:51.964-04:00\' thumbnail:
https://i.ytimg.com/vi/k\_fVlU1FwP4/default.jpg blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-5688090079563010721
blogger\_orig\_url:
http://www.tjmaher.com/2017/06/notes-from-zero-to-continuous-delivery.html
\-\-- **[On-Demand Webinar:]{.underline}** Zero to Continuous Delivery
with Jenkins Pipeline and Blue Ocean\
*Register to watch it online
here!* <https://pages.cloudbees.com/0621-webinar-zero-to-cd-with-blue-ocean-registration>\
\
\"Jenkins has long been the hub of continuous delivery. Jenkins
Pipeline, however, now brings a whole new world of possibilities. This
video shows get started with Jenkins Pipeline and implement a complete,
practical continuous delivery process from start to finish.\
\
\"This webinar shows you how to:\

-   \"Create a Declarative Pipeline for a Java and Node.js Project with
    the Blue Ocean Editor
-   \"Safely iterate on a Jenkins Pipeline to add Build, Test, Analyze,
    and Deploy stages
-   \"Launch different Docker agents for each stage
-   \"Run stages in Parallel to improve Pipeline throughput
-   \"Manually control promotion using the \"input\" step

**[]{.underline}**\
[]{#more}**[\
]{.underline}[Liam Newman, Technical Evangelist at CloudBees,
Inc.]{.underline}**\
\"Liam has spent the majority of his software engineering career
implementing CI/CD systems at companies big and small.  He is a Jenkins
project contributor and an expert in Jenkins Pipeline, both Scripted and
Declarative. When not at work, he enjoys testing gravity by doing
Aikido\".\
\
Liam Newman, Jenkins evangelist, can be reached on Twitter at
@[bitwiseman](https://twitter.com/bitwiseman).\
**[\
]{.underline}[Warning!!!]{.underline}**\
\

-   **This section is a bit too advanced for a manual tester.** It is
    also a bit too advanced for me! I can barely keep up, but only
    because I have tinkered with Jenkins, and have written both Unix
    shell script and a few Groovy scripts. This \"introduction\" to Blue
    Ocean is probably for someone who is well versed in creating a
    deployment pipeline before\... which I have never done before. 

\

\
**[Continuous Delivery]{.underline}**\
\

-   Best approach for producing software in short cycles, higher
    reliability with faster feedback.

\
\
**[Jenkins Pipeline]{.underline}**\
\

-   Created to support CI / CD

\
\
**[Pipeline as code:]{.underline}**\

-   Capture the entire continuous delivery process.
-   Check a Jenkinsfile into your source repo alongside build processes.

\
See[http://Jenkins.io/book/pipeline](http://jenkins.io/book/pipeline) to
get more information on the pipeline versions you can build alongside
your product.\
\
**[Blue Ocean]{.underline}**\
\

-   Built to serve and make Jenkins Pipeline easier and more accessible.

\
\
Liam Newman showed an example: Stages of the build can be created on the
fly: parallel browser test stage, static analysis, and then deployment.
It can show us more useful information.\
\
You can click on exactly the part of the pipeline you wish to see, and
it will only show those log files.\
\
You can edit pipelines in a friendly UI way. Engineers may want to work
in a text editor. Some though prefer to work in a UI. Blue Ocean
satisfies both.\
\
How do we run a new **Blue Ocean** image? Right from Docker!\
\
[Docker run -p 8080:8080 -u root
\\]{style="font-family: "courier new" , "courier" , monospace;"}\
[    -v /var/run/docker.sock:/var/run/docker.sock
\\]{style="font-family: "courier new" , "courier" , monospace;"}\
[   
Jenkinsci/blueocean]{style="font-family: "courier new" , "courier" , monospace;"}\
\
Jenkins instance with Blue Ocean plugin is installed.\
\
Let's start from zero:\

-   Get
    [bitwise-jenkins/jhipster-sample-app](https://github.com/jhipster/jhipster-sample-app) and
    use that as our sample app we will be building a deployment pipeline
    for. 
-   Tools we will be using: Maven, Node / Gulp, Gatling, packaged as a
    Docker container

Plan the pipeline. What do we need?\

-   We need to build the product, the backend in Java.
-   We need to test the product. This means having developers run their
    unit and integration tests, performance engineers running
    performance tests, and front-end ui tests run.
-   We will also be doing some Static Analysis, looking at code coverage
    or making sure the formatting is correct
-   Then, once everything is fine, we will do some deployment.

**[\
]{.underline}[Blue Ocean Pipeline Editor]{.underline}**\
\
Let's say we have a basic Jenkins editor...\
\
Is Blue Ocean a replacement for Jenkins? No. It isn't. It is just a
Plugin that sits on top of the Jenkins server. Installing the plugin
gives you an "Enter Blue Ocean" category.\

-   Where is your source? Choose Git or GitHub, and the code repository.
-   You can create a new pipeline, then select through the UI the
    hipster-sample-app

So, the choices we made were: git-plugin,  jhipster-sample-app,
JS-Nightwatch.js (for Selenium WebDriver GUI testing on Node.js and
JavaScript based front-ends\_\
\

-   More on the
    [git-plugin](https://wiki.jenkins-ci.org/display/JENKINS/Git+Plugin)

\
It looks at branches to see if there is a Jenkins pipeline. Is there
none? It will create a Jenkins pipeline in the repo.\
\

-   You can name stages, such as Build, Backend, Frontend, Static
    Analysis, Deployment. This will create empty stages for you that you
    can build off of.
-   You can build steps off of the basic placeholders.

\
Example: Backend can have a process running in parallel: Let\'s simulate
unit tests running, by echoing the text, \"Unit Test\".\

-   Unit Test: "echo Unit"
-   Performance: Add a shell script to run; "echo Performance"

You can save the pipeline as code, committing it to master, which will
save directly to the bitwise-jenkins / jhipster-sample-app and start a
run from that branch.\
\
\

-   If you look at the embedded Terminal, in General SCM, you can see
    that it is cloning the remote Git repository. Fetching the upstream
    changes, making the configuration changes.
-   It then deployed. We can click on stages to pinpoint exactly the log
    file that dealt with that stage.

\
**[Filling out the Build stage:]{.underline}**\
Don't reinvent your build system in Jenkins Pipeline. We can use it to
perform a build artifact.\
\
In his example, Liam Newman is using Maven.\
\
Each segment in the deployment pipeline is captured as a shell script,
such as "deploy.sh". How that shell script is to executed, with any
preconditions is captured in a Groovy file, such as deploy-stage.groovy.
It is creating distinct abstractions for each stage of the build
process.\
\
Yes, you could put it in one long file. But what happens if something in
the deploy shell script changes? You would be fiddling with every other
stage. Mess one part up, you would mess up it all.\
[\
]{style="font-family: "courier new" , "courier" , monospace;"}[pipeline
{]{style="font-family: "courier new" , "courier" , monospace;"}\
[   agent
{]{style="font-family: "courier new" , "courier" , monospace;"}\
[      docker
{]{style="font-family: "courier new" , "courier" , monospace;"}\
[          image
'maven:3-alpine']{style="font-family: "courier new" , "courier" , monospace;"}\
[          args '-v
/root/.m2:/root/.m2']{style="font-family: "courier new" , "courier" , monospace;"}\
[       
}]{style="font-family: "courier new" , "courier" , monospace;"}\
[    }]{style="font-family: "courier new" , "courier" , monospace;"}\
[\
]{style="font-family: "courier new" , "courier" , monospace;"}[pipeline
{]{style="font-family: "courier new" , "courier" , monospace;"}\
[   agent
any]{style="font-family: "courier new" , "courier" , monospace;"}\
[   stages
{]{style="font-family: "courier new" , "courier" , monospace;"}\
[      stage('Build')
{]{style="font-family: "courier new" , "courier" , monospace;"}\
[         steps
{]{style="font-family: "courier new" , "courier" , monospace;"}\
[            sh
'mvn']{style="font-family: "courier new" , "courier" , monospace;"}\
[       }]{style="font-family: "courier new" , "courier" , monospace;"}\
[     }]{style="font-family: "courier new" , "courier" , monospace;"}\
[   }]{style="font-family: "courier new" , "courier" , monospace;"}\
[}]{style="font-family: "courier new" , "courier" , monospace;"}\
\
This assumes you are using a Linux like environment using a bash shell,
which is fine, but you may want to make sure that your build system is
stable.\
\
Adding an "agent directive" to his build stage:\
\
[stage('Build')
{]{style="font-family: "courier new" , "courier" , monospace;"}\
[    agent
{]{style="font-family: "courier new" , "courier" , monospace;"}\
[       docker
{]{style="font-family: "courier new" , "courier" , monospace;"}\
[            image
'maven:3-alpine']{style="font-family: "courier new" , "courier" , monospace;"}\
[            args '-v
/root/.m2:/root/.m2']{style="font-family: "courier new" , "courier" , monospace;"}\
[       
}]{style="font-family: "courier new" , "courier" , monospace;"}\
[     }]{style="font-family: "courier new" , "courier" , monospace;"}\
\
This will pull down a container for a Maven 3 type Docker image.\
\
Dependencies will be cached in the M2 directory. Downloading takes quite
a while. Caching will save time.\
\
[stage('Build')
{]{style="font-family: "courier new" , "courier" , monospace;"}\
[  /\* ..
\*/]{style="font-family: "courier new" , "courier" , monospace;"}\
[  steps
{]{style="font-family: "courier new" , "courier" , monospace;"}\
[     sh '.mvnw -B clean
package']{style="font-family: "courier new" , "courier" , monospace;"}\
[     stash name: 'war', includes:
'target']{style="font-family: "courier new" , "courier" , monospace;"}\
[   }]{style="font-family: "courier new" , "courier" , monospace;"}\
[ }]{style="font-family: "courier new" , "courier" , monospace;"}\
\
Here, we wlll not run the entire build, we will just create a package, a
WAR file (web archive). We then use Stash to keep the artifact, a \*.war
file, for the duration.\
\
He was able to show, using his Atom editor, and his shell, to do a:\
\
\$ git fetch ---all\
Fetching jhipster\
Fetching origin\
Fetching bitwiseman\
\
.... pulled down the latest phase of changes.\
\
If we open the Jenkinsfile, we can see all we created in the UI stores
as code.\
\
We can commit the changes, push them up to GitHub, and tell it to run
the changes on Blue Ocean.\
\
Test Stage:\
\
[pipeline
{]{style="font-family: "courier new" , "courier" , monospace;"}\
[    agent
any]{style="font-family: "courier new" , "courier" , monospace;"}\
[    stages
{]{style="font-family: "courier new" , "courier" , monospace;"}\
[       stage('Backend Unit Test')
{]{style="font-family: "courier new" , "courier" , monospace;"}\
[          steps
{]{style="font-family: "courier new" , "courier" , monospace;"}\
[              sh './mvnw -B
test']{style="font-family: "courier new" , "courier" , monospace;"}\
[           
}]{style="font-family: "courier new" , "courier" , monospace;"}\
[       
 }]{style="font-family: "courier new" , "courier" , monospace;"}\
[    }]{style="font-family: "courier new" , "courier" , monospace;"}\
[}]{style="font-family: "courier new" , "courier" , monospace;"}\
\
Add the same Docker stage:\
\
[stage('Backend Unit Tests')
{]{style="font-family: "courier new" , "courier" , monospace;"}\
[    agent
{]{style="font-family: "courier new" , "courier" , monospace;"}\
[       docker
{]{style="font-family: "courier new" , "courier" , monospace;"}\
[            image
'maven:3-alpine']{style="font-family: "courier new" , "courier" , monospace;"}\
[            args '-v
/root/.m2:/root/.m2']{style="font-family: "courier new" , "courier" , monospace;"}\
[       
}]{style="font-family: "courier new" , "courier" , monospace;"}\
[     }]{style="font-family: "courier new" , "courier" , monospace;"}\
\
\
We are going to add tests:\
\
[stage('Backend Unit Tests')
{]{style="font-family: "courier new" , "courier" , monospace;"}\
[  /\* ..
\*/]{style="font-family: "courier new" , "courier" , monospace;"}\
[  steps
{]{style="font-family: "courier new" , "courier" , monospace;"}\
[     unstash
'war']{style="font-family: "courier new" , "courier" , monospace;"}\
[     sh './mvnw -B
test']{style="font-family: "courier new" , "courier" , monospace;"}\
[     junit
'\*\*/surefire-reports/\*\*/\*.xml']{style="font-family: "courier new" , "courier" , monospace;"}\
[   }]{style="font-family: "courier new" , "courier" , monospace;"}\
[ }]{style="font-family: "courier new" , "courier" , monospace;"}\
\
The JUNit step publishes the JUnit results so we can look at them in
Jenkins.\
\
stage('Backend Performance Test') {\
   steps {\
      unstash 'war'\
      sh './mvnw -B gatling:execute'\
\
}\
\
Gatling, like many performance tests does not produce JUnit output, so
we can't publish it to Jenkins.\
\
Lastly, we are going to run it in parallel:\
\
[stage('Backend')
{]{style="font-family: "courier new" , "courier" , monospace;"}\
[   steps
{]{style="font-family: "courier new" , "courier" , monospace;"}\
[       
parallel(]{style="font-family: "courier new" , "courier" , monospace;"}\
[           'Unit' :
{]{style="font-family: "courier new" , "courier" , monospace;"}\
[               unstash
'war']{style="font-family: "courier new" , "courier" , monospace;"}\
[               sh '.mvnw -B
test']{style="font-family: "courier new" , "courier" , monospace;"}\
[               junit
'\*\*/surefire-reports/\*\*/\*.xml']{style="font-family: "courier new" , "courier" , monospace;"}\
[           
},]{style="font-family: "courier new" , "courier" , monospace;"}\
[            'Performance; :
{]{style="font-family: "courier new" , "courier" , monospace;"}\
[               unstash
'war']{style="font-family: "courier new" , "courier" , monospace;"}\
[               sh './mvnw -B
gatling:execute']{style="font-family: "courier new" , "courier" , monospace;"}\
[           
})]{style="font-family: "courier new" , "courier" , monospace;"}\
[       
 }]{style="font-family: "courier new" , "courier" , monospace;"}\
[   }]{style="font-family: "courier new" , "courier" , monospace;"}\
\
Note: Bit by bit, we are creating the build process: Bash Shell scripts
to run matched with Groovy scripts that configure them:\
\

-   backend-test-stage.groovy
-   build-stage.groovy
-   deploy-stage.groovy
-   deploy.sh
-   docker.sh

\
\
As Liam Newman demoed, after each stage was created, you could commit
and push first the build stage, then the test stage, then every other
stage to the source control.\
\
Liam would create first the build stage. Commit the changes. Run the
tests. Make sure they still pass. Create the test stage. Run the tests,
make sure they still pass.\
\
He mentioned during his demo that normally, you can set up Jenkins to
act as a listener, to automatically kick off the pre-written unit tests
whenever code is changes, but he was running the demo behind a firewall
and didn't have time to set up the configurations.\
\
For the front end tests, he was using Node, not maven,\
\
[stage('Frontend
Test')]{style="font-family: "courier new" , "courier" , monospace;"}\
[   agent { docker 'node:alpine'
}]{style="font-family: "courier new" , "courier" , monospace;"}\
[   steps
{]{style="font-family: "courier new" , "courier" , monospace;"}\
[      sh 'node
---version']{style="font-family: "courier new" , "courier" , monospace;"}\
[      sh 'yarn
install']{style="font-family: "courier new" , "courier" , monospace;"}\
[      sh 'yarn global add
gulp-cli']{style="font-family: "courier new" , "courier" , monospace;"}\
[      sh 'gulp
test']{style="font-family: "courier new" , "courier" , monospace;"}\
[    }]{style="font-family: "courier new" , "courier" , monospace;"}\
[}]{style="font-family: "courier new" , "courier" , monospace;"}\
\
This will set up a node environment, then the tests will be executed in
that environment.\
\

-   The Analyze stage, we would:
-   Run static analysis
-   Code coverage checks
-   Quality scanning with FindBugs, PMD
-   Creating a Sonarqube object

\
\
See
[jenkins.io/blog/2017/04/18/continuousdelivery-devops-sonarqube/](http://jenkins.io/blog/2017/04/18/continuousdelivery-devops-sonarqube/)\
\
**[Deploy Stage:]{.underline}**\
\

-   Don't reinvent yoru deployment system in Jenkins

\
**[\
]{.underline}[Deployment may mean:]{.underline}**\
\

-   Deploying to AWS / Azure
-   Deploying to a physical datacenter
-   uploading to an app store
-   uploading to an internal artifact server

\
\
With Pipeline, you can follow your usual pull request and code review
process.\
\
Now, that is from zero to continuous delivery.\
\
Other considerations:\
\
Jenkins Pipeline can be used for sending feedback to the team via email,
messages via HipChat, Slack, or others.\
\
\

-   Need to know more about sending out Notifications? See
    [jenkins.io/node/tags/notifications/](http://jenkins.io/node/tags/notifications/)

\
**[Want to use Continuous Integration, allowing a Release Engineer\'s
Input?]{.underline}**\
If you want, you can even add into your pipeline a step where a release
engineer has to check everything is all right before kicking off the
last deploy.sh script.\
\
You can add input messages, and wait for an okay from a human being.\
\
You can do things such as:\
\

-   Deploy to staging automatically, but wait to get the okay from a
    release engineer to deploy to production.
-   You can capture that into an OK button.

\
\
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
