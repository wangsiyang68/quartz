Instruction-level parallelism (ILP) is a technique used in computer architecture to improve the performance of processors by executing multiple instructions in parallel, rather than sequentially. ILP works by identifying and exploiting independent instructions that can be executed concurrently, without violating the program's semantics.

This ability to execute multiple instructions can be done via a few methods
[[Obsidian/Parallel Programming/Superscalar|Superscalar]] (Hardware-based)
[[Obsidian/Parallel Programming/Out Of Order|Out Of Order]] (Compiler-based) 

Dynamic scheduling: The **CPU** is able to dynamically find Independent (dependency free) instructions and execute them in parallel
- ? is this the same as the Out of Order execution by compiler? or is it out of order done by the CPU
- ChatGPT: refers to the technique of analyzing the dependencies between instructions as they are executed, and scheduling them for execution in parallel when possible. This is achieved through a combination of hardware and software mechanisms, including instruction issue and dispatch, resource allocation, and register renaming.

**Advantages**
The difference in advantages between both methods is that the compiler-based approach has less hardware overhead, resulting in a cheaper/lighter CPU. However, the hardware-based approach is better able to deal with dynamic issues.

**Disadvantages**
Dynamic issues, being like each instructions can take up to 1 cycle to 100 cycles. However, in order for the compiler based approach to ensure its correctness, it needs to wait for the maximum number of cycles, even when most instructions take maybe 1 cycle only. Therefore, the performance gain from compiler based optimization is less than that of the CPU 

#pp