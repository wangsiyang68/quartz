# System Programs
---
System programs, also known as system utilities, provide a convenient environment for program development and execution. They are basic tools used by many users for common low-level activities. These tools are very generic, and thus can be considered as part of the "system" instead of individual user apps that we typically install. **Note** that system programs runs on user mode, just like any other user-level applications. When it requires kernel services, they make [[System Call|system calls]] just like any other user programs. 

## Contents
---
1. [[#Categories]]

## Categories
---
**Package Managers**
These programs create, delete, copy, rename, print, dump, list and generally manipulate files and directories. 

**Status Information**
These programs ask the system for various status information, such as datem time,  amount of avilable memory/disk space, number of users, etc. Examples include: `top, ls, df`

**Programming language support**
Compilers, assemblers, debuggers and interpreters for common programming languages are often provided with the operating system or available as a separate download. Examples include `npm, pip`

**Program loading and execution**
Once a program is assembled or compiled, it must be loaded into memory to be executed. The system may provide absolute loaders, relocatable loaders, linkage editors, and overlay loaders.

**Communications**
These programs provide the mechanism for creating virtual connections among processes, users. and computer systems. They allow users to send messages to one another's screens, to browse web pages, to send email messages, to log in remotely, or to transfer files from one machine to another. Examples include `ssh, pipe(|)`

**Background services**
Launched at boot time (upon startup), these are constantly running system-program processes, which are known as services, subsystems or [[Daemon|daemons]]. One example is the network daemon, a service that listens for network connections in order to connect those requests to the correct processes.

## See also
[[User Programs]]

#os