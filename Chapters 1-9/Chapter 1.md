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
