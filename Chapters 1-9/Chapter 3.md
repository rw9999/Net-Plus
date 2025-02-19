# Networking Connectors and Wiring Standards

## Physical Media

Most of us rely on wireless networking methods that work using technologies such as Wi-Fi, radio frequency, and infrared, but even wireless depends on a physical media backbone in place somewhere. And the majority of installed local area networks (LANs) today communicate via some kind of cabling, so let's take a look at the three types of popular cables used in modern networking designs:

- Coaxial

- Twisted-pair

- Fiber optic

### Coaxial Cable

Coaxial cable, referred to as coax, contains a center conductor made of copper that's surrounded by a plastic jacket with a braided shield over it.

A type of plastic such as polyvinyl chloride (PVC) or fluoroethylene propylene (FEP, commonly known as Teflon) covers this metal shield.

The Teflon-type covering is frequently referred to as a **plenum-rated coating**, and it's definitely expensive but often mandated by local or municipal fire code when cable is hidden in walls and ceilings. Plenum rating applies to all types of cabling and is an approved replacement for all other compositions of cable sheathing and insulation like PVC-based assemblies.

The difference between plenum and non-plenum cable comes down to how each is constructed and where you can use it.

Many large multistory buildings are designed to circulate air through the spaces between the ceiling of one story and the floor of the next; this space between floors is referred to as the **plenum**.

And it just happens to be a perfect spot to run all the cables that connect the legions of computers that live in the building.

Unless there's a fire—if that happens, the non-plenum cable becomes a serious hazard because its insulation gives off poisonous smoke that gets circulated throughout the whole building. Plus, non-plenum cables can actually become “wicks” for the fire, helping it quickly spread from room to room and floor to floor.

Because it's a great goal to prevent towering infernos, the National Fire Protection Association (NFPA) demands that cables run within the plenum have been tested and guaranteed as safe. They must be fire retardant and create little or no smoke and poisonous gas when burned. This means you absolutely can't use a non-plenum-type cable in the plenum, but it doesn't mean you can't use it in other places where it's safe. And because it's a lot cheaper, you want to use it where you can.

Thin Ethernet, or thinnet or 10Base2, is a thin coaxial cable. It is the same as thick coaxial cable, except it's only about 5 mm, or 2/10″, diameter coaxial cable. Thin Ethernet coaxial cable is Radio Grade 58, or just RG-58.

![image](https://github.com/user-attachments/assets/c70dde51-4d09-461e-9532-6297ce1e66b8)

The picture shows an example of a thinnet. This connector resembles the coaxial connector used for cable TV, an **F-type connector**.

If you use thinnet cable, you've got to use Bayonet Neill– Concelman (BNC) connectors to attach stations to the network.

![image](https://github.com/user-attachments/assets/c7061763-148b-4ffb-89b0-fdefc4bd3213)

and you have to use 50 ohm terminating resistors at each end of the cable to achieve the proper performance. You can attach a BNC connector to the cable with a crimper that looks like a weird pair of pliers and has a die to crimp the connector. A simple squeeze crimps the connector to the cable.

You can use a BNC coupler to connect two male connectors together or two female connectors together.

You don't have to know much about most coax cable types in networks anymore, especially the thinnet and thicknet types of coaxial cable. Thicknet was known as RG-8 and was about 1/2″ in diameter, also requiring 50 ohm terminating resistors on each end of the cable. Nowadays, we use 75-ohm coax for cable TV; using coax in the Ethernet LAN world is pretty much a thing of the past, but we do use them for high-bandwidth runs in our data centers. RG-6, or CATV coax, is used in our broadband world.

![image](https://github.com/user-attachments/assets/5b7bc896-e657-4d1f-9a3d-eb21bec3ae74)

The picture lists some specifications for the different types of coaxial cable, but understand that we use only RG-59 and RG-6 in today's world.

### F-type

The F connector, or F-type connector, is a form of coaxial connector that is used for cable TV. It has an end that screws to tighten the connector to the interface. It resembles the RG-58 mentioned earlier in this section.

An advantage of using coax cable is the braided shielding that provides resistance to electronic pollution like **electromagnetic interference (EMI)**, **radio frequency interference (RFI)**, and other types of stray electronic signals that can make their way onto a network cable and cause communication problems.

### Twisted-Pair Cable

Twinaxial cabling is used for short-distance high-speed connections such as 10 and 40G Ethernet connections in a data center.

Twinaxial is also known as **twinax**.

The advantage of using twinaxial cable is that there are significant cost savings over fiber-optic cabling since twinaxial cables are copper-based. If your distance is 10 meters or less, using these cables can be a considerable cost savings.

Also in the twinaxial family is direct attach copper (DAC) cable. DAC has connectors at either end of a fixed-length ~26-28 AWG twinaxial copper cable that allows direct communication between devices over copper wire. Like shielded twisted pair (SSTP), DAC uses electromagnetic shielding around the copper cable to increase speeds and to keep communication reliable.

### Ethernet Cable Descriptions

Ethernet cable types are described using a code that follows this format: N <Signaling> X.

The N refers to the signaling rate in megabits per second.

<Signaling> stands for the signaling type—either baseband or broadband.

The X is a unique identifier for a specific Ethernet cabling scheme.

Here's a common example: 100BaseX. The 100 tells us that the transmission speed is 100 Mb, or 100 megabits. The X value can mean several different things; for example, a T is short for twisted-pair. This is the standard for running 100-megabit Ethernet over two pairs (four wires) of Category 5, 5e, 6, 6a, 7, and 8 UTP.

So why are the wires in this cable type twisted? Because when electromagnetic signals are conducted on copper wires in close proximity—like inside a cable—it causes interference called **crosstalk**. Twisting two wires together as a pair minimizes interference and even protects against interference from outside sources.

This cable type is the most common today for the following reasons:

- It's cheaper than other types of cabling.

- It's easy to work with.

- It allows transmission rates that were impossible 10 years ago.

Category is often shortened to Cat. Today, any cable installed should be a minimum of Cat 5e because some cable is now certified to carry bandwidth signals of 350 MHz or beyond. This allows unshielded twisted-pair cables to exceed speeds of 1 Gbps—fast enough to carry broadcast-quality video over a network.

UTP cable is rated in these categories:

**Category 1** Two twisted wire pairs (four wires). It's the oldest type and is only voice grade—it isn't rated for data communication. People refer to it as plain old telephone service (POTS). Before 1983, this was the standard cable used throughout the North American telephone system. POTS cable still exists in parts of the public switched telephone network (PSTN) and supports signals limited to the 1 MHz frequency range.

**Category 2** Four twisted wire pairs (eight wires). It handles up to 4 Mbps, with a frequency limitation of 10 MHz, and is now obsolete.

**Category 3** Four twisted wire pairs (eight wires) with three twists per foot. This type can handle transmissions up to 16 MHz. It was popular in the mid-1980s for up to 10 Mbps Ethernet, but it's now limited to telecommunication equipment and, again, is obsolete for networks.

**Category 4** Four twisted wire pairs (eight wires), rated for 20 MHz; also obsolete.

**Category 5** Four twisted wire pairs (eight wires), used for 100BaseTX (two pair wiring) and rated for 100 MHz. But why use Cat 5 when you can use Cat 5e for the same price? I am not sure you can even buy plain Cat 5 anymore! Using Cat 6 is an option, but it's slightly harder to install due to its size compared to 5e.

**Category 5e (Enhanced)** Four twisted wire pairs (eight wires), recommended for 1000BaseT (four pair wiring) and rated for 100 MHz but capable of handling the disturbance on each pair that's caused by transmitting on all four pairs at the same time—a feature that's needed for Gigabit Ethernet. Any category below 5e shouldn't be used in today's network environments.

![image](https://github.com/user-attachments/assets/feb21ad4-26d3-4c32-b3e9-86138d24fb50)

**Category 6** Four twisted wire pairs (eight wires), used for 1000BaseTX (two pair wiring) and rated for 250 MHz. Cat 6 became a standard in June 2002. You would usually use it as riser cable to connect floors. If you're installing a new network in a new building, there's no reason to use anything but Category 6 UTP cabling and running fiber runs between floors.

**Category 6A (Augmented)** Characterized to 500 MHz with improved crosstalk characteristics, which allows 10GBaseT to be run for up to 100 meters (basic Cat 6 cable has a reduced maximum length when used for 10GBaseT). The most important point is a performance difference between Electronic Industries Alliance and Telecommunications Industry Association (EIA/TIA) component specifications for the NEXT (near-end crosstalk) transmission parameter. Running at a frequency of 500 MHz, an ISO/IEC Cat 6A connector provides double the power (3db) of a Cat 6A connector that conforms with the EIA/TIA specification. Note that 3 dB equals a 100 percent increase of a near-end crosstalk noise reduction.

**Category 7** Allows 10 Gigabit Ethernet over 100 meters of copper cabling. The cable contains four twisted copper wire pairs, just like the earlier standards.

**Category 8** Developed to address the ever-increasing speed of Ethernet and added support for 25G and 40G transmission with a distance of 30 meters, which is perfect for data center deployments.

### Connecting UTP

BNC connectors won't fit very well on UTP cable, so you need to use a **registered jack (RJ)** connector, which you're familiar with because most telephones connect with them.

The connector used with UTP cable is called RJ-11 for phones that use four wires; RJ-45 has four pairs (eight wires)

![image](https://github.com/user-attachments/assets/3175e3ba-c091-4af5-aae3-53c1fc450db6)

Most of the time, UTP uses RJ connectors, and you use a crimper to attach them to a cable, just as you would with BNC connectors. The only difference is that the die that holds the connector is a different shape.

Higher-quality crimping tools have interchangeable dies for both types of cables. We don't use RJ-11 for LANs, but we do use them for our home Digital Subscriber Line (DSL) connections.

![image](https://github.com/user-attachments/assets/787609ba-4b34-4bfd-a496-4158470a0bd2)

RJ-11 uses two wire pairs, and RJ-45 uses four wire pairs.

There's one other type of copper connector, called the RJ-48c, which looks exactly like an RJ-45 connector. This plug is similar to the RJ-45 in that it has four wire pairs, but they are wired differently and used for different circumstances.

RJ-45 is mainly used in LANs with short distances (typically up to 100 meters), where the RJ-48c wiring type would be used with a T1 connection, which is a long-distance wide area network (WAN).

In addition, to protect the signal in an RJ-48c, the wires are typically shielded, whereas the RJ-45 uses unshielded wiring.

### Fiber-Optic Cable

Because fiber-optic cable transmits digital signals using light impulses rather than electricity, it's immune to EMI and RFI.

Fiber cable allows light impulses to be carried on either a glass or a plastic core. Glass can carry the signal a greater distance, but plastic costs less.

Whichever the type of core, it's surrounded by a glass or plastic cladding with a different refraction index that reflects the light back into the core. Around this is a layer of flexible plastic buffer that can be wrapped in an armor coating that's usually Kevlar, which is then sheathed in PVC or plenum.

The cable itself comes in either single-mode fiber or multimode fiber; the difference between them is in the number of light rays (the number of signals) they can carry.

Multimode fiber is most often used for shorter distance applications and single-mode fiber for spanning longer distances.

Pros of fiber-optic cable:

- It's completely immune to EMI and RFI.
- It can transmit up to 40 kilometers (about 25 miles).

Cons of fiber-optic cable:

-  It's difficult to install.

- It's more expensive than twisted-pair.

- Troubleshooting equipment is more expensive than twisted-pair test equipment.

- It's harder to troubleshoot.

### Single-Mode Fiber

Single-mode fiber-optic cable (SMF) is a very high-speed, long-distance media that consists of a single strand—sometimes two strands—of glass fiber that carries the signals.

Light-emitting diodes (LEDs) and laser are the light sources used with SMF.

The light source is transmitted from end to end and pulsed to create communication. This is the type of fiber cable employed to span really long distances because it can transmit data up to 90 times farther than multimode fiber at a faster rate. That is 40 to 80 kilometers depending on the transceiver being used.

Clearly, because the transmission media is glass, the installation of SMF can be a bit tricky. Yes, there are outer layers protecting the glass core, but the cable still shouldn't be crimped or pinched around any tight corners.

### Multimode Fiber

Multimode fiber-optic cable (MMF) also uses light to communicate a signal, but with it, the light is dispersed on numerous paths as it travels through the core and is reflected back.

A special material called **cladding** is used to line the core and focus the light back onto it.

MMF provides high bandwidth at high speeds over medium distances (up to about 3,000 feet), but beyond that it can be really inconsistent. This is why MMF is most often used within a smaller area of one building; SMF can be used between buildings.

MMF is available in glass or in a plastic version that makes installation a lot easier and increases the installation's flexibility.

## Fiber Connectors

Each fiber connector has a benefit or purpose in a fiberoptic installation. It is important to know the visual differences between the fiber connectors and their respective names.

### Straight Tip (ST)

![image](https://github.com/user-attachments/assets/75ebfef7-cef8-4004-83af-f08dce87946d)

The straight tip (ST) connector was originally designed by AT&T for fiber-optic cables. It is commonly used with single-mode fiber.

The connector is one of the most popular connectors to date with fiber optics for WAN connectivity on SMF. The cable connector can be found in both SMF and MMF cable installations.

The cable operates similar to a BNC connector; it is a bayonet-style mechanism that you twist and lock into position. The benefit to this cable is that it will not come loose over time because of the positive locking mechanism.

### Subscriber Connector (SC)

The subscriber (or square) connector (SC) is a square connector with a floating ferrule that contains the fiber-optic cable.

![image](https://github.com/user-attachments/assets/778d81d3-ef2a-4f22-a611-fd1ba9db58e6)

The cable comes with a plastic clip that holds the transmit and receive cables secure for insertion.

These clips generally allow you to disassemble the cable ends so transmit and receive can be swapped.

It can be found in SMF and MMF installations, but it is most popular with MMF installations. 

The SC connector is larger than most modern connectors, so it is starting to be replaced in new installations. 

The cable operates with a push-on/pull-off mating mechanism.

### Small Form Factor Fiber-Optic Connectors

Another fiber-optic connector is the small form factor (SFF) style of connector, which allows more fiber-optic terminations in the same amount of space than its standard-sized counterparts.

The three most popular versions are the mechanical transfer registered jack (MT-RJ or MTRJ), designed by AMP, the local connector (LC), designed by Lucent, and the multi-fiber push on (MPO) developed and licensed by NTT Group.

The MT-RJ fiber-optic connector was the first small form factor fiber-optic connector to be widely used, and it's only one-third the size of the SC and ST connectors it most often replaces.

It offers these benefits:

- Small size
- TX and RX strands in one connector
- Keyed for single polarity
- Pre-terminated ends that require no polishing or epoxy
- Easy to use

![image](https://github.com/user-attachments/assets/55fe5e83-3d1a-4735-8cfb-df7fc97a82d2)

A sample MT-RJ fiber-optic connector ^

The local connector (LC) resembles an RJ-style connector; it has a springloaded detent similar to the RJ connector that allows it to be held in place.

The LC connector has become a popular cable connector because of its size; this allows greater density of ports on a switch. The connector is commonly found on MMF and SMF optic cables.

The cable cannot be disassembled like the SC connector, so transmit and receive fiber lines cannot be swapped side to side.

LC is a newer style of SFF fiber-optic connector that's pulling ahead of the MT-RJ. It's especially popular for use with Fibre Channel adapters (FCs) and is a standard used for fast storage area networks and Gigabit Ethernet adapters.

FC is a very high-speed data transfer protocol (usually running at 2 Gbps, 4 Gbps, 8 Gbps, 16 Gbps, and 32 Gbps) that is different than any other type of storage transfer protocol. 

FC delivers what is called raw black date, in order and lossless. FC connects data storage called storage area networks (SANs).

What is interesting about Fibre Channel networks is that the FC switches create a large, switched fabric, and the switches in an FC network operate in unison as one big switch.

FC transceivers and Ethernet optical modules use different protocols. The FC transceiver belongs to the Fibre Channel protocol, which does not follow the OSI model. Ethernet optical modules use the IEEE 802.3 standard for packet-based physical communication in an LAN.

![image](https://github.com/user-attachments/assets/1ebb8774-3816-4d93-ab9c-bb78360a74e4)

A sample LC fiber-optic connector ^

The LC fiber-optic connector has similar advantages to MT-RJ and other SFF-type connectors, but it's easier to terminate. It uses a ceramic insert just as standard-sized fiber-optic connectors do.

The multi-fiber push on connector is yet another SFF high-density fiberoptic connector that provides 2, 8, 12, or 24 fiber-optic connections in a single connector.

![image](https://github.com/user-attachments/assets/17f80318-46a2-4b0d-ac81-284927414790)

The MPO connector typically fans out from a single connector to multiple LC connectors to provide 10 Gbps to 100 Gbps for each connection. This provides a single interface from a fiber distribution panel to multiple transceivers in a network switch.

### APC vs. UPC

The **angled physical contact (APC)** and **ultra physical contact (UPC)** is a not a connector; it is a finish on the end of the connector to curtain optical decibel loss.

The choice between APC and UPC can make a pretty big difference on how your network will perform.

![image](https://github.com/user-attachments/assets/812c0435-b91c-432b-9125-101372f96cd7)

The ultra-polished connector looks like what you'd expect to find in a fiberoptic end. The cut is perfectly straight.

With the UPC, the light is reflected back down to the core of the fiber cable, which causes a loss of decibels called a return loss because the angled connector causes the light to reflect into the cladding—the thick sides of the glass instead of the core. But the APC doesn't cause nearly as much decibel loss when using this type of connector.

You can tell the difference between an APC and UPC connector finish by looking at the color of the plastic that composes the connector. A green connector has an APC finish on the connector end, and a blue connector has a UPC finish on the connector end.

### Fiber Distribution Panel

Fiber distribution panels (FDPs) are termination and distribution systems for fiber-optic cable facilities.

They consist of a cable management tray and a splice drawer. They are designed for central offices, remote offices, and LANs using fiber-optic facilities.

### Fiber-Optic Transceivers

Fiber-optic transceivers can be either unidirectional (simplex) or bidirectional (duplex).

**Unidirectional** An optic fiber cable is unidirectional when it can only transmit data in one direction, either from the source to the destination or vice versa.

**Bidirectional** Bidirectional optic fiber cable is capable of transmitting data in both directions simultaneously. Bidirectional communication is possible if the cable used is following the EEE 802.3ah 1000BASE-BX10-D and 1000BASE-BX10-U standards. The communication over a single strand of fiber is achieved by separating the transmission wavelength of the two devices.

![image](https://github.com/user-attachments/assets/ffa60a48-8038-4069-8e27-4f33eed186f5)

### Transceivers

A transceiver is a device made up of both a transmitter and a receiver, which are combined and share common circuitry or a single housing.

The term applies to wireless communications devices such as cellular telephones, cordless telephone sets, handheld two-way radios, and mobile two-way radios. Occasionally, the term is used in reference to transmitter and receiver devices in cable or optical fiber systems.

**SFP+** The small form-factor pluggable (SFP) is a compact pluggable optical module transceiver used for both telecommunication and data communications applications. The **enhanced small form-factor pluggable (SFP+)** transceiver is an enhanced version of the SFP that supports data rates up to 16 Gbit/s.

**QSFP** The quad small form-factor pluggable (QSFP) is another compact, hot-pluggable transceiver used for data communications applications. It interfaces networking hardware (such as servers and switches) to a fiberoptic cable or active or passive electrical copper connection. It allows data rates from 4x1 Gbps for QSFP and 4x10 Gbit/s for QSFP+ to the highest rate of 4x28 Gbit/s known as QSFP28 used for 100 Gbit/s links.

### Media Converters

Sometimes, you'll need to convert from one media type to another. Maybe you need to go from one mode of fiber to another mode, or in an even more extreme case, you need to go from fiber to Ethernet.

**Single-Mode Fiber to Ethernet** These devices accept a fiber connector and an Ethernet connector and convert the signal from Ethernet and singlemode fiber.

![image](https://github.com/user-attachments/assets/d99c1888-32c9-48c4-93f4-10fcac2bb8f9)

**Multimode Fiber to Ethernet** These devices accept a fiber connector and an Ethernet connector and convert the signal from Ethernet and multimode fiber.

![image](https://github.com/user-attachments/assets/ccf89306-5a46-4936-b87a-42227295be9a)

**Fiber to Coaxial** These devices accept a fiber connector and a coaxial connector and convert digital signals from optical to coax.

![image](https://github.com/user-attachments/assets/ec3320a9-8fe2-45cd-b36f-cc3a6edfc34a)

**Single-Mode to Multimode Fiber** These devices accept a single-mode fiber connector and a multimode fiber connector and convert the signals between the two.

![image](https://github.com/user-attachments/assets/a4b1698c-f28f-43d9-82f0-d15e8cf39399)

### Serial Cables

Except for multimode fiber, all the cable varieties I've talked about so far are considered serial cable types.

In network communications, **serial** means that one bit after another is sent out onto the wire or fiber and interpreted by a network card or other type of interface on the other end.

Each 1 or 0 is read separately and then combined with others to form data. 

This is very different from parallel communication, where bits are sent in groups and have to be read together to make sense of the message they represent.

**RS-232**

Recommended Standard 232 (RS-232) was a cable standard commonly used for serial data signals connecting the data Terminal Equipment (DTE) and the Data Communications Equipment (DCE), such as a computer's serial port to an external modem.

![image](https://github.com/user-attachments/assets/5dcb7631-6118-4713-84a4-f0ee6772952a)

These cables normally connect to a connector on the device called a DB-9.

Because laptops don't even come with these types of connectors anymore, they've pretty much been replaced by things like USB and USB-C.

**DB-25**

The D series of
connectors was invented by ITT Cannon in 1952, and the D was followed by A, B, C, D, or E, which described the shell size, and then the numbers of pins or sockets. DB-25 tells us we have 25 pins in a “B” size shell. RS-232 devices usually used the DB-25 connector, but today we don't use RS-232 or DB-25, and we rarely use a DB-9, which used to be used for Cisco console cables but has mostly been replaced by USB.

**Universal Serial Bus**

Universal Serial Bus (USB) is now the built-in serial bus du jour of most motherboards. You usually get a maximum of 4 external USB interfaces, but add-on adapters can take that up to as many as 16 serial interfaces. USB can actually connect a maximum of 127 external devices, and it's a much more flexible peripheral bus than either serial or parallel.

When connecting USB peripherals, you've got to connect them either directly to one of the USB ports on the PC or to a USB hub that is connected to one of those USB ports.

![image](https://github.com/user-attachments/assets/35c33e79-cb2d-4b60-8b5f-89c637d3fc06)

Hubs can be chained together to provide multiple USB connections, but even though you can connect up to 127 devices, it's really not practical to go there.

## Cable Properties

We use so many different types of cables in a network because each type has its own properties that specifically make it the best to use for a particular area or purpose. Different types vary in transmission speeds, distance, duplex, noise immunity, and frequency.

### Transmission Speeds

Based on the type of cable or fiber you choose and the network that it's installed in, network administrators can control the speed of a network to meet the network's traffic demands.

Admins usually permit, or would like to have, transmission speeds of up to 10 Gbps or higher on the core areas of their networks that connect various network segments.

In the distribution and access areas, where users connect to switches, it's typically 100/1000 Mbps per connection, but transmission speeds are creeping up because the traffic demand is getting higher.

### Distance

Deciding factors used in choosing what cable type to use often come down to the topology of a network and the distance between its components.

Some network technologies can run much farther than others without communication errors, but all network communication technologies are prone to **attenuation**—the degradation of a signal due to the medium itself and the distance signals have to travel.

Some cable types suffer from attenuation more than others.

### Duplex

All communications are either half-duplex or full-duplex. The difference is whether the communicating devices can “talk” and “listen” at the same time.

During half-duplex communication, a device can either send communication or receive communication, but not both at the same time. Think walkie-talkie—when you press the button on the walkie-talkie, you turn the speaker off and you can't hear anything the other side is saying.

In full-duplex communication, both devices can send and receive communication at the same time. This means that the effective throughput is doubled and communication is much more efficient. Full duplex is typical in most of today's switched networks.

### Noise Immunity (Security, EMI)

Anytime electrons are pushed through two wires next to each other, a magnetic current is created. 

And we can create a current in the wires. This is good because without **magnetic flux**, we wouldn't be using computers—the power that surges through them is a result of it. 

The bad news is that it also creates two communications issues.

First, because the wire is creating a current based on the 1s and 0s coursing through it, with the right tools in hand, people can read the message in the wire without cutting it or even removing the insulation. You've heard of this —it's called **tapping** the wire, and it's clearly a valid security concern.

In ancient history, high-security installations like the Pentagon actually encased communication wires in lead shielding to prevent them from being tapped. STP wires make tapping a little harder, but not hard enough.

The best way to solve the magnetic-flux problem caused by electricity is to not use these wires at all. As I said, fiber-optic cables carry the signal as light on a glass or a really pure plastic strand, and light is not susceptible to magnetic flux, making fiber optics a whole lot harder to tap.

It's still not impossible—you can do it at the equipment level, but you have to actually cut and then repair the cable to do that, which isn't likely to go unnoticed.

The second magnetic-flux issue comes from the outside in instead of from the inside out. Because wires can take on additional current if they're near any source of magnetism, you've got to be really careful where you run your cables.

You can avoid EMI by keeping copper cables away from all powerful magnetic sources like electric motors, speakers, amplifiers, fluorescent light ballasts, and so on. Just keep them away from anything that can generate a magnetic field.

### Frequency

Each cable type has a specified maximum frequency that gives you the transmission bandwidth it can handle. 

Cat 5e cable is tested to 100 MHz maximum frequency and can run 1 Gbps signals for relatively short distances. That's maxing it out, but it's still good for connecting desktop hosts at high speeds. 

On the other hand, Cat 6 is a 250 MHz cable that can handle 1 Gbps data flow all day long with ease. Cat 6 has a lot more twists and thicker cables, so it's best used when connecting floors of a building; however, be sure to check out Cat 7 and 8, which is more of our future cabling.

Although a signal is measured as bandwidth, the capacity to carry the signal in a cable is measured as frequency.

## Wiring Standards

Ethernet cabling is an important thing to understand, especially if you're planning to work on any LAN. 

There are different types of wiring standards available:

- T568A
- T568B
- Straight-through
- Crossover
- Rolled/rollover

### T568A vs. T568B

If you look inside a network cable, you'll find four pairs of wires twisted together to prevent crosstalk; they're also twisted like this to help prevent EMI and tapping. 

The same pins have to be used on the same colors throughout a network to receive and transmit, but how do you decide which color wire goes with which pin?

Two wiring standards have surfaced that have been agreed on by more than 60 vendors, including AT&T, 3Com (acquired by HP), and Cisco, although there isn't 100% agreement. In other words, over the years, some network jacks have been pinned with the T568A standard, and some have used the T568B standard.

**T568A** By looking at the picture, you can see that the green pair is used for pins 1 and 2 but the orange pair is split to pins 3 and 6, separated by the blue pair.

![image](https://github.com/user-attachments/assets/591e09db-37ca-4819-9005-8530ab06c056)

**T568B** Now take a look at the picture below. The orange pair is pins 1 and 2, and the green pair is pins 3 and 6, again separated by the blue pair.

![image](https://github.com/user-attachments/assets/7c3fd81b-54f0-4467-8350-3e18debf93d8)

Note that the only difference between T568A and T568B is that pairs 2 and 3 (orange and green) are swapped. Also, you can use a UTP coupler to connect two RJ-45 connectors together to lengthen a cable or to make a straight-through cable into a crossover, and vice versa.

This only leaves the wire pairs to connect to pins 1, 2, 3, and 6 for data. Remember, if we connect the green-white, green, orange-white, and orange wires to pins 1, 2, 3, and 6, respectively, on both sides of the cable, we're using the T568A standard and creating the kind of straight-through cable that's regularly implemented as a regular patch cable for most networks. 

On the other hand, if we switch from pin 1 to pin 3 and from pin 2 to pin 6 on one side only, we've created a crossover cable for most networks.

### Straight-Through Cable

The straight-through cable is used to connect a host to a switch or hub or a router to a switch or hub.

Four wires are used in straight-through cable to connect 10/100 Ethernet devices.

![image](https://github.com/user-attachments/assets/a8aec32b-ed1b-4082-8694-745e7cb349af)

Notice that only pins 1, 2, 3, and 6 are used. Connect 1 to 1, 2 to 2, 3 to 3, and 6 to 6 and you'll be up and networking in no time. Just remember that this would be a 10/100 Ethernet-only cable, so it wouldn't work with 1000 Mbps or greater Ethernet.

### Crossover Cable

The same four wires are used in this cable, and just as with the straightthrough cable, you simply connect the different pins together. 

Crossover cables can be used to connect these devices:

- Switch to switch

- Hub to hub

- Host to host

- Hub to switch

- Router direct to host

![image](https://github.com/user-attachments/assets/5bfdeeed-6313-4737-ad9b-09daf0f49925)

A crossover cable is typically used to connect two switches, but it can also be used to test communications between two workstations directly, bypassing the switch.

A crossover cable is used only in Ethernet UTP installations. You can connect two workstation NICs or a workstation and a server NIC directly with it.

If you are trying to match the straight-through and crossover cables with the T568A and T568B standard, here is how it would look:

- T568A+T568A = straight-through

- T568B+T568B = straight-through

- T568A+T568B = crossover

Use a cable tester to make sure that what you're dealing with is in fact a crossover cable.

![image](https://github.com/user-attachments/assets/4c42dcea-fb27-4cf0-877d-48d3305b6cf5)

### UTP Gigabit Wiring (1000BaseT)

In the previous examples of 10BaseT and 100BaseT UTP wiring, only two wire pairs were used, but that's just not good enough for Gigabit UTP transmission.

![image](https://github.com/user-attachments/assets/b02c34d7-c936-492f-9596-c8d54e3c5bf3)

1000BaseT UTP wiring requires four wire pairs and uses more advanced electronics so that every pair in the cable can transmit simultaneously. Even so, Gigabit wiring is almost identical to my earlier 10/100 example, except that we'll use the other two pairs in the cable.

For a straight-through cable it's still 1 to 1, 2 to 2, and so on up to pin 8.

### Rolled/Rollover Cable

Although rolled cable isn't used to connect any Ethernet connections together, you can use a rolled Ethernet cable to connect a host EIA-TIA 232 interface to a router console serial communication (COM) port.

If you have a Cisco router or switch, you would use this cable to connect your PC, Mac, or a device like a tablet to the Cisco hardware. Eight wires are used in this cable to connect serial devices, although not all eight are used to send information, just as in Ethernet networking.

![image](https://github.com/user-attachments/assets/ad34fcf9-4e63-4b11-9868-aff2c9e50ce1)

These are probably the easiest cables to make because you just cut the end off on one side of a straight-through cable, turn it over, and put it back on— with a new connector.

### T1 Crossover Cable

There is an older device called a CSU/DSU, which used to be all-so-important. This old device may still be your connection to the Internet for the enterprise if you have serial WANs.

The type of cable you use to connect to this device from your router depends on the interface types that are available on the router.

The router may connect with several types of serial cables if a T1 connection is not built into it. If a T1 connection is built into the router, you will use an Ethernet cable.

![image](https://github.com/user-attachments/assets/eeeb6128-977e-4daf-8e77-bdc06085b03b)

In rare instances you may need to run a cable between two CSU/DSUs. In that case you would need a T1 crossover cable. A T1 cable uses pairs 1 and 2, so connecting two T1 CSU/DSU devices back-to-back requires a crossover cable that swaps these pairs. Specifically, pins 1, 2, 4, and 5 are connected to 4, 5, 1, and 2, respectively.

## Installing Wiring Distributions

### MDF/IDF

The main distribution frame (MDF) is a wiring point that's generally used as a reference point for telephone lines.

It's also considered the WAN termination point. It's installed in the building as part of the prewiring, and the internal lines are connected to it. After that, all that's left is to connect the external (telephone company) lines to the other side to complete the circuit.

Often, another wire frame called an intermediate distribution frame (IDF) is located in an equipment or telecommunications room. It's connected to the MDF and is used to provide greater flexibility for the distribution of all the communications lines to the building. It's typically a sturdy metal rack designed to hold the bulk of cables coming from all over the building.

### 25 Pair

A 25-pair cable consists of 25 individual pairs of wires all inside one common insulating jacket. 

It's not generally used for data cabling, just for telephone cabling, and especially for backbone and cross-connect cables because it reduces the cable clutter significantly. 

This type of cable is often referred to as a **feeder cable** because it supplies signal to many connected pairs.

### 66 Block

If you know what a 66 block is, either you're really old or you work in an old building since they came out in 1962 and can really only be used for old analog telephone connections. This uses the 25-pair cable I just mentioned and is a standard termination block containing 50 rows, which created an industry standard for easy termination of voice cabling.

### 110 Block

A newer type of wiring distribution point called a 110 block has replaced most telephone wire installations and is also used for computer networking.

On one side, wires are punched down; the other side has RJ-11 (for phone) or RJ-45 (for network) connections.

You'll find 110 blocks in sizes from 25 to more than 500 wire pairs, and some can carry 1 Gbps connections when used with Category 6 or greater cables. The hitch is that using Cat 6 with the 110 block is really difficult because of the size of the Cat 6 wiring.

![image](https://github.com/user-attachments/assets/a493049f-e4f9-4d9a-a171-92f49a52eb8e)

There is a proprietary European variant of the 110 block called a Krone block. The **Krone** block is compatible with the 110 block and can be used interchangeably.

### BIX Block

Another type of punch-down block is the BIX block. A BIX block can terminate up to 25 cable pairs and have a slip-in fitting that does not require pre-stripped wires.

### Demarc/Demarc Extension

The demarc (short for demarcation) is the last point of responsibility for the service provider.

It's often at the MDF in your building connection, especially if your building is large, but it's usually just an RJ-45 jack that your channel service unit/data service unit (CSU/DSU) connects from your router to WAN connections.

Network admins often test for connectivity on both sides of the demarc when troubleshooting to determine whether the problem is internal or external. 

The length of copper or fiber that begins after the demarc but still doesn't reach up to your office is referred to as a **demarc extension**.

### Smart Jack

A smart jack, also called a network interface device (NID) or network interface unit (NIU), is owned by the PSTN and is a special network interface that's often used between the service provider's network and the internal network.

You can't physically test to an actual demarc because it's just an RJ-45 jack, but the service provider may install an NID that has power and can be looped for testing purposes.

The smart jack device may also provide for code and protocol conversion, making the signal from the service provider usable by the devices on the internal network like the CSU/DSU.
