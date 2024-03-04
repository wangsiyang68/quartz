## Motivations
Sometimes, the copying of data is the bottleneck of the performance. If we can parallelize the copying of data and the kernel invocations on sections that are not dependent on the earlier mentioned data, then we can speed up the program.![[Pasted image 20230615105521.png]]
![[Pasted image 20230615105541.png]]

## How is it done
This is mainly accomplished with the use of streams. Within a stream, functions are synchronous with respect to issue order, unless other wise stated (e.g. use of a cudaMemcpyAsync). If you want to guarantee the synchronization within a stream, a possible method is to call cudaStreamSynchronized() function to ensure that each instruction within a stream is synchronous.

## Conditions
- For fast performance, cudaMemcpyAsync requires the data to be put in the [[Pinned Region|pinned region]] of the host memory, as opposed to the pageable memory region. This is because the DMA cannot access the page table, and the pageable memory region stores the data in variable addresses. In contrast, the pinned memory has fixed addresses that allow the memory transfer from host to device quickly (instead of staging the memory from paged to device first, before copying to device)  
![[Pasted image 20230615110038.png]]

#pp