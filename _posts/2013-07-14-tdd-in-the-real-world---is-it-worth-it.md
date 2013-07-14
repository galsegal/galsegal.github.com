---
layout: post
title: "TDD In The Real World - Is It Worth It?"
description: "TDD is a hard standard to adopt by developers and organizations. Why?"
category: "architecture"
tags: [Best Practices]
---
{% include JB/setup %}
TDD has become a standard in the development process in the last few years, but still, when an organization needs to decide if to go this way it may raise some resistance from the developers and product teams. Many people already wrote tons of opinions about it, frameworks were built to support it, yet it is not obvious when comes to taking this decision and enforce it.

I know this is a hard one, because unlike many other development process changes, this one effect the programmer directly and may consume up to 50% of his time writing code, and people don't like changes, especially dramatic one like TDD.

TDD, IMHO, is essential as it is painful. The benefits a developer gets from doing TDD well are enormous. The problem is he still doesn't know that. So why is it so important and how does it effect the developer piece of mind?

First, TDD is a tool, not a target. If used correctly it helps the developer write better code, which is what we should aim for. It forces the developer to use abstractions, keep concerns separated, test his code quickly. fix and refactor. Most of the time this is a big step towards clean and stable code that will give the expected results. 

Second, TDD help the code stability over time. It is like a shield that protects the code from breaking when changes are made. This is highly important when dealing with a quick pace development where things change rapidly.

Third, tests can be ran during build processes. Automation is a real game changer and it relays on set of processes that return 0 or 1 - failure or success. Automation is something that needs to be ran many times and its foundation is a nice code coverage with good unit tests as well as integration tests. The amount of time and effort an organization puts in automation can be in vain if tests are not sufficient. 

It all boils up to the piece of mind the developer gets when all this is done. If done correctly there are no more parts of code no one is willing to change because hell will break loose. Code can be changed and remain safe enough for deployment. Less human QA means less errors and mistakes.

The big issue is how to deal with legacy code. I think it should be dealt like a ticking bomb - carefully and slowly. Starting with the easy parts, separating and refactoring them, and moving to the next piece.

Happy testing! 
