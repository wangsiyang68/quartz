## Privileges
CPL = Current Privilege Level
DPL = Descriptor Privilege Level
- each interrupt has a dpl

## Interrupts
Context: Cannot jump to a kernel address, but a user need to access kernel space
- Setting CPL must happen in the kernel space, and not the user space
IDT = Interrupt Descriptor Table

## Virtualization
- Hypvervisor vs container
	- Type 1 & 2 of Hypervisor
	- Aspects to consider
		- Isolation
		- Portability
		- Resource Management
		- Dependency Management
		- Performance vs Isolation Trade Off
			- More performance, less isolation
- Container
	- Only virtualize the OS, isolate Kernel resources, while Hypervisor virutalizes the whole hardware
	- Can limit the resources for each containers
	- Limit Kernel Access for each container/System Call filtre (e.g. only some systems call can be called by container) (minimize TCB)
	- Difference between Chroot?
		- Chroot is more for sekuriti, but it does not necessarily isolate 

## Exploits
- Buffer Overflow in VMM 
	- Target the Monitor
	- Use to escape the VM
## Questions
What types of virtualization are VirtualBox and the WSL?
#ss 