`Objectives`
- Understand firewalls
- Understand firewall security policies
- Know firewall security policy configuration

# 3.1 Introduction to Firewalls
---
## 3.1.1 Firewall Classification
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

### Firewall Networking Modes
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

## 3.1.2 Principle of Firewall Forwarding
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
- A session table is created only after the matching of rules is done, and the packet being handled is the first packet.
- For every subsequent packet the session table is referred to and updated

**Stateful Inspection Mechanism**
- A session can only be created when the first packet passes the inspection of the firewall. Any other packets coming within the same session are also forwarded without being checked. Enabled by default
- If disabled, even if the first packet does not pass, subsequent packets will trigger the creation of a session table as long as they pass

- A session table will usually contain the following information
	- Source and Destination IP address
	- Source and Destination Port number
	- Protocol (eg. TCP)
	- User (eg. abc)
	- Application ( eg. Telnet)

## 3.1.3 Firewall Security Policies and Application
- System has 4 security zones by default: *local*, *trust*, *untrust* and *DMZ*. Security levels of default zones cannot be changed.
- Additional zones(user-defined) can be created and configured.
- Security policy includes
	1. Matching conditions: Source and destination security zone, source and destination address, user, service, application, schedule
	2. Action: Permit or deny
	3. Response Packet: Send or Do not send (based on action, optional)
	4. Profile: Antivirus, intrusion prevention, URL Filtering etc
- Security Policy Configuration Process:
	Start > Configure Interfaces >  Configure security policy >  Save and commit > Exit
Optional steps include:
- Create security zones - After start, before configuring interfaces
- Configure user authentication, configure objects, create profile - After configuring interfaces

- An *address object* is a set of **IPv4**/**IPv6** addresses or **MAC** addresses.
- A *region* is a set of public IP addresses in a certain area
- A *service* is a type of application protocol determined by a **protocol type** and a **port number**.
- An *application* is a computer program used for a specific purpose or task

## 3.1.4 Application Specific Packet Filtering (ASPF)
- Single-channel protocol refer to application services that use only one port during communication. eg. WWW uses port 80
- Multi-channel protocol use 2 or more ports for communication. eg FTP uses 21 and a random port
- Protocols that use random ports cannot be monitored effectively by pure packet filtering
- **ASPF** checks application-layer protocol information. It maintains status information for all connections of a specified application protocol and dynamically determines whether to allow the data packets
- Used to filter packets at the application layer

A *server map table* is generated under the following conditions
1. Sever map entries are generated when multi-channel protocols of the firewall such as **ASPF** are enabled
2. Static server map entries will be generated when there is a **NAT server mapping** or port forwarding
3. Triplet server map entries will be generated when **STUN protocols** (Simple Traversal of UDP through NAT) are configured
4. Dynamic server map entries are generated when **NAT No-PAT** (Network Address Translation without Port Address Translation) is configured

- Port identification maps non-standard protocol ports to identifiable application protocol ports
- Can be done by
	1. Configuring a basic ACL
	2. Configuring port identification/mapping with the ACL

**Fragment Cache**
Used to cache fragments that arrive before the first fragment in the flow. 
Done to prevent the firewall from discarding fragments

**Persistent Connection**
Created sessions have a time limit, which is not suitable for the transmission of big data. 
- Longer sessions can be configured using the command `long link`
- `long link` changes the aging time of the session
- If not data is transmitted withing the session aging time, the session is disconnected


# 3.2 Network Address Translation
---
## 3.2.1 NAT Principle
**NAT** is used to translate private addresses into public addresses to allow devices to communicate across private and public networks
- Is a temporary solution to alleviate shortage of public IPv4 addresses 
*Advantages*
1. IP addresses can be reused(private IPs)
2. Address translation process is transparent to users
3. Privacy protection is available to internal users
4. Load balancing among internal servers is available
*Disadvantages*
1. Network monitoring is more difficult
2. Some applications are restricted


**NAT Categories
1. *Source NAT*
	1. Address pool mode - Uses a fixed public IP from a range of IPs (the pool)
	2. Outbound interface address mode(easy IP) - A number of internal hosts are translated to the same public IPs, usually dynamic IPs
2. *Server mapping*
	1. Static mapping (NAT server) - A one-to-one mapping between a private address and public address. Used when external users should be able to access internal users

## 3.2.1 Source NAT
1. *Address Pool Mode*
	1. *Address Pool Mode (1)*  - One-to-one IP address translation without port translation
	- If the pool is running out of IPs, any subsequent private IPs trying to communicate with the external network will not be translated and hence cannot access the network
	2. *Address Pool Mode (2)* - Many-to-one address translation with port translation. Different private addresses are mapped to the same public address but with different port numbers
2. *Easy IP* - Uses the public IP of the outbound interface of the firewall. Involves port translation
`Difference b/n Address Pool Mode and Easy IP is that the public IP addresses in the pool are static IP addresses granted to the hosting provider. All addresses in Easy IP are translated into a single IP, which can be dynamic`

**NAT Application Level Gateway (NAT ALG)**
A translation proxy used for certain application protocols and can translate the address and port number carried in application layer data.
- Not enabled by default
*Implementation Principle*
	- Set up control connection (TCP three-way handshake) b/n host and server
	- Host sends a **PORT** packet
	- Firewall enables with ALG translates private address and port number in packet
	- Server initiates a data connection to the host
	- Data is transmitted over the established data connection

## 3.2.3 Server Mapping
The NAT server function uses a public address to represent the private address of an internal server
- After the NAT server is configured, the device automatically generates server map entries mapping public addresses to private ones
- The server generates map entries for both inbound and outbound traffic
- Specifying `no-reverse` in the configuration makes the device generate only forward/outbound map entries
## 3.2.4 Application Scenarios
**Interzone Twice NAT**
Configures source NAT based on NAT server function. Simplifies the configuration of the route from server to public network

**Intrazone Twice NAT**
- The firewall translates the *destination address* of the *user's request packet* into the *private address* of the *FTP server*. Also translate the *source address* into the *public address* of the *user*.
- Firewall translate the *source address* of the *response packet* from the *FTP server* into the *public address*. Also translates the *destination address* into the *private address* of the *user*.
# 3.3 Dual-System Hot Standby
---
**Dual-system hot standby** improves network reliability. Two firewalls can be deployed at the *egress* of a network to ensure communication b/n intranet and Internet

## 3.3.1 Technical Principles of Dual-System Hot Standby
- *Virtual Router Redundancy Protocol*  is used to provide router redundancy
- VRRP creates a virtual IP, with all traffic using that IP as the gateway
- There is 1 master router, with the remaining routers serving as backups.
- If there is a failure in the master router, the backups can come online. There is no need to change the configuration as the gateway IP remains as the virtual IP

# 3.4 Firewall User Management
---
# 3.5 Overview of Intrusion Prevention
---
