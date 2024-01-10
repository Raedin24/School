The **Dynamic Host Configuration Protocol (DHCP)** dynamically assigns IP addresses to devices

# 7.1 DHCPv4 Concepts
## 7.1.2 DHCPv4 Operation
- Works in client/server mode
- Client requests and address form the server.
- Client uses that address to connect to the network until lease expires
- Client must communicate with the server occasionally to extend the lease
- Address returns to the pool after lease expires

## 7.1.3 Steps to Obtain a Lease
1. **DHCP Discover** - ***Client*** broadcasts DHCPDISCOVER message containing its *MAC address*. Uses *layer 2 and 3*  broadcast address to communicate with server. Used to find DHCPv4 servers
2. **DHCP Offer** - ***Server***  reserves an available IPv4 address for lease to client.  Also creates *ARP entry* containing the MAC address of the requesting client and the leased IPv4 address of the client. Sends DHCPOFFER to the client
3. **DHCP Request** - ***Client***  sends DHCPREQUEST after receiving DHCPOFFER. Used to notify the selected server for the parameters, and to decline any other servers. Sent as a broadcast
4. **DHCP Acknowledgment** - ***Server***  verifies lease info with an *ICMP ping*  to confirm the address is available. Creates new ARP entry for the client lease and sends DHCPACK message to client.
## 7.1.4 Renewing a Lease
1. DHCP Request: Client sends a request message to server that offered the IPv4 address. If no acknowledgement is received in time, client broadcasts another DHCPREQUEST so another server can extend the lease
2. DHCP Acknowledgement: Server verifies lease information by returning a DHCPACK.
`Both messages can be sent as unicast or broadcast messages`

# 7.2 Configure a Cisco IOS DHCPv4 Server
`A router can be configured to act as a DHCPv4 server`

## 7.2.2 Steps to Configure
1. **Exclude IPv4 addresses** : Router assigns all addresses in the address pool unless specifically excluded. Excluded address should be those manually configured for other devices.
2. **Define a DHCPv4 Pool Name** : Defines a pool with a specific name and puts the router in DHCPv4 configuration mode
3. **Configure the DHCPv4 Pool** : Define the *range of available address* and the *default gateway router* (typically the LAN interface of the router closest to the client)
- Can assign up to **8 gateways** if multiple gateways are required.
- Default lease period is **1** day
- DHCPv4 is enabled by default. Use `no service dhcp` to deactivate

## 7.2.8 DHCPv4 Relay
- In situations where the DHCP server is located on another network, the router cannot forward broadcasts from the clients to the server. **R1** has to be configured to relay DHCPv4 messages to the server
1. **ipconfig /release** - Admin releases all current IPv4 addressing information (**ifconfig** for other systems)
2. **ipconfig /renew** - Admin attempts renews IPv4 addressing info. The PC broadcasts and DHCPDISCOVER message. Request is not successful because router does not forward broadcasts.
3. **ip helper-address** *address* - **R1** has to be configured with this command and the address of the server to relay DHCPv4 broadcasts to the server.
4. **show ip interface** - **R1** accepts broadcast request and forwards them as a unicast to the DHCP server address. Admin can use the `show ip interface` command to verify the configuration
5. **ipconfig /all** - Admin can verify that PCs are able to receive IP addresses with the `ipconfig /all` command

## 7.2.9 Other Service Broadcasts Relayed
By default the `ip helper-address` command forwards the following eight UDP services
1. Port 37: Time
2. Port 49: TACACS
3. Port 53: DNS
4. Port 67: DHCP/BOOTP server
5. Port 68: DHCP/BOOTP client
6. Port 69: TFTP
7. Port 137: NetBIOS name service
8. Port 138: NetBIOS datagram service