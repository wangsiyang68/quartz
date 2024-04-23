## Introduction
- Key Assumption: There is an underlying distribution behind the training data
	- Is it used to calculate the probability of class x given a picture?
		- Yes, given that I have the probability distribution, I can calculate the probability of the distribution giving me a specific example
- Questions:
	- What is MAP and how does it relate to Generative Models?
## Simple context
- GANs to model low/single dimension data (e.g. test scores)
	- How is Maximum Likelihood Estimation used to train Generative models?
		- Find probability of results given distribution parameters
			- Utilise the assumption that all observations in the sample are iid (identical and independently distributed) to reduce the probability of distribution given the model parameters
			- Utilise log to simplify the multiplication into summation
## Harder context
- [[Generative Adversarial Networks]] to model image distribution
	- Cannot use MLE to because images have high dimension space
	- Utilise DNN to encode this complex distribution 
	- Start with random noise
		- Help generator produce diverse sets of data

#dl
