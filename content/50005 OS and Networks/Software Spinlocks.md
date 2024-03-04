# Software Spinlocks
---
"Spinning" means to repeadtedly check whether the lock is available. For software spinlocks, the solution requires the computer to spin on a hardware assisted atomic instruction (e.g. test-and-set). As a result, it will cause [[Critical Section Solutions#Busy Waiting|busy waiting]]. 

The software spinlock exists in the user space like [[Mutex Locks]]

**Note**: It does not make sense to implement spinlocks in single-core architecture, but it is often used in multiprocessor systems.

This is because the core is stuck busy waiting for the condition to change so that the process thats busy waiting can enter the [[Critical Section]]. Since there is only one core, no one else can change the condition, and the process is now stuck outside the critical section. 

However, if you have another core, the other core can do the task in the critical section while the other core is doing the busy wait with the waiting process.

#os