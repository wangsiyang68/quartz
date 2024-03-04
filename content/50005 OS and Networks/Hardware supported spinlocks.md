# Hardware spinlocks
---
hardware spinlocks are possible because many modern computer systems provide special hardware instructions that allow us to either test and modify the content of a word or swap the contents of two words [[Atomicity|atomically]]. 

**Note**: Reason for having these special hardware instructions:

To solve [[Critical Section]] problem in a single core architecture, one will only need to [[Kernel#Disabling interrupts|disable interrupts]] from occurring while a shared variable was being modified. However, in a multi-core architecture, this is not realistic because 
1. Disabling interrupts is time consuming as the message is passed to all processors
2. Message passing will delay entry into critical section
3. If system clock is kept updated by interrupts, it can go out of sync if interrupts are disabled for a long time

#os
