Consists of repeating E and M step:

Start: Randomly initialize the cluster center

E step: Reassign data to new cluster (based on distance to respective centers)
M step: compute new centers for each cluster

Computation is expensive though

## Properties
- Monotonically decreases over time
- No guarantee for global optimum, only guaranted to reach local optimum
	- Depends on the initialized cluster center, the end result could be stable but a really bad local optimum
	- To avoid:
		- Naively: Run K-means multiple times with different initial cluster centers
		- Initialize cluster centers smartly
- Is a hard clustering assignment 
	- i.e. Each data belongs to exactly one cluster
	- c.f. [[Gaussian Mixture Models]] uses soft clustering
#ml 