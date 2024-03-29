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

# 14.2 Packet Forwarding
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
- Primary use of **packet forwarding function** is to *encapsulate packets*  in appropriate data link frame type.
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
- Inbound packets are forwarded to the control plane
- CPU searches for match in fast-switching cache
- If there is no match, packet is process-switched and forwarded, and the flow information is stored in the fast-switching cache
- Subsequent packets with same destination use next-hop without CPU intervention
- Changes in table entry are *packet-triggered*

### 3. Cisco Express Forwarding (CEF)
- Default Cisco IOS packet-forwarding mechanism.
- Build a **Forwarding Information Base (FIB)** and an *adjacency table*
- Table entries are *change-triggered*  meaning they only change when there is a change in the network topology.
- After network convergence, FIB and adjacency table contains all necessary routing information
- Packets are processed and forwarded in the *data plane*


# 14.4 IP Routing Table
## 14.4.2 Routing Table Principles
1. Every router makes its own decisions based on its routing table
2. Routing table entries of a router do not have to match that of a different router
3. Routing information does not provide a return path

- Network discovery is the ability of a routing protocol to share information about the networks it knows with other routers using the same routing protocol.

## 14.4.12 Administrative Distance
- Used to determine which route to install into the IP table in situations where the same route is learnt from different sources.
- The lower the administrative distance (AD), the higher the preference

|Route Source|Administrative Distance|
|---|---|
|Directly connected|0|
|Static route|1|
|EIGRP summary route|5|
|External BGP|20|
|Internal EIGRP|90|
|OSPF|110|
|IS-IS|115|
|RIP|120|
|External EIGRP|170|
|Internal BGP|200|
`A stub network is one accessed by a single route, and the router only has one neighbour`
`A default route can either be static or dynamically learned. 0.0.0.0/0 for IPv4 and ::/0 for IPv6`
`IPv6 routing protocols use the link-local address of the next-hop router, while IPv4 uses the IP address`
# 14.5 Static and Dynamic Routing
Most networks use a combo of dynamic routing protocols and static routes
**Static Routes**
Used:
- As default route for forwarding packets to service provider
- For  routes outside the routing domain
- When the admin wants to explicitly define the path for a specific network
- For routing b/n stub networks
**Dynamic Routing Protocols**
Used:
- In networks consisting of more than just a few routers
- When a change in network topology requires network to automatically determine another path.
- When network needs to be scalable.

| **Feature** | **Dynamic Routing** | **Static Routing** |
| ---- | ---- | ---- |
| Configuration complexity | Independent of network size | Increases with network size |
| Topology changes | Automatically adapts to topology changes | Administrator intervention required |
| Scalability | Suitable for simple to complex network topologies | Suitable for simple topologies |
| Security | Security must be configured | Security is inherent |
| Resource Usage | Uses CPU, memory, and link bandwidth | No additional resources needed |
| Path Predictability | Route depends on topology and routing protocol used | Explicitly defined by the administrator |
## 14.5.2 Dynamic Routing Evolution
**Interior Gateway Protocols**: Used to exchange routing info within a routing domain
- RIPv1 - Released in 1988
- RIPv2 - Released to accommodate growth in network environment
- OSPF and IS-IS - Released to address the needs of even larger networks
- IGRP - Developed by Cisco
- EIGRP - Developed to replace IGRP

**Exterior Gateway Protocols**: Used to exchange routing info between different organizations. Used by ISPs
- EGP
- BGP - Developed to replace EGP. 


|  | **Interior Gateway Protocols** |  |  | **Exterior Gateway Protocols** |  |
| ---- | ---- | ---- | ---- | ---- | ---- |
|  | **Distance Vector** |  | **Link-State** |  | **Path Vector** |
| **IPv4** | RIPv2 | EIGRP | OSPFv2 | IS-IS | BGP-4 |
| **IPv6** | RIPng | EIGRP for IPv6 | OSPFv3 | IS-IS for IPv6 | BGP-MP |
## 14.5.3 Dynamic Routing Protocol Concepts
A routing protocol is a set of *processes*, *algorithms*  and *messages*  that are used to exchange routing information and populate the routing table.
The main components of dynamic routing protocols include
1. **Data structures** - Typically tables and databases. Stored in the *RAM*
2. **Routing protocol messages** - Used to discover neighbouring routers, exchange routing info, and learn and maintain accurate network info
3. **Algorithm** - Used for best path determination

## 14.5.4 Best Path
- The best path to a network is the path with the lowest metric
- A metric is the quantitative valued used to measure the distance to a given network

|**Routing Protocol**|**Metric**|
|---|---|
|**Routing Information Protocol (RIP)**|- Metric is **hop count**.<br>- Each router along a path adds a hop to the hop count.<br>- A maximum of **15** hops allowed. |
|**Open Shortest Path First (OSPF)**|- Metric is **cost** which is the based on the cumulative bandwidth from source to destination.<br>- Faster links are assigned lower costs compared to slower (higher cost) links. |
|**Enhanced Interior Gateway Routing Protocol (EIGRP)**|- Metric is based on the **slowest bandwidth and delay values**.<br>- Could also include load and reliability into the metric calculation. |
## 14.5.5 Load Balancing
- If a router has two or more paths to a destination with equal cost metrics, the router uses both paths.
- This is known as *equal cost load balancing*
- Can increase network performance if done correctly
- Implemented automatically by dynamic routing protocols
- Implemented with static routes if there are multiple static routes to the same destination
`EIGRP supports unequal cost load balancing`