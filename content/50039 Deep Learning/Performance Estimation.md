## Reduce hyperparameters
- Number of epochs
- Number of training examples
- Input resolution

## Without full training
- Use only a single minibatch of training data
- Use only one forward and backward pass
- Use no data and no forward/backward pass?
	- Use number of parameters as a proxy
- GradNorm
	- Square root the summation of gradients of loss on all the praameters

## Kendall Rank correleation coefficient
- To evaluate the suitability of a metric in evaluating a specific series of models
	- A pair (xi​,yi​) and (xj​,yj​) is concordant if the ranks for both x and y move in the same direction, otherwise discordant
	- Get the difference between concordant pair and discordant pairs $(C - D)$
- x is the thing you want to check (e.g. number of parameters), y is the accuracy
- Divide by the number of combinations, which is $\frac{(n)(n-1)}{2}$

Formula:
$$ 
\tau = \frac{2}{n(n-1)} \sum_{i<j}{\text{sign}(x_{i}-x_{j})} *\text{sign}(y_{i}-y_{j})
$$

#dl