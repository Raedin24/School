**Configure Management Interface**

|**Task**|**IOS Commands**|
|---|---|
|Enter global configuration mode.|S1# **configure terminal**|
|Enter interface configuration mode for the SVI.|S1(config)# **interface vlan 99**|
|Configure the management interface IPv4 address.|S1(config-if)# **ip address 172.17.99.11 255.255.255.0**|
|Configure the management interface IPv6 address|S1(config-if)# **ipv6 address 2001:db8:acad:99::11/64**|
|Enable the management interface.|S1(config-if)# **no shutdown**|
|Return to the privileged EXEC mode.|S1(config-if)# **end**|
|Save the running config to the startup config.|S1# **copy running-config startup-config**|
`An IP address applied to the SVI is only for remote management access. Does not allow the switch to route Layer 3 packets`

**Configure Default Gateway**

|**Task**|**IOS Commands**|
|---|---|
|Enter global configuration mode.|S1# **configure terminal**|
|Configure the default gateway for the switch.|S1(config)# **ip default-gateway 172.17.99.1**|
|Return to the privileged EXEC mode.|S1(config)# **end**|
|Save the running config to the startup config.|S1# **copy running-config startup-config**|
```bash
enable
configure terminal
hostname S1
no ip domain lookup
enable secret class
line console 0
password cisco
login
line vty 0 4
password cisco
login
exit
banner motd # Authorized Users Only #
service password-encryption
exit
copy running-config startup-config
```

hostname S2 - Sets device name on network
no ip domain lookup - Prevents network device from trying to do NAT / map to any domain
enable secret `class` - Prevents entry into privilege exec mode. `class` is the password to be set.
- - -
line console 0 - Switches to conf mode to line-configuration mode
password `cisco` - Sets a password for console 0 user exec mode
login - Enforces the password set above
line vty 0 4 - Same as line console, but for remote logins like SSH or Telnet
password `cisco`
login
exit
- - -
banner motd # Authorised Users Only # - Sets a message of the day
~~~
secret has a higher encryption level than password
~~~
service password-encryption - Encrypts the passwords used so far
copy running-config startup-config - Saves the running configuration to the startup configuration. Same as `do wr`.

```
interface range f0/4 f0/24
shutdown
```
Can shut down access to all ports in that range


# PTSA Codes
```Shell
---------------------------Router------------------------------

enable
conf t
hostname Town-Hall
enable secret class
line console 0
password cisco
login
line vty 0 4
password cisco
login
loggin synchronous
exit

security passwords min-length 10
service password-encryption
username netadmin secret Cisco_CCNA7
ip domain-name cisco.com
crypto key generate rsa
1024
ssh version 2
line vty 0 4
login local
transport input ssh

interface g0/0
ip address 192.168.1.126 255.255.255.224
ipv6 address 2001:db8:acad:a::1/64
ipv6 address fe80::1 link-local
description Connected to IT Department Switch
no shutdown

interface g0/1
ip address 192.168.1.158 255.255.255.240
ipv6 address 2001:db8:acad:b::1/64
ipv6 address fe80::1 link-local
description Connected to Administration Switch
no shutdown
exit

ipv6 unicast-routing
banner motd # Authorized Users Only #


----------------------------Switch-----------------------------

enable
conf t
interface vlan 1
ip address 192.168.1.157 255.255.255.240
exit
ip default-gateway 192.168.1.158
interface vlan 1
description Management VLAN
no shutdown

line vty 0 15
password cisco
login
```

**Subnetting Table**

|   |   |   |   |   |   |   |   |
|---|---|---|---|---|---|---|---|
|192.168.1.0/24|   |   |   |   |   |   |   |
|Subnet No.|Num. Hosts|Network Address|First Usable IP|Last Usable IP|Broadcast Address|Subnet Mask|Prefix Length|
|Subnet 1|30|192.168.1.0|192.168.1.1|192.168.1.30|192.168.1.31|255.255.255.224|/27|
|Subnet 2|30|192.168.1.32|192.168.1.33|192.168.1.62|192.168.1.63|255.255.255.224|/27|
|Subnet 3|30|192.168.1.64|192.168.1.65|192.168.1.94|192.168.1.95|255.255.255.224|/27|
|Subnet 4|30|192.168.1.96|192.168.1.97|192.168.1.126|192.168.1.127|255.255.255.224|/27|
|Subnet 5|14|192.168.1.128|192.168.1.129|192.168.1.142|192.168.1.143|255.255.255.240|/28|
|Subnet 6|14|192.168.1.144|192.168.1.145|192.168.1.158|192.168.1.159|255.255.255.240|/28|
|Subnet 7|14|192.168.1.160|192.168.1.161|192.168.1.174|192.168.1.175|255.255.255.240|/28|
|Subnet 8|14|192.168.1.176|192.168.1.177|192.168.1.190|192.168.1.191|255.255.255.240|/28|

**IP Address Table**

|   |   |   |   |
|---|---|---|---|
|**Device**|**Interface**|**IP Address/Mask**|**Default Gateway**|
|Town Hall|G0/0|192.168.1.126/27|N/A|
||G0/0|2001:db8:acad:a::1/64|N/A|
||G0/0|fe80::1|N/A|
||G0/1|192.168.1.158/28|N/A|
||G0/1|2001:db8:acad:b::1/64|N/A|
|Router0|G0/1|fe80::1|N/A|
|Administration Switch|SVI|192.168.1.157/28|192.168.1.158|
|Reception Host|NIC|192.168.1.100/27|192.168.1.126|
|PC1|NIC|2001:db8:acad:a::ff/64|fe80::1|
|Operator Host|NIC|192.168.1.110/27|192.168.1.126|
|PC2|NIC|2001:db8:acad:a::15/64|fe80::1|
|IT Host|NIC|192.168.1.145/28|192.168.1.158|
|PC3|NIC|2001:db8:acad:b::ff/64|fe80::1|
|Server|NIC|192.168.1.147/28|192.168.1.158|
|TFTP Server|NIC|2001:db8:acad:b::15/64|fe80::1|
