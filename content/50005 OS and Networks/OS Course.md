# Learning Objectives

### Week 1: SGG Ch. 1.1 - 1.6, 1.8.3, 1.13.3
(Background)
Define what an [[Operating Systems|operating system]] is

Describe basic roles of an operating system

Know the difference between [[Kernel|User vs Kernel mode]], and how to switch between each mode using [[System Call|system calls]] and [[Interrupt|interrupt]]

Describe [[Computer System Organisation|computer system organisation]] (basic architecture)

Describe how I/O interrupts occur and how the Kernel handles the interrupt

Describe and understand the basic structure of storage/ [[Memory Hierachy|memory device hierarchy]]

Understand the meaning of [[Timesharing]], [[Context Switch]], [[Process Scheduling| scheduling]], and [[Multiprogramming]] - all of which is part of OS process management 

Understand the basic difference between [[Process]] and [[Program]]

### Week 2: SGG Ch. 2.1 - 2.6, 2.7.1 - 2.7.3, 2.9.2
(Background)
Understand a variety of [[OS Services]] and their applications

Describe ways on [[OS UI|how]] to access OS services

Understand the difference between making [[System Call API|direct system calls vs through API]]

Describe the possible ways to [[Parameter Passing|pass parameters]] using system calls

Describe and understand different types of system calls and their purposes

Understand the difference between [[User Programs|user programs]] and [[System Programs|system programs]]

Describe and understand different types of system programs and their purposes

Understand the basic principles behind [[OS Design|OS design]]: simple, layered, microkernel using  examples: macOS, JX, MSDos, and UNIX.

### Week 3: SGG Ch. 3.1-3.3, 3.4.1, 3.6.1, 4.1-4.2, 4.3.1, 4.4, 4.5.1 - 4.5.2
Key ideas: Process states, fork
Understand the concept of [[Process|processes]], and the difference between codes, programs and processes

Understand the difference between [[Concurrency|concurrency]] and [[Parallelism|parallelism]]

Describe and understand various [[Process States|process scheduling states]] and their transitions

Know the process management terms: [[Process Control Block|process control block]], and context switch. 

Describe different types of [[Process Queue|process queues]] and [[I/O queues]]

Know how to create a new process, e.g: using [[fork()]] in C or ProcessBuilder in Java

Understand how [[Interprocess Communication|interprocess communication (IPC)]] works

Understand the concept of [[Threads]] and its difference with process

Describe two types of threads: [[User and Kernel Threads|user and kernels]] and their models

### Week 4: SGG Ch. 6.1-6.4, 6.5.1, 6.5.2, 6.6.1, 6.8.1 - 6.8.2, 6.8.4
Key Ideas: Synchronisation (e.g. [[Producer Consumer Problem|mpmc problem]], solutions like Peterson, semaphore, mutex), Critical Section Problem, Race Condition, condition synchronisation

Understand issues of multiprogramming and [[Concurrency]]: the [[Race Condition|race condition]]

Describe and understand the concept of [[Critical Section|critical section]]

Discuss how [[Peterson's Solution|Peterson’s solution]] solve the critical section problem

Understand how [[Synchronisation Hardware|synchronisation hardware]] works in general

Describe and explain the concepts of [[Mutex|mutex]] and [[Condition Synchronization|condition synchronization]]

Understand other [[Critical Section Solutions|critical section solutions]] that do not require busy waiting: [[Semaphores|semaphores]]

Explain how semaphores can be used as a mutex and condition synchronization

Understand how [[Java Sync|Java implements synchronization]] using synchronized methods and named condition variables

### Week 5: SGG Ch. 7.1-7.4, 7.5.1, 7.5.3, 7.6.2, 7.7
Key Ideas: deadlock

Understand the problem of [[Deadlock|deadlock]]

Describe necessary conditions for deadlock

Draw and explain [[resource allocation graphs]]

Discuss ways to handle deadlocks through [[prevention]], [[detection]], and [[recovery]]

Describe and understand deadlock avoidance algorithm: [[Banker’s algorithm]]

Describe and understand deadlock detection algorithm

Understand the [[difference]] between deadlock avoidance algorithm and deadlock detection algorithm

### Week 6: SGG Ch.10.1, 10.2, 10.3.2 - 10.3.7, 10.6, 11.2.1
Key Ideas: Unix file systems, `open`, `dup`, `dup2`, directory

Understand what is a [[file system]] and the file system namespace
- [[SWOFT]], [[Inode]] table
Understand [[file format]] and [[type]]

Describe and explain possible [[File Operations|operations]] on file

Describe the concepts and the difference between [[file data]] and [[metadata]] (Attributes)

Learn the concepts of [[file descriptors]] and [[file system data structure]], i.e: how the OS stores files in the memory

Understand [[UNIX file system]] [[data structures]] and [[File System Mapping|mapping]] between table entries

Describe the concepts of [[directory]] [[structures]] : tree structures (acyclic and cyclic)

Discuss the difference between symbolic and hard [[links]]

## Lab deliverables
Understand and write [[C]] code
Write shell program in [[Programming assignment 1]]

## Exam Pointers
### MCQ questions
### Short Answer questions
### Long answer questions
Format: 5 questions, covering 4 topics 
- 1x Process, fork
	- Draw the process tree diagram properly
	- threads and processes diagram, meaning
- 2x Race Condition (Producer and Consumer)
	- ~~Detection Solution details
		- ~~Peterson Pseudocode~~
		- ~~(Mutex Lock) Java sync template code~~
			- Conditional Synchronization (reentrant lockout?)
	- ~~Solution requirements~~
	- Conditional Synchronization in general
	- ~~Bounded Buffer template code~~
- 1x Deadlock
	- ~~Resource allocation graph~~
		- ~~How to draw?~~
		- ~~what are the conditions for possibly having deadlock~~
- 1x File System
	- what is the difference between dup and dup2 and what do they all do anyway
	- what is the purpose of a hard link
	- what are some of the key file attributes? (copy into table)

#os