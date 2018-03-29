\-\-- layout: post title: \'Automate Amazon: CommonUtils, methods and
exceptions\' date: \'2015-12-28T12:33:00.000-05:00\' author: T.J. Maher
tags: - code examples - Java - WebDriver - test framework
modified\_time: \'2016-04-29T07:48:44.199-04:00\' blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-5322077568926842592
blogger\_orig\_url:
http://www.tjmaher.com/2015/12/automate-amazon-commonutils-methods-and.html
\-\-- *This post is third of a series of nine. Need to go [back to the
beginning](/2015/12/next-week-automating-amazon-how-i-am.html)?*\
\
The Selenium WebDriver API provides the basic methods to manipulate a
browser to perform actions, such as navigating to a web page, but it
doesn\'t have all the functionality we would need. What if we wanted to
add in exception handling, such as if the web page was not found? What
if we wanted to throw a customized error to a log file when the page was
not found? What if, even upon a success, we wanted to write a message to
the log?\
\
A Common Utilities library, such as one they are using at my workplace,
can be developed to handle these cases. Each Selenium API method is
wrapped in try / catch / throw blocks for exception handling, built-in
with logging functionality. When things go wrong, clear and concise
error messages will save a lot of time debugging if the issue was with
the server, with the code of the site, or the tests themselves.\
\
\
[]{#more}\

### Creating Methods to Navigate to a Web Page

\
Navigating to Amazon.com\'s home page is pretty simple with WebDriver.
All it takes is one driver.get statement in order to navigate to the
login page:\
\

``` {style="background-image: URL(http://2.bp.blogspot.com/_z5ltvMQPaa8/SjJXr_U2YBI/AAAAAAAAAAM/46OqEP32CJ8/s320/codebg.gif); background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 driver.get("http://www.amazon.com/");  
```

\
But what if you wanted to add functionality to write to the log console
every time you use WebDriver to navigate to a web page? This means you
would have to enter two lines of code per driver.get statement.\

``` {style="background-image: URL(http://2.bp.blogspot.com/_z5ltvMQPaa8/SjJXr_U2YBI/AAAAAAAAAAM/46OqEP32CJ8/s320/codebg.gif); background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
  System.out.println("Navigating to: http://www.amazon.com/");  
  driver.get("http://http://www.amazon.com/");  
```

\
Let\'s say you also wanted to add even more:\

-   Logging functionality when an action is performed
-   Catch any errors if the action failed
-   Throw an error to the logs detailing if an error ever happened
-   Include any wait statements, if a page is known to be slow loading. 

\
To satisfy all these new requirements, at work they came up with the
following method for their CommonUtils
library, [navigateToURL]{style="font-family: "courier new" , "courier" , monospace;"}[:]{style="font-family: inherit;"}[ ]{style="font-family: "courier new" , "courier" , monospace;"}\
\

``` {style="background-image: URL(http://2.bp.blogspot.com/_z5ltvMQPaa8/SjJXr_U2YBI/AAAAAAAAAAM/46OqEP32CJ8/s320/codebg.gif); background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 public void navigateToURL(String URL) {  
     System.out.println("Navigating to: " + URL);  
     System.out.println("Thread id = " + Thread.currentThread().getId());  
     try {  
       _driver.navigate().to(URL);  
     } catch (Exception e) {  
       System.out.println("URL did not load: " + URL);  
       throw new TestException("URL did not load");  
     }  
 }  
```

\
[To use this method, we can use this method in a test, passing in the
URL as a String:]{style="font-family: inherit;"}\
[\
]{style="font-family: inherit;"}[navigateToURL(\"http://www.amazon.com/\");]{style="font-family: "courier new" , "courier" , monospace;"}\
[\
]{style="font-family: inherit;"}[Now imagine if you had a whole library
where all the Selenium WebDriver functions are wrapped in try / catch /
throw blocks, logging functionality is added, threads have
identification numbers listed, and any optional wait statements are
included.]{style="font-family: inherit;"}\

### [Methods in the CommonUtils Library]{style="font-family: inherit;"}

[\
]{style="font-family: inherit;"}[These are the methods in the
CommonUtility we can use:]{style="font-family: inherit;"}\
\

-   [[navigateToURL]{.pl-en
    style="background-color: white; box-sizing: border-box; line-height: 16.8px; white-space: pre;"}[(]{style="background-color: white; line-height: 16.8px; white-space: pre;"}[String]{.pl-smi
    style="background-color: white; box-sizing: border-box; line-height: 16.8px; white-space: pre;"}[
    ]{style="background-color: white; line-height: 16.8px; white-space: pre;"}[URL]{.pl-smi
    style="background-color: white; box-sizing: border-box; line-height: 16.8px; white-space: pre;"}[)]{style="background-color: white; line-height: 16.8px; white-space: pre;"}]{style="font-family: inherit;"}

<!-- -->

-   [[getPageTitle]{.pl-en
    style="box-sizing: border-box; line-height: 16.8px;"}[()]{style="line-height: 16.8px;"}]{style="background-color: white; font-family: inherit; line-height: 16.8px; white-space: pre;"}

<!-- -->

-   [[[getElement]{.pl-en
    style="box-sizing: border-box; line-height: 16.8px;"}[(]{style="line-height: 16.8px;"}[By]{.pl-smi
    style="box-sizing: border-box; line-height: 16.8px;"}[
    ]{style="line-height: 16.8px;"}[selector]{.pl-v
    style="box-sizing: border-box; line-height: 16.8px;"}[)]{style="line-height: 16.8px;"}]{style="font-family: inherit; line-height: 16.8px;"}]{style="background-color: white; line-height: 16.8px; white-space: pre;"}

<!-- -->

-   [[[[sendKeys]{.pl-en
    style="box-sizing: border-box; line-height: 16.8px;"}[(]{style="line-height: 16.8px;"}[By]{.pl-smi
    style="box-sizing: border-box; line-height: 16.8px;"}[
    ]{style="line-height: 16.8px;"}[selector]{.pl-v
    style="box-sizing: border-box; line-height: 16.8px;"}[,
    ]{style="line-height: 16.8px;"}[String]{.pl-smi
    style="box-sizing: border-box; line-height: 16.8px;"}[
    ]{style="line-height: 16.8px;"}[value]{.pl-v
    style="box-sizing: border-box; line-height: 16.8px;"}[)]{style="line-height: 16.8px;"}]{style="font-family: inherit; line-height: 16.8px;"}]{style="line-height: 16.8px;"}]{style="background-color: white; line-height: 16.8px; white-space: pre;"}

<!-- -->

-   [[[[[clearField]{.pl-en
    style="box-sizing: border-box; line-height: 16.8px;"}[(]{style="line-height: 16.8px;"}[WebElement]{.pl-smi
    style="box-sizing: border-box; line-height: 16.8px;"}[
    ]{style="line-height: 16.8px;"}[element]{.pl-v
    style="box-sizing: border-box; line-height: 16.8px;"}[)]{style="line-height: 16.8px;"}]{style="font-family: inherit; line-height: 16.8px;"}]{style="line-height: 16.8px;"}]{style="line-height: 16.8px;"}]{style="background-color: white; line-height: 16.8px; white-space: pre;"}

<!-- -->

-   [[[[[[click]{.pl-en
    style="box-sizing: border-box; line-height: 16.8px;"}[(]{style="line-height: 16.8px;"}[By]{.pl-smi
    style="box-sizing: border-box; line-height: 16.8px;"}[
    ]{style="line-height: 16.8px;"}[selector]{.pl-v
    style="box-sizing: border-box; line-height: 16.8px;"}[)]{style="line-height: 16.8px;"}]{style="font-family: inherit; line-height: 16.8px;"}]{style="line-height: 16.8px;"}]{style="line-height: 16.8px;"}]{style="line-height: 16.8px;"}]{style="background-color: white; line-height: 16.8px; white-space: pre;"}

<!-- -->

-   [[[[[[[waitForElementToBeClickable]{.pl-en
    style="box-sizing: border-box; line-height: 16.8px;"}[(]{style="line-height: 16.8px;"}[By]{.pl-smi
    style="box-sizing: border-box; line-height: 16.8px;"}[
    ]{style="line-height: 16.8px;"}[selector]{.pl-v
    style="box-sizing: border-box; line-height: 16.8px;"}[
    )]{style="line-height: 16.8px;"}]{style="font-family: inherit; line-height: 16.8px;"}]{style="line-height: 16.8px;"}]{style="line-height: 16.8px;"}]{style="line-height: 16.8px;"}]{style="line-height: 16.8px;"}]{style="background-color: white; line-height: 16.8px; white-space: pre;"}

<!-- -->

-   [[[[[[[[waitForElementToBeVisible]{.pl-en
    style="box-sizing: border-box; line-height: 16.8px;"}[(]{style="line-height: 16.8px;"}[By]{.pl-smi
    style="box-sizing: border-box; line-height: 16.8px;"}[
    ]{style="line-height: 16.8px;"}[selector]{.pl-v
    style="box-sizing: border-box; line-height: 16.8px;"}[)]{style="line-height: 16.8px;"}]{style="font-family: inherit; line-height: 16.8px;"}]{style="line-height: 16.8px;"}]{style="line-height: 16.8px;"}]{style="line-height: 16.8px;"}]{style="line-height: 16.8px;"}]{style="line-height: 16.8px;"}]{style="background-color: white; line-height: 16.8px; white-space: pre;"}

### 

### How to use the Methods:

\
Selectors can be found By Id or By CSS Selector. If we wanted to grab
the Username textbox, the Password textbox, or the Sign In button of the
Sign In page, we could:\
\

-   Username: getElement(By.cssSelector(\"\#ap\_email\")
-   Password: getElement(By.cssSelector(\"\#ap\_password\")
-   Login Button: getElement(By.cssSelector(\"\#signInSubmit\")

\
\
\... And wherever these CommonUtils methods are used, such as in the
Page Objects, we need to:\
\

-   Import the CommonUtils library. 
-   Extend the Class to inherit the methods declared in CommonUtils. 

\
\
All test code can be found on GitHub
at [Automate-Amazon](https://github.com/tjmaher/automate-amazon/tree/master/automate-amazon/src/test/java).\
\
\
**CommonUtils.java**\

``` {style="background-image: URL(http://2.bp.blogspot.com/_z5ltvMQPaa8/SjJXr_U2YBI/AAAAAAAAAAM/46OqEP32CJ8/s320/codebg.gif); background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
1:  package utils;  
2:  import org.apache.commons.lang3.StringUtils;  
3:  import org.openqa.selenium.*;  
4:  import org.openqa.selenium.interactions.Actions;  
5:  import org.openqa.selenium.support.ui.ExpectedConditions;  
6:  import org.openqa.selenium.support.ui.Select;  
7:  import org.openqa.selenium.support.ui.WebDriverWait;  
8:  import org.testng.TestException;  
9:  import java.util.ArrayList;  
10:  import java.util.List;  
11:  /**  
12:   * Created by tmaher on 12/21/2015.  
13:   */  
14:  public abstract class CommonUtils {  
15:    private static int timeout = 10;  
16:    public CommonUtils() {  
17:      _driver = DriverUtils.getDriver();  
18:    }  
19:    public static WebDriver _driver;  
20:    public WebDriverWait wait;  
21:    public Actions actions;  
22:    public Select select;  
23:    public void navigateToURL(String URL) {  
24:      try {  
25:        _driver.navigate().to(URL);  
26:      } catch (Exception e) {  
27:        System.out.println("FAILURE: URL did not load: " + URL);  
28:        throw new TestException("URL did not load");  
29:      }  
30:    }  
31:    public void navigateBack() {  
32:      try {  
33:        _driver.navigate().back();  
34:      } catch (Exception e) {  
35:        System.out.println("FAILURE: Could not navigate back to previous page.");  
36:        throw new TestException("Could not navigate back to previous page.");  
37:      }  
38:    }  
39:    public String getPageTitle() {  
40:      try {  
41:        return _driver.getTitle();  
42:      } catch (Exception e) {  
43:        throw new TestException(String.format("Current page title is: %s", _driver.getTitle()));  
44:      }  
45:    }  
46:    public String getCurrentURL() {  
47:      try {  
48:        return _driver.getCurrentUrl();  
49:      } catch (Exception e) {  
50:        throw new TestException(String.format("Current URL is: %s", _driver.getCurrentUrl()));  
51:      }  
52:    }  
53:    public WebElement getElement(By selector) {  
54:      try {  
55:        return _driver.findElement(selector);  
56:      } catch (Exception e) {  
57:        System.out.println(String.format("Element %s does not exist - proceeding", selector));  
58:      }  
59:      return null;  
60:    }  
61:    public String getElementText(By selector) {  
62:      waitUntilElementIsDisplayedOnScreen(selector);  
63:      try {  
64:        return StringUtils.trim(_driver.findElement(selector).getText());  
65:      } catch (Exception e) {  
66:        System.out.println(String.format("Element %s does not exist - proceeding", selector));  
67:      }  
68:      return null;  
69:    }  
70:    public List<WebElement> getElements(By Selector) {  
71:      waitForElementToBeVisible(Selector);  
72:      try {  
73:        return _driver.findElements(Selector);  
74:      } catch (Exception e) {  
75:        throw new NoSuchElementException(String.format("The following element did not display: [%s] ", Selector.toString()));  
76:      }  
77:    }  
78:    public List<String> getListOfElementTexts(By selector) {  
79:      List<String> elementList = new ArrayList<String>();  
80:      List<WebElement> elements = getElements(selector);  
81:      for (WebElement element : elements) {  
82:        if (element == null) {  
83:          throw new TestException("Some elements in the list do not exist");  
84:        }  
85:        if (element.isDisplayed()) {  
86:          elementList.add(element.getText().trim());  
87:        }  
88:      }  
89:      return elementList;  
90:    }  
91:    public void click(By selector) {  
92:      WebElement element = getElement(selector);  
93:      waitForElementToBeClickable(selector);  
94:      try {  
95:        element.click();  
96:      } catch (Exception e) {  
97:        throw new TestException(String.format("The following element is not clickable: [%s]", selector));  
98:      }  
99:    }  
100:    public void scrollToThenClick(By selector) {  
101:      WebElement element = _driver.findElement(selector);  
102:      actions = new Actions(_driver);  
103:      try {  
104:        ((JavascriptExecutor) _driver).executeScript("arguments[0].scrollIntoView(true);", element);  
105:        actions.moveToElement(element).perform();  
106:        actions.click(element).perform();  
107:      } catch (Exception e) {  
108:        throw new TestException(String.format("The following element is not clickable: [%s]", element.toString()));  
109:      }  
110:    }  
111:    public void sendKeys(By selector, String value) {  
112:      WebElement element = getElement(selector);  
113:      clearField(element);  
114:      try {  
115:        element.sendKeys(value);  
116:      } catch (Exception e) {  
117:        throw new TestException(String.format("Error in sending [%s] to the following element: [%s]", value, selector.toString()));  
118:      }  
119:    }  
120:    public void clearField(WebElement element) {  
121:      try {  
122:        element.clear();  
123:        waitForElementTextToBeEmpty(element);  
124:      } catch (Exception e) {  
125:        System.out.print(String.format("The following element could not be cleared: [%s]", element.getText()));  
126:      }  
127:    }  
128:    public void waitForElementToDisplay(By Selector) {  
129:      WebElement element = getElement(Selector);  
130:      while (!element.isDisplayed()) {  
131:        System.out.println("Waiting for element to display: " + Selector);  
132:        sleep(200);  
133:      }  
134:    }  
135:    public void waitForElementTextToBeEmpty(WebElement element) {  
136:      String text;  
137:      try {  
138:        text = element.getText();  
139:        int maxRetries = 10;  
140:        int retry = 0;  
141:        while ((text.length() >= 1) || (retry < maxRetries)) {  
142:          retry++;  
143:          text = element.getText();  
144:        }  
145:      } catch (Exception e) {  
146:        System.out.print(String.format("The following element could not be cleared: [%s]", element.getText()));  
147:      }  
148:    }  
149:    public void waitForElementToBeVisible(By selector) {  
150:      try {  
151:        wait = new WebDriverWait(_driver, timeout);  
152:        wait.until(ExpectedConditions.presenceOfElementLocated(selector));  
153:      } catch (Exception e) {  
154:        throw new NoSuchElementException(String.format("The following element was not visible: %s", selector));  
155:      }  
156:    }  
157:    public void waitUntilElementIsDisplayedOnScreen(By selector) {  
158:      try {  
159:        wait = new WebDriverWait(_driver, timeout);  
160:        wait.until(ExpectedConditions.visibilityOfElementLocated(selector));  
161:      } catch (Exception e) {  
162:        throw new NoSuchElementException(String.format("The following element was not visible: %s ", selector));  
163:      }  
164:    }  
165:    public void waitForElementToBeClickable(By selector) {  
166:      try {  
167:        wait = new WebDriverWait(_driver, timeout);  
168:        wait.until(ExpectedConditions.elementToBeClickable(selector));  
169:      } catch (Exception e) {  
170:        throw new TestException("The following element is not clickable: " + selector);  
171:      }  
172:    }  
173:    public void sleep(final long millis) {  
174:      System.out.println((String.format("sleeping %d ms", millis)));  
175:      try {  
176:        Thread.sleep(millis);  
177:      } catch (InterruptedException ex) {  
178:        ex.printStackTrace();  
179:      }  
180:    }  
181:    public void selectIfOptionTextContains(By selector, String searchCriteria) {  
182:      waitForElementToBeClickable(selector);  
183:      Select dropdown = new Select(getElement(selector));  
184:      List<WebElement> options = dropdown.getOptions();  
185:      String optionText = "";  
186:      if (options == null) {  
187:        throw new TestException("Options for the dropdown list cannot be found.");  
188:      }  
189:      for (WebElement option : options) {  
190:        optionText = option.getText().trim();  
191:        boolean isOptionDisplayed = option.isDisplayed();  
192:        if (optionText.contains(searchCriteria) && isOptionDisplayed) {  
193:          try {  
194:            dropdown.selectByVisibleText(optionText);  
195:            break;  
196:          } catch (Exception e) {  
197:            throw new NoSuchElementException(String.format("The following element did not display: [%s] ", selector.toString()));  
198:          }  
199:        }  
200:      }  
201:    }  
202:    public void selectIfOptionTextEquals(By selector, String searchCriteria) {  
203:      waitForElementToBeClickable(selector);  
204:      Select dropdown = new Select(getElement(selector));  
205:      List<WebElement> options = dropdown.getOptions();  
206:      String optionText = "";  
207:      if (options == null) {  
208:        throw new TestException("Options for the dropdown list cannot be found.");  
209:      }  
210:      for (WebElement option : options) {  
211:        optionText = option.getText().trim();  
212:        boolean isOptionDisplayed = option.isDisplayed();  
213:        if (optionText.equals(searchCriteria) && isOptionDisplayed) {  
214:          try {  
215:            dropdown.selectByVisibleText(optionText);  
216:            break;  
217:          } catch (Exception e) {  
218:            throw new NoSuchElementException(String.format("The following element did not display: [%s] ", selector.toString()));  
219:          }  
220:        }  
221:      }  
222:    }  
223:    public List<String> getDropdownValues(By selector) {  
224:      waitForElementToDisplay(selector);  
225:      Select dropdown = new Select(getElement(selector));  
226:      List<String> elementList = new ArrayList<String>();  
227:      List<WebElement> allValues = dropdown.getOptions();  
228:      if (allValues == null) {  
229:        throw new TestException("Some elements in the list do not exist");  
230:      }  
231:      for (WebElement value : allValues) {  
232:        if (value.isDisplayed()) {  
233:          elementList.add(value.getText().trim());  
234:        }  
235:      }  
236:      return elementList;  
237:    }  
238:  }  
```

*All Source Code can be found in T.J. Maher\'s
[Automate-Amazon](https://github.com/tjmaher/automate-amazon/tree/master/automate-amazon/src/test/java)
repository. *\
\
\
**NEXT**: [We finally can write a Sign-In Test!
\>\>](/2015/12/automate-amazon-writing-sign-in-test.html)\
\
-T.J. Maher\
* Sr. QA Engineer, Fitbit*\
* Boston, MA*\
*\
// Automated tester for \[ 9 \] month and counting!*\
*\
Please note: \'Adventures in Automation\' is a personal blog about
automated testing. It is not an official blog
of [Fitbit.com](http://www.fitbit.com/). *\

<div>

*\
*

</div>

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
