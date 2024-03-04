# Packet Loss
---
Two types:
1) error packet = realised after checking checksum, so drop that packet
2) queue is full, so packet arriving to full buffer is lost

Impact of loss on applications:
- Images: more tolerant, can also infer pixels from surroundings
- Banking: probably alot less tolerant

How to calculate the end to end loss?
- Assume losses to be independent!!
- Therefore, loss rate is multiplicative, but not like $L1* L2* L3$. 
	- Instead, its the success that is multiplicative of each other ($S_{i} = 1 - L_{i}$)
	- So e2e losses are complement of the end2end success rate
#networks 