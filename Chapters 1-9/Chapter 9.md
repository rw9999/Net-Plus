# Introduction to IP Routing

IP routing is the process of moving packets from one network to another network using routers.

A **routing protocol** is a tool used by routers to dynamically find all the networks in the internetwork as well as to ensure that all routers have the same routing table. Basically, a routing protocol determines the path of a packet through an internetwork. 

Examples of routing protocols are Routing Information Protocol (RIP), Routing Information Protocol version 2 (RIPv2), Enhanced Interior Gateway Routing Protocol (EIGRP), Open Shortest Path First (OSPF), and Border Gateway Protocol (BGP).

Once all routers know about all networks, a **routed protocol** can be used to send user data (packets) through the established internetwork. 

Routed protocols are assigned to an interface and determine the method of packet delivery. Examples of routed protocols are Internet Protocol (IP) and Internet Protocol version 6 (IPv6).

#

### Routing Basics

Once you create an internetwork by connecting your wide area networks (WANs) and local area networks (LANs) to a router, you need to configure logical network addresses, such as IP addresses, to all hosts on the internetwork so that they can communicate via routers across that internetwork.

In IT, routing essentially refers to the process of taking a packet from one device and sending it through the network to another device on a different network.

Routers don't really care about hosts—they care only about networks and the best path to each network.

The logical network address of the destination host is used to get packets to a network through a routed network, and then the hardware address of the host is used to deliver the packet from a router to the correct destination host.

If your network has no routers, then it should be apparent that, well, you are not routing. But if you do have them, they're there to route traffic to all the networks in your internetwork. 

To be capable of routing packets, a router must know at least the following information:

- Destination network address
- Neighbor routers from which it can learn about remote networks
- Possible routes to all remote networks
- The best route to each remote network
- How to maintain and verify routing information

The router learns about remote networks from neighbor routers or from an administrator.

The router then builds a **routing table** (a map of the internetwork) that describes how to find the remote networks. If a network is directly connected, then the router already knows how to get to it.

If a network isn't directly connected to the router, the router must use one of two ways to learn how to get to it.

One way is called **static routing**, which can be a ton of work because it requires someone to type all network locations into the routing table.

In **dynamic routing**, a protocol on one router communicates with the same protocol running on neighbor routers.

The routers then update each other about all the networks they know about and place this information into the routing table.

If a change occurs in the network, the dynamic routing protocols automatically inform all routers about the event. If static routing is used, the administrator is responsible for updating all changes by hand into all routers.

Understandably, in a large network, it's common to find that a combination of both dynamic and static routing is being used.

![image](https://github.com/user-attachments/assets/393eef92-0087-43ae-95a3-6ea7bc3535f5)

Let's take a look at a simple example that demonstrates how a router uses the routing table to route packets out of an interface.

Lab_A has one serial interface and three LAN interfaces.

Can you figure out which interface Lab_A will use to forward an IP datagram to a host with an IP address of 10.10.10.10?

By using the Cisco IOS command "show ip route", we can see the routing table (map of the internetwork) that router Lab_A will use to make all forwarding decisions:

    Router_A#show ip route
    [output cut]
    Gateway of last resort is not set
    C 10.10.10.0/24 is directly connected,
    FastEthernet0/0
    C 10.10.20.0/24 is directly connected,
    FastEthernet0/1
    C 10.10.30.0/24 is directly connected,
    FastEthernet0/2
    C 10.10.40.0/24 is directly connected,
    Serial 0/0

The C in the routing table output means that the networks listed are “directly connected,” and until we add a routing protocol—something like RIP, EIGRP, and so on—to the routers in our internetwork, or use static routes, we'll have only directly connected networks in our routing table.

By looking at the figure and the output of the routing table, can you tell what Lab_A will do with a received packet that has a destination IP address of 10.10.10.10? If you answered, “The router will packet-switch the packet to interface FastEthernet 0/0, and this interface will then frame the packet and send it out on the network segment,” you're right.

Just because we can, let's look at a different example. Based on the output of the next routing table, which interface will a packet with a destination address of 10.10.10.14 be forwarded to?

    Router_A#sh ip route
    [output cut]
    Gateway of last resort is not set
    C 10.10.10.16/28 is directly connected,
    FastEthernet0/0
    C 10.10.10.8/29 is directly connected,
    FastEthernet0/1
    C 10.10.10.4/30 is directly connected,
    FastEthernet0/2
    C 10.10.10.0/30 is directly connected,
    Serial 0/0

First, you can see that the network is subnetted and that each interface has a different mask.

Here's the answer: 10.10.10.14 would be a host in the 10.10.10.8/29 subnet connected to the FastEthernet 0/1 interface.

When the routing tables of all routers in the network are complete (because they include information about all the networks in the internetwork), they are considered **converged**, or in a steady state.

## The IP Routing Process

