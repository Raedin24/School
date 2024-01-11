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
2. **Server-based** - Router accesses central AAA server which stores all usernames and passwords. 