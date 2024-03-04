Decomposition
- Trend (long term)
- Seasonal (periodic fluctuation)
- Residual (random fluctuations)

History is important for NN to understand the context of a datapoint
- History refers to the amount of datapoints in the past (i.e. $x_{t-1}$)
- History length is like a hyperparameter -- need to train a few times to figure out what is the best
	- Problem: increase in history length necessitates less data points used for training (because the first $x-1$ data points cannot be used for history length $x$)
	- Sort of a solution: pad the start with 0, which may not be as accurate but prevents us from losing the first few datapoints

This problem leads us to having a memory
- This memory is hidden, and is randomly initialized as first (unlearnt)
- After training, the memory has been trained with the correct information to put inside there
	- Hopefully it keeps memory of what has happened in the previous operations

This leads us to a [[Recurrent Neural Network]], which takes in a current value, history, and then outputs the predicted next value, and updated history


## Problems
However, the RNN has a vanishing gradient problem, due to the fact that the memory in the later stages depend on many terms, therefore resulting in a vanishing gradient when doing differentiation

In addition, the current input $x_{t}$ and memory $h_{t-1}$ are still treated the same way, i.e. same calculation, same weight, but they are different parameters and should be treated differently during training

Selectively choose what to remember and forget; an application of this is the [[LSTM|Long Short Term Memory]]

Besides the LSTM model, there is also the [[GRU|Gated Recurrent Units]] models to simplify it

However, LSTM is better than GRU, unless speed is crucial 

GRU benefits:
- Fewer parameters
	- Other than faster to train, less prone to verfitting
	- Can better handle noise/missing data 

#dl