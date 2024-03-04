# Interprocess Communication (IPC)
Processes executing concurrently in the operating system may be either independent processes or cooperating processes. By default, processes are independent and isolated from one another. However, a process is considered cooperating if it can affect or be affected by the other processes executing in the system.

## Contents
1. [[#Rationale]]
2. [[#IPC Methods]]
3. [[#Comparison]]

## Rationale
---
Processes may need to cooperate due to the three reasons:
1. Information sharing
2. Speeding up computations
3. Modularity (protect each segments) and convenience

## IPC Methods
---
There are two main methods of interprocess communication: Shared Memory and Message passing.

### Shared memory
Shared memory is a region in the RAM that can be created and shared among multiple processes using [[System Call]]
Each VM context will be allocated a shared memory within their own VM space. It requires synchronisation (e.g. dont want a process to start writing while another is yet to finish reading). Or else will face race condition problem (similar to [[TOCTOU]])

### Message Passing
Every message passed back and forth between writer and reader through this method must be done using kernel help. Implemented with [[Sockets]]

## Comparison
---
-   **Number of system calls made:**
    
    -   Message Passing, e.g: via socket requires **system calls** for each message passed through `send()` and `receive()`but it is much quicker compared to shared memory to use if only small messages are exchanged.
        
    -   Shared memory requires costly system calls (`shmget` and `shmat`) in the beginning to create the memory segment (this is very costly, depending on the size, pagetable update is required during attaching), but **not afterwards** when processes are using them.  
        
-   **Number of procs using:**
    -   Message passing is **one-to-one**: only between two processes
        
    -   Shared memory can be shared between **many** processes.  
        
-   **Usage comparison:**
    -   Message passing is useful for sending **smaller** amounts of data between two processes, but if large data is exchanged then will suffer from system call overhead.
        
    -   Shared memory is costly if only small amounts of data are exchanged. Useful for **large** and frequent data exchange.  
        
-   **Synchronization mechanism:**
    -   Message passing **does not require any synchronisation** mechanism (because the Kernel will synchronise the two). It will block if required (but can be set to not be blocking too, i.e: block/not block if there’s no message to read but one process requests to read)
        
    -   Shared memory requires **additional synchronisation** to prevent **race-condition** issues (burden on the developer). There’s no blocking support. It also has to be **freed** after they are no longer needed, otherwise will persist in the system until its turned off (check for existing shared memories using `ipcs` in terminal)

#os