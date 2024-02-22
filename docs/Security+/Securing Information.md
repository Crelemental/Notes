### Lesson 5

- Plaintext (or _cleartext_)—an unencrypted message. 
- Ciphertext—an encrypted message. 
- Cipher—the process (or algorithm) used to encrypt and decrypt a message. 
- Cryptanalysis—the art of cracking cryptographic systems.

A hashing algorithm is used to prove integrity. For example, Bob and Alice can compare the values used for a password in the following way:
1. Bob already has a digest calculated from Alice's plaintext password. Bob cannot recover the plaintext password value from the hash.
2. When Alice needs to authenticate to Bob, she types her password, converts it to a hash, and sends the digest to Bob.
3. Bob compares Alice's digest to the hash value he has on file. If they match, he can be sure that Alice typed the same password.

A symmetric cipher is one in which encryption and decryption are both performed by the same secret key. The secret key is so-called because it must be kept secret. If the key is lost or stolen, the security is breached. Symmetric encryption is used for confidentiality. For example, Alice and Bob can share a confidential file in the following way:
1. Alice and Bob meet to agree which cipher to use and a secret key value. They both record the value of the secret key, making sure that no one else can discover it.
2. Alice encrypts a file using the cipher and key.
3. She sends only the ciphertext to Bob over the network.
4. Bob receives the ciphertext and is able to decrypt it by applying the same cipher with his copy of the secret key.
	In a **stream cipher**, each byte or bit of data in the plaintext is encrypted one at a time. This is suitable for encrypting communications where the total length of the message is not known. The plaintext is combined with a separate randomly generated message, calculated from the key and an initialization vector (IV). The IV ensures the key produces a unique ciphertext from the same plaintext. The keystream must be unique, so an IV must not be reused with the same key. The recipient must be able to generate the same keystream as the sender and the streams must be synchronized. Stream ciphers might use markers to allow for synchronization and retransmission. Some types of stream ciphers are made self-synchronizing.
	In a **block cipher**, the plaintext is divided into equal-size blocks (usually 128-bit). If there is not enough data in the plaintext, it is padded to the correct size using some string defined in the algorithm. For example, a 1200-bit plaintext would be padded with an extra 80 bits to fit into 10 x 128-bit blocks. Each block is then subjected to complex transposition and substitution operations, based on the value of the key used.
	**AES**

With an asymmetric cipher, operations are performed by two different but related public and private keys in a key pair. 
Each key is capable of reversing the operation of its pair. For example, if the public key is used to encrypt a message, only the paired private key can decrypt the ciphertext produced. The public key cannot be used to decrypt the ciphertext, even though it was used to encrypt it.
Consequently, asymmetric encryption is mostly used for authentication and non-repudiation and for key agreement and exchange. Key agreement/exchange refers to settling on a secret symmetric key to use for bulk encryption without anyone else discovering it.
	Many public key cryptography products are based on the **RSA** algorithm.
	Elliptic curve cryptography (ECC) is another type of trapdoor function that can be used in public key cryptography ciphers. The principal advantage of ECC over RSA's algorithm is that there are no known "shortcuts" to cracking the cipher or the math that underpins it, regardless of key length.

Public key cryptography and hashing combined can be used to make a digital signature, to prove integrity and authentication.
1. Alice (the sender) creates a digest of a message, using a pre-agreed hash algorithm, and encrypts the digest using Alice’s private key. This creates Alice’s digital signature.
2. Alice attaches the digital signature and sends both the message and public key to Bob (the receiver).
3. Bob decrypts the digital signature using Alice's public key, resulting in the digest of the message.
4. Bob then creates a digest of the message, using the same pre-agreed hash algorithm that Alice used. Bob compares both digests.
The Digital Signature Algorithm (DSA) is a slightly different format for achieving the same sort of goal. DSA uses elliptic curve cryptography (ECC) rather than the RSA cipher.

Therefore, both are used within the same product in a type of key exchange system known as a digital envelope or hybrid encryption. A digital envelope allows the sender and recipient to exchange a symmetric encryption key securely by using public key cryptography

The question then arises of how anyone can trust the identity of the person or server issuing a public key. One solution is to have a third party, referred to as a _certificate authority (CA),_ validate the owner of the public key by issuing the subject with a certificate. The certificate is signed by the CA. If the recipient also trusts the CA, they can also trust the public key wrapped in the subject's certificate. The process of issuing and verifying certificates is called _public key infrastructure (PKI)._

This risk from RSA key exchange is mitigated by perfect forward secrecy (PFS). PFS uses Diffie-Hellman (DH) key agreement to create ephemeral session keys without using the server's private key. Diffie-Hellman allows Alice and Bob to derive the same shared secret just by agreeing some values that are all related by some trapdoor function.

The final part of a cipher suite determines the bulk encryption cipher. When AES is selected as the symmetric cipher, it has to be used in a mode of operation that supports a stream of network data.
	The Cipher Block Chaining (CBC) mode applies an initialization vector (IV) to the first plaintext block to ensure that the key produces a unique ciphertext from any given plaintext. The output of the first ciphertext block is then combined with the next plaintext block using an XOR operation. This process is repeated through the full "chain" of blocks, which (again) ensures that no plaintext block produces the same ciphertext. CBC needs to use padding to ensure that the data to encrypt is an exact multiple of the block size.
	Counter mode (CTM) makes the AES algorithm work as a stream cipher. Counter mode applies an IV plus an incrementing counter value to the key to generate a keystream. The keystream is then XOR'ed to the data in the plaintext blocks. Each block can be processed individually and consequently in parallel, improving performance. Also, counter modes do not need to use padding. Any unused space in the last block is simply discarded.

A message authentication code (MAC) provides an authentication and integrity mechanism by hashing a combination of the message output and a shared secret key. The recipient can perform the same process using his or her copy of the secret key to verify the data. This type of authenticated encryption scheme is specified in a cipher suite as separate functions, such as "AES CBC with HMAC-SHA." Unfortunately, the implementation of this type of authenticated mode in AES CBC is vulnerable to a type of cryptographic attack called a padding oracle attack ([docs.microsoft.com/en-us/dotnet/standard/security/vulnerabilities-cbc-mode](https://docs.microsoft.com/en-us/dotnet/standard/security/vulnerabilities-cbc-mode)).

The weaknesses of CBC arising from the padding mechanism means that stream ciphers or counter modes are strongly preferred. These use Authenticated Encryption with Additional Data (AEAD) modes of operation. In an AEAD scheme, the associated data allows the receiver to use the message header to ensure the payload has not been replayed from a different communication stream.

An AEAD mode is identified by a single hyphenated function name, such as AES-GCM or AES-CCM. The ChaCha20-Poly1305 stream cipher has been developed as an alternative to AES.

Obfuscation is the art of making a message difficult to understand. Obfuscated source code is rewritten in a way that does not affect the way the computer compiles or executes the code, but makes it difficult for a person reading the code to understand how it works.

Often, it is necessary to use an additional random or pseudo-random value in conjunction with the cipher:
- Nonce—the principal characteristic of a nonce is that it is never reused ("number used once") within the same scope (that is, with the same key value). It could be a random or pseudo-random value, or it could be a counter value.
- Initialization vector (IV)—the principal characteristic of an IV is that it is random (or pseudo-random). There may also be a requirement that an IV not be reused (as with a nonce), but this is not the primary characteristic.
- Salt—this is also a random or pseudo-random number or string. The term _salt_ is used specifically in conjunction with hashing password values.

A downgrade attack can be used to facilitate a man-in-the-middle attack by requesting that the server use a lower specification protocol with weaker ciphers and key lengths. For example, rather than use TLS 1.3, as the server might prefer, the client requests the use of SSL. It then becomes easier for Mallory to forge the signature of a certificate authority that Alice trusts and have Alice trust Mallory's public key.

A birthday attack is a type of brute force attack aimed at exploiting collisions in hash functions. A collision is where a function produces the same hash value for two different plaintexts. This type of attack can be used for the purpose of forging a digital signature. The attack works as follows:
1. The attacker creates a malicious document and a benign document that produce the same hash value. The attacker submits the benign document for signing by the target.
2. The attacker then removes the signature from the benign document and adds it to the malicious document, forging the target's signature.
The trick here is being able to create a malicious document that outputs the same hash as the benign document. The birthday paradox means that the computational time required to do this is less than might be expected. The birthday paradox asks how large must a group of people be so that the chance of two of them sharing a birthday is 50%.


### Lesson 6

CAs must maintain a **certificate** revocation list (CRL) of all revoked and suspended certificates, which can be distributed throughout the hierarchy.

A CRL has the following attributes:
- Publish period—the date and time on which the CRL is published. Most CAs are set up to publish the CRL automatically.
- Distribution point(s)—the location(s) to which the CRL is published.
- Validity period—the period during which the CRL is considered authoritative. This is usually a bit longer than the publish period (for example, if the publish period was every 24 hours, the validity period might be 25 hours).
- Signature—the CRL is signed by the CA to verify its authenticity.

Another means of providing up-to-date information is to check the certificate's status on an Online Certificate Status Protocol (OCSP) server, referred to as an _OCSP responder._ Rather than return a whole CRL, this just communicates the status of the requested certificate. Details of the OCSP responder service should be published in the certificate.

Pinning refers to several techniques to ensure that when a client inspects the certificate presented by a server or a code-signed application, it is inspecting the proper certificate. This might be achieved by embedding the certificate data in the application code, or by submitting one or more public keys to an HTTP browser via an HTTP header, which is referred to as _HTTP Public Key Pinning (HPKP)._ The replacement mechanism is the Certificate Transparency Framework.

Cryptographic data—both certificates and keys—are processed as binary using Distinguished Encoding Rules (DER). Binary format files are not commonly used, however.

More typically, the binary data is represented as ASCII text characters using Base64 Privacy-enhanced Electronic Mail (PEM) encoding. ASCII-format data has descriptive headers, such as the "BEGIN CERTIFICATE" string.

A certificate file can also contain more than just a single certificate:
- The PKCS #12 format allows the export of the private key with the certificate. This would be used either to transfer a private key to a host that could not generate its own keys, or to back up/archive a private key. This type of file format is usually password-protected and always binary. On Windows, these usually have a .PFX extension, while MacOS and iOS use .P12. In Linux, the certificate and key are usually stored in separate files.
- The P7B format implements PKCS #7, which is a means of bundling multiple certificates in the same file. It is typically in ASCII format. This is most often used to deliver a chain of certificates that must be trusted by the processing host. It is associated with the use of S/MIME to encrypt email messages. P7B files do not contain the private key. In Linux, the .PEM extension is very widely used for certificate chains.


### Lesson 7 

An **identity and access management (IAM)** system is usually described in terms of four main processes: 
- **Identification**—creating an account or ID that uniquely represents the user, device, or process on the network. 
- **Authentication**—proving that a subject is who or what it claims to be when it attempts to access the resource. 
- **Authorization**—determining what rights subjects should have on each resource, and enforcing those rights. 
- **Accounting**—tracking authorized usage of a resource or use of rights by a subject and alerting when unauthorized use is detected or attempted.

Windows network sign-in—the LSA can pass the credentials for authentication to a network service. The preferred system for network authentication is based on Kerberos, but legacy network applications might use NT LAN Manager (NTLM) authentication.

A single sign-on (SSO) system allows the user to authenticate once to a local device and be authenticated to compatible application servers without having to enter credentials again. In Windows, SSO is provided by the Kerberos framework.

Kerberos is a single sign-on network authentication and authorization protocol used on many networks, notably as implemented by Microsoft's Active Directory (AD) service. Kerberos was named after the three-headed guard dog of Hades (Cerberus) because it consists of three parts. Clients request services from application servers, which both rely on an intermediary—a Key Distribution Center (KDC)—to vouch for their identity. There are two services that make up a KDC: the Authentication Service and the Ticket Granting Service. The KDC runs on port 88 using TCP or UDP.

The Password Authentication Protocol (PAP) is an unsophisticated authentication method developed as part of the Point-to-Point Protocol (PPP), used to transfer TCP/IP data over serial or dial-up connections. It is also used as the basic authentication mechanism in HTTP. It relies on clear text password exchange and is therefore obsolete for most purposes, except through an encrypted tunnel.

The Challenge Handshake Authentication Protocol (CHAP) was also developed as part of PPP as a means of authenticating users over a remote link. CHAP relies on an encrypted challenge in a system called a _three-way handshake._
1. Challenge—the server challenges the client, sending a randomly generated challenge message.
2. Response—the client responds with a hash calculated from the server challenge message and client password (or other shared secret).
3. Verification—the server performs its own hash using the password hash stored for the client. If it matches the response, then access is granted; otherwise, the connection is dropped.
The handshake is repeated with a different challenge message periodically during the connection (although transparent to the user). This guards against _replay attacks,_ in which a previous session could be captured and reused to gain access.

The Initiative for Open Authentication (OATH) is an industry body established with the aim of developing an open, strong authentication framework. _Open_ means a system that any enterprise can link into to perform authentication of users and devices across different networks. _Strong_ means that the system is based not just on passwords, but also on 2- or 3-factor authentication or on 2-step verification. OATH has developed two algorithms for implementing one time passwords (OTPs).

HMAC-based One-time Password Algorithm (HOTP) is an algorithm for token-based authentication ([https://www.ietf.org/rfc/rfc4226.html](https://www.ietf.org/rfc/rfc4226.html)). The authentication server and client token are configured with the same shared secret. This should be an 8-byte value generated by a cryptographically strong random number generator. The token could be a fob-type device or implemented as a smartphone authentication/authenticator app. The shared secret can be transmitted to the smartphone app as a QR code image acquirable by the phone's camera so that the user doesn't have to type anything. Obviously, it is important that no other device is able to acquire the shared secret. The shared secret is combined with a counter to create a one-time password when the user wants to authenticate. The device and server both compute the hash and derive an HOTP value that is 6-8 digits long. This is the value that the user must enter to authenticate with the server. The counter is incremented by one.

The Time-based One-time Password Algorithm (TOTP) is a refinement of the HOTP ([https://datatracker.ietf.org/doc/html/rfc6238](https://nam02.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdatatracker.ietf.org%2Fdoc%2Fhtml%2Frfc6238&data=04%7C01%7Cdandries%40comptia.org%7C79b46abac0f04b29ecae08d9bef00625%7C8c39a7ffe0774d1c9a1c7431fe5eb465%7C0%7C0%7C637750760424782889%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C3000&sdata=iBZcXWlOthfRUWPX5dGZdB8zh1PoUKo3picunapbngM%3D&reserved=0)). One issue with HOTP is that tokens can be allowed to persist unexpired, raising the risk that an attacker might be able to obtain one and decrypt data in the future. In TOTP, the HMAC is built from the shared secret plus a value derived from the device's and server's local timestamps. TOTP automatically expires each token after a short window (60 seconds, for instance). For this to work, the client device and server must be closely time-synchronized. One well-known implementation of HOTP and TOTP is Google Authenticator.

### Lesson 8 

Discretionary access control (DAC) is based on the primacy of the resource owner. The owner is originally the creator of a file or service, though ownership can be assigned to another user. The owner is granted full control over the resource, meaning that he or she can modify its access control list (ACL) to grant rights to others.
DAC is the most flexible model and is currently implemented widely in terms of computer and network security. In terms of file system security, it is the model used by default for most UNIX/Linux distributions and by Microsoft Windows. As the most flexible model, it is also the weakest because it makes centralized administration of security policies the most difficult to enforce. It is also the easiest to compromise, as it is vulnerable to insider threats and abuse of compromised accounts.

Role-based access control (RBAC) adds an extra degree of centralized control to the DAC model. Under RBAC, a set of organizational roles are defined, and subjects allocated to those roles. Under this system, the right to modify roles is reserved to a system owner. Therefore, the system is non-discretionary, as each subject account has no right to modify the ACL of a resource, even though they may be able to change the resource in other ways. Users are said to gain rights implicitly (through being assigned to a role) rather than explicitly (being assigned the right directly).
RBAC can be partially implemented through the use of security group accounts, but they are not identical schemes. Membership of security groups is largely discretionary (assigned by administrators, rather than determined by the system). Also, ideally, a subject should only inherit the permissions of a role to complete a particular task rather than retain them permanently.

Mandatory access control (MAC) is based on the idea of security clearance levels. Rather than defining ACLs on resources, each object and each subject is granted a clearance level, referred to as a label. If the model used is a hierarchical one (that is, high clearance users are trusted to access low clearance objects), subjects are only permitted to access objects at their own clearance level or below.
The labelling of objects and subjects takes place using pre-established rules. The critical point is that these rules cannot be changed by any subject account, and are therefore non-discretionary. Also, a subject is not permitted to change an object's label or to change his or her own label.

Attribute-based access control (ABAC) is the most fine-grained type of access control model. As the name suggests, an ABAC system is capable of making access decisions based on a combination of subject and object attributes plus any context-sensitive or system-wide attributes. As well as group/role memberships, these attributes could include information about the OS currently being used, the IP address, or the presence of up-to-date patches and anti-malware. An attribute-based system could monitor the number of events or alerts associated with a user account or with a resource, or track access requests to ensure they are consistent in terms of timing of requests or geographic location. It could be programmed to implement policies, such as M-of-N control and separation of duties.

Privileged access management (PAM) refers to policies, procedures, and technical controls to prevent the malicious abuse of privileged accounts and to mitigate risks from weak configuration control over privileges. These controls identify and document privileged accounts, giving visibility into their use, and manage the credentials used to access them ([beyondtrust.com/resources/glossary/privileged-access-management-pam](https://www.beyondtrust.com/resources/glossary/privileged-access-management-pam)).

Conditional access is an example of rule-based access control. A conditional access system monitors account or device behavior throughout a session. If certain conditions are met, the account may be suspended or the user may be required to reauthenticate, perhaps using a 2-step verification method. The User Account Control (UAC) and sudo restrictions on privileged accounts are examples of conditional access. The user is prompted for confirmation or authentication when requests that require elevated privileges are made. Role-based rights management and ABAC systems can apply a number of criteria to conditional access, including location-based policies ([docs.microsoft.com/en-us/azure/active-directory/conditional-access/overview](https://docs.microsoft.com/en-us/azure/active-directory/conditional-access/overview)).

Federation is the notion that a network needs to be accessible to more than just a well-defined group of employees. In business, a company might need to make parts of its network open to partners, suppliers, and customers. The company can manage its employee accounts easily enough. Managing accounts for each supplier or customer internally may be more difficult. Federation means that the company trusts accounts created and managed by a different network. As another example, in the consumer world, a user might want to use both Google Apps and X (formerly Twitter). If Google and X establish a federated network for the purpose of authentication and authorization, then the user can log on to X using his or her Google credentials or vice versa.

A federated network or cloud needs specific protocols and technologies to implement user identity assertions and transmit attestations between the principal, the relying party, and the identity provider. Security Assertion Markup Language (SAML) is one such solution. SAML attestations (or authorizations) are written in eXtensible Markup Language (XML). Communications are established using HTTP/HTTPS and the Simple Object Access Protocol (SOAP). These secure tokens are signed using the XML signature specification. The use of a digital signature allows the relying party to trust the identity provider.
As an example of a SAML implementation, Amazon Web Services (AWS) can function as a SAML service provider. This allows companies using AWS to develop cloud applications to manage their customers' user identities and provide them with permissions on AWS without having to create accounts for them on AWS directly.

Enforcing an acceptable use policy (AUP) is important to protect the organization from the security and legal implications of employees misusing its equipment. Typically, the policy will forbid the use of equipment to defraud, to defame, or to obtain illegal material. It will prohibit the installation of unauthorized hardware or software and explicitly forbid actual or attempted snooping of confidential data that the employee is not authorized to access. Acceptable use guidelines must be reasonable and not interfere with employees' fundamental job duties or privacy rights. An organization's AUP may forbid use of Internet tools outside of work-related duties or restrict such use to break times.

