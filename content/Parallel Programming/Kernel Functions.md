**Purpose**
In [[CUDA]], a kernel is a function that runs on the [[GPU]] and is executed in parallel by multiple threads. The kernel is launched by the CPU and runs on the GPU, allowing for parallel execution of the same code across multiple threads.

**Usage**
The kernel function is written in C or C++ and is marked with the `__global__` [[CUDA Qualifier|qualifier]]. This qualifier tells the CUDA compiler that the function should be compiled to run on the GPU and that it can be called from the CPU.

#pp 