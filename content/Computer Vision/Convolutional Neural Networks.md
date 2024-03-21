CNN are a special type of [[Neural Networks]] that typically made up of a few distinguishing features: 
1. [[Convolutional Layer]]
2. [[Max Pooling Layer]]
3. Receptive Field
	1. part of the image that is visible to a neuron, i.e. later in the middle layer of the model, where a single neuron is able to see large portions of the original
4. Shortcut/skip connections + Residual layer
	1. To prevent vanishing gradient problem in deep neural networks
	2. Add the input to the output, via the skip connection and a few weight layers (residual)
	3. Solves the vanishing gradient because it can skip the few layers (residual) during backprop, where usually gradients vanish after it multiply with the differentials. Provides another path for gradients to backprop
5. Batch Normalization
	1. Note that it is not an optimization layer
	2. Reduce covariate shift
		1. The phenomenon where he distribution of input features change over time during training
	3. When the features are not normalized, a small change in one of the feature will may result in a large change in another, resulting in greater loss
	4. In each mini batch during training, compute the mean and standard deviation across all feature 
6. Dropout layers
	1. Carry the 
	2. Works because reduce co-adaptation: Neurons becoming overly dependent on the specific patterns of activity in other neurons, resulting in inability to generalize to new data

Some techniques that are commonly used when employing CNNs:
1. [[CNN Training Scheme]]
2. [[Transfer Learning]]
3. [[Regularization (CV context)]]

Main challenges facing CNN training:
1. [[Overfitting]]

## Finding the right hyperparameters
- EfficientNet
- A convolutional neural network architecture and scaling method that uniformly scales all dimensions of depth/width/resolution using a _compound coefficient_. 
- Unlike conventional practice that arbitrary scales these factors, the EfficientNet scaling method uniformly scales network width, depth, and resolution with a set of fixed scaling coefficients.
#cvfinals