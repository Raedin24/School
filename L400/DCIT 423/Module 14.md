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

