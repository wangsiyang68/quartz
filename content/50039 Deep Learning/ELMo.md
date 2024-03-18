Takes into input the key word and the surrounding text
For the each word in the inputted sentence, produce embeddings for each of them

Key Change: Do not take in word inputs as one hot vectors, but instead decompose the words into characters (one letter at a time)
- Key Insight: Know that there are only 26 latin alphabets, so dimensionality is much reduced

Implementation
- Utilise CNN to get the meaning from context
- Then update the embeddings by transferring context
	- Intuition: similar to how [[LSTM]] propagate Long Term memory, but also bidirectional now this time
	- Also known as Context aggregation using Bi-LSTMs
	- This task was also some similarity to the Context Aggregation Layer in the [[Continuous Bag of Words|CBoW]] model, but its better
- In practice, there is a highway layer between the initial embedding and Bi-LSTM layer for smoother transition
	- Similar to gates used in RNN (forget gate, input gate)
#dl