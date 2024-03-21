## Methodology
The key difference between convolutional layers and fully connected layers as described in Neural Networks are that only a local set of pixels are connected to an activation function in convolutional layers.

Therefore, the output of a filter convolved with a local area of the image is output to the corresponding coordinates in the output layer. By stacking multiple convolutional layers together and training them via backpropagation, we are able to create layers that are able to discriminate against complex features (e.g. eyes in a face)  

When the convolutional filter is convolved with the image, there are filter size, stride and zero padding radius to consider. The filter size is the length of the square filter convolving with the image. The stride is the interval at which the filter convolves with the image. The zero padding radius is the number of layers of 0's that are added along the perimeter of the image, which prevents the image from eventually shrinking after many rounds of convolutions. The output dimensions of the convolutional layer can be described as:
 $$ (N - F + 2P)/S + 1 $$
Where 
N = image length  
F = filter length
P = padding radius
S = stride length  

## Usage
1. Small filters are often used to reduce parameters needed. In fact, 1x1 filters are often employed

#cv