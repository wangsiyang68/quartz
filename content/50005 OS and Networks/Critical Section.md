# Critical Section
Defined as the regions in a program whereby [[Atomicity]] must be guaranteed. For example, when one process is executing its critical section, no other process is allowed to execute its critical section.

Critical sections are often actions upon shared pieces of data. Examples of potential critical sections:
- Changing a **common** variable
- Updating a **shared** table,
- Writing to a **common** file

## Amdahl's Law
Given that a piece of code has a critical section of $\alpha$, then given that there are $N$ CPUs to run the code in parallel, the maximum speedup is
$$\frac{1}{\alpha+\frac{1-\alpha}{N}}$$
## Challenges
 It is a difficult problem to guarantee a critical section will run properly. Therefore, having a critical section in program is a problem and it requires complex synchronization [[Critical Section Solutions|solutions]].

#os