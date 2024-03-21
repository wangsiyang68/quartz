## How does it differ from regular [[Transformers]]?
- **Flatten the patches**
	- $p^2 * c$, where p = length of the patch and c = channel count
	- How are the different channels collapsed? If it is one after another, then won't the similar parts of the photo but different channels have very different position encoding values
	- In total n + 1 tokens, where n is the number of the patches. They usually are vecots
- **CLS token** along with the n linear projection of flattened patches
	- It is learnable
	- Take only the CLS token output from the transformer encoder into the linear classifier, to produce the prediction output
	- Question: what is used to create the CLS token?
- **Layer Normalization** instead of the Batch Norm
	- Layer norm normalizes all features within each sample
		- Take only the normalization values from one sentence?
		- Sentence length refers to the number of tokens in the input sequence, while feature refers to the dimensions or attributes used to represent each token.
- Usually uses **GELU** instead of RELU
	- One advantage is that GELU is smooth, so derivative can be found at $x = 0$

## Some implementation details:
- The positional encoding is calculated with the following formulas:
$$ 
\begin{align*}
\text{PE}(pos, 2i) = 
\begin{cases} 
\sin\left(\frac{pos}{10000^{\frac{2i}{d_{\text{model}}}}}\right) & \text{if } i \text{ is even} 
\end{cases} 
\\
\text{PE}(pos, 2i + 1) = 
\begin{cases} 
\cos\left(\frac{pos}{10000^{\frac{2i}{d_{\text{model}}}}}\right) & \text{if } i \text{ is even} 
\end{cases}
\end{align*}

$$
- Note that the 2i or 2i + 1= index value of the position embedding, not i = index value of position embedding
- $d_{model}$ refers to the length of the Position Embedding (dimension)
- Some intuition:
	- A longer dimension length of the position encoding would result in an even longer period. Therefore it would take even longer before the same number would appear again
- Get K, Q, V vectors = 1 x D * D X $D_k$ (matrix of shape D * $D_{k}$ is the weights bro, weights!)
- Using matrix formulas:
	- Multiply N+1 embeddings with the weights to get Q,K,V
	- Dot product the query and the key
	- Scaling + softmax to get attention
	- Apply the attention to each V vector to get the weighted average of the value vectors.
		- We want the weighted average of the value vectors because that gives me the important parts of the picture patches, summed together with respect to the query
- Multi-head Self Attention:
	- Just some implementation sake details:
		- If single head (which doesnt really happen), then the $D_{k}$ = D
		- However, if multi head, then $D_k$ = $D/h$, where h = number of heads.
		- Dont mix the calculation of dot product from different heads
		- Concatenate the weighted average together to get back the D sized vectors
	- Some intuition of why we use multi-heads:
		- The model can learn attention patterns and capture various aspects of the input image simultaneously
- After using the Multi-head Self Attention, use MLP (Multi-Layer Perceptron)
	- Question: why is MLP used?

## Issues
- Quadratic complexity
	- For N' patches, the complexity is 
		- $\Omega{(\text{MSA})} = 4N'D^2 + 2N'^2D$
			- 4 because there is 4 types of weights: WK, WQ, WV, W0
			- N^2 because need to match n queries for key, and each is D length when dot product, will have D calculations
			- The multiplication between attention and value vectors is mat mul a N' by N' matrix (attn) with a N' by D matrix (N' patches of D length in the V matrix)
- Unable to handle vision problems with different scale objects

## Improvements
- Swin transformer (Sliding Window)
	- Reduce complexity by performing self-attention only within each local window
		- compared to normal ViT, self-attention acrosss all patches in the image
		- The window also moves across the horizontal and vertical axis, by half the window size in the next layer

	- Hierarchical feature maps by merging image patches in deeper layers
		- Concatenate embeddings of each group of 2x2 neighboring patches then do linear projection 
		- In ViT, we would do like 16 pixel by 16 pixel to create 1 embedding
		- However, in Swin Transformer, we would do 4 by 4 pixel to create 1 embedding, then later we do "patch merging" to look at an 8 by 8 pixel area
		- Do the patch merging after n times, where n is to be decided by a hyperparameters
	- No cls token
	- Result: Better identify same objects with different scales 
## ViT with optimum hyperparameters
Also related to [[Convolutional Neural Networks## Finding the right hyperparameters|Setting optimum hyperparamter for CNN]]
- Autoformers?
#dl 