\-\-- layout: post title: \'RESTful Testing with Stripe: Storing API
Keys in properties files and initial setup of StripeUtils\' date:
\'2016-02-23T00:08:00.000-05:00\' author: T.J. Maher tags: - code
examples - Java - Rest API modified\_time:
\'2016-04-29T07:37:12.869-04:00\' blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-3878698421194107402
blogger\_orig\_url:
http://www.tjmaher.com/2016/02/restful-testing-with-stripe-storing-api\_23.html
\-\-- *This post is third in a series of six. Need to go [back to the
beginning](/2016/02/coming-up-how-to-work-with-rest-apis.html)?*\
\
So far we covered why we should incorporate tests other than UI tests
into our automation test suite. We gave a brief background on RESTful
APIs. And we showed how to interact with the Stripe API through GET
methods with HTTPS and POST methods with cURL.\
\
Now, we can start writing code to interact with Stripe! We are going
to:\

-   Store the Stripe API Key in a properties file, pretending that the
    general purpose key is actually two different keys: One for the US
    and one for Canada.
-   Write a method to Load the Properties
-   Create a basic Stripe Utilities that forces the user to select which
    country we are using. Using that information the proper API key is
    loaded. 
-   Start writing a test class containing tests that confirm Stripe
    Utilities can only be instantiated if and only if the country is
    either US or Canada. 

### 

### **What Our Framework Will Look Like** {#what-our-framework-will-look-like style="font-size: medium; font-weight: normal;"}

::: {style="font-size: medium; font-weight: normal;"}
\
[]{#more}**\
**
:::

::: {style="font-size: medium; font-weight: normal;"}
By the end of this blog post, our automated test framework will look
something like this:
:::

::: {style="font-size: medium; font-weight: normal;"}
\
:::

::: {style="font-size: medium; font-weight: normal;"}
**src/test/java**
:::

data

-   LoadProperties.java

libraries

-   StripeUtils.java

properties

-   qa-properties.properties

testcases

-   Stripe.java

### 

First, let\'s talk about storing the keys in properties files.\

###  What is a .properties file?

<div>

We are going to store the Stripe API Key for the general public in a
properties file\... But what is a properties file?\
\
A Properties file is just a plain ole text file with the extension
\".properties\" after it.

</div>

> \".properties is a file extension for files mainly used in Java
> related technologies to store the configurable parameters of an
> application. They can also be used for storing strings for
> Internationalization and localization; these are known as Property
> Resource Bundles.\
> \
> \"Each parameter is stored as a pair of strings, one storing the name
> of the parameter (called the key), and the other storing the value\".
> *- Wikipedia,
> [.properties ](https://en.wikipedia.org/wiki/.properties)*

::: {style="text-align: center;"}
**[. . .]{style="font-size: x-large;"}**
:::

> \"Properties is a subclass of Hashtable. It is used to maintain lists
> of values in which the key is a String and the value is also a
> String.\
> \
> \"The Properties class is used by many other Java classes. For
> example, it is the type of object returned by System.getProperties( )
> when obtaining environmental values \[\...\]\"\
>
> ::: {style="text-align: right;"}
> \- *TutorialsPoint, [Java
> Properties](http://www.tutorialspoint.com/java/java_properties_class.htm) *
> :::

\

### How Do We Implement It?

*StackOverflow, [Loading a Properties File From a Java
Package](http://stackoverflow.com/questions/333363/loading-a-properties-file-from-java-package):*\

> \"When loading the Properties from a Class in the package
> com.al.common.email.templates you can use\"

``` {.lang-java .prettyprint .prettyprinted style="background-color: #eeeeee; border: 0px; color: #393318; font-family: Consolas, Menlo, Monaco, 'Lucida Console', 'Liberation Mono', 'DejaVu Sans Mono', 'Bitstream Vera Sans Mono', 'Courier New', monospace, sans-serif; font-size: 13px; margin-bottom: 1em; max-height: 600px; overflow: auto; padding: 5px; width: auto; word-wrap: normal;"}
Properties prop = new Properties();
InputStream in = getClass().getResourceAsStream("foo.properties");
prop.load(in);
in.close();
```

> \"(Add all the necessary exception handling).

> \"If your class is not in that package, you need to aquire the
> InputStream slightly differently:

``` {.lang-java .prettyprint .prettyprinted 75="" normal="" style="background-color: #eeeeee; border: 0px; color: #393318; font-family: Consolas, Menlo, Monaco, 'Lucida Console', 'Liberation Mono', 'DejaVu Sans Mono', 'Bitstream Vera Sans Mono', 'Courier New', monospace, sans-serif; font-size: 13px; margin-bottom: 1em; max-height: 600px; overflow: auto; padding: 5px;" =""}
InputStream in = 
 getClass().getResourceAsStream("/com/al/common/email/templates/foo.properties");
```

> \"Relative paths (those without a leading \'/\') in
> getResource()/getResourceAsStream() mean that the resource will be
> searched relative to the directory which represents the package the
> class is in.\
> \
> \"Using java.lang.String.class.getResource(\"foo.txt\") would search
> for the (inexistent) file /java/lang/String/foo.txt on the classpath.\
> \
> \"Using an absolute path (one that starts with \'/\') means that the
> current package is ignored\".

\

::: {style="text-align: right;"}
*- *
:::

\

### Store the Stripe API Key

\
We can see in the **Stripe API documentation** at
<https://stripe.com/docs/api#intro> that in the cURL statement used to
hit their endpoint\...\
\

``` {.hljs .language-bash style="background: rgb(39, 43, 45); border-radius: 5px; border: 0px; color: #d0d0d0; direction: ltr; font-family: 'Source Code Pro', Menlo, monospace; font-size: 13px; line-height: 1.5em; outline: 0px; padding: 20px 40px; tab-size: 4; vertical-align: baseline; white-space: pre-wrap; word-break: normal;"}
curl https://api.stripe.com/v1/charges \ -u sk_test_BQokikJOvBiI2HlWgH4olfQ2: 
```

\
\... the Stripe API Key for the general public
is *sk\_test\_BQokikJOvBiI2HlWgH4olfQ2*.\
\
That means that our properties file would look like this:\
\
**properties/qa-properties.properties**\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 # Stripe Public API key 
 stripe.api.key=sk_test_BQokikJOvBiI2HlWgH4olfQ2  
 stripe.api.version=2015-10-01  
```

\

### How to Read the Properties File

We are going to create a class called **LoadProperties** to handle
fetching the properties data.\
\
LoadProperties method (private):\

-   Create a static method *loadProperties,* pointing to where the
    qa-properties.properties file is located. 
-   Instantiate a new Properties object, from a class [built into Java
    7](https://docs.oracle.com/javase/7/docs/api/java/util/Properties.html).
-   Attempt to load the file located at the filepath, catching any
    errors such as if the file is not there, or there is some  Input /
    Output error opening or closing the file. 
-   If there are any errors, print a stack trace. 
-   If there aren\'t any errors, read the file\'s contents in a
    [FileInputStream](https://docs.oracle.com/javase/7/docs/api/java/io/FileInputStream.html)
    called \"f\", the load the contents into properties.
-   Read the entire file, line by line. 

<div>

Once this method is created, we can have a public method, *qaData*, call
this private method. 

</div>

\
**data/LoadProperties.java**\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 public class LoadProperties {  
   public static Properties qaData = loadProperties("src/test/java/properties/qa-properties.properties");  
   private static Properties loadProperties(String filePath) {  
     Properties properties = new Properties();  
     try {  
       FileInputStream f = new FileInputStream(filePath);  
       properties.load(f);  
     } catch (FileNotFoundException e) {  
       e.printStackTrace();  
     } catch (IOException e) {  
       e.printStackTrace();  
     }  
     return properties;  
   }  
   public static String getPropertyValue(String path, String key) {  
     Properties p = loadProperties(path);  
     String result = "";  
     Set<String> values = p.stringPropertyNames();  
     for (String value : values) {  
       if (StringUtils.equalsIgnoreCase(value, key)) {  
         result = p.getProperty(value);  
         break;  
       }  
     }  
     return result;  
   }  
 }  
```

\
\

### The Stripe Utilities class

The only acceptable country is \"Locale.US\". We are going to force
everything else to fail.\
\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 package libraries;  
 import com.stripe.Stripe;  
 import data.LoadProperties;  
 import org.testng.TestException;  
 import org.testng.annotations.Test;  
 import java.util.Locale;  
 /**  
  * Created by tmaher on 2/16/2016.  
  */  
 public class StripeUtils {  
   private static String getAPIKey() {  
     return Stripe.apiKey = LoadProperties.qaData.get("stripe.api.key").toString();  
   }  
   private static String getAPIVersion() {  
     return Stripe.apiVersion = LoadProperties.qaData.get("stripe.api.version").toString();  
   }  
   private static void getAPIKey(Locale country) {  
     getAPIVersion();  
     if (country.equals(Locale.US)) {  
       getAPIKey();  
     } else {  
       throw new TestException("ERROR: Stripe is used only for US. Country entered: " + country);  
     }  
   }  
   public StripeUtils(Locale country) {  
     getAPIKey(country);  
   }  
   private static StripeUtils setAPIKey(Locale country) {  
     return new StripeUtils(country);  
   }  
 }  
```

\

### Test Early. Test Often. 

Let\'s create a folder called *testcases*, and place in it a test class,
*Stripe.java*.\
\
**testcases.Stripe.java:**\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 package testcases;  
 import libraries.StripeUtils;  
 import org.testng.annotations.Test;  
 import java.util.Locale;  
 /**  
  * Created by tmaher on 2/16/2016.  
  */  
 public class Stripe {  
   @Test  
   public void test_validCountry() {  
     StripeUtils stripe = new StripeUtils(Locale.US);  
     // This will always pass.  
   }  
   @Test  
   public void test() {  
     StripeUtils stripe = new StripeUtils(Locale.GERMANY);  
     // This will always fail: ERROR: Stripe is used only for US. Country entered: de_DE   
   }  
 }  
```

\
Our test automation structure is starting to be built!\
\
With the next blog post, we will be getting into using UriBuilder,
HttpGet and other Apache HttpComponents.\
\
Until next time, Happy Testing!\
\
**NEXT:** [UriBuilder, HttpGet and other Apache
HttpComponents](/2016/02/restful-testing-with-stripe-using.html)\
\

::: {#toc-section .toc-section}
**RESTful Testing with Stripe:**\

-   [Introduction](/2016/02/coming-up-how-to-work-with-rest-apis.html)
-   **Part One:** [Intro to REST
    APIs](/2016/02/restful-testing-with-stripe-brief.html)
-   **Part Two:** [Interacting with Stripe using HTTPS and
    cURL](/2016/02/restful-testing-with-stripe-interacting.html)
-   **Part Three:** [API Keys, Property files, and Initial
    Setup](/2016/02/restful-testing-with-stripe-storing-api_23.html)
-   **Part Four:** [UriBuilder, HttpGet and other Apache
    HttpComponents](/2016/02/restful-testing-with-stripe-using.html)
-   **Part Five:** [From JSON to Object: HttpEntity and
    GSON](/2016/02/restful-testing-with-stripe-from-json.html)
-   **Source Code:** [GitHub, T.J.
    Maher](https://github.com/tjmaher/RESTful_Testing_Using_Stripe)
:::

\
\
[-T.J.
Maher]{style="background-color: white; color: #222222; font-family: "calibri"; font-size: 15.4px; line-height: 21.56px;"}\

<div>

\* Sr. QA Engineer, Fitbit*\
* Boston, MA*\
*\
// Automated tester for \[ 11 \] month and counting!*\
*\
Please note: \'Adventures in Automation\' is a personal blog about
automated testing. It is not an official blog
of [Fitbit.com](http://www.fitbit.com/). *

</div>

<div>

*\
*

</div>

\
