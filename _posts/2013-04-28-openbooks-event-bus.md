---
layout: post
title: "Openbook's Event Bus"
description: ""
category: 
tags: []
---
{% include JB/setup %}
We have just released a new version of our Feed API with some great features.

##Event Bus - WTF?
[Openbook] and its peripheral services obtain data from our database replicas. These are copies of the original databases, and used as read only database. We created them to offload the calls from  the original databases. The problem is that replicas has a delay. Most of the time the delay is not noticeable for humans (5 seconds) but it is a lifetime for machines.
Since Openbook gets all his data from replica database, when something changes in the replica, Openbook needs to know about it.

##What Do We Use?
We use [RabbitMQ] for the queuing engine. It is one of the most simple, resilient and efficient piece of software I ever used. 

###But Why Should You Care?
[Openbook] uses a lot of caching. Caching means you get a result from the database and saves it in memory for later use. Next time it is asked for the same data, Openbook serves it from the cache and not from the database, making the response quicker and offloads calls from the database.
This is a good practice, but it has a pitfall - how much time should the data stay in cache and when to update it. It should stay there for a while to be efficient, but needs to be refreshed when the data is changed.
This is where the event bus comes into play. Each event that passes through the Feed system is now published to other consumers. One of them is the Openbook cache manager. Now Openbook will be able to refresh a user's cache and deliver the latest update immediately.
This should solve a lot of data discrepancies that may occur in Openbook. 


###Who Else Can Use The Event Bus?
Every app that needs to be updated in real time about changes. For instance, the first consumer will be Social Alerts that needs to publish gurus trades. Currently it can be delayed up to 10 minutes, but when using the bus, it will be notified milliseconds after the event hit the replica.
Notification services, badges creation services, statistics and analytics, all can use the event bus without impacting the performance of other applications.

We are excited to deliver this piece of infrastructure. This is a major improvement to our architecture and the possibilities are endless.

##What Else?

###Splunk Logging
We are experimenting [Splunk] - a real time file based monitoring tool that will help us create a unified dashboard for the Feed API. Since NewRelic does not support several of our needs, we will use Splunk to have a full dashboard to monitor our system. If this goes well, it is a major improvement on the way to a full DevOps solution. 


###Full Build Automation
In the background we completed full build automation for the Feed API. Combined with Splunk, we are very close to have a full process of updating and monitoring our apps seamlessly, which is the basis for continuous integration and continuous deployment.


[Openbook]: https://openbook.etoro.com
[RabbitMQ]: http://www.rabbitmq.com/
[Splunk]: http://www.splunk.com/
