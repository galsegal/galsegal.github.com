---
layout: post
title: "Great Scaling Lessons From Pinterest"
description: ""
category: "DevOps"
tags: [Inspiration]
---
{% include JB/setup %}
[Pinterest] is one of the fastest growing social media website. With a huge user base and constant growing community, the guys at [Pinterest] had their hands full dealing with all the traffic. The exponential grows forced them to constantly improve their architecture and learn several interesting lessons on the way. 

[Marty Weiner] and [Yashwanth Nelapati] gave a take about scaling Pinterest at the [QCon] conference. This is a must see presentation for all developers who deals with scalability issues. 

My 2 cents, after watching it:

- **Simple design wins**. Today we are bombarded with many new technologies and capabilities that often confuse us more than give us good answers. Simple design comes hand in hand with separation of concerns. 
- **Learn new technologies but prefer mature ones with large communities**. This lesson is not pleasant for "cutting edge" developers, but it bears a solid truth. Mature technologies are reliable and predictable. Combined with a large community you will be able to find the best answer for your problem quickly.
- **A single technology will not solve all your problems, but avoid using too many at once**. There is no "magic" code that can do all the things you wish, so pick the ones that give the best solution for a given problem. On the other hand, managing many different technologies require a lot of time learning their bits and bytes. Each technology fails differently and when the hit is on, it is hard to fix something you don't really know.
- **When you scale by just adding more machines, you are on the right path**. This is what horizontal scaling means. If you can combine it with future prediction about growth, you pave your way to success. 

The full presentation can be found [here].


[Pinterest]: http://pinterest.com/
[Marty Weiner]: http://pinterest.com/martaaay/
[Yashwanth Nelapati]:http://www.linkedin.com/in/yashh
[QCon]: http://www.qconferences.com/
[here]: http://www.infoq.com/presentations/Pinterest
