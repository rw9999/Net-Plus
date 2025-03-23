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

Dynamic Host Configuration Protocol (DHCP) assigns IP addresses to hosts with information provided by a server.

It allows easier administration and works well in small to even very large network environments. 

Many types of hardware can be used as a DHCP server, including routers.

DHCP differs from Bootstrap Protocol (BootP) in that BootP assigns an IP address to a host but the host's hardware address must be entered manually in a BootP table.

You can think of DHCP as a dynamic BootP. But remember that BootP is also used to send an operating system that a host can boot from. DHCP can't do that.

But there is a lot of information a DHCP server can provide to a host when the host is requesting an IP address from the DHCP server.

Here's a partial list of the information a DHCP server can provide:

- IP address
- Subnet mask
- Domain name
- Default gateway (routers)
- DNS

A DHCP server can give even more information than this, but the items in the list are the most common.

A client that sends out a DHCP Discover message in order to receive an IP address sends out a broadcast at both layer 2 and layer 3.

The layer 2 broadcast is all Fs in hex, which looks like this: FF:FF:FF:FF:FF:FF. The Layer 3 broadcast is 255.255.255.255, which means all networks and all hosts.

DHCP is connectionless, which means it uses User Datagram Protocol (UDP) at the Transport layer, also known as the Host-to-Host layer.

![image](https://github.com/user-attachments/assets/2884c050-81b0-4cf0-8dfd-383258eb045a)

The following is the four-step process (sometimes known as the DORA process) a client takes to receive an IP address from a DHCP server:

1. The DHCP client broadcasts a DHCP Discover message looking for a DHCP server (port 67).

2. The DHCP server that received the DHCP Discover message sends a unicast DHCP Offer message back to the host.

3. The client then broadcasts to the server a DHCP Request message asking for the offered IP address and possibly other information.

4. The server finalizes the exchange with a unicast DHCP Acknowledgment message.

What happens if you have a few hosts connected together with a switch or hub and you don't have a DHCP server? You can add IP information by hand (this is called static IP addressing), or Windows provides what is called Automatic Private IP Addressing (APIPA), a feature of later Windows operating systems.

With APIPA, clients can automatically self-configure an IP address and subnet mask (basic IP information that hosts use to communicate)

The IP address range for APIPA is 169.254.0.1 through 169.254.255.254.

The client also configures itself with a default Class B subnet mask of 255.255.0.0.

If you have a DHCP server and your host is using this IP address, this means your DHCP client on your host is not working or the server is down or can't be reached because of a network issue.

#

### Trivial File Transfer Protocol (UDP 69)

Trivial File Transfer Protocol (TFTP) is the stripped-down, stock version of FTP, but it's the protocol of choice if you know exactly what you want and where to find it—plus it's easy to use, and it's fast, too.

It doesn't give you the abundance of functions that FTP does.

TFTP has no directorybrowsing abilities; it can do nothing but send and receive files.

![image](https://github.com/user-attachments/assets/f335107a-b09f-491a-b419-1c7390db122f)

This compact little protocol also skimps in the data department, sending much smaller blocks of data than FTP, and there's no authentication as with FTP, so it's insecure. Few sites support it because of the inherent security risks.

#

### Hypertext Transfer Protocol (TCP 80)

All those snappy websites comprising a mélange of graphics, text, links, and so on—the Hypertext Transfer Protocol (HTTP) is making it all possible.

![image](https://github.com/user-attachments/assets/c3675d84-6de0-4308-900e-3c48beeb1160)

It's used to manage communications between web browsers and web servers, and it opens the right resource when you click a link, wherever that resource may actually reside.

#

### Post Office Protocol v3 (TCP 110)

Post Office Protocol (POP) gives us a storage facility for incoming mail, and the latest version is called POP3.

Basically, how this protocol works is when a client device connects to a POP3 server, messages addressed to that client are released for downloading.

It doesn't allow messages to be downloaded selectively, but once they are, the client-server interaction ends, and you can delete and tweak your messages locally at will. 

A newer standard, IMAP, is being used more and more in place of POP3 because of its flexibility and security.

#

### Network Time Protocol (UDP 123)

Network Time Protocol (NTP) works in conjunction with other synchronization utilities to ensure that all computers on a given network agree on the time.

![image](https://github.com/user-attachments/assets/c09ec3f6-48d9-403c-8b59-753d6204e1f9)

It's very important because so many of the transactions done today are time- and date-stamped.

#

### Internet Message Access Protocol (TCP 143)

Because Internet Message Access Protocol (IMAP) makes it so you get control over how you download your mail, with it, you also gain some much-needed security.

It lets you peek at the message header or download just a part of a message.

With it, you can choose to store messages on the email server hierarchically and link to documents and user groups too. IMAP even gives you search commands to use to hunt for messages based on their subject, header, or content.

As you can imagine, it has some serious authentication features—it actually supports the Kerberos authentication scheme that MIT developed. And yes, IMAP4 is the current version.

#

### Simple Network Management Protocol (UDP 161/162)

Simple Network Management Protocol (SNMP) collects and manipulates valuable network information.

It gathers data by polling the devices on the network from a management station at fixed or random intervals, requiring them to disclose certain information.

When all is well, SNMP receives something called a **baseline**—a report delimiting the operational traits of a healthy network.

This protocol can also stand as a watchdog over the network, quickly notifying managers of any sudden turn of events.

The network watchdogs are called agents, and when aberrations occur, agents send an alert called a trap to the management station.

The Network Management System (NMS) polls the agents through a Management Information Base (MIB).

The MIB is basically a database with a set of predefined questions the NMS can ask the agents regarding the health of the device or network.

![image](https://github.com/user-attachments/assets/5113923a-d49d-47d0-8702-741807e08d3c)

In addition, SNMP can help simplify the process of setting up a network as well as the administration of your entire internetwork.

#

### Lightweight Directory Access Protocol (TCP 389)

If you're the system administrator of any decent-sized network, odds are you have a type of directory in place that keeps track of all your network resources, such as devices and users. But how do you access those directories?

LDAP is a protocol used to access and query directory services systems such as Microsoft Active Directory.

And there is a secure version of LDAP called LDAPS that uses port 636.

This protocol standardizes how you access directories, and its first and second inceptions are described in RFCs 1487 and 1777, respectively. There were a few glitches in those two earlier versions, so a third version—the one most commonly used today—was created to address those issues and is described in RFC 3377.

#

### Hypertext Transfer Protocol Secure (TCP 443)

Hypertext Transfer Protocol Secure (HTTPS) is a secure version of HTTP that arms you with a whole bunch of security tools for keeping transactions between a web browser and a server secure.

It's what your browser needs to fill out forms, sign in, authenticate, and encrypt an HTTP message when you make a reservation or buy something online. The Chromium browser actually requires HTTPS encryption or it will notify you that there is no privacy.

Both SSH (port 22) and HTTPS (port 443) are used to encrypt packets over your intranet and the Internet.

#

### Transport Layer Security/Secure Sockets Layer (TCP 995/465)

Both Transport Layer Security (TLS) and its forerunner, Secure Sockets Layer (SSL), are cryptographic protocols that come in really handy for enabling secure online data-transfer activities like browsing the web, instant messaging, Internet faxing, and so on.

They both use X.509 certificates and asymmetric cryptography to authenticate to the host they are communicating with and to exchange a key. 

This key is then used to encrypt data flowing between the hosts.

This allows for data/message confidentiality, message integrity, and message authentication.

Even though I listed TLS/SSL as using ports 995 and 465, which is true if you're using Gmail, TLS/SSL isn't tied down to any certain ports and can use various different ones.

#

### Server Message Block (TCP 445)

Server Message Block (SMB) is used for sharing access to files and printers and other communications between hosts on a Microsoft Windows network.

SMB runs mostly on TCP port 445 now, but SMB can also run on UDP port 137 and 138 and on TCP port 137 and 139 using NetBIOS.

#

### Syslog (UDP 514)

Reading system messages from a switch's or router's internal buffer is the most popular and efficient method of seeing what's going on with your network at a particular time.

But the best way is to log messages to a syslog server, which stores messages from you and can even time-stamp and sequence them for you, and it's easy to set up and configure.

Syslog allows you to display, sort, and even search messages, all of which makes it a really great troubleshooting tool. The search feature is especially powerful because you can use keywords and even severity levels.

Plus, the server can email admins based on the severity level of the message.

Network devices can be configured to generate a syslog message and forward it to various destinations. 

These four examples are popular ways to gather messages from Cisco devices:

- Logging buffer (on by default)
- Console line (on by default)
- Terminal lines (using the terminal monitor command)
- Syslog server

![image](https://github.com/user-attachments/assets/d5d4d942-c821-49cb-8149-21835a0b7a8a)

Informational is the default and will result in all messages being sent to the buffers and console.

#

### SMTPS (TCP 587)


Simple Mail Transfer Protocol (SMTP), answering our ubiquitous call to email, uses a spooled, or queued, method of mail delivery using TCP port 25. However, this email is sent in clear text, and some email servers can still use this.

SMTPS encrypts email when it is sent, and most email servers use or can use port 587 to send email now; some even demand it. This port, coupled with TLS encryption, will ensure that email is securely sent, following the guidelines set out by the IETF of course.

#

### Lightweight Directory Access Protocol over SSL (TCP 636)

Taking off from our discussion earlier on TCP 389 LDAP, understand that this traffic is transmitted unsecured. Bring in LDAP over SSL TCP 636, which is the suggested use of LDAP in today's networks. To make this function correctly, you need to install a proper certificate from a Microsoft certification authority (CA) or other type of CA.

#

### IMAP over SSL (TCP 993)

Because Internet Message Access Protocol (IMAP) makes it so you get control over how you download your mail, with it, you also gain some much-needed security.

However, IMAP over SSL means that IMAP traffic travels over a security socket to a security port, using TCP port 993 usually.

#

### POP3 over SSL (TCP 995)

As discussed previously. Post Office Protocol (POP) gives us a storage facility for incoming mail, and the latest version of POP is called POP3.

This email is probably downloaded in clear text. 

Either POP3 over SSL or IMAP over SSL is more commonly used to encrypt emails being downloaded from servers today.

#

### Structured Query Language (SQL) Server (TCP 1433)

Microsoft SQL Server has grown from a simple relational database engine to a multipurpose enterprise-level data platform.

TCP port 1433 is the default port for SQL Server, and it's also the official Internet Assigned Number Authority (IANA) socket number for SQL Server. 

Client systems use TCP 1433 to connect to the database engine.

#

### SQLnet (TCP 1521)

SQLnet (also referred to as SQL*Net and Net8) is Oracle's networking software that allows remote data access between programs using Oracle Database.

Applications and databases are shared with different machines and continue communicating as if they were local.

SQLnet is based on Oracle's Transparent Network Substrate (TNS), a network technology that provides a generic interface to all network protocols; however, this is no longer needed today since we have TCP/IP.

SQL*Net is used by both client and server to communicate with one another. Without the Net8 layer acting as the interpreter, the client and server processes cannot interconnect (notice how I used all three names in this section—and all define the same thing).

#

###  MySQL (TCP 3306)

MySQL is a relational database management system based on SQL, or Structured Query Language. 

This is used within companies for data warehousing, e-commerce, logging applications, and more. 

The most common use for MySQL is for the purpose of a cloud-based database.

#

### Remote Desktop Protocol (TCP 3389)

Remote Desktop Protocol (RDP) is a proprietary protocol developed by Microsoft. 

It allows you to connect to another computer and run programs.

RDP operates like Telnet, except instead of getting a command-line promptas you do with Telnet, you get the actual graphical user interface (GUI) of the remote computer.

Clients exist for most versions of Windows, and Macs now come with a preinstalled RDP client.

Microsoft currently calls its official RDP server software Remote Desktop Services; it was called Terminal Services for a while. Microsoft's official client software is called Remote Desktop Connection (RDC), which was called Terminal Services Client in the past.

RDP is an excellent tool for remote clients, allowing users to connect to their work computer from home, for example, and get their email or perform work on other applications without running or installing any of the software on their home computer.

#

### SIP (VoIP) (TCP or UDP 5060/TCP 5061)

