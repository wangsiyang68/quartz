# Kernel
The Kernel is the heart of an operating system. It operates on the physical space, which means that it has full knowledge of all physical addresses instead of virtual addresses, and has complete privilege over all the hardware of the computer system. The only way to access the kernel code is when a process runs in the kernel mode, via very specific [[controlled entry points]]

## Contents
1. [[#Kernel Mode]]


## Kernel Mode
The kernel runs with special privileges, called the kernel mode. It can do what normal [[User Programs]] cannot do:
1. Ultimate access and control to all hardware in the computer system (mouse, keyboard, display, network cards, disk, RAM, CPU, etc)
2. Know (and lives in) the physical address space and manages the [[Memory Hierachy]]
3. Interrupt other user programs
4. Receive and manage I/O requests
5. Manage other user program locations on the RAM, the MMU, and schedule user program executions.

In order for the kernel to have more privileges than other user mode programs, the computer hardware has to support [[dual mode operation]]

## Disabling interrupts
If the kernel allow programs in kernel mode to be interrupted, it is called 

A **re-entrant** kernel allows **multiple** processes to be executing in the kernel mode at any given point of time. However, this may result in [[Race Condition]] problem when processes are executing [[Critical Section|Critical Sections]]


#os