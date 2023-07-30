`Objectives`
- Understand firewalls
- Understand firewall security policies
- Know firewall security policy configuration

# 3.1 Firewall Classification
**Firewall features**
- *Logical area filter* - Able to separate the internet into a trusted and untrusted domain.
- *Hiding intranet structure* - Hides the structure of the internal network ie. the trusted domain
- *Security assurance* - Point above provides security assurance to the user
- *Proactive defense against attacks* - Determines attack based on IP or patterns, and applies actions such as rack release or dropping the packets

1. **Packet Filtering Firewalls**
	- Uses an ACL to filter data packets.
	- Filtering is based on source/destination IP, source/destination port, and protocol
	- When there are complex/lengthy ACL rules, the packet filtering takes a long while
	- Packet filtering does not check filtering status
	- Only packet headers are checked
	*Disadvantages*
	- Unable to associate data packets
	- Only effective at the packet level
	- Unable to adapt to multi-channel protocols such as FTP
	- Does not check the application-layer data

2. **Proxy/Application Firewalls**
	- Firewall is not local to the network	
	- Needs to be configured for every new protocol
	*Procedure*
	- Internet device first sends connection request to firewall
	- Firewall performs security checks on the request. If check fails, connection is blocked
	- If successful, firewall sets up connection between itself, the device, and the server.
	- Packets to/from the server are first sent through firewall
	*Disadvantages*
	- Slow processing
	- Difficult to upgrade - Every protocol needs to have resources specially allocated to it. Hence difficult to upgrade quickly for new protocols
	- Vulnerable to attacks such as DOS - Due to it being dependent on the software and resources of the firewall
3. **Stateful Inspection Firewall**
	- Extension of the packet filtering firewall
	-  Filters based on the packet and also on the connection status
	- Each packet passing through is treated as independent units
	- ACLs are created for each session/traffic
	- Intercepts traffic at the network layer. Checks filtering status
	- Saves header/session information and applies the same rules to subsequent packets with similar info
	- Can be used with both TCP and UDP sessions
	*Procedure*
	- Establish TCP connection b/n the host and the server
	- Host sends an **SYN** packet
	- Server sends back an SYN acknowledge packet, **ACK**
	- Host sends back an **ACK** packet once it receives the packet from the server
	- Firewall checks the connection status throughout the entire process based on the security policy. The packets are discarded if the session info is wrong.
	- 

## Firewall Networking Modes
**Mode 1** - Layer 2 Design
- Firewall is transparent to both domains 
- Firewall does not interrupt existing IP scheme of the environment
- Does not perform routing
- Does not filter packets
**Mode 2** - Layer 3 Design
- Allows the firewall to run on different IP network
- Firewall supports some Layer 3 features such as *Network Address Translation(NAT)* and *Unified Threat Management(UTM)*
- Interrupts existing IP scheme
- Second mode implements redundancy
	- When there is high traffic, packets can be routed to another firewall for processing
- Works even with topology changes

# 3.2 Principle of Firewall Forwarding
**Steps to Packet Filtering**
Upon receiving packet, firewall:
1. Obtains the header
2. Compares header with specified rules
3. Decides whether to forward or discard packet
`Core technique for packet filtering is the Access Control List(ACL)`

**Security Policies**
Control traffic forwarding according to specific rules or actions and apply integrated content security detection to traffic
- Rules focus on packet filtering
- Major applications:
	-  Control network communication through firewall
	- Control access to firewall
- Security policy can be configured using *Telnet*, *Web* User interface or by command 

**Firewall Security Policy Mechanism**
- Defines a list of rules for traffic passing through the firewall
- Steps:
	1.  Incoming data flow passes through the firewall
	2.  Firewall searches for matching security policy and determines whether to allow the next operation
		-  If data matches with none of the security policies, the default policy is used(deny all traffic). Only needed when filtering for the first time, otherwise the session table is refered to.
	3.  Processes data packets according to rules in security policy
- Filtering is based on source/destination IP, source/destination zone, region, user and services such as port number and protocol, applications, and schedule
- A session table is created after the matching of rules is done
**Firewall Interzone Forwarding**