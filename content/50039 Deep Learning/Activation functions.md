## Definition
Activation functions are used determine the output of a neural network layer, which is then passed on to the next layer as input. They usually have the following desirable characteristics:
1. **Non-linearity**: Activation functions introduce non-linear transformations to the output of neurons. This allows neural networks to model complex, non-linear relationships in the data. Without non-linear activation functions, neural networks would reduce to a linear transformation, making them unable to learn complex patterns.
    
2. **Differentiability**: Activation functions should be differentiable, at least almost everywhere, so that gradient-based optimization algorithms like backpropagation can be used to train the neural network. The ability to compute derivatives is crucial for updating the weights of the network during the training process.
    
3. **Range of output values**: Activation functions typically have a bounded range of output values. This helps stabilize the training process and prevents the activation values from growing too large, which can lead to numerical instability (e.g., vanishing or exploding gradients).
    
4. **Output behavior**: Different activation functions have different output behaviors. For example, some activation functions squash the input to a specific range (e.g., between 0 and 1 or -1 and 1), while others allow the output to range from negative to positive infinity. The choice of activation function depends on the requirements of the specific problem and the characteristics of the data.
    
5. **Computational efficiency**: Activation functions should be computationally efficient to evaluate. Since activation functions are applied element-wise to the output of each neuron in a layer, efficient computation is essential for training large-scale neural networks.

## Examples of Activation Functions
- Relu Family
	- Just Relu
	- Leaky
	- Exponential
- Tanh
- [[Sigmoid]]
- [[Softmax]]

#dl