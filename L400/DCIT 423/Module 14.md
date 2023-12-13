# 14.1 Path Determination
Primary functions of a router.
1. Determine the best path to forward packets
2. Forward packets to destination
## 14.2.1 Packet Forwarding Decision Process
1. Data link frame with encapsulated IP packet arrives on the ingress
2. Router examines the destination IP in header and consults routing table
3. Router finds longest prefix match
4. Router encapsulates packet in a data link frame and forwards it out the egress
5. Packet is dropped if there is no matching route entry
`Destination can be a directly connected device or a next-hop router`

### Forwarding on Directly Connected Networks
The router needs to determine the destination MAC address associated with the destination IP address
1. **IPv4 Packet** - Router checks the *ARP table* for destination IP and associated MAC address. If there is no match, router sends an *ARP Request*. Destination device returns an *ARP Reply* with its MAC address. Packet is then forwarded
2. **IPv6 Packet** - Router checks its *neighbour cache*  for the destination IPv6 address and associated MAC address. If there is no match, router sends an *ICMPv6 Neighbour Solicitation (NS)*  message. Destination device returns an *ICMPv6 Neighbour Advertisement (NA)*  message with its MAC address
`Control plane is basically code that directs the data on how and where to move.`