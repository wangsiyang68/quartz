## Architecture

**Positional Encoding**
- Gives extra help to understand the different positioning of words in different languages (e.g. SOV in Korean, SVO in English)
- For example, Values of positional encoding can come from cosine and sine graph values, with the input being token position in input
- The positional values are added to the embeddings, which allows the transformer to keep track of word order
**Utilises [[Attention]] to keep track of relationships between words**
- Self-Attention is a mechanisim to correctly associate each word with another 
- After attention layer, get better embeddings
$$ V_{i} = \sum_{j}^{N}{a_{ij}*v_{j}}$$
- **vectors V, K, Q? Gets the values and keys of what?**
	- Q = query
		- Q blocks have questions we want to ask.
	- K = keys
		- K blocks have important information that helps us answer the questions.
		- Essential information about each token
	- V = values 
		- V blocks have the answers to the questions.
		- The thing that really encodes the information about the thing?
		- $Q*K^T$ is like the weight for V
	- Obtain a similarity score sij using  $Q*K^T$?
	- q,v,k are the same at the start.

- Why does  $\text{softmax}(QK^{T})$ give the similarity score, also known as Attention?
	- Because $Q*K^T$ is a dot product that will help to quantify the similarity 
	- The Query is dot producted against all the Keys, so each token is dot producted against itself and all other Keys
	- The softmax is to give a weighted average of all the values, so that they sum to 1
- Normalize the output with softmax as well, do not want the embedding to change too much
- What is **Multi-Head Attention?**
	- Doing the above calculation of attention values in parallel
	- Improve efficiency/speed
	- Improve performance?
- Train V,K,Q, via forcing them to enter a Linear Layer first
- Go through the [[Encoder-Decoder Model]] multiple times 
**Utilise Output**
- Decoder trains the encoder? Decoder can cheat by taking in the outputs, since we are only really interested in the encoder part of the transformer model?
- What is the Encoder Decoder scheme?
- Note that the key part of this Transformer model is the encoder, which can give you very good embeddings 
**Mask**
- We need to mask the output of the multi-head attention layer because we cannot let the layer cheat too much
- Hide answers that you have not yet produced 
	- e.g. only show up to word number 7 if you are trying to produce the 7th word
#dl 