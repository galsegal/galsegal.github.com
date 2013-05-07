---
layout: post
title: "Feed Update: Improving The Watchlist"
description: "Improving watchlist algorithm"
category: "Feed"
tags: [Infrastructure]
---
{% include JB/setup %}
Short update about the feed: the watchlist (or "My feed" on [Openbook]) is a special type of feed, which is unique for a user, showing all activities (trading and social) of all other users he follows. It is similar in concept the the Twitter feed or Facebook wall. Over the time we saw the watchlist is getting cluttered with many events that are not interesting enough, especially copied trades. The result was the watchlist became less appealing and caused our users to drift away to other parts of Openbook. We got some complaints from our users about this issue and we had to take action.

Now I am happy to announce we did the first improvement in the watchlist algorithm that significantly improves it, by removing all copied trades. Now the watchlist is populated with latest manual trading activities (worth copying) and latest discussions.

The biggest impact IMHO is when copying a single position. When you copy a single position, you can invest more money in it and gain more, while doing it through the "copy trader" mechanism removes the burden of constant checking about new positions, but your money is split into all other positions opened by the guru you copy. Copying a single position gives the user a fine grained control over it, with the chance of gaining more. Having the watchlist shows only manual trades opened by gurus a user finds worth watching can result in better gains.

We already see some users how got it and use check the watchlist more often, so give it a try! 

[Openbook]: https://openbook.etoro.com/