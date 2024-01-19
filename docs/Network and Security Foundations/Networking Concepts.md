# TCP/IP and OSI
![[Pasted image 20231212122409.png]]
### The TCP/IP networking model is made up of four layers: #OSI

1. Application Layer: This layer is responsible for the communication protocols between nodes. The protocols in this layer include hypertext transfer protocol (HTTP and HTTPS), Secure Shell (SSH), and network time protocol (NTP), among many others.
2. Transport Layer: This layer is responsible for the end-to-end transport of data. The protocols that live in this layer are transmission control protocol (TCP) and user datagram protocol (UDP).
3. Network Layer: This layer defines the logical transmission protocols for the whole network. The main protocols that live in this layer are internet protocol (IP), internet control message protocol (ICMP), and address resolution protocol (ARP).
4. Network Interface Layer: This layer establishes how data should be physically sent through the network.

### OSI Model Layers
1. Physical Layer: This layer is responsible for the physical connections of the devices in the network. This layer is implemented through the use of devices such as hubs, repeaters, modem devices, and physical cabling.
2. Data Link Layer: This layer is responsible for the error-free delivery of data to the receiving device or node. This layer is implemented through the use of devices such as switches and bridge devices, as well as anything with a network interface, like wireless or wired network cards.
3. Network Layer: This layer is responsible for the transmission of data between hosts in different networks as well as routing of data packets. This layer is implemented through the use of devices such as routers and some switches.
4. Transport Layer: This layer provides services to the application layer and receives services from the network layer. It is responsible for the reliable delivery of data. It segments and reassembles data in the correct order for it to be sent to the receiving device. It may also handle the reliable delivery of data and any retries of data that are lost or corrupted (for example, TCP does this). This layer is often called the heart of OSI.
5. Session Layer: This layer is responsible for connection establishment, session maintenance, and authentication.
6. Presentation Layer: This layer is responsible for translating data from the application layer into the format required to transmit the data over the network as well as encrypting the data for security if encryption is used.
7. Application Layer: This layer is responsible for network applications (like HTTP or FTP) and their production of data to be transferred over the network.


# Network Media Devices Standards
![[Pasted image 20231213123107.png]]
### UTP cables come in six different standard types as defined by TIA/EIA 568. You can identify the type of cable you have by looking at the writing on the cable itself.

1. Cat3 supports up to 10 Mbps (Megabits per second) for up to 100 meters and is commonly used for phone lines today.
2. Cat4 supports 16 Mbps for up to 100 meters and is not commonly used today.
3. Cat5 is used in Ethernet LANs containing two twisted pairs allowing for up to 100 Mbps up to 100 meters between the device and the switch, hub, or router. This has been practically replaced by the Cat5e specification.
4. Cat5e doubles the number of twisted pairs to four for up to 1 Gbps (Gigabits per second) over up to 100 meters.
5. Cat6 is also used in Ethernet LANs and data centers. Cat6 is made up of four tightly woven twisted pairs (more twists per linear foot) and supports 1 Gbps for up to 100 meters or 10 Gbps for up to 55 meters.
6. Cat6a is an improvement of the Cat6 standard, supporting the same standards and lengths (with the ability to run 10 Gbps over 100 meters maximum), but using a higher quality cable that is more resistant to interference. This is most commonly used in wired networks today.

### There are two types of fiber cables: single-mode and multimode.

1. Single-mode cables are made up of one single glass or plastic fiber. The benefit of a single fiber cable is the ability to carry higher bandwidth for 50 times the distance of a multimode cable. This requires higher cost electronics to create the light and thus is typically used for longer distances (hundreds or thousands of kilometers) and higher bandwidth applications.
2. Multimode cables are wider in diameter due to light modes being sent across the cable. Multimode fibers are highly effective over medium distances (500 meters or less at higher speeds) and are generally used within a LAN. They are also less expensive than single-mode fiber due to the potential for use with LEDs and other lower-cost options for creating the light.
- **ST**: This stands for a straight tip connector. This was the most commonly used connector with multimode fiber until the mid-2000s. It was used on campuses, corporate networks, and for military purposes. Today, LC connectors are usually used instead, as they are denser and more convenient at almost the same cost.
- **LC**: This stands for lucent connector. This is a smaller version of the standard connector (SC). This supports more ports to be used in the same space. This is probably the most common type used in corporate data centers today and is usually used with SFP (small form-factor pluggable) transceivers.
![[Pasted image 20231213124124.png]]
![[Pasted image 20231213124135.png]]

# Network Commands
ifconfig
nslookup
traceroute
whois

What does the address resolution protocol (ARP) cache map?
	IP addresses to MAC addresses


# Network Types

PAN- personal devices 20-30m, ie wireless printer, mouse, etc to a computer
LAN - Local Area Network. House or Office. Uses switch to provide connectivity
WLAN - Wireless Local Area Network. Uses a router to provide connectivity
CAN - Campus Area Network. Networking of multiple LANs across a limited area. CAN would link multiple LANs together similar to the way a WAN does.
MAN - Metro Area Network. 
WAN - Wide Area Network. ie like the WWW
SAN - Storage Area Network. ie like a LAN but for storage
![[Pasted image 20231219124924.png]]
![[Pasted image 20231219124908.png]]

# Network Topologies
### BUS topology
![[Pasted image 20231219125518.png]]
One long cable with devices tapped in along the way, and terminators on either end. Terminators absorb the extra signals. Downside is that if the cable gets cut the terminator disappears and results in lots of noise, errors and weak signal. IE: Cable modem -> Router.

### Ring Topology
![[Pasted image 20231219125740.png]]
Each device connects in a circular configuration. Each computer passes to the next until it comes back to the original computer (in a circle). Sometimes dual ring to preserve connectivity. 
This behavior can be found in computers running ring-based protocols such as token ring or fiber distributed data interface (FDDI).
This dual-ring topology is commonly found in fiberoptic networks, such as the synchronous optical network (SONET) ring.

### Star Topology
![[Pasted image 20231219125935.png]]
Most common in use currently. Consists of a central network device like a switch or router, where all the devices talk to that switch/router. Makes it possible for any device to talk to any other device on the network. Efficient topology and makes running physical cables easier.

### Mesh Topology
![[Pasted image 20231219130103.png]]
Every device is connected directly to every other device. Physically, nearly impossible when connecting more than 2/3 devices because of the cables. Would give every device access to every other device.
The nodes may connect using Wi-Fi or radio signals or by virtual links such as virtual private networks (VPNs). Another example of a mesh network is a collection of routers that are able to communicate with each other and learn the best path for traffic to take when passing from node to node in the mesh.
# Network Architecture
Architecturally speaking, there are two extremes in networking and computing architecture: centralization and decentralization. In between these extremes, however, are two variants: client/server and peer-to-peer. In practice, most organizations use a mixture of these approaches, depending on the application and use case

### Centralization
Instead, the computing and networking resources are hosted in a remote centralized data center, such as a corporate headquarters or a cloud data center. In some ways, cloud computing has allowed a strong centralization approach to make a comeback. You can perform the heavy processing in the cloud without concerns about the hardware of the user’s device.
By placing the computing and networking power in a central location, the owners and operators of the applications can better control the performance and availability of the applications.

### Decentralization
An approach that puts the computing power in the user’s device rather than a data center.
Mismanaged local security could allow data to fall into the wrong hands or even leave the organization on portable drives.
Data created by one user may have been incompatible with other users due to differences in operating systems, application versions, or even applications themselves, such as WordPerfect versus Word.
Systems are able to operate without a network connection because everything is available locally. Ideal for portable systems. Also minimizes points of failure, as the computer is its own point of failure and doesn't rely on other computers.

### Client/Server Model
The client/server model is very popular with enterprise applications such as email and databases, but client/server applications can be found in organizations of nearly any size
Centralized server --- Decentralized client computer
The client/server model allows application designers to implement advanced user interfaces that would not otherwise be possible in a web-based or terminal-based application.
Though the data is stored centrally, the data entry and scanning are performed by the client computer. This could lead to data inconsistency issues if multiple users have the client software installed but they are running different versions of the client software

### Peer to Peer Model (P2P)
Workgroups and very small companies may favor the simplicity of the peer-to-peer model for sharing data as opposed to creating a dedicated server.
Client computers act as both servers and workstations because they share files and printers while allowing a user to log on and use the client computer for normal tasks.

### Wired v Wireless
It is important to note that the network architecture does not depend on whether your network is wired, wireless, or a mixture of the two. You can operate a client/server network using wireless networking just as easily as you can with wired networks. The difference comes down to a couple of factors: portability versus stability.
# Virtual and Cloud Computing
There are two types of hypervisors: Type 1 (bare metal) and Type 2 (hosted). Both types can host VMs; however, they have very different use cases. Type 2 hypervisors, which you will learn about first, look and feel like any other application that you may run on your laptop. Type 1 hypervisors typically requires dedicated hardware and are installed as that machine’s operating system, making them more commonly found in data centers than in home networks.
![[Pasted image 20231219141452.png]]

### Cloud Computing
Consider the meaning and business implications for some of the more well-known and accepted characteristics of cloud computing: on-demand, self-service, resource pooling, elastic, accessible, and measurable.
![[Pasted image 20231220132052.png]]

IAAS (Infrastructure as a service)
	Manages the underlying infrastructure like servers, networking, storage, firewalls, and services. They deploy VMs and Middleware like an on-premise structure. Organizations get full control of the platform

PAAS (Platform as a service)
	Service provider offers the platform on which you build the code instead of hosting a VM on the cloud. Provider manages the underlying infrastructure, firewalls, and networking. Also decides what VM the code will run on and how they're controlled.

SAAS (Software as a service)
	Provider runs the entire stack of physical infrastructure, VMs, OSs, middleware, and applications. IE like GMAIL or Outlook. 

XAAS (X as a service)
	X represents anything like a directory service, backup, or a database. 
	DBAAS (Database as a service) provider runs the database for you and takes care of updating the DB and the OSs.

Private Cloud
	Equipment hosted within a single company’s on-premises data center. The company purchases or leases the computer, storage, and networking hardware and maintains the data center facilities. If a failure occurs, the company is responsible for repairing the problem themselves because all the equipment belongs to and is managed by them.

Public Cloud
	There are many public cloud providers, but some providers, such as Amazon Web Services (AWS), Microsoft Azure, or Google Cloud Platform (GCP), are more well-known because of their marketing and experience in the industry. As with "private cloud," the term "public cloud" refers to the ownership and maintenance of the underlying infrastructure and facilities. In the case of a public cloud, the cloud provider is responsible for maintaining the hardware and repairing the infrastructure instead of the customer.

Community Cloud
	Community clouds are uncommon in the commercial sector but may be found in universities or government agencies. These clouds are data centers that are jointly owned and operated by the tenants.

Hybrid Cloud
	The term hybrid cloud refers to a combination of private cloud and public cloud and is most commonly associated with companies that extend their applications and services between their own data center and that of a public cloud provider's. This may be done to allow the company easy access to additional computing resources during times of burst demand, or as a way to host most of their services in the public cloud with the exception of the few applications that are subject to regulatory controls and must remain at an on-premises data center.

Multi-Cloud
	Multi-cloud is the concept of leveraging the services of multiple public cloud providers, such as hosting your website at AWS and GCP and balancing the users between these providers. This concept, in practice, can add redundancy and flexibility.

#NetworkSec