\-\-- layout: post title: \'Notes on Angie Jones, Make Your Automation
Behave: Extending Your Framework for BDD (June 28, 2017)\' date:
\'2017-07-13T07:48:00.000-04:00\' author: T.J. Maher tags: - bdd - Angie
Jones modified\_time: \'2017-11-03T08:58:35.362-04:00\' thumbnail:
https://i.ytimg.com/vi/QX3P\_DMoqlQ/default.jpg blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-8953561026617022229
blogger\_orig\_url:
http://www.tjmaher.com/2017/07/notes-on-angie-jones-make-your.html \-\--
Notes, **[Make Your Automation Behave: Extending Your Framework for
BDD]{.underline}**\

<div>

Given by Angie Jones, held on Jun 28, 2017  

</div>

<div>

Recording: [A Software Test Professionals
Webinar](http://www.softwaretestpro.com/make-your-automation-behave-extending-your-framework-for-bdd/) (STP)\
\

::: {.et_pb_text .et_pb_module .et_pb_bg_layout_light .et_pb_text_align_left .et_pb_text_0 style="background: rgb(255, 255, 255); border: 0px; box-sizing: border-box; color: #666666; font-family: "Open Sans", Arial, sans-serif; font-size: 14px; margin: 0px 0px 18.4219px; outline: 0px; padding: 0px; vertical-align: baseline; word-wrap: break-word;"}
::: {style="background: transparent; border: 0px; box-sizing: border-box; outline: 0px; padding: 0px 0px 1em; vertical-align: baseline;"}
\"When done properly, Behavior-Driven Development (BDD) can drastically
improve the communication and understanding of requirements. An
additional benefit is being able to utilize the domain-specific language
of the requirements to drive test automation. However, like any other
automation initiative, when done poorly, this too can fail.
:::

::: {style="background: transparent; border: 0px; box-sizing: border-box; outline: 0px; padding: 0px 0px 1em; vertical-align: baseline;"}
***\"In this webinar, Angie Jones provides a hands-on technical look
into how to:***
:::

-   \"utilize Gherkin-written scenarios for test automation
-   \"write scenarios in a way that promote maintainability and
    reusability
-   \"take advantage of advanced Gherkin functionality such as data
    tables and objects
-   \"tie the scenarios to automation code
-   \"incorporate this approach into existing automation frameworks that
    use the page object model design pattern
-   \"share state across multiple steps within a scenario

::: {style="background: transparent; border: 0px; box-sizing: border-box; outline: 0px; padding: 0px; vertical-align: baseline;"}
***\"Upon completion of this webinar, you'll have a better understanding
of how to:***
:::

-   \"Enhance your BDD initiative with test automation
-   \"Cleanly extend an automation framework to support executable
    requirement specifications
-   \"Support advanced techniques such as data tables and objects within
    specifications, as well as sharing state through dependency
    injection\".
:::

::: {.et_pb_text .et_pb_module .et_pb_bg_layout_light .et_pb_text_align_left .et_pb_text_1 style="background: rgb(255, 255, 255); border: 0px; box-sizing: border-box; color: #666666; font-family: "Open Sans", Arial, sans-serif; font-size: 14px; margin: 0px; outline: 0px; padding: 0px; vertical-align: baseline; word-wrap: break-word;"}
### The Speaker: {#the-speaker style="background: transparent; border: 0px; box-sizing: border-box; color: #333333; font-size: 22px; font-weight: 500; line-height: 1em; margin: 0px; outline: 0px; padding: 0px 0px 10px; vertical-align: baseline;"}

::: {style="background: transparent; border: 0px; box-sizing: border-box; outline: 0px; padding: 0px 0px 1em; vertical-align: baseline;"}
![Angie
Jones](http://www.softwaretestpro.com/wp-content/uploads/2017/05/Angie-Jones.gif){.alignleft
.size-full .wp-image-6245 width="163" height="159"}***\"Angie
Jones*** is a Senior Software Engineer in Test at Twitter who has
developed automation strategies and frameworks for countless software
products. As a Master Inventor, she is known for her innovative and
out-of-the-box thinking style which has resulted in more than 20
patented inventions in the US and China. Angie shares her wealth of
knowledge by speaking and teaching at software conferences all over the
world\".
:::

### Speaker Contact Details: {#speaker-contact-details style="background: transparent; border: 0px; box-sizing: border-box; color: #333333; font-size: 22px; font-weight: 500; line-height: 1em; margin: 0px; outline: 0px; padding: 0px 0px 10px; vertical-align: baseline;"}

::: {style="background: transparent; border: 0px; box-sizing: border-box; outline: 0px; padding: 0px; vertical-align: baseline;"}
***Angie Jones -- Senior Software Engineer in Test, Twitter***\
**Twitter:** [\@techgirl1908](https://twitter.com/techgirl1908)\
**LinkedIn:** [Angie Jones](http://www.linkedin.com/in/angiejones)\
**Website:** [AngieJones.tech](http://www.angiejones.tech/)
:::
:::

\
[]{#more}STP will be hosting a software testing conference, STPCon, on
September 25 - 29, 2017 in Washington, DC. You can register at
[http://STPCon.com/event-schedule](http://stpcon.com/event-schedule)\
\
Angie gave a Q&A session to the Ministry of Testing - Boston Tuesday,
11, 2017
at <https://www.meetup.com/ministry-of-testing-boston/events/240813119/>\
\
**[Recording: Make Your Automation Behave]{.underline}**\

\
**[Slides:]{.underline}**\

\

::: {.p1}
\
\
\
**Looking to add BDD to your test suite?**\
\
You do not have to abandon your sturdy old framework to implement BDD.
You can simply extend it![ ]{.Apple-converted-space}
:::

::: {.p2}
\
:::

::: {.p1}
The Page Object is the industry design standard, modeling an object on
the page you are testing, encapsulating how to interact with radio
buttons or textboxes. You then create public methods that interact with
these private methods. These methods can be used in your
tests.[ ]{.Apple-converted-space}
:::

::: {.p2}
\
:::

::: {.p1}
Behavior Driven Development:
:::

-   []{.s1}The Three Amigos, a QA, DEV and Product owner discuss how a
    certain feature should behave. You can describe it in the Gherkin
    style language.[ ]{.Apple-converted-space}

::: {.p2}
\
:::

::: {.p1}
*Want to read how **George Dinwiddie**, Agile Adoption Coach, came up
with the concept of "The Three Amigos"? *\
\

-   *Read his The Tree Amigos Strategy of Developing User Stories
    [[https://www.agileconnection.com/article/three-amigos-strategy-developing-user-stories]{.s2}](https://www.agileconnection.com/article/three-amigos-strategy-developing-user-stories)
    (April 24, 2014). *
-   *See LinkedIn profile
    [[https://www.linkedin.com/in/gdinwiddie/]{.s2}](https://www.linkedin.com/in/gdinwiddie/)
    Blog [[http://idiacomputing.com/]{.s2}](http://idiacomputing.com/)*
:::

::: {.p2}
\
:::

::: {.p2}
\
:::

::: {.p1}
*See Dan North, creator of the Behavior Driven Development (BDD), and
JBehave, and then RSpec, being interviewed at OOPSLA 2007.
[[https://youtu.be/qWsnmx45734]{.s2}](https://youtu.be/qWsnmx45734) *\
\

-   *Cucumber started off as being a compliment to RSpec and Dan North's
    work.[ ]{.Apple-converted-space}*
:::

::: {.p2}
\
:::

::: {.p1}
Let's say you have two source branches of your code:
:::

-   []{.s1}src/main/java
-   []{.s1}src/test/java

::: {.p1}
Your main branch can contain the page objects. The test branch can
contain the packageds cucumber -\> features.
:::

::: {.p2}
\
:::

::: {.p1}
Install the Cucumber plug into your framework's Maven or Gradle files.
If you go to Cucumber.Io it has documentation how to do
this.[ ]{.Apple-converted-space}
:::

::: {.p2}
\
:::

::: {.p1}
You can have as many feature files as you
want.[ ]{.Apple-converted-space}
:::

::: {.p2}
\
:::

::: {.p1}
Feature: Search for Products
:::

::: {.p1}
[   ]{.Apple-converted-space}As a user, I want to search the catalog so
that I can find specific products
:::

::: {.p2}
\
:::

::: {.p1}
Scenario: Click search result
:::

::: {.p1}
[   ]{.Apple-converted-space}Given there is a product named 'Apple TV'
:::

::: {.p1}
[   ]{.Apple-converted-space}And I search for the product
:::

::: {.p1}
[   ]{.Apple-converted-space}When I click the product
:::

::: {.p1}
[   ]{.Apple-converted-space}Then I should be taken to the product page
:::

::: {.p2}
\
:::

::: {.p1}
This feature file acts as manual documentation for how the software
product is supposed to work.[ ]{.Apple-converted-space}
:::

::: {.p2}
\
:::

::: {.p1}
Givens: Setup before the test starts
:::

::: {.p1}
When: The actual test
:::

::: {.p1}
Then: The results of the test.[ ]{.Apple-converted-space}
:::

::: {.p2}
\
:::

::: {.p1}
Note that we don't have any extraneous details, where to click, how to
see the product is Apple TV. Testers can be a bit long-winded being too
explicit what each step means.[ ]{.Apple-converted-space}
:::

::: {.p2}
\
:::

::: {.p1}
Push the details down to the code level.[ ]{.Apple-converted-space}
:::

::: {.p2}
\
:::

::: {.p1}
Under src/test/java/cucumber, Angie likes adding two directories:
:::

-   []{.s1}features
-   []{.s1}stepdefs

::: {.p2}
\
:::

::: {.p1}
The "features" folder contains the outlines for the
scenarios.[ ]{.Apple-converted-space}
:::

::: {.p1}
One steps definitions per functional area keeps things
clean.[ ]{.Apple-converted-space}
:::

::: {.p2}
\
:::

::: {.p1}
These are all you need for Cucumber. You can use your already written
Page Objects into your tests.[ ]{.Apple-converted-space}
:::

::: {.p2}
\
:::

::: {.p1}
public class SearchStepDefs {
:::

::: {.p1}
[   ]{.Apple-converted-space}protected String productName;
:::

::: {.p2}
[    ]{.Apple-converted-space}
:::

::: {.p1}
[   ]{.Apple-converted-space}\@Given("\^threre is a product named
(.\*)\$")
:::

::: {.p1}
[   ]{.Apple-converted-space}public void setProduct(String productName)
{
:::

::: {.p1}
[       ]{.Apple-converted-space}this.productName = productName;
:::

::: {.p1}
[   ]{.Apple-converted-space}}
:::

::: {.p1}
}
:::

::: {.p2}
\
:::

::: {.p1}
\@Given, \@When, \@Then, are annotations borrowed from
Cucumber.[ ]{.Apple-converted-space}
:::

::: {.p2}
\
:::

::: {.p1}
\@When("\^I search for the product\$")
:::

::: {.p1}
public void search(){
:::

::: {.p1}
[   ]{.Apple-converted-space}Page currentPage = new
Page(BaseTests.getWebDriver());
:::

::: {.p1}
[   ]{.Apple-converted-space}searchResults =
currentPage.search(productName);
:::

::: {.p1}
}
:::

::: {.p2}
\
:::

::: {.p1}
... Angie is using the getWebDriver() method already declared in her
framework to spin up a new WebDriver.[ ]{.Apple-converted-space}
:::

::: {.p2}
\
:::

::: {.p1}
A new instance of the page is spun up, in order to create a search
method.[ ]{.Apple-converted-space}
:::

::: {.p2}
\
:::

::: {.p1}
\@When("\^I click the product\$")
:::

::: {.p1}
public void clickProduct(){
:::

::: {.p1}
[   ]{.Apple-converted-space}currentPage =
searchResults.clickProduct(productName);
:::

::: {.p1}
}
:::

::: {.p2}
\
:::

::: {.p1}
Note, we are NOT dealing with elements in our step definitions just as
we do not deal with them in our test classes. Keep it
clean![ ]{.Apple-converted-space}
:::

::: {.p2}
\
:::

::: {.p1}
Let's create a new method... clickProduct... and put it in our
ProductPage.[ ]{.Apple-converted-space}
:::

::: {.p2}
\
:::

::: {.p1}
public ProductPage clickProduct(String productName){
:::

::: {.p1}
[   ]{.Apple-converted-space}WebElement product =
findProduct(productName);
:::

::: {.p1}
[   ]{.Apple-converted-space}product.findElement(productTitle).click();
:::

::: {.p1}
[   ]{.Apple-converted-space}return new
ProductPage(webDriver);[ ]{.Apple-converted-space}
:::

::: {.p2}
\
:::

::: {.p1}
\@Then("\^I should be taken to the product page\$")
:::

::: {.p1}
public void verifyProductPage(){
:::

::: {.p1}
[   ]{.Apple-converted-space}ProductPage productPage =
(ProductPage)currentPage;
:::

::: {.p1}
[   ]{.Apple-converted-space}Assert.assertEquals("Page
title",productPage.getTitle());
:::

::: {.p1}
}
:::

::: {.p2}
\
:::

::: {.p1}
We are using existing code in our step
definitions.[ ]{.Apple-converted-space}
:::

::: {.p2}
\
:::

::: {.p1}
Let's try a different scenario:
:::

::: {.p2}
\
:::

::: {.p1}
Scenario: Add the product from search result to cart
:::

::: {.p1}
[   ]{.Apple-converted-space}Given there is a product named Apple TV
:::

::: {.p1}
[   ]{.Apple-converted-space}When I search for the
product[ ]{.Apple-converted-space}
:::

::: {.p1}
[   ]{.Apple-converted-space}And I add the product to the cart
:::

::: {.p1}
[   ]{.Apple-converted-space}Then the product should be in the cart
:::

::: {.p2}
\
:::

::: {.p1}
We don't want to add cart step definitions to our search step
definitions... that becomes messy and unorganized. Yes, it is a search
test, but we really should create CartStepDefs, adding it to
BaseStepDefs and SearchStepDefs. Cucumber can search through our library
of Step Defs.[ ]{.Apple-converted-space}
:::

::: {.p2}
\
:::

::: {.p1}
Therefore, we can write:
:::

::: {.p2}
\
:::

::: {.p1}
public class CartStepDefs {
:::

::: {.p2}
\
:::

::: {.p1}
[   ]{.Apple-converted-space}\@Then("\^the product should be in the
cart\$")
:::

::: {.p1}
[   ]{.Apple-converted-space}public void verifyProductInCart(){
:::

::: {.p1}
[      ]{.Apple-converted-space}CartPage cartPage = new
CartPage(BaseTests.getWebDriver());
:::

::: {.p1}
[      ]{.Apple-converted-space}Assert.assertTrue( productName + "is in
cart", cartPage.isProductInCart(productName));
:::

::: {.p1}
[      ]{.Apple-converted-space}Assert.assertEquals( "Number of items in
cart", 1, cartPage.getNumberOfProducts(());
:::

::: {.p1}
[   ]{.Apple-converted-space}}
:::

::: {.p1}
}
:::

::: {.p2}
\
:::

::: {.p1}
How do you share data across multiple steps and multiple classes?
Dependency Injection!
:::

::: {.p2}
\
:::

::: {.p1}
Pass a dependency to whoever needs it. Create a BaseStepDefiniton that
holds globals that will be needed across all steps, such as the
productName variable.[ ]{.Apple-converted-space}
:::

::: {.p2}
\
:::

::: {.p1}
public class BaseStepDefs {
:::

::: {.p1}
[   ]{.Apple-converted-space}protected String productName;
:::

::: {.p1}
[   ]{.Apple-converted-space}protected Page currentPage;
:::

::: {.p2}
\
:::

::: {.p1}
[   ]{.Apple-converted-space}public BaseStepDefs() {
:::

::: {.p1}
[   ]{.Apple-converted-space}currentPage = new
Page(BaseTests.getWebDriver());
:::

::: {.p1}
[   ]{.Apple-converted-space}}
:::

::: {.p2}
[    ]{.Apple-converted-space}
:::

::: {.p1}
[   ]{.Apple-converted-space}\@Given("\^there is a product named
(.\*)\$")
:::

::: {.p1}
[   ]{.Apple-converted-space}public void setProduct(String productName)
{
:::

::: {.p1}
[       ]{.Apple-converted-space}this.productName = productName;
:::

::: {.p1}
[   ]{.Apple-converted-space}}
:::

::: {.p1}
}
:::

::: {.p2}
\
:::

::: {.p1}
... Now we need to inject this in the class that needs this
dependency.[ ]{.Apple-converted-space}
:::

::: {.p2}
\
:::

::: {.p1}
There are many ways you can set up dependency injection. Angie Jones
likes using pico container in Spring.[ ]{.Apple-converted-space}
:::

::: {.p2}
\
:::

::: {.p1}
Check in [[Cucumber.io]{.s2}](http://cucumber.io/) on how to do
this.[ ]{.Apple-converted-space}
:::

::: {.p2}
\
:::

\

::: {.p1}
Add a constructor to each of the dependent classes, then include the
dependency as an argument.[ ]{.Apple-converted-space}
:::

\
\
Happy Testing!\
\
-T.J. Maher\
[Twitter](https://twitter.com/tjmaher1) \| [LinkedIn](https://www.linkedin.com/in/tjmaher1) \| [GitHub](https://github.com/tjmaher)\
\
*// Sr. QA Engineer, Software Engineer in Test, Software Tester since
1996.\
// Contributing Writer
for [TechBeacon.](http://techbeacon.com/contributors/thomas-maher)\
// \"Looking to move away from manual QA? Follow [Adventures in
Automation](http://www.tjmaher.com/) on
[Facebook](https://www.facebook.com/AdventuresInAutomation/)!\"*

</div>
