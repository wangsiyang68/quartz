# Daemon
---
A daemon is a background process that performs a specific function or system task. Note that it is created in User Mode. Since it is run in the background, it should not require any user interaction

From Programming Assignment 1, we learn that a Daemon has the following characteristics:
## Characteristics of a Daemon Process

A daemon process is still a normal process, running in **user mode** with certain characteristics which distinguish it from a normal process.

The characteristics of a daemon process are listed below.

### No controlling terminal

By definition, a daemon process **does not require direct user interaction** and therefore must detach itself from any controlling terminal.

In the `ps -ef` output, if the `TTY` column is listed as a `?` meaning it does not have a controlling terminal.

![](https://natalieagus.github.io/50005/assets/images/pa1/9.png)

### PPID is 1

The PPID of a daemon process is 1, meaning that whoever was creating the daemon process must **terminate** to let the daemon process be **adopted** by the `init` process.

### Working directory: root

The working directory of the daemon process is typically the `root` (/) directory.

### Closes all uneeded fd

It closes all unneeded file descriptors. In **Unix** and related computer operating systems, a file descriptor (FD, less frequently fildes) is an abstract indicator (handle) used to access a file or other input/output resource, such as a pipe or network socket.

Also, it **closes** and **redirect** fd 0, 1, and 2 to `/dev/null`.

### Logging

It logs messages through a **central** logging facilities: the `BSD syslog`.

#os 
