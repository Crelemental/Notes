#NetworkSec
# Network Sec Overview
### Vulnerabilities
**Physical Security.** If attackers can gain access to your files or to the physical computers they can steal copies of the data. The SecOps team cannot change the encryption key if the copy leaves the network. It will take a while to brute force the encryption but it will eventually yield. Gotta protect your assets  with **physical security.**

**Weak Passwords / Default**. Weak passwords are easy to compromise as they can be guessed or brute forced using tools that leverage dictionaries of common passwords/combinations. Sometimes complex passwords might be bad as users will tend to write them down rather than memorizing them, posing a security risk. Also leaving default passwords without changing is a horrible practice.

**Misconfigured Firewall Rules**. Say it had a default password and an attacker got access, they could easily change the configs to allow access into your network without your knowledge. Config mistakes are equally dangerous to you security and can leave doors open for attackers. Good practice to routinely review you firewall configs, and change the password.

**Personal Devices in the network**. Allowing users to bring their own device BYOD can save money, but there must be lots of care that those devices do not contaminate the network with viruses or malware. Corporations often require their workers to install special approved antivirus and anti-malware on their devices prior to connecting to the network.

**Advanced Persistent Threats**. A APT is a virus or malware that remains undetected for a while waiting for the right time. It sits idle long enough where it is included in so many backups that the IT department wouldn't be able to backup to an uncompromised version.

**Zero-Days**. An exploit or vulnerability that's not yet known to the public, meaning no patch available to mitigate it. Very dangerous because no pattern files exist in AV or AM software for it to get blocked. Some IPS vendors allow admins to forward unknown or suspicious code patterns to vendors for analysis. So it could block the zero-day, and in the case of false positives it can be unblocked ofc.


### Attacker Types

**Vulnerability testers.** Responsible for scanning servers and network devices for known vulnerabilities. Use such tools like **Nessus.**

**Red Team** tries to attack the security systems while the **Blue Team** defends. A neutral **White Team** observes the festivities and acts as a referee. A **Purple Team** has both teams engage and when the certain success criterias are met, the teams debrief and cross train each other.

**Hackers**. **White Hat** hackers are IT professionals who specialize in penetrating or compromising network security to help an org improve its own security posture. The only attack when authorized to do so.
**Black Hat** hackers possess the knowledge and will to breach systems for profit. Might be monetary, street cred, or source of entertainment. They do not ask for permission and dont help their targets.
**Gray Hat** hackers are a group who may or may not be IT professionals and may or may not break laws in pursuit of hacking goals. Gray hats have no malicious intent in their actions; but may not have obtained permission to perform their attacks.

**Insider Threats**. Sometimes most potent threat is from within your org, as they have legitimate access to systems and are in a position to attack within the network undetected. Accidents happen sometime though, as your account may have been given higher permissions causing problems to be made. Use the case of Least privilege and audit logging of admin changes.

**Nation States**. Intellectual property theft through industrial espionage is a very real concern for many companies. The bigger threat is nation states have larger budgets to hire hackers than the average criminal enterprise.

**Script Kiddies**. Copycat criminals of the hacking community. They typically hack out of curiosity or entertainment and often use poorly documented tools or scripts written by advanced hackers. Typically not IT professionals. Their lack of knowledge contributes to the unpredictability of their actions and random levels of damage. 
### Common Threats and Attacks

**Wiretapping**. It refers to any process that allows an attacker to electronically eavesdrop on a conversation, either between humans or computers. IE like putting wiretaps in-line with a computer network cable and using a packet sniffer to listen and record the traffic on the network. An attacker can use a special listening tool to interpret the EMF surrounding a network cable so that he can eavesdrop on a wire without breaking its connection. Some corps only use fiberoptic in high security areas, as they're immune to EMF listening devices.

**Port Scanning**. An attacker can plan an attack by finding what services or applications are running on a victims computer. Most network services are open TCP ports that accept connections from legit client computers. **Port scanners** check each of these ports by sending tons of TCP/IP packets to the victims computer each on a different port.

**Taking Control**. Once they know which ports are being used, the attacker can run vuln scanners against the computer to learn if there are services that are easily exploited. 
**SQL Injection** allows an attacker to take control of a database server by inserting special commands into input boxes instead of basic text. This allows for commands to be executed in the server to take control of it. Easily fixed by sanitizing the input.
**Buffer Overflow**. Attacker enters text that is too large to fit within a region of memory called a buffer. If it overflows, the characters can overwrite neighboring, possibly executable areas of memory. Special code can be overflowed into those areas and can possibly run code to take control of a server. 

Verify all user input fields are check for unplanned values and enable NX-bit (no execute) on the physical computer or VM. It would allow the CPU to only execute the contents of memory buffers identified as code.

**Spoofing**. man-in-the-middle attack. There are many variants of spoofing. Another example involves ARP poisoning, which is a method attackers use to cause an Ethernet switch to flood all traffic to every port on the switch, including the attacker’s computer.
**DOS**. Many DoS attacks use features within the ICMP, such as "ping." You may recall that ping is a tool commonly used by network administrators to verify that a computer is online. The ping flood attack overwhelms a victim’s computer with an immense volume of ICMP echo-request packets, all containing a forged, randomized source address. The victim’s computer automatically begins sending ICMP echo-reply packets to all these forged source addresses, which eventually overwhelms the victim’s computer so that it cannot do its normal job. There are also other DDoS attacks that aim to exhaust a computer’s CPU or network connections, including SSL attacks, which cause the victim’s computer to consume excessive CPU time as it constantly sets up and tears down thousands of SSL encryption sessions over and over.
**Social Engineering**. It is usually substantially easier to "hack a human" than hack a computer because people are generally trusting of others.
### Risk Mitigation

**Honeypot**. A server or device that is configured to look authentic, possibly containing data that appears to be legit, and legit config files. It's intended to attract or distarct attackers from the actual network. It provides a false positive for hackers believing its the real network. It can also be used to collect data on the hacker and slows down them to trace info by the IDS.

**Proactive and Preventative Measure**. You need to use multiple tools and methods together in an overlapping manner to create rings or layers of security. Minimize your exposure by keeping OSs and apps up to date on patches. Follow security hardening guides that help remove unnecessary services and features that are exploitable.

**Risk Mitigation Response**. Develop and test your containment plans before an attack occurs. Response plan should first help contain the damage from the attack, which may involve quarantining computers or severing network connections, and ten removing the threat and cleaning up the damage. Some attacks are silent and might not cause damage right away, as in rootkits, backdoor attacks, and trojan horses. Run AV and AM scans on your systems regularly.
# CIA Triad
![[Pasted image 20240103203155.png]]
### Confidentiality

The confidentiality principle helps limit access to information, which, by definition, can contradict some of the recommendations found in the availability principle. The goal of confidentiality is to prevent an unauthorized user from accessing, copying, or transmitting the information.

Confidentiality is often equated to privacy because the two terms share many of the same characteristics, such as ensuring that only the intended recipient of the information can access it, following a need-to-know policy, and reducing exposure by destroying all copies of the information that are no longer needed.

There are many ways to breach or compromise the confidentiality of data if the proper precautions are not taken in advance and then routinely checked for accuracy and consistency.

- Unencrypted information is easy to steal and change.
- Deleted files are rarely purged from a disk immediately and often can be recovered with ease.
- The physical theft of a device gives an attacker an unlimited time window to break the encryption of your data.
- Social engineering is a method used by attackers to gain an unsuspecting victim’s trust to provide information, such as passwords or server names, or even just to gain physical building access.
- Accidents and malfunctions also play into the equation. For example, confidentiality of information can easily be breached by storing files in the wrong location, emailing data to the wrong person, or printing confidential information to a public printer.

Some methods that may help prevent compromises include:

- Where possible, encrypt the information at-rest (where it is stored) and in-transit (while it is moving across the network).
- Be sure to encrypt and physically secure your laptops, servers, portable hard drives, and even backup tapes/disks.
- Consider using a tool to securely delete files or overwrite them after deletion.
- Train your employees about social engineering attacks.
- Create and enforce a policy that ensures all users must use complex passwords (a combination of uppercase and lowercase letters, numbers, and symbols with a minimum length) and use multifactor authentication (MFA), such as biometrics or a digital key fob.
- Following the principle of least privilege (which means you only assign users the minimum permissions needed to perform their jobs), institute restrictive access controls on all data and provide access to information on a need-to-know basis only.

### Integrity

The integrity principle helps identify the trustworthiness of the information. It is possible to identify where the information came from and if the data has changed since it was originally sent. Integrity is a function that is often incorporated into encryption and, therefore, works well with the confidentiality principle.

Some of the compromises of data integrity include:

- Man-in-the-middle attacks, where an attacker changes the contents of the message after it was sent, but before it was received
- The intentional or unintentional deletion or modification of data
- Malfunctions in equipment that cause data corruption
- Natural phenomena such as electromagnetic pulse (EMP) attacks, which can destroy or severely corrupt data

Some methods that can be employed to help prevent the compromise of data integrity include:

- Require all data transmissions to use encryption or digital signatures to confirm the identity of the sender and to identify if the message has been changed.
- In cases where digital signatures will not work, use one-way hash calculations, such as SHA-3 (Secure Hash Algorithm 3), to create a value that can be used to verify the data has not changed.
- Use version control within your data storage to help you quickly revert accidental changes or deletions.

### Availability

The goal of the availability principle is to ensure that the data is always accessible by its authorized users. This includes aspects such as adding high availability to your server solutions and minimizing downtime by carefully managing your application updates and patches.

Some of the common actions that can compromise the availability of data include:

- denial-of-service (DoS) and distributed denial-of-service (DDoS) attacks, which prevent legitimate users from accessing the resource by sending an overwhelming amount of data to the target server;
- unplanned downtime due to server crashes or failed upgrades; and
- accidental changes to access control lists, which removes access for authorized users.

Some methods that can be employed to help prevent availability issues include:

- creating and maintaining a full disaster recovery plan that includes a full site failover as well as the method to restore data for individual servers;
- implementing server high availability where possible, employing clustering technology where appropriate; and
- setting up regular backups of your data and considering storing a backup copy at another physical location to protect against site-level disasters.