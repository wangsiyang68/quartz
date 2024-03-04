# File System Mapping
---
Do note that multiple FD entries can point to the same system-wide open file table (**SWOFT**) entry or same file in **inode table** 

**Case 1:** Multiple file descriptor table entries can point to the same system-wide open file table entry.

For example:

1.  Two or more processes read the same file via:
    -   File descriptors are created by one of them and then passed through socket, or
    -   A child inheriting the parent’s file descriptor after fork(). Note that child and parent processes have a separated file descriptor table (note that they are two _different_, separate processes)
2.  A single process that has two or more file descriptors referencing to the same file. In fact, you can do this by doing the system call `dup()` or `dup2()`

**Case 2:** Multiple system-wide open file table entries can point to the same file in the inode table.

We can do this by calling `open` to the **same file** from multiple different processes. The system call `open()` creates a **new entry** in the swoft.

> Both cases are considered as **many-to-one** mapping.

#os