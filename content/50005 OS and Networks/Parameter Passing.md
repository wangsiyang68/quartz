# Parameter Passing
---
System call service routines are just like common functions, which require parameters to run. For example, if we rqeuest a `write`, one parameter required are the bytes to write. In general, there are three ways to pass parameters.

## Contents
1. [[#Registers]]
2. [[#Stack]]
3. [[#Block/Table]]

## Registers
System call can get their parameters from registers. As a result, the kernel will examine certain special registers for that particular system call. This provides for simple and fast access, but there might be more parameters than there are registers.

## Stack
System call can get their parameters from the program stack.

## Block/Table
Systems call can get their parameters from a persistent continguous location (table or block) in the [[RAM]], and then pass the pointer through registers, to be read by the system call routine.

#os