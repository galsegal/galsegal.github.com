---
layout: post
title: "Making Our Feed Better (Preview)"
description: "a series of posts about developing our new feed infrastructire"
category: "Feed"
tags: [Infrastructure, Preview]
---
{% include JB/setup %}
Our feed is a major, if not the major component on [Openbook]. We use it to show users' trading activities, discussions and badges. It is the most engaging component and have a crucial role in our community. Over the years we added several features to the feed and got great feedback along with many feature requests and complaints.
Our focus was on developing other parts of the website and smooth the entrance of new users to our community. All these adjustments were based on the existing feed, but the feed itself was neglected in some ways. In the past few months, due to the growth of our community, the flaws of the feed started to surface and we decided to it is time for some radical change - we need a new infrastructure for our news feed.

We got several requirements from our product department. These requirements were focused on adding new features to the feed, and most important - making it more interesting. We, as the development group, had our list of requirements for the new infrastructure as well. We started working on it 2 months ago and currently our new infrastructure is serving the trading feed on [Openbook].

I must say this is an exciting journey. I was the first server-side programmer of [Openbook] 3.5 years ago. We were a small team and the website itself was minimal. Over the years we gained more users, our community started to grow, as well as the team. I became the team leader and we recruited more talented people, becoming the largest development team on [eToro]. In the past few months we experienced difficulties in managing such a big team and decided to split it to 2 teams: one for managing the front end and be more features-focused, and the other one serves as an infrastructure-focused team. I left my role as team leader and created a new team devoted for building a high performance, easy to scale, easy to extend infrastructure.

We are a small team of 2 (maybe 3 in the near future - we are recruiting!!) programmers: Victor as the software architect, and myself as the team leader and are 100% hands on. This is a great change for me - in the last few years I started to drift away from coding to managing, and I missed it a lot. I must say the last few months were exciting and challenging. I am happy to be back!

##Brief History - How Did Our Feed Used To Work
Since we started small, we needed something to serve our feed. We didn't want to invest the time in building it, and we looked for a provider that can help us. My found [Kickapps] (now PerfectSense) and created a background process that publishes out users' trading activities to Kickapps servers. [Openbook] server called the Kickapps server and got the feed and show it to our users.

At the begging all worked well - the feed was shown quickly and nicely and we could move on with developing other parts of the website. Kickapps had its pitfalls, but overall they were a solid provider, quickly responded to failures and the entire process was pretty smooth.

##Things Gets Sour...

We wanted other feed items to be available (like discussions and comments) and at that time Kickapps did not support these action. We needed to develop it by ourselves, and now our server used 2 different sources when creating the feed. After 2 years we added the badges, and again the server called 3 providers to create the feed. As our community grew, we saw that Openbook struggles with this task.

Another problem started to emerge when the community started to grow, and especially when the "Copy Trader" caught more action. Suddenly one trade made by one of our gurus created another 4000 copied trades in the same time. Publishing all this data to Kickapps took time and as a result the feed was not rapidly updated. If you take in mind that trading activities are almost 95% of all feed items combined, this meant trouble.

Moreover, around 45%-50% of all [Openbook] requests are dealing with feeds, we understood that improving the feed will have a crucial effect on the entire system. 

##Time For a Change

As developers we saw these problems growing and we didn't like it. Combining the growth of the copied trades along with the exponential growth of or community told us this thing is going to blow in our face. We pushed toward a change in the way we publish our feed and finally we made the time to do it. This is where my new team comes in play and it was truly exciting.

The first change we needed to do is start producing and consuming the feed internally. We needed to stop working with Kickapps and do it ourselves. I must say II looked forward for this task - this is a major challenge to create this kind on infrastructure - one with great impact on our users.

##DevOps

Another key point about the way we work is implementing DevOps methods. For those of you who haven't heard about DevOps, here is a short summary:
>DevOps (a portmanteau of development and operations) is a software development method that stresses communication, collaboration and integration between software developers and information technology (IT) professionals.[1] DevOps is a response to the interdependence of software development and IT operations. It aims to help an organization rapidly produce software products and services.

Practically speaking, we are responsible for every aspect of the product we ship. We design it, develop it, do our own QA, implement automatic deployment processes and have a full control over the entire process of dev-QA-deploy-measure. This is a methodology we started to embrace at [eToro] in the past few weeks and it has a huge effect on the way we develop things. As developers and control freaks we love DevOps. We have more freedom and responsibility and it keeps us very close to our product at all its phases.

##The Numbers
So, the first phase is already in production. All [Openbook] trading feed is coming from our servers. Lets talk numbers and see what is all about:

At a given day

- we insert about 280,000 new trading items
- we are able to publish about 4500 new feed items in 1 minutes (and we can do much better here)
- we get about 4,552,000 requests to show different feeds
- we get approx. 50,000 requests per minute in rush time.
- our servers response time is stable between 1.25-3 ms per request.
- the slowest response time we see is 7.5 ms.


Since we deployed the new infrastructure we saw a major improvement on the [Openbook] servers

- feed requests are around 45%-50% of all [Openbook traffic]
- [Openbook] servers response time was improved dramatically - from 300 ms to a steady 90 ms.
- it means [Openbook] has now more resources to allocate for other requests and serves them more quickly.

Here are some graphs taken from our NewRelic dashboard:

Calls [Openbook] used to make to Kickapps and the response time (before):

![kickapps response time][kickapps-repsonse]

Calls [Openbook] makes to the new feed and the response time (after):

![new feed infrastructure response time][feed-response]

Immediate improvement of [Openbook] servers once the new feed infrastructure was deployed:

![Openbook during deployment][openbook-perf-before]

Current [Openbook] servers response time, after all users started to consume the new feed:

![Openbook after deployment][openbook-perf-after]

##What's Next?
We have many things on our plate: 

- we need to move the discussions and the comments to the new feed infrastructure
- we want to add better algorithms to improve the feed content and make it more interesting
- we want to add abilities to share images/videos

There are so many things we can do to make our feed better and I will cover all changes in future posts.

I will also add more details about our development methodology and concepts for the techy people.


[Openbook]: https://openbook.etoro.com
[eToro]: http://etoro.com
[Kickapps]: http://www.perfectsensedigital.com/products/
[kickapps-repsonse]: /assets/images/kickapps-repsonse.png
[feed-response]: /assets/images/feed-response.png
[openbook-perf-before]: /assets/images/openbook-perf-before.png
[openbook-perf-after]: /assets/images/openbook-perf-after.png

