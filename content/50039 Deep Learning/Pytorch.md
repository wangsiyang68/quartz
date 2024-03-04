Autograd means no need to calculate gradients 

`torch.no_grad()`
- What it does
	- Turn off the autograd engine
- When would I use that
	- During the update section of the code because we do not want PyTorch to calculate the gradients of the new defined variables w1 and w2, since we just want to update their values. ([Source](https://datascience.stackexchange.com/questions/32651/what-is-the-use-of-torch-no-grad-in-pytorch))

#dl