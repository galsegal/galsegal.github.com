---
layout: post
title: ".Net Build Script For Continuous Integration"
description: "extend msbuild for CI pipeline"
category: "DevOps"
tags: [CI, tools]
---
{% include JB/setup %}

Going forward to CD is a blessed improvement in a developer's life. The first step in this process is a the ability to build, test, package the code and send it to the CI orchestration tool (Jenkins, TeamCity etc.). This small repo aims to help in this step.

We are now developing our CI process and as a developer I had to give the CI pipeline the executable that needs to be deployed. As in all CI pipelines, the new code that needs to be shipped should pass some tests before it can be ready for shipping. It basically needs to compile without errors and pass all the unit tests. The final product is a zipped file with the new code.

We wanted to prevent bottlenecks in this process and distribute the load of each task in the pipeline to many people - developers, DBAs, configuration managers and so on. The first task should be done by developers without any dependencies.

My solution was to use MsBuild and set up new targets (other than "Clean","Build","Rebuild") and expose an API that does more - unit test and packaging. I used MsBuild Community Tasks that extends MsBuild tasks out of the box.
I created a build script that exposes 3 new targets:

+ build - build the code
+ test - build and run NUnit for the unit tests
+ package - build, test and zip the relevant code for shipping.

The script is available in my [Github page].

The presentation about our CI process was done by the master mind Alon Becker [@alonbecker]:

<iframe src="http://prezi.com/embed/kinvydtyaj4p/?bgcolor=ffffff&amp;lock_to_path=0&amp;autoplay=0&amp;autohide_ctrls=0&amp;features=undefined&amp;disabled_features=undefined" height="500" frameBorder="0"></iframe>


[Github page]: https://github.com/galsegal/.NET-CI-Build-Script
[@alonbecker]: https://twitter.com/alonbecker
