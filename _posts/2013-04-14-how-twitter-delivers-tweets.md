---
layout: post
title: "How Twitter Delivers Tweets"
description: ""
category: "DevOps"
tags: [Inspiration]
---
{% include JB/setup %}
Twitter has its ups and downs over the years, but in the last year or so the Fail Whale is not in sight. Judging from several publications, the guys on Twitter changed architecture, used many different tools and created some themselves, which makes it quite interesting to follow.

One of the latest presentations, given by Raffi Krikorian ([@raffi], Director of the Applications Services group at Twitter) at the [QCon] last October, shed some light about Twitter current architecture.

I am investigating for some time several solutions for our own feed system. Of course, we are smaller that Twitter, but we aim high and I would like to create a system that can scale and extend easily. It seems Twitter was able to find a simple solution to a complex problem by separating concerns and keep each component simple. The system is described to be resilient, fault tolerant and easy to scale.

You can see the presentation [here](http://www.infoq.com/presentations/Real-Time-Delivery-Twitter).

[raffi]: https://twitter.com/raffi
[QCon]: http://www.qconferences.com/
