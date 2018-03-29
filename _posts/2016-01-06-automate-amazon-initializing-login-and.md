\-\-- layout: post title: \'Automate Amazon: Initializing Login and
Cart\' date: \'2016-01-06T19:15:00.000-05:00\' author: T.J. Maher tags:
- code examples - Java - WebDriver - test framework modified\_time:
\'2016-04-29T07:44:40.450-04:00\' blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-9112391319743402945
blogger\_orig\_url:
http://www.tjmaher.com/2016/01/automate-amazon-initializing-login-and.html
\-\-- *This post is sixth of a series of nine. Need to go [back to the
beginning](/2015/12/next-week-automating-amazon-how-i-am.html)?*\
\
While drafting the tests to handle adding products to the shopping cart,
I came across two problems:\
\

-   I kept on on finding that I was logged into my personal Amazon.com
    account instead of the test account. 
-   From one session to the next, Amazon kept remembering what I had in
    my shopping cart the test before. 

<div>

Before the test is run, we need to initialize the login session, and
clear all items found in the cart.\
\
[]{#more}\
**Please Note**:  Using the GUI is the WORST possible way to initialize
the cart or the login. It is far better to use some behind-the-scenes
method the automated test could call in the \@BeforeClass method to be
used during setup of the test.\
\
We are writing this functionality this way only because I can\'t think
of any other way besides do it how I have outlined. Have a better way?
Thoughts? Please add to the comments.\
\
I haven\'t been an automated tester for long. Feel free to give me
pointers!

</div>

\

### What our Directory Structure Will Look Like

\
For this blog entry, we will be expanding upon the what we already had,
so the directory structure will remain the same, except for a new page
object called ShoppingCartPage.\
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

pojo

-   Book

properties

-   user.properties

testcases

-   PurchaseOrderTest

utils

-   CommonUtils
-   DriverUtils

### Initialize the Login

<div>

Initializing the Login is simple. When I am signed
into <http://www.amazon.com/>, I see on the horizontal navigation bar,
\"Hello, Thomas / Your Account\". When you hover your cursor over that
area, and scroll to the bottom, you can see \"Not Thomas? Sign Out\". 

</div>

<div>

\

</div>

<div>

By clicking on the link, you are directed to
<http://www.amazon.com//gp/flex/sign-out.html>. Before you start your
test, you can go to this link and whether or not you are logged in, you
can sign out. 

</div>

<div>

\

</div>

<div>

With this information, we can update our PurchaseOrderTest, our
OrderActions, and Url enum.

</div>

<div>

\

</div>

<div>

**PurchaseOrderTest Addition:**\

``` {style="background-image: URL(http://2.bp.blogspot.com/_z5ltvMQPaa8/SjJXr_U2YBI/AAAAAAAAAAM/46OqEP32CJ8/s320/codebg.gif); background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 orderActions.initializeLogin();  
```

**\
OrderActions Addition:**\

``` {style="background-image: URL(http://2.bp.blogspot.com/_z5ltvMQPaa8/SjJXr_U2YBI/AAAAAAAAAAM/46OqEP32CJ8/s320/codebg.gif); background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
   public void initializeLogin(){  
     System.out.println("INITIALIZING: Signing out, if needed.\n");  
     signOut();  
   }  
   public void signOut(){  
     HomePage homePage = new HomePage();  
     homePage.signOutWithSignOutLink();  
   }  
```

\
**HomePage Addition:**\

``` {style="background-image: URL(http://2.bp.blogspot.com/_z5ltvMQPaa8/SjJXr_U2YBI/AAAAAAAAAAM/46OqEP32CJ8/s320/codebg.gif); background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
   public void signOutWithSignOutLink(){  
     String url = Url.BASEURL.getURL() + Url.SIGNOUT.getURL();  
     navigateToURL(url);  
   }  
```

\
**Url Enum now looks like:**\

``` {style="background-image: URL(http://2.bp.blogspot.com/_z5ltvMQPaa8/SjJXr_U2YBI/AAAAAAAAAAM/46OqEP32CJ8/s320/codebg.gif); background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 public enum Url {  
   PRODUCT_SECTION("/gp/product"),  
   BASEURL("http://www.amazon.com"),  
   SIGNOUT("/gp/flex/sign-out.html");  
   String url;  
   Url(String url){  
     this.url = url;  
   }  
   public String getURL() {  
     return url;  
   }  
 }  
```

\
\... Could this be done all in one method? Definitely! But by
abstracting things out, it makes the code a lot easier to read, and a
lot easier to find what classes you need to add to.\
\

### Initialize the Shopping Cart

</div>

<div>

Initializing the Shopping Cart is a bit more complex. It involves:\
\

-   **Check if the Shopping Cart icon already lists \'0\'**: Looking at
    the shopping cart icon in the horizontal navigation bar, you can see
    that the value isn\'t a graphic. It is just a number in a string
    that we can get and check if the value is already \'0\'.
-   **If not \'0\', go to the Shopping Cart**: Click on the Shopping
    Cart icon to go to the Shopping Cart. 
-   **Get All Delete Buttons**: Gather up all the web elements that are
    a delete button. 
-   **Click all Delete Buttons**: One by one, get the delete button, and
    click on it, removing the item from the cart.

<div>

If we wanted to make this more robust, we could check that at the end of
the process that the cart is empty. With this first pass, we are going
to leave it as is. 

</div>

<div>

**\
**

</div>

<div>

**PurchaseOrderTest Addition:**

</div>

<div>

``` {style="background-image: URL(http://2.bp.blogspot.com/_z5ltvMQPaa8/SjJXr_U2YBI/AAAAAAAAAAM/46OqEP32CJ8/s320/codebg.gif); background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 @Test()  
   public void test_createPurchaseOrderForSingleProduct(){   
     String username = LoadProperties.user.getProperty("tester23.username");  
     String password = LoadProperties.user.getProperty("tester23.password");  
     OrderActions orderActions = new OrderActions();  
     orderActions.initializeLogin();  
     orderActions.navigateToHomePage();  
     orderActions.loginAs(username, password);  
     orderActions.initializeCart();  
 }  
```

</div>

<div>

\
\

-   First, we make sure that all users are logged out.
-   Then, we log in with our test user.
-   We navigate to the home page (http://www.amazon.com/)
-   We use the LoginAs method to log in. 
-   Once we are logged in, we can use the initializeCart method in
    OrderActions.

</div>

<div>

\
**OrderActions Additions:**

</div>

<div>

``` {style="background-image: URL(http://2.bp.blogspot.com/_z5ltvMQPaa8/SjJXr_U2YBI/AAAAAAAAAAM/46OqEP32CJ8/s320/codebg.gif); background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
   public void initializeCart(){  
     System.out.println("INITIALIZING: Deleting all Items in Cart.\n");  
     deleteAllItemsIfAnyFromCart();  
   }  
   public void deleteAllItemsIfAnyFromCart(){  
     HomePage homePage = new HomePage();  
     ShoppingCartPage shoppingCartPage = new ShoppingCartPage();  
     String itemsInCart = homePage.getNumberOfItemsListedInShoppingCartIcon();  
     if (!itemsInCart.equals("0")){  
       homePage.selectShoppingCartIcon();  
       shoppingCartPage.deleteAllItemsInCart();  
     } else {  
       System.out.println("\t* There are already '0' items in the Shopping Cart.");  
     }  
   }  
```

</div>

<div>

\

</div>

<div>

\
**HomePage, what it now looks like:**\

``` {style="background-image: URL(http://2.bp.blogspot.com/_z5ltvMQPaa8/SjJXr_U2YBI/AAAAAAAAAAM/46OqEP32CJ8/s320/codebg.gif); background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 public class HomePage extends CommonUtils {  
   private final By YOUR_ACCOUNT = By.id("nav-link-yourAccount");  
   private final By SHOPPING_CART_ICON = By.cssSelector("#nav-cart");  
   private final By SHOPPING_CART_COUNT = By.cssSelector("#nav-cart > #nav-cart-count");  
   public HomePage(){  
   }  
   public void navigateToHomePage() {  
     String url = Url.BASEURL.getURL();  
     System.out.println("Navigating to Amazon.com: " + url);  
     navigateToURL(url);  
   }  
   public void navigateToSignInPage(){  
     System.out.println("HOME_PAGE: Selecting [YOUR_ACCOUNT] in navigation bar.");  
     scrollToThenClick(YOUR_ACCOUNT);  
     System.out.println("HOME_PAGE: Navigating to the SIGNIN_PAGE.\n");  
   }  
   public void signOutWithSignOutLink(){  
     String url = Url.BASEURL.getURL() + Url.SIGNOUT.getURL();  
     navigateToURL(url);  
   }  
   public void selectShoppingCartIcon(){  
     click(SHOPPING_CART_ICON);  
   }  
   public String getNumberOfItemsListedInShoppingCartIcon(){  
     return getElementText(SHOPPING_CART_COUNT);  
   }  
 }  
```

\
Note that the \#nav-cart-count is actually a child of \#nav-cart. You
need to call the main element, what I dubbed the \"YOUR\_ACCOUNT\" web
element, then get the child element.\
\
\

</div>

<div>

**Create a new ShoppingCartPage:**\

``` {style="background-image: URL(http://2.bp.blogspot.com/_z5ltvMQPaa8/SjJXr_U2YBI/AAAAAAAAAAM/46OqEP32CJ8/s320/codebg.gif); background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
1:  import java.util.List;  
2:  /**  
3:   * Created by tmaher on 12/21/2015.  
4:   */  
5:  public class ShoppingCartPage extends CommonUtils {  
6:    private final By SHOPPING_CART_HEADER = By.cssSelector("h1");  
7:    private final By DELETE_BUTTONS = By.cssSelector("input[value='Delete']");  
8:    private final String SHOPPING_CART_EMPTY_MSG = "Your Shopping Cart is empty.";  
9:    public void verifyOnShoppingCartPage(){  
10:      String url = getCurrentURL();  
11:      System.out.println("SHOPPING_CART_PAGE: Verifying that we are on SHOPPING_CART_PAGE.");  
12:      if (!url.contains("cart")){  
13:        throw new TestException("ERROR: Not on SHOPPING_CART_PAGE! URL: " + url);  
14:      }  
15:    }  
16:    public String getShoppingCartMessage(){  
17:      return getElementText(SHOPPING_CART_HEADER);  
18:    }  
19:    boolean checkIfShoppingCartHeaderListsEmptyMessage(){  
20:      String actualMessage = getShoppingCartMessage();  
21:      return (actualMessage.equals(SHOPPING_CART_EMPTY_MSG));  
22:    }  
23:    public void deleteAllItemsInCart(){  
24:      List<WebElement> deleteButtons = getElements(DELETE_BUTTONS);  
25:      for ( WebElement button : deleteButtons ){  
26:        button.click();  
27:      }  
28:    }  
29:  }  
```

\

</div>

<div>

With the deleteAllItemsInCart method, we can get all the delete button
items, and click every one of them in the list. 

</div>

<div>

\

</div>

</div>

<div>

**CommonUtils methods used:**

</div>

<div>

``` {style="background-image: URL(http://2.bp.blogspot.com/_z5ltvMQPaa8/SjJXr_U2YBI/AAAAAAAAAAM/46OqEP32CJ8/s320/codebg.gif); background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
   public List<WebElement> getElements(By Selector) {  
     waitForElementToBeVisible(Selector);  
     try {  
       return _driver.findElements(Selector);  
     } catch (Exception e) {  
       throw new NoSuchElementException(String.format("The following element did not display: [%s] ", Selector.toString()));  
     }  
   }  
```

</div>

\
\
\... In the next blog post we can finally add the product to the
Shopping Cart Review page and check that the values are what is
expected.\
\
\
Happy coding!\
\

<div>

\

</div>

> ::: {dir="ltr" lang="en"}
> [\@tjmaher1](https://twitter.com/tjmaher1) is writing a good 8 part
> case study of automating a web GUI using
> [\#Java](https://twitter.com/hashtag/Java?src=hash) and
> [\#Selenium](https://twitter.com/hashtag/Selenium?src=hash)
> [\#WebDriver](https://twitter.com/hashtag/WebDriver?src=hash)
> <https://t.co/ylnF64pFnh>
> :::
>
> --- Alan Richardson (\@eviltester) [January 7,
> 2016](https://twitter.com/eviltester/status/685025609156788224)

\
\
**NEXT:** [Writing a Shopping Cart
Test](/2016/01/automate-amazon-writing-shopping-cart.html)\

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
