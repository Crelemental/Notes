**Understand 3.1**
**Risk management process**
	Risk: The possibility of negative impact
		No such thing as 0 risk or 100% security
	Threat: Something that poses risk
		Can be natural or anthropogenic
		Can be accidental or intentional
	Vulnerability: A path that a threat could exploit to cause negative impact
	Control/countermeasure: Something used to reduce risk
		Can be administrative, physical, or logical
	Acceptable risk/risk appetite/risk threshold:
		The amount of risk an organization will allow
		Typically offset by a related (greater) benefit
		Determined by senior management
**Risk visibility and reporting**
	risks can be catalogued and tracked for both internal risk management and external compliance reporting purposes
	risk register; documents identified and recognized risks, as well as mitigation efforts/controls
		should list those items discovered during a risk assessment/business impact assessment (BIA)
	sharing threat intelligence/Indicators of Compromise (IOC)
		some industries have combined intelligence centers/reporting mechanisms for sharing identified threats/risks
	Common Vulnerability Scoring System (CVSS)
		industry standard for gauging severity and impact of potential risks
		free and open
		used by US federal government in its national vulnerability database (NVD), also free to access
**Risk management concepts**
	impact assessments
		the business impact assessment (BIA) is a holistic review of the organization to determine all possible threats and risks, as well as their impact
			includes all types of security, not just IT
			should start with a complete inventory of all assets
				then, some metric should be used to determine sensitivity/criticality of the assets (establishes "critical path" of the organization)
					ie; like money, volume, or otherwise
			the BIA will be different for every organization
**Threat modeling**
	a method used to perceive the environment/asset from the perspective of the attacker
	common threat model used for exams: STRIDE
		from Microsoft, made open-source
**STRIDE**
	Spoofing: Can the user of this asset pretend to be someone they aren't?
	Tampering: Can the user modify the system/application/data?
	Repudiation: Can the user deny taking part in a transaction that they actually performed?
	Information Disclosure: Does the system/app leak? Data escaping
	Denial of Service: Can the user shutdown the system/app in a way other than approved?
	Escalation/Elevation of Privileges: Can the user increase their own permissions?
**Risk management frameworks**
	NIST Risk Management Framework (RMF)
		800-37 (RMF)
			stresses repeatability, continuous monitoring/improvement, and the use of automation in security controls
			free
			only required for US federal agencies and their contractors
		800-53 (a list of controls to apply to your enterprise, depending on your RMF implementation)
			vendor/product agnostic
			exhaustive
	ISO 27001 - the information security management system (ISMS)
		exhaustive; includes all aspect of a security program (physical, IT, personnel, etc)
		recognized worldwide
		suitable for any environment
		expensive
	ISO 27002 - a list of controls to apply to your enterprise, after conducting/applying the ISMS
**Risk tolerance**
	also known as "risk appetite"
	the amount of risk an organization is willing to accept for a given type of activity
	typically, compared against a related benefit (risk-benefit tradeoff, or risk-reward)
	will be different for every organization
	determined by senior management
**Risk treatment | we're going camping, but there are bears in the wild**
	Avoidance - Don't go camping
	Mitigation - Bring bear spray (still some residual risk)
	Acceptance - Realize we might become bear food, still go camping
	Transfer - Take out life insurance policies on family members

**Understand 3.2**
**Legal and regulatory concerns**
	Jurisdiction: a geographical area where a legislature/court has effect
		different jurisdictions have different rules/laws
	Limitations: private entities are restricted on what they can/cannot do
		collect/use/distribute info
	Privacy: the concept that individual humans have a right to control how information that identifies them is shared/distributed

**Understand 3.3**
**Security assessment and vulnerability management activities**
**Security testing**
	Vulnerability scan:
		Passive, does not fix the vulnerabilities it finds, requires definitions, often automated
	Penetration test;
		Active, testers will try to exploit vulnerabilities they discover
	Monitoring and measurement; continuous/continual improvement
		All major industry bodies (NIST, ISO, SANS). currently recommended an ongoing monitoring and improvement program, to ensure that security efforts keep pace with threats/vulnerabilities, are check in an evolving enterprise environment, and continue to meet the needs of the organization
**Risk review**
	Hardware/software can be penetrated prior to delivery, allowing attackers access to the end user's environment
	Having a third-party monitoring service is a way to elevate assurance products are delivered in a secure manner, and obviate liability.
	Minimum security requirements should be part of any purchase agreement/contract; this is part of the secure acquisition process
	Service level agreements (SLAs) similarly are used to ensure a service (instead of a product) meets the needs of the customer (and protects the provider)
		Both in terms of performance and security
		Extensively used in managed services, such as cloud computing
**Vulnerability management lifecycle**
	Just another way of saying "combine both the risk register and the continuous monitoring efforts" and manage the entire vulnerability management through the whole cycle

**Understand 3.4**
**Monitory security platforms**
**Source systems**
	event data can be gathered from just about every entity that exists in the IT environment: application, security, appliances, network devices, and hosts
	clipping level - happy medium between too much logs and no logs at all
**Events of interest**
	event: anything that can be measured in an IT environment (basically everything)
	incident: an unscheduled event
	anomalies: something out of the ordinary
	intrusions: unauthorized access (breach)
	unauthorized changes
	compliance monitoring
**Event aggregation and correlation**
	aggregation: collecting pieces of data in order to grasp a new concept
	correlation: comparing disparate pieces of data to see how they relate
	the timing/sequence of events can help tell a story
		using information from a web server on the perimeter of a network, then a network device between that server and the internal network, then a user device inside the internal environment, we can describe an incident where an external attacker intruded on the enterprise
	the records of event captured from various devices are referred to as "logs". Can tell us the story to an incident
**Log management**
	logs should be protected at a level as high or higher than the systems/data they're logging
	logs should not be stored on the systems/alongside the data they're logging
	centralized storage is good, but creates a single-source location of loss
	off-site storage is good, but requires the same protections (or higher) than the production environment
	consider the use of a **SIEM/SEM/SIM**
		solutions that automate many of the activities involved with logging
		aggregation (collect from a variety of sources)
		normalization (put all data into the same interface)
		secure centralized storage
		analysis
		reporting
		alerts

**Understand 3.5**
**Security baselines and anomalies**
	3.4
**Visualizations, metrics, and trends**
	can be useful for reporting/decision making
	can be detrimental ("juking" reporter can modify the visualization to make it more appealing to management)
**Event data analysis**
	3.4
**Document and communicate findings**
	when aberrational/anomalous events are detected, they may be reported to the incident response team