# Mutex Lock
---
Requries integration with kernel scheduler to prevent [[Critical Section Solutions#Busy Waiting|busy waiting]]. This is because because it will put the requesting [[Threads|thread]]/[[Process]] to **sleep** if the lock has already been acquired by some other thread.

The problem with mutexes is that putting threads to sleep and waking them up again are both rather expensive operations, and they will need quite alot of CPU instructions overhead due to integration with the Kernel Scheduler.

#os