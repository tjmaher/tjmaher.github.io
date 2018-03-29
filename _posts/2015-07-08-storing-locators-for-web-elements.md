\-\-- layout: post title: \'The-Internet: Storing locators for web
elements\' date: \'2015-07-08T23:13:00.002-04:00\' author: T.J. Maher
tags: - code examples - beginner - test framework - Dave Haeffner
modified\_time: \'2016-04-29T19:58:51.402-04:00\' thumbnail:
https://3.bp.blogspot.com/-kdk5F9nQysE/VZNjkZlB68I/AAAAAAAAKvg/XclQTHm\_zDI/s72-c/login.png
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-3384885800991507861
blogger\_orig\_url:
http://www.tjmaher.com/2015/07/storing-locators-for-web-elements.html
\-\-- *Writing automated test code to test against Dave Haeffner\'s mock
site, The-Internet: [Login
Page](https://the-internet.herokuapp.com/login).*\
\
*This post is fourth in a series of six. Need to go [back to the
beginning](/2015/06/simple-manipulation-of-login-page.html)?*\
\

Part Four: Storing locators in Enums
------------------------------------

### How to locate a web element? 

\
There are two main they locate web elements at work:\
\

-   By ID
-   By CSS Selector

Earlier, I wrote about [CSS
Selectors](/2015/04/how-selenium-webdriver-uses-css.html)when finding
web elements.\
\
With the Firefox browser and the Firebug plugin, to find the selectors
of a web element, an automated tester can go to the [Login
Page](https://the-internet.herokuapp.com/login) of Dave Haeffner\'s test
site, The-Internet, and right-click on each element listed:\
[]{#more}\

  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://3.bp.blogspot.com/-kdk5F9nQysE/VZNjkZlB68I/AAAAAAAAKvg/XclQTHm_zDI/s400/login.png){width="400" height="348"}](http://3.bp.blogspot.com/-kdk5F9nQysE/VZNjkZlB68I/AAAAAAAAKvg/XclQTHm_zDI/s1600/login.png)
                                                                                               Welcome to **The-Internet**. 
  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

\
\
There are three main web elements on the page:  the **Username**
textbox, the **Password** textbox, and the **Login** button.\
\
If you have [Firefox](https://www.mozilla.org/en-US/firefox/new/) with
the [Firebug plugin](https://getfirebug.com/downloads) and
[Firepath](https://addons.mozilla.org/En-us/firefox/addon/firepath/) installed,
you can go to each element, right-click on the element, and select
\"Inspect in Firepath\":\
\
**Username** textbox:\
\

-   *\<input id=\"username\" type=\"text\" name=\"username\"/\>*

\
\
**Password** textbox:\
\

-   *\<input id=\"password\" type=\"password\" name=\"password\"/\>*

\
\
**Login** button:\
\

-   *\<button class=\"radius\" type=\"submit\"\>*

\
\
We see that an automated tester can choose to select the web elements by
either Id or by CSS Selector. For this example, just to illustrate how
they are used, I will use CSS selectors. They are:\

-   The Username textbox: \[name=\'username\'\]
-   The Password textbox: \[name=\'password\'\]
-   The Login button: \[class=\'radius\'\]\[type=\'submit\'\]

But the question is, once you find the selectors \-- whether by CSS
selectors or by id \-- where would they be stored? It would be bad form
to store them in code along with the automated test:\
\
[WebElement txtUsername =
driver.findElement(By.id(\"username\"));]{style="font-family: "courier new" , "courier" , monospace;"}

<div>

[System.out.println(\"Entering
username\...\");]{style="font-family: "courier new" , "courier" , monospace;"}

</div>

<div>

[txtUsername.sendKeys(username);]{style="font-family: "courier new" , "courier" , monospace;"}

</div>

<div>

\

</div>

<div>

\... What if the id or name changes? How can you easily find the name of
the elements if they need to be updated? 

</div>

<div>

\

</div>

<div>

One solution is to store these values as constants as **Enums. **which I
covered briefly [in my last blog
entry](http://adventuresinautomation.blogspot.com/2015/07/how-java-stores-constants-static-final.html).\
[\
]{style="line-height: 19.2000007629395px;"}We could have stored them in
constants in Java by setting up some String variables to
be[ ]{style="line-height: 19.2000007629395px;"}[[**public static final**
]{style="font-family: "courier new" , "courier" , monospace;"}[like
so]{style="font-family: inherit;"}[: ]{style="font-family: "courier new" , "courier" , monospace; font-weight: bold;"}]{style="line-height: 19.2000007629395px;"}

</div>

<div>

\

</div>

<div>

<div>

public class LoginPageConstants {

</div>

<div>

\

</div>

<div>

[ ]{.Apple-tab-span style="white-space: pre;"}public static final String
USERNAME = \"\[name=\'username\'\]\";

</div>

<div>

[ ]{.Apple-tab-span style="white-space: pre;"}public static final String
PASSWORD = \"\[name=\'password\'\]\");

</div>

<div>

[ ]{.Apple-tab-span style="white-space: pre;"}public static final String
LOGIN\_BUTTON = \"\[type=\'submit\'\]\[class=\'radius\'\]\";

</div>

<div>

\

</div>

<div>

}

</div>

</div>

<div>

\

</div>

<div>

These variable strings USERNAME, PASSWORD, and LOGIN are global
constants. They can only have the preceding values that we have set,
cannot be accidentally overwritten, wherever they are used. 

</div>

<div>

\

</div>

<div>

#### What are some of the problems of using [public static final]{style="font-family: "courier new" , "courier" , monospace;"}? 

</div>

<div>

\

</div>

<div>

***From the [Java 1.5 Language
Guide](http://docs.oracle.com/javase/1.5.0/docs/guide/language/enums.html):***

</div>

> [*\"This pattern has many problems, such
> as:*]{style="background-color: white;"}\
>
> > -   ***\"Not typesafe** - Since a season is just an `int` you can
> >     pass in any other `int` value where a season is required, or add
> >     two seasons together (which makes no sense).*
> >
> > <!-- -->
> >
> > -   ***\"No namespace** - You must prefix constants of an int enum
> >     with a string (in this case `SEASON_`) to avoid collisions with
> >     other int enum types.*
> >
> > <!-- -->
> >
> > -   ***\"Brittleness** - Because \[\...\] enums are compile-time
> >     constants, they are compiled into clients that use them. If a
> >     new constant is added between two existing constants or the
> >     order is changed, clients must be recompiled. If they are not,
> >     they will still run, but their behavior will be undefined.*
> >
> > <!-- -->
> >
> > -   ***\"Printed values are uninformative** - Because they are just
> >     ints, if you print one out all you get is a number, which tells
> >     you nothing about what it represents, or even what type it is.*

#### 

### How do we store the values of the locators?

\
Storing the values of the locators, we can use enums that may look
like:\
\
[public enum LoginPageEnum implements
ISelector{]{style="font-family: "courier new" , "courier" , monospace;"}\
[\
]{style="font-family: "courier new" , "courier" , monospace;"}[[
]{.Apple-tab-span
style="white-space: pre;"}HEADER(\"h2\"),]{style="font-family: "courier new" , "courier" , monospace;"}\
[ [ ]{.Apple-tab-span
style="white-space: pre;"}USERNAME(\"\[name=\'username\'\]\"),]{style="font-family: "courier new" , "courier" , monospace;"}\
[[ ]{.Apple-tab-span
style="white-space: pre;"}PASSWORD(\"\[name=\'password\'\]\"),]{style="font-family: "courier new" , "courier" , monospace;"}\
[[ ]{.Apple-tab-span
style="white-space: pre;"}LOGIN\_BUTTON(\"\[type=\'submit\'\]\[class=\'radius\'\]\");]{style="font-family: "courier new" , "courier" , monospace;"}\
[\
]{style="font-family: "courier new" , "courier" , monospace;"}[}]{style="font-family: "courier new" , "courier" , monospace;"}\
\
\
Note: If you want to see the full example, you can examine my test code
at [test/java/pages/LoginPage.java](http://test/java/pages/LoginPage.java).\
\
With the above code, we have also captured the locator for the Header
(\"Login Page\").\
\

### How do we access the values that we have stored? 

\

-   A String variable, *id*, is declared in the enum class, to stand for
    the locator for the web element.
-   We can use this variable to access the value in the enum. 
-   We have an interface that passes information By selector, since in
    WebDriver, selectors can pass the locators **By id** or **By
    cssSelector**, and we want to handle both types. To use this
    interface, ISelector, the LoginPageEnum is set up to *implement*
    ISelector. 
-   We even have array capturing the major web elements, in case we want
    to loop through them to see if the element *.isDisplayed()*

\
\
        String id;\
\
        private LoginPageEnum(String Id){\
            this.id = Id;\
        }\
\
        public String getId(){\
            return id;\
        }\
\
        public By selector() {\
            return By.cssSelector(getId());\
        }\
\
        public LoginPageEnum\[\] getDefaultElements(){\
            return new LoginPageEnum\[\] {USERNAME, PASSWORD,
LOGIN\_BUTTON};\
        }\
\
\
For the interface
[ISelector](https://github.com/tjmaher/WebDriver_TheInternet_Advanced/blob/master/src/test/java/interfaces/ISelector.java):\
\
[package
interfaces;]{style="font-family: "courier new" , "courier" , monospace;"}\
[\
]{style="font-family: "courier new" , "courier" , monospace;"}[import
org.openqa.selenium.By;]{style="font-family: "courier new" , "courier" , monospace;"}\
[\
]{style="font-family: "courier new" , "courier" , monospace;"}[public
interface ISelector
{]{style="font-family: "courier new" , "courier" , monospace;"}\
[\
]{style="font-family: "courier new" , "courier" , monospace;"}[       
public By
selector();]{style="font-family: "courier new" , "courier" , monospace;"}\
[}]{style="font-family: "courier new" , "courier" , monospace;"}

<div>

\
The source code for this interface can be found
at [test/java/interfaces/ISelector.java](http://test/java/interfaces/ISelector.java).

</div>

<div>

\

### What is an interface?

<div>

> *\"There are a number of situations in software engineering when it is
> important for disparate groups of programmers to agree to a
> \"contract\" that spells out how their software interacts. Each group
> should be able to write their code without any knowledge of how the
> other group\'s code is written. Generally speaking, interfaces are
> such contracts.* 

> *\"\[\...\] In the Java programming language, an interface is a
> reference type, similar to a class, that can contain only constants,
> method signatures, default methods, static methods, and nested types.
> Method bodies exist only for default methods and static methods.
> Interfaces cannot be instantiated---they can only be implemented by
> classes or extended by other interfaces. * 

> *\"To use an interface, you write a class that implements the
> interface. When an instantiable class implements an interface, it
> provides a method body for each of the methods declared in the
> interface\".\
> - [The Java Tutorials:
> Interfaces](https://docs.oracle.com/javase/tutorial/java/IandI/createinterface.html)*

</div>

<div>

Note that the LoginPageEnum *implements* the ISelector interface. 

</div>

### 

### How to use these selectors to find elements? 

#### Finding the text of the Header

Now that all the prep-work is complete, to find the HEADER selector, we
can use \".selector()\":\
\

> HEADER.selector().

</div>

<div>

If we wanted to create a method to grab the Header text, such as \"Login
Page\" on the Login screen:\
\
[public String
getHeaderText(){]{style="font-family: "courier new" , "courier" , monospace;"}\
\
[ ]{.Apple-tab-span
style="white-space: pre;"}System.out.println(\"Header is: \" +
getElementText(LoginPageEnum.HEADER.selector()));\
        return getElementText(LoginPageEnum.HEADER.selector());\
\
}\
\

### Finding the other web elements using Selectors

\
Likewise, in order to find the selectors for the web elements, all we
need to do is to import LoginPageEnum, and then use:\
\
\

<div>

-   LoginPageEnum.USERNAME.selector()
-   LoginPageEnum.PASSWORD.selector()
-   LoginPageEnum.LOGIN\_BUTTON.selector()

\
\
**NEXT:** [Page Object
Model](/2015/07/the-internet-page-object-model-examples.html)\
\

::: {#toc-section .toc-section}
**Testing The-Internet:**

-   **Part One:** [Sketching out the simple manipulation of a login
    page](/2015/06/simple-manipulation-of-login-page.html)
-   **Part Two:** [Drafting Common
    Utilities](/2015/06/creating-common-utilities-for-webdriver.html)
-   **Part Three:** [Storing Constanst: public final vs
    enums](/2015/07/how-java-stores-constants-static-final.html)
-   **Part Four:** [Storing locators in
    enums](/2015/07/storing-locators-for-web-elements.html)
-   **Part Five:** [Page Object
    Model](/2015/07/the-internet-page-object-model-examples.html)
-   **Part Six:** [Writing the Automated
    Test](/2015/07/the-internet-writing-automated-test.html)
-   **Source Code:** [GitHub, T.J.
    Maher](https://github.com/tjmaher/WebDriver_TheInternet_Advanced)
:::

\
\
\
\
-T.J. Maher\
* Sr. QA Engineer, Fitbit*\
* Boston, MA*\
*\
// Automated tester for \[ 4 \] month and counting!*\
*\
Please note: \'Adventures in Automation\' is a personal blog about
automated testing. It is not an official blog
of [Fitbit.com](http://www.fitbit.com/). *\
\
\

</div>

</div>
