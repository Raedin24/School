# Intro to OSPF
- Is a *link-state* routing protocol
- Offers faster convergence and scales better to larger networks. **Convergence** is the rate at which information is being collected and shared
- Uses the concept of **areas** , with routing domains being divided into distinct areas
- A *link*  is an interface on a router, a network segment connecting two routers.

## Components of OSPF
> ACK packets are always exchanged before information exchange begins

OSPF uses *5*  types of packets
1. Hello
2. Database description
3. Link-state request
4. Link-state update
5. Link-state acknowledgment

OSPF messages are used to create and maintain *3* OSPF databases

| Database                 | Table            | Description                                                                                       |
| ------------------------ | ---------------- | ------------------------------------------------------------------------------------------------- |
| Adjacency Database       | Neighbor Table   | - Lists all neighbor routers with bi-directional comms. Unique for each router. `ip ospf neghbor` |
| Link-State Databse(LSDB) | Topology Table   | - Lists info about all other routers in network. All routers in an area have identical LSDB.      |
| Forwarding Database      | Forwarding Table |                                                                                                   |
- Topology table is built using Dijkstra's SPF algorithm

## Link-State Operation
1. Establish Neighbor Adjacencies
2. Exchange Link-State Advertisements
3. Build link state database
4. Execute the SPF algo
5. Choose the best route