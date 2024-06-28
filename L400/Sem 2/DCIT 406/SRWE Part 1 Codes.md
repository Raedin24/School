**Router R-1 Config**
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
ip address 172.31.40.1 255.255.255.0
exit

int g0/0/1.50
desc "Gateway for VLAN50"
encap dot1q 50
ip address 172.31.50.1 255.255.255.0
exit

int g0/0/1.60
desc "Gateway for VLAN60"
encap dot1q 60
ip address 172.31.60.1 255.255.255.0
exit

int g0/0/1.99
desc "Gateway for VLAN99"
encap dot1q 99 native
ip address 172.31.99.17 255.255.255.240
exit
```

**Switch S-3 Config**
```
enable
configure terminal
int vlan 99
ip address 172.31.99.18 255.255.255.240
no shutdown
exit

ip default-gateway 172.31.99.15
ip domain-name acad.pt
crypto key generate rsa
1024

username admin privilege 15 secret C1sco123!
enable secret C1sco123!
line vty 0 15
transport input ssh
login local
exit
ip ssh version 2

vlan 40
name B3
exit
int vlan 40
ip address 172.31.40.0 255.255.255.0
desc B3
exit

vlan 50
name B4
exit
int vlan 50
ip address 172.31.50.0 255.255.255.0
desc B4
exit

vlan 60
name B5
exit
int vlan 60
ip address 172.31.60.0 255.255.255.0
desc B5
exit

vlan 99
name NetAdmin
exit
int vlan 99
ip address 172.31.99.16 255.255.255.240
desc NetAdmin
exit

int range f0/1-5
switchport mode access
switchport access vlan 40
exit

int range f0/6-10
switchport mode access
switchport access vlan 50
exit

int range f0/11-15
switchport mode access
switchport access vlan 60
exit

int f0/24
switchport mode access
switchport access vlan 99
exit

int g0/1
switchport mode trunk
switchport nonegotiate
switchport trunk allowed vlan 40, 50, 60, 99
switchport trunk native vlan 99
end
copy run start
```