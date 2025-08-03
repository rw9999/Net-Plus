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

- Distance Vector The distance-vector protocols find the best path to a remote network by judging distance. Each time a packet goes through a router, it equals something we call a hop, and the route with the fewest hops to the destination network will be chosen as the best path to it. The vector indicates the direction to the remote network. RIP, RIPv2, and Interior Gateway Routing Protocol (IGRP) are distance-vector routing protocols. These protocols send the entire routing table to all directly connected neighbors.
  
- Link State Using link-state protocols, also called shortest path first protocols, the routers each create three separate tables. One of these tables keeps track of directly attached neighbors, one determines the topology of the entire internetwork, and one is used as the actual routing table. Link-state routers know more about the internetwork than any distance-vector routing protocol. OSPF and IS-IS are IP routing protocols that are completely link state. Link-state protocols send updates containing the state of their own links to all other routers on the network.
  
- Hybrid A hybrid protocol uses aspects of both distance vector and link state, and formerly, EIGRP was the only one you needed to understand to meet the Network+ objectives. But now, BGP is also listed as a hybrid routing protocol because of its capability to work as an EGP and be used in supersized internetworks internally. When deployed in this way, it's called internal BGP, or iBGP, but understand that it's still most commonly utilized as an EGP.

There's no one set way of configuring routing protocols for use in every situation because this really needs to be done on a case-by-case basis.

## Distance-Vector Routing Protocols

The distance-vector routing algorithm passes its complete routing table contents to neighboring routers, which then combine the received routing table entries with their own routing tables to complete and update their individual routing tables.

This is called **routing by rumor** because a router receiving an update from a neighbor router believes the information about remote networks without verifying for itself if the news is actually correct.

It's possible to have a network that has multiple links to the same remote network, and if that's the case, the AD of each received update is checked first.

If the AD is the same, the protocol will then have to use other metrics to determine the best path to use to get to that remote network.

Distance vector uses only hop count to determine the best path to a network. If a router finds more than one link with the same hop count to the same remote network, it will automatically perform what's known as **round-robin load balancing**.

<img width="938" height="371" alt="image" src="https://github.com/user-attachments/assets/4760caa3-805e-47bf-b636-a06b33a23120" />

In the picture, the four routers start off with only their directly connected networks in their routing table. After a distance-vector routing protocol is started on each router, the routing tables are then updated with all route information gathered from neighbor routers.

Each router has only the directly connected networks in its routing table. Also notice that their hop count is zero in every case. Each router sends its complete routing table, which includes the network number, exit interface, and hop count to the network, out to each active interface.

<img width="938" height="371" alt="image" src="https://github.com/user-attachments/assets/85f41f15-ea39-4eaf-b706-c2a8387dc114" />

In this picture, the routing tables are complete because they include information about all the networks in the internetwork. They are considered **converged**.

The hop count for every directly connected network remains zero, but notice that the hop count is incremented by one each time the path completely passes through a router. So, for router 2621A, the path to the 172.16.10.0 network still has a hop count of zero, but the hop count for the path to network 172.16.20.0 is one. The hop count to networks 172.16.30.0 and 172.16.40.0 increases to two, and so on.

Usually, data transmission will cease while routers are converging—a good reason in favor of fast convergence time. In fact, one of the main problems with RIP is its slow convergence time.

As you can see in the second picture, once all the routers have converged, the routing table in each router keeps information about three important things:

- The remote network number

- The interface that the router will use to send packets to reach that particular network

- The hop count, or metric, to the network

Routing convergence time is the time required by protocols to update their forwarding tables after changes have occurred.

#

### Routing Information Protocol ( RIP )

RIP is a true distance-vector routing protocol.

It sends the complete routing table out to all active interfaces every 30 seconds.

RIP uses only one thing to determine the best way to a remote network—the hop count. And because it has a maximum allowable hop count of 15 by default, a hop count of 16 would be deemed unreachable.

This means that although RIP works fairly well in small networks, it's pretty inefficient on large networks with slow WAN links or on networks populated with a large number of routers.

Worse, this dinosaur of a protocol has a bad history of creating routing loops, which were somewhat kept in check by using things like maximum hop count. This is the reason why RIP only permits going through 15 routers before it will judge that route to be invalid.

If all that isn't nasty enough for you, RIP also happens to be glacially slow at converging, which can easily cause latency in your network.

RIP version 1 uses only classful routing, which means that all devices in the network must use the same subnet mask for each specific address class. This is because RIP version 1 doesn't send updates with subnet mask information in tow.

RIP version 2 provides something called prefix routing and does send subnet mask information with the route updates. Doing this is called classless routing.

#

### RIP Version 2 (RIPv2)

RIP version 2 is mostly the same as RIP version 1.

Both RIPv1 and RIPv2 are distance-vector protocols, which means that each router running RIP sends its complete routing tables out to all active interfaces at periodic time intervals.

Also, the timers and loop avoidance schemes are the same in both RIP versions.

Both RIPv1 and RIPv2 are configured with classful addressing (but RIPv2 is considered classless because subnet information is sent with each route update), and both have the same AD (120)

But there are some important differences that make RIPv2 more scalable than RIPv1.

Not advocating using RIP of either version in your network. But because RIP is an open standard, you can use RIP with any brand of router. You can also use OSPF because OSPF is an open standard as well.

<img width="665" height="775" alt="image" src="https://github.com/user-attachments/assets/6d760ce8-8df5-43bb-8139-67c6ab4e4d88" />

RIPv2, unlike RIPv1, is a classless routing protocol (even though it is configured as classful, like RIPv1), which means that it sends subnet mask information along with the route updates. 

By sending the subnet mask information with the updates, RIPv2 can support variable-length subnet masks (VLSMs).

#

### VLSMs and Discontiguous Networks

VLSMs allow classless routing, meaning that the routing protocol sends subnet-mask information with the route updates.

The reason it's good to do this is to save address space.

If we didn't use a routing protocol that supports VLSMs, then every router interface, every node (PC, printer, server, and so on), would have to use the same subnet mask.

As the name suggests, with VLSMs we can have different subnet masks for different router interfaces.

<img width="938" height="474" alt="image" src="https://github.com/user-attachments/assets/d0b2b32d-9c1c-44cc-b3fe-50e4fe302f4d" />

Looking at this figure, you'll notice that we have two routers, each with two LANs and connected together with a WAN serial link.

In a typical classful network design example (RIP or RIPv2 routing protocol), you could subnet a network like this: 

- 192.168.10.0 = Network
- 255.255.255.240 (/28) = Mask

Our subnets would be 0, 16, 32, 48, 64, 80, and so on. This allows us to assign 16 subnets to our internetwork. This allows us to assign 16 subnets to our internetwork.



