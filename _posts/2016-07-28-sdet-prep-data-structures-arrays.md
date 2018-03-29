\-\-- layout: post title: \'SDET Prep: Data Structures: Arrays, Hashmaps
and how to implement them in Java.\' date:
\'2016-07-28T20:03:00.002-04:00\' author: T.J. Maher tags: - SDET - data
structures modified\_time: \'2016-07-31T16:14:11.647-04:00\' thumbnail:
https://4.bp.blogspot.com/-wB1vK0txOMI/V5o-CRFO8mI/AAAAAAAALVc/iOcV8VAxVSkr\_Yss4Mc1tu9mP82G7Y18ACLcB/s72-c/data.png
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-7291875192546067004
blogger\_orig\_url:
http://www.tjmaher.com/2016/07/sdet-prep-data-structures-arrays.html
\-\-- *This blog post is part of a series as I research how to move from
Automation Development to being a [Software Developer in
Test](http://www.tjmaher.com/search/label/SDET). We covered some basic
[algorithms](http://www.tjmaher.com/search/label/algorithms), before.
These next few posts will deal with [data
structures](http://www.tjmaher.com/search/label/data%20structures),
illustrating them with Java. *\
*\
*As an **automation developer**, I\'ve been focusing on browser testing
with Selenium WebDriver and Java, being able to draw from my decades of
experience testing web applications. When it comes to various data
structures, I use arrays, lists, arraylists, and the occasional hashmap
in my day-to-day work, but that is about it.\
\
A **Software Developer in Test** (SDET) isn\'t that far removed from a
**Software Development Engineer** (SDE), relying on data structures and
algorithms I once studied as a Computer Sci major back at Bridgewater
State. *Note: Each link below goes to the respective Harvard University
CS50 video, if any.*\
\

-   **[Data Structures]{.underline}**:
    [Arrays](https://youtu.be/7EdaoE46BTI), [Singly Linked
    Lists](https://youtu.be/5nsKtQuT6E8), [Doubly Linked
    Lists](https://youtu.be/HmAEzp1taIE), [Binary
    Trees](https://youtu.be/mFptHjTT3l8),
    [Stacks](https://youtu.be/9Tp8wHD66lw),
    [Queues](https://youtu.be/SLOrrO7DlYo), ArrayLists, and [Hash
    Tables](https://youtu.be/h2d9b_nEzoA)
-   **[Algorithms]{.underline}**: Breadth First Search and Depth First
    Search (not on CS50), [Binary Search](https://youtu.be/5xlIPT1FRcA),
    [Insertion Sort](https://youtu.be/DFG-XuyPYUQ), [Merge
    Sort](https://youtu.be/EeQ8pwjQxTM),
    [Quicksort](https://youtu.be/aQiWF4E8flQ). 
-   **Concepts such as** [Recursion](https://youtu.be/VrrnjYgDBEk), Bit
    Manipulation (not on CS50),
    [Pointers](https://youtu.be/yOdd3uYC--A), [Dynamic Memory
    Allocation](https://youtu.be/ywqB3ZTf8OE) and
    [Structures](https://youtu.be/6RLxPdZ59y0) 
-   **[Design Patterns]{.underline}** like: Singleton Design Pattern,
    Factory Design Pattern
-   **[Storing
    Memory]{.underline}** in [Stack](https://youtu.be/beqqGIdabrE) vs.
    Heap

\
If you are a manual tester or automated tester and want to shift to
software development, Gayle Laakmann McDowell\'s [Cracking the Coding
Interview](https://www.amazon.com/Cracking-Coding-Interview-Programming-Questions)
is an excellent summation of all terms listed above. It seems to be a
good resource for even Senior developers, who may be far removed from
college.\
\
[]{#more}\
\
When you are a Software Developer, you are always trying to find the
right tool for the job. When we looked at sorting algorithms:\
\

-   **insertion sort** was quite fast for sorting five or less elements,
    but O(n \^ 2) after that.
-   **mergesort** was very quick, O(n log n), but needed a bit of space,
    O(n), when creating new arrays to do the work. Want it fast, but
    space be damned? This algorithm might qualify.  
-   **quicksort**, which we didn\'t look at yet, is very quick on
    average, O(n log n), but at its worst can be as bad as insertion
    sort O(n \^ 2). The good thing it only needs O(log(n)) of space,
    worse case scenario, no matter how big the set of elements are that
    need to be sorted. 

\
See more algorithms at the [Big-O
Cheatsheet](http://bigocheatsheet.com/), by Eric Rowell. It also has a
selection of the Big-O times of Data Structures.\
\

::: {.separator style="clear: both; text-align: center;"}
[![](https://4.bp.blogspot.com/-wB1vK0txOMI/V5o-CRFO8mI/AAAAAAAALVc/iOcV8VAxVSkr_Yss4Mc1tu9mP82G7Y18ACLcB/s640/data.png){width="640"
height="468"}](https://4.bp.blogspot.com/-wB1vK0txOMI/V5o-CRFO8mI/AAAAAAAALVc/iOcV8VAxVSkr_Yss4Mc1tu9mP82G7Y18ACLcB/s1600/data.png)
:::

\
Let\'s go over how to use a few of the data structures, starting with
the most basic ones:\
\
\

Arrays
------

\
Need a way to store a lot of data right next to each other in memory?
Arrays are small identically-sized blocks of space. Only the same data
typed can be stored in each slot in memory, such as **int** or **char**.
If there are *n* elements, First space is 0. Last space is (*n-1)*.\
\
Java has a built in Array object with methods we can use to manipulate
the array.\
\

-   Declare an integer array, setting the values: *int\[\] myArray = {
    1, 2, 3, 4, 5 };*
-   Initialize an array of size 5: *int\[\] blankArray = new int\[5\];*
-   Find the first element: *myArray\[0\] *
-   Print out the array size: *System.out.println(myArray.length);*
-   Print the last element of the array: *int indexLast =
    (myArray.length - 1);
    System.out.println(unsortedArray\[indexLast\]);*
-   Print the entire array:
    *System.out.println(Arrays.toString(myArray)); *
-   Sort the array: *Array.sort(myArray)*
-   Search the array using the binary search algorithm:
    *Array.binarySearch(myArray).*

\
\
If you declared an array of five elements, it will always have five
elements, never six. The space is set in stone.\
\
You can also have multidimentional arrays, such as playing tic-tac-toe
on a board that is 3 by 3. For that we would initialize a 3 x 3 grid of
characters, since we would be using either an \"X\" or an \"O\":\
\

-   Declare a board: *char\[\]\[\] ticTacToe = new char\[3\]\[3\];*
-   The top left corner would be the value: *ticTacToe\[0\]\[0\]*
-   The middle space would be the value: *ticTacToe\[1\]\[1\]*
-   The right bottom corner space would be the value:
    *ticTacToe\[3\]\[3\]*
-   Want to insert an \"O\" in the middle? *ticTacToe\[1\]\[1\] = \'O\';
    // Note the single quotes, suitable for single characters*

\
How about setting up a 10 x 10 board of Battleship to track where your
ships are: true if they are on the space, false if they are not on the
space?\
\

-   Board setup: *boolean\[\]\[\] battleship = new boolean\[10\]\[10\];*

\
\... The idea it is a 10 x 10 array is just an abstraction. It actually
is just allocating 100 spaces in memory. But with this data structure we
can loop along *battleship\[x\]\[y\]* as if it was the grid we imagine.\
\
**CS50**: Introduction to Arrays *(using C++ sourcecode)*:\

\
[*https://youtu.be/7mOJN1c1JEo*](https://youtu.be/7mOJN1c1JEo)\
\

HashMaps
--------

Let\'s make up an example of how a HashMap can be used in Java.\
\
Take the sentence, \"The Quick Brown Fox Jumped Over The Lazy Dog\". How
many \'A\'s does it have? \'Q\'s? \'T\'s?\
\

-   Let\'s store the sentence into a String, and make sure that
    everything is lowercase. Oh, and trim off any whitespace. 
-   And for this example, let\'s pretend that everything is either
    alphanumeric (A thru Z or 0 thru 9) or whitespace, just to make it a
    bit more simple. We can use the String object method
    \"toLowerCase()\" and \"trim()\".

\
Think of a String as a collection of characters. We can convert the
String into one long character array by using the method
\"toCharacterArray()\". Then, we can use a foreach loop to go through
each character.\
\
\... But where would we store the totals of each character? We could
easily set up an array of 26, one for each letter in the English
language, but there might be space not used. This would be pretty
inefficient.\
\
Let\'s create a Hashmap called \"letters\". As we go letter by letter
through the String sentence (as a character array) we can:\
\

-   Declare the Hashmap to be of type \<Character, Integer\>.
-   Loop through the entire sentence, character by character.

Check the letters hashmap. Does it countain a \'q\'?\
\

-   If so, let\'s get whatever the count is up to, increment it by 1,
    then store it in an integer called \"newValue\".
-   Let\'s then put that newValue back in the hashmap, using the
    character by the key.

\
What? No \'q\' in the hashmap?\
\

-   Let\'s put in the letters hashmap the value of \"1\" in that
    character key.

\
Here\'s what I just came up with as a solution:\
\

``` {.brush: .java}
@Test
public void test_HashMap(){
    String sentence = "The Quick Brown Fox Jumped Over the Lazy Dog"
                     .toLowerCase().trim();
    HashMap<Character, Integer> letters = new HashMap<Character, Integer>();
    for (char character : sentence.toCharArray()){
        if (letters.containsKey(character)){
            int newValue = letters.get(character) + 1;
            letters.put(character, newValue);
        } else if (character != ' '){
            letters.put(character, 1);
        }
    }
    System.out.println(letters);
}
```

\
If we run the test, we get:\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 {a=1, b=1, c=1, d=2, e=4, f=1, g=1, h=2, i=1, j=1, k=1, l=1, m=1, n=1, o=4, p=1, q=1, r=2, t=2, u=2, v=1, w=1, x=1, y=1, z=1}  
```

\
\
That is all we have for now when it comes to Software Development. Happy
Testing!\
\
-T.J. Maher\
Sr. QA Engineer,\
Fitbit-Boston\
\
*// BSCS, MSE, and QA Engineer since Aug. 1996\
// Automation developer for \[ 1.5 \] years and still counting!\
// Check out Adventures in Automation and Like us on
[Facebook](https://www.facebook.com/AdventuresInAutomation/)!*
