# Network Topologies and Types
A **client server** network is one where some nodes such as PCs and laptops act mostly as clients. The servers are the more powerful computers that application services and resources are provisioned, managed, and secured on.
A **peer-peer** network is one where each end system acts as both client and server. Provision, management, and security is distributed around the network.
**LANs** usually seen in
	Home/residential networks
	Small office/home office SOHO
	Small and Medium enterprise SME
	Enterprise LANs
	Datacenters

**Topology**
Point-Point link. A single link established between 2 nodes.
#topology
Hybrid Topologies:
	Hierarchical star - aka tree topology. Links between nodes in the tree are backbones or trunks because they aggregate and distribute traffic from multiple different areas of the network. 
	Hierarchical star-mesh - nodes at the top of the hierarchy are in partial or full mesh for redundancy.
	Stars of stars -  a WAN might be configured as a star between central office and branch offices, with each site implementing star topology to connect end systems
	Star with ring -  a ring topology might be used to connect geographically separate sites, with each site implementing star topology

### Tiered network hierarchy
Hierarchical models break down large and complex network design into smaller sections based on functions performed

**Three tiered network hierarchy**
Cisco's design of access, distribution, and core.
![[Pasted image 20240123110223.png]]
**Access/Edge Layer** - allows end-user devices to connect to the network. Access layer is implemented for each site using structured cabling and wall ports for wired access and access points for wireless access. Ultimately connected to workgroup switches, referred to as LAN or data switches.
**Distribution/Aggregation Layer** - provides fault tolerant interconnections between different access blocks at either the core or other distribution blocks. Each access switch has full for partial mesh links to each router or layer 3 switch in the dist layer. Usually implements traffic policies, like routing boundaries, filtering, or QoS. Layer 3 switches use application specific integrated circuit (ASIC), meaning they're far faster as processing.
**Core Layer** - provides highly available network backbone. It provides redundant traffic paths for data to continue to flow around the access and distribution layers of the network.


**Spanning tree protocol (STP)**
A means for bridges or switches to organize themselves into a hierarchy. Switch at the top is the root, with the lowest ID and a priority value. Each switch then determines the shortest path to the root bridge by exchanging information with other switches. STP information is packaged as bridge protocol data unit (BPDU) multicast frames.
Admin should set the priority value to make the choice of one switch as root over others. 
![[Pasted image 20240123111913.png]]

**Broadcast storms** is traffic that is recirculated and amplified by loops in a switching topology, causing network slowdowns and crashing switches.
A **switching loop** is where flooded frames circulate the network perpetually. Because switches flood broadcasts, such as ARP or DHCP requests, out all ports, these frames will go down one link to the next switch, which will send the broadcast back up the redundant link, and back to the originating switch.
Spanning tree should shut down the port if there is a loop. 

### VLANs
Some managed switches allow the configuration of virtual LANs (VLANs) to isolate ports to separate broadcast domains. The simplest means of assigning a node to a VLAN is by configuring the port interface on the switch with a VLAN ID in the range 1 to 4,094. Each VLAN is typically configured with its own subnet address and IP address range. Communications between VLANs must go through an IP router or layer 3 capable switch.

Multiple switches can be interconnected to build a network fabric, to allow for enough ports for the hosts on a network. Interconnection between switches are referred to as trunks. One port on each switch would be configured as a trunk port.

VIDs are normally defined by the IEEE 802.1Q standard. Under 802.1Q, per-VLAN traffic is identified by a tag inserted in the Ethernet frame between the Source Address and EtherType fields. The tag contains information about the VID (from 1 to 4,094) and priority (used for QoS functions).

If a switch port participates in a single VLAN, that port can be configured as untagged (access or host port). An untagged port uses the following port tagging logic:
	If a frame is addressed to a port in the same VLAN on the same switch, no tag needs to be added to the frame.
	If the frame needs to be transported over a trunk link, the switch adds the relevant 802.1Q tag to identify the VLAN, and then forwards the frame over the trunk port.
	If the switch receives an 802.1Q tagged frame on an access port, it strips the tag before forwarding it.

A tagged port will normally be one that is operating as a trunk; capable of transporting traffic addressed to multiple VLANs using 802.1Q frame format. 

# Transport Layer Protocols
Layer 4 protocols are concerned with delivery of multiplexed application data. Each application is assigned a port, allowing a big stream of packets to be directed to the right apps. 
Port 0 - 1023 are preassigned to well known server applications, with other ones 1024-49151.
Ports 49151 are designated for private or dynamic use. 
Client ports are also referred to as ephemeral ports or source ports.
A port number in conjunction with a source IP address forms a socket, which is bound to a software process. Its a connection for established data exchange.

### Transmission control protocol (TCP)
Provides connection-oriented guaranteed communication using acknowledgements to ensure delivery has occurred.
![[Pasted image 20240124095304.png]]
TCP header fields ^^^
TCP connection is used to establish a transfer of a single file during client session, like HTTP. It might involve multiple TCP connections being opened with the server, which would be managed using handshake transactions (using TCP flags).
**TCP 3-way handshake**
1. The client sends a segment with the TCP flag SYN set to the server with a randomly generated sequence number. The client enters the SYN-SENT state.
2. The server, currently in the LISTEN state (assuming it is online), responds with a SYN/ACK segment, containing its own randomly generated sequence number. The server enters the SYN-RECEIVED state.
3. The client responds with an ACK segment. The client assumes the connection is ESTABLISHED.
4. The server opens a connection with the client and enters the ESTABLISHED state.
**TCP Connection Teardown**
1. The client sends a FIN segment to the server and enters the FIN-WAIT1 state.
2. The server responds with an ACK segment and enters the CLOSE-WAIT state.
3. The client receives the ACK segment and enters the FIN-WAIT2 state. The server sends its own FIN segment to the client and goes to the LAST-ACK state.
4. The client responds with an ACK and enters the TIME-WAIT state. After a defined period, the client closes its connection.
5. The server closes the connection when it receives the ACK from the client.

### User datagram protocol (UDP)
Connectionless, nonguaranteed method of communication with no acknowledgements or flow co\ntrol.
Used by application layer protocols that need to send multicast or broadcast traffic.
![[Pasted image 20240124100342.png]]

### Common Ports
![[Pasted image 20240124100409.png]]

### Network Tools

**IP Scanner**
	A tool that performs host discovery and can establish the overall logical topology of the network in terms of subnets and routers. Some can combine this with asset or inventory info about each host, often referred to as IP address management (IPAM).
**`NMAP`** 
	Widely used for IP scanning, as an auditing or pentesting tool.
	Basic behavior for nmap is to ping and send TCP ACK packets to ports 80 and 443 to determine if host is present. Nmap can also perform ARP and ND sweeps if on a local network segment. 
`NETSTAT`
	Allows to check the state of ports on the local host. Can be used to identify suspicious remote connections or for service misconfigurations.
**Remote port scanners**
	Nmap scans
		TCP SYN
		TCP connect
		UDP scans
		Port range
The process of identifying an OS or software application from its responses to probes is called fingerprinting.

### Protocol analyzers
Works in conjunction with a packet capture / sniffer tool. Allows you to analyze either a live capture or a saved capture. 
They can parse each frame in a stream of traffic to reveal its header fields and payload contents in a readable format.
You can also perform traffic analysis, allowing you to see bandwidth consumed by each protocol or host, most active network hosts, monitor link utilization, etc..
# Network Services
### Network addressing services

**DHCP Dynamic host configuration protocol**
Provides an automatic method for allocating an IP address, subnet mask, and other parameters when a host joins a network. 

DHCP is normally deployed as a service of a network operating system or through an appliance such as a switch or router. A DHCP server must be allocated a static IP address and configured with a range (or pool) of IP 
addresses and subnet masks plus option values to allocate.

The client can renew the lease when at least half the lease's period has elapsed (T1 timer) so that it keeps the same IP addressing information.

A DHCP relay agent can be configured to provide forwarding of DHCP traffic between subnets. Routers that can provide this type of forwarding are described as RFC 1542 compliant.

This IP helper functionality can be configured on routers to allow set types of broadcast traffic (including DHCP) to be forwarded to an interface. The IP helper function supports the function of the DHCP relay agent.

### Name resolution services

Host names and Fully Qualified Domain Names (FQDNs) replace the hard to remember IPv4 and IPv6 addresses.
Host names are assigned to computers by the admins, usually when an OS is installed. 
FQDN is used to provide a unique identity for the host belonging to a particular network. Its made up of host name and domain suffix. www.google.com. WWW is the subdomain, and the domain suffix is google.com. 
A domain must be registered with a registrar to ensure its unique to the top level domain. 

**DNS Domain name system**
A global hierarchy of distributed name server databases that contain information on domains and hosts within those domains. Top of the DNS hierarchy is the root represented by (.). 
Below that is the top level domains (TLDs). Most prevalent are .com, .org, .net... 
Info about a domain is found by tracing records from the root down through the hierarchy
When a user presents a FQDN to say, a web browser, it should check its local cache for the mapping. If its not found, it forwards the query to its local name server. ![[Pasted image 20240125103213.png]]
Most queries between name servers are performed as iterative lookups, meaning that a name server responds to a query with either the records or the address of a name server at a lower level authoritative to the namespace.
A recursive lookup means that if the queried server is not authoritative, it does take on the task of querying other name servers until it finds the requested record or times out.

### Configure DNS services
`nslookup` 
	`nslookup -Option Host DNSServer` to troubleshoot DNS name resolution
`dig`
	Domain information grouper queries DNS servers 
	`dig host` simple query
	`dig DNSServer host` queries a specific DNS server
	
# Network Applications
**HTTP**
	HTTP enables clients (typically web browsers) to request resources from an HTTP server. A client connects to the HTTP server using an appropriate TCP port (TCP/80, by default) and submits a request for a resource, using a uniform resource locator (URL). The HTTP payload is usually used to serve HyperText Markup Language (HTML) web pages, which are plain text files with coded tags describing how the page should be formatted.

# Network Availability

# Common Security Concepts

#NetworkPlus