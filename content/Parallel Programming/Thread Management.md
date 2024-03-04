Motivation: Some tasks take longer than others. In addition, dynamic scheduling by hardware means that the exact instruction being run by hardware may not be in order as that in code/assembly. 

Therefore, if we can balance the workloads of threads more evenly, this will result in faster runtime

- **Recap** on [[Critical Section#Amdahl's Law|Amdahl's Law]]: The speedup observed depends on the percentage of the parallel section and number of available cores

## Static vs Dynamic assignment
---
What is it?
- Static: Task assignment is decided at compile time
- Dynamic: Tasks are assigned to threads at runtime

Adv and Disadvantages is similar to that of the compiler based vs dynamic based assignment in [[Instruction Level Parallelism]]

