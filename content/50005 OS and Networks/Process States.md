## Process States
---
As a process executes it changes its scheduling state which reflects the current activity of the process

## States
1. **New**: the process is being created
2. **Running**: Instructions are being executed
3. **Waiting**: The process is waiting for some event to occur (such as an I/O completion or reception of a signal)
4. **Ready**: The process is waiting to be assigned to a processor
5. **Terminated** : The process has finished execution

Sequence of state transition is as follows:
![Process states](images/process_states.png)

#os