# 3.5 Common Network Attacks
Networks are vulnerable to the ff types of attacks
1. Reconnaissance attacks
2. Access Attacks
3. DoS attacks
> Data becomes a payload once encapsulation has occured

### Reconnaissance Attacks
- Info gathering stage
- Used by threat actors to perform unauthorized discovery and mapping of systems, services and vulnerabilities
- Happens before access and DoS attacks

| Technique                    | Description                                                                                                           |
| ---------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| Perform info query           | Used to look for initial info about a target. Tools used include Google search, organization website, whois, etc      |
| Ping sweep of target network | Used to reveal target network address and determine active IPs                                                        |
| Port scan of active IPs      | Used to determine which ports / services are available. Tools used include Nmap, SuperScan, Angry IP Scanner, NetScan |
| Run vulnerability scanners   | Query active ports to identify type and version of application and operating system of host.                          |
| Run exploitation tools       |                                                                                                                       |
### Access Attack
- Exploits known vulnerabilites in authentication, FTP, and web services.
- Used to retrieve data, gain access, or escalate access privileges.
- **Password attack** - Attempt to discover critical system passwords.
- **Spoofing attack** - IP Spoofing, MAC spoofing
### Social Engineering Attacks
- An access attack that attempts to manipulate individuals into divulging info / performing actions

| Technique               | Description                                                                      |
| ----------------------- | -------------------------------------------------------------------------------- |
| Pretexting              | Pretends to need personal / financial data to confirm the identity of receipient |
| Spear Phishing          |                                                                                  |
| Spam                    | Tar                                                                              |
| Something for Something |                                                                                  |
| Baiting                 |                                                                                  |
| Impersonation           |                                                                                  |
| Tailgating              |                                                                                  |
| Shoulder surfing        |                                                                                  |
| Dumpster diving         |                                                                                  |
| Phishing                | Sends fradulent email                                                            |

### Dos and DDoS
- Creates an interruption of network services
- Two main types
	1. Overwhelming Quantity of Traffic
	2. Maliciously Formatted Packets

# 3.6 IP Vulnerabilities and Threats
- Possible because IP does not validate that the source IP in the packet is the actual source.

| IP Attack Techniques            | Description                                                                                                                                                                  |
| ------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ICMP attacks                    | Used for reconnaissance and scanning attacks. Preventable by using ICMP access control list (ACL)                                                                            |
| Amplification and reflection    | Used to create DoS attacks. Newer forms are DNS-based and Network Time Protocol (NTP)                                                                                        |
| Address spoofing attacks        | Threat actors create packets with false source IP address info. Classified into *blind* and *non-blind* spoofing.Non-blind allows one to see the traffic b/n host and target |
| Man-in-the-middle attack (MITM) |                                                                                                                                                                              |
| Session hijacking               |                                                                                                                                                                              |

> ARP resolves  IP addresses to MAC addresses. Works at Layer 2
> NAT resolves public IP addresses to private I
> DNS resolves domain names to IP addresses. 