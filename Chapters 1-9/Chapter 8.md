# IP Subnetting, Troubleshooting IP, and Introduction to NAT

## Subnetting Basics

Subnetting allows you to take one larger network and break it into a bunch of smaller networks.

There are loads of reasons in favor of subnetting, including the following benefits:

**Reduced Network Traffic** We all appreciate less traffic of any kind. With networks, it's no different. Without trusty routers, packet traffic could grind the entire network down to a near standstill. With routers, most traffic will stay on the local network; only packets destined for other networks will pass through the router. Routers create broadcast domains. The more broadcast domains you create, the smaller the broadcast domains and the less network traffic on each network segment.

**Optimized Network Performance** This is the very cool reward you get when you reduce network traffic.

**Simplified Management** It's easier to identify and isolate network problems in a group of smaller connected networks than within one gigantic network.

**Facilitated Spanning of Large Geographical Distances** Because WAN links are considerably slower and more expensive than LAN links, a single large network that spans long distances can create problems in every area previously listed. Connecting multiple smaller networks makes the system more efficient.

#

### How to Create Subnets

To create subnetworks, you take bits from the host portion of the IP address and reserve them to define the subnet address. 

This means fewer bits for hosts, so the more subnets, the fewer bits are left available for defining hosts.

But before you actually implement subnetting, you really need to determine your current requirements as well as plan for future conditions.

Follow these steps—they're your recipe for solid design:

1. Determine the number of required network IDs:
    1. One for each subnet
    2. One for each wide area network (WAN) connection
2. Determine the number of required host IDs per subnet:
    1. One for each TCP/IP host
    2. One for each router interface
3. Based on the previous requirements, create the following:
    1. One subnet mask for your entire network
    2. A unique subnet ID for each physical segment
    3. A range of host IDs for each subnet

#

### Subnet Masks

For the subnet address scheme to work, every machine on the network must know which part of the host address will be used as the subnet address.

This is accomplished by assigning a subnet mask to each machine.

A subnet mask is a 32-bit value that allows the recipient of IP packets to distinguish the network ID portion of the IP address from the host ID portion of the IP address.

The network administrator creates a 32-bit subnet mask composed of 1s and 0s. The 1s in the subnet mask represent the positions that refer to the network, or subnet, addresses.

Not all networks need subnets, meaning they use the default subnet mask. This is basically the same as saying that a network doesn't have a subnet address.

![image](https://github.com/user-attachments/assets/3bbfa6ed-40c6-4c76-886b-9577c005e9d2)

The picture shows shows the default subnet masks for Classes A, B, and C.

These default masks cannot and do not change.

In other words, you can't make a Class B subnet mask read 255.0.0.0. If you try, the host will read that address as invalid and usually won't even let you type it in. For a Class A network, you can't change the first byte in a subnet mask; it must read 255.0.0.0 at a minimum. Similarly, you cannot assign 255.255.255.255, because this is all 1s—a broadcast address. A Class B address must start with 255.255.0.0, and a Class C has to start with 255.255.255.0.

The addresses with the first octet of 224 to 255 are reserved for Class D and E networks. Class D (224–239) is used for multicast addresses and Class E (240–255) for scientific purposes.

But you do need to remember that the multicast range is from 224.0.0.0 through 239.255.255.255.

#

### Classless Inter-Domain Routing (CIDR)

It's basically the method that Internet service providers (ISPs) use to allocate a number of addresses to a company or a home connection.

They provide addresses in a certain block size. Another term for the use of different length subnet masks in the network is **variable-length subnet masking (VLSM)**.

When you receive a block of addresses from an ISP, what you get will look something like this: 192.168.10.32/28.

This is telling you what your subnet mask is. The slash notation (/) means how many bits are turned on (1s).

Obviously, the maximum could only be /32 because a byte is 8 bits and there are 4 bytes in an IP address: 4 × 8 = 32.

But keep in mind that the largest subnet mask available (regardless of the class of address) can only be a /30 because you have to keep at least 2 bits for host bits.

Take, for example, a Class A default subnet mask, which is 255.0.0.0. This means that the first byte of the subnet mask is all ones (1s), or 11111111. When referring to a slash notation, you need to count all the 1 bits to figure out your mask. The 255.0.0.0 is considered a /8 because it has 8 bits that are 1s—that is, 8 bits that are turned on.

Class B default mask would be 255.255.0.0, which is a /16 because 16 bits are (1s): 11111111.11111111.00000000.00000000.

![image](https://github.com/user-attachments/assets/73f50e15-7ed2-4aa9-8257-23b07c51cc2f)

![image](https://github.com/user-attachments/assets/e4f2803e-358c-4ad7-962b-8a7af167151c)

![image](https://github.com/user-attachments/assets/7529a340-f8b4-460d-b801-83ca6fca8c8d)

Although, according to RFC 1518, any device or software that claims to be CIDR-compliant will allow supernetting, meaning a traditional Class C address can be used with a /23 subnet mask, in almost all cases.

The /8 through /15 can be used only with Class A network addresses; /16 through /23 can be used by Class A and B network addresses; and /24 through /30 can be used by Class A, B, and C network addresses.

This is a big reason most companies use Class A network addresses. By being allowed the use of all subnet masks, they gain the valuable benefit of maximum flexibility for their network design.

Supernetting is the opposite of subnetting. Subnetting is the division of a network into subnets. Supernetting is the method of combining smaller networks in a single address.

#

### Subnetting Class C Addresses

There are many different ways to subnet a network.

In a Class C address, only 8 bits are available for defining the hosts.

Remember that subnet bits start at the left and go to the right, without skipping bits.

This means the only Class C subnet masks can be those listed here:

![image](https://github.com/user-attachments/assets/c621e271-7a28-434e-a514-17e4130d6496)

We can't use a /31 or /32 because, remember, we have to leave at least 2 host bits for assigning IP addresses to hosts.

#

### Subnetting a Class C Address: The Fast Way!

Practice Example #1C: 255.255.255.128 (/25)

Because 128 is 10000000 in binary, there is only 1 bit for subnetting, and there are 7 bits for hosts. We're going to subnet the Class C network address 192.168.10.0.

- 192.168.10.0 = Network address

- 255.255.255.128 = Subnet mask

Now, let's answer the big five:

- How many subnets? Because 128 is 1 bit on (10000000), the answer is 2 = 2.

- How many hosts per subnet? We have 7 host bits off (10000000), so the equation is 2 – 2 = 126 hosts.

- What are the valid subnets? 256 – 128 = 128. Remember, we'll start at zero and count in our block size, so our subnets are 0, 128.

- What's the broadcast address for each subnet? The number right before the value of the next subnet is all host bits turned on and equals the broadcast address. For the 0 subnet, the next subnet is 128, so the broadcast address of the 0 subnet is 127.

- What are the valid hosts? These are the numbers between the subnet and broadcast address. The easiest way to find the hosts is to write out the subnet address and the broadcast address. This way, the valid hosts are obvious. The following table shows the 0 and 128 subnets, the valid host ranges of each, and the broadcast address of both subnets:

![image](https://github.com/user-attachments/assets/ac35096d-4dfd-411b-8725-e1afc2224108)

![image](https://github.com/user-attachments/assets/e4836b7e-62a6-4145-ad0e-f059ec9d1fcf)

Okay, looking at a Class C /25, it's pretty clear there are two subnets. But so what —why is this significant? Well actually, it's not, but that's not the right question. What you really want to know is what you would do with this information.

The key to understanding subnetting is to understand the very reason you need to do it. And I'm going to demonstrate this by going through the process of building a physical network—and let's add a router. (We now have an internetwork) Because we added that router, for the hosts on our internetwork to communicate, they must now have a logical network addressing scheme. We could use IPv6, but IPv4 is still the most popular, and it also just happens to be what we're studying at the moment, so that's what we're going with.

By the way, the output you see after the diagram is the routing table of the router, which was displayed by executing the show ip route command on the router. There are two physical networks, so we're going to implement a logical addressing scheme that allows for two logical networks. As always, it's a really good idea to look ahead and consider any likely growth scenarios—both short and long term, but for this example, a /25 will do the trick.

