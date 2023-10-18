- Serial ports are used to connect 2 routers together
- `hostname` is used to uniquely identify devices on a network. It can only be changed when in the configuration terminal
- Types of terminals
	- Line
	- Virtual (VTY)
	- Config
- Switches usually only handle MAC addresses
- To handle/configure a switch remotely, an IP address is needed. To assign an IP address to a switch, a VLAN is used
- `enable` is used to move from the user exec mode to the privilege exec mode
- `configure` is used to move from the privilege mode to the configuration terminal
` > - User exec mode , # - Privilege exec mode`
- `enable secret` is the syntax used to lock access from the user exec mode to the privilege exec mode
- `transport` is used to provide unique usernames and passwords to each user
- `copy running-config startup-config` saves the current configuration to the startup-configuration. Can only be run in the privilege exec mode.
- `do wr` saves the configuration in whichever mode is in use

