Threads are an extension of [[Process]]. They offer [[Concurrency]] but no [[protection]] as they operate in the same address space.

## Contents
1. [[#Benefits]]

## Benefits
1. Responsiveness
	- e.g. Single CPU will serve 3 people simultaneously through [[context switching]]. It does not finish faster, but more progress will be made for each thread initially (i.e. dont have to wait in queue for full 10 minutes before you are served)
2. Low overhead for context switch
	- Does not need to make [[System Call]]

Drawbacks of using Threads:
1. Needs more work for synchronisation

## Thread switching
whether require SVC depends on [[User and Kernel Threads]]
#os