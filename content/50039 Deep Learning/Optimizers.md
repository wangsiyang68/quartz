## Basic idea
- Simple Gradient Descent only works well on convex functions
- If not convex, then may often come to local minimum on the error functions
- We need better optimizers

## Components of a better optimizer
1. Momentum
	- Accelerate the training process by updating the weights of the model by reusing values from the past gradients.
	- How is it different from Learning Rate?
		- Idea: If I had a large change of the gradient previously, then I should take a larger step
		- Therefore, I'm keeping information about the previous gradients and using it to calculate how much to move later
		- This is symbolized by another hyperparameter miu, which is the coefficient for the previous gradient update `f'prev`
	- Payoff: may result in a longer time to reach a minimum
2. LR Decay
	- Gradually reduce the learning rate of gradient descent over iterations
	- Start with a relatively high learning rate, which helps the model to converge quickly
3. LR gradient-based control
	- Use the value of the gradients to adjust the LR accordingly
	- What is the difference between this and #1 and #2?
## Unresolved
1. Which of the above is better? What is better at when?

## Types of other optimizers
Overall intuition: All of these are just variations of Gradient Descent, with tweaks to the formula during training by applying the above "components of a better optimizer" to address the problems of naive Gradient Descent

1. Adagrad
	- squared values of the gradients in a single variable
2. RMSProp
	- Running average of the gradients
	- reuses the logic of momentum formula
3. Adam
	- Uses all of momentum, LR decay and LR gradient based control
	- Has two overall variables: V coefficient models momentum, and S coefficient models LR decay + LR gradient-based control

#dl