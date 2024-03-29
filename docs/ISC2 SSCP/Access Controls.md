**Understand 2.1**
What you need to know -- **Often called IAM or IAAA**
	Identification: knowing a particular subject
		identity assertion: a unique identifier (user ID)
		doesnt have to be confidential
	Authentication: confirming a subject presenting an identify assertion is that subject
		necessarily has to be confidential
		often the password
	Authorization: granting permissions to the subject based on the authenticated identity
	Accountability: means of knowing which subject conducted which transactions
		enduring logs necessary
		provides nonrepudiation
**Single/MFA**
	Factor: an element used to authenticate a subject
	Typically, 3 types of factors
		something you know, have, are
	True multifactor uses at least 2 different types of factors to authenticate a subject (rather than 2FA which is 2 of one factor)
	CER (crossover error rate) is the point at which a graph of a system's return of false negatives crosses a graph of a system's return of false positives. It describes how sensitive a system is. 
**SSO and ADFS, OID**
	Allows users to present credentials once, then access multiple systems
	Enhances the user experience and increases security
		user is more likely to user strong passwords
		user is less likely to write down passwords
	May create a single point of failure or single point of breach
	ADFS
		server-based Microsoft product for federation
	OAuth
		open standard for allowing resource providers/vendors to share restricted resources with users, without requiring the user's credentials.
			an authorization mechanism
			typically uses 3rd party tokens, generated from the user's credentials presented to the 3rd party
			designed specifically for Web traffic
	OpenID Connect
		The authorization layer for OAuth 2.0
**Device Authentication**
	How do we know a device belongs on the network, or its the device it claims to be, or that its being used by a specific user.
	TPM (Trusted Platform Module)
		integrated crypto processor standard (hardware level ensurance that a system boots in the way its supposed to); uses asymmetric encryption
	Certificates; uses asymmetric encryption/PKI
	HSM (hardware security module)
		a symmetric key is known to both the entities (the device and whatever its connecting to
		like a yubikey
**Federated Access (Oauth2, SAML)**
	Federation is like SSO across multiple organizations
		the users of one organization can use their credentials to access the systems/data of other organizations
		Uses OpenID, OAuth, SAML
	SAML: XML based authentication protocol
		Roles
			Identity Provider (IdP)
			Service Provider
			Principal (user)
		Bindings
		Assertions
		Protocols
		Profiles
		Current Ver: SAML 2.0
		https://en.wikipedia.org/wiki/Security_Assertion_Markup_Language

**Understand 2.2**
**Support internetwork trust architectures**
**Trust relationships (1way 2way transitive zero)**
	1 way trust: entities from one network A can trust assets in another B, but this cannot be reversed (B entities cant access A assets)
	2 way trust: entities from 2 networks can trust assets in both
	Transitive trust: if entities from one domain A trust entities from another B, and entities from B trust entities from a 3rd C, then entities from A will trust entities from C.
	Zero Trust: popular modern approach to It/security architecture
		No trusted connections/data feeds; every time data is shared, it is treated as suspect
		Magnifies the defense in depth approach
**Internet, intranet, extranet**
	intranet: network IT resources within the org
		assets are controlled by the org, and therefore trusted
		users are internal
	extranet: part of the org's environment available to users outside the org (contractors/vendors/customers)
	internet: worldwide connection of IT assets
		controlled/owned by many disparate parties, and therefore untrusted
**3rd party connections**
	if 3rd parties are connecting to your environment
		use of a protected extranet would be preferable
	if your org uses connections owned by external entities
		securing the communication itself would be preferable

**Understand 2.3**
**Participate in the identity management lifecycle**
**Proofing**
	Confirming the subject's identity prior to issuing the identity assertion/credentials
		typically performed by HR on the subject's 1st day of employment
			often uses some other form of identity assertions, issued by a government entity (passport)
			often done in conjunction with other required enrollments (insurance, tax)
**Provisioning/Deprovisioning**
	Provisioning: creating credentials and accounts for new users
		typically done upon hiring
		operational manager should work in conjunction with IT department and HR
		credentials must be issued in a secure manner
	Maintenance: asset owners must review access to their resources on a regular basis
		promotions, terminations, resignations
	Deprovisioning: removing access no longer required
		terminations, resignations, changing roles
	**avoid permission creep**: where a employee over the years can get more and more permissions that they may not need to perform their duties
**Authorization**
	Asset owners should review all access to their assets
		at least annually
		for pertinence and necessity
	Role definition
		have the requirements of the position changed?
		have the systems changed?
		operational manager should work in conjunction with IT department and HR
**Identity and Access Management IAM systems**
	OpenID Connect
	SAML (Security Assertion Markup Language)
	Kerberos
		TGT (ticket-granting ticket)
	RADIUS
		remote-access dial-in user service
		client/server protocol for authentication, authorization, and accounting
		can use TCP or UDP
		uses authentication schema such as PAP, CHAP, and EAP to confirm user's credentials (usually userid/password)
	TACACS
		terminal access controller access-control system
		authentication scheme for centrally-managed network access systems
		mostly replaced by TACACS+ or RADIUS

**Understand 2.4**
Mandatory Access Control (MAC)
	military origins
	requires all resources have classifications and all users have clearances
	designed to increase uniformity at the cost of flexibility
Discretionary Access Control (DAC)
	Asset owner may grant access to resources as they see fit
	increases flexibility at the cost of uniformity
Role-Based Access Control (RBAC)
	set of permissions according to the user's job requirements
	asset owner must work with IT and HR to create roles
Rule-Based Access Control
	permissions based on criteria
	gives strong authority to administrator

