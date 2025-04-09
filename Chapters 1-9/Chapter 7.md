# IP Addressing

An IP address is a numeric identifier assigned to each machine on an IP network. It designates the specific location of a device on the network.

An IP address is a logical address, not a hardware address—the latter is hard-coded on a network interface card (NIC) and used for finding hosts on a local network.

IP addressing was designed to allow hosts on one network to communicate with a host on a different network regardless of the type of LANs the hosts are participating in.

## IP Terminology

**Bit** A bit is one binary digit, either a 1 or a 0.

**Byte** A byte is 7 or 8 bits, depending on whether parity is used. For the rest of this chapter, always assume a byte is 8 bits.

**Octet** An octet, made up of 8 bits, is just an ordinary 8-bit binary number. In this chapter, the terms byte and octet are completely interchangeable, and they are typically displayed in decimal up to 255.

**Network Address** This is the designation used in routing to send packets to a remote network—for example, 10.0.0.0, 172.16.0.0, and 192.168.10.0.

**IP Address** A logical address used to define a single host; however, IP addresses can be used to reference many or all hosts as well. If you see something written as just IP, it is referring to IPv4. IPv6 will always be written as IPv6.

**Broadcast Address** The broadcast address is used by applications and hosts to send information to all hosts on a network. Examples include 255.255.255.255, which designates all networks and all hosts; 172.16.255.255, which specifies all subnets and hosts on network 172.16.0.0; and 10.255.255.255, which broadcasts to all subnets and hosts on network 10.0.0.0.

## The Hierarchical IP Addressing Scheme

An IP address consists of 32 bits of information. These bits are divided into four sections, referred to as octets or bytes, and four octets sum up to 32 bits (8 × 4 = 32).

You can depict an IP address using one of three methods:

- Dotted-decimal, as in 172.16.30.56

- Binary, as in 10101100.00010000.00011110.00111000

- Hexadecimal, as in AC.10.1E.38

Each of these examples validly represents the same IP address.

Hexadecimal is used with IPv6, and IP addressing uses dotted-decimal or binary, but you still might find an IP address stored in hexadecimal in some programs.

Windows is a good example of a program that stores a machine's IP address in hex. Windows 11 (and all other Windows versions) stores the IP addresses in hexadecimal subkeys in HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters\Interfaces.

The 32-bit IP address is known as a structured, or hierarchical, address as opposed to a flat, or nonhierarchical, address.

Although either type of addressing scheme can be used, **hierarchical addressing** has been chosen for a very important reason.

The major advantage of this scheme is that it can handle a large number of addresses, namely, 4.3 billion (a 32-bit address space with two possible values for each position—either 0 or 1— gives you 2 , or 4,294,967,296).

The disadvantage of the flat-addressing scheme, and the reason it's not used for IP addressing, relates to routing. If every address were unique, all routers on the Internet would need to store the address of each and every machine on the Internet. This would make 32 efficient routing impossible, even if only a fraction of all possible addresses were used.

The solution to this problem is to use a two- or three-level hierarchical addressing scheme that is structured by network and host or by network, subnet, and host.

This two- or three-level scheme is comparable to a telephone number. The first section, the area code, designates a very large area. The second section, the prefix, narrows the scope to a local calling area. The final segment, the customer number, zooms in on the specific connection.

IP addresses use the same type of layered structure. Rather than all 32 bits being treated as a unique identifier, as in flat addressing, a part of the address is designated as the network address and the other part is designated as either the subnet and host or just the host address.

#

### Network Addressing

The network address—also called the network number—uniquely identifies each network.

Every machine on the same network shares that network address as part of its IP address.

In the IP address 172.16.30.56, for example, 172.16 is the network address.

The host address is assigned to, and uniquely identifies, each machine on a network. This part of the address must be unique because it identifies a particular machine—an individual—as opposed to a network, which is a group. So in the sample IP address 172.16.30.56, the 30.56 is the host address.

The designers of the Internet decided to create classes of networks based on network size.

For the small number of networks possessing a very large number of hosts, they created the rank Class A network. At the other extreme is the Class C network, which is reserved for the numerous networks with a small number of hosts. The class distinction for networks between very large and very small is predictably the Class B network.

Subdividing an IP address into a network and host address is determined by the class designation of your network.

![image](https://github.com/user-attachments/assets/81e59599-5030-41bb-baf6-b00aa2a9a5e2)

To ensure efficient routing, Internet designers defined a mandate for the leading-bits section of the address for each different network class.

For example, since a router knows that a Class A network address always starts with a 0, the router might be able to speed a packet on its way after reading only the first bit of its address.

For now, know that Classes A, B, and C are the only ranges that are used to address hosts in our networks.

### Class A Addresses

In a Class A network address, the first byte is assigned to the network address, and the three remaining bytes are used for the host addresses.

The Class A format is as follows:

    network.host.host.host

For example, in the IP address 49.22.102.70, the 49 is the network address and 22.102.70 is the host address. Every machine on this particular network would begin with the distinctive network address of 49.

Class A network addresses are 1 byte long, with the first bit of that byte reserved and the 7 remaining bits available for manipulation or addressing.

As a result, the theoretical maximum number of Class A networks that can be created is 128. Why? Well, each of the 7-bit positions can be either a 0 or a 1 and 2 gives you 128.

The designers of the IP address scheme said that the first bit of the first byte in a Class A network address must always be off, or 0. This means a Class A address must be between 0 and 127 in the first byte, inclusive.

Consider the following network address:

    0xxxxxxx

If we turn the other 7 bits all off and then turn them all on, we'll find the Class A range of network addresses:

    00000000 = 0
    01111111 = 127

So, a Class A network is defined in the first octet between 0 and 127, and it can't be less or more.

To complicate matters further, the network address of all 0s (0000 0000) is reserved to designate the default route.

Additionally, the address 127, which is reserved for diagnostics, can't be used either, which means you can really only use the numbers 1 to 126 to designate Class A network addresses.

This means the actual number of usable Class A network addresses is 128 minus 2, or 126.

![image](https://github.com/user-attachments/assets/dbc2b8b0-01a1-4ddf-acd8-cc9b7721a35b)
![image](https://github.com/user-attachments/assets/a335b1eb-d45a-4566-973a-1cbc80d2eb25)

Each Class A address has 3 bytes (24 bit positions) for the host address of a machine.

This means there are 2 —or 16,777,216—unique combinations and, therefore, precisely that many potential unique host addresses for each Class A network.

Because host addresses with the two patterns of all 0s and all 1s are reserved, the actual maximum usable number of hosts for a Class A network is 2 minus 2, which equals 16,777,214. Either way, you can see that's a seriously huge number of hosts to have on a network segment.

Here's an example of how to figure out the valid host IDs in a Class A network address:

- All host bits off is the network address: 10.0.0.0.
  
- All host bits on is the broadcast address: 10.255.255.255.

The valid hosts are the numbers in between the network address and the broadcast address: 10.0.0.1 through 10.255.255.254. Notice that 0s and 255s can be valid host IDs. All you need to remember when trying to find valid host addresses is that the host bits can't ever be all turned off or all turned on at the same time.

### Class B Addresses

In a Class B network address, the first 2 bytes are assigned to the network address, and the remaining 2 bytes are used for host addresses. 

The format is as follows:

    network.network.host.host

For example, in the IP address 172.16.30.56, the network address is 172.16, and the host address is 30.56.

With a network address being 2 bytes (8 bits each), we're left with 2 unique combinations.

But the Internet designers decided that all Class B network addresses should start with the binary digit 1, then 0. This leaves 14 bit positions available to manipulate, so in reality, we get 16,384 (that is, 2 ) unique Class B network addresses.

In a Class B network, the request or comments (RFCs) state that the first bit of the first byte must always be turned on, but the second bit must always be turned off.

If we turn the other 6 bits all off and then all on, we will find the range for a Class B network:

    10000000 = 128
    10111111 = 191

As you can see, a Class B network is defined when the first byte is configured from 128 to 191.

A Class B address uses 2 bytes for host addresses. This is 2 minus the two reserved patterns (all 0s and all 1s), for a total of 65,534 possible host addresses for each Class B network.

Here's an example of how to find the valid hosts in a Class B network:

- All host bits turned off is the network address: 172.16.0.0.

- All host bits turned on is the broadcast address: 172.16.255.255.

The valid hosts would be the numbers in between the network address and the broadcast address: 172.16.0.1 through 172.16.255.254.

### Class C Addresses

The first 3 bytes of a Class C network address are dedicated to the network portion of the address, with only 1 measly byte remaining for the host address.

Here's the format:

    network.network.network.host

Using the example IP address 192.168.100.102, the network address is 192.168.100, and the host address is 102.

In a Class C network address, the first 3 bit positions are always the binary 110. The calculation is as follows: 3 bytes, or 24 bits, minus 3 reserved positions leaves 21 positions. Hence, there are 2 , or 2,097,152, possible Class C networks.

For Class C networks, the RFCs define the first 2 bits of the first octet as always turned on, but the third bit can never be on. 

Following the same process as the previous classes, convert from binary to decimal to find the range. Here's the range for a Class C network:

    11000000 = 192
    11011111 = 223

So, if you see an IP address with a range from 192 up to 223, you'll know it's a Class C IP address.

Each unique Class C network has 1 byte to use for host addresses. This gets us to 2 , or 256, minus the two reserved patterns of all 0s and all 1s for a total of 254 available host addresses for each Class C network.

Here's an example of how to find a valid host ID in a Class C network:

- All host bits turned off is the network ID: 192.168.100.0.

- All host bits turned on is the broadcast address: 192.168.100.255.

The valid hosts would be the numbers in between the network address and the broadcast address: 192.168.100.1 through 192.168.100.254.

### Class D and E Addresses

Addresses with the first octet of 224 to 255 are reserved for Class D and E networks.

Class D (224–239) is used for multicast addresses and Class E (240–255) for scientific purposes.

You do need to remember that the multicast range is from 224.0.0.0 through 239.255.255.255.

### Special Purposes of Network Addresses

Some IP addresses are reserved for special purposes, so network administrators can't ever assign them to hosts.

See previous table.

#

### Private IP Addresses (RFC 1918)

The people who created the IP addressing scheme also created what we call private IP addresses.

These addresses can be used on a private network, but they're not routable through the Internet.

This is designed for the purpose of creating a measure of much-needed security, but it also conveniently saves valuable IP address space.

If every host on every network had to have real routable IP addresses, we would have run out of available IP addresses to hand out years ago. But by using private IP addresses, ISPs, corporations, and home users need only a relatively tiny group of bona fide IP addresses to connect their networks to the Internet. 

This is economical because they can use private IP addresses on their inside networks and get along just fine.

To accomplish this task, the ISP and the corporation—the end users, no matter who they are—need to use something called network address translation (NAT), which basically takes a private IP address and converts it for use on the Internet.

NAT provides security in that these IP addresses cannot be seen by external users.

External users will only be able to see the public IP address to which the private IP address has been mapped. 

Moreover, multiple devices in the same private network can use the same, real IP address to transmit out onto the Internet. Doing things this way saves megatons of address space—a very good thing for us all.

RFC 1918 reserved private addresses

![image](https://github.com/user-attachments/assets/64733975-058e-4574-b08f-abb68795b638)

#

### Virtual IP (VIP)

When a public IP address is substituted for the actual private IP address that has been assigned to the network interface of the device, the public IP address becomes an example of what is called a virtual IP address.

This means it doesn't correspond to an actual physical network interface. A well-used example is a subinterface configured on a physical router interface, which allows you to create multiple IPs or subnets on one interface.

There are other examples of such virtual IP addresses. For example, when a web proxy server substitutes its IP address for the sender's IP address before sending a packet to the Internet, it is another example of creating a virtual IP address.

#

### APIPA

What happens if you have a few hosts connected together with a switch or hub and you don't have a DHCP server?

You can add static IP information to a host, or you can use what is called Automatic Private IP Addressing (APIPA). I don't recommend this, but APIPA is a “feature,” so you do need to remember it.

With APIPA, clients can automatically self-configure an IP address and subnet mask, which is the minimum information needed for hosts to communicate when a DHCP server isn't available.

In this way, it could be thought of as a DHCP failover scheme. If all of the hosts set themselves with an APIPA address, they could communicate with one another but unfortunately not with any addresses that were statically configured, such as default gateways.

The IP address range for APIPA is 169.254.0.1 through 169.254.255.254. The client also configures itself with a default Class B subnet mask of 255.255.0.0.

However, when you're in your corporate network and you're running a DHCP server, and your host displays that it is using this IP address range, this means that either your DHCP client on the host is not working, or the DHCP server is down or can't be reached because of a network issue.

For example, if you plug a DHCP client into a port that is disabled, the host will receive an APIPA address. If users cannot connect to the Internet and their IP addresses fall into the APIPA address range, the DHCP server is most likely the problem.

## IPv4 Address Types

Most people use broadcast as a generic term, and most of the time, we understand what they mean. But not always. For example, you might say, “The host broadcasted through a router to a DHCP server,” but, well, it's pretty unlikely that this would ever really happen. What you probably mean— using the correct technical jargon—is, “The DHCP client broadcasted for an IP address; a router then forwarded this as a unicast packet to the DHCP server.” Remember that with IPv4, broadcasts are pretty important, but with IPv6, there aren't any broadcasts sent at all.

**Layer 2 Broadcasts** These are sent to all nodes on a LAN.

**Broadcasts (Layer 3)** These are sent to all nodes on the network.

**Unicast** This is an address for a single interface, and these are used to send packets to a single destination host.

**Multicast** These are packets sent from a single source and transmitted to many devices on different networks. Referred to as one-to-many.

#

### Layer 2 Broadcasts

First, understand that layer 2 broadcasts are also known as hardware broadcasts—they only go out on a LAN, and they don't go past the LAN boundary (router).

The typical hardware address is 6 bytes (48 bits) and looks something like 0c.43.a4.f3.12.c2. The broadcast would be all 1s in binary, which would be all Fs in hexadecimal, as in FF.FF.FF.FF.FF.FF.

#

### Layer 3 Broadcasts

Broadcast messages are meant to reach all hosts on a broadcast domain. These are the network broadcasts that have all host bits on.

Here's an example that you're already familiar with:

The network address of 172.16.0.0 would have a broadcast address of 172.16.255.255—all host bits on.

Broadcasts can also be “any network and all hosts,” as indicated by 255.255.255.255.

A good example of a broadcast message is an Address Resolution Protocol (ARP) request.

When a host has a packet, it knows the logical address (IP) of the destination. To get the packet to the destination, the host needs to forward the packet to a default gateway if the destination resides on a different IP network.

If the destination is on the local network, the source will forward the packet directly to the destination. Because the source doesn't have the MAC address to which it needs to forward the frame, it sends out a broadcast, something that every device in the local broadcast domain will listen to.

This broadcast says, in essence, “If you are the owner of IP address 192.168.2.3, please forward your MAC address to me,” with the source giving the appropriate information.

#

### Unicast Address

A unicast address is assigned to a single interface, and this term is used in both IPv4 and IPv6 to describe your host interface IP address.

#

### Multicast Address (Class D)

Multicast is a different beast entirely. At first glance, it appears to be a hybrid of unicast and broadcast communication, but that isn't quite the case.

Multicast does allow point-to-multipoint communication, which is similar to broadcasts, but it happens in a different manner.

The crux of multicast is that it enables multiple recipients to receive messages without flooding the messages to all hosts on a broadcast domain. However, this is not the default behavior—it's what we can do with multicasting if it's configured correctly.

Multicast works by sending messages or data to IP multicast group addresses.

Routers then forward copies (unlike broadcasts, which are not forwarded) of the packet out every interface that has hosts subscribed to a particular group address.

This is where multicast differs from broadcast messages—with multicast communication, copies of packets, in theory, are sent only to subscribed hosts. When I say in theory, this means the hosts will receive, for example, a multicast packet destined for 224.0.0.10 (this is an EIGRP packet, and only a router running the EIGRP protocol will read it).

All hosts on the broadcast LAN (Ethernet is a broadcast multi-access LAN technology) will pick up the frame, read the destination address, and immediately discard the frame, unless they are in the multicast group. This saves PC processing, not LAN bandwidth.

Multicasting can cause severe LAN congestion, in some instances, if not implemented carefully.

There are several different groups that users or applications can subscribe to. The range of multicast addresses starts with 224.0.0.0 and goes through 239.255.255.255. As you can see, this range of addresses falls within IP Class D address space based on classful IP assignment.

## Internet Protocol Version 6 (IPv6)

