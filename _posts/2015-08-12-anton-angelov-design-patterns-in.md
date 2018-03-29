\-\-- layout: post title: \'Anton Angelov: Design Patterns in Automation
Testing\' date: \'2015-08-12T00:21:00.002-04:00\' author: T.J. Maher
tags: - Design Pattern - test framework modified\_time:
\'2016-04-30T00:07:16.971-04:00\' blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-773846691749941491
blogger\_orig\_url:
http://www.tjmaher.com/2015/08/anton-angelov-design-patterns-in.html
\-\-- I have written a bit in this blog about Software Design Patterns
such as:\

-   Their [early
    history](/2015/05/page-objects-and-design-patterns-in.html) with
    Kent Beck introducing them to OOPSLA (Object-Oriented Programming,
    Systems, Languages & Applications) back in 1987 and their
    popularization with Eric Gamma, Richard Helm, Ralph Johnson and John
    Vlissides (The \"Gang of Four\") book, *Design Patterns: Elements of
    Reusable Object-Oriented Software* (1994).
-   A Boston Software Craftmanship
    [Meetup](/2015/06/meetup-how-to-study-design-patterns.html) I
    attended back in June 2015 on \"How to Study Design Patterns\".
-   As part of \"[Testing
    The-Internet](/2015/06/simple-manipulation-of-login-page.html)\"
    series,  I [talk
    about](/2015/07/the-internet-page-object-model-examples.html) how
    Page Objects are used at my workplace.

\... I haven\'t yet blogged about [Head First Design
Patterns](http://www.amazon.com/Head-First-Design-Patterns-Freeman/dp/0596007124/)
since I am still  halfway through the book, having just finished [Head
First
Java](http://adventuresinautomation.blogspot.com/2015/08/head-first-java-midi-and-swing.html) and
[Head First Object Oriented Analysis and
Design](http://www.amazon.com/Head-First-Object-Oriented-Analysis-Design/dp/0596008678).\
\
Anton Angelov, author of the blog \"[Automate the
Planet](http://automatetheplanet.com/)\",  goes far beyond that.\
\
[]{#more}\
\
\

Design Patterns in Automation Testing
-------------------------------------

Anton Angelov, an automation developer, has been working on a series of
posts called [Design Patterns in Automation
Testing](http://automatetheplanet.com/page-object-pattern/) since April.
 Using Selenium WebDriver and C\# he presents the idea of incorporating
these design patterns into automated tests.\
\

### Page Object Pattern

With the [Page Object
Pattern](http://automatetheplanet.com/page-object-pattern/), all
elements, actions and validations happening on a page is contained in
one single object. Anton uses the Bing search http://www.bing.com/ page
as an example. Web Elements such as the SearchBox, GoButton,
ResultsCount and actions such as Navigate, Search, and ValidateResults
can all be stored in a class called BingMainPage.\
\
This way, you can separate how you interact with the Document Object
Model (the Page Object) with the tests themselves (The Test Class).\
\
For locating the web elements, Anton gives two examples of the Page
Object, one using PageFactory and one not using the built-in Selenium
module, Page Factory.\
\
For the second example, instead of PageFactory it uses:\

> -   *\"Page Object Element Map -- Contains all element properties and
>     their location logic.*
>
> <!-- -->
>
> -   *\"Page Object Validator -- Consists of the validations that will
>     be performed on the page.*
>
> <!-- -->
>
> -   *\"Page Object (BingMainPage)- Holds the actions that can be
>     performed on the page like Search and Navigate. Exposes an easy
>     access to the Page Validator through the Validate() method. The
>     best implementations of the pattern hide the usage of the Element
>     Map, wrapping it through all action methods.*
>
> <!-- -->
>
> -   *\"UI Tests (BingTests) -- This class contains a group of tests
>     related to the above page; it can hold only a single instance of
>     the page object\".*

\
There does seem to be some discussion in the comments section with this
second method, if *asserts*, such as assertTrue in JUnit or TestNG,
should be placed only in the test, not the page object itself.\
\

### Advanced Page Object Patterns 

In order to follow the object oriented principle of DRY (Don\'t Repeat
Yourself), this [blog
post](http://automatetheplanet.com/advanced-page-object-pattern/) walks
the automater through creating a Driver class which has the static
methods StartBrowser, StopBrowser, and BrowserWait.\
\
Now that Anton developed this new class, the earlier work can be
refactored.\
\

### Facade Design Pattern

To make a purchase, Anton created a class,
[PurchaseFacade](http://automatetheplanet.com/facade-design-pattern/)
which groups together the page objects for Checkout, ItemPages,
ShippingAdderess, and SignIn.\
\

### Singleton Design Pattern 

\
With the [Singleton Design
Pattern](http://automatetheplanet.com/singleton-design-pattern/), Anton
goes into topics to use with the Base page class such as:\
\

-   Non-thread-safe BaseSingleton Class
-   Thread-safe BaseSingleton Class with Lock
-   Thread-safe BaseSingleton Class with Lazy
-   Thread-safe BaseSingleton Class with Nested Classes

### Fluent Page Object Pattern

With [this
pattern](http://automatetheplanet.com/fluent-page-object-pattern/),
Anton chains methods, so a test can look like:\

> \*    public void SearchForImageFluent()    {       
> P.BingMainPage.Instance        [ ]{.Apple-tab-span
> style="white-space: pre;"}.Navigate()        [ ]{.Apple-tab-span
> style="white-space: pre;"}.Search(\"facebook\")        [
> ]{.Apple-tab-span style="white-space: pre;"}.ClickImages()        [
> ]{.Apple-tab-span style="white-space: pre;"}.SetSize(Sizes.Large)     
>  [ ]{.Apple-tab-span
> style="white-space: pre;"}.SetColor(Colors.BlackWhite)       [
> ]{.Apple-tab-span style="white-space: pre;"}.SetTypes(Types.Clipart) 
>            [ ]{.Apple-tab-span
> style="white-space: pre;"}.SetPeople(People.All)             [
> ]{.Apple-tab-span style="white-space: pre;"}.SetDate(Dates.PastYear) 
>              [ ]{.Apple-tab-span
> style="white-space: pre;"}.SetLicense(Licenses.All);    }*

\
Other patterns discussed in his series:\
\

-   [IoC Container and Page
    Objects](http://automatetheplanet.com/ioc-container-page-object-pattern-steroids/)
-   [Strategy Design
    Pattern](http://automatetheplanet.com/strategy-design-pattern/)
-   [Advanced Strategy Design
    Pattern](http://automatetheplanet.com/advanced-strategy-design-pattern/)
-   [Observer Design
    Pattern](http://automatetheplanet.com/observer-design-pattern/)
-   [Observer Design Pattern via Events and
    Delegates](http://automatetheplanet.com/observer-design-pattern-events-delegates/)
-   [Observer Design Pattern via IObservable and
    IObserver](http://automatetheplanet.com/observer-design-pattern-iobserver/)

<div>

\

</div>

<div>

\... Not that I understand everything that is being talked about in
these articles, I do think they are a good read.\
\
-T.J. Maher\
 Sr. QA Engineer, Fitbit\
* // Manual tester, 15 years*\
* // Automated tester for \[ 5 \] months and counting*\
\
*Please note: \'Adventures in Automation\' is a personal blog about
automated testing. It is not an official blog
of [Fitbit.com](http://www.fitbit.com/). *

</div>
