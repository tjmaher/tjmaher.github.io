\-\-- layout: post title: Notes on Franklin Webber\'s webinar, The Ruby
Behind Chef date: \'2018-01-04T23:55:00.000-05:00\' author: T.J. Maher
tags: - Chef - DevOps - Ruby modified\_time:
\'2018-01-28T08:43:11.467-05:00\' thumbnail:
https://i.ytimg.com/vi/CnBP2uv3Yog/default.jpg blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-5573106663606708469
blogger\_orig\_url:
http://www.tjmaher.com/2018/01/the-ruby-behind-chef.html \-\-- For the
past week, I\'ve been trying to do a cram session on Ruby, one of the
many programming languages I will be [using in my next
job](https://www.linkedin.com/in/tjmaher1/) as a Software Developer in
Test.\
\
Why Ruby? Chef, A DevOps tool, is written in Ruby\... a language I
don\'t even know.\
\
The quickest way to learn how to swim? Row your boat into the deepest
part of the lake and jump right in. Try not to drown too much.\
\
Likewise, the quickest way I have found for me to learn? Dive right in.
See how how long I can tread water before choking, sputtering, and
coming up for air.\
\
Care to go on a dive with me?\
\
**[\
]{.underline}The Ruby Behind Chef** *(September 2016)*\
*Franklin Webber, Training Lead at Chef*\

[*https://youtu.be/CnBP2uv3Yog*](https://youtu.be/CnBP2uv3Yog)\
\
[]{#more}\
\
The video, above, is very entertaining. Franklin Webber, is both a Chef
developer and a Ruby developer.\
\
The best way to describe how Chef uses Ruby to people who don\'t know
either Chef or Ruby? Franklin talks about how he wants to write a faux
version of Chef that he has dubbed \"T-Rex Chef\".\
\
With **T-REX\_CHEF.rb** Franklin demonstrates, using Ruby, how to parse
a Chef recipe and how to evaluate resources.\
\
By the way, installing Ruby it on the Mac or PC is pretty easy. Just go
to <https://www.ruby-lang.org/en/> and Download it for Windows, Linux or
the Mac.\
\

**Now, what is Chef?**
----------------------

\
\"Chef is a powerful automation platform that transforms infrastructure
into code. Whether you're operating in the cloud, on-premises, or in a
hybrid environment, Chef automates how infrastructure is configured,
deployed, and managed across your network, no matter its size \[\...\]\

-   \"The Chef DK workstation is the location where users interact with
    Chef. On the workstation users author and test
    [cookbooks](https://docs.chef.io/cookbooks.html) using tools such as
    [Test Kitchen](https://docs.chef.io/kitchen.html) and interact with
    the Chef server using the [knife](https://docs.chef.io/knife.html)
    and [chef](https://docs.chef.io/ctl_chef.html) command line tools.
-   \"Chef client nodes are the machines that are managed by Chef. The
    Chef client is installed on each node and is used to configure the
    node to its desired state.
-   \"The Chef server acts as [a hub for configuration
    data](https://docs.chef.io/server_components.html). The Chef server
    stores cookbooks, the policies that are applied to nodes, and
    metadata that describes each registered node that is being managed
    by Chef. Nodes use the Chef client to ask the Chef server for
    configuration details, such as recipes, templates, and file
    distributions\".

<div>

\- [Docs.Chef.IO /
Introduction](https://docs.chef.io/chef_overview.html)\
\

 What is a \"Cookbook\" in Chef?
--------------------------------

\
Chef also uses something called **Cookbooks**:\
\
\"A cookbook is the fundamental unit of configuration and policy
distribution. A cookbook defines a scenario and contains everything that
is required to support that scenario:\

-   \"Recipes that specify the resources to use and the order in which
    they are to be applied
-   \"Attribute values
-   \"File distributions
-   \"Templates
-   \"Extensions to Chef, such as custom resources and libraries\"

\"The chef-client uses Ruby as its reference language for creating
cookbooks and defining recipes, with an extended DSL for specific
resources\". - [Docs.Chef.io /
Cookbooks](https://docs.chef.io/cookbooks.html)\
\
All of this can be overwhelming! Let\'s take it slow\...\
\
\

What is a \"Recipe\" in Chef?
-----------------------------

\"[Recipes](https://docs.chef.io/recipes.html): A recipe is the most
fundamental configuration element within the organization. A recipe:\

-   \"Is authored using Ruby, which is a programming language designed
    to read and behave in a predictable manner
-   \"Is mostly a collection of resources, defined using patterns
    (resource names, attribute-value pairs, and actions); helper code is
    added around this using Ruby, when needed
-   \"Must define everything that is required to configure part of a
    system
-   \"Must be stored in a cookbook
-   \"May be included in a recipe
-   \"May use the results of a search query and read the contents of a
    data bag (including an encrypted data bag)
-   \"May have a dependency on one (or more) recipes
-   \"May tag a node to facilitate the creation of arbitrary groupings
-   \"Must be added to a run-list before it can be used by the
    chef-client
-   \"Is always executed in the same order as listed in a run-list\"

\- [Docs.Chef.io / Recipe](https://docs.chef.io/cookbooks.html)\

 
-

How Does Chef Use Ruby? Calling T-Rex Chef!
-------------------------------------------

To demonstrate how Chef calls a Ruby file, a \"recipe\", evaluates the
resources, then uses them, Franklin Webber scales it back a bit.\
\
Let\'s create this T-Rex version of Chef from scratch.\
\
To create a directory called \"cookbooks\", and store a cookbook in an
Apache sub-directory, he uses the command \"chef generate cookbook
cookbooks/apache\". Tests, stored as a Ruby file are automatically
created in *test/recipe/default\_tests.rb* with default recipes in
*recipes/default.rb*.\
\
To create a file, he creates a file, using the Linux command, \"touch\",
to create his chef simulation, \"trex\_chef\": touch trex\_chef.rb\
\
As a text editor, he uses Atom. You can download it
from <https://atom.io/>.\
\
Franklin launches it from his Mac Terminal, the Mac\'s Command Line
Interface, by typing: *atom .*\
\
What does he want to do?\
\
[\# Load the default recipe from the apache
cookbook]{style="font-family: "courier new" , "courier" , monospace;"}\
[\# Display the contents of the recipe
file ]{style="font-family: "courier new" , "courier" , monospace;"}\
\
If the hashtag \"\#\" is by itself, it means that it is a comment. If it
is in, say, **File\#read**, it signifies that it is an instance method.
If it was a class method, it would have a dot such as \".chown\", based
on the Linux command, which allows you to change the owner.\
\

Ruby Class: File
----------------

\
To load a file, you use the standard Ruby core library command
File\#read at <http://rubydoc.info/stdlib/core/File>.\
\

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://1.bp.blogspot.com/-gwUNDGf-9sA/Wk7vbctzMBI/AAAAAAAAMM4/e-Ne5muqIGUEjtVPQKDT_eJz1YFtFxQaQCLcBGAs/s640/class_file.png){width="640" height="283"}](https://1.bp.blogspot.com/-gwUNDGf-9sA/Wk7vbctzMBI/AAAAAAAAMM4/e-Ne5muqIGUEjtVPQKDT_eJz1YFtFxQaQCLcBGAs/s1600/class_file.png)
                                                                                                         [*http://rubydoc.info/stdlib/core/File*](http://rubydoc.info/stdlib/core/File)
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

\
If you look at the docs, you can see that with the File Object you can
see in the Class Method Summary it has methods such as:\
\

-   .chown: Change the ownership of the file
-   .delete: Delete the file
-   .rename 

\
\
This File class inherits many methods from the Ruby class called IO
(Input / Output). That is where we find the \#read method.\
\
For large files, we would stream them. For small files you can do:\
\
**[trex\_chef.rb]{.underline}** *(First Draft)*\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 recipe_file = 'cookbooks/apache/recipes/default.rb'  
   
 unless File.exists?(recipe_file)  
   File.read(recipe_file)  
   puts "Could not find the file #{recipe_file}"  
   exit  
 end  
   
 # Store the contents of the file in a variable recipe_contents  
 recipe_contents = File.read(recipe_file)   
   
 # Print out the file.   
 puts recipe_contents  
```

\
\
The **recipe\_file** default.rb could contain something like:\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 #  
 #  
 # Cookbook Name :: apache  
 # Recipe:: default  
 #  
 # Copyright (c) 2016: The Authors. All rights reserved.  
```

\
What are the contents that should be displayed?\
\
*cat cookbooks/apache/recipes/default.rb*\
\
[\#]{style="font-family: "courier new" , "courier" , monospace;"}\
[\#]{style="font-family: "courier new" , "courier" , monospace;"}\
[\# Cookbook Name ::
apache]{style="font-family: "courier new" , "courier" , monospace;"}\
[\# Recipe::
default]{style="font-family: "courier new" , "courier" , monospace;"}\
[\#]{style="font-family: "courier new" , "courier" , monospace;"}\
[\# Copyright (c) 2016: The Authors. All rights
reserved.]{style="font-family: "courier new" , "courier" , monospace;"}\
\
When he runs it:\
\
*chef exec ruby trex\_chef.rb *\
\
\... It shows\...\
\
[\#]{style="font-family: "courier new" , "courier" , monospace;"}\
[\#]{style="font-family: "courier new" , "courier" , monospace;"}\
[\# Cookbook Name ::
apache]{style="font-family: "courier new" , "courier" , monospace;"}\
[\# Recipe::
default]{style="font-family: "courier new" , "courier" , monospace;"}\
[\#]{style="font-family: "courier new" , "courier" , monospace;"}\
[\# Copyright (c) 2016: The Authors. All rights
reserved.]{style="font-family: "courier new" , "courier" , monospace;"}\
\
\... And the file is displayed correctly! This mean we have run a recipe
file!\
\
Franklin exclaims: \"Look at it! It\'s so quick! \... It doesn\'t do
anything, but it does read the content of the file!\"\
\

Ruby Class: Kernel\#eval
------------------------

The next thing Franklin looks at is Kernal\#eval found
at <http://www.rubydoc.info/stdlib/core/Kernel#eval-instance_method>\
\
We don\'t just want to read a file\... we want to evaluate it. Methods
for Kernel exist such as:\

-   \#exit
-   \#eval
-   \#puts

\
The Kernel module is included in the type Object, therefore since
everything is of type Object, from strings to integers to floating point
numbers, to other objects. This means that these methods are inherited
in everything Ruby. They aren\'t just global methods floating around.
They are attached to the Kernel module.\
\
Let\'s say we replace the \"puts\" method with the \"eval\" method. It
evaluates it the code:\
\
[eval
recipe\_contents]{style="font-family: "courier new" , "courier" , monospace;"}\
\
\... Nothing will display, since it is all comments right now. If it
contained Ruby code, it would be evaluated for correctness, and if it
was incorrect, it would throw an error.\
\

\"Resources\" in Chef
---------------------

\"A resource is a statement of configuration policy that:\

-   \"Describes the desired state for a configuration item
-   \"Declares the steps needed to bring that item to the desired state
-   \"Specifies a resource type---such as package, template, or service
-   \"Lists additional details (also known as resource properties), as
    necessary
-   \"Are grouped into recipes, which describe working configurations\"

\"Where a resource represents a piece of the system (and its desired
state), a provider defines the steps that are needed to bring that piece
of the system from its current state into the desired state\". [-
Docs.Chef.io / Resource](https://docs.chef.io/resource.html)\

<div>

\

</div>

<div>

Franklin imagines the following resource: 

</div>

<div>

\

</div>

<div>

<div>

[file \'hello.txt\'
do]{style="font-family: "courier new" , "courier" , monospace;"}

</div>

<div>

[   content \'Hello,
world!\']{style="font-family: "courier new" , "courier" , monospace;"}

</div>

<div>

[   action
:create]{style="font-family: "courier new" , "courier" , monospace;"}

</div>

<div>

[end]{style="font-family: "courier new" , "courier" , monospace;"}

</div>

</div>

<div>

[\
]{style="font-family: inherit;"}

</div>

<div>

<div>

[The TYPE (file) named NAME (hello.txt) should be ACTION\'d (create)
with PROPERTIES (content \'Hello,
world!\').]{style="font-family: inherit;"}

</div>

<div>

[\
]{style="font-family: inherit;"}

</div>

<div>

[Let\'s say we change the recipe\_file, **default.rb**, and purposely
add an error: ]{style="font-family: inherit;"}

</div>

</div>

<div>

\

</div>

<div>

``` {style="background: rgb(240, 240, 240); border: 1px dashed rgb(204, 204, 204); font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; width: 646.469px;"}
 #  
 #  
 # Cookbook Name :: apache  
 # Recipe:: default  
 #  
 # Copyright (c) 2016: The Authors. All rights reserved.  

 package 'apache' 
```

\
\... Now, when we run the eval statement, there is an error, because the
method \"package\" is *undefined*. That \"package \'apache\'\" is
actually a method, not a key value pair, and is also unhandled by our
trex\_chef.rb code. 

</div>

<div>

\

</div>

<div>

[A Ruby Method with One Parameter]{style="font-family: inherit;"}
-----------------------------------------------------------------

[def
file(name) ]{style="font-family: "courier new" , "courier" , monospace;"}\
[   \# contents of
method]{style="font-family: "courier new" , "courier" , monospace;"}\
[end]{style="font-family: "courier new" , "courier" , monospace;"}\
\
\... The method named \'file\' has a single parameter named \'name\'.\
\
Note: Leaving off the parenthesis is perfectly fine! They do not need to
be there. Japanese Ruby developers usually would write this like:\
\
[def file
name ]{style="font-family: "courier new" , "courier" , monospace;"}\
[   \# contents of
method]{style="font-family: "courier new" , "courier" , monospace;"}\
[end]{style="font-family: "courier new" , "courier" , monospace;"}\
\
\... And it would work. The parenthesis is simply a visual indicator
that heightens readability.\
\
\
So, let\'s go back to what we have already:\
\
**[trex\_chef.rb]{.underline}** *(Second Draft)*\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 recipe_file = 'cookbooks/apache/recipes/default.rb'  
   
 unless File.exists?(recipe_file)  
   File.read(recipe_file)  
   puts "Could not find the file #{recipe_file}"  
   exit  
 end  
   
 recipe_contents = File.read(recipe_file)  
   
 def package  
   puts "Installing the package..."  
 end  
   
 eval recipe_contents  
```

\
\... because we have the method \"package \'apache\'\" \...\
\
\... the error is now: *Wrong number of arguments (1 for 0)
(ArgumentError).*\
\
This is because the package method has zero arguments, and in our file,
it has one argument: \'apache\'.\
\
If we had re-written:\
\
[def
package(name)]{style="font-family: "courier new" , "courier" , monospace;"}\
[   puts \"Installing the package called
\'\#{name}\'\"]{style="font-family: "courier new" , "courier" , monospace;"}\
[end]{style="font-family: "courier new" , "courier" , monospace;"}\
\
\... it would have worked.\
\
Running it again would produce the message:\
\
*Installing the package called \'apache\'*\

<div>

\

</div>

\"Templates\" in Chef
---------------------

\"A cookbook template is an Embedded Ruby (ERB) template that is used to
dynamically generate static text files. Templates may contain Ruby
expressions and statements, and are a great way to manage configuration
files. Use the template resource to add cookbook templates to recipes;
place the corresponding Embedded Ruby (ERB) template file in a
cookbook's /templates directory\". - [Docs.Chef.io /
Templates](https://docs.chef.io/templates.html)\
What other resources does Chef use? Well, Chef also uses templates, such
as\
\
[template \'/var/www/httpd/index.html\'
do ]{style="font-family: "courier new" , "courier" , monospace;"}\
[   source
\'index.html.erb\']{style="font-family: "courier new" , "courier" , monospace;"}\
[end]{style="font-family: "courier new" , "courier" , monospace;"}\
[\
]{style="font-family: "courier new" , "courier" , monospace;"}[service
\'httpd\'
do]{style="font-family: "courier new" , "courier" , monospace;"}\
[   action \[ :start, :enable
\]]{style="font-family: "courier new" , "courier" , monospace;"}\
[end ]{style="font-family: "courier new" , "courier" , monospace;"}\
\
\
Franklin then adds to trex\_chef.rb, changing the \"apache\" parameter
to \"httpd:\
\
Franklin then adds to **trex\_chef.rb**:\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 recipe_file = 'cookbooks/apache/recipes/default.rb'  
   
 unless File.exists?(recipe_file)  
   File.read(recipe_file)  
   puts "Could not find the file #{recipe_file}"  
   exit  
 end  
   
 recipe_contents = File.read(recipe_file)  
   
 def package  
   puts "Installing the package..."  
 end   
   
 def template(name)  
   puts "Creating the template at '#{name}'  
 end  

 eval recipe_contents 
```

\
\

\"Blocks\" in Ruby
------------------

With Resources, remember this?\
\
[file \'hello.txt\'
do]{style="font-family: "courier new" , "courier" , monospace;"}\
[   content \'Hello,
world!\']{style="font-family: "courier new" , "courier" , monospace;"}\
[   action
:create]{style="font-family: "courier new" , "courier" , monospace;"}\
[end]{style="font-family: "courier new" , "courier" , monospace;"}\
\
\"File\" is nothing more than a method, with \'/hello.txt\' just being
the first parameter.\
\
The [do\...
end]{style="font-family: "courier new" , "courier" , monospace;"} is a
block of code, the second parameter being called.\
\
Now, the method called file, defined in Ruby isn\'t special\... any Ruby
Method Always has a Block.\
\
[def file(name,
&block)]{style="font-family: "courier new" , "courier" , monospace;"}\
[   \#contents of
method]{style="font-family: "courier new" , "courier" , monospace;"}\
[end]{style="font-family: "courier new" , "courier" , monospace;"}\
\
\... The
[&]{style="font-family: "courier new" , "courier" , monospace;"} is a
way to grab the block.\
\
Let\'s say our recipe file, default.rb looks like:\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
  #   
  #   
  # Cookbook Name :: apache   
  # Recipe:: default   
  #   
  # Copyright (c) 2016: The Authors. All rights reserved.   
   
 package 'httpd'   
   
 template '/var/www/httpd/index.html' do   
   source 'index.html.erb'  
 end  
   
 service 'httpd' do  
   action [ :start, :enable ]  
 end   
```

\
Now, our **trex\_chef.rb** file can look like\...\

``` {style="background: #f0f0f0; border: 1px dashed #cccccc; color: black; font-family: "arial"; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"}
 recipe_file = 'cookbooks/apache/recipes/default.rb'  
   
 unless File.exists?(recipe_file)  
   File.read(recipe_file)  
   puts "Could not find the file #{recipe_file}"  
   exit  
 end  
   
 recipe_contents = File.read(recipe_file)  
   
 def package(name)  
   puts "Installing the package named '#{name}'"  
 end  
   
 def template(name, &block)  
   puts "Creating the template at '#{name}'  
   block.call #Execute the block  
 end  
   
 def source(name)  
   puts "Using the source file: #{name}"  
 end  
   
 def service(name)  
   puts "Start and enable the service called '#{name}'"  
   yield if block_given?  
 end  
   
 eval recipe_contents  
```

\
\"Yield\" and \"block\_given\" are Ruby keywords.\
\
*\"\[T\]he mechanism of yielding to blocks in Ruby provides the
programmer with a great flexibility. A block is simply a chunk of code,
and yield allows you to \'inject\' that code at some place into a
function. So if you want your function to work in a slightly different
way, you don\'t have to write a new function, instead you can reuse the
one you already have, but give it a different block\". -
[Codeacademy](https://www.codecademy.com/en/forum_questions/51c72e759c4e9d410501df42)*\
\

 GASP! CHOKE! UGH!
------------------

<div>

\

</div>

<div>

I\'m not sure about you, but at this point I started choking during the
webinar and had to come up for air.

</div>

<div>

\

</div>

<div>

I will leave these and other topics Franklin covers for excercises for
the reader.  

</div>

<div>

-   How Passed Blocks Become
    [Procs](http://ruby-doc.org/core-2.0.0/Proc.html): Proc objects
    bound to a local variable.
-   How to require other Ruby libraries [such as
    \"pry\"](https://learn.co/lessons/debugging-with-pry)
-   Using [binding.pry](https://learn.co/lessons/debugging-with-pry)
-   Using block.call
-   [Context vs scope with
    Ruby](https://ruby-hacking-guide.github.io/module.html): Local
    variables
-   Using [RSpec, behavior driven development for
    Ruby](http://rspec.info/), which matches what Chef uses, with
    spec\_helper.rb, and chef\_spec and in\_spec. 
-   Method calls and \"[lazy
    hashes](https://6ftdan.com/allyourdev/2015/11/13/implement-a-lazy-hash-in-ruby/)\"
    such as { :restart =\> true, :reload =\> true }.
-   Arrays and Symbols

</div>

<div>

Main Takeaway: Chef is built right on top of Ruby. It\'s nothing
special. It is just Ruby code.  

</div>

<div>

\

</div>

<div>

\

</div>

How to Learn Ruby?
------------------

<div>

Franklin recommended to learn Ruby:

</div>

<div>

-   Exercism.io, at <http://exercism.io/languages/ruby/about>, currently
    contains 91 problems you can go through to learn Ruby. You can
    upload your answers and share them with people.
-   Rubydoc.info/stdlib: [http://www.rubydoc.info/stdlib](http://www.rubydoc.info/stdlib/) is
    boring but important.
-   [Metaprogramming Ruby
    2](https://pragprog.com/book/ppmetr/metaprogramming-ruby): Fairly
    advanced, but really gets into what Chef uses. 

</div>

Thank you so much Franklin for this webinar!\
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

</div>
