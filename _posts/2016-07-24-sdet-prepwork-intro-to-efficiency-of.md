\-\-- layout: post title: \'SDET Prepwork: What is an SDET? Intro to the
Efficiency of Sorting Algorithms: Insertion sort vs Merge sort\' date:
\'2016-07-24T14:02:00.001-04:00\' author: T.J. Maher tags: - SDET -
algorithms modified\_time: \'2016-07-26T17:58:13.339-04:00\' thumbnail:
https://4.bp.blogspot.com/-dFqqFZqjFuI/V5S9Z\_vKjmI/AAAAAAAALUQ/\_rXWyVrJt9wTx7cuqHU2DdgOMRopvi2cwCLcB/s72-c/khan.png
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-212560208572396876
blogger\_orig\_url:
http://www.tjmaher.com/2016/07/sdet-prepwork-intro-to-efficiency-of.html
\-\-- *This blog post is part of a series as I research how to move from
Automation Development to being a [Software Developer in
Test](http://www.tjmaher.com/search/label/SDET). These next few posts
will deal with
[algorithms](http://www.tjmaher.com/search/label/algorithms).*\
\

What is the Difference between Automation Developers and Software Developers in Test?
-------------------------------------------------------------------------------------

###  Automation Developers Use Code to Create Tests

\
Have you ever had to perform browser testing on your web application
just before a release to production, taking a week or so to do
regression testing, making sure that after the new functionality was
added that all of the old stuff still worked? And you have ended up
staring at the same twenty pages in a variety of Internet Explorer
browsers, Firefox, and Chrome, and attempted to make sure the elements
on the page are there? That you can still log in? That you can still
perform the same actions in all of the browsers? Don\'t you wish that
someone could just write a computer program to do this testing for you?\
**\
*Create Browser User Interface Tests***: When it comes to browser
testing, automation developers solve this problem, by pairing Selenium
[WebDriver](http://www.tjmaher.com/search/label/WebDriver) with a
computer language such as Java to write clean, readable test code that
uses basic object-oriented design principles such as:\

-   Factoring out any commonalities in your tests into separate methods
    so it is easier to maintain.  
-   Grouping the web elements and methods that interact with the web
    elements on a page into [Page
    Objects](http://www.tjmaher.com/search/label/Page%20Object)
-   Creating wrappers for Selenium objects to provide better diagnostics
    when something goes wrong\... Or using the [Page
    Factory](http://www.tjmaher.com/search/label/Page%20Object) to lazy
    load the web elements initializing them just before you need them.
-   How to use
    [RemoteWebDriver](http://www.tjmaher.com/search/label/RemoteWebDriver)
    and implement different browsers into your testing with [Selenium
    Grid](http://www.tjmaher.com/search/label/SeleniumGrid), Browser
    Stack or [Sauce
    Labs](http://www.tjmaher.com/search/label/Sauce%20Labs).

***Write Performance Tests***: An Automation Developer deals with Stress
Testing, Performance Testing and Load Testing using tools such as
[Apache JMeter](http://jmeter.apache.org/).\

<div>

\
**Script Database Tests:** Want to make sure that the data entered in
the browser user interface is stored correctly in the database? Use
libraries in your favorite programming language that handle opening
connections to the database, and SQL scripts that query that the data
was placed in the correct table.\
\
As an Automation Developer, you might be working with Arrays, Lists, and
ArrayList to assemble and store data, *for* loops and *foreach* loops,
but their focus is on creating the tests.\
\

### **Software Developers in Test Use Code to Write Test Frameworks**

\
\
Software developers in Test take what the Automation Developer does one
step further.\
\
From the Microsoft Developer article, [*What is an
SDET? *](https://blogs.msdn.microsoft.com/seliot/2010/04/18/what-is-an-sdet/)\
\

> \"The SDET role can be compared with that of the SDE (Software
> Development Engineer) role. The latter is what most people would think
> of when they say \'Developer\'. An SDE (depending on level and
> seniority) will Architect, Design, and Implement software systems that
> will be used by the target end users. SDEs are responsible for the
> quality of their software and will implement testing (often unit
> tests), as well as seek reviews for both their designs and their code.
> SDEs will often have influence on the software processes employed, and
> be responsible for following best practices in software development.\
> \
> \"The SDET is also a developer. The SDET must have knowledge of what
> represents good software design. The SDET must be able to create high
> quality, maintainable \[\...\] code. The code generally created by the
> SDET however are for automated test cases and the frameworks to
> execute and report them. An SDET's knowledge of software design is
> often focused on testability, robustness, and performance, and they
> usually play a contributory or reviewer role in the creation of
> designs for production software. An SDETs skill set will often include
> more experience in software processes and how to test software.
> Testing software is generally  done so as to assess and mitigate risk,
> and SDETs need to be expert in this. So an SDET can be summarized as
> having development skills and software quality skills. While SDEs
> should have this also, SDEs balance more towards the former while
> SDETs balance more towards the latter\".

\
\
From talking to other Software Developers \-- both in Test and in
general \-- I\'ve gathered that if you want to make the switch, you
really have to start thinking more about performance.\
\
They need to focus on:\

-   Figuring out how to store data more efficiently in ***data
    structures*** such as stacks, queues, linked lists, hash maps,
    heaps, and binary search trees.
-   Learning what a linear sort is and why it is inefficient, and
    figuring out different ways to search through data studying
    known ***search
    algorithms*** and ***sorting*** ***algorithms ***such as binary
    search, quicksort or mergesort. 
-   Understanding where you want to focus on: If memory is at a premium,
    you want your solution to use the minimum amount of space possible.
    If time the major factor, you want to make your solution as quick as
    possible. Your solution should take into consideration these *space
    complexities* or *time complexities*. 
-   Comparing and contrasting how fast your solution is using Big-O
    notation, and figuring out if your solution you are using will
    scale.

[]{#more} Worrying About Software Performance? Study Data Structures and Algorithms
-----------------------------------------------------------------------------------

\
To help me along, I decided to dive off the deep end this weekend with
Thomas M. Cormen\'s *Introduction to Algorithms*, Third Edition (2009),
and to help stick what I am reading into my mind, I decided to blog
about it. I\'ll try to paraphrase the math the best I can, though it has
been decades since my courses in [Discrete
Mathematics](https://en.wikipedia.org/wiki/Discrete_mathematics).\
\
This isn\'t the first time I have encountered search algorithms: I was a
Computer Science major in the early 1990s, and finished my Masters of
Software Engineering in 2008.\
\
\... I\'m still a bit of a greenhorn, though, when it comes to
actually *being* Software Engineering\... up until a few years ago, my
work was in Software Testing and Quality Assurance. If you happen to
actually be a software engineer, and I say something wacky, or
completely untrue out of ignorance, *please* feel free to correct me in
the comments section on the bottom of this page.\
\
A ***data structure*** is a way to store and organize data so it easier
accessing, modifying and using it. I think of
a ***search*** or ***sorting algorithm*** like a tried-and-true recipe
others can use to figure out how to locate and organize data. Once you
understand the recipes others came up with, then you can come up with
little tweaks here and there, building your own algorithms.\
\

Measuring Efficiency of Algorithms
----------------------------------

\
*Introduction to Algorithms,* Third Edition* *is not an easy read. For
instance, allow me to take an introductory problem as shown on *Chapter
1: The Role of Algorithms in Computing*, pages 12 and 13, in a paragraph
called \"Efficiency\" and attempt to walk you through solving this
problem:\

-   Imagine two computer: a fast computer running a very slow sorting
    algorithm such as ***insertion sort***, and a slow computer running
    a fast sorting algorithm such as ***mergesort***. How long would it
    take to sort 10 million numbers? *What difference would the better
    algorithm make?* 

\
First, let\'s see how long these algorithms takes to sort an unknown
amount of numbers, we\'ll call *\"n\"*.\
\

### The Inefficiency of Insertion Sort

The slow sorting algorithm ***insertion sort***, the book mentions, to
sort *n* numbers, it takes n^2^ (or *n \* n* ) long to sort through
numbers. To sort two numbers it is *two \* two = four*. It uses
exponents, raising each number to the second power:\

-   If *n = 2*, sorting two numbers, the time it takes is 2^2^: 4
-   If *n = 3*, sorting three numbers, the time it takes is 3^2^: 9
-   If *n = 10*, 10^2^: 100
-   If *n = 20*, 20^2^: 400

\

### The Efficiency of Merge Sort

\
The faster sorting algorithm ***merge sort***, the book mentions, to
sort *n* numbers, it takes n log n to search.\
\
Logarithms are sort of like the inverse of exponents.\

-   If *n* = 8, the log *n* is 3, since 2^3^ *(2\*2\*2)*: 8.
-   If *n* = 16, the log *n* is 4, since 2^4^: *(2\*2\*2\*2)*: 16.
-   If *n* = 32, the log *n* is 5, since 2^5^: 32.
-   If *n* = 64, the log *n* is 6, since 2^6^: 64.
-   If *n* = 128, the log *n* is 7, since 2^7^: 128.
-   If *n* = a thousand, the log *n* is roughly 10, since 2^10^: 1024.
-   If *n* = a million, log *n* is roughly 20 since 2^20^ is roughly a
    million.

\
You can plot the efficiency of the two algorithms on a graph, like so,
where *n* can be the amount of numbers that are being sorted. Plot on
the *x-axis* how many numbers you are sorting. The *y-axis* will plot
the factor of time:\

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://4.bp.blogspot.com/-dFqqFZqjFuI/V5S9Z_vKjmI/AAAAAAAALUQ/_rXWyVrJt9wTx7cuqHU2DdgOMRopvi2cwCLcB/s400/khan.png){width="400" height="247"}](https://4.bp.blogspot.com/-dFqqFZqjFuI/V5S9Z_vKjmI/AAAAAAAALUQ/_rXWyVrJt9wTx7cuqHU2DdgOMRopvi2cwCLcB/s1600/khan.png)
                                                          *From Khan Academy, [Algorithm comparison](https://www.khanacademy.org/computing/computer-science/algorithms/merge-sort/a/divide-and-conquer-algorithms)*
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

If you are using an insertion sort, you can see that with small numbers,
the insertion sort is quicker. But if you are trying to sort, say, ten
million numbers, the better algorithm, mergesort will win out.\
\
Let\'s use the example in the book, and say we are using two different
computers, a fast one using the slow insertion sort and a slow computer
using mergesort. Which would win sorting ten million numbers?\
\
Sure, ten million numbers seems like a lot, but the book mentions if
each number is only stored as an 8 byte integer, then the amount of
space to store those numbers would only take up 80 MB (megabytes) in RAM
when doing calculations.\
\
Getting down to specifics\...\

-   Fast computer: Executes 10 billion instructions per second. 
-   Slow computer: Executes 10 million instructions per second.

\
In case you are not familiar with the powers of ten:\

-   Ten is 10^1^
-   A hundred is 10^2^, or *100*
-   A thousand is 10^3^, or *1000*
-   Ten thousand is 10^4^, or *10,000*
-   A hundred thousand is 10^5^, or *100,000*
-   A million is 10^6^, or *1,000,000*
-   Ten million is 10^7^, or *10,000,000*
-   Ten billion is 10^10^, or *10,000,000,000*

We are sorting 10^7^ numbers on a fast computer/ slow algorithm that
runs 10^10^ instructions a second and a slow computer / faster algorithm
that runs 10^7^ instructions a second.\
\
Let\'s complicate the issue further\... why? \... because it will make
the math easier with the two different algorithms:\

-   On the fast computer, an expert programmer writes the slow
    ***insertion sort*** in the machine language, so that it only takes
    2n^2^ instructions to sort *n* numbers.
-   On the slow computer, an average programmer uses a programming
    language and compiler that takes 50 log *n* instructions to sort *n*
    numbers for the faster ***mergesort***.  

Calculating Runtime of Algorithms
---------------------------------

### Slow Algorithm / Fast Computer

Given that:\

-   Insertion sort has an poor efficiency of only n^2^, where n is 10^7^
    (an array of ten million numbers)
-   The insertion sort is implemented at the fast rate of 2n^2^ to sort
    n numbers, where n is 10^7^.
-   We are dividing everything by 10^10^ (10 billion) instructions per
    second.

This gives us: 2 \* (10^7^)^2^ instructions divided by 10^10^
instructions per second.\
\
With Exponent Math, lets calculate (10^7^)^2^:\

-   Since *7 \* 2 = 14*, (10^7^)^2^ gives us 10^14^.
-   This gives us 2 \* (10^14^) instructions divided by
    10^10^ instructions per second.

\
Now let\'s figure out how many seconds this operation will actually
take:\

-   Take 10^14^ and divide it by 10^10^
-   Since *14 minus 10* is 4, then 10^14^ divided by 10^10^ is 10^4^
-   We are left with 2 \* 10^4^: 20,000 seconds
-   Since there is 60 seconds in a minute and 60 minutes in an hour,
    that means there is 3600 seconds in an hour.
-   Dividing 20,000 minus 3600 is roughly 5.5. 

To sort ten million numbers, it is going to take\...\
\... even on the extremely fast computer \...\
\... using a very quick method to implement the very slow algorithm\...\
\
[\... **Five And A Half Hours!**]{style="font-size: medium;"}\
\
Um\... Wow.\
\
Let\'s take a look at what is happening with the other computer\...\
\

### Fast Algorithm / Slow Computer

\
Given that:\

-   Merge sort has a better efficiency of *n* log *n*, where n is
    10^7^ (an array of ten million numbers)
-   The merge sort in this example is implemented at the slower rate of
    50*n* log *n* to sort *n* numbers, where *n* is 10^7^.
-   We are dividing everything on the slower computer by 10^7^ (one
    million) instructions per second.

This gives us: 50 \* 10^7^ log 10^7^ instructions divided by
10^7^ instructions per second.\
\
According to the book, this equals approximately 1163 seconds.\

-   There is 60 seconds in a minute.
-   Dividing 1163 by 60 is 19.38 minutes

To sort ten million numbers, it is going to take\...\
\... on the slow computer \...\
\... using a slow method to implement the faster algorithm\...\
\
**A bit less than twenty minutes.**\
**\
**\

Where We Go From Here
---------------------

\
Over the next few weeks, we will be looking at topics such as:\

-   Big-O Notation and more about Logarithms
-   Data structures such as trees and hashmaps
-   More searching and sorting algorithms such as *mergesort*,
    *quicksort*, and other algorithms, and how to implement them in
    Java.

\
Or, if you want to do some independent study, you can jump to [Eric
Drowell](https://twitter.com/ericdrowell) and his awesome Big O Cheat
Sheet at <http://bigocheatsheet.com/>\
\

Big-O Complexity Chart {#chartTitle style="color: #444444; display: inline-block; font-family: "Helvetica Neue", Helvetica, Arial, sans-serif; font-size: 24px;"}
----------------------

::: {style="font-family: "Helvetica Neue", Helvetica, Arial, sans-serif; line-height: 18.4px; text-align: center;"}
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   `Excellent`{.green style="background-color: #53d000; border-radius: 2px; border: 1px solid rgb(40, 101, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}  `Good`{.yellow-green style="background-color: #c8ea00; border-radius: 2px; border: 1px solid rgb(40, 101, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}   `Fair`{.yellow style="background-color: yellow; border-radius: 2px; border: 1px solid rgb(111, 110, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}   `Bad`{.orange style="background-color: #ffc543; border-radius: 2px; border: 1px solid rgb(178, 0, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}   `Horrible`{.red style="background-color: #ff8989; border-radius: 2px; border: 1px solid rgb(178, 0, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
:::

\

<div>

Array Sorting Algorithms {#sorting style="color: #444444; font-family: "Helvetica Neue", Helvetica, Arial, sans-serif; font-size: 24px; line-height: 24px; margin-top: 30px;"}
------------------------

Algorithm

</div>

</div>

Time Complexity

Space Complexity

Best

Average

Worst

Worst

[Quicksort](http://en.wikipedia.org/wiki/Quicksort)

`O(n log(n))`{.orange
style="background-color: #ffc543; border-radius: 2px; border: 1px solid rgb(178, 0, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

`O(n log(n))`{.orange
style="background-color: #ffc543; border-radius: 2px; border: 1px solid rgb(178, 0, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

`O(n^2)`{.red
style="background-color: #ff8989; border-radius: 2px; border: 1px solid rgb(178, 0, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

`O(log(n))`{.yellow-green
style="background-color: #c8ea00; border-radius: 2px; border: 1px solid rgb(40, 101, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

[Mergesort](http://en.wikipedia.org/wiki/Merge_sort)

`O(n log(n))`{.orange
style="background-color: #ffc543; border-radius: 2px; border: 1px solid rgb(178, 0, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

`O(n log(n))`{.orange
style="background-color: #ffc543; border-radius: 2px; border: 1px solid rgb(178, 0, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

`O(n log(n))`{.orange
style="background-color: #ffc543; border-radius: 2px; border: 1px solid rgb(178, 0, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

`O(n)`{.yellow
style="background-color: yellow; border-radius: 2px; border: 1px solid rgb(111, 110, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

[Timsort](http://en.wikipedia.org/wiki/Timsort)

`O(n)`{.yellow
style="background-color: yellow; border-radius: 2px; border: 1px solid rgb(111, 110, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

`O(n log(n))`{.orange
style="background-color: #ffc543; border-radius: 2px; border: 1px solid rgb(178, 0, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

`O(n log(n))`{.orange
style="background-color: #ffc543; border-radius: 2px; border: 1px solid rgb(178, 0, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

`O(n)`{.yellow
style="background-color: yellow; border-radius: 2px; border: 1px solid rgb(111, 110, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

[Heapsort](http://en.wikipedia.org/wiki/Heapsort)

`O(n log(n))`{.orange
style="background-color: #ffc543; border-radius: 2px; border: 1px solid rgb(178, 0, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

`O(n log(n))`{.orange
style="background-color: #ffc543; border-radius: 2px; border: 1px solid rgb(178, 0, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

`O(n log(n))`{.orange
style="background-color: #ffc543; border-radius: 2px; border: 1px solid rgb(178, 0, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

`O(1)`{.green
style="background-color: #53d000; border-radius: 2px; border: 1px solid rgb(40, 101, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

[Bubble Sort](http://en.wikipedia.org/wiki/Bubble_sort)

`O(n)`{.yellow
style="background-color: yellow; border-radius: 2px; border: 1px solid rgb(111, 110, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

`O(n^2)`{.red
style="background-color: #ff8989; border-radius: 2px; border: 1px solid rgb(178, 0, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

`O(n^2)`{.red
style="background-color: #ff8989; border-radius: 2px; border: 1px solid rgb(178, 0, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

`O(1)`{.green
style="background-color: #53d000; border-radius: 2px; border: 1px solid rgb(40, 101, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

[Insertion Sort](http://en.wikipedia.org/wiki/Insertion_sort)

`O(n)`{.yellow
style="background-color: yellow; border-radius: 2px; border: 1px solid rgb(111, 110, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

`O(n^2)`{.red
style="background-color: #ff8989; border-radius: 2px; border: 1px solid rgb(178, 0, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

`O(n^2)`{.red
style="background-color: #ff8989; border-radius: 2px; border: 1px solid rgb(178, 0, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

`O(1)`{.green
style="background-color: #53d000; border-radius: 2px; border: 1px solid rgb(40, 101, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

[Selection Sort](http://en.wikipedia.org/wiki/Selection_sort)

`O(n^2)`{.red
style="background-color: #ff8989; border-radius: 2px; border: 1px solid rgb(178, 0, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

`O(n^2)`{.red
style="background-color: #ff8989; border-radius: 2px; border: 1px solid rgb(178, 0, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

`O(n^2)`{.red
style="background-color: #ff8989; border-radius: 2px; border: 1px solid rgb(178, 0, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

`O(1)`{.green
style="background-color: #53d000; border-radius: 2px; border: 1px solid rgb(40, 101, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

[Tree Sort](https://en.wikipedia.org/wiki/Tree_sort)

`O(n log(n))`{.orange
style="background-color: #ffc543; border-radius: 2px; border: 1px solid rgb(178, 0, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

`O(n log(n))`{.orange
style="background-color: #ffc543; border-radius: 2px; border: 1px solid rgb(178, 0, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

`O(n^2)`{.red
style="background-color: #ff8989; border-radius: 2px; border: 1px solid rgb(178, 0, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

`O(n)`{.yellow
style="background-color: yellow; border-radius: 2px; border: 1px solid rgb(111, 110, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

[Shell Sort](http://en.wikipedia.org/wiki/Shellsort)

`O(n log(n))`{.orange
style="background-color: #ffc543; border-radius: 2px; border: 1px solid rgb(178, 0, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

`O(n(log(n))^2)`{.red
style="background-color: #ff8989; border-radius: 2px; border: 1px solid rgb(178, 0, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

`O(n(log(n))^2)`{.red
style="background-color: #ff8989; border-radius: 2px; border: 1px solid rgb(178, 0, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

`O(1)`{.green
style="background-color: #53d000; border-radius: 2px; border: 1px solid rgb(40, 101, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

[Bucket
Sort](http://en.wikipedia.org/wiki/Bucket_sort "Only for integers. k is a number of buckets")

`O(n+k)`{.green
style="background-color: #53d000; border-radius: 2px; border: 1px solid rgb(40, 101, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

`O(n+k)`{.green
style="background-color: #53d000; border-radius: 2px; border: 1px solid rgb(40, 101, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

`O(n^2)`{.red
style="background-color: #ff8989; border-radius: 2px; border: 1px solid rgb(178, 0, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

`O(n)`{.yellow
style="background-color: yellow; border-radius: 2px; border: 1px solid rgb(111, 110, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

[Radix
Sort](http://en.wikipedia.org/wiki/Radix_sort "Constant number of digits 'k'")

`O(nk)`{.green
style="background-color: #53d000; border-radius: 2px; border: 1px solid rgb(40, 101, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

`O(nk)`{.green
style="background-color: #53d000; border-radius: 2px; border: 1px solid rgb(40, 101, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

`O(nk)`{.green
style="background-color: #53d000; border-radius: 2px; border: 1px solid rgb(40, 101, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

`O(n+k)`{.yellow
style="background-color: yellow; border-radius: 2px; border: 1px solid rgb(111, 110, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

[Counting
Sort](https://en.wikipedia.org/wiki/Counting_sort "Difference between maximum and minimum number 'k'")

`O(n+k)`{.green
style="background-color: #53d000; border-radius: 2px; border: 1px solid rgb(40, 101, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

`O(n+k)`{.green
style="background-color: #53d000; border-radius: 2px; border: 1px solid rgb(40, 101, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

`O(n+k)`{.green
style="background-color: #53d000; border-radius: 2px; border: 1px solid rgb(40, 101, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

`O(k)`{.yellow
style="background-color: yellow; border-radius: 2px; border: 1px solid rgb(111, 110, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

[Cubesort](https://en.wikipedia.org/wiki/Cubesort)

`O(n)`{.yellow
style="background-color: yellow; border-radius: 2px; border: 1px solid rgb(111, 110, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

`O(n log(n))`{.orange
style="background-color: #ffc543; border-radius: 2px; border: 1px solid rgb(178, 0, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

`O(n log(n))`{.orange
style="background-color: #ffc543; border-radius: 2px; border: 1px solid rgb(178, 0, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

`O(n)`{.yellow
style="background-color: yellow; border-radius: 2px; border: 1px solid rgb(111, 110, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}

***The [Big O Cheatsheet](http://bigocheatsheet.com/) By Eric
Drowell***\
\
\
\
Happy Testing!\
\
-T.J. Maher\
Sr. QA Engineer,\
Fitbit-Boston\
\
*// BSCS, MSE, and QA Engineer since Aug. 1996\
// Automation developer for \[ 1.5 \] years and still counting!\
// Check out Adventures in Automation and Like us
on [Facebook](https://www.facebook.com/AdventuresInAutomation/)!*
