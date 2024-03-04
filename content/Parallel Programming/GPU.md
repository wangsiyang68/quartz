Comparison between GPU and CPU:
- GPUs have higher **latencies** but also higher **bandwith** as compared to CPUs
	- "latency" refers to the delay between the time when a request for data is made and the time when the data is actually available to be used.
	- [[Shared memory]] is a key concept in helping to hide high latencies in GPUs
- GPUs are better for massively **data parallel** operations, while CPUPs are better for **control-heavy** operations
	- [[Context Switch]] is relatively faster in GPU, since each thread's memory are already saved in the warp registers. Therefore, no need for extra cycles to save and reload the current state.

Data should be stored in both the CPU and GPU. 
- In cuda, they can be transferred using some cuda functions


#pp 