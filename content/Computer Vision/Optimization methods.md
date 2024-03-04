**Gradient Descent**
- Batch, Stochastic, MinBatch
- Pros and Cons
	- Batch is more accurate than the Stochastic Gradient descent
		- Because Batch takes the gradient of the entire dataset while Stochastic is just one data point 
		- But **Each Update** takes longer than Stochastic Gradient, because we need to calculate the gradient descent for each data point before updating the weight. Each epoch only update once, compared to stoch gradient where each example will give you a new data point

**Other methods:**
- **Closed form**
	- Kind of like finding the derivative of a matrix and setting it to zero to find the minimum
	- Need to find the **data matrix** (??)
	- what is the phi W approx= y?
		- I think this is related to finding an approximation of phi, which is defined by the Moore-Penrose pseudo Inverse
	- Cons:
		- Takes longer (current version takes O(N^3))
		- Matrix inversion is numerically unstable (when?)
- **Newton** 

#ml 