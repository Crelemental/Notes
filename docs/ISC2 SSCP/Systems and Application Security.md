**Understand 7.1**
**Malware**
	literally malicious software, typically programs
	consume resources
	perform action unknown to users
	communicate back to the attacker
	give the attacker some access/control
	cost the target money
	Types:
		rootkits: gives the attacker fundamental root control of the target system
		spyware: gives the attacker data about the target's behavior
		ransomware: encrypts data on target systems; key to decrypt is sold to target
		scareware: frightens the target into installation
		trojans: appears useful to the target, but has attack purpose
		virus: typically a type of malware that attaches to other files/programs to propagate
		worms: self-propagating; harms by over consumption
		trapdoors: in crypto, a function that is difficult/impossible to calculate in one direction, but simple in the other
		backdoors: a secret means to bypass security in systems/software
		fileless: malware that exists only in RAM
**Malware countermeasures**
	scanners
		signature based solutions that check for instances of known malware
		will not detect zero-day exploits or polymorphic malware
	antimalware
		solutions meant to detect, isolate/quarantine, and remove malware from systems
		may be host-based or network-based or both
		often have many of the traits of malware
	code signing
		a means to avoid inadvertent installation of malware when applying patches/updates
		vendor digitally signs patch/update
**Malicious activity**
	insider threat: someone with authorized access uses it in a harmful way; the most common/damaging attacks
	data theft: taking/exposing data in an unauthorized manner; can be done for a number of reasons
	distributed denial of service DDoS
	botnet
	zero-day exploits: attacks/malware/vulnerabilities for which there is no historical public knowledge
	web-based attacks: utilize browsers/apps/web ports for attack purposes: OWASP Top Ten
	advanced persistent threat (APT): long-term, subtle, sophisticated attack, typically thought to be sponsored by an entity with the power of a nation-state
**Malicious activity countermeasures**
	user awareness: users with knowledge of attack types/ability to recognize may be more resistant to attacks that involve users
	system hardening: common approach to securing an environment by reducing the attack surface on systems
		remove all unnecessary functions
		remove all default accounts
		enforce strong access controls
		consider use of host-based countermeasures
		audit/enforce regularly, randomly, and comprehensively
		follow vendor/industry guidance
	patching: updates to systems/software in order to optimize performance/security
		proactive/reactive
		schedule to minimize interruption
		used signed patches
		test patches prior to install
		backup system prior to patch
		always be prepared to roll back
	isolation: systems with limited access to other systems/networks offer reduced exposure if they are suborned
**Social engineering**
	attacks targeting the user instead of the system
	common types play on human nature and emotions
		bluster, seeking aid, blackmail, etc
		often instill a false sense of urgency in the target
		phishing; social engineering ploy via email, with widely-ranging degrees of specificity for targeting and implementation, sometimes used to deploy malware/Trojan horses or to acquire credentials
		impersonation; often involves pretending to be an authorized entity, or someone in authority
**Behavior analytics**
	using past activity as a comparison to current activity, in order to determine anomalies
	machine learning/artificial intelligence: solutions that have sophisticated code which can interpret prior activity to make determinations about current/future situations
		very useful in widespread/continual monitoring, in order to prioritize the attention of human analysts
	data analytics: interpreting trends/patterns from other (often unrelated) data; can be used maliciously or helpfully
**DLP**
	also sometimes referred to as "Data Leak Prevention," or variations on these terms
	remember: "egress monitoring"
	performs 3 major functions for protecting sensitive/valuable data:
		discovery
		monitoring
		enforcement
	typically requires the use of local agents
	typically placed on all devices/network locations where data could leak: database, user endpoints, routers, firewalls, etc

**Understand 7.2**
**Host based intrusion prevention system (HIPS)**
	security solutions located on the user device
**Host based firewalls**
	security solutions located on the user device
**Application whitelisting**
	 the organization creates a catalog of programs that are approved for use by employees
	 might be helpful in BYOD environments
	 difficult to implement, maintain, and optimize (inhibits innovation/staying current with latest tools)
	 outdated term: newer terminology uses forms of "permitted," instead
**Endpoint encryption**
	whole disk encryption / drive encryption
	all data on secondary storage is encrypted; user needs a key to access it
	can be useful in the situation that the device is stolen/lost; can reduce the likelihood of data being exposed
	however, might affect the usage of non-host-based applications/solutions
**Trusted Platform Module (TPM)**
	topic 2.1
	TPM = cryptoprocessor
**Secure browsing**
	basic protocols for web traffic, such as http, don't provide security
	moreover, browser applications commonly harvest large amounts of data about users/sessions
	use of secure browsers, VPN, https, NAT, and proxies may assist in this regard
	VPN - 6.3
	NAT - network address translation; all outbound IP traffic is depersonalized at the perimeter, such that entities outside the organization cannot identify specific machines/users
**Endpoint detection and response (EDR)**
	full threat detection and response toolkit
	more comprehensive and replaces traditional antivirus software
	leverages real-time global threat information
	"EDR endpoint detection and response is the current name for what we used to call antivirus software. Historically, an organization would install antivirus software on all its endpoints, such as workstations, servers and laptops, and the antivirus software would run in the background scanning files as they were accessed and processes as they were initiated. And enterprise grade antivirus solution would feed logs and alerts back to the main administrator console, which was monitored and may have automatic action rules set for things like allow, ignore quarantine or delete antivirus solutions had a terrible track record of causing major performance issues on endpoints like using inordinate amounts of RAM and constantly keeping the disk in use while it scanned in the background." -> "So today, modern enterprises deploy EDR software. EDR is like an entire toolkit versus a traditional antivirus single screwdriver. EDR integrates tightly with the endpoint OS, leveraging the built in protections using much fewer resources like RAM and Disk, which slowed down overall system performance in older antivirus and antimalware, and still feeds back to a local or cloud based admin console. But there are much more options and much more automated responses. EDR is usually cloud based or at least cloud aware. Getting updates in real time, as well as submitting threat samples to the vendor. Signature vials can change on the fly and are much smaller. Yes, you still have controls like allow, ignore, quarantine and delete, but you can also have advanced commands like isolate from the network or immediately alert the console and stop the user from working. In other words, the are in EDR response means you set pre-programmed rules or scripts based on the threat level that might be detected, and the vendor can artificially increase the response to a threat based on real time data. The vendor is seeing from other customers in other locations, also feeding the vendor data. Additionally, EDR is often touted as being an integral part of a SIEM SEM SIM solution or may plug seamlessly into other threat detection tools, such as an integrated firewall appliance at the edge of the network."
	not solely signature based; can identify threats based on behavior or heuristics
	integrates into other security suites to correlate disparate events in an organization
	leverages real-time global threat information

**Understand 7.3**
**Provisioning techniques**
	devices might be provided to user in a number of ways
		allow users to add their own personal devices to the enterprise environment BYOD
		issues devices to users (owned by the org)
		some compromise between these options (such as allowing users to pick from a variety of offered devices)
	issues associated with this practice:
		potential legal conflict about who owns which data
		potential privacy ramifications
		potential labor impacts (overtime/salary)
		lack of uniformity in applying security solutions/configurations
**Containerization**
	abstracting resources at the OS level
		allows installation and execution of applications/programs within the container, independent from the OS used to boot the device
		isolates software/functionality from the underlying hardware/OS
**Encryption**
	topic 5.2, 7.2
**Mobile application management (MAM)**
	topic 6.4

**Understand 7.4**
**Deployment models**
	public
		multiple customers share provider's resources
	private
		a single customer uses provider's resources
	community
		a specific group shares provider's resources
	hybrid
		any combination of two or more of the other models
		typically, used to describe a situation called "cloud bursting," when a customer will use a public cloud when the capacity of the customer's private cloud is exceeded
**Service models**
	Infrastructure as a Service IaaS
		provider owns the facility/hardware/networking; customer provides the build of the VM, the OS, the apps, and the data
		most flexible for customer
	Platform as a Service PaaS
		provider owns the facility/hardware/networking, and typically the build of the VM and OS; the customer provides the apps and the data
		useful if the customer wants to do software development or use a database engine
	Software as a Service SaaS
		provider owns the facility/hardware/networking, the build of the VM, the OS, and the apps; the customer provides the data
**Virtualization**
	abstracting the processing, short term memory RAM, and functions of a computer away from the hardware where it runs
	often referred to as a virtual machine or VM or instance or guest
	relies of a hypervisor; the software that allocates CPU/RAM to the virtual instance
		Type 1: bare metal, runs directly on the hardware
		Type 2: runs on the OS, similar to any other application
		may be subject to "guest escape" if not properly secured
**Legal and regulatory concerns**
	privacy 1.2
	surveillance 7.2
	data ownership: for legal purposes, in almost all cases, data in the cloud is "owned" by the cloud customer
	eDiscovery: searching data stores for any evidence applicable to a specific case; complicated in the cloud
	jurisdiction: a geographic area a court or lawmaking body has responsibility for
	legislation: law; a legal mandate, issued by a lawmaking body
	regulation: a legal mandate, issued by a regulatory agency
	liability: exposure to risk; literally, "legal responsibility for"
**Data storage, processing, and transmission**
	archiving, recover, resilience: the cloud is a useful way of creating centralized backups from a variety of sources, duplicating centralized storage, and spreading data across multiple locations to counter the threat of loss due to specific geographic hazard
	however, there can be limits on transmitting/storing data in particular locations/jurisdictions
**3rd party/outsourcing requirements**
	SLA, service level agreement: typically used in managed provision arrangements; sets objective parameters to ensure both vendor and customer receive full value of the contract
		should include regular, repeated activities/elements 
		each SLA element needs a specific numeric value
		often tied to monetary incentives
		avoid vendor lock-in and vendor lock-out
	data portability: the ease with which data can be moved from a given cloud provider
	data destruction: in the cloud, only cryptoshredding
	auditing: cloud customer generally can't do their own audits of the cloud provider/data center
**Shared responsibility model**
	without going into too much detail, remember that a managed service relationship requires that both parties (customer and provider) negotiate who will be responsible for which aspects of the environment (physical security, logical security, emergency response, connectivity, etc...)

**Understand 7.5**
**Hypervisor**
	topic 7.4
	follow vendor/industry guidance for secure configs
**Virtual appliances**
	almost any device can be virtualized
	remember that virtual devices need proper security controls/configurations, just as hardware appliances would
	bear in mind that security solutions designed for hardware environments may not properly monitor virtual appliances
**Containers**
	topic 7.3
**Continuity and resilience**
	virtual machines are easily duplicated and populated in the environment; this is one of the appeals of virtualization
		this can complicate uniformity
			mutable
				administrators can modify individual virtual machines
				allows customization, but almost impossible to achieve homogenous environment (version control problems)
			immutable
				all virtual machines have the same baseline configuration; only the template for the virtual machine can be modified, and any changes are pushed to all VMs
**Attacks and countermeasures**
	any attack that can be launched against a physical machine can be launched against a virtual machine; except theft/physical contact
	VMs are much more portable than physical devices; consider device encryption, MFA, or other additional safeguards for VMs
**Shared Storage**
	VMs often share underlying resources, including the CPU, RAM, and 2nd/centralized storage
	again, consider encrypting VM snapshots while in storage, and extra protections on centralized storage