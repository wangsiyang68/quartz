Memory allocated in the pinned region do not get paged back into to the disk, they stay here with fixed addresses until it is freed.

To allocate memory in the Pinned Region, you could use two functions:
- cudaMallocHost: allocates a new section of the pinned memory
- cudaHostRegister: moves a previously allocated section of memory into the pinned region

#pp 