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

The IP routing process is actually pretty simple, and it doesn't change, regardless of the size of your network.

![image](https://github.com/user-attachments/assets/36b8df99-b2d9-4268-9605-43e0a55efcfb)

What happens when Host_A wants to communicate with Host_B on a different network?

Suppose that a user on Host_A pings Host_B's IP address. Routing doesn't get any simpler than this, but it still involves a lot of steps. Let's work through them.

- A packet is created on the host:

1. Internet Control Message Protocol (ICMP) creates an echo request payload (which is just the alphabet in the data field).

2. ICMP hands that payload to IP, which then creates a packet. At a minimum, this packet contains an IP source address, an IP destination address, and a Protocol field with 01h. (Remember that Cisco likes to use 0x in front of hex characters, so this could look like 0x01.) All of that tells the receiving host whom it should hand the payload to when the destination is reached. In this example, it's ICMP.
The packet is forwarded:

3. After the packet is created, IP determines whether the destination IP address is on the local network or a remote one.

4. Because IP has discovered that this is a remote request, the packet needs to be sent to the default gateway so the packet can be routed to the correct remote network. The Registry in Windows is parsed to find the configured default gateway.

5. The default gateway of host 172.16.10.2 (Host_A) is configured to 172.16.10.1. For this packet to be sent to the default gateway, the hardware address of the router's interface Ethernet 0 (configured with the IP address of 172.16.10.1) must be known. Why? So the packet can be handed down to the Data Link layer, framed, and sent to the router's interface that's connected to the 172.16.10.0 network. Because hosts only communicate via hardware addresses on the local LAN, it's important to recognize that for Host_A to communicate to Host_B, it has to send packets to the Media Access Control (MAC) address of the default gateway on the local network.

MAC addresses are always local on the LAN and never go through and past a router.

6. The Address Resolution Protocol (ARP) cache of the host is checked to see whether the IP address of the default gateway has already been resolved to a hardware address. If it has, the packet is then free to be handed to the Data Link layer for framing. (The hardware-destination address is also handed down with that packet.) To view the ARP cache on your host, use the following command:

        C:\>arp -a
        Interface: 172.16.10.2 --- 0x3
        Internet Address Physical
        Address Type
        172.16.10.1 00-15-05-06-31-
        b0 dynamic

If the hardware address isn't already in the ARP cache of the host, an ARP broadcast is sent out onto the local network to search for the hardware address of 172.16.10.1. The router responds to that request and provides the hardware address of Ethernet 0, and the host caches this address.

7. After the packet and destination hardware address have been handed to the Data Link layer, the LAN driver is used to provide media access via the type of LAN being used (in this example, it's Ethernet). A frame is then generated, encapsulating the packet with control information. Within that frame are the hardwaredestination and source addresses plus, in this case, an Ether-Type field that describes the Network layer protocol that handed the packet to the Data Link layer—in this instance, IP. At the end of the frame is something called a Frame Check Sequence (FCS) field that houses the result of the cyclic redundancy check (CRC).

![image](https://github.com/user-attachments/assets/08cfb62e-b4b7-4683-93fd-99f923475329)

It contains Host_A's hardware (MAC) address and the hardware-destination address of the default gateway. It does not include the remote host's MAC address—remember that because it's important!

8. When the frame is completed, it's handed down to the Physical layer to be placed onto the physical medium one bit at a time. In this example, the physical medium is twisted-pair wire. The router receives the packet:

9. Every device within the collision domain receives these bits and builds the frame. They each run a CRC and check the answer in the FCS field. If the answers don't match, the frame is discarded. But if the CRC matches, then the hardware-destination address is checked to see if it matches, too (in this example, it's the router's interface, Ethernet 0). If it's a match, then the Ether-Type field is checked to find the protocol used at the Network layer.

10. The packet is pulled from the frame, and what is left of the frame is discarded. The packet is then handed to the protocol listed in the Ether-Type field—it's given to IP.

The router routes the packet:

11. IP receives the packet and checks the IP destination address. Because the packet's destination address doesn't match any of the addresses configured on the receiving router's interfaces, the router will look up the destination IP network address in its routing table.

12. The routing table must have an entry for the network 172.16.20.0 or the packet will be discarded immediately and an ICMP message will be sent back to the originating device with a Destination Unreachable message.

13. If the router does find an entry for the destination network in its table, the packet is switched to the exit interface—in this example, interface Ethernet 1. The following output displays the Lab_A router's routing table. The C means “directly connected.” No routing protocols are needed in this network because all networks (all two of them) are directly connected:

        Lab_A>sh ip route
        Codes:C - connected,S - static,I -
        IGRP,R - RIP,M - mobile,B –
        BGP, D - EIGRP,EX - EIGRP external,O
        - OSPF,IA - OSPF inter
        area, N1 - OSPF NSSA external type
        1, N2 - OSPF NSSA external
        type 2, E1 - OSPF external type 1, E2 -
        OSPF external type 2,
        E – EGP,i - IS-IS, L1 - IS-IS level-1,
        L2 - IS-IS level-2, ia
        - IS-IS intearea * - candidate
        default, U - per-user static
        route, o – ODR P - periodic
        downloaded static route
        Gateway of last resort is not set
        172.16.0.0/24 is subnetted, 2
        subnets
        C 172.16.10.0 is directly
        connected, Ethernet0
        C 172.16.20.0 is directly
        connected, Ethernet1

14. The router packet-switches the packet to the Ethernet 1 buffer.

15. Now that the packet is in the Ethernet 1 buffer, IP needs to know the hardware address of the destination host and first checks the ARP cache. If the hardware address of Host_B has already been resolved and is in the router's ARP cache, then the packet and the hardware address are handed down to the Data Link layer to be framed. Let's take a look at the ARP cache on the Lab_A router by using the show ip arp command:

        Lab_A#sh ip arp
        Protocol Address Age(min) Hardware
        Addr Type Interface
        Internet 172.16.20.1 -
        00d0.58ad.05f4 ARPA Ethernet1
        Internet 172.16.20.2 3
        0030.9492.a5dd ARPA Ethernet1
        Internet 172.16.10.1 -
        0015.0506.31b0 ARPA Ethernet0
        Internet 172.16.10.2 12
        0030.9492.a4ac ARPA Ethernet0

The dash (-) means that this is the physical interface on the router. From this output, we can see that the router knows the 172.16.10.2 (Host_A) and 172.16.20.2 (Host_B) hardware addresses. Cisco routers will keep an entry in the ARP table for four hours. But if the hardware address hasn't already been resolved, the router then sends an ARP request out E1 looking for the hardware address of 172.16.20.2. Host_B responds with its hardware address, and the packet and hardware-destination address are both sent to the Data Link layer for framing.

16. The Data Link layer creates a frame with the destination and source hardware address, Ether-Type field, and FCS field at the end. The frame is handed to the Physical layer to be sent out on the physical medium one bit at a time.

Finally, the remote host receives the packet:

17. Host_B receives the frame and immediately runs a CRC. If the result matches what's in the FCS field, the hardware-destination address is then checked. If the host finds a match, the Ether-Type field is then checked to determine the protocol that the packet should be handed to at the Network layer—IP, in this example.

18. At the Network layer, IP receives the packet and checks the IP destination address. Because there's finally a match made, the Protocol field is checked to find out whom the payload should be given to

19. The payload is handed to ICMP, which understands that this is an echo request. ICMP responds to this by immediately discarding the packet and generating a new payload as an echo reply. The destination host becomes a source host:

20. A packet is created, including the source and destination IP addresses, Protocol field, and payload. The destination device is now Host_A.

21. IP checks to see whether the destination IP address is a device on the local LAN or on a remote network. Because the destination device is on a remote network, the packet needs to be sent to the default gateway.

22. The default gateway IP address is found in the Registry of the Windows device, and the ARP cache is checked to see whether the hardware address has already been resolved from an IP address.

23. After the hardware address of the default gateway is found, the packet and destination hardware addresses are handed down to the Data Link layer for framing.

24. The Data Link layer frames the packet of information and includes the following in the header:

1. The destination and source hardware addresses
2. The Ether-Type field with 0x0800 (IP) in it
3. The FCS field with the CRC result in tow

25. The frame is now handed down to the Physical layer to be sent out over the network medium one bit at a time. Time for the router to route another packet:

26. The router's Ethernet 1 interface receives the bits and builds a frame. The CRC is run, and the FCS field is checked to make sure the answers match.

27. When the CRC is found to be okay, the hardware-destination address is checked. Because the router's interface is a match, the packet is pulled from the frame, and the Ether-Type field is checked to see which protocol at the Network layer the packet should be delivered to.

28. The protocol is determined to be IP, so it gets the packet. IP runs a CRC check on the IP header first and then checks the destination IP address.

IP does not run a complete CRC the way the Data Link layer does—it only checks the header for errors.

Because the IP destination address doesn't match any of the router's interfaces, the routing table is checked to see whether it has a route to 172.16.10.0. If it doesn't have a route over to the destination network, the packet will be discarded immediately. (This is the source point of confusion for a lot of administrators—when a ping fails, most people think the packet never reached the destination host. But as we see here, that's not always the case. All it takes is just one of the remote routers to be lacking a route back to the originating host's network and—poof!—the packet is dropped on the return trip, not on its way to the host.)

Just a quick note to mention that when (if) the packet is lost on the way back to the originating host, you will typically see a Request Timed Out message because it is an unknown error. If the error occurs because of a known issue, such as a route that is not in the routing table on the way to the destination device, you will see a Destination Unreachable message. This should help you determine if the problem occurred on the way to the destination or on the way back.

29. In this case, the router does know how to get to network 172.16.10.0—the exit interface is Ethernet 0—so the packet is switched to interface Ethernet 0.

30. The router checks the ARP cache to determine whether the hardware address for 172.16.10.2 has already been resolved.

31. Because the hardware address to 172.16.10.2 is already cached from the originating trip to Host_B, the hardware address and packet are handed to the Data Link layer.

32. The Data Link layer builds a frame with the destination and source hardware addresses and then puts IP in the Ether-Type field. A CRC is run on the frame, and the result is placed in the FCS field.

33. The frame is then handed to the Physical layer to be sent out onto the local network one bit at a time. The original source host, now the destination host, receives the reply packet:

34. The destination host receives the frame, runs a CRC, checks the hardware destination address, and looks in the Ether-Type field to find out whom to hand the packet to.

35. IP is the designated receiver, and after the packet is handed to IP at the Network layer, IP checks the Protocol field for further direction. IP finds instructions to give the payload to ICMP, and ICMP determines the packet to be an ICMP echo reply.

36. ICMP acknowledges that it has received the reply by sending an exclamation point (!) to the user interface. ICMP then attempts to send four more echo requests to the destination host.

The key point to understand here is that if you had a much larger network, the process would be the same. In a really big internetwork, the packet just goes through more hops before it finds the destination host. 

It's super important to remember that when Host_A sends a packet to Host_B, the destination hardware address used is the default gateway's Ethernet interface. Why? Because frames can't be placed on remote networks—only local networks. So, packets destined for remote networks must go through the default gateway.

Let's take a look at Host_A's ARP cache now by using the arp -a command from the command prompt:

        C:\>arp -a
        Interface: 172.16.10.2 --- 0x3
        Internet Address   Physical Address
        Type
        172.16.10.1        00-15-05-06-31-b0
        dynamic
        172.16.20.1        00-15-05-06-31-b0
        dynamic

Did you notice that the hardware (MAC) address that Host_A uses to get to Host_B is the Lab_A E0 interface?

Hardware addresses are always local, and they never pass a router's interface. Understanding this process is as important to internetworking as breathing air is to you, so carve this into your memory!

#

### Testing Your IP Routing Understanding

![image](https://github.com/user-attachments/assets/e116b81b-541c-4a10-8a1e-0ac75b6a992e)

The critical information you need to glean from this figure is exactly how IP routing will occur in this example. Okay, we'll cheat a bit. I'll give you the answer, but then you should go back over the figure and see if you can answer example 2 without looking at my answers:

1. The destination address of a frame, from HostA, will be the MAC address of the Fa0/0 interface of the RouterA router.

2. The destination address of a packet will be the IP address of the network interface card (NIC) of the HTTP server.

3. The destination port number in the segment header will have a value of 80.

That example was a pretty simple one, and it was also very to the point. One thing to remember is that if multiple hosts are communicating to the server using HTTP, they must all use a different source port number. That is how the server keeps the data separated at the Transport layer.

![image](https://github.com/user-attachments/assets/a8ab0d25-f989-424c-9ea2-3086b4ed352e)

What you want to understand about the IP routing process here is what happens when HostA sends data to the HTTPS server:

1. The destination address of a frame from HostA will be the MAC address of the Fa0/0 interface of the RouterA router.

2. The destination address of a packet will be the IP address of the NIC of the HTTPS server.

3. The destination port number in the segment header will have a value of 443.

Notice that neither switch was used as either a default gateway or another destination. That's because switches have nothing to do with routing. I wonder how many of you chose the switch as the default gateway (destination) MAC address for HostA.

It's very important to remember that the destination MAC address will always be the router's interface—if your packets are destined for outside the LAN, as they were in these last two examples.

#

### Static and Dynamic Routing

How does a router send packets to remote networks when the only way it can send them is by looking at the routing table to find out how to get to the remote networks? 

And what happens when a router receives a packet for a network that isn't listed in the routing table? 

It doesn't send a broadcast looking for the remote network—the router just discards the packet.

There are several ways to configure the routing tables to include all the networks so that packets will be forwarded.

Understand that what's best for one network isn't necessarily what's best for another. Knowing about and being able to recognize the different types of routing will really help you come up with the best solution for your specific environment and business requirements.

Routing convergence is the time required by the routing protocols to update the routing tables (forwarding tables) on all routers in the network.

![image](https://github.com/user-attachments/assets/649c3a24-6d95-442e-a69e-d8ebad9547a4)

You can see that we can configure a router with either static or dynamic routing. 

If we choose static routing, then we have to go to each router and type in each network and the path that IP will use to send packets. 

However, static routing does not scale well in large networks, but dynamic routing does because network routes are automatically added to the routing table via the routing protocol.

Dynamic routing protocols break up into many different categories or types of protocols.

![image](https://github.com/user-attachments/assets/7d6b83f0-6e4c-45d9-b464-3053ab4a8d51)

An **autonomous system** is a collection of networks or subnets that are in the same administrative domain.

This is another way of saying an administrative domain is within your company's network, and you control or administer all the subnets that are within it.

You control and set the policy for what happens in the network or autonomous system.

You can now see that an IGP operates and routes within an AS and an EGP works outside or between more than one AS.

The most popular protocol for an EGP is Border Gateway Protocol (BGP), which is typically used by ISPs or really large corporations. As an administrator of a small to medium network, you'll probably never use BGP.

Let's talk about all the great things that dynamic routing protocols do for us.

We won't have to go to every single router and define for it, with a static route, what and where every destination network is. Thankfully, we have routing protocols that do much of the work for us.

We still have to know what the routing protocols are going to do and how they will do it, but the protocols will take care of most of the updating and sending information to each other.

That is the end of the EGP branch of the tree, but the IGP branch continues to split out as we go down further.

![image](https://github.com/user-attachments/assets/64bb8f1c-f791-42ad-825e-bceab459350f)

With the IGP split, you can see that there are two primary categories: distance-vector (DV) and link-state (LS) routing protocols.

In the distance-vector category, for example, we have RIP and Interior Gateway Routing Protocol (IGRP).

Under the link-state category are the nonproprietary OSPF and Intermediate System-to-Intermediate System (IS-IS) that were designed to work in larger internetworks.

![image](https://github.com/user-attachments/assets/6a88b53c-a9d0-40c4-ab29-7139c2c71790)

You can see from the diagram that there is a third category: the hybrid protocol category.

The only protocols under this category are EIGRP and BGP. EIGRP is Cisco proprietary (or used to be, but people mostly just run this with Cisco gear) and uses the features of both DV and LS.
