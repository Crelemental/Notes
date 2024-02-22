### Lesson 19

Risk management is a process for identifying, assessing, and mitigating vulnerabilities and threats to the essential functions that a business must perform to serve its customers. You can think of this process as being performed over five phases:
1. Identify mission-essential functions—mitigating risk can involve a large amount of expenditure so it is important to focus efforts. Effective risk management must focus on mission essential functions that could cause the whole business to fail if they are not performed. Part of this process involves identifying critical systems and assets that support these functions.
2. Identify vulnerabilities—for each function or workflow (starting with the most critical), analyze systems and assets to discover and list any vulnerabilities or weaknesses to which they may be susceptible.
3. Identify threats—for each function or workflow, identify the threat sources and actors that may take advantage of or exploit or accidentally trigger vulnerabilities.
4. Analyze business impacts—the likelihood of a vulnerability being activated as a security incident by a threat and the impact of that incident on critical systems are the factors used to assess risk. There are quantitative and qualitative methods of analyzing impacts and likelihood.
5. Identify risk response—for each risk, identify possible countermeasures and assess the cost of deploying additional security controls. Most risks require some sort of mitigation, but other types of response might be more appropriate for certain types and level of risks.

For each business process and each threat, you must assess the degree of risk that exists. Calculating risk is complex, but the two main variables are likelihood and impact:
- Likelihood of occurrence is the probability of the threat being realized.
- Impact is the severity of the risk if realized as a security incident. This may be determined by factors such as the value of the asset or the cost of disruption if the asset is compromised.

Quantitative risk assessment aims to assign concrete values to each risk factor.
- Single Loss Expectancy (SLE)—the amount that would be lost in a single occurrence of the risk factor. This is determined by multiplying the value of the asset by an Exposure Factor (EF). EF is the percentage of the asset value that would be lost.
- Annualized Loss Expectancy (ALE)—the amount that would be lost over the course of a year. This is determined by multiplying the SLE by the Annualized Rate of Occurrence (ARO).

Business impact analysis (BIA) is the process of assessing what losses might occur for a range of threat scenarios. For instance, if a DDoS attack suspends an e-commerce portal for five hours, the business impact analysis will be able to quantify the losses from orders not made and customers moving permanently to other suppliers based on historic data.

A mission essential function (MEF) is one that cannot be deferred. This means that the organization must be able to perform the function as close to continually as possible, and if there is any service disruption, the mission essential functions must be restored first.

Maximum tolerable downtime (MTD) is the longest period of time that a business function outage may occur for without causing irrecoverable business failure. Each business process can have its own MTD, such as a range of minutes to hours for critical functions, 24 hours for urgent functions, seven days for normal functions, and so on.

Recovery time objective (RTO) is the period following a disaster that an individual IT system may remain offline.

Work Recovery Time (WRT). Following systems recovery, there may be additional work to reintegrate different systems, test overall functionality, and brief system users on any changes or different working practices so that the business function is again fully supported.

Recovery Point Objective (RPO) is the amount of data loss that a system can sustain, measured in time. That is, if a database is destroyed by a virus, an RPO of 24 hours means that the data can be recovered (from a backup copy) to a point not more than 24 hours before the database was infected.

### Lesson 20

![[Pasted image 20240221104452.png]]

In very general terms, the order of restoration will be as follows:
1. Enable and test power delivery systems (grid power, power distribution units [PDUs], UPS, secondary generators, and so on).
2. Enable and test switch infrastructure, then routing appliances and systems.
3. Enable and test network security appliances (firewalls, IDS, proxies).
4. Enable and test critical network servers (DHCP, DNS, NTP, and directory services).
5. Enable and test back-end and middleware (databases and business logic). Verify data integrity. 
6. Enable and test front-end applications.
7. Enable client workstations and devices and client browser access.
### Lesson 21

Some types of smart cards used as passkeys for electronic locks can be vulnerable to cloning and skimming attacks:
- Card cloning—this refers to making one or more copies of an existing card. A lost or stolen card with no cryptographic protections can be physically duplicated. Card loss should be reported immediately so that it can be revoked and a new one issued. If there were a successful attack, it might be indicated by use of a card in a suspicious location or time of day.
- Skimming—this refers to using a counterfeit card reader to capture card details, which are then used to program a duplicate. Some types of proximity cards can quite easily be made to transmit the credential to a portable RFID reader that a threat actor could conceal on his or her person. Skimmers installed on public readers, such as ATM machines, can be difficult to spot.

