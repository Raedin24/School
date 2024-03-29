# 15.1 Static Routes
## 15.1.1 Types of Static Routes
Static routes can be configured for IPv4 and IPv6.
Four types of static routes:
1. Standard static route
2. Default static route
3. Floating static route
4. Summary static route

## 15.1.2 Next-Hop Options
The next hop can be identified either by an *IP address*, *exit interface*, or both. How the destination is identified creates one of **3** types of static route
1. **Next-hop route** - Only next-hop IP address specified
2. **Directly connected static route** - Only router exit interface specified
3. **Fully specified static route** - Both next-hop IP and exit interface specified.
`Directly connected static routes should only be used with point-to-point serial interfaces`
`Fully specified static routes are used when the exit interface is a multi-access interface and it is necessary to specifically identify the next hop`
## 15.1.3 IPv4 Static Route Command
```shell
ip route network-address subnet-mask {ip-address | exit-intf [ip-address]} [distance]
```

|**Parameter**|**Description**|
|---|---|
|_network-address_|Identifies the destination IPv4 network address of the remote network to add to the routing table.|
|_subnet-mask_|- Identifies the subnet mask of the remote network.<br>- The subnet mask can be modified to summarize a group of networks and create a summary static route.|
|_ip-address_|- Identifies the next-hop router IPv4 address.<br>- Typically used with broadcast networks (i.e., Ethernet).<br>- Could create a *recursive static route*  where the router performs an additional lookup to find the exit interface. |
|_exit-intf_|- Identifies the exit interface to forward packets.<br>- Creates a *directly connected static route*.<br>- Typically used in a point-to-point configuration. |
|_exit-intf ip-address_|Creates a *fully specified static route*  because it specifies the exit interface and next-hop IPv4 address. |
|_distance_|- Optional command that can be used to assign an administrative distance value between 1 and 255.<br>- Typically used to configure a *floating static route* by setting an administrative distance that is higher than a dynamically learned route. |

## 15.1.4 IPv6 Static Route Command
```shell
ipv6 route ipv6-prefix/prefix-length {ipv6-address | exit-intf [ipv6-address]} [distance]
```

|**Parameter**|**Description**|
|---|---|
|_ipv6-prefix_|Identifies the destination IPv6 network address of the remote network to add to the routing table.|
|_/prefix-length_|Identifies the prefix length of the remote network.|
|_ipv6-address_|- Identifies the next-hop router IPv6 address.<br>- Typically used with broadcast networks (i.e., Ethernet)<br>- Could create a recursive static route where the router performs an additional lookup to find the exit interface.

Remaining parameters are similar in function to IPv4
`ipv6 unicast-routing` must be configured to enable IPv6 routing
`If the IPv6 static route uses a link-local address as the next-hop address, use a fully specified static route.'
> Reason is because link-local addresses are not contained in the IPv6 routing table. Link-local addresses are only unique on a given link/network, buy other networks might also have that link-local address

# 15.2 Configure IP Static Routes
Requires hands-on configuration. No notes needed. Commands are specified above

# 15.3 Configure IP Default Static Routes
## 15.3.1 Default Static Route
A **default route** is a static route that matches all packets. 
- Used to represent any network that is not in the routing table. 
- Commonly used when connecting an edge router to an ISP network, or connecting to a stub router.
**IPv4 Default Static Route**
```shell
ip route 0.0.0.0 0.0.0.0 {ip-address | exit-intf}
```
`Default IPv4 route is aka a quad-zero route`

**IPv6 Default Static Route**
```shell
ipv6 route ::/0 {ip-address | exit-intf}
```

`The IPv6 subnet mask and the IPv6 prefix-length determine how many bits must match b/n the destination IP and the route in the routing table`

# 15.4 Configure Floating Static Routes
## 15.4.1 Floating Static Routes
A **floating static route** is used to provide a backup path to a primary static or dynamic route, in case of link failure.
- It will only be used when the primary route is not available
- Configured with a higher administrative distance than the primary route