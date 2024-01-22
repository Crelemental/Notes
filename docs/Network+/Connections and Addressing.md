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

**Layer 2 Switches**. Performs the same sort of function as a bridge but in a more granular way and with many more ports. Each switch port becomes a separate collision domain. The switch establishes a point-point link between any 2 network nodes, ie **micro-segmentation**. As with a bridge, though, traffic on all switch ports is in the same broadcast domain, unless the switch is configured to use virtual LANs (VLANs).

**NICS**. Network interface card. Transceiver component responsible for physically connecting the node to the transmission medium. A NIC may provision multiple ports on the same card. This allows either connections to different networks or aggregating the separate links into a higher bandwidth channel. Each ethernet port has a unique MAC address, aka an **extended unique identifier (EUI)**.

**MAC address format**
	MAC/EUI is a 48bit (6byte) identifier. Format differs on the system architecture. Often displayed as 6 groups of 2 hexadecimal digits (or 3 groups of 4 hex digits with period separators). 
	**Burned-in addresses**. IEEE gives each card manufacture a range of numbers, and they hard code every interface produced with a unique number from their range. The first six hex digits are known as the **organizationally unique identifier (OUI)**, identify the manufacture of the adapter. Last 6 digits are the serial number.
	Organizations can use locally administered addresses rather than universal coding systems. This is defined by changing the U/L bit from 0 to 1. The rest is configured using the card driver or network management software. 
	**Broadcast Address**. The I/G bit of a MAC address determines whether the frame is addressed to an individual node (0) or a group (1). The latter is used for broadcast and multicast transmissions. MAC address with all 1s of the broadcast address should be processed by all nodes within the same broadcast domain.

### Ethernet Frame Format
![[Pasted image 20240118100523.png]]
**Preamble**. The preamble and the **start frame delimiter (SFD)** are used for clock synchronization and a part of the CSMA/CD protocol to detect collisions early. Preamble consists of 8 bytes (alternating 1s and 0s) and the SFD being two consecutive 1s at the end.

**Error Checking**. The error checking field is a 32bit (4byte) checksum called **cyclic redundancy check (CRC)** or **frame check sequence (FCS)**. It's calculated based on the contents of the frame; if the receiving node performs the same calculation, and they match, it accepts the frame. No mechanism for retransmission if damage is found, this is found in protocol at higher layers.

A standard Ethernet frame has a max length of 1518 bytes, excluding preamble. Each frame has a header composed of:
	6byte destination MAC address field
	6byte source MAC address field
	2byte Ether type field
Max size of the data payload is 1500bytes, also referred to the **maximum transmission unit (MTU)**. 
Most gigabit and 10GbE Ethernet support jumbo frames with a larger MTU such as 9000 bytes. This is whoever not standardized and can cause compatibility issues.

### Packet Sniffers and Taps
A protocol analyzer allows inspection of traffic received by a host or passing over a network link. It depends on a packet sniffer, as its purpose is to capture frames moving over the network medium. 
3 options for connecting a sniffer to a point in the network are:
	**SPAN (switch port analyzer)** means that the sensor is attached to a specially configured port on the switch that receives copies of frames addressed to nominated access ports. Not fully reliable.
	**Passive test access point (TAP)**. A box with ports for incoming and outgoing network cabling and an inductor/optical splitter that physically copies the signal from the cabling to a monitor port. No logic decisions are made so every frame, even corrupt, are sent to the monitor port (unlike a SPAN).
	**Active TAP**. A powered device that performs signal regeneration, which is needed in some circumstances. Some gigabit signaling is complex for a passive tap to monitor. 

**TCPDUMP**
A packet capture utility for LINUX. Basic syntax is: tcpdump -i eth0
Usually used with some filter expression:
	Type: host, net, port, portrange
	Direction: src, dst, host, network, port
	Protocol: arp, icmp, ip, ip6, tcp, udp...
For example, the following command filters frames to those with the source IP 10.1.0.100 and destination port 53 or 80:
tcpdump -i eth0 "src host 10.1.0.100 and (dst port 53 or dst port 80)"

**Wireshark**
Open source graphical packet capture analysis utility. 

### Ethernet Switches
**Unmanaged vs managed** 
	On a soho network, switches are usually unmanaged, standalone units that can be added to a network without any configuration (and sometimes built into router/modem). On corporate networks, switches are most likely managed, meaning switch settings can be configured. 
**Stackable**
	Switches that can be connected together and operate as a group, with the stack being managed as a single unit.
**Modular vs fixed**. 
	Fixed switch comes with a set number of ports and cannot be changed or upgraded, while a modular switch has slots for plug-in cards, meaning they can be configured with different numbers and types of ports.
**Desktop vs rack mounted**
	Simple unmanaged switches with 5-8 ports might be small freestanding units that can be placed on a desktop. Larger switches are designed to be fitted to the standard size racks that hold networking equipment.

**Switch interface configuration**
	Configuration of a managed switch can be performed at a CLI, allowing changes like command modes or hierarchies. 
	{show config} displays the switch's configuration (with startup config being different from running config).
	{show interface} lists the state of all interfaces or the specified interface, identified by type, slot, and port number. 

Most switch interfaces are configured to use **auto-MDI/MDIX** by default. This means that the switch senses the configuration of the connected device and cable wiring and ensures that an MDI uplink to an MDIX port gets configured. This will also ensure a link if a crossover cable is used to connect an end system by mistake.

Switches learn MAC addresses by reading the source address when a frame is received in a port. That address is cached in a MAC address table, implemented as a content addressable memory (CAM). If the MAC address cannot be found in there, the switch will act like a hub and flood all ports except source port. You can also query the MAC address table to find the addresses associated with ports.

**Port security** configuration validates the MAC address of end systems that connect to a switch port. Unknown or frequently changing host MAC addresses might indicate an intrusion attempt. Port security configs have 2 elements: Specify a static MAC address or allow the port to learn and accept a certain number of sticky addresses. Specify an enforcement action when a policy violation is detected (ie alert only or shutdown port).

**Port aggregation** means combining two or more cabled links into a single logical channel. Aka NIC teaming. Often implemented by the Link aggregation control protocol (LACP). Its used to auto-negotiate the bonded link between the switch ports and the end system, detect config errors, and recover from failure of a physical link.

**Port Mirroring**. A switch only forwards unicast traffic only to the specific port connected to the intended destination interface. This prevents sniffing of unicast traffic by hosts on the same switch. Port mirroring allows for legitimate capturing and network traffic analysis. The mirrored port would be used by management or monitoring software, like a packet sniffer, network analyzer, or intrusion detection system (IDS).

**Jumbo Frames**. Ordinarily, an Ethernet frame can carry a data payload or maximum transmission unit (MTU) of up to 1,500 bytes. A jumbo frame is one that supports a data payload of up to around 9,000 bytes. Critical that all hosts and appliances are configure to support them.

**Flow Control**. Allows a server to instruct the switch to pause traffic temporarily to avoid overwhelming its buffer and causing it to drop frames.

**PoE Power over Ethernet**. Supplying electrical power from a switch port over ordinary cabling to a connected, powered device, like a VoIP headset, IP camera, or WAP. 
	802.3af: 13W over the link, 350mA@48V.
	802.3at (PoE+) 25W
	802.3bt (Ultra PoE) 51W (Type 3), or 73W (Type 4)
	



# Troubleshooting Ethernet Networks

### **CompTIA troubleshooting methodology**
1. **Identify the problem:**
	Gather information.
	Duplicate the problem, if possible.
	Question users.
	Identify symptoms.
	Determine if anything has changed.
	Approach multiple problems individually.
2. **Establish a theory of probable cause:**
	Question the obvious.
	Consider multiple approaches.
	Top-to-bottom/bottom-to-top OSI model.
	Divide and conquer.
3. **Test the theory to determine cause:**
	Once theory is confirmed, determine next steps to resolve problem.
	If theory is not confirmed, reestablish new theory or escalate.
4. **Establish a plan of action to resolve the problem and identify potential effects.**
5. **Implement the solution or escalate as necessary.**
6. **Verify full system functionality, and if applicable, implement preventive measures.**
7. **Document findings, actions, and outcomes.**

### **Cable Connectivity Issues**

In Ethernet terms, the **speed** is the expected performance of a link that has been properly installed to operate at 10 Mbps, 100 Mbps, 1 Gbps, or better. Speed is measured as a unit of time-typically milliseconds (ms)-and is also referred to as latency, or delay.
The nominal bit rate will not often be achieved in practice. **Throughput** is an average data transfer rate achieved over a period of time excluding encoding schemes, errors, and other losses incurred at the physical and data link layers.
Noise enforces limitations on this media, expressed as **signal to noise ratio (SNR).** Same with attenuation, which is expressed in decibels (dB).

Cable issues are focused at the physical layer, layer 1. This includes the 
	Network transceiver in host
	patch cable between host and wall
	structured cable between wall and patch
	patch cable between patch panel and switch
	network transceiver in switch port.
Loopback tool can test for a bad port if the problem isnt within the patch cords.

Another way to test cable problems is to check the link lights on the NIC and the switch/router port. Usually its:
	Solid green: Link connected no traffic
	Flickering green: Link operating normally with traffic
	No light: not working/shut down port
	Blinking amber: Fault has been detected (duplex mismatch, collisions)
	Solid amber: port is blocked by spanning tree algorithm, prevents loops within switched network

Most adapters and switches autonegotiate port settings, which could fail. You would have to set both to autonegotiate, or set them manually to work correctly with each other.

**Cable testers**
	A Cable tester reports detailed info on the physical and electrical properties of the cable. It can test and report cable conditions, crosstalk, attenuation, noise, resistance, etc... 
	It might incorporate the function of a **time domain reflectometer (TDR)**. Its used to measure the length of a cable run and can locate open and short circuits, sharp bends, and other imperfections causing performance loss. It transmits a short signal pulse of known amp and duration down a cable and measures the corresponding amp and time delay with the resultant signal reflections.
	
You can use a **multimeter** to check physical connectivity in a copper cable, knowing the respective resistance. IE UTP ethernet cable is found to be 100 ohms, with any deviation meaning the cable has a break. Multimeters for computer networks have the function of a **wire map tester**. The base unit is connected to one end, and the remote unit to the other. When the test is activated, an LED for each wire conductor lights up in sequence, with no LED meaning a problem with the cable. 

**Wire map testers** can find
	Continuity (open)
	Shorts (damaged wire)
	Incorrect pin-out/termination/standards
		Reversed Pair (conductors in a pair wired to different terminals)
		Crossed pair (TX/RX reverse, with conductors from one pair connected to pins belonging to a different pair)

**Network tone generator** and probe can be used to trace a cable from one end to another, useful when cables are bundled and not labeled.

**Attenuation and interference**. If a cable link is too long, decibel loss (dB) may mean the link experiences problems with high error rates and retransmissions, causing reduced speeds and loss of connectivity. 

**Crosstalk**. Usually indicates a problem with bad wiring, a bad connector, or improper termination. Various types of crosstalk can be measured:
	**Near End (NEXT)**- measures crosstalk on the receive pairs at the transmitter end, cause by excessive untwisting of pairs or faulty bonding of shielding.
	**Attenuation to Crosstalk Ratio, Near End (ACRN)**- The difference between insertion loss and NEXT. Equivalent to SNR. High value means signal is stronger than noise, with closer to 0 being high error rates.
	**Attenuation to Crosstalk Ratio**, **Far End (ACRF)**- **Far end crosstalk (FEXT)** is measured on the receive pairs at the recipient end. Difference between insertion loss and FEXT, measures cable performance regardless of link length
	**Power sum**- Gigabit and 10GbE use all 4 pairs. Confirms that a cable is suitable for this type of application.

**Cable Application Issues**

**Straight Through and Crossover Cables**. There are two main formats for patch cords:
	Straight through-the cable is terminated with either T568A at both ends or T568B at both ends. This type of cable is used for an uplink (MDI port to MDIX port).
In fact, crossover cable is no longer required for this type of application, as switches either have an uplink port for this purpose or can autodetect and select between a crossover and straight-through connection. This is referred to as auto-MDI/MDI-X. All Gigabit Ethernet ports support auto-MDI/MDI-X.

**Rollover Cable/Console Cable**
A console cable is used to connect a PC or laptop to the command line terminal of a switch or router. The console port connection on the appliance is a standard RJ-45 jack (but wired in a different way to Ethernet). A program such as PuTTY on the PC is used to establish the connection using the appropriate settings for the serial link.

**Fiber Optic Cable Testing**
Breaks can be found using a **optical time domain reflectometer (OTDR)**. It sends light pulses down the cable and times how long it takes for any reflections to bounce back from the break.
An optical spectrum analyzer (OSA) is used with **wavelength division multiplexing (WDM)** to ensure each channel has sufficient power. OSA can determine whether existing cable is suitable for reuse with WDM and which wavelengths support the link distance required. 
**Dirty optical cables** can cause a great reduction in signal strength or block transmission, usually found at the connecting end. It can be cleaned using solvent designed for fiber optic. Could also occur when cables are spliced.


# IPv4 Addressing

The Internet Protocol (IP) header contains fields to manage the logical addressing and forwarding function. ![[Pasted image 20240120205648.png]]
Version field indicates the version of IP in use, while the Length fields indicate the size of the header and total packet size. Protocol field describes what is contained in the payload so the receiving host knows how to process it. For most packets, TCP/6 or UDP/17 while be indicated in the protocol field. 
Some protocols that directly run on IP would be
	ICMP/1 - internet control message protocol
	IGMP/2 - internet group management protocol
	GRE/47 - generic routing encapsulation
	ESP/50 - encapsulating security payload + AH/51 - authentication header
	EIGRP/88 - enhanced interior gateway routing protocol + OSPF/89 - open shortest path first

An IP address provides 2 pieces of information:
	Network Number (ID) - common to all hosts on the same IP network
	Host Number (ID) - identifies a host within an IP network

An IPv4 address is 32bits long, with it divided into 4 groups of 8 bits, known as octets. It uses a dotted decimal notation, with each octet being a decimal number (rather than bits).
11000110 00110011 01100100 00000001
198           .51             .100           .1

### Network Masks
IP addresses represent both network and host IDs. A 32 bit network mask is used to distinguish between these 2 components in a single IP address. The mask conceals the host ID portion of the IP address and reveals the network ID portion.

Whenever there's a binary 1 in the mask (255), that corresponding binary digit in the IP address is part of the network ID.

so 255.255.255.0 as the network mask for the IP address of 198.51.100.1 means that 198.51.100.0 is the network ID. The only difference between the two is the last digit, which is not masked.

Instead of a dotted decimal mask, this network can be identified with a prefix or slash notation. The prefix is simply the number of bits set to 1 in the mask. So that network can be referred to as 198.51.100.0/24

A long netmask like 255.255.255.0 allows for more network IDs within the overall internetwork, but less hosts per network. A short netmask like 255.0.0.0 allows for millions of hosts per network, but only 126 network addresses. The limit is set by Class A addresses using the default Class A subnet.

### Subnet Masks
The scheme of using whole octet boundaries is inflexible, so a system of dividing networks into subnetworks or subnets was made.

**Subnet addressing** has 3 levels: a network ID, subnet ID, and host ID. To create logical subnets, bits from the host portion of the IP address must be allocated as a subnet address rather than part of the host ID. The subnet ID lies within an octet boundary.![[Pasted image 20240120212911.png]]
Only leaves 4 bits for the Host ID range

Network ID and subnet ID use different masks. The mask for the whole network is still 255.255.255.0. Hosts within the network use the subnet mask 255.255.255.240. Only one mask is applied to the IP address. Mask containing subnet info is only used *within* the IP network, while external IP networks use the netmask. 

### Host address ranges

IP network 198.51.100.0/24 allows for 254 possible host IDs. 8 bits can express 256 values, but the first is the network address, and the last is the broadcast address.
Using some of these 8 host bits as a subnet ID creates extra networks, but each of those subnets has fewer host addresses. ![[Pasted image 20240120213709.png]]
The purpose of subnetting is to create layer 3 broadcast domain segments with fewer hosts. Trick its to fit the scheme to the requirements for number of subnetwork and hosts per subnet. Each bit added to the mask halves the number of host addresses.

**Forwarding at layer 3 is referred to as routing, while forwarding at layer 2 is described as switching.**
![[Pasted image 20240120214613.png]]

If the masked portions of the source and destination IP addresses match then its assumed to be on the same IP network or subnet. Like 198.51.100.17 and 198.51.100.19 with a mask of 255.255.255.240. It will try to deliver the packet locally. If it doesn't match, the IP assumes the packet must be router to another IP network.

When the destination IPv4 address is on a different IP network or subnet, the host forwards the packet to its default gateway rather than delivering locally. **Default gateway** (*IP configuration parameter that identifies the address of a router on the local subnet that the host can use to contact other networks*) is a router configured with a path to remote networks.

Router determines what to do with the packet by performing the same comparison between the source and destination address and netmask. Using its routing table, it determines which interface to use to forward the packet. Paths to other IP networks can be manually configured in the routing table or learned by a dynamic routing protocol.

### ARP (address resolution protocol)
The TCP/IP suite includes ARP to perform the task of resolving an IP address to a hardware address.
When both sending and receiving hosts are within the same broadcast domain or subnet, local address resolution takes place using ARP requests and ARP replies

### Unicast and Broadcast addressing-- Multicast and Anycast addressing
When an IPv4 host wants to send a packet to a single recipient, it uses a **unicast**packet, addressed to the IP address of the destination host.
One means of addressing multiple hosts is to perform a broadcast. A broadcast can be performed by sending a packet to the network or subnet's broadcast address.

IPv4 multicasting allows one host on the Internet (or private IP network) to send content to other hosts that have identified themselves as interested in receiving the originating host's content. The Internet Group Management Protocol (IGMP) is typically used to configure group memberships and IP addresses. **Anycast**means that a group of hosts are configured with the same IP address.

### VLANs and Subnets
If too many hosts are attached to the same switch, broadcast traffic becomes excessive and reduces performance. At layer 2, VLANs fix that. Each interface on a managed switch can be given a VLAN ID. This means that different groups of computers on the same cabling and on the same switches can appear to be in separate LAN segments.

At layer 3, subnetting is the process of logically dividing an IP network into smaller subnetworks, with each subnet having a unique address. Subnets can represent the VLAN design in layer 3 topology.

### Classful addressing
![[Pasted image 20240120222428.png]]
![[Pasted image 20240120222450.png]]
You can identify the address class from the first octet of the IP address.
Netmask for classful addressing
- Class A: 255.0.0.0 (/8)
- Class B: 255.255.0.0 (/16)
- Class C: 255.255.255.0 (/24)

### Public vs private addressing

Private IP addresses can be drawn from the pools of addresses defined in RFC 1918 as non-routable over the internet
* 10.0.0.0 to 10.255.255.255 (Class A private address range).
- 172.16.0.0 to 172.31.255.255 (Class B private address range).
- 192.168.0.0 to 192.168.255.255 (Class C private address range).

**APIPA | Automatic private IP addressing**
Autoconfiguration on an IPv4 network usually means using a **DHCP (Dynamic Host Configuration Protocol)** server. APIPA was designed by Microsoft so that clients that couldn't connect to a DHCP server could communicate on the local network anyway. If a host doesn't receive a response from a DHCP server within a time frame, it selects a random address from 169.254.1.1 to 169.254.254.254.

**Other reserved address ranges**
- Class D addresses (224.0.0.0 through 239.255.255.255) are used for multicasting.
- Class E addresses (240.0.0.0 through 255.255.255.255) are reserved for experimental use and testing.

127.0.0.0 to 127.255.255.255 is reserved to configure a loopback address, which is a special address used to check if TCP/IP is correctly installed on the local host. Usually configured on hosts as 127.0.0.1

OTHER:
- **0.0.0.0/8** - Used when a specific address is unknown. This is typically used as a source address by a client seeking a DHCP lease.
- **255.255.255.255** - Used to broadcast to the local network when the local network address is not known.
- **100.64.0.0/10, 192.0.0.0/24, 192.88.99.0/24, 198.18.0.0/15** - Set aside for a variety of special purposes.
- **192.0.2.0/24, 198.51.100.0/24, 203.0.113.0/24** - Set aside for use in documentation and examples.

**The following factors must be weighed when planning an IPv4 network addressing scheme:**
- The number of IP networks and subnetworks required.
- The number of hosts per subnet that must be supported.
- The network ID must be from a valid public or a private range (not from the loopback, link local reserved range, multicast range, or reserved/experimental range, for instance).
- The network and/or host IDs cannot be all 1s in binary-this is reserved for broadcasts.
- The network and/or host ID cannot be all 0s in binary; 0 means "this network."
- Each host ID must be unique on the IP network or subnet.
- The network ID must be unique on the Internet (if you are using a public addressing scheme) or on your internal system of internetworks (if you are using a private addressing scheme).
![[Pasted image 20240120223549.png]]



# Supporting IPv4 and IPv6 Networks
### Tools to test IP configuration
IP configuration values are assigned statically or dynamically. Most hosts are configured to obtain an address automatically, using DHCP services.
In windows, each ethernet adapter is assigned a name. IP configuration for each adapter interface is often set using the GUI properties via the network connections applet. However you can configure interfaces using `netsh` commands.
`netsh interface ip set address "Ethernet" dhcp`
`netsh interface ip set address "Ethernet" static 10.1.0.1 255.255.255.0 10.1.0.254`
Also you can use netsh to report IP config
`netsh interface ip show config`

Using powershell, the `Get-NetAdapter or Get-NetIPAddress` work to query configs. `New-NetIPAddress or Set-NetIPAddress` can make new and modify configs.

**IPCONFIG**
`ipconfig` displays the IP address, subnet mask, default gateway, for all network interfaces
`ipconfig /all` displays complete TCP/IP config parameters for each interface, including if DHCP is enabled for the interface and the hardware MAC address
`ipconfig /renew [interface]` forces a DHCP client to renew the lease it has for an IP address
`ipconfig /release [interface]` releases the IP address given by the DHCP server so that the interface will no longer have an IP address
`ipconfig /displaydns` displays the DNS resolver cache
`ipconfig /flushdns` clears the DNS resolver cache
`ipconfig /registerdns` registers the host with a DNS server

**IFCONFIG and IP**
On linux, ethernet interfaces are usually eth0, eth1, eth2, etc... 
`ifconfig` is part of legacy net-tools package. 
`ip` command had options for managing routes as well as local interface configuration. Basic reporting of ifconfig can be done by running `ip addr`, with `ip addr show dev eth0` for a single interface only.
`ip  link` shows the status of interfaces
`ip -s link` reports interface statistics

**ARP cache utility**
ARP is used by hosts to determine which MAC address is associated with and IP address on the local network. Queries are sent as broadcasts, which generate traffic on a network, reducing performance. Results are cached in an ARP table. 
`arp` can be used to perform functions related to the ARP table cache.
`arp -a | or -g` shows the ARP cache contents
`arp -s [ip address][MAC address]` adds an entry to the ARP cache.
`arp -d *` deletes all entries in the ARP cache

`ip neigh` on Linux shows entries in the local ARP cache

**ICMP and Ping**
ICMP is used to report errors and send messages about the delivery of a packet. It can be used to test and troubleshoot connectivity issues on IP networks. The `ping` utility sends a configurable number and size of ICMP request packets to a destination host. Both on linux and windows hosts. 
Basic connectivity test is done with `ping [ip address]`. If successful, output shows reply from ip address, and the time it takes for the response to arrive. RTT (round trip time) can be used to diagnose latency problems.
TTL (time to live) IP header field is reduced by one every time a packet is forwarded by a router (hop). TTL output field shows the value of the counter when the packet arrived at its destination. 

### Troubleshoot IP networks
1. Ping the loopback address (ping 127.0.0.1) to verify TCP/IP is installed and loaded correctly. If this fails, reinstall the network protocol stack.
2. Ping the IP address of the local host to verify it was added correctly and to verify that the network adapter is functioning properly. If you cannot ping your own address, there might have been a configuration error, or the network adapter or adapter driver could be faulty.
3. Ping the IP address of the default gateway to verify it is up and running and that you can communicate with another host on the local network.
4. Ping the IP address of other hosts on the same subnet to test for local configuration or link problems.
	If a local host cannot be pinged and the error is destination unreachable, then verify the IP configuration does not contain an incorrect IP address or netmask. If these are correct but pings still time out, suspect either a security issue (such as a switch port security issue) or a problem at the data link or physical layer.
5. Ping the IP address of a remote host to verify you can communicate through the router. If a remote IP address cannot be contacted, check the default gateway parameter on the local host to rule out an incorrect gateway issue. If the gateway is configured correctly and you can ping the router, you need to start investigating the routing infrastructure.
### IPv4 vs IPv6
Inefficiencies in the addressing scheme and unceasing demand for more addresses means that the IPv4 address supply is exhausted.
IPv6 provides a long term solution to the problem of address space exhaustion. Its 128 bit addressing scheme has space for 340 undecillion unique addresses. Allows for every person on the planet to have 4000 addresses.
IPv6 consists of 2 or 3 elements: the main header (fixed length), one ore more optional extension headers, and the payload. 
Other header fields are
	Traffic Class - packet priority
	Flow Label - QoS management like real time streams
	Payload Length - length of the payload, with 0 meaning Jumbo payload
	Next Header -  describes the next extension header or where payload begins
	Hop Limit - replaces TTL field in IPv4 but performs same function

**IPv6 address format**
Contains 8, 16bit numbers (double octets), with each being 4 hex digits:
`2001:0db8:0000:0000:0abc:0000:def0:1234`
Canonical notation: double octet contains leading 0s, they can be ignored. Contiguous series of 0s can be replaced by a double colon. 
`2001:db8::abc:0:def0:1234`

IPv6 addresses are divided into 2 parts, the first 64bits are the network ID, while the 2nd 64bits designate a specific interface. Network addresses are written using classless notation, where /nn is the length of the network prefix in bits. IE prefix /48 and the same 48 bits of an IPv6 address, they're in the same IP network. This also means that they have 16 bits left in the network ID to subnet their network.

`2001:db8:3c4d::/48`
would represent a network address, while:
`2001:db8:3c4d:0001::/64`
would represent a subnet within that network address.
![[Pasted image 20240121171254.png]]

![[Pasted image 20240121171239.png]]
The Neighbor Discovery (ND) protocol performs some of the functions on an IPv6 network that ARP and ICMP perform on IPv4. 
	Address autoconfiguration
	Prefix discovery - enables a host to discover the known network prefixes that have been allocated to the local segment. This facilitates next-hop determination. Prefix discovery uses router solicitation (RS) and router advertisement (RA) messages. An RA contains information about the network prefixes served by the router, information about autconfig options, plus information about link parameters (like MTU and hop limit).
	Local address resolution - allows a host to discover other nodes and routers on the local network.
	Redirection

IPv6 uses a more flexible system of address autoconfiguration called stateless address autoconfiguration (SLAAC):
- The host generates a link local address and tests that it is unique by using the Neighbor Discovery (ND) protocol.
- The host listens for a router advertisement (RA) or transmits a router solicitation (RS) using ND protocol messaging. The router can either provide a network prefix, direct the host to a DHCPv6 server to perform stateful autoconfiguration, or perform some combination of stateless and stateful configuration.

IPv6 uses an updated version of ICMP. The key new features are:
- **Error messaging**-ICMPv6 supports the same sort of destination unreachable and time exceeded messaging as ICMPv4. One change is the introduction of a Packet Too Big class of error. Under IPv6, routers are no longer responsible for packet fragmentation and reassembly, so the host must ensure that they fit in the MTUs of the various links used.
- **Informational messaging**-ICMPv6 supports ICMPv4 functions, such as echo and redirect, plus a whole new class of messages designed to support **Neighbor Discovery (ND)** and **Multicast Listener Discovery (MLD),** such as router and neighbor advertisements and solicitations.

**Dual stack** hosts and routers can run both IPv4 and IPv6 simultaneously and communicate with devices configured with either type of address. Most modern desktop and server operating systems implement dual stack IP.

As an alternative to dual stack, **tunneling** can be used to deliver IPv6 packets across an IPv4 network. Tunneling means that IPv6 packets are inserted into IPv4 packets and routed over the IPv4 network to their destination. Routing decisions are based on the IPv4 address until the packets approach their destinations, at which point the IPv6 packets are stripped from their IPv4 carrier packets and forwarded according to IPv6 routing rules. This carries a high protocol overhead and is not nearly as efficient as operating dual stack hosts.

IPv6 Address Prefixes
![[Pasted image 20240121173831.png]]

# Configure and Troubleshoot Routers

**Routing tables and path selection**
Information about the location of other IP networks and hosts is stored in the routing table. Each entry shows the route to a destination network or host. The parameters that define it are:
	Protocol - source of the route
	Destination - generally directed to network IDs than specific hosts
	Interface - local interface used to forward a packet along the chosen route. Represented as the IP address or as a layer 2 interface ID
	Gateway/next hop - The IP address of the next router along the path to the destination

**Static and default routes**
Routing tables fall into 4 categories
	Direct network routes, for subnets the router is attached to 
	Remote network routes, for subnets and IP networks not directly attached
	Host routes, for routes to a specific IP address
	Default routes, which are used when an exact match for a network or host aren't found

Directly connected routes
	The IP network or subnet for each active router interface is automatically added to the routing table.

Static routes
A static route is manually added to the routing table and only changes if an admin edits it. 

Default routes
A default route is a special type of static route that identifies the next hop router for a destination that cannot be matched by another routing table entry. 0.0.0.0/0 or ::/0 represents the default route. 

**Fragmentation**
	Most systems try to avoid IP fragmentation, which is the mechanism for splitting a layer 3 datagram between multiple frames to fit the MTU of the underlying Data Link network. IPv6 doesn't allow routers to do it all together. 

**Dynamic routing protocols**
A dynamic routing protocol uses and algorithm and metrics to build and maintain a routing information database. It stores info about the networks to which the router is connected and where there are multiple paths, prioritizes one over the rest. Information can be shared with the router's neighbors.

Topology and metrics
Most algorithms are classed as either distance vector or as link state. Some are a hybrid of different methods. The path with the lowest cost metric is preferred. The type of algorithm determines the factors that are used to calculate that metric

Convergence
The process whereby routers running dynamic routing algorithms agree on the network topology. Routers must be able to communicate changes to other routers to avoid black holes and loops. *black hole means discarded packet without notification to the source, loop causes a packet to be forwarded around the network until TTL expires*
Network with all routers sharing the same topology is described as steady state.

**Interior vs exterior gateway protocols**
A network under admin control of a single owner is an autonomous system (AS). An interior gateway protocl (IGP) is one that identifies routes within an AS.

An exterior gateway protocol (EGP) is one that can advertise routes between ASs. An EGP includes a field to communicate the network's AS ID and allows network owners to determine whether they can use paths through another org's network.
![[Pasted image 20240122105032.png]]

RIP (Routing information protocol) is a distance vector routing protocol. It only considers 1 piece of info, the next hop router to reach a given network or subnet. Uses lowest hop count to determine route. RIP sends updates to neighboring routers of its database every 30s.  
- RIPv1 is a classful protocol and uses inefficient broadcasts to communicate updates over UDP port 520.
- RIPv2 supports classless addressing and uses more efficient multicast transmissions over UDP port 520. It also supports authentication.
- RIPng (next generation) is a version of the protocol designed for IPv6. RIPng uses UDP port 521.]

Enhanced IGRP (EIGRP) made to solve lack of support for classless addressing and other limitations. Classed as an advanced distance vector or hybrid routing protocol. The 2 default elements are 
	Bandwidth -  applies a cost based on the lowest bandwidth link in the path
	Delay - applies a cost based on time it takes for a packet to traverse the link
Only send updates when it first establishes contact or when there's a topology change. 

**OSFP**, Open shortest path first, is the most widely adopted link state protocol.![[Pasted image 20240122110422.png]]

**BGP**, Border gateway protocol, designed to be sued between routing domains in a mesh internetwork, and used as a routing protocol between ISPs. BGP works with classless network prefixes called Network Layer Reachability Information (NLRI). Path selection is based on multiple metrics, including hop count, weight, local preference, origin, and community. BGP is not a pure distance vector algorithm. In fact, BGP is more usually classed as a path vector routing protocol.

An administrative distance (AD) value is used to express the relative trustworthiness of the protocol supplying the route.![[Pasted image 20240122110657.png]]

### Troubleshoot routers
**Edge routers**
Placed at the network perimeter, distinguished by external and internal interfaces. They can perform framing to repackage data from the private LAN frame format to the WAN internet access frame format. Customer's router is the customer edge CE, while service provider's router is provider edge PE.
Edge routers designed to work with DSL or cable broadband access methods are SOHO routers. 
Routers designed to service medium to large networks are complex and expensive appliances. They feature specialized processors to handle the routing and forwarding processes, and memory to buffer data.

**Internal routers**
Has no public interfaces. Positioned to implement whatever network topology required. Traffic between local subnets are controlled by separate internal routers.
Many networks are segmented using VLANs feature of managed switches. Traffic between VLANs must be routed. A router connected to a trunk port on a switch can carry all the VLAN to VLAN traffic that must be routed. The router's physical interface is configured with multiple sub-interfaces or virtual interfaces. Each is configured with a specific VLAN ID. 
Layer 3 capable switches are optimized for routing between VLANs. It can  use static and dynamic routing to identify which VLAN an IP address should be forwarded to. 

`router` command is used to view and modify the routing table of end system Windows and Linux hosts. 
`traceroute` supported on Linux and router OSes shows an output of number of hops, and the IP address of the ingress interface of the router or host, and time taken to respond to each probe.
`tracert` on a windows systems, same function as traceroute. 
#NetworkPlus