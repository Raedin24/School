# 10.1 Endpoint Security
## 10.1.1 Common Network Attacks
1. **Distributed Denial of Service (DDoS)**
	- Coordinated attack from many devices, called zombies
	- Attacks aim to halt/degrade public access to a website or its resources
2. **Data Breach**
	- Attacks aims to compromise data servers or hosts to obtain confidential information
3. **Malware**
	- Attack aims to infect hosts with malicious software

## 10.1.2 Network Security Devices
1. **VPN-Enabled Router**
	- Provides secure connection to remote users
	- VPN services can be integrated into the firewall
2. **Next-Generation Firewall (NGFW)**
	Provides:
	- Stateful packet inspection
	- Application visibility / control
	- Next-generation intrusion prevention system (*NGIPS* )
	- Advanced malware protection (*AMP* )
	- URL filtering
3. **Network Access Control (NAC) Device**
	- Includes authentication, authorization, and accounting (*AAA* ) services.
	- Can be integrated into an appliance to manage access policies
	- eg. Cisco Identity Services Engine (ISE)

- Cisco **Email Security Appliance (ESA)**  is designed to monitor SMTP traffic(emails). Works by pulling data from a security database to perform real-time checks of email content. Also encrypts outgoing email messages.
- Cisco **Web Security Appliance (WSA)** is designed to monitor HTTP traffic. Can allow/restrict access to certain features such as chat, messaging, video/audio. Can perform URL blacklisting, web app filtering, and encryption and decryption of web traffic.

# 10.2 Access Control
## 10.2.1 Authentication with a Local Password
- Simplest and least secure method to authenticate remote access is to configure a *login* and *password* combo on **console, vty lines**, and **aux ports**
- Does not provide accountability
- Password is sent in plaintext
- Anyone with password can gain access
```shell
line vty 0 4
password cisco
login
```

- **SSH** is more secure, requires username and password, both of which are encrypted during transmission
- Provides accountability: username is recorded during login.
- Authentication can be done using local database
- Local database authentication has limitations:
	- User accounts must be configured locally on each device
	- Provides no fallback authentication method. If password/username is lost, the only option available is password recovery.
- Alternative to local database is having a central server for usernames and passwords
```shell
ip domain-name cisco.com
crypto key generate rsa general-keys modulus 2048
username admin secret class
ip ssh version 2
line vty 0 4
transport input ssh
login local
```

## 10.2.2 AAA Components
**Authentication** - Who are you?
**Authorization** - What can you do?
**Accounting** - What did you do?

## 10.2.3 Authentication
Two method of implementation
1. **Local** - Stores usernames and passwords locally in a network device (eg. router). Ideal for small networks
2. **Server-based** - Router accesses central AAA server which stores all usernames and passwords. Router uses **Remote Authentication Dial-In User Service** *(RADIUS)* or  **Terminal Access Control Systems** (*TACACS+*) protocols to communicate with server

## 10.2.4 Authorization
- Automatic, does not require users to perform additional steps
- Uses a set of attributes that describes the user's access to the network

## 10.2.5 Accounting
- Collects and reports usage data.
- Keeps a detailed log of exactly what the authenticated user does on the device

## 10.2.6 802.1X
- A port-based *access control and authentication protocol*
- Restricts unauthorized workstations from connecting to a LAN through public switch ports
- Each device in the network has specific roles
	1. **Client (Supplicant)**  - A device running 802.1X-compliant client software
	2. **Switch (Authenticator)** - Acts as intermediary b/n client and authentication server. Can alternatively be a *wireless access point*
	3. **Authentication server** - Validates the identity of the client and notifies the authenticator whether client is authorized to access.


# 10.3 Layer 2 Security Threats
Technologies such as **VPNs**, **Firewalls** and **IPS** 
## 10.3.2 Switch Attack Categories
|**Category**|**Examples**|
|---|---|
|**MAC Table Attacks**|Includes MAC address flooding attacks.|
|**VLAN Attacks**|Includes VLAN hopping and VLAN double-tagging attacks. It also includes attacks between devices on a common VLAN.|
|**DHCP Attacks**|Includes DHCP starvation and DHCP spoofing attacks.|
|**ARP Attacks**|Includes ARP spoofing and ARP poisoning attacks.|
|**Address Spoofing Attacks**|Includes MAC address and IP address spoofing attacks.|
|**STP Attacks**|Includes Spanning Tree Protocol manipulation attacks.|
## 10.3.3 Switch Attack Mitigation
|**Solution**|**Description**|
|---|---|
|**Port Security**|Prevents many types of attacks including MAC address flooding attacks and DHCP starvation attacks.|
|**DHCP Snooping**|Prevents DHCP starvation and DHCP spoofing attacks.|
|**Dynamic ARP Inspection (DAI)**|Prevents ARP spoofing and ARP poisoning attacks.|
|**IP Source Guard (IPSG)**|Prevents MAC and IP address spoofing attacks.|
- Always use secure variants such as **SSH**, Secure Copy Protocol (**SCP**), Secure FTP (**SFTP**), Secure Socket Layer/Transport Layer Security (**SSL/TLS**)
- Use an out-of-band management network for device management
- Use a dedicated management VLAN
- Use ACLs to filter unwanted access
- 