The [[Convolutional Neural Networks|CNN]] training scheme can usually be broken down into the following steps:

1. Dataset Split
2. Data Preprocessing ^78b99f
	1. Zero mean, normalize data 
		1. However, note that only mean is subtracted for convolutional neural networks. Why?
	2. [[Data Augmentation]]
3. Choose CNN architecture
4. Initialize weights
5. Check for reasonable loss
6. Overfit a small section of the data. Why though? ^193abb
7. Tune hyperparameters
	1. e.g. adjust LR

#cv