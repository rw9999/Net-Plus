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

