## Context
- The reverse task of [[Continuous Bag of Words|CBoW]] task, which is now to predict the context given a single word
- Not an easy task, but it can give us something useful in the intermediate process for the embedding process
- Intuition is that even though the performance in this task is not well, since it is harder than CBoW task, it will try harder, and hence return more meaningful embedding

## Description
- Consider a sliding window to generate surrounding words

[Link](https://paperswithcode.com/paper/efficient-estimation-of-word-representations) to paper with code implementations

#dl
