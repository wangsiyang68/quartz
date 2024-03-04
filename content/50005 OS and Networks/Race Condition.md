# Race condition
---
The race condition is defined as a situation where several [[Process|processes]] access and manipulate the same data concurrently **and** the outcome of the execution depends on the particular order in which the access takes place. 

However, since the order of execution is out of the user's control, the result of the program depends on the kernel's scheduling handler, which is not deterministic. 

To avoid race conditions, we need to perform process [[Condition Synchronization|synchronization]] and coordination


#os