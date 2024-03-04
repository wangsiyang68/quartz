**How does it happen**:
1. [[Warp]] selector chooses a warp that is ready and executes it
	1. Ready = all the operands for that warp are in the registers

To note:
- SM implements zero-overhead warp scheduling
	- It is able to do so as all the information needed for the warps are kept within the SM.
- All threads in a warp execute the same instruction when the warp is selected. 
	- This has implications for branching.
	- During branch, the warp cannot run both outcomes of an if else statement since both outcomes are different instructions.
		- This results in some threads running an outcome, and the rest being idle
		- Causing low resource utilization!
- When initializing the number of threads, we always prefer to create way more than there are in GPU to ensure that there is always a thread for thread scheduler to run. Note that this is possible only because of the low cost of context switching between threads in GPU

Potential reason for low performance
1. Too small # of warp per block
	1. Increase the number of threads per block
2. High memory conflict
	1. Decrease the number of memory ops per thread
	2. Increase the efficiency of memory coalescing

#pp