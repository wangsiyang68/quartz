# User and Kernel Threads
---
Reminder that [[Threads]] are not [[Process|processes]]

## User Threads
This is what programmers typically use -- they are scheduled by a run time library (not the [[Kernel]] scheduler)

## Kernel Threads
---
Schedulable entity/lightweight process 
All kernel threads can see each other

Example: tasks like clearing up RAM in the background, which doesnt have to done immediately

## Mappings
---
**Many to one**
The entire process will block if a user thread makes a blocking system call since kernel isnt aware of the presence of these user threads. However, it is lightweight and does not always need a system call when user thread is created

**One to one**
Whenever a user thread is created, it will be linked to a kernel thread. However, there is a limited amount of threads that can be created to not burden the system

**Many to many**
This is complicated and usually a proprietary software so not much details given

#os