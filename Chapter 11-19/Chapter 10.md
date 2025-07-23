# Routing Protocols

Routing protocols are critical to a network's design.

Dynamic routing protocols run only on routers that use them in order to discover networks and update their routing tables.

Using dynamic routing is easier on you, the system administrator, than using the labor-intensive, manually achieved static routing method, but it'll cost you in terms of router CPU processes and bandwidth on the network links.

The source of the increased bandwidth usage and CPU cycles is the operation of the dynamic routing protocol itself.

A router running a dynamic routing protocol shares routing information with its neighboring routers, and it requires additional CPU cycles and additional bandwidth to accomplish that.

## Routing Protocol Basics

Two types of routing protocols are used in internetworks: interior gateway protocols (IGPs) and exterior gateway protocols (EGPs).

IGPs are used to exchange routing information with routers in the same **autonomous system (AS)**.

An AS is a collection of networks under a common administrative domain, which simply means that all routers sharing the same routing table information are in the same AS.

EGPs are used to communicate between multiple ASs. A nice example of an EGP would be Border Gateway Protocol (BGP).

![image](https://github.com/user-attachments/assets/40b81eb6-e391-4b47-822c-04aa2db107d2)

#

### Administrative Distances

The administrative distance (AD) is used to rate the trustworthiness of routing information received on one router from its neighboring router.

An AD is represented as an integer from 0 to 255, where 0 equals the most trusted route and 255 the least.

A value of 255 essentially means, “No traffic is allowed to be passed via this route.”

If a router receives two updates listing the same remote network, the first thing the router checks is the AD. If one of the advertised routes has a lower AD than the other, the route with the lower AD is the one that will get placed in the routing table.

If both advertised routes to the same network have the same AD, then routing protocol metrics like **hop count** or the amount of bandwidth on the lines will be used to find the best path to the remote network

And as it was with the AD, the advertised route with the lowest metric will be placed in the routing table. 

But if both advertised routes have the same AD as well as the same metrics, then the routing protocol will **load-balance** to the remote network. To perform load balancing, a router will send packets down each link to test for the best one.

![image](https://github.com/user-attachments/assets/2d80c933-ada5-4f0c-a0c1-bad1cdee9fbc)

![image](https://github.com/user-attachments/assets/1e434bc8-60fc-42a8-af54-d74aad8877e6)

Understand that if a network is directly connected, the router will always use the interface connected to that network.

Also good to know is that if you configure a static route, the router will believe that route to be the preferred one over any other routes it learns about dynamically.

You can change the ADs of static routes, but by default, they have an AD of 1. That's only one place above zero, so you can see why a static route's default AD will always be considered the best by the router.

This means that if you have a static route, a RIP-advertised route, and an EIGRP-advertised route listing the same network, then by default, the router will always use the static route unless you change the AD of the static route.

#

### Classes of Routing Protocols

The three classes of routing protocols:

- Distance Vector The distance-vector protocols find the best path to a remote network by judging—you guessed it—distance. Each time a packet goes through a router, it equals something we call a hop, and the route with the fewest hops to the destination network will be chosen as the best path to it. The vector indicates the direction to the remote network. RIP, RIPv2, and Interior Gateway Routing Protocol (IGRP) are distance-vector routing protocols. These protocols send the entire routing table to all directly connected neighbors.
  
- Link State Using link-state protocols, also called shortest path first protocols, the routers each create three separate tables. One of these tables keeps track of directly attached neighbors, one determines the topology of the entire internetwork, and one is used as the actual routing table. Link-state routers know more about the internetwork than any distance-vector routing protocol. OSPF and IS-IS are IP routing protocols that are completely link state. Link-state protocols send updates containing the state of their own links to all other routers on the network.
  
- Hybrid A hybrid protocol uses aspects of both distance vector and link state, and formerly, EIGRP was the only one you needed to understand to meet the Network+ objectives. But now, BGP is also listed as a hybrid routing protocol because of its capability to work as an EGP and be used in supersized internetworks internally. When deployed in this way, it's called internal BGP, or iBGP, but understand that it's still most commonly utilized as an EGP.

There's no one set way of configuring routing protocols for use in every situation because this really needs to be done on a case-by-case basis.

## Distance-Vector Routing Protocols

