\-\-- layout: post title: \'Practicing Ruby Through Exercism! \' date:
\'2018-01-07T09:00:00.000-05:00\' author: T.J. Maher tags: - Ruby
modified\_time: \'2018-01-07T09:00:00.491-05:00\' thumbnail:
https://1.bp.blogspot.com/-hmtH6KWz0TQ/WlEYbm65ylI/AAAAAAAAMNk/1-IjrXhk6R8sSvn2xkads3qzjT\_uLTECACLcBGAs/s72-c/helloworld.png
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-7455952272785212426
blogger\_orig\_url:
http://www.tjmaher.com/2018/01/practicing-ruby-through-exercism.html
\-\--

<div>

I think I have covered Ruby fundamentals enough this past week! I
covered:\
\

-   Franklin Webber\'s webinar [The Ruby Behind
    Chef](http://www.tjmaher.com/2018/01/the-ruby-behind-chef.html),
    which started me off
-   Zed Shaw\'s [Learning Ruby the Hard
    Way](https://learnrubythehardway.org/book/)
-   Gone through [Ruby in Twenty
    Minutes](https://www.ruby-lang.org/en/documentation/quickstart/)
    using IRB
-   Most of Codecademy\'s free [Learning
    Ruby](https://www.codecademy.com/learn/learn-ruby) course
-   Two-thirds of [Programming Ruby: The Pragmatic Programmer\'s
    Guide](http://docs.ruby-doc.com/docs/ProgrammingRuby/) to immerse
    myself in more advanced concepts.

<div>

Now, to put all that knowledge that I think I have to the test! I could
start with [CodeWars](http://codewars.org/) or
[HackerRank](https://www.hackerrank.com/domains/ruby/ruby-tutorials)\...

</div>

<div>

\

</div>

<div>

Instead, I wanted to check out the site Franklin Webber mentioned in his
webinar, **Exercism.io**, an open-source practice area written by a
former [JavaRanch.com](http://javaranch.com/) volunteer. 

</div>

<div>

[]{#more}\

</div>

What is Exercism?
-----------------

<div>

-   Official Site: [http://exercism.io](http://exercism.io/)
-   GitHub site: <https://github.com/exercism/>

</div>

<div>

\

</div>

\"Exercism.io is free and Open Source. The [website
prototype](https://github.com/exercism/exercism.io) is written in Ruby
using the Sinatra web framework. It is licensed under the GNU Affero
General Public License. The [command-line
client](https://github.com/exercism/cli) is written in Go, and
distributed under the MIT license.\
\
\"The exercises in the various languages are also released under the MIT
license. An overwhelmingly large number of people have [contributed to
the
codebase](https://github.com/exercism/exercism.io/graphs/contributors).\
\
\"An even larger number of people have contributed through
participation; by completing exercises and participating in the
discussions about code.\
\

</div>

<div>

\"Creator: Katrina Owen. Katrina is a polyglot developer and Ruby Hero
award winner who accidentally became a developer while pursuing a degree
in molecular biology. She began nitpicking code back in 2006 while
volunteering at JavaRanch, and got hooked. When programming, her focus
is on automation, workflow optimization, and refactoring. She cares
deeply about open source and contributes to several projects outside of
exercism\".\

 Get A GitHub Account
---------------------

\
I was able to sign up with my GitHub account. [Don\'t have one? Get
one](http://github.com/)! Not only is it a great way to show code
samples to future employers, you can also demo your code to other
members of Exercism through GitHub.\
\

How Does It Work? 
------------------

**From [Exercism.io / How It Works /
Newbie](http://exercism.io/how-it-works/newbie):**

</div>

<div>

\
\"Using Exercism requires three tools:\

-   \"Your text editor: Write a solution to an exercise using your
    favorite text editor.
-   \"Your command line interface: Fetch problems and submit solutions
    via the command line (or terminal).
-   \"The [exercism.io](http://exercism.io/) website: Review feedback on
    your solution and discuss it with other learners on the website.

\"For each exercise that you do, you\'ll go through the same basic
steps.\

1.  \"Fetch the exercise using the command line.
2.  \"Write code to solve the exercise on your own computer, satisfying
    each of the tests.
3.  \"Submit your solution using the command line. If you get stuck,
    submit what you have and ask for help. You also get to see other
    people\'s solutions to the same problem, which could help you figure
    it out.
4.  \"Review feedback and look at how other people solved the same
    problem on the website. Ask questions about what seems interesting
    or confusing!
5.  \"Improve your solution and resubmit as many times as desired\".

Getting the Command Line Client
-------------------------------

\
Since I have a Windows 10 Machine at home, the first thing I did was go
to the GitHub site of **Exercism / Windows
Installer** at <https://github.com/exercism/windows-installer/releases> and
install it.\
\
If you are already logged into the site, you can copy and paste the code
to configure Exercism with your API Key,
from <http://exercism.io/how-it-works/newbie>

</div>

\
After installation, you can see if it works by typing in the language
you want to practice, such as in
<http://exercism.io/languages/ruby/about>:\
\
[cd
C:\\Exercism]{style="font-family: "courier new" , "courier" , monospace;"}\
[exercism fetch
ruby]{style="font-family: "courier new" , "courier" , monospace;"}\

<div>

</div>

\

::: {style="-webkit-text-stroke-width: 0px; color: black; font-family: "Times New Roman"; font-size: medium; font-style: normal; font-variant-caps: normal; font-variant-ligatures: normal; font-weight: 400; letter-spacing: normal; orphans: 2; text-align: start; text-decoration-color: initial; text-decoration-style: initial; text-indent: 0px; text-transform: none; white-space: normal; widows: 2; word-spacing: 0px;"}
::: {style="margin: 0px;"}
\... And that starts you with the first problem: Hello World. 
:::
:::

\

Open the Problem in a Text Editor
---------------------------------

You can use [the new Emacs 25.3](http://www.gnu.org/software/emacs/),
[the new Vim 7](http://www.vim.org/), [the brand new Notepad++
7.5.4](https://notepad-plus-plus.org/), [Sublime Text
3](https://www.sublimetext.com/), [RubyMine
2017.3](https://www.jetbrains.com/ruby/), or any other way you can to
input code.\
\
Lately, though, I have been experimenting with
[Atom.io](https://atom.io/), a tool I heard about when I was tinkering
with JavaScript last year.\
\
Going into **C:\\Exercism\\ruby\\hello-world** I found three files:\
\

-   GETTING\_STARTED.md, a [Markdown
    file](https://en.wikipedia.org/wiki/Markdown)
-   hello\_world\_test.rb, a Ruby file
-   README.md

\
After opening them all, I found:\
\

-   README tells you how to install a Ruby library (a \"Ruby Gem\")
    called \"minitest\".
-   GETTING\_STARTED.md talks about how these exercises will touch upon
    Test-Driven Development (TDD). You can get started with a [Ruby TDD
    Tutorial from JumpStart
    Labs](http://tutorials.jumpstartlab.com/topics/testing/intro-to-tdd.html) using
    minitest. It will also walk you through how to create a Hello World
    ruby file.
-   hello\_world\_test.rb presents a working minitest file. 

<div>

After running the test as instructed on my MS-DOS Command Prompt,
hello\_world\_test.rb, it failed, as the instructions told me it would.

</div>

<div>

-   C:\\Exercism\\ruby\\hello-world\>ruby hello\_world\_test.rb

  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://1.bp.blogspot.com/-hmtH6KWz0TQ/WlEYbm65ylI/AAAAAAAAMNk/1-IjrXhk6R8sSvn2xkads3qzjT_uLTECACLcBGAs/s640/helloworld.png){width="640" height="72"}](https://1.bp.blogspot.com/-hmtH6KWz0TQ/WlEYbm65ylI/AAAAAAAAMNk/1-IjrXhk6R8sSvn2xkads3qzjT_uLTECACLcBGAs/s1600/helloworld.png)
                                                                                           *Yes, Ruby will run on a Windows 10 machine. You just [need to install it](https://rubyinstaller.org/).*
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

</div>

<div>

\

</div>

Create a Blank Hello World File
-------------------------------

<div>

\

</div>

<div>

Why did it fail? Because hello\_world.rb does not yet exist! I had not
created it. 

</div>

\
\
\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\
\"You got an error, which is exactly as it should be.\
\"This is the first step in the Test-Driven Development\
(TDD) process.\
\
\"The most important part of the error is\
\
   cannot load such file\
\
\"It\'s looking for a file named hello\_world.rb that doesn\'t\
exist yet.\
\
\"To fix the error, create an empty file named hello\_world.rb\
in the same directory as the hello\_world\_test.rb file.\
\
\"Then run the test again\".\
\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\
\

Add Content To The File
-----------------------

Run the test again, and it is another new error. Why? The
hello\_world.rb file is blank.\
\
Next, you need to start adding to the blank hello\_world file.\
\
You will keep on doing this:\
\

-   Working towards a solution to a new exercise.
-   Running your program. 
-   Finding errors. 
-   Reading the error messages, and figuring out how to interpret them.
-   Fixing errors. 
-   Running your program.
-   Success! Jump to the next exercise.

\
And the test that needs to pass? The MiniTest HelloWorldTest:\
[\
]{style="font-family: "courier new" , "courier" , monospace;"}[class
HelloWorldTest \<
Minitest::Test]{style="font-family: "courier new" , "courier" , monospace;"}\
[  def
test\_say\_hi]{style="font-family: "courier new" , "courier" , monospace;"}\
[    \#
skip]{style="font-family: "courier new" , "courier" , monospace;"}\
[    assert\_equal \"Hello, World!\",
HelloWorld.hello]{style="font-family: "courier new" , "courier" , monospace;"}\
[  end]{style="font-family: "courier new" , "courier" , monospace;"}\
[end]{style="font-family: "courier new" , "courier" , monospace;"}\
\
\
This is a pretty wonderful simulation of how programming in the real
world really works!\
\
My advice? Never cut-and-paste code. Even if you are using someone
else\'s solution, always, always type it out. Run it. See if you can
understand it. Compare the keywords used to the official Ruby
documentation.\
\
You only learn by grappling with a problem and studying a solution.
Cutting-and-pasting will never do you any favors in learning how to
code.\
\
Pssst! They don\'t want you to do \"puts \'Hello, World!\'\" and print
the output to the screen. They want you to:\
\

-   return \'Hello, World!\'

<div>

\... If you are brand new to Ruby, you just might not understand that is
what MiniTest wants.

</div>

\

 Does it Pass? Ship it! 
------------------------

\"When everything is passing, you can submit your code with the
following\
command\":\
\
    \$ exercism submit hello\_world.rb\
\
\... And there were minor complications:\
\

-   Exercism is on C:\\, not C:\\Exercism\\ruby\\hello=world directory.
    It is not a global command (yet)
-   exercism fetch: shows where exactly where hello-world is located,
    i.e. C:\\Exercism\\ruby\\hello-world, so I had to do the
    following\...
-   C:\\Exercism\>exercism submit
    C:\\Exercism\\ruby\\hello-world\\hello\_world.rb 

\
\"Programmers generally spend far more time reading code than writing
it.\
\
\"To benefit the most from this exercise, find 3 or more submissions
that you can learn something from, have questions about, or have
suggestions for.\
\
\"Post your thoughts and questions in the comments, and start a
discussion.\
Consider revising your solution to incorporate what you learn.\
\
\"Yours and others\' solutions to this problem:
<http://exercism.io/tracks/ruby/exercises/hello-world>\"\
\
One problem down. Eighty-nine to go! [Here are all the
exercises](http://exercism.io/languages/ruby/exercises)!\
\
This looks like it is going to be fun!\
\

-   exercism fetch ruby

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
