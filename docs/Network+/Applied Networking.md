# Secure Networks 
Effective placement of security appliances depends on segmenting the network into clearly defined areas. At layers two and three, network segmentation enforcement is applied using a combination of virtual LANs and subnets.

The edge firewall can be referred to as the screening firewall or router. The internal firewall filters communications between hosts in the perimeter and hosts on the LAN. This firewall is often described as the choke firewall. A choke point is a purposefully narrow gateway that facilitates better access control and easier monitoring.

Network Address Translation (NAT) was devised as a way of freeing up scarce IP addresses for hosts needing Internet access. NAT is a service translating between a private (or local) addressing scheme used by hosts on the LAN and a public (or global) addressing scheme used by an Internet-facing device. NAT is configured on a border device, such as a router, proxy server, or firewall.

Basic NAT supports multiple simultaneous connections but is still limited by the number of available public IP addresses. Smaller companies may only be allocated a single or small block of addresses by their ISPs. In such cases, a means for multiple private IP addresses to be mapped onto a single public address would be useful. This function is provided by Port Address Translation (PAT). This can be referred to as Network Address Port Translation (NAPT) or NAT overloading or one-to-many NAT.

Network Access Control (NAC) is a system for authenticating endpoints at the point they connect to the network. NAC uses 802.1X port security mechanisms, EAP, and AAA model of supplicants, network access device AAA clients, and AAA servers. NAC enables devices to be authenticated when they connect to switch ports, wireless networks, or virtual private network (VPN) remote access servers.

An intrusion detection system (IDS) performs real-time analysis of either network traffic or system and application logs. Where a firewall applies rules from an ACL, an IDS is configured with signature patterns. Each pattern represents a known type of malicious activity. If a pattern is matched in a traffic stream, the IDS raises an alert.

Compared to the passive logging/alerting functionality of an IDS, an intrusion prevention system (IPS) can provide an active response to any network threats that it matches. One typical preventive measure is to end the session by sending a TCP reset packet to the attacking host. Another option is for the sensor to apply a temporary filter on the firewall to block the attacker's IP address (shunning). Other advanced measures include throttling bandwidth to attacking hosts, applying complex firewall filters, and even modifying suspect packets to render them harmless. Finally, the appliance may be able to run a script or third-party program to perform some other action not supported by the IPS software itself.

### Troubleshoot service issues

**DHCP Server and Scope Exhaustion Issues**
Possible reasons for a client to fail to obtain a lease include:
- The DHCP server is offline. If your DHCP servers go offline, users will continue to connect to the network for a period and thereafter start to lose contact with network services and servers as they come to try to renew a lease.
- No more addresses available (DHCP scope exhaustion). Create a new scope with enough addresses or reduce the lease period. Remember that IP Address Management (IPAM) software suites can be used to track address usage across a complex DHCP infrastructure.
- The router between the client and DHCP server doesn't support BOOTP forwarding. Either install RFC 1542-compliant routers or add another type of DHCP relay agent to each subnet or VLAN.

**Name Resolution Methods**
To troubleshoot name resolution, you should establish exactly how the process works on that specific host. A host can use a variety of methods to resolve a name or FQDN to an IP address. In very general terms, these will be as follows:
1. Check local cache. One complication here is that there are different types of cache and separate caches for individual applications, such as web browsers. On Windows, you can use ipconfig /displaydns and ipconfig /flushdns to monitor and clear the system cache.
2. Check HOSTS. The HOSTS file is a static list of host name to IP address mappings. The default location under Windows is %SystemRoot%\system32\drivers\etc\, while under Linux it is usually placed in the /etc directory. In most cases, HOSTS should not contain any entries (other than the loopback address). Any static entries in HOSTS could be the cause of a name resolution issue. The file can also be used for troubleshooting.
3. Query DNS. A host uses the name servers defined in its IP configuration to resolve queries.

If devices are not in the same VLAN and must communicate, ensure that routing has been configured to enable VLAN-to-VLAN communications. You may also need to configure services such as DHCP relay to allow hosts to contact a DHCP server. Also, if a device is placed in a designated VLAN, its IP configuration must be appropriate in terms of IP address, subnet mask, default gateway, and DNS servers.
# Wireless Networks
### Wireless deployment and troubleshooting

The IEEE 802.11a standard specifies use of the 5 GHz frequency band and a multiplexed carrier scheme called Orthogonal Frequency Division Multiplexing (OFDM). 802.11a has a nominal data rate of 54 Mbps.

The 802.11n standard increases bandwidth by multiplexing the signals from 2 to 4 separate antennas (a radio chain) using a collection of technologies generally referred to as Multiple Input Multiple Output (MIMO).

In basic 802.11 operation modes, bandwidth is shared between all stations because of the CSMA/CA contention protocol. An AP can communicate with only one station at a time; multiple station requests go into a queue. Wi-Fi 5 and Wi-Fi 6 products address this problem using beamforming or Multiuser MIMO (MU-MIMO).

**4G/Long Term Evolution**
Long Term Evolution (LTE) is a converged 4G standard supported by both the GSM and CDMA network providers. LTE devices must have a SIM card issued by the network provider installed. LTE has a maximum downlink of 150 Mbps in theory, but no provider networks can deliver that sort of speed at the time of writing, with around 20 Mbps far more typical of real-world performance.

**5G**
5G uses different spectrum bands from low (sub-6 GHz) to medium/high (20-60 GHz). Low bands have greater range and penetrating power; high bands, also referred to as millimeter wave (mmWave) require close range (a few hundred feet) and cannot penetrate walls or windows. Consequently, design and rollout of 5G services is relatively complex. Rather than a single large antenna serving a large wireless cell, 5G involves installing hundreds of smaller antennas to form an array that can take advantage of multipath and beamforming to overcome the propagation limitations of the spectrum.

### Install wireless networks

In an infrastructure topology, each station is configured to connect through a base station or access point (AP), forming a logical star topology. The AP mediates communications between client devices and can also provide a bridge to a cabled network segment.
The MAC address of the AP is used as the Basic Service Set Identifier (BSSID) . More than one BSS can be grouped together in an Extended Service Set (ESS).

In infrastructure mode, when multiple APs connected to the same distribution system are grouped into an ESS, this is more properly called the Extended SSID (ESSID) . This just means that all the APs are configured with the same SSID and security information.

You can also configure multiple access points to cover areas where it is not possible to run cabling. This is referred to as a wireless distribution system (WDS). You must set the APs to use the same channel, SSID, and security parameters. The APs are configured in WDS/repeater mode. One AP is configured as a base station, while the others are configured as remote stations. The base station can be connected to a cabled segment. The remote stations must not be connected to cabled segments. The remote stations can accept connections from wireless stations and forward all traffic to the base station.

Cisco wireless controllers usually communicate with the APs by using the Lightweight Access Point Protocol (LWAPP). LWAPP allows an AP configured to work in lightweight mode to download an appropriate SSID, standards mode, channel, and security configuration. Alternatives to LWAPP include the derivative Control And Provisioning of Wireless Access Points (CAPWAP) protocol or a proprietary protocol.

### Troubleshoot wireless networks

The nominal link speed is determined by standards support (Wi-Fi 5 or Wi-Fi 6, for instance), use of bonded channels, and optimizations, such as MU-MIMO. If the sender and receiver are far apart or subject to interference, a lower rate will be negotiated to make the link more reliable.

Attenuation and signal strength are measured in decibels. Signal strength is represented as the ratio of a measurement to 1 milliwatt (mw), where 1 mW is equal to 0 dBm. dB and dBm units can be combined to analyze losses and gains in signal strength along a communications path.

The Received Signal Strength Indicator (RSSI) is the strength of the signal sent from the transmitter measured at the receiver on the client end. When you are measuring RSSI, dBm will be a negative value (a fraction of a milliwatt) with values closer to zero representing better performance. RSSI and SNR can be measured by using a Wi-Fi analyzer. This type of software can be installed to a laptop or smartphone. It will record statistics for the AP that the client is currently associated with and detect any other access points in the vicinity.

**Channel Interference**
- Co-channel interference (CCI)-This can be more accurately described as contention. When multiple access points use the same channel, opportunities to transmit are reduced. The wireless devices must use CSMA/CA to find opportunities to transmit. CCI can be measured as a percentage referred to as channel utilization. Channel utilization can be measured from the access point or using a Wi-Fi analyzer. As a design goal, a channel should exhibit no more than 50% utilization.
- Adjacent channel interference (ACI)-This occurs when access points are configured to use different but overlapping channels, such as 1 and 3 in the 2.4 GHz band. ACI slows down the CSMA/CA process and raises noise levels.

EMI can be detected by using a spectrum analyzer. Unlike a Wi-Fi analyzer, a spectrum analyzer must use a special radio receiver-Wi-Fi adapters filter out anything that isn't a Wi-Fi signal

### Troubleshoot wireless security

As an alternative to personal authentication, WPA’s enterprise authentication method implements IEEE 802.1X to use an Extensible Authentication Protocol (EAP) mechanism to authenticate against a network directory. 802.1X defines the use of EAP over Wireless (EAPoW) to allow an access point to forward authentication data without allowing any other type of network access. It is configured by selecting WPA2-Enterprise or WPA3-Enterprise as the security method on the access point.
It passes the credentials of the supplicant to an AAA (RADIUS or TACACS+) server on the wired network for validation.

# WAN Links and Remote Access

The service-related entry point at which the access provider's network terminates is called the demarcation point (or demarc for short) or minimum point of entry (MPOE). The demarc point represents the end of the telco's responsibility for maintaining that part of the cabling.

The T-carrier system was developed by the telecommunications provider Bell Labs to allow multiple calls to be placed on a single cable. A T1 line from the service provider is terminated at the demarc on a smartjack or Network Interface Unit (NIU). The smart jack has an RJ-48C or RJ-48X interface on the customer side that is used to connect to the customer’s Channel Service Unit/Data Service Unit (CSU/DSU).

Digital subscriber line (DSL) is a technology for transferring data over voice-grade telephone lines, often referred to as the local loop. DSL uses the frequencies above those used by the human voice as a full duplex communications channel.

**DSL Types**
- Symmetrical DSL (SDSL) is so-called because it provides the same downlink and uplink bandwidth. There are various types of symmetric DSL service. SDSL services tend to be provided as business packages, rather than to residential customers.
- Asymmetrical DSL (ADSL) is a consumer version of DSL that provides a fast downlink but a slow uplink. There are various iterations of ADSL, with the latest (ADSL2+) offering downlink rates up to about 24 Mbps and uplink rates up to 3.3 Mbps. Service providers may impose usage restrictions to limit the amount of data downloaded per month. Actual speed may be affected by the quality of the cabling in the consumer's premises and between the premises and the exchange, and by the number of users connected to the same DSLAM (contention).

The projects to update this wiring to use fiber optic links are referred to by the umbrella term Fiber to the X (FTTx).
The most expensive solution is Fiber to the Premises (FTTP) or its residential variant Fiber to the Home (FTTH). The essential point about both these implementations is that the fiber link is terminated at the demarc.

Carrier Ethernet provisions point-to-point or point-to-multipoint Ethernet leased lines over wide area networks. Carrier Ethernet may also be referred to as a metro-optical provider link. These services can be used by the customer to join multiple sites together or as a way of connecting their enterprise network to the Internet. From the customer’s perspective, Carrier Ethernet has many advantages. The fact that Carrier Ethernet is easily scalable affords businesses the flexibility to match the service to their changing demands.

### Remote Access

These days, most remote access is implemented as a virtual private network (VPN), running over the Internet.
	VPNs depend on tunneling protocols. Tunneling is used when the source and destination hosts are on the same logical network but connected via different physical networks. The **Point-to-Point Protocol (PPP)** is an encapsulation protocol that works at the Data Link layer (Layer 2). PPP is used to encapsulate IP packets for transmission over serial digital lines. 
	PPP has no security mechanisms, so must be used with other protocols to provision a secure tunnel.
	Where PPP works at Layer 2, **Generic Routing Encapsulation (GRE)** works at Layer 3. A GRE packet can itself encapsulate an IP packet (or most other network layer protocol types) as its payload. The "outer" GRE packet is assigned protocol number 47 and has its own IP source and header address fields. The GRE packet is then itself encapsulated in a Layer 2 frame for transmission to the next hop router. Each intermediate router inspects only the outer GRE header to determine the forwarding destination. At the final destination, the receiving router de-encapsulates the GRE packet to extract the inner IP payload and forwards that inner packet to its destination. GRE does not have any mechanisms for authenticating users or devices and so is often used with other protocols in a VPN solution.
	**Internet Protocol Security (IPSec)** also operates at the network layer (Layer 3) of the OSI model to encrypt packets passing over any network. IPSec is often used with other protocols to provide connection security, but is increasingly used as a native VPN protocol.
	**Transport Layer Security (TLS)** over TCP or datagram TLS (DTLS) over UDP can be used to encapsulate frames or IP packets. The main drawback is that as TLS already operates at the session layer, the headers from the inner and outer packets add up to a significant overhead.

Client-to-site is the "telecommuter" model, allowing home-workers and employees working in the field to connect to the corporate network. An SSL/TLS VPN solution uses certificates to establish the secure tunnel. One example is Microsoft’s Secure Socket Tunneling Protocol (SSTP). Cisco’s Layer 2 Tunneling Protocol (L2TP) is also widely used, in conjunction with IPSec. All these solutions require client software to operate. Most VPN solutions use EAP and AAA/RADIUS architecture to authenticate client devices and users.

**Tunnel Types**
- Full tunnel-Internet access is mediated by the corporate network, which will alter the client's IP address and DNS servers and may use a proxy.
- Split tunnel-the client accesses the Internet directly using its "native" IP configuration and DNS servers.

The creation of a remote access server (RAS) should be accompanied by documentation describing the uses of the service, security risks and countermeasures, and authorized users of the service.
- Restricting access to defined users or groups.
- Restricting access to defined times of day or particular days of the week.
- Restricting privileges on the local network (ideally, remote users would only be permitted access to a clearly defined part of the network).
- Logging and auditing access logons and attempted logons.

The VPN router installed in the central office or hub needs to be a powerful machine capable of aggregating high traffic volumes. This VPN router is also referred to as a VPN headend. VPN headends would normally be installed in groups for load balancing and fault tolerance. A VPN headend must be able to scale to meet changing demand levels. The VPN routers installed at the spokes, are referred to as branch office routers.

A dynamic multipoint VPN (DMVPN) allows VPNs to be set up dynamically according to traffic requirements and demand. DMVPN allows for the use of a dynamic mesh topology between multiple remote sites, effectively setting up direct VPNs, rather than the remote sites having to route traffic via the hub. Each site can communicate with all other spokes directly no matter where they are located.

# Organizational and Physical Security 

### Documents and policies
Configuration management means identifying and documenting all the infrastructure and devices installed at a site. Information Technology Infrastructure Library (ITIL®) is a popular documentation of good and best practice activities and processes for delivering IT services. Under ITIL, configuration management is implemented using the following elements:
- Service assets are things, processes, or people that contribute to the delivery of an IT service. Each asset must be identified by some sort of label.
- A Configuration Item (CI) is an asset that requires specific management procedures for it to be used to deliver the service. CIs are defined by their attributes.
- A baseline documents the approved or authorized state of a CI. This allows auditing processes to detect unexpected or unauthorized change. A baseline can be a configuration baseline (the ACL applied to a firewall, for instance) or a performance baseline (such as the throughput achieved by the firewall).
- A Configuration Management System (CMS) is the tools and databases that collect, store, manage, update, and present information about CIs. A small network might capture this information in spreadsheets and diagrams; there are dedicated applications for enterprise CMS.

A documented change management process minimizes the risk of unscheduled downtime by implementing changes in a planned and controlled way. The need to change is often described either as reactive, where the change is forced on the organization, or as proactive, where the need for change is initiated internally.

In a fully documented environment, each task will be governed by a standard operating procedure (SOP). A SOP sets out the principal goals and considerations, such as budget, security, or customer contact standards, for performing a task and identifies lines of responsibility and authorization for performing it. A SOP may also contain detailed steps for completing a task in an approved way, or these steps may be presented as work instructions.

An audit report focuses on identifying and recording assets. There are many software suites and associated hardware solutions available to assist with audit tracking and managing inventory. An asset management database can be configured to store as much or as little information as is deemed necessary, though typical data would be type, model, serial number, asset ID, location, user(s), value, and service information.

A system life cycle roadmap refers to the controlled acquisition, deployment, use, and decommissioning of assets. An audit and assessment report can identify assets that are no longer fully supported by the vendor or that otherwise no longer meet performance or security requirements.

A port location diagram identifies how wall ports located in work areas are connected back to ports in a distribution frame or patch panel and then from the patch panel ports to the switch ports.
- Main Distribution Frame (MDF)-The location for distribution/core level internal switching. The MDF will terminate trunk links from multiple Intermediate Distribution Frames (IDFs). The MDF also serves as the location for termination of external (WAN) circuits. You should ensure that WAN links to the Internet or to remote offices from the MDF are clearly labeled and that key information such as IP addresses and bandwidth is documented. The WAN provider will assign a circuit ID, and you will need to quote this if raising any sort of support issue.
- Intermediate Distribution Frame (IDF)-In a large network, one or more IDFs provides termination for access layer switches that serve a given area, such as a single office floor. Each IDF has a trunk link to the MDF. Make sure that these are clearly labeled and distinct from access ports.

An incident response plan sets out the procedures, tools, methods of communication, and guidelines for dealing with security incidents. An incident is where security is breached or there is an attempted breach. Incident response is one of the most difficult areas of security to plan for and implement because its aims can be incompatible:
1. The immediate aim is usually to protect confidential data or minimize impacts from its loss and re-establish a secure working system.
2. It may also be important to preserve evidence of the incident with the aim of prosecuting the perpetrators. Forensic evidence collection can interfere with re-establishing availability, however.
3. Follow-up or lessons learned analysis will attempt to prevent reoccurrence of similar incidents.

A disaster recovery plan (DRP) addresses large-scale incidents. These will typically be incidents that threaten the performance or security of a whole site. A DRP should accomplish the following:
- Identify scenarios for natural and non-natural disasters and options for protecting systems.
- Identify tasks, resources, and responsibilities for responding to a disaster. Disaster recovery focuses on tasks such as switching services to failover systems or sites and restoring systems and data from backups.
- Train staff in the disaster planning procedures and how to react well to adverse events.

A business continuity plan (BCP) or continuity of operations plan (COOP) is a collection of processes and resources that enable an organization to maintain normal business operations in the face of some adverse event. Continuity planning activity focuses on the functions performed by a business or other organization:
- Business impact analysis (BIA) identifies mission essential and primary business functions and the risks that would arise if the organization cannot fulfill them.
- IT contingency planning (ITCP) or IT service continuity planning (ITSCP) ensures that these functions are supported by resilient IT systems, working to identify and mitigate all single points of failure from a process or function.

Data loss prevention (DLP) products scan content in structured formats (such as a database with a formal access control model) or unstructured formats, such as email or word processing documents. DLP products use some sort of dictionary database or algorithm (regular expression matching) to identify confidential or personal/sensitive data.

A service level agreement (SLA) is a contractual agreement setting out the detailed terms under which an ongoing service is provided. This can be a legally binding formal contract between supplier and customer businesses or a less formal agreement, such as an SLA agreed between internal departments.

A memorandum of understanding (MOU) is a preliminary or exploratory agreement to express an intent to work together. MOUs are usually intended to be relatively informal and not to act as binding contracts.

An industrial control system (ICS) provides mechanisms for workflow and process automation. An ICS controls machinery used in critical infrastructure, like power suppliers, water suppliers, health services, telecommunications, and national security services. An ICS that manages process automation within a single site is usually referred to as a distributed control system (DCS).

A supervisory control and data acquisition (SCADA) system takes the place of a control server in large-scale, multiple-site ICSs. SCADA typically run as software on ordinary computers, gathering data from and managing plant devices and equipment with embedded PLCs, referred to as field devices. SCADA typically use WAN communications, such as cellular or satellite, to link the SCADA server to field devices.

# Disaster Recovery and High Availability

High availability is a characteristic of a system that can guarantee a certain level of availability. The Maximum Tolerable Downtime (MTD) metric states the requirement for a business function. Downtime is calculated from the sum of scheduled service intervals (Agreed Service Time) plus unplanned outages over the period.
- Recovery time objective (RTO) is the period following a disaster that an individual IT system may remain offline. This represents the maximum amount of time allowed to identify that there is a problem and then perform recovery (restore from backup or switch in an alternative system, for instance).
- Work Recovery Time (WRT). Following systems recovery, there may be additional work to reintegrate different systems, restore data from backups, test overall functionality, and brief system users on any changes or different working practices so that the business function is again fully supported.
RTO+WRT must not exceed MTD!
- Recovery Point Objective (RPO) is the amount of data loss that a system can sustain, measured in time units. That is, if a database is destroyed by a virus, an RPO of 24 hours means that the data can be recovered from a backup copy to a point not more than 24 hours before the database was infected.

Some of the main KPIs relating to component reliability are as follows:
- Mean Time Between Failures (MTBF) represents the expected lifetime of a product. The calculation for MTBF is the total operational time divided by the number of failures. For example, if you have 10 appliances that run for 50 hours and two of them fail, the MTBF is 500 hours divided by 2 failures (10*50)/2, or 250 hours. 10*50 = 500
- Mean Time to Failure (MTTF) expresses a similar metric for non-repairable components. For example, a hard drive may be described with an MTTF, while a server, which could be repaired by replacing the hard drive, would be described with an MTBF. The calculation for MTTF is the total operational time divided by the number of devices. For example, say two drives were installed in the server in a RAID array. One had failed after 10 years, but had never been replaced, and the second failed after 14 years, bringing down the array and the server. The MTTF of the drives is (10+14)/2 = 12 years.
- Mean Time to Repair (MTTR) is a measure of the time taken to correct a fault so that the system is restored to full operation. This can also be described as mean time to replace or recover. MTTR is calculated as the total number of hours of unplanned maintenance divided by the number of failure incidents. This average value can be used to estimate whether a recovery time objective (RTO) is achievable.

Site resiliency is described as hot, warm, or cold:
- A hot site can failover almost immediately. It generally means that the site is already within the organization's ownership and is ready to deploy. For example, a hot site could consist of a building with operational computer equipment that is kept updated with a live data set.
- A warm site could be similar, but with the requirement that the latest data set will need to be loaded.
- A cold site takes longer to set up. A cold site may be an empty building with a lease agreement in place to install whatever equipment is required when necessary.

**Power Distribution Units**
The circuits supplying grid power to a rack, network closet, or server room must meet the load capacity of all the installed equipment (plus room for growth). Consequently, circuits to a server room will typically be higher capacity than domestic or office circuits (30 or 60 amps as opposed to 13 amps, for instance). These circuits may be run through a power distribution unit (PDU). A PDU has circuitry to "clean" the power signal, provides protection against spikes, surges, and brownouts, and can integrate with an uninterruptible power supply (UPS).

### High Availability

Multipathing means that a network node has more than one physical link to another node. Multipathing is a default feature of full and partial mesh internetworks, where routers can select alternative paths through the network if a link is not available. Multipathing can be used anywhere that link redundancy is required. Two common additional scenarios are connections to storage area networks (SANs) and Internet access via an Internet Service Provider (ISP):
- **SAN multipathing**-In a SAN, a server uses shared storage accessed over a network link. Multipathing means that the server has at least two SAN controllers each with a dedicated link to the storage network.
- **Multiple ISPs**-If an organization depends on a single ISP for Internet access, that circuit represents a critical single point of failure. Even if there are multiple circuits to the same ISP, problems within that ISP's routing or DNS infrastructure could result in complete loss of connectivity. Contracting with multiple ISPs and using routing policies to forward traffic over multiple external circuits provides fault tolerance and load balancing. You need to ensure that the ISPs are operating separate infrastructure and not using peering arrangements.

Link aggregation means combining two or more separate cabled links between a host and a switch into a single logical channel. From the host end, this can also be called NIC teaming; at the switch end, it can be called port aggregation and is referred to by Cisco as an EtherChannel.

Where NIC teaming allows load balancing at the component level, a **load balancer** can be deployed as a hardware appliance or software instance to distribute client requests across server nodes in a farm or pool. You can use a load balancer in any situation where you have multiple servers providing the same function.
	**Layer 4 switch**-Basic load balancers make forwarding decisions on IP address and TCP/UDP header values, working at the transport layer of the OSI model.
	**Layer 7 switch (content switch)**-As web applications have become more complex, modern load balancers need to be able to make forwarding decisions based on application-level data, such as a request for a particular URL or data types like video or audio streaming. This requires more complex logic, but the processing power of modern appliances is sufficient to deal with this.
# Network Hardening

### General Attack Types
**Foot-printing and Fingerprinting Attacks**
	Foot-printing and fingerprinting are enumeration or information gathering attacks. Footprinting allows a threat actor to discover the topology and general configuration of the network and security systems. Footprinting can be done by social engineering attacks-persuading users to give information or locating information that has been thrown out as trash, for instance. Port scanning specifically aims to enumerate the TCP or UDP application ports on which a host will accept connections.
	Fingerprinting allows a threat actor to identify device and OS types and versions. When a host running a particular operating system responds to a port scan, the syntax of the response might identify the specific operating system. This fact is also true of application servers, such as web servers, FTP servers, and mail servers. The responses these servers make often include headers or banners that can reveal a great deal of information about the server. A threat actor can use this information to probe for known vulnerabilities.
**Spoofing Attacks**
	The term spoofing covers a wide range of different attacks. Spoofing can include any type of attack where the attacker disguises his or her identity, or in which the source of network information is forged to appear legitimate. Social engineering and techniques such as phishing and pharming, where the attacker sets up a false website in imitation of a real one, are types of spoofing attacks. It is also possible to abuse the way a protocol works or how network packets are constructed to inject false or modified data onto a network. The ARP and DNS protocols are often used as vectors for this type of attack.
**Denial of Service Attacks**
	A denial of service (DoS) attack causes a service at a given host to fail or to become unavailable to legitimate users. Resource exhaustion DoS attacks focus on overloading a service by using up CPU, system RAM, disk space, or network bandwidth. It is also possible for DoS attacks to exploit design failures or other vulnerabilities in application software. A physical DoS attack might involve cutting telephone lines or network cabling or switching off the power to a server. DoS attacks may be motivated by the malicious desire to cause trouble. They may also be part of a wider attack, such as the precursor to a spoofing or data exfiltration attack. DoS can assist these attacks by diverting attention and resources away from the real target. For example, a blinding attack attempts to overload a logging or alerting system with events.

### **On-Path Attacks**
**MAC Spoofing and IP Spoofing**
	A host can arbitrarily select any MAC and/or IP address and attempt to use it on the network. A threat actor might exploit this to spoof the value of a valid MAC or IP address to try to circumvent an access control list or impersonate a legitimate server. For this type of attack to succeed, the threat actor must normally disable the legitimate host or there will be duplicate addresses on the network, which will have unpredictable results.
	IP spoofing is also used in most denial of service (DoS) attacks to mask the origin of the attack and make it harder for the target system to block packets from the attacking system. In this type of spoofing, the threat actor does not care about not receiving return traffic.
**ARP Spoofing**
	ARP spoofing, or ARP cache poisoning, is a common means of perpetrating an on-path attack. It works by broadcasting unsolicited ARP reply packets, also known as gratuitous ARP replies, with a source address that spoofs a legitimate host or router interface. Because ARP has no security, all devices in the same broadcast domain as the rogue host trust this communication and update their MAC:IP address cache table with the spoofed address. Because the threat actor broadcasts endless ARP replies, it overwhelms the legitimate interface.
**Rogue DHCP**
	An on-path attack can also be launched by running a rogue DHCP server. DHCP communications cannot be authenticated, so a host will generally trust the first offer packet that it receives. The threat actor can exploit this to set his or her machine as the subnet's default gateway or DNS resolver.

DNS poisoning is an attack that compromises the name resolution process. Typically, the attacker will replace the valid IP address for a trusted website, such as mybank.example, with the attacker's IP address. The attacker can then intercept all the packets directed to mybank.example and bounce them to the real site, leaving the victim unaware of what is happening (referred to as pharming). Alternatively, DNS spoofing could be used for a DoS attack by directing all traffic for a particular FQDN to an invalid IP address (a black hole).

VLAN hopping is an attack designed to send traffic to a VLAN other than the one the host system is in. This exploits the native VLAN feature of 802.1Q. Native VLANs are designed to provide compatibility with non-VLAN capable switches. The attacker, using a device placed in the native VLAN, crafts a frame with two VLAN tag headers. The first trunk switch to inspect the frame strips the first header, and the frame gets forwarded to the target VLAN. Such an attack can only send packets one way but could be used to perform a DoS attack against a host on a different VLAN.

### Wireless Attacks
**Rogue Access Points**
	A rogue access point is one that has been installed on the network without authorization, whether with malicious intent or not. A malicious user can set up such an AP with something as basic as a smartphone with tethering capabilities, and a non-malicious user could enable such an AP by accident.
**Evil Twins**
	A rogue AP masquerading as a legitimate one is called an evil twin. An evil twin might advertise a similar network name (SSID) to the legitimate one. For example, an evil twin might be configured with the network name "compeny" where the legitimate network name is "company." Alternatively, the evil twin might spoof the SSID and BSSID (MAC address) of an authorized access point and then the attacker might use some DoS technique to overcome the legitimate AP.
**Deauthentication Attacks**
	The use of an evil twin may be coupled with a deauthentication attack. This sends a stream of spoofed management frames to cause a client to deauthenticate from an AP. This might allow the attacker to interpose the evil twin, sniff information about the authentication process, or perform a denial of service (DoS) attack against the wireless infrastructure.

### Hardening

- **Disable unneeded network services**-Any services or protocols that are not used should be disabled. This reduces the attack surface of a network appliance or OS. Attack surface means the range of things that an attacker could possibly exploit in order to compromise the device. It is particularly important to disable unused administration interfaces.
- **Disable unsecure protocols**-Sniffing attacks can be mitigated by encrypting the channel over which communications takes place. This means that even if the eavesdropper can listen to the message, he or she cannot understand it without obtaining the encryption key. It is important to understand which protocols are unsecure in terms of using unencrypted channels. This is particularly important when using a channel to authenticate. Unsecure protocols should be deprecated, and secure protocols used instead. For example, the original versions of SNMP are unencrypted. To implement secure SNMP, either configure SNMPv3, which supports encryption, or use an encapsulation protocol such as IPSec to encrypt SNMP traffic.

**MAC Filtering and Dynamic ARP Inspection**
	Configuring MAC filtering on a switch means defining which MAC addresses are permitted to connect to a particular port. This can be done by creating a list of valid MAC addresses or by specifying a limit to the number of permitted addresses. For example, if port security is enabled with a maximum of two MAC addresses, the switch will record the first two MACs to connect to that port but then drop any traffic from machines with different network adapter IDs that try to connect.
	A switch port security feature such as dynamic ARP inspection (DAI) prevents a host attached to an untrusted port from flooding the segment with gratuitous ARP replies. ARP inspection maintains a trusted database of IP:ARP mappings. It also ensures that ARP packets are validly constructed and use valid IP addresses.
**DHCP Snooping**
	Configuring DHCP snooping causes the switch to inspect DHCP traffic arriving on access ports to ensure that a host is not trying to spoof its MAC address. It can also be used to prevent rogue DHCP servers from operating on the network. With DHCP snooping, only DHCP offers from ports configured as trusted are allowed.
**Port Security/IEEE 802.1X Port-Based Network Access Control**
	MAC limiting and filtering and ARP inspection provide some protection against attacks, but they are not a means of ensuring only valid hosts are connecting to the network. Port security refers to the IEEE 802.1X standard’s Port-Based Network Access Control (PNAC) mechanism. PNAC means that the switch performs some sort of authentication of the attached device before activating the port.

**Private VLANs**
	A private VLAN (PVLAN) applies an additional layer of segmentation by restricting the ability of hosts within a VLAN to communicate directly with one another. This might be used by a hosting company to prevent web servers operated by different customers being able to communicate.

**WIRELESS SECURITY**
- **Preshared keys (PSKs)**-Group authentication allows stations to connect to the network using a shared passphrase, which is used to generate a preshared key (PSK). The passphrase should be sufficient length (14+ characters) to ensure a strong key.
- **Extensible Authentication Protocol**-An access point can implement a similar port security mechanism to switches. This is configured on the access point by selecting enterprise authentication. This allows users to authenticate to the wireless network against a RADIUS server using their regular network credential. EAP also allows for device authentication using digital certificates.
- **Captive portal**-A guest network might be configured to perform authentication by redirecting stations to a secure web page. The user must authenticate to the page and meet other administrator-set requirements, such as accepting a use policy, before the station is authorized to use the network.
- **MAC filtering**-As with a switch, an access point can be configured with an accept or deny list of known MAC addresses.
- Geofencing-Can be used to ensure that the station is within a valid geographic area to access the network, such as ensuring the device is within a building rather than trying to access the WLAN from a car park or other external location.
- **Antenna placement and power levels**-Site designs and surveys facilitate robust wireless coverage when all expected areas receive a strong signal. Power levels and channel selection should be tuned so that access points do not interfere with one another or broadcast a signal that stations can "hear" but cannot reply to. The presence of an unusually strong transmitter (30 dBm+) might indicate the presence of an evil twin rogue access point.
- **Wireless client isolation**-Clients connected to a WLAN are normally within the same broadcast domain and can communicate with one another. An access point can be configured to prevent this so that stations can only communicate via its gateway. Peer-to-peer traffic is dropped by the AP.
- **Guest network isolation**-A guest network can have separate security and forwarding policies applied to it than the network that permits access to the corporate LAN. Typically, a guest network is permitted access to the Internet but not to local servers. Most SOHO routers come with a preconfigured guest network. Within an enterprise, a guest network would be implemented using a separate VLAN.


# Cloud and Datacenter Architecture

An approach to infrastructure management where automation and orchestration fully replace manual configuration is referred to as infrastructure as code (IaC).

One of the risks of using a cloud-based solution is that potentially confidential or commercially secret data may be transferred over links that extend beyond the enterprise’s infrastructure and direct control. As such, it is imperative to identify precisely which risks you are transferring; to identify which responsibilities the service provider is undertaking, and which remain with you. This should be set out in a service level agreement (SLA) as a cloud responsibility matrix.

This means that these components must be fully accessible to scripting-representing the ideal of infrastructure as code. Software defined networking (SDN) is a model for how these processes can be used to provision and deprovision networks.

The principal innovation of SDN is to insert a control layer between the application layer and infrastructure layer. The functions of the control plane are implemented by a virtual device referred to as the SDN controller. Each layer exposes an application programming interface (API) that can be automated by scripts that call functions in the layer above or below. The interface between SDN applications and the SDN controller is described as the service interface or as the "northbound" API, while that between the SDN controller and infrastructure devices is the "southbound" API.

The spine and leaf topology provides better support for east-west traffic and the use of SDN and overlay networks within datacenters. A spine and leaf topology has two layers:
- The spine layer comprises a backbone of top-tier switches. Note that while this is described as a backbone, the spine switches are not linked to one another.
- The leaf layer contains access switches. Each access switch is connected to every spine switch in a full mesh topology. The access switches never have direct connections to one another.

**Colocation** means that a company's private servers and network appliances are installed to a datacenter that is shared by multiple tenants. The colocation provider manages the datacenter environment; the company's servers are installed to dedicated rack space on the datacenter floor. The rack or space within a rack is locked so that only authorized keyholders can gain physical access to the server equipment.

In a branch office topology, access to the datacenter or the cloud would be routed and authorized via the hub office. An SD-WAN is a type of overlay network that provisions a corporate WAN across multiple locations and can facilitate secure access to the cloud directly from a branch office or other remote location. It uses automation and orchestration to provision links dynamically based on application requirements and network congestion, using IPSec to ensure that traffic is tunneled through the underlying transport networks securely. An SD-WAN solution should also apply microsegmentation and zero trust security policies to ensure that all requests and responses are authenticated and authorized.


#NetworkPlus