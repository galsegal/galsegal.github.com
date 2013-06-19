---
layout: post
title: "DDD Boilerplate - A C# Project Template For Visual Studio"
description: "DDD starter project template for Visual Studio"
category: "Architecture"
tags: [tools]
---
{% include JB/setup %}

Creating a DDD solution involves creating many projects for to support DDD structure. This is a tedious job that repeats itself on every new project you create. I noticed most, if not all, projects could use this structure naturally and wanted to speed things up...

I have created a DDD project template for VS2012 that makes all the work.
It includes all the projects and test project needed. There is no code - just the projects and their names. It is just the bare bones needed to get started - no code, no dependencies, just empty projects.

##Where Can I Find It?
The template file can be downloaded from m [Github] repo. Clone the repo and feel free to contriubute.


##How To Use It?
+ The template file called "DDD.zip"
+ Copy the file to "C:\Users\{your name}\Documents\Visual Studio 2012\Templates\ProjectTemplates\Visual C#"
+ Open VS and select "New Project"
+ Under "Visual C# Projects" find "DDD Project Template"
+ Give the solution a name you want and click "OK"
+ You're on!

##Important Note
Make sure you put this project in a folder with a short path like "C:\Projects". 

Since the  namespacing is long, Windows find it hard to create a file with a long path, So don't use it for projects that sits under
"C:\Users\gals\Documents\Visual Studio 2012\Projects\".

Enjoy it and feel free to contribute.
Go DDD!

[Github]: https://github.com/galsegal/ddd-boilerplate