`Objectives`
- Understand firewalls
- Understand firewall security policies
- Know firewall security policy configuration
# 3.1 Firewall Classification
1. **Packet Filtering Firewalls**
	- When there are complex/lengthy ACL rules, the packet filtering takes a long while
	- Packet filtering does not check filtering status
	- Only packet headers are checked
	*Disadvantages*
	- Unable to associate data packets
	- Unable to adapt to multi-channel protocols
	- Does not check the application-layer data

2. **Proxy Firewalls**
	- Firewall is not local to the network
	*Procedure*
	- Internet device first sends connection request to firewall
	- Firewall performs security checks on the request. If check fails, connection is blocked
	- If successful, firewall sets up connection between itself, the device, and the server.
	- Packets to/from the server are first sent through firewall
	*Disadvantages*
	- Slow processing
	- Difficult to upgrade

1. **Stateful Inspection Firewall**
- ACLs are created for each session/traffic
- Intercepts traffic at the network layer. Checks filtering status
- Saves header/session information and applies the same rules to subsequent packets with similar info
## Firewall Networking Modes
**Mode 1**
- Does not perform routing
- Does not filter packets
**Mode 2**
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
- Control traffic forwarding according to specific rules
- Apply integrated content security detection to traffic
- Rules focus on packet filtering
- Control network communication through firewall
- Control access to firewall