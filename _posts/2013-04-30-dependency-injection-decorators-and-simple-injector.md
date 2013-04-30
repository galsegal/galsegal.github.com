---
layout: post
title: "Dependency Injection, Decorators and Simple Injector"
description: "DI with the decorator pattern and how Simple Injector solves it"
category: "Architecture"
tags: [Infrastructure, Best Practices]
---
{% include JB/setup %}
Using [Dependency Injection] is a common practice that been with us for a long time. It is one of the foundations for [TDD] and [DDD] and helps you manage your code dependencies in one place, as well as use abstractions and not implementation, as suggested in the [DIP] principle of SOLID.

I stared using Microsoft's Unity several years ago, which was fine. Over the years many other DI frameworks got more attention, especially Ninject, which came with many features and abilities.
The DI part of the code is not something you play a lot with - it is there, doing its job and most of the time you just ignore it. Yet, lately I have been investigating this field and wanted to see if there is a better solution. The thing I was looking for was a container that manages decorators well.

##Decorator pattern
The [Decorator pattern] is a hard one for DIs. As declared:
> In object-oriented programming, the decorator pattern is a design pattern that allows behavior to be added to an individual object, either statically or dynamically, without affecting the behavior of other objects from the same class.

The result is one interface that has several implementations. When constructing these instances, you create a nested structure, where each instance is injected with a different implementation of the same interface. Upon execution, each implementation does its thing and calls the injected instance to do is own thing. This pattern works well when you want to add functionality without changing existing code.
For Example, we have this structure:

	public interface IActorDecorator
	{
		void Act();
	}

	public class FirstActorDecorator : IActorDecorator
	{
		private readonly IActorDecorator _actorDecorator;

		public FirstActorDecorator(IActorDecorator actorDecorator)
		{
			_actorDecorator = actorDecorator;
		}

		public void Act()
		{
			//do somthing
			_actorDecorator.Act();
		}
	}

	public class SecondActorDecorator : IActorDecorator
	{
		private readonly IActorDecorator _actorDecorator;

		public SecondActorDecorator(IActorDecorator actorDecorator)
		{
			_actorDecorator = actorDecorator;
		}

		public void Act()
		{
			//do somthing else
			_actorDecorator.Act();
		}
	}

	public class ThirdActorDecorator : IActorDecorator
	{
		public ThirdActorDecorator()
		{
			
		}

		public void Act()
		{
			//do one last thing
		}
	}

When we execute this code, we should get "FirstActorDecorator" and call Act(). It will do something and will call the next decorator, which should be "SecondActorDecorator", which in turn will call "ThirdActorDecorator" and the chain is completed.

##What's The Problem?
There are 2 problems here:

+ How to map 3 implementations to the same interface without each decorator will need to know the specific implementation of the next decorator in the chain>
+ How to chain these decorators in a given order?

Of course, this is a solved problem: Unity has an extension that does that, as well as Ninject and others, but there are other players in this field that caught me attention.

##Enter Simple Injector
[Simple Injector] is the new kid on the block. I heard about him from this [benchmark] and was happy to see its speed. It is fast, really fast compared to other DIs like Ninject. 
> The goal of Simple Injector is to provide .NET application developers with an easy, flexible, and fast dependency injection framework, that uses best practices to steers developers towards the pit of success.

##The Pros
+ Really fast
+ Open source
+ Good documentation
+ Live community
+ Supports decorators
+ Supports batch registration

##The Cons
+ New piece of software that controls a crucial part in the your code execution

#The Verdict
I am all in for Simple Injector. After a bunch of tests, load tests many scenarios I am impressed. The code is small, executes fast and does all it has to do beautifully.

I suggest you go over and try it out!



[Dependency Injection]: http://en.wikipedia.org/wiki/Dependency_injection
[TDD]: http://en.wikipedia.org/wiki/Test-driven_development
[DDD]: http://en.wikipedia.org/wiki/Domain-driven_design
[DIP]: http://en.wikipedia.org/wiki/Dependency_inversion_principle
[Decorator pattern]: http://en.wikipedia.org/wiki/Decorator_pattern
[Simple Injector]: http://simpleinjector.codeplex.com/
[benchmark]: http://www.palmmedia.de/blog/2011/8/30/ioc-container-benchmark-performance-comparison
