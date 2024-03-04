# Semaphores
---
The semaphore can be seen as a **generalised [[Mutex Locks|Mutex Lock]]**. It provides mutual exclusion. It is implemented at the [[Kernel]] level, meaning that its execution requires the calling process to change into the kernel mode via trap (SVC) semaphore instructions. 

## Definition
- An integer variable that is maintained in the kernel, initialized to a certain value that represents the number of available resources for the sharing processes
- Is accessed only through 2 standard atomic sys call operations, `wait() //lock` and `signal() //unlock`
- the `wait()` will block if the argument is `== 0`. If not, it will decrement the argument by 1

```
wait(semaphore *S)
{  S->value--;
 if (S->value < 0)
 {
     add this process to S->list; // this will call block() 
 }
}
```

- The `signal()` will increment the argument by 1

```
signal(semaphore *S)
{
 S->value++;
 if (S->value <= 0)
 {
     remove a process P from S->list;
     wakeup(P);
 }
}
```
## System Calls
Purpose: avoid busy waiting in the user process code, (except in the critical section of semaphore, i.e the wait and signal section), but comes at the cost of going into kernel mode.

## Difference with Mutex Lock
Also use the hardware assisted solutions, but implemented inside the kernel space, unlike the Mutex Locks. 

## Example
To solve the [[Producer Consumer Problem]]
- The chars and space semaphore is to synchronise between 1 consumer and 1 producer
- The mutex_p and mutex_c is to sync between multiple producer and consumers respectively.

## Benefits
This is a high level software solution that relies on [[Synchronisation Hardware|synchronization hardware]] and is considered a more robust tool than mutex lock.

Another benefit is that sempahores does not require busy waiting, unlike [[Peterson's Solution]] and [[Synchronisation Hardware|hardware assisted solutions]]. 
#os