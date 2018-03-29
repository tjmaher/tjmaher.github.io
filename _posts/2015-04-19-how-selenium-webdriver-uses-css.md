\-\-- layout: post title: How Selenium WebDriver uses CSS Selectors
date: \'2015-04-19T00:17:00.000-04:00\' author: T.J. Maher tags: -
beginner - WebDriver - CSS Selectors - manual to automation
modified\_time: \'2016-04-29T16:21:59.022-04:00\' thumbnail:
https://4.bp.blogspot.com/-BsVP8MNOMDA/VZNcxfqMKGI/AAAAAAAAKu0/nBj6QHShlv8/s72-c/image2015-4-11%2B12-41-37.png
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-5624965659786224586
blogger\_orig\_url:
http://www.tjmaher.com/2015/04/how-selenium-webdriver-uses-css.html
\-\--

::: {style="color: #333333; font-family: Arial, sans-serif; font-size: 14px; line-height: 20px;"}
*This information is based upon Alan Richardson\'s class, [Selenium 2
WebDriver with
Java.](http://courses.compendiumdev.co.uk/courses/selenium-2-webdriver-with-java) If
there is one thing that I can credit getting my current automation
engineer position at Fitbit, it is this course. *
:::

About CSS Selectors {#about-css-selectors style="border-bottom-color: rgb(0, 153, 0); color: #333333; font-family: Arial, sans-serif; font-size: 20px; font-weight: normal; line-height: 1.5; margin: 10px 0px 0px;"}
-------------------

::: {style="color: #333333; font-family: Arial, sans-serif; font-size: 14px; line-height: 20px; margin-top: 10px;"}
A CSS Selector matches a set of elements. CSS stands for Cascading Style
Sheets, what HTML uses to style the page layout of the web page. It is
reused in Selenium to match the DOM (Document Object Model) elements.\
\
[]{#more}\
:::

Install Firepath {#install-firepath style="border-bottom-color: rgb(0, 153, 0); color: #333333; font-family: Arial, sans-serif; font-size: 20px; font-weight: normal; line-height: 1.5; margin: 30px 0px 0px;"}
----------------

::: {style="color: #333333; font-family: Arial, sans-serif; font-size: 14px; line-height: 20px; margin-top: 10px;"}
[To investigate CSS Selectors, you can use two plugins for Firefox,
Firepath and
Firebug. ](http://courses.compendiumdev.co.uk/courses/selenium-2-webdriver-with-java)
:::

-   Firebug: <http://getfirebug.com/>
-   Firepath: <https://addons.mozilla.org/en-us/firefox/addon/firepath/>

::: {style="color: #333333; font-family: Arial, sans-serif; font-size: 14px; line-height: 20px; margin-top: 10px;"}
Once they are installed, you can right click on a web element, and
\"Inspect in Firepath\". 
:::

::: {style="color: #333333; font-family: Arial, sans-serif; font-size: 14px; line-height: 20px; margin-top: 10px;"}
Firepath will be a tab located in Firebug, far to the right. 
:::

Basic CSS Selectors {#basic-css-selectors style="border-bottom-color: rgb(0, 153, 0); color: #333333; font-family: Arial, sans-serif; font-size: 20px; font-weight: normal; line-height: 1.5; margin: 30px 0px 0px;"}
-------------------

<div>

\

</div>

-   \* : match any element
-   \#id : match any id, such as \#p4. 
-   .classname : match a class such as \".normal\".
-   \[attribute\] : Match on an attribute name.

::: {style="color: #333333; font-family: Arial, sans-serif; font-size: 14px; line-height: 20px; margin-top: 10px;"}
\
:::

::: {style="color: #333333; font-family: Arial, sans-serif; font-size: 14px; line-height: 20px; margin-top: 10px;"}
With Firepath, you can investigate the DOM (Document Object Model) by
XPath, CSS Selector, or Sizzle. At Fitbit, when we cannot select
\"By.id\", we use \"By.cssSelector\". 
:::

::: {style="color: #333333; font-family: Arial, sans-serif; font-size: 14px; line-height: 20px; margin-top: 10px;"}
A demo page was set up for the class on Alan Richardson\'s website, the
\"Find By Playground\"
 at <http://www.compendiumdev.co.uk/selenium/find_by_playground.php>
:::

::: {style="color: #333333; font-family: Arial, sans-serif; font-size: 14px; line-height: 20px; margin-top: 10px;"}
If you right click on the \"This is a paragraph text\" and choose
\"Inspect in Firepath\", the Firebug window pops up with the Firepath
tab displayed. You can then select \"CSS (X)\" from the dropdown next to
the word \"Highlight\". 
:::

::: {style="color: #333333; font-family: Arial, sans-serif; font-size: 14px; line-height: 20px; margin-top: 10px;"}
::: {.separator style="clear: both; text-align: center;"}
[![](https://4.bp.blogspot.com/-BsVP8MNOMDA/VZNcxfqMKGI/AAAAAAAAKu0/nBj6QHShlv8/s400/image2015-4-11%2B12-41-37.png){width="400"
height="342"}](http://4.bp.blogspot.com/-BsVP8MNOMDA/VZNcxfqMKGI/AAAAAAAAKu0/nBj6QHShlv8/s1600/image2015-4-11%2B12-41-37.png)
:::

\
:::

::: {style="color: #333333; font-family: Arial, sans-serif; font-size: 14px; line-height: 20px; margin-top: 10px;"}
:::

::: {style="color: #333333; font-family: Arial, sans-serif; font-size: 14px; line-height: 20px; margin-top: 10px;"}
You can see that the id, \#p1 is shown. 
:::

::: {style="color: #333333; font-family: Arial, sans-serif; font-size: 14px; line-height: 20px; margin-top: 10px;"}
See what happens when you enter the following text in the CSS textbox
when on this page:
:::

::: {style="color: #333333; font-family: Arial, sans-serif; font-size: 14px; line-height: 20px; margin-top: 10px;"}
\
:::

  CSS Text   What happens in the Document Object Model (DOM) on the test page
  ---------- -----------------------------------------------------------------------------------------------------------------------------------------------------------------
  \*         All web elements are selected.
  \[id\]     All elements with ids are selected.
  \#p4       The p4 id tag is selected.
  p          All web elements that are HTML paragraph tags (p) are selected
  p\#p4      All paragraphs with an id of p4 are selected. Just \#p4 may also work, but it makes it more readable.
  p.normal   All paragraph web elements of class=\"normal\" will be selected. .normal would also work, but with the explicit \"p\" tag there, it makes it more readable.
  .has       On this page, there is a class called \"this has multiple values\". By searching on the text \".has\" it picks up on the word \"has\" in the class description.

More Advanced CSS Selectors {#more-advanced-css-selectors style="border-bottom-color: rgb(0, 153, 0); color: #333333; font-family: Arial, sans-serif; font-size: 20px; font-weight: normal; line-height: 1.5; margin: 30px 0px 0px;"}
---------------------------

### Examples {#examples style="color: #333333; font-family: Arial, sans-serif; font-size: 16px; line-height: 1.5; margin: 30px 0px 0px;"}

-   tag\[attribute\] : [match tags with an
    ]{data-mce-style="line-height: 1.4285715;"
    style="line-height: 1.4285715;"}attribute
-   tag\[attribute="value"\] : match tags with a specific attribute
    value, in this case named \"value\"
-   tag\[attr1=\'val1\'\]\[attr2=\'val2\'\] : match tag using multiple
    attribute values called \"val1\" and \"val2\"
-   tag\[attribute\*="alu"\] \" Partial match anywhere on the attribute
    called \"value\"
-   tag\[attribute\^="val"\] : Partial match start of value. \^ is the
    wildcard for the beginning of the word.
-   tag\[attribute\$="lue"\]: Partial match end of value. \$ is the
    wildcard for the end of a word. 
-   tag\[attribute\~="value"\] : Match on space separated values
-   tag\[a=\'val\'\], tag\[b=\'val\'\] : is an \'or\' grouping, where it
    is looking for the tags a=\'val\' or b=\'val\'. If there is no
    comma, is is looking for tags a=\'val\' and b=\'val\'

::: {style="color: #333333; font-family: Arial, sans-serif; font-size: 14px; line-height: 20px; margin-top: 10px;"}
Go back to the \"Find By Playground page\"
 at <http://www.compendiumdev.co.uk/selenium/find_by_playground.php> and
enter Firepath. 
:::

::: {style="color: #333333; font-family: Arial, sans-serif; font-size: 14px; line-height: 20px; margin-top: 10px;"}
See what happens when you enter the following text in the CSS textbox
when on this page:
:::

  ---------------------------------------------------------------------------------------------------------------------------------------------------------
  CSS Text                                                What happens in the Document Object Model (DOM) on the test page
  ------------------------------------------------------- -------------------------------------------------------------------------------------------------
  p.class                                                 All web elements of type paragraph with a class attribute are selected.

  p\[class=\'normal\'\]                                   All paragraph web elements of an attribute of type class = normal are selected.

  div\[class=\'specialDiv\'\]                             All DIV elements with a class called \"specialDiv\".

  div\[class\*=\'Div\'\]                                  With the \"\*=\" it is doing a partial match, matching any class with the word \"Div\" in it. .

  div\[class\$=\'Div\'\]                                  With the \"\$=\" it is matching where \"Div\" is on the end of the class.

  div\[class\^=\'special\'\]                              With the \"\^=\" it is matching where \"special\" is on the beginning of the class.

  div\[class\~=\'has\'\]                                  With the \"\~=\" it found the separate word \"has\" in \"this has multiple values\"

  div\[class=\'nestedDiv\'\]                              Matches all class attributes which equals the word \"nestedDiv\".

  div\[class=\'nestedDiv\'\]\[name=\'nestedDiv\'\]        Matches on the class AND the name is the word \"nestedDiv\".

  div\[class=\'nestedDiv\'\], div\[name=\'nestedDiv\'\]   Matches where the class OR the name is the word \"nestedDiv\".

  \                                                       \
  ---------------------------------------------------------------------------------------------------------------------------------------------------------

How to use CSS Selectors {#how-to-use-css-selectors style="border-bottom-color: rgb(0, 153, 0); color: #333333; font-family: Arial, sans-serif; font-size: 20px; font-weight: normal; line-height: 1.5; margin: 30px 0px 0px;"}
------------------------

::: {style="color: #333333; font-family: Arial, sans-serif; font-size: 14px; line-height: 20px; margin-top: 10px;"}
We use the selector By.cssSelector(\<the css selector string\>).
:::

``` {.brush: .javafx}
@Test
public void findElementsUsingCSSTag(){
 List<WebElement> elements; // We set up a collection of WebElements we are calling "element" using a "List"
 elements = driver.findElements(By.cssSelector("p")); // Store the entire list in the variable called "element". 
}
```

::: {style="color: #333333; font-family: Arial, sans-serif; font-size: 14px; line-height: 20px; margin-top: 10px;"}
[CSS Selector Paths]{style="font-size: 20px; line-height: 1.5;"}
:::

::: {style="color: #333333; font-family: Arial, sans-serif; font-size: 14px; line-height: 20px; margin-top: 10px;"}
CSS Selectors can be found in relation to one another. 
:::

-   A \> B : Match Selector B which is directly under Selector A ( such
    as: \<A\>\<B/\>\</A\> )
-   A B : descendant

> -   selectors separated by space i.e. "this then that"
>
> <!-- -->
>
> -   Any degree of separation
>
> <!-- -->
>
> -   e.g. "div li" would match but "div \> li" would not

-   A + B : B siblings of an A
-   B:first-child : every B which is first child of
    [something]{data-mce-style="line-height: 1.4285715;"
    style="line-height: 1.4285715;"}

::: {style="color: #333333; font-family: Arial, sans-serif; font-size: 14px; line-height: 20px; margin-top: 10px;"}
[Go back to the \"Find By Playground page\"
 at ]{data-mce-style="font-size: 14.0px; line-height: 1.4285715;"
style="line-height: 1.4285715;"}<http://www.compendiumdev.co.uk/selenium/find_by_playground.php>[.
You can see that there is a bullet pointed unordered list of links
(\"jump to para 0\", jump to para 1\",
etc.)]{data-mce-style="font-size: 14.0px; line-height: 1.4285715;"
style="line-height: 1.4285715;"}
:::

::: {style="color: #333333; font-family: Arial, sans-serif; font-size: 14px; line-height: 20px; margin-top: 10px;"}
::: {.separator style="clear: both; text-align: center;"}
[![](https://1.bp.blogspot.com/-3zJhP12fqqo/VZNdBWBw2XI/AAAAAAAAKu8/sTo7Fczhp8E/s400/image2015-4-11%2B16-53-17.png){width="400"
height="271"}](http://1.bp.blogspot.com/-3zJhP12fqqo/VZNdBWBw2XI/AAAAAAAAKu8/sTo7Fczhp8E/s1600/image2015-4-11%2B16-53-17.png)
:::

\
:::

::: {style="color: #333333; font-family: Arial, sans-serif; font-size: 14px; line-height: 20px; margin-top: 10px;"}
[If you right click on \"Jump to para 0\" and \"Inspect Element\", you
will see the HTML
Code:]{data-mce-style="font-size: 14.0px; line-height: 1.4285715;"
style="line-height: 1.4285715;"}
:::

::: {style="color: #333333; font-family: Arial, sans-serif; font-size: 14px; line-height: 20px; margin-top: 10px;"}
::: {.separator style="clear: both; text-align: center;"}
[![](https://4.bp.blogspot.com/-s35PLrZTheM/VZNdLrc8a4I/AAAAAAAAKvE/J4J6-MPbJ5s/s400/image2015-4-11%2B16-55-57.png){width="400"
height="326"}](http://4.bp.blogspot.com/-s35PLrZTheM/VZNdLrc8a4I/AAAAAAAAKvE/J4J6-MPbJ5s/s1600/image2015-4-11%2B16-55-57.png)
:::

\
:::

::: {style="color: #333333; font-family: Arial, sans-serif; font-size: 14px; line-height: 20px; margin-top: 10px;"}
It looks like:
:::

``` {.brush: .javafx}
<div >
 <ul>
  <li> (Bullet Point #1 ) 
  </li>
  <li> (Bullet Point #2 ) 
  </li>
  ...   ...     ...
 </ul>
<div>
```

::: {style="color: #333333; font-family: Arial, sans-serif; font-size: 14px; line-height: 20px; margin-top: 10px;"}
\
:::

::: {style="color: #333333; font-family: Arial, sans-serif; font-size: 14px; line-height: 20px; margin-top: 10px;"}
Let\'s say you wanted to select all the bullet points (the \"li\" tag in
HTML) in an unordered list (The \"ul\" HTML tag) under the DIV tag, the
CSS Selector would be:  div \> ul \> li. 
:::

::: {style="color: #333333; font-family: Arial, sans-serif; font-size: 14px; line-height: 20px; margin-top: 10px;"}
To verify this, we can go into Firepath and check this code:
:::

::: {style="color: #333333; font-family: Arial, sans-serif; font-size: 14px; line-height: 20px; margin-top: 10px;"}
::: {.separator style="clear: both; text-align: center;"}
[![](https://3.bp.blogspot.com/-5N_Bn5aTq5s/VZNdSHjIwrI/AAAAAAAAKvM/5__rIR4Hb0E/s400/image2015-4-11%2B17-1-1.png){width="400"
height="326"}](http://3.bp.blogspot.com/-5N_Bn5aTq5s/VZNdSHjIwrI/AAAAAAAAKvM/5__rIR4Hb0E/s1600/image2015-4-11%2B17-1-1.png)
:::

\
:::

::: {style="color: #333333; font-family: Arial, sans-serif; font-size: 14px; line-height: 20px; margin-top: 10px;"}
Note the text on the bottom pane of Firepath: \"25 matching nodes\". 
:::

::: {style="color: #333333; font-family: Arial, sans-serif; font-size: 14px; line-height: 20px; margin-top: 10px;"}
Now, let\'s say we wanted to find out the number of bullet points by
using the \".size()\" method and and place it in a variable called
numberOfLinks: 
:::

::: {style="color: #333333; font-family: Arial, sans-serif; font-size: 14px; line-height: 20px; margin-top: 10px;"}
\
:::

``` {style="color: #333333; font-size: 14px; line-height: 20px; tab-size: 4; white-space: pre-wrap;"}
int numberOfBulletPoints;
 
numberOfBulletPoints = driver.findElements(By.cssSelector("div > ul > li)).size());
```

### More examples {#more-examples style="color: #333333; font-family: Arial, sans-serif; font-size: 16px; line-height: 1.5; margin: 30px 0px 0px;"}

::: {style="color: #333333; font-family: Arial, sans-serif; font-size: 14px; line-height: 20px; margin-top: 10px;"}
See what happens when you enter the following text in the CSS textbox
when on this page:
:::

  CSS Text          What happens in the Document Object Model (DOM) on the test page
  ----------------- --------------------------------------------------------------------
  li + li           Find all list items with list items as sibling.
  div li            Find all \<div\> tags that have \<li\> list items as a descendant.
  li: first-child   Find the first child of the list \<li\>

::: {style="color: #333333; font-family: Arial, sans-serif; font-size: 14px; line-height: 20px; margin-top: 10px;"}
\
:::

Related articles {#related-articles style="border-bottom-color: rgb(0, 153, 0); color: #333333; font-family: Arial, sans-serif; font-size: 20px; font-weight: normal; line-height: 1.5; margin: 30px 0px 0px;"}
----------------

-   [W3Schools: CSS Selector
    Reference](http://www.w3schools.com/cssref/css_selectors.asp)
    -   Contains an interactive  [CSS Selector
        Tester](http://www.w3schools.com/cssref/trysel.asp)[\
        ](http://www.w3schools.com/cssref/trysel.asp)[Mozilla Developer
        Network: CSS](https://developer.mozilla.org/en-US/docs/CSS)
-   [tuts+: ](http://code.tutsplus.com/tutorials/the-30-css-selectors-you-must-memorize--net-16048)[The
    30 CSS Selectors you Must
    Memorize](http://code.tutsplus.com/tutorials/the-30-css-selectors-you-must-memorize--net-16048)
-   [tuts+: Advanced CSS Level 4 Selectors to Watch Out
    For](http://webdesign.tutsplus.com/articles/css-level-4-selectors-to-watch-out-for--cms-23117)
-   [Quirksmode.org: CSS contents and browser
    compatibility](http://www.quirksmode.org/css/contents.html)
-   [CSS-Tricks.com: Attribute
    Selectors](http://css-tricks.com/attribute-selectors/)
