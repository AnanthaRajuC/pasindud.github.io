---
layout: blog
title: Multiplayer Game architectures
category: blog
tags: [dev me]  
summary: Some insight into multiplayer game architecture
image: /images/blog/multiplayer1.jpg
---


When I was building OMI multiplayer game there were less tutorials I could refer to fit my need..

There is a couple of ways you can technically develop a multiplayer game. Please note these are not the 
methods.

*	Centralized on a server
*	Centralized on a player who is the server with Queue System
*	De-centralized on players peer to peer


###Centralized on a server
	
In this scenario the server choreography everything.


![](/images/blog/multiplayer1.jpg " ")


###Centralized on a player who is the server with Queue


In this case you can use a BAAS or your own queuing mechanism. You have player number plus one queues.If you need to broadcast a message to all players like to start a game, the server component will publish that message to all the players queues. When the player recieve the message the acknowledgement can be published to the server queue. 




![](/images/blog/multiplayer2.jpg " ")


*	Server Queue
	*	Subscribers - Server component
	*	Publishers - All Players


*	Player 1 Queue
	*	Subscribers - Player 1
	*	Publishers - Server component    


*	Player 2 Queue
	*	Subscribers - Player 2
	*	Publishers - Server component    


###De-centralized on players peer to peer


Peer to Peer multiplayer game configuration. This more useable in LAN network where you can directly connect over TCP or UDP


![](/images/blog/multiplayer3.jpg " ")



In the next post I will blog about implementing these and examples on defining a protocol.

####To be continue....
