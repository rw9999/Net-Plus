# Networking Devices

## Common Network Connectivity Devices

Because these devices connect network entities, they're known as **connectivity devices**. 

Here's a list of the devices and related concepts I'll be covering in this chapter:

- Network interface card
- Hub
- Bridge
- Basic switch
- Basic router
- Basic firewall
- IDS/IPS/HIDS
- Access point
- Wireless range extender
- Contention methods
- Dynamic Host Configuration Protocol server
- Load balancer
- Proxy server
- Cable modem
- DSL modem
- Repeater
- Voice gateway
- Media converter
- VPN headend
- Voice over Internet Protocol phone
- Printer
- Physical access control devices
- Cameras
- Heating, ventilation, and air conditioning sensors
 -Internet of Things
- Refrigerator
- Smart speakers
- Smart thermostats
- Smart doorbells
- Industrial control systems/supervisory control and data acquisition

#

### Network Interface Card

A network interface card (NIC) is installed in your computer to connect, or interface, your computer to the network.

It provides the physical, electrical, and electronic connections to the network media.

The NIC is called a layer 2 device because the information it uses for communication, the MAC address, resides on the Data Link layer of the Open Systems Interconnection (OSI) model.

A NIC either is an expansion card or is built right into the computer's motherboard.

Today, almost all NICs are built into the computer motherboard, providing 10, 100, and 1,000 megabits per second (Mbps), but there was a time when all NICs were expansion cards that plugged into motherboard expansion slots. In some notebook computers, NIC adapters can be connected to the USB port or through a PC card slot. Ethernet speeds have been steadily increasing, especially in server chassis with 25, 40, and 100 Gbps NICs now quite common.

![image](https://github.com/user-attachments/assets/d24629c2-e16f-45cb-8463-855ac8bc6f46)

Nowadays, most PCs and laptops of all types come with an Ethernet and wireless connector built into the motherboard, so you usually don't need a separate card. It's rare to find a laptop today without a built-in wireless network card, but you can buy external wireless cards for desktops and laptops if you've got legacy equipment that needs them.

NICs today usually have one, two, or more LEDs; one, usually green, is called a link light, indicating that an Ethernet connection has been established with the device on the other end of the cable, and it flickers when traffic is being passed back or forth.

The other, or others, usually indicates the speed of the connection: 10, 100, or 1,000 Mbps.

There's no universal standard for NIC LEDs, so check the manual to familiarize yourself with the ones you are working with. But it's not always that cut-and-dried that a blinking LED can mean the NIC is receiving a proper signal from the hub or switch; it can also indicate connectivity to and detection of a carrier on a segment. Another possibility is that it's found connectivity with a router or other end device using a crossover cable.

The other LED is aptly named the activity LED, and it tends to flicker constantly. That activity indicates the intermittent transmission and reception of frames arriving at the network or leaving it.

The first LED you should verify is the link LED because if it's not illuminated, the activity LED simply cannot illuminate.

#

### Hub

A hub is the device that connects all the segments of the network together in a star topology Ethernet network.

As a hub has no intelligence, it is a layer 1 (Physical layer) device.

Each device in the network connects directly to the hub through a single cable and is used to connect multiple devices without segmenting a network. 

Any transmission received on one port will be sent out to all the other ports in the hub, including the receiving pair for the transmitting device, so that Carrier Sense Multiple Access with Collision Detection (CSMA/CD) on the transmitter can monitor for collisions.

Basically, this means that if one station sends a broadcast, all the others will receive it; yet based on the addressing found in the Ethernet frame, only the intended recipient will actually listen and process it.

This arrangement simulates the physical bus that the CSMA/CD standard was based on, and it's why we call the use of a hub in an Ethernet environment a physical star/logical bus topology.

![image](https://github.com/user-attachments/assets/da8fc74d-6e77-4764-a96f-d693220030c3)

The picture depicts a typical hub as you might find it employed within a small network. Since there are only two users, there isn't a problem in using a hub here. However, if there were 20 users, everyone would see Bob's request to send a packet to Sally. Most of the time, hubs really aren't recommended for corporate networks because of their limitations.

It's important to note that hubs are nothing more than glorified repeaters that are incapable of recognizing frames and data structures—the reason they act with such a lack of intelligence.

A broadcast sent out by any device on the hub will be propagated to all devices connected to it. And just as in a physical bus topology configuration, any two or more of those connected devices have the potential of causing a collision with each other, which means that this hardware device will create a LAN with the most network traffic collisions. 

Hubs are not suggested for use in today's corporate network for this reason.

#

### Bridge

A bridge—specifically, a transparent bridge—is a network device that connects two similar network segments together.

Its primary function is to keep traffic separated on either side of the bridge, breaking up collision domains.

![image](https://github.com/user-attachments/assets/cfa294ee-cc78-43e4-b3b2-5e7590580795)

What we can see here is that traffic is allowed to pass through the bridge only if the transmission is intended for a station on the opposite side.

The main reasons you would place a bridge in your network would be to connect two segments together or to divide a busy network into two segments.

As bridges use MAC addresses to make forwarding decisions, they are considered layer 2 devices.

Bridges are software-based, so, interestingly, you can think of a switch as a hardware-based, multiport bridge.

In fact, the terms bridge and switch are often used interchangeably because the two devices used basically the same bridging technologies. The past tense is there for a reason—you'd be hard-pressed to buy a bridge today.

#

### Switch

Switches connect multiple segments of a network together much like hubs do, but with three significant differences—a switch recognizes frames and pays attention to the source and destination MAC address of the incoming frame as well as the port on which it was received.

A switch makes each of its ports a unique, singular collision domain. Hubs don't do those things.

They simply send anything they receive on one port out to all the others.

As switches use MAC addresses to make forwarding decisions, they are considered layer 2 devices.

![image](https://github.com/user-attachments/assets/bf5f59ee-7b70-49ab-9c19-a1fe6651c0d3)

The picture shows a typical low-cost Ethernet switch. It looks a lot like a hub. However, switches can come in very large, expensive sizes.

Switches that can perform the basic switching process and do not allow you to configure more advanced features—like adding an IP address for connecting to the device or adding VLANs—are called unmanaged switches.

Others, like Cisco switches that do allow an IP address to be configured for management with such applications as simple network management protocol (SNMP) and do allow special ports to be configured (as in VoIP), are called managed switches.

Switches are layer 2 devices, which means they segment the network with MAC addresses.

If you see the term layer 3 switch, that means you are talking about a router, not a layer 2 switch. The terms router and layer 3 switch are interchangeable.

#

### Router

A router is a network device used to connect many, sometimes disparate, network segments together, combining them into what we call an **internetwork**.

A well-configured router can make intelligent decisions about the best way to get network data to its destination. 

It gathers the information it needs to make these decisions based on a network's particular performance data.

As routers use IP addresses to make forwarding decisions, they are considered layer 3 devices.

![image](https://github.com/user-attachments/assets/6bba3347-4153-4080-a02c-c56e37b37baa)

The picture shows a small office, home office (SOHO) router that provides wired and wireless access for hosts and connects them to the Internet without any necessary configuration. But know that I certainly don't recommend leaving a router with the default configuration

Routers can be multifaceted devices that behave like computers unto themselves with their own complex operating systems—for example, Cisco's IOS.

You can even think of them as CPUs that are totally dedicated to the process of routing packets. And because of their complexity and flexibility, you can configure them to actually perform the functions of other types of network devices (like firewalls, for example) by simply implementing a specific feature within the router's software.

Routers can have many different names: layer 3 switch and multilayer switch are the most common, besides the name router, of course. Remember, if you hear just the word switch, that means a layer 2 device. Routers, layer 3 switches, and multilayer switches are all layer 3 devices.

#

Interface Configurations

When configuring interfaces on a router or switch, unless you're doing complex configurations such as connecting up a Voice over IP (VoIP) network, the interface configurations are pretty straightforward.

There is a major difference between a router interface and a switch interface configuration, however. 

On a switch, you do not add an IP address since they read only to layer 2, and most of the time, you never even need to configure a switch interface. 

First, they are enabled by default, and second, they are very good at auto-detecting the speed, duplex, and, in newer switches, even the Ethernet cable type (crossover or straight-through).

A router is much different, and an IP address is expected on each interface; they are not enabled by default, and a good layer 3 network design must be considered before installing a router.

Let's start by taking a look at a basic Cisco switch configuration.

First, notice by the output shown that there is no configuration on the interfaces, yet you can plug this switch into your network and it would work.

This is because all ports are enabled and there are some very basic configurations that allow the switch to run without any configuration—they can be considered plug-and-play in a small or home network:

    Switch#sh running-config
    [output cut]
    !
    interface FastEthernet0/1
    !
    interface FastEthernet0/2
    !
    interface FastEthernet0/3
    !
    interface FastEthernet0/4
    !
    interface FastEthernet0/5
    !
    interface FastEthernet0/6
    !
    interface FastEthernet0/7
    !
    interface FastEthernet0/8
    !

Let's take a look at a configuration of a simple switch interface. First, we'll notice the duplex options:

    Switch(config-if)#duplex ?
      auto Enable AUTO duplex configuration
      full Force full duplex operation
      half Force half-duplex operation

All switch ports are set to duplex auto by default, and usually you can just leave this configuration alone. However, be aware that if your network interface card is set to half-duplex and the switch port is configured for full-duplex, the port will receive errors and you'll eventually get a call from the user.

This is why it is advised to just leave the defaults on your hosts and switch ports, but it is a troubleshooting spot to check when a problem is reported from a single user.

The next configuration and/or troubleshooting spot you may need to consider is the speed of the port:

    Switch(config-if)#speed ?
       10 Force 10 Mbps operation
       100 Force 100 Mbps operation
       1000 Force 1000 Mbps operation
       auto Enable AUTO speed configuration

Again, this is set to auto, but you may want to force the port to be 1000 and full-duplex. Typically, the NIC will run this without a problem and you'll be sure you're getting the most bang for your buck on your switch port.

Let's take a look at a router interface. We're pretty much going to configure (or not configure) the same parameters.

However, you should be very aware that a router interface and a switch interface perform different functions.

A router interface will break up collision domains just as a switch interface does, but the purpose of a router interface is to create and maintain broadcast domains and the connectivity of WAN services.

Basic layer 2 switches cannot provide these services.

You must have a layer 3 design before you can implement a router, meaning you must have your subnet design laid out on your network diagram, and your IP addressing scheme must be completely understood. You cannot start configuring router interfaces randomly; there must be a design, and it needs to be correct.

Unlike switches, router interfaces do not just work when you plug them intothe network—they must be configured and enabled. All ports are shut down by default, and why shouldn't they be? Unless you have a network design and understand IP addressing, what good is a router to your network?

Let's take a look:

    Router(config-if)#duplex ?
      auto Enable AUTO duplex configuration
      full Force full duplex operation
      half Force half-duplex operation
    
    Router(config-if)#speed ?
      10 Force 10 Mbps operation
      100 Force 100 Mbps operation
      1000 Force 1000 Mbps operation
      auto Enable AUTO speed configuration
    
    Router(config-if)#ip address ?
      A.B.C.D IP address
      dhcp IP Address negotiated via DHCP
      pool IP Address autoconfigured from a
      local DHCP pool

First, we can see that the basics are there, duplex and speed, but also, to make a router interface useful at all we must add an IP address. 

Notice that the options allow you to configure a specific IP address or allow the interface to receive the address from a DHCP server. 

You would use this option only if you had an IP address reservation for the router interface on your DHCP server since having your router get a random IP address from a DHCP server would be hard to manage.

Let's finish the basics:

    Router(config-if)#ip address 1.1.1.1
    255.0.0.0
    Router(config-if)#no shutdown
    Router(config-if)#
    *Oct 5 17:26:46.522: %LINK-3-UPDOWN:
    Interface FastEthernet0/0,
    changed state to up
    *Oct 5 17:26:47.522: %LINEPROTO-5-UPDOWN:
    Line protocol on
    Interface FastEthernet0/0, changed state to up

The interface can now be connected to a layer 2 switch, and the hosts connected to the same broadcast domain must set their default gateway address to 1.1.1.1, and voilà, they can now send packets to the router.

#

### Firewall

Firewalls are your network's security guards, and to be real, they're probably the most important thing to implement on your network.

That's because today's networks are almost always connected to the Internet—a situation that makes security crucial.

A firewall protects your LAN resources from invaders that prowl the Internet for unprotected networks while simultaneously preventing all or some of your LAN's computers from accessing certain services on the Internet.

You can employ them to filter packets based on rules that you or the network administrator create and configure to strictly delimit the type of information allowed to flow in and out of the network's Internet connection. 

Firewalls operate at multiple layers of the OSI model. Some firewalls can operate up to the Application layer.

A firewall can be either a stand-alone “black box” or a software implementation placed on a server or router.

Either way, the firewall will have at least two network connections: one to the Internet (known as the public side) and one to the network (known as the private side).

Sometimes, there is a second firewall.

![image](https://github.com/user-attachments/assets/966b345d-a6ac-4808-aa65-83063f43f759)

This firewall is used to connect servers and equipment that can be considered both public and private (like web and email servers).

This intermediary network is known as a screened subnet or, as it is often called, a **demilitarized zone (DMZ)**.

Firewalls are the first line of defense for an Internet-connected network. Without them in place, any network that's connected to the Internet is essentially wide open to anyone with a little technical savvy who seeks to exploit LAN resources and/or access your network's sensitive information.

In network security, a screened subnet refers to the use of one or more logical screening routers as a first defense on your network.

A typical firewall design can define three separate networks, or zones, to separate the external (untrusted) zone to a trusted (internal and DMZ) zone, also referred to as a perimeter network.

Now, CompTIA likes to call this perimeter network a screened subnet or DMZ, where your DNS server and possibly HTTPS web servers are located.

#

### IDS / IPS

Intrusion detection systems (IDSs) and intrusion prevention systems (IPSs) are very important in today's networks.

They are network security appliances that monitor networks and packets for malicious activity.

An IDS is considered monitor mode and just records and tells you about problems, whereas an IPS can work in real time to stop threats as they occur.

The main difference between them is that an IPS works inline to actively prevent and block intrusions that are detected based on the rules you set up.

IPSs can send an alarm, create correlation rules and remediation, drop malicious packets, provide malware protection, and reset the connection of offending source hosts.

#

### HIDS

In a host-based IDS (HIDS), software runs on one computer to detect abnormalities on that system alone by monitoring applications, system logs, and event logs—not by directly monitoring network traffic.

Systems like these are typically implemented on servers because they're a bear to manage if spread across several client computers on a network.

Plus, if the IDS database is on the local computer and its data becomes compromised by an attack, the IDS data could be corrupted, too.

Other types of IDSs are protocol-based (PIDS), which monitor traffic for one protocol on one server, and application protocol-based (APIDS), which monitor traffic for a group of servers running the same application (such as SQL).

#

### Access Point

Wireless networks are even more important, now more than ever connecting all of our home appliances so they can communicate to apps we control and the Internet. The ease of communicating on a network using an AP instead of having to use an Ethernet cable has changed our world forever.

![image](https://github.com/user-attachments/assets/7dbe2e20-7501-490b-a5b4-ac61be205d26)

The wireless client modulates a digital signal to an analog signal, which the AP can read and demodulate back to a digital signal.

The type of AP described in is known as an autonomous AP because it manages the wireless area with no controller or manager.

The AP creates one collision domain and can run only half-duplex, which is why you can describe an AP as being like a hub.

However, even though some standards provide some full-duplex-type connectivity, a wireless host will never achieve the same type of throughput, security, and consistency that a wired Ethernet network would.

#

### Wireless Range Extender

In some cases you need the WLAN to extend further than the technology in use is designed to deliver. In that case, you can deploy an extender.

These are radios and antennas that operate in the same frequency or channel and receive the signal as a station would and then transmit it in the direction you desire to clients that are out of reach of the original AP.

These devices should be placed so there is at least 15% overlap of the coverage areas of the AP and the extender.

#

### Wireless LAN Controller

In larger wireless networks, managing dozens, hundreds, or even thousands of wireless access points becomes an administrative burden.

This led to the design and deployment of a centralized Wi-Fi configuration controller known as a WLC, or wireless LAN controller.

The WLC lets you configure the complete network on a single device and push the configurations out to the Wi-Fi access points, referred to as lightweight access points, because the controller does the heavy lifting. The access points also tunnel the user data back to the controller, forwarding the traffic onto the LAN.

WLCs greatly reduce the amount of administrative overhead required to manage large enterprise wireless networks.

#

### Load Balancer

Your average router just sends incoming packets to their specified, correlative IP address on the network, but a load balancer can send incoming packets to multiple machines hidden behind one IP address.

In large and busy networks, often a single server does not have the capabilities to serve all requested traffic.

For example, a very busy website on the Internet could have hundreds of thousands of incoming requests every second. This is often too large for a single server to accommodate. Also, if that server were to fail, the whole website could go offline.

Load balancers solve this problem by publishing a virtual IP address to a domain to receive incoming traffic.

The load balancer then has a pool of real servers that it distributes the connections to. The distribution can be based on round robin, least number of connections, response time, a weighted percentage, or other metrics to evenly distribute the workload to the servers.

Health checks are performed to make sure that the servers are operational. If one does not respond, it can be automatically taken offline with the site still operating on the remaining servers.

Capacity can be dynamically added or removed using load balancers by using either manual or automatic scaling based on the current servers' workloads. New servers can dynamically be added and removed from the pool to scale the service up or down.

Today's load-balancing routers follow various rules to determine specifically how they will route network traffic. Depending on your needs, you can set rules based on the least load, fault tolerance, the fastest response times, or just dividing up (balancing) outbound requests for smooth network operations.

In fact, the fault tolerance, or redundancy, as well as the scalability so vital to large networking environments and e-commerce are some of the great benefits we gain using load balancers.

Think about this scenario: Say you have a website where people are placing orders for the stuff you're selling. Obviously, the orders placed vary in size, and the rate at which they come in varies; you definitely wouldn't want your servers becoming so overloaded that they hose up and crash your site, causing you to lose lots of money, now would you? That's where balancingthe load of traffic between a group of servers comes to the rescue, because even if one of them freezes, your customers will still be able to access your site and place orders.

#

### Contention Methods

In both wireless and wired environments that are shared mediums, meaning devices share a collision domain, such as when connected to a hub or when connected to a wireless access point, there is potential for frames from multiple devices colliding, destroying both packets.

Both wired and wireless environments use a contention method to arbitrate access to the medium to help prevent collisions or at the least to recover from them when they occur.

#

### CSMA / CA

When the device sending the frame is transmitting onto a wireless network, the Carrier Sense Multiple Access with Collision Avoidance (CSMA/CA) contention method is used.

The method starts with a check of the medium (in this case, a check of the radio frequency) for activity called **physical carrier sense**.

The frame will go to the AP. The AP will acknowledge reception of the frame. If the frame is destined for another wireless station located on this wireless LAN, the frame will be forwarded to it by the AP. When this occurs, the AP will follow the same CSMA/CA contention method to get the frame onto the wireless medium.

If the frame is destined for a station on the wired LAN, the AP will drop the 802.11 MAC header (which is structured differently from an Ethernet MAC header) and build a new Ethernet MAC header by using its MAC address as the source address and the MAC address of the default gateway as the destination.

The LAN router will receive the frame, and normal LAN routing to the destination will continue from there, using the CSMA/CD contention mechanism (covered a bit later) to place the frame in the wire at each step.

If frames are returned to the station, the AP will receive them, drop the Ethernet MAC header, build an 802.11 MAC header, and return the frame to the wireless station.

When this occurs, the AP will follow the same CSMA/CA contention method to get the frame onto the wireless medium.

#

### Describing CSMA/CA Operation

Because it is impossible for wireless stations to detect collisions, the CSMA/CA contention method is required to arbitrate access to the network.

It requires a more involved process of checking for existing wireless traffic before a frame can be transmitted wirelessly.

The stations (including the AP) must also acknowledge all frames.

The steps in the process are as follows:

1. Laptop A has a frame to send to laptop B. Before sending, laptop A must check for traffic in two ways. First, it performs carrier sense, which means it listens to see whether any radio waves are being received on its transmitter.

2. If the channel is not clear (traffic is being transmitted), laptop A will decrement an internal countdown mechanism called the random backoff algorithm. This counter will have started counting down after the last time this station was allowed to transmit. All stations will be counting down their own individual timers. When a station's timer expires, it is allowed to send.

3. If laptop A checks for carrier sense and there is no traffic and its timer hits zero, it will send the frame.

4. The frame goes to the AP.

5. The AP sends an acknowledgment back to laptop A. Until that acknowledgment is received by laptop A, all other stations must remain silent. The AP will cache the frame, where it already may have other cached frames that need to be relayed to other stations. Each frame that the AP needs to relay must wait its turn to send the frame using the same mechanism as the stations.

6. When the frame's turn comes up in the cache queue, the frame from laptop A will be relayed to laptop B.

7. Laptop B sends an acknowledgment back to the AP. Until that acknowledgment is received by the AP, all other stations must remain silent.

When you consider that this process has to occur for every single frame and that there are many other frame types used by the AP to manage other functions of the network that also create competition for air time, it is no wonder that actual throughput on a wireless LAN is at best about half the advertised rate.

For example, if two wireless stations were the only wireless clients and they were using 802.11g, which is capable of 54 Mbps, the very best throughput experienced would be about 25 to 28 Mbps. Moreover, as soon as a third station arrives, throughput will go down again because the stations are dividing the air time by 3 instead of 2. Add a fourth, and it gets even worse.

#

### CSMA/CD

When the device sending the frame is transmitting onto a wired network, the Carrier Sense Multiple Access with Collision Detection (CSMA/CD) contention method is used.

This method is somewhat more efficient because
it is possible for wired computers to detect collisions while wireless stations cannot. When a host's or router's interface needs to send a frame, it checks the wire, and if no traffic is detected, it sends without checking a random back-off timer.

However, it continues to listen, and if it detects that a collision has occurred, it sends out a jam signal that requires all stations to stop transmitting. Then the two computers that were involved in the collision will both wait a random amount of time (that each arrives at independently) and will resend.

So instead of using a random break-off algorithm every time a transmission occurs, Ethernet uses its ability to detect collisions and uses this timer only when required, which makes the process more efficient.

#

### Describing CSMA/CD Operation

CSMA/CD has mechanisms that help minimize but not eliminate collisions. 

Its operation is as follows:

1. When a device needs to transmit, it checks the wire. If a transmission is already underway, the device can tell. This is called carrier sense.

2. If the wire is clear, the device will transmit. Even as it is transmitting, it is performing carrier sense.

3. If another host is sending simultaneously, there will be a collision. The collision is detected by both devices through carrier sense.

4. Both devices will issue a jam signal to all the other devices, which indicates to them to not transmit.

5. Then both devices will increment a retransmission counter. This is a cumulative total of the number of times this frame has been transmitted and a collision has occurred. There is a maximum number at which the device aborts the transmission of the frame.

6. Both devices will calculate a random amount of time and will wait that amount of time before transmitting again. This calculation is called a random back-off.

7. In most cases, because both devices choose random amounts of time to wait, another collision will not occur.

#

### Dynamic Host Configuration Protocol Server

DHCP servers assign IP addresses to hosts

This protocol gives us a much easier way to administer—by automatically providing IP information—than the alternative and tedious method known as static IP addressing or static assignment, where we have to address each host manually.

It works well in any network environment, from tiny to huge, and allows all types of hardware to be employed as a DHCP server, including routers.

