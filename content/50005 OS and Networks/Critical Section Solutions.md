# Critical Section Solution
---
## Solution Requirements
**Mutual exclusion**
No other process can execute the critical section if there is already one process executing it.

**Progress**
Link to the dining philosophers problem
If there is **no** process in the critical section and some other process wish to enter, the CPU need to grant permission to the waiting process and cannot postpone the permission indefinitely.

**Bounded waiting**
Idea: A process can only wait for a finite amount of time before process is accessed, to avoid starvation. Not the same as busy waiting

results in safety (no race condition) and liveness property (will not hang forever; no progress is [[Mutex]] after all)

## Solution Template
---
analogous to using a toilet cubicle and doing [[Critical Section|critical sections]]
`
```
while(true){
   
   [ENTRY SECTION] #lock here
      CRITICAL SECTION ...
      ...
   [EXIT SECTION] #unlock here
      REMAINDER SECTION ...
      ...
}
```

## Solution Types
1. Software Mutex (outdated, related to [[Peterson's Solution]])
2. [[Hardware supported spinlocks]] (expensive but key to the rest, 4,5,6 implementations)
3. [[Software Spinlocks]]
4. [[Mutex Locks]]
5. [[Semaphores]]
6. [[Conditional Variables]]

## Busy Waiting
Means wasting my clock cycles by repeatedly checking if the locked lock is unlocked yet.
#os