Most data structures are not thread safe.

## Linked List
---
- Naive solution: place a lock on the data structure
	- Drawback: This is very costly because only one thread can access the thread at a time
- Better solution: place multiple locks on the data structure, aka Fine Grained Locking
	- Node by node lock
		- Locks one node -- how does it work?
		- But there is a problem -- what is it?
	- Hand over hand locking
		- Locks two nodes -- how does it work?

## Hash Table
---
Have Naive solution of single lock/lock for each bin
- Better solution: Lock striping
	- Coarse grain, basically a few locks, each lock is responsible for a few bins, generally in terms of every nth lock