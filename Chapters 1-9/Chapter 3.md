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

