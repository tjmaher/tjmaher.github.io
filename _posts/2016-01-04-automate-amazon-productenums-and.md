\-\-- layout: post title: \'Automate Amazon: ProductEnums and
ProductObjects\' date: \'2016-01-04T00:20:00.000-05:00\' author: T.J.
Maher tags: - code examples - Java - Page Object - pojos - WebDriver -
test framework modified\_time: \'2016-04-29T07:51:38.118-04:00\'
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-7518099358610300990
blogger\_orig\_url:
http://www.tjmaher.com/2016/01/automate-amazon-productenums-and.html
\-\-- *This post is fifth of a series of nine. Need to go [back to the
beginning](/2015/12/next-week-automating-amazon-how-i-am.html)?*\
\
What good would a shopping cart test be without adding any test
products? Let\'s investigate how to get to the product items on Amazon.\
\

### What our Directory Structure Will Look Like

\
After we store Url and Product locations in Enums, add to the the
Actions classes, create a Book pojo to store values of a Book product,
and add the ProductsPage page object, our test structure could look like
this:\
\
[]{#more}\
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

pojo

-   Book

properties

-   user.properties

testcases

-   PurchaseOrderTest

utils

-   CommonUtils
-   DriverUtils

\

###  

### Store Product Locations in Enums

<div>

<div>

1.  When I searched for Douglas Adams\' The Hitchhiker\'s Guide to the
    Galaxy, I saw there were many different versions of the four book
    \"trilogy\". The Mass Market Paperback edition was
    at <http://www.amazon.com/gp/product/0345391802>.
2.  After a bit more investigation, I saw that all product information
    was stored in the same subfolders /gp/product, and had a series of
    numbers that referenced the product. 

</div>

</div>

<div>

Under my **src/test/java** created a subfolder named \"**enums**\", and
created two new enum classes: Url and Products.

</div>

<div>

\

</div>

<div>

**Url.java**

</div>

<div>

``` {style="background-image: URL(http://2.bp.blogspot.com/_z5ltvMQPaa8/SjJXr_U2YBI/AAAAAAAAAAM/46OqEP32CJ8/s320/codebg.gif); background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
1:  package enums;  
2:  /**  
3:   * Created by tmaher on 12/22/2015.  
4:   */  
5:  public enum Url {  
6:    PRODUCT_SECTION("/gp/product"),  
7:    BASEURL("http://www.amazon.com");  
8:     
9:    String url;  
10:    Url(String url){  
11:      this.url = url;  
12:    }  
13:    public String getURL() {  
14:      return url;  
15:    }  
16:  }  
```

<div>

\
\... If we were to grow the tests into different sections, we could add
the different product sections here.\
\
Why turn the URL into a constant? What if you wanted to use the same
automation script on different environments, such as if they had
internal test servers such as \"qa2.amazon.com\" or \"qa1.amazon.com\"?
This way we can store all the different types of environments in the
same place.\
\

</div>

<div>

**Products.java**

</div>

``` {style="background-image: URL(http://2.bp.blogspot.com/_z5ltvMQPaa8/SjJXr_U2YBI/AAAAAAAAAAM/46OqEP32CJ8/s320/codebg.gif); background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
1:  package enums;  
2:  /**  
3:   * Created by tmaher on 12/22/2015.  
4:   */  
5:  public enum Products {  
6:    HITCHHIKERS_GUIDE("0345391802", "The Hitchhiker's Guide to the Galaxy");  
7:    // The price will always fluctuate. The product id and product title will be more or less constant.  
8:    private String id;  
9:    private String productTitle;  
10:    Products(String id, String productTitle){  
11:      this.id = id;  
12:      this.productTitle = productTitle;  
13:    }  
14:    public String getProductId(){  
15:      return id;  
16:    }  
17:    public String getProductTitle(){  
18:      return productTitle;  
19:    }  
20:  }  
```

<div>

\

</div>

<div>

\... We can have a whole series of test products, each with their own
enum, id, and product title. We can expand this enum to store more
constants. I don\'t believe we should ever store \"price\" in an enum,
since it always seems to fluctuate.\
\
Now, to navigate to the product page, it would be:

</div>

<div>

\

</div>

``` {style="background-image: URL(http://2.bp.blogspot.com/_z5ltvMQPaa8/SjJXr_U2YBI/AAAAAAAAAAM/46OqEP32CJ8/s320/codebg.gif); background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
1:   public void navigateToProductPage(Products product){  
2:      String url = Url.BASEURL.getURL() + Url.PRODUCT_SECTION.getURL() + "/" + product.getProductId();  
3:      navigateToURL(url);  
4:      System.out.println("PRODUCT_PAGE: Navigated to " + url);  
5:    }  
```

### ProductPage

If you go to the Product Page for The Hitchhiker\'s Guide to the
Galaxy, <http://www.amazon.com/gp/product/0345391802>, you can see a few
product properties you might want to retrieve and store in case you
wanted to compare them to the product properties you see listed as you
go through the process of making a purchase.\
\
For example, there is:\
\

-   Product Title: You can check that the title listed is the same one
    as in the Product enum.
-   Author: The author, no matter what version, will be the late great
    Douglas Adams.
-   Edition: Mass Market Paperback
-   Price: Some days it is \$6.00. Some days it is \$7.00. No matter
    what the price is that day, we need to make sure that as you add the
    product to the cart, and check out with the product, that the same
    price is retained. 
-   There is also the Add to Cart button we may want to click. 

\
You can find out how to interact with these web elements by firing up
Firefox, right clicking on the elements, \"Inspect in Firepath\", and
see what turns up under a CSS Selector.\
\
Under the subdirectory, \"pages\" we could have:\
\
**ProductPage.java**\

``` {style="background-image: URL(http://2.bp.blogspot.com/_z5ltvMQPaa8/SjJXr_U2YBI/AAAAAAAAAAM/46OqEP32CJ8/s320/codebg.gif); background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
1:  package pages;  
2:  import enums.Products;  
3:  import enums.Url;  
4:  import org.openqa.selenium.By;  
5:  import org.testng.TestException;  
6:  import utils.CommonUtils;  
7:  /**  
8:   * Created by tmaher on 12/21/2015.  
9:   */  
10:  public class ProductPage extends CommonUtils {  
11:    private final By PRODUCT_TITLE = By.cssSelector("#productTitle");  
12:    private final By AUTHOR = By.cssSelector(".a-link-normal.contributorNameID");  
13:    private final By EDITION = By.cssSelector(".a-size-medium.a-color-secondary.a-text-normal");  
14:    private final By PRICE = By.cssSelector(".a-size-medium.a-color-price.offer-price.a-text-normal");  
15:    private final By ADD_TO_CART = By.cssSelector("#add-to-cart-button");  
16:    public void navigateToProductPage(Products product){  
17:      String url = Url.BASEURL.getURL() + Url.PRODUCT_SECTION.getURL() + "/" + product.getProductId();  
18:      navigateToURL(url);  
19:      System.out.println("PRODUCT_PAGE: Navigated to " + url);  
20:    }  
21:    public void verifyProductTitle(String expectedTitle){  
22:      String actualTitle = getProductTitle();  
23:      System.out.println("PRODUCT_PAGE: Verifying that the product title is '" + actualTitle + "'");  
24:      if (!expectedTitle.equals(actualTitle)){  
25:        throw new TestException("ERROR: PRODUCT_PAGE: Product Title is ['" + actualTitle + "']. Expected ['" + expectedTitle + "'].");  
26:      }  
27:    }  
28:    public String getProductTitle(){  
29:      return getElementText(PRODUCT_TITLE);  
30:    }  
31:    public String getAuthor(){  
32:      return getElementText(AUTHOR);  
33:    }  
34:    public String getEdition(){  
35:      return getElementText(EDITION);  
36:    }  
37:    public String getPrice(){  
38:      return getElementText(PRICE);  
39:    }  
40:    public void clickAddToCart(){  
41:      System.out.println("PRODUCT_PAGE: Clicking on [ADD_TO_CART] button. \n");  
42:      click(ADD_TO_CART);  
43:    }  
44:  }  
```

\

### Creating the Book object

Now that we have a way to retrieve values, we can create a way to store
values. When it comes to test products, the simplest way might be in a
**Plain Old Java Object**, or *pojo*.\
\
What is a pojo?\
\

> *\"The term was coined while Rebecca Parsons, Josh MacKenzie and I
> were preparing for a talk at a conference in September 2000. In the
> talk we were pointing out the many benefits of encoding business logic
> into regular java objects rather than using Entity Beans. We wondered
> why people were so against using regular objects in their systems and
> concluded that it was because simple objects lacked a fancy name. So
> we gave them one, and it\'s caught on very nicely\". - [Martin
> Fowler](http://www.martinfowler.com/bliki/POJO.html), from his
> [self-titled site](http://www.martinfowler.com/). *

We can use the methods we created with the ProductPage to design a
method to load up the object.\
\
The internal variables that we initialize are:\
\

-   private String productTitle = \"\";
-   private String author = \"\";
-   private String offerPrice = \"\";
-   private String edition = \"\";

\
We can \@Override the toString method, so instead of printing only the
name of the object to the console, we can print out the internal
variables.\
\
**Book.java**\

``` {style="background-image: URL(http://2.bp.blogspot.com/_z5ltvMQPaa8/SjJXr_U2YBI/AAAAAAAAAAM/46OqEP32CJ8/s320/codebg.gif); background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
1:  package pojo;  
2:  import org.testng.TestException;  
3:  import pages.ProductPage;  
4:  /**  
5:   * Created by tmaher on 12/22/2015.  
6:   */  
7:  public class Book {  
8:    private String productTitle = "";  
9:    private String author = "";  
10:    private String offerPrice = "";  
11:    private String edition = "";  
12:    public Book(){  
13:    }  
14:    @Override  
15:    public String toString(){  
16:      return String.format(  
17:          "Product Title: " + this.productTitle + "\n"  
18:          + "Author: " + this.author + "\n"  
19:          + "Edition: " + this.edition + "\n"  
20:          + "Offer Price: " + this.offerPrice + "\n"  
21:      );  
22:    }  
23:    public void loadInfoFromProductPage(){  
24:      ProductPage productPage = new ProductPage();  
25:      String currentURL = productPage.getCurrentURL();  
26:      if (!currentURL.contains("product")){  
27:        throw new TestException("LOAD INFO ERROR: Product data should only be loaded from product page!\nCurrent URL: " + currentURL);  
28:      } else {  
29:        System.out.println("LOAD_INFO: Loading data...\n");  
30:        this.productTitle = productPage.getProductTitle();  
31:        this.author = productPage.getAuthor();  
32:        this.offerPrice = productPage.getPrice();  
33:        this.edition = productPage.getEdition();  
34:      }  
35:    }  
36:    public String getProductTitle() {  
37:      return productTitle;  
38:    }  
39:    public void setProductTitle(String productTitle) {  
40:      this.productTitle = productTitle;  
41:    }  
42:    public String getAuthor() {  
43:      return author;  
44:    }  
45:    public void setAuthor(String author) {  
46:      this.author = author;  
47:    }  
48:    public String getOfferPrice() {  
49:      return offerPrice;  
50:    }  
51:    public void setOfferPrice(String offerPrice) {  
52:      this.offerPrice = offerPrice;  
53:    }  
54:    public String getEdition() {  
55:      return edition;  
56:    }  
57:    public void setEdition(String edition) {  
58:      this.edition = edition;  
59:    }  
60:  }  
```

\

### Expanding the Purchase Order Test

Now, we can expand the PurchaseOrderTest to create a new
test, test\_createPurchaseOrderForSingleProduct, built upon the code for
the test\_Login.\
\
\
**\
PurchaseOrderTest.java**\

``` {style="background-image: URL(http://2.bp.blogspot.com/_z5ltvMQPaa8/SjJXr_U2YBI/AAAAAAAAAAM/46OqEP32CJ8/s320/codebg.gif); background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
1:  package testcases;  
2:  import base.LoadProperties;  
3:  import enums.Products;  
4:  import org.openqa.selenium.WebDriver;  
5:  import actions.*;  
6:  import org.testng.annotations.AfterClass;  
7:  import org.testng.annotations.BeforeClass;  
8:  import org.testng.annotations.Test;  
9:  import pages.ShoppingCartReviewPage;  
10:  import pojo.Book;  
11:  import utils.DriverUtils;  
12:  import static org.testng.Assert.assertEquals;  
13:  /**  
14:   * Created by tmaher on 12/14/2015.  
15:   */  
16:  public class PurchaseOrderTest {  
17:    public WebDriver driver;  
18:    @BeforeClass  
19:    public void setUp(){  
20:      driver = DriverUtils.getDriver();  
21:    }  
22:    @Test()  
23:    public void test_createPurchaseOrderForSingleProduct(){  
24:      Products testBook = Products.HITCHHIKERS_GUIDE;  
25:      String username = LoadProperties.user.getProperty("tester23.username");  
26:      String password = LoadProperties.user.getProperty("tester23.password");  
27:      OrderActions orderActions = new OrderActions();  
28:      orderActions.navigateToHomePage();  
29:      orderActions.loginAs(username, password);  
30:      Book bookProductPage = orderActions.loadProductPageDataIntoProductObject(testBook);  
31:    }  
32:    @AfterClass  
33:    public void tearDown(){  
34:      driver.quit();  
35:    }  
36:  }  
```

</div>

\
Here we are:\

-   Instantiating a new Products enum called testBook. 
-   Setting the value of testBook as *Products.HITCHHIKERS\_GUIDE*.
-   Setting Tester23\'s username and password.
-   Instantiating the Page Object called orderActions, so we can use the
    navigateToHomePage and loginAs methods. 
-   We then create a new instance of the Book pojo, calling it
    *bookProductPage* since it will hold all the values found on the
    product page.
-   We are then calling the method of
    *loadProductPageDataIntoProductObject* to retrieve the data from the
    product page and place it in the Book object we just created. 

\
But how exactly does the object, once created at runtime, get the
values?\
\
**OrderActions.java**\

``` {style="background-image: URL(http://2.bp.blogspot.com/_z5ltvMQPaa8/SjJXr_U2YBI/AAAAAAAAAAM/46OqEP32CJ8/s320/codebg.gif); background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
1:  package actions;  
2:  import enums.Products;  
3:  import pages.*;  
4:  import pojo.Book;  
5:  /**  
6:   * Created by tmaher on 12/21/2015.  
7:   */  
8:  public class OrderActions {  
9:    public void navigateToHomePage(){  
10:      HomePage homePage = new HomePage();  
11:      homePage.navigateToHomePage();  
12:    }  
13:    public void loginAs(String username, String password){  
14:      HomePage homePage = new HomePage();  
15:      SignInPage signIn = new SignInPage();  
16:      homePage.navigateToSignInPage();  
17:      signIn.enterUsername(username);  
18:      signIn.enterPassword(password);  
19:      signIn.clickSignInButton();  
20:    }  
21:    public Book loadProductPageDataIntoProductObject(Products product){  
22:      System.out.println("Starting process to load info for " + product + ":");  
23:      Book book = new Book();  
24:      ProductPage productPage = new ProductPage();  
25:      productPage.navigateToProductPage(product);  
26:      productPage.verifyProductTitle(product.getProductTitle());  
27:      book.loadInfoFromProductPage();  
28:      System.out.println(book + "\n");  
29:      return book;  
30:    }  
31:  }  
```

\
The method *loadProductPageDataIntoProductObject:*\
\

-   Takes in the value Products.HITCHHIKERSGUIDE and assigns it to the
    test product.
-   Creates a new instance of Book pojo.
-   Calls an instance of the ProductPage page object so we can use its
    methods.
-   Navigates to the product page using the BASEURL + PRODUCT\_SECTION +
    PRODUCTID we were talking about earlier. 
-   We load the info from the ProductPage.
-   We print out the values to the console. 

\
When we run the test, it prints out:\
\

``` {style="background-image: URL(http://2.bp.blogspot.com/_z5ltvMQPaa8/SjJXr_U2YBI/AAAAAAAAAAM/46OqEP32CJ8/s320/codebg.gif); background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 Navigating to Amazon.com: http://www.amazon.com  
 HOME_PAGE: Selecting [YOUR_ACCOUNT] in navigation bar.  
 HOME_PAGE: Navigating to the SIGNIN_PAGE.  

 SIGNIN_PAGE: Entering username: amzn.tester23@gmail.com  
 SIGNIN_PAGE: Entering password.  
 SIGNIN_PAGE: Clicking the [SIGN_IN] button.  
 
 Starting process to load info for HITCHHIKERS_GUIDE:  
 PRODUCT_PAGE: Navigated to http://www.amazon.com/gp/product/0345391802  
 PRODUCT_PAGE: Verifying that the product title is 'The Hitchhiker's Guide to the Galaxy'
  
 LOAD_INFO: Loading data... 
 
 Product Title: The Hitchhiker's Guide to the Galaxy  
 Author: Douglas Adams  
 Edition: Mass Market Paperback  
 Offer Price: $6.00  
```

\
With the next blog entry we can investigate adding a product into the
cart and initializing the cart.\
\
Happy coding!\
\
\
**NEXT**: [Let\'s Initialize the Shopping Cart and the Login
\>\>](/2016/01/automate-amazon-initializing-login-and.html)\
\
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
// Automated tester for \[ 8 \] month and counting!*\
*\
Please note: \'Adventures in Automation\' is a personal blog about
automated testing. It is not an official blog
of [Fitbit.com](http://www.fitbit.com/). *
