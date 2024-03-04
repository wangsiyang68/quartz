# Conditional Variables
---
Conditional variables give access to [[Critical Section]] if lock is given and the specific condition is true.

## Purpose
---
Used when you need threads to be executed in a particular **sequence**, in addition to solving critical section problem

## Initialization
---
need to signal before unlocking in the first thread
in thread two:
- after getting mutex, need to check if condition is true anot
	- The conditional wait function will give thread the mutex if there is conditional == True and mutex is available
	- Need to check condition again because some other process might have changed the condition value between thread 1 and thread 2 (the later thread) runtime

#os