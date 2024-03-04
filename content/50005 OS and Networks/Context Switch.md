# Context Switch
---
Context switch is the routine of saving the [[Process States|state]] of a [[Process]], so that it can be restored and resumed at a later point in time. 

## Process details
---
When a CPU switches execution between one process to another, the [[Kernel]] has to store all of the process states onto its corresponding [[Process Control Block|PCB]], and load the new process' information from its PCB before resuming them.

#os