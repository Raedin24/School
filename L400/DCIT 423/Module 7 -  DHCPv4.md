The **Dynamic Host Configuration Protocol (DHCP)** dynamically assigns IP addresses to devices

# 7.1 DHCPv4 Concepts
## 7.1.2 DHCPv4 Operation
- Works in client/server mode
- Client requests and address form the server.
- Client uses that address to connect to the network until lease expires
- Client must communicate with the server occasionally to extend the lease
- Address returns to the pool after lease expires

## 7.1.3 Steps to Obtain a Lease
1. **DHCP Discover** - *Client* broadcasts DHCPDISCOVER message containing its *MAC address*. Uses *layer 2 and 3*  broadcast address to communicate with server. Used to find DHCPv4 servers
2. **DHCP Offer** - *sDHCPOFFER*
3. **DHCP Request** - DHCPREQUEST
4. **DHCP Acknowledgment** - DHCPACK
 