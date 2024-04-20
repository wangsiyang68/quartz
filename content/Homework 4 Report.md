Wang Siyang
1005485
# Part 1

## Question 1
grad_norm implementation:
```python
def grad_norm(layer):
  grad_norm_arr = 0
  for name, param in layer.named_parameters():
        if param.requires_grad and param.grad != None:
            norm_of_grad_by_layer = torch.sqrt(torch.sum(torch.square(param.grad)))
            grad_norm_arr += norm_of_grad_by_layer
  return grad_norm_arr

def get_grad_norm_scores(net, inputs, targets, loss_fn):
  grad_norm_arr = 0
  ### TODO: Complete the function ###
  loss = loss_fn(net(inputs),targets)
  net.zero_grad()
  loss.backward()

  grad_norm_arr = combine_net_proxy(net,grad_norm)
  return grad_norm_arr
```

SNIP implementation:
```python
def SNIP(layer):
  SNIP_arr = 0
  for name, param in layer.named_parameters():
    if param.requires_grad and param.grad != None:
      product = abs(param.grad * param.data)
      SNIP_arr += torch.sum(product)
  return SNIP_arr

def get_SNIP_scores(net, inputs, targets, loss_fn):
  SNIP_arr = 0
  ### TODO: Complete the function ###
  loss = loss_fn(net(inputs),targets)
  net.zero_grad()
  loss.backward()
  SNIP_arr = combine_net_proxy(net,SNIP)
  return SNIP_arr
```
---
# Part 2
## Question 1
Working can be found in `part2.ipynb` 
Output vectors of first attention head:
```
[11.9827, 8.0173, 10.0518], 
[11.9472, 8.0528, 10.1584]
```
Output vectors of second attention head:
```
[9.6324, 6.2710, 9.4517], 
[9.1209, 6.0518, 9.0863]
```
Final output embedding vectors of MSA:
```
[53.8413, 43.6049, 29.3166, 37.9379, 57.7125, 20.1036], 
[52.4510, 42.5048, 28.4002, 37.2783, 56.5748, 20.3168]
```
## Question 2
 Explain the following complexity expression for Multi-head Self-Attention
 $\Omega{(\text{MSA})} = 4N'D^2 + 2N'^2D$ 

$N'$ = The number of input embeddings
$D$ = dimensions of the input embedding vectors

**First term**
- 4 because there is 4 types of weights: WK, WQ, WV, W0
- Each of the N embedding vector is dot producted with each of the D weights of D length (since Weights matrix has shape $(D,D)$ 
- Therefore, $4 * N' * D * D = 4N'D^2$

**Second term**
- Once the Q and K matrices are calculated, we carry out dot product on these two matrices to find attention
	- The matrix Q has a shape of $(N, D)$ and matrix K has a shape of $(N, D)$
	- There are $N'$ queries and $N'$ keys, and each dot product has $D$ calculations
	- Therefore, $N' * N' *D = N'^2 D$
- After $\text{softmax}({\frac{QK^T}{\sqrt{d}}})$ is calculated, the attention is multiplied with matrix $V$
	- The attention has a shape of $(N',N')$, while matrix V has a shape of $(N',D)$
	- Each of the $N'$ weights with length $N'$ is dot producted for each of the D embedding dimensions.
	- Therefore $N * N * D = N'^2 D$
- Since both results are $N'^2 D$, the second term is $2N'^2 D$

## Question 3
EMD = Move 2 to 6, 1 to 4

| From\To | 4   | 5   | 6   |
| ------- | --- | --- | --- |
| **1**   | 1   | 0   | 0   |
| **2**   | 0   | 0   | 1   |

My optimal transport plan has a total cost of 7

I move one mass from position 1 to position 4 = 3 x 1 = 3 cost
I move one mass from position 2 to position 6 = 4 x 1 = 4 cost

Total cost = 3 + 4 = 7