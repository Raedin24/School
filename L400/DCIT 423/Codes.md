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
en - En
conf t
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
service running-config - Encrypts the passwords used so far