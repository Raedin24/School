**Addressing Table** 

| Device           | Interface | IP Address/Mask                  | Default Gateway |
| ---------------- | --------- | -------------------------------- | --------------- |
| CS Department    | G0/0      |                                  | N/A             |
| Router0          | G0/0      | 2001:db8:acad:a::1/64            | N/A             |
| Router0          | G0/0      | fe80::1                          | N/A             |
| Router0          | G0/1      |                                  | N/A             |
| Router0          | G0/1      | 2001:db8:acad:b::1/64            | N/A             |
| Router0          | G0/1      | fe80::1                          | N/A             |
| LAB 214-A Switch | SVI       |                                  |                 |
| 124-1            | NIC       | 192.168.1.97<br>255.255.255.224  | 192.168.1.126   |
| PC1              | NIC       | 2001:db8:acad:a::ff/64           | fe80::1         |
| 124-5            | NIC       | 192.168.1.98<br>255.255.255.224  | 192.168.1.126   |
| PC2              | NIC       | 2001:db8:acad:a::15/64           | fe80::1         |
| 214-1            | NIC       | 192.168.1.145<br>255.255.255.240 | 192.168.1.158   |
| PC3              | NIC       | 2001:db8:acad:b::ff/64           | fe80::1         |
| Server           | NIC       | 192.168.1.146<br>255.255.255.240 | 192.168.1.158   |
| TFTP Server      |           | 2001:db8:acad:b::15/64           | fe80::1         |

**CS Department Router Config**
```
en
conf t
hostname CS-Department
en secret class
service password-encryption
banner motd "My Router"
security passwords min-length 10
login block-for 120 attempts 2 within 30
no ip domain-lookup
ip domain-name cisco.com
crypto key generate rsa
1024

line console 0
password cisco12345
login
logging synchronous
exec-timeout 60
exit

line vty 0 4
password cisco12345
transport input ssh
login local
logging synchronous
exec-timeout 60
exit

line aux 0
password cisco12345
login
logging synchronous
exec-timeout 60
exit
ip ssh version 2
ip ssh time-out 120
username netadmin privilege 15 secret Cisco_CCNA7

interface g0/0
ip address 192.168.1.126 255.255.255.224
description First Florr LAN
ipv6 address 2001:db8:acad:a::1/64
ipv6 address fe80::1 link-local
no shutdown
exit

int g0/1
ip address 192.168.1.158 255.255.255.240
desc Second Floor LAN
ipv6 address 2001:db8:acad:b::1/64
ipv6 address fe80::1 link-local
no shutdown
exit

ipv6 unicast-routing
exit
copy run start
```

**Lab 214-A Switch**
```
en
conf t
enable secret class
service password-encryption
banner motd # Authorized Users Only! #
no ip domain-lookup

line con 0
password cisco12345
login
logging synchronous
exec-timeout 60
exit

line vty 0 15
password cisco12345
login
logging synchronous
exec-timeout 60
exit

int vlan 1
ip add 192.168.1.157 255.255.255.240
no shut
exit
ip default-gateway 192.168.1.158
exit
do wr
```