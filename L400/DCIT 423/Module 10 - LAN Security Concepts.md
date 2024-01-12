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
Technologies such as **VPNs**, **Firewalls** and **IPS** devices are used to protect *Layer 3 to Layer 7*. However, if the Layer 2 is compromised, all subsequent protections are rendered useless, hence the need for Layer 2 security
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

# 10.4 MAC Address Table Attack
## 10.4.1 Switch Operation Review
- Layer 2 switch builds a MAC address table based on the source MAC address in received frames. This info is used to make forwarding decisions
- MAC address tables are stored in volatile memory

## 10.4.2 MAC Address Table Flooding
- MAC address tables have a fixed sized
- MAC address flooding spams fake MAC addresses until the switch MAC table is full.
> When full, the switch treats frames as unknown unicast and floods all incoming traffic out on all ports on the same VLAN
- This allows external actors to capture all frames sent from one host to another on the local LAN / VLAN
`Traffic is flooded only with the local LAN/VLAN. Traffic can only be captured if the threat actor is connected.`

- Port security must be implement to mitigate MAC address table overflow attacks.
- This allows only a specified number of source MAC address to be learned on the port

# 10.5 LAN Attacks
## 10.5.2 VLAN Hopping Attack
- Enables traffic from one VLAN to be seen by another VLAN without the aid of a router
- Threat actor configures the host to *act like a switch*  and spoof **802.1Q** and **DTP signalling** to establish a trunk with the connecting switch
- This allows them to send and receive traffic on any VLAN

## 10.5.3 VLAN Double-Tagging Attack
- Allows a frame to go to a VLAN that the original tag did not specify
- Threat actor embeds a *hidden*  **802.1Q** tag inside a frame that already has an 802.1Q tag.
- Only works if attacker is connected to a port which is in the *same VLAN as the native VLAN*  of the trunk port
- Can be prevented by:
	1. Disable trunking on access ports
	2. Disable auto trunking and use manual trunking as needed
	3. *Native VLANs*  should only be used *on trunk links*.

## 10.5.5 DHCP Attacks
There are **2** types of DHCP attacks

**DHCP Starvation Attack**
- Goal is to create a *denial  of service (DOS)*
- Threat actor creates DHCP discovery messages from fake MAC addresses
- This allows it to consume all available IP addresses

**DHCP Spoofing Attack**
- Threat actor configures rogue DHCP server on network to provide false IP configuration parameters to legitimate clients
- In the *DHCPOFFER* stage, both the legitimate and rogue server offer IP configuration details to the client
- If the rogue server's offer is received first, the client completes the DHCP process with the rogue server.
- If not, in the *DHCPACK*  stage, the rogue server sends out its own acknowledgement packet and can provide the wrong default gateway, DNS server and IP address for client

## 10.5.7 ARP Attacks
**ARP Spoofing and ARP Poisoning Attack**
- A client can send an unsolicited ARP reply, called a *gratuitous ARP*
- This is a broadcast that the host has a specific IP address that is mapped to a specific MAC address
- Other hosts store the MAC and IP address of the gratuitous ARP in their ARP tables
- If a threat actor sends a gratuitous ARP with  a spoofed MAC address, any host can claim to be the owner of any IP and MAC address of their choice