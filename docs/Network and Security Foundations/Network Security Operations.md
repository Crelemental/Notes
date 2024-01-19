# Firewalls, IDS, IPS

### Firewalls
Network firewalls are barriers that intercept and inspect traffic moving from one area of the network to another. Firewalls come in many forms and function. Some might be physical appliances in data centers while some are virtual operating as VMs. Others known as host-based firewalls that operate as apps on workstations and servers. 
### Packet Filters
A firewall that operates at Layer 3 and 4 of the OSI model (network and transport). That equates to IP address (layer3) and the TCP/UDP port (layer4) of the traffic passing through a firewall. They inspect ingress (incoming) and egress (outgoing) traffic and compare it to a database of packet filter rules that decides if it should allow or deny the traffic (forward or drop).
These firewalls only care about the address label (header) of the packets and don't inspect the contents of the payload, meaning dangerous payloads can pass if it comes from approved source and destination values.
### Circuit-Level Gateways
A devices that operates as a middleman between 2 or more systems to help conceal the identity of the client and server. The gateway may change the IP and port number of traffic to allow 2 networks to communicate that otherwise couldn't. They're the foundation of network address translation (NAT) and port address translation (PAT), which are commonly used in firewalls to allow private IP address ranges to communicate on the internet.

### Stateful Inspection
Since TCP requires a ack packet in response to a syn packet, there would have to be at least 2 firewall rules: allowing the sender to send data to the recipient, and one that allows the recipient to respond back to the sender. This would require many rules for many recipients. Firewall vendors implemented a feature called stateful inspection. It allows a firewall to identify traffic as conversational and automatically creates temporary firewall rules to permit the response traffic to flow back to the sender. So with this in place, you only need to create 1 rule in the firewall that allows communication to begin. (This is on layers 3 - 5  on the OSI model).

### Application Level
Proxy servers could act as a middleman, reading and parsing traffic payloads, forwarding it to the destination if its safe. These types of firewalls are usually called application-aware firewalls, or Layer 7 firewalls because application is the 7th layer of the OSI model.

### IDS and IPS
These are advanced security solutions that can identify malicious traffic on a database of known behaviors and payload signatures. IDSs monitor the network to detect threats, while IPSs intercept and block threats.

Both can operate in tap mode where they are attached as listening devices only, which works well for IDSs. 

IPSs must be configured in-line as it should be in the middle of a traffic stream. They can be the choke point in network systems, bridging the traffic while being invisible and inspect every packet coming through it. If it detects and anomaly, it can alert the admins or block the traffic immediately. When it blocks viruses and malware, its called reputation-based protection as it blocks it based on how often that file is found to have viruses. 
# OSI and Security
#OSI 
### Layer 1: Physical
A wired network using Cat6 cables might be prone to eavesdropping, while one with fiber optic cables isn't and would provide greater security. All physical vulnerabilities and threats can be Layer 1 risks, ie like locks on doors and server racks. If physical access is gained, it lowers effectiveness of other security measures in other layers.
### Layer 2: Data Link
Use of WPA2 or WPA3 wireless security with long and complex passphrases can lower the risk of brute force password crackers.
Wired networks are susceptible to ethernet based attacks like **ARP poisoning**, which allows attackers to eavesdrop on all network traffic sent through an ethernet switch. The attacker sends ethernet frames that poison and overwhelm the switches FIB (forwarding information base) causing it to flood every port with every frame it receives. Using a packet sniffer with that can allow the attacker to analyze the received frames and gather info. An IPS is best defense against this.
**VLAN hopping** attacks are also possible, as a misconfigured switch port in trunk mode would allow a hacker to send and receive traffic on any VLAN on the switch, allowing them to join a network normally not available to them if they get access to that computer (connected to the trunk port),
### Layer 3: Network
Where IP and ICMP protocols are. The ICMP protocol allows for echo-request and echo-reply used by the ping command, allowing for **Ping attacks**. These can be ping flood DoS attacks. Also a ping sweep attack can be used to detect which computers are online and therefore figuring out which are susceptible to attacks. Can be mitigated with packet-filtering firewalls. 
Spoofing can happen on layer 2 and 3, as it can impersonate a person's computer IP (3) or MAC address (2). IPS systems are best to prevent this attack.
### Layer 4: Transport
TCP and UDP protocols live here. Services open TCP and UDP ports to allow themselves to receive incoming connections from other computers, like port 53 for DNS. An attacker can abuse this by using a **port scanner** that allows them to scan the victim's computer for open ports they can later attack. Use a packet filtering firewall to defend.
### Layer 5: Session
RPC (remote procedure call) is a protocol at layer 5 that is used by computers to execute functions and procedures on other computer, such as a server launching a program or print job. RPC has been the target for a while, but with regular patching its usually mitigated.
### Layer 6: Presentation
The translation and security layer between applications, allowing computers to encode and encrypt data. Encoding is writing data in a special manner ie like XML or GIF. Encrypting is done at this layer with TLS and the deprecated SSL protocol. Both protocols have been subject to attacks, with the main focus being a mitm attack where the attacker is in between the victim and the encrypted target (like a bank website). The attacker can impersonate the bank's web security by weakness in encryption or fooling the victim into a fake security certificate. Allows the attacker to see everything the victim does without encryption. Can be mitigated using application-layer proxies or an IPS.
### Layer 7: Application
Though you did use HTTPS to encrypt the data between the mobile application and the API, the application is not yet secure. You incorrectly assumed that the API would only receive requests from your mobile application, and therefore the API did not require any special login or authentication process before it forwards requests to the application server. You need to implement authentication between the mobile application and the API. Security professionals use a tool called a vulnerability scanner to detect problems and known bad code that result in vulnerabilities in your applications.
# Encryption Fundamentals
### Symmetric Encryption
Single key. AES
A KMS generates a key, and a master key. 

The sender and receiver must exchange the secret key with each other before encrypting data, in which then it is most vulnerable.
Symmetric key ciphers are fast in how they can calculate the encryption and decryption sequences, making it ideal for large amounts of data.
![[Pasted image 20240105104650.png]]
### Asymmetric Encryption
Two keys. SSL. TLS. IPsec
Its hard to exchange keys prior to data transfer, so PKI (public key infrastructure) is relied upon.
It allows two parties to exchange encrypted data without having first exchange a private/shared key with eachother. 
Each side must create a public and private key. Once the pair is created, the public key is published to a public repository, whereas the private key is kept secret by the owner of the key. If you wish to send this person an encrypted file, you would retrieve their public key from the internet and then use it to encrypt the file. The only way to decrypt the file is to use the recipient’s private key, which should be stored in a very safe place.
PKI can also be used for nonrepudiation and to verify the validity and integrity of data that was sent. Digital signature. The cipher block cant be decrypted if its altered after you signed it, therefore proving the data hasn't changed since you signed it.
It takes lots of computational power to perform encryption on large blocks of data. Therefore there's use of hybrid solutions, combining both types of ciphers in bulk data encryption. ![[Pasted image 20240105105505.png]]
### Elliptic Curve Cryptography
Since PKI is based on mathematical formulas, modern computers can process these equations making the secrecy of the keys not so much. ECC, a new type of asymmetric key creation, uses algebraic structure of elliptic curves to create a key that's smaller than traditional keys, but harder to crack.

![[Pasted image 20240105105841.png]]
![[Pasted image 20240105105956.png]]
# Cloud Security
### Data classification: public, sensitive, restricted
Retention policies dictate how long a piece of data should remain available, either in day-day storage or archive copies. Some data like financial transactions must be kept for extended periods of time. Public cloud providers can offer storage solutions that include data retention policies to protect data from erasure and then deleting when the retention period is over.

### Data Protection
Data is typically not auto backed up by the cloud provider. Same for private clouds. Always worth checking with the provider to determine if a backup exists and how often its created, how long its kept, and how you can retrieve it. 
In a hybrid environment, you may consider backing up the public cloud data to the corporate datacenter. Expensive decision as the provider can charge network transfer fees for data leaving their cloud. You can opt to back up your private cloud to the public cloud as a cheaper solution. 

### Encrypting data at rest
Strongly consider encrypting data at rest, even if you own the server/storage hardware. It provides a physical safeguard for your data as the data remains protected and inaccessible if physically removed.
The key used to encrypt and decrypt thne data is called a Data Encryption Key (DEK). If an attacker obtains it, they can get access to all the encrypted data (or even alter it without your knowledge). 
To avoid this, you can rotate the DEK regularly to limit the time it would be useful for an attacker. Another solution is to encrypt the DEK in the same way you encrypt the data. You use an asymmetric encryption key called a Key Encryption Key (KEK). You will store the encrypted DEK inside a key management server (KMS) that grants the key based on the validity of the KEK.  
### Encryption of Data in Transit
Even in private clouds, the prevalence of malware makes data encryption important to protect against data theft or the manipulation of data in transit. In the case of a hybrid cloud, the wide area network (WAN) link, which connects the private and public clouds, should also be encrypted.
### Application Security
When developing say a web app, and you require to collect credentials, consider using a auth service known as federated identity management. It allows users to auth to you app using federated identity servers at Google, Facebook, etc, where you already have an account.
When google confirms that a user's identity is correct, they send the server a special token that uniquely identifies the user, but doesn't disclose information. 
### Access Control
You must determine who requires access to the data and the degree of access. Like data that everyone has access to but can't change. Always make sure to give users the least amount of privilege to perform duties. 
In private clouds, you can assign permissions to data using internal security authorization controls, like windows file server permissions assigned to users/groups in AD. In public clouds, this might not be possible depending on the provider.
Hybrid clouds, you should configure the public and private cloud providers to use the same IAM (identity and access management) configs. This would standardize user and group names across the clouds making it easier to assign permissions and removes risk of accidentally giving permissions to the wrong users.
### Network Security
Public facing servers on the internet always a exposed to attack and when compromised can allow an attacker to launch additional attacks inside the network. You should isolate these public acing servers when possible to minimize the possible damage an attack can have on a network. IE like a extranet which is a secured region of a private network where firewalls are config'd to carefully inspect traffic entering and leaving the network, and where IPSs can be implemented.
You'll have to manage your cloud based servers. For a private cloud, you can perform the administration using a private network. However, for hybrid clouds, your public server should be behind a firewall and not reachable directly. Instead of opening remote admin ports or service to the internet, consider establishing a VPN or a WAN to your public cloud provider to allow you to manage it as you would in a private environment.

### Cloud Platform Security
Most platforms require authentication to prove your identity and include auth rules like IAM to control what you can access. Some allow for MFA to further verify identity. 
When an application needs to access resources within a cloud provider, it uses a special string of characters known as API keys. You will have to configure the application to auth using the service account and API key rather than a username and password.
Usually public cloud providers keep detailed audit logs of actions taken within their system to help you account for changes and to discover unauthorized use of credentials. Private clouds may or may not do this, depends on the governance policies.

### Clouds
Private Cloud
	Scalable, single tenant clusters of computing, storage, and networking resources owned and maintained by a single company (usually located within a data center belonging to that company). Owner of the equipment bears all the responsibility for the hardware and physical security controls.
Public Cloud
	Hosted by companies, such as AWS, Azure, and GCP. Highly scalable, multi-tenant solutions in datacenters around the world. Providers generally responsible for physical security and hardware security concerns
Hybrid Cloud
	Combination of services running in both public and private clouds. Security concerns typically fall along the lines of the owners of the equipment, with the addition of the data link between the cloud networks (possibly maintained and secured by a 3rd party).
# Wireless Security
![[Pasted image 20240107132717.png]]
3DES
	A symmetric encryption algorithm that uses the DES algorithm 3 times in a row to encrypt data. DES can be compromised by brute force now in less than a day (56bit). 3DES is more complex but can still be compromised. Generally, its been phased out of use. 

AES
	Advanced Encryption Standard, considered a very secure form of encryption today, but might not be with quantum computing and better computing power. Its used with 128, 192, or 256 bit keys. Longer keys are harder to crack but require more computing to encrypt data. Its a symmetric algorithm like DES. AES-NI (AES New Instructions) within the CPU allows it to process AES encryption at very fast speeds, near 10GB/s. Thus, allowing a computer to encrypt its wireless network traffic using AES and transmit it with minimal effect on performance.

WEP
	 Wired Equivalent Privacy, one of the first wireless standards proposed by IEEE in 1997. Provides same level of security as a wired network for wireless networks. Key is either 10 or 26 hexadecimal digits (40 or 104 bit keys). Can be compromised in a day using brute force methods. All packets are encrypted with that key, very vulnerable. 

WPA
	Wi-Fi Protected Access, and WPA2/WPA3 were defined by the Wi-Fi Alliance and IEEE. WPA was a bridge between the WEP standard and more secure IEEE 802.11i standard. 
	WPA uses a variable length alphanumeric passphrase, which is 8-63 characters in length.
	Utilizes TKIP, temporal key integrity protocol. TKIP gives WPA a significant security boost by generating a new 128bit key for every packet sent on the network. 
	Flaws have been found over time leading to new standards.

WPA2
	Biggest difference between WPA2 and WPA was the mandatory support for Counter Mode Cipher Block Chaining Message Authentication Code Protocol (CCMP) (part of the AES standard now). It provided data confidentiality, authentication, and access control to the network.
	Eventually had weaknesses that led to WPA3

WPA3
	It increased the minimum key strength to 192bit for enterprise mode connections, which are often used in organizations instead of the personal mode. 
	WPA3 eliminated the use of a passphrase or key that allowed computers to join a personal mode network. In WPA3, all devices use Simultaneous Authentication of Equals (SAE) method to exchange the network key. It ensures the initial key exchange in personal mode is more secure by eliminating the need to tell others the key before joining the network.
	WPA3 also implements perfect forward secrecy (PFS) that ensures if a key is compromised, that that key only affects data exchanged in that encryption session only.
	Another improvement is the encryption of management frames, such as de-associating from the network (De-auth attack exploit). 

Ad-Hoc
	All wireless communication is performed in a peer-peer fashion and doesnt require a WAP. Rarely used in homes or offices, but helpful in setting up a new device. Occasionally used to transfer files between devices.

Infrastructure
	WAP or a wireless router is sued to connect devices to the network. A WAP acts like an ethernet switch in wired networking and usually has a physical cable that connects it to the rest of the network. A wireless router is a WAP and a router combined into one, and is often used in home and small business environments to connect to the internet while also providing wireless connectivity to devices.

The 802.1x security standard provides network access control at the port level, whether physical or wireless, and provides authentication standard based on Extensible Authentication Protocol (EAP). Auth is done using username/password but also with PKI (public key infrastructure) certificates.
![[Pasted image 20240107141423.png]]
It grants trusted network access by
	1. Client requests access to network via WPA or wired ethernet switch and provides credentials.
	2. The WAP or switch forward the request to a special authentication server running Remote Authentication Dial-in User Service (RADIUS) or EAP, which then it validates the credentials and determines the user's auth based on policies defined by a network admin.
	3. If the credentials are validated and the user is authorized, the WAP or switch grant network access to the user.
	4. If the user is not authenticated properly or doesn't have the auth to access the network, the WAP or switch will block network access to the user.
802.1x can also check the version of AV or malware scanners on a computer, and if it's not to corporate standard, the network admin can configure a policy to limit network access, such as access to update the AV software.

### Wireless attack types
De-auth Attack
	DoS attack where the attacker can force any client off of the network. The attacker doesn't need to be on the network they're attacking. It prevents access to the network, forces users to reconnect (spooofed AP possibly), and can be used to capture the 4way handshake of WPA to gain intelligence.

Fake Access
	An attacker sets up an illegitimate wireless network using their own WAP or even a cellular hotspot. They usually open this network without any security or auth to entice people in a hurry to connect to the rogue WAP.
	When a victim joins the WAP, the attacker becomes privy to all the data the victim sends or receives. The attacker can also redirect data to a different location or modify contents of data. 
	Users should use a VPN tunnel on their devices to connect to a VPN service in the office if needing to use unsecured networks. 
# User Auth and Access Control
### AAA
Authentication
	The process of confirming a user's identity. A system can confirm this via usernames and passwords or with certificates, as in PKI. Microsoft AD is an example of an auth system that confirms the identity of users via passwords. Web browser uses certificates to validate the identity of websites.

Authorization
	Determines what the user has access to on a system. Its important to apply restrictive permissions to your data and to carefully secure access to servers and network devices. User could intentionally or accidentally gain access to confidential data with unrestricted access. 

Accounting
	Auditing*. There's a need for accounting to verify that the restrictions you put in place are working as expected and there is not attempted or actual unauthorized access. It also includes verifying the correct access control settings on data files, providing a forensic trail after a security breach to figure out how an attacker got in, and what they accessed. The logs should be stored away from where auditing is so attackers cannot change them to hide their path. They should also be immutable to prevent anything from happening. 

### MFA
Multi factor authentication, sometime called 2 factor authentication (2FA) is an optional but highly recommended add on to the authentication process.
The whole point to MFA is that even if someone steals your password through social engineering or brute force attacks, they cannot access your device or data without the key fob or without your fingerprint or face. It makes it alot more difficult for a attacker to impersonate you and access your account.
# Device Hardening
### How to Harden Devices
Change the device's password, and never leave it configured with the default password. Attackers can easily search the web and find the default password for any device ever made. 

Remove unnecessary logins. Those accounts that are not used by you (at home) or the network admin team. Periodically review the list of authorized users on each device and remove those that no longer need access. Also check for any unrecognized accounts that are on the device as well and remove any that are found.

Enforce a strong password policy. Enforce this through the device's operating system, if not the company policy for everyone. Can be done through a tool like Microsoft AD. Each user should be required to change their password frequently (30-90 days) to further limit damage if something is compromised. Check reports if possible on when the last time passwords are changed to enforce this. Also configure MFA if possible for every user. 

Remove unnecessary services. Disable or remove them to reduce risk of attack that service opens up. 

Keep patches up to date. Keep it up to date on the latest security update so that attackers cant exploit a security flaw. 

Limit physical access to the device. If someone has physical access to a device, they can break into it if given enough time. Observe the people that physically interact with these devices as they usually have reset buttons an such that can make it easy to compromise.

Only allow changes from a trusted network. Disallow any changes form the public side of the network device, and change to a wireless AP or router from other wireless devices. It makes sure that the one doing the changes is inside the network.

Require encryption for wireless networks. Enable WPA2, and if possible WPA3 so that the traffic crossing the network is encrypted. 

Audit Access. To help look for suspicious activity and to do forensic analysis for when a device gets breached. Collect these logs and store them off the device. Syslog is a common way to gather logs and sent to a syslog server for storage. 

Backup. Keep backup copies of any device configuration files in case they need to be restored due to misconfiguration, attack, or device replacement. Devices should be backed up and stored remotely. Use the idea of 3-2-1 for backups.
#NetworkSec