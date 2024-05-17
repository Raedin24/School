# Intro to OSPF
- Is a *link-state* routing protocol
- Offers faster convergence and scales better to larger networks. **Convergence** is the rate at which information is being collected and shared
- Uses the concept of **areas** , with routing domains being divided into distinct areas
- A *link*  is 
	- an interface on a router
	- a network segment connecting two routers
	- a stub network connected to a single router
- *Link-state*  is the information about the state of a link. Includes
	- *Network prefix*
	- *Prefix length*
	- *Cost*

## Components of OSPF




## Single and Multiarea OSPF
- OSPF supports hierarchical routing using areas.
- An OSPF area is a group of routers that share the same link-state info in their LSDB
> Networks are usually connected to the ISP through area 0

### Multiarea OSPF
1. Smaller routing table
2. Reduces link-state update overhead
3. Reduces frequency of SPF calculations


# 1.2 OSPF Packets


```

```