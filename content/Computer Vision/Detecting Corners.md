Rationale: Easier to use corners to identify similar objects with different rotations, resizing

How is this done?
- Matrix arithmetic
- Harris Detector
	1. Compute image gradients over a small region
	2. Subtract mean from each image gradient (Normalization)
	3. Compute the covariance matrix
	4. Compute Eigenvectors and Eigenvalues
	5. Use threshold on Eigenvalues to detect corners

- Harris detector is invariant to rotation and affine intensity change 
- Note that harris detector is not invariant to scale! (might see a more zoomed in image as an edge rather than the corner)

Eigen-intuition:
- Eigen vectors = new set of coordinates (basis) that fits your function better
- Eigen vlaues = new set of values within the 

To find out:
- Singular Value Decomposition?
- How is this related to PCA? (slide 39 of 122 in lecture 05)
- Why do we need the covariance matrix in detecting corners?
#cv 