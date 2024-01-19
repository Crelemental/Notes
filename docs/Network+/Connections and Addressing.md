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
# Supporting IPv4 and IPv6 Networks
# Configure and Troubleshoot Routers
#NetworkPlus