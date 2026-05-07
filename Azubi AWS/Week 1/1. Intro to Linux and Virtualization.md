**Virtualization** is a technology that allows one to create virtual versions of physical hardware, OS, storage or networks.
- Enables multiple OS to run on a single physical machine

## **Key Concepts**
**Hypervisor** - The software layer that enables virtualization. Manages the creation and running of virtual machines
Has 2 types:
1. **Type 1 (Bare-Metal)**: Runs directly on the host hardware. eg. VMWare ESXi, Microsoft Hyper-V, Xen
2. **Type 2 (Hosted)**: Runs on top of an existing OS. eg. VMWare Workstation, Oracle VirtualBox.

## Benefits of Virtualization
1. **Resource efficiency**: Maximizes hardware utilization by running multiple VMs on a single physical machine.
2. **Isolation**: VMs are isolated from each other, enhancing security and stability
3. **Cost Savings**: Reduces the need for physical hardware
4. **Flexibility**: Easily create, clone, and migrate VMs
5. **Testing and Development**: Provides a sandbox environment for testing new software / configurations

# Linux
- The best-known and most-used open source OS
- Provides the source code for the core functionality of an OS (called ***kernel*** ) which user can modify and expand

## Linux Distributions
- A **distribution** includes the Linux kernel and complementary tools and software applications.
- ![[Pasted image 20260506134957.png]]

**Amazon Linux 2**
- Enterprise-class Linux Distribution
- Designed for use on AWS virtual machines
- Derived from RHEL

## Linux Architecture
1. **Hardware** - Basically the CPU. Cannot directly communicate with users since there is no common language
2. **Kernel** - Acts as the middleman between the user and the hardware. Users communicate to the hardware through the kernel.
3. **Shell** - Executes user commands. Allows users to communicate with the kernel.

### Kernel
- A computer program, the core interface that connects hardware components to the software processes

**Operations performed by a kernel**
1. **Resource Management** - Allocates CPU, RAM, and I/O resources to processes.
2. **Memory Management** - Manages virtual memory and protects memory spaces.
3. **Device Management** - Controls hardware devices via drivers, handles I/O operations and manages interrupts.
4. **System Calls** - Provides a secure interface for applications to request kernel services like file operations and process control.

### Shell
- A **command-line interface (CLI)** that allows users to interact with the OS by typing commands.
- Interprets the commands entered by the user, executes them, and returns the output.
- Acts as the intermediary between the user and kernel
- Eg bash, zsh, fish, tcsh, tmux

