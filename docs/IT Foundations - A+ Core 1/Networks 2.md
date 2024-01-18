#Core1 
The core of the Internet consists of high bandwidth fiber optic links connecting Internet exchange points (IXPs). These trunk links and IXPs are mostly created by telecommunications companies and academic institutions. Within the datacenter supporting any given IXP, Internet service providers (ISPs) establish high-speed links between their networks, using transit and peering arrangements to carry traffic to and from parts of the Internet they do not physically own.

![[Pasted image 20231012153103.png]]

Many internet connection types make use of the national and global telecommunications network referred to as the public switched telephone network (PSTN). The core of the PSTN is fiber optic, but at its edge, it is still often composed of legacy two-pair copper cabling. This low-grade copper wire segment is referred to as the plain old telephone system (POTS), "local loop," or "last mile."

Firewalls: They are often implemented as unified threat management (UTM) appliances to perform multiple other security functions.

**TCP/IP**
![[Pasted image 20231013140901.png]]
When IP is being used with a physical/data link specification, such as Ethernet or Wi-Fi, there must be a mechanism to deliver messages from IP at the Internet layer to host interfaces addressed at the Link layer. This function is performed by the Address Resolution Protocol (ARP), which allows a host to query which MAC address is associated with an IP address.

This can be written in slash notation in the form /24. The prefix can also be expressed in dotted decimal as a subnet mask:![[Pasted image 20231013141618.png]]
### Private Address Ranges

The IPv4 address scheme defines certain ranges as reserved for **private** addressing, often called "RFC 1918" addresses after the document in which they were published. Hosts with IP addresses from these ranges are not allowed to route traffic over the public Internet. Use of the addresses is confined to private LANs. There are three private address ranges:

- 10.0.0.0 to 10.255.255.255 (Class A private address range).
- 172.16.0.0 to 172.31.255.255 (Class B private address range).
- 192.168.0.0 to 192.168.255.255 (Class C private address range).


### Dynamic Host Configuration Protocol

As an alternative to static configuration, a host can receive its IP address, subnet mask, default gateway, and DNS server addresses from a **dynamic** host configuration protocol (DHCP) server.![[Pasted image 20231013155951.png]]


### Automatic Private IP Addressing

Hosts have a failover mechanism for when the IP configuration specifies use of a DHCP server but the host cannot contact one. In this scenario, the computer selects an address at random from the range 169.254.0.1 to 169.254.255.254 . Microsoft calls this **automatic private IP addressing (APIPA)** .

### IPV6
2001:0db8:0000:0000:0abc:0000:def0:1234

To shorten how this is written and typed in configuration dialogs, where a double byte contains leading zeros, they can be ignored. In addition, one contiguous series of zeroes can be replaced by a double colon place marker. Thus, the address above would become

2001:db8::abc:0:def0:1234
![[Pasted image 20231013154110.png]]
While it is possible to configure IPv6 addresses statically, most hosts obtain a global and link-local address via the local router. This process is referred to as StateLess Address Auto Configuration (SLAAC). IPv6 hosts do not need to be configured with a default gateway. IPv6 uses a protocol called Neighbor Discovery (ND). ND is used to implement SLAAC, allows a host to discover a router, and performs the interface address querying functions performed by ARP in IPv4.

![[Pasted image 20231013155039.png]]

TCP is used when the application protocol cannot tolerate missing or damaged information. For example, the following application protocols must use TCP:

- HyperText Transfer Protocol (HTTP)/**HyperText Transfer Protocol Secure (HTTPS)** —This protocol is used to deliver web pages and other resources. The secure version uses encryption to authenticate the server and protect the information that is being transmitted. A single missing packet would cause this process to fail completely.
- **Secure Shell (SSH**) —This protocol is used to access the command-line interface of a computer from across the network. It uses encryption to authenticate the server and user and protect the information that is being transmitted. This process would also fail if a data packet is not received.
![[Pasted image 20231013155350.png]]

### DNS
To avoid the possibility of duplicate host names on the Internet, the host name can be combined with a domain name and suffix. This is referred to as a fully qualified domain name (FQDN). An example of an FQDN might be "nut.widget.example". The host name is nut, and the domain suffix is widget.example. This domain suffix consists of the domain name widget within the top-level domain (TLD) .example . A domain suffix could also contain subdomains between the host and domain name.

Immediately below the root lie the top-level domains (TLDs). There are several types of TLDs, but the most prevalent are generic (such as .com, .org, .net, .info, .biz), sponsored (such as .gov, .edu), and country code (such as .uk, .ca, .de). DNS is operated by ICANN ([icann.org](https://www.icann.org/)), which also manages the generic TLDs. Country codes are generally managed by an organization appointed by the relevant government.![[Pasted image 20231013160509.png]]
![[Pasted image 20231013160546.png]]![[Pasted image 20231013160700.png]]

### VLAN
However, the switching fabric on an enterprise network can provide thousands of ports. Placing hundreds or thousands of hosts in the same broadcast domain reduces performance. To mitigate this, the ports can be divided into groups using a feature of managed switches called **virtual LAN (VLAN)** .

Each VLAN must be configured with its own subnet address and IP address range. Communications between VLANs must go through an IP router. Each VLAN must also be provisioned with its own DHCP and DNS services.

As well as reducing the impact of excessive broadcast traffic, from a security point of view, each VLAN can represent a separate zone. Traffic passing between VLANs can easily be filtered and monitored to ensure it meets security policies. VLANs are also used to separate nodes based on traffic type, such as isolating devices used for VoIP so that they can more easily be prioritized over data passing over other VLANs.

