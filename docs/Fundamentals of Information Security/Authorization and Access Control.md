#ITSec
*Authorization* is the process of determining exactly what an authenticated party can do. You implement it using *access controls* which are tools and systems regulating access.
	Used to carry out: allowing access, denying access, limiting access, and revoking access.
![[Pasted image 20231005170349.png]]

*Access Control Lists (ACLs)* are lists containing information about what kind of access certain parties are allowed to have to a given system. Often implemented as part of application software or operating systems. 

**File System ACLs**
	Read - Write - Execute
	ls -la for Linux file permissions
	
**Network ACLs**
	Filter access based on identifiers such as IP addresses, MAC addresses and ports. Used in routers, switches, and firewall devices. 
	Usually grant or deny permissions to traffic. 
	Common to use both an IP address and a port, called a *socket.* You can allow or deny network traffic form one or more IP addresses with one or more applications on your network.
	Systems with this a vulnerable to a *confused deputy problem attack*. It occurs when the software with access to a resource has a greater level of permission to access the resource than the user who is controlling the software. You can trick the software into using its higher level authority to carry out an attack. 
	Common attacks that exploit this is *cross-site request forgery (CSRF)* and *clickjacking.*
	**CSRF** misuses the authority of the browser on a users computer. If the attacker knows an already authenticated website, the attacker can embed a link in a web page to an image hosted on their own servers. When the user tries to retrieve the image in the link, it also executes additional commands the attacked has embedded in it.![[Pasted image 20231005172112.png]]
	**Clickjacking** happens when an attacker has legitimate control of some portion of a website, in which they can modify the site by placing a invisible layer over something a user would normally click on. It would cause a user to execute a command different to the one intended, tricking the client into making purchases, changing permissions, etc...
![[Pasted image 20231005172530.png]]

An *access control model* is a way of determining who should be allowed access to what resources. Most common are 
**Discretionary access control,** 
	DAC, the owner of the resource determines who gets access to it and exactly what level of access they can have.
**Mandatory access control,** 
	MAC, the owner of the resource doesn't get to decide who gets to access it. Instead, a separate group or individual has the authority to set access to resources.
**Rule-based access control,**
	allows access according to a set of ruled defined by the sysadmin. 
**Role-based access control,** 
	RBAC, allows access based on the role of the individual being granted access. 
**Attribute-based access control, and** 
	ABAC, based on the specific attributes of a person, resource, or environment. 
	Subject Attributes belong to an individual. IE something like CAPTCHAs.
	Resource Attributes belong to a resource, such as an OS or application. 
	Environmental Attributes enable access controls based on environmental conditions. 
**Multilevel access control.**
	Combines several of the access control models. Used when the simple control models aren't robust enough to protect the information to which they control access to. 
	**The Bell-LaPadula Model**
		implements a combination of discretionary and mandatory access controls (DAC AND MAC) and is primarily concerned with the confidentiality of the resource in question (so that unauthorized users cant read it).
		MAC takes control over DAC, where DAC works within the allowed access of the MAC.![[Pasted image 20231005174403.png]]![[Pasted image 20231005174411.png]]
	**The Biba Model**
		Primarily concerned with protecting the integrity of data, even at the expense of confidentiality. More important to keep those from altering it than reading it. ![[Pasted image 20231005174531.png]]
		![[Pasted image 20231005174550.png]]
	**The Brewer and Nash Model**
		Chinese Wall Model* designed to prevent conflicts of interest. 
		*Objects*: Resources such as files or information to a single org
		*Company Groups*: All objects pertaining to an org
		*Conflict Classes*: All groups of objects concerning competing parties
		![[Pasted image 20231005174928.png]]

**Physical Access Controls**
	Tailgating, a problem which occurs when you authenticate your physical access control measure, such as a badge, allowing another unauthenticated person behind you.
	
![[Pasted image 20231005173226.png]]
