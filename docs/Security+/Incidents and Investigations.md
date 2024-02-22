### Lesson 17

The following are the principal stages in an incident response life cycle:
1. Preparation—make the system resilient to attack in the first place. This includes hardening systems, writing policies and procedures, and setting up confidential lines of communication. It also implies creating incident response resources and procedures.
2. Identification—from the information in an alert or report, determine whether an incident has taken place, assess how severe it might be (triage), and notify stakeholders.
3. Containment—limit the scope and magnitude of the incident. The principal aim of incident response is to secure data while limiting the immediate impact on customers and business partners.
4. Eradication—once the incident is contained, remove the cause and restore the affected system to a secure state by wiping a system and applying secure configuration settings.
5. Recovery—with the cause of the incident eradicated, the system can be reintegrated into the business process that it supports. Applying patches and updates to a system to help prevent future incidents is important as well. This recovery phase may involve restoration of data from backup and security testing. Systems must be monitored more closely for a period to detect and prevent any reoccurrence of the attack. The response process may have to iterate through multiple phases of identification, containment, eradication, and recovery to effect a complete resolution.
6. Lessons learned—analyze the incident and responses to identify whether procedures or systems could be improved. It is imperative to document the incident. The outputs from this phase feed back into a new preparation phase in the cycle.

An incident response plan (IRP) lists the procedures, contacts, and resources available to responders for various incident categories. The CSIRT should develop profiles or scenarios of typical incidents (DDoS attack, virus/worm outbreak, data exfiltration by an external adversary, data modification by an internal adversary, and so on). This will guide investigators in determining priorities and remediation plans. A playbook (or runbook) is a data-driven standard operating procedure (SOP) to assist junior analysts in detecting and responding to specific cyberthreat scenarios, such as phishing attempts, SQL injection data exfiltration, connection to a block-listed IP range, and so on. The playbook starts with a SIEM report and query designed to detect the incident and identify the key detection, containment, and eradication steps to take.

Threat research provides insight into adversary tactics, techniques, and procedures (TTPs). Insights from threat research can be used to develop specific tools and playbooks to deal with event scenarios. These stages are often referred to as a cyber kill chain, following the influential white paper Intelligence-Driven Computer Network Defense commissioned by Lockheed Martin

MITRE Corporation's Adversarial Tactics, Techniques, and Common Knowledge (ATT&CK) matrices provide access to a database of known TTPs. This freely available resource ([attack.mitre.org](https://attack.mitre.org/)) tags each technique with a unique ID and places it in one or more tactic categories, such as initial access, persistence, lateral movement, or command and control.

The Diamond Model of Intrusion Analysis suggests a framework to analyze an intrusion event (E) by exploring the relationships between four core features: adversary, capability, infrastructure, and victim.![[Pasted image 20240220101824.png]]

You should distinguish specific incident response planning from other types of planning for disaster recovery and business continuity:
- Disaster recovery plan—a disaster can be seen as a special class of incident where the organization's primary business function is disrupted. Disaster recovery requires considerable resources, such as shifting processing to a secondary site. Disaster recovery will involve a wider range of stakeholders than less serious incidents.
- Business continuity plan (BCP)—this identifies how business processes should deal with both minor and disaster-level disruption. During an incident, a system may need to be isolated. Continuity planning ensures that there is processing redundancy supporting the workflow, so that when a server is taken offline for security remediation, processing can failover to a separate system. If systems do not have this sort of planned resilience, incident response will be much more disruptive.
- Continuity of Operation Planning (COOP)—this terminology is used for government facilities, but is functionally similar to business continuity planning. In some definitions, COOP refers specifically to backup methods of performing mission functions without IT support.

Correlation means interpreting the relationship between individual data points to diagnose incidents of significance to the security team. A SIEM correlation rule is a statement that matches certain conditions. These rules use logical expressions, such as AND and OR, and operators, such as == (matches), < (less than), > (greater than), and in (contains). For example, a single-user logon failure is not a condition that should raise an alert. Multiple user logon failures for the same account, taking place within the space of one hour, is more likely to require investigation and is a candidate for detection by a correlation rule.

A SIEM can enact a retention policy so that historical log and network traffic data is kept for a defined period. This allows for retrospective incident and threat hunting, and can be a valuable source of forensic evidence.

A sensor is a network tap or port mirror that performs packet capture and intrusion detection. One of the key uses of a SIEM is to aggregate data from multiple sensors and log sources, but it might also be appropriate to configure dashboards that show output from a single sensor or source host.

Automation is the action of scripting a single activity, while orchestration is the action of coordinating multiple automations (and possibly manual activity) to perform a complex, multistep task. In the case of security orchestration, automation, and response (SOAR), this task is principally incident response, though the technologies can be used for tasks such as threat hunting too. SOAR is designed as a solution to the problem of the volume of alerts overwhelming analysts' ability to respond, measured as the mean time to respond (MTTR).

The basis of SOAR is to scan the organization's store of security and threat intelligence, analyze it using machine/deep learning techniques, and then use that data to automate and provide data enrichment for the workflows that drive incident response and threat hunting. It can also assist with provisioning tasks, such as creating and deleting user accounts, making shares available, or launching VMs from templates, to try to eliminate configuration errors. The SOAR will use technologies such as cloud and Software-Defined Networking (SDN)/Software-Defined Visibility (SDV) APIs, orchestration tools, and cyberthreat intelligence (CTI) feeds to integrate the different systems that it is managing. It will also leverage technologies such as automated malware signature creation and user and entity behavior analytics (UEBA) to detect threats.

### Lesson 18

Digital forensics is the practice of collecting evidence from computer systems to a standard that will be accepted in a court of law. Forensics investigations are most likely to be launched against crimes arising from insider threats, notably fraud or misuse of equipment (to download or store obscene material, for instance).

E-discovery is a means of filtering the relevant evidence produced from all the data gathered by a forensic examination and storing it in a database in a format such that it can be used as evidence in a trial. E-discovery software tools have been produced to assist this process. Some of the functions of e-discovery suites are:
- Identify and deduplicate files and metadata—many files on a computer system are "standard" installed files or copies of the same file. E-discovery filters these types of files, reducing the volume of data that must be analyzed.
- Search—allow investigators to locate files of interest to the case. As well as keyword search, software might support semantic search. Semantic search matches keywords if they correspond to a particular context.
- Tags—apply standardized keywords or labels to files and metadata to help organize the evidence. Tags might be used to indicate relevancy to the case or part of the case or to show confidentiality, for instance.
- Security—at all points evidence must be shown to have been stored, transmitted, and analyzed without tampering.
- Disclosure—an important part of trial procedure is that the same evidence be made available to both plaintiff and defendant. E-discovery can fulfill this requirement. Recent court cases have required parties to a court case to provide searchable ESI rather than paper records.

The general principle is to capture evidence in the order of volatility, from more volatile to less volatile. The ISOC best practice guide to evidence collection and archiving, published as [tools.ietf.org/html/rfc3227](https://tools.ietf.org/html/rfc3227), sets out the general order as follows:
1. CPU registers and cache memory (including cache on disk controllers, GPUs, and so on).
2. Contents of nonpersistent system memory (RAM), including routing table, ARP cache, process table, kernel statistics.
3. Data on persistent mass storage devices (HDDs, SSDs, and flash memory devices):
	- Partition and file system blocks, slack space, and free space.
	- System memory caches, such as swap space/virtual memory and hibernation files.
	- Temporary file caches, such as the browser cache.
	- User, application, and OS files and directories.
1. Remote logging and monitoring data.
2. Physical configuration and network topology.
3. Archival media and printed documents.

Artifacts refers to any type of data that is not part of the mainstream data structures of an operating system. For example, the Windows Alternate Data Streams (ADS) feature is often used to conceal file data, and various caches, such as prefetch and Amcache, can be used to find indicators of suspicious process behavior.
Data recovery refers to analyzing a disk (or image of a disk) for file fragments stored in slack space. These fragments might represent deleted or overwritten files. The process of recovering them is referred to as carving.

