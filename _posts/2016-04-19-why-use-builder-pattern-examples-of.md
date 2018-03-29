\-\-- layout: post title: Why Use a Builder Pattern? Examples of
Telescoping Constructors when storing Address data date:
\'2016-04-19T07:29:00.001-04:00\' author: T.J. Maher tags: - code
examples - Java - intermediate - Design Pattern - Builder Pattern
modified\_time: \'2016-05-14T14:07:01.568-04:00\' blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-7450291804197536634
blogger\_orig\_url:
http://www.tjmaher.com/2016/04/why-use-builder-pattern-examples-of.html
\-\-- Let\'s say you wanted to fill out the Billing Address of a form
that has the following fields:\

-   Name
-   Street Address 1 
-   Street Address 2
-   City
-   State
-   ZipCode
-   Country

\
If you wanted to store this information into an Address object, the
class could look like:\
\
**Address.java:**\

``` {.brush: .java}
     

public class Address {

  private String name;
  private String streetAddress1;
  private String streetAddress2;
  private String city;
  private String state;
  private String zipCode;
  private String country;
  
}
```

How would we set these fields?\
\
[]{#more}\
\

Exploration: Using Constructors
-------------------------------

\
If we wanted to feed an address such as the one below into an object
called **Address**:\
\
FITBIT\
ONE MARINA PARK DRIVE\
BOSTON, MA 02210\
UNITED STATES\
\
\... we could create a constructor that looks like\...\
\

``` {.brush: .java}
 

public class Address {

  private String name;
  private String streetAddress1;
  private String streetAddress2;
  private String city;
  private String state;
  private String zipCode;
  private String country;

  Address ( String name, String streetAddress1, String city,
            String state, String zipCode, String country){
    this.name = name;
    this.streetAddress1 = streetAddress1;
    this.city = city;
    this.state = state;
    this.zipCode = zipCode;
    this.country = country;
  }
}
```

\
But what if we wanted to add a suite to the address, to make it more
accurate?\
\
FITBIT\
ONE MARINA PARK DRIVE\
SUITE 701 BOSTON, MA 02210\
UNITED STATES\
\
Our entire class now would look like:\

``` {.brush: .java}
 

public class Address {

  private String name;
  private String streetAddress1;
  private String streetAddress2;
  private String city;
  private String state;
  private String zipCode;
  private String country;

  // First Constructor Type: Used When there is only one Address
  Address ( String name, String streetAddress1, String city,
            String state, String zipCode, String country){
    this.name = name;
    this.streetAddress1 = streetAddress1;
    this.city = city;
    this.state = state;
    this.zipCode = zipCode;
    this.country = country;
  }

  // Second Constructor Type: Used When there is Address1 and Address2.
  Address ( String name, String streetAddress1, String streetAddress2,
            String city, String state, String zipCode, String country){
    this.name = name;
    this.streetAddress1 = streetAddress1;
    this.streetAddress2 = streetAddress2;
    this.city = city;
    this.state = state;
    this.zipCode = zipCode;
    this.country = country;
  }
}
```

\

Problem One: Duplication of Code
--------------------------------

\
Yes, this is allowed in Java. It is calling **Overloading the Method**.
(
[Example](https://docs.oracle.com/javase/tutorial/java/javaOO/methods.html)
)\
\
One problem is that the code is not as clean as it could be\... We are
no longer following the main rule of software development: **Don\'t
Repeat Yourself** ( The
[DRY](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself) principle
).\
\
What about if we wanted to mail a package from a warehouse in the Unites
States to someone in the United States? We wouldn\'t need to fill out
the country\... would we need to create yet another overloaded
constructor for the country?\
\

``` {.brush: .java}
 

// Third Constructor Type: Used Within Same Country
Address ( String name, String streetAddress1, String streetAddress2,
            String city, String state, String zipCode){
```

\
We can see that the other problem is that the *signature* of the
Constructor method grows each time the method is overloaded, with even
more duplicated code. It becomes a *telescoping constructor*.\
\

Problem Two: Possible Confusion of Variable Order
-------------------------------------------------

\
Take a look at the following address:\
\
Mr. Address Argentine\
Piedras No 623\
Piso2 Dto.4\
C1070AAM Capital Federal\
ARGENTINA\
\
The US Format is:\

-   City
-   State
-   Zip
-   Country *( optional in the US )*

\
Argentina ( and many other formats ) are\

-   Postal Code
-   City/town/locality
-   Country

These constructors allow you to enter values in the completely wrong
order.\
\

``` {.brush: .java}
 

// Correct Format
Address billingAddress = new Address(
     "FITBIT", "ONE MARINA PARK DRIVE",
     "SUITE 701",
     "BOSTON", "MA", "02210", "United States");

// X INCORRECT FORMAT, but LEGAL!!!
Address shippingAddreess = new Address(
     "Mr. Address Argentine",
     "Piedras No 623",
     "Piso2 Dto.4",    
     "C1070AAM", "Capital Federal",
     "ARGENTINA"); 
```

\
To demonstrate what is happening, let\'s take a step back to figure out
how to print the contents of the Address class.\
\
**Overriding** the *toString* method that allows us to print to the
console.\
\

``` {.brush: .java}
 

  @Override
  public String toString() {
    return "Name: " + this.name + "\n"
        + "Address1: " + this.streetAddress1 + "\n"
        + "Address2: " + this.streetAddress2 + "\n"
        + "City: " + this.city + "\n"
        + "State: " + this.state + "\n"
        + "Zip: " + this.zipCode + "\n"
        + "Country: " + this.country + "\n";
  }
```

\
Now, we can create a test that demonstrate what is happening:\
\

``` {.brush: .java}
 

  @Test
  public static void testAssigningAddresses() {
    Address billingAddress = new Address(
        "FITBIT", "ONE MARINA PARK DRIVE",
        "SUITE 701",
        "BOSTON", "MA", "02210", "United States");
    System.out.println(billingAddress);

    Address shippingAddress = new Address(
        "Mr. Address Argentine",
        "Piedras No 623",
        "Piso2 Dto.4",
        "C1070AAM", "Capital Federal",
        "ARGENTINA");
    System.out.println(shippingAddress);
  }
```

\
The test prints the following output:\
\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 Name: FITBIT  
 Address1: ONE MARINA PARK DRIVE  
 Address2: SUITE 701  
 City: BOSTON  
 State: MA  
 Zip: 02210  
 Country: United States  


 Name: Mr. Address Argentine  
 Address1: Piedras No 623  
 Address2: null  
 City: Piso2 Dto.4  
 State: C1070AAM  
 Zip: Capital Federal  
 Country: ARGENTINA  
```

\
\... With ARGENTINA, the Zip and the State value was transposed!\
\
\
Want to take a look at the sample code listed in full? You can find it
on my GitHub site at
<https://github.com/tjmaher/Address_Telescoping_Constructors/blob/master/src/test/java/Address.java>.\

Introducing the Builder Pattern
-------------------------------

\
Back in 2008, in his book **Effective Java,** ( [Amazon
link](http://www.amazon.com/Effective-Java-2nd-Joshua-Bloch/dp/0321356683/)
) Joshua Block recognized these two problems.\
\
He expanded on the *Builder pattern*, a software design pattern
discussed in the Gang of Four\'s [Design Patterns: Elements of Reusable
Object-Oriented
Software](http://www.amazon.com/Design-Patterns-Elements-Reusable-Object-Oriented/dp/0201633612)
which addresses these concerns.\

> \"Traditionally, programmers have used the telescoping constructor
> pattern, in which you provide a constructor with only the required
> parameters, another with a single optional parameter, a third with two
> optional parameters, and so on, culminating in a constructor with all
> the optional parameters \[\...\]\
> \
> \"\[\...T\]he telescoping constructor pattern works, but it is hard to
> write client code when there are many parameters, and harder still to
> read it. The reader is left wondering what all those values mean and
> must carefully count parameters to find out. Long sequences of
> identically typed parameters can cause subtle bugs. If the client
> accidentally reverses two such parameters, the compiler won't
> complain, but the program will misbehave at runtime.\
> \
> \"Luckily, there is a third alternative that combines the safety of
> the telescoping constructor pattern with the readability of the
> JavaBeans pattern. It is a form of the Builder pattern \[Gamma95, p.
> 97\]. Instead of making the desired object directly, the client calls
> a constructor (or static factory) with all of the required parameters
> and gets a builder object. Then the client calls setter-like methods
> on the builder object to set each optional parameter of interest.
> Finally, the client calls a parameterless build method to generate the
> object, which is immutable\".\
> *- From Joshua Bloch\'s article, [Creating and Destroying Java
> Objects](http://www.informit.com/articles/article.aspx?p=1216151&seqNum=2),
> May 16, 2008.*

\
What if we could set an address like so?:\

``` {.brush: .java}
Address billingAddress = new Address.Builder(
              .setName("Mr. Address Argentine")
              .setAddress1("Piedras No 623")
              .setCity("Piso2 Dto.4")
              .setState("Capital Federal")
              .setZip("C1070AAM")
              .setCountry("ARGENTINA");
```

\
In our next blog article, we will be examining [how to implement
this](http://www.tjmaher.com/2016/05/addressbuilder-builder-pattern-example.html).\
\
\
\
\

::: {#toc-section .toc-section}
**Examining Builder Patterns:**

-   **Part One:** [Anti-Pattern: Telescoping
    Constructors](http://www.tjmaher.com/2016/04/why-use-builder-pattern-examples-of.html)
-   **Part Two:** [Investigating Address
    Builder](http://www.tjmaher.com/2016/05/addressbuilder-builder-pattern-example.html)
-   **Source Code:** [GitHub, T.J.
    Maher](https://github.com/tjmaher/BuilderPattern_Java/tree/master/BuilderPattern_Java/src/src/test/java/com/tmaher/builderpattern)
:::

\
\
Until then, Happy Testing!\
\
- T.J. Maher\
Sr. QA Engineer,\
Fitbit-Boston\
\
*// QA Engineer since Aug. 1996\
// Automation developer for \[ 1 \] year and still counting!*
