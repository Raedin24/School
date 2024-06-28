```shell
enable
conf t
ip route 172.31.10.0 255.255.255.0 GigabitEthernet0/0/0
ip route 172.31.20.0 255.255.255.0 GigabitEthernet0/0/0
ip route 172.31.30.0 255.255.255.0 GigabitEthernet0/0/0

no ip domain-lookup
enable secret class

line con 0
password cisco
login
exit

line vty 0 4
password cisco
login
exit

banner motd # Authorized Access Only! # 
hostname R-1
service password-encryption

int g0/0/0
ip address 172.31.0.1 255.255.255.0
desc "R1 G0/0/0"
no shutdown
exit

int s0/1/0
ip address 209.165.201.2 255.255.255.252
desc "R1 S0/1/0"
no shutdown
exit

int g0/0/1
no shutdown

int g0/0/1.40
desc "Gateway for VLAN40"
encap dot1q 40
ip address
exit

int g0/0/1.40
desc "Gateway for VLAN40"
encap dot1q 40
ip address
exit

int g0/0/1.40
desc "Gateway for VLAN40"
encap dot1q 40
ip address
exit

int g0/0/1.40
desc "Gateway for VLAN40"
encap dot1q 40
ip address
exit
```