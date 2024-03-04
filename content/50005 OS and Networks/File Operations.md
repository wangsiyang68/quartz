# File Operations
---
We can perform **operations** on files, and these operations are possible through the file interface or methods, analogous to the **interface/methods we implement for classes in OOP.**

### File Creation

To create a file, we need to ensure two things are done:

-   A free **space** in the system storage must be found for the file.
-   An **entry** for the new file must be made in the directory (details provided later).

### File Read and Write

In order to R/W to a file, you must first have the **permission** to `open` the file.

> Remember from Lab 1: The creator of the file can modify such permissions using `chmod` command.

If permitted, you must then:

1.  **Open** the file.
    -   This can be done using system call `open()`. There are other methods of opening the file depending on your programming language.
2.  Perform the read/write operation using its respective **file pointer**, to indicate where exactly in the file we want to write or read, _byte by byte_.
3.  **Close** the file.
    -   This can be done using system call `close()`.

### File Deletion

To delete the file, we need to search the **directory** to find the file given the file’s path, and also remove it from the file system (more details later). This action also frees the space initially occupied by the file’s content

### File Truncation

In file truncation, we want to keep all the file attributes but remove its content. We search the directory given the file’s path. Once found, the file length is reset to be zero, and its file space for the content is released.

### File Reposition

This requires us to first have permission to `open` the file and gain a file pointer. And then we reposition the value of the file pointer to be pointing to other portion of the file (e.g: byte N of the file). This can be done in C using `lseek()`
Note that lseek is a system call

## Others

#os