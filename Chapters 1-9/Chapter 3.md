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


