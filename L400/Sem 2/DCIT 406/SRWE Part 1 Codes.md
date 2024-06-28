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

banner motd # Authorized Access Only! #excalidra
```