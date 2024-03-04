## Problem
- Setting all parameters as identical constants (e.g. all to zeroes) is a bad idea
	- The learning result is the same for all neurons, hence no convergence happens
	- Lack diversity, which leads to lack of generalization and can prevent the NN from learning complex patterns.
	- Therefore, resulting in symmetry
		- Where there is a tendency of all neurons to have the same weights and processes
		- Is vulnerable to adversarial attacks
## Better solutions
- Random normal initialization (LeCun1998)
	- Sample from a norm distribution
	- But can result in poor results for deep neural networks
	- Better to just use a random initialization in comparison
- Xavier initialization (Glorot2010)
	- Use zero mean and variance adjusted to the number of input/output parameters of the NN
- He Initialization

#dl