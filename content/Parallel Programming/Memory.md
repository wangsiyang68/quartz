Main Memory (RAM): must be byte addressable

File System: must be page addressable. Can be flash (SSD) or Hard Disk

Recap: 
- Virtual Memory is different from DRAM, in that Virtual memory is a software concept while DRAM is a physical component on the motherboard. Virtual memory can be discontinuous chunks of the DRAM put together, which helps to avoid fragmentations (the wastage of space in DRAM due to the incontiguous space between chunks of memory)

UMA vs NUMA: NUMA is not uniform
- So NUMA has an extra latency if accessing memory in a different chip, because the data needs to travel from other chip to its own chip. This results in performance issue
- To prevent this latency, we can perform thread migration to move cpu to where the DRAM is connected 
	- Thread migration is similar to context switching. The context is saved to the memory, then the thread is then reassigned to the other CPU

#pp 