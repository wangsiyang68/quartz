# Process Control Block
---
The system-wide process table is a data structure maintained by the [[Kernel]] to facilitate [[Context Switch]] and [[Process Scheduling|scheduling]]. Each process metadata is stored by the Kernel in a particular data structure called the process control block (PCB). A process table is made up of an array of PCBs, containing information of current [[Process|processes]] in the system

## Interruption
---
Each time the process is interrupted, the following information in the PCB about the process will be updated:

1.  [[Process States|Process state]]: any of the state of the process – new, ready, running, waiting, terminated
2.  **Program counter**: the address of the _next instruction _for this process
3.  CPU **registers**: the contents of the registers in the CPU when an interrupt occurs, including stack pointer, exception pointer, stack base, linkage pointer, etc. These contents are saved each time to allow the process to be continued correctly afterward.
4.  [[Process Scheduling|Scheduling]] information: access priority, pointers to scheduling queues, and any other scheduling parameters
5.  **Memory-management** information: page tables, MMU-related information, memory limits
6.  **Accounting** information: amount of CPU and real time used, time limits, account numbers, process id (**pid**)
7.  **I/O status** information: the list of I/O devices allocated to the process, a list of open files

#os