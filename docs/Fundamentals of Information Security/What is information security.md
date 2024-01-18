#ITSec
![[Pasted image 20231004184437.png]]![[Pasted image 20231004184939.png]]
**Confidentiality** refers to our ability to protect our data form those who are not authorized to view it. You could implement confidentiality at many levels of a process.
**Integrity** is the ability to prevent people from changing your data in an unauthorized or undesirable manner. To maintain integrity, not only do you need to have the means to prevent unauthorized changes to your data, but you need the ability to reverse unwanted authorized changes.
**Availability** refers to the ability to access our data when we need it. You could lose availability due to a power loss, network attacks, DOS, etc...


**The Parkerian Hexad** complex variation of the CIA triad. Adds on **Possession or control**, **Authenticity**, and **Utility.** 
![[Pasted image 20231004185824.png]]
**Possession or Control** refers to the physical disposition of the media on which the data is stored. This enables you to discuss your loss of the data in its physical medium without involving availability.
**Authenticity** allows you to say whether you've attributed the data in question to the proper owner or creator.
**Utility** refers to how useful the data is to you.


**Attacks** 
4 Categories: Interception, interruption, modification, fabrication.

Confidentiality - Interception
Integrity - Interruption Modification Fabrication
Availability -  Interruption Modification Fabrication

**Interception** attacks allow unauthorized users to access your data, applications, or environments, and they are primarily attacks against confidentiality. 
**Interruption** attacks make your assets unusable or unavailable to you on a temporary or permanent basis. Often affect availability and or integrity (DOS)
**Modification** attacks involve tampering with an asset. Often attack on integrity but also can be availability. 
**Fabrication** attacks involve generating data, processes, communications, or other similar material with a system. Primarily affects integrity but could be availability as well. 


**Threats** 
	Something that has the potential to cause harm. Specific to only certain environments.
**Vulnerabilities**
	Weaknesses or holes that threats can exploit to cause you harm. Many physical and non physical factors play into it.
**Risk**
	The likelihood that something bad will happen. A risk in an environment can have both a threat and a vulnerability that the threat could exploit.
**Impact**
	Some organizations like the NSA add a factor called impact, which takes into account the value of the asset being threatened and use it to calculate risk.


**Risk Management**
![[Pasted image 20231004194641.png]]
**Identify Assets**
	If you cant enumerate your assets and evaluate the importance of each, protecting them can become a difficult task indeed. Also have to decided which are critical business assets to properly secure them.
**Identify Threats** 
	Its useful to have a framework for discussing the nature of a given threat, having the CIA or Parkerian Hexad serve nicely for this exact purpose.


**Assess Vulnerabilities**
	Any given asset may have thousands of threats, but only a small fraction of them will be relevant. 
**Assess Risks**
	Risk is the conjunction of a threat and a vulnerability. 
**Mitigate Risks**
	You can put measures in place to account for each threat. These measures are called *controls*. Controls are divided into 3 categories: Physical, Logical, and Administrative.
	*Physical Controls* protect the physical environment in which your systems sit, or where your data is stored. These controls also control access in and out of such environments. 
	*Logical Controls* or *Technical Controls* protect the systems, networks, and environments that process, transmit, and store your data.
	*Administrative Controls* are based on rules, laws, policies, procedures, guidelines, and other items that are paper in nature. It dictates how users of your environment should behave. **You should have the ability to enforce them as it could lead to false sense of security if not enforced.**


**Incident Response**
	This should be directed at the items that are most likely to cause an organization pain. Part of risk management efforts to identify that.
	Consists of: *Preparation, Detection and Analysis, Containment, Eradication, Recovery, and Post-Incident Activity.*
	![[Pasted image 20231004201121.png]]
	![[Pasted image 20231004201150.png]]
	![[Pasted image 20231004201411.png]]
	![[Pasted image 20231004201519.png]]
	![[Pasted image 20231004201537.png]]
	![[Pasted image 20231004203017.png]]
	![[Pasted image 20231004203242.png]]
	![[Pasted image 20231004203250.png]]
	