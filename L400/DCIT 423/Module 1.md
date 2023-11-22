# Configure a Switch with Initial Settings
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
```terminal
S1(config)# boot system flash:/c2960-lanbasek9-mx.150-2.SE/c2960-lanbasek9-mz.150-2.SE.bin
```
