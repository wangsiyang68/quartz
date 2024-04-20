## Theory: Wasserstein Distance
Formula meaning?
- i.e. why got infinite space?

Purpose:
- Earth-Mover distance can give information about the distance between two distributions, even if they are not overlapping
	- Is a more "lenient" discriminator, so that the model can get better signal during the model training
	- Shift away from giving probability of realness of a picture, but instead scoring the given picture 

Direct computation is not easy; another way to compute it is to use critic functions
- Critic function characteristics:
	- layman: gradient cannot be more than 1
	- mathematically: difference between input must be larger than the difference between output
	- Also known as a set of 1-Lipschitz functions.
- Calculate the difference between expectation of D(p(r) values) and D(p(g) values) 
	- Maximise this difference
	- Also known as KR duality
- KR duality simplifies the computation of Wasserstein Distance by transforming it from an infinite space to a limited space over something
	- Last time the D in the GAN JSD minimization function was the discriminant
- Why replace the discriminant to D?

- KR duality can be then used in place of the JSD minimization formula in GAN, thus giving us the WGAN

## Actual implementation
**WGAN-GP**
Impose an additional gradient penalty in addition to the original critic loss
- So that it satisfy the critic function requirement
- It actually is a similar concept to regularization, we cannot just focus on minimizing the initial part (original critic loss)

Other GANs
- CycleGAN
- Conditional GAN
- Style transfer GANs