## Exploding gradients
### What
- Gradient descent rule has changes that are far greater than the current values in the matrices

### Reasons
- Unlucky initialisations
- Bad starting parameters (learning rate, initial weights)
- Used formulas that are not that nicely differentiable, giving gradients that have to be approximated
- 
### Some solutions
- Downscaling initial parameter values
- Gradient clipping
	- Set max value for change on a single gradient
- Time evolution on learning rate 
	- Progressively decrease learning rate over iterations

## Vanishing Gradients

### Reasons
- Maybe set the gradient too low?

#dl