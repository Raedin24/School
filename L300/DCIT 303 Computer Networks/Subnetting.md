# Steps
1. Identify class of IP address and default subnet mask
2. Convert subnet mask to binary
3. Convert number of hosts to binary and note the number of bits required. Find the subnet generator and octet position.
	Hosts - [     ]
	SG - [    ]
	Octet position - [    ]
1. Starting from the right, reserve a number of 0's corresponding to the number of bit required. The first 1 after that is the subnet generator (the number of hosts, not actual value. Refer to last row of table 2)
2. Generate new subnet mask
3. Use subnet generator to find the network ranges(subnets)

 |  Subnetting Table |
 | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
 | Subnet | 1 | 2 | 4 | 8 | 16 | 32 | 64 | 128 | 256 |
 | Host | 256 | 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
 | Mask | /24 | /25 | /26 | /27 | /28 | /29 | /30 | /31 | /32 |
*Table 1*

| 1             | 1             | 1             | 1             | 1             | 1             | 1            | 1            |
| ------------- | ------------- | ------------- | ------------- | ------------- | ------------- | ------------ | ------------ |
| 31, 23, 15, 7 | 30, 22, 14, 6 | 29, 21, 13, 5 | 28, 20, 12, 4 | 27, 19, 11, 3 | 26, 18, 10, 2 | 25, 17, 9, 1 | 24, 16, 8, 0 |
| 0             | 0             | 0             | 0             | 0             | 0             | 0            | 0            |
| 128           | 64            | 32            | 16            | 8             | 4             | 2            | 1            |
 *Table 2*



## Question 1

**Base IP Address** \- 192.168.4.0 / 24

| Host | Network Address | Broadcast Address | Subnet |
| --- | --- | --- | --- |
| 55  | 192.168.4.0 | 192.168.4.63 | /26 |
| 25  | 192.168.4.64 | 192.168.4.95 | /27 |
| 12  | 192.168.4.96 | 192.168.4.111 | /28 |
| 2   | 192.168.4.112 | 192.168.4.115 | /30 |
| 2   | 192.168.4.116 | 192.168.4.119 | /30 |
| 2   | 192.168.4.120 | 192.168.4.123 | /30 |

## Question 2

**Base IP Address** \- 172.16.0.0 / 16

| Host  | Network Address | Broadcast Address | Subnet              |
| ----- | --------------- | ----------------- | ------------------- |
| 11597 | 172.16.0.0      | 172.16.63.255     | /18 (255.255.192.0) |
| 1245  | 172.16.64.0     | 172.16.71.255     | /21 (255.255.248.0) |
| 597   | 172.16.72.0     | 172.16.75.255     | /22                 |
| 297   | 172.16.76.0     | 172.16.77.255     | /23                 |
| 97    | 172.16.78.0     | 172.16.78.127     | /25                 |
| 17    | 172.16.78.128   | 172.16.78.159     | /27                 |
| 2     | 172.16.78.160   | 172.16.78.163     | /30                 |
| 2     | 172.16.78.164   | 172.16.78.167     | /30                 |
| 2     | 172.16.78.168   | 172.16.78.171     | /30                 |



Every movement into the next octect add 1 to the subnet mask

## Question 3

Base IP Address - 172.16.1.0 / 24

| Host | N.A | B.A | Subnet |
| --- | --- | --- | --- |
| 125 | 172.16.1.0 | 172.16.1.127 | /25 (255.255.255.128) |
| 25  | 172.16.1.128 | 172.16.1.223 | /27 (255.255.255.224) |
| 12  | 172.16.1.160 | 172.16.1.175 | /28 (255.255.255.240) |
| 2   | 172.16.1.176 | 172.16.1.179 | /30 (255.255.255.252) |
| 2   | 172.16.1.180 | 172.16.1.183 | /30 (255.255.255.252) |
| 2   | 172.16.1.184 | 172.16.1.187 | /30 (255.255.255.252) |

|     |     |     |     |
| --- | --- | --- | --- |
| Solution |     |     |     |
| Known |     |     | Problem |
