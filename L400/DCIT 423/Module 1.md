# 1.1 Configure a Switch with Initial Settings
## 1.1.1 Switch Boot Sequence
Switches go through a five-step boot sequence before configuration can be done.
1. The switch loads a *power-on-self-test (POST)* program stored in ROM. POST checks the CPU subsystem, and tests the CPU, DRAM, and the flash file system
2. Switch loads the *boot loader*  software. Stored in the ROM
3. The boot loader performs *low-level CPU initialization*. It initializes the CPU registers, which control where physical memory is mapped, quantity of memory, and its speed.
4. Boot loader initializes the *flash file system*  on the system board.
5. Boot loader locates and loads a default *IOS operating system software*  image into memory and gives control of the switch to the IOS.
## 1.1.2 Boot System Command
- The switch attempts to auto boot using the info in the *BOOT* environment variable.
- If the variable is not set, the switch attempts to load and execute the first executable file it finds.
- The IOS operating system then initializes the interfaces using the commands found in the startup-config file.
- The startup-config file is located in *flash*  and is called the **config.text**.
```Shell
S1(config)# boot system flash:/c2960-lanbasek9-mx.150-2.SE/c2960-lanbasek9-mz.150-2.SE.bin
```
	- `boot system` - main command
	- `flash`: - storage device
	- `c2950...SE/` - path to file system
	- `c2950...SE.bin` - IOS file name

## 1.1.3 Switch LED Indicators
1. **System LED** - Shows whether the system is receiving power and functioning properly. 
	1. Off = no power
	2. Green = normal operation
	3. Amber = on but not functioning properly
2. **(RPS) LED** - Shows  Redundant Power Supply status.
	1. Off = off / not connected properly
	2. Green = Connected and ready to provide backup power
	3. Blinking green = Connected but unavailable, being used to power another device
	4. Amber = Standby mode  / has a fault
	5. Blinking amber = Internal power supply failed, RPS is providing power.
3. **Port Status LED (STAT)** - Indicates the port status mode selected
	1. Green = link present
	2. Blinking green = port is sending/receiving data
	3. Alternating green-amber = link fault
	4. Amber/blinking amber = port is blocked to prevent loops
4. **Port Duplex LED (DUPLX)** - Indicates port duplex mode
	1. Off = half-duplex
	2. Green = full-duplex
5. **Port Speed LED (SPEED)** - Indicates port speed mode
	1. Off = Operating at 10 Mbps
	2. Green = 100 Mbps
	3. Blinking green = 1000 Mbps
6.  **Power over Ethernet LED (PoE)** - Will be present only if PoE is supported. 
	1. Off = PoE is not selected, no ports have been denied power
	2. Blinking amber = PoE is not selected, at least one port has been denied power, or PoE has a fault
	3. Amber = PoE for the port is disabled
	4. Green = PoE is selected
	5. Alternating green-amber = PoE is denied because providing power to device will exceed the switch power capacity.

## 1.1.4 System Crash Recovery
The boot loader provides access into the switch in case of OS failure. Can be access through a console connection. 
**Steps to access boot loader**
1. Connect console cable to switch and PC. Configure terminal emulation software to connect to the switch
2. Unplug switch power cord
3. Reconnect power cord, and press and hold *Mode*  button within 15 seconds
4. Continue pressing until *System LED*  turns amber briefly and the solid green
5. Boot loader `switch:` prompt appears in terminal emulation software on PC

**Recovery Steps**
1.  Use `set` to view path to switch BOOT environment variable type
2. Use `flash_init` to view current files in flash
3. Can use `dir flash` to view directories and files in flash
4. Use `BOOT=flash:...` command to change BOOT environment variable path
5. Can use `set` to verify new BOOT environment variable path
6. Use `boot` to load new IOS type

The boot loader supports the following functions
1. Initializing flash
2. Formatting flash
3. Installing new IOS
4. Changing BOOT environment variable
5. Recovery of passwords

## 1.1.5 Switch Management Access
For a switch to allow remote management access, the following have to be in place: 
1. Default gateway
2.  Switch virtual interface (SVI) configured with 
	1. IPv4 address and subnet mask, or
	2. IPv6 address and prefix length for IPv6
`VLAN 1 is used for switch management by default. Recommended to use other VLAN for management for security reasons. `
# 1.2 Configure Switch Ports
## 1.2.1 Duplex Communication
1. **Full-duplex**
	- Is bidirectional
	- Increases bandwidth efficiency by allowing both ends of a connection transmit and receive data simultaneously.
	- Requires microsegmentation. A microsegmented LAN is created when a switch port has only one device connected and is in full-duplex mode.
	- No collision domain
2. **Half-duplex**
	- Is unidirectional
	- Results in collisions since data can only flow in one direction at a time
Use `duplex` to specify the duplex mode
Use `speed` to set the speed of the link
Note that the above can only be done once in a particular interface

`Mismatched settings for duplex and speed can cause connectivity issues`

## 1.2.4 Switch Verification Commands
  

|**Task**|**IOS Commands**|
|---|---|
|Display interface status and configuration.|S1# **show interfaces** [_interface-id_]|
|Display current startup configuration.|S1# **show startup-config**|
|Display current running configuration.|S1# **show running-config**|
|Display information about flash file system.|S1# **show flash**|
|Display system hardware and software status.|S1# **show version**|
|Display history of command entered.|S1# **show history**|
|Display IP information about an interface.|S1# **show ip interface** [_interface-id_]<br><br>OR<br><br>S1# **show ipv6 interface** [_interface-id_]|
|Display the MAC address table.|S1# **show mac-address-table**<br><br>OR<br><br>S1# **show mac address-table**|

## 1.2.6 Network Access Layer Issues
The following can be deduced based on the output of the `show interfaces` command
- Interface up, line protocol down = Encapsulation type mismatch, other interface is error-disabled, hardware problem
- Interface down, line protocol down = Cable not attached, interface problem
- Interface down = Interface manually disabled (`shutdown`)

# 1.3 Secure Remote Access
## 1.3.1 Telnet Operation
-  **TCP  port 23**
- Uses unsecure plaintext transmission of login authentication and data transmitted.
- Packets can easily be monitored using **Wireshark**

### Steps to setup Telnet
enable password admin -- for getting telnet connection
line vty 0 15
password cisco -- for authentication into configuration mode
login - Enables password checking
## 1.3.2 SSH Operation
- **TCP port 22**
- Provides secure connection, and should be used for management connections.
- Session can still be tracked using the IP address of the admin device, however the username and password are encrytped
`To check whether a switch supports SSH, use the 'show version' command. If 'k9' is included in the filename, the switch supports cryptographic features`

### Steps to setup SSH
Switch must have a unique hostname and correct network connectivity settings before configuring SSH

|**Description** | **Command** |
|---|---|
| Verify SSH support | S1# **show ip ssh** |
| Configure the IP domain | S1(config)# **ip domain-name** *cisco.com*|
| Generate RSA key pairs | S1(config)# **crypto key generate rsa**|
| Configure user authentication (locally)| S1(config)# **username** *admin* **secret** *ccna*|
| Configure vty lines| S1(config)# **line vty** *0  15* |
| | S1(config-line)# **transport input ssh** |
| | S1(config-line)# **login local** |
| | S1(config-line)# **exit** |
| Enable SSH version 2 | S1(config)# **ip ssh version** *2* |


```
Generating an RSA key pair automatically enables SSH
Using a longer modulus is more secure, but takes longer to generate and use
Use 'crypto key zeroize rsa' to delete RSA key pair. Also disables SSH

Configuring vty lines with 'transport input ssh' prevents non-SSH connections
Using 'login local' requires local auth for SSH connections
```
