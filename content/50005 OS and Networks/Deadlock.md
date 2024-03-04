# Deadlock
Question: what may happen if you need multiple locks for a [[Critical Section]]?
Result: Each [[Process]] will take its own lock, and no one will proceed

## Definitions
Deadlock is a situation whereby a set of **blocked** processes (none can make **progress**) each holding a resource and waiting to acquire a resource held by another process in the set.

## Necessary Conditions
4 conditions are necessary but not sufficient to cause a deadlock

Mutual Exclusion
Presence of [[Mutex]]

Hold and Wait
A process holds allocated resources while waiting for each other

No preemption
A resource cannot be removed from a process holding it

Circular Wait
Each process is waiting for another resource that is being held by another process in the circular dependency.

## Solutions
Kind of like how to deal with crime: prevent (police state), avoidance (policing), detection. Or like body health

**Deadlock prevention**
Prevent any of the four necessary conditions from happening

**Deadlock avoidance**
Check if granting the lock request will result in deadlock
[[Banker's Algorithm]]

**Deadlock detection**
Run from time to time to check if deadlock has happened 

#os