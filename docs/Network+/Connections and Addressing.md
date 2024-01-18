#NetworkPlus
# OSI Model #OSI

![[Pasted image 20240116111327.png]]
A network protocol has 2 main functions:
	**Addressing:** Describing where data messages should go, such as a MAC address, IPv4 address, or IPv6 address.
	**Encapsulation:** A method by which protocols build data packets by adding headers and trailers to existing data. Its like an envelope for a letter, with each layer requiring its own envelope. 

* To transmit or receive a communication, _on_ each node, each layer provides services for the layer above and usthe services of the layer below. This is referred to as adjacent layer interaction.
![[Pasted image 20240116114021.png]]
At each level (except the physical layer), the sending node adds a header to the data payload, forming a “chunk” of data called a **protocol data unit (PDU).**

### OSI Model Layers
1. **Physical**
	Cabled, such as a physical signal conductor like fiber optic, or Wireless, such as microwave radio. 
	Specifies physical topology, such as the layout of nodes and links established by the transmission media. Segments being parts of larger networks, typically divided to cope with physical restrictions of the network media, or to improve security. A segment is where all nodes share access to the same media.
	Specifies physical interface, such as cable specifications, the medium's connector and pin-out details, or radio specs.
	Specifies signaling, the process of transmitting and receiving encoded data over the network medium.
	Devices on Layer 1, Physical, would be a Transceiver, Repeater, Hub, Media Converter, and a Modem.
2. **Data Link**
	Responsible for transferring data between nodes on the same segment in a network. A segment here is a area where all nodes can send traffic to one another using hardware addresses no matter the media type. Logical Topology.
	*Nodes that receive or send information are host nodes/end systems, like computers. Those nodes that forward information are intermediate systems or infrastructure nodes.*
	Data link organizes the stream of bits from the physical layer into structured units called frames. It adds control information to the payload in the form of header fields, which include destination hardware addresses and basic error check. 
	Devices on Layer 2, Data Link, would be a NIC, Bridge, Switch, or a AP.
3. **Network**
	Responsible for moving data around a network of networks. The network layer moves information around a internetwork by using logical network and host IDs. There is a variety of physical layer media and data link protocols in this layer. Main appliance is the router at this layer.
	This layer forwards information between networks by examining the destination network-layer address or logical network address. Its forwarded router by router through the internet to the target network. 
	Its important to filter traffic passing between networks, which is why the basic firewall operates at layer 3 to enforce a **ACL (Access Control List).**
4. **Transport**
	The transport layer, aka host-host layer, the content of the packets become significant. Any host on a network will be communicating with other many hosts using different types of networking data. The purpose of the transport layer is to identify each type of network application and assign it a port number. 
	This layer can also implement reliable data delivery mechanisms, like resending data that got lost or damaged (TCP).
	Devices on Layer 4, Transport, can be multi-layer switches (as load balancers), many security appliances, such as advanced firewalls and **intrusion detection systems (IDSs).**
5. **Session**
	Application protocols require the exchange of multiple messages between client and server, which would be classified as a session. This layer establishes a session just for this reason.
6. **Presentation**
	This layer transforms data from the network format to the format required for an application, like character set conversion like ASCII and Unicode. It can also be conceived as supporting data compression and encryption. (But usually done in lower layers).
7. **Application**
	Application layer protocols don't encapsulate, as they provide an interface for software programs on network hosts with an established communication channel (to lower layers) to exchange data. 
	Upper layer protocols provide most of the services that make a network useful, rather than being just functional. This includes web browsing, email communications, remote printing, database services, etc..
![[Pasted image 20240116122135.png]]

### SOHO
Single location  - LAN
SOHO - Small office/home office
WANs connect different geographic regions
The intermediate system powering SOHO networks is usually described as a SOHO router because one of its primary functions is to forward traffic between the LAN and the WAN.
Most SOHO subscriber Internet access is facilitated via the **public switched telephone network (PSTN).** The SOHO router is described as **customer premises equipment (CPE).**
The major infrastructure of the Internet consists of high bandwidth trunks connecting **Internet exchange Points (IXPs).** Within an IXP datacenter, ISPs establish links between their networks, using transit and peering arrangements to carry traffic to and from parts of the internet they do not physically own.
#### SOHO Layers
**Layer 1,** the SOHO router provides a number of RJ-45 ports to connect a local cabled network (LAN). Radio antennas to send and receive signals (WiFi). Also a type of modem is used to connect to the ISPs network (WAN). 
**Layer 2,** SOHO router acts as an Ethernet switch with the RJ-45 jacks. Radio antennas implement some type of WiFi standard, acting as a wireless hub allowing hosts to form a wireless network (with a bridge between the WAP and the Ethernet switch). Each host interface is identified by a media access control (MAC) address.
**Layer 3,** Routing part of the SOHO makes forwarding decissions between the local and public internet. Distinguished by IP addresses. Router runs a DHCP server to allocate a unique address to each host that connects to it. The router's WAN interface is given a public IP address by the ISP.
**Layer 4,** _Network security is essentially a matter of allowing or preventing devices, users, and services (applications) from using the network._ The WAN is the network perimeter, with the SOHO router being able to apply filtering rules to traffic sent between the public and private zones. Each application is given a port number, with the firewall in the router being able to configure rules specifying behavior for each port.

### Hexadecimal
This number of bits is called a byte or an octet. The four decimal numbers in the SOHO router's WAN IP address 203.0.113.1 are octets.
Hex is base 16 with the possible values of each digit represented by the numerals 0 through 9 and the characters A, B, C, D, E, and F.
![[Pasted image 20240117105428.png]]

# Ethernet Cabling
**Copper Cable**. Twisted pair and coaxial cable are the 2 main types. These cables suffer from high attenuation, meaning the signal loses strength over long links. Twisted pair is rated to CAT standards.
**Fiber Optic**. Light signals, not susceptible to interference or noise from other sources and less affected by attenuation. Fiber optic supports higher bandwidth over longer links than copper cable. It divided into **Single Mode (SMF)** and **Multi Mode (MMF)** types. MMF is categorized by **Optical Mode** designations (OM1, 2, 3, 4).

Ethernet uses a contention-based MAC system. Each node connected to the same media are in the same collision domain. If 2 nodes transmit at the same time the signals can collide and neither can reach their destination. 
The Ethernet protocol governing contention and media access is called **Carrier Sense Multiple Access with Collision Detection (CSMA/CD).** On detecting a collision, the node broadcasts a jam signal. Each node that was attempting to use the media then waits for a random period (backoff) before attempting to transmit again.

Unlike a hub, each switch port is a separate collision domain. By eliminating the effect of contention, switches allow for full-duplex transmissions, where a node can transmit and receive simultaneously, and each node can use the full 100 Mbps bandwidth of the cable link to the switch port.

**Twisted pair:** The pairs are twisted at different rates to reduce external interference and crosstalk. Crosstalk is a phenomenon whereby one pair causes interference in another as a result of their proximity. Most twisted pair cable used in office networks is **unshielded twisted pair (UTP).** Modern buildings are often flood-wired using UTP cabling. This involves cables being laid to every location in the building that may need to support a telephone or computer.
Shielded cable can be referred to generically as **shielded twisted pair (STP)**, but there are actually several types of shielding:
	Screened cable has one thin outer foil shield around all pairs. Screened cable is usually designated as **screened twisted pair (ScTP**) or **foiled/unshielded twisted pair (F/UTP)**, or sometimes just **foiled twisted pair (FTP)**.
	Fully shielded cabling has a braided outer screen and foil-shielded pairs and is referred to as **shielded/foiled twisted pair (S/FTP)**. There are also variants with a **foil outer shield (F/FTP).**
![[Pasted image 20240117111734.png]]
![[Pasted image 20240117112251.png]]
### Fiber Optic
There are many different outer jacket designs and materials suited for different installations (indoor/plenum, outdoor, underground, undersea, and so on). Kevlar (Aramid) strands and sometimes fiberglass rods (strength members) are often used to protect the fibers from excessive bending or kinking when "pulling" the cable to install it.
- **Single Mode Fiber (SMF)** has a small core (8 to 10 microns) and a long wavelength, near infrared (1310 nm or 1550 nm) light signal, generated by a laser. Single mode cables support data rates up to 100 Gbps and cable runs of many kilometers, depending on the quality of the cable and optics. There are two grades of SMF cable; OS1 is designed for indoor use, while OS2 is for outdoor deployment.
- **Multimode Fiber (MMF)** has a larger core (62.5 or 50 microns) and shorter wavelength light (850 nm or 1300 nm) transmitted in multiple waves of varying length. MMF uses less expensive optics and consequently is less expensive to deploy than SMF. However, it does not support such high signaling speeds or long distances as single mode and so is more suitable for LANs than WANs.
	- **OM1/OM2**-62.5-micron cable is OM1, while early 50-micron cable is OM2. OM1 and OM2 are mainly rated for applications up to 1 Gbps and use LED transmitters.
	- **OM3/OM4**-these are also 50-micron cable, but manufactured differently, designed for use with 850 nm Vertical-Cavity Surface-Emitting Lasers (VCSEL), also referred to as laser optimized MMF (LOMMF). A VCSEL is not as powerful as the solid-state lasers used for SMF, but it supports higher modulation (transmitting light pulses rapidly) than LED-based optics.

Permanent cables are run through conduit to wall ports at the client access end and a **fiber distribution panel** at the switch end. Fiber patch cables are used to complete the link from the wall port to the NIC and from the patch panel to the switch port. 
A **fusion splicer** achieves a more permanent join with lower insertion loss (<0.1 dB). The fusion splicing machine performs a precise alignment between the two strands and then permanently joins them together using an arc weld.

**Connectors:** 
Straight Tip (ST)
Subscriber Connectors (SC)
Local Connector (LC)
Mechanical Transfer Registered Jack (MTRJ)
![[Pasted image 20240117113438.png]]
![[Pasted image 20240117113607.png]]
The tip of the ferrule can be finished in one of three formats:

- **Physical Contact (PC)-** The faces of the connector and fiber tip are polished so that they curve slightly and fit together better, reducing return loss (interference caused by light reflecting back down the fiber).
- **UltraPhysical Contact (UPC)-** This means the cable and connector are polished to a higher standard than with PC.
- **Angled Physical Contact (APC)-** The faces are angled for an even tighter connection and better return loss performance. APC cannot be mixed with PC or UPC. These connectors are usually deployed when the fiber is being used to carry analog signaling, as in Cable Access TV (CATV) networks. They are also increasingly used for long distance transmissions and for Passive Optical Networks (PON), such as those used to implement Fiber to the x (FTTx) multiple subscriber networks.

Several different punchdown block and IDC formats have been used for telecommunications and data cabling.

* A **66 block** is an older-style distribution frame used to terminate telephone cabling and legacy data applications (pre-Cat 5). A 66 block comprises 50 rows of 4 IDC terminals. The 25-pair cable from the access provider is terminated on one side of the block. On the other side of the block, the terminals terminate the wiring from the PBX. A jumper (bridging clip) is installed over the middle two terminals to complete the connection.
* The 110 block (developed by AT&T) is a type of distribution frame supporting 100 MHz operation (Cat 5) and better. A **110 wiring block** is arranged horizontally rather than vertically, offering better density than a 66 block. There is also more space for labeling the connectors and each column of connectors is color-coded, making management simpler. The incoming wire pairs are fed into channels on the wiring block, then a connector block or wafer is installed to terminate the incoming wiring. Outgoing wire pairs are then punched into the terminals on the connector blocks to complete the circuit.
* Where a 110 block uses a two-piece design where wafer blocks are installed over the main block, competing formats **BIX and Krone** use a single module. 110 blocks and BIX blocks (developed by Nortel) are common in North America, while some European vendors often prefer Krone. As well as the differences in block design, the IDCs are angled differently in each format, requiring a different termination blade to be used to ensure a reliable connection.
* In data networks, numerous moves, adds, and changes (MACs) would require reterminating the wiring. To simplify MACs, a **patch panel** or **patch bay** is a type of distribution block with IDCs on one side and pre-terminated RJ-45 modular ports on the other. This allows incoming and outgoing connections to be reconfigured by changing the patch cable connections, which is much simpler than reterminating punchdown blocks. The structured cabling (running from the work area or forming a backbone) is terminated at the back of the patch panel on the IDCs. An RJ-45 patch cord is used to connect the port to another network port, typically a switch port housed in the same rack. This greatly simplifies wiring connections and is the most commonly installed type of wiring distribution where connections need to be changed often.

### **Tools**
Fixed cable is terminated using a **punchdown tool.** This tool fixes conductors into an IDC. There are different IDC formats (66, 110, BIX, and Krone), and these require different blades.
There are dedicated **cable stripper** tools that have replaceable blades for different data cable types. Cable cutting blades should be rounded to preserve the wire geometry.
A patch cord is created using a **cable crimper**. This tool fixes a plug to a cable. The tools are specific to the type of connector and cable

### Transceivers
Enterprise switches and routers are available with modular, hot-swappable transceivers/media converters for different types of fiber optic patch cord connections.
**SFP/SFP+**
	SFP uses LC connectors and is also designed for Gigabit Ethernet. Enhanced SFP (SFP+) is an updated specification to support 10 GbE but still uses the LC form factor.
**QSFP/QSFP+**
	Quad small form-factor pluggable (QSFP) is a transceiver form factor that supports 4 x 1 Gbps links, typically aggregaed to a single 4 Gbps channel. Enhanced quad small form-factor pluggable (QSFP+) is designed to support 40 GbE by provisioning 4 x 10 Gbps links. QSFP+ is typically used with parallel fiber and multi-fiber push-on (MPO) termination. An MPO backbone ribbon cable bundles 12 or more strands with a single compact terminator (the cables are all manufactured and cannot be field terminated). When used with QSFP+, four strands transmit a full-duplex 40 Gbps link, four strands receive, and the other four strands are unused.
 **BiDirectional Wavelength Division Multiplexing**
	Bidirectional (BiDi) transceivers support transmit and receive signals over the same strand of fiber. This uses WDM to transmit the Tx and Rx signals over slightly shifted wavelengths, such as 1310 nm for Tx and 1490 nm for Rx. BiDi transceivers must be installed in opposite pairs, so the downstream transceiver would have to use 1490 nm for Tx and 1310 for Rx. Bidirectional wavelength division multiplexing (WDM) links are documented in Ethernet standards (1000BASE-BX and 10GBASE-BX).
**Coarse and Dense Wavelength Division Multiplexing**
	Coarse Wavelength Division Multiplexing (CWDM) supports up to 16 wavelengths and is typically used to deploy four or eight bidirectional channels over a single fiber strand. Dense Wavelength Division Multiplexing (DWDM) provisions greater numbers of channels (20, 40, 80, or 160). This means that there is much less spacing between each channel and requires more precise and expensive lasers. CWDM and DWDM transceivers support multi-channel 1 G, 10 G, and 40 G Ethernet links. As with BiDi, the transceivers must be installed in opposite pairs for each channel.

# Ethernet Switching

**Repeaters** overcome the distance limitation by boosting the signal of cables at some point in the cable run. It works at Layer 1 of OSI. 

**Media Convertors** are used to transition from one cable to a cable of a different media type. Usually standalone or rack mounted appliances. Most common are the Single Mode Fiber to Twisted Pair, Multimode Fiber to Twisted Pair, or Single Mode to Multimode Fiber. 

**Hubs**. They act like multiport repeaters so that every port receives transmissions sent from any other port. 

**Bridges**. Operates at Layer 2, connecting separate physical network segments, allowing them to communicate as part of the same logical network (while creating separate collision domains to improve efficiency). Creates 1 logical network, referred to as a **layer 2 broadcast domain.** An Ethernet bridge builds a MAC address table in memory to track which addresses are associated with which of its ports.

**Layer 2 Switches**. Performs the same sort of function as a bridge but in a more granular way and with many more ports. Each switch port becomes a separate collision domain. The switch establishes a point-point link between any 2 network nodes, ie **microsegmentation**.


# Troubleshooting Ethernet Networks
# IPv4 Addressing
# Supporting IPv4 and IPv6 Networks
# Configure and Troubleshoot Routers
