---
layout: post
title: "Better Searches In LogEntries"
description: "LogEntries has improved search capabilities. Find out how to use it."
category: "devops"
tags: [Tools]
---
{% include JB/setup %}

Just had a great talk with the guys from [LogEntries]. We were talking about some major improvements they are about to make and I wanted to share some thoughts. One thing that came up was the ability to make more complex searches on your logs. 

##LogEntries Search Engine
LogEntries search engine uses Reg-ex to filter the wanted results. It is great and offers some flexibility, but if you want more complex queries, well, you have to dig deeply into proper Reg-ex syntax.
I do many searches and always wanted some more power in my hands to get more accurate results. So if you are a log addict like me, you are gonna love these new Search features in Logentries!

##Some Tips About Logging
Logging is good. Log everything. 

Once you do it you get tons of logs and there are 2 main things a log line should deliver:

+ Be readable (for humans or machines, depends on who or what will read it)
+ Be easy to search

Now, it is a good practice to adopt some patterns across your organization when it comes to logging. Here are mine:
 
+ Give each line a topic that suggests whats it about. Use brackets (like \[some term]\) to make searches more simple. 
+ Use key value pairs inside the log line. You can use JSON objects or just key=value patterns.  
+ Decide which keys are a most on all logs, such as "username", "action", "context", "latency" and so on.
+ Add more data freely but in the same key value format.

For example, consider a log line like this one:


  2013-06-21 09:31:30 [Stock] username=john action=buy stockName=goog sucess=true


This is all fair and square, and it gives me great visibility and search capabilities, but sometimes I need to see 2 searches at the same view.

##Introducing AND OR NOT Filters
Though Regex supports AND OR NOT filters, I couldn't wrap my head around it and make it work easily on LogEntries. Now we can easily use AND, OR, and NOT when searching in Logentries: 
Lets say you want to search for search-term A and B (**Make sure the conditions are capitalized.**):

	[A] AND [B]

A or B

	[A] OR [B]

A and not B

	[A] NOT [B]

BTW, you can use multiple AND OR NOT in the search query.

##Free Text Searches
Many times you need to make partial matches, like free text search. For example, consider a log line like this one:

	2013-06-21 09:31:30 [Stock] username=john action=buy stockName=goog sucess=true

If i would like to search all stock buy actions I can use this:

	[Stock] AND /action=buy

The / stands for partial search. Basically it means you treat each search term as a standalone search and combine it with the conditions.

##Summary
Logging is one of the foundations of good programming. We need to do it well and have a good set of tools to analyze them. This improvement is pretty awesome IMHO and answers a real need in the developer's life.


Happy logging!


[LogEntries]: https://logentries.com    
