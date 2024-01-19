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

## Initial Device Settings
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


# DHCP Configuration
| **Task** | **IOS Command** |
| ---- | ---- |
| Exclude addresses | **ip dhcp** excluded-address *low-address*  [*high-address*] |
| Define pool name | **ip dhcp** pool *pool-name* |
| Define the address pool. | **network** _network-number_ [_mask_ \| / _prefix-length_] |
| Define the default router or gateway. | **default-router** address [ _address2….address8_] |
| Define a DNS server. | **dns-server** _address_ [ _address2…address8_] |
| Define the domain name. | **domain-name** _domain_ |
| Define the duration of the DHCP lease. | **lease** {_days_ [_hours_ [ _minutes_]] \| **infinite**} |
| Define the NetBIOS WINS server. | **netbios-name-server** _address_ [ _address2…address8_] |

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
|||2001:db8:acad:a::1/64|N/A|
|||fe80::1|N/A|
||G0/1|192.168.1.158/28|N/A|
|||2001:db8:acad:b::1/64|N/A|
|||fe80::1|N/A|
|Administration Switch|SVI|192.168.1.157/28|192.168.1.158|
|Reception Host (PC1)|NIC|192.168.1.100/27|192.168.1.126|
|||2001:db8:acad:a::ff/64|fe80::1|
|Operator Host (PC2)|NIC|192.168.1.110/27|192.168.1.126|
|||2001:db8:acad:a::15/64|fe80::1|
|IT Host (PC3)|NIC |192.168.1.145/28|192.168.1.158|
|||2001:db8:acad:b::ff/64|fe80::1|
|Server (TFTP Server)|NIC|192.168.1.147/28|192.168.1.158|
|||2001:db8:acad:b::15/64|fe80::1|


# SWRE Part 2 Codes
```shell
Sw-A
---------------------------------------------------------

en
conf t
vlan 10
name users
vlan 999
name unused
exit
int range f0/1-5, g0/1
switchport mode access
switchport access vlan 10
int range f0/1-5
switchport port-security
switchport port-sec maximum 4
switchport port-sec violation restrict
switchport port-sec aging time 10
switchport port-sec mac-address sticky
exit
int f0/1
switchport port-sec mac-address 00D0.D3DC.2825
exit
ip dhcp snooping
ip dhcp snooping vlan 10,999
int range f0/1-5, g0/1
ip dhcp snooping limit rate 5
exit
int g0/1
ip dhcp snooping trust
exit
ip arp inspection vlan 10,999
int g0/1
ip arp inspection trust
exit
int range f0/1-5
spanning-tree portfast
spanning-tree bpduguard enable
int range f0/6-24, g0/2
switchport mode access
switchport access vlan 999
shutdown

------------------------------------------------------------


R-B-10
------------------------------------------------------------

en
conf t
int g0/0/0.10
desc WLAN users
encapsulation dot1q 10
ip address 192.168.10.1 255.255.255.0
exit
ip dhcp excluded-address 192.168.10.1
ip dhcp excluded-address 192.168.10.254
ip dhcp pool WLAN-hosts
network 192.168.10.0 255.255.255.0
default-router 192.168.10.1
dns-server 198.51.100.163
exit
int g0/0/1
ip address dhcp
end
exit

en
conf t
ip route 0.0.0.0 0.0.0.0 g0/0/1
ip route 0.0.0.0 0.0.0.0 s0/1/0 10
ipv6 unicast-routing
ipv6 route ::/0 2001:DB8:ACAD:C::1
ipv6 route ::/0 2001:DB8:ACAD:B::1 10


-----------------------------------------------------------

R-1-A
-----------------------------------------------------------

en
conf t
ip route 0.0.0.0 0.0.0.0 g0/0/2
ip route 0.0.0.0 0.0.0.0 s0/1/0 10
ip route 192.168.10.0 255.255.255.0 g0/0/2
ip route 192.168.10.0 255.255.255.0 s0/1/0 10
ip route 192.168.3.122 255.255.255.255 s0/1/1
ipv6 unicast-routing
ipv6 route ::/0 2001:DB8:ACAD:A::2
ipv6 route ::/0 2001:DB8:ACAD:B::2 10
ipv6 route 2001:DB8:ACAD:3::122/128 2001:DB8:ACAD:D::2
```
# SWRE Final Exam
```shell
R1
---------------------------------------------------------------

en
conf t
no ip domain-lookup
hostname R1
banner motd # Authorized Users Only! #
line console 0
password cisco
login
exit
enable secret class
service password-encryption
security passwords min-length 10
username admin secret admin1pass
ip domain-name ccna-ptsa.com
crypto key generate rsa general-keys modulus 1024
ip ssh version 2
line vty 0 15
login local
transport input ssh
exit
int lo0
ip address 209.165.201.1 255.255.255.224
ipv6 address 2001:db8:acad:209::1/64
ipv6 address fe80::1 link-local
desc Loopback/Simulated Internet
exit
ipv6 unicast-routing
int g0/0/1.2
desc Bikes
encap dot1q 2
ip address 10.19.8.1 255.255.255.192
ipv6 address 2001:db8:acad:a::1/64
ipv6 address fe80::1 link-local
exit
int g0/0/1.3
desc Trikes
encap dot1q 3
ip address 10.19.8.65 255.255.255.224
ipv6 address 2001:db8:acad:b::1/64
ipv6 address fe80::1 link-local
exit
int g0/0/1.4
desc Management
encap dot1q 4
ip address 10.19.8.97 255.255.255.248
ipv6 address 2001:db8:acad:c::1/64
ipv6 address fe80::1 link-local
exit
int g0/0/1.6
encap dot1q 6 native
desc Native
exit
int g0/0/1
no shutdown
exit
ip route 0.0.0.0 0.0.0.0 lo0
ipv6 route ::/0 lo0
ip dhcp excluded-address 10.19.8.1 10.19.8.52
ip dhcp pool CCNA-A
network 10.19.8.0 255.255.255.192
default-router 10.19.8.1
domain-name ccna-a.net
exit
ip dhcp excluded-address 10.19.8.65 10.19.8.84
ip dhcp pool CCNA-B
network 10.19.8.64 255.255.255.224
default-router 10.19.8.65
domain-name ccna-b.net
exit

VLAN 2
router subinterface: 10.19.8.1 /26
subnet: 10.19.8.0 /26
host range: 10.19.8.1 - 10.19.8.62
excluded address range: 10.19.8.1 - 10.19.8.52

VLAN 3
router subinterface: 10.19.8.65 /27
subnet: 10.19.8.64 /27
host range: 10.19.8.65 - 10.19.8.94
excluded address range: 10.19.8.65 - 10.19.8.84


---------------------------------------------------------------

S1
---------------------------------------------------------------

en
conf t
no ip domain-lookup
hostname S1
banner motd # Authorized Users Only! #
line console 0
password cisco
login
exit
enable secret class
service password-encryption
username admin secret admin1pass
ip domain-name ccna-ptsa.com
crypto key generate rsa general-keys modulus 1024
ip ssh version 2
line vty 0 15
login local
transport input ssh
exit
int vlan 4
ip address 10.19.8.98 255.255.255.248
desc Management SVI
no shutdown
exit
ip default-gateway 10.19.8.97
vlan 2
name Bikes
vlan 3
name Trikes
vlan 4
name Management
vlan 5
name Parking
vlan 6
name Native
exit
int range f0/1-2
switchport mode trunk
switchport trunk native vlan 6
exit
int f0/5
switchport mode trunk
switchport trunk native vlan 6
exit
int range f0/1-2
channel-group 1 mode active
int f0/6
switchport mode access
switchport access vlan 2
switchport port-security
switchport port-security maximum 3
switchport port-security mac-address sticky
exit
int range f0/3-4,f0/7-24,g0/1-2
switchport mode access
switchport access vlan 5
desc Unused Ports
shutdown
exit


---------------------------------------------------------------

S2
---------------------------------------------------------------

en
conf t
no ip domain-lookup
hostname S2
banner motd # Authorized Users Only! #
line console 0
password cisco
login
exit
enable secret class
service password-encryption
username admin secret admin1pass
ip domain-name ccna-ptsa.com
crypto key generate rsa general-keys modulus 1024
ip ssh version 2
line vty 0 15
login local
transport input ssh
exit
int vlan 4
ip address 10.19.8.99 255.255.255.248
desc Management SVI
no shutdown
exit
ip default-gateway 10.19.8.97
vlan 2
name Bikes
vlan 3
name Trikes
vlan 4
name Management
vlan 5
name Parking
vlan 6
name Native
exit
int range f0/1-2
switchport mode trunk
switchport trunk native vlan 6
exit
int range f0/1-2
channel-group 1 mode active
int f0/18
switchport mode access
switchport access vlan 3
switchport port-security
switchport port-security maximum 3
switchport port-security mac-address sticky
exit
int range f0/3-17,f0/19-24,g0/1-2
switchport mode access
switchport access vlan 5
desc Unused Ports
shutdown
exit
```
