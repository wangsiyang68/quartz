## Granularity
---
On one extreme, if each work is split into very granular sections, then easier to ensure a more even assignment of work to each process because each workload is short and similar. However, you will end up entering the critical sections of the program more often, hence wasting time. 

The reverse of each point applies for splitting into bigger sections

## Thread-local work queue
---
Solutions to solve imabalnce in queues:
1. Work stealing
	- Thread steal work from other queue when its own queue is empty
2. Work spilling
	- Thread move/spill work to other queue when the other queue is empty

Difference is in the no.# of producer and writer
#pp 