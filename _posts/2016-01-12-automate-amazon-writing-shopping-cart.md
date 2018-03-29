\-\-- layout: post title: \'Automate Amazon: Writing a Shopping Cart
Test \' date: \'2016-01-12T00:06:00.000-05:00\' author: T.J. Maher tags:
- code examples - Java - intermediate - WebDriver - test framework
modified\_time: \'2016-04-29T07:45:12.932-04:00\' thumbnail:
https://3.bp.blogspot.com/-1WKTSWJhm7U/VpBxeLV2r-I/AAAAAAAAK1k/cpeZ7HZgAaQ/s72-c/HitchProduct.png
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-2868336108816892328
blogger\_orig\_url:
http://www.tjmaher.com/2016/01/automate-amazon-writing-shopping-cart.html
\-\-- *This post is seventh in a series of nine. Need to go [back to the
beginning](/2015/12/next-week-automating-amazon-how-i-am.html)?*\
\
Finally! We have the testing framework written!\
\
Now it is time to write a simple test to check to see how we could
develop some tests to use this framework.\
\
Let\'s call our test method in the PurchaseOrderTest class
\"test\_CreatePurchaseForSingleProduct\". Our test can be:\
\

> 1\) Go to the Product page, and check the price of a product, such as the
> mass market edition of the Hitchhiker\'s Guide to the Galaxy  

> 2\) Add the Product to an empty Shopping Cart 

> 3\) Verify the price in the Shopping Cart Review page is the same as the
> product.

\
[]{#more}\
To write our first ever test of the ShoppingCart Review Page, we have
had a lot of setup to do. Luckily, most of it is already written for the
previous six blog entries. We have:\
\

-   Declare the test product to be a single book, the mass market
    edition of the first book in the Hitchhiker\'s Guide to the Galaxy.
     ( [review](/2016/01/automate-amazon-productenums-and.html) ) 
-   Grab the username and password to login. 
-   Instantiate the OrdersActions class so we can process the order with
    methods we set up in the
    class. ( [review](https://www.blogger.com/2015/12/automate-amazon-writing-sign-in-test.html) )
-   We are going to instantiate the page object called the
    ShoppingCartReviewPage, which will be designed below. 
-   We use the methods we wrote in the OrderActions page (
    [review](/2015/12/automate-amazon-writing-sign-in-test.html) ) to
    initialize the Login, logging out if we have to. (
    [review](https://www.blogger.com/2016/01/automate-amazon-initializing-login-and.html)
    )
-   We navigate to the Home Page and and Login as the username and
    password. (
    [review](/2015/12/automate-amazon-writing-sign-in-test.html) )
-   We initialize the cart to remove any previous test products from the
    shopping cart. (
    [review](/2016/01/automate-amazon-initializing-login-and.html) )
-   We grab all data shown on the product page for our test product and
    load up the product
    object. ( [review](https://www.blogger.com/2016/01/automate-amazon-productenums-and.html) ) 
-   We add this test product, a test book, to the Shopping Cart Review
    page, as shown below. 

<div>

Elaborating on our three part test, our test can:

</div>

<div>

-   Get the actual cart subtotal price shown in the Shopping Cart Review
    page. 
-   Retrieve the price stored from the book\'s product page. 
-   Since I like pretty output in my logs, we are going to feed the
    actual and expected results and see if it matches with a (PASS) or
    (FAIL). 
-   And finally, we are going to assert that the actual subtotal price
    in the cart matches what is expected, as shown below.

<div>

It\'s a heck of a lot of setup for one small assertion statement. The
payoff will be in the next blog entry where I will be talking about
testing multiple products and the tests running in parallel. 

</div>

</div>

\

### What our Directory Structure Will Look Like

\
For this blog entry, we will be expanding upon the what we already had,
so the directory structure will remain the same, except for a new page
object called ShoppingCartReviewPage.\
\
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

utils

-   CommonUtils
-   DriverUtils

### The ShoppingCartReviewPage

<div>

Remember that our test product we set up in our test is:\

``` {style="background-image: URL(http://2.bp.blogspot.com/_z5ltvMQPaa8/SjJXr_U2YBI/AAAAAAAAAAM/46OqEP32CJ8/s320/codebg.gif); background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 Products testBook = Products.HITCHHIKERS_GUIDE;  
```

\

#### Navigating to the Page

\
Getting to what I have dubbed the \"Shopping Cart Review Page\" is easy.
All you need to do is:\
\
**Go to the page of the product** at
<http://www.amazon.com/Hitchhikers-Guide-Galaxy-Douglas-Adams/dp/0345391802/>\

::: {.separator style="clear: both; text-align: center;"}
[![](https://3.bp.blogspot.com/-1WKTSWJhm7U/VpBxeLV2r-I/AAAAAAAAK1k/cpeZ7HZgAaQ/s400/HitchProduct.png){width="400"
height="252"}](http://3.bp.blogspot.com/-1WKTSWJhm7U/VpBxeLV2r-I/AAAAAAAAK1k/cpeZ7HZgAaQ/s1600/HitchProduct.png)
:::

\
\... See how the price is \$6.00 USD today? It used to be \$7.00 USD the
day before. Whatever the price is at the time the test is run, we are
going to call that \$6.00 USD the **expected price**.\
\
With our test, we are going to instantiate a new book object, call it
*bookProductPage*, and call the method that we wrote that loads up all
the relevant test data on the Product Page:

</div>

<div>

\

</div>

<div>

``` {style="background-image: URL(http://2.bp.blogspot.com/_z5ltvMQPaa8/SjJXr_U2YBI/AAAAAAAAAAM/46OqEP32CJ8/s320/codebg.gif); background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 Book bookProductPage = orderActions.loadProductPageDataIntoProductObject(testBook);  
```

<div>

\

</div>

<div>

So, bookProductPage now contains:\
\

-   ProductTitle
-   Author
-   OfferPrice
-   Edition

</div>

With future tests, we can compare and contrast the values of this Book
object on the product page with other values. For now, we are just going
to compare the OfferPrice.\
\
Select the **\[ Add to Cart \]** button to add the product to the
shopping cart .\
\

::: {.separator style="clear: both; text-align: center;"}
[![](https://4.bp.blogspot.com/-LerM6xTveyo/VpBy6zKt0CI/AAAAAAAAK1w/djNwgxJ3SPE/s400/ShoppingCartReview.png){width="400"
height="197"}](http://4.bp.blogspot.com/-LerM6xTveyo/VpBy6zKt0CI/AAAAAAAAK1w/djNwgxJ3SPE/s1600/ShoppingCartReview.png)
:::

\
\... See how the Cart shows (1 item) and is \$6.00 USD? That \$6.00 will
be the **actual price**.\
\
With our test, we need to validate that the actual price equals the
expected price. We need to Assert that it is Equal.\
\

#### What the Page Object Looks Like

\
For page elements, on the ShoppingCartReview page, for this test, we
will only need to grab the price of the cart subtotal. We also will need
to write two methods:\

-   Verify we are on the ShoppingCartReview page after clicking the \[
    Add to Cart \] button. 
-   Grab the price. 

<div>

**ShoppingCartReviewPage.java**

</div>

``` {style="background-image: URL(http://2.bp.blogspot.com/_z5ltvMQPaa8/SjJXr_U2YBI/AAAAAAAAAAM/46OqEP32CJ8/s320/codebg.gif); background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
1:  package pages;  
2:  import org.openqa.selenium.By;  
3:  import org.testng.TestException;  
4:  import utils.CommonUtils;  
5:  /**  
6:   * Created by tmaher on 12/21/2015.  
7:   */  
8:  public class ShoppingCartReviewPage extends CommonUtils {  
9:     private final By PRICE = By.cssSelector("[class='a-color-price hlb-price a-inline-block a-text-bold']");  
10:    public void verifyOnShoppingCartReviewPage(){  
11:      String url = getCurrentURL();  
12:      System.out.println("SHOPPING_CART_REVIEW_PAGE: Verifying that we are on SHOPPING_CART_REVIEW_PAGE.");  
13:      if (!url.contains("view")){  
14:        throw new TestException("ERROR: Not on SHOPPING_CART_REVIEW_PAGE! URL: " + url);  
15:      }  
16:    }  
17:    public String getCartSubtotal(){  
18:      return getElementText(PRICE);  
19:    }  
20:  }  
```

<div>

\

</div>

### Retrieve the Actual Price

We already have the test object set up, login and initialization, price
retrieval from the product page, we just need to go to the
ShoppingCartReview page and retrieve that price, too\...\
**\
PurchaseOrderTest.java**\

``` {style="background-image: URL(http://2.bp.blogspot.com/_z5ltvMQPaa8/SjJXr_U2YBI/AAAAAAAAAAM/46OqEP32CJ8/s320/codebg.gif); background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
1:  @Test()  
2:    public void test_createPurchaseOrderForSingleProduct(){  
3:      Products testBook = Products.HITCHHIKERS_GUIDE;  
4:      String username = LoadProperties.user.getProperty("tester23.username");  
5:      String password = LoadProperties.user.getProperty("tester23.password");  
6:      OrderActions orderActions = new OrderActions();  
7:      ShoppingCartReviewPage shoppingCartReviewPage = new ShoppingCartReviewPage();  
8:      orderActions.initializeLogin();  
9:      orderActions.navigateToHomePage();  
10:      orderActions.loginAs(username, password);  
11:      orderActions.initializeCart();  
12:      Book bookProductPage = orderActions.loadProductPageDataIntoProductObject(testBook);  
13:      orderActions.addProductToShoppingCartReview(testBook);  
14:      String actualCartSubtotalPrice = shoppingCartReviewPage.getCartSubtotal();  
15:      String expectedBookPrice = bookProductPage.getOfferPrice();  
16:  }  
```

\
Running what we have for the test looks like\...\

``` {style="background-image: URL(http://2.bp.blogspot.com/_z5ltvMQPaa8/SjJXr_U2YBI/AAAAAAAAAAM/46OqEP32CJ8/s320/codebg.gif); background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 [TestNG] Running:  
  C:\Users\tmaher\.IdeaIC15\system\temp-testng-customsuite.xml  
 INITIALIZING: Signing out, if needed.  
   
 Navigating to Amazon.com: http://www.amazon.com  
 HOME_PAGE: Selecting [YOUR_ACCOUNT] in navigation bar.  
 HOME_PAGE: Navigating to the SIGNIN_PAGE.  
   
 SIGNIN_PAGE: Entering username: amzn.tester23@gmail.com  
 SIGNIN_PAGE: Entering password.  
 SIGNIN_PAGE: Clicking the [SIGN_IN] button.  
   
 INITIALIZING: Deleting all Items in Cart.  
   
 Starting process to load info for HITCHHIKERS_GUIDE:  
 PRODUCT_PAGE: Navigated to http://www.amazon.com/gp/product/0345391802  
 PRODUCT_PAGE: Verifying that the product title is 'The Hitchhiker's Guide to the Galaxy'  
 LOAD_INFO: Loading data...  
   
 Product Title: The Hitchhiker's Guide to the Galaxy  
 Author: Douglas Adams  
 Edition: Mass Market Paperback  
 Offer Price: $6.00  
   
 Adding HITCHHIKERS_GUIDE to cart:  
 PRODUCT_PAGE: Navigated to http://www.amazon.com/gp/product/0345391802  
 PRODUCT_PAGE: Verifying that the product title is 'The Hitchhiker's Guide to the Galaxy'  
 PRODUCT_PAGE: Clicking on [ADD_TO_CART] button.   
   
 SHOPPING_CART_REVIEW_PAGE: Verifying that we are on SHOPPING_CART_REVIEW_PAGE.  
```

\
Compare the actual price with the expected price is simple with
TestNG\... We can use an AssertEquals statement. If the actual price
doesn\'t match the expected price, the test will fail.\

###  Make Log Output More Readable

\
Having the test fail is all well and good\... but it doesn\'t match what
I would write if I was designing an impromptu test plan. I would prefer
to see (PASS) and (FAIL), such as:\
\
**TestHeading**: Describe what the test is supposed to compare:\
\

-   List the actual value
-   List the expected value
-   Mark if the test (PASS) or (FAIL)

<div>

To do this, we can create two methods in OrderActions.java: One
*checkMatchingValues*, and one which has
*outputPassOrFailOnFieldComparison*:

</div>

<div>

\

</div>

<div>

**checkMatchingValues**

</div>

<div>

``` {style="background-image: URL(http://2.bp.blogspot.com/_z5ltvMQPaa8/SjJXr_U2YBI/AAAAAAAAAAM/46OqEP32CJ8/s320/codebg.gif); background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
1:   public boolean checkMatchingValues(String testHeading, Object actualValue, Object expectedValue) {  
2:      String successMessage = "\t* The Expected and Actual Values match. (PASS)\n";  
3:      String failureMessage = "\t* The Expected and Actual Values do not match! (FAIL)\n";  
4:    
5:      boolean doesPriceMatch = false;  
6:    
7:      System.out.println(testHeading);  
8:      System.out.println("\t* Expected Value: " + expectedValue);  
9:      System.out.println("\t* Actual Value: " + actualValue);  
10:    
11:      if (actualValue.equals(expectedValue)) {  
12:        System.out.println(successMessage);  
13:        doesPriceMatch = true;  
14:      } else {  
15:        System.out.println(failureMessage);  
16:        doesPriceMatch = false;  
17:      }  
18:      return doesPriceMatch;  
19:    }  
20:  }  
```

\

</div>

<div>

\... This method is public. We want to be able to call this in our test
every time we compare values, so that it can be outputted to the logs. 

</div>

<div>

\

</div>

<div>

### The Final Version of Our Test

\
With the Assert statement and the output methods, our test now looks
like:

</div>

\
**test\_createPurchaseOrderForSingleProduct()**\

``` {style="background-image: URL(http://2.bp.blogspot.com/_z5ltvMQPaa8/SjJXr_U2YBI/AAAAAAAAAAM/46OqEP32CJ8/s320/codebg.gif); background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
1:  @Test()  
2:    public void test_createPurchaseOrderForSingleProduct(){  
3:      Products testBook = Products.HITCHHIKERS_GUIDE;  
4:      String username = LoadProperties.user.getProperty("tester23.username");  
5:      String password = LoadProperties.user.getProperty("tester23.password");  
6:      OrderActions orderActions = new OrderActions();  
7:      ShoppingCartReviewPage shoppingCartReviewPage = new ShoppingCartReviewPage();  
8:    
9:      orderActions.initializeLogin();  
10:      orderActions.navigateToHomePage();  
11:      orderActions.loginAs(username, password);  
12:      orderActions.initializeCart();  
13:    
14:      Book bookProductPage = orderActions.loadProductPageDataIntoProductObject(testBook);  
15:      orderActions.addProductToShoppingCartReview(testBook);  
16:      String actualCartSubtotalPrice = shoppingCartReviewPage.getCartSubtotal();  
17:      String expectedBookPrice = bookProductPage.getOfferPrice();  
18:      orderActions.checkMatchingValues("Verify the Price Listed for the book:", actualCartSubtotalPrice, expectedBookPrice);  
19:      assertEquals(actualCartSubtotalPrice, expectedBookPrice, "SHOPPING_CART_REVIEW: Cart Subtotal not what is expected!");  
```

\
We are passing in the following values from the test into
*checkMatchingValues*:\
\

-   **TestHeading**: \"Verify the Price Listed for the book:\"
-   **Actual Value**: actualCartTotalPrice
-   **Expected Value:** expectedBookPrice

\
If the test passes, the following output will be sent to the logs\...\
**\
Successful Test Execution:**\

``` {style="background-image: URL(http://2.bp.blogspot.com/_z5ltvMQPaa8/SjJXr_U2YBI/AAAAAAAAAAM/46OqEP32CJ8/s320/codebg.gif); background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 SHOPPING_CART_REVIEW_PAGE: Verifying that we are on SHOPPING_CART_REVIEW_PAGE.  
 Verify the Price Listed for the book:  
      * Expected Value: $6.00  
      * Actual Value: $6.00  
      * The Expected and Actual Values match. (PASS)  
   
   
 ===============================================  
 Default Suite  
 Total tests run: 1, Failures: 0, Skips: 0  
 ===============================================  
```

\
\... If there were failures, not only would the assertion fail, halting
the test,\
\

### Why Worry About Log Output?

*Why worry about the log output? Isn\'t it enough for the test to pass
or fail?*\
\
For me, it is not enough. Coming from a manual testing background, I
want to see *exactly* how the test traverses a site. Without seeing the
output explicitly spelled out as I have it, it is difficult for me to
see the test composition.\
\
Without knowing the test composition, or seeing exactly what values are
being compared and contrasted, having a test pass or fail is meaningless
to me.\
\
Just because the test claims to have passed or failed, there still could
be false positives or false negatives, as it compares and contrasts
incorrect data. 

</div>

\

<div>

**NEXT UP**: 

</div>

<div>

-   [Setup a TestNG XML so we can have Data Driven
    tests](https://www.blogger.com/2016/01/automate-amazon-sketch-of-possible-data.html) \>\>

</div>

<div>

\

</div>

> ::: {dir="ltr" lang="en"}
> [\@tjmaher1](https://twitter.com/tjmaher1) is writing a good 8 part
> case study of automating a web GUI
> using [\#Java](https://twitter.com/hashtag/Java?src=hash) and [\#Selenium](https://twitter.com/hashtag/Selenium?src=hash) [\#WebDriver](https://twitter.com/hashtag/WebDriver?src=hash) <https://t.co/ylnF64pFnh>
> :::
>
> --- Alan Richardson (\@eviltester) [January 7,
> 2016](https://twitter.com/eviltester/status/685025609156788224)

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
[-T.J.
Maher]{style="background-color: white; color: #222222; font-family: "calibri"; font-size: 15.4px; line-height: 21.56px;"}\
* Sr. QA Engineer, Fitbit*\
* Boston, MA*\
*\
// Automated tester for \[ 9 \] month and counting!*\
*\
Please note: \'Adventures in Automation\' is a personal blog about
automated testing. It is not an official blog
of [Fitbit.com](http://www.fitbit.com/). *
