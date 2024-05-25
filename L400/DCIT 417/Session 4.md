**Network management** is the monitoring, testing, configuring and trouble-shooting network components to meet a set of requirements
There are **5** ISO areas for network managements
- Configuration management
- Fault management
- Performance management
- Security management
- Accounting management

**Performance management** is the monitoring and control of a network to ensure it is running as efficiently as possible
**Simple Network Management Protocol (SNMP)** provides framework for managing devices in an internet using the *TCP/IP*  protocol suite.
- Consists of **2** parts
	1. Structure of Management Information (SMI)
	2. Management Information Base (MIB)
- Is used by network performance management tools to monitor network performance
- Provides a set of fundamental operations for monitoring and maintaining an internet
- Is an *application-level (Layer 7)* protocol where a few *manager stations*  control a set of *agents*
`Designed as an application layer protocol to allows monitoring of devices from different manufactures, installed on different physical networks`
- **Manager** is a host that runs the SNMP client program
- **Agent** is a router / host that runs the SNMP server program

SNMP defines the format of packets exchanged b/n a manager and an agent.
- Packets contain the *object (variable)* and *status (value)*
**SMI** defines the following:
- Rules for naming objects
- Object types
- How to encode objects and values
`SMI only defines the rules, not how objects are managed`
**MIB** creates and maintains a collection of named objects, their types and their relationship to each other