# OS Design
---
There is no known ultimate solution when it comes to OS design. Internal structures of known operating systems can vary widely. 

## Policy and Mechanism Separation
---
Policy determines **what** will be done while Mechanism determines **how** to do something. The seapration of policy and mechanism is important for flexibility, as policies are likely to change across places/time.

## OS Structures
---
**Monolithic Structure**
Entire OS in kernel space
*Without Dual Mode*
E.g.MS-DOS

*With Dual Mode*
E.g. Early versions of UNIX-OS

**Layered Approach**
Kueh lapis style
E.g. Windows NT

**Microkernel**
Minimalist style
E.g. First version of Windows NT, Mach

**Hybrid Approach**
Combines both microkernel and monolithic kernel aspects and benefits
E.g. MacOS
#os