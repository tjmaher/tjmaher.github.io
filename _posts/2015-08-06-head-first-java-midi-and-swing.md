\-\-- layout: post title: \'Head First Java: Midi and Swing\' date:
\'2015-08-06T20:42:00.002-04:00\' author: T.J. Maher tags: - code
examples - Java - book review modified\_time:
\'2016-04-29T19:57:36.591-04:00\' thumbnail:
https://2.bp.blogspot.com/\--tjiBvQJpSE/VcBCVxjyHFI/AAAAAAAAKwc/oBdARMpOhJg/s72-c/head\_first\_java.jpg
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-5925745056590923985
blogger\_orig\_url:
http://www.tjmaher.com/2015/08/head-first-java-midi-and-swing.html \-\--
Now that I found a job where I get paid to write code, I might as well
try to practice the language, eh?\
\
Over the past few months, in my quest to practice being a developer, I
have been trying to come up with cute little side-projects in Java that
I could do in my free time, and I have been reading more than a few
textbooks to come up with ideas.\
\
[]{#more}\
\
I first heard of \"Head First Java *(2nd Edition, 2005)*\" back in
February when I was interviewing for automated testing positions over at
Harvard University. Although I didn\'t get the position, when the hiring
manager and I exchanged emails afterwards he referred me to two books to
help me brush up on my Java skills, long unused as a manual software
tester. I was referred to: Murach\'s Java Programming ( [Official
Site](https://www.murach.com/shop/murach-s-java-programming-detail))
 and Head First Java ( [Official
Site](http://www.headfirstlabs.com/books/hfjava/) ). After reading a few
sample chapters of each book, I went with \"Head First Java\".\
\

### Head First Java

\
 I have to say, I have never been so amused by a computer programming
textbook! Thank you, Gray, for referring me to it! It talks about how
Java manages memory, about creating multi-threading apps, sockets, user
interfaces with Java\'s Swing library, and making music through Java\'s
MIDI library but it does it in such a hilarious way that it cracks you
up, with stock images from the 1950s, jokes, bad puns, and mock
interviews with the concepts they are talking about.\
\

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://2.bp.blogspot.com/--tjiBvQJpSE/VcBCVxjyHFI/AAAAAAAAKwc/oBdARMpOhJg/s1600/head_first_java.jpg)](http://2.bp.blogspot.com/--tjiBvQJpSE/VcBCVxjyHFI/AAAAAAAAKwc/oBdARMpOhJg/s1600/head_first_java.jpg)
                                                             As found on [Amazon.com](http://www.amazon.com/Head-First-Java-Kathy-Sierra/dp/0596009208/)
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

#### [What caught my eye were the following blurbs in the introduction:]{style="font-weight: normal;"}

> ***\"Who the book is for: ***

> *\"Do you prefer stimulating dinner party conversation to dry, dull,
> academic lectures?\" Head First Java: Intro Who the book is not for:
> \"Are you afraid to try something different? Would you rather have a
> root canal than mix stripes with plaid? Do you believe than a
> technical book can\'t be serious if there\'s a picture of a duck in
> the memory management section?\" - Head First Java: Intro*

> ***\"Who the book is not for:*** 

> *\"Are you afraid to try something different? Would you rather have a
> root canal than mix stripes with plaid? Do you believe than a
> technical book can\'t be serious if there\'s a picture of a duck in
> the memory management section?\" Head First Java: Intro*

It\'s quite a funny book! After spending so much time with very dry
texts studying, I found it to be a refreshing change of pace to get me
back in the swing of things re-learning Java.\
\

::: {.separator style="clear: both; text-align: center;"}
[![](https://2.bp.blogspot.com/-BQzq6WvQN-Y/VcNx5bAHgaI/AAAAAAAAKw4/_D64CJQRfYY/s320/swimmer.png){width="320"
height="244"}](http://2.bp.blogspot.com/-BQzq6WvQN-Y/VcNx5bAHgaI/AAAAAAAAKw4/_D64CJQRfYY/s1600/swimmer.png)
:::

\
\
Warning: They have a lot of cute graphics, like the ones above.\
\

### My Favorite Project: The BeatBox app

My favorite code example of theirs was the ***BeatBox*** application
found in their chapter on *Using Swing*, Java\'s built-in graphical user
interface toolset. I remember getting into developing user interfaces as
a Computer Science major, using Charles Petzold\'s textbook [Programming
Windows](http://www.amazon.com/Programming-Windows%C2%AE-Edition-Developer-%20Reference/dp/157231995X) using
C and Windows 95. When I encountered the Java\'s Swing library in my
Advanced Programming in Java class in grad school, I found it a lot
easier to work with.\
\
With the BeatBox app, they combine the Swing Library with Musical
Instrument Digital Interface (MIDI) library as part of Java\'s Sound
API.\
\

  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://4.bp.blogspot.com/-709KOt4Mdn0/VcP-SGmw6uI/AAAAAAAAKxQ/pl3sXTQ7Kv0/s320/beatbox.png){width="270" height="320"}](http://4.bp.blogspot.com/-709KOt4Mdn0/VcP-SGmw6uI/AAAAAAAAKxQ/pl3sXTQ7Kv0/s1600/beatbox.png)
                                                                                                 My version of the BeatBox app
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

\

#### Sidenote: The Java Sound API:

> *\"The Java Sound API is a low-level API for effecting and controlling
> the input and output of sound media, including both audio and Musical
> Instrument Digital Interface (MIDI) data. The Java Sound API provides
> explicit control over the capabilities normally required for sound
> input and output, in a framework that promotes extensibility and
> flexibility.* 

> *\"The Java Sound API fulfills the needs of a wide range of
> application developers. Potential application areas include:*\
>
> -   *\"Communication frameworks, such as conferencing and telephony*
>
> <!-- -->
>
> -   *\"End-user content delivery systems, such as media players and
>     music using streamed content*
>
> <!-- -->
>
> -   *\"Interactive application programs, such as games and Web sites
>     that use dynamic content*
>
> <!-- -->
>
> -   *\"Content creation and editing*
>
> <!-- -->
>
> -   *\"Tools, toolkits, and utilities*
>
> *\"The Java Sound API provides the lowest level of sound support on
> the Java platform. It provides application programs with a great
> amount of control over sound operations, and it is extensible. For
> example, the Java Sound API supplies mechanisms for installing,
> accessing, and manipulating system resources such as audio mixers,
> MIDI synthesizers, other audio or MIDI devices, file readers and
> writers, and sound format converters. The Java Sound API does not
> include sophisticated sound editors or graphical tools, but it
> provides capabilities upon which such programs can be built. It
> emphasizes low-level control beyond that commonly expected by the end
> user. - [The Java Tutorials:
> Sound](https://docs.oracle.com/javase/tutorial/sound/index.html)*

\

#### Sidenote: About MIDI:

> [[*\"MIDI was originally designed for passing musical events, such as
> key depressions, between electronic keyboard instruments such as
> synthesizers. Hardware devices known as sequencers stored sequences of
> notes that could control a synthesizer, allowing musical performances
> to be recorded and subsequently played back. Later, hardware
> interfaces were developed that connected MIDI instruments to a
> computer\'s serial port, allowing sequencers to be implemented in
> software. More recently, computer sound cards have incorporated
> hardware for MIDI I/O and for synthesizing musical sound. Today, many
> users of MIDI deal only with sound cards, never connecting to external
> MIDI devices. CPUs have become fast enough that synthesizers, too, can
> be implemented in software. A sound card is needed only for audio I/O
> and, in some applications, for communicating with external MIDI
> devices. - [The Java Tutorials: The MIDI
> Package](https://docs.oracle.com/javase/tutorial/sound/overview-MIDI.html)*]{style="font-family: inherit;"}]{style="line-height: 19.2000007629395px;"}

With the chapter in Head First Java: Using Swing, they walk you
through:\
\

-   Setting up a list of sixteen percussion instruments, taken from the
    MIDI Percussion Key Map. 
-   Set up a Sequencer to play the music, playing the sequence chosen by
    the user. It\'s a fast tempo, 120 beats per minute. The tempo can
    raised or lowered by the user. 
-   Set up a GUI with a list of the 16 percussion instruments the user
    can choose from in the far right column. By checking one of sixteen
    checkboxes for that instrument, the user crafts the sequence that
    will be played in a continuous loop. 
-   Listeners are placed on a Start and a Stop button to play and pause
    the beatbox. 

\

<div>

<div>

Even though you can [download the sourcecode from the
book](http://wickedlysmart.com/get-code/), cutting and pasting what you
need, I find it is easier for me to understand the code by manually
typing the code out and experimenting with it. 

</div>

</div>

<div>

\

</div>

### A Few Modifications:

<div>

I made a few changes with the program:\
\
**Adding New Instrument:**\
\
There are a lot more percussion instruments than the sixteen shown in
the example.\
\

::: {.mainbold align="center" style="color: #666666; font-weight: bold;"}
General MIDI Level 1 Percussion Key Map
:::

</div>

On MIDI Channel 10, each MIDI Note number (\"Key\#\") corresponds to a
different drum sound, as shown below. GM-compatible instruments must
have the sounds on the keys shown here. While many current instruments
also have additional sounds above or below the range show here, and may
even have additional \"kits\" with variations of these sounds, only
these sounds are supported by General MIDI Level 1 devices.

**Key\#**

**Drum Sound**

**Key\#**

**Drum Sound**

35

Acoustic Bass Drum

59

Ride Cymbal 2

36

Bass Drum 1

60

Hi Bongo

37

Side Stick

61

Low Bongo

38

Acoustic Snare

62

Mute Hi Conga

39

Hand Clap

63

Open Hi Conga

40

Electric Snare

64

Low Conga

41

Low Floor Tom

65

High Timbale

42

Closed Hi Hat

66

Low Timbale

43

High Floor Tom

67

High Agogo

44

Pedal Hi-Hat

68

Low Agogo

45

Low Tom

69

Cabasa

46

Open Hi-Hat

70

Maracas

47

Low-Mid Tom

71

Short Whistle

48

Hi-Mid Tom

72

Long Whistle

49

Crash Cymbal 1

73

Short Guiro

50

High Tom

74

Long Guiro

51

Ride Cymbal 1

75

Claves

52

Chinese Cymbal

76

Hi Wood Block

53

Ride Bell

77

Low Wood Block

54

Tambourine

78

Mute Cuica

55

Splash Cymbal

79

Open Cuica

56

Cowbell

80

Mute Triangle

57

Crash Cymbal 2

81

Open Triangle

58

Vibraslap

*From <http://www.midi.org/techspecs/gm1sound.php>*\
\

<div>

<div>

\

</div>

<div>

**Placing Instruments into an Enums file: **

</div>

<div>

**\
**I separated out the instrument keys and instruments placing them in an
enums file:

</div>

</div>

<div>

\

</div>

<div>

**[Snippet of Instruments.java]{.underline}**

</div>

\

<div>

\

</div>

<div>

\

</div>

\

<div>

\

</div>

\

<div>

This makes the program flexible to recognize how many instruments are
listed, by using \'Instrument.values().length\'. Adding instruments to
the Instruments enums adds or changes the list of instruments in the app
automatically.\
\
**Add a Listener to the Grid of Checkboxes**\
\
I created a listener for the instrument checkboxes, so the new beat
would play instantly, instead of waiting for the user to press
\'Start\'.\
\
\
\
I am still trying to figure out how to embed the Java app on an HTML
page. Once I figure that out, I can place it here.  

</div>

\

<div>

**View Source Code**

</div>

<div>

\

-   You can view all the  source code at
    <https://github.com/tjmaher/BeatBox>.

<!-- -->

-   You can download the executable JAR file at
    <https://github.com/tjmaher/BeatBox/tree/master/out/artifacts>

</div>

<div>

\

</div>

<div>

\

</div>

<div>

Maybe after a few years of dabbling in little projects like this, I can
become more proficiency in the language!\
\
\
-T.J. Maher\
 Sr. QA Engineer, Fitbit\
* // Manual tester, 15 years*\
* // Automated tester for \[ 4 \] months and counting*\
\
*Please note: \'Adventures in Automation\' is a personal blog about
automated testing. It is not an official blog
of [Fitbit.com](http://www.fitbit.com/). *

</div>
