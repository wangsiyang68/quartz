# Distributed Systems
---
Examples of Distributed Systems:
- Any computer network (Internet, LAN)
- Multi-player online games
- Industrial control systems
- Multi-threading and virtualization
Concerns:
1. Concurrency
	- [[Race Condition]]
		- Interleaving
	- [[Deadlock]]
		- dining philosopher's problem
	- Secure Time
		- How to synchronise the time across the world?
		- NTP (Network time protocol)
			- Has different layers of time servers
			- beyond the atomic clock layer, servers will share the time within the other servers in the same layer (to give redundancy)
				- Redundancy exist to give more reliability (use majority clock voting and authentication of time server is done here)
1. Fault tolerance and SVC recovery
	- A fault may cause an error, this may lead to a failure (deviation from the st)
		- Result in Denial of service
	- Key: **Byzantine Failure**
		- there are t traitors out of the n generals that will convey the wrong message
		- How many traitors can be tolerated?
			- n >= 3t+1
			- how can the servers always reach the right decision when communicating with each other to reach consensus?
	- Two strategies:
		- Redundancy:
			- Goal: preserve integrity and availability of data by having multiple copies of it and checking them them against each other
			- e.g. like having many mongo db databases of the same damn ding
			- Problem: Higher risk of attack due to more points of attack
		- Fail stop
			- create assertions to detect filures and stop processing
			- Problem: Higher risk of availability attacks since you are always checking if stuff is correct

pollard rho algorithm
#foc 