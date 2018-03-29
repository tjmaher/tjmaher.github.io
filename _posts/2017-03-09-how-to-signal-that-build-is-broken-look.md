\-\-- layout: post title: \'How to Signal that the Build is Broken? Look
for UFOs!: Notes from the March 7th Lean Coffee, Ministry of
Testing-Boston\' date: \'2017-03-09T08:39:00.001-05:00\' author: T.J.
Maher tags: modified\_time: \'2017-03-09T08:39:17.322-05:00\' thumbnail:
https://1.bp.blogspot.com/-VwsaVcF1CFM/WMFWvlEmydI/AAAAAAAALqM/M7mBktqt7ck9Qfpol2pYazbMdMQhldFnACLcB/s72-c/\_MG\_0364.jpg
blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-7324468936810627755
blogger\_orig\_url:
http://www.tjmaher.com/2017/03/how-to-signal-that-build-is-broken-look.html
\-\-- When developing software, mistakes happen. When multiple
developers are working on the same project, the mistakes of one
developer affects all the others, so it is important that you make sure
your code compiles, that it passes all the unit and integration tests
other developers have set up.\
\
If you check in code and merge it haphazardly into the main branch of
whatever source control system you are using, errors may prevent the
build process that sets the web app to run. Your changes? You \"broke
the build\", temporarily preventing your colleagues from doing any work
on that shared project. This is a minor problem\... unless you merged in
your code just before going home. If that happened, you just prevented
anyone who wanted to work the late shift from getting any work done.\
\
If only there was some type of sign, some type of visual cue that the
build was broken!\
\
Tuesday night, during the [Ministry of Testing - Boston\'s Lean
Coffee](http://www.tjmaher.com/2017/03/devops-and-dynatrace-notes-from-march.html), [Andreas
Grabner](https://www.linkedin.com/in/grabnerandi/), a Technology
Strategist at [Dynatrace](https://www.dynatrace.com/), showed us that
there was.\
\
Imagine: You finally solved the problem you had been working on all day,
merged your code, and packed up for the day. Heading for the exit, you
see this:\
\

  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://1.bp.blogspot.com/-VwsaVcF1CFM/WMFWvlEmydI/AAAAAAAALqM/M7mBktqt7ck9Qfpol2pYazbMdMQhldFnACLcB/s400/_MG_0364.jpg){width="400" height="266"}](https://1.bp.blogspot.com/-VwsaVcF1CFM/WMFWvlEmydI/AAAAAAAALqM/M7mBktqt7ck9Qfpol2pYazbMdMQhldFnACLcB/s1600/_MG_0364.jpg)
                                                                                                                 *\"Look! It\'s a Sign! A Sign that We Are Hosed!\"*
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

\
Turn around. Go back to your desk. Your code broke the build. You need
to go fix it.\
\
This is the **Dynatrace DevOps Pipeline State UFO**.\
\
\

  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://lh3.googleusercontent.com/-TexXNAG3Ras/WMFYn5XSTxI/AAAAAAAALqY/rY5xC0mHntk/s640/blogger-image-1181508878.jpg)](https://lh3.googleusercontent.com/-TexXNAG3Ras/WMFYn5XSTxI/AAAAAAAALqY/rY5xC0mHntk/s640/blogger-image-1181508878.jpg)
                                                                                            *Andreas demonstrates the UFO for Ministry of Testing - Boston*
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

\
\
As Andreas explains it in his March 6, 2017 article, [Using the
Dynatrace DevOps Pipeline State
UFO](https://www.dynatrace.com/blog/using-dynatrace-devops-pipeline-state-ufo/),
\"The Dynatrace DevOps Pipeline State UFO was built out of the necessity
to visualize alerts, problems, health and CI/CD pipeline state within
the Dynatrace R&D organization. It sparked a cultural transformation as
it made code quality that we pushed more frequently through our Delivery
Pipeline more visible\".

<div>

\

<div>

\

</div>

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [![](https://4.bp.blogspot.com/-V73ty3zxGmA/WMFap7Uu8XI/AAAAAAAALqk/Bg9F1kEdM2whUnChtwKaPtBnrYe9PDh7gCLcB/s640/UFO.png){width="451" height="640"}](https://4.bp.blogspot.com/-V73ty3zxGmA/WMFap7Uu8XI/AAAAAAAALqk/Bg9F1kEdM2whUnChtwKaPtBnrYe9PDh7gCLcB/s1600/UFO.png)
                                                                                          *Taken from <https://www.dynatrace.com/blog/using-dynatrace-devops-pipeline-state-ufo/>*
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

<div>

\

</div>

<div>

\

</div>

<div>

You can:

</div>

<div>

-   3D Print Your Own UFO: <https://github.com/Dynatrace/ufo>
-   Pre-order Your Own
    UFO: <https://www.dynatrace.com/solutions/devops/ufo/get/>

\
Thank you, Andreas!\
\
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
