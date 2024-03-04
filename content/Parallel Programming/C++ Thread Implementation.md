Wait for thread to finish by calling the **.join()** function. Bad idea to unintentionally leave some threads running on its own while the parent has ended in general
- If thread is detatched, then it will only end when the parent funciton that has called it crashing
- If you dont join and detatch, it is akin to not using freeing memories after use. You end up having zombie threads because they have resources but they cant be called

## Initialization
---
There are three ways to run a thread:
1. Function Pointer
2. Function Object
	1. Difference with pointer is that a class is created with a operator() function
3. Lambda expression

## Criticial Section Issues
---
How to deal with [[Race Condition]]?
- Use [[mutex]]es, which is a special variable
- Try to use a lock_guard as below, because this ensures that the mutex is also unlocked even if the thread is terminated unexpectedly (e.g. due to an exception). This concept is also known as RAII, short for Resource Allocation Is Initialization
![[Pasted image 20230322203333.png]]
## How to deal with [[Deadlock]]?
---
- One way is to lock the mulitple mutexes together
- Use std::adopt_lock to indicate that the mutexesare already locked

To find out: 
C++ implementation? 
Busy wait, busy wait + sleep, interrupt?

#pp 