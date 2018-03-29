\-\-- layout: post title: \'Automate Amazon: Writing a Sign In Test\'
date: \'2015-12-31T01:30:00.000-05:00\' author: T.J. Maher tags: - code
examples - Java - WebDriver - test framework - Login modified\_time:
\'2016-04-29T07:47:26.164-04:00\' blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-6369945823202488947
blogger\_orig\_url:
http://www.tjmaher.com/2015/12/automate-amazon-writing-sign-in-test.html
\-\-- *This post is fourth of a series of nine. Need to go [back to the
beginning](/2015/12/next-week-automating-amazon-how-i-am.html)?*\
\
Drafting a Login Test for Amazon.com won\'t be as easy as [drafting one
for Dave Haeffner\'s mock site,
The-Internet](/2015/07/the-internet-writing-automated-test.html). There
needs to be a lot more infrastructure put in place besides the
CommonUtils library we worked on in the last blog post. Also, Amazon.com
use the word \"Login\". Instead, they use the phrase Sign In.\
\
[]{#more}\

### Sketch the SignIn Steps

<div>

Here\'s how you ~~log into~~ sign into Amazon.com\'s site:

</div>

<div>

1.  Go to Amazon.com\'s home page, <http://www.amazon.com/>
2.  Hover your cursor over the \"Your Account\" block, and click the
    sign in button.
3.  Once you are on the sign in page, enter the username, password into
    the appropriate text boxes. 
4.  Select the Sign In button. 

</div>

<div>

I noticed after following this process a few times, that there sometimes
was a bit of a lag, so we might want to wait until the username and
password actually appear before entering a username and password. 

</div>

<div>

\

### Review: How to find selectors of Web Elements

Let\'s say we want to know about what selectors to use for the username,
password, and Sign In button on the Sign In page.\
\
You can find the ids and cssSelectors of an object by:\

-   Opening the Firefox browser with the Firebug and Firepath plugin. 
-   Going to http://www.amazon.com/ and pressing the \"Sign In\" button.
-   Right clicking and selecting on the textboxes or the button and
    selecting \"Inspect in Firepath\".
-   With the \"Firepath\" tab, make sure \"CSS\" is selected. 

<div>

We can see that the following web elements have these values:

</div>

</div>

<div>

-   Email textbox: cssSelector \#ap\_email
-   Password textbox: cssSelector \#ap\_password
-   Sign In Button: cssSelector \#signInSubmit

<div>

\... Yes, these values are technically IDs and not CSS Selectors. Adding
the \'\#\' makes them CSS Selectors. At my workplace, I find that IDs of
web elements are constantly changing, since the ID is usually a numbered
index. CSS Values seem to change less, so I got in the habit of leaning
towards CSS Selectors over IDs. 

</div>

</div>

<div>

\

</div>

<div>

\

</div>

### Sketch out the Infrastructure Needed

<div>

Judging from what we have listed above, we will need the following
classes written:

</div>

<div>

-   A Test Class, **PurchaseOrderTest**, that stores the tests.
-   A class to store the username and password of test users, and a
    class to retrieve the data.
-   Methods in CommonUtilites that handle sending keys to textboxes,
    clicking on buttons, and hovering-and-clicking on sections of the
    home page.
-   Two classes called Page Objects to store how the **HomePage** and
    the **LoginPage** interacts with the DOM.
-   We can bundle together commonly used methods in an Actions class,
    and call it **OrderActions**.

</div>

<div>

### 

### What our Directory Structure Will Look Like

\
After we store the User Properties, create the Actions classes, and
create the test class, our directory structure could look like:\
\
**src/test/java**\
\

actions

-   OrderActions

base

-   LoadProperties

pages

-   HomePage
-   SignInPage

properties

-   user.properties

testcases

-   PurchaseOrderTest

utils

-   CommonUtils
-   DriverUtils

\
\
\

</div>

<div>

### **Store the User Properties**

\
Store the Username and Password in a text file called a Properties file,
*user.properties*. Create a class called LoadProperties in order to
handle the reading and the writing of the file. (Code formatting
from <http://codeformatter.blogspot.com/>).\
\

</div>

<div>

**java / properties / user.properties:**

</div>

``` {style="background-image: URL(http://2.bp.blogspot.com/_z5ltvMQPaa8/SjJXr_U2YBI/AAAAAAAAAAM/46OqEP32CJ8/s320/codebg.gif); background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
1:  tester23.username=amzn.tester23@gmail.com  
2:  tester23.password=amzntester23  
```

<div>

\
**java / base / LoadProperties.java**

</div>

``` {style="background-image: URL(http://2.bp.blogspot.com/_z5ltvMQPaa8/SjJXr_U2YBI/AAAAAAAAAAM/46OqEP32CJ8/s320/codebg.gif); background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
1:  package base;  
2:  import org.apache.commons.lang3.StringUtils;  
3:  import java.io.FileInputStream;  
4:  import java.io.FileNotFoundException;  
5:  import java.io.IOException;  
6:  import java.util.Properties;  
7:  import java.util.Set;  
8:  /**  
9:   * Created by tmaher on 12/22/2015.  
10:   */  
11:  public class LoadProperties {  
12:    public static Properties user = loadProperties("src/test/java/properties/user.properties");  
13:    private static Properties loadProperties(String filePath) {  
14:      Properties properties = new Properties();  
15:      try {  
16:        FileInputStream f = new FileInputStream(filePath);  
17:        properties.load(f);  
18:      } catch (FileNotFoundException e) {  
19:        e.printStackTrace();  
20:      } catch (IOException e){  
21:        e.printStackTrace();  
22:      }  
23:      return properties;  
24:    }  
25:    public static String getPropertyValue(String path, String key){  
26:      Properties p = loadProperties(path);  
27:      String result = "";  
28:      Set<String> values = p.stringPropertyNames();  
29:      for(String value : values){  
30:        if(StringUtils.equalsIgnoreCase(value, key)){  
31:          result = p.getProperty(value);  
32:          break;  
33:        }  
34:      }  
35:      return result;  
36:    }  
37:  }  
```

<div>

*All Source Code can be found in T.J.
Maher\'s [Automate-Amazon](https://github.com/tjmaher/automate-amazon/tree/master/automate-amazon/src/test/java) repository. *

</div>

<div>

\
Next, we can work from the bottom level to the top:\

-   Adding methods to CommonUtils
-   Abstracting each page into a PageObject such as HomePage and
    SignInPage
-   Bundling the methods in the PageObjects to create repeatable Actions
    we can use.
-   Compose the Actions methods into a test we can run. 

</div>

<div>

### 1. Add to CommonUtil 

Add to CommonUtils methods the basic building blocks our page objects
will call. All Selenium WebDriver calls will be encapsulated in a method
on CommonUtils.\
\

-   **Navigate to a URL**

\

``` {style="background-image: URL(http://2.bp.blogspot.com/_z5ltvMQPaa8/SjJXr_U2YBI/AAAAAAAAAAM/46OqEP32CJ8/s320/codebg.gif); background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 public void navigateToURL(String URL) {  
     try {  
       _driver.navigate().to(URL);  
     } catch (Exception e) {  
       System.out.println("FAILURE: URL did not load: " + URL);  
       throw new TestException("URL did not load");  
     }  
   }  
```

\

-   **SendKeys to a Textbox**, given the web element by selector, and
    the value.

\

``` {style="background-image: URL(http://2.bp.blogspot.com/_z5ltvMQPaa8/SjJXr_U2YBI/AAAAAAAAAAM/46OqEP32CJ8/s320/codebg.gif); background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 public void sendKeys(By selector, String value) {  
     WebElement element = getElement(selector);  
     clearField(element);  
     try {  
       element.sendKeys(value);  
     } catch (Exception e) {  
       throw new TestException(String.format("Error in sending [%s] to the following element: [%s]", value, selector.toString()));  
     }  
 }  
```

\

-   **Click on a button**, given the web element by selector

\

``` {style="background-image: URL(http://2.bp.blogspot.com/_z5ltvMQPaa8/SjJXr_U2YBI/AAAAAAAAAAM/46OqEP32CJ8/s320/codebg.gif); background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 public void click(By selector) {  
     WebElement element = getElement(selector);  
     waitForElementToBeClickable(selector);  
     try {  
       element.click();  
     } catch (Exception e) {  
       throw new TestException(String.format("The following element is not clickable: [%s]", selector));  
     }  
   }  
```

\

-   **Hovers a cursor** over a web element and click it

``` {style="background-image: URL(http://2.bp.blogspot.com/_z5ltvMQPaa8/SjJXr_U2YBI/AAAAAAAAAAM/46OqEP32CJ8/s320/codebg.gif); background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 public void scrollToThenClick(By selector) {  
     WebElement element = _driver.findElement(selector);  
     actions = new Actions(_driver);  
     try {  
       ((JavascriptExecutor) _driver).executeScript("arguments[0].scrollIntoView(true);", element);  
       actions.moveToElement(element).perform();  
       actions.click(element).perform();  
     } catch (Exception e) {  
       throw new TestException(String.format("The following element is not clickable: [%s]", element.toString()));  
     }  
   }  
```

\
\

-   **Waits Until an Element is Visible**

``` {style="background-image: URL(http://2.bp.blogspot.com/_z5ltvMQPaa8/SjJXr_U2YBI/AAAAAAAAAAM/46OqEP32CJ8/s320/codebg.gif); background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 public void waitForElementToBeVisible(By selector) {  
     try {  
       wait = new WebDriverWait(_driver, timeout);  
       wait.until(ExpectedConditions.presenceOfElementLocated(selector));  
     } catch (Exception e) {  
       throw new NoSuchElementException(String.format("The following element was not visible: %s", selector));  
     }  
   }  
```

\

### 2. Page Objects

Now that the Selenium WebDriver functionality has been encapsulated, we
can extend the page objects to use CommonUtils. We are inheriting from
CommonUtilites the above methods.\
\
These Page Objects are the only places that should interact with the web
elements on the page, evaluating if the web elements are there, checking
and setting their values.\
\
On the top of each Page Object, we have the selectors for each web
element. They are each declared *private* because they are only to be
accessed in this page object. They are also declared *final* because
they are constant.\
\
*By* is a reserved word in the Selenium library. Web elements can be
found By.id, By.cssSelector, By.name, etc.\
\
\
\
**HomePage:**\

``` {style="background-image: URL(http://2.bp.blogspot.com/_z5ltvMQPaa8/SjJXr_U2YBI/AAAAAAAAAAM/46OqEP32CJ8/s320/codebg.gif); background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
1:  package pages;  
2:  import enums.Url;  
3:  import org.openqa.selenium.By;  
4:  import utils.CommonUtils;  
5:  /**  
6:   * Created by tmaher on 12/21/2015.  
7:   */  
8:  public class HomePage extends CommonUtils {  
9:    private final By YOUR_ACCOUNT = By.id("nav-link-yourAccount");  
10:    private final By SHOPPING_CART_ICON = By.cssSelector("#nav-cart");  
11:    private final By SHOPPING_CART_COUNT = By.cssSelector("#nav-cart > #nav-cart-count");  
12:    public HomePage(){  
13:    }  
14:    public void navigateToHomePage() {  
15:      String url = Url.BASEURL.getURL();  
16:      System.out.println("Navigating to Amazon.com: " + url);  
17:      navigateToURL(url);  
18:    }  
19:    public void navigateToSignInPage(){  
20:      System.out.println("HOME_PAGE: Selecting [YOUR_ACCOUNT] in navigation bar.");  
21:      scrollToThenClick(YOUR_ACCOUNT);  
22:      System.out.println("HOME_PAGE: Navigating to the SIGNIN_PAGE.\n");  
23:    }  
24:  }  
```

\
**SignInPage:**\

``` {style="background-image: URL(http://2.bp.blogspot.com/_z5ltvMQPaa8/SjJXr_U2YBI/AAAAAAAAAAM/46OqEP32CJ8/s320/codebg.gif); background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
1:  package pages;  
2:  import org.openqa.selenium.By;  
3:  import utils.CommonUtils;  
4:  /**  
5:   * Created by tmaher on 12/21/2015.  
6:   */  
7:  public class SignInPage extends CommonUtils {  
8:    private final By USERNAME = By.cssSelector("#ap_email");  
9:    private final By PASSWORD = By.cssSelector("#ap_password");  
10:    private final By SIGNIN_BUTTON = By.cssSelector("#signInSubmit");  
11:    public void enterUsername(String userName){  
12:      System.out.println("SIGNIN_PAGE: Entering username: " + userName);  
13:      waitForElementToBeVisible(USERNAME);  
14:      sendKeys(USERNAME, userName);  
15:    }  
16:    public void enterPassword(String password){  
17:      System.out.println("SIGNIN_PAGE: Entering password.");  
18:      waitForElementToBeVisible(PASSWORD);  
19:      sendKeys(PASSWORD, password);  
20:    }  
21:    public void clickSignInButton(){  
22:      System.out.println("SIGNIN_PAGE: Clicking the [SIGN_IN] button.\n");  
23:      click(SIGNIN_BUTTON);  
24:    }  
25:  }  
```

\

</div>

### 3. Actions Classes

When someone enters a username into the SignIn page, it\'s a safe bet
that they are going to want to enter a password, too, along with
clicking on the SignIn button. If someone wants to write a test that
explicitly asserts that yes, we can enter text into the username
textbox, they can do that by accessing the SignIn page object. But most
of the time, those three methods will be grouped together.\
\
Below, we group them together in a method called **loginAs**(String
username, String password). Pass in a username and password, and it will
do the rest.\
\
**OrderActions.java**\

``` {style="background-image: URL(http://2.bp.blogspot.com/_z5ltvMQPaa8/SjJXr_U2YBI/AAAAAAAAAAM/46OqEP32CJ8/s320/codebg.gif); background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
1:  package actions;  
2:  import pages.*;  
3:  /**  
4:   * Created by tmaher on 12/21/2015.  
5:   */  
6:  public class OrderActions {  
7:    public void navigateToHomePage(){  
8:      HomePage homePage = new HomePage(); // Instantiate a new HomePage page object 
9:      homePage.navigateToHomePage();  
10:    }  
11:    public void loginAs(String username, String password){  
12:      HomePage homePage = new HomePage();  // Instantiate a new HomePage page object 
13:      SignInPage signIn = new SignInPage();  // Instantiate a new SignInPage page object 
14:      homePage.navigateToSignInPage();  
15:      signIn.enterUsername(username);  // Use the methods on the SignInPage
16:      signIn.enterPassword(password);  
17:      signIn.clickSignInButton();  
18:    }  
19:  }  
```

\
\

### 4. PurchaseOrderTest: test\_Login

Now that we have all the components, we can start assembling the pieces
in the Actions class to form a test.\
\
**PurchaseOrderTest.java**\

``` {style="background-image: URL(http://2.bp.blogspot.com/_z5ltvMQPaa8/SjJXr_U2YBI/AAAAAAAAAAM/46OqEP32CJ8/s320/codebg.gif); background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
1:  package testcases;  
2:  import base.LoadProperties;  
3:  import org.openqa.selenium.WebDriver;  
4:  import actions.*;  
5:  import org.testng.annotations.AfterClass;  
6:  import org.testng.annotations.BeforeClass;  
7:  import org.testng.annotations.Test;  
8:  import utils.DriverUtils;  
9:  import static org.testng.Assert.assertEquals;  
10:  /**  
11:   * Created by tmaher on 12/14/2015.  
12:   */  
13:  public class PurchaseOrderTest {  
14:    public WebDriver driver;  
15:    @BeforeClass  
16:    public void setUp(){  
17:      driver = DriverUtils.getDriver();  
18:    }  
19:    @Test()  
20:    public void test_Login(){  
21:      OrderActions orderActions = new OrderActions();  
22:      String username = LoadProperties.user.getProperty("tester23.username");  
23:      String password = LoadProperties.user.getProperty("tester23.password");  
24:      orderActions.navigateToHomePage();  
25:      orderActions.loginAs(username, password);  
26:   
27:    }  
28:    @AfterClass  
29:    public void tearDown(){  
30:      driver.quit();  
31:    }  
32:  }  
```

*All Source Code can be found in T.J.
Maher\'s [Automate-Amazon](https://github.com/tjmaher/automate-amazon/tree/master/automate-amazon/src/test/java) repository. *\

###  5. Run the Test

\
Now that everything is all set, we can right click on the test method
for test\_Login and run the test:\
\

``` {style="background-image: URL(http://2.bp.blogspot.com/_z5ltvMQPaa8/SjJXr_U2YBI/AAAAAAAAAAM/46OqEP32CJ8/s320/codebg.gif); background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 Navigating to Amazon.com: http://www.amazon.com  
 HOME_PAGE: Selecting [YOUR_ACCOUNT] in navigation bar.  
 HOME_PAGE: Navigating to the SIGNIN_PAGE.  
 SIGNIN_PAGE: Entering username: amzn.tester23@gmail.com  
 SIGNIN_PAGE: Entering password.  
 SIGNIN_PAGE: Clicking the [SIGN_IN] button.  
```

*All Source Code can be found in T.J.
Maher\'s [Automate-Amazon](https://github.com/tjmaher/automate-amazon/tree/master/automate-amazon/src/test/java) repository. *\
*\
*\... Normally, we would then assert if we are on the correct page or
not. I didn\'t add that into the test since what I really wanted to do
was the next blog entry.\
\
Until then, happy coding!\
\

### View the (mostly) Completed Test Code:

-   All test code can be found on GitHub
    at [Automate-Amazon](https://github.com/tjmaher/automate-amazon/tree/master/automate-amazon/src/test/java).

\
**NEXT**: [Setup Objects to Handle Various Products, such as Books!
\>\> ](/2016/01/automate-amazon-productenums-and.html)\
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
of [Fitbit.com](http://www.fitbit.com/). *\
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
