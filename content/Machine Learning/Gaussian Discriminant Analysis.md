Probabilistic generative models **learn the underlying probability distribution** of the training data by making assumptions about the **joint probability distribution** of all variables that generated the data. The joint probability distribution is typically modeled using a set of parameters that need to be learned from the training data.

The learning process involves finding the values of these parameters that maximize the likelihood of the training data. This is done using a technique called **maximum likelihood estimation** (MLE). MLE involves finding the set of parameter values that maximizes the probability of observing the training data, given the assumed joint distribution.

Once the parameters are learned, the generative model can be used to generate new data points that are similar to the training data. This is done by randomly sampling from the joint distribution of the variables.

Compared to Logistic Regression:

1. More parameters required (M^2) vs M, why?
2. Requries a strong modelling assumption for it to work well, as compared to Logistic Regression 

#ml 