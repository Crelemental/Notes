DNS Records, 802 standards, 2 questions on cabeling, lots of basic/easy security questions referring to dns poisoning, etc.


Passed Net+ with a 754. 

What did I use?:
-All of the CertMaster material given by WGU. This BY FAR was the most beneficial way for me.
-I did not watch any videos but have used Messer in the past and am sure he would have done great.
-Jason Dion practice exams through WGU Udemy. I did not take any practice exam more than once (so I didnt memorize the answers) but if I were to, I would recommend waiting a week or so that way the actual questions leave your head.
-On job experience. Personally, I learn VERY well by trying to relay any new information I learn to someone else. I did this with my boss the entire way.

Study suggestions:
-Wireless
-Basic CLI
-Static/dynamic routing
-Troubleshooting connectivity and understanding subnets
-Be comfortable with the different type of cyber attacks

Be comfortable with knowing basic subnetting. Shouldnt need to do anything crazy!

 I completed the PBQs (they were my first 5 questions) that I knew I could knock out quickly then skipped the others to get by the end of the exam.

Dion is tremendously more wordy than the actual exam. The exam is 1-2 sentences and it points you in the right direction and can eliminate at least 2. I only needed to know the very most common/obvious port numbers so no stress there.
![[Pasted image 20240210112357.png]]
20 - FTP
21 - FTP
22 - SFTP
22 - SSH
23 - Telnet
25 - SMTP
53 - DNS
67 - DHCP
68 - DHCP
69 - TFTP
80 - HTTP
110 - POP/POP3
123 - NTP
143 - IMAP
161 - SNMP
162 - SNMP
389 - LDAP
443 - HTTPS / HTTPS (TLS)
445 - SMB
514 - Syslog
587 - SMTP (TLS)
636 - LDAPS
993 - IMAP (SSL)
995 - POP3 (TLS)
1433 - SQL Server
1521 - SQLnet
3306 - MySQL
3389 - RDP
5060/61 - SIP

![[Pasted image 20240210112444.png]]![[Pasted image 20240210112530.png]]

# PBQs
![[Pasted image 20240202094317.png]]
**The primary difference between QSFP+ and SFP is the quad form**. QSFP+ is an evolution of QSFP to support four 10 Gbit/s channels carrying 10-Gigabit Ethernet, 10G Fiber Channel, or InfiniBand, which allows for 4x 10G cables and stackable networking designs that achieve better throughput.
![[Pasted image 20240202095019.png]]
![[Pasted image 20240202095254.png]]
layer 2 switch -> 2 Layer 3 switches
![[Pasted image 20240202095815.png]]
1. Was the server rebooted?
2. console into the vm
3. Research commands
4. dont escalate
![[Pasted image 20240202100103.png]]

![[Pasted image 20240202100416.png]]
1. ifconfig
3. netsh 192.168.1.101 255.255.255.0. 192.168.1.1
4. ipconfig /all
![[Pasted image 20240202100653.png]]
missclick

![[Pasted image 20240202101246.png]]
A. Default Route
D. Broadcast Address
3. 172.16.0.0 mask 255.255.0.0
4. flip them
![[Pasted image 20240202103515.png]]
nmap -sU -sT xxxx
A net.plus.com 192.168.2.10
AAAA net.plus.com
![[Pasted image 20240202103849.png]]A. POP3 / POP allows to retrieve messages and disconnect. mail1.allhoster.com. POP port is 995. Outgoing SMTP as mail2.allhoster.com.  TLS/STARTTLS. Port 587.

B. IMAP. mail1.allhost.com. Port 993. Not applicable to protocol. Outgoing SMTP and mail2.allhoster.com. TLS/STARTTLS. Port 587.
![[Pasted image 20240202105243.png]]
Telnet is on port 23, can be password protected.
encrypted with private and public keys
Remote credential guard
TCP 21 and 20, uses TLS
![[Pasted image 20240202105830.png]]
Any
UDP 514 for Syslog
ping x and ping y
snmpinfo
![[Pasted image 20240202110323.png]]Rule Disabled. WAN. swap both fields
![[Pasted image 20240202111343.png]]
Regional has no servers to backup
![[Pasted image 20240202111739.png]]![[Pasted image 20240202112146.png]]
forgot to select

# Practice short sections
Practice binary -> hexadecimal notation
know the abbreviations
know connector and cable types


1. A network technician needs a cost-effective solution that can multiplex up to 16 wavelengths on an SFP/SFP+ interface. Which multiplexing technique should the network technician use?
	1. CWDM
	2. WDM
	3. BiDi
	4. DWDM
	**Coarse Wavelength Division Multiplexing (CWDM) supports up to 16 wavelengths and typically deploys four or eight bidirectional channels over a single fiber strand.**
	Wavelength Division Multiplexing (WDM) is a means of using a strand to transmit or receive more than one channel at a time.
	Bidirectional (BiDi) transceivers support, transmit, and receive signals over the same strand of fiber. This uses WDM to transmit the transmit (Tx) and receive (Rx) signals over slightly shifted wavelengths.
	Dense Wavelength Division Multiplexing (DWDM) provisions a greater number of channels (20, 40, 80, or 160). This means that there is much less spacing between each channel and requires more precise and expensive lasers.

2. A network administrator is setting up cabling between buildings and needs to transmit the maximum distance possible. Which type of cabling would be most suitable?
	Single Mode (SMF) fiber optic cable supports higher bandwidth over longer links than copper cable. Single mode allows for longer distance transmission than MultiMode.

3. A network cabling engineer reviews different fiber optic connector form factors. Which of the following features a push-pull mechanism that is commonly used with multimode fiber?
	1. Straight Tip
	2. Mechanical Transfer Registered Jack
	3. Subscriber Connector
	4. Local Connector
	**The Subscriber Connector (SC) is a popular type of fiber optic connector that has a square snap-in design. It features a push-pull coupling mechanism, which allows for easy insertion and removal of the connector. The SC connector is available in both single-mode and multimode versions, making it versatile for various fiber optic applications.**  
	The Straight Tip (ST) connector is another common fiber optic connector, but it does not have a snap-in duplex design. It uses a bayonet-style coupling mechanism and is primarily used with multimode fiber.  
	Mechanical Transfer Registered Jack (MT-RJ) is a duplex connector that is primarily used with multimode fiber. It utilizes a small form factor and combines both fiber strands into a single connector. 
	The Local Connector (LC) is a recognized small-form-factor connector, with a latched design. LC connectors are typically used with single-mode fiber optic cables, though they are compatible with multimode fiber.

The first six hex digits of a MAC address (3 bytes or octets), also known as the Organizationally Unique Identifier (OUI), identifies the manufacturer of the adapter.

4. A network architect is assessing network performance. Which of the following is part of the CSMA/CD protocol to identify collisions early? (Select all that apply.)
	**The preamble is for clock synchronization and as part of the Carrier Sense Multiple Access with Collision Detection (CSMA/CD) protocol to identify collisions early.**
	**The Start Frame Delimiter (SFD) is also used for clock synchronization and as part of the CSMA/CD protocol to identify collisions early.**
	The error checking field contains a 32-bit (4-byte) checksum called a Cyclic Redundancy Check (CRC). The CRC is calculated based on the contents of the frame.
	The Cyclic Redundancy Check is also known as the Frame Check Sequence (FCS). There is no mechanism for retransmission if the damage is detected, nor is the CRC completely accurate at detecting damage.

The Simple Network Management Protocol (SNMP) is a widely used agent-based framework for remote management and monitoring of servers and network appliances.

NIC teaming, also sometimes called port bonding or port aggregation, can be accomplished using the Link Aggregation Control protocol. This can provide redundancy and extra bandwidth when there are multiple clients, as load balancing is performed.

DTLS secured CoAP uses port 5684.

UDP is generally preferable to TCP for IoT networks because IoT communications focus on low latency communications more than reliability. 

![[Pasted image 20240204174312.png]]![[Pasted image 20240204174323.png]]![[Pasted image 20240204174329.png]]

In IPv6, the interface identifier is always the last 64 bits.

An enterprise network provides remote database services delivered using a commercial relational database management system (RDBMS) to employees of an architectural firm. To secure the data, TLS encryption is required by both the server and the client. Propose a method of configuring the authentication that will provide for this requirement.
	A public key infrastructure uses a Certificate Authority to issue certificates containing keys. By ensuring all clients have certificates that match the host, security can be assured.

![[Pasted image 20240204174832.png]]

Category 6a fully shielded cabling has a braided outer screen and foil-shielded pairs and is referred to as shielded/foiled twisted pair (S/FTP).

26-bit mask provides a range of 64 IP addresses (2^6), with 62 host addresses. A subnet with "/26" CIDR notation reserves one address for the network and one for broadcast, leaving 62 addresses available. The subnet mask for a "/26" network is 255.255.255.192.

A data center network administrator working for a cloud services company is configuring an SDN that is optimized for east-west traffic. The SDN must be loop-free so that spanning tree protocol is not required, instead utilizing a protocol called Equal Cost Multipathing (ECMP) to distribute traffic between the links to the top-tier switches. Most importantly, all server resources will be on-premises, so the solution should avoid the use of the public Internet and the use of Protocol-Independent Multicast (PIM) protocols, instead establishing private links with guaranteed service levels to operate as an overlay network and configure point-to-point or point-to-multipoint links between nodes without respect to the underlying physical and data link topologies (in other words, tunneling through the network layer). The SDN must also feature multipath redundancy to allow for load balancing and failover. Choose a multipath routing protocol that will best fulfill these requirements.
	Shortest Path Bridging (SPB) and Multiprotocol Label Switching (MPLS) can be used together for private links, using SPB and IS-IS (a link-state IGP that uses shortest-path-first algorithm to determine routes) as a link-layer overlay and MPLS as a link-layer-independent "Layer 2.5" underlay.

NIST Special Publication 800-63B establishes a 14 character minimum password length for critical infrastructure such as switches. NIST asserts that password length is more important than password complexity in terms of password security.

Straight Tip (ST) is an early bayonet-style connector with a twist-and-push locking mechanism. ST was primarily used for multimode networks, however, it is no longer routinely utilized in Ethernet deployments.

While IPv6 does not use ARP, it is also vulnerable to layer 2 spoofing if the unencrypted Neighbor Discovery (ND) protocol is used.

Two routers count as two hops. Switches do not count as hops.

An IP datagram larger than 750 bytes would have to be fragmented across more than one Ethernet frame. Since the default MTU is 1500, most clients will be configured for that. If the legacy device does not support fragmentation, packets will be lost.

A physical access control system (PACS) is a network of monitored locks, intruder alarms, and video surveillance cameras.

A building automation system (BAS) or smart building for offices and data centers can include PACS, but also network-based configuration and monitoring of heating, ventilation, and air conditioning (HVAC), fire control, power and lighting, and elevators and escalators.

Building subsystems are implemented by programmable logic controllers (PLCs) and various types of sensors that measure temperature, air pressure, humidity, room occupancy, and so on.

IoT devices usually require a communications hub to facilitate wireless networking. There must also be a control system, as most IoT devices are headless, meaning they have no user control interface

A network engineer is testing an application over the IPv6 protocol. Determine how the server can cast packets to an entire local subnet.
	 Multicast to associated private topology - The Multicast Listener Discovery (MLD) protocol allows nodes to join a multicast group and discover whether members of a group are present on a local subnet.

A network specialist is installing a VoIP gateway in an office building that uses a legacy analog phone system. The office managers want to be able to use the old phone handsets and fax machines as well as add new VoIP endpoints but plans to cancel services with the company providing the analog telephone services and replace all legacy voice cabling. Plan a method for providing VoIP services while retaining legacy handsets and fax machines. (Select all that apply.)
	A VoIP gateway or adapter can be used to connect POTS handsets and fax machines to a VoIP PBX. This type of device is also called a Foreign Exchange Subscriber (FXS) gateway.
	Analog devices for connection to legacy phone networks called Foreign Exchange Office (FXO) can be used to facilitate compatibility.

Using Nmap with the -sn switch will suppress the port scan, which can reduce scanning time on large networks.

A service provider has terminated a T1 link to a mid-sized company using the T-carrier system. After patching from where the service provider terminated their connection, where would the customer connect for connectivity?
	The customer connects to the CSU / DSU. The cabling from the smartjack to the CSU/DSU can use an ordinary RJ-45 patch cord.

In WPA3, the Simultaneous Authentication of Equals (SAE) protocol replaces the 4-way handshake, which has been found to be vulnerable to various attacks.

In a wireless distribution system (WDS) setup with repeater mode, all APs must use the same channel to maintain the communication between the main AP and repeaters.

The system uses the subnet 0.0.0.0/8 when a specific address is unknown and typically used as a source address by a client seeking a Dynamic Host Configuration Protocol (DHCP) lease.

The flow label is for quality of service (QoS) management, such as for real-time streams. The security engineer sets the flow label to 0 for packets not part of any delivery sequence or structure.

The arp -s IPAddress MACAddress adds an entry to the ARP cache. Under Windows, the network administrator needs to enter the MACAddress with hyphens between each hex byte.

The first 8 bits indicate that the address is within the multicast scope 1111 1111. A multicast address sends a packet from a single source to multiple network interfaces.

Another way to indicate a multicast IPv6 address is ff, which is the same as 1111 1111. Unlike IPv4, IPv6 routers must support multicast.

The spanning tree protocol (STP) information gets packaged as bridge protocol data unit (BPDU) multicast frames. Each switch then determines the shortest path to the root bridge by exchanging information with other switches.

When the network is not converged, no communications can take place. Under the original 802.1D standard, this made the network unavailable for extended periods (tens of seconds) during configuration changes.

The interface GigabitEthernet0/0 is the first command. Normally, for a switch interface to process tagged frames, it would have to be configured as a trunk port. This adds a lot of configuration complexity.

IP scanning uses lightweight standalone open source or commercial tools, such as Nmap, AngryIP, or PRTG. An IP scanner is a tool that performs host discovery.

A server administrator is analyzing a normal Transmission Control Protocol (TCP) Teardown connection to their servers. How many FIN-WAIT states does the client go through during this process?
	The client goes through two FIN-WAIT states. In the first step, the client sends a FIN segment to the server and then enters the FIN-WAIT1 state.

RTP Control Protocol (RTCP) is a session on each RTP stream that monitors the quality of the connection and provides reports that the network stacks can use to tune Quality of Service (QoS) parameters.

Cisco's proprietary Hot Standby Router Protocol (HSRP) allows multiple physical routers to serve as a single default gateway for a subnet. Each router must have an interface connected to the subnet, with its own unique MAC address and IP address.

Review Leaf, and spine topologies

A Unified Threat Management (UTM) appliance enforces a variety of security-related measures, combining the work of a firewall, malware scanner, and intrusion detection/prevention. A UTM centralizes the threat management service, providing simpler configuration and reporting than isolated applications spread across several servers or devices.

Packet captures contain every packet that is sent and received by the network. By using a program like Wireshark to analyze the packet captures, you can see what kind of information and metadata is contained within the packets. By conducting this type of packet analysis, an attacker (or cybersecurity analyst) can determine if software versions are being sent as part of the packets and their associated metadata.

The Domain Name System (DNS) uses port 53 and is a hierarchical and decentralized naming system for computers, services, or other resources connected to the Internet or a private network. Split Domain Name System (Split DNS) is an implementation in which separate DNS servers are provided for security and privacy management for internal and external networks. This can provide a security and privacy management mechanism by logical or physical separation of DNS information for network-internal access and access from an insecure, public network like the Internet. Under this configuration, there are two sets of DNS information, and the results are provided based upon the source address of the requester (internal or external).

 The 802.11a (Wireless A) standard utilizes a 5 GHz frequency to provide wireless networking at speeds up to 54 Mbps. Unfortunately, when this was first released, the radios to operate with this standard were fairly expensive, so it did not sell well or become widespread.

The 802.11g (Wireless G) standard utilizes a 2.4 GHz frequency to provide wireless networking at speeds up to 54 Mbps.

An evil twin is the most common way to perform an on-path attack on a wireless network. An evil twin is a rogue wireless access point that masquerades as a legitimate Wi-Fi access point so that an attacker can gather personal or corporate information without the user's knowledge.

The route command is used to create, view, or modify manual entries in the network routing tables of a computer or server.

The 802.11ac (Wireless AC or Wi-Fi 5) standard utilizes a 5 GHz frequency to provide wireless networking at theoretical speeds up to 3.5 Gbps. Wireless AC uses channel bonding to create a single channel of up to 160 MHz to provide additional bandwidth. Wireless AC uses multi-user multiple-input-multiple-output (MU-MIMO) technology to use multiple antennas to transmit and receive data at higher speeds.

If the switchport is configured for 802.1q trunking instead of as an access host port, the workstation will be unable to reach the DHCP server through the port and will fall back to using an APIPA address.

In SNMPv3, the authPriv option ensures that the communications are sent with authentication and privacy. This uses MD5 and SHA for authentication and DES and AES for privacy and encryption.

Which of the following components is used to identify a variable that may be set or read using SNMP?
- Granular trap
- MIB
- Verbose trap
- OID
    (Correct)
    OBJ-3.1: The Simple Network Management Protocol (SNMP) uses ports 161 and 162, and it is a networking protocol used for the management and monitoring of network-connected devices in Internet Protocol networks. A unique objective identifier (OID) identifies a variable that can be read or set using the SNMP protocol. The management information base (MIB) is a translation file that is used to describe the structure of the management data of a device subsystem using a hierarchical namespace containing object identifiers (OID). A trap is an asynchronous notification from the agent to the manager. A trap is sent by the agent to notify the management of a significant event that is occurring in real-time, such as an alarming condition. A granular trap contains a unique object identifier (OID) number and a value for that OID. A verbose trap may contain all the information about a given alert or event as its payload. A verbose trap contains more information and data than a granular trap, and therefore requires more bandwidth to send the verbose trap over the network.

The network administrator is troubleshooting the switchports for a file server with dual NICs. The file server needs to be configured for redundancy, and the dual NICs need to be combined for maximum throughput. What feature on the switch should the network administrator ensure is enabled for best results?
	OBJ-2.3: The Link Aggregation Control Protocol (LACP) is the 802.3ad protocol is used to group numerous physical ports to make one high bandwidth path. This method can increase bandwidth and therefore, throughput. LACP can also provide network redundancy and load balancing. The Spanning Tree Protocol (STP) is a network protocol that builds a loop-free logical topology for Ethernet networks to prevent bridge loops and the broadcast storms that result from them. STP is defined in the IEEE 802.1d standard. A Bridge Protocol Data Unit (BPDU) is used by STP to prevent the bridge loops. Load balancing refers to the process of distributing a set of tasks over a set of resources, with the aim of making their overall processing more efficient. Load balancing can optimize the response time and avoid unevenly overloading some compute nodes while other compute nodes are left idle.

Your network relies on the use of ATM cells. At which layer of the OSI model do ATM cells operate?
	OBJ-1.1: In the data link layer (layer 2) of the OSI model, the basic unit of transfer is called a frame. In an ATM network, though, these frames are called cells and are of a fixed (53 octets or bytes) length that allows for faster switching of the cells across the network.

Max is a network technician who just terminated the ends on a new copper cable used between two legacy switches. When he connects the two switches using the cable, they fail to establish a connection. What is MOST likely the issue?`
	OBJ-2.3: There are two types of cable, Straight-through and Crossover. In this instance, a crossover cable would need to be used to communicate with legacy switches since they won't support MDIX. A medium dependent interface crossover (MDIX) is a version of the medium dependent interface (MDI) enabling a connection between corresponding devices, such as a switch to another switch. If the switch doesn't MDIX, then you must use a crossover cable to connect them. Bend radius cannot be the correct answer to this question since copper cables are being used and not fiber cables. Bend radius is a concern when using fiber cables as it leads to increase reflections and a decrease in signal strength. An RJ-11 connector only has 6 pins and is smaller than an RJ-45 connector. The technician would visually be able to see the difference as the RJ-11 connector would not fit properly in the switchports.





