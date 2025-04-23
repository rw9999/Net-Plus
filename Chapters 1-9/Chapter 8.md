![image](https://github.com/user-attachments/assets/54e9a6ac-3229-48a3-971d-b396c1f852a3)# IP Subnetting, Troubleshooting IP, and Introduction to NAT

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

When you've chosen a possible subnet mask for your network and need to determine the number of subnets, valid hosts, and broadcast addresses of a subnet that the mask provides, all you need to do is answer five simple questions:

- How many subnets does the chosen subnet mask produce?
- How many valid hosts per subnet are available?
- What are the valid subnets?
- What's the broadcast address of each subnet?
- What are the valid hosts in each subnet?

Here's how you get the answers to those five big questions:

- How many subnets? 2<sup>x</sup> = number of subnets. x is the number of masked bits, or the 1s. For example, in 11000000, the number of 1s gives us 2<sup>2</sup> subnets. In this example, there are four subnets.

- How many hosts per subnet? 2<sup>y</sup> – 2 = number of hosts per subnet. y is the number of unmasked bits, or the 0s. For example, in 11000000, the number of 0s gives us 2<sup>6</sup> – 2 hosts. In this example, there are 62 hosts per subnet. You need to subtract 2 for the subnet address and the broadcast address, which are not valid hosts.

- What are the valid subnets? 256 – subnet mask = block size, or increment number. An example would be 256 – 192 = 64. The block size of a 192 mask is always 64. Start counting at zero in blocks of 64 until you reach the subnet mask value, and these are your subnets. 0, 64, 128, 192.

- What's the broadcast address for each subnet? Now here's the really easy part. Because we counted our subnets in the last section as 0, 64, 128, and 192, the broadcast address is always the number right before the next subnet. For example, the 0 subnet has a broadcast address of 63 because the next subnet is 64. The 64 subnet has a broadcast address of 127 because the next subnet is 128. And so on. And remember, the broadcast address of the last subnet is always 255.

- What are the valid hosts? Valid hosts are the numbers between the subnets, omitting all the 0s and all the 1s. For example, if 64 is the subnet number and 127 is the broadcast address, then 65–126 is the valid host range—it's always the numbers between the subnet address and the broadcast address.


### Practice Example #1C: 255.255.255.128 (/25)

Because 128 is 10000000 in binary, there is only 1 bit for subnetting, and there are 7 bits for hosts. We're going to subnet the Class C network address 192.168.10.0.

- 192.168.10.0 = Network address

- 255.255.255.128 = Subnet mask

Now, let's answer the big five:

- How many subnets? Because 128 is 1 bit on (10000000), the answer is 2<sup>1</sup> = 2.

- How many hosts per subnet? We have 7 host bits off (10000000), so the equation is 2<sup>7</sup> – 2 = 126 hosts.

- What are the valid subnets? 256 – 128 = 128. Remember, we'll start at zero and count in our block size, so our subnets are 0, 128.

- What's the broadcast address for each subnet? The number right before the value of the next subnet is all host bits turned on and equals the broadcast address. For the 0 subnet, the next subnet is 128, so the broadcast address of the 0 subnet is 127.

- What are the valid hosts? These are the numbers between the subnet and broadcast address. The easiest way to find the hosts is to write out the subnet address and the broadcast address. This way, the valid hosts are obvious. The following table shows the 0 and 128 subnets, the valid host ranges of each, and the broadcast address of both subnets:

![image](https://github.com/user-attachments/assets/ac35096d-4dfd-411b-8725-e1afc2224108)

![image](https://github.com/user-attachments/assets/e4836b7e-62a6-4145-ad0e-f059ec9d1fcf)

Okay, looking at a Class C /25, it's pretty clear there are two subnets. But so what —why is this significant? Well actually, it's not, but that's not the right question. What you really want to know is what you would do with this information.

The key to understanding subnetting is to understand the very reason you need to do it. And I'm going to demonstrate this by going through the process of building a physical network—and let's add a router. (We now have an internetwork) Because we added that router, for the hosts on our internetwork to communicate, they must now have a logical network addressing scheme. We could use IPv6, but IPv4 is still the most popular, and it also just happens to be what we're studying at the moment, so that's what we're going with.

By the way, the output you see after the diagram is the routing table of the router, which was displayed by executing the show ip route command on the router. There are two physical networks, so we're going to implement a logical addressing scheme that allows for two logical networks. As always, it's a really good idea to look ahead and consider any likely growth scenarios—both short and long term, but for this example, a /25 will do the trick.

### Practice Example #2C: 255.255.255.192 (/26)

In this second example, we're going to subnet the network address 192.168.10.0 using the subnet mask 255.255.255.192.

- 192.168.10.0 = Network address
- 255.255.255.192 = Subnet mask

It's time to answer the big five:

- How many subnets? Because 192 is 2 bits on (11000000), the answer is 2<sup>2</sup> = 4 subnets.
- How many hosts per subnet? We have 6 host bits off (11000000), so the equation is 2<sup>6</sup> – 2 = 62 hosts.
- What are the valid subnets? 256 – 192 = 64. Remember, we start at zero and count in our block size, so our subnets are 0, 64, 128, and 192.
- What's the broadcast address for each subnet? The number right before the value of the next subnet is all host bits turned on and equals the broadcast address. For the 0 subnet, the next subnet is 64, so the broadcast address for the 0 subnet is 63.
- What are the valid hosts? These are the numbers between the subnet and broadcast address. The easiest way to find the hosts is to write out the subnet address and the broadcast address. This way, the valid hosts are obvious. The following table shows the 0, 64, 128, and 192 subnets, the valid host ranges of each, and the broadcast address of each subnet:

![image](https://github.com/user-attachments/assets/a1107dae-5c70-4bea-9e0b-f891f1bb3dfb)

![image](https://github.com/user-attachments/assets/308ff3ba-1918-4004-be3c-83dbdf807cd4)

The /26 mask provides four subnetworks, and we need a subnet for each router interface. With this mask, in this example, we actually have room to add another router interface.

### Practice Example #3C: 255.255.255.224 (/27)

This time, we'll subnet the network address 192.168.10.0 and subnet mask 255.255.255.224.

- 192.168.10.0 = Network address
- 255.255.255.224 = Subnet mask

- How many subnets? 224 is 11100000, so our equation is 2<sup>3</sup> = 8
- How many hosts? 2<sup>5</sup> – 2 = 30.
- What are the valid subnets? 256 – 224 = 32. We just start at zero and count to the subnet mask value in blocks (increments) of 32: 0, 32, 64, 96, 128, 160, 192, and 224.
- What's the broadcast address for each subnet (always the number right before the next subnet)?
- What are the valid hosts (the numbers between the subnet number and the broadcast address)?

To answer the last two questions, first just write out the subnets, and then write out the broadcast address—the number right before the next subnet.

Last, fill in the host address. The following table gives you all the subnets for the 255.255.255.224 Class C subnet mask:

![image](https://github.com/user-attachments/assets/d24bc22e-d5d3-4827-a42b-7618d32c2163)

![image](https://github.com/user-attachments/assets/50a226f2-6435-4782-92e3-860595571e8e)

### Practice Example #4C: 255.255.255.240 (/28)

Let's practice on another one:

- 192.168.10.0 = Network address
- 255.255.255.240 = Subnet mask

- Subnets? 240 is 11110000 in binary. 2<sup>4</sup> = 16.
- Hosts? 4 host bits, or 2<sup>4</sup> – 2 = 14.
- Valid subnets? 256 – 240 = 16. 0, 16, 32, 48, 64, 80, 96, 112, 128, 144, 160, 176, 192, 208, 224, 240.
- Broadcast address for each subnet?
- Valid hosts?

To answer the last two questions, check out the following table. It gives you the subnets, valid hosts, and broadcast address for each subnet. 

First, find the address of each subnet using the block size (increment). 

Second, find the broadcast address of each subnet increment (it's always the number right before the next valid subnet); then, just fill in the host address.

### Practice Example #5C: 255.255.255.248 (/29)

- 192.168.10.0 = Network address
- 255.255.255.248 = Subnet mask

- Subnets? 248 in binary = 11111000. 2<sup>5</sup> = 32.
- Hosts? 2<sup>3</sup> – 2 = 6.
- Valid subnets? 256 – 248 = 8, start at zero: 0, 8, 16, 24, 32, 40, 48, 56, 64, 72, 80, 88, 96, 104, 112, 120, 128, 136, 144, 152, 160, 168, 176, 184, 192, 200, 208, 216, 224, 232, 240, and 248.
- Broadcast address for each subnet?
- Valid hosts?

### Practice Example #6C: 255.255.255.252 (/30)

- 192.168.10.0 = Network address
- 255.255.255.252 = Subnet mask

- Subnets? 64.
- Hosts? 2.
- Valid subnets? 0, 4, 8, 12, and so on, all the way to 252.

- Broadcast address for each subnet (always the number right before the next subnet)?
- Valid hosts (the numbers between the subnet number and the broadcast address)?

 #
 
 ### So What Do You Know Now?

 Here's where you can really apply what you've learned so far and begin committing it all to memory

 When you see a subnet mask or slash notation (CIDR), you should know the following when working with Class C networks.

 /25
 
What do you know about a /25?

- 128 mask
- 1 bit on and 7 bits off (10000000)
- Block size of 128
- 2 subnets, each with 126 hosts

/26

And what do you know about a /26?

- 192 mask
- 2 bits on and 6 bits off (11000000)
- Block size of 64
- 4 subnets, each with 62 hosts

/27

What about a /27?

- 224 mask
- 3 bits on and 5 bits off (11100000)
- Block size of 32
- 8 subnets, each with 30 hosts

/28

And what about a /28?

- 240 mask
- 4 bits on and 4 bits off
- Block size of 16
- 16 subnets, each with 14 hosts

/29

What do you know about a /29?

- 248 mask
- 5 bits on and 3 bits off
- Block size of 8
- 32 subnets, each with 6 hosts

/30

And last, what about a /30?

- 252 mask
- 6 bits on and 2 bits off
- Block size of 4
- 64 subnets, each with 2 hosts

Regardless of whether you have a Class A, Class B, or Class C address, the /30 mask will provide you with only two hosts, ever. This mask is suited almost exclusively for use on point-to-point links.

#

### Subnetting Class B Addresses

Notice that we have a lot more possible subnet masks than we do with a Class C network address:

255.255.0.0 (/16)
255.255.128.0 (/17)
255.255.192.0 (/18)
255.255.224.0 (/19)
255.255.240.0 (/20)
255.255.248.0 (/21)
255.255.252.0 (/22)
255.255.254.0 (/23)
255.255.255.0 (/24)
255.255.255.128(/25)
255.255.255.192(/26)
255.255.255.224(/27)
255.255.255.240(/28)
255.255.255.248(/29)
255.255.255.252(/30)

We know the Class B network address has 16 bits available for host addressing. 

This means we can use up to 14 bits for subnetting (because we have to leave at least 2 bits for host addressing).

Using a /16 means you are not subnetting with Class B, but it is a mask you can use.

The process of subnetting a Class B network is pretty much the same as it is for a Class C, except that you have more host bits and you start in the third octet.

Use the same subnet numbers for the third octet with Class B that you used for the fourth octet with Class C, but add a 0 to the network portion and a 255 to the broadcast section in the fourth octet.

The following table shows you an example host range of two subnets used in a Class B 240 (/20) subnet mask:

![image](https://github.com/user-attachments/assets/5da0aec0-5d5c-497a-8559-13fd7f7665d5)

Notice that these are the same numbers we used in the fourth octet with a /28 mask, but we moved them to the third octet and added a .0 and .255 at the end. Just add the valid hosts between the numbers, and you're set.

### Subnetting Practice Examples: Class B Addresses

The following sections will give you an opportunity to practice subnetting Class B addresses. Again, I have to mention that this is the same as subnetting with Class C, except we start in the third octet—with the exact same numbers.

### Practice Example #1B: 255.255.128.0 (/17)

Let's take a look at our first example:

- 172.16.0.0 = Network address
- 255.255.128.0 = Subnet mask

- Subnets? 2<sup>1</sup> = 2 (same as Class C).
- Hosts? 2<sup>15</sup> – 2 = 32,766 (7 bits in the third octet, and 8 in the fourth).
- Valid subnets? 256 – 128 = 128. 0, 128. Remember that subnetting in Class B starts in the third octet, so the subnet numbers are really 0.0 and 128.0, as shown in the next table. These are the exact numbers we used with Class C; we use them in the third octet and add a 0 in the fourth octet for the network address.
- Broadcast address for each subnet?

The following table shows the two subnets available, the valid host range, and the broadcast address of each:

![image](https://github.com/user-attachments/assets/78a2d52a-5360-431c-b31b-7a0e46c430f8)

Notice that we just added the fourth octet's lowest and highest values and came up with the answers. And again, it's done the same way as for a Class C subnet. We just use the same numbers in the third octet and added 0 and 255 in the fourth octet.

### Practice Example #2B: 255.255.192.0 (/18)

Let's take a look at a second example with Class B.

- 172.16.0.0 = Network address
- 255.255.192.0 = Subnet mask

- Subnets? 2<sup>2</sup> = 4.
- Hosts? 2<sup>14</sup> – 2 = 16,382 (6 bits in the third octet, and 8 in the fourth).
- Valid subnets? 256 – 192 = 64. 0, 64, 128, 192. Remember that we're in the third octet, so the subnet numbers are really 0.0, 64.0, 128.0, and 192.0, as shown in the next table.
- Broadcast address for each subnet?
- Valid hosts?

The following table shows the four subnets available, the valid host range, and the broadcast address of each:

![image](https://github.com/user-attachments/assets/57dbe6bf-e23e-47f2-9247-c538069659dc)

Again, it's pretty much the same as it is for a Class C subnet—we just added 0 and 255 in the fourth octet for each subnet in the third octet.

#

### Practice Example #3B: 255.255.240.0 (/20)

Let's take a look:

172.16.0.0 = Network address
255.255.240.0 = Subnet mask

- Subnets? 2<sup>4</sup> = 16.
- Hosts? 2<sup>12</sup> – 2 = 4,094.
- Valid subnets? 256 – 240 = 16, but we start counting from 0. 0, 16, 32, 48, and so on, up to 240. Notice that these are the same numbers as a Class C 240 mask—we just put them in the third octet and add a 0 and 255 in the fourth octet.
- Broadcast address for each subnet?
- Valid hosts?

The following table shows the first four subnets, valid hosts, and broadcast address in a Class B 255.255.240.0 mask:

![image](https://github.com/user-attachments/assets/3151df10-1331-4f99-af90-00fc945120c5)

![image](https://github.com/user-attachments/assets/a08e3252-b412-44b4-813d-a1bd2a77649c)

### Practice Example #4B: 255.255.254.0 (/23)

Let's take a look:

- 172.16.0.0 = Network address
- 255.255.254.0 = Subnet mask

- Subnets? 2<sup>7</sup> = 128.
- Hosts? 2<sup>9</sup> – 2 = 510.
- Valid subnets? 256 – 254 = 0, 2, 4, 6, 8, and so on, up to 254.
- Broadcast address for each subnet?
- Valid hosts?

The following table shows the first five subnets, valid hosts, and broadcast address in a Class B 255.255.254.0 mask:

![image](https://github.com/user-attachments/assets/90ab6a4b-6a48-4d79-840e-889aae74effd)

![image](https://github.com/user-attachments/assets/97a83fa1-ab7d-4f0c-9990-c740e2de7a76)

### Practice Example #5B: 255.255.255.0 (/24)

Contrary to popular belief, 255.255.255.0 used with a Class B network address is not called a Class B network with a Class C subnet mask. It's amazing how many people see this mask used in a Class B network and think it's a Class C subnet mask. This is a Class B subnet mask with 8 bits of subnetting—it's considerably different from a Class C mask. Subnetting this address is fairly simple:

- 172.16.0.0 = Network address
- 255.255.255.0 = Subnet mask

- Subnets? 2<sup>8</sup> = 256.
- Hosts? 2<sup>8</sup> – 2 = 254.
- Valid subnets? 256 – 255 = 1. 0, 1, 2, 3, and so on, all the way to 255.
- Broadcast address for each subnet?
- Valid hosts?

### Practice Example #6B: 255.255.255.128 (/25)

This is one of the hardest subnet masks you can play with. And worse, it actually is a really good subnet to use in production because it creates more than 500 subnets with a whopping 126 hosts for each subnet—a nice mixture.

- 172.16.0.0 = Network address
- 255.255.255.128 = Subnet mask

- Subnets? 2<sup>9</sup> = 512.
- Hosts? 2<sup>7</sup> – 2 = 126.
- Valid subnets? Now for the tricky part. 256 – 255 = 1. 0, 1, 2, 3, and so on for the third octet. But you can't forget the one subnet bit used in the fourth octet. Remember when I showed you how to figure one subnet bit with a Class C mask? You figure this out the same way. (Now you know why I showed you the 1-bit subnet mask in the Class C section—to make this part easier.) You actually get two subnets for each third octet value, hence the 512 subnets. For example, if the third octet is showing subnet 3, the two subnets would actually be 3.0 and 3.128.
- Broadcast address for each subnet?
- Valid hosts?

### Practice Example #7B: 255.255.255.192 (/26)

Now, this is where Class B subnetting gets easy. Because the third octet has a 255 in the mask section, whatever number is listed in the third octet is a subnet number. However, now that we have a subnet number in the fourth octet, we can subnet this octet just as we did with Class C subnetting. Let's try it:

- 172.16.0.0 = Network address
- 255.255.255.192 = Subnet mask

- Subnets? 2<sup>10</sup> = 1024.
- Hosts? 2<sup>6</sup> – 2 = 62.
- Valid subnets? 256 – 192 = 64. The subnets are shown in the following table. Do these numbers look familiar?
- Broadcast address for each subnet?
- Valid hosts?

Notice that for each subnet value in the third octet, you get subnets 0, 64, 128, and 192 in the fourth octet.

### Practice Example #8B: 255.255.255.224 (/27)

This is done the same way as the preceding subnet mask, except that we have more subnets and fewer hosts per subnet available.

- 172.16.0.0 = Network address
- 255.255.255.224 = Subnet mask

- Subnets? 2<sup>11</sup> = 2048.
- Hosts? 2<sup>5</sup> – 2 = 30.
- Valid subnets? 256 – 224 = 32. 0, 32, 64, 96, 128, 160, 192, 224.
- Broadcast address for each subnet?
- Valid hosts?

#

### Subnetting in Your Head: Class B Addresses

1. What subnet and broadcast address is the IP address 172.16.10.33 255.255.255.224 (/27) a member of?

   The interesting octet is the fourth octet. 256 – 224 = 32. 32 + 32 = 64. Bingo: 33 is between 32 and 64. However, remember that the third octet is considered part of the subnet, so the answer is the 10.32 subnet. The broadcast is 10.63 because 10.64 is the next subnet. That was a pretty easy one.

2. What subnet and broadcast address is the IP address 172.16.66.10 255.255.192.0 (/18) a member of?

   The interesting octet is the third octet instead of the fourth octet. 256 – 192 = 64. 0, 64, 128. The subnet is 172.16.64.0. The broadcast must be 172.16.127.255 because 128.0 is the next subnet.

Notice in the last example I started counting at zero. This is called **ip subnet-zero**. It is a command that if executed on a router, allows us to use the zero subnet as our first subnet. This may or may not be enabled on your router. If it is not enabled, then you cannot start counting subnets at zero. Most routers, if not all routers these days, support ip subnet-zero.

3. What subnet and broadcast address is the IP address 172.16.50.10 255.255.224.0 (/19) a member of? 

   256 – 224 = 0, 32, 64 (remember, we always start counting at zero). The subnet is 172.16.32.0, and the broadcast must be 172.16.63.255 because 64.0 is the next subnet.

4. What subnet and broadcast address is the IP address 172.16.46.255 255.255.240.0 (/20) a member of?

   256 – 240 = 16. The third octet is interesting to us. 0, 16, 32, 48. This subnet address must be in the 172.16.32.0 subnet, and the broadcast must be 172.16.47.255 because 48.0 is the next subnet. So, yes, 172.16.46.255 is a valid host.

5. What subnet and broadcast address is the IP address 172.16.45.14 255.255.255.252 (/30) a member of?
  
   Where is the interesting octet? 256 – 252 = 0, 4, 8, 12, 16 (in the fourth octet). The subnet is 172.16.45.12, with a broadcast of 172.16.45.15 because the next subnet is 172.16.45.16.

6. What is the subnet and broadcast address of the host 172.16.88.255/20?

   What is a /20? If you can't answer this, you can't answer this question, can you? A /20 is 255.255.240.0, which gives us a block size of 16 in the third octet, and because no subnet bits are on in the fourth octet, the answer is always 0 and 255 in the fourth octet. 0, 16, 32, 48, 64, 80, 96. Bingo: 88 is        between  80 and 96, so the subnet is 80.0 and the broadcast address is 95.255.

7. A router receives a packet on an interface with a destination address of 172.16.46.191/26. What will the router do with this packet?

    Discard it. Do you know why? 172.16.46.191/26 is a 255.255.255.192 mask, which gives us a block size of 64. Our subnets are then 0, 64, 128, 192. 191 is the broadcast address of the 128 subnet, so a router, by default, will discard any broadcast packets.

## Troubleshooting IP Addressing

![image](https://github.com/user-attachments/assets/fa36754f-5dc0-4c72-a517-26a728c50f7f)

Let's use this picture as an example of your basic IP trouble—poor Sally can't log into the Windows server.

Let's get started by going over the basic troubleshooting steps.

Pretend you're at Sally's host and she's complaining that she can't communicate to a server that just happens to be on a remote network:

1. Open a command prompt window on Sally's host, and ping 127.0.0.1.

        C:\>ping 127.0.0.1
        Pinging 127.0.0.1 with 32 bytes of data:
        Reply from 127.0.0.1: bytes=32 time<1ms
        TTL=128
        Reply from 127.0.0.1: bytes=32 time<1ms
        TTL=128
        Reply from 127.0.0.1: bytes=32 time<1ms
        TTL=128
        Reply from 127.0.0.1: bytes=32 time<1ms
        TTL=128
        Ping statistics for 127.0.0.1:
        Packets: Sent = 4, Received = 4, Lost
        = 0 (0% loss),
        Approximate round trip times in milliseconds:
        Minimum = 0ms, Maximum = 0ms, Average
        = 0ms

This is the diagnostic, or IPv4 loopback address, and if you get a successful ping, your IP stack is considered to be initialized. If it fails, then you have an IP stack failure and need to reinstall TCP/IP on the host.

If you ping the loopback address and receive an “unable to contact IP driver, error code 2” message, you need to reinstall the TCP/IP protocol suite on the host.

2. Now, from the same command prompt window, ping the IP address of the local host.

        C:\>ping 172.16.10.2
        Pinging 172.16.10.2 with 32 bytes of data:
        Reply from 172.16.10.2: bytes=32 time<1ms
        TTL=128
        Reply from 172.16.10.2: bytes=32 time<1ms
        TTL=128 Reply from 172.16.10.2: bytes=32
        time<1ms TTL=128
        Reply from 172.16.10.2: bytes=32 time<1ms
        TTL=128
        Ping statistics for 172.16.10.2:
        Packets: Sent = 4, Received = 4, Lost
        = 0 (0% loss),
        Approximate round trip times in milliseconds:
        Minimum = 0ms, Maximum = 0ms, Average
        = 0ms

If that's successful, your network interface card (NIC) is functioning. 

If it fails, there is a problem with the NIC. 

Success here doesn't mean that a cable is plugged into the NIC, only that the IP protocol stack on the host can communicate to the NIC (via the LAN driver).

3. From the command prompt window, ping the default gateway (router).

        C:\>ping 172.16.10.1
        Pinging 172.16.10.1 with 32 bytes of data:
        Reply from 172.16.10.1: bytes=32 time<1ms
        TTL=128
        Reply from 172.16.10.1: bytes=32 time<1ms
        TTL=128
        Reply from 172.16.10.1: bytes=32 time<1ms
        TTL=128
        Reply from 172.16.10.1: bytes=32 time<1ms
        TTL=128
        Ping statistics for 172.16.10.1:
        Packets: Sent = 4, Received = 4, Lost
        = 0 (0% loss),
        Approximate round trip times in milliseconds:
        Minimum = 0ms, Maximum = 0ms, Average
        = 0ms

If the ping works, it means that the NIC is plugged into the network and can communicate on the local network. If it fails, you have a local physical network problem that could be anywhere from the NIC to the router.

4. If steps 1 through 3 were successful, try to ping the remote server.

        C:\>ping 172.16.20.2
        Pinging 172.16.20.2 with 32 bytes of data:
        Reply from 172.16.20.2: bytes=32 time<1ms
        TTL=128
        Reply from 172.16.20.2: bytes=32 time<1ms
        TTL=128
        Reply from 172.16.20.2: bytes=32 time<1ms
        TTL=128
        Reply from 172.16.20.2: bytes=32 time<1ms
        TTL=128
        Ping statistics for 172.16.20.2:
        Packets: Sent = 4, Received = 4, Lost
        = 0 (0% loss),
        Approximate round trip times in milliseconds:
        Minimum = 0ms, Maximum = 0ms, Average
        = 0ms

If that works, then you know that you have IP communication between the local host and the remote server. You also know that the remote physical network is working.

If the user still can't communicate with the server after steps 1 through 4 are successful, you probably have some type of name resolution problem and need to check your Domain Name System (DNS) settings.

But if the ping to the remote server fails, then you know you have some type of remote physical network problem and need to go to the server and work through steps 1 through 3 until you find the snag.

Basic yet handy command-line tools that you can use to help troubleshoot your network from both a PC and a Cisco router (the commands might do the same thing, but they are implemented differently):

**Packet InterNet Groper** (ping) Uses an Internet Control Message Protocol (ICMP) echo request and replies to test if a host IP stack is initialized and alive on the network.

**Traceroute** Displays the list of routers on a path to a network destination by using time to live (TTL) time-outs and ICMP error messages. This command will work on a router, MAC, or Linux box, but not from a Windows command prompt.

**Tracert** Same command as traceroute , but it's a Microsoft Windows command and will not work on other devices, like a Cisco router or macOS or Linux box.

**arp -a** Displays IP–to–MAC-address mappings on a Windows PC.

**ipconfig /all** Used only from a command prompt. Shows you the PC network configuration.

Once you've gone through all these steps and used the appropriate command-line tools, if necessary, what do you do if you find a problem? How do you go about fixing an IP address configuration error?

#

### Determining IP Address Problems

It's common for a host, router, or other network device to be configured with the wrong IP address, subnet mask, or default gateway. Because this happens way too often, I'm going to teach you how to both determine and fix IP address configuration errors.

Once you've worked through the four basic steps of troubleshooting and determined there's a problem, you obviously then need to find and fix it.

It really helps to draw out the network and IP addressing scheme. If it's already done, consider yourself lucky; although it should be done, it rarely is. And if it is, it's usually outdated or inaccurate anyway. Typically it is not done, and you'll probably just have to bite the bullet and start from scratch.

Once you have your network accurately drawn out, including the IP addressing scheme, you need to verify each host's IP address, mask, and default gateway address to determine the problem. (I'm assuming that you don't have a physical problem or that if you did, you've already fixed it.)

![image](https://github.com/user-attachments/assets/8df85194-0f54-492a-951f-280a337bae72)

Let's check out the example.

A user in the sales department calls and tells you that she can't get to Server A in the marketing department. You ask her if she can get to Server B in the marketing department, but she doesn't know because she doesn't have rights to log onto that server. What do you do?

You ask the client to go through the four troubleshooting steps that you learned about in the preceding section.

Steps 1 through 3 work, but step 4 fails. By looking at the figure, can you determine the problem? Look for clues in the network drawing.

First, the WAN link between the Lab_A router and the Lab_B router shows the mask as a /27.

You should already know that this mask is 255.255.255.224 and then determine that all networks are using this mask. 

The network address is 192.168.1.0. What are our valid subnets and hosts? 256 – 224 = 32, so this makes our subnets 0, 32, 64, 96, 128, and so on. 

So, by looking at the figure, you can see that subnet 32 is being used by the sales department, the WAN link is using subnet 96, and the marketing department is using subnet 64.

Now you have to determine what the valid host ranges are for each subnet. The valid hosts for the Sales LAN are 33 through 62—the broadcast address is 63 because the next subnet is 64, right? 

For the Marketing LAN, the valid hosts are 65 through 94 (broadcast 95), and for the WAN link, 97 through 126 (broadcast 127).

By looking at the figure, you can determine that the default gateway on the Lab_B router is incorrect. That address is the broadcast address of the 64 subnet, so there's no way it could be a valid host.

![image](https://github.com/user-attachments/assets/f528af4b-4111-44d3-9a40-72b73e2ce36a)

A user in the Sales LAN can't get to ServerB. You have the user run through the four basic troubleshooting steps and find that the host can communicate to the local network but not to the remote network. Find and define the IP addressing problem.

If you use the same steps used to solve the last problem, you can see first that the WAN link again provides the subnet mask to use—/29, or 255.255.255.248. You need to determine what the valid subnets, broadcast addresses, and valid host ranges are to solve this problem.

The 248 mask is a block size of 8 (256 – 248 = 8), so the subnets both start and increment in multiples of 8. By looking at the figure, you see that the Sales LAN is in the 24 subnet, the WAN is in the 40 subnet, and the Marketing LAN is in the 80 subnet.

Can you see the problem yet? The valid host range for the Sales LAN is 25–30, and the configuration appears correct. The valid host range for the WAN link is 41–46, and this also appears correct. The valid host range for the 80 subnet is 81–86, with a broadcast address of 87 because the next subnet is 88. ServerB has been configured with the broadcast address of the subnet.

Now that you can figure out misconfigured IP addresses on hosts, what do you do if a host doesn't have an IP address and you need to assign one? What you need to do is look at other hosts on the LAN and figure out the network, mask, and default gateway. Let's take a look at a couple of examples of how to find and apply valid IP addresses to hosts.

You need to assign a server and router IP addresses on a LAN. The subnet assigned on that segment is 192.168.20.24/29, and the router needs to be assigned the first usable address and the server the last valid host ID. What are the IP address, mask, and default gateway assigned to the server?

To answer this, you must know that a /29 is a 255.255.255.248 mask, which provides a block size of 8. The subnet is known as 24, the next subnet in a block of 8 is 32, so the broadcast address of the 24 subnet is 31, which makes the valid host range 25–30:

- Server IP address: 192.168.20.30
- Server mask: 255.255.255.248
- Default gateway: 192.168.20.25 (router's IP address)

![image](https://github.com/user-attachments/assets/8e48fe2a-4d23-4a8a-af9d-0afc6a8c4964)

Look at the router's IP address on Ethernet0. What IP address, subnet mask, and valid host range could be assigned to the host?

The IP address of the router's Ethernet0 is 192.168.10.33/27. As you already know, a /27 is a 224 mask with a block size of 32. The router's interface is in the 32 subnet. The next subnet is 64, so that makes the broadcast address of the 32 subnet 63 and the valid host range 33–62:

- Host IP address: 192.168.10.34–62 (any address in the range except for 33, which is assigned to the router)
- Mask: 255.255.255.224
- Default gateway: 192.168.10.33

![image](https://github.com/user-attachments/assets/3bfb7db8-4611-482a-ad31-7c9bee495a7f)

The picture shows two routers with Ethernet configurations already assigned.

What are the host addresses and subnet masks of hosts A and B?

RouterA has an IP address of 192.168.10.65/26 and RouterB has an IP address of 192.168.10.33/28. What are the host configurations? RouterA Ethernet0 is in the 192.168.10.64 subnet, and RouterB Ethernet0 is in the 192.168.10.32 network:

- HostA IP address: 192.168.10.66–126
 -HostA mask: 255.255.255.192
- HostA default gateway: 192.168.10.65
- HostB IP address: 192.168.10.34–46
- HostB mask: 255.255.255.240
- HostB default gateway: 192.168.10.33

![image](https://github.com/user-attachments/assets/018e36e8-378a-4562-9946-4531ce4cfa54)

The picture shows two routers; you need to configure the S0/0 interface on RouterA. 

The network assigned to the serial link is 172.16.16.0/22. What IP address can be assigned?

First, you must know that a /22 CIDR is 255.255.252.0, which makes a block size of 4 in the third octet. Because 16 is listed, the available range is 16.1 through 19.254; so, for example, the IP address S0/0 could be 172.16.18.255 because that's within the range.

![image](https://github.com/user-attachments/assets/e8f526a8-8d6c-4267-b097-172474ef89a0)

You have one Class C network ID, and you need to provide one usable subnet per city while allowing enough usable host addresses for each city specified in the picture.

What is your mask?

Actually, this is probably the easiest thing you've done all day! I count 5 subnets needed, and the Chicago office needs 15 users (always look for the network that needs the most hosts). What block size is needed for the Chicago office? 32. (Remember, you cannot use a block size of 16 because you always have to subtract 2!) What mask provides you with a block size of 32? 224. Bingo! This provides 8 subnets, each with 30 hosts.

## Introduction to Network Address Translation (NAT)

Similar to Classless Inter-Domain Routing (CIDR), the original intention for NAT was to slow the depletion of available IP address space by allowing many private IP addresses to be represented by some smaller number of public IP addresses.

Since then, it's been discovered that NAT is also a useful tool for network migrations and mergers, server load sharing, and creating “virtual servers.”

At times, NAT really decreases the overwhelming amount of public IP addresses required in your networking environment. And NAT comes in very handy when two companies that have duplicate internal addressing schemes merge.

NAT is also great to have around when an organization changes its ISP and the networking manager doesn't want the hassle of changing the internal address scheme.

Here's a list of situations when it's best to have NAT on your side:

- You need to connect to the Internet and your hosts don't have globally unique IP addresses.

- You change to a new ISP that requires you to renumber your network.

- You need to merge two intranets with duplicate addresses.

![image](https://github.com/user-attachments/assets/de7d1e36-1cb3-40b7-984d-9276582233fc)

You typically use NAT on a border router.

There are truly some serious snags related to NAT use.

For a visual of the pros and cons linked to using NAT:

![image](https://github.com/user-attachments/assets/a32d8b05-b227-4b5e-9c76-2e19b104d838)

#

### Types of Network Address Translation

**Static NAT (SNAT)** This type of NAT is designed to allow one-to-one mapping between local and global addresses. Keep in mind that the static version requires you to have one real Internet IP address for every host on your network.

**Dynamic NAT (DNAT)** This version gives you the ability to map an unregistered IP address to a registered IP address from a pool of registered IP addresses. You don't have to statically configure your router to map an inside-to-an-outside address as you would using static NAT, but you do have to have enough real, bona fide IP addresses for everyone who's going to be sending packets to and receiving them from the Internet.

**Overloading** This is the most popular type of NAT configuration. Understand that overloading really is a form of dynamic NAT that maps multiple unregistered IP addresses to a single registered IP address—many-to-one—by using different ports. Now, why is this so special? Well, because it's also known as port address translation (PAT). And by using PAT (NAT Overload), you get to have thousands of users connect to the Internet using only one real global IP address. NAT Overload is the real reason we haven't run out of valid IP addresses on the Internet.

#

### NAT Names

Addresses used after NAT translations are called **global addresses**.

These are usually the public addresses used on the Internet, but remember, you don't need public addresses if you aren't going on the Internet.

**Local addresses** are the ones we use before network translation.

So, the inside local address is actually the private address of the sending host that's trying to get to the Internet, while the outside local address is the address of the destination host.

The latter is usually a public address (web address, mail server, and so on) and is how the packet begins its journey.

After translation, the inside local address is then called the **inside global address**, and the outside global address then becomes the name of the destination host.

![image](https://github.com/user-attachments/assets/88e42265-6815-4ac9-918f-01cf4a2fb640)

#

### How NAT Works

![image](https://github.com/user-attachments/assets/67502292-5768-4eda-84f1-ca8c6a538d41)

In the example shown, host 10.1.1.1 sends an outbound packet to the border router configured with NAT. The router identifies the IP address as an inside local IP address destined for an outside network, translates the address, and documents the translation in the NAT table.

The packet is sent to the outside interface with the new translated source address. The external host returns the packet to the destination host, and the NAT router translates the inside global IP address back to the inside local IP address using the NAT table. This is as simple as it gets.

![image](https://github.com/user-attachments/assets/672a1568-fe95-4bd0-a6c0-940077ae46d6)

Let's take a look at a more complex configuration using overloading, or what is also referred to as PAT.

With overloading, all inside hosts get translated to one single IP address, which is why it's called overloading. Again, the reason we have not run out of available IP addresses on the Internet is because of overloading port address translation.

In addition to the inside local IP address and outside global IP address, we now have port numbers. These port numbers help the router identify which host should receive the return traffic.

Port numbers are used at the Transport layer to identify the local host in this example.

If we had to use IP addresses to identify the source hosts, that would be called static NAT, and we would run out of addresses.

PAT allows us to use the Transport layer to identify the hosts, which in turn allows us to use (theoretically) up to 65,000 hosts with one real IP address.

We've been discussing translating IP addresses using some type of network address translation. However, using a router or firewall, you can also perform port forwarding, which is translating the port number of a packet to a new destination.

The destination may be a predetermined network port (using any IP protocol, but typically TCP or UDP ports) on a host within a private network behind a NAT router. Based on the received port number, a remote host can communicate to servers behind the NAT gateway to the local network.
