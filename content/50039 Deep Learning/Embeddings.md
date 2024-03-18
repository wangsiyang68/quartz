## Definition
- A function that transforms an object x, into another object x'
- Output mathematically more useful objects than the input

## Properties
Injective
- All input maps towards only one output
	- Non-injective: multiple inputs can be linked to one output
		- If one input could be linked to multiple output is that non-injective?
Surjective
- All output maps towards at least one input
	- Non-surjective: 
Bijective
- Both injective and surjective, one to one mapping exists for all inputs and outputs
- As a result, both input and output should have the same cardinality (same number of elements in the set)

Reason why bijective is good: We want to invert embeddings. We want each input to be encoded as a unique value. Bijective allows us to do that

Therefore Ideally: we have a one-hot vector that maps a single input to output, orthogonal bases

## Problem
However, in language context, this is not the case
- Identical word (input) can have different meaning (output)
	- Within the same language, within different languages etc
	- **Based on the context, you should get different embeddings**
- Identical word should have similar embedding only if same meaning
	- Kitty = Kitten != Kitchen
- Meaning varies based on the context
	- Covid is similar to cold in non medical context
	- However, covid is different from cold in a medical context
- Practically inefficient to store all the words as an orthogonal vector
	- Too much size needed

## Solution
Use AI to produce embeddings
- Frequency-based embeddings (not so popular but is usually the start)
- Prediction-based embeddings ([[Continuous Bag of Words]], [[SkipGram]])
	- Both methods are known as "Word2Vec" methods
	- Start from one-hot vector
	- Then iteratively produce a better embedding
		- Use CBoW model and extract the subsection of the model that gives embedding
	- Then extract the embedding layer
- GloVe (abit dated but it was important and its fast)
- Both methods are considered unsupervised learning
	- The model learns from the distributional properties of the text corpus, such as word co-occurrence patterns, rather than relying on labeled examples.

## Current Approach
Find a universal embedding 
- [[FastText]] by Mikolov...again
- [[ELMo]] to take into consider the context
- Finally we arrive at the current holy grail [[Transformers]]

## Evaluation
- Using Dot product to find the similarity between two word embedding vectors?
- Extrinsic (Evaluate it on another NLP task via transfer learning)
- Intrinsic (Human Judgement -- but flawed)
	- Semantic proximity
		- Similar words are close to each other (use dot product to calculate vectors)
	- Preserve word analogies
		- France - Paris = Germany - Berlin

#dl 