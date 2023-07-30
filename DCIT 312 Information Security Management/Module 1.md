# 1.1 Basic Concepts of Information Security
## 1.1 Information and Information Security
**Information Security** is the process of ensuring safe data communication and preventing issues such as information leakage, modification, and disruption. It refers to the preservation of *confidentiality*, *integrity*, and *availability* of data through security technologies
- *Confidentiality* refers to the secrecy of the information
- *Integrity* is when the information is not tampered with during storage or transmission
- *Availability* refers to who can access the information
Additional principles have been added with the development of internet technologies:
- *Controllability* refers to what can be controlled about the information(when it can be exposed, what actions can be performed eg deletion)
- *Non-repudiation* is concerned with verifying the source of the information 

### Causes of attacks
1. **Direct Cause**
	1. Virus
	2. Vulnerability
	3. Trojan horse
	4. Backdoor program
	5. DDOS attacks
2. **Indirect Cause**
	1. Information System complexity
	2. Human and environment factors

## 1.2 Information Security Risks and Management
### Risks Involved in Information Security
1. **Physical risks** - Device theft and destruction, network device fault, unavailability due to power failure
2. **Network risks** -  Internet risk(threats from outside), intranet risk(inside risks)
3. **System risks** - Database system configuration security, security database, security of services running in the system
4. **Information risks** - Storage security, transmission security, access security
5. **Application risks** - Network virus, OS security, email application security, web service security, FTP service security, DNS sevice security
**6. Management risks**
	1. National policy 
		- Effective national information security regulation. 
		- Specialized agency to manage information security
	2. Enterprise system - Inherits same rules
	3. Management system - Inherits same rules

# 1.2 Information Security Standards and Specification
## 1.2.1 Information Security Standards and Specification
### **Significance of Information Security Standards**
**Standards** are normative documents that are jointly formulated, approved by recognized authorities, and used throught the industry to achieve the best security

International organizations related to information security standardization:
- *International Organization for Standardization(ISO)* - Composed of reps from various organisations. Promotes worldwide proprietary, industrial and commercial standards
- *International Electrotechnical Commission(IEC)* - Prepares and publishes standards for all electrical, electronic and related technologies
Other standards organization:
- *Cyber and Information Security Technical Committee(TC8) of China Communications Standards Association(CSSA)*
- *International Telecommunication Union(ITU)*
- *Internet Engineering Task Force(IETF)*

Common Info Security Standards
1. ISO 27001
2. China: Graded Protection of Information Security (GB)
3. US: Trusted Computer System Evaluation Criteria(TCSEC)
4. EU: Information Technology Security Evaluation Criteria(ITSEC)

## 1.2.2 ISO 27001 ISMS
**ISMS** stands for Information Security Management System.
- Is a set of policies and the standard procedure for an enterprise to systematically organise sensitive information
- Based on the ***BS7799*** standard developed the British Standards Institution(BSI)
- Objective is to minimise risk and ensure business continuity by limiting the impact of a security breach
**Idealogy/Steps of ISMS**
1. *Plan* - Establish an ISMS
2. *Do* - Implement and operate ISMS
3. *Check* - Monitor and review ISMS
4. *Action* - Maintain and improve ISMS

### ISO 27000 ISMS Family of Standards
The most important among this family are the **ISO/IEC 27001** and the **ISO/IEC 27002**
- **ISO/IEC 27001** provides the requirement for an information security management system
- **ISO/IEC 27002** is a supplement for 27001 and provides the guidelines for organisational information security standards and information security management practices
- There are 14 control areas in ISO 27002
![[Pasted image 20230729194532.png]]

### ISO 27001 Project Implementation Methodology
1. **Plan**
	1. Project initiation and variance analysis
	2. Risk assessment
	3. System design and release
2. **Do, Check** - System operation and monitoring. Involves ISMS trial run , system operation monitoring and business continuity management training.
3. **Act** - Certification and continuous improvement. Involves auditing(internal and external)

## 1.2.3 Graded Protection of Information Security
The grades are defined based on the extent of information system damage to citizens, society, and state.
![[Pasted image 20230729205006.png]]
**Graded Protection Process**
1. *Grading* - Primary step
2. *Filing* - Mandatory procedure for notifying the supervision department
3. *Assessment* - Assessment of the status of security protection
4. *Rectification* - Key to the implementation of graded protection
5. *Supervision* - External management of graded protection

# 1.3 Basic Network Concepts
## 1.3.1 TCP/IP Architecture
### Architecture of a Typical Campus Network
1. **Access Layer** - Network components are connected directly to the user or peripherals, such as printers, laptops, smart television
2. **Aggregation Layer** - All traffic from access layer goes to aggregation layer. On this layer, permission controls and ACLs can be applied. Typical layer for application of routing protocols
3. **Core Layer** - Carries all information from within an organisation that is going to the internet or a different network. Might include other routers and firewalls 
4. **Egress zone** - Typically the routers of the service provider

## 1.3.2 Common Network Protocols
# 1.4 Common Network Devices
- Network devices are the basic components of a network. They need to be deployed and configured when constructing a network to meet connection or security requirements
## 1.4.1 Basic Network Devices
1. **Switch** 
	- Works at the data link layer
	- Forwards data *frames*
	- Performs 3 actions
		- Flooding
		- Forwarding
		- Discarding
		-  Determines where to send each incoming message frame by looking at the media access control (MAC) address. 
	- Records the source MAC address and the corresponding interface of the received frame in the MAC address table
	- Floods the frame if the destination MAC address of the data frame is not in the MAC address table, or is a broadcast address
	- Discards a frame when it is received on an interface that has the same source and destination MAC address. This is because the switch assumes that the frame is looping back to itself and discards it to prevent a broadcast storm. Will also discard a frame is if the frame contains a VLAN tag which is not allowed on the port.
2. **Router**
	- Selects an optimal path for forwarding data *packets*
3. **Firewall**
	- Used to protect one network area against network attacts and intrusions from other network areas
Link to extra [info](https://www.cisco.com/c/en/us/products/security/firewalls/what-is-a-firewall.html)
![e8e594e9d29cbf6fdd3d31d165cf1980.png](e8e594e9d29cbf6fdd3d31d165cf1980.png)
![394308ea0421fc08469a1298a5554e0f.png](394308ea0421fc08469a1298a5554e0f.png)

**Firewall Security Zone**
- A security zone is a portion of a network that has specific security requirements set. 
- Each zone consists of a single interface or a group of interfaces, to which a security policy is applied
- More [info](https://www.kwtrain.com/blog/network-security-zones)

## 1.4.2 Initial Device Login
`3.2.1 Basic Service Configurations`

**Versatile Routing Platform**
- Universal OS platform for Huawei datacom products
- Supports multiple types of devices
- Provides TCP/IP routing services

**Command Line**
- CLI is divided into command views
	- User view
	- System view
	- Interface view
	- Protocol view
- Commands can only be executed after entering the command view
- **Help(?)**
	- *Full help* -  Displays all the keywords and parameters of a command view
	- *Partial help* - Displays all keywords and parameters that start with the character/string entered
- **Tab**
	- Complete command if there is only one match for a keyword
	- Displays possible commands if there are multiple matches

**Device Login Management**
Devices can be logged into via
- Console
- Telnet
- SSH
- Web
1. **Console**
	- In device manager, check params of the local port
	- Configure the connection interface and communication params
2. **Web Login**
	- Set IP address obtaining mode to obtain an IP address automatically
	- Directly connect Ethernet Interface to default management interface, or connect via switch
	- Enter https://192.168.0.1 in browser to access login page
	- Enter default username and password
- To login through the service interface, configure the web login function on the device
	- Enable web management function
	- Enable HTTP or HTTPS management
	- Set port number
	- Configure a web admin
	- Configure the login interface
3. **Telnet**
	- Disabled by default on NGFW. First login NGFW through other means and enable Telnet service
	- Configure a Telnet admin
	- Configure the login interface
4. **SSH** 
	- Provides more security and authentication functions for login
	- Can be configured on the USG inteface

![07d08ece16c110ce50ed3f3c3fa24bc6.png](07d08ece16c110ce50ed3f3c3fa24bc6.png)
![b1ea494c8329cae523122a350c66077d.png](b1ea494c8329cae523122a350c66077d.png)

`3.2.2 Basic System Settings`
**Device File Management**
Can be used for
- Configuration file management
- System file management (Software upgrade)
- License management

1. **Configuration file managements**
File types
- *Saved-configuration* - Used for the next startup of the USG. Is stored in the flash memory or CF card of the USG. Persists across restarts
- *Current-configuration* - The configuration currently in use. Similar properties as saved-configuration
- Common operation for the config file
	- Save file
	- Erase file(restore to factory settings)
	- Configure file for next startup
	- Restart device
2. **Version Upgrade**
Steps
	- > System
	- > System Upgrade
	- > One-click upgrade
3. **License Configuration**
	- A license is provided by a vendor to authorize the usage scope and validity period of product features
	- It controls whether certain features are available
	- Steps
		 - >System
		- >License Management
		- >Upload license file

# 1.5 Common Information Security Threats
## 1.5.1 Current Situation of Information Security Threats
## 1.5.2 Threats to Network Security
## 1.5.3 Threats to Application Security
1*