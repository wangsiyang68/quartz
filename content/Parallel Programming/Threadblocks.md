**Purpose**: A thread block is a group of threads that can cooperate and communicate with each other through [[Shared memory]]. The number of threads in a thread block is limited by the hardware, and can be specified by the programmer when launching the kernel. The number of threads in a block is typically a multiple of 32, which is called a [[Warp]].

Logically, all threads in a threadblock are run together, but in real life, the threads are run in warps (a set of 32 threads). Therefore, we cannot guarantee sequential running within threads in a threadblock either

#pp