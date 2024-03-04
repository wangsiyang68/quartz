## Key Idea:
The [[Grid|hierarchy]] of cuda thread organization needs to be strong!

## Main method
Once the [[Kernel Functions|kernel]] (e.g. `add(a,b,c,n)`) is defined, it can be launched from the CPU using the following syntax:

```cu
dim3 dimGrid(32,1,1);
dim3 dimBlock(128,1,1);
vecAddKernel<<<dimGrid, dimBlock>>>(...)
```

The `<<< >>>` syntax is called the "triple angle-bracket" syntax, and is used to specify the launch configuration.

The first parameter specifies the dimensions of the grid in the number of [[Threadblocks|blocks]]. The second specifies the dimensions of each block in the number of threads. Each such parameter is of the `dim3` type. The exact block and thread can then be accessed via the `.x`, `.y`, `.z` parameter of the `blockID` and `threadID` object respectively

## Other methods
For convenience, CUDA C provides a special shortcut for launching a kernel with one-dimensional grids and blocks. Instead of dim3 variables, arithmetic expressions can be used to specify the configurations of 1D grids and blocks. In this case, the CUDA C compiler simply takes the arithmetic expression as the x dimensions and assumes that the y and z dimensions are 1.

`add<<<numBlocks, threadsPerBlock>>>(a, b, c, n);`

In this example, `numBlocks` and `threadsPerBlock` specify the number of [[Threadblocks]] and [[threads]] per block, respectively, to be used in the kernel launch. 

#pp