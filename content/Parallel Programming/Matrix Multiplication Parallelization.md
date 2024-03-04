Naive Implementation
- Columnwise block striping
	- Suffers from [[false sharing]] problem
	- Solution to fix this: row wise block striping
- Row wise block striping
	- Assign a row of resultant matrix C to each thread
	- Avoids the False Sharing problem in general because of the memory layout. 
		- Storing the row values will ensure contiguous cache access?
	- However, naive implementation of this will result in [[Cache Misses#Capacity Miss|Capacity Miss]]
 
## Related topics
- [[Cache Misses]]
- spaitial locality and temporal locality
#pp 