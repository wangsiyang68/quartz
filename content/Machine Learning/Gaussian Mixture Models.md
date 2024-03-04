## [What is it](https://scikit-learn.org/stable/modules/mixture.html)
A probabilistic model that assumes all the data points are generated from a mixture of a finite number of Gaussian distributions with unknown parameters. One can think of mixture models as generalizing k-means clustering to incorporate information about the covariance structure of the data as well as the centers of the latent Gaussians.

## Related to:
- [[Gaussian Discriminant Analysis]]
	- Except that we do not know of what the label is
	- And that this is a "soft" version, whereby instead of a hard 0,1 indicator function in GDA, we use a responsibility function (a probability function) to decide if a data point belongs to a certain GDA
- [[K-Means]]
	- Like K-means, we do not know of the label
	- Employ the E-M algorithm

## How is it done
(Key Idea)
- Responsibility instead of indicator function is used
#ml