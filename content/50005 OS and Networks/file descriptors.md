# File Descriptor
---
The fd table exists per-process.

Whenever a process `open()` or `dup()` a file, the opened file is associated with a **file descriptor**.
#todo figure out the difference between `dup()` and `dup2()`

-   A file descriptor is a number that **uniquely** (unique in that process) identifies an open file in a computer’s operating system
-   A file descriptor has a file `pointer` field, that is a pointer to the **system wide open-file-table**.

There are 3 standard fd per process (i.e. Each process has three fd modes)

-   **0u**: This is `stdin` (standard input stream), obtained from the terminal (eg: `/dev/ttys011`)
-   **1u**: This is `stdout` (standard output stream), directed to the terminal
-   **2u**: This is `stderr` (standard error stream), directed to the terminal as well

When open is called,
- the smalled id that is not used in file descriptor table will be allocated to the file
- so file ptr of that fd will link to an open row in [[SWOFT]]
- New [[SWOFT]] entry will create a pointer to its inode entry

#os