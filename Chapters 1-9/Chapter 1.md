# Chapter 1

#### What is a network?

A network is "a group or system of interconnected peple or things"

A computer network means two or more connected computers that can share resources such as data and applications, office machines, an internet connection, or combination of these.

![image](https://github.com/user-attachments/assets/042319d0-fbc9-4af9-98f1-5b99e1432b92)

The figure above shoesd a basic network made up of only two hosts comptuters connected; they share resources such as files and even a printer hooked up to one of the hosts. These two hosts "talk" to eaach other using a computer language called **binary code**, which consists of 1s and 0s in a specific order that describes exaacly what they want to "say".

### The Local Area Network

A local area network **(LAN)** is usually retricted to spanning a particular geographoc location such as an office building, a single department within a corporate office, or even a home office.

Back in the day, you couldn't put more than 30 workstations with strict limitations on distance. Because of technological advances, we're not nearly as restricted in regard to both a LAN's size and the distance a LAN can span.

It's still best to split a big LAN into smaller logical zones known as **workgroups** to make administration.

The meaning of the term **workgroup** in this context is slightly different than when the term is used in contrast to domains. 

In that context, a workgroup is a set of devices with no security association with one another (whereas in a domain they do have that association).

In this context, we simply mean they physically are in the same network segment.

In a typical business environment, it's a good idea to arrange your LAN's workgroups along department divisions; for instance, you would create a workgroup for Accounting, another one for Sales, and maybe another for Marketing, etc.

![image](https://github.com/user-attachments/assets/579b5b13-66b8-49fc-857d-d7de0539a13b)

Notice that there's a Marketing workgroup and a Sales workgroup. These are LANs in their most basic form. Any device that connects to the Marketing LAN can access the resources of the Marketing LAN—in this case, the servers and printer.

There are two problems with this:

 - You must be physically connected to a workgroup's LAN to get the resources from it.
  
 - You can't get from one LAN to the other LAN and use the server data and printing resources remotely.

This is a typical network issue that's easily resolved by using a cool device called a **router** to connect the two LANs. 

![image](https://github.com/user-attachments/assets/1a23336a-bd81-4089-8273-8a7f2401c729)

Even though you can use routers for more than just connecting LANs, the router shown is a great solution because the host computers from the Sales LAN can get to the resources (server data and printers) of the Marketing LAN, and vice versa.

Now, you might be thinking that we really don't need the router—that we could just physically connect the two workgroups with a type of cable that would allow the Marketing and Sales workgroups to hook up somehow. Well, we could do that, but if we did, we would have only one big, cumbersome workgroup instead of separate workgroups for Marketing and Sales, and that kind of arrangement just isn't practical for today's networks.

This is because with smaller, individual-yet-connected groups, the users on each LAN enjoy much faster response times when accessing resources, and administrative tasks are a lot easier too. Larger workgroups run more slowly because there's a legion of hosts within them that are all trying to get to the same resources simultaneously.

### Common Network Components

There are a lot of different machines, devices, and media that make up our networks. Let's talk about three of the most common:

- Workstations
- Servers
- Hosts

### Workstations

Workstations are often seriously powerful computers that run more than one central processing unit (CPU) and whose resources are available to other users on the network to access when needed.

People often use the terms workstation and client interchangeably.

But technically speaking, they are different.

A **client machine** is any device on the network that can ask for access to resources like a printer or other hosts from a server or powerful workstation.

The term **host** is used to describe pretty much anything that takes an IP address.

### Servers

Servers are also powerful computers. They get their name because they truly are “at the service” of the network and run specialized software known as the network operating system to maintain and control the network.

In a good design that optimizes the network's performance, servers are highly specialized and are there to handle one important labor-intensive job. This is not to say that a single server can't do many jobs, but more often than not, you'll get better performance if you dedicate a server to a single task.

Not always, though—sometimes they have more than one job. But whether servers are designated for one job or are network multitaskers, they can maintain the network's data integrity by backing up the network's software and providing redundant hardware (for fault tolerance). And no matter what, they all serve a number of client machines.

I want to make sure you know that servers must have considerably superior CPUs, hard-drive space, and memory—a lot more than a simple client's capacity—because they serve many client machines and provide any resources they require. Because they're so important, you should always put your servers in a very secure area. My company's servers are in a locked server room because not only are they really pricey workhorses, they also store huge amounts of important and sensitive company data, so they need to be kept safe from any unauthorized access.

### Hosts

This can be kind of confusing because when people refer to hosts, they really can be referring to almost any type of networking devices—including workstations and servers.

You'll find that usually this term comes up when people are talking about resources and jobs that have to do with Transmission Control Protocol/Internet Protocol (TCP/IP). The scope of possible machines and devices is so broad because, in TCP/IPspeak, host means any network device with an IP address.

## Network Types

When we refer to parts of our network, we classify the sections of the network with a type. This designation of a particular type helps us generalize its use and function. Some of these designation types can use various technologies for connectivity, and some use specific technologies.

### Metropolitan Area Network

A **metropolitan area network (MAN)** is just as it sounds, a network covering a metropolitan area used to interconnect various buildings and facilities usually over a carrier provider network.

Think of a MAN as a concentrated WAN. MANs typically offer high-speed interconnections using in-ground fiber optics and can be very cost effective for high-speed interconnects.

A carrier provider network is typically a leased network connection. These providers will lease lines between two or more networks to provide connectivity.

### Wide Area Network

WAN networks are what we use to span large geographic areas and truly go the distance. Like the internet, WANs usually employ both routers and public links, so that's generally the criteria used to define them.

Here are some important ways that WANs are different from LANs:

- WANs usually need a router port or ports.

- WANs span larger geographic areas and/or can link disparate locations.

- WANs are usually slower.

- We can choose when and how long we connect to a WAN. A LAN is all or nothing—our workstation is connected to it either permanently or not at all, although most of us have dedicated WAN links now.

- WANs can utilize either private or public data transport media such as phone lines.

We get the word **Internet** from the term **internetwork**.

An internetwork is a type of LAN and/or WAN that connects a bunch of networks, or intranets.

In an internetwork, hosts still use hardware addresses to communicate with other hosts on the LAN. However, they use logical addresses (IP addresses) to communicate with hosts on a different LAN (other side of the router).

And **routers** are the devices that make this possible. Each connection into a router is a different logical network

![image](https://github.com/user-attachments/assets/c36d30c7-f449-4a3c-86a0-c20abf8a1898)

The picture above demonstrates how routers are employed to create an internetwork and how they enable our LANs to access WAN resources.

The Internet is a prime example of what's known as a **distributed WAN**—an internetwork that's made up of a lot of interconnected computers located in a lot of different places.

There's another kind of WAN, referred to as **centralized**, that's composed of a main, centrally located computer or location that remote computers and devices can connect to.

### Personal Area Network

For close proximity connections there are PANs, or personal area networks.

These are seen with smartphones and laptops in a conference room where local connections are used to collaborate and send data between devices.

While a PAN can use a wired connection such as Ethernet or USB, it is more common that short distance wireless connections are used such as Bluetooth, infrared, or ZigBee.

PANs are intended for close proximity between devices such as connecting to a projector, printer, or a co-worker's computer and extend usually only a few meters.

### Campus Area Network

A CAN, or campus area network, covers a limited geographical network such as a college or corporate campus. The CAN typically interconnects LANs in various buildings and offers a Wi-Fi component for roaming users.

A campus area network is between a LAN and WAN in scope. They are larger than a local area network but smaller than a metropolitan area network or wide area network.

Most CANs offer Internet connectivity as well as access to data center resources.

### Storage Area Network

A storage area network (SAN) is designed for, and used exclusively by, storage systems.

SANs interconnect servers to storage arrays containing centralized banks of hard drive or similar storage media.

SANs are usually found only in data centers and do not mix traffic with other LANs. 

The protocols are designed specifically for storage, with Fibre Channel being the most prevalent along with iSCSI. 

The network hardware is different from LAN switches and routers and is designed specifically to carry storage traffic.

Fibre Channel over Ethernet (FCoE) is a technology that encapsulates Fibre Channel over Ethernet. The protocol is typically used as a transitional technology until the next generation of equipment can support iSCSI. The sweet spot to FCoE is that you can use existing Ethernet infrastructure.

### Software-Defined Wide Area Network

A software-defined wide area network (SDWAN) is a virtual WAN architecture that uses software to manage connectivity, devices, and services and can make changes in the network based on current operations.

SDWANs integrate any type of transport architectures such as MPLS, LTE, and broadband Internet services to securely connect users to applications.

The SDWAN controller can make changes in real time to add or remove bandwidth or route around failed circuits. SDWANs can simplify wide area networking management and operations by decoupling the networking hardware from its control mechanism.

### Multiprotocol Label Switching

The term Multiprotocol Label Switching (MPLS), as used in this chapter, will define the actual layout of what is one of the most popular WAN protocols in use today.

MPLS has become one of the most innovative and flexible networking technologies on the market, and it has some key advantages over other WAN technologies:

- Physical layout flexibility

- Prioritizing of data

- Redundancy in case of link failure

- One-to-many connection

MPLS is a switching mechanism that imposes labels (numbers) to data and then uses those labels to forward data when it arrives at the MPLS network.

![image](https://github.com/user-attachments/assets/293ba3ad-abae-4e68-b1db-20209ed7114c)

The labels are assigned on the edge of the MPLS network, and forwarding inside the MPLS network (cloud) is done solely based on labels through virtual links instead of physical links.

Prioritizing data is a huge advantage; for example, voice data could have priority over basic data based on the labels. And since there are multiple paths for the data to be forwarded through the MPLS cloud, there's even some redundancy provided as well.

### Multipoint Generic Routing Encapsulation

The Multipoint Generic Routing Encapsulation (mGRE) protocol refers to a carrier or service provider offering that dynamically creates and terminates connections to nodes on a network.

mGRE is used in Dynamic Multipoint VPN deployments. The protocol enables dynamic connections without having to pre-configure static tunnel endpoints. 

The protocol encapsulates user data, creates a VPN connection to one or many nodes, and, when completed, tears down the connection.

## Network Architecture: Peer-to-Peer or Client-Server?

### Peer-to-Peer Networks

Computers connected in peer-to-peer networks do not have any central or special authority—they're all peers, meaning that when it comes to authority, they're all equals.

The authority to perform a security check for proper access rights lies with the computer that has the desired resource being requested from it.

It also means that the computers coexisting in a peer-to-peer network can be client machines that access resources and server machines and provide those resources to other computers.

This actually works pretty well as long as there isn't a huge number of users on the network, if each user backs things up locally, and if your network doesn't require much security.

If your network is running Windows, macOS, or Linux in a local LAN workgroup, you have a peer-to-peer network.

![image](https://github.com/user-attachments/assets/08ffb22b-e337-4b8d-906d-44f661538c69)

Keep in mind that peer-to-peer networks definitely present security-oriented challenges; for instance, just backing up company data can get pretty sketchy!

Backing up all your critical data may be tough, but it's vital.

Haven't all of us forgotten where we've put an important file? And then there's that glaring security issue to tangle with. Because security is not centrally governed, each and every user has to remember and maintain a list of users and passwords on each and every machine. Worse, some of those all-important passwords for the same users change on different machines—even for accessing different resources.

### Client-Server Networks

Client-server networks are pretty much the polar opposite of peer-to-peer networks because in them, a single server uses a network operating system for managing the whole network.

Here's how it works: A client machine's request for a resource goes to the main server, which responds by handling security and directing the client to the desired resource. This happens instead of the request going directly to the machine with the desired resource, and it has some serious advantages.

First, because the network is much better organized and doesn't depend on users remembering where needed resources are, it's a whole lot easier to find the files you need because everything is stored in one spot—on that special server. Your security also gets a lot tighter because all usernames and passwords are on that specific server, which is never ever used as a workstation.

You even gain scalability because client-server networks can have legions of workstations on them. And surprisingly, with all those demands, the network's performance is actually optimized.

![image](https://github.com/user-attachments/assets/eb56b877-8a09-4d00-b711-e4f8d819429a)

The picture above shows a client-server network with a server that has a database of access rights, user accounts, and passwords.

Many of today's networks are ideally a healthy blend of peer-to-peer and client-server architectures, with carefully specified servers that permit the simultaneous sharing of resources from devices running workstation operating systems.

Even though the supporting machines can't handle as many inbound connections at a time, they still run the server service reasonably well. And if this type of mixed environment is designed well, most networks benefit greatly by having the capacity to take advantage of the positive aspects of both worlds.

## Physical Network Topologies

Just as a topographical map is a type of map that shows the shape of the terrain, the physical topology of a network is also a type of map.

It defines the specific characteristics of a network, such as where all the workstations and other devices are located and the precise arrangement of all the physical media such as cables.

A network's physical topology gives you the lay of the land, and the logical topology shows how a digital signal or data navigates through that layout.

Here are the topologies you're most likely to run into these days:

- Bus
- Star/hub-and-spoke
- Ring
- Mesh
- Point-to-point
- Point-to-multipoint
- Hybrid

### Bus Topology

The bus topology consists of two distinct and terminated ends, with each of its computers connecting to one unbroken cable running its entire length.

Back in the day, we used to attach computers to that main cable with wire taps, but this didn't work all that well so we began using drop cables in their place. If we were dealing with 10Base2 Ethernet, we would slip a connector called a “T” into the main cable anywhere we wanted to connect a device to it instead of using drop cables.

![image](https://github.com/user-attachments/assets/378f57ad-7250-4242-9457-c5d57634088f)

Even though all the computers on this kind of network see all the data flowing through the cable, only the one computer, which the data is specifically addressed to, actually gets the data.

Some of the benefits of using a bus topology are that it's easy to install, and it's not very expensive, partly because it doesn't require as much cable as the other types of physical topologies.

But it also has some drawbacks: For instance, it's hard to troubleshoot, change, or move, and it really doesn't offer much in the way of fault tolerance because everything is connected to that single cable. This means that any fault in the cable would basically bring down the whole network.

**Fault tolerance** is the capability of a computer or a network system to respond to a condition automatically, often resolving it, which reduces the impact on the system. If faulttolerance measures have been implemented correctly on a network, it's highly unlikely that any of that network's users will know that a problem ever existed at all.

### Star topology

A star (hub-and-spoke) topology's computers are connected to a central point with their own individual cables or wireless connections. You'll often find that central spot inhabited by a device like a hub, a switch, or an access point.

Star topology offers lots of advantages over bus topology, making it more widely used even though it obviously requires more physical media.

One of its best features is that because each computer or network segment is connected to the central device individually, if the cable fails, it brings down only the machine or network segment related to the point of failure. This makes the network much more fault-tolerant as well as a lot easier to troubleshoot.

Another great thing about a star topology is that it's a lot more scalable—all you have to do if you want to add to it is run a new cable and connect to the machine at the core of the star.

![image](https://github.com/user-attachments/assets/8027008c-94ed-4a3c-a963-319b0461c3ee)

Although it is called a star (hub-and-spoke) topology, it also looks a lot like a bike wheel with spokes connecting to the hub in the middle of the wheel and extending outward to connect to the rim. And just as with that bike wheel, it's the hub device, actually more often a switch today, at the center of a star topology network that can give you the most grief if something goes wrong with it. If that central hub or switch happens to fail, down comes the whole network,

And here's a list of benefits you gain by going with it:

- New stations can be added or moved easily and quickly.

- A single cable failure won't bring down the entire network.

- It's relatively easy to troubleshoot.

And here are the disadvantages to using a star topology:

- The total installation cost can be higher because of the larger number of cables, even though prices have become more competitive.

- It has a single point of failure—the hub or other central device such as a switch.

There are two more sophisticated implementations of a star topology. The first is called a **point-to-point link**, where you have not only the device in the center of the spoke acting as a hub but also the device on the other end, which extends the network. This is still a star-wired topology, but as I'm sure you can imagine, it gives you a lot more scalability.

Another refined version is the wireless version, access points are pretty much just wireless hubs or switches that behave like their wired counterparts. They create a point-by-point connection to endpoints and other wireless access points.

### Ring Topology

In this type of topology, each computer is directly connected to other computers within the same network.

![image](https://github.com/user-attachments/assets/6e2e7266-fd2f-4cd4-b273-f828414aed20)

You can see that the network's data flows from computer to computer back to the source, with the network's primary cable forming a ring.

The problem is, the ring topology has a lot in common with the bus topology because if you want to add to the network, you have no choice but to break the cable ring, which is likely to bring down the entire network

This is one big reason that ring topology isn't very popular—you just won't run into it a lot as I did in the 1980s and early 1990s. It's also pricey because you need several cables to connect each computer, it's really hard to reconfigure, and as you've probably guessed, it's not fault-tolerant.

But even with all that being said, if you work at an Internet service provider (ISP), you may still find a physical ring topology in use for a technology called SONET or some other WAN technology. However, you won't find any LANs in physical rings anymore.

Although the ring topology is not used in LANs today, you will see the ring topology implemented with WAN providers.

### Mesh Topology

In this type of topology, you'll find that there's a path from every machine to every other one in the network.

You won't find it used in LANs very often, if ever, these days, but you will find a modified version of it known as a hybrid mesh used in a restrained manner on WANs, including the Internet.

Often, hybrid mesh topology networks will have quite a few connections between certain places to create redundancy (backup). And other types of topologies can sometimes be found in the mix too, which is another reason it's dubbed **hybrid**.

Just remember that it isn't a full-on mesh topology if there isn't a connection between all devices in the network.

![image](https://github.com/user-attachments/assets/7d274e85-d9cc-46db-ace3-dbd16848eda5)

A full mesh physical topology is least likely to have a collision, which happens when the data from two hosts trying to communicate simultaneously “collides” and gets lost.

This is also the reason you'll usually find the hybrid version in today's WANs. In fact, the mesh topology is actually pretty rare now, but it's still used because of the robust fault tolerance it offers. Because you have a multitude of connections, if one goes on the blink, computers and other network devices can simply switch to one of the many redundant connections that are up and running. AAAll that cabling in the mesh topology makes it a very pricey implementation.

You can make your network management much less insane than it is with mesh by using what's known as a partial mesh topology solution instead. You may lose a little fault tolerance, but if you go the partial mesh route, you still get to use the same technology between all the network's devices. Just remember that with partial mesh, not all devices will be interconnected, so it's important to choose the ones that will be wisely.

### Point-to-Point Topology

As its name implies, in a point-to-point topology you have a direct connection between two routers or switches, giving you one communication path.

The routers in a point-to-point topology can be linked by a serial cable, making it a physical network, or if they're located far apart and connected only via a circuit within a Frame Relay or MPLS network, it's a logical network instead.

![image](https://github.com/user-attachments/assets/2e24a4b7-e63e-4517-9e21-558ef668adf7)

The two round things radiating arrows represent our network's two routers, and that lightning bolt represents a WAN link.

The second part of the diagram shows two computers connected by a cable—a point-to-point link.

You'll usually find point-to-point networks within many of today's WANs, and as you can see in the third part. A link from a computer to a hub or switch is also a valid point-to-point connection. A common version of this setup consists of a direct wireless link between two wireless bridges that's used to connect computers in two different buildings together.

### Point-to-Multipoint Topology

A point-to-multipoint topology consists of a succession of connections between an interface on one router and multiple destination routers—one point of connection to multiple points of connection. Each of the routers and every one of their interfaces involved in the point-to-multipoint connection are part of the same network.

![image](https://github.com/user-attachments/assets/55b6f1c7-bf4e-4df8-972b-1d09690cbad3)

The picture above shows a WAN and demonstrates a point-to-multipoint network. You can clearly see a single, corporate router connecting to multiple branches.

![image](https://github.com/user-attachments/assets/b869edaf-41b2-4b23-a0d0-7c5734562260)

The picture above shows another prime example of a point-to-multipoint network: a college or corporate campus.'

### Hybrid Topology

Hybrid topology means just that—a combination of two or more types of physical or logical network topologies working together within the same network.

![image](https://github.com/user-attachments/assets/345dff77-3653-4665-86a0-ec938b656dbd)

The picture above depicts a hybrid network topology; it shows a few LANs connected by switches in a star topology configuration. The LANs are connected in a full mesh, which is connected to a router and a WAN link on a counter-rotating ring network.

## Topology Selection, Backbones, and Segments


