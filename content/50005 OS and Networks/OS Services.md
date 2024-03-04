# OS Services
The [[Operating Systems|OS]] provides services for user programs.

## Contents
1. [[#Basic support]]
2. [[#Sharing Resources]]

## Basic support
**Program execution**
The system must be able to load a program into memory and run that program upon request. The program must be able to end its execution, either normally or abnormally (indicating error).

**I/O operations**
Interrupt programs and manage asynchronous I/O requests

**File system manipulation**
Read and write to files and directories. Create and delete them by name, search for a given file, and list file information.

**Process communication**
[[Interprocess Communication|Communications]] between processes run in their separate virtual environment may be implemented via shared memory or message passing, in which packets of information are moved between processes by the operating system.

**Error detection**
The OS needs to be constantly aware of possible errors. For each error type, the OS should take the appropriate action to ensure correct and consisten coupling.

## Sharing Resources
**Resource sharing**
Resources must be allocated to different users or jobs when they are running at the same time. Some of these resources include: CPU cycles, main memory, file storage, I/O device routines.

**Resource accounting**
This record keeping may be used for accounting or simply for accumulating usage statistics.

## Network and Security
Provides protection and security against external threats, especially since all access to system resources is controlled.

**Defenses**
Defend against potential threats coming from external I/O devices, including modems and network adapters that may make invalid access attempts. It may also record network traffic and connections for detection of break-ins.

#os