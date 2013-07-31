---
layout: post
title: "Statsd C# Client And Aspect Oriented Programming"
description: "Combine StatD and AOP for a winning monitoring solution"
category: "devops"
tags: [Tools]
---
{% include JB/setup %}

Statsd is a state of the art measurement tool created by [Etsy]. It collects metrics and uses Graphite to visualize them as graphs in unobtrusive way with minimal performance impact. There are some C# clients for Statsd, and all of them take the approach of giving the developer the ability to send metrics via one code line. 

When I started to use Statsd I felt this approach is not enough for me. I needed to wrap a method with something and time its execution and wanted a nice and clean way of doing it without polluting my code with metric lines. 

##Enter AOP

> Aspect Oriented Programming is a programming paradigm that aims to increase modularity by allowing the separation of cross-cutting concerns.

AOP allows the developer to enforce cross cutting concerns, such as logging, monitoring, profiling, authenticating etc in a way that will decorate the code. Attributes are classic AOP implementation in C#, but they also come with a burden - you need to use reflection and check if the method has attributes, and than do something with them.

To the rescue comes [PostSharp] - a leading library in AOP for C#. PostSharp takes the concept of attributes and use it differently. When you use a PostSharp attribute, during the build, the PostSharp engine looks for these attributes and insert them where needed in the IL, so basically you don't need reflection no more - the code from the attribute is injected to the right places and executes in an orderly fashion. This means no penalties during runtime and cleaner code - blessing from heaven!

Few more words about PostSharp: They offer a free edition (called Express) which is good for commercial use.
If you want to use it:

+ download PostSharp from here: [http://www.postsharp.net/download][1]
+ follow the installation instructions
+ go to PostSharp and request a free license: [http://www.postsharp.net/Purchase/Review-Licensee.aspx][2] 
+ register the license in Visual Studio

##Wrapping It All Up
My job was simple - I needed to combine PostSharp abilities with Statsd C# client (I chose [statsd-csharp-client] by Goncalo Pereira). I created 3 attributes: Counter, Timing and Gauge, and that's it.

You can find out more about this project on github [Varshaman] project.

BTW, **Varshaman** is a rain gauge in Hindu mythology.

Happy monitoring.


[Etsy]: http://www.etsy.com/ 
[PostSharp]: http://www.postsharp.net/
[statsd-csharp-client]: https://github.com/goncalopereira/statsd-csharp-client
[Varshaman]: https://github.com/galsegal/Varshaman
[1]: http://www.postsharp.net/download
[2]: http://www.postsharp.net/Purchase/Review-Licensee.aspx
