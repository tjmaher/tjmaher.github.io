\-\-- layout: post title: \'SDET Prepwork: What is Big O notation and
Logs? Comparing Growth Rate in Algorithms\' date:
\'2016-07-25T07:00:00.000-04:00\' author: T.J. Maher tags: - SDET -
algorithms modified\_time: \'2016-07-26T11:42:26.663-04:00\' thumbnail:
https://2.bp.blogspot.com/-HYYyglKgMGU/V5VLl0KLdRI/AAAAAAAALUo/SuxIvBWBhwo\_0CrLYGkXvscaZGQFNP\_zgCLcB/s72-c/growth.png
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-2546229986055248606
blogger\_orig\_url:
http://www.tjmaher.com/2016/07/sdet-prepwork-what-is-big-o-notation.html
\-\-- *This blog post is part of a series as I research how to move from
Automation Development to being a [Software Developer in
Test](http://www.tjmaher.com/search/label/SDET). These next few posts
will deal
with [algorithms](http://www.tjmaher.com/search/label/algorithms).*\
\
What is the difference? \... Well, the main thing is that as an
automated tester, I haven\'t needed to worry about Big-O notation and
sorting algorithms, such as the ones found on [Eric
Drowell](https://twitter.com/ericdrowell)\'s [Big-O Cheat
Sheet](http://bigocheatsheet.com/).\
\

Big-O Complexity Chart {#chartTitle style="color: #444444; display: inline-block; font-family: "Helvetica Neue", Helvetica, Arial, sans-serif; font-size: 24px; line-height: 24px;"}
----------------------

::: {style="font-family: "Helvetica Neue", Helvetica, Arial, sans-serif; line-height: 18.4px; text-align: center;"}
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   `Excellent`{.green style="background-color: #53d000; border-radius: 2px; border: 1px solid rgb(40, 101, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}  `Good`{.yellow-green style="background-color: #c8ea00; border-radius: 2px; border: 1px solid rgb(40, 101, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}   `Fair`{.yellow style="background-color: yellow; border-radius: 2px; border: 1px solid rgb(111, 110, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}   `Bad`{.orange style="background-color: #ffc543; border-radius: 2px; border: 1px solid rgb(178, 0, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}   `Horrible`{.red style="background-color: #ff8989; border-radius: 2px; border: 1px solid rgb(178, 0, 0); display: inline-block; font-family: Monaco, Menlo, Consolas, "Courier New", monospace; font-size: 12px; padding: 3px; width: 100px;"}
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
:::

Array Sorting Algorithms {#sorting style="color: #444444; font-family: "Helvetica Neue", Helvetica, Arial, sans-serif; font-size: 24px; line-height: 24px; margin-top: 30px;"}
------------------------

Algorithm

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

::: {style="text-align: center;"}
***The [Big O Cheatsheet](http://bigocheatsheet.com/) By Eric Drowell***
:::

\
\
In this blog post, we are going to be focusing on walking through the
sorting algorithms ***Insertion Sort***, ***Mergesort***, and
***Quicksort***, and implementing them in Java code.\
\
First things first, though\...\

 What is Big O Notation? 
-------------------------

Big O notation is how computer scientists compare and contrast the
efficiency of sorting and searching algorithms, the tried-and-true
recipes used to write programs that search through massive amounts of
data.\
\
The concept of Big O notation was first introduced and the popularized
by the German mathematicians, first by Paul Gustav Bachman, in his
book on analytical number theory, Analytische Zahlentheorie, and then by
Edmund Landau.\
\
The \"O\" symbol mentioned in the book was initially an omicron, the
15th letter of the Greek alphabet, showing a formula to show the formula
of a rate of growth.\
\
[]{#more}\

> \"Big O notation (with a capital letter O, not a zero), also called
> *Landau\'s symbol*, is a symbolism used in complexity theory, computer
> science, and mathematics to describe the asymptotic behavior of
> functions. Basically, it tells you how fast a function grows or
> declines.\
> \
> \"Landau\'s symbol comes from the name of the German number
> theoretician Edmund Landau who invented the notation \[\...\]\
> \
> \"For example, when analyzing some algorithm, one might find that the
> time (or the number of steps) it takes to complete a problem of size
> *n* is given by *T(n)* = 4 n^2^ - 2 *n* + 2.\
> \
> \"If we ignore constants (which makes sense because those depend on
> the particular hardware the program is run on) and slower growing
> terms, we could say \'T(n) grows at the order of n^2^\' and write:
> *T(n) = O(n^2^)*. - MIT 16.070, [Introduction to Computers and
> Programming](http://web.mit.edu/16.070/www/lecture/big_o.pdf).

\
Here is a list of functions, from slow growing to fast growing. If you
are dealing with massive amounts of data, you want to match the most
effective searching or sorting algorithm with its Big O notation.\

-   **Constant growth**: O(1)
-   **Logarithmic growth**: O(log n)
-   **Linear growth**: O(n)
-   **Polynomial growth**: O(n^c^)
-   **Quadratic growth**: O(n^2^)
-   **Exponential growth**: O(c^n^)

 What Was That About Complexity? 
---------------------------------

\
 From **The Idiot\'s Guide to the Big O** at
<http://www.corejavainterviewquestions.com/idiots-guide-big-o/>\

> \"**O(1)/Constant Complexity**: Constant. This means irrelevant of the
> size of the data set the algorithm will always take a constant time.
> *1 item takes 1 second, 10 items takes 1 second, 100 items takes 1
> second*. It always takes the same amount of time.\
> \
> \"**O(log n)/Logarithmic Complexity**: Not as good as constant, but
> still pretty good. The time taken increases with the size of the data
> set, but not proportionately so. This means the algorithm takes longer
> per item on smaller datasets relative to larger ones. *1 item takes 1
> second, 10 items takes 2 seconds, 100 items takes 3 seconds*. If your
> dataset has 10 items, each item causes 0.2 seconds latency. If your
> dataset has 100, it only takes 0.03 seconds extra per item. This makes
> log n algorithms very scalable.\
> \
> \"**O(n)/Linear Complexity**: The larger the data set, the time taken
> grows proportionately. *1 item takes 1 second, 10 items takes 10
> seconds, 100 items takes 100 seconds*.\
> \
> \"**O(n log n)**: A nice combination of the previous two. Normally
> there's 2 parts to the sort, the first loop is O(n), the second is
> O(log n), combining to form O(n log n) *1 item takes 2 seconds, 10
> items takes 12 seconds, 100 items takes 103 seconds*.\
> \
> \"**O(n\^2)/Quadratic Complexity**: Things are getting extra slow. *1
> item takes 1 second, 10 items takes 100, 100 items takes 10000*.\
> \
> \"**O(2\^n): Exponential Growth**! The algorithm takes twice as long
> for every new element added. *1 item takes 1 second, 10 items takes
> 1024 seconds, 100 items takes* 1267650600228229401496703205376
> seconds.\
> \
> \"It is important to notice that the above is not ordered by the best
> to worst complexity. There is no \'best\' algorithm, as it completely
> hinges on the size of the dataset and the task at hand\".

Visualizing Growth  
--------------------

\
If you are more of a visual person (like me), maybe this chart would
help. It is taken from Richard Meyr\'s lecture on **Discrete
Mathematics**.\

::: {.separator style="clear: both; text-align: center;"}
[![](https://2.bp.blogspot.com/-HYYyglKgMGU/V5VLl0KLdRI/AAAAAAAALUo/SuxIvBWBhwo_0CrLYGkXvscaZGQFNP_zgCLcB/s400/growth.png){width="400"
height="301"}](https://2.bp.blogspot.com/-HYYyglKgMGU/V5VLl0KLdRI/AAAAAAAALUo/SuxIvBWBhwo_0CrLYGkXvscaZGQFNP_zgCLcB/s1600/growth.png)
:::

\

\
\

What Were Logs, Again?
----------------------

Logarithms were first described in John Napier\'s book, *Mirifici
Logarithmorum Canonis Descriptio* (Description of the Wonderful Rule of
Logarithms), 1614. You can take a look at an English translation in
Adobe PDF format at
<http://www.17centurymaths.com/contents/napier/ademonstratiobookone.pdf>\
\

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://4.bp.blogspot.com/-hqRDXRU_L8o/V5Vb_bOSZPI/AAAAAAAALVA/u-20ZvE1yWArGzjRpbt4F8wU7CdOwBfsQCLcB/s400/napier.png){width="400" height="293"}](https://4.bp.blogspot.com/-hqRDXRU_L8o/V5Vb_bOSZPI/AAAAAAAALVA/u-20ZvE1yWArGzjRpbt4F8wU7CdOwBfsQCLcB/s1600/napier.png)
                                                            *Or you can read a book about his book, \"[John Napier and the Invention of Logarithms](https://archive.org/details/johnnapierinvent00hobsiala)\" (1914)*
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

\
\... Too much? How about a video from Khan Academy?
See <https://youtu.be/Z5myJ8dg_rM>\
\

\
\
If you really want to know what Logarithmic functions are about, I would
suggest the free class at Khan Academy, as part of its Algebra II
course, [Introduction to
Logarithms](https://www.khanacademy.org/math/algebra2/exponential-and-logarithmic-functions/introduction-to-logarithms/v/logarithms).\
\
With exponents, 2^4^ (or 2 \^ 4, two to the power of four) is *2 \* 2 \*
2 \* 2* ==\> 16.\
\
What if we want to find out, though, the power that 2 needs to be raised
by to get the answer of 16?\
\

-   *2^x^ = 16*

\... We just found that out\... x = 4.\
\
We can write it as: *log~2~16 = x.*\
\
And *log~3~ 81* = x is the same as *3^x^ = 81 \...* which is *3 \* 3 \*
3 \* 3* =\> *x = 4*. Or \"The log of base 3 of 81 is 4\".\
\

Searching Through Numbers Using Binary Search
---------------------------------------------

\
Let\'s say you wanted to use a **Binary Search Algorithm** to search
through a list of numbers, and you have read that it has a Big O of *log
n* when it comes to searching through the numbers. How many tries, worse
case scenario, would it take to search through eight numbers? Sixteen?
Thirty-two? Sixty-four? A thousand? A million?\
\

-   If n = 8, the *log n* is 3, since 2^3^ (2\*2\*2): 8.
-   If n = 16, the *log n* is 4, since 2^4^: (2\*2\*2\*2): 16.
-   If n = 32, the *log n* is 5, since 2^5^: 32.
-   If n = 64, the *log* n is 6, since 2^6^: 64.
-   If n = 128, the *log n* is 7, since 2^7^: 128.
-   If n = a thousand, the log n is roughly 10, since 2^10^: 1024.
-   If n = a million, log n is roughly 20 since 2^20^ is roughly a
    million. 

\... It\'s okay if you don\'t know what binary search algorithms are. We
will go into that later.\
\
But we figured out that:\
\

-   If there are eight numbers, it will take a maximum of three tries to
    get the number. 
-   If there are sixteen numbers, it will take a maximum of four tries
    to get the number.
-   If there are thirty-two numbers, it will take a maximum of five
    tries to get the number. 
-   If there are a thousand numbers, it will take a maximum of ten tries
    to get the number. 
-   If there are a million numbers, it will take a maximum of twenty
    tries to get the number. 

\... So, that\'s how you use Logarithms to calculate the efficiency of
your algorithm!\
\

What\'s Next?
-------------

\
Next, we can walk through a few algorithms and implement them in Java:\

-   **Insertion sort**: O (n\^2) 
-   **Mergesort**: O (n log (n)) 
-   **Quicksort**: Between two ranges, both the average O(n log n) and
    the worst: O (n\^2) 

\
Until Then, Happy Testing!\
\
-T.J. Maher\
Sr. QA Engineer,\
Fitbit-Boston\
\
*// BSCS, MSE, and QA Engineer since Aug. 1996\
// Automation developer for \[ 1.5 \] years and still counting!\
// Check out Adventures in Automation and Like us on
[Facebook](https://www.facebook.com/AdventuresInAutomation/)!*
