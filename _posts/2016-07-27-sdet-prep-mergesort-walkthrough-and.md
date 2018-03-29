\-\-- layout: post title: \'SDET Prep: Mergesort: Walkthrough and sample
code from \"Cracking the Coding Interview\"\' date:
\'2016-07-27T23:29:00.002-04:00\' author: T.J. Maher tags: - SDET -
algorithms modified\_time: \'2016-07-27T23:32:28.430-04:00\' thumbnail:
https://i.ytimg.com/vi/EeQ8pwjQxTM/default.jpg blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-1780981842280845747
blogger\_orig\_url:
http://www.tjmaher.com/2016/07/sdet-prep-mergesort-walkthrough-and.html
\-\-- *This blog post is part of a series as I research how to move from
Automation Development to being a [Software Developer in
Test](http://www.tjmaher.com/search/label/SDET). These next few posts
will deal
with [algorithms](http://www.tjmaher.com/search/label/algorithms).*\
*\
*I\'ve often found good technical videos as difficult to find as good
documentation, and for the same reasons\... they are geared more towards
developers who use the technology day-to-day. The last time I used
sorting algorithms on a regular basis such as *Insertion* and *Selection
Sort*, *Bubble Sort*, *Mergesort*, and *Quicksort* was when I was a Comp
Sci Major back in the 1990s. I haven\'t really seen them while I have
been an automation developer.\
\
Luckily, there is Harvard University\'s **CS50** at
<https://www.youtube.com/user/cs50tv>\
\
With our [last blog
post](http://www.tjmaher.com/2016/07/sdet-prep-insertion-sort-and-learning.html),
we covered the sorting algorithm **Insertion Sort,** good for sorting
small amounts, but not very efficient for large amounts. In this blog
post, we are going to be covering an algorithm that is faster for larger
amounts\... though it does take up a bit of space.\
\

Mergesort
---------

\
**Mergesort** is a \"divide-and-conquer\" algorithm. According to
[Wikipedia](https://en.wikipedia.org/wiki/Divide_and_conquer_algorithms),
 \"In computer science, divide and conquer (D&C) is an algorithm design
paradigm based on multi-branched recursion. A divide and conquer
algorithm works by recursively breaking down a problem into two or more
sub-problems of the same or related type, until these become simple
enough to be solved directly. The solutions to the sub-problems are then
combined to give a solution to the original problem\".\
\
Stanford University  professor emeritus Donald Knuth \-- author of the
1960s saga \"[The Art of Computer
Programming](http://www.cs.utsa.edu/~wagner/knuth/)\" \-- cites the
mathematician and computer scientist John von Neuman as inventing the
Mergesort in 1945.\
\
[]{#more}\
\
**[CS50: Mergesort]{.underline}**\
*Rob Bowden, Harvard University*\

\
*<https://www.youtube.com/watch?v=EeQ8pwjQxTM> *\
*\
*\

Examine Merging Sorted Lists
----------------------------

<div>

\

</div>

<div>

What would be the fastest way to merge two already sorted lists, such as
List A: \[4, 15, 16, 50\] and List B: \[8, 23, 42, 108\]? Alternating
lists? Using every other number? 

</div>

-   Look at the first elements of the list: Which one is smallest? 4? Or
    8? \... it\'s 4, so that can be removed from List A and placed as
    the first element, the beginning, of a new merged list. 
-   Look at the first two elements of the new list: List A: \[15, 16,
    50\] and List B: \[8, 23, 42, 108\].  8 is smaller, so it is removed
    from List B, and placed as the second element of the new merged
    list. 
-   Keep on going until we have nothing left in List A or List B. If one
    of the list runs out, take everything left on the other list and
    append it onto the merged list. 

<div>

What would we do if everything is in unsorted order?

</div>

<div>

\

</div>

### Examine Working with Unsorted Lists

<div>

\

</div>

<div>

Let\'s create a new list: \[108, 15, 50, 4, 8, 42, 23, 16\]. What would
be the fastest way to sort this lists?

</div>

-   What is the n value? What is the number of items in the list?
-   Divide the list down the middle, creating two lists: If n is even,
    half of the numbers will be in one, and half will be in the other.
    If n is odd, just place it in either. It doesn\'t matter.
-   For this example, we have List A: \[108, 15, 50, 4\] and for List B:
    \[8, 42, 23, 16\]
-   Now, let\'s divide everything in half again: List A:\[108, 15\].
    List B: \[50, 4\]. List C: \[8, 42\], List D: \[23, 16\]. Is there
    an odd-man out? Doesn\'t matter, just place him in a list. 
-   Divide in half again, until we have one element per list\... size
    = 1. \[108\] \[15\] \[50\] \[4\] \[8\] \[42\] \[23\] \[16\].

<div>

\

</div>

<div>

Now, we merge!

</div>

-   Merge the first two lists: \[108\] and \[15\] =\> \[15, 108\]
-   Merge the next two lists: \[50\] and \[4\] =\> \[4, 50\] 
-   Merge \[8\] and \[42\] =\> \[8, 42\]
-   Merge \[23\] and \[16\] =\> \[16, 23\]

<div>

\

</div>

<div>

All merged? Run the merge algorithm again!

</div>

-   \[15, 108\] and \[4, 50\]: We can assume that the two lists are
    sorted. Compare 15 to 4: 4 is removed from the second list added to
    a new list leaving \[15, 108\] and \[50\]. Next, the 15 and 50 is
    compared. 
-   Do this pattern again and again until you are down to two final
    lists. Run the merge again! 

<div>

\

</div>

<div>

How fast was this sorting algorithm compared to one such as Insertion
sort (which we covered before) in Big-O notation?

</div>

<div>

\

</div>

<div>

Big-O:

</div>

-   O(n log n): Mergesort
-   O(n2): Insertion sort (and Bubble sort, and Selection sort, which we
    will not covered in this blog). 

<div>

\

</div>

<div>

Here\'s what it looks like as a graph: 

</div>

<div>

\

</div>

<div>

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  [![](https://4.bp.blogspot.com/-dFqqFZqjFuI/V5S9Z_vKjmI/AAAAAAAALUQ/_rXWyVrJt9wTx7cuqHU2DdgOMRopvi2cwCLcB/s400/khan.png){width="400" height="247"}](https://4.bp.blogspot.com/-dFqqFZqjFuI/V5S9Z_vKjmI/AAAAAAAALUQ/_rXWyVrJt9wTx7cuqHU2DdgOMRopvi2cwCLcB/s1600/khan.png)
  *From Khan Academy, [Algorithm comparison](https://www.khanacademy.org/computing/computer-science/algorithms/merge-sort/a/divide-and-conquer-algorithms)*
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

<div>

\

</div>

<div>

Need to sort a really big list? This algorithm is the fastest.

</div>

<div>

\

</div>

<div>

There are some drawbacks:

</div>

<div>

-   Sorting a small list of five (5) elements? Use the Insertion Sort
    algorithm. It\'s faster.
-   This will take up a lot more space than Bubble Sort. If RAM or Hard
    Drive space is at a premium, this is not the best solution. 

</div>

\

Coding Mergesort in Java
------------------------

\
We\'ll wrap up with sample code taken from Gayle Laakmann McDowell\'s
wonderful book, [Cracking the Coding
Interview](https://www.amazon.com/Cracking-Coding-Interview-Programming-Questions),
which I have been trying to use as a study guide for the past day or so,
referred to me by the Senior Engineering Manager at Fitbit-Boston.\
\
Gayle also is author of the site <https://careercup.com/> which also
covers programming problems that might be asked on interviews. Quoting
and using sample code from *Chapter 11: Sorting and Searching:
Mergesort*\....\

> \"Merge sort divides the array in half, sorts each of those halves,
> and then merges them back together. Each of those halves has the same
> sorting algorithm applied to it. Eventually, you are merging just two
> single-element arrays. It is the \"merge\" part that does all the
> heavy lifting.\
> \
> \"The merge method operates by copying all the elements from the
> target array segment into a helper array, keeping track of where the
> start of the left and right halves should be (helperLeft and
> helperRight). We then iterate through helper, copying the smaller
> element from each half into the array. At the end, we copy any
> remaining elements into the target array.\"

\
\
Let\'s walk through Gayle\'s mergesort solution, after we do a bit of
setup.\
\
We\'ll declare an array of integers like above and feed them into a new
method, we will call *mergesort*:\

-   int\[\] initialArray = \[108, 15, 50, 4, 8, 42, 23, 16\];
-   This means that initialArray\[0\] is 108. initialArray\[1\] is
    15. initialArray\[2\] is 50. 
-   initialArray.length is 8.
-   The very last integer, since we are starting at index 0 is
    (initialArray.length - 1).
-   We feed the initialArray into mergesort like so:
    *mergesort(initialArray);*

\
\

``` {.brush: .java}
void mergesort(int[] array) {
   int[] helper = new int[array.length];
   mergesort(array, helper, 0, array.length - 1);
}
```

\

-   Pass in the integer array into mergesort.
-   Declare a new helper integer array.
-   Does the array we passed in have a length of eight? Declare the
    helper array to be of the same length of the array we passed in. 
-   Pass into an overloaded method of the same name (mergesort) with a
    new signature. 
-   We are passing into mergesort the initial array, the empty helper
    array, the index of the beginning of the array (\"0\"), and the end
    of the array (Whatever the length was, subtracting one). Remember,
    with counting arrays, we start off with \"0\".  

\

``` {.brush: .java}
void mergesort(int[] array, int[] helper, int low, int high) {
   if (low < high) {
      int middle = (low + high) / 2;
      mergesort(array, helper, low, middle); // Sort left half
      mergesort(array, helper, middle+1, high); // Sort right half
      merge(array, helper, low, middle, high); // Merge them
    }
}
```

\
Let\'s say this is the first time around:\
\

-   We have the contents of initialArray = \[108, 15, 50, 4, 8, 42, 23,
    16\]
-   We have a brand-new blank helper array. 
-   The \"low\" is the index of 0. The \"high\" is the last position,
    the array length minus one, which is (*8 minus 1* ) or 7.
-   We want to make sure that starting index is less than the ending
    index. Yes, 0 \> 7. 
-   We then take the low, add the high, and divide by 2 to get the
    middle and store it as an integer called \"middle\". 7 plus 0 = 7.
    Divide by 2, and you get 3 with a remainder. Since we are storing
    this in an integer, just the \"3\" is stored as the new middle
    index. 

<div>

Now for recursion\... *Did you know the definition of recursion is
\"recursion\"?* 

</div>

<div>

\

</div>

<div>

We are splitting the list into two parts:

</div>

<div>

-   We are going to feed into one array (\[108, 15, 50, 4, 8, 42, 23,
    16\]), the helper array, the low index of position \"0\", and the
    high of the middle position, \"3\". It\'ll be looking at \[108, 15,
    50, 4\].
-   We are going to feed into the other array the entire list (\[108,
    15, 50, 4, 8, 42, 23, 16\]), the helper array, the middle +1 as the
    low. ( initialArray\[4\] is 8 ) and the high of \"7\". Therefore, it
    is looking at \[8, 42, 23, 16\]. 
-   Round and round it will go, dividing in half and half again. Soon,
    there will be an array where the low is index 0, and the high fed
    into mergeSort will also be 0\... then the program will realize that
    it has to stop dividing since (low \< high) will then fail. You will
    have \"108\" be in an array. 

</div>

\

``` {.brush: .java}
void merge(int[] array, int[] helper, int low, int middle, int high) {
    // Copy both halves into a helper array 
    for (int i = low; i <= high; i++) {
          helper[i] = array[i];
    }
    int helperLeft = low;
    int helperRight = middle + 1;
    int current = low;

// Iterate through helper array. Compare the left and right
// half, copying back the smaller element from the two halves
// into the original array. 
 
  while (helperLeft <= middle && helperRight <= high) {
   if (helper[helperLeft] <= helper[helperRight]) {
   array[current] = helper[helperLeft];
   helperLeft++;
  } else { // If right element is smaller than left element
   array[current] = helperfhelperRight];
   helperRight++;
  }
  current++;
 }

// Copy the rest of the left side of the array into the
// target array 

  int remaining = middle - helperLeft;
  for (int i = 0; i <= remaining; i++) {
   array [current + i] = helper[helperLeft + i]j
  }
 }
```

\
\
As Gladys lists in her book:

> *\"You may notice that only the remaining elements from the left half
> of the helper array are copied into the target array. Why not the
> right half? The right half doesn\'t need to be copied because it\'s
> already there.\
> \
> \"Consider, for example, an array like \[lj 4, 5 \|\| 2, 8, 9\]
> (the\"\| (\"indicates the partition point). Prior to merging the two
> halves, both the helper array and the target array segment will end
> with \[8, 9\]. Once we copy over four elements (1, 4, 5, and 2) into
> the target array, the \[8, 9\] will still be in place in both arrays.
> There\'s no need to copy them over\".*

\
Next blog entry, we will continue to use \"Cracking the Coding
Interview\" as a source as we examine Data Structures.\
Until then, Happy Testing!\
\
-T.J. Maher\
Sr. QA Engineer,\
Fitbit-Boston\
\
*// BSCS, MSE, and QA Engineer since Aug. 1996\
// Automation developer for \[ 1.5 \] years and still counting!\
// Check out Adventures in Automation and Like us on
[Facebook](https://www.facebook.com/AdventuresInAutomation/)!*
