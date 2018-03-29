\-\-- layout: post title: \'Test The-Internet 2.0: Page Factories:
Setting up, creating them, and understanding how they work\' date:
\'2016-06-30T23:26:00.002-04:00\' author: T.J. Maher tags: - Page Object
- test framework - Page Factory modified\_time:
\'2016-07-05T17:06:16.801-04:00\' thumbnail:
https://2.bp.blogspot.com/-MedHu5ui8gs/V3WekrjHh3I/AAAAAAAALLU/Kh-IbMJIA4QOORp2pb2fvKyh5\_mUIpgOQCLcB/s72-c/login.png
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-7415687677777184256
blogger\_orig\_url:
http://www.tjmaher.com/2016/06/page-factories-setting-up-creating-them.html
\-\-- Let\'s say we wanted to automated a Login Page such as the one on
Dave Haeffner\'s test site,
[The-Internet](http://the-internet.herokuapp.com/login). How would we
find the username, password and Login button so we can enter the
appropriate text into the appropriate text boxes?\
**[\
]{.underline}**\

  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://2.bp.blogspot.com/-MedHu5ui8gs/V3WekrjHh3I/AAAAAAAALLU/Kh-IbMJIA4QOORp2pb2fvKyh5_mUIpgOQCLcB/s400/login.png){width="400" height="283"}](https://2.bp.blogspot.com/-MedHu5ui8gs/V3WekrjHh3I/AAAAAAAALLU/Kh-IbMJIA4QOORp2pb2fvKyh5_mUIpgOQCLcB/s1600/login.png)
                                                                                                          *Dave Haeffner\'s <http://the-internet.herokuapp.com/login>*
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Like we did [last
July](http://www.tjmaher.com/2015/06/simple-manipulation-of-login-page.html), we
would make sure that Selenium WebDriver methods such as sendKeys (to
enter text) and click (to click on a button) [were safely
wrapped](http://www.tjmaher.com/2015/06/creating-common-utilities-for-webdriver.html)
in a set of common utilities, then [call these new methods by
selector](http://www.tjmaher.com/2015/07/the-internet-page-object-model-examples.html),
such as css or id.\
\
\... Or we could just use the **PageFactory**.\
\

<div>

-   Read more about [Dave
    Haeffner](http://www.tjmaher.com/2015/06/spotlight-on-dave-haeffner.html)
-   View the [PageFactory on
    GitHub](https://github.com/SeleniumHQ/selenium/blob/master/java/client/src/org/openqa/selenium/support/PageFactory.java)

</div>

\
Using it is relatively simple to implement, as shown in the illustration
below. Reading the JavaDocs and understanding how it works is much
harder.\
\
\
[]{#more}

Setting Up Page Factory and Page Object
---------------------------------------

\
A Page Object is a class that contains all our web elements for that
page. We implement the PageFactory by importing PageFactory and FindBy
into the page object. We use the \@FindBy annotations and search for the
web element by id or css selector. Then we store the result returned in
a WebElement, such as *usernameTextbox* or *passwordTextbox*, ready to
use!\
\
\

-   Need to more about [Page
    Objects](http://www.tjmaher.com/2015/05/page-objects-and-design-patterns-in.html)
    and locators?
-   Or how WebDriver [uses CSS
    Selectors](http://www.tjmaher.com/2015/04/how-selenium-webdriver-uses-css.html)?

\
\
Remember though, we need to make sure to initialize all the web
elements. Who knows what is in them when the page is created? This is
why we are using the PageFactory method *initElements* to initialize the
elements on the page, passing in an instance of the WebDriver we will be
using (*driver*), and the instance of the LoginPage (*this*).\
\
To instantiate a new Firefox browser, then pass that into a newly
created instance of the Login page object:\
\

``` {.brush: .java}
WebDriver driver = new FirefoxDriver();
LoginPage login = new LoginPage(driver);
```

\
But what could the new Login page object look like?\
\
**[LoginPage.java:]{.underline}**\

``` {.brush: .java}
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.support.FindBy;
import org.openqa.selenium.support.PageFactory;

public class LoginPage {

    private String password;

    @FindBy(id = "h2")
    private WebElement header;

    @FindBy(css = "[name='username']")
    private WebElement usernameTextbox;

    @FindBy(css = "[name='password']")
    private WebElement passwordTextbox;

    @FindBy(css = "[type='submit'][class='radius']")
    private WebElement loginButton;

    private WebDriver driver;

    public LoginPage(WebDriver driver) {
        this.driver = driver;
        PageFactory.initElements(driver, this);
    }

    public void loginAs(String username) {
        usernameTextbox.sendKeys(username);
        String password = "SuperSecretPassword!";
        passwordTextbox.sendKeys(this.password);
        loginButton.click();
    }
```

\
The loginAs method:\
\

-   Takes the value of the username and enters the text into the textbox
    using WebDriver\'s sendKeys method. 
-   Declares a String variable, entering in the super secret password.
-   Enters the password.
-   Selects the login button. 

Using the Page Factory and Page Object 
---------------------------------------

<div>

\
Now, let\'s write a test that uses the page object. 

</div>

\
**[\
]{.underline}[LoginPageTest.java:]{.underline}**\

``` {.brush: .java}
    @Test
    public void test_FirefoxLogin() throws Exception{
        driver = new FirefoxDriver();
        driver.get("http://the-internet.herokuapp.com/login");
        LoginPage login = new LoginPage(driver);
        login.loginAs("tomsmith");
        // Place assert statements here.
    }
```

\
The test will:\
\

-   Open up a new Firefox  browser and go to the Login page in the URL. 
-   Instantiate a new Login Page, passing in the Firefox driver.
-   All web elements will be located and initialized.
-   The username and password will be entered and the Login Button will
    be selected.

<div>

\... If we were doing a real test, we would have done some assertions,
searching for the success (or failure) of the login, judging by the page
we were on and the message that was displayed on the page, but that is
for the next chapter. 

</div>

<div>

\

</div>

What Happens With Web Elements Not Found?
-----------------------------------------

Before, we had to make sure that Selenium method was wrapped in try/
catch blocks in
the [CommonUtilities](http://www.tjmaher.com/2015/12/automate-amazon-commonutils-methods-and.html) library
class we created. What if an element could not be found due to a slow
loading page, or a page that could not be found? We might get an
oh-so-vague message of a *NullPointerError*.\
\
Let\'s make a typo, calling the selector for the \"username\" a
\"usernam\" and see what happens:\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 org.openqa.selenium.NoSuchElementException: Unable to locate element: {"method":"css selector","selector":"[name='usernam']"}  
 <snip>  
 *** Element info: {Using=css selector, value=[name='usernam']}  
     <snip>  
      at pages.LoginPage.loginAs(LoginPage.java:43)  
      at pages.LoginPageTest.test_FirefoxLogin(LoginPageTest.java:56)  
      </snip>  
 Caused by: org.openqa.selenium.NoSuchElementException: Unable to locate element: {"method":"css selector","selector":"[name='usernam']"}  
 For documentation on this error, please visit: http://seleniumhq.org/exceptions/no_such_element.html  
```

\
Ugh! A huge stack trace and a wall of text. It\'s not the [logging that
I like to
see](http://www.tjmaher.com/2016/02/do-you-actually-know-what-your.html) as
a former manual tester, but it is something. At least it is better than
a *NullPointerError*.\
\

How Does the Page Factory Initialization Work? 
-----------------------------------------------

Let\'s take a look at the [Page Factory
section](https://github.com/SeleniumHQ/selenium/blob/master/java/client/src/org/openqa/selenium/support/PageFactory.java)
of Selenium WebDriver to see how the page is initialized:\
\

> \"Instantiate an instance of the given class, and set a lazy proxy for
> each of the WebElement and List\<WebElement\> fields that have been
> declared, assuming that the field name is also the HTML element\'s
> \'id\' or \'name\'.\
> \
> \"This means that for the class: public class Page { private
> WebElement submit; } there will be an element that can be located
> using the xpath expression *\"//\*\[\@id=\'submit\'\]\"* or
> *\"//\*\[\@name=\'submit\'\]\"*\
> \
> \"By default, the element or the list is looked up each and every time
> a method is called upon it. To change this behaviour, simply annotate
> the field with the CacheLookup. To change how the element is located,
> use the FindBy annotation. This method will attempt to instantiate the
> class given to it, preferably using a constructor which takes a
> WebDriver instance as its only argument or falling back on a no-arg
> constructor. An exception will be thrown if the class cannot be
> instantiated\".

\
\
Did you understand that? It seems that we don\'t really need the
\@FindBy annotation if we just name the WebElement variable the same as
the element\'s name or id.\
\
When we instantiate a new LoginPage, passing along the WebDriver
instance, it then is stored in the *WebDriver driver* property of the
class, and then is passed into initElements, along with an instance of
the entire LoginPage that will be proxied: usernameTextbox,
passwordTextbox and all web elements.\
\

``` {.brush: .java}
    public LoginPage(WebDriver driver) {
        this.driver = driver;
        PageFactory.initElements(driver, this);
    }
```

\
From what I can tell:\
\

-   InitElements takes in the Firefox driver and lists our LoginPage as
    the page object to proxy.
-   PageFactory then passes these values into [instantiatePage(driver,
    pageClassToProxy)]{style="background-color: white; color: #333333; font-family: "consolas" , "liberation mono" , "menlo" , "courier" , monospace; font-size: 12px; line-height: 16.8px; white-space: pre;"}
-   An attempt is made to find the LoginPage class constructor,
    providing there is a method, no instantiation exception, run time
    exception, or illegal access.  
-   It does this by using the *java.lang.reflect.Constructor class*
-   See *pageClassToProxy.getConstructor(WebDriver.class)*
-   Then, it is returning *constructor.newInstance(driver), *capturing
    the information in the page variable back in initElements. 

\
According to JournalDev\'s [Java Reflection Example
Tutorial](http://www.journaldev.com/1789/java-reflection-example-tutorial),
\"getConstructors() method returns the list of public constructors of
the class reference of object\". We are passing in WebDriver.class,
getting that classes constructors.\
\
Only when you are using the proxy for the page class does the LoginPage
get initialized. When you actually are using the proxy, then the proxy
finally loads the web elements with the elements on the page. We don\'t
need to wrap the element up with try/ catch blocks like we did with
CommonUtils before.\
\

What about \@FindBy?
--------------------

Taking a look at the [FindBy
documentation](https://github.com/SeleniumHQ/selenium/blob/master/java/client/src/org/openqa/selenium/support/FindBy.java)
in WebDriver, you can find a locator by more than just \@FindBy(id =
\"h2\") or \@FindBy(css = \"\[name=\'username\'\]\").\
\
You can use: id, name, className, css, tagName, linkText,
partialLinkText and even xpath, if you want to live dangerously.\

> \"Used to mark a field on a Page Object to indicate an alternative
> mechanism for locating the element or a list of elements. Used in
> conjunction with PageFactory this allows users to quickly and easily
> create PageObjects.\
> \
> \"You can either use this annotation by specifying both \'how\' and
> \'using\' or by specifying one of the location strategies (eg: \"id\")
> with an appropriate value to use. Both options will delegate down to
> the matching By methods in By class\".

\
Next, we will look at setting up Selenium Grid.\
\
Until then, Happy Testing!\
\
-T.J. Maher\
Sr. QA Engineer,\
Fitbit-Boston\
\
*// QA Engineer since Aug. 1996\
// Automation developer for \[ 1.5 \] years and still counting!\
// Check out Adventures in Automation on
[Facebook](https://www.facebook.com/AdventuresInAutomation/)!*
