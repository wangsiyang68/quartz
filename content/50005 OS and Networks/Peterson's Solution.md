# Peterson's Solution
---
Peterson's solution is a software-based approach that solves the [[Race Condition]] problem, but two restrictions apply:
- Strictly **two** [[Process|processes]] that alternate execution between their critical sections and remainder sections (can be generalised to N processes with proper data structures, but out of syllabus)
- Architectures where `LD` and `ST` are [[Atomicity|atomic]]
- Cannot work in multicore CPU (implication from second condition)

Peterson's solution is **necessary and complete** as a solution for solving critical sections

Intuition: if its your turn `turn == i` and you are ready `flag[i] == true`, then you can enter the critical section (`flag` is like an array that contains the `boolean` value whether you are ready or not)

**Template pseudocode**
Note that the **while** statement of the pseudocode is tricky
The while statement prevents perpetual scheduling of a particular process, hence no queue cutting. Therefore, we will have [[Critical Section Solutions#Solution Requirements|bounded waiting]] 

```
## FOR P[i]
do{
   flag[i] = true;
   turn = j; ## gentleman's agreement to let other go first
   while (flag[j] && turn == j); // this is a while LINE; busy waiting here because if this line is true then P[j] is in critical section 
   // CRITICAL SECTION HERE
   // ...
   flag[i] = false;
   // REMAINDER SECTION HERE
   // ...
}while(true)
```

**Common Exam questions**
change the variables, will any of the three conditions for a solution still be true?
- change via swapping the flag and turn before the cs
change turn to not gentle mans agreement = mutex not guaranteed
Note that if i switch turn's value from j to i in both lines in both processes, that means that 

(ended at 32nd minute)
Mutual Exclusion
Can someone join me while im in the critical section?

Bounded waiting:
Given that I am already waiting, can anyone cut my queue and make me wait indefinitely?

Progress:
if no one waiting, will i go in?
#os