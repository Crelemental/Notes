### Lesson 1
CIA
- Confidentiality means that certain information should only be known to certain people. 
- Integrity means that the data is stored and transferred as intended and that modification is only done by authorized sources. 
- Availability means that information is accessible to those authorized to view or modify it.

Non-repudiation means that a subject cannot deny doing something, such as creating, modifying, or sending a resource. For example, a legal document, such as a will, must usually be witnessed when it is signed. If there is a dispute about whether the document was correctly executed, the witness can provide evidence that it was.

![[Pasted image 20240212101920.png]]

**Security Operations Center (SOC)**
	A security operations center (SOC) is a location where security professionals monitor and protect critical information assets across other business functions, such as finance, operations, sales/marketing, and so on. Because SOCs can be difficult to establish, maintain, and finance, they are usually employed by larger corporations, like a government agency or a healthcare company.

**Development and operations (DevOps)** is a cultural shift within an organization to encourage much more collaboration between developers and system administrators. By creating a highly orchestrated environment, IT personnel and developers can build, test, and release software faster and more reliably. Many consider a DevOps approach to administration as the only way organizations can take full advantage of the potential benefits offered by cloud service providers.

A dedicated **cyber incident response team (CIRT)**, a **computer security incident response team (CSIRT)**, or a **computer emergency response team (CERT)**, can be used as a single or partnered point-of-contact for the notification of security incidents. This function might be handled by the SOC, or it might be established as an independent business unit.

A security control is something designed to give a system or data asset the properties of confidentiality, integrity, availability, and non-repudiation. Controls can be divided into three broad categories, representing the way the control is implemented:
- Technical—the control is implemented as a system (hardware, software, or firmware). For example, firewalls, antivirus software, and OS access control models are technical controls. Technical controls may also be described as logical controls.
- Operational—the control is implemented primarily by people rather than systems. For example, security guards and training programs are operational controls rather than technical controls.
- Managerial—the control gives oversight of the information system. Examples could include risk identification or a tool allowing the evaluation and selection of other security controls.

**ISO 27001** is part of an overall 27000 series of information security standards, also known as 27K. Of these, 27002 classifies security controls, 27017 and 27018 reference cloud security, and 27701 focuses on personal data and privacy.

**ISO 31K** ([iso.org/iso-31000-risk-management.html](https://www.iso.org/iso-31000-risk-management.html)) is an overall framework for enterprise risk management (ERM). ERM considers risks and opportunities beyond cybersecurity by including financial, customer service, competition, and legal liability factors. ISO 31K establishes best practices for performing risk assessments.

Within SSAE No. 18 (the current specification), there are several levels of reporting:
- Service Organization Control (SOC2)—evaluates the internal controls implemented by the service provider to ensure compliance with Trust Services Criteria (TSC) when storing and processing customer data. TSC refers to security, confidentiality, integrity, availability, and privacy properties. A SOC2 Type I report assesses the system design, while a Type II report assesses the ongoing effectiveness of the security architecture over a period of 6-12 months. SOC2 reports are highly detailed and designed to be restricted. They should only be shared with the auditor and regulators, and with important partners under non-disclosure agreement (NDA) terms.
- SOC3—a less detailed report certifying compliance with SOC2. SOC3 reports can be freely distributed.

In the US, for example, the Sarbanes-Oxley Act (SOX) mandates the implementation of risk assessments, internal controls, and audit procedures. The Computer Security Act (1987) requires federal agencies to develop security policies for computer systems that process confidential information. In 2002, the Federal Information Security Management Act (FISMA) was introduced to govern the security of data processed by federal government agencies.

### Lesson 2

![[Pasted image 20240212105450.png]]

The term Advanced Persistent Threat (APT) was coined to understand the behavior underpinning modern types of cyber adversaries. Rather than think in terms of systems being infected with a virus or Trojan, an APT refers to the ongoing ability of an adversary to compromise network security—to obtain and maintain access—using a variety of tools and techniques.

Unintentional threats usually arise from lack of awareness or from carelessness, such as users demonstrating poor password management. Another example of unintentional insider threat is the concept of shadow IT, where users purchase or introduce computer hardware or software to the workplace without the sanction of the IT department and without going through a procurement and security analysis process.

A tactic, technique, or procedure (TTP) is a generalized statement of adversary behavior. The term is derived from US military doctrine ([mwi.usma.edu/what-is-army-doctrine](https://mwi.usma.edu/what-is-army-doctrine/)). TTPs categorize behaviors in terms of campaign strategy and approach (tactics), generalized attack vectors (techniques), and specific intrusion tools and methods (procedures).

An indicator of compromise (IoC) is a residual sign that an asset or network has been successfully attacked or is continuing to be attacked. Put another way, an IoC is evidence of a TTP.

The Structured Threat Information eXpression (STIX) part of the framework describes standard terminology for IoCs and ways of indicating relationships between them.

Automated Indicator Sharing (AIS) is a service offered by the Department of Homeland Security (DHS) for companies to participate in threat intelligence sharing ([us-cert.gov/ais](https://us-cert.cisa.gov/ais)). It is especially aimed at ISACs, but private companies can join too.





### Lesson 3

`ipconfig`
`ifconfig`
`ping`
`arp` - display the local machine's Address Resolution Protocol (ARP) cache. The ARP cache shows the MAC address of the interface associated with each IP address the local host has communicated with recently. This can be useful if you are investigating a suspected spoofing attack. For example, a sign of a man-in-the-middle attack is where the M
`route` - view and configure the host's local routing table. Most end systems use a default route to forward all traffic for remote networks via a gateway router
`tracert` - uses ICMP probes to report the round trip time (RTT) for hops between the local host and a host on a remote network. tracert is the Windows version of the tool.
`traceroute` - performs route discovery from a Linux host. traceroute uses UDP probes rather than ICMP, by default.
`pathping` - provides statistics for latency and packet loss along a route over a longer measuring period. pathping is a Windows tool; the equivalent on Linux is `mtr`

`nmap`
	-sS TCP SYN for fast half-open scan
	-sU UDP ports
	-p port range
	-sV or -A to probe a host more intensively

`netstat` - show the state of TCP/UDP ports on the local machine. The same command is used on both Windows and Linux, though with different options syntax. You can use netstat to check for service misconfigurations (perhaps a host is running a web or FTP server that a user installed without authorization).

`nslookup / dig` - 

theHarvester is a tool for gathering open-source intelligence (OSINT) for a particular domain or company name ([github.com/laramies/theHarvester](https://github.com/laramies/theHarvester)). It works by scanning multiple public data sources to gather emails, names, subdomains, IPs, URLs and other relevant data.

While you can use tools such as dig and whois to query name records and hosting details and to check that external DNS services are not leaking too much information, a tool such as dnsenum packages a number of tests into a single query ([github.com/fwaeytens/dnsenum](https://github.com/fwaeytens/dnsenum)). As well as hosting information and name records, dnsenum can try to work out the IP address ranges that are in use.

Port scanning is difficult to conceal from detection systems, unless it is performed slowly and results are gathered over an extended period. Another option is to disguise the source of probes. To that end, scanless is a tool that uses third-party sites ([github.com/vesche/scanless](https://github.com/vesche/scanless)). This sort of tool is also useful in a defensive sense, by scanning for ports and services that are open but shouldn't be.

curl is a command line client for performing data transfers over many types of protocol ([curl.haxx.se](https://curl.haxx.se/)). This tool can be used to submit HTTP GET, POST, and PUT requests as part of web application vulnerability testing. curl supports many other data transfer protocols, including FTP, IMAP, LDAP, POP3, SMB, and SMTP.

The list of services and version information that a host is running can be cross-checked against lists of known software vulnerabilities. This type of scanning is usually performed using automated tools. Nessus, produced by Tenable Network Security ([tenable.com/products/nessus/nessus-professional](https://www.tenable.com/products/nessus/nessus-professional)), is one of the best-known commercial vulnerability scanners. It is available in on-premises (Nessus Manager) and cloud (Tenable Cloud) versions, as well as a Nessus Professional version, designed for smaller networks. The product is free to use for home users but paid for on a subscription basis for enterprises. As a previously open-source program, Nessus also supplies the source code for many other scanners.

hping is an open-source spoofing tool that provides a penetration tester with the ability to craft network packets to exploit vulnerable firewalls and IDSs. hping can perform the following types of test:
- Host/port detection and firewall testing—like Nmap, hping can be used to probe IP addresses and TCP/UDP ports for responses.
- Traceroute—if ICMP is blocked on a local network, hping offers alternative ways of mapping out network routes. hping can use arbitrary packet formats, such as probing DNS ports using TCP or UDP, to perform traces.
- Denial of service (DoS)—hping can be used to perform flood-based DoS attacks from randomized source IPs. This can be used in a test environment to determine how well a firewall, IDS, or load balancer responds to such attacks.

As the name suggests, tcpreplay takes previously captured traffic that has been saved to a .pcap file and replays it through a network interface ([linux.die.net/man/1/tcpreplay](https://linux.die.net/man/1/tcpreplay)). Optionally, fields in the capture can be changed, such as substituting MAC or IP addresses. tcpreplay is useful for analysis purposes. If you have captured suspect traffic, you can replay it through a monitored network interface to test intrusion detection rules.

Sn1per ([github.com/1N3/Sn1per](https://github.com/1N3/Sn1per)) is a framework designed for penetration test reporting and evidence gathering. It can integrate with other tools such as Metasploit and Nikto to run automated suites of tests. Results can be displayed as web reports.

One simple but effective tool for testing connectivity is **Netcat (nc)**, available for both Windows and Linux. Netcat is a computer networking utility for reading and writing raw data over a network connection, and can be used for port scanning and fingerprinting.

Attacks come from different sources and motivations. You may wish to test both resistance to external (targeted and untargeted) and insider threats. You need to determine how much information about the network to provide to the consultant:
- Black box (or unknown environment)—the consultant is given no privileged information about the network and its security systems. This type of test would require the tester to perform a reconnaissance phase. Black box tests are useful for simulating the behavior of an external threat.
- White box (or known environment)—the consultant is given complete access to information about the network. This type of test is sometimes conducted as a follow-up to a black box test to fully evaluate flaws discovered during the black box test. The tester skips the reconnaissance phase in this type of test. White box tests are useful for simulating the behavior of a privileged insider threat.
- Gray box (or partially known environment)—the consultant is given some information; typically, this would resemble the knowledge of junior or non-IT staff to model particular types of insider threats. This type of test requires partial reconnaissance on the part of the tester. Gray box tests are useful for simulating the behavior of an unprivileged insider threat

### Lesson 4

The classic impersonation attack is for the social engineer to phone into a department, claim they have to adjust something on the user's system remotely, and get the user to reveal their password. This specific attack is also referred to as _pretexting._

Dumpster diving refers to combing through an organization's (or individual's) garbage to try to find useful documents (or even files stored on discarded removable media).

Spear phishing—a phishing scam where the attacker has some information that makes an individual target more likely to be fooled by the attack. Each phishing message is tailored to address a specific target user. The attacker might know the name of a document that the target is editing, for instance, and send a malicious copy, or the phishing email might show that the attacker knows the recipient's full name, job title, telephone number, or other details that help convince the target that the communication is genuine.

Whaling—a spear phishing attack directed specifically against upper levels of management in the organization (CEOs and other "big fish"). Upper management may also be more vulnerable to ordinary phishing attacks because of their reluctance to learn basic security procedures.

SMiShing—this refers to using short message service (SMS) text communications as the vector.

Pharming is a passive means of redirecting users from a legitimate website to a malicious one. Rather than using social engineering techniques to trick the user, pharming relies on corrupting the way the victim's computer performs Internet name resolution, so that they are redirected from the genuine site to the malicious one. For example, if mybank.foo should point to the IP address 2.2.2.2, a pharming attack would corrupt the name resolution process to make it point to IP address 6.6.6.6.

A watering hole attack is another passive technique where the threat actor does not have to risk communicating directly with the target. It relies on the circumstance that a group of targets may use an unsecure third-party website. For example, staff running an international e-commerce site might use a local pizza delivery firm. If an attacker can compromise the pizza delivery firm's website or deploy a type of malvertising, they may be able to infect the computers of the e-commerce company's employees and penetrate the e-commerce company systems.

Media viruses infect
- Non-resident/file infector—the virus is contained within a host executable file and runs with the host process. The virus will try to infect other process images on persistent storage and perform other payload actions. It then passes control back to the host program.
- Memory resident—when the host file is executed, the virus creates a new process for itself in memory. The malicious process remains in memory, even if the host process is terminated.
- Boot—the virus code is written to the disk boot sector or the partition table of a fixed disk or USB media, and executes as a memory resident process when the OS starts or the media is attached to the computer.
- Script and macro viruses—the malware uses the programming features available in local scripting engines for the OS and/or browser, such as PowerShell, Windows Management Instrumentation (WMI), JavaScript, Microsoft Office documents with Visual Basic for Applications (VBA) code enabled, or PDF documents with JavaScript enabled.

Fileless is not a definitive classification, but it describes a collection of common behaviors and techniques:
- Fileless malware does not write its code to disk. The malware uses memory resident techniques to run in its own process, within a host process or dynamic link library (DLL), or within a scripting host. This does not mean that there is no disk activity at all, however. The malware may change registry values to achieve persistence (executing if the host computer is restarted). The initial execution of the malware may also depend on the user running a downloaded script, file attachment, or Trojan software package.
- Fileless malware uses lightweight shellcode to achieve a backdoor mechanism on the host. The shellcode is easy to recompile in an obfuscated form to evade detection by scanners. It is then able to download additional packages or payloads to achieve the actor's actions and/or objectives. These packages can also be obfuscated, streamed, and compiled on the fly to evade automated detection.
- Fileless malware may use "live off the land" techniques rather than compiled executables to evade detection. This means that the malware code uses legitimate system scripting tools, notably PowerShell and Windows Management Instrumentation (WMI), to execute payload actions. If they can be executed with sufficient permissions, these environments provide all the tools the attacker needs to perform scanning, reconfigure settings, and exfiltrate data.

