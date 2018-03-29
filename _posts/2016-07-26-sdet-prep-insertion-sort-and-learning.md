\-\-- layout: post title: \'SDET Prep: Insertion Sort and Learning By
Video\' date: \'2016-07-26T16:41:00.000-04:00\' author: T.J. Maher tags:
- SDET - algorithms modified\_time: \'2016-07-26T17:54:12.113-04:00\'
thumbnail: https://i.ytimg.com/vi/gM95HHI4gLk/default.jpg blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-5364586245105643186
blogger\_orig\_url:
http://www.tjmaher.com/2016/07/sdet-prep-insertion-sort-and-learning.html
\-\-- *This blog post is part of a series as I research how to move from
Automation Development to being a [Software Developer in
Test](http://www.tjmaher.com/search/label/SDET). These next few posts
will deal
with [algorithms](http://www.tjmaher.com/search/label/algorithms).*\
\
When I find my programming skills are a bit rusty from disuse, I find
watching educational videos on the internet is the next best thing to
face-to-face instruction in a classroom.\
\
With online lessons, I can repeat an example as many times as I want,
rewind the lesson, and I can pause the screen to type out the code they
are using, playing around with it immediately \-- the best way to learn
code.\
\
Within the last couple of blog posts, when we started talking about
measuring the efficiency of algorithms using Big-O notation, I displayed
Eric Drowell\'s Big-O Complexity Chart of commonly used sorting
algorithms.\
\
We are going to cover three of those sorting algorithms in a bit more
detail: Insertion sort, mergesort, and quicksort, starting with
Insertion sort.\
\
As a reference, we\'ll use lessons from Khan Academy, and from
Harvard\'s CS 50.\
\
[]{#more}\

What is Khan Academy?
---------------------

\
When Sal Khan started tutoring his cousins remotely back in 2004,
placing lessons on YouTube, he left the setting of the video as public.
He started comments from the general public about how much they loved
his courses. Sal built a company around that concept.\
\
Hear Sal talk about how he started Khan Academy in his TED talk back in
2011:\
\

\
\
Khan Academy is free to join, funded by donations. Need to study
concepts you once knew back in high school but have forgotten? Khan
Academy is a good refresher.\
\

What is Harvard\'s CS 50?
-------------------------

\
Harvard created an [Introduction to Computer Science course for
edX](https://www.edx.org/course/introduction-computer-science-harvardx-cs50x)
they named after their on-campus course, CS 50, \"an introduction to the
intellectual enterprises of computer science and the art of
programming\".\

> *\"CS50 is an introduction to computer science and programming. The
> first eight weeks are spent coding in C, developing a foundation in
> basic programming tools and concepts (e.g., loops, data structures,
> memory management). The remaining weeks are intensive immersions into
> web programming and databases, covering HTML, CSS, PHP, Javascript,
> and SQL\".* -
> [Quora](https://www.quora.com/Is-CS50-worth-taking-at-Harvard)

\
You can find its courses either on the edX site, or floating around on
its [YouTube
Channel](https://www.youtube.com/channel/UCcabW7890RKJzL968QWEykA).\
\

Khan Academy: The Insertion sort algorithm
------------------------------------------

\

\
\
Let\'s say you have a list in Python:\
\[7, 3, 1, 2, 4, 6\]\
\
Going by the video, the list is sorted like so:\
\
Initial: \[7, 3, 1, 2, 4, 6\]\
\
Step 1: \[3, 7, 1, 2, 4, 6\]\
Step 2: \[1, 3, 7, 2, 4, 6\]\
Step 3: \[1, 2, 3, 7, 4, 6\]\
Step 4: \[1, 2, 3, 4, 7, 6\]\
Step 5: \[1, 2, 3, 4, 6, 7\]\
\
Need more help visualizing this?\
\

Harvard CS50: Visualizing Insertion Sort
----------------------------------------

If you need more help visualizing this, how about Harvard\'s **CS50.tv**
video from Tommy, using Styrofoam cups?\
\

Here is a copy of the pseudocode they are using:\
\

``` {.brush: .python}
 for i = 1 to n - 1
   element = array[i]
   j = i
   while (j > 0 and array[j - 1] > element
        array[j] = array[j - 1]
        j = j -1
    array[j] = element
```

\
Need more information?\
\
How about another Harvard CS50 Video, this time with Doug Lloyd?\
\
**[Insertion Sort:]{.underline}**\

\
\
In insertion sort, the idea of the algorithm is to build your sorted
array in place, shifting elements out of the way if necessary to make
room as you go.\
\
In pseudocode:\
\
Call the first element of the array \"sorted\".\
Repeat until all elements are sorted:\

-   Look at the next unsorted element. 
-   Insert into the \"sorted\" portion by shifting the requisite number
    of elements. 

\

Khan Academy: Insertion Sort in Python
--------------------------------------

\
But how would you implement this in Python?\
\
Of the top of his head, Sal Khan writes the following code, noting that
it is not the best way to solve this problem.\
\
 

\
\
\

``` {.brush: .python}
 def insertion_sort(list)
     for index in range(1,len(list)):
          value = list[index]
          i = index - 1
          while i > 0
               if value < list[i]:
                   list[i+1] = list[i] #shift number in slot i right to slot i+1
                   list[i] = value # shift value left into slot i
                   i = i - 1
         else:
              break

>>> a = [7, 1, 3, 5, 9, 2, 3]
>>> insertion_sort(a)
>>> print(a)
[1, 2, 3, 3, 5, 7, 9]
```

\

Khan Academy: More Detail
-------------------------

\
Khan Academy\'s Computer Science course on [Insertion
Sort](https://www.khanacademy.org/computing/computer-science/algorithms/insertion-sort/a/insertion-sort)
has a tutorial that walks you through an insertion sort, showing you the
pseudocode on the algorithm, then performs a proof demonstrating that
the worst case is O(n \^2) with a best case of O(n).\
\

Joe James: Insertion Sort
-------------------------

\
Insertion Sort in Java Let\'s take a look at another example, Joe
James\' Java: Insertion Sort sorting algorithm.\
\
\
 

\
\
Joe James, in his example, takes a list of numbers: \[5, 8, 1, 3, 9,
6\]\
**\
Sort Item 0**: Item 0 is already \"sorted\", since all items to the left
are smaller.\
**Sort Item 1**: We see that it is an \"8\". Let\'s have that be a \"Key
Value\".\
\
Is the Key Value less than Item 0?\
\

-   Is 8 \< 5? 
-   No, so Item 1 can be considered sorted. 

**Sort Item 2**: Key Value = \"1\".\
\

-   Is Key Value Less than Item 1? 
-   Is k \< 8? 
-   Yes, so 8 and 1 is swapped. 
-   Is k \> 5? 
-   Yes, so 1 and 5 is swapped. 

\
\
\... This continues for the rest of the numbers.\
\
How would we code this?\
\
Joe uses:\
\

-   i for the outer loop, incrementing the index by 1
-   The variable \"key\" for the key value 
-   j for the inner loop which is shifting to the left.

\
\

``` {.brush: .java}
public int[] insertionSort (int[] list) {
   int i, j, key, temp;
   for (i=1; i < list.length; i++) {
       key = list[i];
       j = i -1;
       while (j >=0 && key < list[j]) {
          temp = list[j];
          list[j] = list[j +1];
          list[ j+1] = temp;
          j--;
     }
   }
   return list;
}
```

\
\... Watch enough videos of a subject, material such as JavaPoint\'s
version of Insertion Sort becomes easier to
understand! <http://www.javatpoint.com/insertion-sort-in-java>\
\

``` {.brush: .java}
 
public class InsertionSortExample {  
   public static void insertionSort(int array[]) {  
      int n = array.length;  
      for (int j = 1; j < n; j++) {  
         int key = array[j];  
         int i = j-1;  
         while ( (i > -1) && ( array [i] > key ) ) {  
            array [i+1] = array [i];  
            i--;  
         }  
         array[i+1] = key;  
         }  
       }  
       
    public static void main(String a[]){    
        int[] arr1 = {9,14,3,2,43,11,58,22};    
        System.out.println("Before Insertion Sort");    
        for(int i:arr1){    
            System.out.print(i+" ");    
        }    
        System.out.println();    
            
        insertionSort(arr1);//sorting array using insertion sort    
           
        System.out.println("After Insertion Sort");    
        for(int i:arr1){    
            System.out.print(i+" ");    
        }    
    }    
}    
```

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
// Check out Adventures in Automation and Like us on
[Facebook](https://www.facebook.com/AdventuresInAutomation/)!*
