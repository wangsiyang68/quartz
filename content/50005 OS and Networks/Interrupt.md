# Interrupts
Interrupt-Driven I/O operations allow the CPU to efficiently handle interrupts without having to waste resources, such as waiting for asynchronous interrupts. There are two kinds of interrupts, [[#Hardware Interrupt|hardware]] and [[#Software Interrupt|software]] interrupt

## Contents
---
1. [[#Hardware Interrupt]]
2. [[#Software Interrupt]]

## Hardware Interrupt
---
Input from external devices activates the interrupt-request line, thus pausing the current execution of [[User Programs]].

**Process**
Upon presence of new input (e.g. keyboard press, mouse click, or completion of previous I/O requests made by drivers), the device controllers will invoke an interrupt request by setting the bit on the interrupt-request line.

**Vectored Interrupt System**
In this system, the interrupt signal includes the identity of the device sending the interrupt signal, hence allowing the kernel to know exactly which interrupt service routine to execute. It is more usefull when there are sparse I/O request.

**Polled Interrupt System**
The interrupted program enters a routine, where the CPU scans all devices to determine which device made a service request. As a result, the kernel must send a signal out to each controller to determine if any device made a service request periodically. It is simpler to implement, but more time-wasting if there I/O requests are sparse.

## Software Interrupt
---
A software generated interrupt that is invoked from the instruction of a program itself because the current execution of user program needs to access [[Kernel]] services

#os