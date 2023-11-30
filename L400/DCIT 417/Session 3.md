A wireless network can be 
1. *AP-based* - there is a central device (access point) that connects different terminal devices eg. router. Common in Office/Home LANs
2. *Ad hoc based*  - The end devices form connections among themselves when there is a need to transmit information
	- In situations where the communicating devices are out of the range of the other device, a node/terminal device can act as an intermediary and transmit packets b/n devices. 
	- Common in 
		- Vehicular ad hoc network (VANET)
		- Mobile ad hoc network (MANET)
		- Wireless sensor network (WSN)

## Building a point to point topology
`Ipv4GlobalRoutingHelper` - Used to populate the routing tables
`NodeContainer` - Used to create all connected nodes required by the topology
`PointToPointHelper` - Used to set the channel attributes (data rate, delay)
`InternetStackHelper` - Used to install all basic network protocols
`Ipv4AddressHelper` - Used to set and assign IPv4 addresses and the subnets to the nodes

## Generate Application
`UdpEchoSeverHel`