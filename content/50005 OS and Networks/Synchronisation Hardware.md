# Synchronization Hardware
---
The [[Race Condition]] problem can be solved using hardware. All proposed solutions are based on the premise of hardware locking to protect the [[Critical Section|critical sections]]. One difference from software locks are that the number of hardware locks per system is physically limited.

## Background
[[Peterson's Solution]] is a software solution that is not guaranteed to work on modern computer architectures where `LD/ST` might not be atomic (e.g. many processors accessing the same location)

Preventing Interrupts
#todo

Atomic Instructions
#todo 

#os