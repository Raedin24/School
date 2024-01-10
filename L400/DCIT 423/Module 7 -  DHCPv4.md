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
4. **DHCP Acknowledgment** - ***Server***  DHCPACK
 