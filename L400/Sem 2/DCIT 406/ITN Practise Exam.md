Subnetting Table

  

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