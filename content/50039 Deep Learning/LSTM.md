6 New operations!!
## Components
1. Forget Gate
	1. How much of long term memory will be remembered?
2. Input Gate
	1. Determine how we should update Long Term memory with 2 parts:
		1. Potential LT memory calculated from Input & ST Memory (with Tanh function)
		2. % Potential Memory to Remember calculated from Input and ST Memory (with sigmoid function)
3. Output Gate
	4. Determine the new ST Memory, based on the Output of LT Memory through tanh func & % potential memory to remember
4. Hidden State
## New cell state
$$ c_t = f_t * c_{t-1} + i_t *tanh(W_c * x_t + U_c * h_{t-1} + b_c)$$
- first term: how much of history does model want to remember?
- second term: how much of new input does model want to remember?
- Memory is tracked in different places @ $c_t$ and $h_t$,
	- $c_t$ cell state is memory that retains long term information over time
	- $h_t$ captures the shorter term dependencies of the data

cell state = long term memory
hidden state = short term memory

#dl