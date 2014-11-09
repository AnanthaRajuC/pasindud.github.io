---
layout: blog
title: Scaling USSD Application
category: blog
tags: [php ,ideamart]  
summary: How I scaled php ussd applications
image: /images/blog/ScalingUSSD.png
---

Manning high traffic USSD applications is a tricky business because they should maintain a session for each user, other than SMS where there is no need to remember a state. Making it more hard is that each USSD request has a session timeout of avg 1s.

Most of the time is network traffic and fetching users state and responding to the new input.

###PHP USSD Application Scaling

![](/images/blog/ScalingUSSD.png " ")

*	LB - load balancer without sticky sessions.

*	PHP Application - Are the PHP application servers.

*	Memcache - quick access memory to retrieve session information.

*	MySQL Master -  Is write biased it help to keep a record about users activities which can be analysed later.


*	MySQL Slave - Is DB is read biased and feeds the dashboard where we track many variables like number of action's per second, unique number of users etc.


