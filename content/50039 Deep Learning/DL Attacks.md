## Types of attacks
1. Reduce performance of model (confuse it) by doing smth specific (e.g. adding special type of noise to give wrong label)
	1. Apply gradient-based optimization to compute the perturbation
	2. Use gradient ascent to change the image to increase the loss (**add** the loss * epsilon to the image)
	3. And then only take the **sign/direction of the loss** to the input, so that the perturbation still works while making the difference imperceptible.
		1. This is also known as FGSM (Fast Gradient Sign Model) Besides adding noise, we can also subtract the loss with respect to another low confidence category, doing gradient descent goes towards the other class type
	2. Surrogate Attack
		1.  a type of black box attack
		2. Recreate copy g of the model f being attacked
		3. Produce attack sample of white box attacks mentioned earlier on recreated model g
2. Infer private training data used

## Defense 
1. Use adversarial training
	1. Expose model to adversarial inputs during training, allowing it to learn from these perturbed examples and not to be fooled when seeing them in the inference stage.

#dl