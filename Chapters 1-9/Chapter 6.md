# Introduction to the Internet Protocol

## Introducing TCP/IP

### A Brief History of TCP/IP

The very first request for comments (RFC) was published in April 1969, which paved the way for today's Internet and its protocols. Each of these protocols is specified in the multitude of RFCs, which are observed, maintained, sanctioned, filed, and stored by the Internet Engineering Task Force (IETF).

TCP first came on the scene in 1974. In 1978, it was divided into two distinct protocols, TCP and IP, and finally documented into an RFC in 1980.Then, in 1983, TCP/IP replaced the Network Control Protocol (NCP) and was authorized as the official data transport means for anything connecting to ARPAnet. ARPAnet was the Internet's ancestor, created by ARPA, the DoD's Advanced Research Projects Agency, again, way back in 1969 in reaction to the Soviets' launching of Sputnik. ARPA was soon redubbed DARPA, and it was divided into ARPAnet and MILNET (also in 1983); both were finally dissolved in 1990.

But contrary to what you might think, most of the development work on TCP/IP happened at UC Berkeley in Northern California, where a group of scientists were simultaneously working on the Berkeley version of UNIX, which soon became known as the BSD, or the Berkeley Software Distribution series of UNIX versions. Of course, because TCP/IP worked so well, it was packaged into subsequent releases of BSD UNIX and offered to other universities and institutions if they bought the distribution tape. Basically, BSD UNIX bundled with TCP/IP began as shareware in the world of academia and, as a result, became the basis of the huge success and exponential growth of today's Internet as well as smaller private and corporate intranets.

As usual, what may have started as a small group of TCP/IP aficionados evolved, and as it did, the US government created a program to test any new published standards and ensure they passed certain criteria. This was to protect TCP/IP's integrity and to ensure that no developer changed anything too dramatically or added any proprietary features. It's this very quality— this open-systems approach to the TCP/IP family of protocols—that pretty much sealed its popularity because it guarantees a solid connection between myriad hardware and software platforms with no strings attached.

#

### The DoD Model and TCP/IP

The DoD model is basically a condensed version of the OSI model; it's composed of four, instead of seven, layers:

- Process/Application layer
- Host-to-Host layer
- Internet layer
- Network Access layer

![image](https://github.com/user-attachments/assets/6a394e82-3734-48ae-8b08-d9ce4ebbe5fe)

The picture shows a comparison of the DoD model and the OSI reference model. As you can see, the two are similar in concept, but each has a different number of layers with different names.

When the different protocols in the IP stack are discussed, two layers of the OSI and DoD models are interchangeable.

In other words, the Internet layer and the Network layer describe the same thing, as do the Host-to-Host layer and the Transport layer. The other two layers of the DoD model, Process/Application and Network Access, are composed of multiple layers of the OSI model.

The Process/Application layer defines protocols for node-to-node application communication and also controls user-interface specifications.

The Host-to-Host layer parallels the functions of the OSI's Transport layer, defining protocols for setting up the level of transmission service for applications.

It tackles issues such as creating reliable end-to-end communication and ensuring the error-free delivery of data. It handles packet sequencing and maintains data integrity.

The Internet layer corresponds to the OSI's Network layer, designating the protocols relating to the logical transmission of packets over the entire network. It takes care of the logical addressing of hosts by giving them an IP address, and it handles the routing of packets among multiple networks.

At the bottom of the DoD model, the Network Access layer monitors the data exchange between the host and the network. The equivalent of the Data Link and Physical layers of the OSI model, the Network Access layer oversees hardware addressing and defines protocols for the physical transmission of data.

The DoD and OSI models are alike in design and concept and have similar functions in similar layers.

![image](https://github.com/user-attachments/assets/07e50f15-3a64-425c-932c-28741c2ad3ad)

The picture shows the TCP/IP protocol suite and how its protocols relate to the DoD model layers.

#

### The Process/Application Layer Protocols

#

### File Transfer Protocol (TCP 20, 21)

File Transfer Protocol (FTP) is the protocol that actually lets you transfer files across an IP network, and it can accomplish this between any two machines that are using it.

But FTP isn't just a protocol; it's also a program. Operating as a protocol, FTP is used by applications. As a program, it's employed by users to perform file tasks by hand.

FTP also allows for access to both directories and files and can accomplish certain types of directory operations, such as relocating files into different directories.

![image](https://github.com/user-attachments/assets/a2ad6963-8b15-4bc9-bca1-49fe454385ca)

Accessing a host through FTP is only the first step, though.

Users must then be subjected to an authentication login that's probably secured with passwords and usernames implemented by system administrators to restrict access.

You can get around this somewhat by adopting the username anonymous—although what you'll gain access to will be limited.

Even when employed by users manually as a program, FTP's functions are limited to listing and manipulating directories, typing file contents, and copying files between hosts. It can't execute remote files as programs.

The problem with FTP is that all data is sent in clear text, just as with Telnet. If you need to make sure your FTP transfers are secure, then you'll use SFTP.

#

### Secure Shell (TCP 22)

The Secure Shell (SSH) protocol sets up a secure Telnet session over a standard TCP/IP connection and is employed for doing things like logging into other systems, running programs on remote systems, and moving files from one system to another.

![image](https://github.com/user-attachments/assets/ccd493e3-7eb3-48f4-ad04-60385271c6c8)

And it does all of this while maintaining a nice, strong, encrypted connection.

You can think of it as the new-generation protocol that's now used in place of rsh and rlogin —even Telnet.

#

### Secure File Transfer Protocol (TCP 22)

Secure File Transfer Protocol (SFTP) is used when transferring files over an encrypted connection.

It uses an SSH session (which was previously covered), which encrypts the connection, and SSH uses port 22, hence the port 22 for SFTP.

Apart from the secure part, it's used just as FTP is—for transferring files between computers on an IP network, such as the Internet.

#

### Telnet (TCP 23)

Telnet is the chameleon of protocols—its specialty is terminal emulation.

It allows a user on a remote client machine, called the Telnet client, to access the resources of another machine, the Telnet server.

Telnet achieves this by pulling a fast one on the Telnet server and making the client machine appear as though it were a terminal directly attached to the local network.

This projection is actually a software shell—a virtual terminal that can interact with the chosen remote host.

![image](https://github.com/user-attachments/assets/258187de-85ba-4888-b8c1-faf69506fa5b)

These emulated terminals are of the text-mode type and can execute refined procedures such as displaying menus that give users the opportunity to choose options and access the applications on the duped server.

Users begin a Telnet session by running the Telnet client software and then logging into the Telnet server.

Telnet offers no security or encryption and is replaced by Secure Shell (SSH) when security across the remote-configuration session is needed or desired.

#

### Simple Mail Transfer Protocol (TCP 25)

Simple Mail Transfer Protocol (SMTP), answering our ubiquitous call to email, uses a spooled, or queued, method of mail delivery.

Once a message has been sent to a destination, the message is spooled to a device—usually a disk.

The server software at the destination posts a vigil, regularly checking the queue for messages.

When it detects them, it proceeds to deliver them to their destination. SMTP is used to send mail; POP3 is used to receive mail.

#

### Domain Name System (TCP and UDP 53)

Domain Name System (DNS) resolves hostnames—specifically, Internet names, such as www.lammle.com —to their corresponding IP addresses.

You don't have to use DNS; you can just type in the IP address of any device you want to communicate with. An IP address identifies hosts on a network and the Internet as well.

However, DNS was designed to make our lives easier. Think about this: What would happen if you wanted to move your web page to a different service provider? The IP address would change, and no one would know what the new one was.

DNS allows you to use a domain name to specify an IP address. You can change the IP address as often as you want and no one will know the difference.

![image](https://github.com/user-attachments/assets/07894171-5d4e-4cb7-9d60-ae48a8cbbad5)

DNS is used to resolve a fully qualified domain name (FQDN)—for example, www.lammle.com or todd.lammle.com —to an IP address. An FQDN, or DNS namespace, is a hierarchy that can logically locate a system based on its domain identifier.


If you want to resolve the name _todd_, you must either type in the FQDN of todd.lammle.com or have a device, such as a PC or router, add the suffix for you.

For example, on a Cisco router, you can use the command IP domain-name lammle.com to append each request with the lammle.com domain. If you don't do that, you'll have to type in the FQDN to get DNS to resolve the name.

An important thing to remember about DNS is that if you can ping a device with an IP address but can't use its FQDN, you might have some type of DNS configuration failure.

#

### Dynamic Host Configuration Protocol/Bootstrap Protocol (UDP 67/68)

