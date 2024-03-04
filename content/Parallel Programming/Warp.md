**Definition**: A warp is a group of 32 threads that **execute the same instruction at the same time**. In other words, a warp is the basic unit of parallelism in [[CUDA]]. When a CUDA kernel is executed, the GPU schedules the warps for execution on the available hardware resources.


#pp 