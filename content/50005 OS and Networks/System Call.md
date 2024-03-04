# System Call
---
A piece of code invoked by the program to enter [[Kernel|kernel mode]], so that the program can access privileged instructions.

## Contents
---
1. [[#Definition]]
2. [[#Blocking vs Non-Blocking]]
3. [[#Examples]]


## Definition
---
System calls are programming interfaces provided by the OS Kernel for users to access kernel services. Unlike [[Interrupt#Hardware Interrupt|I/O interrupts]], systems calls are [[Interrupt#Software Interrupt|software generated interrupts]] (trap instruction).


## Blocking vs Non-Blocking
---
A blocking system call is one that must wait until the action can be completed (synchronous). On the other hand, a non-blocking system call can return almost immediately without waiting for the I/O to complete (asynchronous). Each system call will have its blocking and non blocking counterpart

## Examples
---
In general, system calls can be grouped into six major categories: 1) Process control, 2) File manipulation, 3) Device manipulation, 4) Information maintenance, 5) Communication, 6) Protection. Each OS will provide these [[OS Services|services]] through their own specific APIs.

#os