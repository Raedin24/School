Network and System security is the discipline concerned with protecting computer networks, systems and data from unauthorized access, misuse or disruption
Ensures
- *Confidentiality*
- *Integrity*
- *Availability*

## Security Standards
A series of **documented processes** that define how to **implement, manage and monitor** security controls
- **Ghana Cybersecurity Act** - Act No. *1038 of 202* . Concerned with development of cybersecurity
- **Data Protection Act** - Protects individuals' privacy and personal data by regulating the processing of personal information
- **National Institute of Standards and Technology (NIST)** - A U.S. federal agency. Deals with measurement science, standards and tech related to government use and promotion of private-sector innovation. Developed the
	- Federal Information Processing Standards (*FIPS*)
	- Special Publications (*SP*)
- **Internet Society (ISOC)** - Addresses issues about the future of the Internet
- **International Telecommunication Union (ITU-T)** - Produces standards covering all fields of telecommunications. Standards are referred to as *Recommendations*
- **International Organization for Standardization (ISO)** - Worldwide federation of national standards bodies.

## Threats to Network and System Security
- **Malware** - Software designed to infiltrate
- **Phishing** - Tactics used to trick individuals into divulging confidential info
- **Denial of Service (DoS)** and **Distributed Denial of Service (DDOS)** - Coordinated efforts to overwhelm network resources
- **Insider Threats** - Malicious activities carried out by individuals with authorized access

## Principles of Network Security
1. **Confidentiality** - Ensuring sensitive info is only accessible by *authorized individuals/systems*
2. **Integrity** - Maintaining the *accuracy*, *consistency* and *trustworthiness* of data throughout its lifecyclye
3. **Availability** - Ensuring services and resources are *accessible*  and *usable* when needed

## CIA Triad
- A security model designed to help organizations develop security policies to keep their sensitve data secure
- Consists of the principles mentioned above
![[Pasted image 20240516105015.png]]
- Two additional concepts are added by some security experts
	- **Authenticity** - Being genuine and verifiable. ie. confidence in the validity of a transmission, message or message originator
	- **Accountability** - Actions of an entity should be traced uniquely to that entity. Supports *nonrepudation*, *deterrence*, *fault isolation*, *intrusion detection and prevention*


## Cryptography in Network Security
**Cryptography** is used to facilitate secure comms and data protection through *encryption* and *decryption* processes.
1. **Symmetric Encryption** - Uses a single shared key for both encryption and decryption
2. **Asymmetric Encryption** - Uses a pair of keys (*public* and *private*)  for encryption and decryption
3. **Digital Signatures** - Verifying the authenticity and integrity of digital messages

## Secure Network Protocols
Essential for safeguarding data transmission over networks
1. **Secure Layer / Transport Layer Security (SSL/TLS)** - Encrypts data exchanged between web servers and clients
2. **Internet Protocol Security (IPSec)** - Secures communication at the IP layer, enable VPNs and secure data transmission
3. **Secure Shell (SSH)** - Secures remote access and command execution on network devices
## Authentication and Authorization
**Authentication** - Verifies the identity of users/devices
**Authorization** - Determines the level of access
Implemented through:
1. **Passwords** - Traditional authentication method. Uses secret credentials known only to authorized users
2. **Multi-Factor Authentication (MFA)** - Requires multiple forms of authentication (eg passwords, biometrics etc)
3. **Access Control Models** - Defines access permissions based on roles, attributes, or policies
4. **Peer entity authentication** - Two entities are considered peers if they implement the same protocol in different systems.Provides corroboration of the identity of a peer entity in an association
5. **Data origin authentication** - Provides corroboration of the source of a data unit. Does not provide protection against duplication or modification of data units. eg. email

## Security Technologies
**Firewalls** monitor and control incoming and outgoing traffic based on predefined security rules
**Intrusion Detection Systems (IDS)** analyze network traffic for suspicious patterns or anomalies.
**Virtual Private Networks** enable secure comms over public networks by creating encrypted tunnels b/n endpoints
	- *Remote Access VPNs* - Allows remote users to securely connect to a private network from remote locations
	- *Site-to-Site VPNs* - Secure connections b/n geographically dispersed networks or sites
**Network Access Control (NAC)**  ensures only authorized devices/users can access network resources
	- *Policy Enforcement* - Enforces security policies for access control based on ***user identity, device type, compliance status***
	- *Endpoint Security* - Assesses the security posture of devices trying to access the network