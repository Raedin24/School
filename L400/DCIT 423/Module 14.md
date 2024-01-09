# 14.1 Path Determination
Primary functions of a router.
1. Determine the best path to forward packets (using routing table)
2. Forward packets to destination

`Prefix length of route in routing table is used to determine minimum match length for best path`
## 14.1.6 Build the Routing Table
A **routing table** consists of prefixes and their prefix lengths. Routers learn routes in the following ways
**Directly Connected Networks**
- Networks that are configured on the active interface of a router. 
- Added to the routing table when an interface with an *IP address* and *subnet mask*  is active
**Remote Networks**
- Not directly connected to the router.
- Can be discovered in **2** ways
- *Static routes* : Added when a route is manually configured
- *Dynamic routes* : Added when a routing protocol learns about the remote network
**Default Route**
- Specifies the next-hop router when routing table does not contain destination IP.
- Can be manually or dynamically configured
- Also called the *gateway of last resort* 
## 14.2.1 Packet Forwarding Decision Process
1. Data link frame with encapsulated IP packet arrives on the ingress
2. Router examines the destination IP in header and consults routing table
3. Router finds longest prefix match
4. Router encapsulates packet in a data link frame and forwards it out the egress
5. Packet is dropped if there is no matching route entry
`Destination can be a directly connected device or a next-hop router`

### Forwarding on Directly Connected Networks
The router needs to determine the destination MAC address associated with the destination IP address ^218ef8
1. **IPv4 Packet** - Router checks the *ARP table* for destination IP and associated MAC address. If there is no match, router sends an *ARP Request*. Destination device returns an *ARP Reply*   with its MAC address. Packet is then forwarded
2. **IPv6 Packet** - Router checks its *neighbour cache*  for the destination IPv6 address and associated MAC address. If there is no match, router sends an *ICMPv6 Neighbour Solicitation (NS)*  message. Destination device returns an *ICMPv6 Neighbour Advertisement (NA)*  message with its MAC address
`Control plane is basically code that directs the data on how and where to move.`

## Forwarding on Remote Networks
If router and next-hop router are on an ethernet network, a similar process as [[#^218ef8 |above]] will be done for IPv4 and IPv6. However here the router searches for the *IP address of next-hop*  instead of destination address of packet

`Packet is dropped if there is no matching entry and no default route`

## 14.2.3 Packet Forwarding Mechanisms
- Primary use of** packet forwarding function** is to *encapsulate packets*  in appropriate data link frame type.
- Faster encapsulation = faster packet forwarding.
- Routers support **3** mechanisms
### 1. Process Switching
- Inbound packets are forwarded to the control plane
- CPU matches destination address in routing table, determines the exit interface, and forwards the packet
- Repeats for every packet
- Slow, rarely used in modern networks

### 2. Fast Switching
- Successor to process switching.
- Uses a **fast-switching cache** to store next-hop info.
- 
