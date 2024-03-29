**Understand 6.1**
**OSI and TCP/IP Models**
	OSI 7 layer model maps technologies, protocols, and messages across a stack of notional layers to enhance discussion of networking topics #OSI
	TCP/IP model is a 4 layer model that nobody besides Cisco uses anymore
	They don't match up perfectly
**Network topologies**
	Bus
	Ring
	Mesh
	Star
**Network relationships**
	Peer-peer (P2P)
		networked machines communicate directly with each other, sharing storage/processing power
	client-server
		client machines (general purpose machines) connect to servers (single purpose, specific use); servers are shared among clients on the network
**Transmission media types**
	wired
		twisted pair: copper, cheap, flexible
		coaxial cable: copper, heavier
		fiber optic: glass/ceramic, expensive, fragile
	wireless
		802.11 - family of standards
		easy to connect/intercept/surveil
		should encrypt WPA2 or WPA3
**SDN and SDWAN**
	SDN: abstracting the network function away from the underlying hardware, and allowing fast, efficient, automated control
	SD-WAN: abstracts WAN technologies away from hardware, allowing implementation of company-wide policies/processes across geographically distinct locations
		WAN: Wide area network
**Commonly used ports and protocols**
	ftp - send files, 20 and 21
	ssh - 22
	telnet - 23
	smtp - 25
	http - 80
	ntp - 123
	snmp - 161

**Understand 6.2**
**Distributed denial of service (DDOS)**
	DOS: any type of attack intended to affect the availability of the system
		could include: shutting down power, destroying components, blocking traffic, rendering system inoperable
		example: teardrop attack
	DDOS: using multiple attacking machines simultaneously to target the intended victim
		typically, involves flooding the target with traffic
		often uses intermediaries, sometimes without the knowledge of the owners ("botnet")
		example: Smurf, Ping flooding, SYN flood
**Man in the middle**
	situation where an intermediary is between 2 parties engaged in communication
	could affect any and all portions of the CIA triad
		eavesdropping/surveillance...confidentiality
		modifying data in transit....integrity
		disconnecting one party...availability
**Domain name system poisoning**
	DNS: the method used to relate IP addresses to specific URLs
	in DNS poisoning, the attacker changes the relevant IP address in the victim's DNS cache, redirecting traffic to an illegitimate site
**and countermeasures**
	CNDs, content delivery networks
	might be useful to remove single points of failure
	its a way to deliver content in an easier and more efficient way to users

**Understand 6.3**
**Network access controls, standards and protocols**
**Remote access operation and configuration**
	thin client
		client device has no/limited local processing/storage capacity; can only function when connected to centralized assets
		limits potential harm/risk
	virtual private network (VPN)
		creates a secure "tunnel" across untrusted networks 
		allows remote users to have permissions equivalent to what they would have if they were using internal devices
		typically uses encapsulation and encryption
		terms to know:
			point-point tunneling protocol (PPTP)
			Layer 2 tunneling protocol (L2TP)
			IPSec
**802.1x**
	international standard for authenticating device requests to join a network
	defines "Extensible Authentication Protocol (EAP)"
		device/user contacts an authenticating mechanism (server), and presents credentials (user/pass; certificate; etc)
		authenticator determines whether access is allowed
		many varieties/similar approaches have been created over the years
			LEAP, MS-CHAP, PEAP, etc..
**RADIUS and TACACS**
	RADIUS: remote access dial in user service
		client/server protocol for authentication, authorization, and accounting
		can use TCP or UDP
		uses authentication schema such as PAP, CHAP, and EAP to confirm user's credentials
	TACACS: terminal access controller access control system
		authentication scheme for centrally managed network access systems
		mostly replaced by TACACS+ or RADIUS

**Understand 6.4**
**Logical and physical placement of network devices**
	inline
		devices that route data between networked machines
		ie routers, switches, firewalls
	passive
		networking: network nodes only follow preset instructions in directing network traffic (mainly routers)
		monitoring: a device that surveils traffic in order to detect anomalies IDS
	virtual
		networking architecture and rules are not defined by physical connections, but by software arrangement; aka SDN
**Segmentation**
	isolating portions of the network (groups of devices) from each other based on their sensitivity/use
		physical/logical: network elements might be physically isolated (changing which cables connect to which devices) or logically isolated (with software and rules like SDN)
		data/control plane: in SDN, the control plane is the conceptual layer where rules are set, and the data planes is where they are followed
	SDN: Application plane -> APIs -> Control Plane -> Rules/Software -> Data Plane -> Hardware/Data
	Virtual local area network (VLAN): creating rules within the LAN that enforce logical isolation
	Access control list (ACL): set of rules in switches/routers that determine which systems/traffic are allowed on the network
	Firewall zones: using firewalls to enforce traffic rules, instead of routers/switches
	Micro-segmentation: most often used in context of cloud/virtualized environments, where specific rulesets can be applied to individual virtual machines, functions, or users; extremely granular isolation
**Secure device management**
	ensuring that only approved users/systems/devices can get access to sensitive data/networks
	typically used in environments where users can utilize their own personal devices to access assets owned by their organization (BYOD)
		generally includes some form of mobile application management (MAM) or mobile device management (MDM) solution
			inventory/enrollment
			monitoring
			enforcement

**Understand 6.5**
**Firewalls and proxies**
	Firewalls
		a solution typically used to inspect and filter traffic between networks
		hardware/software
		often located on perimeters of networks
		"next generation": provides additional functions
		web application firewall: specifically monitors HTTP traffic
		similar to IDS/IPS, can use definitions, historical/behavioral data, content, and/or rules
			"stateful": understand the order of protocols
		proxy: a solution (often a firewall) that acts as an intermediary between communicating devices
**Intrusion Detections Systems, and Intrusion prevention systems**
	Typically used to monitor internal traffic
	Intrusion detection system (IDS)
		discovers anomalous activity/threats and sends an alert
			definition-based
			behavioral/historical
			rule-based
	Intrusion prevention system (IPS)
		functions as an IDS, but also performs a response action (blocking a port, suspending an account, etc..)
**Routers and switches**
	switches: connects network segments
		typically operate at OSI layers 2 and 3
		user physical address to route data
	routers: connect networks
		typically operate at OSI layer 3 and 4
		use logical addresses to route data
**Traffic-shaping devices**
	Wide area network (WAN) optimization
		efforts to reduce communication degradation due to dropped packets and congestion
		may involve:
			deduplication (removing redundant traffic from communications)
			compression (shrinking data sizes)
			caching (storing data locally instead of sending it repeatedly)
			forward error-correction (sending extra packets with the same data in order to preclude requests to retransmit data)
			rate limits (restricting consumption per user/system)
	load balancing
		spread workload across multiple systems/devices
		parallel processing and clustering

**Understand 6.6**
**Wireless technologies**
	Cell phones work by connecting to a local tower; the tower forwards the connection to another tower or a satellite, which passes the connection to a tower near the recipient, which connects to the recipient's phone
	4G vs 5G
		5G offers more bandwidth, energy efficiency, and connections per tower
	WiFi
		802.11 family of protocols
		use AES 256
	Bluetooth
		sometimes referred to as "personal area network"
		limited-range communication standard often used for auxiliary devices
		can be subject to interception, surveillance, highjacking
	NFC 
		proximity cards
		if NFC shows up on your exam, I will buy you dinner :)
**Authentication and encryption protocols**
	Wired Equivalent Privacy (WEP)
		don't use it
		deprecated because symmetric keystream repeats too soon
	WiFi Protected Access (WPA)
		uses TKIP (temporal key integrity protocol)
		don't use it
		deprecated because the algorithm isn't strong enough
	Use WPA2 with AES256
	Extensible Authentication Protocol
**IOT**
	Typically used in consumer appliances
	common elements:
		not much local processing/storage
		not much security
		interface with physical realm