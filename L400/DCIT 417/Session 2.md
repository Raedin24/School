**Network Simulators**
1. ns-2
2. ns-3
3. OMNeT++
4. openWNS
5. Vienna LTE Simulator

**When to use Simulation**
1. Real computing system not available - Can be due to
	1. Complexity: large networks
	2. Cost: space communications, satellite
	3. Danger: PPDR systems, emergency networks
2. Quick alternative evaluation of
	1. Network topology: star/mesh networks
	2. TCP / UDP for an app
	3. WiMAX or LTE connections
3. Evaluating complex analytical models where the optimal formula is unavailable
	1. QoS solutions
	2. Optimization routing for WSN
	3. Channel access techniques 

**Advantages of Simulation**
1. Cheaper
2. Bugs can be discovered early
3. Can be applied in a wide range (numerical techniques, over topology)
4. Can be tuned to detail

**Disadvantages of Simulation**
1. Accuracy - Might not reflect reality
2. Computationally expensive for large systems
3. Might be slow

## Components
1. **NodeContainer** - A topology helper that provides a way to *create*, *manage* and *access* **Node** objects
2. **PointToPointHelper** - Used to create a point-to-point link b/n nodes. Configure *PointToPointNetDevice*  and *PointToPointChannel*
3. **NetDeviceContainer** - Used to connect two **netdevices**
4. **InternetStackHelper** - Used to install internet protocols in the nodes. Protocols include *TCP*, *UDP*, *IP* etc
5. **Ipv4AddressHelper** - Used to manage the allocation of IP addresses
6. **Ipv4InterfaceContainer** - Used to perform address assignment
7. **Application Package** - Used to simulate the generation and transmission of data packets. Supports **TCP*** and **UDP** traffic
## Simulation Workflow
1. Command Line Arguments
2. Set Attribute Values and Random Seed
3. Create Nodes
4. Create Point-to-Point Links
5. Install the link in nodes
6. Install Communication Protocol stack
7. Add and configure Logical Topology
8. Add and configure Applications
9. Run and End the Simulation