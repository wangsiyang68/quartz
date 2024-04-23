## Introduction
Utilise two components: Generator and Discriminator. Both are Neural Networks
- Generator turns random noise into data in dataset to the best of its ability
- Discriminator checks the output from Generator, and checks if it is real (from original dataset) or fake (created by generator)

## Training
- Step 1: Update Discriminator
	- First, train D be able to differentiate between real and fake images real good
		- Utilise gradient ascent to update the discriminator
- Step 2: Fix generator G
	- Second, Train G to fool the discriminator
		- Utilise gradient descent to update the generator
- Math Equation for training (summary)
$$
\underset{G}{min}\underset{D}{max} \text{ (D,G)} = E_{x\sim{p_{data}(x)}} \log{D(x)} + E_{x\sim{p_{data}(x)}}
$$
## Proof
- During the training the optimum discriminator, we will arrive at D*(x)
	- Differentiate to get $\frac{D(x)}{D(x) + G(x)}$, which is the optimum discriminator given p(g)
- During the training the optimum generator, we are also trying to minimize JSD, which means to reduce the divergence between generator model and differentiator model
	- JS Divergence function insert here
	- 
## Model details
- **Upsampling**
	- Need it to increase resolution of feature map
	- All the key information/context that is needed can be represented inside the random data, then we just use a good upsampling kernel to increase the resolution
	- Theres alot of the actual image that does not contribute to the semantics of the image, so we don't need that at the start
	- High dimension at the start will mean that there are more parameters to change. Instead of having weights for the entire high dimension, we just need to now train the transpose kernel to be good
		- use transpose convolution (kind of like the reverse of standard convolution)
			- Take the input value in input matrix, multiply with kernel and put it on the new output at the input value/based on the stride length
- **Divergence**
	- Use JS Divergence which is **symmetric**, instead of KL divergence, which is non symmetric
		- Jenson-Shannon still needs the KL divergence, just that more stuff wrapped around it
		- `0 <= JSD <= ln(2)` is the limits of the JSD value
			- ln(2) being the scenario when P,Q are disjoint
	- Objective of divergence is to measure the difference between the fake data and real data
	- So do I optimize the discriminator

## Difficulties
- Difficult to synchronize D and G performance
	- D too bad -> No meaningful training for G to improve
	- D too good -> G just never gets good?
- Unable to guide G to improve when G is crappy (i.e. P,Q are disjoint)
	- **From the Generator**: when there is a change from very disjoint model, to slightly less disjoint model, the JSD is still at a maximum (since both are still disjoint). So cannot tell that there is improvement -> already saturated at a really poor local minimum -> no further increase (kinda like gradient vanishing)
		- A likely scenario at the start when the two distributions are very disjoint
	- **When Generator is learning from given optimum discriminator**, and disjoint data and generator datasets, differentiation of D with respect to x is near 0, then there is no gradient for generator to learn$$\frac{\partial{D}}{\partial{\theta_{g}}} = \frac{\partial{D}}{\partial{x'}}
\frac{\partial{x'}}{\partial{\theta_{g}}}$$
	- If given less strict discriminator, this problem will be solved as there is some gradient that is non-zero
- Mode collapse
	- Lazy generator; it only produces the easier to produce outputs as they are the ones that can help to minimise the divergence

## Variants 
These variants are proposed to address the problems discussed earlier
- Wasserstein GAN (WGAN)
	- Earth-Mover distance
		- cost to transport distribution Preal to Pg
		- depends on the weight and distance (cost = mass * distance)
		- Moving a probability distribution **shape** to a desired probability distribution **shape**
			- i.e. there is no differentiation of the points in the distribution from start to end
			- There can be many different total costs, depending on how you moved the earth
		- W

#dl