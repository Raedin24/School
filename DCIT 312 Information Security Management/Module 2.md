# 2. Common Server Types and Threats
- A server is a computer system that provides services to other machines over a network
- A server is a high-performance computer that provides business services to external computers/clients through a network.
## 2.1 Server Overview
Services provided by servers
- Web applications
- File download
- Database-based storage

Features of servers
- Availability
- Usability
- Scalability
- Manageability
![9b9e100934fcf6eced74906e21dcbc36.png](9b9e100934fcf6eced74906e21dcbc36.png)
![5ad61048bc326c38836614ce83ef407e.png](5ad61048bc326c38836614ce83ef407e.png)
### Types (by appearance)
1. Rack Server
	- Best-selling
	- Small chasis
	- Multiple servers can be installed in one cabinet
2. Tower Server
	- Traditional type
	- Large chassis
	- High internal scalability
	- Large area
3. Blade Server
	- High-density server
	- Energy efficient
	- Centralized management
	- Quick deployment
4. Cabinet Server
	- High-end enterprise server
	- Complex internal structure with large number of devices
	- Many different device units may be placed in the same cabinet
## 2.2 Common Server Software
- Software works in client/server (C/S) or browser/server(B/S) mode.
1. File Server - Provides file sharing services to clients
2. Database Server - Consists of one/more computers and a DBMS running on a LAN. Services include query, update, security and multi-user access control
3. Mail server - Used to manage sending and receiving emails. More secure and efficient than free email servers
4. FTP Server - Computer that provides file transfer and access services
5. DNS Server - Consists of a DNS resolver and a DNS server. Stores the domain names and IP addresses of all hosts on a network and can convert a domain name into the corresponding IP address

## 2.3 Server Security Threats
1. **Malicious Programs**
	- Can be divided into 2 categories
		- Dependent on host programs that cannot take effect without an application
		- Independent threats in a self-contained program that can be scheduled and run by an OS
	- Includes Trojan horses, worms and viruses
2. **Brute force cracking by hackers**
	- Used to acquire passwords when conventional means fail
	- Exhaustive search method in which hacker tries many possible combinations to obtain the password
3. **SQL Injections**
	- Is when malicious SQL commands are inserted into the input field of a web form, or into the query string of a page
	- Used to deceive the server to execute malicious SQL commands
	- Commands are used to build / manipulate dynamic SQL commands
4. **DDoS attacks***
	- Targets large sites such as commercial companies, search engines and government departments
	- Launched by multiple controlled machines to a specific target

 ![ebf99a2341fd65a0e5fa5d2d5da39261.png](ebf99a2341fd65a0e5fa5d2d5da39261.png)
 
 ## 2.4 Vulnerabilities and Patches
 A vulnerability is a defect/weakness in the hardware, software or protocols of computer system security policies
 - Basically anything that can be exploited by a threat to gain unauthorized access to information or to disrupt critical processing
### Vulnerability Classification
1. By exploitation 
	1. Local
	2. Remote
2. By location
	1. OS
	2. Network protocol stack
	3. Non-server program
	4. Hardware
	5. Password recovery
3. By level of threat to the system and possibility of being exploited
	1. High-level
	2. Medium-level
	3. Low-level
Causes
- Defects in software / protocol design
- Bugs in software
- Improper system configuration
- Limited security awareness

