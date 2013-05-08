---
layout: post
title: "LogEntries Tips And Tricks"
description: "Tips and tricks when working with LogEntries"
category: 
tags: [Best Practices, Logging]
---
{% include JB/setup %}
[LogEntries] is an online logging dashboard. It allows you to collect your logs and view them online, search them, collect events and more. Here are some tips and tricks for better usage: 

##Arrange Your Logs
LogEntries allows you to query your logs via a Regex engine. In order for you to group events and ease the search, find a way to help this engine do its work. I found it is best to write some context on every line of log. For example, if you have several "topics" you want to track, write the topic name in the begging of the log line:

    2013-05-01 03:43:39 {SomeTopic} some logging text 
It is also a good practice to wrap your topic with an exclusive identifier. I choose brackets or curly braces since I don't use them in my logged text. 

##Added Tagging
In the LogEntries dashboard, go to your log screen and click the "Tagging" tab. Create a new tag, give it a name and event name and use the topic as your search pattern, i.e. {SomeTopic}. Go back to the Entries tab and wait for new logs to arrive. LogEntries will not tag your previous log lines, only the ones after the tag was created.

##Add Events
If you linked your tag to an event, you will see a counter at the top of the screen showing the number of times this event showed up in a given time frame. If you want a fine grained counters, you can create a custom event and link it to the tag you created. Use the "Event" button on the left pane to do that. Using custom event can be beneficial for graphs, more of it later.

Some word about events: if you are going to use them a lot, as I do, make sure you create some naming convention that will help you manage them easily. I use "appName-eventName" to distinguish events for different apps, since events are globally available.

##Add Alerts
If you want to be notified when an event happens, you can do it in the "Alerts" tab. Link an event or search pattern and set it up (pretty self explanatory).

##Add Graphs
This is a cool feature that allows you to get quick overview about events in your system. Doing it is pretty easy via the "Graphs" tab but take into consideration it works only with events, not search patters. If you linked a search pattern to an event, you are good to go. 

##Summary
LogEntries is great if you need you your logs to be available online. Tough the search engine is pretty basic but is efficient for most use cases. Alerts and graphs also have their benefits. 

Need for capabilities? let me know. 

[LogEntries]: https://logentries.com/
