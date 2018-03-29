\-\-- layout: post title: How to Clone a Repository in IntelliJ date:
\'2016-05-27T07:30:00.003-04:00\' author: T.J. Maher tags: - GIT -
IntelliJ modified\_time: \'2016-05-27T07:31:21.536-04:00\' thumbnail:
https://1.bp.blogspot.com/-3\_GN4F36QVM/V0ZLcDZn86I/AAAAAAAALC8/nOjic0Jo2gMFK3UL4OgrutiTHu0JyXnygCLcB/s72-c/InelliJ%2BHome%2BScreen.png
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-4682423241569292528
blogger\_orig\_url:
http://www.tjmaher.com/2016/05/how-to-clone-repository-in-intellij.html
\-\-- Want to fiddle around with any code that I have created on GitHub,
such as **RESTful Testing Using Stripe** at
<https://github.com/tjmaher/RESTful_Testing_Using_Stripe>?\
\
This is a walkthrough on how to clone a repository through IntelliJ, an
Integrated Development Environment (IDE) that I use for work.\
\

### [What is GitHub](http://www.howtogeek.com/180167/htg-explains-what-is-github-and-what-do-geeks-use-it-for/), from How-to Geek:

> *\"To understand GitHub, you must first have an understanding of Git.
> Git is an open-source version control system that was started by Linus
> Trovalds -- the same person who created Linux. Git is similar to other
> version control systems -- Subversion, CVS, and Mercurial to name a
> few.\
> *\
> []{#more}*\
> \"So, Git is a \'version control system,\' what's that mean? When
> developers are creating something (an application, for example), they
> are making constant changes to the code and releasing new versions, up
> to and after the first official (non-beta) release.\
> \
> \"Version control systems keep these revisions straight, and store the
> modifications in a central repository. This allows developers to
> easily collaborate, as they can download a new version of the
> software, make changes, and upload the newest revision. Every
> developer can see these new changes, download them, and contribute.\
> \
> \"Similarly, people who have nothing to do with the development of a
> project can still download the files and use them. Most Linux users
> should be familiar with this process, as using Git, Subversion, or
> some other similar method is pretty common for downloading needed
> files, especially in preparation for compiling a program from source
> code (a rather common practice for Linux geeks).\
> \
> \"In case you are wondering why Git is the preferred version control
> system of most developers, it has multiple advantages over the other
> systems available, including a more efficient way to store file
> changes and ensuring file integrity. If you're interested in knowing
> the details, check out this page to read a thorough explanation on how
> Git works.\
> \
> \"We've established that Git is a version control system, similar but
> better than the many alternatives available. So, what makes GitHub so
> special? Git is a command-line tool, but the center around which all
> things involving Git revolve -- effectively, the Hub, is GitHub.com,
> where developers can store their projects and network with likeminded
> people\".* - [\[ MORE
> \]](http://www.howtogeek.com/180167/htg-explains-what-is-github-and-what-do-geeks-use-it-for/)

### **Why clone a repository?**

> *When you create a repository on GitHub, it exists as a remote
> repository. You can clone your repository to create a local copy on
> your computer and sync between the two locations.\
> \
> This procedure assumes you have already created a repository on
> GitHub, or have an existing repository owned by someone else you\'d
> like to contribute to. -
> [GitHub](https://help.github.com/articles/cloning-a-repository/)*

\

### Step One: Get IntelliJ:

\
IntelliJ can be downloaded for free at <https://www.jetbrains.com/idea/>
\... The free Community Edition is absolutely wonderful! I do like the
integrated database functionality in IntelliJ Enterprise Edition which I
use at work.\
\

### Step Two: Start IntelliJ 

You should see the Home screen of IntelliJ\
\

::: {.separator style="clear: both; text-align: center;"}
[![](https://1.bp.blogspot.com/-3_GN4F36QVM/V0ZLcDZn86I/AAAAAAAALC8/nOjic0Jo2gMFK3UL4OgrutiTHu0JyXnygCLcB/s400/InelliJ%2BHome%2BScreen.png){width="400"
height="232"}](https://1.bp.blogspot.com/-3_GN4F36QVM/V0ZLcDZn86I/AAAAAAAALC8/nOjic0Jo2gMFK3UL4OgrutiTHu0JyXnygCLcB/s1600/InelliJ%2BHome%2BScreen.png)
:::

\

### Step Three: Checkout Version Control

\
On the Home Screen, select \"Check out from Version Control\" and log
into your GitHub account or sign up if you do not have one.\
\

::: {.separator style="clear: both; text-align: center;"}
[![](https://3.bp.blogspot.com/-akAecwzfAnQ/V0ZLjPH95TI/AAAAAAAALDA/1HIun22c4ukqvmyOnXP8jWfK744blt7hgCLcB/s400/IntelliJ%2BGithub.png){width="400"
height="233"}](https://3.bp.blogspot.com/-akAecwzfAnQ/V0ZLjPH95TI/AAAAAAAALDA/1HIun22c4ukqvmyOnXP8jWfK744blt7hgCLcB/s1600/IntelliJ%2BGithub.png)
:::

\
\... Note: You can also checkout anything you want to experiment with on
GitHub, CVS, Git, Mecurical, or Subversion.\
\

### Step Four: Clone Repository

\
Enter into the Clone Repository Window the following details, plus the
Git Repository URL. Go
to <https://github.com/tjmaher/RESTful_Testing_Using_Stripe> and press
the \"Clone or Download\" button to get the URL.\
\

-   **Git Repository URL**:
    https://github.com/tjmaher/RESTful\_Testing\_Using\_Stripe.git
-   **Parent Directory**: Select where you want to place it on your
    local computer, such as in your home directory. I like placing
    projects at C:\\Users\\tmaher\\code\\ on my Windows 10 machine at
    home.
-   **The Directory:** Name where you are installing the code:
    RESTful\_Testing\_Using\_Stripe

\

::: {.separator style="clear: both; text-align: center;"}
[![](https://2.bp.blogspot.com/-N7NvQ3wWXFA/V0ZNV0O6BcI/AAAAAAAALDQ/Z-s-wOX40OAu0-m86ipqqHwSFyQGVgo1QCLcB/s640/clone.png){width="640"
height="200"}](https://2.bp.blogspot.com/-N7NvQ3wWXFA/V0ZNV0O6BcI/AAAAAAAALDQ/Z-s-wOX40OAu0-m86ipqqHwSFyQGVgo1QCLcB/s1600/clone.png)
:::

\
\
Once you press \[ CLONE \] the code in the project will automatically
open.\
\

-   Want to know what is happening when cloning a Git repository? See
    [*Git-SCM*](https://git-scm.com/docs/git-clone).
-   Too much detail? See [*GitHub
    help*](https://help.github.com/articles/cloning-a-repository/).

\
\
Happy Testing!\
\
-T.J. Maher\
Sr. QA Engineer,\
Fitbit-Boston\
\
*// QA Engineer since Aug. 1996\
// Automation developer for \[ 1 \] year and still counting!*
