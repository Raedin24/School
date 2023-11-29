**Configure Management Interface **

|**Task**|**IOS Commands**|
|---|---|
|Enter global configuration mode.|S1# **configure terminal**|
|Enter interface configuration mode for the SVI.|S1(config)# **interface vlan 99**|
|Configure the management interface IPv4 address.|S1(config-if)# **ip address 172.17.99.11 255.255.255.0**|
|Configure the management interface IPv6 address|S1(config-if)# **ipv6 address 2001:db8:acad:99::11/64**|
|Enable the management interface.|S1(config-if)# **no shutdown**|
|Return to the privileged EXEC mode.|S1(config-if)# **end**|
|Save the running config to the startup config.|S1# **copy running-config startup-config**|
`An IP address applied to the SVI is only for remote management access. Does not allow the switch to route Layer 3 packets`

**Configure Default Gateway**

|**Task**|**IOS Commands**|
|---|---|
|Enter global configuration mode.|S1# **configure terminal**|
|Configure the default gateway for the switch.|S1(config)# **ip default-gateway 172.17.99.1**|
|Return to the privileged EXEC mode.|S1(config)# **end**|
|Save the running config to the startup config.|S1# **copy running-config startup-config**|
```bash
enable
configure terminal
hostname S1
no ip domain lookup
enable secret class
line console 0
password cisco
login
line vty 0 4
password cisco
login
exit
banner motd # Authorized Users Only #
service password-encryption
exit
copy running-config startup-config
```

hostname S2 - Sets device name on network
no ip domain lookup - Prevents network device from trying to do NAT / map to any domain
enable secret `class` - Prevents entry into privilege exec mode. `class` is the password to be set.
- - -
line console 0 - Switches to conf mode to line-configuration mode
password `cisco` - Sets a password for console 0 user exec mode
login - Enforces the password set above
line vty 0 4 - Same as line console, but for remote logins like SSH or Telnet
password `cisco`
login
exit
- - -
banner motd # Authorised Users Only # - Sets a message of the day
~~~
secret has a higher encryption level than password
~~~
service password-encryption - Encrypts the passwords used so far
copy running-config startup-config - Saves the running configuration to the startup configuration. Same as `do wr`.

```
interface range f0/4 f0/24
shutdown
```
Can shut down access to all ports in that range