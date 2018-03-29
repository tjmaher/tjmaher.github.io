\-\-- layout: post title: \'Builder Pattern: Creating an
AddressBuilder\' date: \'2016-05-14T04:54:00.001-04:00\' author: T.J.
Maher tags: - code examples - Java - Design Pattern - Builder Pattern
modified\_time: \'2016-05-16T14:18:32.861-04:00\' thumbnail:
https://1.bp.blogspot.com/-jF9\_XTtoocQ/VzbIpK28FtI/AAAAAAAAK\_c/cgCqtHs7lPYCZ7sgiBaHFMOA8-n3GMhLgCLcB/s72-c/Builder\_UML\_class\_diagram.png
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-937632644379332332
blogger\_orig\_url:
http://www.tjmaher.com/2016/05/addressbuilder-builder-pattern-example.html
\-\-- Earlier, I talked about why software developers would use a
Builder Pattern to solve problems such as the bad habit of too many
overloaded methods [telescoping out of
control](http://www.tjmaher.com/2016/04/why-use-builder-pattern-examples-of.html).
With this post, I was going to go over a bit more of what I have found,
and give a simple example of an AddressBuilder.\
\
Down the road, I was going to test out I could use this pattern to
create a ProductBuilder (such as
[ALTA.BLK.LARGE.US](https://www.fitbit.com/alta)) that I could use at my
workplace.\
\
Much further down the road, I was going to experiment with creating a
TestBuilder, where I could set different test parameters, such as
placing a standard shopping cart order with multiple products, set the
shipping level, and payment types.\
\
\... For now, though, I\'ll stick with attempting to create an
AddressBuilder.\
[]{#more}\
\

Sidenote: Fitbit-Boston is hiring!
----------------------------------

\
And, yes, if you are a Senior Software Developer in the Boston area,
[Fitbit is hiring like crazy](https://www.fitbit.com/jobs/search#all)
with positions on our eCommerce team, on the Firmware team that builds
software for our devices, on our automation tool development team, and
on our IOS development team\... mention where you saw this link when you
apply!\
\

The Gang of Four\'s Builder Pattern
-----------------------------------

\
The Builder pattern was first introduced in [Design Patterns: Elements
of Reusable Object-Oriented
Software](http://www.amazon.com/Design-Patterns-Elements-Reusable-Object-Oriented/dp/0201633612)
*(1994)*, written by the \"Gang of Four\":
[\@EricGamma](https://twitter.com/ErichGamma), Richard Helm, Ralph
Johnson and John Vlissides.\
\

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://1.bp.blogspot.com/-jF9_XTtoocQ/VzbIpK28FtI/AAAAAAAAK_c/cgCqtHs7lPYCZ7sgiBaHFMOA8-n3GMhLgCLcB/s640/Builder_UML_class_diagram.png){width="640" height="216"}](https://1.bp.blogspot.com/-jF9_XTtoocQ/VzbIpK28FtI/AAAAAAAAK_c/cgCqtHs7lPYCZ7sgiBaHFMOA8-n3GMhLgCLcB/s1600/Builder_UML_class_diagram.png)
                                                                            *From [Design Patterns: Elements of Reusable Object-Oriented Software](http://www.amazon.com/Design-Patterns-Elements-Reusable-Object-Oriented/dp/0201633612).*
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

\
The purpose of this pattern was to \"Separate the construction of a
complex object from its representation so that the same construction
process can create different representations\". There are four parts
according to the book:\
\
**Builder:**\

-   \"\[\...\] specifies an abstract interface for creating parts of a
    Product object\".

\
\
**ConcreteBuilder**\

-   \"\[\...\] constructs and assembles parts of the product by
    implementing the Builder interface\".
-   \"\[\...\] defines and keeps track of the representation it
    creates\".
-   \"\[\...\] provides an interface for retrieving the product\"

\
\
**Director**\

-   \"\[\...\] constructs an object using the Builder interface\".

\
\
**Product**\

-   \"\[\...\] represents the complex object under construction.
    ConcreteBuilder builds the product\'s internal representation and
    defines the process by which it\'s assembled\".
-   \"\[\...\] includes classes that define the constituent parts,
    including interfaces for assembling the parts into the final
    result\".

\... If you want to read more about Design Patterns, I have [blogged a
bit about them](http://www.tjmaher.com/search/label/Design%20Pattern).\
\

Effective Java\'s Builder Pattern
---------------------------------

\
The Builder Pattern was re-introduced in Joshua Bloch\'s (
[\@JoshBloch](https://twitter.com/joshbloch) ) guide, [Effective
Java](http://www.amazon.com/Effective-Java-2nd-Joshua-Bloch/dp/0321356683)
(2001). From his blog post, [Creating and Destroying Java
Objects](http://www.informit.com/articles/article.aspx?p=1216151&seqNum=2):\

> *\"Instead of making the desired object directly, the client calls a
> constructor (or static factory) with all of the required parameters
> and gets a builder object. Then the client calls setter-like methods
> on the builder object to set each optional parameter of interest.
> Finally, the client calls a parameterless build method to generate the
> object, which is immutable. The builder is a static member class
> \[\...\] of the class it builds.\"\
> \
> \"The Builder pattern is flexible. A single builder can be used to
> build multiple objects. The parameters of the builder can be tweaked
> between object creations to vary the objects. The builder can fill in
> some fields automatically, such as a serial number that automatically
> increases each time an object is created\".*

\
\
Joshua also mentions that another benefit is that the class is now
immutable: Its state, the value of its variables, they won\'t change
after it is created. It\'s pretty set in concrete.\
\

Proceed With Caution, Though
----------------------------

\
Joshua does urge caution: \"The Builder pattern does have disadvantages
of its own\":\

-   **Performance Cost when Creating Object**: \"In order to create an
    object, you must first create its builder. While the cost of
    creating the builder is unlikely to be noticeable in practice, it
    could be a problem in some performance-critical situations\".
-   **Only If Parameters \>= 4**: \"\[T\]he Builder pattern is more
    verbose than the telescoping constructor pattern, so it should be
    used only if there are enough parameters, say, four or more\".

\

Drafting the Address
--------------------

\
Consider a small sample of the types of addresses you can have:\

-   An address with Address Name, Address, City and State, such as:
    *Fitbit-Boston, One Marina Park Drive, Boston, MA* , suitable for
    directions in Google Maps.
-   A mailing address, which can add a second line to the address, and
    includes a zip code, such as *Suite 701*, and *02210*.
-   An address which also adds the country, such as *United States*.

\
If we were to create this, we would have to use three different
constructors. Instead, we will create an Address Builder so that we can
assemble the address like so:\

-   Address.Builder(\"Fitbit-Boston\", \"One Marina Park Drive\",
    \"Boston\", \"MA\").build();
-   Address.Builder(\"Fitbit-Boston\", \"One Marina Park Drive\",
    \"Boston\", \"MA\") .setAddress2(\"Suite
    701\").setZip(\"02210\").build();
-   Address.Builder(\"Fitbit-Boston\", \"One Marina Park Drive\",
    \"Boston\", \"MA\") .setAddress2(\"Suite
    701\").setZip(\"02210\").setCountry(\"United States\").build();

\... But now we are getting ahead of ourselves!\
\

Writing the Code
----------------

\
First, let\'s set up the parameters in the class.\
\
The Address object, once constructed from the class, will be unchanging.
We will use the keyword **final** when we declare the variable, making
it a constant.\
\
**Address.java**\

``` {.brush: .java}
 
public class Address {
    private final String addressName; 
    private final String address1; 
    private final String address2; 
    private final String city; 
    private final String state;
    private final String zip;
    private final String country; 
```

\
Next, we are going to set up the ConcreteBuilder type, making this
internal class static.\
\
According to our Address example above, there are two types of fields:\

-   Required, such as Address Name, Address Line 1, City, State
-   Optional, such as Address Line 2, Zip Code, and Country

\
The optional ones we will save as Strings, but with the required fields,
such as Address Name, we will also the keyword **final**.\
\
**Builder**\

``` {.brush: .java}
 
public static class Builder {
        // Required Parameters
        private final String name;
        private final String address1;
        private final String city;
        private final String state;

        // Optional Parameters
        private String address2;
        private String zip;
        private String country;
  }
```

\
Once we figure out which fields are always required, we can create a
constructor for the Builder class, to feed the values inputted into the
Address\' private fields. We do that with the **this** keyword.\

``` {.brush: .java}
 
public Builder(String name, String address1, 
               String city, String state) {
            this.name = name;
            this.address1 = address1;
            this.city = city;
            this.state = state;
}
```

\
Next, we want a way to set up the optional parameters:\

``` {.brush: .java}
 
       public Builder setAddress2(String value) {
            address2 = value;
            return this;
        }

        public Builder setCountry(String value) {
            country = value;
            return this;
        }

        public Builder setZip(String value) {
            zip = value;
            return this;
        }
```

\
Let\'s create a method called build to build the object:\

``` {.brush: .java}
    public Address build() {
            return new Address(this);
        }
    }
```

\
Now, let\'s create a constructor for Address, and make it private,
accessible only to the Builder itself.\

``` {.brush: .java}
private Address(Builder builder) {
        this.addressName = builder.name;
        this.address1 = builder.address1;
        this.city = builder.city;
        this.state = builder.state;
        this.address2 = builder.address2;
        this.country = builder.country;
        this.zip = builder.zip;
    }
```

\... And there you have it! Our Address and Address Builder is all
constructed!\
\

Crafting a Test
---------------

\
Now that we created everything\... how can we turn this into a test?\
\
Let\'s write a method print out the address we assembled. To keep things
neat, let\'s not print out any blank lines.\
\
If there isn\'t an Address2, or a Zip code, let\'s not print it out.\
\
And, not to get all \"meta\", but let\'s use a Builder pattern called
StringBuilder to assemble all the pieces of the address. We can create a
StringBuilder object, call it \"output\" and append the values of the
String components to the StringBuilder.\
\

``` {.brush: .java}
    
   private StringBuilder appendIfNotBlank(
      StringBuilder output, String value ){
         if (value != null ){
             output.append(value).append("\n");
         }
         return output;
   }
```

\... This method will save us a lot of code duplication, following the
software design principle of **Don\'t Repeat Yourself** (DRY).\
\
Let\'s override the method we use to print, the *toString()* method
added to every single Java object.\

``` {.brush: .java}
@Override
public String toString(){
   StringBuilder output = new StringBuilder();
   output.append(this.addressName).append("\n")
        .append(this.address1 ).append("\n");
   appendIfNotBlank(output, address2);
   output.append(this.city).append(", ").append(this.state).append("  ");
   appendIfNotBlank(output, this.zip);
   appendIfNotBlank(output, this.country);
   output.append("\n");
   return output.toString();
}
```

\
\
Last, but not least, let\'s create a test to:\

-   Assemble the new addresses we are creating
-   Store them in variables such as *fitbitBostonAddress* and
    *fitbitBostonMailingAddressWithCountry*.
-   Print out the new addresses and see what happens!

``` {.brush: .java}
@Test
public void test_printUnitedStatesAddresses(){
   Address fitbitBostonAddress = new Address.Builder("Fitbit-Boston", 
       "One Marina Park Drive", "Boston", "MA").build();
   Address fitbitBostonMailingAddress = new Address.Builder("Fitbit-Boston", 
       "One Marina Park Drive", "Boston", "MA")
        .setAddress2("Suite 701").setZip("02210").build();
   Address fitbitBostonMailingAddressWithCountry = new Address.Builder("Fitbit-Boston", 
       "One Marina Park Drive", "Boston", "MA")
        .setAddress2("Suite 701").setZip("02210").setCountry("United States").build();

   System.out.println("Sample Address Formats:\n");
   System.out.println(fitbitBostonAddress);
   System.out.println(fitbitBostonMailingAddress);
   System.out.println(fitbitBostonMailingAddressWithCountry);
}
```

The Moment of Truth
-------------------

\
When we run the test, we get the following output printed out:

\

``` {.CICodeFormatter}
 [TestNG] Running:  
  C:\Users\tmaher\.IdeaIC15\system\temp-testng-customsuite.xml  
 Sample Address Formats:  
   
 Fitbit-Boston  
 One Marina Park Drive  
 Boston, MA   
   
 Fitbit-Boston  
 One Marina Park Drive  
 Suite 701  
 Boston, MA 02210  
   
   
 Fitbit-Boston  
 One Marina Park Drive  
 Suite 701  
 Boston, MA 02210  
 United States  
   
   
 ===============================================  
 Default Suite  
 Total tests run: 1, Failures: 0, Skips: 0  
 ===============================================  
```

\
Looking for sourcecode you can play around with? You can view it on my
GitHub site under
[BuilderPattern\_Java](https://github.com/tjmaher/BuilderPattern_Java/tree/master/BuilderPattern_Java/src/src/test/java/com/tmaher/builderpattern).\
\
\

::: {#toc-section .toc-section}
**Examining Builder Patterns:**\

-   **Part One:** [Anti-Pattern: Telescoping
    Constructors](http://www.tjmaher.com/2016/04/why-use-builder-pattern-examples-of.html)
-   **Part Two:** [Investigating Address
    Builder](http://www.tjmaher.com/2016/05/addressbuilder-builder-pattern-example.html)
-   **Source Code:** [GitHub, T.J.
    Maher](https://github.com/tjmaher/BuilderPattern_Java/tree/master/BuilderPattern_Java/src/src/test/java/com/tmaher/builderpattern)
:::

\
\
\
That\'s it for now! Happy Testing!\
\
-T.J. Maher\
Sr. QA Engineer,\
Fitbit-Boston\
\
*// QA Engineer since Aug. 1996\
// Automation developer for \[ 1 \] year and still counting!*
