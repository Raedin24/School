### 11.1.2 Mitigate MAC Address Table Attacks
Simplest and most effective way to prevent MAC address table overflow attacks is to enable port security
Port security
- Limits the number of valid MAC addresses allowed on a port
- Allows admins to manually configure MAC addresses for a port or to permit the switch to dynamically learn a limited number of MAC addresses.

### 11.1.3 Enable Port Security
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
### 11.1.4 Limit and Learn MAC Addresses
The switch can be configured to learn MAC addresses in 3 ways
1. **Manually configured** - Admin manually configures a static MAC address
`switchport port-security mac-address *mac-address*`
2. **Dynamically learned** - When the `switchport port-security` command is entered, current source MAC for devices connected to the port is automatically secured. This address is not saved and will have to be re-learnt after switch reboots.
3. **Dynamically learned - Sticky** - Learned MAC address are saved to the running config. Saving the running config commits the learnt address to *NVRAM*. 

### 11.1.5 Port Security Aging
Used to remove secure MAC addresses without manually deleting the existing secure MAC address
1. **Absolute** - Address are deleted after the specified aging time
2. **Inactivity** - Address are deleted only after a period of inactivity

### Port Security Violation Modes
By default, the security violation mode is set to `shutdown`. Hence, when a port violation occurs, the port enters the `error-disabled` state
**Modes**
1. `shutdown` - Port enters the *error-disabled* state immediately, turns off, sends a syslog message and increments the violation counter. Must be restarted to re-enable the port
2. `restrict` - Port drops packets with unknown source addresses until the number of secure MAC addresses falls below the max allowed, or the max is increased. Increments the violation counter and generates a syslog message
3. `protect` - Similar to *restrict*, except that no syslog message is sent and violation counter is not increased
![[Pasted image 20231206161615.png]]

`Every time a port is in trunk, it needs to be added to the native VLAN`