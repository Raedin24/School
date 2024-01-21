Task 1

MANET Routing Protocols

MANET stands for Mobile Ad hoc Network. It can be defined as a collection of low-power wireless mobile nodes forming a temporary wireless network without the aid of established infrastructure or centralised administration (_What Is MANET | IGI Global_, 2020). In simpler terms, they are wireless networks without a fixed infrastructure, where nodes are able to communicate with each other dynamically. MANET routing protocols are used to adapt to changes in network topology to enable continuous network service. This report discusses 3 MANET routing protocols

 

# Optimised Link State Routing (OLSR)

## Route Discovery Process

Optimised Link State Routing is a proactive routing protocol. This means it constantly maintains and updates information on the network topology. It uses a link state approach where each node periodically broadcasts HELLO messages about its neighbours and their connectivity. This information is used by other nodes to build and maintain Minimal Control Sets (MCS). The route discovery process includes constructing a Multi-Point Relay (MPR) set. MPR is used to forward control messages and reduce message flooding from redundant transmissions.

## Route Maintenance

Route maintenance in OLSR is done by actively updating the link state information. If a node does not receive HELLO messages from a neighbour, it removes the associated link from its MCS and informs other neighbours. This causes its neighbours to also update their information, keeping the routing table consistent

## Opportunities for Performance Improvements

1. The MPR selection process can be enhanced
    
2. Hierarchical OLSR: Implement cluster-based routing for large networks, reducing control traffic by delegating routing within clusters to cluster heads.
    
3. Multilevel Routing: Combine proactive and reactive approaches. Proactive routing can be used for frequently accessed destinations and reactive routing for less frequent communication, optimizing resource utilisation.
    

# Ad-hoc On-Demand Distance Vector (AODV)

## Route Discovery Process

Ad-hoc On-Demand Distance Vector is a reactive routing protocol. This means that routes are established only when necessary, on-demand. When a source node wants to communicate with a destination node, it initiates a route discovery process by broadcasting a request for connection via Route Request (RREQ) packet. Other nodes on the path to the destination node send a Route Reply (RREP) message back to the source node (Rouse, 2012). The source node then uses the route with the least number of hops to get information across to the destination node.

## Route Maintenance

Routes are dynamically maintained using Route Reply (RREP) and Route Error (RERR) messages. RREPs are used to discover and create new routes. When a node detects a link failure, it sends an RERR packet. Other nodes receiving this RERR consults the routing table and remove all the routes that contain the bad nodes (Klein-Berndt, n.d.)

## Opportunities for Performance Improvements

1. Route Caching: Store recently used routes to facilitate faster re-use and reduce RREQ flooding, especially in frequent communication patterns.
    
2. Local Repair: Enable nodes to proactively discover alternate paths within their vicinity when receiving RERRs, minimising route re-discovery overhead and delays.
    
3. Mobility Prediction: Utilise mobility prediction techniques to anticipate node movement and proactively update routes before link breakage, reducing delays and packet loss.
    

 

 

Destination-Sequenced Distance Vector (DSDV)

## Route Discovery Process

Destination-Sequenced Distance Vector is a proactive routing protocol. It maintains a table containing all possible routes, each with an assigned sequence number, destination and hop count. Nodes periodically exchange DSDV tables, maintaining a consistent routing table. When a route needs to be discovered, nodes exchange their routing tables, and the route with the highest sequence number is selected.

## Route Maintenance

DSDV uses periodic updates to maintain routing tables. Nodes broadcast updates with revised sequence numbers or hop counts for other destination nodes. This information is used by other nodes to adjust their tables as needed.

## Opportunities for Performance Improvements

1. Distance-based Triggering: Limit updates to affected destinations and neighbours instead of broadcasting complete tables for minor topology changes, reducing control overhead.
    
2. Zone Routing: Partition the network into zones for localised routing within zones and summary routing between zones, optimising traffic and scalability in large networks.
    
3. Hybrid Routing: Combine DSDV's loop-free properties with proactive updates from lightweight protocols like OLSR to maintain consistent routing information while reducing control traffic.
    

 

 

 

 

## References

_What is MANET | IGI Global_. (2020). Igi-Global.com. [https://www.igi-global.com/dictionary/guaranteeing-quality-service-mobile-hoc/17814#:~:text=A%20MANET%2C%20which%20stands%20for,established%20infrastructure%20or%20centralized%20administration](https://www.igi-global.com/dictionary/guaranteeing-quality-service-mobile-hoc/17814#:~:text=A%20MANET%2C%20which%20stands%20for,established%20infrastructure%20or%20centralized%20administration "https://www.igi-global.com/dictionary/guaranteeing-quality-service-mobile-hoc/17814#:~:text=A%20MANET%2C%20which%20stands%20for,established%20infrastructure%20or%20centralized%20administration").

‌

Rouse, M. (2012, April 10). _Ad Hoc On-Demand Distance Vector_. Techopedia. [https://www.techopedia.com/definition/2922/ad-hoc-on-demand-distance-vector-aodv](https://www.techopedia.com/definition/2922/ad-hoc-on-demand-distance-vector-aodv "https://www.techopedia.com/definition/2922/ad-hoc-on-demand-distance-vector-aodv")

Klein-Berndt, L. (n.d.). _A Quick Guide to AODV Routing_. Retrieved December 15, 2023, from [https://citeseerx.ist.psu.edu/document?repid=rep1&type=pdf&doi=c4962f7b7b41e2147487a67b1ca803dad25f5d01#:~:text=The%20Route%20Error%20Message%20](https://citeseerx.ist.psu.edu/document?repid=rep1&type=pdf&doi=c4962f7b7b41e2147487a67b1ca803dad25f5d01#:~:text=The%20Route%20Error%20Message%20 "https://citeseerx.ist.psu.edu/document?repid=rep1&type=pdf&doi=c4962f7b7b41e2147487a67b1ca803dad25f5d01#:~:text=The%20Route%20Error%20Message%20")(RERR)

‌

‌

 

Task 2

# Improvements to LEACH Protocol

The Low-Energy Adaptive Clustering Hierarchy (LEACH) protocol is a hierarchical protocol where the majority of the nodes transmit their packets to a cluster head, and the cluster heads aggregate the data and forwards it to the base station. Nodes are chosen at random to become cluster heads at each round of transmission (Wikipedia Contributors, 2023). This report reviews five papers with proposed improvements to the LEACH protocol.

1. # **Improved LEACH Protocol for Wireless Sensor Networks** (Kumar & Kaur, 2011):  This paper focuses on the energy usage requirement of the original LEACH protocol. It proposed two main changes:
    
2. Residual Energy Selection - I-LEACH selects nodes to become cluster heads based on the node’s residual energy, instead of probability or random selection as used in LEACH.
    
3. Distance-based Clustering - Clusters are formed based on coordinates and node locations. This guarantees that a cluster head is within reasonable distance to every sensor node, minimising long-distance transmissions and energy consumption.
    

Results from the paper show that I-LEACH improves the network lifespan, going 171 more rounds, and is 15% more energy efficient

 

4. **LEACH-A: An adaptive method for improving leach protocol** (Zhao & Yang, 2014): This paper proposed an adaptive routing protocol with an energy threshold E0. A cluster head is selected from among the nodes whose residual energy is greater than E0, based on which node has the greatest energy. This ensures that nodes with higher energy reserves are more likely to become a cluster head, balancing the energy load distribution
    

LEACH-A has a 20-30% increase in network lifetime as compared to LEACH, especially in simulations with varying node energy levels.

 

5. **LEACH-B: An Improved LEACH Protocol for Wireless Sensor Networks (**Mu & Tang, 2010**):** With the LEACH-Balanced, the first selection of cluster heads is done according to the original LEACH protocol. However, a second selection is done to modify the number of cluster heads, based on the node’s energy levels. This allows the energy within each cluster to be maintained at a near-optimal state.
    

 

6. **An improvement on LEACH protocol (Cell-LEACH)** (Yektaparast et al, 2014)**:** This approach introduces a cellular structure to the network, dividing it into smaller cells with dedicated cluster heads. Nodes within a cell communicate directly with their designated cluster head, minimising hops and energy consumption. Cell-LEACH also incorporates a dynamic cluster head selection mechanism based on residual energy.
    
7. # **An improvement on LEACH protocol (EZ-LEACH)** (Salmabadi et al, 2015)**:** EZ-LEACH focuses on simplifying the LEACH protocol to reduce computational complexity and overhead. It utilises a static cluster head selection based on node IDs, eliminating the need for dynamic calculations and message exchanges. Additionally, EZ-LEACH employs data aggregation and compression at cluster heads, similar to LEACH-B.
    

# While EZ-LEACH exhibits slightly lower network lifetime compared to other enhanced protocols (approximately 5-10% improvement over LEACH), its simplicity and reduced overhead make it attractive for resource-constrained sensor nodes

 

 

## References

Wikipedia Contributors. (2023, July 24). _Low-energy adaptive clustering hierarchy_. Wikipedia; Wikimedia Foundation. [https://en.wikipedia.org/wiki/Low-energy_adaptive_clustering_hierarchy#:~:text=LEACH%20is%20a%20hierarchical%20protocol,cluster%20head%20in%20this%20round](https://en.wikipedia.org/wiki/Low-energy_adaptive_clustering_hierarchy#:~:text=LEACH%20is%20a%20hierarchical%20protocol,cluster%20head%20in%20this%20round "https://en.wikipedia.org/wiki/Low-energy_adaptive_clustering_hierarchy#:~:text=LEACH%20is%20a%20hierarchical%20protocol,cluster%20head%20in%20this%20round").

Tong, M., & Tang, M. (2010, September). LEACH-B: an improved LEACH protocol for wireless sensor network. In _2010 6th international conference on wireless communications networking and mobile computing (WiCOM)_ (pp. 1-4). IEEE.

Zhao, J., & Yang, L. (2014). LEACH-A: An adaptive method for improving leach protocol. _Sensors & Transducers_, _162_(1), 136.

A. Yektaparast, F. -H. Nabavi and A. Sarmast, "An improvement on LEACH protocol (Cell-LEACH)," _2012 14th International Conference on Advanced Communication Technology (ICACT)_, PyeongChang, Korea (South), 2012, pp. 992-996.

Salmabadi, H., Sarram, M. A., & Adibnia, F. (2015, November). An improvement on LEACH protocol (EZ-LEACH). In _2015 2nd International Conference on Knowledge-Based Engineering and Innovation (KBEI)_ (pp. 956-960). IEEE.