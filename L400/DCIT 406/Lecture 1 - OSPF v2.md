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

OSPF messages are used to create and maintain 3 OSPF databases