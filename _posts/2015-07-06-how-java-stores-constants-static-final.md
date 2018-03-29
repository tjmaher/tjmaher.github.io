\-\-- layout: post title: \'The-Internet: Storing constants: static
final vs enums\' date: \'2015-07-06T01:15:00.001-04:00\' author: T.J.
Maher tags: - code examples - beginner - Page Object - test framework -
Dave Haeffner modified\_time: \'2016-04-29T19:58:15.805-04:00\'
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-868232293441013708
blogger\_orig\_url:
http://www.tjmaher.com/2015/07/how-java-stores-constants-static-final.html
\-\--

### Testing The-Internet:

[*Rewriting the automated test code we use at work to test against Dave
Haeffner\'s mock site, The-Internet: [Login
Page](https://the-internet.herokuapp.com/login).*]{style="font-family: inherit; font-weight: normal;"}\
\
*This post is third in a series of six. Need to go [back to the
beginning](/2015/06/simple-manipulation-of-login-page.html)?*\
\
\

**Part Three**: Storing Constants 
----------------------------------

<div>

### Setting Constants Using Static Final

<div>

When using values such as the username and password of a Login screen
hardcoding values within your automated test is a bad idea. 

</div>

<div>

\

</div>

<div>

If there was an automated test that was to go
to <https://the-internet.herokuapp.com/login> and enter the username and
password for Tom Smith (*tomsmith / SuperSecretPassword!*).

</div>

<div>

\
[]{#more}\

</div>

<div>

> WebElement txtUsername = driver.findElement(By.id(\"username\"));\
> System.out.println(\"Entering username\...\");\
> txtUsername.sendKeys(\"tomsmith\"); 

> WebElement txtPassword = driver.findElement(By.id(\"password\"));\
> System.out.println(\"Entering password\...\");\
> txtPassword.sendKeys(\"SuperSecretPassword!\");

</div>

<div>

What if the username or password changes? How can you easily find the
users that need to be updated? 

</div>

<div>

\

</div>

<div>

With the username and password embedded in the test, the test is not
easily maintainable. 

</div>

<div>

\

</div>

<div>

<div>

Before these enumerated data types were introduced into Java 1.5, we
could only have declared them as **[public static
final: ]{style="font-family: "courier new" , "courier" , monospace;"}**

</div>

<div>

\

</div>

<div>

Let\'s examine parts of the code I wrote in my initial quick and dirty
test of Dave Haeffner\'s site
in <https://github.com/tjmaher/WebDriver_TheInternet_Basics/blob/master/src/test/java/SimpleManipulationWebElements.java>:

</div>

<div>

\

</div>

<div>

> [private static final String USERNAME =
> \"tomsmith\";]{style="font-family: inherit;"}[private static final
> String PASSWORD =
> \"SuperSecretPassword!\";]{style="font-family: inherit;"}[\
> ]{style="font-family: inherit;"}\...\
> \...\
> txtUsername.sendKeys(username); *// enters the username into the
> textbox*\
> txtPassword.sendKeys(password); *// enters the password into the
> textbox*

</div>

</div>

<div>

\

</div>

<div>

The Java keywords **static** and **final** are how you declare
constants. 

</div>

<div>

\

</div>

<div>

About the keyword **static**: 

</div>

> *\"Sometimes, you want to have variables that are common to all
> objects. This is accomplished with the static modifier. Fields that
> have the **static** modifier in their declaration are called static
> fields or class variables. They are associated with the class, rather
> than with any object. Every instance of the class shares a class
> variable, which is in one fixed location in memory. Any object can
> change the value of a class variable, but class variables can also be
> manipulated without creating an instance of the class\". - The Java
> Tutorials: [Classes and
> Objects](https://docs.oracle.com/javase/tutorial/java/javaOO/classvars.html)*

<div>

About the keyword **final**:

</div>

<div>

> *\"The static modifier, in combination with the final modifier, is
> also used to define constants. The final modifier indicates that the
> value of this field cannot change.* 

> *\"For example, the following variable declaration defines a constant
> named PI, whose value is an approximation of pi (the ratio of the
> circumference of a circle to its diameter):* 

> *\"static final double PI = 3.141592653589793;* 

> *\"Constants defined in this way cannot be reassigned, and it is a
> compile-time error if your program tries to do so. By convention, the
> names of constant values are spelled in uppercase letters. If the name
> is composed of more than one word, the words are separated by an
> underscore (\_)\".- The Java Tutorials: [Classes and
> Objects](https://docs.oracle.com/javase/tutorial/java/javaOO/classvars.html)*

</div>

<div>

*\
*

</div>

### Setting Constants using Enums

<div>

Another solution is to store these USERNAME and PASSWORD values
as **Enums**. 

</div>

<div>

\

</div>

<div>

> *[\"An enum type is a special data type that enables for a variable to
> be a set of predefined constants. The variable must be equal to one of
> the values that have been predefined for it. Common examples include
> compass directions (values of NORTH, SOUTH, EAST, and WEST) and the
> days of the week.]{style="font-family: inherit;"} *

> *[\"Because they are constants, the names of an enum type\'s fields
> are in uppercase letters.]{style="font-family: inherit;"}[In the Java
> programming language, you define an enum type by using
> the `enum` keyword \[\...\]]{style="font-family: inherit;"}*

> [*\"[You should use enum types any time you need to represent a fixed
> set of constants. That includes natural enum types such as the planets
> in our solar system and data sets where you know all possible values
> at compile time---for example, the choices on a menu, command line
> flags, and so
> on.]{style="line-height: 19.2000007629395px;"} \-- [**Enum
> Types**,](https://docs.oracle.com/javase/tutorial/java/javaOO/enum.html) The
> Java Tutorials, Oracle.com. *]{style="font-family: inherit;"}

</div>

</div>

<div>

\

</div>

<div>

These variable strings USERNAME and PASSWORD are global constants. They
can only have the preceding values that we have set, cannot be
accidentally overwritten, wherever they are used. 

</div>

<div>

\

</div>

<div>

What are some of the problems of using [public static
final]{style="font-family: "courier new" , "courier" , monospace;"}? 

</div>

<div>

\

</div>

<div>

***From the [Java 1.5 Language
Guide](http://docs.oracle.com/javase/1.5.0/docs/guide/language/enums.html):***

</div>

> [*\"*]{style="background-color: white;"}*public static final int
> SEASON\_WINTER = 0;*

> *public static final int SEASON\_SPRING = 1;*

> *public static final int SEASON\_SUMMER = 2;*

> *public static final int SEASON\_FALL   = 3;*

> [*This pattern has many problems, such
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
> > -   ***\"Brittleness** - Because int enums are compile-time
> >     constants, they are compiled into clients that use them. If a
> >     new constant is added between two existing constants or the
> >     order is changed, clients must be recompiled. If they are not,
> >     they will still run, but their behavior will be undefined.*
> >
> > <!-- -->
> >
> > -   ***\"Printed values are uninformative** - Because they are just
> >     ints, if you print one out all you get is \[text\], which tells
> >     you nothing about what it represents, or even what type it is.*

> *[\[\...\] \"So when should you use enums? Any time you need a fixed
> set of constants. That includes natural enumerated types (like the
> planets, days of the week, and suits in a card deck) as well as other
> sets where you know all possible values at compile time, such as
> choices on a menu, rounding modes, command line flags, and the
> like.\"]{style="background-color: white;"} * 

In the Seasons example above, they mention that using enums, it could
look like:\
\

> *\"enum Season { WINTER, SPRING, SUMMER, FALL }\"*

### 

### Using Enums to Store Usernames and Passwords

By using enums, we can group a test user\'s login credentials, both
username and password. Here is an example I wrote based on what we are
currently using at work at the time:\
\
[public enum UserEnum
{]{style="font-family: "courier new" , "courier" , monospace;"}\
[\
]{style="font-family: "courier new" , "courier" , monospace;"}[   
TOM\_SMITH(\"tomsmith\",\"SuperSecretPassword!\");]{style="font-family: "courier new" , "courier" , monospace;"}\
[\
]{style="font-family: "courier new" , "courier" , monospace;"}[   
String
userName;]{style="font-family: "courier new" , "courier" , monospace;"}\
[    String
password;]{style="font-family: "courier new" , "courier" , monospace;"}\
[\
]{style="font-family: "courier new" , "courier" , monospace;"}[   
private UserEnum(String UserName, String
Password){]{style="font-family: "courier new" , "courier" , monospace;"}\
[       
this.userName=UserName;]{style="font-family: "courier new" , "courier" , monospace;"}\
[       
this.password=Password;]{style="font-family: "courier new" , "courier" , monospace;"}\
[    }]{style="font-family: "courier new" , "courier" , monospace;"}\
[\
]{style="font-family: "courier new" , "courier" , monospace;"}[   
public String
getUserName(){]{style="font-family: "courier new" , "courier" , monospace;"}\
[        return
userName;]{style="font-family: "courier new" , "courier" , monospace;"}\
[    }]{style="font-family: "courier new" , "courier" , monospace;"}\
[\
]{style="font-family: "courier new" , "courier" , monospace;"}[   
public String
getPassword(){]{style="font-family: "courier new" , "courier" , monospace;"}\
[        return
password;]{style="font-family: "courier new" , "courier" , monospace;"}\
[    }]{style="font-family: "courier new" , "courier" , monospace;"}\
[}
// ]{style="font-family: "courier new" , "courier" , monospace;"}*From
my
code: [test/java/tests/LoginTest.java](https://github.com/tjmaher/WebDriver_TheInternet_Advanced/blob/master/src/test/java/tests/LoginTest.java).*\

<div>

\

</div>

\
**Please note**: Storing usernames and passwords as a UserEnum is a bad
idea. It is better to store them in a properties file, where they can be
more secure. I am just using them here to illustrate a simple example of
using an Enum with The-Internet.\
\
To access the username and password for user TOM SMITH, we could just
call:\

> \
> \
> \
> \
> \
> \
> \
> \
>
> TOM\_SMITH.getUserName();
>
> TOM\_SMITH.getPassword();

<div>

If we wanted to pass all the user information for TOM SMITH to a method
that logs the user in by passing in the entire enum:

</div>

<div>

\

</div>

> logIntoPage(TOM\_SMITH);

<div>

\

</div>

<div>

The method create to handle logging in users, such as
with [WebDriver\_TheInternet\_Advanced:
test/java/pages/LoginPage.java](https://github.com/tjmaher/WebDriver_TheInternet_Advanced/blob/master/src/test/java/pages/LoginPage.java),
can then extract the information from the enum itself. 

</div>

<div>

<div>

\

</div>

<div>

    public void logIntoPage(UserEnum user){

</div>

<div>

\

</div>

<div>

        String username = user.getUserName();

</div>

<div>

        String password = user.getPassword();

</div>

<div>

\

</div>

<div>

        enterUserName(username);

</div>

<div>

        enterPassword(password);

</div>

<div>

         

</div>

<div>

        // Click the login button

</div>

<div>

    }

</div>

</div>

<div>

\

</div>

<div>

For my next blog post, I will cover how we currently use enums for
locators at my workplace.\
\
**NEXT:** [Storing locators in
enums](/2015/07/storing-locators-for-web-elements.html)\
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
