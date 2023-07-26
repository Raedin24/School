# 1. Basic Concepts of Information Security
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
1. Physical risks - Device theft and destruction, network device fault, unavailability due to power failure
2. Network risks -  Internet risk(threats from outside), intranet risk(inside risks)
3. System risks - Database system configuration security, security database, security of services running in the system
4. Information risks - Storage security, transmission security, access security
5. Application risks - Network virus, OS security, email application security, web service security, FTP service security, DNS sevice security
6. Management risks - 

# 3. Common Network Devices
- Network devices are the basic components of a network. They need to be deployed and configured when constructing a network to meet connection or security requirements
## 3.1 Basic Network Devices
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

## 3.2 Device Initial Login
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
