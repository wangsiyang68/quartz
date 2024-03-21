No closed form because the formula has an additional R matrix, which depends on w, which is the thing you want to find (weights)

In practice, Newton method is not used either because calculating the Hessian is computationally intensive (requires finding the inverse of a matrix)
- However, there is another method used to approximate the Hessian that is faster, and that is used IRL


An extension of logistic regression is [[Softmax Regression]], which is the multiclass version of it
#ml