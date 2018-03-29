\-\-- layout: post title: \'Automate Amazon: Sketch of Possible Data
Driven Tests with TestNG\' date: \'2016-01-14T00:13:00.001-05:00\'
author: T.J. Maher tags: - code examples - beginner - Java - TestNG -
WebDriver - test framework modified\_time:
\'2016-04-29T07:41:39.535-04:00\' blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-7847725997322005500
blogger\_orig\_url:
http://www.tjmaher.com/2016/01/automate-amazon-sketch-of-possible-data.html
\-\-- *This post is eighth of a series of nine. Need to go [back to the
beginning](/2015/12/next-week-automating-amazon-how-i-am.html)?*\
\

### Background: Our Automation Framework

This section is going to be a little bit different than the others, more
experimental.\
\
With previous sections, I wrote how we *actually* created an automated
framework at my workplace\... as of December 2015.\
\
With this section, I am going to talk about how you *could* possibly do
data-driven testing with TestNG, without showing a running system. On my
local environment, I had some trouble with the setup with running tests
in parallel. I can talk about how to modify your \@Test, how to set up a
testsuite for TestNG.\
\
[]{#more}My workplace, for a few two-week sprints, was experimenting
with how we acquire our test data. Normally, we use TestRail, a
web-based graphical user interface where with dropdowns and listboxes we
can set up which test product, test credit card, test billing and
shipping address to use for a particular test. But what if we were to
use TestNG\'s XML input file to get our input data?\
\
We\'re constantly revising how we do things. Our automation framework
over this past summer looks very different than what we had in early
December of last year.\
\
Compare:\

-   [Testing
    The-Internet](/2015/06/simple-manipulation-of-login-page.html),
    written back in June 2015
-   [Automate
    Amazon](/2015/12/next-week-automating-amazon-how-i-am.html), which
    started back in December 2015

\
As more automation engineers are added to our team, as we experiment
with different ways of doing things, as we learn more about other
teams\' standards and practices, our automation framework evolves.\
\
Before this investigation of TestNG, our automation framework consisted
of:\

-   Storing data such as username and passwords in **Properties files**
    ( [review](/2015/12/automate-amazon-writing-sign-in-test.html) )
-   Storing Credit Card numbers, Test Addresses, and other test
    parameters in **Enums**
    ( [review](/2016/01/automate-amazon-productenums-and.html) ) 
-   Storing the various instances of test data, such as the initial test
    data, so we can compare it with what is seen on a Review page and a
    Checkout page, in
    **POJOs** ( [review](/2016/01/automate-amazon-productenums-and.html) )
    which we can instantiate during out test  ( review )
-   Storing TestNG tests in **Test Classes** and \@Test methods, within
    a folder called testcases. ( review )
-   The Test Class methods  can only call methods encapsulated in our
    **Actions
    classes** ( [review](/2015/12/automate-amazon-writing-sign-in-test.html) )
-   The Actions classes can only call methods we have in our **Page
    Objects** (
    [review](/2015/12/automate-amazon-writing-sign-in-test.html) )
-   Only Page Objects can interact with the Selenium WebDriver calls to
    the Document Object Model (DOM), which we wrapped in try / catch /
    throw blocks in our **Common Utilities library** (
    [review](/2015/12/automate-amazon-commonutils-methods-and.html) )

\
TestNG\'s XML file is going to add a new layer to the automation,
allowing us to perform data-driven testing, and run multiple tests in
parallel.\
\

### What is Data Driven Testing? 

What if we treated our current test like a black box? Instead of
hardcoding a test product into the test method like so\...\

``` {style="background-image: URL(http://2.bp.blogspot.com/_z5ltvMQPaa8/SjJXr_U2YBI/AAAAAAAAAAM/46OqEP32CJ8/s320/codebg.gif); background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
   @Test()  
   public void test_createPurchaseOrderForSingleProduct(){  
     Products testBook = Products.HITCHHIKERS_GUIDE;  
     ...  
     OrderActions orderActions = new OrderActions();  
     Book bookProductPage = orderActions.loadProductPageDataIntoProductObject(testBook);  
```

\
\... what if we could feed in the test products before the test actually
starts?\
\
The test would remain the same. It would be the test data that changed.
That is **Data Driven Testing**.\
\
From TutorialsPoint: [What is Data Driven
Testing?](http://www.tutorialspoint.com/software_testing_dictionary/data_driven_testing.htm)\

> *\"Data-driven testing is creation of test scripts where test data
> and/or output values are read from data files instead of using the
> same hard-coded values each time the test runs. This way, testers can
> test how the application handles various inputs effectively. It can be
> any of the below data files.*\
>
> -   *\"Datapools*
>
> <!-- -->
>
> -   *\"Excel files*
>
> <!-- -->
>
> -   *\"ADO objects*
>
> <!-- -->
>
> -   *\"CSV files*
>
> <!-- -->
>
> -   *\"ODBC sources\"*

\... With TestNG, we will be experimenting with creating an TestNG Test
Suite with XML.\
\

### What is TestNG?

**\
From the
[Introduction](http://testng.org/doc/documentation-main.html#introduction)
on TestNG\'s site:**\

> *\"[TestNG](http://testng.org/) is a testing framework designed to
> simplify a broad range of testing needs, from unit testing (testing a
> class in isolation of the others) to integration testing (testing
> entire systems made of several classes, several packages and even
> several external frameworks, such as application servers).* 

> *\"Writing a test is typically a three-step process:*\
>
> -   *\"Write the business logic of your test and insert TestNG
>     annotations in your code.*
>
> <!-- -->
>
> -   *\"Add the information about your test (e.g. the class name, the
>     groups you wish to run, etc\...) in a testng.xml file or in
>     build.xml.*
>
> <!-- -->
>
> -   *\"Run TestNG\".*

\

###  Add Another Product to Our Framework

\
Let\'s go to Amazon.com and select a few other products we could use as
test products.\
\
We already have **The Hitchhiker\'s Guide to the Galaxy** *by Douglas
Adams* at <http://www.amazon.com/gp/product/0345391802>\
\
\
Let\'s add a few more\...\
\
**The Hobbit** *by J.R.R. Tolkein*: *Mass Market
Paperback*: <http://www.amazon.com/gp/product/0345339681>\
\
**Ringworld** *by Larry Niven: Mass Market
Paperback:* <http://www.amazon.com/gp/product/0345333926>\
\
**Foundation** *by Issac Asimov: Mass Market
Paperback: *<http://www.amazon.com/gp/product/0553293354>\
\
We can add all of these books to our **Products** Enum class:\

``` {style="background-image: URL(http://2.bp.blogspot.com/_z5ltvMQPaa8/SjJXr_U2YBI/AAAAAAAAAAM/46OqEP32CJ8/s320/codebg.gif); background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
1:  package enums;  
2:  /**  
3:   * Created by tmaher on 12/22/2015.  
4:   */  
5:  public enum Products {  
6:    HITCHHIKERS_GUIDE("0345391802", "The Hitchhiker's Guide to the Galaxy"),  
7:    THE_HOBBIT("0345339681", "The Hobbit"),  
8:    RINGWORLD("0345333926", "Ringworld"),  
9:    FOUNDATION("0553293354", "Foundation");  
10:    // The price will always fluctuate. The product id and product title will be more or less constant.  
11:    private String id;  
12:    private String productTitle;  
13:    Products(String id, String productTitle){  
14:      this.id = id;  
15:      this.productTitle = productTitle;  
16:    }  
17:    public String getProductId(){  
18:      return id;  
19:    }  
20:    public String getProductTitle(){  
21:      return productTitle;  
22:    }  
23:  }  
```

\
Now, we need to come up with the XML input file\....\
\

### What our Directory Structure Will Look Like

\
For this blog entry, we will be expanding upon the what we already had,
so the directory structure will remain the same, except for a new XML
file called \"testsuite\_books.xml\".\
**src/test/java**\

actions

-   OrderActions

base

-   LoadProperties

enums

-   Products
-   Url

pages

-   HomePage
-   SignInPage
-   ProductPage
-   ShoppingCartPage
-   ShoppingCartReviewPage

pojo

-   Book

properties

-   user.properties

testcases

-   PurchaseOrderTest
-   **testsuite\_books.xml**

utils

-   CommonUtils
-   DriverUtils

### Refactor the Test Class

Remember our test method in the PurchaseOrderTest.java class?\
\
We are going to modify it a bit, so the test book is no longer hard
coded.\
\

``` {style="background-image: URL(http://2.bp.blogspot.com/_z5ltvMQPaa8/SjJXr_U2YBI/AAAAAAAAAAM/46OqEP32CJ8/s320/codebg.gif); background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
  @Parameters( {"testBook"} )  
   @Test()  
   public void test_createPurchaseOrderForSingleProduct(Products testBook){  
     ...  
     OrderActions orderActions = new OrderActions();  
     ShoppingCartReviewPage shoppingCartReviewPage = new ShoppingCartReviewPage();  
     ...  
     Book bookProductPage = orderActions.loadProductPageDataIntoProductObject(testBook);  
```

\
If we declare FOUNDATION or THE\_HOBBIT to be the test book, this test
will now go to those product pages.\
\

<div>

### Add a TestNG XML file

**testsuite\_books.xml**\

``` {style="background-image: URL(http://2.bp.blogspot.com/_z5ltvMQPaa8/SjJXr_U2YBI/AAAAAAAAAAM/46OqEP32CJ8/s320/codebg.gif); background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 <?xml version="1.0" encoding="UTF-8" ?>  
 <!DOCTYPE suite SYSTEM "http://testng.org/testng-1.0.dtd">  
 <suite name="Purchasing Test: Books" verbose="1" preserve-order="true" parallel="methods" thread-count="5">  
 <test name="Verify product price on Shopping Cart Review page | HITCHHIKERS_GUIDE" preserve-order="true">  
   <parameter name="testBook" value="HITCHHIKERS_GUIDE"/>  
   <classes>  
     <class name="testcases.PurchaseOrderTest" />  
   </classes>  
 </test>  
 <test name="Verify product price on Shopping Cart Review page | THE_HOBBIT" preserve-order="true">  
   <parameter name="testBook" value="THE_HOBBIT"/>  
   <classes>  
     <class name="testcases.PurchaseOrderTest" />  
   </classes>  
 </test>  
 </suite>  
```

\
This XML file sets up two tests:\
\

-   Verify product price on Shopping Cart Review page \|
    HITCHHIKERS\_GUIDE
-   Verify product price on Shopping Cart Review page \| THE\_HOBBIT

In theory, running these tests, both tests would execute, each test with
its own output.\
\
Well, that\'s everything that I had planned for Automate Amazon. Hope
you enjoyed reading the examples as much as I had writing them!\
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
[\
]{style="background-color: white; color: #222222; font-family: "calibri"; font-size: 15.4px; line-height: 21.56px;"}[-T.J.
Maher]{style="background-color: white; color: #222222; font-family: "calibri"; font-size: 15.4px; line-height: 21.56px;"}\
* Sr. QA Engineer, Fitbit*\
* Boston, MA*\
*\
// Automated tester for \[ 10 \] months and counting!*\
*\
Please note: \'Adventures in Automation\' is a personal blog about
automated testing. It is not an official blog
of [Fitbit.com](http://www.fitbit.com/). *

</div>
