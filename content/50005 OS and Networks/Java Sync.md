# Java Sync
---
Each instance of a class is a lock
Threads running same method of same instance will be synchronized with each other. which means one at a time, but does not specify order

## Implementation
---
**Synchronised method**
```
public synchronized returnType methodName(args)
{
       // Critical section here
       // ...
}
```

Can also use **synchronised statement**
Create an object called mutexLock, then use a synchronized() statment that 

Also possible to create **Java static locks** where synced methods/attr are static.

Sometimes, certain implementations require you to release the lock N times after acquiring it N times

## Sets
---
Entry Set: ready to run but cannot run because lock not available
Wait Set: also waiting for the lock, but the threads are waiting for a certain condition, **not waiting for the lock**

## Conditional Variable
---
need to check conditional variable inside the synchronized method
no one to wake you thread up

```
public synchronized void doWork(int id)
{
   while (turn != id) // turn is a shared variable
   {
       try
       {
           wait(); 
       }
       catch (InterruptedException e)
       {
       }
   }
   // CRITICAL SECTION
   // ... 
   turn = (turn + 1) % N;
   notify();
}
```

## Exam qns
---
#todo
Why insufficient to just notify instaed of notifyAll?

strategies
make sure that there is a while loop instead of just an if statement
write consumer and producer code side by side
come up with scenarios: 1) empty, 2) filled, 3) partially filled

## Reentrant lock
---
Means can be acquired again by a process already holding on to the lock
allow process to get the lock again, usage is in recursive alogrithms


## Fine grained condition synchronization
---
As opposed to notifyall threads, can notify the right condition too!
Usage: lock, wait, signal
#os 