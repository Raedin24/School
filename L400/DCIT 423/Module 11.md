## 11.1.2 Mitigate MAC Address Table Attacks
Simplest and most effective way to prevent MAC address table overflow attacks is to enable port security
Port security
- Limits the number of valid MAC addresses allowed on a port
- Allows admins to manually configure MAC addresses for a port or to permit the switch to dynamically learn a limited number of MAC addresses.

## 11.1.3 Enable Port Security
- Port security can only be configured on manually configured `access` or `trunk` ports 
- Command used is `switchport port-security`
`By default, Layer 2 switch ports are set to dynamic auto (trunking on)`

```Bash
interface f0/1
switchport mode access
switchport port-security
```

To view the port security configuration
```Bash
show port-security interface f0/1
```
## 11.1.4 Limit and Learn MAC Addresses
The switch can be configured to learn MAC addresses in 3 ways
1. **Manually configured** - Admin manually configures a static MAC address
`switchport port-security mac-address *mac-address*`
2. **Dynamicall learned** - 