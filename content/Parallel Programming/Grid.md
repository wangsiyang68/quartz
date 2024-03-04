**Purpose**: define a group of [[Threadblocks|blocks]]. All CUDA threads in a grid execute the same kernel function. That is why during the [[Instantiating cuda kernels|instantiation]] of a CUDA kernel, you define the number of threadblocks in a grid and threads in a threadblock, because you will create 1 grid with the specified amount of threadblocks and threads, which will then run the same said kernel.

**Funfact**: Note that you cannot guarantee the order of the blocks in a grid, as this allows for scalability between GPUs (Some GPUs can run more grids at one go, while others can't)

**Example**: A 3 dimensional grid can be generated with the following host code:
`dim3 dimGrid(2,2,1)`
- `dim3` is a built-in CUDA data type used to represent dimensions for blocks and threads in a CUDA grid. It is a three-dimensional vector-like type that contains three unsigned integers representing the number of threads or blocks along each dimension of the grid.
#pp 