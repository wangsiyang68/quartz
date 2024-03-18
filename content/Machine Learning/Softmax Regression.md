## Definition
Also known as multinomial logistic regression, softmax classifier, maximum entropy classifier
Note that log in the loss function refers to natural log, i.e. ln
$$ s(x_{i}) = \frac{e^{x_i}}{\sum_{j=1}^{n}{e^{x_j}}}$$
## Purpose
Rescale/normalize values so that the trend is preserved, but the new vector consists of positive values that sum up to one

Steps: 
1. Calculate logits (linear regression)
2. Set probabilities to be above >= 0 (e.g. can take the exponent of each value)
3. normalize so that probabilities sum to 1
4. Compare y_pred value and y_gt value
5. Caluclate [[Cross Entropy]]

## Some intuition
- Cross Entropy loss is set as -log because we want to maximize probability
	- Max(prob) = max log(prob) = min (-log(prob)) (given that the log function is )
- Exponential in the softmax is going to give much higher confidence if the activation is large (imagine e^x1 and e^x2 vs x1 & x2)
#ml 