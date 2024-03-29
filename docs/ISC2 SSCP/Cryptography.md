**Understand 5.1**
**Confidentiality**
	some cryptographic solutions can be used to make data illegible to unauthorized people (can be read, not understood)
**Integrity and authenticity**
	some cryptographic solutions can be used to verify data has not been modified, or that the data comes from the declared source
**Data sensitivity**
	many kinds of data need to be protected in terms of both confidentiality and integrity (PII, EPHI)
**Regulatory and industry best practice**
	crypto is required by some laws and many standards
	PCI DSS, HIPPA

**Understand 5.2**
**Crypto terms**
	Plaintext -  data in a readable form
	Ciphertext - plain text after a crypto system, encrypted
	Encryption - process of converting plain text to ciphertext
	Decryption - reverse process of ^^^
	Cryptographic key - unique key that only the authorized individual has to decrypt and cipher
	Work factor - the amount of time to try all the potential keys for a potential crypto system to decrypt it
	Key space - number of potential keys for a given crypto system
	Initialization vector - way to add randomization to the ciphertext so that the output is always different
**Strength of encryption keys**
	typically, longer the key, higher the work factor
	asymmetric cryptosystems tend to need longer keys to provide the same protection as symmetric cryptosystems
	current modern algorithm widely perceived as secure: AES 256
**Hashing**
	hashing is not cryptography, but often used in conjunction with it
	a one-way mathematical conversion of the plaintext to a *representation* of the plaintext, called the "message digest," or the "hash"
	hashing algorithms convert messages of any size to a digest of a fixed size
	every message, when hashed, creates a unique digest
		used to demonstrate integrity
	Outmoded hashing algorithms: MD5, SHA
	Current acceptable hashing algorithms:  SHA256, SHA3
	Traits of a good hash function
		deterministic: a given plaintext will always result in a specific digest
		collision-resistant: for any given digest, it is unlikely to find 2 sensible input plaintexts
		avalanche effect: changing any one character of the input plaintext changes the entire digest
		strictly one-way: should be mathematically unfeasible to learn the plaintext from the digest
**Salting**
	encryption and hashing are both deterministic: if you put the same plaintext in, all the time, you will get the same output, everytime
		can be bad for operational security; any change in a regular message can be detected by surveillance, even if the message can't be read
	to address this, we can add a string of random characters to the message, every time the message is encrypted/hashed, such that the output is different every time
	in hashing, this practice is called "salting"; in crypto its called the "initialization vector"
**Symmetric/Asymmetric/Elliptic Curve Cryptography**
	Symmetric
		same key is used to encrypt and decrypt the message
		usually called "shared key" or "shared secret" crypto
		relatively fast
		only provides confidentiality
		does not scale well
		requires out-of-band key distribution
	Asymmetric
		one key to encrypt, another, related key to decrypt
		can provide confidentiality and/or nonrepudiation *depending on how it is used*
			nonrepudiation can be implemented in ways to offer authentication
	Elliptic Curve Cryptography (ECC)
		Uses algebraic structure of elliptic curves (different from discrete logs)
		Can provide equivalent security with smaller key sizes
**Nonrepudiation**
	a participant in a transaction cannot deny afterward that they took part
	digital signatures/certificates
	hash-based message authentication code (HMAC)
		can provide integrity and authenticity of a message using symmetric crypto and hashing
	audit trails - who sent what and where
**Digital signature**
	provides integrity and nonrepudiation
	does NOT provide confidentiality
	typically uses a hash function and the private key form asymmetric crypto
**Digital Certificate**
	a 3rd party confirmation of someone's public key
	uses public keys from asymmetric crypto and digital signatures
	only asserts ownership of a given public key
	uses the X509 format
	established by PKI (public key infrastructure)
**PKI (public key infrastructure)**
	the way we create and distribute digital certificates
	a way of providing trust between 2 entities electronically
	requires the use of a trusted 3rd party to the transaction
	an organization can setup its own PKI for its own participants
**Cryptographic attacks, cryptanalysis, and countermeasures**
	not much; unlikely to be on exam
	brute force
		trying to overcome the work factor by trying all possible keys
			quantum
		trying to deduce original input of a hashed message by creating a list of all possible inputs and all possible hashes (rainbow table)
	math
		breaking the algorithm to "solve" the crypto without the key
		doing statistical analysis on an encrypted message
	most common and effective: exploiting crypto implementation

**Understand 5.3**
**Services and protocols**
	IPsec
		Adds elements to a standard IP packet to provide more security functions
			AH - authentication header; ensures integrity and origin of the header
			ESP - encapsulating security payload; encrypts the payload
			SA - security association; the sender and recipient negotiate which type of crypto they'll use
			trailer - integrity check
			Transport Mode: end-end encryption (original IP header stays intact)
			Tunnel Mode: point-point encryption (original IP header encrypted and replaced with IPsec header)
			![[Pasted image 20240326112244.png]]
	SSL/TLS
		![[Pasted image 20240326112444.png]]
	S/MIME
		public standard for securing email
		available in most modern email applications
		uses asymmetric encryption and digital signature to offer confidentiality, nonrepudiation, and authentication of emails
	DKIM
		additional email option for appending a digital signature based on the authenticated domain of the sender
	many protocols used in modern communication are not inherently secure
	other protocols were created as secure alternatives
	when designing systems/processes, the enterprise architect might consider the used of secure protocols (understanding that these add more overhead and have negative impact on productivity)
	Not Secure - http smtp ftp
	Secure - https s/mime sftp tls

**Understand 5.4**
**Fundamental key management concepts**
	storage - don't store the keys with the thing its used with.
	rotation - don't use old keys
	composition - the longer the key, the greater the work factor (more computational overhead)
	generation - don't let users use the same passphrases or passwords for the cipher system
	destruction
	exchange
	revocation - certificate revocation list
	escrow - if a key becomes lost, that encrypted data is not recoverable. Backup and copy keys (still risky)
**Web of Trust (WOT)**
	used to authenticate public key/owner bindings
		alternative to PKI
		decentralized; based on individual trust
	Pretty Good Privacy (PGP)
		origin of WOT concept
		asymmetric crypto for secure email
	GNU Privacy Guard (GPG)
		open source version of PGP (interoperable)
	blockchain: recent attempts to implement a decentralized reputational system with WOT