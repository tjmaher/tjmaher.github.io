\-\-- layout: post title: Elemental Selenium code examples are being
written in Java! date: \'2016-04-13T01:27:00.002-04:00\' author: T.J.
Maher tags: - beginner - Java - WebDriver - Dave Haeffner
modified\_time: \'2016-04-29T08:06:52.576-04:00\' thumbnail:
https://4.bp.blogspot.com/-88S2jejYIu0/Vw3QADT0vqI/AAAAAAAAK-E/TyPYtAw5u4c3RDfVdSbim5FAEicO-ABlwCLcB/s72-c/elementak-selenium.png
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-2867227353940146923
blogger\_orig\_url:
http://www.tjmaher.com/2016/04/elemental-selenium-code-examples-are.html
\-\-- I love reading [Elemental
Selenium](http://elementalselenium.com/tips), automation development
tips written by Dave Haeffner \-- who I have written about [in this
blog](http://www.tjmaher.com/2015/06/spotlight-on-dave-haeffner.html).\
\

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://4.bp.blogspot.com/-88S2jejYIu0/Vw3QADT0vqI/AAAAAAAAK-E/TyPYtAw5u4c3RDfVdSbim5FAEicO-ABlwCLcB/s400/elementak-selenium.png){width="400" height="363"}](https://4.bp.blogspot.com/-88S2jejYIu0/Vw3QADT0vqI/AAAAAAAAK-E/TyPYtAw5u4c3RDfVdSbim5FAEicO-ABlwCLcB/s1600/elementak-selenium.png)
                                                                                                       *Archive of Dave\'s [Weekly Newsletter](http://elementalselenium.com/) of Automation Tips!*
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

\
The only problem has been that Dave\'s language of choice for the code
examples is in Ruby. Since I only have been just getting back into
coding, I have had difficulty converting the code into Java, what I am
using on the workplace.\
\
There is hope! If you take a look on Dave\'s (
[\@TourDeDave](https://twitter.com/TourDeDave) ) [GitHub
site](https://github.com/tourdedave), you can find the corresponding
Elemental Selenium Tips [source
code](https://github.com/tourdedave/elemental-selenium-tips).\
\
\
[]{#more}\
\

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://3.bp.blogspot.com/-iuN4BMAsfWA/Vw3Rh-b-STI/AAAAAAAAK-Q/qjZpIahAiHwC4WnQBaHje1pxVa1Eez5tACLcB/s400/tips.png){width="400" height="290"}](https://3.bp.blogspot.com/-iuN4BMAsfWA/Vw3Rh-b-STI/AAAAAAAAK-Q/qjZpIahAiHwC4WnQBaHje1pxVa1Eez5tACLcB/s1600/tips.png)
                                                                               [Sourcecode](https://github.com/tourdedave/elemental-selenium-tips) for examples in the Elemental Selenium Tips
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

\
It looks like around a third of the seventy examples have been converted
to Java.\
\
Let\'s compare the first tip, [uploading a
file](http://elementalselenium.com/tips/1-upload-a-file), about how to
setup and teardown a browser.\
**\
Setup/
Teardown**: [Ruby](http://elementalselenium.com/tips/1-upload-a-file):\

``` {.brush: .ruby}

 # filename: upload.rb  
 require 'selenium-webdriver'  
 require 'rspec/expectations'  
 include RSpec::Matchers  
 def setup  
  @driver = Selenium::WebDriver.for :firefox  
 end  
 def teardown  
  @driver.quit  
 end  
 def run  
  setup  
  yield  
  teardown  
 end  
```

\
\
[Setup/
Teardown: ]{style="font-weight: bold;"}[Java](https://github.com/tourdedave/elemental-selenium-tips/blob/master/01-upload-a-file/java/src/test/java/Upload.java):\

``` {.brush: .javafx}
public class Upload {  
   WebDriver driver;  
   @Before  
   public void setUp() throws Exception {  
     driver = new FirefoxDriver();  
   }  
   @After  
   public void tearDown() throws Exception {  
     driver.quit();  
   }  
```

\
\... You know, they look pretty similar. Let\'s compare the Ruby version
Dave has in his original tip to the one that he has in GitHub.\
\
**File Upload
Test:** [Ruby](http://elementalselenium.com/tips/1-upload-a-file):\

``` {.brush: .ruby}
 run do  
  filename = 'some-file.txt'  
  file = File.join(Dir.pwd, filename)  
  @driver.get 'http://the-internet.herokuapp.com/upload'  
  @driver.find_element(id: 'file-upload').send_keys file  
  @driver.find_element(id: 'file-submit').click  
  uploaded_file = @driver.find_element(id: 'uploaded-files').text  
  expect(uploaded_file).to eql filename  
 end  
```

\
\
**File Upload
Test**: [Java](https://github.com/tourdedave/elemental-selenium-tips/blob/master/01-upload-a-file/java/src/test/java/Upload.java):\

``` {.brush: .javafx}
 @Test  
   public void uploadFile() throws Exception {  
     String filename = "some-file.txt";  
     File file = new File(filename);  
     String path = file.getAbsolutePath();  
     driver.get("http://the-internet.herokuapp.com/upload");  
     driver.findElement(By.id("file-upload")).sendKeys(path);  
     driver.findElement(By.id("file-submit")).click();  
     String text = driver.findElement(By.id("uploaded-files")).getText();  
     assertThat(text, is(equalTo(filename)));  
   }  
```

\
Ruby and Java are as different as night and day. If you were a newly
minted software developer, there would be no way to translate from Ruby,
where much of the complexities are hidden from view, to Java, where
everything is all out in the open.\
\
Wondering what the AssertThat is? That is
[Hamcrest](https://code.google.com/archive/p/hamcrest/wikis/Tutorial.wiki).
Instead of using TestNG\'s assertEquals(actualValue, expectedValue) this
is a bit more readable.\
\
I\'m glad that the code examples from Ruby to Java. This would help
former manual testers like myself not just learn automation development,
but learn Java development.\
\
Hrm\... it looks like Dave is [looking for people to translate Ruby to
Java](https://github.com/tourdedave/elemental-selenium-tips) for some of
his code examples:\

> *\"They\'re currently only available in Ruby. But for each one that
> gets converted to a new programming language, I\'ll do a full write-up
> for it.*\
> *\"To submit your entry:*\
>
> -   *\"Fork the repo*
> -   *\"Choose a tip to port*
> -   *\"Add a folder to it for the language you want (e.g., javascript,
>     java, csharp, php, python, etc.)*
> -   *\"Write the code example*
> -   *\"Submit a pull request\"*

\... Work has been quite busy, bleeding into my free time\... but maybe
I can make this my next weekend project?\
\
- T.J. Maher\
 Sr. QA Engineer, Fitbit-Boston\
\
*// Software QA Engineer since August 1996*\
*// Automation Developer: \[ 1 \] year and counting*
