Definition
- CBoW tries to predict a word in the middle of `2k + 1 ` words (k words in front, k words behind)
- Embedding Layer > Context Aggregation Layer > Missing word Prediction layer

How does it work?
- How does embedding layer work?
	- Has a shape DxV, where D << V so that the dimension is much less than what we started with at the one-hot encoding
	- V = vocab size
	- D = dimension of embedding space
- Context Aggregation Layer
	- Summing surrounding word embeddings to produce another vector that describes the **context** for the missing word
	- Context aggregation is not trainable though
	- Gives an "average" context carried by the surrounding words
- Both layers are then iteratively improved by checking how good does the CBoW model predict the missing word

Cons
- Will not be able to convert typos into non-typo embeddings

#dl