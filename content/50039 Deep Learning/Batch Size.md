Batch v. Stochastic v. Mini-Batch

## QnA
- Why is stochastic faster than batch?
	- Because you get updates immediately after training on one data point, while in batch you have to wait for all the data points to go through before you can get an update 
- Why is stochastic more erratic than batch?
	- Because one data point does not generalize well to the whole dataset. Batch on the other hand, will update the model based on all the learnings from all data points, which is a much better learning compared to the stochastic style
- How does the Backprop actually work in any batch size larger than 1?

#dl