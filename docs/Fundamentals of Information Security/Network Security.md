
One strategy for reducing the impact of attacks is *network segmentation*. You can divide a network into smaller networks called *subnets*. You can control the flow of information between these networks. 

You could also secure networks by funneling traffic through *choke points*. It might be the routers that move traffic from one subnet to another, firewalls that filter traffic through your networks or portions of the networks, or the application proxies that filter the traffic for applications.

A *firewall* is a mechanism for maintaining control over the traffic that flows in or out of networks. Usually placed between points where the level of trust changes, like the border between the internal network and the internet. They work by examining *packets* moving through the network to determine which ones it should allow in or out. 

Packet Filtering

**Stateful Packet Inspection** firewalls uses a state table to keep track of the connection state and allows traffic that is part of a new or already established connection.

**Deep Packet Inspection** firewalls analyze the actual content of the traffic that flows through them. Privacy concerns.

**Proxy Servers** are special kinds of firewalls that provide security and performance features for applications. They serve as choke points and allow you to log the traffic that goes through them. 

**DMZs (demilitarized zone)** is a layer of protection that separates a device from the rest of the network. You do this by using multiple layers of firewalls.![[Pasted image 20231007143617.png]]
It creates a zone that allows public facing servers to be accessed from the outside while both providing a measure of protection for them and restricting traffic from those servers from penetrating more sensitive portions of your network.

**Implementing Network IDS (intrusion detection systems)** 
	Hardware or software tools that monitor networks, hosts, or applications for unauthorized activity. They're either **signature-based detection** or **anomaly-based detection.**
	SB IDS act like most av systems. It compares signatures to incoming traffic signatures that might be in a database of known attacks.
	AB IDS works by determining natural traffic and activity in a network and measuring against current traffic to detect patterns that aren't present normally.

Packet crafting attacks use packets of traffic that carry attacks or malicious code designed to avoid detection by IDS.

A **Honeypot** is a system that can detect, monitor, and sometimes tamper with the activities of an attacker. You configure them to deliberately display fake vulnerabilities or materials that would make the system attractive to an attacker.
You can expand them into networks of them called honeynets. It connects multiple honeypots with varying configurations and vulnerabilities, with a centralized instrumentation for monitoring them all. https://www.honeynet.org

Tools that can map the topology of firewalls. **Scapy** is well known for such efforts. It can construct specially craft ICMP packets that evade normal measure put in place to prevent you form seeing the devices that are behind a firewall. You can also script it to manipulate network traffic and test how firewalls and IDS respond. 
#ITSec