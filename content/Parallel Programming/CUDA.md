Made up of three relevant libraries
1. [[CuDNN]]
2. CuBLAS
	1. Proprietary code
3. **Cutlass**
	1. Pretty important code because it uses CuBLAS, and this library is open source

## Terminology
- CUDA functions are also called [[Kernel Functions]]
- Memory in GPU is organized into [[Grid|Grids]], [[Threadblocks|blocks]], [[GPU Threads|threads]]
	- Grid is a set of threadblocks
	- Threadblock is a set of threads
![[Pasted image 20230515161711.png]]
- Each threadblock is divided into [[Warp|warps]]
- [[Thread Scheduling]]
## CUDA usage concepts
- [[cudaMalloc]]
- [[cudaMemcpy]]
- cudaError, Success, ErrorMemoryAllocation
- [[Instantiating cuda kernels]]
- [[cudaFree]]
- [[Parallel Programing Methods]]

## CUDA Performance Considerations
- [[GPU Threads|Setting number of threads]]
	- Getting the max # of threads per SM 
- [[Branch Divergence]]
	- Avoiding branch divergence
- [[Shared memory]]
	- Caputre locality with manually managed cache-like memory
	- Avoid bank conflict (not too important in this course)
- [[Coalescing]]
	- Aligning memory accesses to maximize bandwith
- [[Overlap IO with computation|Streams]]
#pp