\-\-- layout: post title: \'Automate Amazon: Sketch out a Use Case\'
date: \'2015-12-24T05:00:00.000-05:00\' author: T.J. Maher tags: - code
examples - Java - WebDriver - test framework modified\_time:
\'2016-04-29T07:49:18.514-04:00\' thumbnail:
https://1.bp.blogspot.com/-zsmCrX96mUE/Vng-2ZCrB5I/AAAAAAAAK1Q/fO1NmgSWvIE/s72-c/Hitchhiker.jpg
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-7524014198537052282
blogger\_orig\_url:
http://www.tjmaher.com/2015/12/automate-amazon-sketch-out-use-case.html
\-\-- *This post is second of a series of nine. Need to go [back to the
beginning](/2015/12/next-week-automating-amazon-how-i-am.html)?*\
\
With the last blog entry, we talked about setting up a development
environment and running our first test.\
\
With this entry, we are going to examine Amazon.com\'s site and see if
we can come up with a quick test to automate creating a purchase order
with Amazon\'s Sign In, AddToCart and Checkout process.\
\
[]{#more}\

### Draft the Test

#### Go to the Sign In Page

\
The SignInPage is where we Sign into the site, entering the email
address and password into the appropriate text boxes, and select the
\"Sign in\" button. We need to:\
\

-   Go to http://www.amazon.com/
-   Mouseover to \"Hello. Sign in Your Account\"
-   Select the \"Sign In\" button

#### 

#### Sign Into the Site

-   At the Sign In page enter the test user name and password.
-   Log into the site.

\

#### Select a Test Project

<div>

\

</div>

For an initial test product in the Purchase Order test, let\'s use a
Mass Market Paperback copy of **The Hitchhiker\'s Guide to the Galaxy**,
by Douglas Adams. This is the first book in the four book \"Hitchhiker
trilogy\", re-released by Del Ray in 1995.\
\
You can find the Amazon link to the book
at <http://www.amazon.com/gp/product/0345391802>\
\

::: {.separator style="clear: both; text-align: center;"}
[![](https://1.bp.blogspot.com/-zsmCrX96mUE/Vng-2ZCrB5I/AAAAAAAAK1Q/fO1NmgSWvIE/s320/Hitchhiker.jpg){width="196"
height="320"}](http://1.bp.blogspot.com/-zsmCrX96mUE/Vng-2ZCrB5I/AAAAAAAAK1Q/fO1NmgSWvIE/s1600/Hitchhiker.jpg)
:::

\
Besides a lot of absurdist and excellent nerdy humor, this test product
has many properties.\
\

-   **ProductTitle**: The Hitchhiker\'s Guide to the Galaxy
-   **Author**: Douglas Adams
-   **OfferPrice**: \$7.19
-   **Edition**: Mass Market Paperback

\
While we add this book to the cart and checkout with it \-- as much as
we can do without any test credit cards \-- we will be attempting to
verify at each stage that these four properties stay the same.\
\
Now, let\'s walk through the site, seeing what happens when we add this
book to the cart.\

#### ProductPage

\
First, let\'s come up with some more proper names we can use.\
\

-   Let\'s call http://www.amazon.com/ the HomePage, and the url the
    baseURL.
-   Since the subfolder
    is [/product/](http://www.amazon.com/gp/product/) let\'s call this
    section the ProductPage. 
-   Since the suffix for the URL
    is [0345391802](http://www.amazon.com/gp/product/0345391802), let\'s
    call this the productID
-   So, to get to this specific URL it is baseURL + productPage +
    productID.

\
Now, let\'s select the **\[AddToCart\]** button.\
\

#### ShoppingCartPage 

\
Here, we can verify that the properties on the ProductPage carried over
to the ShoppingCart page:\

-   **ProductTitle**: The Hitchhiker\'s Guide to the Galaxy
-   **Author**: Douglas Adams
-   **OfferPrice**: \$7.19
-   **Edition**: Mass Market Paperback

\... Since we don\'t have any test credit cards, let\'s skip placing
your order and end the test here.\
\

### Components of the Test

The test methods can go in the package **testcases** in a class called
**PurchaseOrderTest.java**.\
\
From our sketch, it looks like we can collect the web elements in the
package **pages** into the following [Page
Objects](/2015/07/the-internet-page-object-model-examples.html):\
\

-   HomePage
-   SignInPage
-   ProductPage
-   ShoppingCartPage

\
The individual page objects would be Java classes that only contained
encapsulate getting, setting, and validating the web elements.\
\
We could do the extra step of grouping up common elements of the test
such as the steps to sign into Amazon.com in an **actions** package in a
class called PurchaseOrderActions.java.\
\
\

### View the (mostly) Completed Test Code:

-   All test code can be found on GitHub
    at [Automate-Amazon](https://github.com/tjmaher/automate-amazon/tree/master/automate-amazon/src/test/java).

\
**NEXT**: [Setting up Common Utility Methods
\>\>](/2015/12/automate-amazon-commonutils-methods-and.html)\
\
[-T.J.
Maher]{style="background-color: white; color: #222222; font-family: "calibri"; font-size: 15.4px; line-height: 21.56px;"}\
* Sr. QA Engineer, Fitbit*\
* Boston, MA*\
*\
// Automated tester for \[ 8 \] month and counting!*\
*\
*

*Please note: \'Adventures in Automation\' is a personal blog about automated testing. It is not an official blog of [Fitbit.com](http://www.fitbit.com/). *
------------------------------------------------------------------------------------------------------------------------------------------------------------

\
\

::: {#toc-section .toc-section}
**Automate Amazon**:\

-   [Introduction](/2015/12/next-week-automating-amazon-how-i-am.html)
-   **Part One:** [Environment
    Setup](/2015/12/automate-amazon-development-environment.html)
-   **Part Two:** [Sketch Use
    Case](/2015/12/automate-amazon-sketch-out-use-case.html)
-   **Part Three:** [CommonUtils, methods,
    exceptions](/2015/12/automate-amazon-commonutils-methods-and.html)
-   **Part Four:** [Write Sign In
    Test](/2015/12/automate-amazon-writing-sign-in-test.html)
-   **Part Five:** [Product Enums and
    Objects](/2016/01/automate-amazon-productenums-and.html)
-   **Part Six:** [Initializing Login and
    Cart](/2016/01/automate-amazon-initializing-login-and.html)
-   **Part Seven:** [Writing Shopping Cart
    Test](/2016/01/automate-amazon-writing-shopping-cart.html)
-   **Part Eight:** [Data Driven Tests with TestNG
    XML](/2016/01/automate-amazon-sketch-of-possible-data.html)
-   **Part Nine:** [Code Review Request,
    please! ](/2016/01/code-review-request-please-automated.html)
-   **Source Code:** [GitHub, T.J.
    Maher](https://github.com/tjmaher/automate-amazon/)
:::

\
\
