\-\-- layout: post title: \'The-Internet: Page Object Model examples\'
date: \'2015-07-28T22:33:00.001-04:00\' author: T.J. Maher tags: - code
examples - beginner - Page Object - test framework - Dave Haeffner
modified\_time: \'2016-04-29T19:57:05.325-04:00\' thumbnail:
https://4.bp.blogspot.com/-kdk5F9nQysE/VZNjkZlB68I/AAAAAAAAKvk/4X2jFoEQtZM/s72-c/login.png
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-3491846563612475010
blogger\_orig\_url:
http://www.tjmaher.com/2015/07/the-internet-page-object-model-examples.html
\-\--

::: {style="font-size: medium; font-weight: normal;"}
[*Writing automated test code to test against Dave Haeffner\'s mock
site, The-Internet: [Login
Page](https://the-internet.herokuapp.com/login).*]{style="font-family: inherit;"}
:::

*This post is fifth in a series of six. Need to go [back to the
beginning](/2015/06/simple-manipulation-of-login-page.html)?*\
\

Part Five: What is the Page Object Model?  
-------------------------------------------

<div>

### According to the original Selenium Wiki

<div>

The **Page Object Model** appeared as early as March of 2013, on the
wiki for Selenium WebDriver.
<https://code.google.com/p/selenium/wiki/PageObjects>

</div>

<div>

\
[]{#more}\

</div>

<div>

Imagine modelling a Java class on a Login page. 

</div>

</div>

<div>

\

</div>

  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://4.bp.blogspot.com/-kdk5F9nQysE/VZNjkZlB68I/AAAAAAAAKvk/4X2jFoEQtZM/s320/login.png){width="320" height="279"}](http://4.bp.blogspot.com/-kdk5F9nQysE/VZNjkZlB68I/AAAAAAAAKvk/4X2jFoEQtZM/s1600/login.png)
                                                                                               Welcome to **The-Internet**!
  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

<div>

<div>

\

</div>

<div>

<div>

There are two major actions you can do on a Login page: 

</div>

<div>

-   Create a successful login
-   Create an unsuccessful login. 

</div>

</div>

<div>

One could create one method for each action one could perform in a
page. 

</div>

<div>

\

</div>

<div>

With their early example, they have methods to type a username and
password, click a submit button, methods that handle a login success and
a login failure, and a method called \"*loginAs*\" which accepts the
strings for a Username and Password and wraps up all the methods that
*typeUsername(username)*, *typePassword(password)*, and returns the
*submitLogin()*.  

</div>

<div>

\

</div>

<div>

<div>

They advise, in general, not to make assertions on the page. Those are
for the tests, themselves. 

</div>

</div>

<div>

\

</div>

<div>

For more information you can go to [Selenium Wiki: Page
Objects](https://code.google.com/p/selenium/wiki/PageObjects) on
Google.Code.Com 

</div>

<div>

\

</div>

<div>

Originally, the concept encapsulating objects of a page dealt with the
window of a user interface, not a web browser. See [Window
Driver](http://martinfowler.com/eaaDev/WindowDriver.html) by Martin
Fowler, *8/26/2004,* also from ThoughtWorks, the company that brought
you Selenium 1 and Selenium 2: WebDriver. * *

</div>

<div>

\

</div>

<div>

**Note**: The Selenium Wiki information is out of date. For archival
purposes, you can [browse the
wiki](https://code.google.com/p/selenium/w/list) which has been in
existence since Selenium WebDriver first came out. The new home for the
documentation is at <https://seleniumhq.github.io/docs/>

</div>

<div>

\

</div>

### According to the new Selenium Wiki

<div>

\

</div>

<div>

With the new wiki, the Page Object model is now referred to as a \"Page
Object Design Pattern\". Instead of informal language of the earlier
wiki, it speaks in the language of a software professional. 

</div>

<div>

\

</div>

<div>

**Why use Page Objects?**

</div>

<div>

\

</div>

> -   \"**Readable:** Business stake holders can understand it.
> -   \"**Writable**: Easy to write, avoids unnecessary duplication.
> -   \"**Extensible**: Functionality can (reasonably) be added without
>     breaking contracts and existing functionality.
> -   \"**Maintainable**: By leaving the implementation details out of
>     test cases, you are well-insulated against changes to the
>     \[automated test\]
>
> \"\[\...\] This method completely abstracts the concepts of input
> fields, buttons, clicking, and even pages from your test code. Using
> this approach, all your tester has to do is call this method. This
> gives you a maintenance advantage: if the login fields ever changed,
> you would only ever have to change this method\--not your tests\".

</div>

<div>

### Page Object Example

</div>

<div>

We could write a Page Object for the Login page of The-Internet as such:

</div>

<div>

\

</div>

<div>

</div>

<div>

\

</div>

With this example, we have three main methods of the LoginPage class:\
\

-   **enterUserName**: Pass a username as a String, and this method will
    send the username into the textbox. 
-   **enterPassword**: Likewise, pass a password as a String, and this
    method will send the password into the textbox. 
-   **logIntoPage**: Send the username and password, such as the test
    user data stored in an enum fashion for this example, and it will
    call the above methods to enter the username and password, and click
    the Login button. 

<div>

But what are those odd lines of code that is not exactly Selenium?

</div>

<div>

<div>

-   waitForElementToBeVisible(LoginPageEnum.PASSWORD.selector());
-   sendKeys(LoginPageEnum.USERNAME.selector(), user);
-   click(LoginPageEnum.LOGIN\_BUTTON.selector());

</div>

</div>

<div>

Just as we do at my workplace, I encapsulated some of the code:\
\
**[LoginPageEnum.java]{.underline}**

</div>

<div>

\

</div>

\

<div>

\

</div>

<div>

-   **Locators on the *LoginPage* are being stored as Enums**: Since
    locators could be in either By.id or By.cssSelector, I created an
    interface, ISelector and implemented it in the enum class. Adding
    the name of the enum in the method and \"*.selector()*\" after it is
    an easy way to make the code more readable. To see the full code,
    you can scroll to the bottom of
    the [LoginPage](https://github.com/tjmaher/WebDriver_TheInternet_Advanced/blob/master/src/test/java/pages/LoginPage.java) I
    have listed on GitHub.

<div>

\

</div>

<div>

**[CommonUtils.java]{.underline}**

</div>

</div>

<div>

\
\

\

-   **Commonly used WebDriver functionality is stored in a class,
    CommonUtils**: Need to handle syncing? Logging functionality? The
    methods in the CommonUtils class act as a wrapper. To see the full
    code, you can go to
    the [CommonUtils](https://github.com/tjmaher/WebDriver_TheInternet_Advanced/blob/master/src/test/java/utils/CommonUtils.java) page
    I have listed on GitHub.

\
\
\
\

</div>

<div>

The working code for the PageObjects
[LoginPage](https://github.com/tjmaher/WebDriver_TheInternet_Advanced/blob/master/src/test/java/pages/LoginPage.java)
and
[SecureArea](https://github.com/tjmaher/WebDriver_TheInternet_Advanced/blob/master/src/test/java/pages/SecureArea.java) along
with
[CommonUtils](https://github.com/tjmaher/WebDriver_TheInternet_Advanced/blob/master/src/test/java/utils/CommonUtils.java),
and the enum
class [UserEnum.java](https://github.com/tjmaher/WebDriver_TheInternet_Advanced/blob/master/src/test/java/enums/UserEnum.java) can
be found in my GitHub repository,
[WebDriver\_TheInternet\_Advanced](https://github.com/tjmaher/WebDriver_TheInternet_Advanced).\
\
\

</div>

<div>

Now that we have done all this work, in the next blog post, we can write
out our test\...\
\
**NEXT:** [Writing the Automated
Test](/2015/07/the-internet-writing-automated-test.html)\
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
-T.J. Maher\
* Sr. QA Engineer, Fitbit*\
* Boston, MA*\
*\
// Automated tester for \[ 4 \] month and counting!*\
*\
Please note: \'Adventures in Automation\' is a personal blog about
automated testing. It is not an official blog
of [Fitbit.com](http://www.fitbit.com/). *

</div>
