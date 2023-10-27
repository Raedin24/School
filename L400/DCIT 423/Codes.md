hostname S2 - Sets device name on network
no ip domain lookup - Prevents network device from trying to do NAT / map to any domain
enable secret `class` - Prevents entry into privilege exec mode. `class` is the password to be set.
line console 0 - Switches to conf mode to line-configuration mode
password `cisco` - Sets a password for console 0 user exec mode
login - Enforces the password set above
