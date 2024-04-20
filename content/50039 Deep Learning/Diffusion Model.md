Also a Generative Model, inspired by physics (nonequilibrium thermodynamics)
Two key processes: forward and reverse
- Forward process: turn data into noise (training)
- Reverse process: turn noise into data (inference? part)
	- Can reuse the weights here to create new images
	- Difficult, cannot just subtract random noise at this stage to get back the previous stage, it would just be ineffective as it is akin to adding noise
	- Need to estimate/predict the noise that was added to the image during the forward stage
	- Key to doing so is to understand the image

**Forward process**: how is it modelled?
There is this function that is used for generating the next image of the forward function
$$
\text{q}(x_t|x_{t-1}) = \mathcal{N}(x_t;\sqrt{1-\beta_t}*X_{t-1}, \beta_tI)
$$
- Purpose: the conditional distribution $q(x_t∣x_{t−1})$ plays a fundamental role in diffusion models by capturing the temporal evolution of the system, incorporating uncertainty, providing flexibility in parameterization, and enabling the generation of synthetic data for various applications.
- Variance schedule?
	- is $\beta_{t}$, used in the c
- What is the covariance?
- Use it to model the forward process 
- In practice, we reparameterize it to get something simpler:
	- How?
	- why do we create $\alpha_t = 1 - \beta_t$ ?
- Sample $x_t$  at any t in a single step
	- We can directly go from $x_0$ to $x_t$ in one step, without having to go through the proper step by step process, while ensuring that we still do the denoising correctly
- Unroll the $x_t$
	- to do what though?

**Reverse Process** to train a model that can help us remove the noise
- Given $x_t$, what is $x_{t-1}$ (the more clearer image) 
- Assume: Given $x_t$, $x_{t-1}$ is a normal distribution
- And then we go through a bunch of complicated math to find an appropriate target for the denoising step from t to t-1
	- Intuition: Includes proper scaling and subtracting the noise


If denoising aims to predict the noise that was used, then if it is good, then give a random noise, it can hopefully give something interesting?
- Style transfer how?